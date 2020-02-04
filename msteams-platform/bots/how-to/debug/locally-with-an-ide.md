---
title: Testar e depurar o bot localmente
author: clearab
description: Testando e Depurando o bot localmente com um IDE
ms.topic: overview
ms.author: anclear
ms.openlocfilehash: 8494302b41e33910cb33f8c6889d82505b703577
ms.sourcegitcommit: 4329a94918263c85d6c65ff401f571556b80307b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/01/2020
ms.locfileid: "41672586"
---
# <a name="test-and-debug-your-bot-locally"></a>Testar e depurar o bot localmente

Ao testar o bot, você precisa levar em consideração o (s) contexto (es) em que deseja que o bot seja executado, bem como qualquer funcionalidade que você possa ter adicionado ao bot que exija dados específicos do Microsoft Teams. Certifique-se de que o método escolhido para testar o bot se alinhe com sua funcionalidade.

## <a name="test-by-uploading-to-teams"></a>Testar carregando para o Microsoft Teams

A maneira mais abrangente de testar o bot é criando um pacote de aplicativos e carregando-o para o Microsoft Teams. Este é o único método para testar a funcionalidade completa disponível para o bot, em todos os escopos.

Há dois métodos para carregar seu aplicativo. Você pode usar o [app Studio](~/concepts/build-and-test/app-studio-overview.md) para ajudá-lo ou pode [criar um pacote de aplicativos](~/concepts/build-and-test/apps-package.md) manualmente e [carregar o aplicativo](~/concepts/deploy-and-publish/apps-upload.md). Se você precisar alterar seu manifesto e recarregar seu aplicativo, você deve [excluir seu bot](#deleting-a-bot-from-teams) antes de carregar seu pacote de aplicativos alterado.

## <a name="debug-your-bot-locally"></a>Depurar seu bot localmente

Se você estiver hospedando o bot localmente durante o desenvolvimento, será necessário usar um serviço de encapsulamento como o [ngrok](https://ngrok.com/) para testar o bot. Depois de baixar e instalar o ngrok, execute o comando a seguir para iniciar o serviço de encapsulamento (talvez seja necessário adicionar o ngrok ao seu caminho).

```bash
ngrok http <port> -host-header=localhost:<port>
```

Use o ponto de extremidade https fornecido pelo ngrok em seu manifesto de aplicativo. Se você fechar a janela de comando e reiniciar, receberá uma nova URL e será necessário atualizar o endereço do ponto de extremidade do bot para usá-la também.

## <a name="testing-your-bot-without-uploading-to-teams"></a>Testando o bot sem carregar no Teams

Ocasionalmente, talvez seja necessário testar o bot sem instalá-lo como um aplicativo no Teams. Fornecemos dois métodos para fazer isso abaixo. Testar seu bot sem instalá-lo como um aplicativo pode ser útil para garantir que seu bot esteja disponível e respondendo, no entanto, ele não permitirá que você teste toda a abrangência da funcionalidade do Microsoft Teams que você pode ter adicionado ao bot. Se você precisar testar totalmente seu bot, siga as instruções para testar o [carregamento](#test-by-uploading-to-teams).

### <a name="use-the-bot-emulator"></a>Usar o emulador de bot

O emulador de estrutura de bot é um aplicativo de área de trabalho que permite que os desenvolvedores de bot testem e depurem seus bots, local ou remotamente. Usando o emulador, você pode bater papo com o bot e inspecionar as mensagens que o seu bot envia e recebe. Isso pode ser útil para verificar se o seu bot está disponível e respondendo, no entanto, o emulador não permitirá que você teste qualquer funcionalidade específica da equipe que você adicionou ao bot, nem as respostas do seu bot serão uma representação visual precisa de como eles serão ser renderizado no Teams. Se você precisar testar qualquer um desses itens, é melhor [carregar seu bot](#test-by-uploading-to-teams).

Instruções completas sobre o emulador da estrutura do bot podem ser encontradas [aqui](/azure/bot-service/bot-service-debug-emulator?view=azure-bot-service-4.0).

### <a name="talk-to-your-bot-directly-by-id"></a>Fale com o seu bot diretamente pela ID

>[!Important]
>Falar com o bot por ID é destinado apenas para fins de teste básicos. Qualquer funcionalidade específica da equipe que você adicionou ao bot não funcionará.

Você também pode iniciar uma conversa com o bot usando sua ID. Dois métodos para isso são fornecidos abaixo. Quando um bot foi adicionado por meio de um desses métodos, ele não será endereçável em conversas de canal e você não poderá aproveitar outros recursos do aplicativo Microsoft Teams, como guias ou extensões de mensagens.

1. Na página do [painel de bot](https://dev.botframework.com/bots) do bot, em **canais**, selecione **Adicionar ao Microsoft Teams**. O Microsoft Teams será iniciado com um chat pessoal com o bot.
2. Faça referência direta à ID de aplicativo do bot no Microsoft Teams:
   * Na página do [painel de bot](https://dev.botframework.com/bots) do bot, em **detalhes**, copie a **ID do aplicativo da Microsoft** para o bot.
  
     ![Obtendo a AppID do bot](~/assets/images/bots_appid_botframework.png)
  
   * No Microsoft Teams, no painel **chat** , selecione o ícone **Adicionar chat** . Para **:**, Cole a ID do aplicativo da Microsoft de seu bot.
  
     ![Obtendo a AppID do bot](~/assets/images/bots_uploading.png)

     A ID do aplicativo deve resolver o nome do seu bot.

   * Selecione seu bot e envie uma mensagem para iniciar uma conversa.
   * Como alternativa, você pode colar a ID de aplicativo do bot na caixa de pesquisa no canto superior esquerdo do Microsoft Teams. Na página de resultados da pesquisa, navegue até a guia pessoas para ver o bot e começar a conversar com ele.

O bot receberá o `conversationUpdate` evento exatamente como os bots adicionados a uma equipe, mas sem as informações da equipe `channelData` no objeto.

## <a name="blocking-a-bot-in-personal-chat"></a>Bloqueando um bot no chat pessoal

Observe que os usuários podem optar por bloquear o envio de mensagens de chat pessoais de seu bot. Eles podem alternar isso clicando com o botão direito do mouse no seu bot no canal de chat e escolhendo **Bloquear conversa de bot**. Isso significa que seus bots continuarão a enviar mensagens, mas o usuário não receberá essas mensagens.

![Bloqueando um bot](~/assets/images/bots/botdisable.png)

## <a name="removing-a-bot-from-a-team"></a>Remover um bot de uma equipe

Os usuários podem excluir o bot escolhendo o ícone Trash-can na lista de bots no modo de exibição do teams. Observe que isso apenas remove o bot do uso da equipe; os usuários individuais ainda poderão interagir no contexto pessoal.

Os bots no contexto pessoal não podem ser desabilitados ou removidos por um usuário, de forma abreviada de remover completamente o bot do Microsoft Teams.

## <a name="disabling-a-bot-in-teams"></a>Desabilitar um bot no Teams

Para interromper o recebimento de mensagens, vá para o painel do bot e edite o canal do Microsoft Teams. Desmarque a opção **habilitar no Microsoft Teams** . Isso impede que os usuários interajam com o bot, mas ele ainda será detectável, e os usuários ainda poderão adicioná-lo ao Microsoft Teams.

## <a name="deleting-a-bot-from-teams"></a>Excluindo um bot do Microsoft Teams

Para remover seu bot completamente do Teams, vá para o painel de bot e edite o canal do Microsoft Teams. Escolha o botão **excluir** na parte inferior. Isso impede que os usuários descubram, adicionem ou interajam com seu bot. Observe que isso não remove o bot das instâncias de outras equipes de outros usuários, embora ele pare de funcionar também.
