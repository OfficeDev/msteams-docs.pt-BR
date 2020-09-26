---
title: Adicionar chatbot de agentes virtuais de energia ao Teams
author: laujan
description: integração de um chatbot de agentes virtuais de alimentação na plataforma do Microsoft Teams
ms.topic: how-to
ms.author: lajanuar
ms.openlocfilehash: 0a85738857015e4bce9627333ed6f1a74e489c43
ms.sourcegitcommit: b51a4982842948336cfabedb63bdf8f72703585e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/25/2020
ms.locfileid: "48279693"
---
# <a name="integrate-a-power-virtual-agents-chatbot-with-microsoft-teams"></a>Integrar um chatbot de agentes virtuais de energia ao Microsoft Teams

[Os agentes virtuais de alimentação](/power-virtual-agents/fundamentals-what-is-power-virtual-agents) são uma solução de interface gráfica orientada e sem código que capacita todos os membros da sua equipe a criarem chatbotss avançados e de conversa que se integram facilmente à plataforma do Microsoft Teams. Todo o conteúdo criado nos agentes de energia virtual é renderizado naturalmente no Teams e nos agentes virtuais de energia os bots participam dos usuários na tela de bate-papo nativo do teams. Seus administradores de ti, analistas de negócios, especialistas de domínio e desenvolvedores de aplicativos qualificados podem projetar, desenvolver e publicar agentes virtuais inteligentes para o Microsoft Teams sem precisar configurar um ambiente de desenvolvimento, criar um serviço Web ou registrar-se diretamente na estrutura do bot.  *Consulte* [Create a chatbot for Teams with Microsoft Power virtual Agents](../what-are-bots.md#create-a-chatbot-for-teams-with-microsoft-power-virtual-agents).

> [!NOTE]
> Ao adicionar seu chatbot ao Microsoft Teams, alguns dados, como o conteúdo de bot e o conteúdo de chat do usuário final, serão compartilhados com o Microsoft Teams (o que significa que seus dados fluirão para fora da [conformidade e dos limites regionais ou regionais da sua organização](/power-virtual-agents/data-location)). <br/>
> Para obter mais informações, consulte [segurança e conformidade no Microsoft Teams](/MicrosoftTeams/security-compliance-overview).

## <a name="make-your-chatbot-reachable-in-teams-in-the-power-virtual-agents-portal"></a>Tornar seu chatbot acessível no Microsoft Teams no portal de agentes virtuais de energia

1. **Publicar o conteúdo do bot mais recente**.  Depois de criar um chatbot no portal de [agentes virtuais de energia](https://powervirtualagents.microsoft.com), você precisa publicar o bot pelo menos uma vez para que os usuários do teams possam interagir com ele. Confira [publicar o conteúdo mais recente do bot](/power-virtual-agents/publication-fundamentals-publish-channels#publish-the-latest-bot-content).

![publicar no portal de agentes virtuais de energia](../../assets/images/pva-publish.png)

2. **Configure o canal Teams**. Após publicar seu bot, você pode adicionar o canal Teams para tornar o bot acessível para os usuários do teams.

![canais no portal de agentes virtuais de energia](../../assets/images/pva-channels.png)

3. **Gerar uma ID de aplicativo para seu chatbot**  Quando o canal Teams tiver sido adicionado com êxito ao chatbot, uma **ID de aplicativo** será gerada na caixa de diálogo. A ID do aplicativo é um identificador exclusivo gerado pela Microsoft para o bot.  Copie e salve a ID do aplicativo — você precisará mais tarde para criar um pacote de aplicativos para o Microsoft Teams.

## <a name="add-your-bot-to-teams-using-app-studio"></a>Adicionar seu bot ao Teams usando o app Studio

Se o [upload de aplicativos personalizados estiver habilitado](/microsoftteams/admin-settings) na instância do Microsoft Teams, você poderá usar o Teams app Studio para carregar diretamente seu chatbot e começar a usá-lo imediatamente. Se quiser compartilhar seu chatbot, você pode solicitar que o seu administrador disponibilize o bot no catálogo de aplicativos do locatário ou envie outras pessoas para o seu pacote de aplicativos e peça para carregá-lo de forma independente.

1. **Instale o app Studio no Teams**. O app Studio é um aplicativo do teams que você pode instalar no repositório do teams que simplifica a criação e o registro de seu bot no Microsoft Teams: 

  * Selecione o ícone repositório de aplicativos na parte inferior da barra de navegação à esquerda na sua instância do Teams e pesquise o **app Studio**.
>
&emsp;&emsp; <img  width="450px" title="Localizando o app Studio no repositório" src="../../assets/images/get-started/app-studio-store.png" alt="app in studio store view"/>    

  * Selecione o bloco do **app Studio** e escolha **instalar** na caixa de diálogo pop-up.
>
&emsp;&emsp; <img  width="450px" title="Instalando o app Studio" src="../../assets/images/get-started/app-studio-install.png" alt="install app studio view"/>

2. **Crie o manifesto do aplicativo do teams no app Studio**.  Os bots no Teams são definidos por um arquivo de manifesto de aplicativo (JSON) que fornece informações básicas sobre o bot e seus recursos. No **app Studio** , selecione **Editor de manifesto**para   =>  **criar um novo aplicativo**.
3. **Adicione os detalhes de bot**. Para obter uma descrição completa de cada campo, confira [definição de esquema de manifesto](../../resources/schema/manifest-schema.md). Certifique-se de concluir todos os campos obrigatórios.
4. **Configure seu bot**. Navegue até a guia **bots** , selecione o botão **configuração** , escolha **bot existente**e digite o nome do seu bot.
5. **Adicione sua ID de aplicativo**. Navegue para **se conectar a uma ID de bot diferente** e cole na **ID do aplicativo** que você copiou anteriormente. Em escopo, selecione **pessoal** e, em seguida, selecione **salvar**.
6. **Adicione domínios válidos para o bot**.  Esta etapa só será necessária se o seu bot exigir que o usuário entre. Navegue até **domínios e permissões** e, no campo **domínios válidos** , insira o seguinte:

```bash
token.botframework.com
```

7.  **Teste e distribua o bot**. Escolha a guia **testar e distribuir** e escolha **instalar** para adicionar seu bot diretamente à sua instância do teams. Opcionalmente, você pode baixar seu pacote de aplicativos concluído para compartilhar com usuários do teams ou fornecer a ele para o seu administrador para tornar o bot disponível no catálogo de aplicativos do locatário.
8. **Inicie um chat**. O processo de instalação para adicionar seus agentes virtuais de alimentação bot de chat ao Teams está completo. Agora você pode iniciar uma conversa com seu bot em um chat pessoal.

> [!div class="nextstepaction"]
> [Saiba mais sobre a publicação do bot de agentes virtuais de energia](/power-virtual-agents/publication-fundamentals-publish-channels)
