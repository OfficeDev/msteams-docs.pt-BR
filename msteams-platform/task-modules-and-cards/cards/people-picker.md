---
title: Seletor de Pessoas em Cartões Adaptáveis
description: Descreve como usar o controle Seletor de Pessoas em Cartões Adaptáveis
localization_priority: Normal
keywords: Seletor de Pessoas de Cartões Adaptáveis
ms.topic: reference
author: Rajeshwari-v
ms.author: surbhigupta
ms.openlocfilehash: 8a78be74d8142600ccc08093744491a19900e60b
ms.sourcegitcommit: 3bfd0d2c4d83f306023adb45c8a3f829f7150b1d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65073417"
---
# <a name="people-picker-in-adaptive-cards"></a>Seletor de Pessoas em Cartões Adaptáveis

>[!NOTE]
> Atualmente, o Seletor de Pessoas em Cartões Adaptáveis está disponível [](../../resources/dev-preview/developer-preview-intro.md#public-developer-preview-for-microsoft-teams) na versão prévia do desenvolvedor público somente para dispositivos móveis e ga (disponibilidade geral) para área de trabalho.

O Seletor de Pessoas ajuda os usuários a pesquisar e selecionar usuários no Cartão Adaptável. Você pode adicionar o Seletor de Pessoas como controle de entrada ao Cartão Adaptável, que funciona em chats, canais, módulos de tarefas e guias. O People Picker dá suporte aos seguintes recursos:

* Pesquisa um ou vários usuários.
* Seleciona um ou vários usuários.
* Reatribui a um ou vários usuários.
* Popula previamente o nome dos usuários selecionados.

## <a name="popular-scenarios"></a>Cenários populares

A tabela a seguir fornece cenários populares para o Seletor de Pessoas em Cartões Adaptáveis e as ações correspondentes:

|Cenários|Ações|
|----------|-------------------------|
|Cenários baseados em aprovação| Para solicitar, atribuir e reatribuir a aprovação ao usuário pretendido com base no requisito.|
|Gestão de incidentes| Para acompanhar incidentes e notificar, atribuir e reatribuir ao usuário pretendido para ação imediata.|
|Gerenciamento de projeto| Para atribuir tíquetes ou bugs a usuários específicos.|
|Pesquisa do usuário| Para pesquisar usuários em toda a organização.|

# <a name="desktop"></a>[Desktop](#tab/desktop)

O cliente Web e desktop dá suporte ao Seletor de Pessoas no Cartão Adaptável. Ao pesquisar na Web, o Seletor de Pessoas envolve uma experiência de digitação embutida.

### <a name="reassignment-scenario-example"></a>Exemplo de cenário de reatribuição

O usuário A (Robert) recebe um tíquete para uma tarefa em um canal e percebe o destinatário incorreto. O usuário A reatribui a tarefa que envia as informações de volta para o bot.

Para reatribuir qualquer tarefa:

1. Selecione  Reatribuir onde o campo seletor de pessoas é pré-preenchido com o nome para reatribuir a tarefa ao usuário pretendido.
1. Remova o nome do usuário incorreto.
1. Selecione os usuários pretendido de acordo com o cenário de imagem, o usuário B (Mona) e o usuário C (Robin) para a tarefa.
1. Selecione **Atribuir**. Depois de atribuir, as informações são enviadas ao bot.
   O bot atualiza o Cartão Adaptável e notifica os usuários pretendido.

A imagem a seguir mostra o cenário de reatribuição:

![Seletor de Pessoas na Área de Trabalho](../../assets/images/cards/desktoppp.gif)

# <a name="mobile"></a>[Dispositivo móvel](#tab/mobile)

> [!NOTE]
> Atualmente, esse recurso está disponível apenas na versão [prévia do desenvolvedor](../../resources/dev-preview/developer-preview-intro.md#public-developer-preview-for-microsoft-teams) público.

Os clientes móveis Android e iOS dão suporte ao Seletor de Pessoas em Cartões Adaptáveis. Você pode usar o Seletor de Pessoas no celular para pesquisar e selecionar o usuário para aprimorar a experiência do usuário. A experiência de pesquisa é semelhante a qualquer outra experiência de seleção de usuário no celular.

### <a name="reassignment-scenario-example"></a>Exemplo de cenário de reatribuição

O usuário A (Robert) recebe um tíquete para uma tarefa em um canal e percebe o destinatário incorreto. O usuário A reatribui a tarefa que envia as informações de volta para o bot.

Para reatribuir qualquer tarefa:

1. Selecione  Reatribuir onde o campo seletor de pessoas é pré-preenchido com o nome para reatribuir a tarefa ao usuário pretendido.
1. Remova o nome do usuário incorreto.
1. Selecione os usuários pretendido de acordo com o cenário de imagem, o usuário B (Mona) e o usuário C (Robin) para a tarefa.
1. Selecione **Concluído**.
1. Selecione **Atribuir**. Depois de atribuir, as informações são enviadas ao bot.
   O bot atualiza o Cartão Adaptável e notifica os usuários pretendido.

A imagem a seguir mostra o cenário de reatribuição:

![Seletor de Pessoas no Celular](../../assets/images/cards/mobilepp.gif)

---

## <a name="implement-people-picker"></a>Implementar o Seletor de Pessoas

O Seletor de Pessoas é implementado como uma extensão do [controle Input.ChoiceSet](https://adaptivecards.io/explorer/Input.ChoiceSet.html) . O controle de entrada inclui as seguintes seleções:

* Lista suspensa, como uma seleção expandida.
* Botão de opção, como uma única seleção.
* Caixas de seleção, como várias seleções.  

> [!NOTE]
> O `Input.ChoiceSet` controle é baseado no e `style` nas `isMultiSelect` propriedades.  

### <a name="update-schema"></a>Atualizar esquema

As propriedades a seguir são adições ao esquema `Input.ChoiceSet` para habilitar a experiência do Seletor de Pessoas no cartão:  

#### <a name="inputchoiceset-control"></a>Controle Input.ChoiceSet

|Propriedade |Tipo |Obrigatório |Descrição |
|----|----|----|----|
|**choices.data** |**Data.Query** |Não |Habilita o preenchimento automático dinâmico para diferentes tipos de usuário, buscando resultados do conjunto de dados especificado. |

#### <a name="dataquery"></a>Data.Query

|Propriedade |Tipo |Obrigatório |Descrição|
|--|--|--|--|
|**Dataset** |String |Sim |O tipo de dados que deve ser buscado dinamicamente.|

#### <a name="dataset"></a>Dataset

A tabela a seguir fornece valores predefinidos como **conjunto de dados** para o seletor de pessoas:

|Dataset|Escopo da Pesquisa
|--|--|
|**graph.microsoft.com/users** |Pesquise todos os membros em toda a organização.|
|**graph.microsoft.com/users?scope=currentContext** |Pesquise dentro dos membros da conversa atual, como chat ou canal no qual o cartão específico é enviado.|

### <a name="example"></a>Exemplo

O exemplo de código para criar o Seletor de Pessoas com a pesquisa da organização é o seguinte:

```json
{
 "type": "AdaptiveCard",
 "body": [
  {
   "type": "TextBlock",
   "size": "Medium",
   "weight": "Bolder",
   "text": "People Picker with Org search enabled"
  },
  {
   "type": "Input.ChoiceSet",
   "choices": [],
   "choices.data": {
    "type": "Data.Query",
    "dataset": "graph.microsoft.com/users"
   },
   "id": "people-picker",
   "isMultiSelect": true
  }
 ],
 "actions": [
  {
   "type": "Action.Submit",
   "title": "Submit"
  }
 ],
 "$schema": "http://adaptivecards.io/schemas/adaptive-card.json",
 "version": "1.2"
}
```  

A imagem a seguir ilustra o Seletor de Pessoas em Cartões Adaptáveis com a pesquisa da organização:

:::image type="content" source="../../assets/images/Cards/peoplepicker-org-search.png" alt-text="Pesquisa da organização do seletor de pessoas":::

Para habilitar a pesquisa dentro de uma lista de membros da conversa, use o conjunto de dados apropriado definido na tabela [do conjunto de](#dataset) dados. `isMultiSelect` é usada para habilitar a seleção de vários usuários no controle. Ele é definido como false por padrão e essa configuração permite que você selecione apenas um usuário.

### <a name="data-submission"></a>Envio de dados

Você pode usar `Action.Submit` ou `Action.Execute` enviar dados selecionados para o bot. A `invoke` carga recebida no bot é uma lista de IDs Microsoft Azure Active Directory (Azure AD) ou as IDs fornecidas na lista estática.
No Seletor de Pessoas, quando um usuário é selecionado no controle, o `Azure AD ID` do usuário é o valor enviado de volta. É `Azure AD ID` uma cadeia de caracteres e identifica exclusivamente um usuário no diretório.

O formato do valor enviado ao bot depende do valor da `isMultiSelect` propriedade:

|valor de `isMultiSelect`|Formatar|
|--|--|
|false _(seleção única)_|<selected_Azure_AD_ID>|
|true _(seleção multi)_|<selected_Azure_AD_ID_1>, <selected_Azure_AD_ID_2>,<selected_Azure_AD_ID_3>|  

Com o `Azure AD ID`, o Seletor de Pessoas pré-seleciona o usuário correspondente.

## <a name="preselection-of-user"></a>Pré-seleção do usuário

O Seletor de Pessoas dá suporte à pré-seleção do usuário no controle ao criar e enviar um Cartão Adaptável. `Input.ChoiceSet` dá suporte `value` à propriedade usada para pré-selecionar um usuário. O formato dessa propriedade `value` é o mesmo que o formato de valor enviado no envio [de dados](#data-submission).  
A lista a seguir fornece as informações para pré-selecionar usuários:

* Para um único usuário no controle, especifique `Azure AD ID` o usuário como o `value`.
* Para vários usuários, como `isMultiSelect` é, `true`especifique uma cadeia de caracteres separada por vírgulas de `Azure AD ID`s.  

O exemplo a seguir descreve a pré-seleção de um único usuário:

```json
{
 "type": "AdaptiveCard",
 "body": [
  {
   "type": "TextBlock",
   "size": "Medium",
   "weight": "Bolder",
   "text": "People Picker with Org search enabled"
  },
  {
   "type": "Input.ChoiceSet",
   "choices": [],
   "choices.data": {
    "type": "Data.Query",
    "dataset": "graph.microsoft.com/users"
   },
   "id": "people-picker",
   "value": "<Azure AD ID 1>"
  }
 ],
 "actions": [
  {
   "type": "Action.Submit",
   "title": "Submit"
  }
 ],
 "$schema": "http://adaptivecards.io/schemas/adaptive-card.json",
 "version": "1.2"
}
```  

O exemplo a seguir descreve a pré-seleção de vários usuários:

```json
{
 "type": "AdaptiveCard",
 "body": [
  {
   "type": "TextBlock",
   "size": "Medium",
   "weight": "Bolder",
   "text": "People Picker with Org search enabled"
  },
  {
   "type": "Input.ChoiceSet",
   "choices": [],
   "choices.data": {
    "type": "Data.Query",
    "dataset": "graph.microsoft.com/users"
   },
   "id": "people-picker",
   "isMultiSelect": true,
   "value": "<Azure AD ID 1>,<Azure AD ID 2>,<Azure AD ID 3>"
  }
 ],
 "actions": [
  {
   "type": "Action.Submit",
   "title": "Submit"
  }
 ],
 "$schema": "http://adaptivecards.io/schemas/adaptive-card.json",
 "version": "1.2"
}
```

## <a name="static-choices"></a>Opções estáticas

As opções estáticas dão suporte a cenários em que perfis personalizados devem ser inseridos nos conjuntos de dados predefinidos. `Input.ChoiceSet` dá suporte à especificação `choices` estaticamente no json. A opção estática é usada para criar as opções das quais o usuário pode selecionar.

> [!NOTE]
> Estáticos `choices` são usados com conjuntos de dados dinâmicos.

A escolha consiste em `title` e `value`. Quando usadas junto com o Seletor de Pessoas, `title` `value` essas opções são convertidas em perfis de usuário que têm o nome e o identificador como o identificador. Esses perfis personalizados também fazem parte dos resultados da pesquisa quando a consulta de pesquisa corresponde ao determinado `title`.
O exemplo a seguir descreve as opções estáticas:

```json
{
 "type": "AdaptiveCard",
 "body": [
  {
   "type": "TextBlock",
   "size": "Medium",
   "weight": "Bolder",
   "text": "People Picker with Org search enabled"
  },
  {
   "type": "Input.ChoiceSet",
   "choices": [
    {
     "title": "Custom Profile 1",
     "value": "Profile1"
    },
    {
     "title": "Custom Profile 2",
     "value": "Profile2"
    }
   ],
   "choices.data": {
    "type": "Data.Query",
    "dataset": "graph.microsoft.com/users"
   },
   "id": "people-picker",
   "isMultiSelect": true
  }
 ],
 "actions": [
  {
   "type": "Action.Submit",
   "title": "Submit"
  }
 ],
 "$schema": "http://adaptivecards.io/schemas/adaptive-card.json",
 "version": "1.2"
}
```

A imagem a seguir ilustra o Seletor de Pessoas em Cartões Adaptáveis com opções estáticas na pesquisa da organização:

:::image type="content" source="../../assets/images/Cards/peoplepicker-static-choice.png" alt-text="people-picker-static-choice":::

Você pode implementar o Seletor de Pessoas para um gerenciamento eficiente de tarefas em diferentes cenários.  

## <a name="code-sample"></a>Exemplo de código

| Nome do exemplo           | Descrição | C#    | Node.js   |
|:---------------------|:--------------|:---------|:--------|
|Controle de seletor de pessoas em Cartões Adaptáveis| Este exemplo demonstra como usar o controle seletor de pessoas em Cartões Adaptáveis.|[View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/bot-people-picker-adaptive-card/csharp)|[Exibir](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/bot-people-picker-adaptive-card/nodejs) |

## <a name="see-also"></a>Confira também

[Referência de cartões](cards-reference.md)
