---
title: Adicionar chatbot de Agentes Virtuais do Power ao Teams
author: laujan
description: integrando um chatbot do Power Virtual Agents na plataforma teams
ms.topic: how-to
localization_priority: Normal
ms.author: lajanuar
ms.openlocfilehash: d6d9f4292e22df7ca0f5841a2fc579b9e3b1d2f3
ms.sourcegitcommit: 825abed2f8784d2bab7407ba7a4455ae17bbd28f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2021
ms.locfileid: "52020071"
---
# <a name="add-power-virtual-agents-chatbot"></a>Adicionar chatbot de Agentes Virtuais do Power 

O Power Virtual Agents é uma solução de interface gráfica sem código e orientada que capacita todos os membros da sua equipe a criar chatbots ricos e conversais que se integram facilmente à plataforma do Teams. Todo o conteúdo de autoria no Power Virtual Agents é renderiza naturalmente no Teams. Os bots do Power Virtual Agents se envolvem com usuários na tela de chat nativa do Teams. Os administradores de TI, analistas de negócios, especialistas em domínio e desenvolvedores de aplicativos qualificados podem projetar, desenvolver e publicar agentes virtuais inteligentes para o Teams sem precisar configurar um ambiente de desenvolvimento. Eles podem criar um serviço Web ou se registrar diretamente com a Estrutura de Bots. 

Este documento orienta você sobre como disponibilizar seu chatbot no Teams por meio do portal do Power Virtual Agents e adicionar seu bot ao Teams usando o App Studio. 

Os Agentes Virtuais do Power permitem que você crie chatbots poderosos que possam responder a perguntas feitas por seus clientes, outros funcionários ou visitantes do seu site ou serviço.

Esses bots podem ser criados facilmente sem a necessidade de desenvolvedores ou desenvolvedores de dados.

> [!NOTE]
> Ao adicionar seu chatbot ao Microsoft Teams, alguns dos dados, como conteúdo de bot e conteúdo de chat do usuário, são compartilhados com o Microsoft Teams. Isso significa que seus dados fluem fora da conformidade da sua organização e dos limites [geográficos ou regionais.](/power-virtual-agents/data-location) <br/>

## <a name="make-your-chatbot-available-in-teams-through-the-power-virtual-agents-portal"></a>Disponibilizar seu chatbot no Teams por meio do portal do Power Virtual Agents

Para disponibilizar seu chatbot no Teams por meio do portal do Power Virtual Agents, você deve executar as seguintes etapas de processo:

**Para disponibilizar o chatbot no Teams**

1. **Publicar o conteúdo de bot mais recente**  
Depois de criar um chatbot no portal do Power Virtual Agents, você deve publicar seu bot antes que os usuários do Teams possam interagir com ele. Para obter mais informações, consulte [Publicar o conteúdo de bot mais recente.](/power-virtual-agents/publication-fundamentals-publish-channels#publish-the-latest-bot-content)

   ![publicar no portal de agentes virtuais de energia](../../assets/images/pva-publish.png)

1. **Configurar o canal do Teams**  
Depois de publicar seu bot, adicione o canal do Teams para disponibilizar o bot aos usuários do Teams.

   ![canais no portal de agentes virtuais de energia](../../assets/images/pva-channels.png)

1. **Gerar uma ID de aplicativo para seu chatbot**  
Depois de adicionar o canal do Teams ao chatbot, uma **ID de aplicativo** é gerada na caixa de diálogo. A ID do aplicativo é um identificador gerado pela Microsoft exclusivo para seu bot. Salve a ID do aplicativo para criar um pacote de aplicativos para o Teams.

## <a name="add-your-bot-to-teams-using-app-studio"></a>Adicionar seu bot ao Teams usando o App Studio

Se [o carregamento de aplicativos](/microsoftteams/admin-settings) personalizados estiver habilitado em sua instância do Teams, você poderá usar o Teams App Studio para carregar diretamente seu chatbot e começar a usá-lo imediatamente. Para compartilhar seu chatbot, você pode solicitar que o administrador disponibilizar seu bot no catálogo de aplicativos de locatário ou pode enviar seu pacote de aplicativos para outras pessoas e pedir que eles o carreguem independentemente.

1. **Instalar o App Studio no Teams**  
App Studio é um aplicativo do Teams. Instale o App Studio no armazenamento do Teams que simplifica o processo de criação e registro de bots no Teams: 

   1. Selecione o ícone da loja de aplicativos na instância do Teams e procure **App Studio**.

      &emsp;&emsp; <img  width="450px" alt="Finding App Studio in the Store" src="../../assets/images/get-started/app-studio-store.png"/>   

   1. Selecione o **grupo App Studio** e selecione **Instalar** na caixa de diálogo pop-up.

      &emsp;&emsp; <img  width="450px" alt="Installing App Studio" src="../../assets/images/get-started/app-studio-install.png"/>

1. **Criar o manifesto do aplicativo do Teams no App Studio**  
Bots no Teams são definidos por um arquivo JSON de manifesto do aplicativo que fornece as informações básicas sobre seu bot e seus recursos. No **App Studio,** selecione **Editor de manifesto** e selecione Criar um novo **aplicativo.**  
A imagem a seguir orienta você a criar um novo aplicativo no App Studio:  

   ![criar um novo aplicativo](../../assets/images/get-started/create-new-app.png)

1. **Adicionar detalhes do bot**  
Conclua todos os campos necessários. Para uma descrição completa de cada campo, consulte [definição de esquema de manifesto](../../resources/schema/manifest-schema.md).   
A imagem a seguir orienta você a adicionar os detalhes do aplicativo:  

   ![adicionar detalhes do aplicativo](../../assets/images/get-started/add-app-details.png)

1. **Configurar seu bot** Para configurar o bot, execute as seguintes etapas: 
     1. Abra a **guia Bots.** 
     1. Selecione **Configurar**  >  **bot existente** e insira o nome do bot.

   A imagem a seguir orienta você a configurar um bot:    

   ![Configuração de bot](../../assets/images/get-started/bot-set-up.png) 

   A imagem a seguir orienta você a configurar um bot existente:      

   ![configuração de bot existente](../../assets/images/get-started/existing-bot-set-up.png)    
1. **Adicionar sua ID do aplicativo**  
Para adicionar a ID do aplicativo, execute as seguintes etapas:  
    1. Selecione **Conectar a uma id de bot diferente** e colar a **ID do aplicativo que** você copiou anteriormente. 
    1. Selecione **Salvar**  >  **Pessoal de**  >  **Escopo**.      
A imagem a seguir orienta você a configurar um bot existente:    

   ![adicionar id do aplicativo](../../assets/images/get-started/add-app-id.png)

1. **Adicionar domínios válidos para seu bot**  
Esta etapa só será necessária se o bot exigir que o usuário entre. Selecione **Domínios e permissões** e, no campo **Domínios Válidos,** forneça a seguinte entrada:

    ```bash
       token.botframework.com
    ```

7.  **Testar e distribuir seu bot**  
Abra **a guia Teste e distribua** e selecione **Instalar** para adicionar seu bot diretamente à sua instância do Teams. Como alternativa, você pode baixar o pacote de aplicativos concluído para compartilhar com usuários do Teams ou fornece-lo ao administrador para disponibilizar seu bot no catálogo de aplicativos do locatário.

8. **Iniciar um chat**   
O processo de configuração para adicionar seu bot de chat do Power Virtual Agents ao Teams está concluído. Agora você pode iniciar uma conversa com seu bot em um chat pessoal.

## <a name="see-also"></a>Confira também
> [!div class="nextstepaction"]
> [Agentes virtuais do Power](/power-virtual-agents/fundamentals-what-is-power-virtual-agents)  

> [!div class="nextstepaction"]
> [Crie um chatbot para o Teams com agentes virtuais do Microsoft Power.](../bot-features.md#bots-and-the-microsoft-power-virtual-agents)  

> [!div class="nextstepaction"]
>  [Portal de Agentes Virtuais do Power](https://powervirtualagents.microsoft.com)

> [!div class="nextstepaction"]
> [Publicar seu bot agentes virtuais do Power](/power-virtual-agents/publication-fundamentals-publish-channels)

> [!div class="nextstepaction"]
> [Segurança e conformidade no Microsoft Teams](/MicrosoftTeams/security-compliance-overview).

## <a name="next-step"></a>Próxima etapa

> [!div class="nextstepaction"]
> [Criar assistente virtual](~/samples/virtual-assistant.md)

