---
title: Conectores de Office 365
description: Descreve como começar a usar os conectores do Office 365 no Microsoft Teams
keywords: conector do o365 no teams
ms.date: 04/19/2019
ms.openlocfilehash: dcd9f7e68dfe834fbcac245941944007beedf478
ms.sourcegitcommit: 0aeb60027f423d8ceff3b377db8c3efbb6da4d17
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/11/2020
ms.locfileid: "48998018"
---
# <a name="creating-office-365-connectors-for-microsoft-teams"></a>Criando conectores do Office 365 para o Microsoft Teams

>Com os aplicativos do Microsoft Teams, você pode adicionar seu conector existente do Office 365 ou criar um novo para incluir no Microsoft Teams. Confira [compilar seu próprio conector](/outlook/actionable-messages/connectors-dev-dashboard#build-your-own-connector) para obter mais informações.

## <a name="adding-a-connector-to-your-teams-app"></a>Adicionando um conector ao aplicativo do Microsoft Teams

Você pode distribuir seu conector registrado como parte do seu pacote de aplicativos do Microsoft Teams. Seja como uma solução autônoma ou um dos vários [recursos](~/concepts/extensibility-points.md) que sua experiência habilita no Teams, você pode [empacotar](~/concepts/build-and-test/apps-package.md) e [publicar](~/concepts/deploy-and-publish/apps-publish.md) seu conector como parte do seu envio do AppSource ou pode fornecer os usuários diretamente para upload no Microsoft Teams.

Para distribuir seu conector, você precisa se registrar usando o [painel do desenvolvedor conectores](https://outlook.office.com/connectors/home/login/#/publish). Por padrão, quando um conector é registrado, supõe-se que seu conector funcionará em todos os produtos do Office 365 que dão suporte a eles, incluindo o Outlook e o Microsoft Teams. Se esse _não_ for o caso e você precisar criar um conector que funciona apenas no Microsoft Teams, fale conosco diretamente nos [envios de aplicativos do Microsoft Teams](mailto:teamsubm@microsoft.com).

> [!IMPORTANT]
> Após escolher **salvar** no painel do desenvolvedor conectores, seu conector é registrado. Se você deseja publicar seu conector no AppSource, siga as instruções em [publicar seu aplicativo do Microsoft Teams para o AppSource](~/concepts/deploy-and-publish/apps-publish.md). Se você não deseja publicar seu aplicativo no AppSource e, em vez disso, apenas distribuí-lo diretamente para sua organização, você pode fazer isso [publicando em sua organização](#publish-connectors-for-your-organization). Se você só quiser publicar na sua organização, nenhuma ação adicional será necessária no painel do conector.

### <a name="integrating-the-configuration-experience"></a>Integração da experiência de configuração

Os usuários vão concluir toda a experiência de configuração do conector sem ter que sair do cliente do teams. Para obter essa experiência, o Microsoft Teams incorporará a página de configuração diretamente em um iframe. A sequência de operações é a seguinte:

1. O usuário clica no seu conector para começar o processo de configuração.
2. O Microsoft Teams carregará sua experiência de configuração em linha.
3. O usuário interage com sua experiência na Web para concluir a configuração.
4. O usuário pressiona "Save", que dispara um retorno de chamada em seu código.
5. Seu código processará o evento Save recuperando as configurações de webhook (documentadas abaixo). O código deve armazenar o webhook para postar eventos mais tarde.

Você pode reutilizar sua experiência de configuração da Web existente ou criar uma versão separada para ser hospedada especificamente no Teams. O código deve:

1. Inclua o SDK do JavaScript do Microsoft Teams. Isso dá a seu código acesso às APIs para executar operações comuns, como obter o contexto de usuário/canal/equipe atual e iniciar fluxos de autenticação. Inicialize o SDK ligando `microsoftTeams.initialize()` .
2. Chame `microsoftTeams.settings.setValidityState(true)` quando você deseja habilitar o botão salvar. Você deve fazer isso como uma resposta a uma entrada de usuário válida, como uma seleção ou uma atualização de campo.
3. Registre um `microsoftTeams.settings.registerOnSaveHandler()` manipulador de eventos, que é chamado quando o usuário clica em salvar.
4. Chame `microsoftTeams.settings.setSettings()` para salvar as configurações do conector. O que é salvo aqui também é o que será mostrado na caixa de diálogo de configuração se o usuário tentar atualizar uma configuração existente para o seu conector.
5. Chamada `microsoftTeams.settings.getSettings()` para buscar Propriedades de webhook, incluindo a própria URL. Você deve chamá-lo além de durante o evento Save, você também deve chamá-lo quando sua página é carregada pela primeira vez no caso de uma reconfiguração.
6. Opcion Registre um `microsoftTeams.settings.registerOnRemoveHandler()` manipulador de eventos, que é chamado quando o usuário remove seu conector. Esse evento dá ao seu serviço uma oportunidade de realizar qualquer ação de limpeza.

#### <a name="getsettings-response-properties"></a>`GetSettings()` Propriedades de resposta

>[!Note]
>Os parâmetros retornados pela `getSettings` chamada aqui são diferentes de se você fosse invocar esse método a partir de uma guia e difere daqueles documentados [aqui](/javascript/api/%40microsoft/teams-js/settings.settings?view=msteams-client-js-latest&preserve-view=true).

| Parâmetro   | Detalhes |
|-------------|---------|
| `entityId`       | A ID da entidade, conforme definido pelo código ao chamar `setSettings()` . |
| `configName`  | O nome da configuração, conforme definido pelo código ao chamar `setSettings()` . |
| `contentUrl` | A URL da página de configuração, conforme definido pelo seu código ao chamar `setSettings()` |
| `webhookUrl` | A URL do webhook criada para esse conector. Persista a URL do webhook e use-a para publicar o JSON estruturado para enviar cartões ao canal. A `webhookUrl` é retornada quando o aplicativo retorna com êxito. |
| `appType` | Os valores retornados podem ser `mail`, `groups` ou `teams` correspondente ao Email do Office 365, Grupos do Office 365 ou Microsoft Teams respectivamente. |
| `userObjectId` | Esta é a ID exclusiva correspondente ao usuário do Office 365 que iniciou a configuração do conector. Ela deve ser protegida. Este valor pode ser usado para associar o usuário no Office 365 que realizou a configuração para o usuário no seu serviço. |

Se você precisar autenticar o usuário como parte do carregamento da página na etapa 2 acima, consulte [este link](~/tabs/how-to/authentication/auth-flow-tab.md) para obter detalhes sobre como você pode integrar o logon quando sua página é incorporada.

> [!NOTE]
> Devido a motivos de compatibilidade entre clientes, seu código precisará chamar `microsoftTeams.authentication.registerAuthenticationHandlers()` os métodos de retorno de chamada URL e Success/Failure antes de chamar `authenticate()` .

#### <a name="handling-edits"></a>Como lidar com edições

O código deve lidar com usuários que retornam para editar uma configuração de conector existente. Para fazer isso, chame `microsoftTeams.settings.setSettings()` durante a configuração inicial com os seguintes parâmetros:

- `entityId` é a identificação personalizada que é compreendida pelo serviço e que representa o que o usuário configurou.
- `configName` é um nome amigável que o código de configuração pode recuperar
- `contentUrl` é uma URL personalizada que é carregada quando um usuário edita uma configuração de conector existente. Você pode usar essa URL para tornar mais fácil o código manipular o caso de edição.

Normalmente, essa chamada é feita como parte do seu manipulador de eventos Save. Depois, quando o `contentUrl` acima for carregado, seu código deverá chamar `getSettings()` para pré-popular todas as configurações ou formulários na sua interface do usuário de configuração.

#### <a name="handling-removals"></a>Como lidar com remoções

Opcionalmente, você pode executar um manipulador de eventos quando o usuário remove uma configuração de conector existente. Você registra esse manipulador chamando `microsoftTeams.settings.registerOnRemoveHandler()` . Esse manipulador pode ser usado para realizar operações de limpeza, como a remoção de entradas de um banco de dados.

### <a name="including-the-connector-in-your-manifest"></a>Incluindo o conector em seu manifesto

Você pode baixar o manifesto do aplicativo Teams gerado automaticamente no Portal. Para que você possa usá-lo para testar ou publicar seu aplicativo, no entanto, você deve fazer o seguinte:

- Inclua dois ícones, seguindo as instruções nos [ícones](~/concepts/build-and-test/apps-package.md#icons).
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

Agora você pode iniciar a experiência de configuração. Lembre-se de que esse fluxo ocorre completamente no Microsoft Teams como uma experiência hospedada.

Para verificar se uma `HttpPOST` ação está funcionando corretamente, [envie mensagens para o seu conector](~/webhooks-and-connectors/how-to/connectors-using.md).

## <a name="publish-connectors-for-your-organization"></a>Conectores de publicação para sua organização

Às vezes, talvez você não queira publicar seu aplicativo do conector no AppSource/loja público, mas gostaria que ele esteja disponível somente para os usuários em sua organização. Nesses casos, você pode carregar seu aplicativo de conector personalizado no [Catálogo de aplicativos da sua organização](~/concepts/deploy-and-publish/apps-publish.md). Dessa forma, o aplicativo do conector estará disponível somente para essa organização, e você não precisará publicar seu conector no armazenamento público.

Depois de carregar seu pacote de aplicativos, para configurar e usar o conector em uma equipe, ele poderá ser instalado no catálogo de aplicativos da organização seguindo estas etapas:

1. Selecione o ícone aplicativos na barra de navegação vertical da extrema esquerda.
1. Na janela **aplicativos** , selecione **conectores**.
1. Selecione o conector que você deseja adicionar e será exibida uma janela de caixa de diálogo pop-up.
1. Selecione a barra **Adicionar a uma equipe** .
1. Na próxima janela de diálogo, digite um nome de equipe ou de canal.
1. Selecione **Configurar uma** barra de conector no canto inferior direito da janela da caixa de diálogo.
1. O conector estará disponível na seção &#9679;&#9679;&#9679; => *mais opções*  =>  *conectores*  =>  *todos os*  =>  *conectores da sua equipe* para essa equipe. Você pode navegar rolando até esta seção ou pesquisar o aplicativo do conector.
1. Para configurar ou modificar o conector, selecione a barra **Configurar** .
