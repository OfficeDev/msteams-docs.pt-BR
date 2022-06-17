---
title: Criar um webhook de entrada
author: laujan
description: Neste módulo, saiba como adicionar o Webhook de Entrada ao aplicativo do Teams e postar quaisquer solicitações externas para o Teams usando-o
ms.localizationpriority: high
ms.topic: conceptual
ms.author: lajanuar
ms.openlocfilehash: 5374b9327abb15949a31ab47443c273a111ad7b9
ms.sourcegitcommit: ca84b5fe5d3b97f377ce5cca41c48afa95496e28
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/17/2022
ms.locfileid: "66142189"
---
# <a name="create-an-incoming-webhook"></a>Criar um webhook de entrada

Um Webhook de Entrada permite que aplicativos externos compartilhem conteúdos nos canais do Microsoft Teams. Os webhooks são usados como ferramentas para rastrear e notificar. Os webhooks fornecem uma URL exclusiva para enviar uma carga JSON com uma mensagem no formato de cartão. Os cartões são contêineres de interface do usuário que incluem conteúdo e ações relacionadas a um único tópico. Você pode usar os cartões nos seguintes recursos:

* Bots
* Extensões de mensagens
* Conectores

## <a name="key-features-of-an-incoming-webhook"></a>Principais recursos de um Webhook de Entrada

A tabela a seguir fornece os recursos e a descrição de um Webhook de Entrada:

| Recursos | Descrição |
| -------- | ----------- |
|Envie cartões adaptáveis usando um Webhook de Entrada | Cartões Adaptáveis pode ser enviado por meio de Webhooks de Entrada. Para obter mais informações, consulte [Enviar Cartões Adaptáveis usando Webhooks de Entrada](../../webhooks-and-connectors/how-to/connectors-using.md#send-adaptive-cards-using-an-incoming-webhook).|
|Suporte a mensagens acionáveis|Os cartões de mensagem a ação são suportados em todos os grupos do Office 365, incluindo o Teams. Se você enviar mensagens por meio de cartões, deverá usar o formato de cartão de mensagem acionável. Para mais informações, consulte o [legado de referência de cartões de mensagens acionáveis](/outlook/actionable-messages/message-card-reference) e [playground de cartões de mensagens](https://messagecardplayground.azurewebsites.net).|
|Suporte independente a mensagens HTTPS|Os cartões fornecem informações de forma clara e consistente. Qualquer ferramenta ou estrutura que possa enviar solicitações HTTPS POST pode enviar mensagens para o Teams por meio de um Webhook de Entrada.|
|Markdown compatível|Todos os campos de texto em cartões de mensagens acionáveis suportam Markdown básico. Não use a marcação HTML em seus cartões. O HTML será ignorado e tratado como texto sem formatação.|
|Configuração com escopo|O Webhook de Entrada tem escopo e está configurado no nível do canal.|
|Definições de recursos seguros|As mensagens são formatadas como cargas JSON. Essa estrutura declarativa de mensagens impede a inserção de código mal-intencionado.|

<!--- TBD: A note should be short and eye-catching. No need to put a list item inside a Note or any admonition for that matter. Re-write the below list item.
--->

> [!NOTE]
>
> * Bots do Teams, extensões de mensagens, Webhook de entrada e Bot Framework suporte a Cartões Adaptáveis. Os Cartões Adaptáveis são uma estrutura de plataforma de cartão cruzado aberta que é usada em todas as plataformas, como Windows, Android, iOS e assim por diante. Atualmente, os [Conectores Teams](../../webhooks-and-connectors/how-to/connectors-creating.md) não suportam os Cartões Adaptáveis. No entando, é impossível criar um [fluxo](https://flow.microsoft.com/blog/microsoft-flow-in-microsoft-teams/) que publicam Cartões Adaptáveis para um canal Teams.
> * Para mais informações sobre cartões e webhooks, veja [Cartões Adaptáveis e Webhooks de Entrada](~/task-modules-and-cards/what-are-cards.md#adaptive-cards-and-incoming-webhooks).

## <a name="create-an-incoming-webhook"></a>Criar um webhook de entrada

Para adicionar um Webhook de Entrada a um canal do Teams, siga as seguintes etapas:

1. Abra o canal ao qual você deseja adicionar o gancho da web e selecione &#8226;&#8226;&#8226; **Mais opções** a partir da barra de navegação superior.
1. Selecione **Conectadores** no menu suspenso:

    ![Selecionar conector](~/assets/images/connectors.png)

1. Pesquise para **Webhook de Entrada** e selecione **Adicionar**.
1. Selecionar **Configurar**, providenciar um nome, e atualize uma imagem para seu webhook se necessário:

    ![Botão configurar](~/assets/images/configure.png)

1. Copie e salve a URL exclusiva do webhook presente na janela de diálogo. A URL mapeia o canal e você pode usá-la para enviar informações ao Teams. Selecione **Concluído**.

    ![URL única](~/assets/images/url.png)

O webhook está disponível no canal do Teams.

Você pode criar e enviar mensagens acionáveis por meio do Webhook de Entrada ou do Conector do Office 365. Para obter mais informações, veja [Criar e enviar mensagens](~/webhooks-and-connectors/how-to/connectors-using.md).

> [!NOTE]
> No Teams, selecione **Definições** > **Permitir aos membros** > **criar, atualizar, e remover conectores**, para que qualquer membro da equipe possa adicionar, modificar ou excluir um conector.

## <a name="remove-an-incoming-webhook"></a>Remover um Webhook de Entrada

Para remover um Webhook de Entrada de um canal do Teams, siga as seguintes etapas:

1. Abra o canal e selecione &#8226;&#8226;&#8226; **Mais opções** na barra de navegação superior.
1. Selecione **Conectores** de um menu suspenso.
1. Selecione **Configurado** em **Gerenciar**.
1. Selecione o **<*1*> Configurado** para ver uma lista de seus conectores atuais:

    ![Webhook configurado](~/assets/images/configured.png)

1. Selecione **Gerenciar** para o conector que você deseja eliminar:

    ![Gerenciar webhook](~/assets/images/manage.png)

1. Selecione **Remover** para exibir a caixa de diálogo **Remover Configuração**.

    ![Remover Configuração](~/assets/images/removeconfiguration.png)

1. Preencha os campos da caixa de diálogo e as caixas de seleção e selecione **Remover**.

    ![Remoção Final](~/assets/images/finalremove.png)

## <a name="code-sample"></a>Exemplo de código

| Nome de exemplo           | Descrição | C#    | Node.js   |
|:---------------------|:--------------|:---------|:--------|
|Webhook de entrada|Este código de exemplo demonstra como enviar o cartão usando um webhook de entrada. |[View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/incoming-webhook/csharp)|[Exibir](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/incoming-webhook/nodejs) |

## <a name="see-also"></a>Confira também

* [Criar um Webhook de Saída](~/webhooks-and-connectors/how-to/add-outgoing-webhook.md)
* [Criar um conector do Office 365](~/webhooks-and-connectors/how-to/connectors-creating.md)
* [Criar e enviar mensagens](~/webhooks-and-connectors/how-to/connectors-using.md)
* [Compartilhar no Teams a partir de aplicativos Web](~/concepts/build-and-test/share-to-teams-from-web-apps.md)
* [Integrar aplicativos Web](~/samples/integrate-web-apps-overview.md)
