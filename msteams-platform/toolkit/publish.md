---
title: Publicar aplicativos do Teams usando o Kit de Ferramentas do Teams
author: zyxiaoyuer
description: Neste módulo, saiba como publicar aplicativos Teams usando Teams Toolkit e publicar em escopo ou permissão de sideload individuais
ms.localizationpriority: medium
ms.topic: overview
ms.date: 11/29/2021
ms.openlocfilehash: 0ae6ab1f128eccae6df4fff20364f590106ab146
ms.sourcegitcommit: ca84b5fe5d3b97f377ce5cca41c48afa95496e28
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/17/2022
ms.locfileid: "66142602"
---
# <a name="publish-teams-apps-using-teams-toolkit"></a>Publicar aplicativos do Teams usando o Kit de Ferramentas do Teams

Após criar o aplicativo, você poderá distribuí-lo para diferentes escopos, tais como individual, equipe, organização ou qualquer pessoa. A distribuição depende de vários fatores, incluindo necessidades, requisitos comerciais e técnicos e sua meta para o aplicativo. A distribuição para diferentes escopos pode precisar de um processo de análise diferente. Em geral, quanto maior o escopo, mais análises precisam ser feitas no aplicativo por questões de segurança e conformidade.

## <a name="prerequisite"></a>Pré-requisito

* [Instalar o Kit de Ferramentas do Teams](https://marketplace.visualstudio.com/items?itemName=TeamsDevApp.ms-teams-vscode-extension) versão v3.0.0+.

> [!TIP]
> Certifique-se de ter o projeto do aplicativo do Teams no VS code.

## <a name="publish-to-individual-scope-or-sideload-permission"></a>Publicar para um escopo individual ou permissão de sideload

Os usuários podem adicionar um aplicativo personalizado ao Teams fazendo upload de um pacote do aplicativo em um arquivo *.zip diretamente para uma equipe ou em um contexto pessoal. Adicionar um aplicativo personalizado por meio do upload de um pacote do aplicativo é conhecido como sideload e permite que você teste o aplicativo durante o desenvolvimento, antes que o aplicativo esteja pronto para ser amplamente distribuído, conforme mencionado nos seguintes cenários:

* Testar e depurar um aplicativo localmente.
* Crie um aplicativo para você mesmo, como automatizar um fluxo de trabalho.
* Construa um aplicativo para pequenos conjuntos de usuários, como, por exemplo, seu grupo de trabalho.

Você pode criar um aplicativo apenas para uso interno e compartilhá-lo com sua equipe sem enviá-lo ao catálogo de aplicativos do Teams na loja de aplicativos do Teams.

**Para criar seu aplicativo para o arquivo *.zip do pacote do aplicativo**

Você pode criar o pacote do aplicativo selecionando `Zip Teams metadata package` de **IMPLANTAÇÃO** no Treeview do Kit de Ferramentas do Teams. É necessário executar `Provision in the cloud` primeiro. O pacote do aplicativo gerado estará localizado em `{your project folder}/build/appPackage/appPackage.{env}.zip`.

Execute as seguintes etapas para fazer upload do pacote do aplicativo:

1. No cliente do Teams, selecione **Aplicativos** na barra esquerda.
2. Selecione **Gerenciar seus aplicativos**.
3. Selecione **publicar um aplicativo**

   :::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/pub.png" alt-text="publish":::

4. Selecione **Fazer o upload de um aplicativo personalizado**:

   :::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/uplo.png" alt-text="upload":::

## <a name="publish-to-your-organization"></a>Publicar em sua organização

Quando o aplicativo estiver pronto para uso em produção, você pode enviar o aplicativo usando a API de envio de aplicativos do Teams, chamada de API do Graph, um ambiente de desenvolvimento integrado (IDE), como o Microsoft Visual Studio Code, instalado com o kit de ferramentas do Teams. Você pode selecionar **Publicar no Teams** da **IMPLANTAÇÃO** no TreeView do Kit de Ferramentas do Teams ou o gatilho **Teams: Publicar no Teams** na paleta de comandos. Em seguida, selecione **Instalar para sua organização**:

![Instalar para sua organização](./images/installforyourorganization.png)

O aplicativo está disponível em **Gerenciar aplicativos** no Centro de administração do Microsoft Teams, onde você e o administrador podem examiná-lo e aprová-lo.

Como administrador, **Gerenciar aplicativos** no [Centro de administração do Microsoft Teams](https://admin.teams.microsoft.com/policies/manage-apps) é onde você pode exibir e gerenciar todos os aplicativos do Teams da sua organização. Você pode ver o status e as propriedades dos aplicativos em nível organizacional, aprovar ou carregar novos aplicativos personalizados para a loja de aplicativos da sua organização, bloquear ou permitir aplicativos no nível organizacional, adicionar aplicativos a equipes, comprar serviços para aplicativos de terceiros, visualizar permissões solicitadas por aplicativos, dar consentimento do administrador a aplicativos e [gerenciar configurações de aplicativos em toda a organização ](https://admin.teams.microsoft.com/policies/manage-apps).

O kit de ferramentas do Teams para Visual Studio Code, criado sobre a API de Envio de Aplicativos do Teams, permite automatizar o processo de envio para aprovação de aplicativos personalizados no Teams.

> [!NOTE]
> O aplicativo ainda não está publicado na loja de aplicativos da sua organização. A etapa envia o aplicativo para o Centro de administração do Microsoft Teams, onde você pode aprová-lo para publicação na loja de aplicativos da sua organização.

## <a name="admin-approval-for-teams-apps"></a>Aprovação do administrador para aplicativos do Teams

O administrador do seu locatário do Teams pode então acessar **Gerenciar aplicativos** no Centro de administração do Microsoft Teams, no painel de navegação à esquerda, vá para Aplicativos do Teams > Gerenciar aplicativos. Você pode exibir todos os aplicativos do Teams da sua organização. No widget de Aprovação Pendente, na parte superior da página, você saberá quando um aplicativo personalizado será enviado para aprovação.
Na tabela, um aplicativo recém-enviado publica automaticamente o status dos aplicativos enviados e bloqueados. Você pode classificar a coluna de status de publicação em ordem decrescente para encontrar o aplicativo:

 :::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/admin-approval-for-teams-app-1.png" alt-text="aprovação":::

Selecione o nome do aplicativo para acessar a página de detalhes do aplicativo. Na guia Sobre, você pode exibir os detalhes sobre o aplicativo, incluindo a descrição, o status e a ID do aplicativo:

 :::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/about-submitted-app-1.png" alt-text="aplicativo enviado":::

Execute as seguintes etapas para publicar o aplicativo :

1. Na navegação à esquerda do Centro de administração do Microsoft Teams, vá para Aplicativos do Teams > **Gerenciar aplicativos**.
2. Selecione o nome do aplicativo para ir para a página de detalhes do aplicativo, e então na caixa de status, selecione **Publicar**.
Após a publicação do aplicativo, o status de publicação é alterado para publicado e o status é automaticamente alterado para permitido.

## <a name="publish-to-microsoft-store"></a>Publicar na Microsoft Store

Você pode distribuir seu aplicativo diretamente na loja do Microsoft Teams e alcançar milhões de usuários em todo o mundo. Se seu aplicativo também estiver em destaque na loja, você poderá alcançar instantaneamente clientes em potencial. Os aplicativos publicados na loja do Teams também são listados automaticamente no Microsoft AppSource, que é o mercado oficial para aplicativos e soluções do Microsoft 365.

Para obter mais informações, consulte ([Publicar seu aplicativo na Microsoft Teams store](../concepts/deploy-and-publish/appsource/publish.md#publish-your-app-to-the-microsoft-teams-store)).

## <a name="see-also"></a>Confira também

* [Gerenciar vários ambientes](TeamsFx-multi-env.md)
* [Colaborar com outros desenvolvedores no projeto do Teams](TeamsFx-collaboration.md)
