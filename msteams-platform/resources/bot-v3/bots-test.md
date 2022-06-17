---
title: Testar e depurar seu aplicativo
description: Neste artigo, você saberá como testar e depurar seus bots no Microsoft Teams e testar seu bot sem carregar no Teams
ms.topic: how-to
ms.localizationpriority: medium
ms.date: 03/20/2019
ms.openlocfilehash: 3cfb76443566a0ca5c279547f7b3db490c6095d3
ms.sourcegitcommit: ca84b5fe5d3b97f377ce5cca41c48afa95496e28
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/17/2022
ms.locfileid: "66143694"
---
# <a name="test-and-debug-your-microsoft-teams-bot"></a>Testar e depurar seu bot do Microsoft Teams

[!include[v3-to-v4-SDK-pointer](~/includes/v3-to-v4-pointer-bots.md)]

Ao testar o bot, você precisa levar em consideração os contextos em que deseja que o bot seja executado, bem como qualquer funcionalidade que você tenha adicionado ao bot que exija dados específicos do Microsoft Teams. Verifique se o método escolhido para testar o bot está alinhado com sua funcionalidade.

## <a name="test-by-uploading-to-teams"></a>Testar carregando no Teams

A maneira mais abrangente de testar seu bot é criando um pacote de aplicativos e carregando-o no Teams. Esse é o único método para testar a funcionalidade completa disponível para seu bot, em todos os escopos.

Há dois métodos para carregar seu aplicativo. Você pode usar o [App Studio](~/concepts/build-and-test/app-studio-overview.md) ou criar [manualmente um pacote de aplicativos](~/concepts/build-and-test/apps-package.md) e [carregar seu aplicativo](~/concepts/deploy-and-publish/apps-upload.md). Se você precisar alterar o manifesto e recarregar o aplicativo, deverá [excluir o bot](#deleting-a-bot-from-teams) antes de carregar o pacote do aplicativo alterado.

## <a name="debug-your-bot-locally"></a>Depurar seu bot localmente

Se você estiver hospedando seu bot localmente durante o desenvolvimento, precisará usar um serviço de túnel como [o ngrok](https://ngrok.com/) para testar o bot. Depois de baixar e instalar o ngrok, execute o comando abaixo para iniciar o serviço de túnel. Talvez seja necessário adicionar o ngrok ao caminho.

```bash
ngrok http <port> -host-header=localhost:<port>
```

Use o ponto de extremidade https fornecido pelo ngrok no manifesto do aplicativo. Se você fechar a janela de comando e reiniciar, receberá uma nova URL e precisará atualizar o endereço do ponto de extremidade do bot para usá-lo também.

## <a name="testing-your-bot-without-uploading-to-teams"></a>Testando seu bot sem carregar no Teams

Ocasionalmente, é necessário testar seu bot sem instalá-lo como um aplicativo no Teams. Fornecemos dois métodos para teste. Testar o bot sem instalá-lo como um aplicativo pode ser útil para garantir que o bot esteja disponível e respondendo, no entanto, ele não permitirá que você teste toda a amplitude da funcionalidade do Microsoft Teams que você pode ter adicionado ao bot. Se você precisar testar o bot completamente, siga as instruções para [testar carregando](#test-by-uploading-to-teams).

### <a name="use-the-bot-emulator"></a>Usar o Bot Emulator

O Bot Framework Emulator é um aplicativo da área de trabalho que permite aos desenvolvedores de bot testar e depurar seus bots, localmente ou remotamente. Usando o emulador, você pode conversar com seu bot e inspecionar as mensagens que seu bot envia e recebe. Isso pode ser útil para verificar se o bot está disponível e respondendo, no entanto, o emulador não permitirá que você teste nenhuma funcionalidade específica do Teams que você adicionou ao bot, nem as respostas do bot serão uma representação visual precisa de como eles são renderizados no Teams. Se você precisar testar qualquer uma dessas coisas, não é melhor carregar o [bot](#test-by-uploading-to-teams).

Instruções completas sobre o Bot Framework Emulator podem ser encontradas [aqui](/azure/bot-service/bot-service-debug-emulator?view=azure-bot-service-4.0&preserve-view=true).

### <a name="talk-to-your-bot-directly-by-id"></a>Fale com seu bot diretamente por ID

>[!Important]
>Conversar com seu bot por ID destina-se apenas para fins de teste.

Você também pode iniciar uma conversa com seu bot usando sua ID. Dois métodos para fazer isso são fornecidos abaixo. Quando um bot tiver sido adicionado por meio de um desses métodos, ele não poderá ser endereçável em conversas de canal e você não poderá aproveitar outros recursos de aplicativo do Microsoft Teams, como guias ou extensões de mensagem.

1. Na página [Painel de bot](https://dev.botframework.com/bots) para seu o bot, em **Canais**, selecione **Adicionar ao Microsoft Teams**. O Microsoft Teams será iniciado com um chat pessoal com seu bot.
2. Faça referência direta à ID do aplicativo do bot de dentro do Microsoft Teams:
   * Na página [Painel do bot](https://dev.botframework.com/bots) para seu bot, em **Detalhes**, copie a **ID do aplicativo da Microsoft** para o bot.
  
      :::image type="content" source="../../assets/images/bots_appid_botframework.png" alt-text="Painel do Bot":::
  
   * No Microsoft Teams, no painel de **Chat**, selecione o **ícone Adicionar chat**. Em **Para**, cole a ID do Aplicativo da Microsoft de seu bot.
  
      :::image type="content" source="../../assets/images/bots_uploading.png" alt-text="Carregando o AppID para o bot"border="true":::

     A ID do aplicativo deve ser resolvida para o nome do bot.

   * Selecione seu bot e envie uma mensagem para iniciar uma conversa.
   * Como alternativa, você pode colar a ID do aplicativo do bot na caixa de pesquisa no canto superior esquerdo do Microsoft Teams. Na página de resultados da pesquisa, navegue até a guia Pessoas para ver seu bot e começar a conversar com ele.

Seu bot receberá o evento `conversationUpdate` assim como bots adicionados a uma equipe, mas sem as informações da equipe no objeto `channelData`.

## <a name="blocking-a-bot-in-personal-chat"></a>Bloqueando um bot no chat pessoal

Observe que os usuários podem optar por impedir que seu bot envie mensagens de chat pessoais. Eles podem alternar isso clicando com o botão direito do mouse no bot no canal de chat e escolhendo **Bloquear conversas com bot**. Isso significa que seus bots continuarão a enviar mensagens, mas o usuário não receberá essas mensagens.

  :::image type="content" source="../../assets/images/bots/botdisable.png" alt-text="Bloqueando um bot"border="true":::

## <a name="removing-a-bot-from-a-team"></a>Removendo um bot de uma equipe

Os usuários podem excluir o bot escolhendo o ícone de lixeira na lista de bots no modo de exibição de equipes. Observe que isso apenas remove o bot do uso dessa equipe, os usuários individuais podem interagir no contexto pessoal.

Os bots no contexto pessoal não podem ser desabilitados ou removidos por um usuário, faltando remover completamente o bot do Teams.

## <a name="disabling-a-bot-in-teams"></a>Desabilitando um bot no Teams

Para interromper o recebimento de mensagens pelo bot, acesse o Painel de Bot e edite o canal do Microsoft Teams. Desmarque a opção **Habilitar no Microsoft Teams**. Isso impede que os usuários interajam com o bot, mas ele ainda será detectável e os usuários poderão adicioná-lo às equipes.

## <a name="deleting-a-bot-from-teams"></a>Excluindo um bot do Teams

Para remover completamente o bot do Teams, acesse o Painel de Bot e edite o canal do Microsoft Teams. Escolha o botão **Excluir** na parte inferior. Isso impede que os usuários descubram, adicionem ou interajam com seu bot. Isso não remove o bot das instâncias de Teams outros usuários, embora ele deixe de funcionar para eles também.

## <a name="removing-your-bot-from-appsource"></a>Removendo seu bot do AppSource

Se você quiser remover o bot do aplicativo Teams no AppSource (antes chamado de Office Store), deverá remover o bot do manifesto do aplicativo e reenviar seu aplicativo para validação. Para saber mais, confira [Publicar seu aplicativo do Microsoft Teams no AppSource](~/concepts/deploy-and-publish/apps-publish.md).
