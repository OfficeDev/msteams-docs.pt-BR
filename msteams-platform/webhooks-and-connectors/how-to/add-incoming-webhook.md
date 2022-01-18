---
title: Criar um webhook de entrada
author: laujan
description: descreva como adicionar Webhook de Entrada ao aplicativo Teams e postar solicitações externas ao Teams com webhooks de entrada
keywords: webhook de saída das guias do Teams
ms.localizationpriority: high
ms.topic: conceptual
ms.author: lajanuar
ms.openlocfilehash: 308eaf9f08e946f468f02d897ad556681d1cc832
ms.sourcegitcommit: 9e448dcdfd78f4278e9600808228e8158d830ef7
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/17/2022
ms.locfileid: "62059760"
---
# <a name="create-incoming-webhook"></a>Criar Webhooks de Entrada

O Webhook de Entrada permite que todos os aplicativos externos compartilhem conteúdo em canais do Teams. Esses webhooks são usados como ferramentas de acompanhamento e notificação. Eles fornecem uma URL exclusiva, para a qual você envia uma carga JSON com uma mensagem no formato de cartão. Os cartões são contêineres de interface do usuário que incluem conteúdo e ações relacionadas a um único tópico. As Teams usam cartões dentro dos seguintes recursos:

* Bots
* Extensões de mensagens
* Conectores

## <a name="key-features-of-incoming-webhook"></a>Principais recursos do Webhook de Entrada

A tabela a seguir fornece os recursos e a descrição do Webhook de Entrada:

| Recursos | Descrição |
| ------- | ----------- |
|Envie cartões adaptáveis usando um Webhook de Entrada|Cartões Adaptáveis pode ser enviado por meio de Webhooks de Entrada. Para obter mais informações, consulte [Enviar Cartões Adaptáveis usando Webhooks de Entrada](../../webhooks-and-connectors/how-to/connectors-using.md#send-adaptive-cards-using-an-incoming-webhook).|
|Suporte a mensagens acionáveis|Os cartões de mensagem a ação são suportados em todos os grupos do Office 365, incluindo o Teams. Se você enviar mensagens por meio de cartões, deverá usar o formato de cartão de mensagem acionável. Para mais informações, consulte o [legado de referência de cartões de mensagens acionáveis](/outlook/actionable-messages/message-card-reference) e [playground de cartões de mensagens](https://messagecardplayground.azurewebsites.net).|
|Suporte independente a mensagens HTTPS|Os cartões fornecem informações de forma clara e consistente. Qualquer ferramenta ou estrutura que possa enviar solicitações HTTPS POST pode enviar mensagens para o Teams por meio de um Webhook de Entrada.|
|Markdown compatível|Todos os campos de texto em cartões de mensagens acionáveis suportam Markdown básico. Não use a marcação HTML em seus cartões. O HTML será ignorado e tratado como texto sem formatação.|
|Configuração com escopo|O Webhook de Entrada tem escopo e está configurado no nível do canal.|
|Definições de recursos seguros|As mensagens são formatadas como cargas JSON. Essa estrutura declarativa de mensagens impede a inserção de código mal-intencionado.|

> [!NOTE]
> * Bots do Teams, extensões de mensagens, Webhook de entrada e Bot Framework suporte Cartões Adaptáveis. Cartões Adaptáveis é uma estrutura de plataforma de cartão cruzado aberta que pode ser usada em todas as plataformas, como Windows, Android, iOS e assim por diante. Atualmente, os [Conectores Teams](../../webhooks-and-connectors/how-to/connectors-creating.md) não suportam os Cartões Adaptáveis. No entando, é impossível criar um [fluxo](https://flow.microsoft.com/blog/microsoft-flow-in-microsoft-teams/) que publicam Cartões Adaptáveis para um canal Teams.
> * Para mais informações sobre cartões e webhooks, veja [Cartões Adaptáveis e Webhooks de Entrada](~/task-modules-and-cards/what-are-cards.md#adaptive-cards-and-incoming-webhooks).

## <a name="create-incoming-webhook"></a>Criar Webhooks de Entrada

**Para adicionar um Webhook de Entrada a um canal do Teams**

1. Vá até o canal onde você deseja adicionar o gancho da web e selecione &#8226;&#8226;&#8226; **Mais opções** a partir da barra de navegação superior.
1. Selecione **Conectadores** no menu suspenso:

    ![Selecionar conector](~/assets/images/connectors.png)

1. Pesquise para **Webhook de Entrada** e selecione **Adicionar**.
1. Selecionar **Configurar**, providenciar um nome, e atualize uma imagem para seu webhook se requerido:

    ![Botão configurar](~/assets/images/configure.png)

1. A janela de diálogo apresenta uma URL exclusiva que mapeia para o canal. Copie e salve a URL do webhook para enviar informações ao Microsoft Teams e selecione **Feito**:

    ![URL única](~/assets/images/url.png)

O webhook está disponível no canal do Teams.

Você pode criar e enviar mensagens acionáveis por meio do Webhook de Entrada ou do Conector do Office 365. Para obter mais informações, veja [Criar e enviar mensagens](~/webhooks-and-connectors/how-to/connectors-using.md).

> [!NOTE]
> No Teams, selecione **Definições** > **Permitir aos membros** > **criar, atualizar, e remover conectores**, para que qualquer membro da equipe possa adicionar, modificar ou excluir um conector.

## <a name="remove-incoming-webhook"></a>Remover Webhook de Entrada

**Para remover um Webhook de Entrada de um canal Teams**

1. Ir para o canal.
1. Selecione &#8226;&#8226;&#8226; **Mais opções** na barra de navegação superior.
1. Selecione **Conectores** de um menu suspenso.
1. No canto esquerdo, sob **Gerenciar**, selecione **Configurado**.
1. Selecione o **<*1*> Configurado** para ver uma lista de seus conectores atuais:

    ![Webhook configurado](~/assets/images/configured.png)

1. Selecione **Gerenciar** próximo ao conector que você deseja eliminar:

    ![Gerenciar webhook](~/assets/images/manage.png)

1. Selecione **Remover**:

    ![Remover webhook](~/assets/images/remove.png)

    A **Configuração de Remover** aparece na caixa de diálogo:

    ![Remover Configuração](~/assets/images/removeconfiguration.png)

1. Preencha os campos da caixa de diálogo e as caixas de seleção e selecione **Remover**:

    ![Remoção Final](~/assets/images/finalremove.png)

    O webhook é removido do canal do Teams.

## <a name="see-also"></a>Confira também

* [Criar um Webhook de Saída](~/webhooks-and-connectors/how-to/add-outgoing-webhook.md)
* [Criar um conector do Office 365](~/webhooks-and-connectors/how-to/connectors-creating.md)
* [Criar e enviar mensagens](~/webhooks-and-connectors/how-to/connectors-using.md)
* [Criar um botão Compartilhar para o Teams](../../concepts/build-and-test/share-to-teams.md#create-share-to-teams-button)
* [Integrar aplicativos Web](~/samples/integrate-web-apps-overview.md)
