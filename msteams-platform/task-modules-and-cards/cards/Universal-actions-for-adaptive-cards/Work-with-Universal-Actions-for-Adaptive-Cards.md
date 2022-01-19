---
title: Trabalhar com Ações Universais para Cartões Adaptáveis
description: Aprenda a trabalhar com as Ações Universais para Cartões Adaptáveis, incluindo Esquema para UniversalActions para cartões adaptáveis, modelo de atualização e compatibilidade com códigos.
ms.topic: conceptual
ms.localizationpriority: medium
ms.openlocfilehash: 6a7160e1aa2dff6500335dc6b8557fcd94e836d8
ms.sourcegitcommit: c65a868744e4108b5d786de2350981e3f1f05718
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/19/2022
ms.locfileid: "62080950"
---
# <a name="work-with-universal-actions-for-adaptive-cards"></a>Trabalhar com Ações Universais para Cartões Adaptáveis

Ações universais para cartões adaptáveis fornecem uma maneira de implementar cenários baseados em Cartão Adaptável para ambos, Teams e Outlook. Este documento aborda os seguintes tópicos:

* [Esquema usado em Ações Universais para Cartões Adaptáveis](#schema-for-universal-actions-for-adaptive-cards)
* [Modelo de atualização](#refresh-model)
* [`adaptiveCard/action` atividade de invocação](#adaptivecardaction-invoke-activity)
* [Compatibilidade com versões anteriores](#backward-compatibility)

## <a name="quick-start-guide-to-use-universal-actions-for-adaptive-cards-in-teams"></a>Guia de início rápido para usar Ações Universais para Cartões Adaptáveis Teams

1. Substitua todas as instâncias de `Action.Submit` por `Action.Execute` para atualizar um cenário existente no Teams.
2. Adicione uma cláusula ao seu Cartão Adaptável, se você quiser usar o modelo de atualização automática ou se seu cenário `refresh` exigir Exibições Específicas do Usuário.

    >[!NOTE]
    > Especifique a propriedade `userIds` para identificar quais usuários obtêm atualizações automáticas.

3. Manipule solicitações de invocação `adaptiveCard/action` em seu bot.
4. Use o contexto da solicitação de invocação para responder com cartões criados para um usuário.

    > [!NOTE]
    > Sempre que um bot retorna um novo cartão como resultado do processamento de um `Action.Execute`, a resposta deve estar de acordo com o formato de resposta.

## <a name="schema-for-universal-actions-for-adaptive-cards"></a>Esquema de Ações Universais para Cartões Adaptáveis

Ações universais para cartões adaptáveis são introduzidas no esquema cartões adaptáveis versão 1.4. Para usar o Cartão Adaptável com eficiência, a propriedade `version` do seu Cartão Adaptável deve ser definida como 1.4.

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

* UserIds é uma matriz de MRIs de usuário, que faz parte `refresh` da propriedade em Cartões Adaptáveis.

* Se a propriedade de lista `userIds` for especificada como `userIds: []` na seção de atualização do cartão, o cartão não será atualizado automaticamente. Em vez disso, uma opção **Atualizar Cartão** é exibida para o usuário no menu de três pontos na Web ou área de trabalho e no menu de contexto de pressionamento longo no celular, ou seja, Android ou iOS para atualizar manualmente o cartão.

* A propriedade userIds é adicionada porque os canais no Teams podem incluir um número grande de membros. Se todos os membros estão exibindo o canal ao mesmo tempo, uma atualização automática incondicional resultará em muitas chamadas simultâneas para o bot. A propriedade sempre deve ser incluída para identificar quais usuários devem obter uma atualização automática com um máximo de `userIds` *60 (60) MRIs* de usuário.

* Você pode buscar Teams MRIs de usuário do membro da conversa. Para obter mais informações sobre como adicionar na lista userIds na seção de atualização do Cartão Adaptável, consulte [fetch roster or user profile](/microsoftteams/platform/bots/how-to/get-teams-context?tabs=dotnet#fetch-the-roster-or-user-profile).

 Você pode obter a MRI do usuário para canal, Chat de Grupo ou chat 1:1 usando o exemplo a seguir:

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

Ações universais para cartões adaptáveis permitem definir propriedades que permitem compatibilidade com versões anteriores de Outlook e Teams.

### <a name="teams"></a>Teams

Para garantir a compatibilidade com versões anteriores do Teams nos Cartões Adaptáveis, você deve incluir a propriedade `fallback` e definir seu valor como `Action.Submit`. Além disso, o código do bot deve processar `Action.Execute` e `Action.Submit`.

Para obter mais informações, consulte [compatibilidade com versões anteriores no Teams](/adaptive-cards/authoring-cards/universal-action-model#teams).

## <a name="code-samples"></a>Exemplos de código

|Nome do exemplo | Descrição | .NETCore | Node.js |
|----------------|-----------------|--------------|--------------|
| Bot de refeições do Teams | Crie um bot que aceite a ordem de alimentação usando Cartões Adaptáveis. |[Exibir](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/bot-teams-catering/csharp)| Ainda não disponível |
| Cartões adaptáveis de fluxos de trabalho sequenciais | Demonstre como implementar fluxos de trabalho sequenciais, exibições específicas do usuário e cartões adaptáveis atualizados em bots. | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/bot-sequential-flow-adaptive-cards/csharp) | [Exibir](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/bot-sequential-flow-adaptive-cards/nodejs) |

## <a name="see-also"></a>Confira também

* [Ações de Cartão Adaptável no Teams](~/task-modules-and-cards/cards/cards-actions.md#adaptive-cards-actions)
* [Como os bots funcionam](/azure/bot-service/bot-builder-basics?view=azure-bot-service-4.0&preserve-view=true)
* [Fluxos de Trabalho Sequenciais](~/task-modules-and-cards/cards/universal-actions-for-adaptive-cards/sequential-workflows.md)
* [Cartões atualizados](~/task-modules-and-cards/cards/universal-actions-for-adaptive-cards/up-to-date-views.md)
* [Comentários sobre a conclusão do formulário](~/bots/how-to/conversations/conversation-messages.md#form-completion-feedback)