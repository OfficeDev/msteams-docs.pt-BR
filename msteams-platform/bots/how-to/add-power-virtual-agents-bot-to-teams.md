---
title: Adicionar Power Virtual Agents chatbot ao Teams
author: surbhigupta
description: Aprenda a integrar um chatbot Power Virtual Agents na plataforma Teams para criar chatbots de conversa e integrá-lo ao Teams
ms.topic: how-to
ms.localizationpriority: medium
ms.author: lajanuar
ms.openlocfilehash: a95b3fe3b9191facc2554262444bc4b558c372ed
ms.sourcegitcommit: 8a0ffd21c800eecfcd6d1b5c4abd8c107fcf3d33
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2022
ms.locfileid: "63453835"
---
# <a name="add-power-virtual-agents-chatbot"></a>Adicionar um chatbot de Agentes Virtuais de Energia

Power Virtual Agents é uma solução de interface gráfica sem código e orientada que capacita todos os membros da sua equipe a criar chatbots ricos e conversacionais que se integram facilmente à plataforma Teams. Todo o conteúdo Power Virtual Agents renderiza naturalmente em Teams. Power Virtual Agents bots se envolvem com usuários na tela Teams de chat nativa. Os administradores de TI, analistas de negócios, especialistas em domínio e desenvolvedores de aplicativos qualificados podem projetar, desenvolver e publicar agentes virtuais inteligentes para Teams sem precisar configurar um ambiente de desenvolvimento. Eles podem criar um serviço Web ou se registrar diretamente com a Estrutura de Bots.

Este documento orienta você sobre como disponibilizar seu chatbot no Teams por meio do portal Power Virtual Agents e adicionar seu bot ao Teams usando o App Studio.

Power Virtual Agents permite criar chatbots poderosos que podem responder a perguntas feitas por seus clientes, outros funcionários ou visitantes do seu site ou serviço.

Esses bots podem ser criados facilmente sem a necessidade de desenvolvedores ou desenvolvedores de dados.

> [!NOTE]
> * Ao adicionar seu chatbot Microsoft Teams, alguns dos dados, como conteúdo de bot e conteúdo de chat do usuário, são compartilhados com Microsoft Teams. Isso significa que seus dados fluem fora da conformidade [da sua organização e dos limites geográficos ou regionais](/power-virtual-agents/data-location). <br/>
> * Você não deve usar o Microsoft Power Platform para criar aplicativos que devem ser publicados no Teams de aplicativos. Os aplicativos da Plataforma Microsoft Power só podem ser publicados no armazenamento de aplicativos de uma organização.

## <a name="make-your-chatbot-available-in-teams-through-the-power-virtual-agents-portal"></a>Disponibilizar seu chatbot no Teams por meio do portal Power Virtual Agents.

Para disponibilizar seu chatbot no Teams por meio do portal Power Virtual Agents, execute as seguintes etapas de processo:

Para disponibilizar o chatbot em Teams:

1. **Publicar o conteúdo de bot mais recente**  
Depois de criar um chatbot no portal Power Virtual Agents, você deve publicar seu bot antes Teams os usuários possam interagir com ele. Para obter mais informações, consulte [Publicar o conteúdo de bot mais recente](/power-virtual-agents/publication-fundamentals-publish-channels#publish-the-latest-bot-content).

   ![publicar no portal de agentes virtuais de energia](../../assets/images/pva-publish.png)

1. **Configurar o Teams canal**  
Depois de publicar seu bot, adicione o canal Teams para disponibilizar o bot para Teams usuários.

   ![canais no portal de agentes virtuais de energia](../../assets/images/pva-channels.png)

1. **Gerar uma ID de aplicativo para seu chatbot**  
Depois de adicionar o Teams ao chatbot, uma **ID de** aplicativo é gerada na caixa de diálogo. A ID do aplicativo é um identificador gerado pela Microsoft exclusivo para seu bot. Salve a ID do aplicativo para criar um pacote de aplicativos para Teams.

## <a name="add-your-bot-to-teams-using-app-studio"></a>Adicionar seu bot ao Teams usando o App Studio

Se [o carregamento de aplicativos](/microsoftteams/admin-settings) personalizados estiver habilitado em sua instância Teams, você poderá usar Teams App Studio para carregar diretamente seu chatbot e começar a usá-lo imediatamente. Para compartilhar seu chatbot, você pode solicitar que o administrador disponibilizar seu bot no catálogo de aplicativos de locatário ou pode enviar seu pacote de aplicativos para outras pessoas e pedir que eles o carreguem independentemente.

1. **Instalar o App Studio no Teams**  
O App Studio é um Teams aplicativo. Instale o App Studio no Teams que simplifica o processo de criação e registro de bots Teams:

   1. Selecione o ícone da loja de aplicativos Teams instância e pesquise **o App Studio**.

      &emsp;&emsp; <img  width="450px" alt="Finding App Studio in the Store" src="../../assets/images/get-started/app-studio-store.png"/>

   1. Selecione o **grupo App Studio** e selecione **Instalar** na caixa de diálogo pop-up.

      &emsp;&emsp; <img  width="450px" alt="Installing App Studio" src="../../assets/images/get-started/app-studio-install.png"/>

1. **Criar o Teams de aplicativo no App Studio**  
Bots no Teams são definidos por um arquivo JSON de manifesto de aplicativo que fornece as informações básicas sobre seu bot e seus recursos. No **App Studio**, selecione **Editor de manifesto** e selecione **Criar um novo aplicativo**.

    ![criar um novo aplicativo](../../assets/images/get-started/create-new-app.png)

1. **Adicionar detalhes do bot**  
Conclua todos os campos necessários. Para uma descrição completa de cada campo, consulte [definição de esquema de manifesto](../../resources/schema/manifest-schema.md).

    ![adicionar detalhes do aplicativo](../../assets/images/get-started/add-app-details.png)

1. **Configurar seu bot** Para configurar o bot, execute as seguintes etapas:
     1. Abra a **guia Bots** .
     1. Selecione **SetupExisting**  >  bot e insira o nome do bot.

   ![Configuração de bot](../../assets/images/get-started/bot-set-up.png)

   A imagem a seguir mostra como configurar um bot existente:

   ![configuração de bot existente](../../assets/images/get-started/existing-bot-set-up.png)

1. **Adicionar sua ID do aplicativo**  
Para adicionar a ID do aplicativo, execute as seguintes etapas:  
    1. Selecione **Conexão para uma id de bot** diferente e colar a **ID do aplicativo** que você copiou anteriormente.
    1. Selecione **ScopePersonalSave** >  > .

    ![adicionar id do aplicativo](../../assets/images/get-started/add-app-id.png)

1. **Adicionar domínios válidos para seu bot**  
Esta etapa só será necessária se o bot exigir que o usuário entre. Selecione **Domínios e permissões** e, no campo **Domínios Válidos** , forneça a seguinte entrada:

    ```bash
       token.botframework.com
    ```

1. **Testar e distribuir seu bot**  
Abra **a guia Testar e** distribua e selecione **Instalar** para adicionar seu bot diretamente à sua Teams instância. Como alternativa, você pode baixar o pacote de aplicativos concluído para compartilhar com Teams usuários ou fornecer ao administrador para disponibilizar seu bot no catálogo de aplicativos de locatário.

1. **Iniciar um chat** O processo de configuração para adicionar seu Power Virtual Agents de chat ao Teams está concluído. Agora você pode iniciar uma conversa com seu bot em um chat pessoal.

## <a name="next-step"></a>Próxima etapa

> [!div class="nextstepaction"]
> [Criar um assistente virtual](~/samples/virtual-assistant.md)

## <a name="see-also"></a>Confira também

* [Agentes virtuais do Power](/power-virtual-agents/fundamentals-what-is-power-virtual-agents)  
* [Criar um chatbot para Teams com o Microsoft Power Virtual Agents](../bot-features.md#bots-with-power-virtual-agents)
* [Power Virtual Agents portal](https://powervirtualagents.microsoft.com)
* [Publicar seu Power Virtual Agents bot](/power-virtual-agents/publication-fundamentals-publish-channels)
* [Segurança e conformidade no Microsoft Teams](/MicrosoftTeams/security-compliance-overview)
