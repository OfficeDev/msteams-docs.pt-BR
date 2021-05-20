---
title: Poste pedidos externos para Microsoft Teams com webhooks de entrada
author: laujan
description: como adicionar webhook de entrada para Teams app
keywords: equipes guias webhook de saída
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
# <a name="post-external-requests-to-teams-with-incoming-webhooks"></a>Poste pedidos externos para Teams com webhooks de entrada

## <a name="what-are-incoming-webhooks-in-teams"></a>O que são webhooks de entrada em Teams?

Webhooks de entrada são um tipo especial de Connector em Teams que fornecem uma maneira simples de um aplicativo externo compartilhar conteúdo em canais de equipe e são frequentemente usados como ferramentas de rastreamento e notificação. Teams fornece uma URL exclusiva para a qual você envia uma carga JSON com a mensagem que você deseja POSTAR, normalmente em um formato de cartão. Os cartões são recipientes de interface de usuário (Interface do Usuário) que contêm conteúdo e ações relacionadas a um único tópico e são uma maneira de apresentar dados de mensagens de forma consistente. Teams usa cartões dentro de três recursos:

* Bots
* Extensões de mensagens
* Conectores

## <a name="incoming-webhook-key-features"></a>Recursos-chave de webhook recebidos

| Recurso | Descrição |
| ------- | ----------- |
|Configuração escopo|Os webhooks de entrada são escopo e configurados no nível do canal. Por exemplo, os webhooks de saída são escopo e configurados no nível da equipe.|
|Definições de recursos seguras|As mensagens são formatadas como cargas JSON. Esta estrutura de mensagens declarativas impede a injeção de código malicioso, pois não há execução de código no cliente.|
|Suporte acionável de mensagens|Se você optar por enviar mensagens via cartões, você deve usar o formato **de cartão de mensagem acionável.** Cartões de mensagem acionáveis são suportados em todos os grupos Office 365, incluindo Teams. Aqui estão links para a referência do [cartão de mensagem acionável Legacy](/outlook/actionable-messages/message-card-reference) e o playground do cartão [mensagem](https://messagecardplayground.azurewebsites.net).|
|Suporte independente de mensagens HTTPS| As cartas são uma ótima maneira de apresentar informações de forma clara e consistente. Qualquer ferramenta ou estrutura que possa enviar solicitações HTTPS POST pode enviar mensagens para Teams através de um webhook de entrada.|
|Suporte de markdown|Todos os campos de texto em cartões de mensagens acionáveis suportam markdown básico. **Não use marcação HTML em seus cartões**. O HTML será ignorado e tratado como texto sem formatação.|

> [!Note]
> Teams bots, extensões de mensagens, webhooks de entrada e o Bot Framework suporta Cartões Adaptativos, uma estrutura de plataforma multi-cartão aberta. [Teams conectores](../../webhooks-and-connectors/how-to/connectors-creating.md) não suportam cartões adaptativos atualmente. No entanto, é possível criar um [fluxo](https://flow.microsoft.com/blog/microsoft-flow-in-microsoft-teams/) que poste Cartões Adaptativos em um canal Teams.

## <a name="add-an-incoming-webhook-to-a-teams-channel"></a>Adicione um webhook de entrada a um canal de Teams

> [!Important]  
> Se **as permissões de membros Configurações** da sua equipe  =>  permitirem que os membros criem, atualizem e removam  =>  **conectores,** qualquer membro da equipe poderá adicionar, modificar ou excluir um conector.

**Para adicionar um webhook de entrada**

1. Navegue até o canal onde deseja adicionar o webhook e selecione (&#8226;&#8226;&#8226;) *Mais opções* da barra de navegação superior.
1. Escolha **Conectores** no menu suspenso e procure por **Webhook de entrada**.
1. Selecione o botão **Configurar,** forneça um nome e, opcionalmente, carregue um avatar de imagem para o seu webhook.
1. A janela de diálogo apresentará uma URL exclusiva que irá mapear para o canal. Certifique-se de **copiar e salvar a URL**— você precisará fornecê-la ao serviço externo.
1. Selecione o botão **Fazer.** O webhook estará disponível no canal da equipe.

## <a name="remove-an-incoming-webhook-from-a-teams-channel"></a>Remova um webhook de entrada de um canal Teams

**Para remover um webhook de entrada**

1. Navegue até o canal onde o webhook foi adicionado e selecione (&#8226;&#8226;&#8226;) *Mais opções* da barra de navegação superior.
1. Escolha **Conectores** no menu suspenso.
1. À esquerda, em **Gerenciar,** escolha **Configurado**.
1. Selecione o *número Configurado* para ver uma lista de conectores atuais.
1. Selecione **Gerenciar** ao lado do conector que deseja excluir.
1. Selecione o botão **Remover** e você será apresentado com uma caixa de diálogo *Remover configuração.*
1. Opcionalmente, complete os campos da caixa de diálogo e as caixas de seleção antes de selecionar o botão **Remover.** O webhook será excluído do canal da equipe.

## <a name="distribution"></a>distribuição

Você tem três opções para distribuir seu webhook de entrada:

* Configure um webhook de entrada diretamente para sua equipe.
* Adicione uma página de configuração e enrole seu webhook de entrada em um [Conector O365](~/webhooks-and-connectors/how-to/connectors-creating.md)
* Embale e publique seu Conector como parte do envio [do AppSource.](~/concepts/deploy-and-publish/office-store-guidance.md)

## <a name="see-also"></a>Confira também

[Enviando mensagens para Conectores e Webhooks](~/webhooks-and-connectors/how-to/connectors-using.md)
