---
title: Assistente Virtual do Microsoft Teams
description: Como criar bot e habilidades do Assistente Virtual para uso no Microsoft Teams
ms.topic: how-to
keywords: bots do assistente virtual do teams
ms.openlocfilehash: d72b1afbf975707d694d4aaef31263a3ce467629
ms.sourcegitcommit: 976e870cc925f61b76c3830ec04ba6e4bdfde32f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/27/2021
ms.locfileid: "50014611"
---
# <a name="virtual-assistant-for-microsoft-teams"></a><span data-ttu-id="1fdea-104">Assistente Virtual do Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="1fdea-104">Virtual Assistant for Microsoft Teams</span></span>

<span data-ttu-id="1fdea-105">O Assistente Virtual é um modelo de código aberto da Microsoft que permite criar uma solução de conversa robusta, mantendo o controle total da experiência do usuário, da identidade visual organizacional e dos dados necessários.</span><span class="sxs-lookup"><span data-stu-id="1fdea-105">Virtual Assistant is a Microsoft open-source template that enables you to create a robust conversational solution while maintaining full control of user experience, organizational branding, and necessary data.</span></span> <span data-ttu-id="1fdea-106">O modelo principal do Assistente [Virtual](https://microsoft.github.io/botframework-solutions/overview/virtual-assistant-template) é o bloco de construção básico que reúne as tecnologias da Microsoft necessárias para criar um Assistente Virtual, incluindo o [SDK](https://github.com/microsoft/botframework-sdk)da Estrutura do Bot, Noções Básicas sobre Idiomas [(ÂMBITO),](https://www.luis.ai/)Criador de [QnA,](https://www.qnamaker.ai/)bem como recursos essenciais, incluindo registro de habilidades, contas vinculadas, intenção de conversa básica de oferecer aos usuários finais uma variedade de interações e experiências perfeitas.</span><span class="sxs-lookup"><span data-stu-id="1fdea-106">The [Virtual Assistant core template](https://microsoft.github.io/botframework-solutions/overview/virtual-assistant-template) is the basic building block that brings together the Microsoft technologies required to build a Virtual Assistant, including the [Bot Framework SDK](https://github.com/microsoft/botframework-sdk), [Language Understanding (LUIS)](https://www.luis.ai/), [QnA Maker](https://www.qnamaker.ai/), as well as essential capabilities including  skills registration, linked accounts, basic conversational intent to offer end users a range of seamless interactions and experiences.</span></span> <span data-ttu-id="1fdea-107">Além disso, os recursos de modelo incluem exemplos avançados de habilidades de conversa [reutilizáveis.](https://microsoft.github.io/botframework-solutions/overview/skills)</span><span class="sxs-lookup"><span data-stu-id="1fdea-107">In addition, the template capabilities include rich examples of reusable conversational [skills](https://microsoft.github.io/botframework-solutions/overview/skills).</span></span>  <span data-ttu-id="1fdea-108">Habilidades individuais podem ser integradas em uma solução de Assistente Virtual para habilitar vários cenários.</span><span class="sxs-lookup"><span data-stu-id="1fdea-108">Individual skills can be integrated in a Virtual Assistant solution to enable multiple scenarios.</span></span> <span data-ttu-id="1fdea-109">Usando o SDK do Bot Framework, as habilidades são apresentadas no formulário do código-fonte, permitindo que você personalize e estenda conforme necessário.</span><span class="sxs-lookup"><span data-stu-id="1fdea-109">Using the Bot Framework SDK, Skills are presented in source code form enabling you to customize and extend as required.</span></span> <span data-ttu-id="1fdea-110">Veja [o que é uma habilidade de estrutura de bot.](https://microsoft.github.io/botframework-solutions/overview/skills/)</span><span class="sxs-lookup"><span data-stu-id="1fdea-110">See [What is a Bot Framework Skill](https://microsoft.github.io/botframework-solutions/overview/skills/).</span></span>

![Diagrama de visão geral do Assistente Virtual](../assets/images/bots/virtual-assistant/overview.png)

<span data-ttu-id="1fdea-112">As atividades de mensagens de texto são roteadas para habilidades associadas pelo núcleo do Assistente Virtual usando um modelo [de expedição.](/azure/bot-service/bot-builder-tutorial-dispatch?view=azure-bot-service-4.0&tabs=cs)</span><span class="sxs-lookup"><span data-stu-id="1fdea-112">Text message activities are routed to associated skills by the Virtual Assistant core using a [dispatch](/azure/bot-service/bot-builder-tutorial-dispatch?view=azure-bot-service-4.0&tabs=cs) model.</span></span> 

## <a name="implementation-considerations"></a><span data-ttu-id="1fdea-113">Considerações sobre implementação</span><span class="sxs-lookup"><span data-stu-id="1fdea-113">Implementation considerations</span></span>

<span data-ttu-id="1fdea-114">A decisão de adicionar um Assistente Virtual pode incluir muitos determinantes e diferir para cada organização.</span><span class="sxs-lookup"><span data-stu-id="1fdea-114">The decision to add a Virtual Assistant can include many determinants and differ for each organization.</span></span> <span data-ttu-id="1fdea-115">Aqui estão os fatores que suportam a implementação de um Assistente Virtual para sua organização:</span><span class="sxs-lookup"><span data-stu-id="1fdea-115">Here are the factors that support implementing a Virtual Assistant for your organization:</span></span>

- <span data-ttu-id="1fdea-116">Uma equipe central gerencia todas as experiências dos funcionários e tem a capacidade de criar uma experiência de Assistente Virtual e gerenciar atualizações para a experiência principal, incluindo a adição de novas habilidades.</span><span class="sxs-lookup"><span data-stu-id="1fdea-116">A central team manages all employee experiences and has the capability to build a Virtual Assistant experience and manage updates to the core experience including the addition of new skills.</span></span>
- <span data-ttu-id="1fdea-117">Vários aplicativos existem entre funções comerciais e/ou o número deve crescer no futuro.</span><span class="sxs-lookup"><span data-stu-id="1fdea-117">Multiple applications exist across business functions and/or the number is expected to grow in the future.</span></span>
- <span data-ttu-id="1fdea-118">Os aplicativos existentes são personalizáveis, pertencentes à organização, e podem ser convertidos em habilidades para um Assistente Virtual.</span><span class="sxs-lookup"><span data-stu-id="1fdea-118">Existing applications are customizable, owned by the organization, and can be converted into skills for a Virtual Assistant.</span></span>
- <span data-ttu-id="1fdea-119">A equipe central de experiências de funcionários é capaz de influenciar personalizações em aplicativos existentes e fornecer as orientações necessárias para integrar aplicativos existentes como habilidades na experiência do Assistente Virtual</span><span class="sxs-lookup"><span data-stu-id="1fdea-119">The central employee-experiences team is able to influence customizations to existing apps and provide necessary guidance for integrating existing applications as skills in Virtual Assistant experience</span></span>

![A equipe central mantém o assistente e as equipes de funções comerciais contribuem com habilidades](../assets/images/bots/virtual-assistant/business-functions.png)

## <a name="create-a-teams-focused-virtual-assistant"></a><span data-ttu-id="1fdea-121">Criar um Assistente Virtual focado no Teams</span><span class="sxs-lookup"><span data-stu-id="1fdea-121">Create a Teams-focused Virtual Assistant</span></span>

<span data-ttu-id="1fdea-122">A Microsoft publicou um [modelo do Visual Studio](https://marketplace.visualstudio.com/items?itemName=BotBuilder.VirtualAssistantTemplate) para criar Assistentes Virtuais e habilidades.</span><span class="sxs-lookup"><span data-stu-id="1fdea-122">Microsoft has published a [Visual Studio template](https://marketplace.visualstudio.com/items?itemName=BotBuilder.VirtualAssistantTemplate) for building Virtual Assistants and skills.</span></span> <span data-ttu-id="1fdea-123">Com o modelo do Visual Studio, você pode criar um Assistente Virtual, alimentado por uma experiência baseada em texto com suporte para cartões rich limitados com ações.</span><span class="sxs-lookup"><span data-stu-id="1fdea-123">With the Visual Studio template, you can create a Virtual Assistant, powered by a text-based experience with support for limited rich cards with actions.</span></span> <span data-ttu-id="1fdea-124">Aprimoramos o modelo base do Visual Studio para incluir recursos de plataforma do Microsoft Teams e excelentes experiências de aplicativos do Teams.</span><span class="sxs-lookup"><span data-stu-id="1fdea-124">We have enhanced the Visual Studio base template to include Microsoft Teams platform capabilities and power great Teams app experiences.</span></span> <span data-ttu-id="1fdea-125">Alguns dos recursos incluem suporte para cartões adaptáveis avançados, módulos de tarefas, chats de equipes/grupos e extensões de mensagens.</span><span class="sxs-lookup"><span data-stu-id="1fdea-125">A few of the capabilities include support for rich adaptive cards, task modules, teams/group chats and messaging extensions.</span></span> <span data-ttu-id="1fdea-126">*Confira também*, [Tutorial: Estender seu Assistente Virtual ao Microsoft Teams.](https://microsoft.github.io/botframework-solutions/clients-and-channels/tutorials/enable-teams/1-intro/)</span><span class="sxs-lookup"><span data-stu-id="1fdea-126">*See also*, [Tutorial: Extend Your Virtual Assistant to Microsoft Teams](https://microsoft.github.io/botframework-solutions/clients-and-channels/tutorials/enable-teams/1-intro/).</span></span>

![Diagrama de alto nível de uma solução do Assistente Virtual](../assets/images/bots/virtual-assistant/high-level-diagram.png)

### <a name="add-adaptive-cards-to-your-virtual-assistant"></a><span data-ttu-id="1fdea-128">Adicionar cartões adaptáveis ao Assistente Virtual</span><span class="sxs-lookup"><span data-stu-id="1fdea-128">Add adaptive cards to your Virtual Assistant</span></span>

<span data-ttu-id="1fdea-129">Para expedir as solicitações corretamente, o Assistente Virtual precisa identificar o modelo DEES correto e as habilidades correspondentes associadas a ele.</span><span class="sxs-lookup"><span data-stu-id="1fdea-129">To dispatch requests properly, your Virtual Assistant needs to identify the correct LUIS model and corresponding skill associated with it.</span></span> <span data-ttu-id="1fdea-130">No entanto, o mecanismo de expedição não pode ser usado para atividades de ação de cartão, pois o modelo DOLS associado a uma habilidade pode não ser treinado para textos de ação do cartão, pois são palavras-chave fixas e pré-definidas, não expressões de um usuário.</span><span class="sxs-lookup"><span data-stu-id="1fdea-130">However, the dispatching mechanism cannot be used for card action activities since the LUIS model associated with a skill may not be trained for card action texts since these are fixed, pre-defined keywords, not utterances from a user.</span></span>

<span data-ttu-id="1fdea-131">Resolvemos isso incorporando informações de habilidade na carga de ação do cartão.</span><span class="sxs-lookup"><span data-stu-id="1fdea-131">We have resolved this by embedding skill information in the card action payload.</span></span> <span data-ttu-id="1fdea-132">Todas as habilidades devem ser `skillId` integradas no  `value` campo das ações do cartão.</span><span class="sxs-lookup"><span data-stu-id="1fdea-132">Every skill should embed `skillId` in the  `value` field of card actions.</span></span> <span data-ttu-id="1fdea-133">Essa é a melhor maneira de garantir que cada atividade de ação do cartão carregue as informações de habilidades relevantes e o Assistente Virtual possa utilizar essas informações para expedir.</span><span class="sxs-lookup"><span data-stu-id="1fdea-133">This is the best way to ensure that each card action activity carries the relevant skill information and Virtual Assistant can utilize this information for dispatching.</span></span>

<span data-ttu-id="1fdea-134">Veja a seguir um exemplo de dados de ação do cartão.</span><span class="sxs-lookup"><span data-stu-id="1fdea-134">Below is a card action data sample.</span></span> <span data-ttu-id="1fdea-135">Ao fornecer no `skillId` construtor, garantimos que as informações de habilidade sempre estão presentes em ações de cartão.</span><span class="sxs-lookup"><span data-stu-id="1fdea-135">By providing `skillId` in the constructor we ensure that skill information is always present in card actions.</span></span>

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

<span data-ttu-id="1fdea-136">Em seguida, `SkillCardActionData` apresentamos a classe no modelo do Assistente Virtual para extrair `skillId` da carga de ação do cartão.</span><span class="sxs-lookup"><span data-stu-id="1fdea-136">Next, we introduce `SkillCardActionData` class in the Virtual Assistant template to extract `skillId` from the card action payload.</span></span>

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

<span data-ttu-id="1fdea-137">Veja a seguir um trecho de código para extrair dados  `skillId` de ação do cartão.</span><span class="sxs-lookup"><span data-stu-id="1fdea-137">Below is a code snippet to extract  `skillId` from card action data.</span></span> <span data-ttu-id="1fdea-138">Implementamos-o como um método de extensão na [classe Activity.](https://github.com/microsoft/botframework-sdk/blob/master/specs/botframework-activity/botframework-activity.md)</span><span class="sxs-lookup"><span data-stu-id="1fdea-138">We implemented it as an  extension method in the [Activity](https://github.com/microsoft/botframework-sdk/blob/master/specs/botframework-activity/botframework-activity.md) class.</span></span>

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

### <a name="handle-interruptions-gracefully"></a><span data-ttu-id="1fdea-139">Lidar com interrupções normalmente</span><span class="sxs-lookup"><span data-stu-id="1fdea-139">Handle interruptions gracefully</span></span>

<span data-ttu-id="1fdea-140">O Assistente Virtual pode lidar com interrupções nos casos em que um usuário tenta invocar uma habilidade enquanto outra habilidade está ativa no momento.</span><span class="sxs-lookup"><span data-stu-id="1fdea-140">Virtual Assistant can handle interruptions in cases where a user tries to invoke a skill while another skill is currently active.</span></span> <span data-ttu-id="1fdea-141">introduzimos e, com base no `TeamsSkillDialog` `TeamsSwitchSkillDialog` [SkillDialog](https://github.com/microsoft/botframework-solutions/blob/5b46d73e220bbb4fba86c48be532e495535ca78a/sdk/csharp/libraries/microsoft.bot.solutions/Skills/SkillDialog.cs) e [SwitchSkillDialog](https://github.com/microsoft/botframework-solutions/blob/6d40fa8ae05f96b0c5e0464e01361a9e1deb696c/sdk/csharp/libraries/microsoft.bot.solutions/Skills/Dialogs/SwitchSkillDialog.cs)da Estrutura de Bot, para permitir que os usuários troquem uma experiência de habilidade de ações de cartão.</span><span class="sxs-lookup"><span data-stu-id="1fdea-141">we have introduced `TeamsSkillDialog` and `TeamsSwitchSkillDialog`, based on Bot Framework's [SkillDialog](https://github.com/microsoft/botframework-solutions/blob/5b46d73e220bbb4fba86c48be532e495535ca78a/sdk/csharp/libraries/microsoft.bot.solutions/Skills/SkillDialog.cs) and [SwitchSkillDialog](https://github.com/microsoft/botframework-solutions/blob/6d40fa8ae05f96b0c5e0464e01361a9e1deb696c/sdk/csharp/libraries/microsoft.bot.solutions/Skills/Dialogs/SwitchSkillDialog.cs), to enable users to switch a skill experience from card actions.</span></span> <span data-ttu-id="1fdea-142">Para lidar com essa solicitação, o Assistente Virtual solicita ao usuário uma mensagem de confirmação para alternar habilidades.</span><span class="sxs-lookup"><span data-stu-id="1fdea-142">To handle this request the Virtual Assistant prompts the user with a confirmation message to switch skills.</span></span>

![Prompt de confirmação ao alternar para uma nova habilidade](../assets/images/bots/virtual-assistant/switch-skills-prompt.png)

### <a name="handling-task-module-requests"></a><span data-ttu-id="1fdea-144">Manipulando solicitações de módulo de tarefa</span><span class="sxs-lookup"><span data-stu-id="1fdea-144">Handling task module requests</span></span>

<span data-ttu-id="1fdea-145">Para adicionar recursos de módulo de tarefa a um Assistente Virtual, dois métodos adicionais são incluídos no manipulador de atividades do Assistente Virtual: `OnTeamsTaskModuleFetchAsync` e `OnTeamsTaskModuleSubmitAsync` .</span><span class="sxs-lookup"><span data-stu-id="1fdea-145">To add task module capabilities to a Virtual Assistant, two additional methods are included in the Virtual Assistant activity handler: `OnTeamsTaskModuleFetchAsync` and `OnTeamsTaskModuleSubmitAsync`.</span></span> <span data-ttu-id="1fdea-146">Esses métodos escutam atividades relacionadas ao módulo de tarefa do Assistente Virtual, identificam as habilidades associadas à solicitação e encaminham a solicitação para a habilidade identificada.</span><span class="sxs-lookup"><span data-stu-id="1fdea-146">These methods listen to task module-related activities from Virtual Assistant, identify the skill associated with the request, and forward the request to the identified skill.</span></span> 

<span data-ttu-id="1fdea-147">O encaminhamento de solicitação é feito por meio do  [método SkillHttpClient](/dotnet/api/microsoft.bot.builder.integration.aspnet.core.skills.skillhttpclient?view=botbuilder-dotnet-stable) `PostActivityAsync` .</span><span class="sxs-lookup"><span data-stu-id="1fdea-147">Request forwarding is done via the  [SkillHttpClient](/dotnet/api/microsoft.bot.builder.integration.aspnet.core.skills.skillhttpclient?view=botbuilder-dotnet-stable), `PostActivityAsync` method.</span></span> <span data-ttu-id="1fdea-148">Ele retorna a resposta `InvokeResponse` como a qual é analisado e convertido para `TaskModuleResponse` .</span><span class="sxs-lookup"><span data-stu-id="1fdea-148">It returns the response as `InvokeResponse` which is parsed and converted to `TaskModuleResponse` .</span></span>

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

<span data-ttu-id="1fdea-149">Uma abordagem semelhante é seguida para expedição de ação do cartão e respostas do módulo de tarefa.</span><span class="sxs-lookup"><span data-stu-id="1fdea-149">A similar approach is followed for card action dispatching and task module responses.</span></span> <span data-ttu-id="1fdea-150">Os dados de busca e envio de ação do módulo de tarefa são atualizados para `skillId` incluir.</span><span class="sxs-lookup"><span data-stu-id="1fdea-150">Task module fetch and submit action data is updated to include `skillId`.</span></span> <span data-ttu-id="1fdea-151">O método Activity Extension extrai da carga que fornece detalhes `GetSkillId` sobre as habilidades que precisam ser `skillId` invocadas.</span><span class="sxs-lookup"><span data-stu-id="1fdea-151">Activity Extension method `GetSkillId` extracts `skillId` from the payload which provides details about the skill that needs to be invoked.</span></span>

<span data-ttu-id="1fdea-152">Veja a seguir um trecho de código `OnTeamsTaskModuleFetchAsync` para `OnTeamsTaskModuleSubmitAsync` métodos e trechos de código.</span><span class="sxs-lookup"><span data-stu-id="1fdea-152">Below is a code snippet for `OnTeamsTaskModuleFetchAsync` and `OnTeamsTaskModuleSubmitAsync` methods.</span></span>

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

<span data-ttu-id="1fdea-153">Além disso, todos os domínios de habilidade devem ser incluídos na seção no arquivo de manifesto do Assistente Virtual para que os módulos de tarefa invocados por meio de uma habilidade `validDomains` sejam renderados corretamente.</span><span class="sxs-lookup"><span data-stu-id="1fdea-153">Additionally, all skill domains must be included in the `validDomains` section in Virtual Assistant's manifest file so that task modules invoked via a skill render properly.</span></span>

### <a name="handling-collaborative-app-scopes"></a><span data-ttu-id="1fdea-154">Manipulando escopos de aplicativo colaborativos</span><span class="sxs-lookup"><span data-stu-id="1fdea-154">Handling collaborative app scopes</span></span>

<span data-ttu-id="1fdea-155">Os aplicativos do Teams podem existir em vários escopos, incluindo chat 1:1, chat em grupo e canais.</span><span class="sxs-lookup"><span data-stu-id="1fdea-155">Teams apps can exist in multiple scopes including 1:1 chat, group chat, and channels.</span></span> <span data-ttu-id="1fdea-156">O modelo principal do Assistente Virtual foi projetado para chats 1:1.</span><span class="sxs-lookup"><span data-stu-id="1fdea-156">The core Virtual Assistant template is designed for 1:1 chats.</span></span> <span data-ttu-id="1fdea-157">Como parte da experiência de integração, o Assistente Virtual solicita aos usuários o nome e mantém o estado do usuário.</span><span class="sxs-lookup"><span data-stu-id="1fdea-157">As part of the onboarding experience Virtual Assistant  prompts users for name and maintains user state.</span></span> <span data-ttu-id="1fdea-158">Como essa experiência de integração não é adequada para escopos de chat/canal de grupo, ela foi removida.</span><span class="sxs-lookup"><span data-stu-id="1fdea-158">Since that onboarding experience is not suited for group chat/channel scopes it has been removed.</span></span>

<span data-ttu-id="1fdea-159">As habilidades devem lidar com atividades em vários escopos (bate-papo 1:1, chat em grupo e conversa de canal).</span><span class="sxs-lookup"><span data-stu-id="1fdea-159">Skills should handle activities in multiple scopes (1:1 chat, group chat, and channel conversation).</span></span> <span data-ttu-id="1fdea-160">Se nenhum desses escopos for suportado, as habilidades deverão responder com uma mensagem apropriada.</span><span class="sxs-lookup"><span data-stu-id="1fdea-160">If any of these scopes are not supported, skills should respond with an appropriate message.</span></span>

<span data-ttu-id="1fdea-161">As seguintes funções de processamento foram adicionadas ao núcleo do Assistente Virtual:</span><span class="sxs-lookup"><span data-stu-id="1fdea-161">The following  processing functions have been added to Virtual Assistant core:</span></span>

- <span data-ttu-id="1fdea-162">O Assistente Virtual pode ser invocado sem qualquer mensagem de texto de um chat ou canal de grupo.</span><span class="sxs-lookup"><span data-stu-id="1fdea-162">Virtual Assistant can be invoked without any text message from a group chat or channel.</span></span>
- <span data-ttu-id="1fdea-163">As entradas são limpas (ou seja, remova o @mention necessário do bot) antes de enviar a mensagem para o módulo de expedição.</span><span class="sxs-lookup"><span data-stu-id="1fdea-163">Articulations are cleaned (i.e.,  remove the necessary @mention of the bot) before sending the message to the dispatch module.</span></span>

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

### <a name="handling-messaging-extensions"></a><span data-ttu-id="1fdea-164">Manipulando extensões de mensagens</span><span class="sxs-lookup"><span data-stu-id="1fdea-164">Handling messaging extensions</span></span>

<span data-ttu-id="1fdea-165">Os comandos para uma extensão de mensagens são declarados no arquivo de manifesto do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="1fdea-165">The commands for a messaging extension are declared in your app manifest file.</span></span> <span data-ttu-id="1fdea-166">A interface do usuário da extensão de mensagens é alimentada por esses comandos.</span><span class="sxs-lookup"><span data-stu-id="1fdea-166">The messaging extension user interface is powered by those commands.</span></span> <span data-ttu-id="1fdea-167">Para que um Assistente Virtual ative um comando de extensão de mensagens (como uma habilidade anexada), o próprio manifesto do Assistente Virtual deve conter esses comandos.</span><span class="sxs-lookup"><span data-stu-id="1fdea-167">For a Virtual Assistant to power a messaging extension command (as an attached skill), a Virtual Assistant's own manifest must contain those commands.</span></span> <span data-ttu-id="1fdea-168">Os comandos do manifesto de uma habilidade individual também devem ser adicionados ao manifesto do Assistente Virtual.</span><span class="sxs-lookup"><span data-stu-id="1fdea-168">The commands from an individual skill's manifest should be added to the Virtual Assistant's manifest as well.</span></span> <span data-ttu-id="1fdea-169">A ID de comando fornece informações sobre uma habilidade associada acrescentando a ID do aplicativo da habilidade por meio de um separador ( `:` ).</span><span class="sxs-lookup"><span data-stu-id="1fdea-169">The command ID provides information about an associated skill by appending the skill's app ID via a separator (`:`).</span></span>

<span data-ttu-id="1fdea-170">Veja a seguir um trecho de um arquivo de manifesto de habilidades.</span><span class="sxs-lookup"><span data-stu-id="1fdea-170">Below is a snippet from a skill's manifest file.</span></span>

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

<span data-ttu-id="1fdea-171">E, abaixo está o trecho de código do arquivo de manifesto do Assistente Virtual correspondente.</span><span class="sxs-lookup"><span data-stu-id="1fdea-171">And, below is the corresponding Virtual Assistant manifest file code snippet.</span></span>

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

<span data-ttu-id="1fdea-172">Depois que os comandos são invocados por um usuário, o Assistente Virtual pode identificar uma habilidade associada ao analisar a ID de comando, atualizar a atividade removendo o sufixo extra ( ) da ID de comando e encaminhá-lo para a habilidade `:<skill_id>` correspondente.</span><span class="sxs-lookup"><span data-stu-id="1fdea-172">Once the commands are invoked by a user, the Virtual Assistant can identify an associated skill by parsing the command ID, update the activity by removing the extra suffix (`:<skill_id>`) from the command ID,  and forward it to the corresponding skill.</span></span> <span data-ttu-id="1fdea-173">O código de uma habilidade não precisa lidar com o sufixo extra, portanto, os conflitos entre as IDs de comando entre habilidades são evitados.</span><span class="sxs-lookup"><span data-stu-id="1fdea-173">The code for a skill doesn't need to handle the extra suffix, thus, conflicts between command IDs across skills are avoided.</span></span> <span data-ttu-id="1fdea-174">Com essa abordagem, todos os comandos de pesquisa e ação de uma habilidade em todos os contextos ("redação", "commandBox" e "mensagem") podem ser acionados por um Assistente Virtual.</span><span class="sxs-lookup"><span data-stu-id="1fdea-174">With this approach, all the search and action commands of a skill within all contexts ("compose", "commandBox" and "message") can be powered by a Virtual Assistant.</span></span>

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

<span data-ttu-id="1fdea-175">Algumas atividades de extensão de mensagens não incluem a ID do comando.</span><span class="sxs-lookup"><span data-stu-id="1fdea-175">Some messaging extension activities do not include the command ID.</span></span> <span data-ttu-id="1fdea-176">Por exemplo, `composeExtension/selectItem` contém apenas o valor da ação de toque de invocação.</span><span class="sxs-lookup"><span data-stu-id="1fdea-176">For example, `composeExtension/selectItem` contains only the value of the invoke tap action.</span></span> <span data-ttu-id="1fdea-177">Para identificar as habilidades associadas, `skillId`  é anexado a cada cartão de item enquanto forma uma resposta para `OnTeamsMessagingExtensionQueryAsync` .</span><span class="sxs-lookup"><span data-stu-id="1fdea-177">To identify the associated skill, `skillId`  is attached to each item card while forming a response for `OnTeamsMessagingExtensionQueryAsync`.</span></span> <span data-ttu-id="1fdea-178">(Isso é semelhante à abordagem para [adicionar cartões adaptáveis ao Assistente Virtual.](#add-adaptive-cards-to-your-virtual-assistant)</span><span class="sxs-lookup"><span data-stu-id="1fdea-178">(This is similar to the approach for [adding adaptive  cards to your Virtual Assistant](#add-adaptive-cards-to-your-virtual-assistant).</span></span>

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

## <a name="example-convert-the-book-a-room-app-template-to-a-virtual-assistant-skill"></a><span data-ttu-id="1fdea-179">Exemplo: Converter o modelo de aplicativo de uma sala de livro em uma habilidade do Assistente Virtual</span><span class="sxs-lookup"><span data-stu-id="1fdea-179">Example: Convert the Book-a-room app template to a Virtual Assistant skill</span></span>

<span data-ttu-id="1fdea-180">[Book-a-room](app-templates.md#book-a-room) é um bot do [Microsoft Teams](../bots/what-are-bots.md) que permite aos usuários encontrar e reservar rapidamente uma sala de reunião por 30 (padrão), 60 ou 90 minutos a partir da hora atual.</span><span class="sxs-lookup"><span data-stu-id="1fdea-180">[Book-a-room](app-templates.md#book-a-room) is a [Microsoft Teams bot](../bots/what-are-bots.md) that lets users quickly find and reserve a meeting room for 30 (default), 60, or 90 minutes starting from the current  time.</span></span> <span data-ttu-id="1fdea-181">Os escopos de bot de sala de livro para conversas pessoais ou 1:1.</span><span class="sxs-lookup"><span data-stu-id="1fdea-181">The Book-a-room bot scopes to personal or 1:1 conversations.</span></span>

![Assistente Virtual com uma habilidade de "reservar uma sala"](../assets/images/bots/virtual-assistant/book-a-room-skill.png)

<span data-ttu-id="1fdea-183">A seguir estão as alterações delta introduzidas para convertê-la em uma habilidade que pode ser anexada a um Assistente Virtual.</span><span class="sxs-lookup"><span data-stu-id="1fdea-183">Followings are the delta changes introduced to convert it to a skill which can be attached to a Virtual Assistant.</span></span> <span data-ttu-id="1fdea-184">Diretrizes semelhantes podem ser seguidas para converter qualquer bot v4 existente em uma habilidade.</span><span class="sxs-lookup"><span data-stu-id="1fdea-184">Similar guidelines can be followed to convert any existing v4 bot to a skill.</span></span>

### <a name="skill-manifest"></a><span data-ttu-id="1fdea-185">Manifesto de habilidades</span><span class="sxs-lookup"><span data-stu-id="1fdea-185">Skill manifest</span></span>

<span data-ttu-id="1fdea-186">Um manifesto de habilidades é um arquivo JSON que expõe o ponto de extremidade, a ID, o nome e outros metadados relevantes de uma habilidade (esse manifesto é diferente do manifesto usado para sideload de um aplicativo no Microsoft Teams) Um Assistente Virtual requer um caminho para esse arquivo como uma entrada para anexar uma habilidade.</span><span class="sxs-lookup"><span data-stu-id="1fdea-186">A skill manifest is a JSON file that exposes a skill's messaging endpoint, id, name, and other relevant metadata (this manifest is different than the manifest used for sideloading an app in Microsoft Teams) A Virtual Assistant requires a path to this file as an input to attach a skill.</span></span> <span data-ttu-id="1fdea-187">Adicionamos o seguinte manifesto à pasta wwwroot do bot.</span><span class="sxs-lookup"><span data-stu-id="1fdea-187">We have added the following manifest to the bot's wwwroot folder.</span></span>

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

### <a name="luis-integration"></a><span data-ttu-id="1fdea-188">Integração COM OLS</span><span class="sxs-lookup"><span data-stu-id="1fdea-188">LUIS Integration</span></span>

<span data-ttu-id="1fdea-189">O modelo de expedição do Assistente Virtual foi criado com base nos modelos DEIS das habilidades anexadas.</span><span class="sxs-lookup"><span data-stu-id="1fdea-189">Virtual Assistant's dispatch model is built on top of attached skills' LUIS models.</span></span> <span data-ttu-id="1fdea-190">O modelo de expedição identifica a intenção de cada atividade de texto e descobre habilidades associadas a ela.</span><span class="sxs-lookup"><span data-stu-id="1fdea-190">The dispatch model identifies the intent for every text activity and finds out skill associated with it.</span></span>

<span data-ttu-id="1fdea-191">O Assistente Virtual requer o modelo de HABILIDADE (no formato) como `.lu` uma entrada enquanto anexa uma habilidade.</span><span class="sxs-lookup"><span data-stu-id="1fdea-191">Virtual Assistant requires skill's LUIS model (in `.lu` format) as an input while attaching a skill.</span></span> <span data-ttu-id="1fdea-192">O json DOLs pode ser convertido `.lu` em formato usando a ferramenta botframework-cli.</span><span class="sxs-lookup"><span data-stu-id="1fdea-192">LUIS json can be converted to `.lu` format using botframework-cli  tool.</span></span>

```json
botskills connect --remoteManifest "<url to skill's manifest>" --luisFolder "<path to the folder containing your Skill's .lu files>" --languages "en-us" --cs
```

```bash
npm i -g @microsoft/botframework-cli
bf luis:convert --in <pathToLUIS.json> --out <pathToLuFile>
```

<span data-ttu-id="1fdea-193">O bot de reservar uma sala tem dois comandos principais para os usuários:</span><span class="sxs-lookup"><span data-stu-id="1fdea-193">Book-a-room bot has two main commands for users:</span></span>

- `Book room`
- `Manage Favorites`

<span data-ttu-id="1fdea-194">Nós fizemos um modelo DEES noções básicas sobre esses dois comandos.</span><span class="sxs-lookup"><span data-stu-id="1fdea-194">We have built a LUIS model understanding these two commands.</span></span> <span data-ttu-id="1fdea-195">Os segredos correspondentes precisam ser preenchidos em `cognitivemodels.json` .</span><span class="sxs-lookup"><span data-stu-id="1fdea-195">Corresponding secrets need to be populated in `cognitivemodels.json`.</span></span> <span data-ttu-id="1fdea-196">O arquivo JSON JSON correspondente pode ser encontrado [aqui](https://github.com/OfficeDev/microsoft-teams-apps-bookaroom/blob/nebhagat/microsoft-teams-apps-bookaroom-skill/Deployment/Resources/LU/book-a-meeting.json) e é assim que o arquivo `.lu` correspondente se parece.</span><span class="sxs-lookup"><span data-stu-id="1fdea-196">The corresponding LUIS JSON file can be found [here](https://github.com/OfficeDev/microsoft-teams-apps-bookaroom/blob/nebhagat/microsoft-teams-apps-bookaroom-skill/Deployment/Resources/LU/book-a-meeting.json) and this is how the corresponding `.lu` file looks like.</span></span>

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

<span data-ttu-id="1fdea-197">Com essa abordagem, qualquer comando emite por um usuário para o Assistente Virtual relacionado a ou pode ser identificado como um comando associado ao `book room` bot livro-a-sala e é encaminhado para essa `manage favorites` habilidade.</span><span class="sxs-lookup"><span data-stu-id="1fdea-197">With this approach, any command issues by a user to Virtual Assistant related to `book room` or `manage favorites` can be identified as a command associated with Book-a-room bot and is forwarded to this skill.</span></span>
<span data-ttu-id="1fdea-198">Por outro lado, o bot de sala de livro precisa usar o modelo DOES para entender esses comandos se eles não são digitados como estão (por exemplo: `I want to manage my favorite rooms` ).</span><span class="sxs-lookup"><span data-stu-id="1fdea-198">On the other hand, Book-a-room room bot needs to use LUIS model to understand these commands if they are not typed as is (for example: `I want to manage my favorite rooms`).</span></span>

### <a name="multi-language-support"></a><span data-ttu-id="1fdea-199">Suporte a vários idiomas</span><span class="sxs-lookup"><span data-stu-id="1fdea-199">Multi-Language support</span></span>

<span data-ttu-id="1fdea-200">Para este exemplo, criamos apenas um modelo DEES com cultura em inglês.</span><span class="sxs-lookup"><span data-stu-id="1fdea-200">For this example, we have only created a LUIS model with English culture.</span></span> <span data-ttu-id="1fdea-201">Você pode criar modelos DEIS correspondentes a outros idiomas e adicionar entrada a `cognitivemodels.json` .</span><span class="sxs-lookup"><span data-stu-id="1fdea-201">You can create LUIS models corresponding to other languages and add entry to `cognitivemodels.json`.</span></span>

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

<span data-ttu-id="1fdea-202">Em paralelo, adicione o `.lu` arquivo correspondente no caminho da pasta.</span><span class="sxs-lookup"><span data-stu-id="1fdea-202">In parallel, add corresponding `.lu` file in luisFolder path.</span></span> <span data-ttu-id="1fdea-203">A estrutura de pastas deve ser a seguinte:</span><span class="sxs-lookup"><span data-stu-id="1fdea-203">Folder structure should be as follows:</span></span>

```bash
| - luisFolder

        | - en-us

                | - book-a-meeting.lu

        | - your_language_culture

                | - book-a-meeting.lu
```

<span data-ttu-id="1fdea-204">Atualize o comando botskills da seguinte forma para modificar o `languages` parâmetro:</span><span class="sxs-lookup"><span data-stu-id="1fdea-204">Update botskills command as follows to modify `languages` parameter:</span></span>

```json
botskills connect --remoteManifest "<url to skill's manifest>" --luisFolder "<path to luisFolder>" --languages "en-us, your_language_culture" --cs
```

<span data-ttu-id="1fdea-205">O Assistente Virtual `SetLocaleMiddleware` usa para identificar a localidade atual e invocar o modelo de expedição correspondente.</span><span class="sxs-lookup"><span data-stu-id="1fdea-205">Virtual Assistant uses `SetLocaleMiddleware` to identify current locale and invoke corresponding dispatch model.</span></span> <span data-ttu-id="1fdea-206">(A atividade da estrutura bot tem o campo de localidade que é usado por este middleware.) Recomendamos usar o mesmo para suas habilidades também.</span><span class="sxs-lookup"><span data-stu-id="1fdea-206">(Bot framework activity has locale field which is used by this middleware.) We recommend to use the same for your skill as well.</span></span> <span data-ttu-id="1fdea-207">Book-a-room bot does not use this middleware and instead gets locale from Bot framework activity's [clientInfo entity](https://github.com/microsoft/botframework-sdk/blob/master/specs/botframework-activity/botframework-activity.md#clientinfo).</span><span class="sxs-lookup"><span data-stu-id="1fdea-207">Book-a-room bot does not use this middleware and instead gets locale from Bot framework activity's [clientInfo entity](https://github.com/microsoft/botframework-sdk/blob/master/specs/botframework-activity/botframework-activity.md#clientinfo).</span></span>

### <a name="claim-validation"></a><span data-ttu-id="1fdea-208">Validação de declaração</span><span class="sxs-lookup"><span data-stu-id="1fdea-208">Claim validation</span></span>

<span data-ttu-id="1fdea-209">Adicionamos [claimsValidator](https://github.com/nebhagat/msteams-virtual-assistant-dotnet/blob/master/msteams-virtual-assistant-dotnet/Authentication/AllowedCallersClaimsValidator.cs) para restringir os chamadores às habilidades.</span><span class="sxs-lookup"><span data-stu-id="1fdea-209">We have added [claimsValidator](https://github.com/nebhagat/msteams-virtual-assistant-dotnet/blob/master/msteams-virtual-assistant-dotnet/Authentication/AllowedCallersClaimsValidator.cs) to restrict callers to the skill.</span></span> <span data-ttu-id="1fdea-210">Para permitir que um Assistente Virtual chame essa habilidade, preencha a matriz com essa ID de aplicativo específica `AllowedCallers` `appsettings` do Assistente Virtual.</span><span class="sxs-lookup"><span data-stu-id="1fdea-210">To allow a Virtual Assistant to call this skill, populate `AllowedCallers` array from `appsettings` with that particular Virtual Assistant's app ID.</span></span>

```
"AllowedCallers": [ "<caller_VA1_appId>", "<caller_VA2_appId>" ],
```

<span data-ttu-id="1fdea-211">A matriz de chamadores permitidos pode restringir quais habilidades os consumidores podem acessar as habilidades.</span><span class="sxs-lookup"><span data-stu-id="1fdea-211">The allowed callers array can restrict which skill consumers can access the skill.</span></span> <span data-ttu-id="1fdea-212">Adicione uma única entrada `*` a essa matriz para aceitar chamadas de qualquer consumidor de habilidades.</span><span class="sxs-lookup"><span data-stu-id="1fdea-212">Add single entry `*` to this array, to accept calls from any skill consumer.</span></span>

```
"AllowedCallers": [ "*" ],
```
<span data-ttu-id="1fdea-213">A documentação detalhada para adicionar validação de declarações a uma habilidade pode ser encontrada [aqui.](https://docs.microsoft.com/azure/bot-service/skill-implement-skill?view=azure-bot-service-4.0&tabs=cs#claims-validator)</span><span class="sxs-lookup"><span data-stu-id="1fdea-213">Detailed documentation for adding claims validation to a skill can be found [here](https://docs.microsoft.com/azure/bot-service/skill-implement-skill?view=azure-bot-service-4.0&tabs=cs#claims-validator).</span></span>

### <a name="card-refresh-limitation"></a><span data-ttu-id="1fdea-214">Limitação da atualização do cartão</span><span class="sxs-lookup"><span data-stu-id="1fdea-214">Card refresh limitation</span></span>

<span data-ttu-id="1fdea-215">A atividade de atualização (atualização do cartão) ainda não é suportada por meio do Assistente Virtual[(problema do github).](https://github.com/microsoft/botbuilder-dotnet/issues/3686)</span><span class="sxs-lookup"><span data-stu-id="1fdea-215">Updating activity (card refresh) is not supported yet via Virtual Assistant ([github issue](https://github.com/microsoft/botbuilder-dotnet/issues/3686)).</span></span> <span data-ttu-id="1fdea-216">Portanto, substituímos todas as chamadas de atualização de cartão ( `UpdateActivityAsync` ) por postar novas chamadas de cartão( `SendActivityAsync` ).</span><span class="sxs-lookup"><span data-stu-id="1fdea-216">Hence, we have replaced all card refresh calls (`UpdateActivityAsync`) with posting new card calls(`SendActivityAsync`).</span></span>

### <a name="card-actions-and-task-module-flows"></a><span data-ttu-id="1fdea-217">Ações de cartão e fluxos de módulo de tarefa</span><span class="sxs-lookup"><span data-stu-id="1fdea-217">Card actions and task module flows</span></span>

<span data-ttu-id="1fdea-218">Para encaminhar as atividades do módulo de tarefa ou ação de cartão para uma habilidade associada, as habilidades precisam ser integradas `skillId` a ela.</span><span class="sxs-lookup"><span data-stu-id="1fdea-218">To forward card action or task module activities to an associated skill, the skill needs to embed `skillId` to it.</span></span>
<span data-ttu-id="1fdea-219">Ação de cartão bot de sala de livro, as cargas de ação de busca e envio do módulo de tarefa são modificadas para conter `skillId` como um parâmetro.</span><span class="sxs-lookup"><span data-stu-id="1fdea-219">Book-a-room bot card action, task module fetch and submit action payloads are modified to contain `skillId` as a parameter.</span></span> 

<span data-ttu-id="1fdea-220">Para obter mais informações, [consulte esta](https://msteams-captain.visualstudio.com/xGrowth%20App%20Templates/_wiki/wikis/xGrowth.wiki/88/Virtual-Assistant-for-MS-Teams?anchor=rich-cards) seção nesta documentação.</span><span class="sxs-lookup"><span data-stu-id="1fdea-220">For more information refer [this](https://msteams-captain.visualstudio.com/xGrowth%20App%20Templates/_wiki/wikis/xGrowth.wiki/88/Virtual-Assistant-for-MS-Teams?anchor=rich-cards) section from this documentation.</span></span>

### <a name="handle-activities-from-group-chat-or-channel-scope"></a><span data-ttu-id="1fdea-221">Manipular atividades do chat de grupo ou do escopo do canal</span><span class="sxs-lookup"><span data-stu-id="1fdea-221">Handle activities from group chat or channel scope</span></span>

<span data-ttu-id="1fdea-222">O bot de livro em sala foi projetado apenas para chats privados (escopo pessoal/1:1).</span><span class="sxs-lookup"><span data-stu-id="1fdea-222">Book-a-room bot is designed for private chats (personal/1:1 scope) only.</span></span> <span data-ttu-id="1fdea-223">Como personalizemos o Assistente Virtual para dar suporte a escopos de canal e chat de grupo, o Assistente Virtual pode ser invocado desses escopos e, portanto, o bot de livro em sala pode obter atividades para o mesmo.</span><span class="sxs-lookup"><span data-stu-id="1fdea-223">Since we have customized Virtual Assistant to support group chat and channel scopes, the Virtual Assistant might be invoked from these scopes and thus, Book-a-room bot might get activities for the same.</span></span> <span data-ttu-id="1fdea-224">Portanto, o bot de uma sala de livro é personalizado para lidar com essas atividades.</span><span class="sxs-lookup"><span data-stu-id="1fdea-224">Hence Book-a-room bot is customized to handle those activities.</span></span> <span data-ttu-id="1fdea-225">A verificação foi colocada nos métodos do manipulador de atividades do `OnMessageActivityAsync` bot de uma sala de livro.</span><span class="sxs-lookup"><span data-stu-id="1fdea-225">The check has been put in `OnMessageActivityAsync` methods of Book-a-room bot's activity handler.</span></span>

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

<span data-ttu-id="1fdea-226">Você também pode aproveitar as habilidades existentes no repositório [de Soluções](https://github.com/microsoft/botframework-solutions/tree/master/skills/csharp) da Estrutura de Bot ou criar uma nova habilidade do zero.</span><span class="sxs-lookup"><span data-stu-id="1fdea-226">You can also leverage existing skills from [Bot Framework Solutions repository](https://github.com/microsoft/botframework-solutions/tree/master/skills/csharp) or create a new skill altogether from scratch.</span></span> <span data-ttu-id="1fdea-227">Tutoriais para o posterior podem ser [encontrados aqui.](https://microsoft.github.io/botframework-solutions/overview/skills/)</span><span class="sxs-lookup"><span data-stu-id="1fdea-227">Tutorials for the later can be found [here](https://microsoft.github.io/botframework-solutions/overview/skills/).</span></span> <span data-ttu-id="1fdea-228">Consulte a [documentação do](https://docs.microsoft.com/azure/bot-service/skills-conceptual?view=azure-bot-service-4.0)   Assistente Virtual e arquitetura de habilidades.</span><span class="sxs-lookup"><span data-stu-id="1fdea-228">Please refer to [documentation](https://docs.microsoft.com/azure/bot-service/skills-conceptual?view=azure-bot-service-4.0)   for Virtual Assistant and skills architecture.</span></span>

## <a name="sample-code-to-get-started"></a><span data-ttu-id="1fdea-229">Código de exemplo para começar</span><span class="sxs-lookup"><span data-stu-id="1fdea-229">Sample code to get started</span></span>

- [<span data-ttu-id="1fdea-230">Modelo do visual studio atualizado</span><span class="sxs-lookup"><span data-stu-id="1fdea-230">Updated visual studio template</span></span>](https://github.com/nebhagat/msteams-virtual-assistant-dotnet)
- [<span data-ttu-id="1fdea-231">Book-a-room bot skill code</span><span class="sxs-lookup"><span data-stu-id="1fdea-231">Book-a-room bot skill code</span></span>](https://github.com/OfficeDev/microsoft-teams-apps-bookaroom/tree/nebhagat/microsoft-teams-apps-bookaroom-skill)

## <a name="virtual-assistant-known-limitations"></a><span data-ttu-id="1fdea-232">Limitações conhecidas do Assistente Virtual</span><span class="sxs-lookup"><span data-stu-id="1fdea-232">Virtual Assistant known limitations</span></span>

- <span data-ttu-id="1fdea-233">**EndOfConversation**.</span><span class="sxs-lookup"><span data-stu-id="1fdea-233">**EndOfConversation**.</span></span> <span data-ttu-id="1fdea-234">Uma habilidade deve enviar uma `endOfConversation` atividade quando terminar uma conversa.</span><span class="sxs-lookup"><span data-stu-id="1fdea-234">A skill should send an `endOfConversation` activity when it finishes a conversation.</span></span> <span data-ttu-id="1fdea-235">base dessa atividade, um Assistente Virtual finaliza o contexto com essa habilidade específica e volta ao contexto do Assistente Virtual (raiz).</span><span class="sxs-lookup"><span data-stu-id="1fdea-235">basis this activity, a Virtual Assistant ends context with that particular skill and gets back into Virtual Assistant's (root) context.</span></span> <span data-ttu-id="1fdea-236">Para o bot de uma sala de livro, não há um estado claro onde a conversa pode ser encerrada.</span><span class="sxs-lookup"><span data-stu-id="1fdea-236">For Book-a-room bot, there is no clear state where conversation can be ended.</span></span> <span data-ttu-id="1fdea-237">Portanto, não enviamos do bot de uma sala de livro e quando o usuário deseja voltar ao contexto raiz, ele pode simplesmente fazer `endOfConversation` isso por `start over` comando.</span><span class="sxs-lookup"><span data-stu-id="1fdea-237">Hence we have not sent `endOfConversation` from Book-a-room bot and when user wants to go back to root context they can simply do that by `start over` command.</span></span>
- <span data-ttu-id="1fdea-238">**Atualização do cartão.**</span><span class="sxs-lookup"><span data-stu-id="1fdea-238">**Card refresh**.</span></span> <span data-ttu-id="1fdea-239">As atções do cartão ainda não são suportadas por meio do Assistente Virtual.</span><span class="sxs-lookup"><span data-stu-id="1fdea-239">Card refreshes is not yet supported through Virtual Assistant.</span></span>
- <span data-ttu-id="1fdea-240">**Extensões de mensagens.:**</span><span class="sxs-lookup"><span data-stu-id="1fdea-240">**Messaging extensions**.:</span></span>
  - <span data-ttu-id="1fdea-241">Atualmente, um Assistente Virtual pode dar suporte a no máximo dez comandos para extensões de mensagens.</span><span class="sxs-lookup"><span data-stu-id="1fdea-241">Currently, a Virtual Assistant can support a maximum of ten commands for messaging extensions.</span></span>
  - <span data-ttu-id="1fdea-242">A configuração de extensões de mensagens não tem como escopo comandos individuais, mas sim para toda a extensão.</span><span class="sxs-lookup"><span data-stu-id="1fdea-242">Configuration of messaging extensions is not scoped to individual commands but for the entire extension itself.</span></span> <span data-ttu-id="1fdea-243">Isso limita a configuração de cada habilidade individual por meio do Assistente Virtual.</span><span class="sxs-lookup"><span data-stu-id="1fdea-243">This limits configuration for each individual skill through Virtual Assistant.</span></span>
  - <span data-ttu-id="1fdea-244">As IDs de comando de extensões de mensagens têm um comprimento máximo de [64](../resources/schema/manifest-schema.md#composeextensions) caracteres e 37 caracteres serão usados para incorporar informações de habilidades.</span><span class="sxs-lookup"><span data-stu-id="1fdea-244">Messaging extensions command IDs have a maximum length of [64 characters](../resources/schema/manifest-schema.md#composeextensions) and 37 characters will be used for embedding skill information.</span></span> <span data-ttu-id="1fdea-245">Assim, as restrições atualizadas para a ID de comando são limitadas a 27 caracteres.</span><span class="sxs-lookup"><span data-stu-id="1fdea-245">Thus, updated constraints for command ID are limited to 27 characters.</span></span>
>
>
