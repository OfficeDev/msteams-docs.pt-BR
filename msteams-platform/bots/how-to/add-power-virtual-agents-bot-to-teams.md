---
title: Adicionar chatbot de Agentes Virtuais do Power ao Teams
author: laujan
description: integrando um chatbot do Power Virtual Agents na plataforma teams
ms.topic: how-to
ms.author: lajanuar
ms.openlocfilehash: 6103e3b58d7283eab6e9a9932f6dc7778d6fc697
ms.sourcegitcommit: 79e6bccfb513d4c16a58ffc03521edcf134fa518
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/13/2021
ms.locfileid: "51697092"
---
# <a name="integrate-a-power-virtual-agents-chatbot-with-microsoft-teams"></a>Integrar um chatbot de Agentes Virtuais do Power com o Microsoft Teams

[O Power Virtual Agents](/power-virtual-agents/fundamentals-what-is-power-virtual-agents) é uma solução de interface gráfica sem código e orientada que capacita todos os membros da sua equipe a criar chatbots ricos e conversais que se integram facilmente à plataforma do Teams. Todo o conteúdo de autoria em Agentes Virtuais do Power é renderiza naturalmente nos bots do Teams e do Power Virtual Agents se envolvem com os usuários na tela de chat nativa do Teams. Seus administradores de TI, analistas de negócios, especialistas em domínio e desenvolvedores de aplicativos qualificados podem projetar, desenvolver e publicar agentes virtuais inteligentes para o Teams sem precisar configurar um ambiente de desenvolvimento, criar um serviço Web ou se registrar diretamente com a Estrutura de Bots.  *Consulte* [Create a chatbot for Teams with Microsoft Power Virtual Agents](../bot-features.md#bots-and-the-microsoft-power-virtual-agents).

> [!NOTE]
> Ao adicionar seu chatbot ao Microsoft Teams, alguns dos dados, como conteúdo de bot e conteúdo de chat do usuário final, serão compartilhados com o Microsoft Teams (o que significa que seus dados fluirão fora da conformidade da sua organização e dos limites geográficos ou regionais [).](/power-virtual-agents/data-location) <br/>
> Para obter mais informações, consulte [Segurança e conformidade no Microsoft Teams](/MicrosoftTeams/security-compliance-overview).

## <a name="make-your-chatbot-available-in-teams-via-the-power-virtual-agents-portal"></a>Disponibilizar seu chatbot no Teams por meio do portal do Power Virtual Agents

1. **Publicar o conteúdo do bot mais recente.**  Depois de criar um chatbot no portal do [Power Virtual Agents,](https://powervirtualagents.microsoft.com)você precisará publicar seu bot pelo menos uma vez para que os usuários do Teams possam interagir com ele. Consulte [Publicar o conteúdo de bot mais recente.](/power-virtual-agents/publication-fundamentals-publish-channels#publish-the-latest-bot-content)

![publicar no portal de agentes virtuais de energia](../../assets/images/pva-publish.png)

2. **Configurar o canal do Teams**. Depois de publicar seu bot, você pode adicionar o canal do Teams para disponibilizar o bot aos usuários do Teams.

![canais no portal de agentes virtuais de energia](../../assets/images/pva-channels.png)

3. **Gerar uma ID de aplicativo para seu chatbot**.  Quando o canal do Teams tiver sido adicionado com êxito ao chatbot, uma **ID de** aplicativo será gerada na caixa de diálogo. A ID do aplicativo é um identificador gerado pela Microsoft exclusivo para seu bot.  Copie e salve a ID do aplicativo — você precisará dela mais tarde para criar um pacote de aplicativos para o Teams.

## <a name="add-your-bot-to-teams-using-app-studio"></a>Adicionar seu bot ao Teams usando o App Studio

Se [o carregamento de aplicativos](/microsoftteams/admin-settings) personalizados estiver habilitado na instância do Teams, você poderá usar o Teams App Studio para carregar diretamente seu chatbot e começar a usá-lo imediatamente. Se você quiser compartilhar seu chatbot, você pode solicitar que o administrador disponibilizar seu bot no catálogo de aplicativos de locatário ou pode enviar a outras pessoas seu pacote de aplicativos e pedir que eles o carreguem independentemente.

1. **Instalar o App Studio no Teams**. O App Studio é um aplicativo do Teams que você pode instalar na loja do Teams que simplifica a criação e o registro do bot no Teams: 

  * Selecione o ícone da loja de aplicativos na parte inferior da barra de nav esquerda em sua instância do Teams e procure **App Studio**.
>

&emsp;&emsp; <img  width="450px" alt="Finding App Studio in the Store" src="/msteams-docs/msteams-platform/assets/images/get-started/app-studio-store.png"/>   

  * Selecione o **grupo App Studio** e escolha **Instalar** na caixa de diálogo pop-up.
>
&emsp;&emsp; <img  width="450px" alt="Installing App Studio" src="../../assets/images/get-started/app-studio-install.png"/>

2. **Criar o manifesto do aplicativo teams no App Studio**.  Bots no Teams são definidos por um arquivo JSON (manifesto do aplicativo) que fornece informações básicas sobre seu bot e seus recursos. No **App Studio,** selecione **Editor de manifesto** Criar um novo   =>  **aplicativo.**
3. **Adicione os detalhes do bot.** Para uma descrição completa de cada campo, consulte [definição de esquema de manifesto](../../resources/schema/manifest-schema.md). Certifique-se de concluir todos os campos necessários.
4. **Configurar seu bot**. Navegue até **a guia Bots,** selecione o botão **Instalação,** escolha **Bot** existente e insira o nome do bot.
5. **Adicione sua ID do aplicativo.** Navegue **até Conectar a uma id de bot** diferente e colar na **ID do aplicativo que** você copiou anteriormente. No escopo, selecione **Pessoal** e, em seguida, selecione **Salvar**.
6. **Adicione domínios válidos para seu bot**.  Esta etapa só será necessária se o bot exigir que o usuário entre. Navegue **até Domínios e permissões** e na entrada do campo **Domínios Válidos:**

```bash
token.botframework.com
```

7.  **Teste e distribua seu bot**. Escolha a **guia Testar e distribuir** e escolha **Instalar** para adicionar seu bot diretamente à sua instância do Teams. Opcionalmente, você pode baixar seu pacote de aplicativos concluído para compartilhar com usuários do Teams ou fornece-lo ao administrador para disponibilizar seu bot no catálogo de aplicativos de locatário.
8. **Iniciar um chat**. O processo de instalação para adicionar seu bot de chat do Power Virtual Agents ao Teams está concluído. Agora você pode iniciar uma conversa com seu bot em um chat pessoal.

> [!div class="nextstepaction"]
> [Saiba mais: Publicar seu bot agentes virtuais do Power](/power-virtual-agents/publication-fundamentals-publish-channels)
