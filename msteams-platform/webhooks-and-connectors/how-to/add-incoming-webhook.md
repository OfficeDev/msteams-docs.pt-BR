---
title: Postar solicitações externas no Microsoft Teams com webhooks de entrada
author: laujan
description: adicionar webhook de entrada ao aplicativo teams
keywords: webhook de saída de guias do Teams*
ms.topic: conceptual
ms.author: lajanuar
ms.openlocfilehash: a05f9ec448a722f3d662a8323a40ebe6b2de1e27
ms.sourcegitcommit: 23ceb25d07a76f03ffe92cf1ac578b7c50b0bafc
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/07/2021
ms.locfileid: "49777914"
---
# <a name="post-external-requests-to-teams-with-incoming-webhooks"></a>Postar solicitações externas para o Teams com webhooks de entrada

## <a name="what-are-incoming-webhooks-in-teams"></a>O que são webhooks de entrada no Teams?

Os webhooks de entrada são um tipo especial de Conector no Teams que fornecem uma maneira simples para um aplicativo externo compartilhar conteúdo em canais de equipe e geralmente são usados como ferramentas de rastreamento e notificação. O Teams fornece uma URL exclusiva para a qual você envia uma carga JSON com a mensagem que você deseja POSTAR, normalmente em um formato de cartão. Cartões são contêineres de interface do usuário (UI) que contêm conteúdo e ações relacionadas a um único tópico e são uma maneira de apresentar dados de mensagens de maneira consistente. O Teams usa cartões em três recursos:

* Bots
* Extensões de mensagens
* Conectores

## <a name="incoming-webhook-key-features"></a>Recursos de chave de webhook de entrada

| Recurso | Descrição |
| ------- | ----------- |
|Configuração com escopo|Os webhooks de entrada têm escopo e são configurados no nível do canal (por exemplo, os webhooks de saída têm escopo e são configurados no nível da equipe).|
|Definições de recursos seguros|As mensagens são formatadas como cargas JSON. Essa estrutura declarativa de mensagens impede a injeção de código mal-intencionado, pois não há nenhuma execução de código no cliente.|
|Suporte a mensagens a actionable|Se você optar por enviar mensagens por meio de cartões, deverá usar o **formato de cartão de mensagem a actionable.** Cartões de mensagem a ação são suportados em todos os grupos do Office 365, incluindo o Teams. Aqui estão os links para a referência [de cartão de mensagem a ação herdado](/outlook/actionable-messages/message-card-reference) e o playground do cartão de [mensagem.](https://messagecardplayground.azurewebsites.net)|
|Suporte independente a mensagens HTTPS| Cartões são uma ótima maneira de apresentar informações de maneira clara e consistente. Qualquer ferramenta ou estrutura que possa enviar solicitações HTTPS POST pode enviar mensagens para o Teams por meio de um webhook de entrada.|
|Suporte a Markdown|Todos os campos de texto em cartões de mensagens a actionable suportam Markdown básico. **Não use marcação HTML em seus cartões.** O HTML será ignorado e tratado como texto sem formatação.|

> [!Note]
> Os bots do Teams, extensões de mensagens, webhooks de entrada e a Estrutura de Bot suportam Cartões Adaptáveis, uma estrutura de plataforma de cartão cruzado aberta. [No momento, os](../../webhooks-and-connectors/how-to/connectors-creating.md) conectores do Teams não são compatíveis com Cartões Adaptáveis. No entanto, é possível criar um fluxo [que](https://flow.microsoft.com/blog/microsoft-flow-in-microsoft-teams/) posta Cartões Adaptáveis em um canal do Teams.

## <a name="add-an-incoming-webhook-to-a-teams-channel"></a>Adicionar um webhook de entrada a um canal do Teams

> [!Important]  
> Se as permissões de Membro de Configurações da sua equipe Permitir que os membros criem, atualizem e removam conectores estão  =>    =>  **selecionadas,** qualquer membro da equipe pode adicionar, modificar ou excluir um conector.

1. Navegue até o canal em que deseja adicionar o webhook e selecione (&#8226;&#8226;&#8226;) *Mais Opções* na barra de navegação superior.
1. Choose **Connectors** from the drop-down menu and search for **Incoming Webhook**.
1. Selecione o **botão Configurar,** forneça um nome e, opcionalmente, carregue um avatar de imagem para seu webhook.
1. A janela de diálogo apresentará uma URL exclusiva que será mapeda para o canal. Certifique-se de **copiar e salvar a URL**— você precisará providelá-la para o serviço externo.
1. Selecione o **botão** Pronto. O webhook estará disponível no canal de equipe.

## <a name="remove-an-incoming-webhook-from-a-teams-channel"></a>Remover um webhook de entrada de um canal do Teams

1. Navegue até o canal em que o webhook foi adicionado e selecione (&#8226;&#8226;&#8226;) *Mais Opções* na barra de navegação superior.
1. Escolha **Conectores** no menu suspenso.
1. À esquerda, em **Gerenciar,** escolha **Configurado.**
1. Selecione o *número Configurado para* ver uma lista de seus conectores atuais.
1. Selecione **Gerenciar** ao lado do conector que você deseja excluir.
1. Selecione o **botão Remover** e você receberá uma caixa de diálogo *Remover* Configuração.
1. Opcionalmente, preencha os campos e caixas de seleção da caixa de diálogo antes de selecionar o **botão** Remover. O webhook será excluído do canal de equipe.

## <a name="distribution"></a>Distribuição

Você tem três opções para distribuir seu webhook de entrada:

* Configurar um webhook de entrada diretamente para sua equipe.
* Adicionar uma página de configuração e quebrar o webhook de entrada em um [conector do O365](~/webhooks-and-connectors/how-to/connectors-creating.md)
* Empacote e publique seu Conector como parte do envio [ao AppSource.](~/concepts/deploy-and-publish/office-store-guidance.md)

## <a name="learn-more"></a>Saiba mais

* [Enviar mensagens para Conectores e Webhooks](~/webhooks-and-connectors/how-to/connectors-using.md)
