---
title: Criar um Assistente Virtual
description: Como criar um Assistente Virtual e habilidades para uso no Microsoft Teams
localization_priority: Normal
ms.topic: how-to
keywords: bots de assistente virtual do teams
ms.openlocfilehash: 976dacbd8b0bef7a3158d5ff35c5c38d97707c63
ms.sourcegitcommit: e327c9766dfa05abb468cdc71319e3cba7c6c79f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/14/2021
ms.locfileid: "53428720"
---
# <a name="create-virtual-assistant"></a><span data-ttu-id="778dd-104">Criar um Assistente Virtual</span><span class="sxs-lookup"><span data-stu-id="778dd-104">Create Virtual Assistant</span></span> 

<span data-ttu-id="778dd-105">Assistente Virtual é um modelo de código aberto da Microsoft que permite que você crie uma solução de conversação robusta, mantendo o controle total da experiência do usuário, da identidade visual organizacional e dos dados necessários.</span><span class="sxs-lookup"><span data-stu-id="778dd-105">Virtual Assistant is a Microsoft open-source template that enables you to create a robust conversational solution while maintaining full control of user experience, organizational branding, and necessary data.</span></span> <span data-ttu-id="778dd-106">O [Assistente Virtual](https://microsoft.github.io/botframework-solutions/overview/virtual-assistant-template) principal é o bloco de construção básico que reúne as tecnologias da Microsoft necessárias para criar um Assistente Virtual, incluindo o [SDK](https://github.com/microsoft/botframework-sdk)da Estrutura de Bot, o Entendimento de Idioma [(LUIS)](https://www.luis.ai/)e o [QnA Maker](https://www.qnamaker.ai/).</span><span class="sxs-lookup"><span data-stu-id="778dd-106">The [Virtual Assistant core template](https://microsoft.github.io/botframework-solutions/overview/virtual-assistant-template) is the basic building block that brings together the Microsoft technologies required to build a Virtual Assistant, including the [Bot Framework SDK](https://github.com/microsoft/botframework-sdk), [Language Understanding (LUIS)](https://www.luis.ai/), and [QnA Maker](https://www.qnamaker.ai/).</span></span> <span data-ttu-id="778dd-107">Ele também reúne os recursos essenciais, incluindo registro de habilidades, contas vinculadas, intenção de conversa básica para oferecer uma variedade de interações e experiências perfeitas aos usuários.</span><span class="sxs-lookup"><span data-stu-id="778dd-107">It also brings together the essential capabilities including  skills registration, linked accounts, basic conversational intent to offer a range of seamless interactions and experiences to users.</span></span> <span data-ttu-id="778dd-108">Além disso, os recursos do modelo incluem exemplos avançados de habilidades de conversa [reutilizáveis.](https://microsoft.github.io/botframework-solutions/overview/skills)</span><span class="sxs-lookup"><span data-stu-id="778dd-108">In addition, the template capabilities include rich examples of reusable conversational [skills](https://microsoft.github.io/botframework-solutions/overview/skills).</span></span>  <span data-ttu-id="778dd-109">As habilidades individuais são integradas em uma Assistente Virtual para habilitar vários cenários.</span><span class="sxs-lookup"><span data-stu-id="778dd-109">Individual skills are integrated in a Virtual Assistant solution to enable multiple scenarios.</span></span> <span data-ttu-id="778dd-110">Usando o SDK da Estrutura de Bot, as habilidades são apresentadas no formulário de código-fonte, permitindo que você personalize e se estenda conforme necessário.</span><span class="sxs-lookup"><span data-stu-id="778dd-110">Using the Bot Framework SDK, skills are presented in source code form, enabling you to customize and extend as required.</span></span> <span data-ttu-id="778dd-111">Para obter mais informações sobre as habilidades do Bot Framework, consulte [What is a Bot Framework skill](https://microsoft.github.io/botframework-solutions/overview/skills/).</span><span class="sxs-lookup"><span data-stu-id="778dd-111">For more information on skills of Bot Framework, see [What is a Bot Framework skill](https://microsoft.github.io/botframework-solutions/overview/skills/).</span></span> <span data-ttu-id="778dd-112">Este documento orienta você sobre Assistente Virtual de implementação para organizações, como criar um Teams de Assistente Virtual, exemplo relacionado, exemplo de código e limitações de Assistente Virtual.</span><span class="sxs-lookup"><span data-stu-id="778dd-112">This document guides you on Virtual Assistant implementation considerations for organizations, how to create a Teams focused Virtual Assistant, related example, code sample, and limitations of Virtual Assistant.</span></span>
<span data-ttu-id="778dd-113">A imagem a seguir exibe a visão geral do assistente virtual:</span><span class="sxs-lookup"><span data-stu-id="778dd-113">The following image displays the overview of virtual assistant:</span></span>

![Assistente Virtual diagrama de visão geral](../assets/images/bots/virtual-assistant/overview.png)

<span data-ttu-id="778dd-115">As atividades de mensagem de texto são roteadas para habilidades associadas pelo núcleo Assistente Virtual usando um modelo [de](/azure/bot-service/bot-builder-tutorial-dispatch?view=azure-bot-service-4.0&tabs=cs&preserve-view=true) expedição.</span><span class="sxs-lookup"><span data-stu-id="778dd-115">Text message activities are routed to associated skills by the Virtual Assistant core using a [dispatch](/azure/bot-service/bot-builder-tutorial-dispatch?view=azure-bot-service-4.0&tabs=cs&preserve-view=true) model.</span></span> 

## <a name="implementation-considerations"></a><span data-ttu-id="778dd-116">Considerações sobre implementação</span><span class="sxs-lookup"><span data-stu-id="778dd-116">Implementation considerations</span></span>

<span data-ttu-id="778dd-117">A decisão de adicionar um Assistente Virtual inclui muitos determinantes e difere para cada organização.</span><span class="sxs-lookup"><span data-stu-id="778dd-117">The decision to add a Virtual Assistant includes many determinants and differs for each organization.</span></span> <span data-ttu-id="778dd-118">Os fatores de suporte de uma implementação Assistente Virtual para sua organização são:</span><span class="sxs-lookup"><span data-stu-id="778dd-118">The supporting factors of a Virtual Assistant implementation for your organization are as follows:</span></span>

* <span data-ttu-id="778dd-119">Uma equipe central gerencia todas as experiências dos funcionários.</span><span class="sxs-lookup"><span data-stu-id="778dd-119">A central team manages all employee experiences.</span></span> <span data-ttu-id="778dd-120">Ele tem a capacidade de criar uma experiência Assistente Virtual e gerenciar atualizações para a experiência principal, incluindo a adição de novas habilidades.</span><span class="sxs-lookup"><span data-stu-id="778dd-120">It has the capability to build a Virtual Assistant experience and manage updates to the core experience including the addition of new skills.</span></span>
* <span data-ttu-id="778dd-121">Vários aplicativos existem entre funções comerciais e o número deve crescer no futuro.</span><span class="sxs-lookup"><span data-stu-id="778dd-121">Multiple applications exist across business functions and the number is expected to grow in the future.</span></span>
* <span data-ttu-id="778dd-122">Os aplicativos existentes são personalizáveis, pertencentes à organização, e são convertidos em habilidades para um Assistente Virtual.</span><span class="sxs-lookup"><span data-stu-id="778dd-122">Existing applications are customizable, owned by the organization, and are converted into skills for a Virtual Assistant.</span></span>
* <span data-ttu-id="778dd-123">A equipe de experiências do funcionário central é capaz de influenciar personalizações para aplicativos existentes.</span><span class="sxs-lookup"><span data-stu-id="778dd-123">The central employee experiences team is able to influence customizations to existing apps.</span></span> <span data-ttu-id="778dd-124">Ele também fornece orientações necessárias para integrar aplicativos existentes como habilidades Assistente Virtual experiência.</span><span class="sxs-lookup"><span data-stu-id="778dd-124">It also provides necessary guidance for integrating existing applications as skills in Virtual Assistant experience.</span></span>

<span data-ttu-id="778dd-125">A imagem a seguir exibe as funções comerciais de Assistente Virtual:</span><span class="sxs-lookup"><span data-stu-id="778dd-125">The following image displays the business functions of Virtual Assistant:</span></span> 

![A equipe central mantém o assistente e as equipes de função de negócios contribuem com habilidades](../assets/images/bots/virtual-assistant/business-functions.png)

## <a name="create-a-teams-focused-virtual-assistant"></a><span data-ttu-id="778dd-127">Criar um Teams de Assistente Virtual</span><span class="sxs-lookup"><span data-stu-id="778dd-127">Create a Teams-focused Virtual Assistant</span></span>

<span data-ttu-id="778dd-128">A Microsoft publicou um [Visual Studio para](https://marketplace.visualstudio.com/items?itemName=BotBuilder.VirtualAssistantTemplate) a criação de assistentes virtuais e habilidades.</span><span class="sxs-lookup"><span data-stu-id="778dd-128">Microsoft has published a [Visual Studio template](https://marketplace.visualstudio.com/items?itemName=BotBuilder.VirtualAssistantTemplate) for building Virtual Assistants and skills.</span></span> <span data-ttu-id="778dd-129">Com o modelo Visual Studio, você pode criar um Assistente Virtual, alimentado por uma experiência baseada em texto com suporte para cartões rich limitados com ações.</span><span class="sxs-lookup"><span data-stu-id="778dd-129">With the Visual Studio template, you can create a Virtual Assistant, powered by a text based experience with support for limited rich cards with actions.</span></span> <span data-ttu-id="778dd-130">Aprimoramos o modelo Visual Studio base para incluir recursos de Microsoft Teams plataforma e ter excelentes Teams de aplicativos.</span><span class="sxs-lookup"><span data-stu-id="778dd-130">We have enhanced the Visual Studio base template to include Microsoft Teams platform capabilities and power great Teams app experiences.</span></span> <span data-ttu-id="778dd-131">Alguns dos recursos incluem suporte para cartões adaptáveis avançados, módulos de tarefas, equipes ou chats de grupo e extensões de mensagens.</span><span class="sxs-lookup"><span data-stu-id="778dd-131">A few of the capabilities include support for rich Adaptive Cards, task modules, teams or group chats, and messaging extensions.</span></span> <span data-ttu-id="778dd-132">Para obter mais informações sobre como estender Assistente Virtual Microsoft Teams, consulte [Tutorial: Extend Your Assistente Virtual to Microsoft Teams](https://microsoft.github.io/botframework-solutions/clients-and-channels/tutorials/enable-teams/1-intro/).</span><span class="sxs-lookup"><span data-stu-id="778dd-132">For more information on extending Virtual Assistant to Microsoft Teams, see [Tutorial: Extend Your Virtual Assistant to Microsoft Teams](https://microsoft.github.io/botframework-solutions/clients-and-channels/tutorials/enable-teams/1-intro/).</span></span>    
<span data-ttu-id="778dd-133">A imagem a seguir exibe o diagrama de alto nível de uma Assistente Virtual solução:</span><span class="sxs-lookup"><span data-stu-id="778dd-133">The following image displays the high level diagram of a Virtual Assistant solution:</span></span>

![Diagrama de alto nível de uma Assistente Virtual solução](../assets/images/bots/virtual-assistant/high-level-diagram.png)

### <a name="add-adaptive-cards-to-your-virtual-assistant"></a><span data-ttu-id="778dd-135">Adicionar cartões adaptáveis ao seu Assistente Virtual</span><span class="sxs-lookup"><span data-stu-id="778dd-135">Add Adaptive Cards to your Virtual Assistant</span></span>

<span data-ttu-id="778dd-136">Para despachar as solicitações corretamente, Assistente Virtual deve identificar o modelo DEID correto e as habilidades correspondentes associadas a ele.</span><span class="sxs-lookup"><span data-stu-id="778dd-136">To dispatch requests properly, your Virtual Assistant must identify the correct LUIS model and corresponding skill associated with it.</span></span> <span data-ttu-id="778dd-137">No entanto, o mecanismo de expedição não pode ser usado para atividades de ação de cartão como o modelo DEAA associado a uma habilidade, é treinado para textos de ação de cartão.</span><span class="sxs-lookup"><span data-stu-id="778dd-137">However, the dispatching mechanism cannot be used for card action activities as the LUIS model associated with a skill, is trained for card action texts.</span></span> <span data-ttu-id="778dd-138">Os textos de ação do cartão são palavras-chave fixas, pré-definidas e não comentadas de um usuário.</span><span class="sxs-lookup"><span data-stu-id="778dd-138">The card action texts are fixed, pre-defined keywords, and not commented from a user.</span></span>

<span data-ttu-id="778dd-139">Essa desvantagem é resolvida incorporando informações de habilidade na carga de ação do cartão.</span><span class="sxs-lookup"><span data-stu-id="778dd-139">This drawback is resolved this by embedding skill information in the card action payload.</span></span> <span data-ttu-id="778dd-140">Cada habilidade deve incorporar `skillId` no campo de ações de  `value` cartão.</span><span class="sxs-lookup"><span data-stu-id="778dd-140">Every skill should embed `skillId` in the  `value` field of card actions.</span></span> <span data-ttu-id="778dd-141">Você deve garantir que cada atividade de ação de cartão carregue as informações de habilidade relevantes e Assistente Virtual pode utilizar essas informações para a expedição.</span><span class="sxs-lookup"><span data-stu-id="778dd-141">You must ensure that each card action activity carries the relevant skill information, and Virtual Assistant can utilize this information for dispatching.</span></span>

<span data-ttu-id="778dd-142">Você deve fornecer no construtor para garantir que as informações de habilidade `skillId` sempre estão presentes em ações de cartão.</span><span class="sxs-lookup"><span data-stu-id="778dd-142">You must provide `skillId` in the constructor to ensure that the skill information is always present in card actions.</span></span>
<span data-ttu-id="778dd-143">Um código de exemplo de dados de ação de cartão é mostrado na seção a seguir:</span><span class="sxs-lookup"><span data-stu-id="778dd-143">A card action data sample code is shown in the following section:</span></span>
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

<span data-ttu-id="778dd-144">Em seguida, a classe no modelo Assistente Virtual é introduz para extrair da carga `SkillCardActionData` `skillId` de ação do cartão.</span><span class="sxs-lookup"><span data-stu-id="778dd-144">Next, `SkillCardActionData` class in the Virtual Assistant template is introduces to extract `skillId` from the card action payload.</span></span>
<span data-ttu-id="778dd-145">Um trecho de código para extrair da carga de ação  `skillId` do cartão é mostrado na seção a seguir:</span><span class="sxs-lookup"><span data-stu-id="778dd-145">A code snippet to extract  `skillId` from card action payload is shown in the following section:</span></span>

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

<span data-ttu-id="778dd-146">A implementação é feita por um método de extensão na [classe Atividade.](https://github.com/microsoft/botframework-sdk/blob/master/specs/botframework-activity/botframework-activity.md)</span><span class="sxs-lookup"><span data-stu-id="778dd-146">The implementation is done by an extension method in the [Activity](https://github.com/microsoft/botframework-sdk/blob/master/specs/botframework-activity/botframework-activity.md) class.</span></span>
<span data-ttu-id="778dd-147">Um trecho de código para extrair dados de ação de cartão  `skillId` é mostrado na seção a seguir:</span><span class="sxs-lookup"><span data-stu-id="778dd-147">A code snippet to extract  `skillId` from card action data is shown in the following section:</span></span>

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

### <a name="handle-interruptions"></a><span data-ttu-id="778dd-148">Manipular interrupções</span><span class="sxs-lookup"><span data-stu-id="778dd-148">Handle interruptions</span></span>

<span data-ttu-id="778dd-149">Assistente Virtual pode lidar com interrupções em casos em que um usuário tenta invocar uma habilidade enquanto outra habilidade está ativa no momento.</span><span class="sxs-lookup"><span data-stu-id="778dd-149">Virtual Assistant can handle interruptions in cases where a user tries to invoke a skill while another skill is currently active.</span></span> <span data-ttu-id="778dd-150">`TeamsSkillDialog`e são `TeamsSwitchSkillDialog` introduzidos com base em [SkillDialog](https://github.com/microsoft/botframework-solutions/blob/5b46d73e220bbb4fba86c48be532e495535ca78a/sdk/csharp/libraries/microsoft.bot.solutions/Skills/SkillDialog.cs) e [SwitchSkillDialog](https://github.com/microsoft/botframework-solutions/blob/6d40fa8ae05f96b0c5e0464e01361a9e1deb696c/sdk/csharp/libraries/microsoft.bot.solutions/Skills/Dialogs/SwitchSkillDialog.cs)do Bot Framework.</span><span class="sxs-lookup"><span data-stu-id="778dd-150">`TeamsSkillDialog`, and `TeamsSwitchSkillDialog`are introduced based on Bot Framework's [SkillDialog](https://github.com/microsoft/botframework-solutions/blob/5b46d73e220bbb4fba86c48be532e495535ca78a/sdk/csharp/libraries/microsoft.bot.solutions/Skills/SkillDialog.cs) and [SwitchSkillDialog](https://github.com/microsoft/botframework-solutions/blob/6d40fa8ae05f96b0c5e0464e01361a9e1deb696c/sdk/csharp/libraries/microsoft.bot.solutions/Skills/Dialogs/SwitchSkillDialog.cs).</span></span> <span data-ttu-id="778dd-151">Eles permitem que os usuários alternem uma experiência de habilidade de ações de cartão.</span><span class="sxs-lookup"><span data-stu-id="778dd-151">They enable users to switch a skill experience from card actions.</span></span> <span data-ttu-id="778dd-152">Para lidar com essa solicitação, o Assistente Virtual solicita ao usuário uma mensagem de confirmação para alternar habilidades:</span><span class="sxs-lookup"><span data-stu-id="778dd-152">To handle this request, the Virtual Assistant prompts the user with a confirmation message to switch skills:</span></span>

![Prompt de confirmação ao mudar para uma nova habilidade](../assets/images/bots/virtual-assistant/switch-skills-prompt.png)

### <a name="handle-task-module-requests"></a><span data-ttu-id="778dd-154">Manipular solicitações de módulo de tarefa</span><span class="sxs-lookup"><span data-stu-id="778dd-154">Handle task module requests</span></span>

<span data-ttu-id="778dd-155">Para adicionar recursos de módulo de tarefa a um Assistente Virtual, dois métodos adicionais são incluídos no manipulador de Assistente Virtual de atividades: `OnTeamsTaskModuleFetchAsync` e `OnTeamsTaskModuleSubmitAsync` .</span><span class="sxs-lookup"><span data-stu-id="778dd-155">To add task module capabilities to a Virtual Assistant, two additional methods are included in the Virtual Assistant activity handler: `OnTeamsTaskModuleFetchAsync` and `OnTeamsTaskModuleSubmitAsync`.</span></span> <span data-ttu-id="778dd-156">Esses métodos ouvem atividades relacionadas ao módulo de tarefas Assistente Virtual, identificam a habilidade associada à solicitação e encaminham a solicitação para a habilidade identificada.</span><span class="sxs-lookup"><span data-stu-id="778dd-156">These methods listen to task module-related activities from Virtual Assistant, identify the skill associated with the request, and forward the request to the identified skill.</span></span> 

<span data-ttu-id="778dd-157">O encaminhamento de solicitação é feito [por meio do método SkillHttpClient](/dotnet/api/microsoft.bot.builder.integration.aspnet.core.skills.skillhttpclient?view=botbuilder-dotnet-stable&preserve-view=true) `PostActivityAsync` ,.</span><span class="sxs-lookup"><span data-stu-id="778dd-157">Request forwarding is done through the [SkillHttpClient](/dotnet/api/microsoft.bot.builder.integration.aspnet.core.skills.skillhttpclient?view=botbuilder-dotnet-stable&preserve-view=true), `PostActivityAsync` method.</span></span> <span data-ttu-id="778dd-158">Retorna a resposta como `InvokeResponse` a qual é analisado e convertido em `TaskModuleResponse` .</span><span class="sxs-lookup"><span data-stu-id="778dd-158">It returns the response as `InvokeResponse` which is parsed and converted to `TaskModuleResponse` .</span></span>


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

<span data-ttu-id="778dd-159">Uma abordagem semelhante é seguida para a expedição de ações de cartão e respostas do módulo de tarefa.</span><span class="sxs-lookup"><span data-stu-id="778dd-159">A similar approach is followed for card action dispatching and task module responses.</span></span> <span data-ttu-id="778dd-160">Os dados de ação de busca e envio do módulo de tarefa são atualizados para incluir `skillId` .</span><span class="sxs-lookup"><span data-stu-id="778dd-160">Task module fetch and submit action data is updated to include `skillId`.</span></span> <span data-ttu-id="778dd-161">O método Activity Extension extrai da carga que fornece detalhes `GetSkillId` sobre a habilidade que precisa ser `skillId` invocada.</span><span class="sxs-lookup"><span data-stu-id="778dd-161">Activity Extension method `GetSkillId` extracts `skillId` from the payload which provides details about the skill that needs to be invoked.</span></span>

<span data-ttu-id="778dd-162">O trecho de código para `OnTeamsTaskModuleFetchAsync` e os métodos são dados na seção a `OnTeamsTaskModuleSubmitAsync` seguir:</span><span class="sxs-lookup"><span data-stu-id="778dd-162">The code snippet for `OnTeamsTaskModuleFetchAsync` and `OnTeamsTaskModuleSubmitAsync` methods are given in the following section:</span></span>

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

            return invokeResponse.GetTaskModuleResponse();
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

<span data-ttu-id="778dd-163">Além disso, você deve incluir todos os domínios de habilidade na seção no arquivo de manifesto do Assistente Virtual para que os módulos de tarefa invocados por meio de uma habilidade `validDomains` renderizar corretamente.</span><span class="sxs-lookup"><span data-stu-id="778dd-163">Additionally, you must include all skill domains in the `validDomains` section in Virtual Assistant's manifest file so that task modules invoked through a skill render properly.</span></span>

### <a name="handle-collaborative-app-scopes"></a><span data-ttu-id="778dd-164">Manipular escopos de aplicativo colaborativos</span><span class="sxs-lookup"><span data-stu-id="778dd-164">Handle collaborative app scopes</span></span>

<span data-ttu-id="778dd-165">Teams aplicativos podem existir em vários escopos, incluindo chat 1:1, chat em grupo e canais.</span><span class="sxs-lookup"><span data-stu-id="778dd-165">Teams apps can exist in multiple scopes including 1:1 chat, group chat, and channels.</span></span> <span data-ttu-id="778dd-166">O modelo Assistente Virtual principal foi projetado para chats 1:1.</span><span class="sxs-lookup"><span data-stu-id="778dd-166">The core Virtual Assistant template is designed for 1:1 chats.</span></span> <span data-ttu-id="778dd-167">Como parte da experiência de integração, Assistente Virtual solicita aos usuários o nome e mantém o estado do usuário.</span><span class="sxs-lookup"><span data-stu-id="778dd-167">As part of the onboarding experience Virtual Assistant prompts users for name and maintains user state.</span></span> <span data-ttu-id="778dd-168">Como essa experiência de integração não é adequada para chat em grupo ou escopos de canal, ela foi removida.</span><span class="sxs-lookup"><span data-stu-id="778dd-168">Since that onboarding experience is not suited for group chat or channel scopes it has been removed.</span></span>

<span data-ttu-id="778dd-169">As habilidades devem lidar com atividades em vários escopos, como chat 1:1, chat em grupo e conversa de canal.</span><span class="sxs-lookup"><span data-stu-id="778dd-169">Skills should handle activities in multiple scopes, such as 1:1 chat, group chat, and channel conversation.</span></span> <span data-ttu-id="778dd-170">Se nenhum desses escopos tiver suporte, as habilidades deverão responder com uma mensagem apropriada.</span><span class="sxs-lookup"><span data-stu-id="778dd-170">If any of these scopes are not supported, skills must respond with an appropriate message.</span></span>

<span data-ttu-id="778dd-171">As seguintes funções de processamento foram adicionadas ao Assistente Virtual principal:</span><span class="sxs-lookup"><span data-stu-id="778dd-171">The following  processing functions have been added to Virtual Assistant core:</span></span>

* <span data-ttu-id="778dd-172">Assistente Virtual pode ser invocada sem qualquer mensagem de texto de um chat de grupo ou canal.</span><span class="sxs-lookup"><span data-stu-id="778dd-172">Virtual Assistant can be invoked without any text message from a group chat or channel.</span></span>
* <span data-ttu-id="778dd-173">As articulações são limpas antes de enviar a mensagem para o módulo de expedição.</span><span class="sxs-lookup"><span data-stu-id="778dd-173">Articulations are cleaned before sending the message to the dispatch module.</span></span> <span data-ttu-id="778dd-174">Por exemplo, remova o @mention necessário do bot.</span><span class="sxs-lookup"><span data-stu-id="778dd-174">For example, remove the necessary @mention of the bot.</span></span>

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

### <a name="handle-messaging-extensions"></a><span data-ttu-id="778dd-175">Manipular extensões de mensagens</span><span class="sxs-lookup"><span data-stu-id="778dd-175">Handle messaging extensions</span></span>

<span data-ttu-id="778dd-176">Os comandos de uma extensão de mensagens são declarados no arquivo de manifesto do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="778dd-176">The commands for a messaging extension are declared in your app manifest file.</span></span> <span data-ttu-id="778dd-177">A interface do usuário de extensão de mensagens é alimentada por esses comandos.</span><span class="sxs-lookup"><span data-stu-id="778dd-177">The messaging extension user interface is powered by those commands.</span></span> <span data-ttu-id="778dd-178">Para que Assistente Virtual um comando de extensão de mensagens como uma habilidade anexada, o próprio manifesto de um Assistente Virtual deve conter esses comandos.</span><span class="sxs-lookup"><span data-stu-id="778dd-178">For a Virtual Assistant to power a messaging extension command as an attached skill, a Virtual Assistant's own manifest must contain those commands.</span></span> <span data-ttu-id="778dd-179">Você deve adicionar os comandos do manifesto de uma habilidade individual ao manifesto Assistente Virtual do usuário.</span><span class="sxs-lookup"><span data-stu-id="778dd-179">You must add the commands from an individual skill's manifest to the Virtual Assistant's manifest.</span></span> <span data-ttu-id="778dd-180">A ID do comando fornece informações sobre uma habilidade associada, adicionando a ID do aplicativo da habilidade por meio de um separador `:` .</span><span class="sxs-lookup"><span data-stu-id="778dd-180">The command ID provides information about an associated skill by appending the skill's app ID through a separator `:`.</span></span>

<span data-ttu-id="778dd-181">O trecho do arquivo de manifesto de uma habilidade é mostrado na seção a seguir:</span><span class="sxs-lookup"><span data-stu-id="778dd-181">The snippet from a skill's manifest file is shown in the following section:</span></span>

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

<span data-ttu-id="778dd-182">O trecho Assistente Virtual código de arquivo de manifesto correspondente é mostrado na seção a seguir:</span><span class="sxs-lookup"><span data-stu-id="778dd-182">The corresponding Virtual Assistant manifest file code snippet is shown in the following section:</span></span>

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

<span data-ttu-id="778dd-183">Depois que os comandos são invocados por um usuário, o Assistente Virtual pode identificar uma habilidade associada ao analisar a ID do comando, atualizar a atividade removendo o sufixo extra da ID de comando e encaminhá-la para a habilidade `:<skill_id>` correspondente.</span><span class="sxs-lookup"><span data-stu-id="778dd-183">Once the commands are invoked by a user, the Virtual Assistant can identify an associated skill by parsing the command ID, update the activity by removing the extra suffix `:<skill_id>` from the command ID,  and forward it to the corresponding skill.</span></span> <span data-ttu-id="778dd-184">O código de uma habilidade não precisa manipular o sufixo extra.</span><span class="sxs-lookup"><span data-stu-id="778dd-184">The code for a skill doesnot need to handle the extra suffix.</span></span> <span data-ttu-id="778dd-185">Assim, conflitos entre IDs de comando entre habilidades são evitados.</span><span class="sxs-lookup"><span data-stu-id="778dd-185">Thus, conflicts between command IDs across skills are avoided.</span></span> <span data-ttu-id="778dd-186">Com essa abordagem, todos os comandos de pesquisa e ação de uma  habilidade em todos os contextos, como **redação,** **commandBox** e mensagem são alimentados por um Assistente Virtual.</span><span class="sxs-lookup"><span data-stu-id="778dd-186">With this approach, all the search and action commands of a skill within all contexts, such as **compose**, **commandBox**, and **message** are powered by a Virtual Assistant.</span></span>

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

<span data-ttu-id="778dd-187">Algumas atividades de extensão de mensagens não incluem a ID do comando.</span><span class="sxs-lookup"><span data-stu-id="778dd-187">Some messaging extension activities do not include the command ID.</span></span> <span data-ttu-id="778dd-188">Por exemplo, `composeExtension/selectItem` contém apenas o valor da ação chamar toque.</span><span class="sxs-lookup"><span data-stu-id="778dd-188">For example, `composeExtension/selectItem` contains only the value of the invoke tap action.</span></span> <span data-ttu-id="778dd-189">Para identificar a habilidade associada, é anexado a `skillId`  cada cartão de item ao formar uma resposta para `OnTeamsMessagingExtensionQueryAsync` .</span><span class="sxs-lookup"><span data-stu-id="778dd-189">To identify the associated skill, `skillId`  is attached to each item card while forming a response for `OnTeamsMessagingExtensionQueryAsync`.</span></span> <span data-ttu-id="778dd-190">Isso é semelhante à abordagem para [adicionar cartões adaptáveis ao seu Assistente Virtual](#add-adaptive-cards-to-your-virtual-assistant).</span><span class="sxs-lookup"><span data-stu-id="778dd-190">This is similar to the approach for [adding adaptive  cards to your Virtual Assistant](#add-adaptive-cards-to-your-virtual-assistant).</span></span>

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

## <a name="example"></a><span data-ttu-id="778dd-191">Exemplo</span><span class="sxs-lookup"><span data-stu-id="778dd-191">Example</span></span>

<span data-ttu-id="778dd-192">O exemplo a seguir mostra como converter o modelo de aplicativo Book-a-room em uma habilidade de Assistente Virtual: Book-a-room é um Microsoft Teams que permite que os usuários encontrem e reservem rapidamente uma sala de reunião para 30, 60 ou 90 minutos a partir da hora atual.</span><span class="sxs-lookup"><span data-stu-id="778dd-192">The following example shows how to convert the Book-a-room app template to a Virtual Assistant skill: Book-a-room is a Microsoft Teams that allows users quickly to find and reserve a meeting room for 30, 60, or 90 minutes starting from the current time.</span></span> <span data-ttu-id="778dd-193">O tempo padrão é de 30 minutos.</span><span class="sxs-lookup"><span data-stu-id="778dd-193">The default time is 30 minutes.</span></span> <span data-ttu-id="778dd-194">Os escopos de bot book-a-room para conversas pessoais ou 1:1.</span><span class="sxs-lookup"><span data-stu-id="778dd-194">The Book-a-room bot scopes to personal or 1:1 conversations.</span></span> <span data-ttu-id="778dd-195">A imagem a seguir exibe um Assistente Virtual com um **livro uma habilidade de** sala:</span><span class="sxs-lookup"><span data-stu-id="778dd-195">The following image displays a Virtual Assistant with a **book a room** skill:</span></span>

![Assistente Virtual com uma habilidade de "reservar uma sala"](../assets/images/bots/virtual-assistant/book-a-room-skill.png)

<span data-ttu-id="778dd-197">A seguir estão as alterações delta introduzidas para convertê-la em uma habilidade anexada a um Assistente Virtual.</span><span class="sxs-lookup"><span data-stu-id="778dd-197">Followings are the delta changes introduced to convert it to a skill which is attached to a Virtual Assistant.</span></span> <span data-ttu-id="778dd-198">Diretrizes semelhantes são seguidas para converter qualquer bot v4 existente em uma habilidade.</span><span class="sxs-lookup"><span data-stu-id="778dd-198">Similar guidelines are followed to convert any existing v4 bot to a skill.</span></span>

### <a name="skill-manifest"></a><span data-ttu-id="778dd-199">Manifesto de habilidades</span><span class="sxs-lookup"><span data-stu-id="778dd-199">Skill manifest</span></span>

<span data-ttu-id="778dd-200">Um manifesto de habilidades é um arquivo JSON que expõe o ponto de extremidade, a ID, o nome e outros metadados relevantes de uma habilidade.</span><span class="sxs-lookup"><span data-stu-id="778dd-200">A skill manifest is a JSON file that exposes a skill's messaging endpoint, ID, name, and other relevant metadata.</span></span> <span data-ttu-id="778dd-201">Esse manifesto é diferente do manifesto usado para sideload de um aplicativo Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="778dd-201">This manifest is different than the manifest used for sideloading an app in Microsoft Teams.</span></span> <span data-ttu-id="778dd-202">Um Assistente Virtual requer um caminho para esse arquivo como uma entrada para anexar uma habilidade.</span><span class="sxs-lookup"><span data-stu-id="778dd-202">A Virtual Assistant requires a path to this file as an input to attach a skill.</span></span> <span data-ttu-id="778dd-203">Adicionamos o manifesto a seguir à pasta wwwroot do bot.</span><span class="sxs-lookup"><span data-stu-id="778dd-203">We have added the following manifest to the bot's wwwroot folder.</span></span>

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

### <a name="luis-integration"></a><span data-ttu-id="778dd-204">Integração DO LUIS</span><span class="sxs-lookup"><span data-stu-id="778dd-204">LUIS Integration</span></span>

<span data-ttu-id="778dd-205">Assistente Virtual modelo de expedição da Assistente Virtual é criado com base nos modelos DEIS das habilidades anexadas.</span><span class="sxs-lookup"><span data-stu-id="778dd-205">Virtual Assistant's dispatch model is built on top of attached skills' LUIS models.</span></span> <span data-ttu-id="778dd-206">O modelo de expedição identifica a intenção de cada atividade de texto e descobre as habilidades associadas a ela.</span><span class="sxs-lookup"><span data-stu-id="778dd-206">The dispatch model identifies the intent for every text activity and finds out skill associated with it.</span></span>

<span data-ttu-id="778dd-207">Assistente Virtual requer o modelo DEIS de habilidade no `.lu` formato como uma entrada ao anexar uma habilidade.</span><span class="sxs-lookup"><span data-stu-id="778dd-207">Virtual Assistant requires skill's LUIS model in `.lu` format as an input while attaching a skill.</span></span> <span data-ttu-id="778dd-208">O json de LUIS é convertido `.lu` em formato usando a ferramenta botframework-cli.</span><span class="sxs-lookup"><span data-stu-id="778dd-208">LUIS json is converted to `.lu` format using botframework-cli  tool.</span></span>

```json
botskills connect --remoteManifest "<url to skill's manifest>" --luisFolder "<path to the folder containing your Skill's .lu files>" --languages "en-us" --cs
```

```bash
npm i -g @microsoft/botframework-cli
bf luis:convert --in <pathToLUIS.json> --out <pathToLuFile>
```

<span data-ttu-id="778dd-209">O bot book-a-room tem dois comandos principais para os usuários:</span><span class="sxs-lookup"><span data-stu-id="778dd-209">Book-a-room bot has two main commands for users:</span></span>

- `Book room`
- `Manage Favorites`

<span data-ttu-id="778dd-210">Construímos um modelo DEAD compreendendo esses dois comandos.</span><span class="sxs-lookup"><span data-stu-id="778dd-210">We have built a LUIS model by understanding these two commands.</span></span> <span data-ttu-id="778dd-211">Os segredos correspondentes devem ser preenchidos em `cognitivemodels.json` .</span><span class="sxs-lookup"><span data-stu-id="778dd-211">Corresponding secrets must be populated in `cognitivemodels.json`.</span></span> <span data-ttu-id="778dd-212">O arquivo JSON DO LUIS correspondente é encontrado [aqui](https://github.com/OfficeDev/microsoft-teams-apps-bookaroom/blob/nebhagat/microsoft-teams-apps-bookaroom-skill/Deployment/Resources/LU/en-us/book-a-meeting.json).</span><span class="sxs-lookup"><span data-stu-id="778dd-212">The corresponding LUIS JSON file is found [here](https://github.com/OfficeDev/microsoft-teams-apps-bookaroom/blob/nebhagat/microsoft-teams-apps-bookaroom-skill/Deployment/Resources/LU/en-us/book-a-meeting.json).</span></span>
<span data-ttu-id="778dd-213">O arquivo `.lu` correspondente é mostrado na seção a seguir:</span><span class="sxs-lookup"><span data-stu-id="778dd-213">The corresponding `.lu` file is shown in the following section:</span></span>

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

<span data-ttu-id="778dd-214">Com essa abordagem, qualquer comando emitido por um usuário para Assistente Virtual relacionado ou identificado como um comando associado ao bot e é encaminhado para `book room` `manage favorites` essa `Book-a-room` habilidade.</span><span class="sxs-lookup"><span data-stu-id="778dd-214">With this approach, any command issued by a user to Virtual Assistant related to `book room` or `manage favorites` are identified as a command associated with `Book-a-room` bot and is forwarded to this skill.</span></span>
<span data-ttu-id="778dd-215">Por outro lado, `Book-a-room room` o bot precisa usar o modelo DEAD para entender esses comandos se eles não são digitados completos.</span><span class="sxs-lookup"><span data-stu-id="778dd-215">On the other hand, `Book-a-room room` bot needs to use LUIS model to understand these commands if they are not typed full.</span></span> <span data-ttu-id="778dd-216">Por exemplo: `I want to manage my favorite rooms`.</span><span class="sxs-lookup"><span data-stu-id="778dd-216">For example: `I want to manage my favorite rooms`.</span></span>

### <a name="multi-language-support"></a><span data-ttu-id="778dd-217">Suporte a vários idiomas</span><span class="sxs-lookup"><span data-stu-id="778dd-217">Multi-Language support</span></span>

<span data-ttu-id="778dd-218">Como exemplo, um modelo DEAD com apenas cultura em inglês é criado.</span><span class="sxs-lookup"><span data-stu-id="778dd-218">As an example, a LUIS model with only English culture is created.</span></span> <span data-ttu-id="778dd-219">Você pode criar modelos DEIS correspondentes a outros idiomas e adicionar entrada a `cognitivemodels.json` .</span><span class="sxs-lookup"><span data-stu-id="778dd-219">You can create LUIS models corresponding to other languages and add entry to `cognitivemodels.json`.</span></span>

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

<span data-ttu-id="778dd-220">Em paralelo, adicione o `.lu` arquivo correspondente no caminho de luisFolder.</span><span class="sxs-lookup"><span data-stu-id="778dd-220">In parallel, add corresponding `.lu` file in luisFolder path.</span></span> <span data-ttu-id="778dd-221">A estrutura de pastas deve ser a seguinte:</span><span class="sxs-lookup"><span data-stu-id="778dd-221">Folder structure should be as follows:</span></span>

```bash
| - luisFolder

        | - en-us

                | - book-a-meeting.lu

        | - your_language_culture

                | - book-a-meeting.lu
```

<span data-ttu-id="778dd-222">Para modificar `languages` o parâmetro, atualize o comando botskills da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="778dd-222">To modify `languages` parameter, update botskills command as follows:</span></span>

```json
botskills connect --remoteManifest "<url to skill's manifest>" --luisFolder "<path to luisFolder>" --languages "en-us, your_language_culture" --cs
```

<span data-ttu-id="778dd-223">Assistente Virtual usa `SetLocaleMiddleware` para identificar a localidade atual e invocar o modelo de expedição correspondente.</span><span class="sxs-lookup"><span data-stu-id="778dd-223">Virtual Assistant uses `SetLocaleMiddleware` to identify current locale and invoke corresponding dispatch model.</span></span> <span data-ttu-id="778dd-224">A atividade da estrutura bot tem o campo de localidade que é usado por esse middleware.</span><span class="sxs-lookup"><span data-stu-id="778dd-224">Bot framework activity has locale field which is used by this middleware.</span></span> <span data-ttu-id="778dd-225">Você também pode usar o mesmo para suas habilidades.</span><span class="sxs-lookup"><span data-stu-id="778dd-225">You can use the same for your skill as well.</span></span> <span data-ttu-id="778dd-226">Book-a-room bot does not use this middleware and instead gets locale from Bot framework activity's [clientInfo entity](https://github.com/microsoft/botframework-sdk/blob/master/specs/botframework-activity/botframework-activity.md#clientinfo).</span><span class="sxs-lookup"><span data-stu-id="778dd-226">Book-a-room bot does not use this middleware and instead gets locale from Bot framework activity's [clientInfo entity](https://github.com/microsoft/botframework-sdk/blob/master/specs/botframework-activity/botframework-activity.md#clientinfo).</span></span>

### <a name="claim-validation"></a><span data-ttu-id="778dd-227">Validação de declaração</span><span class="sxs-lookup"><span data-stu-id="778dd-227">Claim validation</span></span>

<span data-ttu-id="778dd-228">Adicionamos [claimsValidator para](https://github.com/nebhagat/msteams-virtual-assistant-dotnet/blob/master/msteams-virtual-assistant-dotnet/Authentication/AllowedCallersClaimsValidator.cs) restringir os chamadores à habilidade.</span><span class="sxs-lookup"><span data-stu-id="778dd-228">We have added [claimsValidator](https://github.com/nebhagat/msteams-virtual-assistant-dotnet/blob/master/msteams-virtual-assistant-dotnet/Authentication/AllowedCallersClaimsValidator.cs) to restrict callers to the skill.</span></span> <span data-ttu-id="778dd-229">Para permitir que um Assistente Virtual chame essa habilidade, preencha a matriz com essa ID de aplicativo Assistente Virtual de aplicativo `AllowedCallers` `appsettings` específico.</span><span class="sxs-lookup"><span data-stu-id="778dd-229">To allow a Virtual Assistant to call this skill, populate `AllowedCallers` array from `appsettings` with that particular Virtual Assistant's app ID.</span></span>

```
"AllowedCallers": [ "<caller_VA1_appId>", "<caller_VA2_appId>" ],
```

<span data-ttu-id="778dd-230">A matriz de chamadores permitidos pode restringir quais clientes de habilidades podem acessar a habilidade.</span><span class="sxs-lookup"><span data-stu-id="778dd-230">The allowed callers array can restrict which skill consumers can access the skill.</span></span> <span data-ttu-id="778dd-231">Adicione entrada única `*` a essa matriz, para aceitar chamadas de qualquer consumidor de habilidades.</span><span class="sxs-lookup"><span data-stu-id="778dd-231">Add single entry `*` to this array, to accept calls from any skill consumer.</span></span>

```
"AllowedCallers": [ "*" ],
```

<span data-ttu-id="778dd-232">Para obter mais informações sobre como adicionar validação de declarações a uma habilidade, [consulte add claims validation to skill](/azure/bot-service/skill-implement-skill?view=azure-bot-service-4.0&tabs=cs#claims-validator&preserve-view=true).</span><span class="sxs-lookup"><span data-stu-id="778dd-232">For more information on adding claims validation to a skill, see [add claims validation to skill](/azure/bot-service/skill-implement-skill?view=azure-bot-service-4.0&tabs=cs#claims-validator&preserve-view=true).</span></span>

### <a name="limitation-of-card-refresh"></a><span data-ttu-id="778dd-233">Limitação da atualização do cartão</span><span class="sxs-lookup"><span data-stu-id="778dd-233">Limitation of card refresh</span></span> 

<span data-ttu-id="778dd-234">A atualização da atividade, como a atualização do cartão, ainda não é suportada Assistente Virtual ([problema github](https://github.com/microsoft/botbuilder-dotnet/issues/3686)).</span><span class="sxs-lookup"><span data-stu-id="778dd-234">Updating activity, such as card refresh is not supported yet through Virtual Assistant ([github issue](https://github.com/microsoft/botbuilder-dotnet/issues/3686)).</span></span> <span data-ttu-id="778dd-235">Portanto, substituímos todas as chamadas de atualização de cartão `UpdateActivityAsync` por postagem de novas chamadas de `SendActivityAsync` cartão.</span><span class="sxs-lookup"><span data-stu-id="778dd-235">Hence, we have replaced all card refresh calls `UpdateActivityAsync` with posting new card calls `SendActivityAsync`.</span></span>

### <a name="card-actions-and-task-module-flows"></a><span data-ttu-id="778dd-236">Ações de cartão e fluxos de módulos de tarefa</span><span class="sxs-lookup"><span data-stu-id="778dd-236">Card actions and task module flows</span></span>

<span data-ttu-id="778dd-237">Para encaminhar atividades de ação de cartão ou módulo de tarefa a uma habilidade associada, a habilidade deve incorporar `skillId` a ela.</span><span class="sxs-lookup"><span data-stu-id="778dd-237">To forward card action or task module activities to an associated skill, the skill must embed `skillId` to it.</span></span>
<span data-ttu-id="778dd-238">`Book-a-room` ação de cartão de bot, busca de módulo de tarefa e envio de cargas de ação são modificadas para conter `skillId` como um parâmetro.</span><span class="sxs-lookup"><span data-stu-id="778dd-238">`Book-a-room` bot card action, task module fetch and submit action payloads are modified to contain `skillId` as a parameter.</span></span> 

<span data-ttu-id="778dd-239">Para obter mais [informações, consulte esta](/microsoftteams/platform/samples/virtual-assistant#add-adaptive-cards-to-your-virtual-assistant) seção nesta documentação.</span><span class="sxs-lookup"><span data-stu-id="778dd-239">For more information refer [this](/microsoftteams/platform/samples/virtual-assistant#add-adaptive-cards-to-your-virtual-assistant) section from this documentation.</span></span>

### <a name="handle-activities-from-group-chat-or-channel-scope"></a><span data-ttu-id="778dd-240">Manipular atividades do chat de grupo ou do escopo do canal</span><span class="sxs-lookup"><span data-stu-id="778dd-240">Handle activities from group chat or channel scope</span></span>

<span data-ttu-id="778dd-241">`Book-a-room bot` foi projetado para chats privados, como apenas escopo pessoal ou 1:1.</span><span class="sxs-lookup"><span data-stu-id="778dd-241">`Book-a-room bot` is designed for private chats, such as personal or 1:1 scope only.</span></span> <span data-ttu-id="778dd-242">Como personalizaremos o Assistente Virtual para dar suporte aos escopos de chat e canal de grupo, o Assistente Virtual deve ser invocado dos escopos de canal e, portanto, o bot deve obter atividades para o `Book-a-room` mesmo escopo.</span><span class="sxs-lookup"><span data-stu-id="778dd-242">Since we have customized Virtual Assistant to support group chat and channel scopes, the Virtual Assistant must be invoked from the channel scopes and thus, `Book-a-room` bot must get activities for the same scope.</span></span> <span data-ttu-id="778dd-243">Portanto, `Book-a-room` o bot é personalizado para lidar com essas atividades.</span><span class="sxs-lookup"><span data-stu-id="778dd-243">Hence `Book-a-room`bot is customized to handle those activities.</span></span> <span data-ttu-id="778dd-244">Você pode encontrar os métodos de check-in `OnMessageActivityAsync` do manipulador de atividades do `Book-a-room` bot.</span><span class="sxs-lookup"><span data-stu-id="778dd-244">You can find the check in `OnMessageActivityAsync` methods of `Book-a-room` bot's activity handler.</span></span>

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

<span data-ttu-id="778dd-245">Você também pode aproveitar as habilidades existentes do repositório [de Soluções](https://github.com/microsoft/botframework-components/tree/main/skills/csharp) da Estrutura de Bot ou criar uma nova habilidade completamente do zero.</span><span class="sxs-lookup"><span data-stu-id="778dd-245">You can also leverage existing skills from [Bot Framework Solutions repository](https://github.com/microsoft/botframework-components/tree/main/skills/csharp) or create a new skill altogether from scratch.</span></span> <span data-ttu-id="778dd-246">Para criar uma nova habilidade, consulte [tutoriais para criar uma nova habilidade.](https://microsoft.github.io/botframework-solutions/overview/skills/)</span><span class="sxs-lookup"><span data-stu-id="778dd-246">For creating a new skill, see [tutorials to create a new skill](https://microsoft.github.io/botframework-solutions/overview/skills/).</span></span> <span data-ttu-id="778dd-247">Para Assistente Virtual documentação de arquitetura de habilidades e habilidades,[consulte Assistente Virtual e arquitetura de habilidades.](/azure/bot-service/skills-conceptual?view=azure-bot-service-4.0&preserve-view=true)</span><span class="sxs-lookup"><span data-stu-id="778dd-247">For Virtual Assistant and skills architecture documentation, see[Virtual Assistant and skills architecture](/azure/bot-service/skills-conceptual?view=azure-bot-service-4.0&preserve-view=true).</span></span>  

## <a name="limitations-of-virtual-assistant"></a><span data-ttu-id="778dd-248">Limitações de Assistente Virtual</span><span class="sxs-lookup"><span data-stu-id="778dd-248">Limitations of Virtual Assistant</span></span> 

* <span data-ttu-id="778dd-249">**EndOfConversation**: Uma habilidade deve enviar uma `endOfConversation` atividade quando terminar uma conversa.</span><span class="sxs-lookup"><span data-stu-id="778dd-249">**EndOfConversation**: A skill must send an `endOfConversation` activity when it finishes a conversation.</span></span> <span data-ttu-id="778dd-250">Com base na atividade, um Assistente Virtual termina o contexto com essa habilidade específica e volta ao contexto raiz do Assistente Virtual do usuário.</span><span class="sxs-lookup"><span data-stu-id="778dd-250">Based on the activity, a Virtual Assistant ends context with that particular skill and gets back into Virtual Assistant's root context.</span></span> <span data-ttu-id="778dd-251">Para o bot book-a-room, não há um estado claro em que a conversa seja encerrada.</span><span class="sxs-lookup"><span data-stu-id="778dd-251">For Book-a-room bot, there is no clear state where conversation is ended.</span></span> <span data-ttu-id="778dd-252">Portanto, não enviamos do bot e quando o usuário deseja voltar ao contexto raiz, ele `endOfConversation` pode simplesmente fazer isso por `Book-a-room` `start over` comando.</span><span class="sxs-lookup"><span data-stu-id="778dd-252">Hence we have not sent `endOfConversation` from `Book-a-room` bot and when user wants to go back to root context they can simply do that by `start over` command.</span></span>  
* <span data-ttu-id="778dd-253">**Atualização do** cartão : Ainda não há suporte para atualização de cartão por meio Assistente Virtual.</span><span class="sxs-lookup"><span data-stu-id="778dd-253">**Card refresh**: Card refresh is not yet supported through Virtual Assistant.</span></span>  
* <span data-ttu-id="778dd-254">**Extensões de mensagens**:</span><span class="sxs-lookup"><span data-stu-id="778dd-254">**Messaging extensions**:</span></span>
  * <span data-ttu-id="778dd-255">Atualmente, um Assistente Virtual pode suportar no máximo dez comandos para extensões de mensagens.</span><span class="sxs-lookup"><span data-stu-id="778dd-255">Currently, a Virtual Assistant can support a maximum of ten commands for messaging extensions.</span></span>
  * <span data-ttu-id="778dd-256">A configuração de extensões de mensagens não tem escopo para comandos individuais, mas para toda a extensão em si.</span><span class="sxs-lookup"><span data-stu-id="778dd-256">Configuration of messaging extensions is not scoped to individual commands but for the entire extension itself.</span></span> <span data-ttu-id="778dd-257">Isso limita a configuração para cada habilidade individual por meio Assistente Virtual.</span><span class="sxs-lookup"><span data-stu-id="778dd-257">This limits configuration for each individual skill through Virtual Assistant.</span></span>
  * <span data-ttu-id="778dd-258">As IDs de comando de extensões de mensagens têm um comprimento máximo de [64](../resources/schema/manifest-schema.md#composeextensions) caracteres e 37 caracteres são usados para incorporar informações de habilidades.</span><span class="sxs-lookup"><span data-stu-id="778dd-258">Messaging extensions command IDs have a maximum length of [64 characters](../resources/schema/manifest-schema.md#composeextensions) and 37 characters are used for embedding skill information.</span></span> <span data-ttu-id="778dd-259">Assim, as restrições atualizadas para a ID de comando são limitadas a 27 caracteres.</span><span class="sxs-lookup"><span data-stu-id="778dd-259">Thus, updated constraints for command ID are limited to 27 characters.</span></span>

<span data-ttu-id="778dd-260">Você também pode aproveitar as habilidades existentes do repositório [de Soluções](https://github.com/microsoft/botframework-components/tree/main/skills/csharp) da Estrutura de Bot ou criar uma nova habilidade completamente do zero.</span><span class="sxs-lookup"><span data-stu-id="778dd-260">You can also leverage existing skills from [Bot Framework Solutions repository](https://github.com/microsoft/botframework-components/tree/main/skills/csharp) or create a new skill altogether from scratch.</span></span> <span data-ttu-id="778dd-261">Tutoriais para o posterior podem ser [encontrados aqui](https://microsoft.github.io/botframework-solutions/overview/skills/).</span><span class="sxs-lookup"><span data-stu-id="778dd-261">Tutorials for the later can be found [here](https://microsoft.github.io/botframework-solutions/overview/skills/).</span></span> <span data-ttu-id="778dd-262">Consulte a [documentação para Assistente Virtual](/azure/bot-service/skills-conceptual?view=azure-bot-service-4.0&preserve-view=true) e arquitetura de habilidades.</span><span class="sxs-lookup"><span data-stu-id="778dd-262">Please refer to [documentation](/azure/bot-service/skills-conceptual?view=azure-bot-service-4.0&preserve-view=true) for Virtual Assistant and skills architecture.</span></span>

## <a name="code-sample"></a><span data-ttu-id="778dd-263">Exemplo de código</span><span class="sxs-lookup"><span data-stu-id="778dd-263">Code sample</span></span>

| <span data-ttu-id="778dd-264">**Nome do exemplo**</span><span class="sxs-lookup"><span data-stu-id="778dd-264">**Sample name**</span></span> | <span data-ttu-id="778dd-265">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="778dd-265">**Description**</span></span> | <span data-ttu-id="778dd-266">**C#**  **.NET**</span><span class="sxs-lookup"><span data-stu-id="778dd-266">**C#**  **.NET**</span></span> |
|----------|-----------------|---------------------------|
| <span data-ttu-id="778dd-267">Modelo de visual studio atualizado</span><span class="sxs-lookup"><span data-stu-id="778dd-267">Updated visual studio template</span></span> | <span data-ttu-id="778dd-268">Modelo personalizado para dar suporte aos recursos das equipes.</span><span class="sxs-lookup"><span data-stu-id="778dd-268">Customized template to support teams capabilities.</span></span> | [<span data-ttu-id="778dd-269">Exibir</span><span class="sxs-lookup"><span data-stu-id="778dd-269">View</span></span>](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/app-virtual-assistant/csharp) |
| <span data-ttu-id="778dd-270">Book-a-room bot skill code</span><span class="sxs-lookup"><span data-stu-id="778dd-270">Book-a-room bot skill code</span></span> | <span data-ttu-id="778dd-271">Permite que você encontre e reserve rapidamente uma sala de reunião em qualquer lugar.</span><span class="sxs-lookup"><span data-stu-id="778dd-271">Lets you quickly find and book a meeting room on the go.</span></span> | [<span data-ttu-id="778dd-272">Exibir</span><span class="sxs-lookup"><span data-stu-id="778dd-272">View</span></span>](https://github.com/OfficeDev/microsoft-teams-apps-bookaroom/tree/nebhagat/microsoft-teams-apps-bookaroom-skill) |


## <a name="see-also"></a><span data-ttu-id="778dd-273">Confira também</span><span class="sxs-lookup"><span data-stu-id="778dd-273">See also</span></span>

* [<span data-ttu-id="778dd-274">Integrar aplicativos Web</span><span class="sxs-lookup"><span data-stu-id="778dd-274">Integrate web apps</span></span>](~/samples/integrate-web-apps-overview.md)
* [<span data-ttu-id="778dd-275">Book-a-room</span><span class="sxs-lookup"><span data-stu-id="778dd-275">Book-a-room</span></span>](app-templates.md#book-a-room)
* [<span data-ttu-id="778dd-276">Microsoft Teams bot</span><span class="sxs-lookup"><span data-stu-id="778dd-276">Microsoft Teams bot</span></span>](../bots/what-are-bots.md)
