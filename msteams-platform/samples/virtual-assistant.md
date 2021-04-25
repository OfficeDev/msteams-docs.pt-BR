---
title: Assistente Virtual do Microsoft Teams
description: Como criar bot e habilidades do Assistente Virtual para uso no Microsoft Teams
ms.topic: how-to
keywords: bots de assistente virtual do teams
ms.openlocfilehash: 52591435c5a7e1c65a8f86a7c41fe4a3a4fa5c83
ms.sourcegitcommit: dd2220f691029d043aaddfc7c229e332735acb1d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/24/2021
ms.locfileid: "51996020"
---
# <a name="virtual-assistant-for-microsoft-teams"></a>Assistente Virtual do Microsoft Teams

O Assistente Virtual é um modelo de código aberto da Microsoft que permite que você crie uma solução de conversação robusta, mantendo o controle total da experiência do usuário, da identidade visual organizacional e dos dados necessários. O modelo principal do Assistente [Virtual](https://microsoft.github.io/botframework-solutions/overview/virtual-assistant-template) é o bloco de construção básico que reúne as tecnologias da Microsoft necessárias para criar um Assistente Virtual, incluindo o [SDK](https://github.com/microsoft/botframework-sdk)da Estrutura de Bots, o Entendimento de Idioma [(LUIS),](https://www.luis.ai/)o [QnA Maker](https://www.qnamaker.ai/), bem como recursos essenciais, incluindo o registro de habilidades, contas vinculadas, intenção de conversa básica para oferecer aos usuários finais uma variedade de interações e experiências perfeitas. Além disso, os recursos do modelo incluem exemplos avançados de habilidades de conversa [reutilizáveis.](https://microsoft.github.io/botframework-solutions/overview/skills)  Habilidades individuais podem ser integradas em uma solução de Assistente Virtual para habilitar vários cenários. Usando o SDK da Estrutura de Bot, as habilidades são apresentadas no formulário de código-fonte, permitindo que você personalize e estenda conforme necessário. Consulte [O que é uma habilidade de estrutura de bots.](https://microsoft.github.io/botframework-solutions/overview/skills/)

![Diagrama de visão geral do Assistente Virtual](../assets/images/bots/virtual-assistant/overview.png)

As atividades de mensagem de texto são roteadas para habilidades associadas pelo núcleo do Assistente Virtual usando um modelo [de](/azure/bot-service/bot-builder-tutorial-dispatch?view=azure-bot-service-4.0&tabs=cs&preserve-view=true) expedição. 

## <a name="implementation-considerations"></a>Considerações sobre implementação

A decisão de adicionar um Assistente Virtual pode incluir muitos determinantes e diferir para cada organização. Aqui estão os fatores que suportam a implementação de um Assistente Virtual para sua organização:

- Uma equipe central gerencia todas as experiências dos funcionários e tem a capacidade de criar uma experiência de Assistente Virtual e gerenciar atualizações para a experiência principal, incluindo a adição de novas habilidades.
- Vários aplicativos existem entre funções comerciais e/ou o número deve crescer no futuro.
- Os aplicativos existentes são personalizáveis, pertencentes à organização e podem ser convertidos em habilidades para um Assistente Virtual.
- A equipe central de experiências de funcionários é capaz de influenciar personalizações para aplicativos existentes e fornecer orientações necessárias para integrar aplicativos existentes como habilidades na experiência do Assistente Virtual

![A equipe central mantém o assistente e as equipes de função de negócios contribuem com habilidades](../assets/images/bots/virtual-assistant/business-functions.png)

## <a name="create-a-teams-focused-virtual-assistant"></a>Criar um Assistente Virtual com foco no Teams

A Microsoft publicou um [Visual Studio para](https://marketplace.visualstudio.com/items?itemName=BotBuilder.VirtualAssistantTemplate) a criação de assistentes virtuais e habilidades. Com o Visual Studio, você pode criar um Assistente Virtual, alimentado por uma experiência baseada em texto com suporte para cartões rich limitados com ações. Aprimoramos o modelo Visual Studio base para incluir recursos de plataforma do Microsoft Teams e excelentes experiências de aplicativos do Teams. Alguns dos recursos incluem suporte para cartões adaptáveis avançados, módulos de tarefas, chats de equipes/grupos e extensões de mensagens. *Consulte também*, [Tutorial: Estender seu Assistente Virtual para o Microsoft Teams](https://microsoft.github.io/botframework-solutions/clients-and-channels/tutorials/enable-teams/1-intro/).

![Diagrama de alto nível de uma solução de Assistente Virtual](../assets/images/bots/virtual-assistant/high-level-diagram.png)

### <a name="add-adaptive-cards-to-your-virtual-assistant"></a>Adicionar cartões adaptáveis ao assistente virtual

Para despachar as solicitações corretamente, o Assistente Virtual precisa identificar o modelo DEID correto e as habilidades correspondentes associadas a ele. No entanto, o mecanismo de expedição não pode ser usado para atividades de ação de cartão, uma vez que o modelo DEAD associado a uma habilidade pode não ser treinado para textos de ação de cartão, uma vez que são palavras-chave fixas, pré-definidas, não palavras-chave de um usuário.

Resolvemos isso incorporando informações de habilidade na carga de ação do cartão. Cada habilidade deve incorporar `skillId` no campo de ações de  `value` cartão. Essa é a melhor maneira de garantir que cada atividade de ação de cartão carregue as informações de habilidades relevantes e o Assistente Virtual possa utilizar essas informações para a expedição.

Abaixo está um exemplo de dados de ação de cartão. Ao fornecer no `skillId` construtor, garantimos que as informações de habilidade sempre estão presentes nas ações de cartão.

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

Em seguida, apresentamos a classe no modelo assistente virtual para extrair da carga `SkillCardActionData` `skillId` de ação do cartão.

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

Abaixo está um trecho de código para extrair  `skillId` dos dados de ação do cartão. Implementamos como um método de extensão na [classe Atividade.](https://github.com/microsoft/botframework-sdk/blob/master/specs/botframework-activity/botframework-activity.md)

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

### <a name="handle-interruptions-gracefully"></a>Manipular interrupções normalmente

O Assistente Virtual pode lidar com interrupções em casos em que um usuário tenta invocar uma habilidade enquanto outra habilidade está ativa no momento. apresentamos e , com base em `TeamsSkillDialog` `TeamsSwitchSkillDialog` [SkillDialog](https://github.com/microsoft/botframework-solutions/blob/5b46d73e220bbb4fba86c48be532e495535ca78a/sdk/csharp/libraries/microsoft.bot.solutions/Skills/SkillDialog.cs) e [SwitchSkillDialog](https://github.com/microsoft/botframework-solutions/blob/6d40fa8ae05f96b0c5e0464e01361a9e1deb696c/sdk/csharp/libraries/microsoft.bot.solutions/Skills/Dialogs/SwitchSkillDialog.cs)da Estrutura do Bot, para permitir que os usuários alternem uma experiência de habilidade das ações de cartão. Para lidar com essa solicitação, o Assistente Virtual solicita ao usuário uma mensagem de confirmação para alternar habilidades.

![Prompt de confirmação ao mudar para uma nova habilidade](../assets/images/bots/virtual-assistant/switch-skills-prompt.png)

### <a name="handling-task-module-requests"></a>Manipulando solicitações de módulo de tarefa

Para adicionar recursos de módulo de tarefa a um Assistente Virtual, dois métodos adicionais são incluídos no manipulador de atividades do Assistente Virtual: `OnTeamsTaskModuleFetchAsync` e `OnTeamsTaskModuleSubmitAsync` . Esses métodos ouvem atividades relacionadas ao módulo de tarefas do Assistente Virtual, identificam a habilidade associada à solicitação e encaminham a solicitação para a habilidade identificada. 

O encaminhamento de solicitação é feito por  [meio do método SkillHttpClient](/dotnet/api/microsoft.bot.builder.integration.aspnet.core.skills.skillhttpclient?view=botbuilder-dotnet-stable&preserve-view=true) `PostActivityAsync` ,. Retorna a resposta como `InvokeResponse` a qual é analisado e convertido em `TaskModuleResponse` .

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

Uma abordagem semelhante é seguida para a expedição de ações de cartão e respostas do módulo de tarefa. Os dados de ação de busca e envio do módulo de tarefa são atualizados para incluir `skillId` . O método Activity Extension extrai da carga que fornece detalhes `GetSkillId` sobre a habilidade que precisa ser `skillId` invocada.

Abaixo está um trecho de código para `OnTeamsTaskModuleFetchAsync` e `OnTeamsTaskModuleSubmitAsync` métodos.

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

Além disso, todos os domínios de habilidade devem ser incluídos na seção no arquivo de manifesto do Assistente Virtual para que os módulos de tarefa invocados por meio de uma habilidade `validDomains` sejam renderados corretamente.

### <a name="handling-collaborative-app-scopes"></a>Manipulando escopos de aplicativo colaborativos

Os aplicativos do Teams podem existir em vários escopos, incluindo chat 1:1, chat em grupo e canais. O modelo principal do Assistente Virtual foi projetado para chats 1:1. Como parte da experiência de integração, o Assistente Virtual solicita aos usuários o nome e mantém o estado do usuário. Como essa experiência de integração não é adequada para escopos de chat/canal de grupo, ela foi removida.

As habilidades devem lidar com atividades em vários escopos (chat 1:1, chat em grupo e conversa de canal). Se nenhum desses escopos tiver suporte, as habilidades deverão responder com uma mensagem apropriada.

As seguintes funções de processamento foram adicionadas ao núcleo do Assistente Virtual:

- O Assistente Virtual pode ser invocado sem qualquer mensagem de texto de um chat de grupo ou canal.
- As articulações são limpas (ou seja, remova o @mention necessário do bot) antes de enviar a mensagem para o módulo de expedição.

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

### <a name="handling-messaging-extensions"></a>Manipulando extensões de mensagens

Os comandos de uma extensão de mensagens são declarados no arquivo de manifesto do aplicativo. A interface do usuário de extensão de mensagens é alimentada por esses comandos. Para que um Assistente Virtual ative um comando de extensão de mensagens (como uma habilidade anexada), o próprio manifesto do Assistente Virtual deve conter esses comandos. Os comandos do manifesto de uma habilidade individual também devem ser adicionados ao manifesto do Assistente Virtual. A ID do comando fornece informações sobre uma habilidade associada, acrescentando a ID do aplicativo da habilidade por meio de um separador ( `:` ).

Abaixo está um trecho do arquivo de manifesto de uma habilidade.

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

E, abaixo está o trecho de código de arquivo de manifesto do Assistente Virtual correspondente.

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

Depois que os comandos são invocados por um usuário, o Assistente Virtual pode identificar uma habilidade associada ao analisar a ID de comando, atualizar a atividade removendo o sufixo extra ( ) da ID de comando e encaminhá-la para a habilidade `:<skill_id>` correspondente. O código de uma habilidade não precisa manipular o sufixo extra, portanto, os conflitos entre as IDs de comando entre as habilidades são evitados. Com essa abordagem, todos os comandos de pesquisa e ação de uma habilidade em todos os contextos ("composição", "commandBox" e "mensagem") podem ser acionados por um Assistente Virtual.

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

Algumas atividades de extensão de mensagens não incluem a ID do comando. Por exemplo, `composeExtension/selectItem` contém apenas o valor da ação chamar toque. Para identificar a habilidade associada, é anexado a `skillId`  cada cartão de item ao formar uma resposta para `OnTeamsMessagingExtensionQueryAsync` . (Isso é semelhante à abordagem para [adicionar cartões adaptáveis ao assistente virtual.](#add-adaptive-cards-to-your-virtual-assistant)

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

## <a name="example-convert-the-book-a-room-app-template-to-a-virtual-assistant-skill"></a>Exemplo: Converter o modelo de aplicativo book-a-room em uma habilidade do Assistente Virtual

[Book-a-room](app-templates.md#book-a-room) é um bot do [Microsoft Teams](../bots/what-are-bots.md) que permite aos usuários encontrar e reservar rapidamente uma sala de reunião para 30 (padrão), 60 ou 90 minutos a partir da hora atual. Os escopos de bot book-a-room para conversas pessoais ou 1:1.

![Assistente Virtual com uma habilidade de "reservar uma sala"](../assets/images/bots/virtual-assistant/book-a-room-skill.png)

A seguir estão as alterações delta introduzidas para convertê-la em uma habilidade que pode ser anexada a um Assistente Virtual. Diretrizes semelhantes podem ser seguidas para converter qualquer bot v4 existente em uma habilidade.

### <a name="skill-manifest"></a>Manifesto de habilidades

Um manifesto de habilidade é um arquivo JSON que expõe o ponto de extremidade, a ID, o nome e outros metadados relevantes de uma habilidade (esse manifesto é diferente do manifesto usado para sideload de um aplicativo no Microsoft Teams) Um Assistente Virtual requer um caminho para esse arquivo como uma entrada para anexar uma habilidade. Adicionamos o manifesto a seguir à pasta wwwroot do bot.

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

### <a name="luis-integration"></a>Integração DO LUIS

O modelo de expedição do Assistente Virtual é criado com base nos modelos DEIS das habilidades anexadas. O modelo de expedição identifica a intenção de cada atividade de texto e descobre as habilidades associadas a ela.

O Assistente Virtual requer o modelo DEIS da habilidade (em `.lu` formato) como uma entrada ao anexar uma habilidade. O json de LUIS pode ser convertido em formato usando a `.lu` ferramenta botframework-cli.

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

Construímos um modelo DEAD noções básicas sobre esses dois comandos. Os segredos correspondentes precisam ser preenchidos em `cognitivemodels.json` . O arquivo JSON do LUIS correspondente pode ser encontrado [aqui](https://github.com/OfficeDev/microsoft-teams-apps-bookaroom/blob/nebhagat/microsoft-teams-apps-bookaroom-skill/Deployment/Resources/LU/book-a-meeting.json) e é assim que o arquivo `.lu` correspondente se parece.

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

Com essa abordagem, qualquer problema de comando de um usuário para o Assistente Virtual relacionado ou pode ser identificado como um comando associado ao `book room` bot Book-a-room e é encaminhado para `manage favorites` essa habilidade.
Por outro lado, o bot de sala de livro precisa usar o modelo DEA para entender esses comandos se eles não são digitados como está (por exemplo: `I want to manage my favorite rooms` ).

### <a name="multi-language-support"></a>Suporte a vários idiomas

Para este exemplo, criamos apenas um modelo DEAD com cultura em inglês. Você pode criar modelos DEIS correspondentes a outros idiomas e adicionar entrada a `cognitivemodels.json` .

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

Em paralelo, adicione o `.lu` arquivo correspondente no caminho de luisFolder. A estrutura de pastas deve ser a seguinte:

```bash
| - luisFolder

        | - en-us

                | - book-a-meeting.lu

        | - your_language_culture

                | - book-a-meeting.lu
```

Atualizar o comando botskills da seguinte forma para modificar o `languages` parâmetro:

```json
botskills connect --remoteManifest "<url to skill's manifest>" --luisFolder "<path to luisFolder>" --languages "en-us, your_language_culture" --cs
```

O Assistente Virtual `SetLocaleMiddleware` usa para identificar a localidade atual e invocar o modelo de expedição correspondente. (A atividade da estrutura bot tem um campo de localidade que é usado por esse middleware.) Recomendamos usar o mesmo para suas habilidades também. Book-a-room bot does not use this middleware and instead gets locale from Bot framework activity's [clientInfo entity](https://github.com/microsoft/botframework-sdk/blob/master/specs/botframework-activity/botframework-activity.md#clientinfo).

### <a name="claim-validation"></a>Validação de declaração

Adicionamos [claimsValidator para](https://github.com/nebhagat/msteams-virtual-assistant-dotnet/blob/master/msteams-virtual-assistant-dotnet/Authentication/AllowedCallersClaimsValidator.cs) restringir os chamadores à habilidade. Para permitir que um Assistente Virtual chame essa habilidade, preencha a matriz com a ID de aplicativo específica do Assistente `AllowedCallers` `appsettings` Virtual.

```
"AllowedCallers": [ "<caller_VA1_appId>", "<caller_VA2_appId>" ],
```

A matriz de chamadores permitidos pode restringir quais clientes de habilidades podem acessar a habilidade. Adicione entrada única `*` a essa matriz, para aceitar chamadas de qualquer consumidor de habilidades.

```
"AllowedCallers": [ "*" ],
```
Documentação detalhada para adicionar validação de declarações a uma habilidade pode ser encontrada [aqui](https://docs.microsoft.com/azure/bot-service/skill-implement-skill?view=azure-bot-service-4.0&tabs=cs#claims-validator&preserve-view=true).

### <a name="card-refresh-limitation"></a>Limitação de atualização de cartão

A atividade de atualização (atualização de cartão) ainda não é suportada por meio do Assistente Virtual ([problema github](https://github.com/microsoft/botbuilder-dotnet/issues/3686)). Portanto, substituímos todas as chamadas de atualização de cartão ( `UpdateActivityAsync` ) com a postagem de novas chamadas de cartão( `SendActivityAsync` ).

### <a name="card-actions-and-task-module-flows"></a>Ações de cartão e fluxos de módulos de tarefa

Para encaminhar atividades de ação de cartão ou módulo de tarefa a uma habilidade associada, a habilidade precisa incorporar `skillId` a ela.
Ação de cartão bot do book-a-room, busca de módulo de tarefa e envio de cargas de ação são modificadas para conter `skillId` como parâmetro. 

Para obter mais [informações, consulte esta](https://msteams-captain.visualstudio.com/xGrowth%20App%20Templates/_wiki/wikis/xGrowth.wiki/88/Virtual-Assistant-for-MS-Teams?anchor=rich-cards) seção nesta documentação.

### <a name="handle-activities-from-group-chat-or-channel-scope"></a>Manipular atividades do chat de grupo ou do escopo do canal

O bot book-a-room foi projetado apenas para chats privados (escopo pessoal/1:1). Como personalização do Assistente Virtual para dar suporte a chats em grupo e escopos de canal, o Assistente Virtual pode ser invocado a partir desses escopos e, portanto, o bot book-a-room pode obter atividades para o mesmo. Portanto, o bot book-a-room é personalizado para lidar com essas atividades. A verificação foi colocada em métodos do manipulador de atividades do `OnMessageActivityAsync` bot book-a-room.

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

Você também pode aproveitar as habilidades existentes do repositório [de Soluções](https://github.com/microsoft/botframework-solutions/tree/master/skills/csharp) da Estrutura de Bot ou criar uma nova habilidade completamente do zero. Tutoriais para o posterior podem ser [encontrados aqui](https://microsoft.github.io/botframework-solutions/overview/skills/). Consulte a [documentação para](https://docs.microsoft.com/azure/bot-service/skills-conceptual?view=azure-bot-service-4.0&preserve-view=true) Assistente Virtual e arquitetura de habilidades.

## <a name="code-sample"></a>Exemplo de código

| **Exemplo de nome** | **Descrição** | **C#** | **.NET** |
|----------|-----------------|----------|------------------|
| Modelo de visual studio atualizado | Modelo personalizado para dar suporte aos recursos das equipes. | [View](https://github.com/OfficeDev/microsoft-teams-apps-bookaroom/tree/nebhagat/microsoft-teams-apps-bookaroom-skill) |
| Book-a-room bot skill code | Permite que você encontre e reserve rapidamente uma sala de reunião em qualquer lugar. |  | [View](https://github.com/nebhagat/msteams-virtual-assistant-dotnet) |



## <a name="virtual-assistant-known-limitations"></a>Limitações conhecidas do Assistente Virtual

- **EndOfConversation**. Uma habilidade deve enviar `endOfConversation` uma atividade quando terminar uma conversa. base dessa atividade, um Assistente Virtual termina o contexto com essa habilidade específica e volta ao contexto do Assistente Virtual (raiz). Para o bot book-a-room, não há um estado claro em que a conversa possa ser encerrada. Portanto, não enviamos do bot book-a-room e quando o usuário deseja voltar ao contexto raiz, ele pode simplesmente `endOfConversation` fazer isso por `start over` comando.
- **Atualização de cartão**. As atções de cartão ainda não são suportadas por meio do Assistente Virtual.
- **Extensões de mensagens**.:
  - Atualmente, um Assistente Virtual pode suportar no máximo dez comandos para extensões de mensagens.
  - A configuração de extensões de mensagens não tem escopo para comandos individuais, mas para toda a extensão em si. Isso limita a configuração para cada habilidade individual por meio do Assistente Virtual.
  - As IDs de comando de extensões de mensagens têm um comprimento máximo de [64](../resources/schema/manifest-schema.md#composeextensions) caracteres e 37 caracteres serão usados para incorporar informações de habilidades. Assim, as restrições atualizadas para a ID de comando são limitadas a 27 caracteres.
>
>
