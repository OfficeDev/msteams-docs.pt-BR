---
title: Depurar seus chamados e o bot de reunião localmente
description: Saiba como você também pode usar o ngrok para desenvolver chamadas e bots de reunião online no computador local.
ms.topic: how-to
ms.localizationpriority: medium
keywords: túnel ngrok de desenvolvimento local
ms.date: 11/18/2018
ms.openlocfilehash: c55ec6e5d7296f4ee04ae3ad3de0f9bb82cfd276
ms.sourcegitcommit: 8a0ffd21c800eecfcd6d1b5c4abd8c107fcf3d33
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2022
ms.locfileid: "63453359"
---
# <a name="develop-calling-and-online-meeting-bots-on-your-local-pc"></a>Desenvolver bots de reunião online e de chamada no computador local

Em [Executar e depurar seu aplicativo](../../concepts/build-and-test/debug.md) , explicamos como usar [o ngrok](https://ngrok.com) para criar um túnel entre o computador local e a Internet. Neste tópico, saiba como você também pode usar o ngrok e seu computador local para desenvolver bots que suportam chamadas e reuniões online.

Bots de mensagens usam HTTP, mas chamadas e bots de reunião online usam o TCP de nível inferior. O Ngrok dá suporte a tuneis TCP, além de tuneis HTTP.

## <a name="configure-ngrokyml"></a>Configurar ngrok.yml

Vá para [o ngrok](https://ngrok.com) e inscreva-se em uma conta gratuita ou faça logon em sua conta existente. Depois de entrar, vá para o [painel e](https://dashboard.ngrok.com) receba seu token de auth.

Crie um arquivo de configuração ngrok `ngrok.yml` e adicione a seguinte linha. Para obter mais informações sobre onde o arquivo pode ser localizado, consulte [ngrok](https://ngrok.com/docs#config):

  `authtoken: <Your-AuthToken>`

## <a name="set-up-signaling"></a>Configurar sinalização

Em [Bots de chamadas e](./calls-meetings-bots-overview.md) reuniões online, abordamos a sinalização de chamadas sobre como os bots detectam e respondem a novas chamadas e eventos durante uma chamada. Os eventos de sinalização de chamada são enviados por HTTP POST para o ponto de extremidade de chamada do bot.

Assim como com a API de mensagens do bot, para que a Plataforma de Mídia em tempo real fale com seu bot, seu bot deve ser acessível pela Internet. O Ngrok torna isso simples. Adicione as seguintes linhas ao ngrok.yml:

```yaml
tunnels:
    signaling:
        addr: 12345
        proto: http
```

## <a name="set-up-local-media"></a>Configurar mídia local

> [!NOTE]
> Esta seção só é necessária para bots de mídia hospedados pelo aplicativo e pode ser ignorada se você não hospedar mídia por conta própria.

A mídia hospedada por aplicativo usa certificados e tuneis TCP. As etapas a seguir são necessárias:

1. Os pontos de extremidade TCP públicos do Ngrok têm URLs fixas. Eles são `0.tcp.ngrok.io`, `1.tcp.ngrok.io`e assim por diante. Você deve ter uma entrada CNAME DNS para seu serviço que aponta para essas URLs. Por exemplo, digamos que `0.bot.contoso.com` se `0.tcp.ngrok.io`refere a , `1.bot.contoso.com` refere-se `1.tcp.ngrok.io`a e assim por diante.
2. Um certificado SSL é necessário para suas URLs. Para facilitar, use um certificado SSL emitido para um domínio de curinga. Nesse caso, seria `*.bot.contoso.com`. Esse certificado SSL é validado pelo SDK de mídia, portanto, deve corresponder à URL pública do bot. Anote a impressão digital e instale-a nos certificados do computador.
3. Agora, configurar um túnel TCP para encaminhar o tráfego para o localhost. Escreva as seguintes linhas em seu ngrok.yml:

    ```yaml
    media:
        addr: 8445
        proto: tcp
    ```

## <a name="start-ngrok"></a>Iniciar ngrok

Agora que a configuração do ngrok está pronta, inicia-a:

  `ngrok.exe start -all -config <Path to your ngrok.yml>`

Isso inicia ngrok e define as URLs públicas que fornecem os tuneis ao seu localhost. A seguir está um exemplo da saída:

```cmd
Forwarding  http://signal.ngrok.io -> localhost:12345
Forwarding  https://signal.ngrok.io -> localhost:12345
Forwarding  tcp://1.tcp.ngrok.io:12332 -> localhost:8445
```

Aqui está `12345` a porta de sinalização, é `8445` a porta hospedada pelo aplicativo e `12332` é a porta de mídia remota exposta pelo ngrok. Observe que temos um encaminhamento de `1.bot.contoso.com` para `1.tcp.ngrok.io`. Isso será usado como a URL de mídia do bot. Obviamente, esses números de porta são apenas exemplos e você pode usar qualquer porta disponível.

### <a name="update-code"></a>Código de atualização

Depois que o ngrok está em execução, atualize o código para usar a configuração que você acabou de configurar.

#### <a name="update-signaling"></a>Atualizar sinalização

Na chamada BotBuilder, altere a `NotificationUrl` URL de sinalização fornecida pelo ngrok.

```csharp
statefulClientBuilder.SetNotificationUrl(
    new Uri("https://signal.ngrok.io/notificationEndpoint"))
```

> [!NOTE]
> Substitua o sinal pelo fornecido pelo ngrok e pelo `NotificationEndpoint` caminho do controlador que recebe a notificação.

> [!IMPORTANT]
>
> * A URL em `SetNotificationUrl` deve ser HTTPS.
>
> Sua instância local deve estar escutando o tráfego HTTP na porta de sinalização. As solicitações feitas pela plataforma de chamadas e reuniões online chegarão ao bot como tráfego HTTP do localhost, a menos que a criptografia de ponta a ponta esteja configurada.

#### <a name="update-media"></a>Atualizar mídia

Atualize o `MediaPlatformSettings` seguinte:

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
> A impressão digital do certificado fornecida no deve `MediaPlatformSettings` corresponder ao FQDN do Serviço. É por isso que as entradas DNS são necessárias.

## <a name="caveats"></a>Advertências

* As contas gratuitas de Ngrok **não fornecem** criptografia de ponta a ponta. Os dados HTTPS terminam na URL ngrok e os fluxos de dados não criptografados de ngrok para `localhost`. Se você exigir criptografia de ponta a ponta, considere uma conta ngrok paga. Consulte [TLS tunnels](https://ngrok.com/docs#tls) for steps on setting up secure end-to-end tunnels.
* Como a URL de retorno de chamada de bot é dinâmica, os cenários de chamada de entrada exigem que você atualize com frequência seus pontos de extremidade ngrok. Uma maneira de corrigir isso é usar uma conta ngrok paga que fornece subdomas fixos para os quais você pode apontar seu bot e a plataforma.
* Os tuneis Ngrok também podem ser usados com o [Azure Service Fabric](/azure/service-fabric/service-fabric-overview). Para ver um exemplo de como fazer isso, consulte o [aplicativo de exemplo HueBot](https://github.com/microsoftgraph/microsoft-graph-comms-samples/tree/master/Samples/V1.0Samples/LocalMediaSamples/HueBot/HueBot).
