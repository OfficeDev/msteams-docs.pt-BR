---
title: Testar e depurar seu bot localmente
author: surbhigupta
description: Saiba mais sobre como testar e depurar seu bot localmente com um IDE no ambiente do Teams por meio do sideload, fora do Teams usando o Bot Emulador e falando diretamente com seu bot.
ms.topic: overview
ms.localizationpriority: medium
ms.author: anclear
ms.openlocfilehash: da6e04e4df8824f4dc13d63e0aa4cd5bb6afb48a
ms.sourcegitcommit: 430bf416bb8d1b74f926c8b5d5ffd3dbb0782286
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/10/2022
ms.locfileid: "65297223"
---
# <a name="test-and-debug-your-bot-locally"></a>Testar e depurar seu bot localmente

Ao testar o bot, você precisa considerar os contextos em que deseja que o bot seja executado, bem como qualquer funcionalidade que você tenha adicionado ao bot que exija dados específicos do Microsoft Teams. Verifique se o método escolhido para testar o bot está alinhado com sua funcionalidade.

## <a name="test-by-uploading-to-teams"></a>Testar carregando no Teams

A maneira mais abrangente de testar seu bot é criando um pacote de aplicativos e carregando-o no Teams. Esse é o único método para testar a funcionalidade completa disponível para seu bot, em todos os escopos.

Há dois métodos para carregar seu aplicativo:

* Use o [App Studio](~/concepts/build-and-test/app-studio-overview.md).
* [Criar um pacote do aplicativo](~/concepts/build-and-test/apps-package.md) manualmente e, em seguida, [carregue seu aplicativo](~/concepts/deploy-and-publish/apps-upload.md).

> [!NOTE]
> Para alterar o manifesto e carregar novamente seu aplicativo, [exclua o bot](#delete-a-bot-from-teams) antes de carregar o pacote do aplicativo alterado.
> Para testar o bot, habilite o sideload no Teams. Consulte [Habilitar o sideload](/microsoftteams/platform/concepts/build-and-test/prepare-your-o365-tenant#enable-custom-teams-apps-and-turn-on-custom-app-uploading).

## <a name="debug-your-bot-locally"></a>Depurar seu bot localmente

Se estiver hospedando seu bot localmente durante o desenvolvimento, precisará usar um serviço de túnel como o [ngrok](https://ngrok.com/) para testar o bot. Depois de baixar e instalar o ngrok, adicione `ngrok` ao caminho e execute o seguinte comando para iniciar o serviço de túnel:

```bash
ngrok http <port> -host-header=localhost:<port>
```

Use o ponto de extremidade https fornecido pelo ngrok no manifesto do aplicativo.

> [!NOTE]
> Se você fechar a janela de comando e reiniciar, uma nova URL será gerada e você precisará atualizar o endereço do ponto de extremidade do bot para usá-la.

## <a name="test-your-bot-without-uploading-to-teams"></a>Testando seu bot sem carregar no Teams

Ocasionalmente, é necessário testar seu bot sem instalá-lo como um aplicativo no Teams. Fornecemos dois métodos para teste. Testar o bot sem instalá-lo como um aplicativo pode ser útil para garantir que o bot esteja disponível e respondendo, no entanto, ele não permitirá testar toda a amplitude da funcionalidade do Microsoft Teams que você adicionou ao bot. Se quiser testar totalmente seu bot, confira [testar carregando](#test-by-uploading-to-teams).

### <a name="use-the-bot-emulator"></a>Usar o Bot Emulator

O Bot Framework Emulator é um aplicativo da área de trabalho que permite aos desenvolvedores de bot testar e depurar seus bots, localmente ou remotamente. Usando o emulador, você pode conversar com seu bot e inspecionar as mensagens que seu bot envia e recebe. Isso é útil para verificar se o bot está disponível e respondendo. No entanto, o emulador não permite testar nenhuma funcionalidade específica do Teams que você adicionou ao bot, nem as respostas do bot são uma representação visual precisa de como elas serão renderizadas no Teams. Se precisar testar qualquer uma dessas opções, é melhor [carregar seu bot](#test-by-uploading-to-teams).

Para obter mais informações, consulte [instruções completas sobre o Bot Framework Emulator](/azure/bot-service/bot-service-debug-emulator?view=azure-bot-service-4.0&preserve-view=true).

### <a name="talk-to-your-bot-directly-by-id"></a>Fale com seu bot diretamente por ID

> [!Important]
> Conversar com seu bot por ID destina-se apenas para fins de teste. Qualquer funcionalidade específica do Teams que você adicionou ao bot não funcionará.

Inicie uma conversa com seu bot usando sua ID. Quando um bot é adicionado por meio de um desses métodos, ele não será endereçável em conversas de canal e você não poderá aproveitar outros recursos de aplicativo do Microsoft Teams, como guias ou extensões de mensagem. Você pode iniciar uma conversa de uma das seguintes maneiras:

* Na página [Painel de bot](https://dev.botframework.com/bots) para seu o bot, em **Canais**, selecione **Adicionar ao Microsoft Teams**. O Microsoft Teams inicia um chat pessoal com seu bot.

* Faça referência direta à ID do aplicativo do bot de dentro do Microsoft Teams:
   1. Na página [Painel do bot](https://dev.botframework.com/bots) para seu bot, em **Detalhes**, copie a **ID do aplicativo da Microsoft** para o bot.
  
      ![Obtendo o AppID para o bot](~/assets/images/bots_appid_botframework.png)
  
   2. No Microsoft Teams, no painel de **Chat**, selecione o **ícone Adicionar chat**. Em **Para**, cole a ID do aplicativo da Microsoft do seu bot.
  
      ![Carregando bots](~/assets/images/bots_uploading.png)

      A ID do aplicativo deve ser resolvida para o nome do bot.

   3. Selecione seu bot e envie uma mensagem para iniciar uma conversa.
      Como alternativa, você pode colar a ID do aplicativo do bot na caixa de pesquisa no canto superior esquerdo do Microsoft Teams. Na página de resultados da pesquisa, vá para a guia **Pessoas** para ver seu bot e começar a conversar com ele.

> [!Note]
> Para que o Microsoft Teams faça referência à ID do aplicativo do bot, habilite [sideload de aplicativos](/microsoftteams/platform/concepts/build-and-test/prepare-your-o365-tenant#enable-custom-teams-apps-and-turn-on-custom-app-uploading).

Seu bot recebe o evento `conversationUpdate` à medida que você adiciona os bots a uma equipe, sem as informações da equipe no objeto `channelData`.

## <a name="block-a-bot-in-personal-chat"></a>Bloquear um bot no chat pessoal

Observe que os usuários podem optar por impedir que seu bot envie mensagens de chat pessoais. Eles podem alternar isso clicando com o botão direito do mouse no bot no canal de chat e escolhendo **Bloquear conversas com bot**. Isso significa que seus bots continuam enviando mensagens, no entanto, o usuário não as recebe.

![Bloqueando um bot](~/assets/images/bots/botdisable.png)

## <a name="remove-a-bot-from-a-team"></a>Remover um bot de uma equipe

Os usuários podem excluir o bot escolhendo o ícone de lixeira na lista de bots no modo de exibição de equipes. Observe que isso apenas remove o bot do uso dessa equipe, os usuários individuais podem interagir no contexto pessoal. Os bots no contexto pessoal não podem ser desabilitados ou removidos pelos usuários.

## <a name="disable-a-bot-in-teams"></a>Desabilitar um bot no Teams

Para impedir que o bot receba mensagens, vá para o **Painel do Bot** e edite o canal do Teams. Desmarque a opção **Habilitar no Microsoft Teams**. Isso impede que os usuários interajam com o bot, no entanto, ele ainda será detectável e os usuários poderão adicioná-lo ao Teams.

## <a name="delete-a-bot-from-teams"></a>Excluir um bot do Teams

Para remover completamente o bot do Teams, acesse o **Painel do Bot** e edite o canal do Teams. Escolha o botão **Excluir** na parte inferior. Isso impede que os usuários descubram, adicionem ou interajam com seu bot. Isso não remove o bot das instâncias do Teams de outros usuários, no entanto, ele para de funcionar para eles também.

## <a name="see-also"></a>Confira também

* [Depurar o bot com o middleware de inspeção](/azure/bot-service/bot-service-debug-inspection-middleware)
* [Depurar seus chamados e o bot de reunião localmente](~/bots/calls-and-meetings/debugging-local-testing-calling-meeting-bots.md)
