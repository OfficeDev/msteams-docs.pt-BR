---
title: Estender uma extensão Teams mensagem em Microsoft 365
description: Veja como atualizar sua extensão de mensagem de Teams baseada em pesquisa para ser executada em Outlook
ms.date: 02/11/2022
ms.topic: tutorial
ms.custom: m365apps
ms.openlocfilehash: 3bab70d85d071763ffbbae7cb1dae11534d0e812
ms.sourcegitcommit: 0117c4e750a388a37cc189bba8fc0deafc3fd230
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65104536"
---
# <a name="extend-a-teams-message-extension-across-microsoft-365"></a>Estender uma extensão Teams mensagem em Microsoft 365

> [!NOTE]
> *Estender uma extensão Teams de mensagem* em Microsoft 365 está disponível atualmente apenas na versão prévia [do desenvolvedor público](../resources/dev-preview/developer-preview-intro.md). Os recursos incluídos na pré-visualização podem não estar completos e podem sofrer alterações antes de se tornarem disponíveis no lançamento público. Eles são fornecidos apenas para fins de teste e exploração. Eles não devem ser usados em aplicativos de produção.

As extensões de [mensagem baseadas](/microsoftteams/platform/messaging-extensions/what-are-messaging-extensions) em pesquisa permitem que os usuários pesquisem um sistema externo e compartilhem resultados por meio da área de mensagem de composição do Microsoft Teams cliente. Estendendo seus aplicativos Teams em Microsoft 365 (versão prévia[)](overview.md), agora você pode trazer suas extensões de mensagem do Teams baseadas em pesquisa para Outlook para experiências da área de trabalho e da Web do Windows.

O processo para atualizar sua extensão de mensagem Teams de pesquisa para executar Outlook envolve estas etapas:

> [!div class="checklist"]
>
> * Atualizar o manifesto do aplicativo
> * Adicionar um Outlook para o bot
> * Realizar sideload do aplicativo atualizado no Teams

O restante deste guia explicará essas etapas e mostrará como visualizar sua extensão de mensagem em ambos os Outlook para Windows desktop e Web.

## <a name="prerequisites"></a>Pré-requisitos

Para concluir este tutorial, você precisará de:

* Um locatário Microsoft 365 área restrita do Programa para Desenvolvedores
* Seu locatário de área restrita registrado *em Office 365 Versões Direcionadas*
* Um ambiente de teste com Office aplicativos instalados do Microsoft 365 Apps *beta*
* Microsoft Visual Studio código com a extensão Teams Toolkit (versão prévia) (opcional)

> [!div class="nextstepaction"]
> [Instalar pré-requisitos](prerequisites.md)

## <a name="prepare-your-message-extension-for-the-upgrade"></a>Preparar sua extensão de mensagem para a atualização

Se você tiver uma extensão de mensagem existente, faça uma cópia ou uma ramificação do projeto de produção para testar e atualizar a ID do aplicativo no manifesto do aplicativo para usar um novo identificador (diferente da ID do aplicativo de produção).

Se você quiser usar o código de exemplo para concluir este tutorial, siga as etapas de instalação no [](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/javascript_nodejs/50.teams-messaging-extensions-search) exemplo de pesquisa de extensão de mensagem Teams para criar rapidamente uma extensão de mensagem baseada em Microsoft Teams pesquisa. Ou você pode começar com o mesmo exemplo de Pesquisa de Extensões de Mensagem do Teams atualizado para o [SDK do TeamsJS v2 Preview](https://github.com/OfficeDev/TeamsFx-Samples/tree/v2/NPM-search-connector-M365) e prosseguir para Visualizar sua extensão de mensagem [Outlook](#preview-your-message-extension-in-outlook). O exemplo atualizado também está disponível na extensão Teams Toolkit: *DevelopmentView* >  *samplesNPM* >  **Search Connector**.

:::image type="content" source="images/toolkit-search-sample.png" alt-text="Exemplo do Conector de Pesquisa do NPM Teams Toolkit":::

## <a name="update-the-app-manifest"></a>Atualizar o manifesto do aplicativo

Você precisará usar o esquema de manifesto Teams versão prévia do desenvolvedor e [a](/microsoftteams/platform/resources/schema/manifest-schema-dev-preview) `m365DevPreview` versão do manifesto para habilitar sua extensão de mensagem Teams ser executada Outlook.

Você tem duas opções para atualizar o manifesto do aplicativo:

# <a name="teams-toolkit"></a>[Kit de ferramentas do Teams](#tab/manifest-teams-toolkit)

1. Abra a *paleta de comandos*: `Ctrl+Shift+P`
1. Execute o comando `Teams: Upgrade Teams manifest to support Outlook and Office apps` e selecione o arquivo de manifesto do aplicativo. As alterações serão feitas no local.

# <a name="manual-steps"></a>[Etapas manuais](#tab/manifest-manual)

Abra o Teams manifesto do aplicativo e atualize o `$schema` e `manifestVersion` com os seguintes valores:

```json
{
    "$schema" : "https://raw.githubusercontent.com/OfficeDev/microsoft-teams-app-schema/preview/DevPreview/MicrosoftTeams.schema.json",
    "manifestVersion" : "m365DevPreview"
}
```

---

Se você usou Teams Toolkit para criar seu aplicativo de extensão de mensagem, poderá usá-lo para validar as alterações no arquivo de manifesto e identificar erros. `Ctrl+Shift+P` Abra a paleta de comandos e localize **Teams:** Valide o arquivo de manifesto ou selecione a opção no menu Implantação do Teams Toolkit (procure o ícone Teams no lado esquerdo do Visual Studio Code).

:::image type="content" source="images/toolkit-validate-manifest-file.png" alt-text="Teams Toolkit opção 'Validar arquivo de manifesto' no menu 'Implantação'":::

## <a name="add-an-outlook-channel-for-your-bot"></a>Adicionar um Outlook para o bot

No Microsoft Teams, uma extensão de mensagem consiste em um serviço Web que você hospeda e um manifesto do aplicativo, que define onde seu serviço Web está hospedado. O serviço Web aproveita o esquema de mensagens do [SDK do Bot Framework](/azure/bot-service/bot-service-overview) e o protocolo de comunicação segura por meio de um canal Teams registrado para o bot.

Para que os usuários interajam com sua extensão de Outlook, você precisará adicionar um canal Outlook ao bot:

1. No [Microsoft Azure portal](https://portal.azure.com) (ou [portal do Bot Framework](https://dev.botframework.com), se você registrou anteriormente), navegue até o recurso de bot.

1. No *Configurações*, selecione **Canais**.

1. Clique em **Outlook**, selecione a **guia Extensões de mensagem** e clique em **Salvar**.

    :::image type="content" source="images/azure-bot-channel-message-extensions.png" alt-text="Adicionar um Outlook &quot;Extensões de Mensagem&quot; para seu bot no painel Canais de Bot do Azure":::

1. Confirme se o Outlook está listado junto com Microsoft Teams no **painel Canais do** bot:

    :::image type="content" source="images/azure-bot-channels.png" alt-text="Painel Canais de Bot do Azure listando Microsoft Teams e Outlook canais":::

## <a name="update-microsoft-azure-active-directory-azure-ad-app-registration-for-sso"></a>Atualizar Microsoft Azure Active Directory do aplicativo (Azure AD) para SSO

> [!NOTE]
> Você pode ignorar [a](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/javascript_nodejs/50.teams-messaging-extensions-search) etapa se estiver usando um exemplo de pesquisa de extensão de Teams mensagem, pois o cenário não envolve Azure Active Directory (AAD) autenticação de Sign-On única.

Azure Active Directory o SSO (logon único) para extensões de mensagem funciona da mesma maneira no Outlook como no [Teams](/microsoftteams/platform/bots/how-to/authentication/auth-aad-sso-bots), no entanto, você precisa adicionar vários identificadores de aplicativo cliente ao registro de aplicativo do Azure AD do bot no portal do Registros de aplicativo *do* locatário.

1. Entre no portal do Azure com [sua](https://portal.azure.com) conta de locatário da área restrita.
1. Abra **Registros de aplicativo**.
1. Selecione o nome do aplicativo para abrir o registro do aplicativo.
1. Selecione  **Expor uma API** (em *Gerenciar*).

Na seção **Aplicativos cliente autorizados** , verifique se todos os seguintes `Client Id` valores estão listados:

|Microsoft 365 aplicativo cliente | ID do cliente |
|--|--|
|Teams desktop e móvel |1fec8e78-bce4-4aaf-ab1b-5451cc387264 |
|Web do Teams |5e3ce6c0-2b1f-4285-8d4b-75ee78787346 |
|Outlook para área de trabalho | d3590ed6-52b3-4102-aeff-aad2292ab01c |
|Outlook Web Access | 00000002-0000-0ff1-ce00-000000000000 |
|Outlook Web Access | bc59ab01-8403-45c6-8796-ac3ef710b3e3 |

## <a name="sideload-your-updated-message-extension-in-teams"></a>Realizar sideload da extensão de mensagem atualizada Teams

A etapa final é fazer sideload da extensão de mensagem atualizada (pacote [de](/microsoftteams/platform/concepts/build-and-test/apps-package) aplicativos) Microsoft Teams. Depois de concluída, a extensão de mensagem aparecerá nos Aplicativos *instalados* da área de composição da mensagem.

1. Empacote seu Teams aplicativo ([ícones de manifesto e aplicativo](/microsoftteams/platform/resources/schema/manifest-schema#icons)) em um arquivo zip. Se você usou Teams Toolkit para criar seu aplicativo, poderá fazer isso facilmente usando a opção de pacote de metadados do **Zip Teams** *no menu* Implantação do Teams Toolkit:

    :::image type="content" source="images/toolkit-zip-teams-metadata-package.png" alt-text="Opção 'Compactar Teams pacote de metadados' Teams Toolkit extensão para Visual Studio Code":::

1. Faça logon no Teams com sua conta de locatário de área restrita e verifique se você está  na Visualização Pública do Desenvolvedor clicando no menu de reticências (**...**) pelo seu perfil de usuário  e abrindo Sobre para verificar  se a opção De visualização do Desenvolvedor está ativada.

    :::image type="content" source="images/teams-dev-preview.png" alt-text="No Teams de reticências, abra &quot;Sobre&quot; e verifique se a opção 'Visualização do Desenvolvedor' está marcada":::

1. Abra o *painel Aplicativos* e clique **Upload um** aplicativo personalizado e, em seguida **, Upload para mim ou minhas equipes**.

    :::image type="content" source="images/teams-upload-custom-app.png" alt-text="Botão 'Upload um aplicativo personalizado' no painel Teams 'Aplicativos'":::

1. Selecione o pacote do aplicativo e clique em *Abrir*.

Depois de realizar o sideload Teams, a extensão de mensagem estará disponível Outlook na Web.

## <a name="preview-your-message-extension-in-outlook"></a>Visualizar sua extensão de mensagem Outlook

Agora você está pronto para testar sua extensão de mensagem em execução Outlook na Windows desktop e na Web. Embora sua extensão de mensagem atualizada continue a ser executada no Teams com suporte completo a recursos para extensões de [mensagem, há](/microsoftteams/platform/messaging-extensions/what-are-messaging-extensions) limitações nesta versão prévia antecipada da experiência habilitada para Outlook estar ciente de:

* As extensões de mensagem Outlook são limitadas ao contexto de [*composição de* email](/microsoftteams/platform/resources/schema/manifest-schema#composeextensions). Mesmo que sua Teams de `commandBox` mensagem inclua como um contexto em seu manifesto *, a versão* prévia atual será limitada à opção de composição de email (`compose`). Não há suporte para a invocação de uma extensão de mensagem da caixa Outlook *pesquisa* global.
* [Não há suporte para comandos de](/microsoftteams/platform/messaging-extensions/how-to/action-commands/define-action-command?tabs=AS) extensão de mensagem baseados em ação Outlook. Se o aplicativo tiver comandos baseados em pesquisa e ação, ele será exibido no Outlook mas o menu de ação não estará disponível.
* Não há suporte para a [inserção de mais de cinco Cartões](/microsoftteams/platform/task-modules-and-cards/cards/design-effective-cards?tabs=design) Adaptáveis em um email; Não há suporte para Cartões Adaptáveis v1.4 e posteriores.
* [Ações de](/microsoftteams/platform/task-modules-and-cards/cards/cards-actions?tabs=json) cartão do `messageBack`tipo , `imBack`e `invoke`não `signin` têm suporte para cartões inseridos. O suporte é limitado a `openURL`: ao clicar, o usuário será redirecionado para a URL especificada em uma nova guia.

Ao testar sua extensão de mensagem, você pode identificar a origem (originada de Teams versus Outlook) de solicitações de bot pela [channelId](https://github.com/Microsoft/botframework-sdk/blob/main/specs/botframework-activity/botframework-activity.md#channel-id) do objeto [Activity](https://github.com/Microsoft/botframework-sdk/blob/main/specs/botframework-activity/botframework-activity.md). Quando um usuário executa uma consulta, seu serviço recebe um objeto padrão do Bot Framework `Activity` . Uma das propriedades no objeto Activity é `channelId`, que terá o valor de `msteams` ou `outlook`, dependendo de onde a solicitação de bot se origina. Para obter mais informações, consulte  [o SDK de extensões de mensagem baseadas em pesquisa](/microsoftteams/platform/resources/messaging-extension-v3/search-extensions).

### <a name="outlook-on-the-web"></a>Outlook na Web

Para visualizar seu aplicativo em execução Outlook na Web:

1. Faça logon no [outlook.com](https://www.outlook.com) usando credenciais para seu locatário de teste.
1. Selecione **Nova mensagem**.
1. Abra **o menu de** submenu Mais aplicativos na parte inferior da janela de composição.

:::image type="content" source="images/outlook-web-compose-more-apps.png" alt-text="Clique no menu 'Mais aplicativos' na parte inferior da janela de composição de email para usar a extensão de mensagem":::

Sua extensão de mensagem será listada. Você pode invocá-lo a partir daí e usá-lo da mesma forma que faria ao redigir uma mensagem Teams.

### <a name="outlook"></a>Outlook

> [!IMPORTANT]
> Consulte as atualizações mais recentes no [Microsoft Teams – Blog](https://devblogs.microsoft.com/microsoft365dev/) do Desenvolvedor do Microsoft 365 para verificar se o Outlook na área de trabalho do Windows para aplicativos pessoais do Teams está disponível para seu locatário de teste.

Para visualizar seu aplicativo em execução Outlook na Windows desktop:

1. Inicie Outlook conectado com credenciais para seu locatário de teste. 1. Clique em **Novo Email**.
1. Abra o menu **de submenu** Mais aplicativos na faixa de opções superior.

Sua extensão de mensagem será listada. Você pode invocá-lo a partir daí e usá-lo da mesma forma que faria ao redigir uma mensagem Teams.

## <a name="next-steps"></a>Próximas etapas

Outlook extensões de Teams de mensagem estão em versão prévia e não têm suporte para uso em produção. Veja como distribuir sua extensão de mensagem Outlook habilitada para visualização de audiências para fins de teste.

### <a name="single-tenant-distribution"></a>Distribuição de locatário único

Outlook e Office guias pessoais habilitadas para Office podem ser distribuídas para um público-alvo de versão prévia em um locatário de teste (ou produção) de uma das três maneiras:

#### <a name="teams-client"></a>Cliente do Teams

No menu *Aplicativos*, selecione *Gerenciar seus* aplicativosEnviar  > **um aplicativo para sua organização**. Isso requer aprovação do administrador de TI.

#### <a name="microsoft-teams-admin-center"></a>Microsoft Teams Admin Center

Como administrador Teams, você pode carregar e pré-instalar o pacote do aplicativo para o locatário da sua organização Teams [administrador](https://admin.teams.microsoft.com/). Consulte [Upload seus aplicativos personalizados no centro Microsoft Teams de administração para](/MicrosoftTeams/upload-custom-apps) obter detalhes.

#### <a name="microsoft-admin-center"></a>Centro de Administração da Microsoft

Como administrador global, você pode carregar e pré-instalar o pacote do aplicativo do [administrador da Microsoft](https://admin.microsoft.com/). Consulte [Testar e implantar Microsoft 365 Apps por parceiros no portal de aplicativos integrados](/microsoft-365/admin/manage/test-and-deploy-microsoft-365-apps) para obter detalhes.

### <a name="multitenant-distribution"></a>Distribuição multilocatário

A distribuição para o Microsoft AppSource ainda não tem suporte durante essa versão prévia inicial do desenvolvedor Outlook extensões de mensagem Teams habilitadas.
