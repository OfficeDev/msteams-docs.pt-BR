---
title: Testar e depurar seu bot localmente
author: surbhigupta
description: Saiba mais sobre como testar e depurar seu bot localmente com um IDE dentro do ambiente do Teams por meio do sideload, fora do Teams usando o bot emulador e conversando diretamente com o bot.
ms.topic: overview
ms.localizationpriority: medium
ms.author: anclear
ms.openlocfilehash: a673f1cd260c9b53de477cdd5084bd521c79bd41
ms.sourcegitcommit: 0117c4e750a388a37cc189bba8fc0deafc3fd230
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65103983"
---
# <a name="test-and-debug-your-bot-locally"></a>Testar e depurar seu bot localmente

Ao testar seu bot, você precisa levar em consideração os contextos nos quais deseja que o bot seja executado e qualquer funcionalidade que você possa ter adicionado ao bot que exija dados específicos do Microsoft Teams. Verifique se o método escolhido para testar o bot está alinhado com sua funcionalidade.

## <a name="test-by-uploading-to-teams"></a>Testar carregando no Teams

A maneira mais abrangente de testar seu bot é criando um pacote de aplicativos e carregando-o para Teams. Esse é o único método para testar a funcionalidade completa disponível para o bot em todos os escopos.

Há dois métodos para carregar seu aplicativo:

* Use [o App Studio](~/concepts/build-and-test/app-studio-overview.md).
* [Crie um pacote de aplicativo](~/concepts/build-and-test/apps-package.md) manualmente e carregue [seu aplicativo](~/concepts/deploy-and-publish/apps-upload.md).

> [!NOTE]
> Para alterar o manifesto e carregar novamente seu aplicativo, [exclua o bot](#delete-a-bot-from-teams) antes de carregar o pacote do aplicativo alterado.
> Para testar o bot, habilite o sideload em Teams. Consulte [habilitar o sideload](/microsoftteams/platform/concepts/build-and-test/prepare-your-o365-tenant#enable-custom-teams-apps-and-turn-on-custom-app-uploading).

## <a name="debug-your-bot-locally"></a>Depurar o bot localmente

Se você estiver hospedando seu bot localmente durante o desenvolvimento, precisará usar um serviço de túnel como [o ngrok](https://ngrok.com/) para testar o bot. Depois de baixar e instalar o ngrok, adicione `ngrok` ao caminho e execute o seguinte comando para iniciar o serviço de túnel:

```bash
ngrok http <port> -host-header=localhost:<port>
```

Use o ponto de extremidade https fornecido pelo ngrok no manifesto do aplicativo.

> [!NOTE]
> Se você fechar a janela de comando e reiniciar, uma nova URL será gerada e você precisará atualizar o endereço do ponto de extremidade do bot para usá-la.

## <a name="test-your-bot-without-uploading-to-teams"></a>Testar o bot sem carregar no Teams

Ocasionalmente, pode ser necessário testar seu bot sem instalá-lo como um aplicativo no Teams. Fornecemos dois métodos para testar o bot. Testar o bot sem instalá-lo como um aplicativo pode ser útil para garantir que o bot esteja disponível e respondendo Microsoft Teams, no entanto, ele não permitirá que você teste a amplitude completa da funcionalidade que você pode ter adicionado ao bot. Se você precisar testar totalmente o bot, confira [o teste carregando](#test-by-uploading-to-teams).

### <a name="use-the-bot-emulator"></a>Usar o bot Emulator

O Bot Framework Emulator é um aplicativo da área de trabalho que permite que os desenvolvedores de bot testem e depurem seus bots localmente ou remotamente. O emulador ajuda você a conversar com seu bot e inspecionar as mensagens que seu bot envia e recebe. Isso pode ser útil para verificar se o bot está disponível e respondendo. No entanto, o emulador não permite que você teste nenhuma funcionalidade específica do Teams que você adicionou ao bot, nem as respostas do bot são uma representação visual precisa de como elas são renderizadas no Teams. Se você precisar testar qualquer uma dessas coisas, é melhor [carregar o bot](#test-by-uploading-to-teams).

Para obter mais informações, [consulte instruções completas sobre o Bot Framework Emulator](/azure/bot-service/bot-service-debug-emulator?view=azure-bot-service-4.0&preserve-view=true).

### <a name="talk-to-your-bot-directly-by-id"></a>Fale com seu bot diretamente por ID

> [!Important]
> Conversar com seu bot por ID destina-se apenas a fins de teste básicos. Qualquer Teams funcionalidade específica que você adicionou ao bot não funcionará.

Você também pode iniciar uma conversa com o bot usando sua ID. Quando um bot é adicionado por meio de um desses métodos, ele não é enderecável em conversas de canal e você não pode aproveitar outras funcionalidades do aplicativo Microsoft Teams como guias ou extensões de mensagem. Você pode iniciar uma conversa de uma das seguintes maneiras:

* Na página [Painel de Bot](https://dev.botframework.com/bots) do bot, em **Canais**, selecione **Adicionar ao Microsoft Teams**. Microsoft Teams inicia um chat pessoal com seu bot.

* Faça referência direta à ID do aplicativo do bot de dentro Microsoft Teams:
   1. Na página [Painel do Bot](https://dev.botframework.com/bots) do bot, em **Detalhes**, copie a **ID do Aplicativo microsoft** para o bot.
  
      ![Obtendo o AppID para o bot](~/assets/images/bots_appid_botframework.png)
  
   2. Abra Microsoft Teams, no painel **Chat**, selecione o ícone **Adicionar chat**. Em **Para:**, cole a ID do aplicativo Microsoft do bot.
  
      ![Carregando bots](~/assets/images/bots_uploading.png)

      A ID do aplicativo deve ser resolvida para o nome do bot.

   3. Selecione seu bot e envie uma mensagem para iniciar uma conversa.
      Como alternativa, você pode colar a ID do aplicativo do bot na caixa de pesquisa na parte superior esquerda Microsoft Teams. Na página de resultados da pesquisa, navegue até **a guia Pessoas** para ver seu bot e começar a conversar com ele.

> [!Note]
> Para Microsoft Teams consultar a ID do aplicativo do bot, habilite o [sideload de aplicativos](/microsoftteams/platform/concepts/build-and-test/prepare-your-o365-tenant#enable-custom-teams-apps-and-turn-on-custom-app-uploading).

Seu bot recebe o evento `conversationUpdate` à medida que você adiciona os bots a uma equipe, sem as informações da equipe no `channelData` objeto.

## <a name="block-a-bot-in-personal-chat"></a>Bloquear um bot no chat pessoal

Os usuários podem optar por impedir que seu bot envie mensagens de chat pessoais. Eles podem alternar isso clicando com o botão direito do mouse no bot no canal de chat e escolhendo **Bloquear conversa de bot**. Isso significa que seus bots continuam a enviar mensagens, no entanto, o usuário não recebe as mensagens.

![Bloqueando um bot](~/assets/images/bots/botdisable.png)

## <a name="remove-a-bot-from-a-team"></a>Remover um bot de uma equipe

Os usuários podem excluir o bot escolhendo o ícone de lixeira na lista de bots na exibição da equipe. Isso remove apenas o bot do uso dessa equipe, e os usuários individuais ainda podem interagir no contexto pessoal. Os bots no contexto pessoal não podem ser desabilitados ou removidos pelos usuários.

## <a name="disable-a-bot-in-teams"></a>Desabilitar um bot no Teams

Para impedir que o bot receba mensagens, vá para o **Painel de Bot** e edite o Microsoft Teams de dados. **Desmarque a opção Habilitar Microsoft Teams** configuração. Isso impede que os usuários interajam com o bot, no entanto, ele ainda será detectável e os usuários ainda poderão adicioná-lo ao Teams.

## <a name="delete-a-bot-from-teams"></a>Excluir um bot do Teams

Para remover completamente o bot do Teams, vá para o Painel do **Bot** e edite o Microsoft Teams canal. Escolha o **botão** Excluir na parte inferior. Isso impede que os usuários descubram, adicionem e interajam com seu bot. Isso não remove o bot das instâncias de Teams usuário, no entanto, ele também para de funcionar para eles.

## <a name="see-also"></a>Confira também

* [Depurar o bot com o middleware de inspeção](/azure/bot-service/bot-service-debug-inspection-middleware)
* [Depurar seus chamados e o bot de reunião localmente](~/bots/calls-and-meetings/debugging-local-testing-calling-meeting-bots.md)
