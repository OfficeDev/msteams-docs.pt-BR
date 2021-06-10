---
title: Depurar seus chamados e o bot de reunião localmente
description: Saiba como você também pode usar o ngrok para desenvolver chamadas e bots de reunião online no computador local.
ms.topic: how-to
localization_priority: Normal
keywords: túnel ngrok de desenvolvimento local
ms.date: 11/18/2018
ms.openlocfilehash: 0f29f77e5030a7dbef9e8f7cefae4e055b7cc5b5
ms.sourcegitcommit: 825abed2f8784d2bab7407ba7a4455ae17bbd28f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2021
ms.locfileid: "52020159"
---
# <a name="develop-calling-and-online-meeting-bots-on-your-local-pc"></a><span data-ttu-id="6799d-104">Desenvolver bots de reunião online e de chamada no computador local</span><span class="sxs-lookup"><span data-stu-id="6799d-104">Develop calling and online meeting bots on your local PC</span></span>

<span data-ttu-id="6799d-105">Em [Executar e depurar seu aplicativo,](../../concepts/build-and-test/debug.md) explicamos como usar [o ngrok](https://ngrok.com) para criar um túnel entre o computador local e a Internet.</span><span class="sxs-lookup"><span data-stu-id="6799d-105">In [Run and debug your app](../../concepts/build-and-test/debug.md) we explain how to use [ngrok](https://ngrok.com) to create a tunnel between your local computer and the internet.</span></span> <span data-ttu-id="6799d-106">Neste tópico, saiba como você também pode usar o ngrok e seu computador local para desenvolver bots que suportam chamadas e reuniões online.</span><span class="sxs-lookup"><span data-stu-id="6799d-106">In this topic, learn how you can also use ngrok and your local PC to develop bots that support calls and online meetings.</span></span>

<span data-ttu-id="6799d-107">Bots de mensagens usam HTTP, mas chamadas e bots de reunião online usam o TCP de nível inferior.</span><span class="sxs-lookup"><span data-stu-id="6799d-107">Messaging bots use HTTP, but calls and online meeting bots use the lower-level TCP.</span></span> <span data-ttu-id="6799d-108">O Ngrok dá suporte a tuneis TCP, além de tuneis HTTP.</span><span class="sxs-lookup"><span data-stu-id="6799d-108">Ngrok supports TCP tunnels in addition to HTTP tunnels.</span></span> 

## <a name="configure-ngrokyml"></a><span data-ttu-id="6799d-109">Configurar ngrok.yml</span><span class="sxs-lookup"><span data-stu-id="6799d-109">Configure ngrok.yml</span></span>

<span data-ttu-id="6799d-110">Vá para [o ngrok](https://ngrok.com) e inscreva-se em uma conta gratuita ou faça logon em sua conta existente.</span><span class="sxs-lookup"><span data-stu-id="6799d-110">Go to [ngrok](https://ngrok.com) and sign up for a free account or log into your existing account.</span></span> <span data-ttu-id="6799d-111">Depois de entrar, vá para o [painel e](https://dashboard.ngrok.com) receba seu token de auth.</span><span class="sxs-lookup"><span data-stu-id="6799d-111">After you've signed in, go to the [dashboard](https://dashboard.ngrok.com) and get your auth token.</span></span>

<span data-ttu-id="6799d-112">Crie um arquivo de configuração ngrok `ngrok.yml` e adicione a seguinte linha.</span><span class="sxs-lookup"><span data-stu-id="6799d-112">Create an ngrok configuration file `ngrok.yml` and add the following line.</span></span> <span data-ttu-id="6799d-113">Para obter mais informações sobre onde o arquivo pode ser localizado, consulte [ngrok](https://ngrok.com/docs#config):</span><span class="sxs-lookup"><span data-stu-id="6799d-113">For more information on where the file can be located, see [ngrok](https://ngrok.com/docs#config):</span></span>

  `authtoken: <Your-AuthToken>`

## <a name="set-up-signaling"></a><span data-ttu-id="6799d-114">Configurar sinalização</span><span class="sxs-lookup"><span data-stu-id="6799d-114">Set up signaling</span></span>

<span data-ttu-id="6799d-115">Em [Bots de](./calls-meetings-bots-overview.md)chamadas e reuniões online, abordamos a sinalização de chamada sobre como os bots detectam e respondem a novas chamadas e eventos durante uma chamada.</span><span class="sxs-lookup"><span data-stu-id="6799d-115">In [Calls and online meetings bots](./calls-meetings-bots-overview.md), we discussed call signaling on how bots detect and respond to new calls and events during a call.</span></span> <span data-ttu-id="6799d-116">Os eventos de sinalização de chamada são enviados por HTTP POST para o ponto de extremidade de chamada do bot.</span><span class="sxs-lookup"><span data-stu-id="6799d-116">Call signaling events are sent through HTTP POST to the bot's calling endpoint.</span></span>

<span data-ttu-id="6799d-117">Assim como com a API de mensagens do bot, para que a Plataforma de Mídia em tempo real fale com seu bot, seu bot deve ser acessível pela Internet.</span><span class="sxs-lookup"><span data-stu-id="6799d-117">As with the bot's messaging API, for the Real-time Media Platform to talk to your bot, your bot must be reachable over the internet.</span></span> <span data-ttu-id="6799d-118">O Ngrok torna isso simples.</span><span class="sxs-lookup"><span data-stu-id="6799d-118">Ngrok makes this simple.</span></span> <span data-ttu-id="6799d-119">Adicione as seguintes linhas ao ngrok.yml:</span><span class="sxs-lookup"><span data-stu-id="6799d-119">Add the following lines to your ngrok.yml:</span></span>

```yaml
tunnels:
    signaling:
        addr: 12345
        proto: http
```

## <a name="set-up-local-media"></a><span data-ttu-id="6799d-120">Configurar mídia local</span><span class="sxs-lookup"><span data-stu-id="6799d-120">Set up local media</span></span>

> [!NOTE]
> <span data-ttu-id="6799d-121">Esta seção só é necessária para bots de mídia hospedados pelo aplicativo e pode ser ignorada se você não hospedar mídia por conta própria.</span><span class="sxs-lookup"><span data-stu-id="6799d-121">This section is only required for application-hosted media bots and can be skipped if you don't host media yourself.</span></span>

<span data-ttu-id="6799d-122">A mídia hospedada por aplicativo usa certificados e tuneis TCP.</span><span class="sxs-lookup"><span data-stu-id="6799d-122">Application-hosted media uses certificates and TCP tunnels.</span></span> <span data-ttu-id="6799d-123">As etapas a seguir são necessárias:</span><span class="sxs-lookup"><span data-stu-id="6799d-123">The following steps are required:</span></span>

1. <span data-ttu-id="6799d-124">Os pontos de extremidade TCP públicos do Ngrok têm URLs fixas.</span><span class="sxs-lookup"><span data-stu-id="6799d-124">Ngrok's public TCP endpoints have fixed URLs.</span></span> <span data-ttu-id="6799d-125">Eles são `0.tcp.ngrok.io` , e assim por `1.tcp.ngrok.io` diante.</span><span class="sxs-lookup"><span data-stu-id="6799d-125">They are `0.tcp.ngrok.io`, `1.tcp.ngrok.io`, and so on.</span></span> <span data-ttu-id="6799d-126">Você deve ter uma entrada CNAME DNS para seu serviço que aponta para essas URLs.</span><span class="sxs-lookup"><span data-stu-id="6799d-126">You must have a DNS CNAME entry for your service that points to these URLs.</span></span> <span data-ttu-id="6799d-127">Por exemplo, digamos que se refere `0.bot.contoso.com` `0.tcp.ngrok.io` a , `1.bot.contoso.com` refere-se `1.tcp.ngrok.io` a e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="6799d-127">For example, let's say `0.bot.contoso.com` refers to `0.tcp.ngrok.io`, `1.bot.contoso.com` refers to `1.tcp.ngrok.io`, and so on.</span></span>
2. <span data-ttu-id="6799d-128">Um certificado SSL é necessário para suas URLs.</span><span class="sxs-lookup"><span data-stu-id="6799d-128">An SSL certificate is required for your URLs.</span></span> <span data-ttu-id="6799d-129">Para facilitar, use um certificado SSL emitido para um domínio de curinga.</span><span class="sxs-lookup"><span data-stu-id="6799d-129">To make it easy, use an SSL certificate issued to a wild card domain.</span></span> <span data-ttu-id="6799d-130">Nesse caso, seria `*.bot.contoso.com` .</span><span class="sxs-lookup"><span data-stu-id="6799d-130">In this case, it would be `*.bot.contoso.com`.</span></span> <span data-ttu-id="6799d-131">Esse certificado SSL é validado pelo SDK de mídia, portanto, deve corresponder à URL pública do bot.</span><span class="sxs-lookup"><span data-stu-id="6799d-131">This SSL certificate is validated by the media SDK, so it must match your bot's public URL.</span></span> <span data-ttu-id="6799d-132">Anote a impressão digital e instale-a nos certificados do computador.</span><span class="sxs-lookup"><span data-stu-id="6799d-132">Note the thumbprint and install it in your machine certificates.</span></span>
3. <span data-ttu-id="6799d-133">Agora, configurar um túnel TCP para encaminhar o tráfego para o localhost.</span><span class="sxs-lookup"><span data-stu-id="6799d-133">Now, set up a TCP tunnel to forward the traffic to localhost.</span></span> <span data-ttu-id="6799d-134">Escreva as seguintes linhas em seu ngrok.yml:</span><span class="sxs-lookup"><span data-stu-id="6799d-134">Write the following lines into your ngrok.yml:</span></span>

    ```yaml
    media:
        addr: 8445
        proto: tcp
    ```

## <a name="start-ngrok"></a><span data-ttu-id="6799d-135">Iniciar ngrok</span><span class="sxs-lookup"><span data-stu-id="6799d-135">Start ngrok</span></span>

<span data-ttu-id="6799d-136">Agora que a configuração do ngrok está pronta, inicia-a:</span><span class="sxs-lookup"><span data-stu-id="6799d-136">Now that the ngrok configuration is ready, launch it:</span></span>

  `ngrok.exe start -all -config <Path to your ngrok.yml>`

<span data-ttu-id="6799d-137">Isso inicia ngrok e define as URLs públicas que fornecem os tuneis ao seu localhost.</span><span class="sxs-lookup"><span data-stu-id="6799d-137">This starts ngrok and defines the public URLs which provide the tunnels to your localhost.</span></span> <span data-ttu-id="6799d-138">A seguir está um exemplo da saída:</span><span class="sxs-lookup"><span data-stu-id="6799d-138">Following is an example of the output:</span></span>

```cmd
Forwarding  http://signal.ngrok.io -> localhost:12345
Forwarding  https://signal.ngrok.io -> localhost:12345
Forwarding  tcp://1.tcp.ngrok.io:12332 -> localhost:8445
```

<span data-ttu-id="6799d-139">Aqui está a porta de sinalização, é a porta hospedada pelo aplicativo e é a porta de mídia remota `12345` `8445` exposta pelo `12332` ngrok.</span><span class="sxs-lookup"><span data-stu-id="6799d-139">Here, `12345` is the signaling port, `8445` is the application-hosted port, and `12332` is the remote media port exposed by ngrok.</span></span> <span data-ttu-id="6799d-140">Observe que temos um encaminhamento de `1.bot.contoso.com` para `1.tcp.ngrok.io` .</span><span class="sxs-lookup"><span data-stu-id="6799d-140">Note that we have a forwarding from `1.bot.contoso.com` to `1.tcp.ngrok.io`.</span></span> <span data-ttu-id="6799d-141">Isso será usado como a URL de mídia do bot.</span><span class="sxs-lookup"><span data-stu-id="6799d-141">This will be used as the media URL for the bot.</span></span> <span data-ttu-id="6799d-142">Obviamente, esses números de porta são apenas exemplos e você pode usar qualquer porta disponível.</span><span class="sxs-lookup"><span data-stu-id="6799d-142">Of course, these port numbers are just examples and you can use any available port.</span></span>

### <a name="update-code"></a><span data-ttu-id="6799d-143">Código de atualização</span><span class="sxs-lookup"><span data-stu-id="6799d-143">Update code</span></span>

<span data-ttu-id="6799d-144">Depois que o ngrok está em execução, atualize o código para usar a configuração que você acabou de configurar.</span><span class="sxs-lookup"><span data-stu-id="6799d-144">After ngrok is up and running, update the code to use the config you just set up.</span></span>

#### <a name="update-signaling"></a><span data-ttu-id="6799d-145">Atualizar sinalização</span><span class="sxs-lookup"><span data-stu-id="6799d-145">Update signaling</span></span>

<span data-ttu-id="6799d-146">Na chamada BotBuilder, altere a `NotificationUrl` URL de sinalização fornecida pelo ngrok.</span><span class="sxs-lookup"><span data-stu-id="6799d-146">In the BotBuilder call, change the `NotificationUrl` to the signaling URL provided by ngrok.</span></span>

```csharp
statefulClientBuilder.SetNotificationUrl(
    new Uri("https://signal.ngrok.io/notificationEndpoint"))
```

> [!NOTE]
> <span data-ttu-id="6799d-147">Substitua o sinal pelo fornecido pelo ngrok e pelo caminho `NotificationEndpoint` do controlador que recebe a notificação.</span><span class="sxs-lookup"><span data-stu-id="6799d-147">Replace signal with the one provided by ngrok and the `NotificationEndpoint` with the controller path that receives notification.</span></span>

> [!IMPORTANT]
> * <span data-ttu-id="6799d-148">A URL em `SetNotificationUrl` deve ser HTTPS.</span><span class="sxs-lookup"><span data-stu-id="6799d-148">The URL in `SetNotificationUrl` must be HTTPS.</span></span>
> 
> <span data-ttu-id="6799d-149">Sua instância local deve estar escutando o tráfego HTTP na porta de sinalização.</span><span class="sxs-lookup"><span data-stu-id="6799d-149">Your local instance must be listening to HTTP traffic on the signaling port.</span></span> <span data-ttu-id="6799d-150">As solicitações feitas pela plataforma de chamadas e reuniões online chegarão ao bot como tráfego HTTP do localhost, a menos que a criptografia de ponta a ponta esteja configurada.</span><span class="sxs-lookup"><span data-stu-id="6799d-150">The requests made by the calls and online meetings platform will reach the bot as localhost HTTP traffic unless end-to-end encryption is set up.</span></span>

#### <a name="update-media"></a><span data-ttu-id="6799d-151">Atualizar mídia</span><span class="sxs-lookup"><span data-stu-id="6799d-151">Update media</span></span>

<span data-ttu-id="6799d-152">Atualize `MediaPlatformSettings` o seguinte:</span><span class="sxs-lookup"><span data-stu-id="6799d-152">Update your `MediaPlatformSettings` as following:</span></span>

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
> <span data-ttu-id="6799d-153">A impressão digital do certificado fornecida no `MediaPlatformSettings` deve corresponder ao FQDN do Serviço.</span><span class="sxs-lookup"><span data-stu-id="6799d-153">The certificate thumbprint provided in the `MediaPlatformSettings` must match the Service FQDN.</span></span> <span data-ttu-id="6799d-154">É por isso que as entradas DNS são necessárias.</span><span class="sxs-lookup"><span data-stu-id="6799d-154">That is why the DNS entries are required.</span></span>

## <a name="caveats"></a><span data-ttu-id="6799d-155">Advertências</span><span class="sxs-lookup"><span data-stu-id="6799d-155">Caveats</span></span>

- <span data-ttu-id="6799d-156">As contas gratuitas de Ngrok **não fornecem** criptografia de ponta a ponta.</span><span class="sxs-lookup"><span data-stu-id="6799d-156">Ngrok free accounts **don't** provide end-to-end encryption.</span></span> <span data-ttu-id="6799d-157">Os dados HTTPS terminam na URL ngrok e os fluxos de dados não criptografados de ngrok para `localhost` .</span><span class="sxs-lookup"><span data-stu-id="6799d-157">The HTTPS data ends at the ngrok URL and the data flows unencrypted from ngrok to `localhost`.</span></span> <span data-ttu-id="6799d-158">Se você exigir criptografia de ponta a ponta, considere uma conta ngrok paga.</span><span class="sxs-lookup"><span data-stu-id="6799d-158">If you require end-to-end encryption, consider a paid ngrok account.</span></span> <span data-ttu-id="6799d-159">Consulte [TLS tunnels](https://ngrok.com/docs#tls) for steps on setting up secure end-to-end tunnels.</span><span class="sxs-lookup"><span data-stu-id="6799d-159">See [TLS tunnels](https://ngrok.com/docs#tls) for steps on setting up secure end-to-end tunnels.</span></span>
- <span data-ttu-id="6799d-160">Como a URL de retorno de chamada de bot é dinâmica, os cenários de chamada de entrada exigem que você atualize com frequência seus pontos de extremidade ngrok.</span><span class="sxs-lookup"><span data-stu-id="6799d-160">Because the bot callback URL is dynamic, incoming call scenarios require you to frequently update your ngrok endpoints.</span></span> <span data-ttu-id="6799d-161">Uma maneira de corrigir isso é usar uma conta ngrok paga que fornece subdomas fixos para os quais você pode apontar seu bot e a plataforma.</span><span class="sxs-lookup"><span data-stu-id="6799d-161">One way to fix this is to use a paid ngrok account which provides fixed subdomains to which you can point your bot and the platform.</span></span>
- <span data-ttu-id="6799d-162">Os tuneis Ngrok também podem ser usados com [o Azure Service Fabric](/azure/service-fabric/service-fabric-overview).</span><span class="sxs-lookup"><span data-stu-id="6799d-162">Ngrok tunnels can also be used with [Azure Service Fabric](/azure/service-fabric/service-fabric-overview).</span></span> <span data-ttu-id="6799d-163">Para ver um exemplo de como fazer isso, consulte o aplicativo de exemplo [HueBot.](/microsoftgraph/microsoft-graph-comms-samples/tree/master/Samples/LocalMediaSamples/HueBot/HueBot)</span><span class="sxs-lookup"><span data-stu-id="6799d-163">For an example of how to do this, see the [HueBot sample app](/microsoftgraph/microsoft-graph-comms-samples/tree/master/Samples/LocalMediaSamples/HueBot/HueBot).</span></span>
