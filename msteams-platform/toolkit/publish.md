---
title: Publicar aplicativos do Teams usando o Kit de Ferramentas do Teams
author: zyxiaoyuer
description: publicar Teams aplicativos
ms.author: yanjiang
ms.localizationpriority: medium
ms.topic: overview
ms.date: 11/29/2021
---


# <a name="publish-teams-apps-using-teams-toolkit"></a>Publicar aplicativos do Teams usando o Kit de Ferramentas do Teams

Depois de criar o aplicativo, você pode distribuir seu aplicativo para escopos diferentes, como individual, equipe, organização ou qualquer pessoa. A distribuição depende de vários fatores, incluindo necessidades, requisitos técnicos e comerciais e sua meta para o aplicativo. A distribuição para escopos diferentes pode precisar de um processo de revisão diferente. Em geral, quanto maior o escopo, mais o aplicativo precisa passar por questões de segurança e conformidade.

## <a name="prerequisite"></a>Pré-requisito

* [Instale Teams Toolkit](https://marketplace.visualstudio.com/items?itemName=TeamsDevApp.ms-teams-vscode-extension) versão v3.0.0+.

> [!TIP]
> Verifique se você Teams projeto de aplicativo no código VS.

## <a name="publish-to-individual-scope-or-sideload-permission"></a>Publicar em escopo individual ou permissão de sideload

Os usuários podem adicionar aplicativo personalizado Teams carregando um pacote de aplicativo em um arquivo *.zip diretamente para uma equipe ou em contexto pessoal. Adicionar um aplicativo personalizado carregando um pacote de aplicativo é conhecido como sideload e permite que você teste o aplicativo enquanto está sendo desenvolvido, antes que o aplicativo esteja pronto para ser amplamente distribuído, conforme mencionado nos seguintes cenários:

* Teste e depure um aplicativo localmente.
* Crie um aplicativo para si mesmo, como para automatizar um fluxo de trabalho.
* Crie um aplicativo para um pequeno conjunto de usuários, como seu grupo de trabalho.

Você pode criar um aplicativo apenas para uso interno e compartilhá-lo com sua equipe sem Teams ao catálogo de aplicativos do Teams app store.

**Para criar seu aplicativo para.zip *de pacote de aplicativos**

Você pode criar o pacote de aplicativos selecionando em `Zip Teams metadata package` **DEPLOYMENT** em Treeview of Teams Toolkit. Você precisa executar primeiro `Provision in the cloud` . O pacote de aplicativo gerado estará localizado em `{your project folder}/build/appPackage/appPackage.{env}.zip`.

Execute as seguintes etapas para carregar o pacote de aplicativos:

1. No cliente Teams, selecione **Aplicativos** na barra esquerda.
2. Selecione **Gerenciar seus aplicativos**.
3. Selecione **publicar um aplicativo**

   :::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/pub.png" alt-text="publish":::

4. Selecione **Upload um aplicativo personalizado**:

   :::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/uplo.png" alt-text="upload":::

## <a name="publish-to-your-organization"></a>Publicar em sua organização 

Quando o aplicativo estiver pronto para uso em produção, você poderá enviar o aplicativo usando a API de envio de aplicativo Teams, chamada da API Graph, um ambiente de desenvolvimento integrado (IDE), como o código Microsoft Visual Studio instalado com Teams toolkit. Você pode selecionar **Publicar para Teams** **de IMPLANTAÇÃO** no TreeView do Teams Toolkit ou Teams **: Publicar** no Teams da paleta de comandos. Em seguida **, selecione Instalar para sua organização**:

![Instalar para sua organização](./images/installforyourorganization.png)

O aplicativo está disponível no Centro de administração **Gerenciar aplicativos** do Microsoft Teams, onde você e o administrador podem revisá-lo e aprove-lo.

Como administrador, **Gerenciar aplicativos** no centro [](https://admin.teams.microsoft.com/policies/manage-apps) de administração Microsoft Teams é onde você pode exibir e gerenciar todos os Teams aplicativos para sua organização. Você pode ver o status e as propriedades do nível da organização dos aplicativos, aprovar ou carregar novos aplicativos personalizados no armazenamento de aplicativos da sua organização, bloquear ou permitir aplicativos no nível da organização, adicionar [aplicativos às equipes](https://admin.teams.microsoft.com/policies/manage-apps), comprar serviços para aplicativos de terceiros, exibir permissões solicitadas por aplicativos, conceder consentimento de administrador a aplicativos e gerenciar configurações de aplicativos de toda a organização.

Teams kit de ferramentas para Visual Studio Code criado sobre Teams API de Envio de Aplicativos do Teams e permite automatizar o processo de envio para aprovação para aplicativos personalizados no Teams.

> [!NOTE]
> O aplicativo ainda não publica na loja de aplicativos da sua organização. A etapa envia o aplicativo para o centro de administração Microsoft Teams onde você pode aprove-lo para publicação na loja de aplicativos da sua organização.

## <a name="admin-approval-for-teams-apps"></a>Aprovação do administrador para Teams aplicativos

O administrador do seu locatário Teams pode, em seguida, ir para  o Centro de administração gerenciar aplicativos no centro de administração Microsoft Teams, na navegação à esquerda, vá para Teams aplicativos > Gerenciar aplicativos. Você pode exibir todos os Teams aplicativos para sua organização. No widget de aprovação pendente na parte superior da página permite que você saiba quando um aplicativo personalizado é enviado para aprovação.
Na tabela, um aplicativo recém-enviado publica automaticamente o status de aplicativos enviados e bloqueados. Você pode classificar a coluna de status de publicação em ordem decrescente para encontrar o aplicativo:

 :::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/admin-approval-for-teams-app-1.png" alt-text="aprovação":::

Selecione o nome do aplicativo para ir para a página de detalhes do aplicativo. Na guia Sobre, você pode exibir detalhes sobre o aplicativo, incluindo descrição, status e ID do aplicativo:

 :::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/about-submitted-app-1.png" alt-text="aplicativo enviado":::

Execute as etapas a seguir para publicar o aplicativo :

1. Na navegação à esquerda do centro de administração Microsoft Teams, acesse Teams aplicativos > **Gerenciar aplicativos**.
2. Selecione o nome do aplicativo para ir para a página de detalhes do aplicativo e, na caixa status, selecione **Publicar**.
Depois de publicar o aplicativo, o status de publicação muda para publicado e o status muda automaticamente para permitido.

## <a name="publish-to-microsoft-store"></a>Publicar na Microsoft Store

Você pode distribuir seu aplicativo diretamente para a loja dentro Microsoft Teams e alcançar milhões de usuários em todo o mundo. Se seu aplicativo também estiver em destaque na loja, você poderá alcançar instantaneamente clientes em potencial. Os aplicativos publicados no Teams store também listam automaticamente no Microsoft AppSource, que é o marketplace oficial para Microsoft 365 aplicativos e soluções.

Para obter mais informações, [consulte publish to microsoft Teams store]([Publish your app to the Microsoft Teams store](../concepts/deploy-and-publish/appsource/publish.md#publish-your-app-to-the-microsoft-teams-store))

## <a name="see-also"></a>Confira também

* [Gerenciar vários ambientes](TeamsFx-multi-env.md)
* [Colaborar com outros desenvolvedores no Teams projeto](TeamsFx-collaboration.md)