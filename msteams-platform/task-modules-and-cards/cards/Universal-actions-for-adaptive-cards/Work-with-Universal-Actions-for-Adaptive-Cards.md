---
title: Trabalhar com Ações Universais para Cartões Adaptáveis
description: Trabalhe com as Ações Universais para Cartões Adaptáveis.
ms.topic: conceptual
localization_priority: Normal
ms.openlocfilehash: 4361f1c7774837b728c6382df4e62e00ea912e35
ms.sourcegitcommit: 999f5c607671e088ea8a461fa7dbb63f8d61c39b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/25/2021
ms.locfileid: "52649696"
---
# <a name="work-with-universal-actions-for-adaptive-cards"></a>Trabalhar com Ações Universais para Cartões Adaptáveis

Ações universais para cartões adaptáveis fornece uma maneira de implementar cenários baseados em Cartão Adaptável para ambos, Teams e Outlook. Este documento aborda o seguinte:

* [Esquema usado para ações universais para cartões adaptáveis](#schema-for-universal-actions-for-adaptive-cards)
* [Modelo de atualização](#refresh-model)
* [`adaptiveCard/action` invocar atividade](#adaptivecardaction-invoke-activity)
* [Compatibilidade com versões anteriores](#backward-compatibility)

## <a name="quick-start-guide-to-leverage-universal-actions-for-adaptive-cards-in-teams"></a>Guia de início rápido para aproveitar ações universais para cartões adaptáveis no Teams

1. Substitua todas as instâncias `Action.Submit` de para atualizar um cenário existente no `Action.Execute` Teams.
2. Adicione uma cláusula ao seu Cartão Adaptável, se você quiser aproveitar o modelo de atualização automática ou se seu cenário `refresh` exigir Exibições Específicas do Usuário.

    >[!NOTE]
    > `userIds`Especifique a propriedade a ser identificada, quais usuários receberão atualizações automáticas.

3. Manipular `adaptiveCard/action` solicitações de invocação em seu bot.
4. Use o contexto da solicitação de invocação para responder com cartões criados especificamente para um usuário.

    > [!NOTE]
    > Sempre que o bot retorna um novo cartão como resultado do processamento de um , a resposta `Action.Execute` deve estar em conformidade com o formato de resposta.

## <a name="schema-for-universal-actions-for-adaptive-cards"></a>Esquema de ações universais para cartões adaptáveis

Ações universais para cartões adaptáveis é introduzido no esquema cartões adaptáveis versão 1.4. Para usar o Cartão Adaptável de forma eficaz, a propriedade do seu Cartão Adaptável deve `version` ser definida como 1,4.

> [!NOTE]
> Definir a propriedade como 1.4 torna seu Cartão Adaptável incompatível com clientes mais antigos das plataformas ou aplicativos, como Outlook e Teams, pois eles não suportam as Ações Universais para Cartões `version` Adaptáveis.

Se você definir a versão do cartão como menor que 1,4 e usar ambas as propriedades e `refresh` `Action.Execute` , o seguinte ocorrerá:

| Cliente | Comportamento |
| :-- | :-- |
| Teams | Seu cartão para de funcionar. O cartão não é atualizado `Action.Execute` e não é renderizada dependendo da versão do Teams cliente. Para garantir a máxima compatibilidade Teams, defina `Action.Execute` com um na propriedade `Action.Submit` fallback. |

Para obter mais informações sobre como dar suporte a clientes mais antigos, consulte [backward compatibility](#backward-compatibility).

### <a name="actionexecute"></a>Action.Exebonito

Ao ser autor de Cartões Adaptáveis, substitua `Action.Submit` e `Action.Http` por `Action.Execute` . O esquema para `Action.Execute` é semelhante ao de `Action.Submit` .

Para obter mais informações, [consulteAction.Exeesquema e propriedades atraentes.](/adaptive-cards/authoring-cards/universal-action-model#actionexecute)

Agora, você pode usar o modelo de atualização para permitir que cartões adaptáveis atualizem automaticamente.

## <a name="refresh-model"></a>Modelo de atualização

Para atualizar automaticamente seu Cartão Adaptável, defina sua propriedade, que incorpora uma `refresh` ação de tipo e uma `Action.Execute` `userIds` matriz.

Para obter mais informações, [consulte refresh schema and properties](/adaptive-cards/authoring-cards/universal-action-model#refresh-mechanism).

## <a name="user-ids-in-refresh"></a>IDs de usuário na atualização

Veja a seguir os recursos de UserIds na atualização:

* UserIds é uma matriz de MRI do usuário que faz parte da `refresh` propriedade em Cartões Adaptáveis.

* Se a propriedade list for especificada como na seção de atualização do cartão, o `userIds` cartão não será atualizado `userIds: []` automaticamente. Em vez disso, uma opção Refresh **Card** é exibida para o usuário no menu de ponto triplo na Web ou área de trabalho e no menu de contexto de pressão longa no celular, ou seja, Android ou iOS para atualizar manualmente o cartão.

* A propriedade UserIds é adicionada porque os canais Teams podem incluir um grande número de membros. Se todos os membros estão exibindo o canal ao mesmo tempo, uma atualização automática incondicional resulta em muitas chamadas simultâneas para o bot. Para evitar isso, a propriedade sempre deve ser incluída para identificar quais usuários devem obter uma atualização automática com um máximo de `userIds` *60 (60) MRIs* de usuário.

* Para obter mais informações sobre como você pode buscar Teams MRIs de usuário do membro da conversa para adicionar na lista userIds na seção de atualização do Cartão Adaptável, consulte [fetch roster](/microsoftteams/platform/bots/how-to/get-teams-context?tabs=dotnet#fetch-the-roster-or-user-profile)or user profile .

* Exemplo Teams MRI do usuário é`29:1bSnHZ7Js2STWrgk6ScEErLk1Lp2zQuD5H2qQ960rtvstKp8tKLl-3r8b6DoW0QxZimuTxk_kupZ1DBMpvIQQUAZL-PNj0EORDvRZXy8kvWk`

> [!NOTE]
> A propriedade é ignorada no Outlook e a `userIds` propriedade é sempre ativada `refresh` automaticamente. Não há nenhum problema de escala no Outlook porque os usuários visualizam o cartão em momentos diferentes.

A próxima etapa é usar a atividade `adaptiveCard/action` de invocação para entender qual solicitação deve ser feita após `Action.Execute` a execução.

## <a name="adaptivecardaction-invoke-activity"></a>`adaptiveCard/action` invocar atividade

Quando `Action.Execute` é executado no cliente, um novo tipo de atividade Invoke é feito no `adaptiveCard/action` bot.

Para obter mais informações, consulte [request format and properties for a typical invoke `adaptiveCard/action` activity](/adaptive-cards/authoring-cards/universal-action-model#request-format).

Para obter mais informações, consulte [formato de resposta e propriedades para uma atividade de `adaptiveCard/action` invocação típica com tipos de resposta com suporte.](/adaptive-cards/authoring-cards/universal-action-model#response-format)

Em seguida, você pode aplicar compatibilidade com versões anteriores a clientes mais antigos em diferentes plataformas e tornar seu Cartão Adaptável compatível.

## <a name="backward-compatibility"></a>Compatibilidade com versões anteriores

Ações universais para cartões adaptáveis permite definir propriedades que permitem compatibilidade com versões anteriores de Outlook e Teams.

### <a name="teams"></a>Teams

Para garantir a compatibilidade com versões anteriores dos Cartões Adaptáveis com versões mais antigas Teams, você deve incluir a propriedade e definir seu `fallback` valor como `Action.Submit` . Além disso, seu código de bot deve processar `Action.Execute` tanto quanto `Action.Submit` .

Para obter mais informações, consulte [backward compatibility on Teams](/adaptive-cards/authoring-cards/universal-action-model#teams).

## <a name="code-sample"></a>Exemplo de código

|Exemplo de nome | Descrição | . NETCore |
|----------------|-----------------|--------------|
| Teams de bufê | Crie um bot simples que aceite a ordem de alimentação usando Cartões Adaptáveis. |[View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/bot-teams-catering/csharp)|

## <a name="see-also"></a>Confira também

* [Ações de Cartão Adaptável em Teams](~/task-modules-and-cards/cards/cards-actions.md#adaptive-cards-actions)
* [Como os bots funcionam](/azure/bot-service/bot-builder-basics?view=azure-bot-service-4.0&preserve-view=true)
