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
# <a name="create-virtual-assistant"></a>Criar um Assistente Virtual 

Virtual Assistant é um modelo de código aberto da Microsoft que permite criar uma solução de conversação robusta, mantendo o controle total da experiência do usuário, da marca organizacional e dos dados necessários. O [modelo principal do Virtual Assistant](https://microsoft.github.io/botframework-solutions/overview/virtual-assistant-template) é o bloco básico de construção que reúne as tecnologias microsoft necessárias para construir um Assistente Virtual, incluindo o Bot Framework [SDK,](https://github.com/microsoft/botframework-sdk) [Language Understanding (LUIS)](https://www.luis.ai/)e [QnA Maker](https://www.qnamaker.ai/). Também reúne os recursos essenciais, incluindo registro de habilidades, contas vinculadas, intenção conversacional básica para oferecer uma gama de interações e experiências perfeitas aos usuários. Além disso, os recursos do modelo incluem exemplos ricos de [habilidades](https://microsoft.github.io/botframework-solutions/overview/skills)de conversação reutilizáveis.  As habilidades individuais são integradas em uma solução de Assistente Virtual para habilitar vários cenários. Usando o Bot Framework SDK, as habilidades são apresentadas no formulário de código-fonte, permitindo que você personalize e se estenda conforme necessário. Para obter mais informações sobre as habilidades do Bot Framework, consulte [o que é uma habilidade do Bot Framework](https://microsoft.github.io/botframework-solutions/overview/skills/). Este documento orienta você sobre considerações de implementação do Virtual Assistant para organizações, como criar um Assistente Virtual focado em Teams, exemplo relacionado, amostra de código e limitações do Assistente Virtual.
A imagem a seguir exibe a visão geral do assistente virtual:

![Diagrama de visão geral do assistente virtual](../assets/images/bots/virtual-assistant/overview.png)

As atividades de mensagem de texto são roteadas para habilidades associadas pelo núcleo assistente virtual usando um modelo [de despacho.](/azure/bot-service/bot-builder-tutorial-dispatch?view=azure-bot-service-4.0&tabs=cs&preserve-view=true) 

## <a name="implementation-considerations"></a>Considerações de implementação

A decisão de adicionar um Assistente Virtual inclui muitos determinantes e difere para cada organização. Os fatores de suporte de uma implementação do Assistente Virtual para sua organização são os seguintes:

* Uma equipe central gerencia todas as experiências dos funcionários. Ele tem a capacidade de construir uma experiência de Assistente Virtual e gerenciar atualizações para a experiência principal, incluindo a adição de novas habilidades.
* Existem várias aplicações em todas as funções de negócios e espera-se que o número cresça no futuro.
* Os aplicativos existentes são personalizáveis, de propriedade da organização, e são convertidos em habilidades para um Assistente Virtual.
* A equipe central de experiências dos funcionários é capaz de influenciar personalizações em aplicativos existentes. Também fornece orientações necessárias para integrar aplicativos existentes como habilidades na experiência do Assistente Virtual.

A imagem a seguir exibe as funções de negócios do Assistente Virtual: 

![Equipe central mantém o assistente, e equipes de funções de negócios contribuem com habilidades](../assets/images/bots/virtual-assistant/business-functions.png)

## <a name="create-a-teams-focused-virtual-assistant"></a>Crie um assistente virtual focado em Teams

A Microsoft publicou um [modelo Visual Studio](https://marketplace.visualstudio.com/items?itemName=BotBuilder.VirtualAssistantTemplate) para a construção de Assistentes Virtuais e habilidades. Com o modelo Visual Studio, você pode criar um Assistente Virtual, alimentado por uma experiência baseada em texto com suporte para cartões ricos limitados com ações. Nós melhoramos o modelo base de Visual Studio para incluir Microsoft Teams recursos da plataforma e potencialar grandes experiências de Teams aplicativos. Alguns dos recursos incluem suporte para cartões adaptativos ricos, módulos de tarefas, equipes ou chats em grupo e extensões de mensagens. Para obter mais informações sobre a extensão do Assistente Virtual para Microsoft Teams, consulte [Tutorial: Amplie seu assistente virtual para Microsoft Teams](https://microsoft.github.io/botframework-solutions/clients-and-channels/tutorials/enable-teams/1-intro/).    
A imagem a seguir exibe o diagrama de alto nível de uma solução de Assistente Virtual:

![Diagrama de alto nível de uma solução de Assistente Virtual](../assets/images/bots/virtual-assistant/high-level-diagram.png)

### <a name="add-adaptive-cards-to-your-virtual-assistant"></a>Adicione cartões adaptativos ao seu assistente virtual

Para despachar as solicitações corretamente, o Assistente Virtual deve identificar o modelo LUIS correto e a habilidade correspondente associada a ele. No entanto, o mecanismo de expedição não pode ser usado para atividades de ação de cartão, pois o modelo LUIS associado a uma habilidade, é treinado para textos de ação de cartão. Os textos de ação do cartão são fixos, palavras-chave pré-definidas e não são comentados por um usuário.

Essa desvantagem é resolvida incorporando informações de habilidade na carga de ação do cartão. Todas as habilidades devem ser incorporadas `skillId` no campo das ações de  `value` cartas. Você deve garantir que cada atividade de ação de cartão carregue as informações de habilidade relevantes, e o Assistente Virtual pode utilizar essas informações para despachar.

Você deve fornecer `skillId` no construtor para garantir que as informações de habilidade estão sempre presentes nas ações do cartão.
Um código de amostra de dados de ação do cartão é mostrado na seguinte seção:
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

Em seguida, `SkillCardActionData` a classe no modelo assistente virtual é introduz para extrair da carga de `skillId` ação do cartão.
Um trecho de código para extrair  `skillId` da carga de ação do cartão é mostrado na seguinte seção:

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

A implementação é feita por um método de extensão na classe [Atividade.](https://github.com/microsoft/botframework-sdk/blob/master/specs/botframework-activity/botframework-activity.md)
Um trecho de código para extrair  `skillId` dos dados de ação do cartão é mostrado na seguinte seção:

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

### <a name="handle-interruptions"></a>Interrupções no manuseio

O Virtual Assistant pode lidar com interrupções nos casos em que um usuário tenta invocar uma habilidade enquanto outra habilidade está ativa no momento. `TeamsSkillDialog`, e `TeamsSwitchSkillDialog` são introduzidos com base no [SkillDialog](https://github.com/microsoft/botframework-solutions/blob/5b46d73e220bbb4fba86c48be532e495535ca78a/sdk/csharp/libraries/microsoft.bot.solutions/Skills/SkillDialog.cs) do Bot Framework e [no SwitchSkillDialog](https://github.com/microsoft/botframework-solutions/blob/6d40fa8ae05f96b0c5e0464e01361a9e1deb696c/sdk/csharp/libraries/microsoft.bot.solutions/Skills/Dialogs/SwitchSkillDialog.cs). Eles permitem que os usuários alternem uma experiência de habilidade a partir de ações de cartão. Para lidar com essa solicitação, o Assistente Virtual solicita ao usuário uma mensagem de confirmação para mudar as habilidades:

![Prompt de confirmação ao mudar para uma nova habilidade](../assets/images/bots/virtual-assistant/switch-skills-prompt.png)

### <a name="handle-task-module-requests"></a>Manuseie as solicitações do módulo de tarefa

Para adicionar recursos de módulo de tarefa a um Assistente Virtual, dois métodos adicionais estão incluídos no manipulador de atividades do Assistente Virtual: `OnTeamsTaskModuleFetchAsync` e `OnTeamsTaskModuleSubmitAsync` . Esses métodos ouvem atividades relacionadas ao módulo de tarefa do Virtual Assistant, identificam a habilidade associada à solicitação e encaminham a solicitação para a habilidade identificada. 

O encaminhamento da solicitação é feito através do [Método SkillHttpClient](/dotnet/api/microsoft.bot.builder.integration.aspnet.core.skills.skillhttpclient?view=botbuilder-dotnet-stable&preserve-view=true) `PostActivityAsync` . Ele retorna a resposta como `InvokeResponse` a qual é analisado e convertido para `TaskModuleResponse` .


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

Uma abordagem semelhante é seguida para o envio de ação do cartão e respostas do módulo de tarefa. O módulo de tarefas busca e envio de dados de ação é atualizado para incluir `skillId` . O método `GetSkillId` de extensão de atividade extrai `skillId` da carga útil que fornece detalhes sobre a habilidade que precisa ser invocada.

O trecho de código `OnTeamsTaskModuleFetchAsync` e `OnTeamsTaskModuleSubmitAsync` os métodos são dados na seguinte seção:

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

Além disso, você deve incluir todos os domínios de habilidade na `validDomains` seção no arquivo manifesto do Virtual Assistant para que os módulos de tarefa sejam invocados por meio de uma renderização de habilidade corretamente.

### <a name="handle-collaborative-app-scopes"></a>Lidar com escopos de aplicativos colaborativos

Teams aplicativos podem existir em vários escopos, incluindo bate-papo 1:1, bate-papo em grupo e canais. O modelo principal do Assistente Virtual foi projetado para bate-papos 1:1. Como parte da experiência de onboarding, o Virtual Assistant solicita nome aos usuários e mantém o estado do usuário. Uma vez que essa experiência de onboarding não é adequada para o bate-papo em grupo ou escopos de canal, ele foi removido.

As habilidades devem lidar com atividades em vários escopos, como bate-papo 1:1, bate-papo em grupo e conversa de canal. Se algum desses escopos não for suportado, as habilidades devem responder com uma mensagem apropriada.

As seguintes funções de processamento foram adicionadas ao núcleo do Assistente Virtual:

* O Assistente Virtual pode ser invocado sem qualquer mensagem de texto de um chat ou canal em grupo.
* As articulações são limpas antes de enviar a mensagem para o módulo de despacho. Por exemplo, remova as @mention necessárias do bot.

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

### <a name="handle-messaging-extensions"></a>Manuseie extensões de mensagens

Os comandos para uma extensão de mensagens são declarados no arquivo manifesto do aplicativo. A interface do usuário de extensão de mensagens é alimentada por esses comandos. Para um Assistente Virtual alimentar um comando de extensão de mensagens como uma habilidade anexada, o próprio manifesto de um assistente virtual deve conter esses comandos. Você deve adicionar os comandos de um manifesto de habilidade individual ao manifesto do Assistente Virtual. O ID de comando fornece informações sobre uma habilidade associada, anexando o ID do aplicativo da habilidade através de um separador `:` .

O trecho do arquivo manifesto de uma habilidade é mostrado na seguinte seção:

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

O trecho de código de arquivo de manifesto do Assistente Virtual correspondente é mostrado na seguinte seção:

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

Uma vez que os comandos são invocados por um usuário, o Assistente Virtual pode identificar uma habilidade associada analisando o ID de comando, atualizar a atividade removendo o sufixo extra `:<skill_id>` do ID de comando e encaminhá-lo para a habilidade correspondente. O código para uma habilidade não precisa lidar com o sufixo extra. Assim, os conflitos entre as IDs de comando através de habilidades são evitados. Com essa abordagem, todos os comandos de busca e ação de uma habilidade dentro de todos os contextos, como **compor,** **commandBox** e **mensagem** são alimentados por um Assistente Virtual.

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

Algumas atividades de extensão de mensagens não incluem o ID de comando. Por exemplo, `composeExtension/selectItem` contém apenas o valor da ação de toque de invocação. Para identificar a habilidade associada, `skillId`  é anexado a cada cartão de item enquanto forma uma resposta para `OnTeamsMessagingExtensionQueryAsync` . Isso é semelhante à abordagem para [adicionar cartões adaptativos ao seu Assistente Virtual](#add-adaptive-cards-to-your-virtual-assistant).

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

## <a name="example"></a>Exemplo

O exemplo a seguir mostra como converter o modelo de aplicativo Book-a-room para uma habilidade de Assistente Virtual: Book-a-room é uma Microsoft Teams que permite aos usuários encontrar e reservar rapidamente uma sala de reunião por 30, 60 ou 90 minutos a partir do momento atual. O tempo padrão é de 30 minutos. Os escopos do robô Book-a-room para conversas pessoais ou 1:1. A imagem a seguir exibe um Assistente Virtual com um livro uma habilidade **de quarto:**

![Assistente Virtual com uma habilidade de "reservar um quarto"](../assets/images/bots/virtual-assistant/book-a-room-skill.png)

A seguir estão as alterações delta introduzidas para convertê-lo em uma habilidade que é anexada a um Assistente Virtual. Diretrizes semelhantes são seguidas para converter qualquer bot v4 existente em uma habilidade.

### <a name="skill-manifest"></a>Manifesto de habilidades

Um manifesto de habilidade é um arquivo JSON que expõe o ponto final de mensagens de uma habilidade, ID, nome e outros metadados relevantes. Este manifesto é diferente do manifesto usado para carregar um aplicativo em Microsoft Teams. Um Assistente Virtual requer um caminho para este arquivo como uma entrada para anexar uma habilidade. Adicionamos o seguinte manifesto à pasta wwwroot do bot.

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

### <a name="luis-integration"></a>Integração LUIS

O modelo de despacho do Virtual Assistant é construído em cima dos modelos LUIS de habilidades anexadas. O modelo de despacho identifica a intenção para cada atividade de texto e descobre a habilidade associada a ela.

O Assistente Virtual requer o modelo LUIS da habilidade em `.lu` formato como uma entrada ao anexar uma habilidade. LUIS json é convertido em `.lu` formato usando a ferramenta botframework-cli.

```json
botskills connect --remoteManifest "<url to skill's manifest>" --luisFolder "<path to the folder containing your Skill's .lu files>" --languages "en-us" --cs
```

```bash
npm i -g @microsoft/botframework-cli
bf luis:convert --in <pathToLUIS.json> --out <pathToLuFile>
```

O bot book-a-room tem dois comandos principais para os usuários:

- `Book room`
- `Manage Favorites`

Construímos um modelo LUIS entendendo esses dois comandos. Os segredos correspondentes devem ser preenchidos em `cognitivemodels.json` . O arquivo LUIS JSON correspondente é encontrado [aqui](https://github.com/OfficeDev/microsoft-teams-apps-bookaroom/blob/nebhagat/microsoft-teams-apps-bookaroom-skill/Deployment/Resources/LU/book-a-meeting.json).
O arquivo correspondente `.lu` é mostrado na seguinte seção:

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

Com essa abordagem, qualquer comando emitido por um usuário para Assistente Virtual relacionado `book room` ou é identificado como um comando associado ao bot e é encaminhado para essa `manage favorites` `Book-a-room` habilidade.
Por outro lado, o bot precisa usar o `Book-a-room room` modelo LUIS para entender esses comandos se eles não estiverem digitado completos. Por exemplo: `I want to manage my favorite rooms`.

### <a name="multi-language-support"></a>Suporte multi-idioma

Como exemplo, um modelo LUIS com apenas cultura inglesa é criado. Você pode criar modelos LUIS correspondentes a outros idiomas e adicionar entrada a `cognitivemodels.json` .

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

Em paralelo, adicione o arquivo correspondente `.lu` no caminho luisPato. A estrutura da pasta deve ser a seguinte:

```bash
| - luisFolder

        | - en-us

                | - book-a-meeting.lu

        | - your_language_culture

                | - book-a-meeting.lu
```

Para modificar `languages` o parâmetro, atualize o comando botskills da seguinte forma:

```json
botskills connect --remoteManifest "<url to skill's manifest>" --luisFolder "<path to luisFolder>" --languages "en-us, your_language_culture" --cs
```

O Virtual Assistant usa `SetLocaleMiddleware` para identificar o local atual e invocar o modelo de despacho correspondente. A atividade de estrutura de bot tem campo de localização que é usado por este middleware. Você pode usar o mesmo para sua habilidade também. O bot book-a-room não usa este middleware e, em vez disso, obtém locale da [entidade clienteInfo](https://github.com/microsoft/botframework-sdk/blob/master/specs/botframework-activity/botframework-activity.md#clientinfo)da empresa de framework Bot .

### <a name="claim-validation"></a>Validação de reivindicações

Adicionamos [reivindicaçõesValidator](https://github.com/nebhagat/msteams-virtual-assistant-dotnet/blob/master/msteams-virtual-assistant-dotnet/Authentication/AllowedCallersClaimsValidator.cs) para restringir os chamadores à habilidade. Para permitir que um Assistente Virtual chame essa habilidade, preencha `AllowedCallers` a matriz com o `appsettings` ID do aplicativo do Virtual Assistant em particular.

```
"AllowedCallers": [ "<caller_VA1_appId>", "<caller_VA2_appId>" ],
```

O array de chamadores permitido pode restringir qual habilidade os consumidores podem acessar a habilidade. Adicione uma única entrada `*` a esta matriz, para aceitar chamadas de qualquer consumidor de habilidade.

```
"AllowedCallers": [ "*" ],
```

Para obter mais informações sobre a adição de validação de sinistros a uma habilidade, consulte [adicionar validação de sinistros à habilidade](/azure/bot-service/skill-implement-skill?view=azure-bot-service-4.0&tabs=cs#claims-validator&preserve-view=true).

### <a name="limitation-of-card-refresh"></a>Limitação da atualização do cartão 

A atualização da atividade, como a atualização do cartão, ainda não é suportada através do Virtual Assistant[(problema do github).](https://github.com/microsoft/botbuilder-dotnet/issues/3686) Por isso, substituímos todas as chamadas de atualização `UpdateActivityAsync` de cartões com a postagem de novas chamadas de cartão `SendActivityAsync` .

### <a name="card-actions-and-task-module-flows"></a>Ações de cartão e fluxos de módulos de tarefa

Para encaminhar as atividades de ação de cartão ou módulo de tarefa para uma habilidade associada, a habilidade deve `skillId` incorporá-la.
`Book-a-room` ação do cartão de bot, a busca do módulo de tarefa e o envio de cargas de ação são modificados para conter `skillId` como parâmetro. 

Para obter mais informações, consulte [esta](https://msteams-captain.visualstudio.com/xGrowth%20App%20Templates/_wiki/wikis/xGrowth.wiki/88/Virtual-Assistant-for-MS-Teams?anchor=rich-cards) seção a partir desta documentação.

### <a name="handle-activities-from-group-chat-or-channel-scope"></a>Lidar com atividades a partir de bate-papo em grupo ou escopo de canal

`Book-a-room bot` é projetado para chats privados, como apenas escopo pessoal ou 1:1. Como temos o Assistente Virtual personalizado para apoiar o chat em grupo e os escopos do canal, o Assistente Virtual deve ser invocado a partir dos escopos do canal e, portanto, `Book-a-room` o bot deve obter atividades para o mesmo escopo. Portanto, `Book-a-room` o bot é personalizado para lidar com essas atividades. Você pode encontrar os métodos de check-in `OnMessageActivityAsync` do manipulador de `Book-a-room` atividades do bot.

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

Você também pode aproveitar as habilidades existentes do [repositório de Soluções de Estrutura de Bot](https://github.com/microsoft/botframework-solutions/tree/master/skills/csharp) ou criar uma nova habilidade completamente do zero. Para criar uma nova habilidade, consulte [tutoriais para criar uma nova habilidade](https://microsoft.github.io/botframework-solutions/overview/skills/). Para assistente virtual e documentação de arquitetura de habilidades, consulte[Assistente Virtual e arquitetura de habilidades](/azure/bot-service/skills-conceptual?view=azure-bot-service-4.0&preserve-view=true).  

## <a name="limitations-of-virtual-assistant"></a>Limitações do Assistente Virtual 

* **EndOfConversation**: Uma habilidade deve enviar uma `endOfConversation` atividade quando terminar uma conversa. Com base na atividade, um Assistente Virtual termina o contexto com essa habilidade particular e volta ao contexto raiz do Virtual Assistant. Para o robô Book-a-room, não há um estado claro onde a conversa é encerrada. Portanto, não enviamos `endOfConversation` do bot e quando o usuário quer voltar ao contexto raiz eles podem `Book-a-room` simplesmente fazer isso por `start over` comando.  
* **Atualização do** cartão : A atualização do cartão ainda não é suportada através do Virtual Assistant.  
* **Extensões de mensagens:**
  * Atualmente, um Assistente Virtual pode suportar no máximo dez comandos para extensões de mensagens.
  * A configuração das extensões de mensagens não é escopo para comandos individuais, mas para toda a extensão em si. Isso limita a configuração de cada habilidade individual através do Virtual Assistant.
  * As IDs de comando de extensões de mensagens têm um comprimento máximo de [64 caracteres](../resources/schema/manifest-schema.md#composeextensions) e 37 caracteres são usados para incorporar informações de habilidade. Assim, as restrições atualizadas para o ID de comando são limitadas a 27 caracteres.

Você também pode aproveitar as habilidades existentes do [repositório de Soluções de Estrutura de Bot](https://github.com/microsoft/botframework-solutions/tree/master/skills/csharp) ou criar uma nova habilidade completamente do zero. Tutoriais para o mais tarde podem ser encontrados [aqui](https://microsoft.github.io/botframework-solutions/overview/skills/). Consulte a [documentação](/azure/bot-service/skills-conceptual?view=azure-bot-service-4.0&preserve-view=true) para Assistente Virtual e arquitetura de habilidades.

## <a name="code-sample"></a>Exemplo de código

| **Nome da amostra** | **Descrição** | **C#** | **.NET** |
|----------|-----------------|----------|------------------|
| Modelo de estúdio visual atualizado | Modelo personalizado para suportar recursos de equipes. | [View](https://github.com/OfficeDev/microsoft-teams-apps-bookaroom/tree/nebhagat/microsoft-teams-apps-bookaroom-skill) |
| Código de habilidade de robô de livro-a-quarto | Permite que você encontre rapidamente e reserve uma sala de reunião em movimento. |  | [View](https://github.com/nebhagat/msteams-virtual-assistant-dotnet) |


## <a name="see-also"></a>Confira também

- [Integrar aplicativos Web](~/samples/integrate-web-apps-overview.md)

- [Livro-a-sala](app-templates.md#book-a-room)

- [Microsoft Teams bot](../bots/what-are-bots.md)