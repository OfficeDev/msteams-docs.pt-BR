---
title: Adicionar um chatbot do Power Virtual Agents ao Teams
author: surbhigupta
description: Aprenda a integrar um chatbot do Power Virtual Agents na plataforma do Teams para criar chatbots de conversa e integrá-lo ao Teams
ms.topic: how-to
ms.localizationpriority: high
ms.author: lajanuar
ms.openlocfilehash: 53a938ca4a195ba6f477de130a8290242709cb19
ms.sourcegitcommit: f15bd0e90eafb00e00cf11183b129038de8354af
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2022
ms.locfileid: "65111770"
---
# <a name="add-power-virtual-agents-chatbot"></a>Adicionar um chatbot de Agentes Virtuais de Energia

Uma solução de interface gráfica guiada sem código que capacita todos os membros da sua equipe a criar bots de chat avançados e conversacionais que se integram facilmente à plataforma do Teams. Todo o conteúdo criado no Power Virtual Agents renderiza naturalmente no Teams. Os bots do Power Virtual Agents interagem com usuários na tela de chat nativa do Teams. Os administradores de TI, analistas de negócios, especialistas de domínio e desenvolvedores de aplicativos qualificados podem projetar, desenvolver e publicar agentes virtuais inteligentes para o Teams sem precisar configurar um ambiente de desenvolvimento. Eles podem criar um serviço Web ou se registrar diretamente no Bot Framework.

Este documento orienta você sobre como disponibilizar seu chatbot no Teams por meio do portal do Power Virtual Agents e adicionar seu bot ao Teams usando o App Studio.

O Power Virtual Agents permite criar chatbots poderosos que podem responder a perguntas feitas por seus clientes, outros funcionários ou visitantes do seu site ou serviço.

Esses bots podem ser criados facilmente sem a necessidade de cientistas de dados ou desenvolvedores.

> [!NOTE]
> * Ao adicionar seu chatbot ao Microsoft Teams, alguns dos dados, como conteúdo de bot e conteúdo de chat do usuário, são compartilhados com o Microsoft Teams. Isso significa que seus dados fluem fora da [conformidade e limites geográficos ou regionais da sua organização](/power-virtual-agents/data-location). <br/>
> * Você não deve usar o Microsoft Power Platform para criar aplicativos que devem ser publicados na loja de aplicativos do Teams. Os aplicativos do Microsoft Power Platform podem ser publicados somente na loja de aplicativos de uma organização.

## <a name="make-your-chatbot-available-in-teams-through-the-power-virtual-agents-portal"></a>Disponibilize seu chatbot no Teams por meio do portal do Power Virtual Agents

Para disponibilizar seu chatbot no Teams por meio do portal do Power Virtual Agents, você deve executar as seguintes etapas de processo:

Para disponibilizar o chatbot no Teams:

1. **Publicar o conteúdo mais recente do bot**  
Depois de criar um chatbot no portal Power Virtual Agents, você deve publicar seu bot antes que os usuários do Teams possam interagir com ele. Para obter mais informações, consulte [Publicar o conteúdo mais recente do bot](/power-virtual-agents/publication-fundamentals-publish-channels#publish-the-latest-bot-content).

   ![publicar no portal do power virtual agents](../../assets/images/pva-publish.png)

1. **Configurar o canal do Teams**  
Depois de publicar seu bot, adicione o canal do Teams para disponibilizar o bot aos usuários do Teams.

   ![canais no portal do power virtual agents](../../assets/images/pva-channels.png)

1. **Gere uma ID de aplicativo para seu chatbot**  
Depois de adicionar o canal do Teams ao chatbot, uma **ID de aplicativo** é gerada na caixa de diálogo. A ID é um identificador exclusivo gerado pela Microsoft para o aplicativo. Salve a ID do aplicativo para criar um pacote de aplicativos para o Teams.

## <a name="add-your-bot-to-teams-using-app-studio"></a>Adicionar seu bot ao Teams usando o App Studio

Se [carregar aplicativos personalizados estiver habilitado](/microsoftteams/admin-settings)na sua instância do Teams, você poderá usar o Teams App Studio para carregar diretamente seu chatbot e começar a usá-lo imediatamente. Para compartilhar seu chatbot, você pode solicitar que o administrador disponibilize seu bot no catálogo de aplicativos do locatário ou pode enviar o pacote do aplicativo para outras pessoas e pedir para carregá-lo de forma independente.

1. **Instalar o App Studio no Teams**  
O App Studio é um aplicativo do Teams. Instale o App Studio da loja do Teams que simplifica o processo de criação e registro de bots no Teams:

   1. Selecione o ícone da loja de aplicativos na instância do Teams e pesquise por **App Studio**.

      &emsp;&emsp; <img  width="450px" alt="Finding App Studio in the Store" src="../../assets/images/get-started/app-studio-store.png"/>

   1. Selecione o bloco **App Studio** e selecione **Instalar** na caixa de diálogo pop-up.

      &emsp;&emsp; <img  width="450px" alt="Installing App Studio" src="../../assets/images/get-started/app-studio-install.png"/>

1. **Crie o manifesto do aplicativo Teams no App Studio**  
Os bots no Teams são definidos por um arquivo JSON de manifesto do aplicativo que fornece as informações básicas sobre seu bot e seus recursos. No **App Studio**, selecione **Editor de manifesto** e selecione **Criar um novo aplicativo**.

    ![criar um novo aplicativo](../../assets/images/get-started/create-new-app.png)

1. **Adicione detalhes do bot**  
Preencha todos os campos obrigatórios. Para obter uma descrição completa de cada campo, consulte [definição de esquema de manifesto](../../resources/schema/manifest-schema.md).

    ![adicionar detalhes do aplicativo](../../assets/images/get-started/add-app-details.png)

1. **Configure o seu bot** para configurar o bot, execute as seguintes etapas:
     1. Abra a guia **Bots**.
     1. Selecione **Configurar** > **Bot existente** e insira o nome do bot.

   ![Configuração de bot](../../assets/images/get-started/bot-set-up.png)

   A imagem a seguir mostra como configurar um bot existente:

   ![configuração de bot existente](../../assets/images/get-started/existing-bot-set-up.png)

1. **Adicione a ID de seu aplicativo**  
Para adicionar a ID do aplicativo, execute as seguintes etapas:  
    1. Selecione **Conectar-se a uma ID de bot diferente** e cole a **ID do aplicativo** que você copiou anteriormente.
    1. Selecione **Escopo** > **Pessoal** > **Salvar**.

    ![adicionar a id do aplicativo](../../assets/images/get-started/add-app-id.png)

1. **Adicione domínios válidos para seu bot**  
Essa etapa só será necessária se o bot exigir que o usuário entre. Selecione **Domínios e permissões** e, no campo **Domínios válidos**, forneça a seguinte entrada:

    ```bash
       token.botframework.com
    ```

1. **Teste e distribua seu bot**  
Abra a guia **Testar e distribuir** e selecione **Instalar** para adicionar seu bot diretamente à instância do Teams. Como alternativa, você pode baixar o pacote de aplicativos concluído para compartilhar com usuários do Teams ou for fornecido ao administrador para disponibilizar seu bot no catálogo de aplicativos de locatários.

1. **Inicie um chat** o processo de configuração para adicionar seu chatbot do Power Virtual Agents ao Teams está concluído. Agora você pode iniciar uma conversa com seu bot em um chat pessoal.

## <a name="next-step"></a>Próxima etapa

> [!div class="nextstepaction"]
> [Criar um assistente virtual](~/samples/virtual-assistant.md)

## <a name="see-also"></a>Confira também

* [Agentes virtuais do Power](/power-virtual-agents/fundamentals-what-is-power-virtual-agents)  
* [Criar um chatbot para o Teams com o Microsoft Power Virtual Agents](../bot-features.md#bots-with-power-virtual-agents)
* [ Portal do Power Virtual Agents portal](https://powervirtualagents.microsoft.com)
* [Publicar seu bot do Power Virtual Agents](/power-virtual-agents/publication-fundamentals-publish-channels)
* [Segurança e conformidade no Microsoft Teams](/MicrosoftTeams/security-compliance-overview)
