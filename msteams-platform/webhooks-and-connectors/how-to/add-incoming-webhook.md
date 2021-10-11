---
title: Criar um Webhook de entrada
author: laujan
description: descreve como adicionar o Webhook de entrada ao Teams aplicativo e postar solicitações externas para Teams com webhooks de entrada
keywords: teams tabs outgoing webhook
ms.localizationpriority: medium
ms.topic: conceptual
ms.author: lajanuar
ms.openlocfilehash: 546ca7643ee64412dab6c383e4090dd631a643c8
ms.sourcegitcommit: c04a1a792773a9d5c61169c5702d94a8c478ad1c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/11/2021
ms.locfileid: "60260698"
---
# <a name="create-incoming-webhook"></a>Criar Webhook de entrada

O Webhook de entrada permite que todos os aplicativos externos compartilhem conteúdo em Teams canais. Esses webhooks são usados como ferramentas de rastreamento e notificação. Eles fornecem uma URL exclusiva, para a qual você envia uma carga JSON com uma mensagem no formato de cartão. Os cartões são contêineres de interface do usuário que incluem conteúdo e ações relacionadas a um único tópico. Teams cartões nos seguintes recursos:

* Bots
* Extensões de mensagens
* Conectores

## <a name="key-features-of-incoming-webhook"></a>Principais recursos do Webhook de entrada

A tabela a seguir fornece os recursos e a descrição do Webhook de entrada:

| Recursos | Descrição |
| ------- | ----------- |
|Cartões adaptáveis usando um Webhook de entrada|Cartões adaptáveis podem ser enviados por meio de Webhooks de entrada. Para obter mais informações, [consulte Send Adaptive Cards using Incoming Webhooks](../../webhooks-and-connectors/how-to/connectors-using.md#send-adaptive-cards-using-an-incoming-webhook).|
|Suporte a mensagens a ações|Os cartões de mensagem a ação são suportados em todos os grupos Office 365, incluindo Teams. Se você enviar mensagens por meio de cartões, deverá usar o formato de cartão de mensagem a ação. Para obter mais informações, consulte [referência de cartão de mensagem a actionable herdado](/outlook/actionable-messages/message-card-reference) e playground de cartão de [mensagem](https://messagecardplayground.azurewebsites.net).|
|Suporte independente de mensagens HTTPS|Os cartões fornecem informações de forma clara e consistente. Qualquer ferramenta ou estrutura que possa enviar solicitações HTTPS POST pode enviar mensagens para Teams por meio de um Webhook de entrada.|
|Suporte a markdown|Todos os campos de texto em cartões de mensagens a ação suportam Markdown básico. Não use marcação HTML em seus cartões. O HTML será ignorado e tratado como texto sem formatação.|
|Configuração com escopo|O Webhook de entrada tem escopo e configuração no nível do canal.|
|Definições de recursos seguros|As mensagens são formatadas como cargas JSON. Essa estrutura declarativa de mensagens impede a inserção de código mal-intencionado.|

> [!NOTE]
> * Teams bots, extensões de mensagens, Webhook de entrada e a Estrutura de Bot suportam Cartões Adaptáveis, uma estrutura de plataforma de cartão cruzado aberta. Atualmente, Teams [conectores não](../../webhooks-and-connectors/how-to/connectors-creating.md) suportam Cartões Adaptáveis. No entanto, é possível criar um [fluxo que](https://flow.microsoft.com/blog/microsoft-flow-in-microsoft-teams/) poste Cartões Adaptáveis em um canal Teams.
> * Para obter mais informações sobre cartões e webhooks, consulte [Cartões adaptáveis e Webhooks de entrada.](~/task-modules-and-cards/what-are-cards.md#adaptive-cards-and-incoming-webhooks)

## <a name="create-incoming-webhook"></a>Criar Webhook de entrada

**Para adicionar um Webhook de entrada a um Teams canal**

1. Vá para o canal onde você deseja adicionar o webhook e selecione &#8226;&#8226;&#8226; **mais opções** na barra de navegação superior.
1. Selecione **Conectores** no menu suspenso:

    ![Selecionar Conector](~/assets/images/connectors.png)

1. Pesquise **o Webhook de entrada** e selecione **Adicionar**.
1. Selecione **Configurar**, forneça um nome e carregue uma imagem para seu webhook, se necessário:

    ![Botão Configurar](~/assets/images/configure.png)

1. A janela de diálogo apresenta uma URL exclusiva que mapeia para o canal. Copie e salve a URL do webhook, para enviar informações para Microsoft Teams e selecione **Feito**:

    ![URL exclusiva](~/assets/images/url.png)

O webhook está disponível no canal Teams.

> [!NOTE]
> Em Teams, selecione **Configurações** Permissões de membro Permitir que os membros criem, atualizem e  >    >  **removam** conectores, para que qualquer membro da equipe possa adicionar, modificar ou excluir um conector.

## <a name="remove-incoming-webhook"></a>Remover Webhook de entrada

**Para remover um Webhook de entrada de um Teams canal**

1. Vá para o canal.
1. Selecione &#8226;&#8226;&#8226; **Mais opções** na barra de navegação superior.
1. Selecione **Conectores** no menu suspenso.
1. À esquerda, em **Gerenciar**, selecione **Configurado**.
1. Selecione **< *o 1>* Configurado para** ver uma lista dos conectores atuais:

    ![Webhook configurado](~/assets/images/configured.png)

1. Selecione **Gerenciar** ao lado do conector que você deseja remover:

    ![Gerenciar webhook](~/assets/images/manage.png)

1. Selecione **Remover**:

    ![Remover webhook](~/assets/images/remove.png)

    A **caixa de diálogo Remover Configuração** é exibida:

    ![Remover Configuração](~/assets/images/removeconfiguration.png)

1. Conclua os campos e caixas de seleção da caixa de diálogo e selecione **Remover**:

    ![Remover Final](~/assets/images/finalremove.png)

    O webhook é removido do Teams canal.

## <a name="see-also"></a>Confira também

* [Criar um Webhook de Saída](~/webhooks-and-connectors/how-to/add-outgoing-webhook.md)
* [Criar um conector do Office 365](~/webhooks-and-connectors/how-to/connectors-creating.md)
* [Criar e enviar mensagens](~/webhooks-and-connectors/how-to/connectors-using.md)
