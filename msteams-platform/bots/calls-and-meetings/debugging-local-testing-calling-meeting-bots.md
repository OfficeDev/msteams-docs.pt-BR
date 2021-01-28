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
# <a name="how-to-develop-calling-and-online-meeting-bots-on-your-local-pc"></a><span data-ttu-id="376f9-104">Como desenvolver bots de chamada e reuniões online em seu computador local</span><span class="sxs-lookup"><span data-stu-id="376f9-104">How to develop calling and online meeting bots on your local PC</span></span>

<span data-ttu-id="376f9-105">Em [Executar e depurar seu aplicativo,](../../concepts/build-and-test/debug.md) explicamos como usar [o ngrok](https://ngrok.com) para criar um túnel entre o computador local e a Internet.</span><span class="sxs-lookup"><span data-stu-id="376f9-105">In [Run and debug your app](../../concepts/build-and-test/debug.md) we explain how to use [ngrok](https://ngrok.com) to create a tunnel between your local computer and the internet.</span></span> <span data-ttu-id="376f9-106">Neste tópico, saiba como você também pode usar o ngrok e seu computador local para desenvolver bots que suportam chamadas e reuniões online.</span><span class="sxs-lookup"><span data-stu-id="376f9-106">In this topic, learn how you can also use ngrok and your local PC to develop bots that support calls and online meetings.</span></span>

<span data-ttu-id="376f9-107">Os bots de mensagens usam HTTP, mas as chamadas e os bots de reunião online usam o TCP de nível inferior.</span><span class="sxs-lookup"><span data-stu-id="376f9-107">Messaging bots use HTTP, but calls and online meeting bots use the lower-level TCP.</span></span> <span data-ttu-id="376f9-108">O Ngrok dá suporte a túnel TCP, além de túnel HTTP; você aprenderá a seguir.</span><span class="sxs-lookup"><span data-stu-id="376f9-108">Ngrok supports TCP tunnels in addition to HTTP tunnels; you'll learn how, below.</span></span>

## <a name="configuring-ngrokyml"></a><span data-ttu-id="376f9-109">Configurando ngrok.yml</span><span class="sxs-lookup"><span data-stu-id="376f9-109">Configuring ngrok.yml</span></span>

<span data-ttu-id="376f9-110">Vá para [o ngrok](https://ngrok.com) e inscreva-se para uma conta gratuita ou faça logon em sua conta existente.</span><span class="sxs-lookup"><span data-stu-id="376f9-110">Go to [ngrok](https://ngrok.com) and sign up for a free account or log into your existing account.</span></span> <span data-ttu-id="376f9-111">Depois de fazer logon, vá para o [painel](https://dashboard.ngrok.com) e receba seu authtoken.</span><span class="sxs-lookup"><span data-stu-id="376f9-111">Once you've logged in, go to the [dashboard](https://dashboard.ngrok.com) and get your authtoken.</span></span>

<span data-ttu-id="376f9-112">Crie um arquivo de configuração ngrok (veja aqui para obter mais informações sobre onde esse arquivo pode ser `ngrok.yml` localizado) e adicione esta linha: [](https://ngrok.com/docs#config)</span><span class="sxs-lookup"><span data-stu-id="376f9-112">Create an ngrok configuration file `ngrok.yml` (see [here](https://ngrok.com/docs#config) for more information on where this file can be located) and add this line:</span></span>

  `authtoken: <Your-AuthToken>`

## <a name="setting-up-signaling"></a><span data-ttu-id="376f9-113">Configurando a sinalização</span><span class="sxs-lookup"><span data-stu-id="376f9-113">Setting up signaling</span></span>

<span data-ttu-id="376f9-114">Em [bots de](./calls-meetings-bots-overview.md)chamadas e reuniões online, discutimos a sinalização de chamada — como os bots detectam e respondem a novas chamadas e eventos durante uma chamada.</span><span class="sxs-lookup"><span data-stu-id="376f9-114">In [Calls and online meetings bots](./calls-meetings-bots-overview.md), we discussed call signaling — how bots detect and respond to new calls and events during a call.</span></span> <span data-ttu-id="376f9-115">Eventos de sinalização de chamada são enviados via HTTP POST para o ponto de extremidade de chamada do bot.</span><span class="sxs-lookup"><span data-stu-id="376f9-115">Call signaling events are sent via HTTP POST to the bot's calling endpoint.</span></span>

<span data-ttu-id="376f9-116">Assim como na API de mensagens do bot, para que a Plataforma de Mídia em Tempo Real converse com seu bot, seu bot deve estar acessível pela Internet.</span><span class="sxs-lookup"><span data-stu-id="376f9-116">As with the bot's messaging API, in order for the Real-time Media Platform to talk to your bot, your bot must be reachable over the internet.</span></span> <span data-ttu-id="376f9-117">O Ngrok torna isso simples: adicione as seguintes linhas ao ngrok.yml:</span><span class="sxs-lookup"><span data-stu-id="376f9-117">Ngrok makes this simple — add the following lines to your ngrok.yml:</span></span>

```yaml
tunnels:
    signaling:
        addr: 12345
        proto: http
```

## <a name="setting-up-local-media"></a><span data-ttu-id="376f9-118">Configurando a mídia local</span><span class="sxs-lookup"><span data-stu-id="376f9-118">Setting up local media</span></span>

> [!NOTE]
> <span data-ttu-id="376f9-119">Esta seção só é necessária para bots de mídia hospedados pelo aplicativo e pode ser ignorada se você não hospedar mídia por conta própria.</span><span class="sxs-lookup"><span data-stu-id="376f9-119">This section is only required for application-hosted media bots and can be skipped if you don't host media yourself.</span></span>

<span data-ttu-id="376f9-120">A mídia hospedada pelo aplicativo usa certificados e túnel TCP.</span><span class="sxs-lookup"><span data-stu-id="376f9-120">Application-hosted media uses certificates and TCP tunnels.</span></span> <span data-ttu-id="376f9-121">As etapas a seguir são necessárias:</span><span class="sxs-lookup"><span data-stu-id="376f9-121">The following steps are required:</span></span>

- <span data-ttu-id="376f9-122">Os pontos de extremidade TCP públicos do Ngrok têm URLs fixas.</span><span class="sxs-lookup"><span data-stu-id="376f9-122">Ngrok's public TCP endpoints have fixed URLs.</span></span> <span data-ttu-id="376f9-123">Eles são `0.tcp.ngrok.io` , e assim por `1.tcp.ngrok.io` diante.</span><span class="sxs-lookup"><span data-stu-id="376f9-123">They are `0.tcp.ngrok.io`, `1.tcp.ngrok.io`, and so on.</span></span> <span data-ttu-id="376f9-124">Você deve ter uma entrada CNAME DNS para seu serviço que aponta para essas URLs.</span><span class="sxs-lookup"><span data-stu-id="376f9-124">You should have a DNS CNAME entry for your service that points to these URLs.</span></span> <span data-ttu-id="376f9-125">Neste exemplo, digamos que `0.bot.contoso.com` se refere a , `0.tcp.ngrok.io` `1.bot.contoso.com` refere-se `1.tcp.ngrok.io` a e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="376f9-125">In this example, let's say `0.bot.contoso.com` refers to `0.tcp.ngrok.io`, `1.bot.contoso.com` refers to `1.tcp.ngrok.io`, and so on.</span></span>
- <span data-ttu-id="376f9-126">Um certificado SSL é necessário para suas URLs.</span><span class="sxs-lookup"><span data-stu-id="376f9-126">A SSL certificate is required for your URLs.</span></span> <span data-ttu-id="376f9-127">Para facilitar, use um certificado SSL emitido para um domínio curinga.</span><span class="sxs-lookup"><span data-stu-id="376f9-127">To make it easy, use a SSL certificate issued to a wild card domain.</span></span> <span data-ttu-id="376f9-128">Nesse caso, `*.bot.contoso.com` seria.</span><span class="sxs-lookup"><span data-stu-id="376f9-128">In this case, it would be `*.bot.contoso.com`.</span></span> <span data-ttu-id="376f9-129">Esse certificado SSL é validado pelo SDK de mídia, portanto, ele deve corresponder à URL pública do seu bot.</span><span class="sxs-lookup"><span data-stu-id="376f9-129">This SSL certificate is validated by the media SDK, so it should match your bot's public URL.</span></span> <span data-ttu-id="376f9-130">Anote a impressão digital e instale-a nos certificados do computador.</span><span class="sxs-lookup"><span data-stu-id="376f9-130">Note the thumbprint and install it in your machine certificates.</span></span>
- <span data-ttu-id="376f9-131">Agora, configure um túnel TCP para encaminhar o tráfego para o localhost.</span><span class="sxs-lookup"><span data-stu-id="376f9-131">Now, setup a TCP tunnel to forward the traffic to localhost.</span></span> <span data-ttu-id="376f9-132">Escreva as seguintes linhas em seu ngrok.yml:</span><span class="sxs-lookup"><span data-stu-id="376f9-132">Write the following lines into your ngrok.yml:</span></span>

    ```yaml
    media:
        addr: 8445
        proto: tcp
    ```

## <a name="start-ngrok"></a><span data-ttu-id="376f9-133">Iniciar ngrok</span><span class="sxs-lookup"><span data-stu-id="376f9-133">Start ngrok</span></span>

<span data-ttu-id="376f9-134">Agora que a configuração do ngrok está pronta, inicia-a:</span><span class="sxs-lookup"><span data-stu-id="376f9-134">Now that the ngrok configuration is ready, launch it:</span></span>

  `ngrok.exe start -all -config <Path to your ngrok.yml>`

<span data-ttu-id="376f9-135">Isso inicia o ngrok e define as URLs públicas que fornecem os túnel para o seu localhost.</span><span class="sxs-lookup"><span data-stu-id="376f9-135">This starts ngrok and defines the public URLs which provide the tunnels to your localhost.</span></span> <span data-ttu-id="376f9-136">A saída tem a seguinte aparência:</span><span class="sxs-lookup"><span data-stu-id="376f9-136">The output looks like the following:</span></span>

```cmd
Forwarding  http://signal.ngrok.io -> localhost:12345
Forwarding  https://signal.ngrok.io -> localhost:12345
Forwarding  tcp://1.tcp.ngrok.io:12332 -> localhost:8445
```

<span data-ttu-id="376f9-137">Aqui está a porta de sinalização, a porta hospedada pelo aplicativo e a porta de mídia remota `12345` `8445` exposta pelo `12332` ngrok.</span><span class="sxs-lookup"><span data-stu-id="376f9-137">Here, `12345` is the signaling port, `8445` is the application-hosted port, and `12332` is the remote media port exposed by ngrok.</span></span> <span data-ttu-id="376f9-138">Observe que temos um encaminhamento de `1.bot.contoso.com` para `1.tcp.ngrok.io` .</span><span class="sxs-lookup"><span data-stu-id="376f9-138">Note that we have a forwarding from `1.bot.contoso.com` to `1.tcp.ngrok.io`.</span></span> <span data-ttu-id="376f9-139">Isso será usado como a URL de mídia para o bot.</span><span class="sxs-lookup"><span data-stu-id="376f9-139">This will be used as the media URL for the bot.</span></span> <span data-ttu-id="376f9-140">É claro que esses números de porta são apenas exemplos e você pode usar qualquer porta disponível.</span><span class="sxs-lookup"><span data-stu-id="376f9-140">Of course, these port numbers are just examples and you can use any available port.</span></span>

### <a name="update-code"></a><span data-ttu-id="376f9-141">Código de atualização</span><span class="sxs-lookup"><span data-stu-id="376f9-141">Update code</span></span>

<span data-ttu-id="376f9-142">Depois que o ngrok for executado, atualize o código para usar a configuração que você acabou de configurar.</span><span class="sxs-lookup"><span data-stu-id="376f9-142">Once ngrok is up and running, update the code to use the config you just set up.</span></span>

#### <a name="update-signaling"></a><span data-ttu-id="376f9-143">Atualizar a sinalização</span><span class="sxs-lookup"><span data-stu-id="376f9-143">Update signaling</span></span>

- <span data-ttu-id="376f9-144">Na chamada BotBuilder, altere a `NotificationUrl` URL de sinalização fornecida pelo ngrok.</span><span class="sxs-lookup"><span data-stu-id="376f9-144">In the BotBuilder call, change the `NotificationUrl` to the signaling URL provided by ngrok.</span></span>

```csharp
statefulClientBuilder.SetNotificationUrl(
    new Uri("https://signal.ngrok.io/notificationEndpoint"))
```

> [!NOTE]
> <span data-ttu-id="376f9-145">Substitua o sinal pelo fornecido pelo ngrok e pelo caminho `NotificationEndpoint` do controlador que recebe a notificação.</span><span class="sxs-lookup"><span data-stu-id="376f9-145">Replace signal with the one provided by ngrok and the `NotificationEndpoint` with the controller path that receives notification.</span></span>

> <span data-ttu-id="376f9-146">**IMPORTANTE:** a URL deve `SetNotificationUrl` ser HTTPS.</span><span class="sxs-lookup"><span data-stu-id="376f9-146">**IMPORTANT**: The URL in `SetNotificationUrl` must be HTTPS.</span></span>

> <span data-ttu-id="376f9-147">**IMPORTANTE:** sua instância local deve estar escutando o tráfego HTTP na porta de sinalização.</span><span class="sxs-lookup"><span data-stu-id="376f9-147">**IMPORTANT**: Your local instance must be listening to HTTP traffic on the signaling port.</span></span> <span data-ttu-id="376f9-148">As solicitações feitas pelas chamadas e pela plataforma de reuniões online chegarão ao bot como tráfego HTTP do localhost, a menos que a criptografia de ponta a ponta esteja configurada.</span><span class="sxs-lookup"><span data-stu-id="376f9-148">The requests made by the calls and online meetings platform will reach the bot as localhost HTTP traffic unless end-to-end encryption is set up.</span></span>

#### <a name="update-media"></a><span data-ttu-id="376f9-149">Atualizar mídia</span><span class="sxs-lookup"><span data-stu-id="376f9-149">Update media</span></span>

<span data-ttu-id="376f9-150">Atualize `MediaPlatformSettings` o seu para o seguinte.</span><span class="sxs-lookup"><span data-stu-id="376f9-150">Update your `MediaPlatformSettings` to the following.</span></span>

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
> <span data-ttu-id="376f9-151">A impressão digital do certificado fornecida acima deve corresponder ao FQDN do Serviço.</span><span class="sxs-lookup"><span data-stu-id="376f9-151">The certificate thumbprint provided above should match the Service FQDN.</span></span> <span data-ttu-id="376f9-152">É por isso que as entradas DNS são necessárias.</span><span class="sxs-lookup"><span data-stu-id="376f9-152">That is why the DNS entries are required.</span></span>

## <a name="next-steps"></a><span data-ttu-id="376f9-153">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="376f9-153">Next steps</span></span>

<span data-ttu-id="376f9-154">Seu bot agora pode ser executado localmente e todos os fluxos funcionam a partir do seu localhost.</span><span class="sxs-lookup"><span data-stu-id="376f9-154">Your bot can now run locally and all the flows work from your localhost.</span></span>

## <a name="caveats"></a><span data-ttu-id="376f9-155">Advertências</span><span class="sxs-lookup"><span data-stu-id="376f9-155">Caveats</span></span>

- <span data-ttu-id="376f9-156">As contas gratuitas do Ngrok **não fornecem** criptografia de ponta a ponta.</span><span class="sxs-lookup"><span data-stu-id="376f9-156">Ngrok free accounts **don't** provide end-to-end encryption.</span></span> <span data-ttu-id="376f9-157">Os dados HTTPS terminam na URL ngrok e os fluxos de dados não criptografados de ngrok para `localhost` .</span><span class="sxs-lookup"><span data-stu-id="376f9-157">The HTTPS data ends at the ngrok URL and the data flows unencrypted from ngrok to `localhost`.</span></span> <span data-ttu-id="376f9-158">Se você precisar de criptografia de ponta a ponta, considere uma conta ngrok paga.</span><span class="sxs-lookup"><span data-stu-id="376f9-158">If you require end-to-end encryption, consider a paid ngrok account.</span></span> <span data-ttu-id="376f9-159">Consulte [os túnel TLS](https://ngrok.com/docs#tls) para obter etapas sobre como configurar túnel seguros de ponta a ponta.</span><span class="sxs-lookup"><span data-stu-id="376f9-159">See [TLS tunnels](https://ngrok.com/docs#tls) for steps on setting up secure end-to-end tunnels.</span></span>
- <span data-ttu-id="376f9-160">Como a URL de retorno de chamada de bot é dinâmica, os cenários de chamada de entrada exigem que você atualize frequentemente seus pontos de extremidade ngrok.</span><span class="sxs-lookup"><span data-stu-id="376f9-160">Because the bot callback URL is dynamic, incoming call scenarios require you to frequently update your ngrok endpoints.</span></span> <span data-ttu-id="376f9-161">Uma maneira de corrigir isso é usar uma conta ngrok paga que fornece subdomains fixos para os quais você pode apontar seu bot e a plataforma.</span><span class="sxs-lookup"><span data-stu-id="376f9-161">One way to fix this is to use a paid ngrok account which provides fixed subdomains to which you can point your bot and the platform.</span></span>
- <span data-ttu-id="376f9-162">Os túnel Ngrok também podem ser usados com o [Azure Service Fabric.](/azure/service-fabric/service-fabric-overview)</span><span class="sxs-lookup"><span data-stu-id="376f9-162">Ngrok tunnels can also be used with [Azure Service Fabric](/azure/service-fabric/service-fabric-overview).</span></span> <span data-ttu-id="376f9-163">Para um exemplo de como fazer isso, consulte o aplicativo de exemplo [HueBot.](/microsoftgraph/microsoft-graph-comms-samples/tree/master/Samples/LocalMediaSamples/HueBot/HueBot)</span><span class="sxs-lookup"><span data-stu-id="376f9-163">For an example of how to do this, see the [HueBot sample app](/microsoftgraph/microsoft-graph-comms-samples/tree/master/Samples/LocalMediaSamples/HueBot/HueBot).</span></span>
