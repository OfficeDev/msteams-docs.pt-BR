---
title: Estender uma extensão de mensagem do Teams Microsoft 365
description: Saiba como atualizar sua extensão de mensagem baseada em pesquisa para ser executada no Outlook, além do Microsoft Teams.
ms.date: 10/10/2022
ms.topic: tutorial
ms.custom: m365apps
ms.localizationpriority: high
ms.openlocfilehash: 9b153eaaaa4cf3eb59d1a7b34122b569ae0d0d1a
ms.sourcegitcommit: 10debe0f01574a21aab54bfac692a4c8373263a8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2022
ms.locfileid: "68789931"
---
# <a name="extend-a-teams-message-extension-across-microsoft-365"></a>Estender uma extensão de mensagem do Teams Microsoft 365

As [extensões de mensagem](/microsoftteams/platform/messaging-extensions/what-are-messaging-extensions) baseadas em pesquisa permitem que os usuários pesquisem um sistema externo e compartilhem resultados por meio da área de redação de mensagem do cliente Microsoft Teams. Agora você pode trazer extensões de mensagens do Teams baseadas em pesquisa de produção para visualizar audiências no Outlook para área de trabalho do Windows e outlook.com [estendendo seus aplicativos do Teams pelo Microsoft 365](overview.md).

O processo para atualizar sua extensão de mensagem do Teams baseada em pesquisa envolve as seguintes etapas:

> [!div class="checklist"]
>
> * Atualize seu manifesto do aplicativo.
> * Adicione um canal do Outlook para seu bot.
> * Realize sideload do aplicativo atualizado no Teams.

O restante deste guia orienta você nestas etapas e mostra como visualizar sua extensão de mensagem no Outlook para a área de trabalho do Windows e na Web.

## <a name="prerequisites"></a>Pré-requisitos

Para concluir este tutorial, você precisa:

* Um locatário de área restrita do Programa para Desenvolvedores do Microsoft 365.
* Registro em *versões direcionadas do Office 365* para seu locatário de área restrita.
* Um ambiente de teste com aplicativos Office instalados do *Canal beta* dos Aplicativos do Microsoft 365.
* (Opcional) Código do Microsoft Visual Studio com a extensão Kit de Ferramentas do Teams.

> [!div class="nextstepaction"]
> [Instalar pré-requisitos](prerequisites.md)

## <a name="link-unfurling"></a>Desenrolamento de link

Se a extensão de mensagem baseada em pesquisa for compatível com [a desenrolação de link](../messaging-extensions/how-to/link-unfurling.md) no Teams, concluir as etapas deste tutorial também permitirá a desenrolação de link em ambientes de área de trabalho do Outlook na Web e do Windows. A seção [Exemplos de código](#code-sample) abaixo fornece um aplicativo de desenrolamento de link simples para teste.

## <a name="prepare-your-message-extension-for-the-upgrade"></a>Preparar sua extensão de mensagem para a atualização

Se você tiver uma extensão de mensagem existente e produção, faça uma cópia ou uma ramificação do projeto para testar e atualizar sua ID do aplicativo no manifesto do aplicativo para usar um novo identificador (diferente da ID do aplicativo de produção).

Se você quiser usar o código de exemplo para concluir o tutorial completo sobre como atualizar um aplicativo existente do Teams, siga as etapas de configuração [no exemplo de pesquisa de extensão de mensagem do Teams](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/javascript_nodejs/50.teams-messaging-extensions-search) para criar rapidamente uma extensão de mensagem baseada em pesquisa do Microsoft Teams.

Como alternativa, você pode usar o aplicativo habilitado para Outlook pronto na seção a seguir e ignorar a parte [*Atualizar o manifesto do aplicativo*](#update-the-app-manifest) deste tutorial.

### <a name="quickstart"></a>Início rápido

Para começar com uma [extensão de mensagem de exemplo](https://github.com/OfficeDev/TeamsFx-Samples/tree/ga/NPM-search-connector-M365) que já está habilitada para execução no Outlook, use a extensão kit de ferramentas do Teams para Visual Studio Code.

1. No Visual Studio Code, abra a paleta de comandos (`Ctrl+Shift+P`), digite `Teams: Create a new Teams app`.
1. Selecione a opção **Criar um novo aplicativo do Teams**.
1. Selecione **Extensão de mensagem baseada em Pesquisa** para baixar o código de exemplo para uma extensão de mensagem do Teams usando o manifesto mais recente do aplicativo Teams (versão `1.13`).

    :::image type="content" source="images/toolkit-palatte-search-sample.png" alt-text="A captura de tela é um exemplo que mostra a paleta de comandos VS Code tipo 'Criar um novo aplicativo do Teams' para listar as opções de exemplo do Teams.":::

    O exemplo também está disponível como *Conector de Pesquisa do NPM* na galeria de Exemplos do Kit de Ferramentas do Teams. No painel kit de ferramentas do Teams, selecione *Desenvolvimento* > *Exibir exemplos* > **Conector de pesquisa do NPM**.

    :::image type="content" source="images/toolkit-search-sample.png" alt-text="A captura de tela é um exemplo que mostra o exemplo do Conector de Pesquisa do NPM na galeria De exemplos do Teams Toolkit.":::

1. Selecione linguagem de programação preferencial.
1. Selecione um local no computador local para a pasta workspace e insira o nome do aplicativo.
1. Abra a paleta de comandos (`Ctrl+Shift+P`) e digite `Teams: Provision in the cloud` para criar os recursos de aplicativo necessários (Serviço de Aplicativo do Azure, plano do Serviço de Aplicativo, Bot do Azure e Identidade Gerenciada) em sua conta do Azure.
1. Selecione uma assinatura e um grupo de recursos.
1. Selecione **Provisionar**.
1. Abra a paleta de comandos (`Ctrl+Shift+P`) e digite `Teams: Deploy to the cloud` para implantar o código de exemplo nos recursos provisionados no Azure e iniciar o aplicativo.
1. Selecione **Implantar**.

A partir daqui, você pode pular para [Adicionar um canal do Outlook para seu bot](#add-an-outlook-channel-for-your-bot) para concluir a etapa final de habilitar a extensão de mensagem do Teams para funcionar no Outlook. (O manifesto do aplicativo já está fazendo referência à versão correta, portanto, nenhuma atualização é necessária).

## <a name="update-the-app-manifest"></a>Atualizar o manifesto do aplicativo

Você precisa usar a versão `1.13` do esquema de [manifesto do desenvolvedor do Teams](../resources/schema/manifest-schema.md) para habilitar sua extensão de mensagem do Teams a ser executada no Outlook.

Você tem duas opções para atualizar o manifesto do aplicativo:

# <a name="teams-toolkit"></a>[Kit de ferramentas do Teams](#tab/manifest-teams-toolkit)

1. Abra a paleta de comandos: `Ctrl+Shift+P`. 
1. Execute o `Teams: Upgrade Teams manifest` e selecione o arquivo de manifesto do aplicativo. As alterações serão feitas em vigor.

# <a name="manual-steps"></a>[Etapas manuais](#tab/manifest-manual)

Abra o manifesto do aplicativo Teams e atualize o `$schema` e `manifestVersion` com os seguintes valores:

```json
{
    "$schema" : "https://developer.microsoft.com/json-schemas/teams/v1.13/MicrosoftTeams.schema.json",
    "manifestVersion" : "1.13"
}
```

---

Se você usou o Kit de Ferramentas do Teams para criar seu aplicativo de extensão de mensagem, poderá usá-lo para validar as alterações no arquivo de manifesto e identificar erros. Abra a paleta de comandos (`Ctrl+Shift+P`) e localize **o Teams: validar o arquivo de manifesto**.

## <a name="add-an-outlook-channel-for-your-bot"></a>Adicionar um canal do Outlook para seu bot

No Microsoft Teams, uma extensão de mensagem consiste em um serviço Web que você hospeda e um manifesto do aplicativo, que define onde seu serviço Web está hospedado. O serviço Web aproveita o esquema de mensagens do [SDK do Bot Framework](/azure/bot-service/bot-service-overview) e o protocolo de comunicação segura por meio de um canal do Teams registrado para seu bot.

Para que os usuários interajam com sua extensão de mensagem do Outlook, você precisa adicionar um canal do Outlook ao bot:

1. No [Microsoft portal do Azure](https://portal.azure.com) (ou [portal do Bot Framework](https://dev.botframework.com), se você registrou anteriormente lá), acesse o recurso do bot.

1. De *Configurações*, selecione **Canais**.

1. Em *Canais disponíveis*, selecione **Outlook**. Selecione a guia **Extensões de mensagem** e, em seguida, **Aplicar**.

    :::image type="content" source="images/azure-bot-channel-message-extensions.png" alt-text="A captura de tela é um exemplo que mostra o canal 'Extensões de Mensagem' do Outlook para o bot no painel Canais de Bot do Azure.":::

1. Confirme se seu canal do Outlook está listado junto com o Teams no painel **Canais** do seu bot.

    :::image type="content" source="images/azure-bot-channels.png" alt-text="A captura de tela é um exemplo que mostra o painel Canais de Bot do Azure listando os canais do Teams e do Outlook.":::

## <a name="update-microsoft-azure-active-directory-azure-ad-app-registration-for-sso"></a>Atualizar Microsoft Azure Active Directory aplicativo do Azure AD (Azure AD) para SSO

> [!NOTE]
> Você pode ignorar essa etapa se estiver usando o aplicativo de [exemplo](#quickstart) fornecido neste tutorial, pois o cenário não envolve a autenticação Sign-On única do Azure Active Directory (AAD).

O SSO (logon único) do Azure Active Directory (AD) para extensões de mensagem funciona da mesma maneira no Outlook [que no Teams](/microsoftteams/platform/bots/how-to/authentication/auth-aad-sso-bots). No entanto, você precisa adicionar vários identificadores de aplicativo cliente ao registro do aplicativo Azure AD do bot no portal *Registros de aplicativo* do locatário.

1. Entre no [portal do Azure](https://portal.azure.com) com sua conta de locatário da área restrita.
1. Abra **Registros de aplicativo**.
1. Selecione o nome do aplicativo para abrir o registro do aplicativo.
1. Selecionar **Expor uma API** (em *Gerenciar*).
1. Na seção **Aplicativos do cliente autorizados**, certifique-se de que todos os valores `Client Id` a seguir estejam listados:

   |Microsoft 365 aplicativo cliente | ID do cliente |
   |--|--|
   |Área de trabalho e dispositivos móveis do Teams |1fec8e78-bce4-4aaf-ab1b-5451cc387264 |
   |Web do Teams |5e3ce6c0-2b1f-4285-8d4b-75ee78787346 |
   |Outlook para área de trabalho | d3590ed6-52b3-4102-aeff-aad2292ab01c |
   |Outlook Web Access | 00000002-0000-0ff1-ce00-000000000000 |
   |Outlook Web Access | bc59ab01-8403-45c6-8796-ac3ef710b3e3 |

## <a name="sideload-your-updated-message-extension-in-teams"></a>Realizar sideload da extensão de mensagem atualizada no Teams

A etapa final é carregar de lado sua extensão de mensagem atualizada ([pacote de aplicativo](/microsoftteams/platform/concepts/build-and-test/apps-package)) no Teams. Depois de concluir, a extensão de mensagem será exibida em seus *Aplicativos* instalados da área de mensagem de composição.

1. Empacote seu aplicativo do Teams ([ícones de manifesto e aplicativo](/microsoftteams/platform/resources/schema/manifest-schema#icons)) em um arquivo zip. Se você usou o Kit de Ferramentas do Teams para criar seu aplicativo, pode fazer isso facilmente usando a opção de pacote de metadados **Zip Teams** no menu *Implantação* do Kit de Ferramentas do Teams.

    :::image type="content" source="images/toolkit-zip-teams-metadata-package.png" alt-text="A captura de tela é um exemplo que mostra a opção &quot;Pacote de metadados do Zip Teams&quot; na extensão do Teams Toolkit para Visual Studio Code.":::

1. Entre no Teams com sua conta de locatário da área restrita e alterne para o modo de *Visualização do Desenvolvedor*. Selecione o menu de reticências (**...**) em seu perfil de usuário e selecione: **sobre** > **Visualização do desenvolvedor**.

    :::image type="content" source="images/teams-dev-preview.png" alt-text="A captura de tela é um exemplo que mostra a opção &quot;Visualização do Desenvolvedor&quot;.":::

1. Selecione **Aplicativos** para abrir o painel **Gerenciar seus aplicativos**. Em seguida, selecione **Carregar um aplicativo**.

    :::image type="content" source="../assets/images/teams-manage-your-apps.png" alt-text="A captura de tela é um exemplo que mostra a opção &quot;Carregar um aplicativo&quot;.":::

1. Escolha **Carregar uma opção de aplicativo personalizada** , selecione seu pacote de aplicativo e instale -o (*Adicionar*) ao cliente do Teams.

    :::image type="content" source="../assets/images/teams-upload-custom-app.png" alt-text="A captura de tela é um exemplo que mostra a opção &quot;Carregar um aplicativo personalizado&quot; no Teams.":::

Depois de ser sideload por meio do Teams, sua extensão de mensagem estará disponível no Outlook para área de trabalho e Web do Windows.

## <a name="preview-your-message-extension-in-outlook"></a>Visualizar sua extensão de mensagem no Outlook

Veja como testar sua extensão de mensagem em execução no Outlook na área de trabalho do Windows e na Web.

### <a name="outlook-on-the-web"></a>Outlook na Web

Para visualizar seu aplicativo em execução no Outlook na Web:

1. Entre em [outlook.com](https://www.outlook.com) usando suas credenciais de locatário de teste.
1. Selecione **Nova mensagem**.
1. Abra **Mais aplicativos** na parte inferior da janela de composição.

    :::image type="content" source="images/outlook-web-compose-more-apps.png" alt-text="A captura de tela é um exemplo que mostra o menu 'Mais aplicativos' na parte inferior da janela de composição de email para usar sua extensão de mensagem.":::

Your message extension is listed. You can invoke it from there and use it just as you would while composing a message in Teams.

### <a name="outlook"></a>Outlook

Para visualizar seu aplicativo em execução no Outlook na área de trabalho do Windows:

1. Inicie o Outlook e entre com suas credenciais de locatário de teste.
1. Selecione **Novo Email**.
1. Abra o menu **Mais aplicativos** na faixa de opções superior.

    :::image type="content" source="images/outlook-desktop-compose-more-apps.png" alt-text="A captura de tela é um exemplo que mostra o 'Mais Aplicativos' na faixa de opções da janela de composição para usar sua extensão de mensagem.":::

Sua extensão de mensagem está listada. Ela abre um painel adjacente para exibir os resultados da pesquisa.

## <a name="troubleshooting"></a>Solução de problemas

 Embora sua extensão de mensagem atualizada continue a ser executada no Teams com um [suporte de recurso para extensões de mensagem](/microsoftteams/platform/messaging-extensions/what-are-messaging-extensions), há limitações nesta visualização inicial da experiência habilitada para Outlook para estar ciente de:

* As extensões de mensagem no Outlook são limitadas ao contexto de [*composição* de email](/microsoftteams/platform/resources/schema/manifest-schema#composeextensions). Mesmo que sua extensão de mensagem do Teams inclua `commandBox` como um *contexto* em seu manifesto, a visualização atual é limitada à opção de composição de email (`compose`). Não há suporte para invocar uma extensão de mensagem da caixa global de *Pesquisa* do Outlook.
* Não há suporte para comandos [de extensão de mensagem baseados em ação](/microsoftteams/platform/messaging-extensions/how-to/action-commands/define-action-command?tabs=AS) no Outlook. Se o aplicativo tiver comandos baseados em pesquisa e ação, ele será exibido no Outlook, mas o menu de ação não estará disponível.
* Não há suporte para a inserção de mais de cinco [Cartões Adaptáveis](/microsoftteams/platform/task-modules-and-cards/cards/design-effective-cards?tabs=design) em um email; Cartões Adaptáveis v1.4 e posterior não têm suporte.
* [As ações de cartão](/microsoftteams/platform/task-modules-and-cards/cards/cards-actions?tabs=json) do tipo `messageBack`, `imBack`, `invoke` e `signin` não têm suporte para cartões inseridos. O suporte é limitado a `openURL`: quando selecionado, o usuário é redirecionado para a URL especificada em uma nova guia.

Use os canais da[Comunidade de desenvolvedores do Microsoft Teams](/microsoftteams/platform/feedback) para relatar problemas e fornecer comentários.

### <a name="debugging"></a>Depuração

Ao testar sua extensão de mensagem, você pode identificar a origem (originada do Teams versus Outlook) de solicitações de bot pelo [channelId](https://github.com/Microsoft/botframework-sdk/blob/main/specs/botframework-activity/botframework-activity.md#channel-id) do objeto [Atividade](https://github.com/Microsoft/botframework-sdk/blob/main/specs/botframework-activity/botframework-activity.md). Quando um usuário executa uma consulta, seu serviço recebe um objeto Bot Framework `Activity` padrão. Uma das propriedades no objeto Activity é `channelId`, que terá o valor de ou `outlook`, dependendo de `msteams` onde a solicitação do bot se origina. Para obter mais informações, consulte [SDK de extensões de mensagem baseadas em pesquisa](/microsoftteams/platform/resources/messaging-extension-v3/search-extensions).

## <a name="code-sample"></a>Exemplo de código

| **Nome de exemplo** | **Descrição** | **Node.js** |
|---------------|--------------|--------|
| Conector de Pesquisa do NPM | Use Teams Toolkit to build a message extension app. Works in Teams, Outlook. |  [Exibir](https://github.com/OfficeDev/TeamsFx-Samples/tree/ga/NPM-search-connector-M365) |
| Teams Link Unfurling | Aplicativo do Teams simples para demonstrar a desenrolação de link. Funciona no Teams, Outlook. | [Exibir](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/javascript_nodejs/55.teams-link-unfurling)

## <a name="next-step"></a>Próxima etapa

Publique seu aplicativo para ser detectável no Teams, no Outlook e no Office:

> [!div class="nextstepaction"]
> [Publicar aplicativos do Teams para Outlook e Office](publish.md)
