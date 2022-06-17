---
title: Depurar seus chamados e o bot de reunião localmente
description: Neste módulo, saiba como você também pode usar o ngrok para desenvolver chamadas e bots de reunião online em seu computador local.
ms.topic: how-to
ms.localizationpriority: medium
ms.date: 11/18/2018
ms.openlocfilehash: 518d0b846737eca7f4c182dba032b2c85366cee6
ms.sourcegitcommit: ca84b5fe5d3b97f377ce5cca41c48afa95496e28
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/17/2022
ms.locfileid: "66143813"
---
# <a name="develop-calling-and-online-meeting-bots-on-your-local-pc"></a>Desenvolver bots de chamadas e reuniões online no computador local

Em [Executar e depurar seu aplicativo](../../concepts/build-and-test/debug.md), explicamos como usar [o ngrok](https://ngrok.com) para criar um túnel entre o computador local e a Internet. Neste tópico, saiba como você também pode usar o ngrok e seu computador local para desenvolver bots que dão suporte a chamadas e reuniões online.

Os bots de mensagens usam HTTP, mas as chamadas e os bots de reunião online usam o TCP de nível inferior. O Ngrok dá suporte a túneis TCP além de túneis HTTP.

## <a name="configure-ngrokyml"></a>Configurar ngrok.yml

Acesse [o ngrok](https://ngrok.com) e inscreva-se em uma conta gratuita ou faça logon em sua conta existente. Depois de entrar, acesse o [painel](https://dashboard.ngrok.com) obtenha o token de autenticação.

Crie um arquivo de configuração ngrok `ngrok.yml` e adicione a linha a seguir. Para obter mais informações sobre onde o arquivo pode ser localizado, consulte [ngrok](https://ngrok.com/docs#config):

  `authtoken: <Your-AuthToken>`

## <a name="set-up-signaling"></a>Configurar a sinalização

Em [Chamadas e em bots](./calls-meetings-bots-overview.md) de reuniões online, discutimos a sinalização de chamada sobre como os bots detectam e respondem a novas chamadas e eventos durante uma chamada. Eventos de sinalização de chamada são enviados por meio de HTTP POST para o ponto de extremidade de chamada do bot.

Assim como na API de mensagens do bot, para que a Plataforma de Mídia em tempo real fale com seu bot, seu bot deve estar acessível pela Internet. O ngrok simplifica isso. Adicione as seguintes linhas ao seu ngrok.yml:

```yaml
tunnels:
    signaling:
        addr: 12345
        proto: http
```

## <a name="set-up-local-media"></a>Configurar mídia local

> [!NOTE]
> Esta seção só é necessária para bots de mídia hospedados pelo aplicativo e pode ser ignorada se você não hospedar mídia por conta própria.

A mídia hospedada pelo aplicativo usa certificados e túneis TCP. As etapas a seguir são necessárias:

1. Os pontos de extremidade TCP públicos do mngrok têm URLs fixas. Eles são `0.tcp.ngrok.io`, `1.tcp.ngrok.io`e assim por diante. Você deve ter uma entrada DNS CNAME para seu serviço que aponte para essas URLs. Por exemplo, digamos que `0.bot.contoso.com` se refere a `0.tcp.ngrok.io`, `1.bot.contoso.com` refere-se `1.tcp.ngrok.io`a e assim por diante.
2. Um certificado SSL é necessário para suas URLs. Para facilitar, use um certificado SSL emitido para um domínio curinga. Nesse caso, seria a partir da pasta `*.bot.contoso.com`. Esse certificado SSL é validado pelo SDK de mídia, portanto, ele deve corresponder à URL pública do bot. Anote a impressão digital e instale-a nos certificados do computador.
3. Agora, configure um túnel TCP para encaminhar o tráfego para o localhost. Grave as seguintes linhas em seu ngrok.yml:

    ```yaml
    media:
        addr: 8445
        proto: tcp
    ```

## <a name="start-ngrok"></a>Iniciar ngrok

Agora que a configuração do ngrok está pronta, inicie-a:

  `ngrok.exe start -all -config <Path to your ngrok.yml>`

Isso inicia o ngrok e define as URLs públicas, que fornecem os túneis para o localhost. A seguir, um exemplo de saída:

```cmd
Forwarding  http://signal.ngrok.io -> localhost:12345
Forwarding  https://signal.ngrok.io -> localhost:12345
Forwarding  tcp://1.tcp.ngrok.io:12332 -> localhost:8445
```

Aqui, `12345` é a porta de sinalização, `8445` é a porta hospedada pelo aplicativo e `12332` é a porta de mídia remota exposta pelo ngrok. Observe que temos um encaminhamento de `1.bot.contoso.com` para `1.tcp.ngrok.io`. Isso será usado como a URL de mídia para o bot. É claro que esses números de porta são apenas exemplos e você pode usar qualquer porta disponível.

### <a name="update-code"></a>Código de atualização

Depois que o ngrok estiver em execução, atualize o código para usar a configuração que você acabou de configurar.

#### <a name="update-signaling"></a>Atualizar sinalização

Na chamada do BotBuilder, altere o `NotificationUrl` para a URL de sinalização fornecida pelo ngrok.

```csharp
statefulClientBuilder.SetNotificationUrl(
    new Uri("https://signal.ngrok.io/notificationEndpoint"))
```

> [!NOTE]
> Substitua o sinal pelo fornecido pelo ngrok e o `NotificationEndpoint` pelo caminho do controlador que recebe a notificação.

> [!IMPORTANT]
>
> * A URL em `SetNotificationUrl`deve ser HTTPS.
>
> Sua instância local deve estar escutando o tráfego HTTP na porta de sinalização. As solicitações feitas pelas chamadas e pela plataforma de reuniões online chegarão ao bot como tráfego HTTP do localhost, a menos que a criptografia de ponta a ponta esteja configurada.

#### <a name="update-media"></a>Atualizar mídia

Atualize o `MediaPlatformSettings` da maneira a seguir:

```csharp
var mediaPlatform = new MediaPlatformSettings
{
    ApplicationId = <Your application id>
    MediaPlatformInstanceSettings = new MediaPlatformInstanceSettings
    {
        CertificateThumbprint = <Your SSL Cert thumbprint>,
        InstanceInternalPort = <Localhost media port>,
        InstancePublicPort = <Ngrok exposed remote media port>,
        InstancePublicIPAddress = new IPAddress(0x0),
        ServiceFqdn = <Media url for bot (eg: 1.bot.contoso.com)>,
    },
}
```

> [!NOTE]
> A impressão digital do certificado fornecida no `MediaPlatformSettings` deve corresponder ao FQDN de serviço. É por isso que as entradas DNS são necessárias.

## <a name="caveats"></a>Advertências

* As contas gratuitas do Ngrok **não** fornecem criptografia de ponta a ponta. Os dados HTTPS terminam na URL do ngrok e os fluxos de dados não criptografados de ngrok para `localhost`. Se você precisar de criptografia de ponta a ponta, considere uma conta ngrok paga. Consulte usar [túneis TLS](https://ngrok.com/docs#tls) obter etapas sobre como configurar túneis seguros de ponta a ponta.
* Como a URL de retorno de chamada do bot é dinâmica, os cenários de chamada de entrada exigem que você atualize com frequência seus pontos de extremidade ngrok. Uma maneira de corrigir isso é usar uma conta ngrok paga, que fornece subdomínios fixos para os quais você pode apontar seu bot e a plataforma.
* Os túneis Ngrok também podem ser usados com o [Azure Service Fabric](/azure/service-fabric/service-fabric-overview). Para obter um exemplo de como fazer isso, consulte o aplicativo [de exemplo HueBot](https://github.com/microsoftgraph/microsoft-graph-comms-samples/tree/master/Samples/V1.0Samples/LocalMediaSamples/HueBot/HueBot).
