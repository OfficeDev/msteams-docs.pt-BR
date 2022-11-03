---
title: Trabalhar com Ações Universais para Cartões Adaptáveis
description: Aprenda a trabalhar com as Ações Universais para Cartões Adaptáveis, incluindo esquema para UniversalActions para cartões adaptáveis, modelo de atualização e compatibilidade com atraso
ms.topic: conceptual
ms.localizationpriority: medium
ms.openlocfilehash: d723b565cadfacc550cd4fd9c8648149e9d164e2
ms.sourcegitcommit: c3601696cced9aadc764f1e734646ee7711f154c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/03/2022
ms.locfileid: "68833006"
---
# <a name="work-with-universal-actions-for-adaptive-cards"></a>Trabalhar com Ações Universais para Cartões Adaptáveis

Universal Actions for Adaptive Cards provide a way to implement Adaptive Card based scenarios for both, Teams and Outlook. This document covers the following topics:

* [Esquema usado em Ações Universais para Cartões Adaptáveis](#schema-for-universal-actions-for-adaptive-cards)
* [Modelo de atualização](#refresh-model)
* [`adaptiveCard/action` atividade de invocação](#adaptivecardaction-invoke-activity)
* [Compatibilidade com versões anteriores](#backward-compatibility)

## <a name="quick-start-guide-to-use-universal-actions-for-adaptive-cards-in-teams"></a>Guia de início rápido para usar Ações Universais para Cartões Adaptáveis no Teams

1. Substitua todas as instâncias de `Action.Submit` por `Action.Execute` para atualizar um cenário existente no Teams.
2. Adicione uma cláusula `refresh` ao seu Cartão Adaptável, se você desejar usar o modelo de atualização automática ou se seu cenário exigir Exibições Específicas do Usuário.

    >[!NOTE]
    > Especifique a `userIds` propriedade para identificar quais usuários recebem atualizações automáticas.

3. Manipule solicitações de invocação `adaptiveCard/action` em seu bot.
4. Use o contexto da solicitação de invocação para responder com cartões criados para um usuário.

    > [!NOTE]
    > Sempre que um bot retorna um novo cartão como resultado do processamento de um `Action.Execute`, a resposta deve estar de acordo com o formato de resposta.

## <a name="schema-for-universal-actions-for-adaptive-cards"></a>Esquema de Ações Universais para Cartões Adaptáveis

As Ações Universais para Cartões Adaptáveis são introduzidas no esquema de Cartões Adaptáveis versão 1.4. Para usar o Cartão Adaptável com eficiência, a propriedade `version` do seu Cartão Adaptável deve ser definida como 1.4.

> [!NOTE]
> Definir a propriedade `version` como 1.4 torna seu Cartão Adaptável incompatível com clientes mais antigos das plataformas ou aplicativos, como o Outlook e o Teams, pois eles não dão suporte às Ações Universais para Cartões Adaptáveis.

Se você definir a versão do cartão como menor que 1.4 e usar uma ou ambas, propriedade `refresh` e `Action.Execute`, ocorrerá o seguinte:

| Cliente | Comportamento |
| :-- | :-- |
| Teams | Seu cartão para de funcionar. O cartão não é atualizado e `Action.Execute` não é renderizado dependendo da versão do cliente do Teams. Para garantir a compatibilidade máxima no Teams, defina `Action.Execute` com um `Action.Submit` na propriedade de fallback. |

Para obter mais informações sobre como dar suporte a clientes mais antigos, consulte [compatibilidade com versões anteriores](#backward-compatibility).

### <a name="actionexecute"></a>Action.Execute

Ao criar Cartões Adaptáveis, substitua `Action.Submit` e `Action.Http` por `Action.Execute`. O esquema para `Action.Execute` é semelhante ao de `Action.Submit`.

Para obter mais informações, consulte o [esquema e as propriedades Action.Execute](/adaptive-cards/authoring-cards/universal-action-model#actionexecute).

Agora, você pode usar o modelo de atualização para permitir que Cartões Adaptáveis sejam atualizados automaticamente.

## <a name="refresh-model"></a>Modelo de atualização

Para atualizar automaticamente seu Cartão Adaptável, defina sua propriedade `refresh`, que insere uma ação do tipo `Action.Execute` e uma matriz `userIds`.

Para obter mais informações, consulte [atualizar esquema e propriedades](/adaptive-cards/authoring-cards/universal-action-model#refresh-mechanism).

## <a name="user-ids-in-refresh"></a>IDs de usuário na atualização

Estes são os recursos de UserIds na atualização:

* UserIds é uma matriz de MRIs de usuários, que faz parte da propriedade `refresh` em Cartões Adaptáveis.

* Se a `userIds` propriedade list for especificada como `userIds: []` na seção de atualização do cartão, o cartão não será atualizado automaticamente. Em vez disso, uma opção **Cartão de Atualização** é exibida para o usuário no menu de ponto triplo no cliente web ou área de trabalho do Teams e no menu de contexto de imprensa longa no Teams mobile, ou seja, Android ou iOS para atualizar manualmente o cartão. Como alternativa, você pode optar por ignorar `userIds` completamente a propriedade de atualização caso o cenário envolva <=60 membros em chats ou canais de grupo do Teams. O cliente do Teams invoca automaticamente chamadas de atualização para todos os usuários se o grupo ou canal tiver <=60 usuários.

* A propriedade userIds é adicionada porque os canais no Teams podem incluir um número grande de membros. Se todos os membros estão exibindo o canal ao mesmo tempo, uma atualização automática incondicional resultará em muitas chamadas simultâneas para o bot. A propriedade `userIds` deve sempre ser incluída para identificar quais usuários devem obter uma atualização automática com um máximo de *60 (sessenta) MRIs de usuário*.

* You can fetch Teams conversation member's user MRIs. For more information on how to add in userIds list in refresh section of Adaptive Card, see [fetch roster or user profile](/microsoftteams/platform/bots/how-to/get-teams-context?tabs=dotnet#fetch-the-roster-or-user-profile).

 Você pode obter a MRI do usuário para o canal, chat em grupo ou chat 1:1 usando o seguinte exemplo:

 1. Usando TurnContext  

     `userMRI= turnContext.Activity.From.Id`

 1. Usando o método GetMemberAsync
  
     `var member = await TeamsInfo.GetMemberAsync(turnContext, turnContext.Activity.From.Id, cancellationToken);var userMRI = member.Id;`

* Exemplo de MRI de usuário do Teams é `29:1bSnHZ7Js2STWrgk6ScEErLk1Lp2zQuD5H2qQ960rtvstKp8tKLl-3r8b6DoW0QxZimuTxk_kupZ1DBMpvIQQUAZL-PNj0EORDvRZXy8kvWk`

> [!NOTE]
> A propriedade `userIds` é ignorada no Outlook e a propriedade `refresh` é sempre ativada automaticamente. Não há nenhum problema de escala no Outlook porque os usuários exibem o cartão em momentos diferentes.

A próxima etapa é usar a atividade de inovação `adaptiveCard/action` para entender qual solicitação deve ser feita depois que `Action.Execute` é executado.

## <a name="adaptivecardaction-invoke-activity"></a>`adaptiveCard/action` atividade de invocação

Quando `Action.Execute` é executado no cliente, um novo tipo de Atividade de invocação `adaptiveCard/action` é realizada no bot.

Para obter mais informações, consulte [formato da solicitação e propriedades de uma atividade de invocação`adaptiveCard/action` típica ](/adaptive-cards/authoring-cards/universal-action-model#request-format).

Para obter mais informações, consulte [formato de resposta e propriedade de uma atividade de invocação típica `adaptiveCard/action` com tipos de resposta com suporte](/adaptive-cards/authoring-cards/universal-action-model#response-format).

Em seguida, você pode aplicar a compatibilidade com versões anteriores a clientes mais antigos em diferentes plataformas e tornar seu Cartão Adaptável compatível.

## <a name="backward-compatibility"></a>Compatibilidade com versões anteriores

As Ações Universais para Cartões Adaptáveis permitem definir propriedades que habilitam a compatibilidade com versões anteriores do Outlook e do Teams.

### <a name="teams"></a>Teams

To ensure backward compatibility of your Adaptive Cards with older versions of Teams, you must include the `fallback` property and set its value to `Action.Submit`. Also, your bot code must process both `Action.Execute` and `Action.Submit`.

Para obter mais informações, consulte [compatibilidade com versões anteriores no Teams](/adaptive-cards/authoring-cards/universal-action-model#teams).

## <a name="code-samples"></a>Exemplos de código

|Nome do exemplo | Descrição | .NETCore | Node.js |
|----------------|-----------------|--------------|--------------|
| Bot de refeições do Teams | Crie um bot que aceite a ordem dos alimentos usando Cartões Adaptáveis. |[Exibir](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/bot-teams-catering/csharp)| NA |
| Cartões Adaptáveis de Fluxos de Trabalho Sequenciais | Demonstre como implementar Fluxos de Trabalho Sequenciais, Exibições Específicas do Usuário e Cartões Adaptáveis atualizados em bots. | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/bot-sequential-flow-adaptive-cards/csharp) | [Exibir](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/bot-sequential-flow-adaptive-cards/nodejs) |

## <a name="see-also"></a>Confira também

* [Ações de Cartão Adaptável no Teams](~/task-modules-and-cards/cards/cards-actions.md#adaptive-cards-actions)
* [Como os bots funcionam](/azure/bot-service/bot-builder-basics?view=azure-bot-service-4.0&preserve-view=true)
* [Fluxos de Trabalho Sequenciais](~/task-modules-and-cards/cards/universal-actions-for-adaptive-cards/sequential-workflows.md)
* [Cartões atualizados](~/task-modules-and-cards/cards/universal-actions-for-adaptive-cards/up-to-date-views.md)
* [Comentários de preenchimento do formulário](~/bots/how-to/conversations/conversation-messages.md#form-completion-feedback)
