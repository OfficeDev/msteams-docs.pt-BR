---
title: Depurar seus chamados e o bot de reunião localmente
description: Saiba como você também pode usar o ngrok para desenvolver chamadas e bots de reunião online em seu computador local.
ms.topic: how-to
keywords: túnel ngrok de desenvolvimento local
ms.date: 11/18/2018
ms.openlocfilehash: e9b77df18c8d80f02134dc7912b5796023082039
ms.sourcegitcommit: 976e870cc925f61b76c3830ec04ba6e4bdfde32f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/27/2021
ms.locfileid: "50014303"
---
# <a name="how-to-develop-calling-and-online-meeting-bots-on-your-local-pc"></a>Como desenvolver bots de chamada e reuniões online em seu computador local

Em [Executar e depurar seu aplicativo,](../../concepts/build-and-test/debug.md) explicamos como usar [o ngrok](https://ngrok.com) para criar um túnel entre o computador local e a Internet. Neste tópico, saiba como você também pode usar o ngrok e seu computador local para desenvolver bots que suportam chamadas e reuniões online.

Os bots de mensagens usam HTTP, mas as chamadas e os bots de reunião online usam o TCP de nível inferior. O Ngrok dá suporte a túnel TCP, além de túnel HTTP; você aprenderá a seguir.

## <a name="configuring-ngrokyml"></a>Configurando ngrok.yml

Vá para [o ngrok](https://ngrok.com) e inscreva-se para uma conta gratuita ou faça logon em sua conta existente. Depois de fazer logon, vá para o [painel](https://dashboard.ngrok.com) e receba seu authtoken.

Crie um arquivo de configuração ngrok (veja aqui para obter mais informações sobre onde esse arquivo pode ser `ngrok.yml` localizado) e adicione esta linha: [](https://ngrok.com/docs#config)

  `authtoken: <Your-AuthToken>`

## <a name="setting-up-signaling"></a>Configurando a sinalização

Em [bots de](./calls-meetings-bots-overview.md)chamadas e reuniões online, discutimos a sinalização de chamada — como os bots detectam e respondem a novas chamadas e eventos durante uma chamada. Eventos de sinalização de chamada são enviados via HTTP POST para o ponto de extremidade de chamada do bot.

Assim como na API de mensagens do bot, para que a Plataforma de Mídia em Tempo Real converse com seu bot, seu bot deve estar acessível pela Internet. O Ngrok torna isso simples: adicione as seguintes linhas ao ngrok.yml:

```yaml
tunnels:
    signaling:
        addr: 12345
        proto: http
```

## <a name="setting-up-local-media"></a>Configurando a mídia local

> [!NOTE]
> Esta seção só é necessária para bots de mídia hospedados pelo aplicativo e pode ser ignorada se você não hospedar mídia por conta própria.

A mídia hospedada pelo aplicativo usa certificados e túnel TCP. As etapas a seguir são necessárias:

- Os pontos de extremidade TCP públicos do Ngrok têm URLs fixas. Eles são `0.tcp.ngrok.io` , e assim por `1.tcp.ngrok.io` diante. Você deve ter uma entrada CNAME DNS para seu serviço que aponta para essas URLs. Neste exemplo, digamos que `0.bot.contoso.com` se refere a , `0.tcp.ngrok.io` `1.bot.contoso.com` refere-se `1.tcp.ngrok.io` a e assim por diante.
- Um certificado SSL é necessário para suas URLs. Para facilitar, use um certificado SSL emitido para um domínio curinga. Nesse caso, `*.bot.contoso.com` seria. Esse certificado SSL é validado pelo SDK de mídia, portanto, ele deve corresponder à URL pública do seu bot. Anote a impressão digital e instale-a nos certificados do computador.
- Agora, configure um túnel TCP para encaminhar o tráfego para o localhost. Escreva as seguintes linhas em seu ngrok.yml:

    ```yaml
    media:
        addr: 8445
        proto: tcp
    ```

## <a name="start-ngrok"></a>Iniciar ngrok

Agora que a configuração do ngrok está pronta, inicia-a:

  `ngrok.exe start -all -config <Path to your ngrok.yml>`

Isso inicia o ngrok e define as URLs públicas que fornecem os túnel para o seu localhost. A saída tem a seguinte aparência:

```cmd
Forwarding  http://signal.ngrok.io -> localhost:12345
Forwarding  https://signal.ngrok.io -> localhost:12345
Forwarding  tcp://1.tcp.ngrok.io:12332 -> localhost:8445
```

Aqui está a porta de sinalização, a porta hospedada pelo aplicativo e a porta de mídia remota `12345` `8445` exposta pelo `12332` ngrok. Observe que temos um encaminhamento de `1.bot.contoso.com` para `1.tcp.ngrok.io` . Isso será usado como a URL de mídia para o bot. É claro que esses números de porta são apenas exemplos e você pode usar qualquer porta disponível.

### <a name="update-code"></a>Código de atualização

Depois que o ngrok for executado, atualize o código para usar a configuração que você acabou de configurar.

#### <a name="update-signaling"></a>Atualizar a sinalização

- Na chamada BotBuilder, altere a `NotificationUrl` URL de sinalização fornecida pelo ngrok.

```csharp
statefulClientBuilder.SetNotificationUrl(
    new Uri("https://signal.ngrok.io/notificationEndpoint"))
```

> [!NOTE]
> Substitua o sinal pelo fornecido pelo ngrok e pelo caminho `NotificationEndpoint` do controlador que recebe a notificação.

> **IMPORTANTE:** a URL deve `SetNotificationUrl` ser HTTPS.

> **IMPORTANTE:** sua instância local deve estar escutando o tráfego HTTP na porta de sinalização. As solicitações feitas pelas chamadas e pela plataforma de reuniões online chegarão ao bot como tráfego HTTP do localhost, a menos que a criptografia de ponta a ponta esteja configurada.

#### <a name="update-media"></a>Atualizar mídia

Atualize `MediaPlatformSettings` o seu para o seguinte.

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
> A impressão digital do certificado fornecida acima deve corresponder ao FQDN do Serviço. É por isso que as entradas DNS são necessárias.

## <a name="next-steps"></a>Próximas etapas

Seu bot agora pode ser executado localmente e todos os fluxos funcionam a partir do seu localhost.

## <a name="caveats"></a>Advertências

- As contas gratuitas do Ngrok **não fornecem** criptografia de ponta a ponta. Os dados HTTPS terminam na URL ngrok e os fluxos de dados não criptografados de ngrok para `localhost` . Se você precisar de criptografia de ponta a ponta, considere uma conta ngrok paga. Consulte [os túnel TLS](https://ngrok.com/docs#tls) para obter etapas sobre como configurar túnel seguros de ponta a ponta.
- Como a URL de retorno de chamada de bot é dinâmica, os cenários de chamada de entrada exigem que você atualize frequentemente seus pontos de extremidade ngrok. Uma maneira de corrigir isso é usar uma conta ngrok paga que fornece subdomains fixos para os quais você pode apontar seu bot e a plataforma.
- Os túnel Ngrok também podem ser usados com o [Azure Service Fabric.](/azure/service-fabric/service-fabric-overview) Para um exemplo de como fazer isso, consulte o aplicativo de exemplo [HueBot.](/microsoftgraph/microsoft-graph-comms-samples/tree/master/Samples/LocalMediaSamples/HueBot/HueBot)
