---
title: Estender uma extensão de mensagem do Teams Microsoft 365
description: Veja como atualizar a extensão de mensagem do Teams baseada em pesquisa para ser executada no Outlook
ms.date: 02/11/2022
ms.topic: tutorial
ms.custom: m365apps
ms.localizationpriority: high
ms.openlocfilehash: 7e3a0d772367952c1726648fce2f10e1d8b885b2
ms.sourcegitcommit: f15bd0e90eafb00e00cf11183b129038de8354af
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2022
ms.locfileid: "65111371"
---
# <a name="extend-a-teams-message-extension-across-microsoft-365"></a>Estender uma extensão de mensagem do Teams Microsoft 365

> [!NOTE]
> *Extendindo uma extensão de mensagem do Teams em Microsoft 365* está disponível atualmente apenas em [Visualização Pública do Desenvolvedor](../resources/dev-preview/developer-preview-intro.md). Os recursos incluídos na pré-visualização podem não estar completos e podem sofrer alterações antes de se tornarem disponíveis no lançamento público. Eles são fornecidos apenas para fins de teste e exploração. Eles não devem ser usados em aplicativos de produção.

As [extensões de mensagem](/microsoftteams/platform/messaging-extensions/what-are-messaging-extensions) baseadas em pesquisa permitem que os usuários pesquisem um sistema externo e compartilhem resultados por meio da área de redação de mensagem do cliente Microsoft Teams. Ao [estender seus aplicativos do Teams no Microsoft 365 (versão prévia)](overview.md), agora você pode trazer suas extensões de mensagem do Teams baseadas em pesquisa para o Outlook para Windows desktop e experiências na Web.

O processo para atualizar sua extensão de mensagem do Teams baseada em pesquisa para executar o Outlook envolve estas etapas:

> [!div class="checklist"]
>
> * Atualizar o manifesto do aplicativo
> * Adicionar um canal do Outlook para seu bot
> * Realizar sideload do aplicativo atualizado no Teams

O restante deste guia orientará você durante essas etapas e mostrará como visualizar sua extensão de mensagem no Outlook para Área de Trabalho do Windows e na Web.

## <a name="prerequisites"></a>Pré-requisitos

Para concluir este tutorial, você precisará de:

* Um locatário Microsoft 365 área restrita do Programa para Desenvolvedores
* Seu locatário de área restrita registrado em *Versões direcionadas do Office 365*
* Um ambiente de teste com aplicativos do Office instalados do *canal beta* do Microsoft 365 Apps
* Microsoft Visual Studio código com a extensão do Kit de Ferramentas do Teams (versão prévia) (opcional)

> [!div class="nextstepaction"]
> [Instalar pré-requisitos](prerequisites.md)

## <a name="prepare-your-message-extension-for-the-upgrade"></a>Preparar sua extensão de mensagem para a atualização

Se você tiver uma extensão de mensagem existente, faça uma cópia ou uma ramificação do projeto de produção para testar e atualizar sua ID do aplicativo no manifesto do aplicativo para usar um novo identificador (diferente da ID do aplicativo de produção).

Se você quiser usar o código de exemplo para concluir este tutorial, siga as etapas de configuração em [Exemplo de pesquisa de extensão de mensagem do Teams](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/javascript_nodejs/50.teams-messaging-extensions-search) para criar rapidamente uma extensão de mensagem baseada em pesquisa do Microsoft Teams. Ou você pode começar com o mesmo [exemplo de pesquisa de extensões de mensagem do Teams atualizado para a visualização do TeamsJS SDK v2](https://github.com/OfficeDev/TeamsFx-Samples/tree/v2/NPM-search-connector-M365) e prosseguir para [Visualizar sua extensão de mensagem no Outlook](#preview-your-message-extension-in-outlook). O exemplo atualizado também está disponível na extensão do Kit de Ferramentas do Teams: *Desenvolvimento* > *Ver amostras* > **Conector de pesquisa do NPM**.

:::image type="content" source="images/toolkit-search-sample.png" alt-text="Exemplo do Conector de Pesquisa NPM no Kit de Ferramentas do Teams":::

## <a name="update-the-app-manifest"></a>Atualizar o manifesto do aplicativo

Você precisará usar o esquema [Manifesto de visualização do desenvolvedor do Teams](/microsoftteams/platform/resources/schema/manifest-schema-dev-preview) e a versão do manifesto `m365DevPreview` para permitir que a extensão de mensagem do Teams seja executada no Outlook.

Você tem duas opções para atualizar o manifesto do aplicativo:

# <a name="teams-toolkit"></a>[Kit de ferramentas do Teams](#tab/manifest-teams-toolkit)

1. Abra a *paleta de Comando*: `Ctrl+Shift+P`
1. Execute o `Teams: Upgrade Teams manifest to support Outlook and Office apps` e selecione o arquivo de manifesto do aplicativo. As alterações serão feitas em vigor.

# <a name="manual-steps"></a>[Etapas manuais](#tab/manifest-manual)

Abra o manifesto do aplicativo Teams e atualize o `$schema` e `manifestVersion` com os seguintes valores:

```json
{
    "$schema" : "https://raw.githubusercontent.com/OfficeDev/microsoft-teams-app-schema/preview/DevPreview/MicrosoftTeams.schema.json",
    "manifestVersion" : "m365DevPreview"
}
```

---

Se você usou o Kit de Ferramentas do Teams para criar seu aplicativo de extensão de mensagem, poderá usá-lo para validar as alterações no arquivo de manifesto e identificar erros. Abra a paleta de comandos `Ctrl+Shift+P` e localize **Teams: Validar arquivo de manifesto** ou selecione a opção no menu Implantação do Kit de Ferramentas do Teams (procure o ícone do Teams no lado esquerdo do Visual Studio Code).

:::image type="content" source="images/toolkit-validate-manifest-file.png" alt-text="Kit de ferramentas do Teams 'Validar arquivo de manifesto' no menu 'Implantação'":::

## <a name="add-an-outlook-channel-for-your-bot"></a>Adicionar um canal do Outlook para seu bot

No Microsoft Teams, uma extensão de mensagem consiste em um serviço Web que você hospeda e um manifesto do aplicativo, que define onde seu serviço Web está hospedado. O serviço Web aproveita o esquema de mensagens do [SDK do Bot Framework](/azure/bot-service/bot-service-overview) e o protocolo de comunicação segura por meio de um canal do Teams registrado para seu bot.

Para que os usuários interajam com sua extensão de mensagem do Outlook, você precisará adicionar um canal do Outlook ao bot:

1. Desde o [portal do Microsoft Azure](https://portal.azure.com) (ou o [portal do Bot Framework](https://dev.botframework.com) se você registrou anteriormente lá), navegue até o recurso de bot.

1. De *Configurações*, selecione **Canais**.

1. Clique em **Outlook**, selecione a guia **Extensões de mensagem** e clique em **Salvar**.

    :::image type="content" source="images/azure-bot-channel-message-extensions.png" alt-text="Adicione um canal de 'Extensões de Mensagem' do Outlook para seu bot no painel Canais de Bot do Azure":::

1. Confirme se o canal do Outlook está listado junto com o Microsoft Teams no painel **Canais** do bot:

    :::image type="content" source="images/azure-bot-channels.png" alt-text="O painel Canais de Bot do Azure listando os canais do Microsoft Teams e do Outlook":::

## <a name="update-microsoft-azure-active-directory-azure-ad-app-registration-for-sso"></a>Atualizar Microsoft Azure Active Directory aplicativo do Azure AD (Azure AD) para SSO

> [!NOTE]
> Você pode pular a etapa se estiver usando o [exemplo de pesquisa de extensão de mensagem do Teams](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/javascript_nodejs/50.teams-messaging-extensions-search), pois o cenário não envolve a autenticação de logon único do Azure Active Directory (AAD).

O logon único (SSO) do Azure Active Directory para extensões de mensagem funciona no Outlook [da mesma maneira do que no Teams](/microsoftteams/platform/bots/how-to/authentication/auth-aad-sso-bots), no entanto, você precisa adicionar vários identificadores de aplicativo cliente ao registro do aplicativo Azure AD do seu bot no portal de *registros do aplicativo* do locatário.

1. Entre no [portal do Azure](https://portal.azure.com) com sua conta de locatário da área restrita.
1. Abra **Registros de aplicativo**.
1. Selecione o nome do aplicativo para abrir o registro do aplicativo.
1. Selecionar **Expor uma API** (em *Gerenciar*).

Na seção **Aplicativos do cliente autorizados**, certifique-se de que todos os valores `Client Id` a seguir estejam listados:

|Microsoft 365 aplicativo cliente | ID do cliente |
|--|--|
|Área de trabalho e dispositivos móveis do Teams |1fec8e78-bce4-4aaf-ab1b-5451cc387264 |
|Web do Teams |5e3ce6c0-2b1f-4285-8d4b-75ee78787346 |
|Outlook para área de trabalho | d3590ed6-52b3-4102-aeff-aad2292ab01c |
|Outlook Web Access | 00000002-0000-0ff1-ce00-000000000000 |
|Outlook Web Access | bc59ab01-8403-45c6-8796-ac3ef710b3e3 |

## <a name="sideload-your-updated-message-extension-in-teams"></a>Realizar sideload da extensão de mensagem atualizada no Teams

A etapa final é realizar o sideload da extensão de mensagem atualizada ([pacote de aplicativos](/microsoftteams/platform/concepts/build-and-test/apps-package)) no Microsoft Teams. Depois de concluído, sua extensão de mensagem aparecerá em seus *Aplicativos* instalados na área de composição de mensagem.

1. Empacote seu aplicativo do Teams ([ícones de manifesto e aplicativo](/microsoftteams/platform/resources/schema/manifest-schema#icons)) em um arquivo zip. Se você usou o Kit de Ferramentas do Teams para criar seu aplicativo, poderá fazer isso facilmente usando a opção **Compactar o pacote de metadados do Teams** no menu *Implantação* do Kit de Ferramentas do Teams:

    :::image type="content" source="images/toolkit-zip-teams-metadata-package.png" alt-text="'Pacote de metadados do Zip Teams' na extensão do Kit de Ferramentas do Teams para Visual Studio Code":::

1. Faça logon no Teams com sua conta de locatário de sandbox e verifique se você está na *Visualização Pública do Desenvolvedor* clicando no menu de reticências (**...**) do seu perfil de usuário e abrindo **Sobre** para verificar se a opção *Visualização do Desenvolvedor* está ativada.

    :::image type="content" source="images/teams-dev-preview.png" alt-text="Do menu de reticências do Teams, abra 'Sobre' e verifique se a opção 'Visualização do Desenvolvedor' está marcada":::

1. Abra o painel *Aplicativos*, e clique em **Carregue um aplicativo personalizado** e, em seguida, **Carregue para mim ou minhas equipes**.

    :::image type="content" source="images/teams-upload-custom-app.png" alt-text="'Carregar um aplicativo personalizado' no painel 'Aplicativos' do Teams":::

1. Selecione o pacote do aplicativo e clique em *Open*.

Após o sideload por meio do Teams, sua extensão de mensagem estará disponível no Outlook na Web.

## <a name="preview-your-message-extension-in-outlook"></a>Visualizar sua extensão de mensagem no Outlook

Agora você está pronto para testar sua extensão de mensagem em execução no Outlook na área de trabalho do Windows e na Web. Embora sua extensão de mensagem atualizada continue a ser executada no Teams com um [suporte de recurso para extensões de mensagem](/microsoftteams/platform/messaging-extensions/what-are-messaging-extensions), há limitações nesta visualização inicial da experiência habilitada para Outlook para estar ciente de:

* As extensões de mensagem no Outlook são limitadas ao contexto de [*composição* de email](/microsoftteams/platform/resources/schema/manifest-schema#composeextensions). Mesmo que sua extensão de mensagem do Teams inclua `commandBox` como um *contexto* em seu manifesto, a visualização atual é limitada à opção de composição de email (`compose`). Não há suporte para invocar uma extensão de mensagem da caixa global de *Pesquisa* do Outlook.
* [A extensão de mensagem baseada em ação](/microsoftteams/platform/messaging-extensions/how-to/action-commands/define-action-command?tabs=AS) comandos não têm suporte no Outlook. Se o aplicativo tiver comandos baseados em pesquisa e ação, ele será exibido no Outlook, mas o menu de ação não estará disponível.
* Não há suporte para a inserção de mais de cinco [Cartões Adaptáveis](/microsoftteams/platform/task-modules-and-cards/cards/design-effective-cards?tabs=design) em um email; Cartões Adaptáveis v1.4 e posterior não têm suporte.
* [As ações de cartão](/microsoftteams/platform/task-modules-and-cards/cards/cards-actions?tabs=json) do tipo `messageBack`, `imBack`, `invoke` e `signin` não têm suporte para cartões inseridos. O suporte é limitado a `openURL`: ao clicar, o usuário será redirecionado para a URL especificada em uma nova guia.

Ao testar sua extensão de mensagem, você pode identificar a origem (originada do Teams versus Outlook) de solicitações de bot pelo [channelId](https://github.com/Microsoft/botframework-sdk/blob/main/specs/botframework-activity/botframework-activity.md#channel-id) do objeto [Atividade](https://github.com/Microsoft/botframework-sdk/blob/main/specs/botframework-activity/botframework-activity.md). Quando um usuário executa uma consulta, seu serviço recebe um objeto Bot Framework `Activity` padrão. Uma das propriedades no objeto Activity é `channelId`, que terá o valor de `msteams` ou `outlook`, dependendo de onde a solicitação do bot se origina. Para obter mais informações, consulte [SDK de extensões de mensagem com base em pesquisa](/microsoftteams/platform/resources/messaging-extension-v3/search-extensions).

### <a name="outlook-on-the-web"></a>Outlook na Web

Para visualizar seu aplicativo em execução no Outlook na Web:

1. Faça logon em [outlook.com](https://www.outlook.com) usando credenciais para seu locatário de teste.
1. Selecione **Nova mensagem**.
1. Abra **Mais aplicativos** na parte inferior da janela de composição.

:::image type="content" source="images/outlook-web-compose-more-apps.png" alt-text="Clique no menu 'Mais aplicativos' na parte inferior da janela de composição de email para usar a extensão de mensagem":::

Sua extensão de mensagem será listada. Você pode invocá-lo de lá e usá-lo da mesma forma que faria ao redigir uma mensagem no Teams.

### <a name="outlook"></a>Outlook

> [!IMPORTANT]
> Consulte as atualizações mais recentes no [Microsoft Teams – Blog do desenvolvedor do Microsoft 365](https://devblogs.microsoft.com/microsoft365dev/) para verificar se o suporte do Outlook para área de trabalho do Windows para aplicativos pessoais do Teams está disponível para seu locatário de teste.

Para visualizar seu aplicativo em execução no Outlook na área de trabalho do Windows:

1. Inicie o Outlook conectado com credenciais para seu locatário de teste. 1. Clique em **Novo Email**.
1. Abra o menu **Mais aplicativos** na faixa de opções superior.

Sua extensão de mensagem será listada. Você pode invocá-lo de lá e usá-lo da mesma forma que faria ao redigir uma mensagem no Teams.

## <a name="next-steps"></a>Próximas etapas

As extensões de mensagem do Teams habilitadas para Outlook estão em versão prévia e não têm suporte para uso em produção. Veja como distribuir sua extensão de mensagem habilitada para Outlook para visualizar públicos-alvo para fins de teste.

### <a name="single-tenant-distribution"></a>Distribuição de locatário único

As guias pessoais habilitadas para Outlook e Office podem ser distribuídas para um público-alvo de visualização em um locatário de teste (ou produção) de uma das três maneiras:

#### <a name="teams-client"></a>Cliente do Teams

No menu *Aplicativos*, selecione *Gerenciar seus aplicativos* > **Enviar um aplicativo para sua organização**. Isso requer a aprovação do seu administrador de TI.

#### <a name="microsoft-teams-admin-center"></a>Centro de Administração do Microsoft Teams

Como administrador do Teams, você pode carregar e pré-instalar o pacote de aplicativos para o locatário da sua organização a partir de [administrador de Teams](https://admin.teams.microsoft.com/). Consulte [Carregue seus aplicativos personalizados no centro de administração do Microsoft Teams](/MicrosoftTeams/upload-custom-apps) para obter detalhes.

#### <a name="microsoft-admin-center"></a>Centro de Administração da Microsoft

Como administrador global, você pode carregar e pré-instalar o pacote do aplicativo do [administrador de Microsoft](https://admin.microsoft.com/). Consulte [Testar e implantar aplicativos do Microsoft 365 por parceiros no portal de aplicativos integrados](/microsoft-365/admin/manage/test-and-deploy-microsoft-365-apps) para obter detalhes.

### <a name="multitenant-distribution"></a>Distribuição multilocatário

A distribuição para Microsoft AppSource ainda não tem suporte durante essa visualização antecipada do desenvolvedor das extensões de mensagem do Teams habilitadas para Outlook.
