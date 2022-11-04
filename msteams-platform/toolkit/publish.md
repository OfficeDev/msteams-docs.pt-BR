---
title: Publicar aplicativos do Teams usando o Kit de Ferramentas do Teams
author: zyxiaoyuer
description: Neste módulo, saiba como publicar aplicativos do Teams usando o Teams Toolkit e publicar em escopo individual ou permissão de sideload
ms.localizationpriority: medium
ms.topic: overview
ms.date: 11/29/2021
ms.openlocfilehash: d6333afb6d62fc832310c165c30970254998e91e
ms.sourcegitcommit: c3601696cced9aadc764f1e734646ee7711f154c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/03/2022
ms.locfileid: "68833153"
---
# <a name="publish-teams-apps-using-teams-toolkit"></a>Publicar aplicativos do Teams usando o Kit de Ferramentas do Teams

Após criar o aplicativo, você poderá distribuí-lo para diferentes escopos, tais como individual, equipe, organização ou qualquer pessoa. A distribuição depende de vários fatores, como necessidades, requisitos comerciais e técnicos e sua meta para o aplicativo. A distribuição para diferentes escopos pode precisar de um processo de análise diferente. Em geral, quanto maior o escopo, mais análises precisam ser feitas no aplicativo por questões de segurança e conformidade.

:::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/publish-flow.png" alt-text="fluxo de publicação":::

Veja o que você aprenderá nesta seção:

* [Publicar para um escopo individual ou permissão de sideload](#publish-to-individual-scope-or-sideload-permission)
* [Publicar em sua organização](#publish-to-your-organization)
* [Publicar na loja do Microsoft Teams](#publish-to-microsoft-teams-store)

## <a name="prerequisites"></a>Pré-requisitos

* Crie seu [pacote de aplicativos](~/concepts/build-and-test/apps-package.md) e [valide-o](https://dev.teams.microsoft.com/appvalidation.html) para erros.
* [Habilitar o upload de aplicativos personalizados](~/concepts/build-and-test/prepare-your-o365-tenant.md#enable-custom-teams-apps-and-turn-on-custom-app-uploading) no Teams.
* Verifique se o aplicativo está em execução e é acessível por meio de HTTPs.
* Verifique se você seguiu o conjunto de diretrizes na publicação do aplicativo na loja do Microsoft Teams para publicar seu aplicativo.

## <a name="publish-to-individual-scope-or-sideload-permission"></a>Publicar para um escopo individual ou permissão de sideload

Você pode adicionar um aplicativo personalizado ao Teams carregando um [pacote de aplicativo](../concepts/build-and-test/apps-package.md) em um arquivo *.zip diretamente em uma equipe ou em contexto pessoal. Adicionar um aplicativo personalizado carregando um pacote de aplicativo é conhecido como sideload. Ele permite que você teste o aplicativo durante o carregamento no Teams. Você pode criar e testar o aplicativo nos seguintes cenários:

* Testar e depurar um aplicativo localmente.
* Crie um aplicativo para você mesmo, como automatizar um fluxo de trabalho.
* Construa um aplicativo para pequenos conjuntos de usuários, como, por exemplo, seu grupo de trabalho.

Você pode criar um aplicativo apenas para uso interno e compartilhá-lo com sua equipe sem enviá-lo ao catálogo de aplicativos do Teams na loja de aplicativos do Teams. Para obter mais informações, consulte [Carregar seu aplicativo no Teams](../concepts/deploy-and-publish/apps-upload.md).

### <a name="to-build-your-app-to-zip-app-package-file"></a>Para criar seu aplicativo para o arquivo de pacote de aplicativo zip

Você precisa executar `Provision in the cloud` primeiro antes de criar o pacote do aplicativo. As etapas a seguir ajudam você a criar o pacote de aplicativos.

* Selecione **Pacote de metadados do Zip Teams** em **DEPLOYMENT**.<br>
    O pacote do aplicativo gerado estará localizado em `{your project folder}/build/appPackage/appPackage.{env}.zip`.

### <a name="to-upload-app-package"></a>Para carregar o pacote de aplicativos

Execute as seguintes etapas para fazer upload do pacote do aplicativo:

1. No cliente do Teams, selecione **Aplicativos** > **Gerenciar seus aplicativos** > **carregar um aplicativo**.

   :::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/publish1.png" alt-text="publicar um aplicativo":::

   **O upload de uma** janela do aplicativo é exibido.

2. Selecione **Fazer o upload de um aplicativo personalizado**.

   :::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/upload.png" alt-text="carregar um aplicativo":::

   Agora o aplicativo está sideload no cliente do Teams e você pode adicioná-lo e exibi-lo.

## <a name="publish-to-your-organization"></a>Publicar em sua organização

Quando o aplicativo estiver pronto para uso na produção, você pode enviar o aplicativo usando a API de envio de aplicativo do Teams, chamada de API do Graph. A API de envio de aplicativo do Teams é um IDE (ambiente de desenvolvimento integrado), como o Microsoft Visual Studio Code instalado com o kit de ferramentas do Teams. As seguintes etapas ajudam você a publicar o aplicativo em sua organização:

* [Publicar no Teams Toolkit](#publish-from-teams-toolkit)
* [Aprovar no Centro de Administração](#approve-on-admin-center)

### <a name="publish-from-teams-toolkit"></a>Publicar no Teams Toolkit

As seguintes etapas ajudam você a publicar o aplicativo no Teams Toolkit:

1. Você pode publicar seu aplicativo teams de uma das seguintes maneiras:
     * Selecione **Publicar no Teams** em **IMPLANTAÇÃO** na visão de árvore do Kit de Ferramentas do Teams.
     * Insira o gatilho **Teams: publicar no Teams** na paleta de comandos.

   :::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/select-publish.png" alt-text="Selecionar Publicar":::

1. Selecione **Instalar para sua organização**.

   :::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/installforyourorganization.png" alt-text="Instalar para sua organização":::

   Agora, o aplicativo é publicado com êxito no portal de administração e você vê o seguinte aviso:

   :::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/confirm-publish.png" alt-text="Confirmar Publicação":::

Agora, o aplicativo está disponível no centro de administração **Gerenciar aplicativos** do Microsoft Teams, onde você e o administrador podem revisá-lo e aprová-lo.

> [!NOTE]
> O aplicativo ainda não está publicado na loja de aplicativos da sua organização. A etapa envia o aplicativo para o Centro de administração do Microsoft Teams, onde você pode aprová-lo para publicação na loja de aplicativos da sua organização.

### <a name="approve-on-admin-center"></a>Aprovar no Centro de Administração

O kit de ferramentas do Teams para Visual Studio Code criado em cima da API de Envio de Aplicativos do Teams e permite automatizar o processo de envio à aprovação de aplicativos personalizados no Teams.

  > [!NOTE]
  > Certifique-se de ter o projeto do aplicativo do Teams no VS code. Como administrador, **Gerenciar aplicativos** no [Centro de administração do Microsoft Teams](https://admin.teams.microsoft.com/policies/manage-apps) é onde você pode exibir e gerenciar todos os aplicativos do Teams da sua organização. Você pode fazer as seguintes atividades no centro de administração:
  >
  > * Consulte o status do nível da organização e as propriedades dos aplicativos.
  > * Aprovar ou carregar novos aplicativos personalizados na loja de aplicativos da sua organização.
  > * Bloquear ou permitir aplicativos no nível da organização.
  > * Adicione aplicativos ao Teams.
  > * Compre serviços para aplicativos de terceiros.
  > * Exibir permissões solicitadas por aplicativos.
  > * Conceda o consentimento do administrador aos aplicativos.
  > * [Gerenciar configurações de aplicativo em toda a organização](https://admin.teams.microsoft.com/policies/manage-apps).

As seguintes etapas ajudam você a aprovar do Centro de Administração:

1. Selecione **Ir para o portal de administração**.

1. Selecione o :::image type="icon" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/Showall.PNG"::: ícone > **aplicativo** >  teams **Gerenciar aplicativos**.

   :::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/select-manage-apps.png" alt-text="Selecione Gerenciar aplicativos":::

   Você pode exibir todos os aplicativos do Teams para sua organização.

   No widget de Aprovação Pendente, na parte superior da página, você saberá quando um aplicativo personalizado será enviado para aprovação. Na tabela, um aplicativo recém-enviado publica automaticamente o status dos aplicativos enviados e bloqueados. Você pode classificar a coluna de status de publicação em ordem decrescente para localizar o aplicativo.

   :::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/admin-approval-for-teams-app-1.png" alt-text="aprovação":::

1. Selecione o nome do aplicativo para acessar a página de detalhes do aplicativo. Na guia **Sobre** , você pode exibir detalhes sobre o aplicativo, incluindo descrição, status e ID do aplicativo.

   :::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/about-submitted-app-1.png" alt-text="aplicativo enviado":::

1. Selecione a lista suspensa de status e altere de **Enviado** para **Publicar**.

   Após a publicação do aplicativo, o status de publicação é alterado para publicado e o status é automaticamente alterado para permitido.

   Para obter mais informações, consulte [Publicar em sua organização](/MicrosoftTeams/manage-apps?toc=%2Fmicrosoftteams%2Fplatform%2Ftoc.json&bc=%2Fmicrosoftteams%2Fplatform%2Fbreadcrumb%2Ftoc.json)

## <a name="publish-to-microsoft-teams-store"></a>Publicar na loja do Microsoft Teams

Você pode distribuir seu aplicativo diretamente na loja do Microsoft Teams e alcançar milhões de usuários em todo o mundo. Se seu aplicativo também estiver em destaque na loja, você poderá alcançar instantaneamente clientes em potencial. Os aplicativos publicados na loja do Teams também são listados automaticamente no Microsoft AppSource, que é o mercado oficial para aplicativos e soluções do Microsoft 365.

Para obter mais informações, consulte [Publicar seu aplicativo na loja do Microsoft Teams](../concepts/deploy-and-publish/appsource/publish.md#publish-your-app-to-the-microsoft-teams-store).

## <a name="see-also"></a>Confira também

* [Distribuir seu aplicativo Microsoft Teams](../concepts/deploy-and-publish/apps-publish-overview.md)
* [Criar pacote de aplicativos do Teams](../concepts/build-and-test/apps-package.md)
* [Preparar o locatário do Microsoft 365](../concepts/build-and-test/prepare-your-o365-tenant.md)
* [Publicar seu aplicativo na loja do Microsoft Teams](../concepts/deploy-and-publish/appsource/publish.md)
* [Carregar seu aplicativo no Teams](../concepts/deploy-and-publish/apps-upload.md)
* [Gerenciar o aplicativo teams no centro de administração do Microsoft Teams](/MicrosoftTeams/manage-apps?toc=%2Fmicrosoftteams%2Fplatform%2Ftoc.json&bc=%2Fmicrosoftteams%2Fplatform%2Fbreadcrumb%2Ftoc.json)
