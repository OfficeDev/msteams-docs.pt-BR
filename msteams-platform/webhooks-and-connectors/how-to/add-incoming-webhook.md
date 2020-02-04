---
title: Postar solicitações externas para o Microsoft Teams com WebHooks de entrada
author: laujan
description: ''
keywords: guias do Microsoft Teams saída de webhook *
ms.topic: conceptual
ms.author: laujan
ms.openlocfilehash: c2b3f5dd581441f89aff344c35fe7e110d4d2e68
ms.sourcegitcommit: 4329a94918263c85d6c65ff401f571556b80307b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/01/2020
ms.locfileid: "41672886"
---
# <a name="post-external-requests-to-teams-with-incoming-webhooks"></a>Postar solicitações externas para o Microsoft Teams com WebHooks de entrada

## <a name="what-are-incoming-webhooks-in-teams"></a>O que são WebHooks de entrada no Microsoft Teams?

Os WebHooks de entrada são um tipo especial de conector no Microsoft Teams que oferecem uma maneira simples para um aplicativo externo compartilhar conteúdo em canais de equipe e é freqüentemente usado como ferramentas de rastreamento e de notificação. O Microsoft Teams fornece uma URL exclusiva para a qual você envia uma carga JSON com a mensagem que você deseja postar, normalmente em um formato de cartão. Os cartões são contêineres de interface do usuário (UI) que contêm conteúdo e ações relacionadas a um único tópico e são uma maneira de apresentar dados de mensagens de forma consistente. O Microsoft Teams usa cartões dentro de três recursos:

* Bots
* Extensões de Mensagens
* Conectores

## <a name="incoming-webhook-key-features"></a>Recursos principais de webhook de entrada

| Recurso | Descrição |
| ------- | ----------- |
|Configuração com escopo|Os WebHooks de entrada são delimitados e configurados no nível do canal (por exemplo, os WebHooks de saída têm escopo e estão configurados no nível da equipe).|
|Definições de recursos seguros|As mensagens são formatadas como cargas JSON. Essa estrutura de mensagens declarativa impede a injeção de código mal-intencionado, já que não há execução de código no cliente.|
|Suporte a mensagens acionáveis|Se você optar por enviar mensagens por meio de cartões, deverá usar o formato de **cartão de mensagem acionável** . Cartões de mensagens acionáveis são compatíveis com todos os grupos do Office 365, incluindo o Teams. Aqui estão os links para a [referência de cartão de mensagem acionável herdada](/outlook/actionable-messages/message-card-reference) e o [cartão de mensagens playground](https://messagecardplayground.azurewebsites.net).|
|Suporte a mensagens HTTPS independentes| Os cartões são uma ótima maneira de apresentar informações de forma clara e consistente. Qualquer ferramenta ou estrutura que possa enviar solicitações HTTP POST poderá enviar mensagens ao Microsoft Teams por meio de um webhook de entrada.|
|Redução do suporte|Todos os campos de texto em cartões de mensagens acionáveis dão suporte à redução básica. **Não use marcação HTML em seus cartões**. O HTML será ignorado e tratado como texto sem formatação.|

> [!Note]  
> Os bots do Microsoft Teams, as extensões de mensagens e a estrutura de bot dão suporte a cartões adaptáveis, uma estrutura de plataforma de cartão cruzado aberto. No momento, os conectores do Teams não dão suporte a cartões adaptáveis. No entanto, é possível criar um [fluxo](https://flow.microsoft.com/blog/microsoft-flow-in-microsoft-teams/) que posta cartões adaptáveis em um canal do teams.

## <a name="add-an-incoming-webhook-to-a-teams-channel"></a>Adicionar um webhook de entrada a um canal do teams

> [!Important]  
> Se as **configurações** => de**Membros** => da equipe**permitir que os membros criem, atualizem e removerem conectores** estiverem selecionados, qualquer membro da equipe poderá adicionar, modificar ou excluir um conector.

1. Navegue até o canal onde você deseja adicionar o webhook e selecione (&#8226;&#8226;&#8226;) *mais opções* da barra de navegação superior.
1. Escolha **conectores** no menu suspenso e procure **webhook de entrada**.
1. Selecione o botão **Configurar** , forneça um nome e, opcionalmente, carregue um avatar de imagem para o seu webhook.
1. A janela de diálogo apresentará uma URL exclusiva que será mapeada para o canal. Certifique-se de **copiar e salvar a URL**, você precisará fornecer o serviço de fora.
1. Selecione o botão **concluído** . O webhook estará disponível no canal de equipe.

## <a name="remove-an-incoming-webhook-from-a-teams-channel"></a>Remover um webhook de entrada de um canal do teams

1. Navegue até o canal onde o webhook foi adicionado e selecione (&#8226;&#8226;&#8226;) *mais opções* da barra de navegação superior.
1. Escolha **conectores** no menu suspenso.
1. À esquerda, em **gerenciar**, escolha **configurado**.
1. Selecione o *número configurado* para ver uma lista de seus conectores atuais.
1. Selecione **gerenciar** ao lado do conector que você deseja excluir.
1. Selecione o botão **remover** e será exibida uma caixa de diálogo *remover configuração* .
1. Opcionalmente, preencha os campos de caixa de diálogo e caixas de seleção antes de selecionar o botão **remover** . O webhook será excluído do canal de equipe.

## <a name="distribution"></a>Distribuição

Você tem três opções para distribuir seu webhook de entrada:

* Configure um webhook de entrada diretamente para sua equipe.
* Adicionar uma página de configuração e quebrar seu webhook de entrada em um [conector do O365](~/webhooks-and-connectors/how-to/connectors-creating.md)
* Empacote e publique seu conector como parte do seu envio do [AppSource](~/concepts/deploy-and-publish/office-store-guidance.md) .

## <a name="learn-more"></a>Saiba mais

* [Enviar mensagens para conectores e WebHooks](~/webhooks-and-connectors/how-to/connectors-using.md)