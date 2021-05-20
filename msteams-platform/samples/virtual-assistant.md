---
title: Criar um Assistente Virtual
description: Como criar bot virtual assistente e habilidades para uso em Microsoft Teams
localization_priority: Normal
ms.topic: how-to
keywords: equipes robôs assistentes virtuais
ms.openlocfilehash: 072d9cb5742cd39101587cad32e3048bd36cc1d8
ms.sourcegitcommit: 51e4a1464ea58c254ad6bd0317aca03ebf6bf1f6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2021
ms.locfileid: "52566870"
---
# <a name="create-virtual-assistant"></a><span data-ttu-id="e70b7-104">Criar um Assistente Virtual</span><span class="sxs-lookup"><span data-stu-id="e70b7-104">Create Virtual Assistant</span></span> 

<span data-ttu-id="e70b7-105">Virtual Assistant é um modelo de código aberto da Microsoft que permite criar uma solução de conversação robusta, mantendo o controle total da experiência do usuário, da marca organizacional e dos dados necessários.</span><span class="sxs-lookup"><span data-stu-id="e70b7-105">Virtual Assistant is a Microsoft open-source template that enables you to create a robust conversational solution while maintaining full control of user experience, organizational branding, and necessary data.</span></span> <span data-ttu-id="e70b7-106">O [modelo principal do Virtual Assistant](https://microsoft.github.io/botframework-solutions/overview/virtual-assistant-template) é o bloco básico de construção que reúne as tecnologias microsoft necessárias para construir um Assistente Virtual, incluindo o Bot Framework [SDK,](https://github.com/microsoft/botframework-sdk) [Language Understanding (LUIS)](https://www.luis.ai/)e [QnA Maker](https://www.qnamaker.ai/).</span><span class="sxs-lookup"><span data-stu-id="e70b7-106">The [Virtual Assistant core template](https://microsoft.github.io/botframework-solutions/overview/virtual-assistant-template) is the basic building block that brings together the Microsoft technologies required to build a Virtual Assistant, including the [Bot Framework SDK](https://github.com/microsoft/botframework-sdk), [Language Understanding (LUIS)](https://www.luis.ai/), and [QnA Maker](https://www.qnamaker.ai/).</span></span> <span data-ttu-id="e70b7-107">Também reúne os recursos essenciais, incluindo registro de habilidades, contas vinculadas, intenção conversacional básica para oferecer uma gama de interações e experiências perfeitas aos usuários.</span><span class="sxs-lookup"><span data-stu-id="e70b7-107">It also brings together the essential capabilities including  skills registration, linked accounts, basic conversational intent to offer a range of seamless interactions and experiences to users.</span></span> <span data-ttu-id="e70b7-108">Além disso, os recursos do modelo incluem exemplos ricos de [habilidades](https://microsoft.github.io/botframework-solutions/overview/skills)de conversação reutilizáveis.</span><span class="sxs-lookup"><span data-stu-id="e70b7-108">In addition, the template capabilities include rich examples of reusable conversational [skills](https://microsoft.github.io/botframework-solutions/overview/skills).</span></span>  <span data-ttu-id="e70b7-109">As habilidades individuais são integradas em uma solução de Assistente Virtual para habilitar vários cenários.</span><span class="sxs-lookup"><span data-stu-id="e70b7-109">Individual skills are integrated in a Virtual Assistant solution to enable multiple scenarios.</span></span> <span data-ttu-id="e70b7-110">Usando o Bot Framework SDK, as habilidades são apresentadas no formulário de código-fonte, permitindo que você personalize e se estenda conforme necessário.</span><span class="sxs-lookup"><span data-stu-id="e70b7-110">Using the Bot Framework SDK, skills are presented in source code form, enabling you to customize and extend as required.</span></span> <span data-ttu-id="e70b7-111">Para obter mais informações sobre as habilidades do Bot Framework, consulte [o que é uma habilidade do Bot Framework](https://microsoft.github.io/botframework-solutions/overview/skills/).</span><span class="sxs-lookup"><span data-stu-id="e70b7-111">For more information on skills of Bot Framework, see [What is a Bot Framework skill](https://microsoft.github.io/botframework-solutions/overview/skills/).</span></span> <span data-ttu-id="e70b7-112">Este documento orienta você sobre considerações de implementação do Virtual Assistant para organizações, como criar um Assistente Virtual focado em Teams, exemplo relacionado, amostra de código e limitações do Assistente Virtual.</span><span class="sxs-lookup"><span data-stu-id="e70b7-112">This document guides you on Virtual Assistant implementation considerations for organizations, how to create a Teams focused Virtual Assistant, related example, code sample, and limitations of Virtual Assistant.</span></span>
<span data-ttu-id="e70b7-113">A imagem a seguir exibe a visão geral do assistente virtual:</span><span class="sxs-lookup"><span data-stu-id="e70b7-113">The following image displays the overview of virtual assistant:</span></span>

![Diagrama de visão geral do assistente virtual](../assets/images/bots/virtual-assistant/overview.png)

<span data-ttu-id="e70b7-115">As atividades de mensagem de texto são roteadas para habilidades associadas pelo núcleo assistente virtual usando um modelo [de despacho.](/azure/bot-service/bot-builder-tutorial-dispatch?view=azure-bot-service-4.0&tabs=cs&preserve-view=true)</span><span class="sxs-lookup"><span data-stu-id="e70b7-115">Text message activities are routed to associated skills by the Virtual Assistant core using a [dispatch](/azure/bot-service/bot-builder-tutorial-dispatch?view=azure-bot-service-4.0&tabs=cs&preserve-view=true) model.</span></span> 

## <a name="implementation-considerations"></a><span data-ttu-id="e70b7-116">Considerações de implementação</span><span class="sxs-lookup"><span data-stu-id="e70b7-116">Implementation considerations</span></span>

<span data-ttu-id="e70b7-117">A decisão de adicionar um Assistente Virtual inclui muitos determinantes e difere para cada organização.</span><span class="sxs-lookup"><span data-stu-id="e70b7-117">The decision to add a Virtual Assistant includes many determinants and differs for each organization.</span></span> <span data-ttu-id="e70b7-118">Os fatores de suporte de uma implementação do Assistente Virtual para sua organização são os seguintes:</span><span class="sxs-lookup"><span data-stu-id="e70b7-118">The supporting factors of a Virtual Assistant implementation for your organization are as follows:</span></span>

* <span data-ttu-id="e70b7-119">Uma equipe central gerencia todas as experiências dos funcionários.</span><span class="sxs-lookup"><span data-stu-id="e70b7-119">A central team manages all employee experiences.</span></span> <span data-ttu-id="e70b7-120">Ele tem a capacidade de construir uma experiência de Assistente Virtual e gerenciar atualizações para a experiência principal, incluindo a adição de novas habilidades.</span><span class="sxs-lookup"><span data-stu-id="e70b7-120">It has the capability to build a Virtual Assistant experience and manage updates to the core experience including the addition of new skills.</span></span>
* <span data-ttu-id="e70b7-121">Existem várias aplicações em todas as funções de negócios e espera-se que o número cresça no futuro.</span><span class="sxs-lookup"><span data-stu-id="e70b7-121">Multiple applications exist across business functions and the number is expected to grow in the future.</span></span>
* <span data-ttu-id="e70b7-122">Os aplicativos existentes são personalizáveis, de propriedade da organização, e são convertidos em habilidades para um Assistente Virtual.</span><span class="sxs-lookup"><span data-stu-id="e70b7-122">Existing applications are customizable, owned by the organization, and are converted into skills for a Virtual Assistant.</span></span>
* <span data-ttu-id="e70b7-123">A equipe central de experiências dos funcionários é capaz de influenciar personalizações em aplicativos existentes.</span><span class="sxs-lookup"><span data-stu-id="e70b7-123">The central employee experiences team is able to influence customizations to existing apps.</span></span> <span data-ttu-id="e70b7-124">Também fornece orientações necessárias para integrar aplicativos existentes como habilidades na experiência do Assistente Virtual.</span><span class="sxs-lookup"><span data-stu-id="e70b7-124">It also provides necessary guidance for integrating existing applications as skills in Virtual Assistant experience.</span></span>

<span data-ttu-id="e70b7-125">A imagem a seguir exibe as funções de negócios do Assistente Virtual:</span><span class="sxs-lookup"><span data-stu-id="e70b7-125">The following image displays the business functions of Virtual Assistant:</span></span> 

![Equipe central mantém o assistente, e equipes de funções de negócios contribuem com habilidades](../assets/images/bots/virtual-assistant/business-functions.png)

## <a name="create-a-teams-focused-virtual-assistant"></a><span data-ttu-id="e70b7-127">Crie um assistente virtual focado em Teams</span><span class="sxs-lookup"><span data-stu-id="e70b7-127">Create a Teams-focused Virtual Assistant</span></span>

<span data-ttu-id="e70b7-128">A Microsoft publicou um [modelo Visual Studio](https://marketplace.visualstudio.com/items?itemName=BotBuilder.VirtualAssistantTemplate) para a construção de Assistentes Virtuais e habilidades.</span><span class="sxs-lookup"><span data-stu-id="e70b7-128">Microsoft has published a [Visual Studio template](https://marketplace.visualstudio.com/items?itemName=BotBuilder.VirtualAssistantTemplate) for building Virtual Assistants and skills.</span></span> <span data-ttu-id="e70b7-129">Com o modelo Visual Studio, você pode criar um Assistente Virtual, alimentado por uma experiência baseada em texto com suporte para cartões ricos limitados com ações.</span><span class="sxs-lookup"><span data-stu-id="e70b7-129">With the Visual Studio template, you can create a Virtual Assistant, powered by a text based experience with support for limited rich cards with actions.</span></span> <span data-ttu-id="e70b7-130">Nós melhoramos o modelo base de Visual Studio para incluir Microsoft Teams recursos da plataforma e potencialar grandes experiências de Teams aplicativos.</span><span class="sxs-lookup"><span data-stu-id="e70b7-130">We have enhanced the Visual Studio base template to include Microsoft Teams platform capabilities and power great Teams app experiences.</span></span> <span data-ttu-id="e70b7-131">Alguns dos recursos incluem suporte para cartões adaptativos ricos, módulos de tarefas, equipes ou chats em grupo e extensões de mensagens.</span><span class="sxs-lookup"><span data-stu-id="e70b7-131">A few of the capabilities include support for rich Adaptive Cards, task modules, teams or group chats, and messaging extensions.</span></span> <span data-ttu-id="e70b7-132">Para obter mais informações sobre a extensão do Assistente Virtual para Microsoft Teams, consulte [Tutorial: Amplie seu assistente virtual para Microsoft Teams](https://microsoft.github.io/botframework-solutions/clients-and-channels/tutorials/enable-teams/1-intro/).</span><span class="sxs-lookup"><span data-stu-id="e70b7-132">For more information on extending Virtual Assistant to Microsoft Teams, see [Tutorial: Extend Your Virtual Assistant to Microsoft Teams](https://microsoft.github.io/botframework-solutions/clients-and-channels/tutorials/enable-teams/1-intro/).</span></span>    
<span data-ttu-id="e70b7-133">A imagem a seguir exibe o diagrama de alto nível de uma solução de Assistente Virtual:</span><span class="sxs-lookup"><span data-stu-id="e70b7-133">The following image displays the high level diagram of a Virtual Assistant solution:</span></span>

![Diagrama de alto nível de uma solução de Assistente Virtual](../assets/images/bots/virtual-assistant/high-level-diagram.png)

### <a name="add-adaptive-cards-to-your-virtual-assistant"></a><span data-ttu-id="e70b7-135">Adicione cartões adaptativos ao seu assistente virtual</span><span class="sxs-lookup"><span data-stu-id="e70b7-135">Add Adaptive Cards to your Virtual Assistant</span></span>

<span data-ttu-id="e70b7-136">Para despachar as solicitações corretamente, o Assistente Virtual deve identificar o modelo LUIS correto e a habilidade correspondente associada a ele.</span><span class="sxs-lookup"><span data-stu-id="e70b7-136">To dispatch requests properly, your Virtual Assistant must identify the correct LUIS model and corresponding skill associated with it.</span></span> <span data-ttu-id="e70b7-137">No entanto, o mecanismo de expedição não pode ser usado para atividades de ação de cartão, pois o modelo LUIS associado a uma habilidade, é treinado para textos de ação de cartão.</span><span class="sxs-lookup"><span data-stu-id="e70b7-137">However, the dispatching mechanism cannot be used for card action activities as the LUIS model associated with a skill, is trained for card action texts.</span></span> <span data-ttu-id="e70b7-138">Os textos de ação do cartão são fixos, palavras-chave pré-definidas e não são comentados por um usuário.</span><span class="sxs-lookup"><span data-stu-id="e70b7-138">The card action texts are fixed, pre-defined keywords, and not commented from a user.</span></span>

<span data-ttu-id="e70b7-139">Essa desvantagem é resolvida incorporando informações de habilidade na carga de ação do cartão.</span><span class="sxs-lookup"><span data-stu-id="e70b7-139">This drawback is resolved this by embedding skill information in the card action payload.</span></span> <span data-ttu-id="e70b7-140">Todas as habilidades devem ser incorporadas `skillId` no campo das ações de  `value` cartas.</span><span class="sxs-lookup"><span data-stu-id="e70b7-140">Every skill should embed `skillId` in the  `value` field of card actions.</span></span> <span data-ttu-id="e70b7-141">Você deve garantir que cada atividade de ação de cartão carregue as informações de habilidade relevantes, e o Assistente Virtual pode utilizar essas informações para despachar.</span><span class="sxs-lookup"><span data-stu-id="e70b7-141">You must ensure that each card action activity carries the relevant skill information, and Virtual Assistant can utilize this information for dispatching.</span></span>

<span data-ttu-id="e70b7-142">Você deve fornecer `skillId` no construtor para garantir que as informações de habilidade estão sempre presentes nas ações do cartão.</span><span class="sxs-lookup"><span data-stu-id="e70b7-142">You must provide `skillId` in the constructor to ensure that the skill information is always present in card actions.</span></span>
<span data-ttu-id="e70b7-143">Um código de amostra de dados de ação do cartão é mostrado na seguinte seção:</span><span class="sxs-lookup"><span data-stu-id="e70b7-143">A card action data sample code is shown in the following section:</span></span>
```csharp
    public class CardActionData
    {
        public CardActionData(string skillId)
        {
            this.SkillId = skillId;
        }

        [JsonProperty("skillId")]
        public string SkillId { get; set; }
    }

    ...
    var button = new CardAction
    {
        Type = ActionTypes.MessageBack,
        Title = "Card action button",
        Text = "card action button text",
        Value = new CardActionData(<SkillId>),
    };
```

<span data-ttu-id="e70b7-144">Em seguida, `SkillCardActionData` a classe no modelo assistente virtual é introduz para extrair da carga de `skillId` ação do cartão.</span><span class="sxs-lookup"><span data-stu-id="e70b7-144">Next, `SkillCardActionData` class in the Virtual Assistant template is introduces to extract `skillId` from the card action payload.</span></span>
<span data-ttu-id="e70b7-145">Um trecho de código para extrair  `skillId` da carga de ação do cartão é mostrado na seguinte seção:</span><span class="sxs-lookup"><span data-stu-id="e70b7-145">A code snippet to extract  `skillId` from card action payload is shown in the following section:</span></span>

```csharp
    // Skill Card action data should contain skillId parameter
    // This class is used to deserialize it and get skillId 
    public class SkillCardActionData
    {
        /// <summary>
        /// Gets the ID of the skil that should handle this card
        /// </summary>
        [JsonProperty("skillId")]
        public string SkillId { get; set; }
    }
```

<span data-ttu-id="e70b7-146">A implementação é feita por um método de extensão na classe [Atividade.](https://github.com/microsoft/botframework-sdk/blob/master/specs/botframework-activity/botframework-activity.md)</span><span class="sxs-lookup"><span data-stu-id="e70b7-146">The implementation is done by an extension method in the [Activity](https://github.com/microsoft/botframework-sdk/blob/master/specs/botframework-activity/botframework-activity.md) class.</span></span>
<span data-ttu-id="e70b7-147">Um trecho de código para extrair  `skillId` dos dados de ação do cartão é mostrado na seguinte seção:</span><span class="sxs-lookup"><span data-stu-id="e70b7-147">A code snippet to extract  `skillId` from card action data is shown in the following section:</span></span>

```csharp
    public static class ActivityExtensions
    {
        // Fetches skillId from CardAction data if present
        public static string GetSkillId(this Activity activity)
        {
            string skillId = string.Empty;

            try
            {
                if (activity.Type.Equals(ActivityTypes.Message) && activity.Value != null)
                {
                    var data = JsonConvert.DeserializeObject<SkillCardActionData>(activity.Value.ToString());
                    skillId = data.SkillId;
                }
                else if (activity.Type.Equals(ActivityTypes.Invoke) && activity.Value != null)
                {
                    var data = JsonConvert.DeserializeObject<SkillCardActionData>(JObject.Parse(activity.Value.ToString()).SelectToken("data").ToString());
                    skillId = data.SkillId;
                }
            }
            catch
            {
                // If not able to retrive skillId, empty skillId should be returned
            }

            return skillId;
        }
    }
```

### <a name="handle-interruptions"></a><span data-ttu-id="e70b7-148">Interrupções no manuseio</span><span class="sxs-lookup"><span data-stu-id="e70b7-148">Handle interruptions</span></span>

<span data-ttu-id="e70b7-149">O Virtual Assistant pode lidar com interrupções nos casos em que um usuário tenta invocar uma habilidade enquanto outra habilidade está ativa no momento.</span><span class="sxs-lookup"><span data-stu-id="e70b7-149">Virtual Assistant can handle interruptions in cases where a user tries to invoke a skill while another skill is currently active.</span></span> <span data-ttu-id="e70b7-150">`TeamsSkillDialog`, e `TeamsSwitchSkillDialog` são introduzidos com base no [SkillDialog](https://github.com/microsoft/botframework-solutions/blob/5b46d73e220bbb4fba86c48be532e495535ca78a/sdk/csharp/libraries/microsoft.bot.solutions/Skills/SkillDialog.cs) do Bot Framework e [no SwitchSkillDialog](https://github.com/microsoft/botframework-solutions/blob/6d40fa8ae05f96b0c5e0464e01361a9e1deb696c/sdk/csharp/libraries/microsoft.bot.solutions/Skills/Dialogs/SwitchSkillDialog.cs).</span><span class="sxs-lookup"><span data-stu-id="e70b7-150">`TeamsSkillDialog`, and `TeamsSwitchSkillDialog`are introduced based on Bot Framework's [SkillDialog](https://github.com/microsoft/botframework-solutions/blob/5b46d73e220bbb4fba86c48be532e495535ca78a/sdk/csharp/libraries/microsoft.bot.solutions/Skills/SkillDialog.cs) and [SwitchSkillDialog](https://github.com/microsoft/botframework-solutions/blob/6d40fa8ae05f96b0c5e0464e01361a9e1deb696c/sdk/csharp/libraries/microsoft.bot.solutions/Skills/Dialogs/SwitchSkillDialog.cs).</span></span> <span data-ttu-id="e70b7-151">Eles permitem que os usuários alternem uma experiência de habilidade a partir de ações de cartão.</span><span class="sxs-lookup"><span data-stu-id="e70b7-151">They enable users to switch a skill experience from card actions.</span></span> <span data-ttu-id="e70b7-152">Para lidar com essa solicitação, o Assistente Virtual solicita ao usuário uma mensagem de confirmação para mudar as habilidades:</span><span class="sxs-lookup"><span data-stu-id="e70b7-152">To handle this request, the Virtual Assistant prompts the user with a confirmation message to switch skills:</span></span>

![Prompt de confirmação ao mudar para uma nova habilidade](../assets/images/bots/virtual-assistant/switch-skills-prompt.png)

### <a name="handle-task-module-requests"></a><span data-ttu-id="e70b7-154">Manuseie as solicitações do módulo de tarefa</span><span class="sxs-lookup"><span data-stu-id="e70b7-154">Handle task module requests</span></span>

<span data-ttu-id="e70b7-155">Para adicionar recursos de módulo de tarefa a um Assistente Virtual, dois métodos adicionais estão incluídos no manipulador de atividades do Assistente Virtual: `OnTeamsTaskModuleFetchAsync` e `OnTeamsTaskModuleSubmitAsync` .</span><span class="sxs-lookup"><span data-stu-id="e70b7-155">To add task module capabilities to a Virtual Assistant, two additional methods are included in the Virtual Assistant activity handler: `OnTeamsTaskModuleFetchAsync` and `OnTeamsTaskModuleSubmitAsync`.</span></span> <span data-ttu-id="e70b7-156">Esses métodos ouvem atividades relacionadas ao módulo de tarefa do Virtual Assistant, identificam a habilidade associada à solicitação e encaminham a solicitação para a habilidade identificada.</span><span class="sxs-lookup"><span data-stu-id="e70b7-156">These methods listen to task module-related activities from Virtual Assistant, identify the skill associated with the request, and forward the request to the identified skill.</span></span> 

<span data-ttu-id="e70b7-157">O encaminhamento da solicitação é feito através do [Método SkillHttpClient](/dotnet/api/microsoft.bot.builder.integration.aspnet.core.skills.skillhttpclient?view=botbuilder-dotnet-stable&preserve-view=true) `PostActivityAsync` .</span><span class="sxs-lookup"><span data-stu-id="e70b7-157">Request forwarding is done through the [SkillHttpClient](/dotnet/api/microsoft.bot.builder.integration.aspnet.core.skills.skillhttpclient?view=botbuilder-dotnet-stable&preserve-view=true), `PostActivityAsync` method.</span></span> <span data-ttu-id="e70b7-158">Ele retorna a resposta como `InvokeResponse` a qual é analisado e convertido para `TaskModuleResponse` .</span><span class="sxs-lookup"><span data-stu-id="e70b7-158">It returns the response as `InvokeResponse` which is parsed and converted to `TaskModuleResponse` .</span></span>


```csharp
    public static TaskModuleResponse GetTaskModuleRespose(this InvokeResponse invokeResponse)
    {
        if (invokeResponse.Body != null)
        {
            return new TaskModuleResponse()
            {
                Task = GetTask(invokeResponse.Body),
            };
        }

        return null;
    }

    private static TaskModuleResponseBase GetTask(object invokeResponseBody)
        {
            JObject resposeBody = (JObject)JToken.FromObject(invokeResponseBody);
            var task = resposeBody.GetValue("task");
            var taskType = task.SelectToken("type").ToString();

            return taskType switch
            {
                "continue" => new TaskModuleContinueResponse()
                {
                    Type = taskType,
                    Value = task.SelectToken("value").ToObject<TaskModuleTaskInfo>(),
                },
                "message" => new TaskModuleMessageResponse()
                {
                    Type = taskType,
                    Value = task.SelectToken("value").ToString(),
                },
                _ => null,
            };
        }
```

<span data-ttu-id="e70b7-159">Uma abordagem semelhante é seguida para o envio de ação do cartão e respostas do módulo de tarefa.</span><span class="sxs-lookup"><span data-stu-id="e70b7-159">A similar approach is followed for card action dispatching and task module responses.</span></span> <span data-ttu-id="e70b7-160">O módulo de tarefas busca e envio de dados de ação é atualizado para incluir `skillId` .</span><span class="sxs-lookup"><span data-stu-id="e70b7-160">Task module fetch and submit action data is updated to include `skillId`.</span></span> <span data-ttu-id="e70b7-161">O método `GetSkillId` de extensão de atividade extrai `skillId` da carga útil que fornece detalhes sobre a habilidade que precisa ser invocada.</span><span class="sxs-lookup"><span data-stu-id="e70b7-161">Activity Extension method `GetSkillId` extracts `skillId` from the payload which provides details about the skill that needs to be invoked.</span></span>

<span data-ttu-id="e70b7-162">O trecho de código `OnTeamsTaskModuleFetchAsync` e `OnTeamsTaskModuleSubmitAsync` os métodos são dados na seguinte seção:</span><span class="sxs-lookup"><span data-stu-id="e70b7-162">The code snippet for `OnTeamsTaskModuleFetchAsync` and `OnTeamsTaskModuleSubmitAsync` methods are given in the following section:</span></span>

```csharp
    // Invoked when a "task/fetch" event is received to invoke task module.
    protected override async Task<TaskModuleResponse> OnTeamsTaskModuleFetchAsync(ITurnContext<IInvokeActivity> turnContext, TaskModuleRequest taskModuleRequest, CancellationToken cancellationToken)
    {
        try
        {
            string skillId = (turnContext.Activity as Activity).GetSkillId();
            var skill = _skillsConfig.Skills.Where(s => s.Value.AppId == skillId).First().Value;

            // Forward request to correct skill
            var invokeResponse = await _skillHttpClient.PostActivityAsync(this._appId, skill, _skillsConfig.SkillHostEndpoint, turnContext.Activity as Activity, cancellationToken);

            return invokeResponse.GetTaskModuleRespose();
        }
        catch (Exception exception)
        {
            await turnContext.SendActivityAsync(_templateEngine.GenerateActivityForLocale("ErrorMessage"));
            _telemetryClient.TrackException(exception);

            return null;
        }
    }

    // Invoked when a 'task/submit' invoke activity is received for task module submit actions.
    protected override async Task<TaskModuleResponse> OnTeamsTaskModuleSubmitAsync(ITurnContext<IInvokeActivity> turnContext, TaskModuleRequest taskModuleRequest, CancellationToken cancellationToken)
    {
        try
        {
            string skillId = (turnContext.Activity as Activity).GetSkillId();
            var skill = _skillsConfig.Skills.Where(s => s.Value.AppId == skillId).First().Value;

            // Forward request to correct skill
            var invokeResponse = await _skillHttpClient.PostActivityAsync(this._appId, skill, _skillsConfig.SkillHostEndpoint, turnContext.Activity as Activity, cancellationToken).ConfigureAwait(false);

            return invokeResponse.GetTaskModuleRespose();
        }
        catch (Exception exception)
        {
            await turnContext.SendActivityAsync(_templateEngine.GenerateActivityForLocale("ErrorMessage"));
            _telemetryClient.TrackException(exception);

            return null;
        }
    }
```

<span data-ttu-id="e70b7-163">Além disso, você deve incluir todos os domínios de habilidade na `validDomains` seção no arquivo manifesto do Virtual Assistant para que os módulos de tarefa sejam invocados por meio de uma renderização de habilidade corretamente.</span><span class="sxs-lookup"><span data-stu-id="e70b7-163">Additionally, you must include all skill domains in the `validDomains` section in Virtual Assistant's manifest file so that task modules invoked through a skill render properly.</span></span>

### <a name="handle-collaborative-app-scopes"></a><span data-ttu-id="e70b7-164">Lidar com escopos de aplicativos colaborativos</span><span class="sxs-lookup"><span data-stu-id="e70b7-164">Handle collaborative app scopes</span></span>

<span data-ttu-id="e70b7-165">Teams aplicativos podem existir em vários escopos, incluindo bate-papo 1:1, bate-papo em grupo e canais.</span><span class="sxs-lookup"><span data-stu-id="e70b7-165">Teams apps can exist in multiple scopes including 1:1 chat, group chat, and channels.</span></span> <span data-ttu-id="e70b7-166">O modelo principal do Assistente Virtual foi projetado para bate-papos 1:1.</span><span class="sxs-lookup"><span data-stu-id="e70b7-166">The core Virtual Assistant template is designed for 1:1 chats.</span></span> <span data-ttu-id="e70b7-167">Como parte da experiência de onboarding, o Virtual Assistant solicita nome aos usuários e mantém o estado do usuário.</span><span class="sxs-lookup"><span data-stu-id="e70b7-167">As part of the onboarding experience Virtual Assistant prompts users for name and maintains user state.</span></span> <span data-ttu-id="e70b7-168">Uma vez que essa experiência de onboarding não é adequada para o bate-papo em grupo ou escopos de canal, ele foi removido.</span><span class="sxs-lookup"><span data-stu-id="e70b7-168">Since that onboarding experience is not suited for group chat or channel scopes it has been removed.</span></span>

<span data-ttu-id="e70b7-169">As habilidades devem lidar com atividades em vários escopos, como bate-papo 1:1, bate-papo em grupo e conversa de canal.</span><span class="sxs-lookup"><span data-stu-id="e70b7-169">Skills should handle activities in multiple scopes, such as 1:1 chat, group chat, and channel conversation.</span></span> <span data-ttu-id="e70b7-170">Se algum desses escopos não for suportado, as habilidades devem responder com uma mensagem apropriada.</span><span class="sxs-lookup"><span data-stu-id="e70b7-170">If any of these scopes are not supported, skills must respond with an appropriate message.</span></span>

<span data-ttu-id="e70b7-171">As seguintes funções de processamento foram adicionadas ao núcleo do Assistente Virtual:</span><span class="sxs-lookup"><span data-stu-id="e70b7-171">The following  processing functions have been added to Virtual Assistant core:</span></span>

* <span data-ttu-id="e70b7-172">O Assistente Virtual pode ser invocado sem qualquer mensagem de texto de um chat ou canal em grupo.</span><span class="sxs-lookup"><span data-stu-id="e70b7-172">Virtual Assistant can be invoked without any text message from a group chat or channel.</span></span>
* <span data-ttu-id="e70b7-173">As articulações são limpas antes de enviar a mensagem para o módulo de despacho.</span><span class="sxs-lookup"><span data-stu-id="e70b7-173">Articulations are cleaned before sending the message to the dispatch module.</span></span> <span data-ttu-id="e70b7-174">Por exemplo, remova as @mention necessárias do bot.</span><span class="sxs-lookup"><span data-stu-id="e70b7-174">For example, remove the necessary @mention of the bot.</span></span>

```csharp
    if (innerDc.Context.Activity.Conversation?.IsGroup == true)
    {
        // Remove bot atmentions for teams/groupchat scope
        innerDc.Context.Activity.RemoveRecipientMention();

        // If bot is invoked without any text, reply with FirstPromptMessage
        if (string.IsNullOrWhiteSpace(innerDc.Context.Activity.Text))
        {
            await innerDc.Context.SendActivityAsync(_templateEngine.GenerateActivityForLocale("FirstPromptMessage"));
            return EndOfTurn;
        }
    }
```

### <a name="handle-messaging-extensions"></a><span data-ttu-id="e70b7-175">Manuseie extensões de mensagens</span><span class="sxs-lookup"><span data-stu-id="e70b7-175">Handle messaging extensions</span></span>

<span data-ttu-id="e70b7-176">Os comandos para uma extensão de mensagens são declarados no arquivo manifesto do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="e70b7-176">The commands for a messaging extension are declared in your app manifest file.</span></span> <span data-ttu-id="e70b7-177">A interface do usuário de extensão de mensagens é alimentada por esses comandos.</span><span class="sxs-lookup"><span data-stu-id="e70b7-177">The messaging extension user interface is powered by those commands.</span></span> <span data-ttu-id="e70b7-178">Para um Assistente Virtual alimentar um comando de extensão de mensagens como uma habilidade anexada, o próprio manifesto de um assistente virtual deve conter esses comandos.</span><span class="sxs-lookup"><span data-stu-id="e70b7-178">For a Virtual Assistant to power a messaging extension command as an attached skill, a Virtual Assistant's own manifest must contain those commands.</span></span> <span data-ttu-id="e70b7-179">Você deve adicionar os comandos de um manifesto de habilidade individual ao manifesto do Assistente Virtual.</span><span class="sxs-lookup"><span data-stu-id="e70b7-179">You must add the commands from an individual skill's manifest to the Virtual Assistant's manifest.</span></span> <span data-ttu-id="e70b7-180">O ID de comando fornece informações sobre uma habilidade associada, anexando o ID do aplicativo da habilidade através de um separador `:` .</span><span class="sxs-lookup"><span data-stu-id="e70b7-180">The command ID provides information about an associated skill by appending the skill's app ID through a separator `:`.</span></span>

<span data-ttu-id="e70b7-181">O trecho do arquivo manifesto de uma habilidade é mostrado na seguinte seção:</span><span class="sxs-lookup"><span data-stu-id="e70b7-181">The snippet from a skill's manifest file is shown in the following section:</span></span>

```json
 "composeExtensions": [
    {
        "botId": "<Skil_App_Id>",
        "commands": [
            {
                "id": "searchQuery",
                "context": [ "compose", "commandBox" ],
                "description": "Test command to run query",
    ....
```

<span data-ttu-id="e70b7-182">O trecho de código de arquivo de manifesto do Assistente Virtual correspondente é mostrado na seguinte seção:</span><span class="sxs-lookup"><span data-stu-id="e70b7-182">The corresponding Virtual Assistant manifest file code snippet is shown in the following section:</span></span>

```json
 "composeExtensions": [
    {
        "botId": "<VA_App_Id>",
        "commands": [
            {
                "id": "searchQuery:<skill_id>",
                "context": [ "compose", "commandBox" ],
                "description": "Test command to run query",
    ....
```

<span data-ttu-id="e70b7-183">Uma vez que os comandos são invocados por um usuário, o Assistente Virtual pode identificar uma habilidade associada analisando o ID de comando, atualizar a atividade removendo o sufixo extra `:<skill_id>` do ID de comando e encaminhá-lo para a habilidade correspondente.</span><span class="sxs-lookup"><span data-stu-id="e70b7-183">Once the commands are invoked by a user, the Virtual Assistant can identify an associated skill by parsing the command ID, update the activity by removing the extra suffix `:<skill_id>` from the command ID,  and forward it to the corresponding skill.</span></span> <span data-ttu-id="e70b7-184">O código para uma habilidade não precisa lidar com o sufixo extra.</span><span class="sxs-lookup"><span data-stu-id="e70b7-184">The code for a skill doesnot need to handle the extra suffix.</span></span> <span data-ttu-id="e70b7-185">Assim, os conflitos entre as IDs de comando através de habilidades são evitados.</span><span class="sxs-lookup"><span data-stu-id="e70b7-185">Thus, conflicts between command IDs across skills are avoided.</span></span> <span data-ttu-id="e70b7-186">Com essa abordagem, todos os comandos de busca e ação de uma habilidade dentro de todos os contextos, como **compor,** **commandBox** e **mensagem** são alimentados por um Assistente Virtual.</span><span class="sxs-lookup"><span data-stu-id="e70b7-186">With this approach, all the search and action commands of a skill within all contexts, such as **compose**, **commandBox**, and **message** are powered by a Virtual Assistant.</span></span>

```csharp
    const string MessagingExtensionCommandIdSeparator = ":";

    // Invoked when a 'composeExtension/submitAction' invoke activity is received for a messaging extension action command
    protected override async Task<MessagingExtensionActionResponse> OnTeamsMessagingExtensionSubmitActionAsync(ITurnContext<IInvokeActivity> turnContext, MessagingExtensionAction action, CancellationToken cancellationToken)
    {
        return await ForwardMessagingExtensionActionCommandActivityToSkill(turnContext, action, cancellationToken);
    }

    // Forwards invoke activity to right skill for messaging extension action commands.
    private async Task<MessagingExtensionActionResponse> ForwardMessagingExtensionActionCommandActivityToSkill(ITurnContext<IInvokeActivity> turnContext, MessagingExtensionAction action, CancellationToken cancellationToken)
    {
        var skillId = ExtractSkillIdFromMessagingExtensionActionCommand(turnContext, action);
        var skill = _skillsConfig.Skills.Where(s => s.Value.AppId == skillId).First().Value;
        var invokeResponse = await _skillHttpClient.PostActivityAsync(this._appId, skill, _skillsConfig.SkillHostEndpoint, turnContext.Activity as Activity, cancellationToken).ConfigureAwait(false);

        return invokeResponse.GetMessagingExtensionActionResponse();
    }

    // Extracts skill Id from messaging extension command and updates activity value
    private string ExtractSkillIdFromMessagingExtensionActionCommand(ITurnContext<IInvokeActivity> turnContext, MessagingExtensionAction action)
    {
        var commandArray = action.CommandId.Split(MessagingExtensionCommandIdSeparator);
        var skillId = commandArray.Last();

        // Update activity value by removing skill id before forwarding to the skill.
        var activityValue = JsonConvert.DeserializeObject<MessagingExtensionAction>(turnContext.Activity.Value.ToString());
        activityValue.CommandId = string.Join(MessagingExtensionCommandIdSeparator, commandArray, 0 commandArray.Length - 1);
        turnContext.Activity.Value = activityValue;

        return skillId;
    }
```

<span data-ttu-id="e70b7-187">Algumas atividades de extensão de mensagens não incluem o ID de comando.</span><span class="sxs-lookup"><span data-stu-id="e70b7-187">Some messaging extension activities do not include the command ID.</span></span> <span data-ttu-id="e70b7-188">Por exemplo, `composeExtension/selectItem` contém apenas o valor da ação de toque de invocação.</span><span class="sxs-lookup"><span data-stu-id="e70b7-188">For example, `composeExtension/selectItem` contains only the value of the invoke tap action.</span></span> <span data-ttu-id="e70b7-189">Para identificar a habilidade associada, `skillId`  é anexado a cada cartão de item enquanto forma uma resposta para `OnTeamsMessagingExtensionQueryAsync` .</span><span class="sxs-lookup"><span data-stu-id="e70b7-189">To identify the associated skill, `skillId`  is attached to each item card while forming a response for `OnTeamsMessagingExtensionQueryAsync`.</span></span> <span data-ttu-id="e70b7-190">Isso é semelhante à abordagem para [adicionar cartões adaptativos ao seu Assistente Virtual](#add-adaptive-cards-to-your-virtual-assistant).</span><span class="sxs-lookup"><span data-stu-id="e70b7-190">This is similar to the approach for [adding adaptive  cards to your Virtual Assistant](#add-adaptive-cards-to-your-virtual-assistant).</span></span>

```csharp
    // Invoked when a 'composeExtension/selectItem' invoke activity is received for compose extension query command.
    protected override async Task<MessagingExtensionResponse> OnTeamsMessagingExtensionSelectItemAsync(ITurnContext<IInvokeActivity> turnContext, JObject query, CancellationToken cancellationToken)
    {
        var data = JsonConvert.DeserializeObject<SkillCardActionData>(query.ToString());
        var skill = _skillsConfig.Skills.Where(s => s.Value.AppId == data.SkillId).First().Value;
        var invokeResponse = await _skillHttpClient.PostActivityAsync(this._appId, skill, _skillsConfig.SkillHostEndpoint, turnContext.Activity as Activity, cancellationToken).ConfigureAwait(false);

        return invokeResponse.GetMessagingExtensionResponse();
    }
```

---

## <a name="example"></a><span data-ttu-id="e70b7-191">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e70b7-191">Example</span></span>

<span data-ttu-id="e70b7-192">O exemplo a seguir mostra como converter o modelo de aplicativo Book-a-room para uma habilidade de Assistente Virtual: Book-a-room é uma Microsoft Teams que permite aos usuários encontrar e reservar rapidamente uma sala de reunião por 30, 60 ou 90 minutos a partir do momento atual.</span><span class="sxs-lookup"><span data-stu-id="e70b7-192">The following example shows how to convert the Book-a-room app template to a Virtual Assistant skill: Book-a-room is a Microsoft Teams that allows users quickly to find and reserve a meeting room for 30, 60, or 90 minutes starting from the current time.</span></span> <span data-ttu-id="e70b7-193">O tempo padrão é de 30 minutos.</span><span class="sxs-lookup"><span data-stu-id="e70b7-193">The default time is 30 minutes.</span></span> <span data-ttu-id="e70b7-194">Os escopos do robô Book-a-room para conversas pessoais ou 1:1.</span><span class="sxs-lookup"><span data-stu-id="e70b7-194">The Book-a-room bot scopes to personal or 1:1 conversations.</span></span> <span data-ttu-id="e70b7-195">A imagem a seguir exibe um Assistente Virtual com um livro uma habilidade **de quarto:**</span><span class="sxs-lookup"><span data-stu-id="e70b7-195">The following image displays a Virtual Assistant with a **book a room** skill:</span></span>

![Assistente Virtual com uma habilidade de "reservar um quarto"](../assets/images/bots/virtual-assistant/book-a-room-skill.png)

<span data-ttu-id="e70b7-197">A seguir estão as alterações delta introduzidas para convertê-lo em uma habilidade que é anexada a um Assistente Virtual.</span><span class="sxs-lookup"><span data-stu-id="e70b7-197">Followings are the delta changes introduced to convert it to a skill which is attached to a Virtual Assistant.</span></span> <span data-ttu-id="e70b7-198">Diretrizes semelhantes são seguidas para converter qualquer bot v4 existente em uma habilidade.</span><span class="sxs-lookup"><span data-stu-id="e70b7-198">Similar guidelines are followed to convert any existing v4 bot to a skill.</span></span>

### <a name="skill-manifest"></a><span data-ttu-id="e70b7-199">Manifesto de habilidades</span><span class="sxs-lookup"><span data-stu-id="e70b7-199">Skill manifest</span></span>

<span data-ttu-id="e70b7-200">Um manifesto de habilidade é um arquivo JSON que expõe o ponto final de mensagens de uma habilidade, ID, nome e outros metadados relevantes.</span><span class="sxs-lookup"><span data-stu-id="e70b7-200">A skill manifest is a JSON file that exposes a skill's messaging endpoint, ID, name, and other relevant metadata.</span></span> <span data-ttu-id="e70b7-201">Este manifesto é diferente do manifesto usado para carregar um aplicativo em Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="e70b7-201">This manifest is different than the manifest used for sideloading an app in Microsoft Teams.</span></span> <span data-ttu-id="e70b7-202">Um Assistente Virtual requer um caminho para este arquivo como uma entrada para anexar uma habilidade.</span><span class="sxs-lookup"><span data-stu-id="e70b7-202">A Virtual Assistant requires a path to this file as an input to attach a skill.</span></span> <span data-ttu-id="e70b7-203">Adicionamos o seguinte manifesto à pasta wwwroot do bot.</span><span class="sxs-lookup"><span data-stu-id="e70b7-203">We have added the following manifest to the bot's wwwroot folder.</span></span>

```bash
botskills connect --remoteManifest "<url to skill's manifest>" ..
```

```json
{
  "$schema": "https://schemas.botframework.com/schemas/skills/skill-manifest-2.1.preview-0.json",
  "$id": "microsoft_teams_apps_bookaroom",
  "name": "microsoft-teams-apps-bookaroom",
  "description": "microsoft-teams-apps-bookaroom description",
  "publisherName": "Your Company",
  "version": "1.1",
  "iconUrl": "<icon url>",
  "copyright": "Copyright (c) Microsoft Corporation. All rights reserved.",
  "license": "",
  "privacyUrl": "<privacy url>",
  "endpoints": [
    {
      "name": "production",
      "protocol": "BotFrameworkV3",
      "description": "Production endpoint for the skill",
      "endpointUrl": "<endpoint url>",
      "msAppId": "skill app id"
    }
  ],
  "dispatchModels": {
    "languages": {
      "en-us": [
        {
          "id": "microsoft-teams-apps-bookaroom-en",
          "name": "microsoft-teams-apps-bookaroom LU (English)",
          "contentType": "application/lu",
          "url": "file://book-a-meeting.lu",
          "description": "English language model for the skill"
        }
      ]
    }
  },
  "activities": {
    "message": {
      "type": "message",
      "description": "Receives the users utterance and attempts to resolve it using the skill's LU models"
    }
  }
}
```

### <a name="luis-integration"></a><span data-ttu-id="e70b7-204">Integração LUIS</span><span class="sxs-lookup"><span data-stu-id="e70b7-204">LUIS Integration</span></span>

<span data-ttu-id="e70b7-205">O modelo de despacho do Virtual Assistant é construído em cima dos modelos LUIS de habilidades anexadas.</span><span class="sxs-lookup"><span data-stu-id="e70b7-205">Virtual Assistant's dispatch model is built on top of attached skills' LUIS models.</span></span> <span data-ttu-id="e70b7-206">O modelo de despacho identifica a intenção para cada atividade de texto e descobre a habilidade associada a ela.</span><span class="sxs-lookup"><span data-stu-id="e70b7-206">The dispatch model identifies the intent for every text activity and finds out skill associated with it.</span></span>

<span data-ttu-id="e70b7-207">O Assistente Virtual requer o modelo LUIS da habilidade em `.lu` formato como uma entrada ao anexar uma habilidade.</span><span class="sxs-lookup"><span data-stu-id="e70b7-207">Virtual Assistant requires skill's LUIS model in `.lu` format as an input while attaching a skill.</span></span> <span data-ttu-id="e70b7-208">LUIS json é convertido em `.lu` formato usando a ferramenta botframework-cli.</span><span class="sxs-lookup"><span data-stu-id="e70b7-208">LUIS json is converted to `.lu` format using botframework-cli  tool.</span></span>

```json
botskills connect --remoteManifest "<url to skill's manifest>" --luisFolder "<path to the folder containing your Skill's .lu files>" --languages "en-us" --cs
```

```bash
npm i -g @microsoft/botframework-cli
bf luis:convert --in <pathToLUIS.json> --out <pathToLuFile>
```

<span data-ttu-id="e70b7-209">O bot book-a-room tem dois comandos principais para os usuários:</span><span class="sxs-lookup"><span data-stu-id="e70b7-209">Book-a-room bot has two main commands for users:</span></span>

- `Book room`
- `Manage Favorites`

<span data-ttu-id="e70b7-210">Construímos um modelo LUIS entendendo esses dois comandos.</span><span class="sxs-lookup"><span data-stu-id="e70b7-210">We have built a LUIS model by understanding these two commands.</span></span> <span data-ttu-id="e70b7-211">Os segredos correspondentes devem ser preenchidos em `cognitivemodels.json` .</span><span class="sxs-lookup"><span data-stu-id="e70b7-211">Corresponding secrets must be populated in `cognitivemodels.json`.</span></span> <span data-ttu-id="e70b7-212">O arquivo LUIS JSON correspondente é encontrado [aqui](https://github.com/OfficeDev/microsoft-teams-apps-bookaroom/blob/nebhagat/microsoft-teams-apps-bookaroom-skill/Deployment/Resources/LU/book-a-meeting.json).</span><span class="sxs-lookup"><span data-stu-id="e70b7-212">The corresponding LUIS JSON file is found [here](https://github.com/OfficeDev/microsoft-teams-apps-bookaroom/blob/nebhagat/microsoft-teams-apps-bookaroom-skill/Deployment/Resources/LU/book-a-meeting.json).</span></span>
<span data-ttu-id="e70b7-213">O arquivo correspondente `.lu` é mostrado na seguinte seção:</span><span class="sxs-lookup"><span data-stu-id="e70b7-213">The corresponding `.lu` file is shown in the following section:</span></span>

```
> ! Automatically generated by [LUDown CLI](https://github.com/Microsoft/botbuilder-tools/tree/master/Ludown), Tue Mar 31 2020 17:30:32 GMT+0530 (India Standard Time)

> ! Source LUIS JSON file: book-a-meeting.json

> ! Source QnA TSV file: Not Specified

> ! Source QnA Alterations file: Not Specified


> # Intent definitions

## BOOK ROOM
- book a room
- book room
- please book a room
- reserve a room
- i want to book a room
- i want to book a room please
- get me a room please
- get me a room


## MANAGE FAVORITES
- manage favorites
- manage favorite
- please manage my favorite rooms
- manage my favorite rooms please
- manage my favorite rooms
- i want to manage my favorite rooms

## None


> # Entity definitions


> # PREBUILT Entity definitions


> # Phrase list definitions


> # List entities

> # RegEx entities
```

<span data-ttu-id="e70b7-214">Com essa abordagem, qualquer comando emitido por um usuário para Assistente Virtual relacionado `book room` ou é identificado como um comando associado ao bot e é encaminhado para essa `manage favorites` `Book-a-room` habilidade.</span><span class="sxs-lookup"><span data-stu-id="e70b7-214">With this approach, any command issued by a user to Virtual Assistant related to `book room` or `manage favorites` are identified as a command associated with `Book-a-room` bot and is forwarded to this skill.</span></span>
<span data-ttu-id="e70b7-215">Por outro lado, o bot precisa usar o `Book-a-room room` modelo LUIS para entender esses comandos se eles não estiverem digitado completos.</span><span class="sxs-lookup"><span data-stu-id="e70b7-215">On the other hand, `Book-a-room room` bot needs to use LUIS model to understand these commands if they are not typed full.</span></span> <span data-ttu-id="e70b7-216">Por exemplo: `I want to manage my favorite rooms`.</span><span class="sxs-lookup"><span data-stu-id="e70b7-216">For example: `I want to manage my favorite rooms`.</span></span>

### <a name="multi-language-support"></a><span data-ttu-id="e70b7-217">Suporte multi-idioma</span><span class="sxs-lookup"><span data-stu-id="e70b7-217">Multi-Language support</span></span>

<span data-ttu-id="e70b7-218">Como exemplo, um modelo LUIS com apenas cultura inglesa é criado.</span><span class="sxs-lookup"><span data-stu-id="e70b7-218">As an example, a LUIS model with only English culture is created.</span></span> <span data-ttu-id="e70b7-219">Você pode criar modelos LUIS correspondentes a outros idiomas e adicionar entrada a `cognitivemodels.json` .</span><span class="sxs-lookup"><span data-stu-id="e70b7-219">You can create LUIS models corresponding to other languages and add entry to `cognitivemodels.json`.</span></span>

```json
{
  "defaultLocale": "en-us",
  "languageModels": {
    "en-us": {
      "luisAppId": "",
      "luisApiKey": "",
      "luisApiHost": ""
    },
    "<your_language_culture>": {
      "luisAppId": "",
      "luisApiKey": "",
      "luisApiHost": ""
    }
  }
}
```

<span data-ttu-id="e70b7-220">Em paralelo, adicione o arquivo correspondente `.lu` no caminho luisPato.</span><span class="sxs-lookup"><span data-stu-id="e70b7-220">In parallel, add corresponding `.lu` file in luisFolder path.</span></span> <span data-ttu-id="e70b7-221">A estrutura da pasta deve ser a seguinte:</span><span class="sxs-lookup"><span data-stu-id="e70b7-221">Folder structure should be as follows:</span></span>

```bash
| - luisFolder

        | - en-us

                | - book-a-meeting.lu

        | - your_language_culture

                | - book-a-meeting.lu
```

<span data-ttu-id="e70b7-222">Para modificar `languages` o parâmetro, atualize o comando botskills da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="e70b7-222">To modify `languages` parameter, update botskills command as follows:</span></span>

```json
botskills connect --remoteManifest "<url to skill's manifest>" --luisFolder "<path to luisFolder>" --languages "en-us, your_language_culture" --cs
```

<span data-ttu-id="e70b7-223">O Virtual Assistant usa `SetLocaleMiddleware` para identificar o local atual e invocar o modelo de despacho correspondente.</span><span class="sxs-lookup"><span data-stu-id="e70b7-223">Virtual Assistant uses `SetLocaleMiddleware` to identify current locale and invoke corresponding dispatch model.</span></span> <span data-ttu-id="e70b7-224">A atividade de estrutura de bot tem campo de localização que é usado por este middleware.</span><span class="sxs-lookup"><span data-stu-id="e70b7-224">Bot framework activity has locale field which is used by this middleware.</span></span> <span data-ttu-id="e70b7-225">Você pode usar o mesmo para sua habilidade também.</span><span class="sxs-lookup"><span data-stu-id="e70b7-225">You can use the same for your skill as well.</span></span> <span data-ttu-id="e70b7-226">O bot book-a-room não usa este middleware e, em vez disso, obtém locale da [entidade clienteInfo](https://github.com/microsoft/botframework-sdk/blob/master/specs/botframework-activity/botframework-activity.md#clientinfo)da empresa de framework Bot .</span><span class="sxs-lookup"><span data-stu-id="e70b7-226">Book-a-room bot does not use this middleware and instead gets locale from Bot framework activity's [clientInfo entity](https://github.com/microsoft/botframework-sdk/blob/master/specs/botframework-activity/botframework-activity.md#clientinfo).</span></span>

### <a name="claim-validation"></a><span data-ttu-id="e70b7-227">Validação de reivindicações</span><span class="sxs-lookup"><span data-stu-id="e70b7-227">Claim validation</span></span>

<span data-ttu-id="e70b7-228">Adicionamos [reivindicaçõesValidator](https://github.com/nebhagat/msteams-virtual-assistant-dotnet/blob/master/msteams-virtual-assistant-dotnet/Authentication/AllowedCallersClaimsValidator.cs) para restringir os chamadores à habilidade.</span><span class="sxs-lookup"><span data-stu-id="e70b7-228">We have added [claimsValidator](https://github.com/nebhagat/msteams-virtual-assistant-dotnet/blob/master/msteams-virtual-assistant-dotnet/Authentication/AllowedCallersClaimsValidator.cs) to restrict callers to the skill.</span></span> <span data-ttu-id="e70b7-229">Para permitir que um Assistente Virtual chame essa habilidade, preencha `AllowedCallers` a matriz com o `appsettings` ID do aplicativo do Virtual Assistant em particular.</span><span class="sxs-lookup"><span data-stu-id="e70b7-229">To allow a Virtual Assistant to call this skill, populate `AllowedCallers` array from `appsettings` with that particular Virtual Assistant's app ID.</span></span>

```
"AllowedCallers": [ "<caller_VA1_appId>", "<caller_VA2_appId>" ],
```

<span data-ttu-id="e70b7-230">O array de chamadores permitido pode restringir qual habilidade os consumidores podem acessar a habilidade.</span><span class="sxs-lookup"><span data-stu-id="e70b7-230">The allowed callers array can restrict which skill consumers can access the skill.</span></span> <span data-ttu-id="e70b7-231">Adicione uma única entrada `*` a esta matriz, para aceitar chamadas de qualquer consumidor de habilidade.</span><span class="sxs-lookup"><span data-stu-id="e70b7-231">Add single entry `*` to this array, to accept calls from any skill consumer.</span></span>

```
"AllowedCallers": [ "*" ],
```

<span data-ttu-id="e70b7-232">Para obter mais informações sobre a adição de validação de sinistros a uma habilidade, consulte [adicionar validação de sinistros à habilidade](/azure/bot-service/skill-implement-skill?view=azure-bot-service-4.0&tabs=cs#claims-validator&preserve-view=true).</span><span class="sxs-lookup"><span data-stu-id="e70b7-232">For more information on adding claims validation to a skill, see [add claims validation to skill](/azure/bot-service/skill-implement-skill?view=azure-bot-service-4.0&tabs=cs#claims-validator&preserve-view=true).</span></span>

### <a name="limitation-of-card-refresh"></a><span data-ttu-id="e70b7-233">Limitação da atualização do cartão</span><span class="sxs-lookup"><span data-stu-id="e70b7-233">Limitation of card refresh</span></span> 

<span data-ttu-id="e70b7-234">A atualização da atividade, como a atualização do cartão, ainda não é suportada através do Virtual Assistant[(problema do github).](https://github.com/microsoft/botbuilder-dotnet/issues/3686)</span><span class="sxs-lookup"><span data-stu-id="e70b7-234">Updating activity, such as card refresh is not supported yet through Virtual Assistant ([github issue](https://github.com/microsoft/botbuilder-dotnet/issues/3686)).</span></span> <span data-ttu-id="e70b7-235">Por isso, substituímos todas as chamadas de atualização `UpdateActivityAsync` de cartões com a postagem de novas chamadas de cartão `SendActivityAsync` .</span><span class="sxs-lookup"><span data-stu-id="e70b7-235">Hence, we have replaced all card refresh calls `UpdateActivityAsync` with posting new card calls `SendActivityAsync`.</span></span>

### <a name="card-actions-and-task-module-flows"></a><span data-ttu-id="e70b7-236">Ações de cartão e fluxos de módulos de tarefa</span><span class="sxs-lookup"><span data-stu-id="e70b7-236">Card actions and task module flows</span></span>

<span data-ttu-id="e70b7-237">Para encaminhar as atividades de ação de cartão ou módulo de tarefa para uma habilidade associada, a habilidade deve `skillId` incorporá-la.</span><span class="sxs-lookup"><span data-stu-id="e70b7-237">To forward card action or task module activities to an associated skill, the skill must embed `skillId` to it.</span></span>
<span data-ttu-id="e70b7-238">`Book-a-room` ação do cartão de bot, a busca do módulo de tarefa e o envio de cargas de ação são modificados para conter `skillId` como parâmetro.</span><span class="sxs-lookup"><span data-stu-id="e70b7-238">`Book-a-room` bot card action, task module fetch and submit action payloads are modified to contain `skillId` as a parameter.</span></span> 

<span data-ttu-id="e70b7-239">Para obter mais informações, consulte [esta](https://msteams-captain.visualstudio.com/xGrowth%20App%20Templates/_wiki/wikis/xGrowth.wiki/88/Virtual-Assistant-for-MS-Teams?anchor=rich-cards) seção a partir desta documentação.</span><span class="sxs-lookup"><span data-stu-id="e70b7-239">For more information refer [this](https://msteams-captain.visualstudio.com/xGrowth%20App%20Templates/_wiki/wikis/xGrowth.wiki/88/Virtual-Assistant-for-MS-Teams?anchor=rich-cards) section from this documentation.</span></span>

### <a name="handle-activities-from-group-chat-or-channel-scope"></a><span data-ttu-id="e70b7-240">Lidar com atividades a partir de bate-papo em grupo ou escopo de canal</span><span class="sxs-lookup"><span data-stu-id="e70b7-240">Handle activities from group chat or channel scope</span></span>

<span data-ttu-id="e70b7-241">`Book-a-room bot` é projetado para chats privados, como apenas escopo pessoal ou 1:1.</span><span class="sxs-lookup"><span data-stu-id="e70b7-241">`Book-a-room bot` is designed for private chats, such as personal or 1:1 scope only.</span></span> <span data-ttu-id="e70b7-242">Como temos o Assistente Virtual personalizado para apoiar o chat em grupo e os escopos do canal, o Assistente Virtual deve ser invocado a partir dos escopos do canal e, portanto, `Book-a-room` o bot deve obter atividades para o mesmo escopo.</span><span class="sxs-lookup"><span data-stu-id="e70b7-242">Since we have customized Virtual Assistant to support group chat and channel scopes, the Virtual Assistant must be invoked from the channel scopes and thus, `Book-a-room` bot must get activities for the same scope.</span></span> <span data-ttu-id="e70b7-243">Portanto, `Book-a-room` o bot é personalizado para lidar com essas atividades.</span><span class="sxs-lookup"><span data-stu-id="e70b7-243">Hence `Book-a-room`bot is customized to handle those activities.</span></span> <span data-ttu-id="e70b7-244">Você pode encontrar os métodos de check-in `OnMessageActivityAsync` do manipulador de `Book-a-room` atividades do bot.</span><span class="sxs-lookup"><span data-stu-id="e70b7-244">You can find the check in `OnMessageActivityAsync` methods of `Book-a-room` bot's activity handler.</span></span>

```csharp
    protected override async Task OnMessageActivityAsync(ITurnContext<IMessageActivity> turnContext, CancellationToken cancellationToken)
    {
        // Check if activities are from groupchat/ teams scope. This might happen when the bot is consumed by Virtual Assistant.
        if (turnContext.Activity.Conversation.IsGroup == true)
        {
            await ShowNotSupportedInGroupChatCardAsync(turnContext).ConfigureAwait(false);
        }
        else
        {
            ...
        }
    }
```

<span data-ttu-id="e70b7-245">Você também pode aproveitar as habilidades existentes do [repositório de Soluções de Estrutura de Bot](https://github.com/microsoft/botframework-solutions/tree/master/skills/csharp) ou criar uma nova habilidade completamente do zero.</span><span class="sxs-lookup"><span data-stu-id="e70b7-245">You can also leverage existing skills from [Bot Framework Solutions repository](https://github.com/microsoft/botframework-solutions/tree/master/skills/csharp) or create a new skill altogether from scratch.</span></span> <span data-ttu-id="e70b7-246">Para criar uma nova habilidade, consulte [tutoriais para criar uma nova habilidade](https://microsoft.github.io/botframework-solutions/overview/skills/).</span><span class="sxs-lookup"><span data-stu-id="e70b7-246">For creating a new skill, see [tutorials to create a new skill](https://microsoft.github.io/botframework-solutions/overview/skills/).</span></span> <span data-ttu-id="e70b7-247">Para assistente virtual e documentação de arquitetura de habilidades, consulte[Assistente Virtual e arquitetura de habilidades](/azure/bot-service/skills-conceptual?view=azure-bot-service-4.0&preserve-view=true).</span><span class="sxs-lookup"><span data-stu-id="e70b7-247">For Virtual Assistant and skills architecture documentation, see[Virtual Assistant and skills architecture](/azure/bot-service/skills-conceptual?view=azure-bot-service-4.0&preserve-view=true).</span></span>  

## <a name="limitations-of-virtual-assistant"></a><span data-ttu-id="e70b7-248">Limitações do Assistente Virtual</span><span class="sxs-lookup"><span data-stu-id="e70b7-248">Limitations of Virtual Assistant</span></span> 

* <span data-ttu-id="e70b7-249">**EndOfConversation**: Uma habilidade deve enviar uma `endOfConversation` atividade quando terminar uma conversa.</span><span class="sxs-lookup"><span data-stu-id="e70b7-249">**EndOfConversation**: A skill must send an `endOfConversation` activity when it finishes a conversation.</span></span> <span data-ttu-id="e70b7-250">Com base na atividade, um Assistente Virtual termina o contexto com essa habilidade particular e volta ao contexto raiz do Virtual Assistant.</span><span class="sxs-lookup"><span data-stu-id="e70b7-250">Based on the activity, a Virtual Assistant ends context with that particular skill and gets back into Virtual Assistant's root context.</span></span> <span data-ttu-id="e70b7-251">Para o robô Book-a-room, não há um estado claro onde a conversa é encerrada.</span><span class="sxs-lookup"><span data-stu-id="e70b7-251">For Book-a-room bot, there is no clear state where conversation is ended.</span></span> <span data-ttu-id="e70b7-252">Portanto, não enviamos `endOfConversation` do bot e quando o usuário quer voltar ao contexto raiz eles podem `Book-a-room` simplesmente fazer isso por `start over` comando.</span><span class="sxs-lookup"><span data-stu-id="e70b7-252">Hence we have not sent `endOfConversation` from `Book-a-room` bot and when user wants to go back to root context they can simply do that by `start over` command.</span></span>  
* <span data-ttu-id="e70b7-253">**Atualização do** cartão : A atualização do cartão ainda não é suportada através do Virtual Assistant.</span><span class="sxs-lookup"><span data-stu-id="e70b7-253">**Card refresh**: Card refresh is not yet supported through Virtual Assistant.</span></span>  
* <span data-ttu-id="e70b7-254">**Extensões de mensagens:**</span><span class="sxs-lookup"><span data-stu-id="e70b7-254">**Messaging extensions**:</span></span>
  * <span data-ttu-id="e70b7-255">Atualmente, um Assistente Virtual pode suportar no máximo dez comandos para extensões de mensagens.</span><span class="sxs-lookup"><span data-stu-id="e70b7-255">Currently, a Virtual Assistant can support a maximum of ten commands for messaging extensions.</span></span>
  * <span data-ttu-id="e70b7-256">A configuração das extensões de mensagens não é escopo para comandos individuais, mas para toda a extensão em si.</span><span class="sxs-lookup"><span data-stu-id="e70b7-256">Configuration of messaging extensions is not scoped to individual commands but for the entire extension itself.</span></span> <span data-ttu-id="e70b7-257">Isso limita a configuração de cada habilidade individual através do Virtual Assistant.</span><span class="sxs-lookup"><span data-stu-id="e70b7-257">This limits configuration for each individual skill through Virtual Assistant.</span></span>
  * <span data-ttu-id="e70b7-258">As IDs de comando de extensões de mensagens têm um comprimento máximo de [64 caracteres](../resources/schema/manifest-schema.md#composeextensions) e 37 caracteres são usados para incorporar informações de habilidade.</span><span class="sxs-lookup"><span data-stu-id="e70b7-258">Messaging extensions command IDs have a maximum length of [64 characters](../resources/schema/manifest-schema.md#composeextensions) and 37 characters are used for embedding skill information.</span></span> <span data-ttu-id="e70b7-259">Assim, as restrições atualizadas para o ID de comando são limitadas a 27 caracteres.</span><span class="sxs-lookup"><span data-stu-id="e70b7-259">Thus, updated constraints for command ID are limited to 27 characters.</span></span>

<span data-ttu-id="e70b7-260">Você também pode aproveitar as habilidades existentes do [repositório de Soluções de Estrutura de Bot](https://github.com/microsoft/botframework-solutions/tree/master/skills/csharp) ou criar uma nova habilidade completamente do zero.</span><span class="sxs-lookup"><span data-stu-id="e70b7-260">You can also leverage existing skills from [Bot Framework Solutions repository](https://github.com/microsoft/botframework-solutions/tree/master/skills/csharp) or create a new skill altogether from scratch.</span></span> <span data-ttu-id="e70b7-261">Tutoriais para o mais tarde podem ser encontrados [aqui](https://microsoft.github.io/botframework-solutions/overview/skills/).</span><span class="sxs-lookup"><span data-stu-id="e70b7-261">Tutorials for the later can be found [here](https://microsoft.github.io/botframework-solutions/overview/skills/).</span></span> <span data-ttu-id="e70b7-262">Consulte a [documentação](/azure/bot-service/skills-conceptual?view=azure-bot-service-4.0&preserve-view=true) para Assistente Virtual e arquitetura de habilidades.</span><span class="sxs-lookup"><span data-stu-id="e70b7-262">Please refer to [documentation](/azure/bot-service/skills-conceptual?view=azure-bot-service-4.0&preserve-view=true) for Virtual Assistant and skills architecture.</span></span>

## <a name="code-sample"></a><span data-ttu-id="e70b7-263">Exemplo de código</span><span class="sxs-lookup"><span data-stu-id="e70b7-263">Code sample</span></span>

| <span data-ttu-id="e70b7-264">**Nome da amostra**</span><span class="sxs-lookup"><span data-stu-id="e70b7-264">**Sample name**</span></span> | <span data-ttu-id="e70b7-265">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="e70b7-265">**Description**</span></span> | <span data-ttu-id="e70b7-266">**C#**</span><span class="sxs-lookup"><span data-stu-id="e70b7-266">**C#**</span></span> | <span data-ttu-id="e70b7-267">**.NET**</span><span class="sxs-lookup"><span data-stu-id="e70b7-267">**.NET**</span></span> |
|----------|-----------------|----------|------------------|
| <span data-ttu-id="e70b7-268">Modelo de estúdio visual atualizado</span><span class="sxs-lookup"><span data-stu-id="e70b7-268">Updated visual studio template</span></span> | <span data-ttu-id="e70b7-269">Modelo personalizado para suportar recursos de equipes.</span><span class="sxs-lookup"><span data-stu-id="e70b7-269">Customized template to support teams capabilities.</span></span> | [<span data-ttu-id="e70b7-270">View</span><span class="sxs-lookup"><span data-stu-id="e70b7-270">View</span></span>](https://github.com/OfficeDev/microsoft-teams-apps-bookaroom/tree/nebhagat/microsoft-teams-apps-bookaroom-skill) |
| <span data-ttu-id="e70b7-271">Código de habilidade de robô de livro-a-quarto</span><span class="sxs-lookup"><span data-stu-id="e70b7-271">Book-a-room bot skill code</span></span> | <span data-ttu-id="e70b7-272">Permite que você encontre rapidamente e reserve uma sala de reunião em movimento.</span><span class="sxs-lookup"><span data-stu-id="e70b7-272">Lets you quickly find and book a meeting room on the go.</span></span> |  | [<span data-ttu-id="e70b7-273">View</span><span class="sxs-lookup"><span data-stu-id="e70b7-273">View</span></span>](https://github.com/nebhagat/msteams-virtual-assistant-dotnet) |


## <a name="see-also"></a><span data-ttu-id="e70b7-274">Confira também</span><span class="sxs-lookup"><span data-stu-id="e70b7-274">See also</span></span>

- [<span data-ttu-id="e70b7-275">Integrar aplicativos Web</span><span class="sxs-lookup"><span data-stu-id="e70b7-275">Integrate web apps</span></span>](~/samples/integrate-web-apps-overview.md)

- [<span data-ttu-id="e70b7-276">Livro-a-sala</span><span class="sxs-lookup"><span data-stu-id="e70b7-276">Book-a-room</span></span>](app-templates.md#book-a-room)

- [<span data-ttu-id="e70b7-277">Microsoft Teams bot</span><span class="sxs-lookup"><span data-stu-id="e70b7-277">Microsoft Teams bot</span></span>](../bots/what-are-bots.md)