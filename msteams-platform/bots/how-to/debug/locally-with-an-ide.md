---
title: Testar e depurar seu bot localmente
author: surbhigupta
description: Saiba mais sobre como testar e depurar seu bot localmente com um IDE no ambiente do Teams por meio de sideload e muito mais.
ms.topic: overview
ms.localizationpriority: medium
ms.author: anclear
ms.openlocfilehash: c2b68279000da27aa055e591bcccc0a91e7f3769
ms.sourcegitcommit: 69a45722c5c09477bbff3ba1520e6c81d2d2d997
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/11/2022
ms.locfileid: "67312202"
---
# <a name="test-and-debug-your-bot-locally-with-ide"></a>Testar e depurar seu bot localmente com o IDE

Ao testar seu bot, você precisa considerar os contextos em que deseja que o bot seja executado e qualquer funcionalidade que possa ter adicionado ao bot que exija dados específicos do Microsoft Teams. Verifique se o método escolhido para testar o bot está alinhado com sua funcionalidade.

## <a name="test-by-uploading-to-teams"></a>Testar carregando no Teams

A maneira mais abrangente de testar seu bot é criando um pacote de aplicativos e carregando-o no Teams. Carregar o pacote do aplicativo no Teams é o único método para testar a funcionalidade completa disponível para o bot em todos os escopos.

Há dois métodos para carregar seu aplicativo:

* Use [o Portal do Desenvolvedor para o Teams](~/concepts/build-and-test/teams-developer-portal.md).
* [Criar um pacote do aplicativo](~/concepts/build-and-test/apps-package.md) manualmente e, em seguida, [carregue seu aplicativo](~/concepts/deploy-and-publish/apps-upload.md).

> [!NOTE]
> Para alterar o manifesto e carregar novamente seu aplicativo, [exclua o bot](#delete-a-bot-from-teams) antes de carregar o pacote do aplicativo alterado.
> Para testar o bot, habilite o sideload no Teams. Consulte [Habilitar o sideload](/microsoftteams/platform/concepts/build-and-test/prepare-your-o365-tenant#enable-custom-teams-apps-and-turn-on-custom-app-uploading).

## <a name="debug-your-bot-locally"></a>Depurar seu bot localmente

Se estiver hospedando seu bot localmente durante o desenvolvimento, precisará usar um serviço de túnel como o [ngrok](https://ngrok.com/) para testar o bot. Depois de baixar e instalar o ngrok, adicione `ngrok` ao caminho e execute o seguinte comando para iniciar o serviço de túnel:

```bash
ngrok http <port> --host-header=localhost:<port>
```

Use o ponto de extremidade https fornecido pelo ngrok no manifesto do aplicativo.

> [!NOTE]
> Se você fechar a janela de comando e reiniciar, uma nova URL será gerada e você precisará atualizar o endereço do ponto de extremidade do bot para usá-la.

## <a name="test-your-bot-without-uploading-to-teams"></a>Testando seu bot sem carregar no Teams

Ocasionalmente, é necessário testar seu bot sem instalá-lo como um aplicativo no Teams. Fornecemos dois métodos para teste. Testar o bot sem instalá-lo como um aplicativo pode ser útil para garantir que o bot esteja disponível e respondendo. No entanto, ele não permitirá que você teste toda a amplitude da funcionalidade do Microsoft Teams que você adicionou ao seu bot. Se quiser testar totalmente seu bot, confira [testar carregando](#test-by-uploading-to-teams).

### <a name="use-the-bot-emulator"></a>Usar o Bot Emulator

O Bot Framework Emulator é um aplicativo da área de trabalho que permite aos desenvolvedores de bot testar e depurar seus bots, localmente ou remotamente. Usando o emulador, você pode conversar com seu bot e inspecionar as mensagens que seu bot envia e recebe. Isso é útil para verificar se o bot está disponível e respondendo. No entanto, o emulador não permite testar nenhuma funcionalidade específica do Teams que você adicionou ao bot, nem as respostas do bot são uma representação visual precisa de como elas serão renderizadas no Teams. Se precisar testar qualquer uma dessas opções, é melhor [carregar seu bot](#test-by-uploading-to-teams).

Para obter mais informações, consulte [instruções completas sobre o Bot Framework Emulator](/azure/bot-service/bot-service-debug-emulator?view=azure-bot-service-4.0&preserve-view=true).

### <a name="talk-to-your-bot-directly-by-id"></a>Fale com seu bot diretamente por ID

> [!Important]
> Conversar com seu bot por ID destina-se apenas para fins de teste. Qualquer funcionalidade específica do Teams que você adicionou ao bot não funcionará.

Inicie uma conversa com seu bot usando sua ID. Quando um bot é adicionado por meio de um desses métodos, ele não é enderecável em conversas de canal e você não pode aproveitar outros recursos de aplicativo do Teams, como guias ou extensões de mensagem. Inicie uma conversa de uma das seguintes maneiras:

* Na página [Painel de bot](https://dev.botframework.com/bots) para seu o bot, em **Canais**, selecione **Adicionar ao Microsoft Teams**. O Teams inicia um chat pessoal com seu bot.

* Faça referência direta à ID do aplicativo do bot de dentro do Teams:
   1. Na página [Painel do bot](https://dev.botframework.com/bots) para seu bot, em **Detalhes**, copie a **ID do aplicativo da Microsoft** para o bot.
  
      ![Obtendo o AppID para o bot](~/assets/images/bots_appid_botframework.png)
  
   2. Abra o Microsoft Teams, no painel Chat, seleciona o **ícone Adicionar chat** . Em **Para**, cole a ID do aplicativo da Microsoft do seu bot.
  
      ![Carregando bots](~/assets/images/bots_uploading.png)

      A ID do aplicativo deve ser resolvida para o nome do bot.

   3. Selecione seu bot e envie uma mensagem para iniciar uma conversa.
      Como alternativa, você pode colar a ID do aplicativo do bot na caixa de pesquisa no canto superior esquerdo do Teams. Na página de resultados da pesquisa, vá para a guia **Pessoas** para ver seu bot e começar a conversar com ele.

> [!Note]
> Para o Teams fazer referência à ID do aplicativo do bot, habilite [o sideload de aplicativos](/microsoftteams/platform/concepts/build-and-test/prepare-your-o365-tenant#enable-custom-teams-apps-and-turn-on-custom-app-uploading).

Seu bot recebe o evento `conversationUpdate` à medida que você adiciona os bots a uma equipe, sem as informações da equipe no objeto `channelData`.

## <a name="block-a-bot-in-personal-chat"></a>Bloquear um bot no chat pessoal

Observe que os usuários podem optar por impedir que seu bot envie mensagens de chat pessoais. Eles podem alternar isso clicando com o botão direito do mouse no bot no canal de chat e escolhendo **Bloquear conversas com bot**. Isso significa que os bots continuam a enviar mensagens, no entanto, o usuário não recebe as mensagens.

![Bloqueando um bot](~/assets/images/bots/botdisable.png)

## <a name="remove-a-bot-from-a-team"></a>Remover um bot de uma equipe

Os usuários podem excluir o bot escolhendo o ícone de lixeira na lista de bots no modo de exibição de equipes. Isso remove apenas o bot do uso dessa equipe. Os usuários individuais ainda podem interagir no contexto pessoal. Os bots no contexto pessoal não podem ser desabilitados ou removidos pelos usuários.

## <a name="disable-a-bot-in-teams"></a>Desabilitar um bot no Teams

Para impedir que o bot receba mensagens, vá para o **Painel do Bot** e edite o canal do Teams. Desmarque a opção **Habilitar no Microsoft Teams**. Isso impede que os usuários interajam com o bot, no entanto, ele ainda será detectável e os usuários poderão adicioná-lo ao Teams.

## <a name="delete-a-bot-from-teams"></a>Excluir um bot do Teams

Para remover completamente o bot do Teams, acesse o **Painel do Bot** e edite o canal do Teams. Escolha o botão **Excluir** na parte inferior. Excluir um bot do Teams impede que os usuários descubram, adicionem e interajam com seu bot. A exclusão de um bot do Teams não remove o bot das instâncias do Teams de outro usuário, no entanto, ele também para de funcionar para eles.

## <a name="see-also"></a>Confira também

* [Depurar o bot com o middleware de inspeção](/azure/bot-service/bot-service-debug-inspection-middleware)
* [Depurar seus chamados e o bot de reunião localmente](~/bots/calls-and-meetings/debugging-local-testing-calling-meeting-bots.md)
