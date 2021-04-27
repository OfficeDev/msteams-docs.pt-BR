---
title: Conectores de Office 365
description: Descreve como começar a usar os Conectores do Office 365 no Microsoft Teams
keywords: conector do o365 no teams
localization_priority: Normal
ms.topic: conceptual
ms.date: 04/19/2019
ms.openlocfilehash: 8091f71e22fcbdc297e2f7b54665b47e597e670e
ms.sourcegitcommit: 825abed2f8784d2bab7407ba7a4455ae17bbd28f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2021
ms.locfileid: "52018394"
---
# <a name="creating-office-365-connectors-for-microsoft-teams"></a>Criando conectores do Office 365 para o Microsoft Teams

>Com os aplicativos do Microsoft Teams, você pode adicionar seu Conector do Office 365 existente ou criar um novo para incluir no Microsoft Teams. Confira [Criar seu próprio Conector para](/outlook/actionable-messages/connectors-dev-dashboard#build-your-own-connector) obter mais informações.

## <a name="adding-a-connector-to-your-teams-app"></a>Adicionando um Conector ao seu Aplicativo do Teams

Você pode distribuir seu Conector registrado como parte do pacote de aplicativos do Teams. Seja como uma solução autônoma ou um dos vários recursos que sua [](~/concepts/build-and-test/apps-package.md) experiência [](~/concepts/deploy-and-publish/apps-publish.md) habilita no Teams, você pode empacotar e publicar seu Conector como parte do envio do AppSource ou você pode fornecer aos usuários diretamente para carregar no Teams. [](~/concepts/extensibility-points.md)

Para distribuir seu Conector, você precisa se registrar usando o Painel do Desenvolvedor [de Conectores.](https://outlook.office.com/connectors/home/login/#/publish) Por padrão, depois que um Conector é registrado, presume-se que seu Conector funcionará em todos os produtos do Office 365 que os suportam, incluindo Outlook e Teams. Se esse não _for o_ caso e você precisar criar um Conector que funcione apenas no Microsoft Teams, entre em contato conosco diretamente em Envios de [Aplicativos do Microsoft Teams.](mailto:teamsubm@microsoft.com)

> [!IMPORTANT]
> Depois de escolher **Salvar** no Painel do Desenvolvedor de Conectores, seu Conector será registrado. Se você quiser publicar seu Conector no AppSource, siga as instruções em Publicar seu [aplicativo do Microsoft Teams no AppSource](~/concepts/deploy-and-publish/apps-publish.md). Se você não quiser publicar seu aplicativo no AppSource e, em vez disso, simplesmente distribuí-lo diretamente para sua organização, você pode fazer isso publicando em [sua organização.](#publish-connectors-for-your-organization) Se você quiser apenas publicar em sua organização, nenhuma ação será necessária no painel conector.

### <a name="integrating-the-configuration-experience"></a>Integrando a experiência de configuração

Seus usuários concluirão toda a experiência de configuração do Conector sem precisar sair do cliente do Teams. Para atingir essa experiência, o Teams incorporará sua página de configuração diretamente em um iframe. A sequência de operações é a seguinte:

1. O usuário clica no conector para iniciar o processo de configuração.
2. O Teams carregará sua experiência de configuração em linha.
3. O usuário interage com sua experiência da Web para concluir a configuração.
4. O usuário pressiona "Salvar", que dispara um retorno de chamada em seu código.
5. Seu código processará o evento save recuperando as configurações de webhook (documentadas abaixo). Em seguida, seu código deve armazenar o webhook para postar eventos posteriormente.

Você pode reutilizar sua experiência de configuração da Web existente ou criar uma versão separada para ser hospedada especificamente no Teams. Seu código deve:

1. Inclua o SDK JavaScript do Microsoft Teams. Isso fornece acesso de código a APIs para executar operações comuns, como obter o contexto atual de usuário/canal/equipe e iniciar fluxos de autenticação. Inicializar o SDK chamando `microsoftTeams.initialize()`.
2. Chame `microsoftTeams.settings.setValidityState(true)` quando quiser habilitar o botão Salvar. Você deve fazer isso como uma resposta à entrada de usuário válida, como uma seleção ou uma atualização de campo.
3. Registre `microsoftTeams.settings.registerOnSaveHandler()` um manipulador de eventos, que é chamado quando o usuário clica em Salvar.
4. Chame `microsoftTeams.settings.setSettings()` para salvar as configurações do conector. O que é salvo aqui também é o que será mostrado na caixa de diálogo de configuração se o usuário tentar atualizar uma configuração existente para o conector.
5. Chame `microsoftTeams.settings.getSettings()` para buscar propriedades de webhook, incluindo a PRÓPRIA URL. Você deve chamar isso Além de durante o evento save, você também deve chamar isso quando sua página for carregada pela primeira vez no caso de uma nova configuração.
6. (Opcional) Registre `microsoftTeams.settings.registerOnRemoveHandler()` um manipulador de eventos, que é chamado quando o usuário remove o conector. Esse evento oferece ao seu serviço a oportunidade de executar qualquer ação de limpeza.

Aqui está um HTML de exemplo para criar uma página de configuração do Conector sem o CSS:

```html
<h2>Send notifications when tasks are:</h2>
<div class="col-md-8">
    <section id="configSection">
        <form id="configForm">
            <input type="radio" name="notificationType" value="Create" onclick="onClick()"> Created
            <br>
            <br>
            <input type="radio" name="notificationType" value="Update" onclick="onClick()"> Updated
        </form>
    </section>
</div>

<script src="https://statics.teams.microsoft.com/sdk/v1.5.2/js/MicrosoftTeams.min.js" crossorigin="anonymous"></script>
<script src="/Scripts/jquery-1.10.2.js"></script>

<script type="text/javascript">

        function onClick() {
            microsoftTeams.settings.setValidityState(true);
        }

        microsoftTeams.initialize();
        microsoftTeams.settings.registerOnSaveHandler(function (saveEvent) {
            var radios = document.getElementsByName('notificationType');

            var eventType = '';
            if (radios[0].checked) {
                eventType = radios[0].value;
            } else {
                eventType = radios[1].value;
            }

            microsoftTeams.settings.setSettings({
                 entityId: eventType,
                contentUrl: "https://YourSite/Connector/Setup",
                removeUrl:"https://YourSite/Connector/Setup",
                 configName: eventType
                });

            microsoftTeams.settings.getSettings(function (settings) {
                // We get the Webhook URL in settings.webhookUrl which needs to be saved. 
                // This can be used later to send notification.
            });

            saveEvent.notifySuccess();
        });

        microsoftTeams.settings.registerOnRemoveHandler(function (removeEvent) {
            alert("Removed" + JSON.stringify(removeEvent));
        });

</script>
```

#### <a name="getsettings-response-properties"></a>`GetSettings()` propriedades de resposta

>[!Note]
>Os parâmetros retornados pela chamada aqui são diferentes do que se você fosse invocar esse método de uma guia e diferir daqueles `getSettings` documentados [aqui](/javascript/api/%40microsoft/teams-js/settings.settings?view=msteams-client-js-latest&preserve-view=true).

| Parâmetro   | Detalhes |
|-------------|---------|
| `entityId`       | A ID da entidade, conforme definido pelo código ao chamar `setSettings()` . |
| `configName`  | O nome da configuração, conforme definido pelo código ao chamar `setSettings()` . |
| `contentUrl` | A URL da página de configuração, conforme definido pelo código ao chamar `setSettings()` |
| `webhookUrl` | A URL de webhook criada para esse conector. Persista a URL do webhook e use-a para POSTAR JSON estruturado para enviar cartões para o canal. A `webhookUrl` é retornada quando o aplicativo retorna com êxito. |
| `appType` | Os valores retornados podem ser `mail`, `groups` ou `teams` correspondente ao Email do Office 365, Grupos do Office 365 ou Microsoft Teams respectivamente. |
| `userObjectId` | Esta é a id exclusiva correspondente ao usuário do Office 365 que iniciou a instalação do conector. Ela deve ser protegida. Este valor pode ser usado para associar o usuário no Office 365 que realizou a configuração para o usuário no seu serviço. |

Se você precisar autenticar o usuário como parte do carregamento de sua página na etapa 2 acima, consulte este [link](~/tabs/how-to/authentication/auth-flow-tab.md) para obter detalhes sobre como você pode integrar o logon quando sua página é incorporada.

> [!NOTE]
> Devido a motivos de compatibilidade entre clientes, seu código precisará chamar com a URL e os métodos de retorno de chamada de `microsoftTeams.authentication.registerAuthenticationHandlers()` sucesso/falha antes de chamar `authenticate()` .

#### <a name="handling-edits"></a>Manipulando edições

O código deve lidar com o retorno de usuários para editar uma configuração de conector existente. Para fazer isso, chame `microsoftTeams.settings.setSettings()` durante a configuração inicial com os seguintes parâmetros:

- `entityId` é a ID personalizada que é compreendida pelo seu serviço e representa o que o usuário configurou.
- `configName` é um nome amigável que seu código de configuração pode recuperar
- `contentUrl` é uma URL personalizada que é carregada quando um usuário edita uma configuração de conector existente. Você pode usar essa URL para facilitar o seu código lidar com o caso de edição.

Normalmente, essa chamada é feita como parte do manipulador de eventos save. Em seguida, quando o acima for carregado, seu código deverá chamar para pré-estipular quaisquer configurações ou formulários na interface do usuário `contentUrl` `getSettings()` de configuração.

#### <a name="handling-removals"></a>Manipulando remoções

Opcionalmente, você pode executar um manipulador de eventos quando o usuário remover uma configuração de conector existente. Você registra esse manipulador chamando `microsoftTeams.settings.registerOnRemoveHandler()` . Esse manipulador pode ser usado para executar operações de limpeza, como a remoção de entradas de um banco de dados.

### <a name="including-the-connector-in-your-manifest"></a>Incluindo o Conector em seu Manifesto

Você pode baixar o manifesto do aplicativo do Teams gerado automaticamente no portal. Antes de usá-lo para testar ou publicar seu aplicativo, você deve fazer o seguinte:

- [Incluir dois ícones](../../concepts/build-and-test/apps-package.md#app-icons).
- Modifique a parte dos `icons` do manifesto para se referir aos nomes de arquivo dos ícones em vez das URLs.

O seguinte arquivo manifest.json contém os elementos básicos necessários para testar e enviar seu aplicativo.

> [!NOTE]
> Substitua `id` e `connectorId` no exemplo a seguir pelo GUID do Conector.

#### <a name="example-manifestjson-with-connector"></a>Exemplo de manifest.json com o Conector

```json
{
  "$schema": "https://developer.microsoft.com/json-schemas/teams/v1.8/MicrosoftTeams.schema.json",
  "manifestVersion": "1.5",
  "id": "e9343a03-0a5e-4c1f-95a8-263a565505a5",
  "version": "1.0",
  "packageName": "com.sampleapp",
  "developer": {
    "name": "Publisher",
    "websiteUrl": "https://www.microsoft.com",
    "privacyUrl": "https://www.microsoft.com",
    "termsOfUseUrl": "https://www.microsoft.com"
  },
  "description": {
    "full": "This is a sample manifest for an app with a connector with an inline configuration experience.",
    "short": "This is a sample manifest for an app with a connector."
  },
  "icons": {
    "outline": "sampleapp-outline.png",
    "color": "sampleapp-color.png"
  },
  "connectors": [
    {
      "connectorId": "e9343a03-0a5e-4c1f-95a8-263a565505a5",
      "configurationUrl": "https://teamstodoappconnectorwithinlineconfig.azurewebsites.net/Connector/Setup",
      "scopes": [
        "team"
      ]
    }
  ],
  "name": {
    "short": "Sample App",
    "full": "Sample App Long Name"
  },
  "accentColor": "#FFFFFF"
}
```

## <a name="testing-your-connector"></a>Testar o Conector

Para testar o Conector, carregue-o em uma equipe, como em qualquer outro aplicativo. Você pode criar um pacote .zip usando o arquivo de manifesto do Painel do Desenvolvedor do Connectors (modificado conforme indicado na seção anterior) e os dois arquivos de ícone.

Depois de carregar o aplicativo, abra a lista de conectores em qualquer canal. Role até a parte inferior para ver o aplicativo na seção **Carregado**.

![Captura de tela da seção carregada na caixa de diálogo do Conector](~/assets/images/connectors/connector_dialog_uploaded.png)

Agora você pode iniciar a experiência de configuração. Esteja ciente de que esse fluxo ocorre inteiramente dentro do Microsoft Teams como uma experiência hospedada.

Para verificar se uma `HttpPOST` ação está funcionando corretamente, [envie mensagens para seu conector](~/webhooks-and-connectors/how-to/connectors-using.md).

## <a name="publish-connectors-for-your-organization"></a>Publicar Conectores para sua organização

Às vezes, talvez você não queira publicar seu aplicativo conector na AppSource/Store pública, mas gostaria que ele fosse disponibilizado apenas para os usuários em sua organização. Nesses casos, você pode carregar seu aplicativo de conector personalizado no Catálogo de [Aplicativos da sua organização.](~/concepts/deploy-and-publish/apps-publish.md) Dessa forma, seu aplicativo conector estará disponível apenas para essa organização e você não precisará publicar seu conector no armazenamento público.

Depois de carregar seu pacote de aplicativos, para configurar e usar o conector em uma Equipe, ele pode ser instalado no catálogo de aplicativos da organização seguindo estas etapas:

1. Selecione o ícone de aplicativos na barra de navegação vertical extrema esquerda.
1. Na janela **Aplicativos,** selecione **Conectores**.
1. Selecione o conector que você deseja adicionar e uma janela de diálogo pop-up será exibida.
1. Selecione a **barra Adicionar a uma equipe.**
1. Na próxima janela de diálogo, digite um nome de equipe ou canal.
1. Selecione a **barra Configurar um conector** no canto inferior direito da janela de diálogo.
1. O conector estará disponível na seção &#9679;&#9679;&#9679; => *Mais* opções Conectores Todos os Conectores para você  =>    =>    =>  *equipe* para essa equipe. Você pode navegar rolando até esta seção ou pesquisar o aplicativo do conector.
1. Para configurar ou modificar o conector, selecione a **barra Configurar.**

## <a name="code-sample"></a>Exemplo de código
|**Exemplo de nome** | **Descrição** | **.NET** | **Node.js** |
|----------------|------------------|--------|----------------|
| Conectores    | Exemplo do Conector do Office 365 gerando notificações para o canal do Teams.|   [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/connector-todo-notification/csharp) | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/connector-github-notification/nodejs)|
| Exemplo de conectores genéricos |Exemplo de código para um conector genérico que é fácil de personalizar para qualquer sistema que oferece suporte a webhooks.|  | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/connector-generic/nodejs)|
