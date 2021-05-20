---
title: Teste e depure seu bot
description: Descreve como testar bots em Microsoft Teams
keywords: equipes bots testando
ms.topic: how-to
localization_priority: Normal
ms.date: 03/20/2019
ms.openlocfilehash: 269b0680e45d764cf4cb0269c40d3d202145edb8
ms.sourcegitcommit: 51e4a1464ea58c254ad6bd0317aca03ebf6bf1f6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2021
ms.locfileid: "52566457"
---
# <a name="test-and-debug-your-microsoft-teams-bot"></a>Teste e depure seu bot de Microsoft Teams

[!include[v3-to-v4-SDK-pointer](~/includes/v3-to-v4-pointer-bots.md)]

Ao testar seu bot, você precisa levar em consideração tanto o contexto(s) que você deseja que seu bot seja executado, bem como qualquer funcionalidade que você possa ter adicionado ao seu bot que requer dados específicos para Microsoft Teams. Certifique-se de que o método escolhido para testar seu bot esteja alinhado com sua funcionalidade.

## <a name="test-by-uploading-to-teams"></a>Teste carregando para Teams

A maneira mais abrangente de testar seu bot é criando um pacote de aplicativos e enviando-o para Teams. Este é o único método para testar toda a funcionalidade disponível para o seu bot, em todos os escopos.

Existem dois métodos para carregar seu aplicativo. Você pode usar [o App Studio](~/concepts/build-and-test/app-studio-overview.md) para ajudá-lo, ou pode criar manualmente um pacote de [aplicativos](~/concepts/build-and-test/apps-package.md) e carregar [seu aplicativo](~/concepts/deploy-and-publish/apps-upload.md). Se você precisar alterar seu manifesto e recarregar seu aplicativo, você deve [excluir seu bot](#deleting-a-bot-from-teams) antes de carregar seu pacote de aplicativo alterado.

## <a name="debug-your-bot-locally"></a>Depurar seu bot localmente

Se você estiver hospedando seu bot localmente durante o desenvolvimento, você precisará usar um serviço de tunelamento como [ngrok](https://ngrok.com/) para testar seu bot. Depois de baixar e instalar ngrok, execute o comando abaixo para iniciar o serviço de tunelamento. Você pode precisar adicionar ngrok ao seu caminho.

```bash
ngrok http <port> -host-header=localhost:<port>
```

Use o ponto final https fornecido pela ngrok em seu manifesto de aplicativo. Se você fechar sua janela de comando e reiniciar, você terá uma nova URL, e você precisará atualizar seu endereço de ponto final do bot para usar esse também.

## <a name="testing-your-bot-without-uploading-to-teams"></a>Testando seu bot sem fazer upload para Teams

Ocasionalmente, pode ser necessário testar seu bot sem instalá-lo como um aplicativo em Teams. Nós fornecemos dois métodos para fazê-lo abaixo. Testar seu bot sem instalá-lo como um aplicativo pode ser útil para garantir que seu bot esteja disponível e respondendo, no entanto, ele não permitirá que você teste toda a amplitude da funcionalidade Microsoft Teams que você pode ter adicionado ao seu bot. Se você precisar testar totalmente o seu bot, siga as instruções para [testar carregando](#test-by-uploading-to-teams).

### <a name="use-the-bot-emulator"></a>Use o Emulador de Bot

O Bot Framework Emulator é um aplicativo de desktop que permite que os desenvolvedores de bots testem e depurem seus bots, local ou remotamente. Usando o emulador, você pode conversar com seu bot e inspecionar as mensagens que seu bot envia e recebe. Isso pode ser útil para verificar se o seu bot está disponível e responder, no entanto, o emulador não permitirá que você teste qualquer funcionalidade específica Teams que você adicionou ao seu bot, nem as respostas do seu bot serão uma representação visual precisa de como elas serão renderizadas em Teams. Se você precisa testar qualquer uma dessas coisas é melhor [carregar o seu bot](#test-by-uploading-to-teams).

Instruções completas sobre o Bot Framework Emulator podem ser [encontradas aqui](/azure/bot-service/bot-service-debug-emulator?view=azure-bot-service-4.0&preserve-view=true).

### <a name="talk-to-your-bot-directly-by-id"></a>Fale com seu bot diretamente por Id

>[!Important]
>Falar com seu bot por identificação destina-se apenas a fins de teste.

Você também pode iniciar uma conversa com seu bot usando seu Id. Dois métodos para fazê-lo são dados abaixo. Quando um bot foi adicionado através de um desses métodos, ele não será endereçado em conversas de canal, e você não pode tirar proveito de outros recursos de aplicativos Microsoft Teams, como guias ou extensões de mensagens.

1. Na página [Bot Dashboard](https://dev.botframework.com/bots) para o seu bot, em **Canais,** selecione **Adicionar ao Microsoft Teams**. Microsoft Teams será lançado com um bate-papo pessoal com seu bot.
2. Consulte diretamente o ID do aplicativo do seu bot de dentro de Microsoft Teams:
   * Na página [Do Painel de Bots](https://dev.botframework.com/bots) para o seu bot, em **Detalhes,** copie o **ID do Microsoft App** para o seu bot.
  
     ![Obtendo o AppID para o bot](~/assets/images/bots_appid_botframework.png)
  
   * De dentro Microsoft Teams, no painel **Chat,** selecione o ícone **Adicionar chat.** **Para:**, cole o ID do aplicativo Microsoft do seu bot.
  
     ![Carregando o AppID para o bot](~/assets/images/bots_uploading.png)

     O ID do aplicativo deve ser resolvido com o nome do seu bot.

   * Selecione seu bot e envie uma mensagem para iniciar uma conversa.
   * Alternativamente, você pode colar o ID do aplicativo do seu bot na caixa de pesquisa no canto superior esquerdo em Microsoft Teams. Na página de resultados de pesquisa, navegue até a guia Pessoas para ver seu bot e comece a conversar com ele.

Seu bot receberá o `conversationUpdate` evento assim como bots adicionados a uma equipe, mas sem as informações da equipe no `channelData` objeto.

## <a name="blocking-a-bot-in-personal-chat"></a>Bloqueando um bot em bate-papo pessoal

Observe que os usuários podem optar por bloquear seu bot de enviar mensagens de bate-papo pessoais. Eles podem alternar isso clicando com o botão direito do mouse no seu bot no canal de bate-papo e escolhendo **bloquear a conversa do bot**. Isso significa que seus bots continuarão a enviar mensagens, mas o usuário não receberá essas mensagens.

![Bloqueando um bot](~/assets/images/bots/botdisable.png)

## <a name="removing-a-bot-from-a-team"></a>Removendo um bot de uma equipe

Os usuários podem excluir o bot escolhendo o ícone de lata de lixo na lista de bots na exibição de suas equipes. Observe que isso só remove o bot do uso dessa equipe; usuários individuais ainda poderão interagir em contexto pessoal.

Bots em contexto pessoal não podem ser desativados ou removidos por um usuário, a não ser remover completamente o bot de Teams.

## <a name="disabling-a-bot-in-teams"></a>Desativando um bot em Teams

Para impedir que seu bot receba mensagens, vá ao seu Bot Dashboard e edite o canal Microsoft Teams. Limpe a opção **Ativar Microsoft Teams.** Isso impede que os usuários interajam com o bot, mas ele ainda será possível e os usuários ainda poderão adicioná-lo às equipes.

## <a name="deleting-a-bot-from-teams"></a>Excluindo um robô de Teams

Para remover seu bot completamente de Teams, vá para o seu Bot Dashboard e edite o canal Microsoft Teams. Escolha o botão **Excluir** na parte inferior. Isso impede que os usuários descubram, adoem ou interajam com seu bot. Observe que isso não remove o bot das instâncias Teams de outros usuários, embora ele deixe de funcionar para eles também.

## <a name="removing-your-bot-from-appsource"></a>Removendo seu bot do AppSource

Se você quiser remover seu bot do seu aplicativo Teams no AppSource (anteriormente Office Store), você deve remover o bot do manifesto do aplicativo e reenviar seu aplicativo para validação. Para obter mais informações, consulte [Publicar seu aplicativo Microsoft Teams para AppSource](~/concepts/deploy-and-publish/apps-publish.md).
