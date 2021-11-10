---
title: Criar um Assistente Virtual
description: Saiba como criar um Assistente Virtual para Microsoft Teams usando exemplos de código e trechos de código com recursos como cartões adaptáveis; manipulação de interrupções, solicitações de módulo de tarefa, escopos de aplicativo colaborativos e extensões de mensagens; usando manifesto de habilidades; Suporte para vários idiomas, validação de declaração, integração com o LUIS e modo.
ms.localizationpriority: medium
ms.topic: how-to
keywords: bots de assistente virtual do teams
ms.openlocfilehash: 2082e160387bd6ad80fa526e3dab39b385a6e955
ms.sourcegitcommit: af1d0a4041ce215e7863ac12c71b6f1fa3e3ba81
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/10/2021
ms.locfileid: "60889227"
---
# <a name="create-virtual-assistant"></a>Criar um Assistente Virtual

Assistente Virtual é um modelo de código aberto da Microsoft que permite que você crie uma solução de conversação robusta, mantendo o controle total da experiência do usuário, da identidade visual organizacional e dos dados necessários. O [Assistente Virtual](https://microsoft.github.io/botframework-solutions/overview/virtual-assistant-template) principal é o bloco de construção básico que reúne as tecnologias da Microsoft necessárias para criar um Assistente Virtual, incluindo o [SDK](https://github.com/microsoft/botframework-sdk)da Estrutura de Bot, o Entendimento de Idioma [(LUIS)](https://www.luis.ai/)e o [QnA Maker](https://www.qnamaker.ai/). Ele também reúne os recursos essenciais, incluindo registro de habilidades, contas vinculadas, intenção de conversa básica para oferecer uma variedade de interações e experiências perfeitas aos usuários. Além disso, os recursos do modelo incluem exemplos avançados de habilidades de conversa [reutilizáveis.](https://microsoft.github.io/botframework-solutions/overview/skills)  As habilidades individuais são integradas em uma Assistente Virtual para habilitar vários cenários. Usando o SDK da Estrutura de Bot, as habilidades são apresentadas no formulário de código-fonte, permitindo que você personalize e se estenda conforme necessário. Para obter mais informações sobre as habilidades do Bot Framework, consulte [What is a Bot Framework skill](https://microsoft.github.io/botframework-solutions/overview/skills/). Este documento orienta você sobre Assistente Virtual de implementação para organizações, como criar um Teams de Assistente Virtual, exemplo relacionado, exemplo de código e limitações de Assistente Virtual.
A imagem a seguir exibe a visão geral do assistente virtual:

![Assistente Virtual diagrama de visão geral](../assets/images/bots/virtual-assistant/overview.png)

As atividades de mensagem de texto são roteadas para habilidades associadas pelo núcleo Assistente Virtual usando um modelo [de](/azure/bot-service/bot-builder-tutorial-dispatch?view=azure-bot-service-4.0&tabs=cs&preserve-view=true) expedição.

## <a name="implementation-considerations"></a>Considerações sobre implementação

A decisão de adicionar um Assistente Virtual inclui muitos determinantes e difere para cada organização. Os fatores de suporte de uma implementação Assistente Virtual para sua organização são:

* Uma equipe central gerencia todas as experiências dos funcionários. Ele tem a capacidade de criar uma experiência Assistente Virtual e gerenciar atualizações para a experiência principal, incluindo a adição de novas habilidades.
* Vários aplicativos existem entre funções comerciais e o número deve crescer no futuro.
* Os aplicativos existentes são personalizáveis, pertencentes à organização, e são convertidos em habilidades para um Assistente Virtual.
* A equipe de experiências do funcionário central é capaz de influenciar personalizações para aplicativos existentes. Ele também fornece orientações necessárias para integrar aplicativos existentes como habilidades Assistente Virtual experiência.

A imagem a seguir exibe as funções comerciais de Assistente Virtual:

![A equipe central mantém o assistente e as equipes de função de negócios contribuem com habilidades](../assets/images/bots/virtual-assistant/business-functions.png)

## <a name="create-a-teams-focused-virtual-assistant"></a>Criar um Teams de Assistente Virtual

A Microsoft publicou um [Visual Studio para](https://marketplace.visualstudio.com/items?itemName=BotBuilder.VirtualAssistantTemplate) a criação de assistentes virtuais e habilidades. Com o modelo Visual Studio, você pode criar um Assistente Virtual, alimentado por uma experiência baseada em texto com suporte para cartões rich limitados com ações. Aprimoramos o modelo Visual Studio base para incluir recursos de Microsoft Teams plataforma e ter excelentes Teams de aplicativos. Alguns dos recursos incluem suporte para cartões adaptáveis avançados, módulos de tarefas, equipes ou chats de grupo e extensões de mensagens. Para obter mais informações sobre como estender Assistente Virtual Microsoft Teams, consulte [Tutorial: Extend Your Assistente Virtual to Microsoft Teams](https://microsoft.github.io/botframework-solutions/clients-and-channels/tutorials/enable-teams/1-intro/).    
A imagem a seguir exibe o diagrama de alto nível de uma Assistente Virtual solução:

![Diagrama de alto nível de uma Assistente Virtual solução](../assets/images/bots/virtual-assistant/high-level-diagram.png)

### <a name="add-adaptive-cards-to-your-virtual-assistant"></a>Adicionar cartões adaptáveis ao seu Assistente Virtual

Para despachar as solicitações corretamente, Assistente Virtual deve identificar o modelo DEID correto e as habilidades correspondentes associadas a ele. No entanto, o mecanismo de expedição não pode ser usado para atividades de ação de cartão, já que o modelo DEAD associado a uma habilidade é treinado para textos de ação de cartão. Os textos de ação do cartão são palavras-chave fixas, pré-definidas e não comentadas de um usuário.

Essa desvantagem é resolvida por meio da incorporação de informações de habilidade na carga de ação do cartão. Cada habilidade deve incorporar `skillId` no campo de ações de  `value` cartão. Você deve garantir que cada atividade de ação de cartão carregue as informações de habilidade relevantes e Assistente Virtual pode utilizar essas informações para a expedição.

Você deve fornecer no construtor para garantir que as informações de habilidade `skillId` sempre estão presentes em ações de cartão.
Um código de exemplo de dados de ação de cartão é mostrado na seção a seguir:
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

Em seguida, a classe no modelo Assistente Virtual é introduzida para `SkillCardActionData` extrair da carga de ação do `skillId` cartão.
Um trecho de código para extrair da carga de ação  `skillId` do cartão é mostrado na seção a seguir:

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

A implementação é feita por um método de extensão na [classe Atividade.](https://github.com/microsoft/botframework-sdk/blob/master/specs/botframework-activity/botframework-activity.md)
Um trecho de código para extrair dados de ação de cartão  `skillId` é mostrado na seção a seguir:

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

### <a name="handle-interruptions"></a>Manipular interrupções

Assistente Virtual pode lidar com interrupções em casos em que um usuário tenta invocar uma habilidade enquanto outra habilidade está ativa no momento. `TeamsSkillDialog`e são `TeamsSwitchSkillDialog` introduzidos com base em [SkillDialog](https://github.com/microsoft/botframework-solutions/blob/5b46d73e220bbb4fba86c48be532e495535ca78a/sdk/csharp/libraries/microsoft.bot.solutions/Skills/SkillDialog.cs) e [SwitchSkillDialog](https://github.com/microsoft/botframework-solutions/blob/6d40fa8ae05f96b0c5e0464e01361a9e1deb696c/sdk/csharp/libraries/microsoft.bot.solutions/Skills/Dialogs/SwitchSkillDialog.cs)do Bot Framework. Eles permitem que os usuários alternem uma experiência de habilidade de ações de cartão. Para lidar com essa solicitação, o Assistente Virtual solicita ao usuário uma mensagem de confirmação para alternar habilidades:

![Prompt de confirmação ao mudar para uma nova habilidade](../assets/images/bots/virtual-assistant/switch-skills-prompt.png)

### <a name="handle-task-module-requests"></a>Manipular solicitações de módulo de tarefa

Para adicionar recursos de módulo de tarefa a um Assistente Virtual, dois métodos adicionais são incluídos no manipulador de Assistente Virtual de atividades: `OnTeamsTaskModuleFetchAsync` e `OnTeamsTaskModuleSubmitAsync` . Esses métodos ouvem atividades relacionadas ao módulo de tarefas Assistente Virtual, identificam a habilidade associada à solicitação e encaminham a solicitação para a habilidade identificada. 

O encaminhamento de solicitação é feito [por meio do método SkillHttpClient](/dotnet/api/microsoft.bot.builder.integration.aspnet.core.skills.skillhttpclient?view=botbuilder-dotnet-stable&preserve-view=true) `PostActivityAsync` ,. Retorna a resposta como `InvokeResponse` a qual é analisado e convertido em `TaskModuleResponse` .


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

O trecho de código para `OnTeamsTaskModuleFetchAsync` e os métodos são dados na seção a `OnTeamsTaskModuleSubmitAsync` seguir:

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

Além disso, você deve incluir todos os domínios de habilidade na seção no arquivo de manifesto do Assistente Virtual para que os módulos de tarefa invocados por meio de uma habilidade `validDomains` renderizar corretamente.

### <a name="handle-collaborative-app-scopes"></a>Manipular escopos de aplicativo colaborativos

Teams aplicativos podem existir em vários escopos, incluindo chat 1:1, chat em grupo e canais. O modelo Assistente Virtual principal foi projetado para chats 1:1. Como parte da experiência de integração, Assistente Virtual solicita aos usuários o nome e mantém o estado do usuário. Como a experiência de integração não é adequada para escopos de chat de grupo ou canal, ela foi removida.

As habilidades devem lidar com atividades em vários escopos, como chat 1:1, chat em grupo e conversa de canal. Se nenhum desses escopos tiver suporte, as habilidades deverão responder com uma mensagem apropriada.

As seguintes funções de processamento foram adicionadas ao Assistente Virtual principal:

* Assistente Virtual pode ser invocada sem qualquer mensagem de texto de um chat de grupo ou canal.
* As articulações são limpas antes de enviar a mensagem para o módulo de expedição. Por exemplo, remova o @mention necessário do bot.

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

### <a name="handle-messaging-extensions"></a>Manipular extensões de mensagens

Os comandos de uma extensão de mensagens são declarados no arquivo de manifesto do aplicativo. A interface do usuário de extensão de mensagens é alimentada por esses comandos. Para que Assistente Virtual um comando de extensão de mensagens como uma habilidade anexada, o próprio manifesto de um Assistente Virtual deve conter esses comandos. Você deve adicionar os comandos do manifesto de uma habilidade individual ao manifesto Assistente Virtual do usuário. A ID do comando fornece informações sobre uma habilidade associada, adicionando a ID do aplicativo da habilidade por meio de um separador `:` .

O trecho do arquivo de manifesto de uma habilidade é mostrado na seção a seguir:

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

O trecho Assistente Virtual código de arquivo de manifesto correspondente é mostrado na seção a seguir:

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

Depois que os comandos são invocados por um usuário, o Assistente Virtual pode identificar uma habilidade associada ao analisar a ID do comando, atualizar a atividade removendo o sufixo extra da ID de comando e encaminhá-la para a habilidade `:<skill_id>` correspondente. O código de uma habilidade não precisa manipular o sufixo extra. Assim, conflitos entre IDs de comando entre habilidades são evitados. Com essa abordagem, todos os comandos de pesquisa e ação de uma  habilidade em todos os contextos, como **redação,** **commandBox** e mensagem são alimentados por um Assistente Virtual.

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

Algumas atividades de extensão de mensagens não incluem a ID do comando. Por exemplo, `composeExtension/selectItem` contém apenas o valor da ação chamar toque. Para identificar a habilidade associada, é anexado a `skillId`  cada cartão de item ao formar uma resposta para `OnTeamsMessagingExtensionQueryAsync` . Isso é semelhante à abordagem para [adicionar cartões adaptáveis ao seu Assistente Virtual](#add-adaptive-cards-to-your-virtual-assistant).

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

O exemplo a seguir mostra como converter o modelo de aplicativo Book-a-room em uma habilidade de Assistente Virtual: Book-a-room é um Microsoft Teams que permite que os usuários encontrem e reservem rapidamente uma sala de reunião para 30, 60 ou 90 minutos a partir da hora atual. O tempo padrão é de 30 minutos. Os escopos de bot book-a-room para conversas pessoais ou 1:1. A imagem a seguir exibe um Assistente Virtual com um **livro uma habilidade de** sala:

![Assistente Virtual com uma habilidade de "reservar uma sala"](../assets/images/bots/virtual-assistant/book-a-room-skill.png)

A seguir estão as alterações delta introduzidas para convertê-la em uma habilidade anexada a um Assistente Virtual. Diretrizes semelhantes são seguidas para converter qualquer bot v4 existente em uma habilidade.

### <a name="skill-manifest"></a>Manifesto de habilidades

Um manifesto de habilidades é um arquivo JSON que expõe o ponto de extremidade, a ID, o nome e outros metadados relevantes de uma habilidade. Esse manifesto é diferente do manifesto usado para sideload de um aplicativo Microsoft Teams. Um Assistente Virtual requer um caminho para esse arquivo como uma entrada para anexar uma habilidade. Adicionamos o manifesto a seguir à pasta wwwroot do bot.

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

Assistente Virtual modelo de expedição da Assistente Virtual é criado com base nos modelos DEIS das habilidades anexadas. O modelo de expedição identifica a intenção de cada atividade de texto e descobre as habilidades associadas a ela.

Assistente Virtual requer o modelo DEIS de habilidade no `.lu` formato como uma entrada ao anexar uma habilidade. O json de LUIS é convertido `.lu` em formato usando a ferramenta botframework-cli.

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

Construímos um modelo DEAD compreendendo esses dois comandos. Os segredos correspondentes devem ser preenchidos em `cognitivemodels.json` . O arquivo JSON DO LUIS correspondente é encontrado [aqui](https://github.com/OfficeDev/microsoft-teams-apps-bookaroom/blob/nebhagat/microsoft-teams-apps-bookaroom-skill/Deployment/Resources/LU/en-us/book-a-meeting.json).
O arquivo `.lu` correspondente é mostrado na seção a seguir:

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

Com essa abordagem, qualquer comando emitido por um usuário para Assistente Virtual relacionado ou identificado como um comando associado ao bot e é encaminhado para `book room` `manage favorites` essa `Book-a-room` habilidade.
Por outro lado, `Book-a-room room` o bot precisa usar o modelo DEAD para entender esses comandos se eles não são digitados completos. Por exemplo: `I want to manage my favorite rooms`.

### <a name="multi-language-support"></a>Suporte a vários idiomas

Como exemplo, um modelo DEAD com apenas cultura em inglês é criado. Você pode criar modelos DEIS correspondentes a outros idiomas e adicionar entrada a `cognitivemodels.json` .

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

Para modificar `languages` o parâmetro, atualize o comando botskills da seguinte forma:

```json
botskills connect --remoteManifest "<url to skill's manifest>" --luisFolder "<path to luisFolder>" --languages "en-us, your_language_culture" --cs
```

Assistente Virtual usa `SetLocaleMiddleware` para identificar a localidade atual e invocar o modelo de expedição correspondente. A atividade da estrutura bot tem o campo de localidade que é usado por esse middleware. Você também pode usar o mesmo para suas habilidades. Book-a-room bot does not use this middleware and instead gets locale from Bot framework activity's [clientInfo entity](https://github.com/microsoft/botframework-sdk/blob/master/specs/botframework-activity/botframework-activity.md#clientinfo).

### <a name="claim-validation"></a>Validação de declaração

Adicionamos [claimsValidator para](https://github.com/nebhagat/msteams-virtual-assistant-dotnet/blob/master/msteams-virtual-assistant-dotnet/Authentication/AllowedCallersClaimsValidator.cs) restringir os chamadores à habilidade. Para permitir que um Assistente Virtual chame essa habilidade, preencha a matriz com essa ID de aplicativo Assistente Virtual de aplicativo `AllowedCallers` `appsettings` específico.

```
"AllowedCallers": [ "<caller_VA1_appId>", "<caller_VA2_appId>" ],
```

A matriz de chamadores permitidos pode restringir quais clientes de habilidades podem acessar a habilidade. Adicione entrada única `*` a essa matriz, para aceitar chamadas de qualquer consumidor de habilidades.

```
"AllowedCallers": [ "*" ],
```

Para obter mais informações sobre como adicionar validação de declarações a uma habilidade, [consulte add claims validation to skill](/azure/bot-service/skill-implement-skill?view=azure-bot-service-4.0&tabs=cs#claims-validator&preserve-view=true).

### <a name="limitation-of-card-refresh"></a>Limitação da atualização do cartão 

A atualização da atividade, como a atualização do cartão, ainda não é suportada Assistente Virtual ([problema github](https://github.com/microsoft/botbuilder-dotnet/issues/3686)). Portanto, substituímos todas as chamadas de atualização de cartão `UpdateActivityAsync` por postagem de novas chamadas de `SendActivityAsync` cartão.

### <a name="card-actions-and-task-module-flows"></a>Ações de cartão e fluxos de módulos de tarefa

Para encaminhar atividades de ação de cartão ou módulo de tarefa a uma habilidade associada, a habilidade deve incorporar `skillId` a ela.
`Book-a-room` ação de cartão de bot, busca de módulo de tarefa e envio de cargas de ação são modificadas para conter `skillId` como um parâmetro. 

Para obter mais [informações, consulte esta](/microsoftteams/platform/samples/virtual-assistant#add-adaptive-cards-to-your-virtual-assistant) seção nesta documentação.

### <a name="handle-activities-from-group-chat-or-channel-scope"></a>Manipular atividades do chat de grupo ou do escopo do canal

`Book-a-room bot` foi projetado para chats privados, como apenas escopo pessoal ou 1:1. Como personalizaremos o Assistente Virtual para dar suporte aos escopos de chat e canal de grupo, o Assistente Virtual deve ser invocado dos escopos de canal e, portanto, o bot deve obter atividades para o `Book-a-room` mesmo escopo. Portanto, `Book-a-room` o bot é personalizado para lidar com essas atividades. Você pode encontrar os métodos de check-in `OnMessageActivityAsync` do manipulador de atividades do `Book-a-room` bot.

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

Você também pode aproveitar as habilidades existentes do repositório [de Soluções](https://github.com/microsoft/botframework-components/tree/main/skills/csharp) da Estrutura de Bot ou criar uma nova habilidade completamente do zero. Para criar uma nova habilidade, consulte [tutoriais para criar uma nova habilidade.](https://microsoft.github.io/botframework-solutions/overview/skills/) Para Assistente Virtual documentação de arquitetura de habilidades e habilidades,[consulte Assistente Virtual e arquitetura de habilidades.](/azure/bot-service/skills-conceptual?view=azure-bot-service-4.0&preserve-view=true)  

## <a name="limitations-of-virtual-assistant"></a>Limitações de Assistente Virtual 

* **EndOfConversation**: Uma habilidade deve enviar uma `endOfConversation` atividade quando terminar uma conversa. Com base na atividade, um Assistente Virtual termina o contexto com essa habilidade específica e volta ao contexto raiz do Assistente Virtual do usuário. Para o bot book-a-room, não há um estado claro em que a conversa seja encerrada. Portanto, não enviamos do bot e quando o usuário deseja voltar ao contexto raiz, ele `endOfConversation` pode simplesmente fazer isso por `Book-a-room` `start over` comando.  
* **Atualização do** cartão : Ainda não há suporte para atualização de cartão por meio Assistente Virtual.  
* **Extensões de mensagens**:
  * Atualmente, um Assistente Virtual pode suportar no máximo dez comandos para extensões de mensagens.
  * A configuração de extensões de mensagens não tem escopo para comandos individuais, mas para toda a extensão em si. Isso limita a configuração para cada habilidade individual por meio Assistente Virtual.
  * As IDs de comando de extensões de mensagens têm um comprimento máximo de [64](../resources/schema/manifest-schema.md#composeextensions) caracteres e 37 caracteres são usados para incorporar informações de habilidades. Assim, as restrições atualizadas para a ID de comando são limitadas a 27 caracteres.

Você também pode aproveitar as habilidades existentes do repositório [de Soluções](https://github.com/microsoft/botframework-components/tree/main/skills/csharp) da Estrutura de Bot ou criar uma nova habilidade completamente do zero. Tutoriais para o posterior podem ser [encontrados aqui](https://microsoft.github.io/botframework-solutions/overview/skills/). Consulte a [documentação para Assistente Virtual](/azure/bot-service/skills-conceptual?view=azure-bot-service-4.0&preserve-view=true) e arquitetura de habilidades.

## <a name="code-sample"></a>Exemplo de código

| **Nome do exemplo** | **Descrição** | **C#**  **.NET** |
|----------|-----------------|---------------------------|
| Modelo de visual studio atualizado | Modelo personalizado para dar suporte aos recursos das equipes. | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/app-virtual-assistant/csharp) |
| Book-a-room bot skill code | Permite que você encontre e reserve rapidamente uma sala de reunião em qualquer lugar. | [Exibir](https://github.com/OfficeDev/microsoft-teams-apps-bookaroom/tree/nebhagat/microsoft-teams-apps-bookaroom-skill) |


## <a name="see-also"></a>Confira também

* [Integrar aplicativos Web](~/samples/integrate-web-apps-overview.md)
* [Book-a-room](app-templates.md#app-template-code-samples)
* [Microsoft Teams bot](../bots/what-are-bots.md)
