---
title: Assistente virtual para o Microsoft Teams
description: Como criar as habilidades e bot do assistente virtual para uso no Microsoft Teams
keywords: bots do assistente virtual do Microsoft Teams
ms.openlocfilehash: 0bb1ad832fd33675e607874fcc50f20ffbb96943
ms.sourcegitcommit: 26b7404142706290810064f8216abaa1c262d1e5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/16/2020
ms.locfileid: "45145990"
---
# <a name="virtual-assistant-for-microsoft-teams"></a>Assistente virtual para o Microsoft Teams

O virtual Assistant é um modelo de código aberto da Microsoft que permite que você crie uma solução de conversação robusta, mantendo o controle total da experiência do usuário, da identidade visual da organização e dos dados necessários. O [modelo principal do assistente virtual](https://microsoft.github.io/botframework-solutions/overview/virtual-assistant-template) é o bloco de construção básico que reúne as tecnologias da Microsoft necessárias para criar um assistente virtual, incluindo o [SDK da estrutura de bot](https://github.com/microsoft/botframework-sdk), a compreensão da [linguagem (Luis)](https://www.luis.ai/), o [QnA Maker](https://www.qnamaker.ai/), bem como os recursos essenciais, incluindo o registro de habilidades, contas vinculadas, intenção de conversa básica para oferecer aos usuários finais uma variedade de interações e experiências contínuas Além disso, os recursos de modelo incluem exemplos ricos de [habilidades](https://microsoft.github.io/botframework-solutions/overview/skills)de conversa reutilizáveis.  Habilidades individuais podem ser integradas em uma solução de assistente virtual para permitir vários cenários. Usando o SDK da estrutura de bot, as habilidades são apresentadas no formulário de código-fonte, permitindo que você personalize e estenda conforme necessário. Veja [o que é uma habilidade da estrutura de bot](https://microsoft.github.io/botframework-solutions/overview/skills/).

![Diagrama visão geral do assistente virtual](../assets/images/bots/virtual-assistant/overview.png)

As atividades de mensagem de texto são roteadas para habilidades associadas pelo núcleo do assistente virtual usando um modelo de [expedição](/azure/bot-service/bot-builder-tutorial-dispatch?view=azure-bot-service-4.0&tabs=cs) . 

## <a name="implementation-considerations"></a>Considerações de implementação

A decisão de adicionar um assistente virtual pode incluir muitos determinantes e diferentes para cada organização. Estes são os fatores que dão suporte à implementação de um assistente virtual para sua organização:

- Uma equipe central gerencia todas as experiências de funcionários e tem a capacidade de criar uma experiência de assistente virtual e gerenciar atualizações para a experiência principal, incluindo a adição de novas habilidades.
- Existem vários aplicativos nas funções de negócios e/ou o número deve crescer no futuro.
- Os aplicativos existentes são personalizáveis, pertencentes à organização e podem ser convertidos em habilidades para um assistente virtual.
- A equipe central de experiências de funcionários é capaz de influenciar as personalizações para aplicativos existentes e fornecer orientações necessárias para integrar os aplicativos existentes como habilidades na experiência do assistente virtual

![A equipe central mantém o assistente e as equipes de funções corporativas contribuem as habilidades](../assets/images/bots/virtual-assistant/business-functions.png)

## <a name="create-a-teams-focused-virtual-assistant"></a>Criar um assistente virtual focado em equipes

A Microsoft publicou um [modelo do Visual Studio](https://marketplace.visualstudio.com/items?itemName=BotBuilder.VirtualAssistantTemplate) para criar habilidades e assistentes virtuais. Com o modelo do Visual Studio, você pode criar um assistente virtual, equipado com uma experiência baseada em texto com suporte para cartões ricos limitados com ações. Aprimoramos o modelo de base do Visual Studio para incluir recursos de plataforma do Microsoft Teams e experiências de aplicativo para o Power Great Teams. Alguns dos recursos incluem suporte para cartões adaptáveis avançados, módulos de tarefas, bate-papos de equipes/grupos e extensões de mensagens. *Confira também* [o tutorial: Estenda seu assistente virtual para o Microsoft Teams](https://microsoft.github.io/botframework-solutions/clients-and-channels/tutorials/enable-teams/1-intro/).

![Diagrama de alto nível de uma solução de assistente virtual](../assets/images/bots/virtual-assistant/high-level-diagram.png)

### <a name="add-adaptive-cards-to-your-virtual-assistant"></a>Adicionar cartões adaptáveis ao seu assistente virtual

Para distribuir solicitações corretamente, seu assistente virtual precisa identificar o modelo de LUIS correto e a habilidade correspondente associada a ele. No entanto, o mecanismo de expedição não pode ser usado para atividades de ação de cartão, pois o modelo LUIS associado a uma habilidade pode não ser treinado para textos de ação de cartão, uma vez que são palavras-chave predefinidas, não utterances de um usuário.

Resolvemos isso incorporando informações de habilidade na carga de ações do cartão. Cada habilidade deve ser incorporada `skillId` no `value` campo de ações do cartão. Esta é a melhor maneira de garantir que cada atividade de ação de cartão tenha as informações de habilidades relevantes e o assistente virtual podem utilizar essas informações para expedição.

Veja a seguir um exemplo de dados de ação de cartão. Ao fornecer `skillId` o construtor, garantimos que as informações de habilidades estejam sempre presentes em ações de cartão.

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

Em seguida, apresentamos `SkillCardActionData` uma classe no modelo do virtual Assistant para extrair `skillId` da carga de ação do cartão.

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

Veja a seguir um trecho de código para extrair `skillId` dados de ação de cartão. Implementamos como um método de extensão na classe [Activity](https://github.com/microsoft/botframework-sdk/blob/master/specs/botframework-activity/botframework-activity.md) .

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

### <a name="handle-interruptions-gracefully"></a>Controlar as interrupções normalmente

O virtual Assistant pode lidar com interrupções em casos em que um usuário tenta invocar uma habilidade enquanto outra está ativa no momento. Apresentamos `TeamsSkillDialog` e `TeamsSwitchSkillDialog` , com base no [SkillDialog](https://github.com/microsoft/botframework-solutions/blob/5b46d73e220bbb4fba86c48be532e495535ca78a/sdk/csharp/libraries/microsoft.bot.solutions/Skills/SkillDialog.cs) e no [SwitchSkillDialog](https://github.com/microsoft/botframework-solutions/blob/6d40fa8ae05f96b0c5e0464e01361a9e1deb696c/sdk/csharp/libraries/microsoft.bot.solutions/Skills/Dialogs/SwitchSkillDialog.cs)da estrutura de bot, para permitir que os usuários alternem uma experiência de habilidades de ações de cartão. Para lidar com essa solicitação, o virtual Assistant solicita ao usuário uma mensagem de confirmação para trocar de habilidades.

![Prompt de confirmação ao mudar para uma nova habilidade](../assets/images/bots/virtual-assistant/switch-skills-prompt.png)

### <a name="handling-task-module-requests"></a>Tratamento de solicitações de módulo de tarefa

Para adicionar recursos de módulo de tarefa a um assistente virtual, dois métodos adicionais estão incluídos no manipulador de atividade do virtual Assistant: `OnTeamsTaskModuleFetchAsync` e `OnTeamsTaskModuleSubmitAsync` . Esses métodos ouvem as atividades relacionadas ao módulo de tarefas do assistente virtual, identificam a habilidade associada à solicitação e encaminham a solicitação para a habilidade identificada. 

O encaminhamento de solicitação é feito por meio do método [SkillHttpClient](/dotnet/api/microsoft.bot.builder.integration.aspnet.core.skills.skillhttpclient?view=botbuilder-dotnet-stable), `PostActivityAsync` . Ele retorna a resposta como `InvokeResponse` que é analisada e convertida em `TaskModuleResponse` .

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

Uma abordagem semelhante é seguida para respostas de ações de cartão e de módulo de tarefa. Os dados de ação buscar e enviar do módulo de tarefa são atualizados para incluir `skillId` . `GetSkillId`O método de extensão de atividade extrai `skillId` da carga que fornece detalhes sobre a habilidade que precisa ser invocada.

Veja a seguir um trecho de código `OnTeamsTaskModuleFetchAsync` e `OnTeamsTaskModuleSubmitAsync` métodos.

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

Além disso, todos os domínios de habilidade devem ser incluídos na `validDomains` seção no arquivo de manifesto do assistente virtual para que os módulos de tarefa invocados por meio de uma habilidade sejam renderizados adequadamente.

### <a name="handling-collaborative-app-scopes"></a>Lidando com escopos de aplicativos colaborativos

Os aplicativos do teams podem existir em vários escopos, incluindo o chat 1:1, o chat de grupo e os canais. O modelo do assistente virtual principal foi projetado para 1:1 chats. Como parte do assistente virtual de experiência de integração solicita aos usuários o nome e mantém o estado do usuário. Como a experiência de integração não é adequada para o chat de grupo/escopos de canal, ela foi removida.

As habilidades devem lidar com atividades em vários escopos (1:1 chat, chat de grupo e conversa de canal). Se qualquer um desses escopos não for suportado, as habilidades devem responder com uma mensagem apropriada.

As seguintes funções de processamento foram adicionadas ao Core Assistant virtual:

- O assistente virtual pode ser chamado sem nenhuma mensagem de texto de um chat de grupo ou canal.
- Articulations são limpos (ou seja, remova o @mention necessário do bot) antes de enviar a mensagem para o módulo de expedição.

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

### <a name="handling-messaging-extensions"></a>Tratamento de extensões de mensagens

Os comandos para uma extensão de mensagens são declarados no arquivo de manifesto do aplicativo. A interface de usuário de extensão de mensagens é alimentada por esses comandos. Para que um assistente virtual Ligue um comando de extensão de mensagens (como uma habilidade anexada), o próprio manifesto do assistente virtual deve conter esses comandos. Os comandos do manifesto de uma habilidade individual também devem ser adicionados ao manifesto do assistente virtual. A ID do comando fornece informações sobre uma habilidade associada acrescentando a ID do aplicativo da habilidade por um separador ( `:` ).

Veja a seguir um trecho de código do arquivo de manifesto de uma habilidade.

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

E abaixo está o trecho de código do arquivo de manifesto do assistente virtual correspondente.

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

Depois que os comandos são invocados por um usuário, o assistente virtual pode identificar uma habilidade associada analisando a ID do comando, atualizar a atividade removendo o sufixo extra ( `:<skill_id>` ) da ID de comando e encaminhá-lo à habilidade correspondente. O código para uma habilidade não precisa manipular o sufixo extra, portanto, os conflitos entre as IDs de comando nas habilidades são evitados. Com essa abordagem, todos os comandos de ação e de pesquisa de uma habilidade dentro de todos os contextos ("redigir", "commandBox" e "mensagem") podem ser alimentados por um assistente virtual.

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

Algumas atividades de extensão de mensagens não incluem a ID de comando. Por exemplo, `composeExtension/selectItem` contém apenas o valor da ação chamar toque. Para identificar a habilidade associada, o `skillId` está anexado a cada cartão de item ao formar uma resposta para o `OnTeamsMessagingExtensionQueryAsync` . (Isso é semelhante à abordagem de [adição de cartões adaptáveis ao seu assistente virtual](#add-adaptive-cards-to-your-virtual-assistant).

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

## <a name="example-convert-the-book-a-room-app-template-to-a-virtual-assistant-skill"></a>Exemplo: converter o modelo de aplicativo de livro-a-Room em uma habilidade de assistente virtual

[Book-a-Room](app-templates.md#book-a-room) é um [bot do Microsoft Teams](../bots/what-are-bots.md) que permite que os usuários encontrem e reservem rapidamente uma sala de reunião para 30 (padrão), 60 ou 90 minutos a partir da hora atual. Os escopos de bot de livro-a-Room para conversas pessoais ou de 1:1.

![Assistente virtual com uma habilidade de "reservar uma sala"](../assets/images/bots/virtual-assistant/book-a-room-skill.png)

A seguir estão as alterações delta introduzidas para convertê-lo em uma habilidade que pode ser anexada a um assistente virtual. Diretrizes semelhantes podem ser seguidas para converter qualquer bot v4 existente em uma habilidade.

### <a name="skill-manifest"></a>Manifesto de habilidades

Um manifesto de habilidade é um arquivo JSON que expõe o ponto de extremidade de mensagem de uma habilidade, ID, nome e outros metadados relevantes (esse manifesto é diferente do manifesto usado para o Sideload de um aplicativo no Microsoft Teams) um assistente virtual requer um caminho para esse arquivo como uma entrada para anexar uma habilidade. Adicionamos o manifesto a seguir à pasta wwwroot do bot.

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

### <a name="luis-integration"></a>Integração do LUIS

O modelo de expedição do virtual Assistant é construído na parte superior dos modelos LUIS da habilidade associada. O modelo de expedição identifica a intenção de cada atividade de texto e descobre a habilidade associada a ela.

O virtual Assistant requer o modelo de LUIS da habilidade (em `.lu` formato) como uma entrada ao anexar uma habilidade. LUIS JSON pode ser convertido em `.lu` Format usando a ferramenta botframework-CLI.

```json
botskills connect --remoteManifest "<url to skill's manifest>" --luisFolder "<path to the folder containing your Skill's .lu files>" --languages "en-us" --cs
```

```bash
npm i -g @microsoft/botframework-cli
bf luis:convert --in <pathToLUIS.json> --out <pathToLuFile>
```

O bot de livro a sala tem dois comandos principais para os usuários:

- `Book room`
- `Manage Favorites`

Criamos um modelo de LUIS que entende esses dois comandos. Os segredos correspondentes precisam ser preenchidos `cognitivemodels.json` . O arquivo JSON LUIS correspondente pode ser encontrado [aqui](https://github.com/OfficeDev/microsoft-teams-apps-bookaroom/blob/nebhagat/microsoft-teams-apps-bookaroom-skill/Deployment/Resources/LU/book-a-meeting.json) e é assim que o arquivo correspondente se `.lu` parece.

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

Com essa abordagem, qualquer problema de comando de um usuário para o assistente virtual relacionado `book room` ou `manage favorites` pode ser identificado como um comando associado ao bot de livro a sala e é encaminhado para essa habilidade.
Por outro lado, o bot de sala de livros e salas precisa usar o modelo de LUIS para entender esses comandos se não forem digitados como estão (por exemplo: `I want to manage my favorite rooms` ).

### <a name="multi-language-support"></a>Suporte a vários idiomas

Para este exemplo, criamos apenas um modelo LUIS com cultura em inglês. Você pode criar modelos do LUIS correspondentes a outros idiomas e adicionar entrada ao `cognitivemodels.json` .

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

Em paralelo, adicione o `.lu` arquivo correspondente no caminho luisFolder. A estrutura de pastas deve ser a seguinte:

```bash
| - luisFolder

        | - en-us

                | - book-a-meeting.lu

        | - your_language_culture

                | - book-a-meeting.lu
```

Atualize o comando botskills da seguinte maneira para modificar o `languages` parâmetro:

```json
botskills connect --remoteManifest "<url to skill's manifest>" --luisFolder "<path to luisFolder>" --languages "en-us, your_language_culture" --cs
```

O virtual Assistant usa `SetLocaleMiddleware` para identificar a localidade atual e invocar o modelo de expedição correspondente. (A atividade da estrutura do bot tem o campo locale que é usado por este middleware.) Recomendamos usar o mesmo para sua habilidade também. O bot Book-a-Room não usa esse middleware e, em vez disso, obtém a localidade da [entidade clientInfo](https://github.com/microsoft/botframework-sdk/blob/master/specs/botframework-activity/botframework-activity.md#clientinfo)da atividade da estrutura de bot.

### <a name="claim-validation"></a>Validação de declaração

Adicionamos [claimsValidator](https://github.com/nebhagat/msteams-virtual-assistant-dotnet/blob/master/msteams-virtual-assistant-dotnet/Authentication/AllowedCallersClaimsValidator.cs) para restringir os chamadores à habilidade. Para permitir que um assistente virtual Chame essa habilidade, preencha a `AllowedCallers` matriz `appsettings` com essa ID de aplicativo do assistente virtual específico.

```
"AllowedCallers": [ "<caller_VA1_appId>", "<caller_VA2_appId>" ],
```

A matriz de chamadores permitidos pode restringir quais consumidores de habilidade podem acessar a habilidade. Adicione uma única entrada `*` a esta matriz para aceitar chamadas de qualquer consumidor de habilidades.

```
"AllowedCallers": [ "*" ],
```
A documentação detalhada para a adição de validação de declarações a uma habilidade pode ser encontrada [aqui](https://docs.microsoft.com/azure/bot-service/skill-implement-skill?view=azure-bot-service-4.0&tabs=cs#claims-validator).

### <a name="card-refresh-limitation"></a>Limitação de atualização de cartão

A atualização da atividade (atualização de cartão) ainda não é suportada por meio do virtual Assistant ([problema do GitHub](https://github.com/microsoft/botbuilder-dotnet/issues/3686)). Portanto, substituimos todas as chamadas de atualização de cartão ( `UpdateActivityAsync` ) por postar novas chamadas de cartão ( `SendActivityAsync` ).

### <a name="card-actions-and-task-module-flows"></a>Ações de cartão e fluxos de módulo de tarefa

Para encaminhar as atividades de cartão ou de módulo de tarefa para uma habilidade associada, a habilidade precisa incorporá `skillId` -la.
A ação de cartão de bot de livro-a-Room, busca e envio de cargas de ação são modificadas para conter `skillId` como um parâmetro. 

Para obter mais informações, consulte [esta](https://msteams-captain.visualstudio.com/xGrowth%20App%20Templates/_wiki/wikis/xGrowth.wiki/88/Virtual-Assistant-for-MS-Teams?anchor=rich-cards) seção nesta documentação.

### <a name="handle-activities-from-group-chat-or-channel-scope"></a>Gerenciar atividades de chat de grupo ou escopo de canal

O bot de livro-a-Room é projetado apenas para chats privados (escopo pessoal/1:1). Como o virtual Assistant foi personalizado para oferecer suporte ao chat de grupo e escopos de canal, o assistente virtual pode ser invocado desses escopos e, portanto, o bot de livro-a-Room pode obter atividades para o mesmo. Logo, o bot Book-a-Room é personalizado para lidar com essas atividades. O cheque foi colocado em `OnMessageActivityAsync` métodos do manipulador de atividade do bot do Book-a-Room.

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

Você também pode aproveitar as habilidades existentes do [repositório do bot Framework Solutions](https://github.com/microsoft/botframework-solutions/tree/master/skills/csharp) ou criar uma nova habilidade totalmente a partir do zero. Os tutoriais do mais recentes podem ser encontrados [aqui](https://microsoft.github.io/botframework-solutions/overview/skills/). Consulte a [documentação](https://docs.microsoft.com/azure/bot-service/skills-conceptual?view=azure-bot-service-4.0) do assistente virtual e da arquitetura de habilidades.

## <a name="sample-code-to-get-started"></a>Exemplo de código para começar

- [Modelo do Visual Studio atualizado](https://github.com/nebhagat/msteams-virtual-assistant-dotnet)
- [Código de qualificação de bot de livro a Room](https://github.com/OfficeDev/microsoft-teams-apps-bookaroom/tree/nebhagat/microsoft-teams-apps-bookaroom-skill)

## <a name="virtual-assistant-known-limitations"></a>Limitações conhecidas do assistente virtual

- **EndOfConversation**. Uma habilidade deve enviar uma `endOfConversation` atividade ao concluir uma conversa. com base nessa atividade, um assistente virtual termina o contexto com essa determinada habilidade e retorna ao contexto do virtual Assistant (raiz). Para o bot de livro-a-Room, não há estado claro em que a conversa pode ser concluída. Portanto, não enviamos `endOfConversation` o bot de livro a sala e quando o usuário deseja voltar para o contexto raiz eles podem simplesmente fazer isso por `start over` comando.
- **Atualização de cartão**. As atualizações de cartão ainda não são suportadas pelo virtual Assistant.
- **Extensões de mensagens**.:
  - Atualmente, um assistente virtual pode dar suporte a um máximo de dez comandos para extensões de mensagens.
  - A configuração de extensões de mensagens não é delimitada por comandos individuais, mas apenas para toda a extensão. Isso limita a configuração de cada habilidade individual pelo assistente virtual.
  - As IDs de comando de extensões de mensagens têm um tamanho máximo de [64 caracteres](../resources/schema/manifest-schema.md#composeextensions) e 37 caracteres serão usados para inserir informações de habilidades. Portanto, as restrições atualizadas para a ID de comando são limitadas a 27 caracteres.
>
>
