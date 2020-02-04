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
# <a name="how-to-develop-calling-and-online-meeting-bots-on-your-local-pc"></a><span data-ttu-id="30a80-104">Como desenvolver as chamadas e bots de reunião online no computador local</span><span class="sxs-lookup"><span data-stu-id="30a80-104">How to develop calling and online meeting bots on your local PC</span></span>

<span data-ttu-id="30a80-105">Em [executar e depurar seu aplicativo](../../concepts/build-and-test/debug.md) , explicamos como usar o [ngrok](https://ngrok.com) para criar um túnel entre o computador local e a Internet.</span><span class="sxs-lookup"><span data-stu-id="30a80-105">In [Run and debug your app](../../concepts/build-and-test/debug.md) we explain how to use [ngrok](https://ngrok.com) to create a tunnel between your local computer and the internet.</span></span> <span data-ttu-id="30a80-106">Neste tópico, saiba como você também pode usar o ngrok e o computador local para desenvolver bots que dão suporte a chamadas e reuniões online.</span><span class="sxs-lookup"><span data-stu-id="30a80-106">In this topic, learn how you can also use ngrok and your local PC to develop bots that support calls and online meetings.</span></span>

<span data-ttu-id="30a80-107">Os bots de mensagens usam HTTP, mas chamadas e bots de reunião online usam o TCP de nível inferior.</span><span class="sxs-lookup"><span data-stu-id="30a80-107">Messaging bots use HTTP, but calls and online meeting bots use the lower-level TCP.</span></span> <span data-ttu-id="30a80-108">O Ngrok dá suporte a túneis TCP, além de túneis HTTP; Você aprenderá como, abaixo.</span><span class="sxs-lookup"><span data-stu-id="30a80-108">Ngrok supports TCP tunnels in addition to HTTP tunnels; you'll learn how, below.</span></span>

## <a name="configuring-ngrokyml"></a><span data-ttu-id="30a80-109">Configurando o ngrok. yml</span><span class="sxs-lookup"><span data-stu-id="30a80-109">Configuring ngrok.yml</span></span>

<span data-ttu-id="30a80-110">Vá para [ngrok](https://ngrok.com) e inscreva-se para uma conta gratuita ou faça logon em sua conta existente.</span><span class="sxs-lookup"><span data-stu-id="30a80-110">Go to [ngrok](https://ngrok.com) and sign up for a free account or log into your existing account.</span></span> <span data-ttu-id="30a80-111">Depois de fazer logon, vá para o [painel](https://dashboard.ngrok.com) e obtenha o authToken.</span><span class="sxs-lookup"><span data-stu-id="30a80-111">Once you've logged in, go to the [dashboard](https://dashboard.ngrok.com) and get your authtoken.</span></span>

<span data-ttu-id="30a80-112">Crie um arquivo `ngrok.yml` de configuração do ngrok (veja [aqui](https://ngrok.com/docs#config) para obter mais informações sobre onde esse arquivo pode ser localizado) e adicione esta linha:</span><span class="sxs-lookup"><span data-stu-id="30a80-112">Create an ngrok configuration file `ngrok.yml` (see [here](https://ngrok.com/docs#config) for more information on where this file can be located) and add this line:</span></span>

  `authtoken: <Your-AuthToken>`

## <a name="setting-up-signaling"></a><span data-ttu-id="30a80-113">Configurando a sinalização</span><span class="sxs-lookup"><span data-stu-id="30a80-113">Setting up signaling</span></span>

<span data-ttu-id="30a80-114">Em [chamadas e bots de reuniões online](./calls-meetings-bots-overview.md), discutimos a sinalização de chamadas, como os bots detectam e respondem a novas chamadas e eventos durante uma chamada.</span><span class="sxs-lookup"><span data-stu-id="30a80-114">In [Calls and online meetings bots](./calls-meetings-bots-overview.md), we discussed call signaling — how bots detect and respond to new calls and events during a call.</span></span> <span data-ttu-id="30a80-115">Eventos de sinalização de chamada são enviados via HTTP POST para o ponto de extremidade de chamada do bot.</span><span class="sxs-lookup"><span data-stu-id="30a80-115">Call signaling events are sent via HTTP POST to the bot's calling endpoint.</span></span>

<span data-ttu-id="30a80-116">Assim como ocorre com a API de mensagens do bot, para que a plataforma de mídia em tempo real fale com seu bot, seu bot deve estar acessível pela Internet.</span><span class="sxs-lookup"><span data-stu-id="30a80-116">As with the bot's messaging API, in order for the Real-time Media Platform to talk to your bot, your bot must be reachable over the internet.</span></span> <span data-ttu-id="30a80-117">Ngrok torna isso simples, adicione as seguintes linhas ao seu Ngrok. yml:</span><span class="sxs-lookup"><span data-stu-id="30a80-117">Ngrok makes this simple — add the following lines to your ngrok.yml:</span></span>

```yaml
tunnels:
    signaling:
        addr: 12345
        proto: http
```

## <a name="setting-up-local-media"></a><span data-ttu-id="30a80-118">Configurando mídia local</span><span class="sxs-lookup"><span data-stu-id="30a80-118">Setting up local media</span></span>

> [!NOTE]
> <span data-ttu-id="30a80-119">Esta seção só é necessária para bots de mídia hospedados por aplicativos e pode ser ignorada se você não hospedar mídias por conta própria.</span><span class="sxs-lookup"><span data-stu-id="30a80-119">This section is only required for application-hosted media bots and can be skipped if you don't host media yourself.</span></span>

<span data-ttu-id="30a80-120">Mídia hospedada por aplicativo usa certificados e túneis de TCP.</span><span class="sxs-lookup"><span data-stu-id="30a80-120">Application-hosted media uses certificates and TCP tunnels.</span></span> <span data-ttu-id="30a80-121">As etapas a seguir são necessárias:</span><span class="sxs-lookup"><span data-stu-id="30a80-121">The following steps are required:</span></span>

- <span data-ttu-id="30a80-122">Os pontos de extremidade de TCP públicos do Ngrok têm URLs fixas.</span><span class="sxs-lookup"><span data-stu-id="30a80-122">Ngrok's public TCP endpoints have fixed URLs.</span></span> <span data-ttu-id="30a80-123">Eles são `0.tcp.ngrok.io`, `1.tcp.ngrok.io`e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="30a80-123">They are `0.tcp.ngrok.io`, `1.tcp.ngrok.io`, and so on.</span></span> <span data-ttu-id="30a80-124">Você deve ter uma entrada DNS CNAME para o serviço que aponta para essas URLs.</span><span class="sxs-lookup"><span data-stu-id="30a80-124">You should have a DNS CNAME entry for your service that points to these URLs.</span></span> <span data-ttu-id="30a80-125">Neste exemplo, vamos `0.bot.contoso.com` dizer se refere a, `0.tcp.ngrok.io` `1.bot.contoso.com` refere- `1.tcp.ngrok.io`se a, e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="30a80-125">In this example, let's say `0.bot.contoso.com` refers to `0.tcp.ngrok.io`, `1.bot.contoso.com` refers to `1.tcp.ngrok.io`, and so on.</span></span>
- <span data-ttu-id="30a80-126">Um certificado SSL é necessário para suas URLs.</span><span class="sxs-lookup"><span data-stu-id="30a80-126">A SSL certificate is required for your URLs.</span></span> <span data-ttu-id="30a80-127">Para facilitar, use um certificado SSL emitido para um domínio curinga.</span><span class="sxs-lookup"><span data-stu-id="30a80-127">To make it easy, use a SSL certificate issued to a wild card domain.</span></span> <span data-ttu-id="30a80-128">Nesse caso, seria `*.bot.contoso.com`.</span><span class="sxs-lookup"><span data-stu-id="30a80-128">In this case, it would be `*.bot.contoso.com`.</span></span> <span data-ttu-id="30a80-129">Esse certificado SSL é validado pelo SDK de mídia, portanto, ela deve corresponder à URL pública do seu bot.</span><span class="sxs-lookup"><span data-stu-id="30a80-129">This SSL certificate is validated by the media SDK, so it should match your bot's public URL.</span></span> <span data-ttu-id="30a80-130">Anote a impressão digital e instale-a em seus certificados de máquina.</span><span class="sxs-lookup"><span data-stu-id="30a80-130">Note the thumbprint and install it in your machine certificates.</span></span>
- <span data-ttu-id="30a80-131">Agora, configure um túnel TCP para encaminhar o tráfego para localhost.</span><span class="sxs-lookup"><span data-stu-id="30a80-131">Now, setup a TCP tunnel to forward the traffic to localhost.</span></span> <span data-ttu-id="30a80-132">Escreva as seguintes linhas em seu ngrok. yml:</span><span class="sxs-lookup"><span data-stu-id="30a80-132">Write the following lines into your ngrok.yml:</span></span>

    ```yaml
    media:
        addr: 8445
        proto: tcp
    ```

## <a name="start-ngrok"></a><span data-ttu-id="30a80-133">Iniciar ngrok</span><span class="sxs-lookup"><span data-stu-id="30a80-133">Start ngrok</span></span>

<span data-ttu-id="30a80-134">Agora que a configuração do ngrok está pronta, inicie-a:</span><span class="sxs-lookup"><span data-stu-id="30a80-134">Now that the ngrok configuration is ready, launch it:</span></span>

  `ngrok.exe start -all -config <Path to your ngrok.yml>`

<span data-ttu-id="30a80-135">Isso inicia o ngrok e define as URLs públicas que fornecem os túneis para seu localhost.</span><span class="sxs-lookup"><span data-stu-id="30a80-135">This starts ngrok and defines the public URLs which provide the tunnels to your localhost.</span></span> <span data-ttu-id="30a80-136">A saída será semelhante ao seguinte:</span><span class="sxs-lookup"><span data-stu-id="30a80-136">The output looks like the following:</span></span>

```cmd
Forwarding  http://signal.ngrok.io -> localhost:12345
Forwarding  https://signal.ngrok.io -> localhost:12345
Forwarding  tcp://1.tcp.ngrok.io:12332 -> localhost:8445
```

<span data-ttu-id="30a80-137">Aqui `12345` está a porta de sinalização, `8445` é a porta hospedada pelo aplicativo e `12332` é a porta de mídia remota exposta pelo ngrok.</span><span class="sxs-lookup"><span data-stu-id="30a80-137">Here, `12345` is the signaling port, `8445` is the application-hosted port, and `12332` is the remote media port exposed by ngrok.</span></span> <span data-ttu-id="30a80-138">Observe que temos um encaminhamento de `1.bot.contoso.com` para. `1.tcp.ngrok.io`</span><span class="sxs-lookup"><span data-stu-id="30a80-138">Note that we have a forwarding from `1.bot.contoso.com` to `1.tcp.ngrok.io`.</span></span> <span data-ttu-id="30a80-139">Ele será usado como a URL de mídia do bot.</span><span class="sxs-lookup"><span data-stu-id="30a80-139">This will be used as the media URL for the bot.</span></span> <span data-ttu-id="30a80-140">Obviamente, esses números de porta são apenas exemplos e você pode usar qualquer porta disponível.</span><span class="sxs-lookup"><span data-stu-id="30a80-140">Of course, these port numbers are just examples and you can use any available port.</span></span>

### <a name="update-code"></a><span data-ttu-id="30a80-141">Código de atualização</span><span class="sxs-lookup"><span data-stu-id="30a80-141">Update code</span></span>

<span data-ttu-id="30a80-142">Depois que o ngrok estiver em funcionamento, atualize o código para usar o config que você acabou de configurar.</span><span class="sxs-lookup"><span data-stu-id="30a80-142">Once ngrok is up and running, update the code to use the config you just set up.</span></span>

#### <a name="update-signaling"></a><span data-ttu-id="30a80-143">Sinalização de atualização</span><span class="sxs-lookup"><span data-stu-id="30a80-143">Update signaling</span></span>

- <span data-ttu-id="30a80-144">Na chamada BotBuilder, altere o `NotificationUrl` para a URL de sinalização fornecida por ngrok.</span><span class="sxs-lookup"><span data-stu-id="30a80-144">In the BotBuilder call, change the `NotificationUrl` to the signaling URL provided by ngrok.</span></span>

```csharp
statefulClientBuilder.SetNotificationUrl(
    new Uri("https://signal.ngrok.io/notificationEndpoint"))
```

> [!NOTE]
> <span data-ttu-id="30a80-145">Substitua o sinal por um fornecido pelo ngrok e `NotificationEndpoint` com o caminho do controlador que recebe a notificação.</span><span class="sxs-lookup"><span data-stu-id="30a80-145">Replace signal with the one provided by ngrok and the `NotificationEndpoint` with the controller path that receives notification.</span></span>

> <span data-ttu-id="30a80-146">**Importante**: a URL em `SetNotificationUrl` deve ser HTTPS.</span><span class="sxs-lookup"><span data-stu-id="30a80-146">**IMPORTANT**: The URL in `SetNotificationUrl` must be HTTPS.</span></span>

> <span data-ttu-id="30a80-147">**Importante**: sua instância local deve estar ouvindo o tráfego http na porta de sinalização.</span><span class="sxs-lookup"><span data-stu-id="30a80-147">**IMPORTANT**: Your local instance must be listening to HTTP traffic on the signaling port.</span></span> <span data-ttu-id="30a80-148">As solicitações feitas pelas chamadas e a plataforma de reuniões online alcançarão o bot como tráfego HTTP de localhost, a menos que a criptografia de ponta a ponta seja configurada.</span><span class="sxs-lookup"><span data-stu-id="30a80-148">The requests made by the calls and online meetings platform will reach the bot as localhost HTTP traffic unless end-to-end encryption is set up.</span></span>

#### <a name="update-media"></a><span data-ttu-id="30a80-149">Atualizar mídia</span><span class="sxs-lookup"><span data-stu-id="30a80-149">Update media</span></span>

<span data-ttu-id="30a80-150">Atualize o `MediaPlatformSettings` para o seguinte.</span><span class="sxs-lookup"><span data-stu-id="30a80-150">Update your `MediaPlatformSettings` to the following.</span></span>

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
> <span data-ttu-id="30a80-151">A impressão digital de certificado fornecida acima deve corresponder ao FQDN de serviço.</span><span class="sxs-lookup"><span data-stu-id="30a80-151">The certificate thumbprint provided above should match the Service FQDN.</span></span> <span data-ttu-id="30a80-152">É por isso que as entradas DNS são obrigatórias.</span><span class="sxs-lookup"><span data-stu-id="30a80-152">That is why the DNS entries are required.</span></span>

## <a name="next-steps"></a><span data-ttu-id="30a80-153">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="30a80-153">Next steps</span></span>

<span data-ttu-id="30a80-154">Agora, o seu bot pode ser executado localmente e todos os fluxos funcionam de seu localhost.</span><span class="sxs-lookup"><span data-stu-id="30a80-154">Your bot can now run locally and all the flows work from your localhost.</span></span>

## <a name="caveats"></a><span data-ttu-id="30a80-155">ADVERTÊNCIAS</span><span class="sxs-lookup"><span data-stu-id="30a80-155">Caveats</span></span>

- <span data-ttu-id="30a80-156">As contas gratuitas do Ngrok **não** fornecem criptografia de ponta a ponta.</span><span class="sxs-lookup"><span data-stu-id="30a80-156">Ngrok free accounts **don't** provide end-to-end encryption.</span></span> <span data-ttu-id="30a80-157">Os dados HTTPS terminam na URL ngrok e os fluxos de dados descriptografados do `localhost`ngrok para o.</span><span class="sxs-lookup"><span data-stu-id="30a80-157">The HTTPS data ends at the ngrok URL and the data flows unencrypted from ngrok to `localhost`.</span></span> <span data-ttu-id="30a80-158">Se você precisar de criptografia de ponta a ponta, considere uma conta de ngrok paga.</span><span class="sxs-lookup"><span data-stu-id="30a80-158">If you require end-to-end encryption, consider a paid ngrok account.</span></span> <span data-ttu-id="30a80-159">Consulte [TLS túneis](https://ngrok.com/docs#tls) para etapas sobre a configuração de túneis de ponta a ponta.</span><span class="sxs-lookup"><span data-stu-id="30a80-159">See [TLS tunnels](https://ngrok.com/docs#tls) for steps on setting up secure end-to-end tunnels.</span></span>
- <span data-ttu-id="30a80-160">Como a URL de retorno de chamada do bot é dinâmica, os cenários de chamadas de entrada exigem que você atualize freqüentemente seus pontos de extremidade do ngrok.</span><span class="sxs-lookup"><span data-stu-id="30a80-160">Because the bot callback URL is dynamic, incoming call scenarios require you to frequently update your ngrok endpoints.</span></span> <span data-ttu-id="30a80-161">Uma maneira de corrigir isso é usar uma conta de ngrok paga que fornece subdomínios fixos para os quais você pode apontar seu bot e a plataforma.</span><span class="sxs-lookup"><span data-stu-id="30a80-161">One way to fix this is to use a paid ngrok account which provides fixed subdomains to which you can point your bot and the platform.</span></span>
- <span data-ttu-id="30a80-162">Os túneis Ngrok também podem ser usados com o [Azure Service Fabric](/azure/service-fabric/service-fabric-overview).</span><span class="sxs-lookup"><span data-stu-id="30a80-162">Ngrok tunnels can also be used with [Azure Service Fabric](/azure/service-fabric/service-fabric-overview).</span></span> <span data-ttu-id="30a80-163">Para obter um exemplo de como fazer isso, confira o [aplicativo de exemplo HueBot](/microsoftgraph/microsoft-graph-comms-samples/tree/master/Samples/LocalMediaSamples/HueBot/HueBot).</span><span class="sxs-lookup"><span data-stu-id="30a80-163">For an example of how to do this, see the [HueBot sample app](/microsoftgraph/microsoft-graph-comms-samples/tree/master/Samples/LocalMediaSamples/HueBot/HueBot).</span></span>
