---
title: Testar e depurar seu bot
description: Descreve como testar bots no Microsoft Teams
keywords: teste de bots do teams
ms.topic: how-to
ms.date: 03/20/2019
ms.openlocfilehash: 6403d9ba16510860492735944899285058d9c0f3
ms.sourcegitcommit: 79e6bccfb513d4c16a58ffc03521edcf134fa518
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/13/2021
ms.locfileid: "51696602"
---
# <a name="test-and-debug-your-microsoft-teams-bot"></a>Testar e depurar seu bot do Microsoft Teams

[!include[v3-to-v4-SDK-pointer](~/includes/v3-to-v4-pointer-bots.md)]

Ao testar seu bot, você precisa levar em consideração os contextos em que deseja que seu bot seja executado, bem como qualquer funcionalidade que você possa ter adicionado ao bot que exija dados específicos do Microsoft Teams. Certifique-se de que o método escolhido para testar seu bot se alinhe com sua funcionalidade.

## <a name="test-by-uploading-to-teams"></a>Testar carregando no Teams

A maneira mais abrangente de testar seu bot é criando um pacote de aplicativos e carregando-o no Teams. Este é o único método para testar a funcionalidade completa disponível para o bot, em todos os escopos.

Há dois métodos para carregar seu aplicativo. Você pode usar o [App Studio](~/concepts/build-and-test/app-studio-overview.md) para ajudá-lo ou criar manualmente um pacote de [aplicativos](~/concepts/build-and-test/apps-package.md) e [carregar seu aplicativo.](~/concepts/deploy-and-publish/apps-upload.md) Se você precisar alterar seu manifesto e carregar seu aplicativo de novo, exclua seu [bot](#deleting-a-bot-from-teams) antes de carregar seu pacote de aplicativo alterado.

## <a name="debug-your-bot-locally"></a>Depurar seu bot localmente

Se você estiver hospedando seu bot localmente durante o desenvolvimento, precisará usar um serviço de túnel como [o ngrok](https://ngrok.com/) para testar seu bot. Depois de baixar e instalar o ngrok, execute o comando abaixo para iniciar o serviço de tunelamento (talvez seja necessário adicionar ngrok ao seu caminho).

```bash
ngrok http <port> -host-header=localhost:<port>
```

Use o ponto de extremidade https fornecido pelo ngrok no manifesto do aplicativo. Se você fechar a janela de comando e reiniciar, você terá uma nova URL e precisará atualizar seu endereço de ponto de extremidade do bot para usá-la também.

## <a name="testing-your-bot-without-uploading-to-teams"></a>Testar seu bot sem carregar no Teams

Ocasionalmente, pode ser necessário testar seu bot sem instalá-lo como um aplicativo no Teams. Fornecemos dois métodos para fazer isso abaixo. Testar seu bot sem instalá-lo como um aplicativo pode ser útil para garantir que o bot está disponível e respondendo, no entanto, ele não permitirá que você teste a amplitude completa da funcionalidade do Microsoft Teams que você pode ter adicionado ao seu bot. Se você precisar testar totalmente seu bot, siga as instruções de [teste carregando](#test-by-uploading-to-teams).

### <a name="use-the-bot-emulator"></a>Usar o Emulador de Bot

O Emulador da Estrutura de Bots é um aplicativo de área de trabalho que permite aos desenvolvedores de bot testar e depurar seus bots, localmente ou remotamente. Usando o emulador, você pode conversar com seu bot e inspecionar as mensagens que seu bot envia e recebe. Isso pode ser útil para verificar se o bot está disponível e respondendo, no entanto, o emulador não permitirá que você teste nenhuma funcionalidade específica do Teams adicionada ao bot, nem as respostas do bot serão uma representação visual precisa de como eles serão renderizados no Teams. Se você precisar testar qualquer uma dessas coisas, é melhor [carregar seu bot](#test-by-uploading-to-teams).

Instruções completas sobre o Emulador da Estrutura de Bot podem ser encontradas [aqui](/azure/bot-service/bot-service-debug-emulator?view=azure-bot-service-4.0&preserve-view=true).

### <a name="talk-to-your-bot-directly-by-id"></a>Fale com seu bot diretamente por ID

>[!Important]
>Conversar com seu bot por Id destina-se apenas a fins de teste.

Você também pode iniciar uma conversa com seu bot usando sua ID. Dois métodos para fazer isso são dados abaixo. Quando um bot tiver sido adicionado por meio de um desses métodos, ele não poderá ser abordada em conversas de canal e você não poderá tirar proveito de outros recursos de aplicativo do Microsoft Teams, como guias ou extensões de mensagens.

1. Na página [Painel de Bot](https://dev.botframework.com/bots) para seu bot, em **Canais,** selecione **Adicionar ao Microsoft Teams**. O Microsoft Teams será lançado com um chat pessoal com seu bot.
2. Fazer referência direta à ID do aplicativo do bot de dentro do Microsoft Teams:
   * Na página [Painel de Bot](https://dev.botframework.com/bots) para seu bot, em **Detalhes**, copie a **ID** do Aplicativo microsoft para seu bot.
  
     ![Obter o AppID para o bot](~/assets/images/bots_appid_botframework.png)
  
   * No Microsoft Teams, no painel **Chat,** selecione o **ícone Adicionar chat.** **Para:**, colar a ID do aplicativo Microsoft do seu bot.
  
     ![Carregando o AppID para o bot](~/assets/images/bots_uploading.png)

     A ID do aplicativo deve ser resolvida com o nome do bot.

   * Selecione seu bot e envie uma mensagem para iniciar uma conversa.
   * Como alternativa, você pode colar a ID do aplicativo do bot na caixa de pesquisa na parte superior esquerda do Microsoft Teams. Na página resultados da pesquisa, navegue até a guia Pessoas para ver seu bot e começar a conversar com ele.

Seu bot receberá o `conversationUpdate` evento da mesma forma que bots adicionados a uma equipe, mas sem as informações da equipe no `channelData` objeto.

## <a name="blocking-a-bot-in-personal-chat"></a>Bloquear um bot no chat pessoal

Observe que os usuários podem optar por impedir que seu bot envie mensagens de chat pessoais. Eles podem alternar isso clicando com o botão direito do mouse no bot no canal de chat e escolhendo **Bloquear conversa bot**. Isso significa que seus bots continuarão a enviar mensagens, mas o usuário não receberá essas mensagens.

![Bloqueando um bot](~/assets/images/bots/botdisable.png)

## <a name="removing-a-bot-from-a-team"></a>Remover um bot de uma equipe

Os usuários podem excluir o bot escolhendo o ícone de lixeira na lista de bots no seu exibição de equipes. Observe que isso remove apenas o bot do uso dessa equipe; os usuários individuais ainda poderão interagir no contexto pessoal.

Os bots no contexto pessoal não podem ser desabilitados ou removidos por um usuário, além de remover completamente o bot do Teams.

## <a name="disabling-a-bot-in-teams"></a>Desabilitar um bot no Teams

Para interromper o recebimento de mensagens do bot, vá para o Painel de Bot e edite o canal do Microsoft Teams. Des limpar **a opção Habilitar no Microsoft Teams.** Isso impede que os usuários interajam com o bot, mas ele ainda será descoberto e os usuários ainda poderão adicioná-lo às equipes.

## <a name="deleting-a-bot-from-teams"></a>Excluir um bot do Teams

Para remover completamente o bot do Teams, vá até seu Painel de Bot e edite o canal do Microsoft Teams. Escolha o **botão Excluir** na parte inferior. Isso impede que os usuários descubram, adicionem ou interajam com seu bot. Observe que isso não remove o bot das instâncias do Teams de outros usuários, embora ele também deixe de funcionar para eles.

## <a name="removing-your-bot-from-appsource"></a>Removendo seu bot do AppSource

Se você quiser remover seu bot do seu aplicativo do Teams no AppSource (anteriormente Office Store), você deve remover o bot do manifesto do aplicativo e reabrir seu aplicativo para validação. Confira [Publicar seu aplicativo do Microsoft Teams no AppSource](~/concepts/deploy-and-publish/apps-publish.md) para obter mais informações.
