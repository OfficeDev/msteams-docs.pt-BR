---
title: Estender uma Teams de mensagens em Microsoft 365
description: Veja como atualizar sua extensão de mensagens baseada em pesquisa Teams ser executado em Outlook
ms.date: 11/15/2021
ms.topic: tutorial
ms.custom: m365apps
ms.openlocfilehash: 5c37eff384f3aa9d2d5f615272ec7a5518de4e8d
ms.sourcegitcommit: 6e33289c55a1a83adb9b7b38c42d781c699786f7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2022
ms.locfileid: "62345377"
---
# <a name="extend-a-teams-messaging-extension-across-microsoft-365"></a>Estender uma Teams de mensagens em Microsoft 365

> [!NOTE]
> *Estender uma extensão Teams de mensagens* em Microsoft 365 está disponível no momento apenas na [visualização do desenvolvedor público](../resources/dev-preview/developer-preview-intro.md). Os recursos incluídos na pré-visualização podem não estar completos e podem sofrer alterações antes de se tornarem disponíveis no lançamento público. Eles são fornecidos apenas para fins de teste e exploração. Eles não devem ser usados em aplicativos de produção.

Extensões de [mensagens baseadas](/microsoftteams/platform/messaging-extensions/what-are-messaging-extensions) em pesquisa permitem que os usuários pesquisem um sistema externo e compartilhem resultados por meio da área de mensagem de composição do cliente Microsoft Teams. Estendendo seus aplicativos Teams por meio de [Microsoft 365 (visualização)](overview.md), agora você pode trazer suas extensões de mensagens baseadas em pesquisa Teams para Outlook para Windows de área de trabalho e web.

O processo para atualizar sua extensão de mensagens baseada em pesquisa Teams para executar Outlook envolve estas etapas:

> [!div class="checklist"]
> * Atualizar o manifesto do aplicativo
> * Adicionar um Outlook para seu bot
> * Fazer sideload do aplicativo atualizado Teams

O restante deste guia guiará você por estas etapas e mostrará como visualizar sua extensão de mensagens em ambos os Outlook para Windows desktop e web.

## <a name="prerequisites"></a>Pré-requisitos

Para concluir este tutorial, você precisará:

 - Um locatário Microsoft 365 área de área de trabalho do Programa de Desenvolvedores
 - Seu locatário de área de Office 365 *Versões Direcionadas*
 - Um ambiente de teste com Office aplicativos instalados no canal Microsoft 365 Apps *beta*
 - Visual Studio Code com a extensão Teams Toolkit (Visualização) (Opcional)

> [!div class="nextstepaction"]
> [Instalar pré-requisitos](prerequisites.md)

## <a name="prepare-your-messaging-extension-for-the-upgrade"></a>Preparar sua extensão de mensagens para a atualização

Se você tiver uma extensão de mensagens existente, faça uma cópia ou uma ramificação do seu projeto de produção para testar e atualizar sua ID do aplicativo no manifesto do aplicativo para usar um novo identificador (distinto da ID do aplicativo de produção).

Se você quiser usar código de exemplo para concluir este tutorial, siga [as](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/javascript_nodejs/50.teams-messaging-extensions-search) etapas de configuração em um exemplo de pesquisa de extensão de mensagens Teams para criar rapidamente uma extensão de mensagens baseada em pesquisa Microsoft Teams pesquisa. Ou, você pode começar com o mesmo exemplo de Pesquisa de Extensões de Mensagens do Teams atualizado para o [TeamsJS SDK v2 Preview](https://github.com/OfficeDev/TeamsFx-Samples/tree/v2/NPM-search-connector-M365) e prosseguir para Visualizar sua extensão de mensagens [no](#preview-your-messaging-extension-in-outlook) Outlook. O exemplo atualizado também está disponível em uma extensão Teams Toolkit: *DevelopmentView* >  *samplesNPM* >  **Search Connector**.

:::image type="content" source="images/toolkit-search-sample.png" alt-text="Exemplo do NpM Search Connector no Teams Toolkit":::

## <a name="update-the-app-manifest"></a>Atualizar o manifesto do aplicativo

Você precisará usar o [](/microsoftteams/platform/resources/schema/manifest-schema-dev-preview) `m365DevPreview` esquema de manifesto Teams de visualização do desenvolvedor e a versão do manifesto para habilitar sua extensão de mensagens Teams para ser executado Outlook.

Você tem duas opções para atualizar o manifesto do aplicativo:

# <a name="teams-toolkit"></a>[Kit de ferramentas do Teams](#tab/manifest-teams-toolkit)

1. Abra a *paleta Comando*: `Ctrl+Shift+P`
1. Execute o `Teams: Upgrade Teams manifest to support Outlook and Office apps` comando e selecione o arquivo de manifesto do aplicativo. As alterações serão feitas no local.

# <a name="manual-steps"></a>[Etapas manuais](#tab/manifest-manual)

Abra seu Teams de aplicativo e atualize o `$schema` e `manifestVersion` com os seguintes valores:

```json
{
    "$schema" : "https://raw.githubusercontent.com/OfficeDev/microsoft-teams-app-schema/preview/DevPreview/MicrosoftTeams.schema.json",
    "manifestVersion" : "m365DevPreview"
}
```
---

Se você usou Teams Toolkit para criar seu aplicativo de extensão de mensagens, poderá usá-lo para validar as alterações no arquivo de manifesto e identificar quaisquer erros. Abra a paleta `Ctrl+Shift+P` de comandos e encontre **Teams:** Valide o arquivo de manifesto ou selecione a opção no menu Implantação do Teams Toolkit (procure o ícone Teams no lado esquerdo do Visual Studio Code).

:::image type="content" source="images/toolkit-validate-manifest-file.png" alt-text="Teams Toolkit opção &quot;Validar arquivo de manifesto&quot; no menu 'Implantação'":::

## <a name="add-an-outlook-channel-for-your-bot"></a>Adicionar um Outlook para seu bot

Em Microsoft Teams, uma extensão de mensagens consiste em um serviço Web que você hospeda e um manifesto de aplicativo, que define onde seu serviço Web está hospedado. O serviço Web aproveita o esquema de mensagens [do Bot Framework SDK](/azure/bot-service/bot-service-overview) e o protocolo de comunicação seguro por meio de um canal Teams registrado para o bot.

Para que os usuários interajam com sua extensão de mensagens Outlook, você precisará adicionar um canal Outlook ao bot:

1. No [portal do Azure](https://portal.azure.com) (ou [portal da Estrutura de Bots](https://dev.botframework.com) , se você registrou anteriormente), navegue até o recurso bot.

1. No *Configurações*, selecione **Canais**.

1. Clique em **Outlook**, selecione a guia **Extensões de mensagem** e clique em **Salvar**.

    :::image type="content" source="images/azure-bot-channel-message-extensions.png" alt-text="Adicionar um Outlook &quot;Extensões de Mensagem&quot; para seu bot no painel Canais de Bot do Azure":::

1. Confirme se seu Outlook está listado junto com Microsoft Teams no painel **Canais do** bot:

    :::image type="content" source="images/azure-bot-channels.png" alt-text="Painel canais bot do Azure listando canais de Microsoft Teams e Outlook":::

## <a name="update-azure-ad-app-registration-for-sso"></a>Atualizar o registro de aplicativo do Azure AD para SSO

> [!NOTE]
> Você pode ignorar a etapa se estiver usando Teams de pesquisa de extensão de [mensagens, pois](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/javascript_nodejs/50.teams-messaging-extensions-search) o cenário não envolve Azure Active Directory (AAD) autenticação de Sign-On única.

Azure Active Directory Logor único (SSO) para extensões de mensagens funciona da mesma maneira no Outlook como no [Teams](/microsoftteams/platform/bots/how-to/authentication/auth-aad-sso-bots), no entanto, você precisa adicionar vários identificadores de aplicativo cliente ao registro do aplicativo do Azure AD do bot no portal de registros de *aplicativos* do locatário.

1. Entre no [portal do Azure](https://portal.azure.com) com sua conta de locatário de área de reserva.
1. Abrir **registros de aplicativos**.
1. Selecione o nome do aplicativo para abrir o registro do aplicativo.
1. Selecione  **Expor uma API** (em *Gerenciar*).

Na seção **Aplicativos cliente autorizados** , verifique se todos os seguintes valores `Client Id` estão listados:

|Microsoft 365 cliente | ID do cliente |
|--|--|
|Teams desktop e mobile |1fec8e78-bce4-4aaf-ab1b-5451cc387264 |
|Teams Web |5e3ce6c0-2b1f-4285-8d4b-75ee78787346 |
|Outlook para área de trabalho | d3590ed6-52b3-4102-aeff-aad2292ab01c |
|Outlook Web Access | 00000002-0000-0ff1-ce00-0000000000000000 |
|Outlook Web Access | bc59ab01-8403-45c6-8796-ac3ef710b3e3 |

## <a name="sideload-your-updated-messaging-extension-in-teams"></a>Fazer sideload da extensão de mensagens atualizada no Teams

A etapa final é fazer sideload da extensão de mensagens atualizada ([pacote de](/microsoftteams/platform/concepts/build-and-test/apps-package) aplicativos) no Microsoft Teams. Depois de concluída, sua extensão de mensagens aparecerá em seus *Aplicativos* instalados da área de mensagem de redação.

1. Empacote seu Teams ([ícones](/microsoftteams/platform/resources/schema/manifest-schema#icons) de manifesto e aplicativo) em um arquivo zip. Se você usou Teams Toolkit para criar seu aplicativo, você pode facilmente fazer isso usando Teams opção de pacote de **metadados zip** *no menu* Implantação do Teams Toolkit:

    :::image type="content" source="images/toolkit-zip-teams-metadata-package.png" alt-text="Opção 'Pacote Teams de metadados zip' Teams Toolkit extensão para Visual Studio Code":::

1. Faça logon no Teams com sua conta de locatário de área de segurança e verifique se você está  na Visualização do Desenvolvedor Público clicando no menu reellipse (**...**) pelo perfil de usuário e abrindo **Sobre** para verificar se  a opção de visualização do Desenvolvedor está alternada.

    :::image type="content" source="images/teams-dev-preview.png" alt-text="No Teams menu de releições, abra a opção 'Sobre' e verifique se a opção 'Visualização do Desenvolvedor' está marcada":::

1. Abra o *painel Aplicativos* e clique **Upload um aplicativo** personalizado e, em seguida, **Upload para mim ou minhas equipes**.

    :::image type="content" source="images/teams-upload-custom-app.png" alt-text="Botão &quot;Upload um aplicativo personalizado&quot; no painel Teams &quot;Aplicativos&quot;":::

1. Selecione seu pacote de aplicativos e clique em *Abrir*.

Depois de ser carregado Teams, sua extensão de mensagens estará disponível Outlook na Web.

## <a name="preview-your-messaging-extension-in-outlook"></a>Visualizar sua extensão de mensagens no Outlook

Agora você está pronto para testar sua extensão de mensagens em execução Outlook na Windows desktop e na Web. Embora sua extensão de mensagens atualizada continue a ser executado em Teams com suporte completo a recursos para extensões de [mensagens, há](/microsoftteams/platform/messaging-extensions/what-are-messaging-extensions) limitações nesta visualização inicial da experiência habilitada para Outlook para estar ciente:

* As extensões de mensagens no Outlook estão limitadas ao contexto de [*composição de* email](/microsoftteams/platform/resources/schema/manifest-schema#composeextensions). Mesmo que sua Teams de `commandBox` mensagens inclua como um contexto em seu manifesto *, a* visualização atual é limitada à opção de composição de email (`compose`). Não há suporte para invocar uma extensão de mensagens da caixa de pesquisa *Outlook global.*
* [Comandos de extensão de mensagens baseados](/microsoftteams/platform/messaging-extensions/how-to/action-commands/define-action-command?tabs=AS) em ação não são suportados Outlook. Se o aplicativo tiver comandos baseados em pesquisa e ação, ele será Outlook, mas o menu de ação não estará disponível.
* Não há suporte para a inserção de mais de cinco [Cartões](/microsoftteams/platform/task-modules-and-cards/cards/design-effective-cards?tabs=design) Adaptáveis em um email; Cartões adaptáveis v1.4 e posteriores não são suportados.
* [Ações de](/microsoftteams/platform/task-modules-and-cards/cards/cards-actions?tabs=json) cartão do tipo `messageBack`, `imBack`, `invoke`e `signin` não são suportadas para cartões inseridos. O suporte é limitado a `openURL`: ao clicar, o usuário será redirecionado para a URL especificada em uma nova guia.

Ao testar sua extensão de mensagens, você pode identificar a origem (proveniente de Teams versus Outlook) de solicitações de bot pelo [channelId](https://github.com/Microsoft/botframework-sdk/blob/main/specs/botframework-activity/botframework-activity.md#channel-id) do [objeto Activity](https://github.com/Microsoft/botframework-sdk/blob/main/specs/botframework-activity/botframework-activity.md). Quando um usuário executa uma consulta, seu serviço recebe um objeto Da Estrutura de Bot `Activity` padrão. Uma das propriedades no objeto Activity `channelId`é , que terá o valor de `msteams` ou `outlook`, dependendo de onde a solicitação de bot se origina. Para obter mais, consulte  [Search based messaging extensions SDK](/microsoftteams/platform/resources/messaging-extension-v3/search-extensions).

### <a name="outlook"></a>Outlook

Para visualizar seu aplicativo em execução Outlook na área de trabalho Windows, abra Outlook conectado com credenciais para seu locatário de teste. Clique em **Novo Email**. Abra o menu **de sobrevoo** Mais aplicativos na faixa de opções superior. Sua extensão de mensagens será listada. Você pode invocá-lo a partir daí e usá-lo da mesma forma que faria ao compor uma mensagem no Teams.

### <a name="outlook-on-the-web"></a>Outlook na Web

Para visualizar seu aplicativo em execução Outlook na Web, faça logoff [outlook.com](https://www.outlook.com) usando credenciais para seu locatário de teste. Clique em **Nova mensagem**. Abra o menu **de** sobreposição Mais aplicativos na parte inferior da janela de composição. Sua extensão de mensagens será listada. Você pode invocá-lo a partir daí e usá-lo da mesma forma que faria ao compor uma mensagem no Teams.

## <a name="next-steps"></a>Próximas etapas

Outlook habilitadas Teams de mensagens estão em visualização e não têm suporte para uso de produção. Veja como distribuir sua extensão Outlook de mensagens habilitada para visualização de audiências para fins de teste.

### <a name="single-tenant-distribution"></a>Distribuição de locatário único

Outlook e Office pessoais habilitadas para Office podem ser distribuídas para um público-alvo de visualização em um locatário de teste (ou produção) de uma das três maneiras:

#### <a name="teams-client"></a>Teams cliente

No menu *Aplicativos*, selecione *Gerenciar seus* **aplicativosSubmitir um aplicativo para sua organização**. >  Isso requer aprovação do administrador de IT.

#### <a name="microsoft-teams-admin-center"></a>Microsoft Teams Admin Center

Como administrador Teams, você pode carregar e pré-instalar o pacote de aplicativos para o locatário da sua organização em https://admin.teams.microsoft.com/. Consulte [Upload seus aplicativos personalizados no centro de administração Microsoft Teams para](/MicrosoftTeams/upload-custom-apps) obter detalhes.

#### <a name="microsoft-admin-center"></a>Centro de Administração da Microsoft

Como administrador global, você pode carregar e pré-instalar o pacote de aplicativos de https://admin.microsoft.com/. Consulte [Test and deploy Microsoft 365 Apps by partners in the Integrated apps portal](/microsoft-365/admin/manage/test-and-deploy-microsoft-365-apps) for details.

### <a name="multi-tenant-distribution"></a>Distribuição de vários locatários

A distribuição para o Microsoft AppSource ainda não é suportada durante essa visualização inicial do desenvolvedor Outlook extensões Teams de mensagens.
