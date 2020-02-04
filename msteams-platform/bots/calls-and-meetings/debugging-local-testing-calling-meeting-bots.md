---
title: Como desenvolver as chamadas e bots de reunião online no computador local
description: Saiba como você também pode usar o ngrok para desenvolver chamadas e bots de reunião online no seu computador local.
keywords: túnel ngrok de desenvolvimento local
ms.date: 11/18/2018
ms.openlocfilehash: b6cd2ba5a3866da8085b3da42377ab9e21f12f5f
ms.sourcegitcommit: 4329a94918263c85d6c65ff401f571556b80307b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/01/2020
ms.locfileid: "41672870"
---
# <a name="how-to-develop-calling-and-online-meeting-bots-on-your-local-pc"></a>Como desenvolver as chamadas e bots de reunião online no computador local

Em [executar e depurar seu aplicativo](../../concepts/build-and-test/debug.md) , explicamos como usar o [ngrok](https://ngrok.com) para criar um túnel entre o computador local e a Internet. Neste tópico, saiba como você também pode usar o ngrok e o computador local para desenvolver bots que dão suporte a chamadas e reuniões online.

Os bots de mensagens usam HTTP, mas chamadas e bots de reunião online usam o TCP de nível inferior. O Ngrok dá suporte a túneis TCP, além de túneis HTTP; Você aprenderá como, abaixo.

## <a name="configuring-ngrokyml"></a>Configurando o ngrok. yml

Vá para [ngrok](https://ngrok.com) e inscreva-se para uma conta gratuita ou faça logon em sua conta existente. Depois de fazer logon, vá para o [painel](https://dashboard.ngrok.com) e obtenha o authToken.

Crie um arquivo `ngrok.yml` de configuração do ngrok (veja [aqui](https://ngrok.com/docs#config) para obter mais informações sobre onde esse arquivo pode ser localizado) e adicione esta linha:

  `authtoken: <Your-AuthToken>`

## <a name="setting-up-signaling"></a>Configurando a sinalização

Em [chamadas e bots de reuniões online](./calls-meetings-bots-overview.md), discutimos a sinalização de chamadas, como os bots detectam e respondem a novas chamadas e eventos durante uma chamada. Eventos de sinalização de chamada são enviados via HTTP POST para o ponto de extremidade de chamada do bot.

Assim como ocorre com a API de mensagens do bot, para que a plataforma de mídia em tempo real fale com seu bot, seu bot deve estar acessível pela Internet. Ngrok torna isso simples, adicione as seguintes linhas ao seu Ngrok. yml:

```yaml
tunnels:
    signaling:
        addr: 12345
        proto: http
```

## <a name="setting-up-local-media"></a>Configurando mídia local

> [!NOTE]
> Esta seção só é necessária para bots de mídia hospedados por aplicativos e pode ser ignorada se você não hospedar mídias por conta própria.

Mídia hospedada por aplicativo usa certificados e túneis de TCP. As etapas a seguir são necessárias:

- Os pontos de extremidade de TCP públicos do Ngrok têm URLs fixas. Eles são `0.tcp.ngrok.io`, `1.tcp.ngrok.io`e assim por diante. Você deve ter uma entrada DNS CNAME para o serviço que aponta para essas URLs. Neste exemplo, vamos `0.bot.contoso.com` dizer se refere a, `0.tcp.ngrok.io` `1.bot.contoso.com` refere- `1.tcp.ngrok.io`se a, e assim por diante.
- Um certificado SSL é necessário para suas URLs. Para facilitar, use um certificado SSL emitido para um domínio curinga. Nesse caso, seria `*.bot.contoso.com`. Esse certificado SSL é validado pelo SDK de mídia, portanto, ela deve corresponder à URL pública do seu bot. Anote a impressão digital e instale-a em seus certificados de máquina.
- Agora, configure um túnel TCP para encaminhar o tráfego para localhost. Escreva as seguintes linhas em seu ngrok. yml:

    ```yaml
    media:
        addr: 8445
        proto: tcp
    ```

## <a name="start-ngrok"></a>Iniciar ngrok

Agora que a configuração do ngrok está pronta, inicie-a:

  `ngrok.exe start -all -config <Path to your ngrok.yml>`

Isso inicia o ngrok e define as URLs públicas que fornecem os túneis para seu localhost. A saída será semelhante ao seguinte:

```cmd
Forwarding  http://signal.ngrok.io -> localhost:12345
Forwarding  https://signal.ngrok.io -> localhost:12345
Forwarding  tcp://1.tcp.ngrok.io:12332 -> localhost:8445
```

Aqui `12345` está a porta de sinalização, `8445` é a porta hospedada pelo aplicativo e `12332` é a porta de mídia remota exposta pelo ngrok. Observe que temos um encaminhamento de `1.bot.contoso.com` para. `1.tcp.ngrok.io` Ele será usado como a URL de mídia do bot. Obviamente, esses números de porta são apenas exemplos e você pode usar qualquer porta disponível.

### <a name="update-code"></a>Código de atualização

Depois que o ngrok estiver em funcionamento, atualize o código para usar o config que você acabou de configurar.

#### <a name="update-signaling"></a>Sinalização de atualização

- Na chamada BotBuilder, altere o `NotificationUrl` para a URL de sinalização fornecida por ngrok.

```csharp
statefulClientBuilder.SetNotificationUrl(
    new Uri("https://signal.ngrok.io/notificationEndpoint"))
```

> [!NOTE]
> Substitua o sinal por um fornecido pelo ngrok e `NotificationEndpoint` com o caminho do controlador que recebe a notificação.

> **Importante**: a URL em `SetNotificationUrl` deve ser HTTPS.

> **Importante**: sua instância local deve estar ouvindo o tráfego http na porta de sinalização. As solicitações feitas pelas chamadas e a plataforma de reuniões online alcançarão o bot como tráfego HTTP de localhost, a menos que a criptografia de ponta a ponta seja configurada.

#### <a name="update-media"></a>Atualizar mídia

Atualize o `MediaPlatformSettings` para o seguinte.

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
> A impressão digital de certificado fornecida acima deve corresponder ao FQDN de serviço. É por isso que as entradas DNS são obrigatórias.

## <a name="next-steps"></a>Próximas etapas

Agora, o seu bot pode ser executado localmente e todos os fluxos funcionam de seu localhost.

## <a name="caveats"></a>ADVERTÊNCIAS

- As contas gratuitas do Ngrok **não** fornecem criptografia de ponta a ponta. Os dados HTTPS terminam na URL ngrok e os fluxos de dados descriptografados do `localhost`ngrok para o. Se você precisar de criptografia de ponta a ponta, considere uma conta de ngrok paga. Consulte [TLS túneis](https://ngrok.com/docs#tls) para etapas sobre a configuração de túneis de ponta a ponta.
- Como a URL de retorno de chamada do bot é dinâmica, os cenários de chamadas de entrada exigem que você atualize freqüentemente seus pontos de extremidade do ngrok. Uma maneira de corrigir isso é usar uma conta de ngrok paga que fornece subdomínios fixos para os quais você pode apontar seu bot e a plataforma.
- Os túneis Ngrok também podem ser usados com o [Azure Service Fabric](/azure/service-fabric/service-fabric-overview). Para obter um exemplo de como fazer isso, confira o [aplicativo de exemplo HueBot](/microsoftgraph/microsoft-graph-comms-samples/tree/master/Samples/LocalMediaSamples/HueBot/HueBot).
