---
title: Carregar seu aplicativo personalizado
description: Descreve como carregar seu aplicativo no Microsoft Teams
ms.topic: how-to
keywords: aplicativos de equipes carregar
ms.openlocfilehash: 2e7a21dc27fdfe824ecacebabbb61a3b99ae8e79
ms.sourcegitcommit: 976e870cc925f61b76c3830ec04ba6e4bdfde32f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/27/2021
ms.locfileid: "50014338"
---
# <a name="upload-an-app-package-to-microsoft-teams"></a>Carregar um pacote do aplicativo para o Microsoft Teams

Para testar sua experiência de aplicativo no Microsoft Teams, você precisa carregar seu aplicativo para o Teams. Carregar adiciona o aplicativo à equipe selecionada, e você e os membros da equipe podem interagir com ele, como os usuários finais.

> [!NOTE]
> Carregar um pacote atualizado para um aplicativo existente com um bot pode não mostrar alterações na guia quando visualizado por meio da janela conversas. É melhor acessá-lo por meio do sub-sub-uso de aplicativos ou testar em um ambiente de teste limpo.

## <a name="create-your-upload-package"></a>Criar seu pacote de upload

Para o desenvolvimento, bem como o envio ao AppSource (antigo Office Store), você deve criar um pacote que pode ser carregado contendo as informações para descrever sua experiência. O pacote, um arquivo .zip, contém o manifesto do aplicativo e ícones que definem exclusivamente sua experiência.

Para criar um pacote de upload, [confira Criar o pacote para o aplicativo Microsoft Teams.](../build-and-test/apps-package.md)

Com o pacote criado, agora você pode carregar em uma equipe. Depois de carregado, ele estará disponível para todos os usuários na equipe selecionada e somente para os usuários dessa equipe.

## <a name="load-your-package-into-teams"></a>Carregar seu pacote no Teams

Você pode testar seu pacote carregando-o no Teams.

> [!NOTE]
> Para que o carregamento funcione, o administrador do locatário deve primeiro [habilitar o carregamento de aplicativos.](/microsoftteams/admin-settings)

Há duas maneiras de carregar seu aplicativo no Teams:

* Usando a Loja
* Usando a guia Aplicativos

## <a name="upload-your-package-into-a-team-or-conversation-using-the-store"></a>Carregar seu pacote em uma equipe ou conversa usando a Loja

1. No canto inferior esquerdo do Teams, escolha o ícone da Loja. Na página da Loja, escolha "Carregar um aplicativo personalizado".

  ![Exibir equipe](../../assets/images/store-upload-a-custom-app2.png)

2. Na caixa *de* diálogo Abrir, navegue até o pacote que você deseja carregar e escolha *Abrir.*

   ![Menu Adicionar](../../assets/images/NewappAddmenudropdown.png)

O pacote carregado agora deve estar disponível para uso na equipe ou na conversa especificada na caixa de diálogo de consentimento. Se seu aplicativo não aparecer, o motivo mais comum será um erro no manifesto, especialmente ids para o aplicativo, bot e extensões de mensagens. Se o aplicativo não tiver escopo para conversas, essa opção não será exibida.

>[!NOTE]
> Os aplicativos em conversas estão atualmente [na](../../resources/dev-preview/developer-preview-intro.md)Visualização do Desenvolvedor e a opção não aparecerá se o Teams não estiver sendo executado nesse modo.

![Exemplo de bot na lista de bots carregados](../../assets/images/botinlist.jpg)

## <a name="upload-your-package-into-a-team-using-the-apps-tab"></a>Carregar seu pacote em uma equipe usando a guia Aplicativos

1. Na equipe de destino, escolha *Mais opções* (**&#8943;**) e escolha *Gerenciar equipe*.

   > [!NOTE]
   > Você deve ser o proprietário da equipe ou o proprietário deve permitir que os usuários adicionem os tipos de aplicativo apropriados para que essa funcionalidade apareça.

2. Selecione a guia Aplicativos e escolha *Carregar um aplicativo personalizado* no canto inferior direito.

   ![Ponto de entrada de carregamento](../../assets/images/UploadACustomApp.png)

3. Navegue até e selecione seu pacote .zip no computador.

4. Após uma breve pausa, você verá seu aplicativo carregado na lista.

   ![Exemplo de bot na lista de bots carregados](../../assets/images/botinlist.jpg)

Se o aplicativo não carregar, o motivo mais comum será um erro no manifesto, especialmente ids para o aplicativo, bot e extensões de mensagens.

## <a name="accessing-your-uploaded-configurable-tab"></a>Acessando sua guia configurável carregada

Se o aplicativo contiver guias, os usuários poderão fixá-las em qualquer conversa ou canal de equipe usando o fluxo da galeria de guias padrão:

1. Vá para um canal na equipe. Escolha *+* ( Adicionar uma *guia*) à direita das guias existentes.

2. Selecione sua guia na galeria exibida.

3. Aceite a solicitação de consentimento.

4. Configure sua guia por meio de sua página [de configuração](../../tabs/how-to/create-tab-pages/configuration-page.md) e escolha *Salvar*.

  ![A caixa de diálogo Adicionar uma guia, com uma galeria de guias disponíveis](../../assets/images/tab_gallery.png)

## <a name="accessing-your-uploaded-bot"></a>Acessando seu bot carregado

Quando você adiciona um bot a uma equipe, ele deve ser disponibilizado por qualquer pessoa dessa equipe, dentro e fora dos canais de equipe, dependendo da definição de escopo do bot. Você e outros membros da equipe verão uma postagem no canal Geral indicando que o bot foi adicionado à equipe.

Para um bot habilitado para equipes, você pode começar invocando seu bot @mentioning o nome do bot, que deve ser preenchimento automático.

Para testar chats diretos com seu bot, você pode acessá-lo por meio da página de aplicativo, @mention-lo em um canal ou pesquisá-lo na janela Novo **Chat.**

Ao adicionar seu bot a uma conversa para testar chats diretos com seu bot, você pode @mention-lo em uma conversa ou pesquisá-lo na janela Novo **Chat.**

## <a name="accessing-your-uploaded-connector"></a>Acessando seu Conector carregado

Com o aplicativo carregado na equipe ou na conversa, os usuários podem configurar um Conector usando o fluxo da galeria de Conectores padrão:

1. Vá para um canal na equipe. Escolha *Mais opções* (*&#8943;*) e escolha *Conectores*.

2. Selecione o Conector na **seção Sideload** na parte inferior.

3. Configure seu Conector por meio de sua página [de configuração](../../webhooks-and-connectors/how-to/connectors-creating.md) e escolha *Salvar*.

  ![A caixa de diálogo Adicionar uma guia, com uma galeria de guias disponíveis.](../../assets/images/connector_gallery.png)

## <a name="accessing-your-uploaded-messaging-extension"></a>Acessando sua extensão de mensagens carregada

Um aplicativo carregado com uma extensão de mensagens aparece automaticamente no menu Mais opções *(* *&#8943;*) na caixa de redação.

![Extensões de mensagens](../../assets/images/compose-extensions/cesampleapp.png)

## <a name="removing-or-updating-your-app"></a>Removendo ou atualizando seu aplicativo

Se você quiser remover seu aplicativo, selecione o ícone de lixeira ao lado do nome do aplicativo na lista de bots do View Teams.

Se você alterar as informações do manifesto, primeiro remova o aplicativo e, em seguida, adicione o pacote atualizado (de acordo com o carregamento do [pacote em uma equipe).](#load-your-package-into-teams) Observe que, em geral, as alterações de código em seu serviço não exigem que você recarde o manifesto, a menos que essas alterações recarram as atualizações do manifesto (como alterações na URL ou na ID do aplicativo da Microsoft para seu bot).

> [!NOTE]
> Não há nenhuma maneira de remover completamente um bot do contexto pessoal. Se o bot for removido e adicionado outra vez, a comunicação adicional com o bot será acrescentada à conversa anterior.

## <a name="troubleshooting-notes"></a>Notas de solução de problemas

* Se o manifesto não carregar, verifique se você seguiu [](../../concepts/build-and-test/apps-package.md) todas as instruções em Criar o pacote e validou seu manifesto em relação [ao esquema.](../../resources/schema/manifest-schema.md)
