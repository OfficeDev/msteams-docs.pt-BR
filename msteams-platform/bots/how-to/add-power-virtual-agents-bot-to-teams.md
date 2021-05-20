---
title: Adicione Power Virtual Agents chatbot ao Teams
author: laujan
description: integrando um chatbot Power Virtual Agents na plataforma Teams
ms.topic: how-to
localization_priority: Normal
ms.author: lajanuar
ms.openlocfilehash: 2a8f9c23eaa1acf2555b91cc4caf8d0f3298c114
ms.sourcegitcommit: 51e4a1464ea58c254ad6bd0317aca03ebf6bf1f6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2021
ms.locfileid: "52566114"
---
# <a name="add-power-virtual-agents-chatbot"></a>Adicionar um chatbot de Agentes Virtuais de Energia 

Power Virtual Agents é uma solução de interface gráfica guiada sem código que capacita cada membro de sua equipe a criar chatbots ricos e conversacionais que se integram facilmente com a plataforma Teams. Todo o conteúdo de autoria em Power Virtual Agents renderiza naturalmente em Teams. Power Virtual Agents bots se envolvem com os usuários na tela de bate-papo nativa Teams. Os administradores de TI, analistas de negócios, especialistas em domínio e desenvolvedores de aplicativos qualificados podem projetar, desenvolver e publicar agentes virtuais inteligentes para Teams sem ter que configurar um ambiente de desenvolvimento. Eles podem criar um serviço web ou se registrar diretamente no Bot Framework. 

Este documento orienta você sobre como disponibilizar seu chatbot em Teams através do portal Power Virtual Agents e adicionar seu bot a Teams usando o App Studio. 

Power Virtual Agents permite criar chatbots poderosos que podem responder a perguntas feitas por seus clientes, outros funcionários ou visitantes do seu site ou serviço.

Esses bots podem ser criados facilmente sem a necessidade de cientistas de dados ou desenvolvedores.

> [!NOTE]
> Ao adicionar seu chatbot ao Microsoft Teams, alguns dos dados, como conteúdo de bot e conteúdo de bate-papo do usuário, são compartilhados com Microsoft Teams. Isso significa que seus dados fluem fora da conformidade da sua [organização e das fronteiras geográficas ou regionais.](/power-virtual-agents/data-location) <br/>

## <a name="make-your-chatbot-available-in-teams-through-the-power-virtual-agents-portal"></a>Disponibilize seu chatbot em Teams através do portal Power Virtual Agents

Para disponibilizar seu chatbot em Teams através do portal Power Virtual Agents, você deve executar as seguintes etapas do processo:

**Para disponibilizar o chatbot em Teams**

1. **Publique o conteúdo mais recente do bot**  
Depois de criar um chatbot no portal Power Virtual Agents, você deve publicar seu bot antes de Teams os usuários possam interagir com ele. Para obter mais informações, consulte [Publicar o conteúdo de bot mais recente](/power-virtual-agents/publication-fundamentals-publish-channels#publish-the-latest-bot-content).

   ![publicar no portal de agentes virtuais de poder](../../assets/images/pva-publish.png)

1. **Configure o canal Teams**  
Depois de publicar seu bot, adicione o canal Teams para disponibilizar o bot aos usuários Teams.

   ![canais no portal de agentes virtuais de poder](../../assets/images/pva-channels.png)

1. **Gere um ID de aplicativo para o seu chatbot**  
Depois de adicionar o canal Teams ao seu chatbot, um **ID do aplicativo** é gerado na caixa de diálogo. O App ID é um identificador exclusivo gerado pela Microsoft para o seu bot. Salve o App ID para criar um pacote de aplicativos para Teams.

## <a name="add-your-bot-to-teams-using-app-studio"></a>Adicione seu bot a Teams usando o App Studio

Se [o upload de aplicativos personalizados estiver ativado](/microsoftteams/admin-settings) em sua Teams instância, você pode usar Teams App Studio para carregar diretamente seu chatbot e começar a usá-lo imediatamente. Para compartilhar seu chatbot, você pode solicitar ao seu administrador para disponibilizar seu bot no catálogo do aplicativo de inquilino ou você pode enviar seu pacote de aplicativo para outros e pedir-lhes para carregá-lo independentemente.

1. **Instalar o App Studio no Teams**  
App Studio é um aplicativo Teams. Instale o App Studio na loja Teams que simplificou o processo de criação e registro de bots em Teams: 

   1. Selecione o ícone da loja de aplicativos Teams instância e procure por **App Studio**.

      &emsp;&emsp; <img  width="450px" alt="Finding App Studio in the Store" src="../../assets/images/get-started/app-studio-store.png"/>   

   1. Selecione o **azulejo App Studio** e selecione **Instalar** na caixa de diálogo pop-up.

      &emsp;&emsp; <img  width="450px" alt="Installing App Studio" src="../../assets/images/get-started/app-studio-install.png"/>

1. **Crie o manifesto do aplicativo Teams no App Studio**  
Bots em Teams são definidos por um arquivo JSON manifesto de aplicativo que fornece as informações básicas sobre seu bot e seus recursos. No **App Studio**, selecione o editor **Manifest** e selecione Criar um **novo aplicativo**.

    ![criar um novo aplicativo](../../assets/images/get-started/create-new-app.png)

1. **Adicione os detalhes do seu bot**  
Complete todos os campos necessários. Para obter uma descrição completa de cada campo, consulte [a definição do esquema manifesto](../../resources/schema/manifest-schema.md).

    ![adicionar detalhes do aplicativo](../../assets/images/get-started/add-app-details.png)

1. **Configure seu bot** Para configurar o bot, execute as seguintes etapas: 
     1. Abra a guia **Bots.** 
     1. Selecione **Configurar**  >  **bot existente** e digite o nome do seu bot.

   ![Configuração do bot](../../assets/images/get-started/bot-set-up.png) 

   A imagem a seguir mostra como configurar um bot existente:      

   ![configuração de bot existente](../../assets/images/get-started/existing-bot-set-up.png)
       
1. **Adicione seu ID de aplicativo**  
Para adicionar seu ID de aplicativo, execute as seguintes etapas:  
    1. Selecione **Conexão para um id de bot diferente** e cole o **Id** do aplicativo que você copiou anteriormente. 
    1. Selecione Salvar pessoal **do escopo**  >    >  .

    ![adicionar id aplicativo](../../assets/images/get-started/add-app-id.png)

1. **Adicione domínios válidos para o seu bot**  
Esta etapa só é necessária se o bot exigir que o usuário faça login. Selecione **Domínios e permissões** e no campo **Domínios Válidos,** forneça a seguinte entrada:

    ```bash
       token.botframework.com
    ```

1. **Teste e distribua seu bot**  
Abra a guia **Teste e distribua** e selecione **Instalar** para adicionar seu bot diretamente à sua Teams instância. Alternativamente, você pode baixar o pacote de aplicativos completo para compartilhar com Teams usuários ou fornecê-lo ao seu administrador para disponibilizar seu bot no catálogo do aplicativo de inquilino.

1. **Comece um bate-papo**   
O processo de configuração para adicionar seu bot de chat Power Virtual Agents a Teams está completo. Agora você pode começar uma conversa com seu bot em um bate-papo pessoal.

## <a name="see-also"></a>Confira também

- [Agentes virtuais do Power](/power-virtual-agents/fundamentals-what-is-power-virtual-agents)  

- [Crie um chatbot para Teams com a Microsoft Power Virtual Agents](../bot-features.md#bots-and-the-microsoft-power-virtual-agents).  

- [portal Power Virtual Agents](https://powervirtualagents.microsoft.com)

- [Publique seu bot de Power Virtual Agents](/power-virtual-agents/publication-fundamentals-publish-channels)

- [Segurança e conformidade em Microsoft Teams](/MicrosoftTeams/security-compliance-overview).

## <a name="next-step"></a>Próxima etapa

> [!div class="nextstepaction"]
> [Criar assistente virtual](~/samples/virtual-assistant.md)

