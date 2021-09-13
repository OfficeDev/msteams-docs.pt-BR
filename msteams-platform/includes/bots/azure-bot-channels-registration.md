---
title: Registro de canal bot do Azure
description: descreve os canais bot do Azure para registro
localization_priority: Normal
ms.topic: overview
ms.author: surbhigupta12
ms.openlocfilehash: 96d7ed857074547d0c3da5b412b8065d063f3a3100da6a7431fd65879bfa91ff
ms.sourcegitcommit: 3ab1cbec41b9783a7abba1e0870a67831282c3b5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/07/2021
ms.locfileid: "57703693"
---
1. No portal [do Azure](https://ms.portal.azure.com/#home), em Serviços do Azure, selecione **Criar um recurso**.
1. Na caixa de pesquisa, digite "bot". E na lista lista listada, selecione **Registro de Canais de Bot**.
1. Selecione o **botão Criar.**
1. Na folha **Registro de Canal** bot, forneça as informações solicitadas sobre seu bot.
1. Deixe a **caixa de ponto de extremidade** Mensagens vazia por enquanto, você inserirá a URL necessária após a implantação do bot. A imagem a seguir mostra um exemplo das configurações de registro:

    ![registro de canais de aplicativo bot](../../assets/images/authentication/auth-bot-channels-registration.png)

1. Clique **em ID e senha do** Aplicativo Microsoft e crie **Novo**.

    ![Criar a ID do Aplicativo Microsoft ](../../assets/images/authentication/CreateMicrosoftAppID.png) ![ Criar nova ID do Aplicativo Microsoft](../../assets/images/authentication/CreateNewMicrosoftAppID.png)    

1. Clique **em Criar ID do Aplicativo no** link Portal de Registro de Aplicativos.

   ![Registros de aplicativos](../../assets/images/authentication/AppRegistration.png)
   
1. Na janela de registro **do aplicativo exibido,** clique na guia **Novo registro** no canto superior esquerdo.
1. Insira o nome do aplicativo bot que você está registrando, nós utilizamos *BotTeamsAuth* (você precisa selecionar seu próprio nome exclusivo).
1. Para os **tipos de conta** com suporte, selecione Contas em qualquer diretório organizacional (Qualquer diretório do *Azure AD - Multitenant) e contas pessoais da Microsoft (por exemplo, Skype, Xbox)*.
1. Clique no **botão Registrar.** Depois de concluído, o Azure exibe a página *Visão* Geral do aplicativo.
1. Copie e salve em um arquivo o valor da **ID do** aplicativo (cliente).
1. No painel esquerdo, clique em **Certificado e segredos.**
    1. Em *Segredos do Cliente,* clique **em Novo segredo do cliente.**
    1. Adicione uma descrição para identificar esse segredo de outras pessoas que talvez você precise criar para este aplicativo.
    1. Set *Expires* to your selection.
    1. Clique em **Adicionar**.
    1. Copie o segredo do cliente e salve-o em um arquivo.
1. Volte para a janela **Registro** do Canal bot  e copie a *ID* do aplicativo e o segredo do cliente nas caixas **ID** do Aplicativo Microsoft e **Senha,** respectivamente.
1. Clique em **OK**.
1. Por fim, clique em **Criar**.

Depois que o Azure tiver criado o recurso de registro, ele será incluído na lista de grupos de recursos.  

![grupo de registro de canais de aplicativo bot](~/assets/images/authentication/auth-bot-channels-registration-group.PNG)

Depois que o registro de canais de bot for criado, você precisará habilitar o Teams canal.

1. No portal [do Azure](https://ms.portal.azure.com/#home), em serviços do Azure, selecione o **Registro** de Canal bot que você acabou de criar.
1. No painel esquerdo, clique em **Canais**.
1. Clique no Microsoft Teams e escolha **Salvar**.
