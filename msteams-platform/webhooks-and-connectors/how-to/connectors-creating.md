---
title: Conectores de Office 365
description: Descreve como começar com Office 365 Conectores em Microsoft Teams
keywords: conector do o365 no teams
localization_priority: Normal
ms.topic: conceptual
ms.date: 04/19/2019
ms.openlocfilehash: 9eaaedf88d907dd7a7422068ab5d20450345f0e7
ms.sourcegitcommit: 51e4a1464ea58c254ad6bd0317aca03ebf6bf1f6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2021
ms.locfileid: "52566807"
---
# <a name="creating-office-365-connectors-for-microsoft-teams"></a>Criando conectores de Office 365 para Microsoft Teams

>Com Microsoft Teams aplicativos, você pode adicionar seu conector Office 365 existente ou construir um novo para incluir em Microsoft Teams. Consulte [Construir seu próprio Conector](/outlook/actionable-messages/connectors-dev-dashboard#build-your-own-connector) para obter mais informações.

## <a name="adding-a-connector-to-your-teams-app"></a>Adicionando um Conector ao seu aplicativo Teams

Você pode distribuir seu Conector registrado como parte do pacote de aplicativos do Teams. Seja como uma solução autônoma ou um dos vários [recursos](~/concepts/extensibility-points.md) que sua experiência permite em Teams, você pode [empacotar](~/concepts/build-and-test/apps-package.md) e [publicar](~/concepts/deploy-and-publish/apps-publish.md) seu Conector como parte de sua submissão appSource, ou você pode fornecê-lo diretamente aos usuários para upload dentro de Teams.

Para distribuir seu Conector, você precisa se registrar usando o [Painel de Desenvolvedor de Conectores](https://outlook.office.com/connectors/home/login/#/publish). Por padrão, uma vez que um Conector é registrado, presume-se que seu Conector funcionará em todos os Office 365 produtos que os suportam, incluindo Outlook e Teams. Se esse _não_ for o caso e você precisar criar um Conector que só funciona em Microsoft Teams, entre em contato diretamente conosco [em Microsoft Teams Submissões de Aplicativos](mailto:teamsubm@microsoft.com).

> [!IMPORTANT]
> Depois de escolher **Salvar** no Painel de Desenvolvedor de Conectores, seu Conector é registrado. Se você quiser publicar seu Conector no AppSource, siga as instruções em [Publicar seu aplicativo Microsoft Teams para AppSource](~/concepts/deploy-and-publish/apps-publish.md). Se você não deseja publicar seu aplicativo no AppSource e, em vez disso, simplesmente distribuí-lo diretamente para sua organização, você pode fazê-lo [publicando para sua organização](#publish-connectors-for-your-organization). Se você quiser publicar apenas para sua organização, nenhuma ação adicional é necessária no painel Conector.

### <a name="integrating-the-configuration-experience"></a>Integrando a experiência de configuração

Seus usuários completarão toda a experiência de configuração do Connector sem ter que deixar o Teams cliente. Para alcançar essa experiência, Teams incorporará sua página de configuração diretamente dentro de um iframe. A sequência de operações é a seguinte:

1. O usuário clica no conector para iniciar o processo de configuração.
2. Teams carregará sua experiência de configuração em linha.
3. O usuário interage com sua experiência na Web para completar a configuração.
4. O usuário pressiona "Salvar", o que aciona um retorno de chamada em seu código.
5. Seu código processará o evento de salvamento recuperando as configurações do webhook (documentado abaixo). Seu código deve então armazenar o webhook para postar eventos mais tarde.

Você pode reutilizar sua experiência de configuração web existente ou criar uma versão separada para ser hospedada especificamente em Teams. Seu código deve:

1. Inclua o Microsoft Teams JavaScript SDK. Isso dá ao seu código acesso às APIs para realizar operações comuns, como obter o contexto atual do usuário/canal/equipe e iniciar fluxos de autenticação. Inicializar o SDK chamando `microsoftTeams.initialize()`.
2. Ligue `microsoftTeams.settings.setValidityState(true)` quando quiser ativar o botão Salvar. Você deve fazer isso como uma resposta à entrada de usuário válida, como uma seleção ou atualização de campo.
3. Registre um `microsoftTeams.settings.registerOnSaveHandler()` manipulador de eventos, que é chamado quando o usuário clica em Salvar.
4. Chamada `microsoftTeams.settings.setSettings()` para salvar as configurações do conector. O que é salvo aqui também é o que será mostrado na caixa de diálogo de configuração se o usuário tentar atualizar uma configuração existente para o seu conector.
5. Chamada `microsoftTeams.settings.getSettings()` para buscar propriedades webhook, incluindo a url em si. Você deve chamá-lo Além de durante o evento salvar, você também deve chamá-lo quando sua página é carregada pela primeira vez no caso de uma re-configuração.
6. (Opcional) Registre um `microsoftTeams.settings.registerOnRemoveHandler()` manipulador de eventos, que é chamado quando o usuário remove seu conector. Este evento dá ao seu serviço a oportunidade de realizar quaisquer ações de limpeza.

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
>Os parâmetros retornados pela `getSettings` chamada aqui são diferentes do que se você fosse invocar este método a partir de uma guia, e diferem daqueles documentados [aqui](/javascript/api/%40microsoft/teams-js/settings.settings?view=msteams-client-js-latest&preserve-view=true).

| Parâmetro   | Detalhes |
|-------------|---------|
| `entityId`       | O ID da entidade, conforme definido pelo seu código ao `setSettings()` ligar. |
| `configName`  | O nome de configuração, conforme definido pelo seu código ao chamar `setSettings()` . |
| `contentUrl` | A URL da página de configuração, conforme definido pelo seu código ao chamar `setSettings()` . |
| `webhookUrl` | A URL do webhook criada para este conector. Persista a URL do webhook e use-a para POST estruturada JSON para enviar cartões para o canal. A `webhookUrl` é retornada quando o aplicativo retorna com êxito. |
| `appType` | Os valores retornados podem ser `mail`, `groups` ou `teams` correspondente ao Email do Office 365, Grupos do Office 365 ou Microsoft Teams respectivamente. |
| `userObjectId` | Este é o id único correspondente ao usuário Office 365 que iniciou a configuração do conector. Ela deve ser protegida. Este valor pode ser usado para associar o usuário no Office 365 que realizou a configuração para o usuário no seu serviço. |

Se você precisar autenticar o usuário como parte do carregamento da sua página na etapa 2 acima, consulte [este link](~/tabs/how-to/authentication/auth-flow-tab.md) para obter detalhes sobre como você pode integrar o login quando sua página estiver incorporada.

> [!NOTE]
> Devido a razões de compatibilidade entre clientes, seu código precisará ligar `microsoftTeams.authentication.registerAuthenticationHandlers()` com a URL e os métodos de retorno de chamada de sucesso/falha antes de chamar `authenticate()` .

#### <a name="handling-edits"></a>Manipulação de edições

O código deve lidar com o retorno de usuários para editar uma configuração de conector existente. Para isso, ligue `microsoftTeams.settings.setSettings()` durante a configuração inicial com os seguintes parâmetros:

- `entityId` é o ID personalizado que é entendido pelo seu serviço e representa o que o usuário configurou.
- `configName` é um nome amigável que seu código de configuração pode recuperar
- `contentUrl` é uma URL personalizada que é carregada quando um usuário edita uma configuração de conector existente. Você pode usar esta URL para facilitar o seu código para lidar com o caso de edição.

Normalmente, esta chamada é feita como parte do seu manipulador de eventos de salvamento. Em seguida, quando o `contentUrl` acima estiver carregado, seu código deve chamar `getSettings()` para prepovoar quaisquer configurações ou formulários em sua interface de configuração.

#### <a name="handling-removals"></a>Manipulação de remoções

Você pode executar opcionalmente um manipulador de eventos quando o usuário remove uma configuração de conector existente. Registre este manipulador `microsoftTeams.settings.registerOnRemoveHandler()` ligando. Este manipulador pode ser usado para executar operações de limpeza, como remover entradas de um banco de dados.

### <a name="including-the-connector-in-your-manifest"></a>Incluindo o Conector em seu Manifesto

Você pode baixar o manifesto de aplicativo Teams gerado automaticamente no portal. Antes de usá-lo para testar ou publicar seu aplicativo, porém, você deve fazer o seguinte:

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

Agora você pode iniciar a experiência de configuração. Esteja ciente de que esse fluxo ocorre inteiramente dentro de Microsoft Teams como uma experiência hospedada.

Para verificar se uma `HttpPOST` ação está funcionando corretamente, [envie mensagens para o seu conector](~/webhooks-and-connectors/how-to/connectors-using.md).

## <a name="publish-connectors-for-your-organization"></a>Publique conectores para sua organização

Às vezes, você pode não querer publicar seu aplicativo de conector para o appsource/store público, mas gostaria que ele estivesse disponível apenas para os usuários da sua organização. Nesses casos, você pode carregar seu aplicativo de conector personalizado para o [Catálogo de Aplicativos da](~/concepts/deploy-and-publish/apps-publish.md)sua organização . Dessa forma, seu aplicativo de conector estará disponível apenas para essa organização, e você não precisará publicar seu conector na loja pública.

Depois de carregar seu pacote de aplicativos, para configurar e usar o conector em uma equipe, ele pode ser instalado a partir do catálogo de aplicativos da organização seguindo estas etapas:

1. Selecione o ícone de aplicativos da barra de navegação vertical de extrema esquerda.
1. Na janela **Aplicativos** selecione **Conectores**.
1. Selecione o conector que deseja adicionar e uma janela de diálogo pop-up será exibida.
1. Selecione **o Adicionar a uma** barra de equipe.
1. Na próxima janela de diálogo digite um nome de equipe ou canal.
1. Selecione configurar uma barra **de conector** no canto inferior direito da janela de diálogo.
1. O conector estará disponível na seção &#9679;&#9679;&#9679; => *Mais opções*  =>  *Conectores*  =>  *Todos os*  =>  *Conectores para sua equipe* para essa equipe. Você pode navegar rolando para esta seção ou procurar o aplicativo conector.
1. Para configurar ou modificar o conector selecione a barra **Configurar.**

## <a name="code-sample"></a>Exemplo de código
|**Nome da amostra** | **Descrição** | **.NET** | **Node.js** |
|----------------|------------------|--------|----------------|
| Conectores    | Amostra Office 365 Conector gerando notificações ao canal das equipes.|   [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/connector-todo-notification/csharp) | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/connector-github-notification/nodejs)|
| Amostra de conectores genéricos |Código de amostra para um conector genérico que é fácil de personalizar para qualquer sistema que suporte webhooks.|  | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/connector-generic/nodejs)|
