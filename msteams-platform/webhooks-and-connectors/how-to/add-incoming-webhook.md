---
title: Postar solicitações externas para Microsoft Teams com webhooks de entrada
author: laujan
description: como adicionar webhook de entrada ao Teams app
keywords: teams tabs outgoing webhook
localization_priority: Normal
ms.topic: conceptual
ms.author: lajanuar
ms.openlocfilehash: bb2306cb57c069d3bed06702495da2775694643a
ms.sourcegitcommit: 51e4a1464ea58c254ad6bd0317aca03ebf6bf1f6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2021
ms.locfileid: "52566814"
---
# <a name="post-external-requests-to-teams-with-incoming-webhooks"></a>Postar solicitações externas para Teams com webhooks de entrada

## <a name="what-are-incoming-webhooks-in-teams"></a>O que são webhooks de entrada Teams?

Os webhooks de entrada são um tipo especial de Conector no Teams que fornecem uma maneira simples para um aplicativo externo compartilhar conteúdo em canais de equipe e são frequentemente usados como ferramentas de rastreamento e notificação. Teams fornece uma URL exclusiva para a qual você envia uma carga JSON com a mensagem que você deseja POSTAR, normalmente em um formato de cartão. Os cartões são contêineres de interface do usuário (interface do usuário) que contêm conteúdo e ações relacionadas a um único tópico e são uma maneira de apresentar dados de mensagem de forma consistente. Teams usa cartões em três recursos:

* Bots
* Extensões de mensagens
* Conectores

## <a name="incoming-webhook-key-features"></a>Recursos de chave de webhook de entrada

| Recurso | Descrição |
| ------- | ----------- |
|Configuração com escopo|Os webhooks de entrada são escopo e configurados no nível do canal. Por exemplo, os webhooks de saída são escopos e configurados no nível da equipe.|
|Definições de recursos seguros|As mensagens são formatadas como cargas JSON. Essa estrutura declarativa de mensagens impede a injeção de código mal-intencionado, pois não há nenhuma execução de código no cliente.|
|Suporte a mensagens a ações|Se você optar por enviar mensagens por meio de cartões, deverá usar o formato de cartão de mensagem a **actionable.** Os cartões de mensagem a ação são suportados em todos os grupos Office 365, incluindo Teams. Aqui estão links para a referência de cartão de mensagem [a ação herdado](/outlook/actionable-messages/message-card-reference) e o playground [de cartão de mensagem](https://messagecardplayground.azurewebsites.net).|
|Suporte independente de mensagens HTTPS| Os cartões são uma ótima maneira de apresentar informações de forma clara e consistente. Qualquer ferramenta ou estrutura que possa enviar solicitações HTTPS POST pode enviar mensagens para Teams por meio de um webhook de entrada.|
|Suporte a markdown|Todos os campos de texto em cartões de mensagens a ação suportam Markdown básico. **Não use marcação HTML em seus cartões.** O HTML será ignorado e tratado como texto sem formatação.|

> [!Note]
> Teams bots, extensões de mensagens, webhooks de entrada e a Estrutura de Bots suportam Cartões Adaptáveis, uma estrutura de plataforma aberta entre cartões. [Teams conectores](../../webhooks-and-connectors/how-to/connectors-creating.md) atualmente não suportam Cartões Adaptáveis. No entanto, é possível criar um [fluxo que](https://flow.microsoft.com/blog/microsoft-flow-in-microsoft-teams/) poste Cartões Adaptáveis em um canal Teams.

## <a name="add-an-incoming-webhook-to-a-teams-channel"></a>Adicionar um webhook de entrada a um Teams canal

> [!Important]  
> Se as permissões de membro da sua equipe Configurações Permitir que os membros criem, atualizem e removam conectores estão  =>    =>  **selecionados,** qualquer membro da equipe pode adicionar, modificar ou excluir um conector.

**Para adicionar um webhook de entrada**

1. Navegue até o canal onde você deseja adicionar o webhook e selecione (&#8226;&#8226;&#8226;) *Mais* Opções na barra de navegação superior.
1. Escolha **Conectores** no menu suspenso e pesquise por **Webhook de entrada.**
1. Selecione o **botão Configurar,** forneça um nome e, opcionalmente, carregue um avatar de imagem para seu webhook.
1. A janela de diálogo apresentará uma URL exclusiva que mapeará para o canal. Certifique-se de **copiar e salvar a URL**, você precisará fornecer para o serviço externo.
1. Selecione o **botão Done.** O webhook estará disponível no canal de equipe.

## <a name="remove-an-incoming-webhook-from-a-teams-channel"></a>Remover um webhook de entrada de um Teams canal

**Para remover um webhook de entrada**

1. Navegue até o canal onde o webhook foi adicionado e selecione (&#8226;&#8226;&#8226;) *Mais Opções* na barra de navegação superior.
1. Escolha **Conectores** no menu suspenso.
1. À esquerda, em **Gerenciar**, escolha **Configurado**.
1. Selecione o *número Configurado para* ver uma lista dos conectores atuais.
1. Selecione **Gerenciar** ao lado do conector que você deseja excluir.
1. Selecione o **botão Remover** e você receberá uma caixa de diálogo *Remover Configuração.*
1. Opcionalmente, conclua os campos e caixas de seleção da caixa de diálogo antes de selecionar o **botão Remover.** O webhook será excluído do canal de equipe.

## <a name="distribution"></a>Distribuição

Você tem três opções para distribuir seu webhook de entrada:

* Configurar um webhook de entrada diretamente para sua equipe.
* Adicione uma página de configuração e envolva seu webhook de entrada em um [Conector O365](~/webhooks-and-connectors/how-to/connectors-creating.md)
* Empacote e publique seu Conector como parte do envio [do AppSource.](~/concepts/deploy-and-publish/office-store-guidance.md)

## <a name="see-also"></a>Confira também

[Enviando mensagens para Conectores e Webhooks](~/webhooks-and-connectors/how-to/connectors-using.md)
