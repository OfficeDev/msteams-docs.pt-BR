---
title: Carregar seu aplicativo personalizado
description: Descreve como carregar seu aplicativo no Microsoft Teams
ms.topic: how-to
ms.author: lajanuar
keywords: carregamento de aplicativos do teams
ms.openlocfilehash: c9102fa5b7056dda0db8d3e260bfb3e94b7f4e56
ms.sourcegitcommit: 7b4f383b506d4bc68a1b5641d6e0f404edbfbc6d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/22/2021
ms.locfileid: "51946477"
---
# <a name="upload-an-app-package-to-microsoft-teams"></a>Carregar um pacote do aplicativo para o Microsoft Teams

Para testar sua experiência de aplicativo no Microsoft Teams, você precisa carregar seu aplicativo no Teams. O carregamento adiciona o aplicativo à equipe selecionada e todos os membros da equipe podem interagir com ele como usuários finais.

> [!NOTE]
> Carregar um pacote atualizado para um aplicativo existente com um bot pode não mostrar alterações na guia quando exibido pela janela de conversas. Você pode acessar o aplicativo por meio do sub-uso ou teste de aplicativos em um ambiente limpo.

## <a name="create-your-upload-package"></a>Criar seu pacote de carregamento

Para desenvolvimento e envio do AppSource, você deve criar um pacote que você pode carregar. O pacote deve conter as informações para descrever sua experiência. O pacote é um arquivo .zip que contém o manifesto do aplicativo e ícones que definem sua experiência com exclusividade.

Para criar um pacote de carregamento, consulte [Create the package for your Microsoft Teams app](../build-and-test/apps-package.md).

Depois de criar o pacote, carregue-o em uma equipe. O pacote carregado só está disponível para os usuários da equipe selecionada.

## <a name="load-your-package-into-teams"></a>Carregar seu pacote no Teams

Você pode testar seu pacote carregando-o no Teams.

> [!NOTE]
> Para carregar para funcionar, o administrador do locatário deve primeiro [habilitar o carregamento de aplicativos.](/microsoftteams/admin-settings)

Há duas maneiras de carregar seu aplicativo no Teams:

* Usando a Loja
* Usando a guia Aplicativos

## <a name="upload-your-package-into-a-team-or-conversation-using-the-store"></a>Carregar seu pacote em uma equipe ou conversa usando a Loja

1. No canto inferior esquerdo do Teams, escolha o **ícone da** Loja. Na página Da Loja, escolha **Carregar um aplicativo personalizado.**

  ![Exibir equipe](../../assets/images/store-upload-a-custom-app2.png)

2. Na caixa **de diálogo Abrir,** navegue até o pacote que você deseja carregar e escolha Abrir.

   ![Adicionar menu](../../assets/images/NewappAddmenudropdown.png)

O pacote carregado deve estar disponível para uso na equipe ou na conversa especificada na caixa de diálogo de consentimento. Se seu aplicativo não aparecer, o motivo mais comum será um erro no manifesto, especialmente as IDs do aplicativo, bot e extensões de mensagens. Se o aplicativo não tiver escopo para conversas, essa opção não aparecerá.

>[!NOTE]
> Os aplicativos em conversas estão atualmente [na](../../resources/dev-preview/developer-preview-intro.md)Visualização do Desenvolvedor e a opção não aparece se o Teams não estiver sendo executado nesse modo.

![Exemplo de bot na lista de bots carregados](../../assets/images/botinlist.jpg)

## <a name="upload-your-package-into-a-team-using-the-apps-tab"></a>Carregar seu pacote em uma equipe usando a guia Aplicativos

1. Na equipe de destino, escolha **Mais opções** (**&#8943;**) e selecione **Gerenciar equipe**.

   > [!NOTE]
   > Você deve ser o proprietário da equipe ou o proprietário deve dar acesso aos usuários para adicionar os tipos de aplicativo apropriados para que essa funcionalidade apareça.

2. Selecione a **guia Aplicativos** e escolha **Carregar um aplicativo personalizado** no canto inferior direito.

   ![Ponto de entrada de carregamento](../../assets/images/UploadACustomApp.png)

3. Selecione seu pacote .zip no computador.

4. Você pode ver seu aplicativo carregado na lista.

   ![Exemplo de bot na lista de bots carregados](../../assets/images/botinlist.jpg)

Se o aplicativo não for carregado, o motivo mais comum será um erro no manifesto, especialmente as IDs do aplicativo, bot e extensões de mensagens.

## <a name="access-your-uploaded-configurable-tab"></a>Acessar sua guia configurável carregada

Se o aplicativo contiver guias, os usuários poderão fixá-las em qualquer conversa ou canal de equipe usando o fluxo de galeria de guias padrão:

1. Vá para um canal na equipe. Escolha **+** adicionar uma guia à direita das guias existentes.

2. Selecione sua guia na galeria exibida.

3. Aceite o prompt de consentimento.

4. Configure sua guia por meio de sua [página de configuração](../../tabs/how-to/create-tab-pages/configuration-page.md) e selecione **Salvar**.

  ![A caixa de diálogo Adicionar uma guia, com uma galeria de guias disponíveis](../../assets/images/tab_gallery.png)

## <a name="access-your-uploaded-bot"></a>Acessar seu bot carregado

Depois de adicionar o bot a uma equipe, ele deve ser usável por qualquer pessoa nessa equipe, dentro e fora dos canais de equipe, dependendo da definição do escopo do bot. Todos os membros da equipe podem ver uma postagem no **canal Geral** indicando que o bot foi adicionado à equipe.

Para um bot do Teams, você pode começar invocando seu bot @mentioning o nome do bot.

Para testar chats diretos com seu bot, você pode acessá-lo por meio da página @mention app em um canal ou pesquisá-lo na janela **Novo Chat.**

Você pode @mention o bot em uma conversa ou pesquisá-lo na janela **Novo Chat** para testar chats diretos com seu bot.

## <a name="access-your-uploaded-connector"></a>Acessar o conector carregado

Com o aplicativo carregado na equipe ou na conversa, os usuários podem configurar um Conector usando o fluxo de galeria de Conectores padrão:

1. Vá para um canal na equipe. Escolha **Mais opções** (*&#8943;*) e escolha **Conectores**.

2. Selecione seu Conector na **seção Sideloaded** na parte inferior.

3. Configure seu conector por meio de sua [página de configuração](../../webhooks-and-connectors/how-to/connectors-creating.md) e selecione **Salvar**.

  ![A caixa de diálogo Adicionar uma guia, com uma galeria de guias disponíveis.](../../assets/images/connector_gallery.png)

## <a name="access-your-uploaded-messaging-extension"></a>Acessar sua extensão de mensagens carregada

Um aplicativo carregado com uma extensão de mensagens aparece automaticamente no menu **Mais** opções (*&#8943;*) na caixa de redação.

![Extensões de mensagens](../../assets/images/compose-extensions/cesampleapp.png)


## <a name="remove-or-update-your-app"></a>Remover ou atualizar seu aplicativo

Para remover seu aplicativo, selecione o ícone de exclusão ao lado do nome do aplicativo na lista Exibir bots **do Teams.** Se você alterar as informações do manifesto, primeiro remova o aplicativo e adicione o pacote atualizado, consulte [Carregar seu pacote em uma equipe](#load-your-package-into-teams). As alterações de código em seu serviço não exigem que você carregue seu manifesto novamente. No entanto, se as alterações de código exigirem atualizações de manifesto, como alterações na URL ou na ID do aplicativo microsoft para seu bot, você deve carregar o manifesto novamente.

> [!NOTE]
> Não é possível remover um bot de um contexto pessoal inteiramente. Se o bot for removido e adicionado novamente, a comunicação adicional com o bot será acrescentada à conversa anterior.

## <a name="troubleshooting-notes"></a>Anotações de solução de problemas

Se o manifesto não for carregado, verifique se você seguiu todas as instruções em [Criar](../../concepts/build-and-test/apps-package.md) o pacote e validou seu manifesto em relação ao [esquema](../../resources/schema/manifest-schema.md).
