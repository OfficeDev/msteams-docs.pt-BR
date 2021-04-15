---
title: Criar uma extensão de mensagem usando o App Studio
author: clearab
description: Saiba como criar uma extensão de mensagens do Microsoft Teams usando o App Studio.
ms.topic: conceptual
ms.author: anclear
ms.openlocfilehash: 25086d959004046e8227de46b31d840c0b3fd228
ms.sourcegitcommit: 79e6bccfb513d4c16a58ffc03521edcf134fa518
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/13/2021
ms.locfileid: "51697218"
---
# <a name="create-a-messaging-extension-using-app-studio"></a><span data-ttu-id="b5944-103">Criar uma extensão de mensagem usando o App Studio</span><span class="sxs-lookup"><span data-stu-id="b5944-103">Create a messaging extension using App Studio</span></span>

> [!TIP]
> <span data-ttu-id="b5944-104">Procurando uma maneira mais rápida de começar?</span><span class="sxs-lookup"><span data-stu-id="b5944-104">Looking for a faster way to get started?</span></span> <span data-ttu-id="b5944-105">Crie uma [extensão de mensagens](../build-your-first-app/build-messaging-extension.md) usando o microsoft Teams Toolkit.</span><span class="sxs-lookup"><span data-stu-id="b5944-105">Create a [messaging extension](../build-your-first-app/build-messaging-extension.md) using the Microsoft Teams Toolkit.</span></span>

<span data-ttu-id="b5944-106">Em um nível alto, você precisará concluir as etapas a seguir para criar uma extensão de mensagens.</span><span class="sxs-lookup"><span data-stu-id="b5944-106">At a high level, you'll need to complete the following steps to create a messaging extension.</span></span>

1. <span data-ttu-id="b5944-107">Preparar seu ambiente de desenvolvimento</span><span class="sxs-lookup"><span data-stu-id="b5944-107">Prepare your development environment</span></span>
2. <span data-ttu-id="b5944-108">Crie e implante seu serviço Web (ao desenvolver use um serviço de tunelamento como ngrok para ser executado localmente)</span><span class="sxs-lookup"><span data-stu-id="b5944-108">Create and deploy your web service (while developing use a tunneling service like ngrok to run it locally)</span></span>
3. <span data-ttu-id="b5944-109">Registrar seu serviço Web com a estrutura bot</span><span class="sxs-lookup"><span data-stu-id="b5944-109">Register your web service with the Bot Framework</span></span>
4. <span data-ttu-id="b5944-110">Criar seu pacote de aplicativos</span><span class="sxs-lookup"><span data-stu-id="b5944-110">Create your app package</span></span>
5. <span data-ttu-id="b5944-111">Carregar um pacote do aplicativo para o Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="b5944-111">Upload your package to Microsoft Teams</span></span>

<span data-ttu-id="b5944-112">Criar seu serviço Web, criar seu pacote de aplicativos e registrar seu serviço Web com a Estrutura de Bot pode ser feito em qualquer ordem.</span><span class="sxs-lookup"><span data-stu-id="b5944-112">Creating your web service, creating your app package, and registering your web service with the Bot Framework can be done in any order.</span></span> <span data-ttu-id="b5944-113">Como essas três partes estão tão entrelaçadas, não importa qual ordem você as faça, você precisará retornar para atualizar as outras.</span><span class="sxs-lookup"><span data-stu-id="b5944-113">Because those three pieces are so intertwined, no matter which order you do them in you'll need return to update the others.</span></span> <span data-ttu-id="b5944-114">Seu registro precisa do ponto de extremidade de mensagens do seu serviço Web implantado, e seu serviço Web precisa da ID e da senha criadas a partir do seu registro.</span><span class="sxs-lookup"><span data-stu-id="b5944-114">Your registration needs the messaging endpoint from your deployed web service, and your web service needs the Id and password created from your registration.</span></span> <span data-ttu-id="b5944-115">O manifesto do aplicativo também precisa dessa ID para conectar o Teams ao seu serviço Web.</span><span class="sxs-lookup"><span data-stu-id="b5944-115">Your app manifest also needs that Id to connect Teams to your web service.</span></span>

<span data-ttu-id="b5944-116">À medida que você estiver criando sua extensão de mensagens, você estará se movendo regularmente entre alterar o manifesto do aplicativo e implantar código no seu serviço Web.</span><span class="sxs-lookup"><span data-stu-id="b5944-116">As you're building your messaging extension, you'll regularly be moving between changing your app manifest, and deploying code to your web service.</span></span> <span data-ttu-id="b5944-117">Ao trabalhar com o manifesto do aplicativo, lembre-se de que você pode manipular manualmente o arquivo JSON ou fazer alterações por meio do App Studio.</span><span class="sxs-lookup"><span data-stu-id="b5944-117">When working with the app manifest, keep in mind that you can either manually manipulate the JSON file, or make changes through App Studio.</span></span> <span data-ttu-id="b5944-118">De qualquer forma, você precisará implantar (carregar) seu aplicativo no Teams quando fizer uma alteração no manifesto, mas não é necessário fazer isso ao implantar alterações no seu serviço Web.</span><span class="sxs-lookup"><span data-stu-id="b5944-118">Either way, you'll need to re-deploy (upload) your app in Teams when you make a change to the manifest, but there's no need to do so when you deploy changes to your web service.</span></span>

[!include[prepare environment](~/includes/prepare-environment.md)]

## <a name="create-your-web-service"></a><span data-ttu-id="b5944-119">Criar seu serviço Web</span><span class="sxs-lookup"><span data-stu-id="b5944-119">Create your web service</span></span>

<span data-ttu-id="b5944-120">O centro de sua extensão de mensagens é seu serviço Web.</span><span class="sxs-lookup"><span data-stu-id="b5944-120">The heart of your messaging extension is your web service.</span></span> <span data-ttu-id="b5944-121">Ele definirá uma única rota, normalmente `/api/messages` , para receber todas as solicitações.</span><span class="sxs-lookup"><span data-stu-id="b5944-121">It will define a single route, typically `/api/messages`, to receive all requests on.</span></span> <span data-ttu-id="b5944-122">Se você estiver começando do zero, você tem algumas opções para escolher.</span><span class="sxs-lookup"><span data-stu-id="b5944-122">If you're getting started from scratch, you have a few options to choose from.</span></span>

* <span data-ttu-id="b5944-123">Use um dos nossos [tutoriais de](#learn-more) início rápido que o guiarão pela criação do seu serviço Web.</span><span class="sxs-lookup"><span data-stu-id="b5944-123">Use one of our [quickstarts](#learn-more) tutorials that will guide you through the creation of your web service.</span></span>
* <span data-ttu-id="b5944-124">Escolha um dos exemplos de extensão de mensagens disponíveis no repositório de exemplo da Estrutura de [Bots](https://github.com/Microsoft/BotBuilder-Samples) para começar.</span><span class="sxs-lookup"><span data-stu-id="b5944-124">Choose one of the messaging extension samples available in the [Bot Framework sample repository](https://github.com/Microsoft/BotBuilder-Samples) to start from.</span></span>
* <span data-ttu-id="b5944-125">Se você estiver usando JavaScript, use o gerador [Yeoman](https://github.com/OfficeDev/generator-teams) para o Microsoft Teams para scaffold seu aplicativo do Teams, incluindo seu serviço Web.</span><span class="sxs-lookup"><span data-stu-id="b5944-125">If you're using JavaScript, use the [Yeoman generator for Microsoft Teams](https://github.com/OfficeDev/generator-teams) to scaffold your Teams app, including your web service.</span></span>
* <span data-ttu-id="b5944-126">Criar seu serviço Web a partir do zero.</span><span class="sxs-lookup"><span data-stu-id="b5944-126">Create your web service from scratch.</span></span> <span data-ttu-id="b5944-127">Você pode optar por adicionar o SDK do verificador de bot para o seu idioma ou trabalhar diretamente com as cargas JSON.</span><span class="sxs-lookup"><span data-stu-id="b5944-127">You can choose to add the Bot Framework SDK for your language, or you can work directly with the JSON payloads.</span></span>

## <a name="register-your-web-service-with-the-bot-framework"></a><span data-ttu-id="b5944-128">Registrar seu serviço Web com a estrutura bot</span><span class="sxs-lookup"><span data-stu-id="b5944-128">Register your web service with the Bot Framework</span></span>

<span data-ttu-id="b5944-129">As extensões de mensagens aproveitam o esquema de mensagens da Estrutura de Bot e o protocolo de comunicação seguro; se você ainda não tiver um, precisará registrar seu serviço Web na Estrutura de Bots.</span><span class="sxs-lookup"><span data-stu-id="b5944-129">Messaging extensions take advantage of the Bot Framework's messaging schema and secure communication protocol; if you don't already have one you'll need to register your web service on the Bot Framework.</span></span> <span data-ttu-id="b5944-130">A ID do Aplicativo da Microsoft (vamos nos referir a isso como sua ID de Bot de dentro do Teams, para identificá-la de outras IDs de aplicativos com as quais você pode estar trabalhando) e o ponto de extremidade de mensagens com o qual seu registro com a Estrutura de Bots será usado em sua extensão de mensagens para receber e responder a solicitações.</span><span class="sxs-lookup"><span data-stu-id="b5944-130">The Microsoft App Id (we'll refer to this as your Bot Id from inside of Teams, to identify it from other App Id's you might be working with) and the messaging endpoint your register with the Bot Framework will be used in your messaging extension to receive and respond to requests.</span></span> <span data-ttu-id="b5944-131">Se você estiver usando um registro existente, certifique-se de [habilitar o canal do Microsoft Teams](/azure/bot-service/bot-service-manage-channels.md?view=azure-bot-service-4.0&preserve-view=true).</span><span class="sxs-lookup"><span data-stu-id="b5944-131">If you're using an existing registration, make sure you [enable the Microsoft Teams channel](/azure/bot-service/bot-service-manage-channels.md?view=azure-bot-service-4.0&preserve-view=true).</span></span>

<span data-ttu-id="b5944-132">Se você seguir um dos inícios rápidos ou começar a partir de um dos exemplos disponíveis, você será orientado a registrar seu serviço Web.</span><span class="sxs-lookup"><span data-stu-id="b5944-132">If you follow one of the quickstarts or start from one of the available samples you'll be guided through registering your web service.</span></span> <span data-ttu-id="b5944-133">Se você quiser registrar manualmente seu serviço, você tem três opções para fazer isso.</span><span class="sxs-lookup"><span data-stu-id="b5944-133">If you want to manually register your service you have three options to do so.</span></span> <span data-ttu-id="b5944-134">Se você optar por se registrar sem usar uma assinatura do Azure, não poderá aproveitar o fluxo de autenticação OAuth simplificado fornecido pela Estrutura de Bots.</span><span class="sxs-lookup"><span data-stu-id="b5944-134">If you choose to register without using an Azure subscription you will not be able to take advantage of the simplified OAuth authentication flow provided by the Bot Framework.</span></span> <span data-ttu-id="b5944-135">Você poderá migrar seu registro para o Azure após a criação.</span><span class="sxs-lookup"><span data-stu-id="b5944-135">You will be able to migrate your registration to Azure after creation.</span></span>

* <span data-ttu-id="b5944-136">Se você tiver uma assinatura do Azure (ou quiser criar uma nova), poderá registrar seu serviço Web manualmente usando o Portal do Azure.</span><span class="sxs-lookup"><span data-stu-id="b5944-136">If you have an Azure subscription (or want to create a new one), you can register your web service manually using the Azure Portal.</span></span> <span data-ttu-id="b5944-137">Crie um recurso "Registro de Canais bot".</span><span class="sxs-lookup"><span data-stu-id="b5944-137">Create a "Bot Channels Registration" resource.</span></span> <span data-ttu-id="b5944-138">Você pode escolher a camada de preços gratuita, pois as mensagens do Microsoft Teams não contam para o total de mensagens aceitável por mês.</span><span class="sxs-lookup"><span data-stu-id="b5944-138">You can choose the free pricing tier, as messages from Microsoft Teams do not count towards your total allowable messages per month.</span></span>
* <span data-ttu-id="b5944-139">Se você não quiser usar uma assinatura do Azure, poderá usar o [portal de registro herdado.](https://dev.botframework.com/bots/new)</span><span class="sxs-lookup"><span data-stu-id="b5944-139">If you do not wish to use an Azure subscription, you can use the [legacy registration portal](https://dev.botframework.com/bots/new).</span></span>
* <span data-ttu-id="b5944-140">O App Studio também pode ajudá-lo a registrar seu serviço Web (bot).</span><span class="sxs-lookup"><span data-stu-id="b5944-140">App Studio can also help you register your web service (bot).</span></span> <span data-ttu-id="b5944-141">Os serviços Web registrados por meio do App Studio não são registrados no Azure.</span><span class="sxs-lookup"><span data-stu-id="b5944-141">Web services registered through App Studio are not registered in Azure.</span></span> <span data-ttu-id="b5944-142">Você pode usar o [portal herdado](https://dev.botframework.com/bots) para exibir, gerenciar e migrar seus registros.</span><span class="sxs-lookup"><span data-stu-id="b5944-142">You can use the [legacy portal](https://dev.botframework.com/bots) to view, manage, and migrate your registrations.</span></span>

## <a name="create-your-app-manifest"></a><span data-ttu-id="b5944-143">Criar seu manifesto do aplicativo</span><span class="sxs-lookup"><span data-stu-id="b5944-143">Create your app manifest</span></span>

<span data-ttu-id="b5944-144">Você pode usar o aplicativo Studio para ajudá-lo a criar seu manifesto de aplicativo ou a criá-lo manualmente.</span><span class="sxs-lookup"><span data-stu-id="b5944-144">You can either use App Studio to help you create your app manifest, or create it manually.</span></span>

### <a name="create-your-app-manifest-using-app-studio"></a><span data-ttu-id="b5944-145">Criar seu manifesto do aplicativo usando o App Studio</span><span class="sxs-lookup"><span data-stu-id="b5944-145">Create your app manifest using App Studio</span></span>

<span data-ttu-id="b5944-146">Você pode usar o aplicativo App Studio de dentro do cliente do Microsoft Teams para ajudar a criar o manifesto do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="b5944-146">You can use the App Studio app from within the Microsoft Teams client to help create your app manifest.</span></span>

1. <span data-ttu-id="b5944-147">No cliente do Teams, abra o aplicativo Studio no menu de estouro **...** no trilho de navegação à esquerda.</span><span class="sxs-lookup"><span data-stu-id="b5944-147">In the Teams client, open App Studio from the **...** overflow menu on the left navigation rail.</span></span> <span data-ttu-id="b5944-148">Se ainda não estiver instalado, você poderá fazer isso pesquisando por ele.</span><span class="sxs-lookup"><span data-stu-id="b5944-148">If it isn't already installed, you can do so by searching for it.</span></span>
2. <span data-ttu-id="b5944-149">Na guia **Editor de manifesto,** selecione **Criar** um novo aplicativo (ou se você estiver adicionando uma extensão de mensagens a um aplicativo existente, você pode importar seu pacote de aplicativo)</span><span class="sxs-lookup"><span data-stu-id="b5944-149">On the **Manifest editor** tab select **Create a new app** (or if you're adding a messaging extension to an existing app, you can import your app package)</span></span>
3. <span data-ttu-id="b5944-150">Adicione os detalhes do aplicativo (Confira [definição de esquema de manifesto](~/resources/schema/manifest-schema.md) para obter descrições completas de cada campo).</span><span class="sxs-lookup"><span data-stu-id="b5944-150">Add your app details (see [manifest schema definition](~/resources/schema/manifest-schema.md) for full descriptions of each field).</span></span>
4. <span data-ttu-id="b5944-151">Na guia **Extensões de Mensagens,** clique no botão **Instalação.**</span><span class="sxs-lookup"><span data-stu-id="b5944-151">On the **Messaging extensions** tab click the **Setup** button.</span></span>
5. <span data-ttu-id="b5944-152">Você pode criar um novo serviço Web (bot) para sua extensão de mensagens usar ou se você já registrou um selecione/adicione-o aqui.</span><span class="sxs-lookup"><span data-stu-id="b5944-152">You can either create a new web service (bot) for your messaging extension to use, or if you've already registered one select/add it here.</span></span>
6. <span data-ttu-id="b5944-153">Se necessário, atualize o endereço do ponto de extremidade do bot para apontar para o seu bot.</span><span class="sxs-lookup"><span data-stu-id="b5944-153">If necessary, update your bot endpoint address to point to your bot.</span></span> <span data-ttu-id="b5944-154">Ela deve ser similar a `https://someplace.com/api/messages`.</span><span class="sxs-lookup"><span data-stu-id="b5944-154">It should look something like `https://someplace.com/api/messages`.</span></span>
7. <span data-ttu-id="b5944-155">O **botão Adicionar** na seção **Comando** orientará você através da adição de comandos à extensão de mensagens.</span><span class="sxs-lookup"><span data-stu-id="b5944-155">The **Add** button in the **Command** section will guide you through adding commands to your messaging extension.</span></span> <span data-ttu-id="b5944-156">Consulte a [seção Saiba mais](#learn-more) para obter mais informações sobre como adicionar comandos.</span><span class="sxs-lookup"><span data-stu-id="b5944-156">See the [Learn more](#learn-more) section for links to more information on adding commands.</span></span> <span data-ttu-id="b5944-157">Lembre-se de que você pode definir até 10 comandos para sua extensão de mensagens.</span><span class="sxs-lookup"><span data-stu-id="b5944-157">Remember you can define up to 10 commands for your messaging extension.</span></span>
8. <span data-ttu-id="b5944-158">A **seção Manipuladores de** Mensagens permite que você adicione um domínio em que suas mensagens serão disparadas.</span><span class="sxs-lookup"><span data-stu-id="b5944-158">The **Message Handlers** section allows you to add a domain that your messaging will trigger on.</span></span> <span data-ttu-id="b5944-159">Consulte [link unfurling](~/messaging-extensions/how-to/link-unfurling.md) para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="b5944-159">See [link unfurling](~/messaging-extensions/how-to/link-unfurling.md) for more information.</span></span>

<span data-ttu-id="b5944-160">Na guia **Concluir =>** e distribuir, você pode **Baixar** o pacote do aplicativo (que inclui o manifesto do aplicativo, bem como os ícones do aplicativo) ou **Instalar** o pacote.</span><span class="sxs-lookup"><span data-stu-id="b5944-160">From the **Finish => Test and distribute** tab you can **Download** your app package (which includes your app manifest as well as your app icons), or **Install** the package.</span></span>

### <a name="create-your-app-manifest-manually"></a><span data-ttu-id="b5944-161">Criar o manifesto do aplicativo manualmente</span><span class="sxs-lookup"><span data-stu-id="b5944-161">Create your app manifest manually</span></span>

<span data-ttu-id="b5944-162">Assim como com bots e [](~/resources/schema/manifest-schema.md#composeextensions) guias, você atualiza o manifesto do aplicativo do aplicativo para incluir as propriedades de extensão de mensagens.</span><span class="sxs-lookup"><span data-stu-id="b5944-162">As with bots and tabs, you update the [app manifest](~/resources/schema/manifest-schema.md#composeextensions) of your app to include the messaging extension properties.</span></span> <span data-ttu-id="b5944-163">Essas propriedades governam como sua extensão de mensagens aparece e se comporta no cliente do Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="b5944-163">These properties govern how your messaging extension appears and behaves in the Microsoft Teams client.</span></span> <span data-ttu-id="b5944-164">As extensões de mensagens são suportadas começando com v1.0 do manifesto.</span><span class="sxs-lookup"><span data-stu-id="b5944-164">Messaging extensions are supported beginning with v1.0 of the manifest.</span></span>

#### <a name="declare-your-messaging-extension"></a><span data-ttu-id="b5944-165">Declarar sua extensão de mensagens</span><span class="sxs-lookup"><span data-stu-id="b5944-165">Declare your messaging extension</span></span>

<span data-ttu-id="b5944-166">Para adicionar uma extensão de mensagens, inclua uma nova estrutura JSON de nível superior no manifesto do aplicativo com a `composeExtensions` propriedade.</span><span class="sxs-lookup"><span data-stu-id="b5944-166">To add a messaging extension, include a new top-level JSON structure in your app manifest with the `composeExtensions` property.</span></span> <span data-ttu-id="b5944-167">Você cria uma única extensão de mensagens para seu aplicativo, com até 10 comandos.</span><span class="sxs-lookup"><span data-stu-id="b5944-167">You create a single messaging extension for your app, with up to 10 commands.</span></span>

> [!NOTE]
> <span data-ttu-id="b5944-168">O manifesto refere-se a extensões de mensagens como `composeExtensions` .</span><span class="sxs-lookup"><span data-stu-id="b5944-168">The manifest refers to messaging extensions as `composeExtensions`.</span></span> <span data-ttu-id="b5944-169">Isso é para manter a compatibilidade com compatibilidade com backward.</span><span class="sxs-lookup"><span data-stu-id="b5944-169">This is to maintain backward compatibility.</span></span>

<span data-ttu-id="b5944-170">A definição de extensão é um objeto que tem a seguinte estrutura:</span><span class="sxs-lookup"><span data-stu-id="b5944-170">The extension definition is an object that has the following structure:</span></span>

| <span data-ttu-id="b5944-171">Nome da propriedade</span><span class="sxs-lookup"><span data-stu-id="b5944-171">Property name</span></span> | <span data-ttu-id="b5944-172">Objetivo</span><span class="sxs-lookup"><span data-stu-id="b5944-172">Purpose</span></span> | <span data-ttu-id="b5944-173">Obrigatório?</span><span class="sxs-lookup"><span data-stu-id="b5944-173">Required?</span></span> |
|---|---|---|
| `botId` | <span data-ttu-id="b5944-174">O ID exclusivo do aplicativo Microsoft para o bot conforme registrado na estrutura do bot.</span><span class="sxs-lookup"><span data-stu-id="b5944-174">The unique Microsoft app ID for the bot as registered with the Bot Framework.</span></span> <span data-ttu-id="b5944-175">Normalmente, isso deve ser o mesmo que a ID do aplicativo geral do Teams.</span><span class="sxs-lookup"><span data-stu-id="b5944-175">This should typically be the same as the ID for your overall Teams app.</span></span> | <span data-ttu-id="b5944-176">Sim</span><span class="sxs-lookup"><span data-stu-id="b5944-176">Yes</span></span> |
| `canUpdateConfiguration` | <span data-ttu-id="b5944-177">Habilita o item de menu **Configurações.**</span><span class="sxs-lookup"><span data-stu-id="b5944-177">Enables **Settings** menu item.</span></span> | <span data-ttu-id="b5944-178">Não</span><span class="sxs-lookup"><span data-stu-id="b5944-178">No</span></span> |
| `commands` | <span data-ttu-id="b5944-179">Matriz de comandos compatíveis com essa extensão de mensagens.</span><span class="sxs-lookup"><span data-stu-id="b5944-179">Array of commands that this messaging extension supports.</span></span> <span data-ttu-id="b5944-180">Você está limitado a 10 comandos.</span><span class="sxs-lookup"><span data-stu-id="b5944-180">You are limited to 10 commands.</span></span> | <span data-ttu-id="b5944-181">Sim</span><span class="sxs-lookup"><span data-stu-id="b5944-181">Yes</span></span> |

#### <a name="define-your-commands"></a><span data-ttu-id="b5944-182">Definir seus comandos</span><span class="sxs-lookup"><span data-stu-id="b5944-182">Define your commands</span></span>

<span data-ttu-id="b5944-183">Sua extensão de mensagens deve declarar um ou mais comandos, que definem onde os usuários podem disparar sua extensão de mensagens e o tipo de interação.</span><span class="sxs-lookup"><span data-stu-id="b5944-183">Your messaging extension should declare one or more commands, which define where your users can trigger your messaging extension, and the type of interaction.</span></span> <span data-ttu-id="b5944-184">Confira [mais informações sobre](#learn-more) comandos de extensão de mensagens.</span><span class="sxs-lookup"><span data-stu-id="b5944-184">See [learn more](#learn-more) for more information on messaging extension commands.</span></span>

#### <a name="simple-manifest-example"></a><span data-ttu-id="b5944-185">Exemplo de manifesto simples</span><span class="sxs-lookup"><span data-stu-id="b5944-185">Simple manifest example</span></span>

<span data-ttu-id="b5944-186">O exemplo a seguir é um objeto de extensão de mensagens simples no manifesto do aplicativo com um comando de pesquisa.</span><span class="sxs-lookup"><span data-stu-id="b5944-186">The following example is a simple messaging extension object in the app manifest with a search command.</span></span> <span data-ttu-id="b5944-187">Esse não é o arquivo de manifesto completo do aplicativo, apenas a parte específica das extensões de mensagens.</span><span class="sxs-lookup"><span data-stu-id="b5944-187">This is not the entire app manifest file, just the part specific to messaging extensions.</span></span> <span data-ttu-id="b5944-188">Confira [o esquema de manifesto do aplicativo](~/resources/schema/manifest-schema.md) para ver um exemplo completo.</span><span class="sxs-lookup"><span data-stu-id="b5944-188">See [app manifest schema](~/resources/schema/manifest-schema.md) for a complete example.</span></span>

```json
...
"composeExtensions": [
  {
    "botId": "abcd1234-1fc5-4d97-a142-35bb662b7b23",
    "canUpdateConfiguration": true,
    "commands": [
      {
        "id": "searchCmd",
        "description": "Search you ToDo's",
        "title": "Search",
        "initialRun": true,
        "parameters": [
          {
            "name": "searchKeyword",
            "description": "Enter your search keywords",
            "title": "Keywords"
          }
        ]
      }
    ]
  }
]
...
```

#### <a name="complete-app-manifest-example"></a><span data-ttu-id="b5944-189">Exemplo de manifesto completo do aplicativo</span><span class="sxs-lookup"><span data-stu-id="b5944-189">Complete app manifest example</span></span>

```json
{
  "$schema": "https://developer.microsoft.com/json-schemas/teams/v1.8/MicrosoftTeams.schema.json",
  "manifestVersion": "1.5",
  "version": "1.0",
  "id": "57a3c29f-1fc5-4d97-a142-35bb662b7b23",
  "packageName": "com.microsoft.teams.samples.Todo",
  "developer": {
    "name": "John Developer",
    "websiteUrl": "http://todobotservice.azurewebsites.net/",
    "privacyUrl": "http://todobotservice.azurewebsites.net/privacy",
    "termsOfUseUrl": "http://todobotservice.azurewebsites.net/termsofuse"
  },
  "name": {
    "short": "To Do",
    "full": "To Do"
  },
  "description": {
    "short": "Find or create a new task in To Do",
    "full": "Find or create a new task in To Do"
  },
  "icons": {
    "outline": "todo-outline.jpg",
    "color": "todo-color.jpg"
  },
  "accentColor": "#ff6a00",
  "composeExtensions": [
    {
      "botId": "57a3c29f-1fc5-4d97-a142-35bb662b7b23",
      "canUpdateConfiguration": true,
      "commands": [
        {
          "id": "searchCmd",
          "description": "Search you Todo's",
          "title": "Search",
          "initialRun": true,
          "context": ["commandBox", "compose"],
          "parameters": [
            {
              "name": "searchKeyword",
              "description": "Enter your search keywords",
              "title": "Keywords"
            }
          ]
        },
        {
          "id": "addTodo",
          "description": "Create a To Do item",
          "title": "Create To Do",
          "type": "action",
          "context": ["commandBox", "message", "compose"],
          "parameters": [
            {
              "name": "Name",
              "description": "To Do Title",
              "title": "Title",
              "inputType": "text"
            },
            {
              "name": "Description",
              "description": "Description of the task",
              "title": "Description",
              "inputType": "textarea"
            },
            {
              "name": "Date",
              "description": "Due date for the task",
              "title": "Date",
              "inputType": "date"
            }
          ]
        },
        {
          "id": "reassignTodo",
          "description": "Reassign a todo item",
          "title": "Reassign a todo item",
          "type": "action",
          "fetchTask": true,
          "parameters": [
            {
              "name": "Name",
              "title": "Title"
            }
          ]
        }
      ]
    }
  ],
  "permissions": [
    "identity",
    "messageTeamMembers"
  ],
  "validDomains": [
    "todobotservice.azurewebsites.net",
    "*.todobotservice.azurewebsites.net"
  ]
}
```

## <a name="add-your-invoke-message-handlers"></a><span data-ttu-id="b5944-190">Adicionar seus manipuladores de mensagens de invocação</span><span class="sxs-lookup"><span data-stu-id="b5944-190">Add your invoke message handlers</span></span>

<span data-ttu-id="b5944-191">Quando os usuários acionarem a extensão de mensagens, você precisará lidar com a mensagem de invocação inicial, coletar algumas informações do usuário e processar essas informações e responder adequadamente.</span><span class="sxs-lookup"><span data-stu-id="b5944-191">When your users trigger your messaging extension you'll need to handle the initial invoke message, collect some information from the user, then process that information and respond appropriately.</span></span> <span data-ttu-id="b5944-192">Para fazer isso, primeiro você precisará decidir que tipo de comandos deseja adicionar [](~/messaging-extensions/how-to/action-commands/define-action-command.md) à extensão de mensagens e adicionar comandos de ação ou adicionar comandos [de pesquisa.](~/messaging-extensions/how-to/search-commands/define-search-command.md)</span><span class="sxs-lookup"><span data-stu-id="b5944-192">To do that, you'll first need to decide what kind of commands you want to add to your messaging extension and either [add an action commands](~/messaging-extensions/how-to/action-commands/define-action-command.md) or [add a search commands](~/messaging-extensions/how-to/search-commands/define-search-command.md).</span></span>

## <a name="messaging-extensions-in-teams-meetings"></a><span data-ttu-id="b5944-193">Extensões de mensagens em reuniões do Teams</span><span class="sxs-lookup"><span data-stu-id="b5944-193">Messaging extensions in Teams meetings</span></span>

> [!NOTE]
> <span data-ttu-id="b5944-194">Se uma reunião ou chat de grupo tiver usuários federados na lista, o Teams suprime o acesso a extensões de mensagens para todos os usuários, incluindo o organizador.</span><span class="sxs-lookup"><span data-stu-id="b5944-194">If a meeting or group chat has federated users in the roster, Teams suppresses access to messaging extensions for all users, including the organizer.</span></span>

<span data-ttu-id="b5944-195">Quando uma reunião começa, os participantes do Teams podem interagir diretamente com sua extensão de mensagens durante uma chamada ao vivo.</span><span class="sxs-lookup"><span data-stu-id="b5944-195">Once a meeting begins, Teams participants can interact directly with your messaging extension during a live call.</span></span> <span data-ttu-id="b5944-196">Considere o seguinte ao criar sua extensão de mensagens na reunião:</span><span class="sxs-lookup"><span data-stu-id="b5944-196">Consider the following when building your in-meeting messaging extension:</span></span>

1. <span data-ttu-id="b5944-197">**Localização**</span><span class="sxs-lookup"><span data-stu-id="b5944-197">**Location**.</span></span> <span data-ttu-id="b5944-198">Sua extensão de mensagens pode ser invocada da área de mensagem de redação, da caixa de comando ou @mentioned no chat da reunião.</span><span class="sxs-lookup"><span data-stu-id="b5944-198">Your messaging extension can be invoked from the compose message area, the command box, or @mentioned in the meeting chat.</span></span>

1. <span data-ttu-id="b5944-199">**Metadados**.</span><span class="sxs-lookup"><span data-stu-id="b5944-199">**Metadata**.</span></span> <span data-ttu-id="b5944-200">Quando sua extensão de mensagens é invocada, ela pode identificar o usuário e o locatário `userId` de `tenantId` e .</span><span class="sxs-lookup"><span data-stu-id="b5944-200">When your messaging extension is invoked it can identify the user and tenant from `userId` and `tenantId`.</span></span> <span data-ttu-id="b5944-201">O `meetingId` pode ser encontrado como parte do objeto `channelData`.</span><span class="sxs-lookup"><span data-stu-id="b5944-201">The `meetingId` can be found as part of the `channelData` object.</span></span> <span data-ttu-id="b5944-202">Seu aplicativo pode usar e `userId` `meetingId`  para a solicitação de API recuperar funções `GetParticipant` de usuário.</span><span class="sxs-lookup"><span data-stu-id="b5944-202">Your app can use the `userId` and `meetingId`  for the `GetParticipant` API request to retrieve user roles.</span></span>

1. <span data-ttu-id="b5944-203">**Tipo de comando**.</span><span class="sxs-lookup"><span data-stu-id="b5944-203">**Command type**.</span></span> <span data-ttu-id="b5944-204">Se a extensão da mensagem usar [comandos baseados em ação,](../messaging-extensions/what-are-messaging-extensions.md#action-commands)ela deverá seguir as guias [autenticação de login](../tabs/how-to/authentication/auth-aad-sso.md) único.</span><span class="sxs-lookup"><span data-stu-id="b5944-204">If your message extension uses [action-based commands](../messaging-extensions/what-are-messaging-extensions.md#action-commands), it should follow tabs [single sign-on](../tabs/how-to/authentication/auth-aad-sso.md) authentication.</span></span>

1. <span data-ttu-id="b5944-205">**Experiência do usuário**.</span><span class="sxs-lookup"><span data-stu-id="b5944-205">**User experience**.</span></span> <span data-ttu-id="b5944-206">A extensão de mensagens deve parecer e se comportar da mesma forma que faria fora de uma reunião.</span><span class="sxs-lookup"><span data-stu-id="b5944-206">You messaging extension should look and behave the same as it would outside a meeting.</span></span>

## <a name="next-steps"></a><span data-ttu-id="b5944-207">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="b5944-207">Next steps</span></span>

* [<span data-ttu-id="b5944-208">Criar comandos de ação</span><span class="sxs-lookup"><span data-stu-id="b5944-208">Create action commands</span></span>](~/messaging-extensions/how-to/action-commands/define-action-command.md)
* [<span data-ttu-id="b5944-209">Criar comandos de pesquisa</span><span class="sxs-lookup"><span data-stu-id="b5944-209">Create search commands</span></span>](~/messaging-extensions/how-to/search-commands/define-search-command.md)
* [<span data-ttu-id="b5944-210">Desenrolamento de link</span><span class="sxs-lookup"><span data-stu-id="b5944-210">Link unfurling</span></span>](~/messaging-extensions/how-to/link-unfurling.md)

## <a name="learn-more"></a><span data-ttu-id="b5944-211">Saiba mais</span><span class="sxs-lookup"><span data-stu-id="b5944-211">Learn more</span></span>

<span data-ttu-id="b5944-212">Experimente em um início rápido:</span><span class="sxs-lookup"><span data-stu-id="b5944-212">Try it out in a quickstart:</span></span>

* <span data-ttu-id="b5944-213">Início rápido para C #</span><span class="sxs-lookup"><span data-stu-id="b5944-213">Quickstarts for C#</span></span>
  * [<span data-ttu-id="b5944-214">Extensão de mensagens com comandos baseados em ação</span><span class="sxs-lookup"><span data-stu-id="b5944-214">Messaging extension with action-based commands</span></span>](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/csharp_dotnetcore/51.teams-messaging-extensions-action)
  * [<span data-ttu-id="b5944-215">Extensão de mensagens com comandos baseados em pesquisa</span><span class="sxs-lookup"><span data-stu-id="b5944-215">Messaging extension with search-based commands</span></span>](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/csharp_dotnetcore/50.teams-messaging-extensions-search)
* <span data-ttu-id="b5944-216">Início rápido para JavaScript</span><span class="sxs-lookup"><span data-stu-id="b5944-216">Quickstarts for JavaScript</span></span>
  * [<span data-ttu-id="b5944-217">Extensão de mensagens com comandos baseados em ação</span><span class="sxs-lookup"><span data-stu-id="b5944-217">Messaging extension with action-based commands</span></span>](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/javascript_nodejs/51.teams-messaging-extensions-action)
  * [<span data-ttu-id="b5944-218">Extensão de mensagens com comandos baseados em pesquisa</span><span class="sxs-lookup"><span data-stu-id="b5944-218">Messaging extension with search-based commands</span></span>](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/javascript_nodejs/50.teams-messaging-extensions-search)

<span data-ttu-id="b5944-219">Saiba mais sobre os conceitos de desenvolvimento do Teams:</span><span class="sxs-lookup"><span data-stu-id="b5944-219">Learn more about Teams development concepts:</span></span>

* [<span data-ttu-id="b5944-220">Compreender os recursos do aplicativo teams</span><span class="sxs-lookup"><span data-stu-id="b5944-220">Understand Teams app capabilities</span></span>](../concepts/capabilities-overview.md)
* [<span data-ttu-id="b5944-221">O que são extensões de mensagens?</span><span class="sxs-lookup"><span data-stu-id="b5944-221">What are messaging extensions?</span></span>](../messaging-extensions/what-are-messaging-extensions.md)
