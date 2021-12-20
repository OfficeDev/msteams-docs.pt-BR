---
title: Testar e depurar seu bot localmente
author: surbhigupta
description: Saiba mais sobre como testar e depurar seu bot localmente com um IDE em um ambiente Teams por meio de sideload, fora do Teams usando o emulador bot e conversando diretamente com seu bot.
ms.topic: overview
ms.localizationpriority: medium
ms.author: anclear
ms.openlocfilehash: 087c18998df0a24470da8059eb107343588c3aa0
ms.sourcegitcommit: a2d7d2bdf4b056b35f29c6fdb315bc7dc28b6f6f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/20/2021
ms.locfileid: "61569571"
---
# <a name="test-and-debug-your-bot-locally"></a>Testar e depurar seu bot localmente

Ao testar seu bot, você precisa levar em consideração os contextos em que deseja que seu bot seja executado e qualquer funcionalidade que você possa ter adicionado ao bot que exija dados específicos para Microsoft Teams. Certifique-se de que o método escolhido para testar seu bot se alinhe com sua funcionalidade.

## <a name="test-by-uploading-to-teams"></a>Teste carregando no Teams

A maneira mais abrangente de testar seu bot é criando um pacote de aplicativos e carregando-o para Teams. Este é o único método para testar a funcionalidade completa disponível para o bot, em todos os escopos.

Há dois métodos para carregar seu aplicativo:

* Use [o App Studio](~/concepts/build-and-test/app-studio-overview.md).
* [Crie um pacote de aplicativo](~/concepts/build-and-test/apps-package.md) manualmente e carregue seu [aplicativo](~/concepts/deploy-and-publish/apps-upload.md).

> [!NOTE]
> Para alterar o manifesto e carregar seu aplicativo de novo, [exclua](#delete-a-bot-from-teams) o bot antes de carregar o pacote de aplicativo alterado.
> Para testar o bot, habilita o sideload em Teams. Consulte [habilitar sideloading](/concepts/build-and-test/prepare-your-o365-tenant#enable-custom-teams-apps-and-turn-on-custom-app-uploading).

## <a name="debug-your-bot-locally"></a>Depurar seu bot localmente

Se você estiver hospedando seu bot localmente durante o desenvolvimento, precisará usar um serviço de túnel como [o ngrok](https://ngrok.com/) para testar seu bot. Depois de baixar e instalar o ngrok, adicione ao seu caminho e execute o seguinte comando `ngrok` para iniciar o serviço de túnel:

```bash
ngrok http <port> -host-header=localhost:<port>
```

Use o ponto de extremidade https fornecido pelo ngrok no manifesto do aplicativo.

> [!NOTE]
> Se você fechar a janela de comando e reiniciar, uma nova URL será gerada e você precisará atualizar seu endereço de ponto de extremidade do bot para usá-la.

## <a name="test-your-bot-without-uploading-to-teams"></a>Teste seu bot sem carregar no Teams

Ocasionalmente, pode ser necessário testar seu bot sem instalá-lo como um aplicativo Teams. Fornecemos dois métodos para testar o bot. Testar seu bot sem instalá-lo como um aplicativo pode ser útil para garantir que o bot está disponível e respondendo, no entanto, ele não permitirá que você teste a amplitude completa da funcionalidade Microsoft Teams que você pode ter adicionado ao bot. Se você precisar testar totalmente seu bot, consulte [testando carregando](#test-by-uploading-to-teams).

### <a name="use-the-bot-emulator"></a>Use o bot Emulator

O Bot Framework Emulator é um aplicativo de área de trabalho que permite aos desenvolvedores de bot testar e depurar seus bots localmente ou remotamente. O emulador ajuda você a conversar com seu bot e inspecionar as mensagens que seu bot envia e recebe. Isso pode ser útil para verificar se o bot está disponível e respondendo. No entanto, o emulador não permite que você teste nenhuma funcionalidade específica Teams que você adicionou ao bot, nem as respostas do bot são uma representação visual precisa de como elas são renderizadas Teams. Se você precisar testar qualquer uma dessas coisas, é melhor [carregar seu bot](#test-by-uploading-to-teams).

Para obter mais informações, [consulte instruções completas sobre o Bot Framework Emulator](/azure/bot-service/bot-service-debug-emulator?view=azure-bot-service-4.0&preserve-view=true).

### <a name="talk-to-your-bot-directly-by-id"></a>Fale com seu bot diretamente por ID

> [!Important]
> Conversar com seu bot por ID destina-se apenas a fins de teste básicos. Qualquer Teams funcionalidade específica que você adicionou ao bot não funciona.

Você também pode iniciar uma conversa com seu bot usando sua ID. Quando um bot é adicionado por meio de um desses métodos, ele não pode ser abordada em conversas de canal e você não pode tirar proveito de outros recursos Microsoft Teams aplicativos, como guias ou extensões de mensagens. Você pode iniciar uma conversa de uma das seguintes maneiras:

* Na página [Painel de Bot](https://dev.botframework.com/bots) para seu bot, em **Canais,** selecione **Adicionar a Microsoft Teams**. Microsoft Teams inicia um chat pessoal com seu bot.

* Fazer referência direta à ID do aplicativo do bot de dentro Microsoft Teams:
   1. Na página [Painel de Bot](https://dev.botframework.com/bots) para seu bot, em **Detalhes**, copie a **ID** do Aplicativo microsoft para seu bot.
  
      ![Obter o AppID para o bot](~/assets/images/bots_appid_botframework.png)
  
   2. Abra Microsoft Teams, no painel **Chat,** selecione o ícone **Adicionar chat.** Em **Para:**, colar a ID do aplicativo Microsoft do seu bot.
  
      ![Carregando bots](~/assets/images/bots_uploading.png)

      A ID do aplicativo deve ser resolvida com o nome do bot.

   3. Selecione seu bot e envie uma mensagem para iniciar uma conversa.
      Como alternativa, você pode colar a ID do aplicativo do bot na caixa de pesquisa na parte superior esquerda Microsoft Teams. Na página resultados da pesquisa, navegue até a guia **Pessoas** para ver seu bot e começar a conversar com ele.

Seu bot recebe o `conversationUpdate` evento à medida que você adiciona os bots a uma equipe, sem as informações da equipe no `channelData` objeto.

## <a name="block-a-bot-in-personal-chat"></a>Bloquear um bot no chat pessoal

Os usuários podem optar por impedir que seu bot envie mensagens de chat pessoais. Eles podem alternar isso clicando com o botão direito do mouse no bot no canal de chat e escolhendo **Bloquear conversa bot**. Isso significa que seus bots continuam a enviar mensagens, no entanto, o usuário não recebe as mensagens.

![Bloqueando um bot](~/assets/images/bots/botdisable.png)

## <a name="remove-a-bot-from-a-team"></a>Remover um bot de uma equipe

Os usuários podem excluir o bot escolhendo o ícone de lixeira na lista de bots no ponto de vista da equipe. Isso remove apenas o bot do uso dessa equipe, os usuários individuais ainda podem interagir no contexto pessoal. Os bots no contexto pessoal não podem ser desabilitados ou removidos pelos usuários.

## <a name="disable-a-bot-in-teams"></a>Desabilitar um bot no Teams

Para impedir que seu bot receba mensagens, vá para o Painel de **Bot** e edite o canal Microsoft Teams de bot. **Desativer a opção Habilitar Microsoft Teams.** Isso impede que os usuários interajam com o bot, no entanto, ele ainda será descoberto e os usuários ainda poderão adicioná-lo ao Teams.

## <a name="delete-a-bot-from-teams"></a>Excluir um bot do Teams

Para remover completamente o bot do Teams, vá para o Painel de **Bot** e edite o Microsoft Teams canal. Escolha o **botão Excluir** na parte inferior. Isso impede que os usuários descubram, adicionem e interajam com seu bot. Isso não remove o bot das instâncias de Teams outros usuários, no entanto, ele também deixa de funcionar para eles.

## <a name="see-also"></a>Confira também

* [Depurar o bot com o middleware de inspeção](/azure/bot-service/bot-service-debug-inspection-middleware)
* [Depurar seus chamados e o bot de reunião localmente](~/bots/calls-and-meetings/debugging-local-testing-calling-meeting-bots.md)
