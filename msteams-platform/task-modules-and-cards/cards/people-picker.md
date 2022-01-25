---
title: Seletor de Pessoas nos Cartões Adaptáveis
description: Descreve como usar o controle People Picker em Cartões Adaptáveis
localization_priority: Normal
keywords: Se picker de pessoas de cartões adaptáveis
ms.topic: reference
author: Rajeshwari-v
ms.author: surbhigupta
ms.openlocfilehash: b09293c26dac6721b92fcf1d574560a3da7e281a
ms.sourcegitcommit: 7209e5af27e1ebe34f7e26ca1e6b17cb7290bc06
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/25/2022
ms.locfileid: "62212472"
---
# <a name="people-picker-in-adaptive-cards"></a>Seletor de Pessoas nos Cartões Adaptáveis

>[!NOTE]
> Atualmente, o People Picker em Cartões [](../../resources/dev-preview/developer-preview-intro.md#public-developer-preview-for-microsoft-teams) Adaptáveis está disponível na visualização de desenvolvedor público apenas para dispositivos móveis e geralmente disponíveis (GA) para área de trabalho.

O Seletor de Pessoas ajuda os usuários a pesquisar e selecionar usuários no Cartão Adaptável. Você pode adicionar o People Picker como controle de entrada ao Cartão Adaptável, que funciona em chats, canais, módulos de tarefas e guias. O People Picker dá suporte aos seguintes recursos:        

* Pesquisa usuários individuais ou múltiplos.
* Seleciona usuários individuais ou múltiplos. 
* Reatribui para usuários individuais ou múltiplos. 
* Prepopula o nome dos usuários selecionados.

## <a name="popular-scenarios"></a>Cenários populares 

A tabela a seguir fornece cenários populares para o Seletor de Pessoas em Cartões Adaptáveis e as ações correspondentes:

|Cenários|Ações|
|----------|-------------------------|
|Cenários baseados em aprovação| Para solicitar, atribuir e reatribuir a aprovação ao usuário pretendido com base no requisito.|
|Gestão de incidentes| Para rastrear incidentes e notificar, atribuir e reatribuir ao usuário pretendido para ação imediata.| 
|Gerenciamento de projeto| Para atribuir tíquetes ou bugs a usuários específicos.|
|User lookup| Para pesquisar usuários em toda a organização.|

# <a name="desktop"></a>[Desktop](#tab/desktop)

O cliente da Web e da área de trabalho suporta o People Picker no Cartão Adaptável. Ao pesquisar na Web, o People Picker envolve uma experiência de digitação em linha.

### <a name="reassignment-scenario-example"></a>Exemplo de cenário de reatribuição

O usuário A (Robert) recebe um tíquete para uma tarefa em um canal e percebe o destinatário incorreto. O Usuário A reatribui a tarefa que envia as informações de volta para o bot. 

**Para reatribuir qualquer tarefa**

1. Selecione **Reatribuir** onde o campo seletor de pessoas é pré-populado com nome para reatribuir a tarefa ao usuário pretendido.
1. Remova o nome do usuário incorreto. 
1. Selecione os usuários pretendido de acordo com o cenário de imagem, o usuário B (Mona) e o usuário C (Robin) para a tarefa. 
1. Selecione **Atribuir**. Após a atribuição, as informações são enviadas para o bot. 
   O bot atualiza o Cartão Adaptável e notifica os usuários pretendido. 
 
A imagem a seguir mostra o cenário de reatribuição:    

![Se picker de pessoas na área de trabalho](../../assets/images/cards/desktoppp.gif)

# <a name="mobile"></a>[Dispositivo móvel](#tab/mobile)

> [!NOTE]
> Atualmente, esse recurso está disponível apenas na [visualização de desenvolvedor](../../resources/dev-preview/developer-preview-intro.md#public-developer-preview-for-microsoft-teams) público.

Os clientes móveis Android e iOS suportam o Seletor de Pessoas em Cartões Adaptáveis. Você pode usar o Seletor de Pessoas no celular para pesquisar e selecionar o usuário para aprimorar a experiência do usuário. A experiência de pesquisa é semelhante a qualquer outra experiência de seleção de usuário no celular.

### <a name="reassignment-scenario-example"></a>Exemplo de cenário de reatribuição

O usuário A (Robert) recebe um tíquete para uma tarefa em um canal e percebe o destinatário incorreto. O Usuário A reatribui a tarefa que envia as informações de volta para o bot. 

**Para reatribuir qualquer tarefa**

1. Selecione **Reatribuir** onde o campo seletor de pessoas é pré-populado com nome para reatribuir a tarefa ao usuário pretendido.
1. Remova o nome do usuário incorreto.
1. Selecione os usuários pretendido de acordo com o cenário de imagem, o usuário B (Mona) e o usuário C (Robin) para a tarefa.
1. Selecione **Concluído**.
1. Selecione **Atribuir**. Após a atribuição, as informações são enviadas para o bot. 
   O bot atualiza o Cartão Adaptável e notifica os usuários pretendido. 

A imagem a seguir mostra o cenário de reatribuição: 

![People Picker on Mobile](../../assets/images/cards/mobilepp.gif)

---

## <a name="implement-people-picker"></a>Implementar o Se picker de pessoas

O People Picker é implementado como uma extensão do [controle Input.ChoiceSet.](https://adaptivecards.io/explorer/Input.ChoiceSet.html) O controle de entrada inclui as seguintes seleções:   

* Menu suspenso, como uma seleção expandida.
* Botão de rádio, como uma única seleção.
* Caixas de seleção, como várias seleções.  

> [!NOTE]
> O `Input.ChoiceSet` controle é baseado nas propriedades `style` `isMultiSelect` e.  

### <a name="update-schema"></a>Atualizar esquema

As seguintes propriedades são adições ao `Input.ChoiceSet` esquema para habilitar a experiência do Selador de Pessoas no cartão:  

#### <a name="inputchoiceset-control"></a>Controle Input.ChoiceSet

|Propriedade |Tipo |Obrigatório |Descrição |
|----|----|----|----|
|**choices.data** |**Data.Query** |Não |Habilita a conclusão automática dinâmica para diferentes tipos de usuário, buscando resultados do conjuntos de dados especificado. |

#### <a name="dataquery"></a>Data.Query

|Propriedade |Tipo |Obrigatório |Descrição|
|--|--|--|--|
|**dataset** |Cadeia de Caracteres |Sim |O tipo de dados que deve ser buscado dinamicamente.|   

#### <a name="dataset"></a>dataset
A tabela a seguir fornece valores predefinidos como **conjunto de dados** para o seletor de pessoas:   

|dataset|Escopo da Pesquisa
|--|--|
|**graph.microsoft.com/users** |Pesquise todos os membros na organização.|
|**graph.microsoft.com/users?scope=currentContext** |Pesquise dentro dos membros da conversa atual, como chat ou canal no qual o cartão específico é enviado.|        

### <a name="example"></a>Exemplo
O exemplo de código para criar o Se picker de pessoas com a pesquisa da organização é o seguinte:

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

A imagem a seguir ilustra o Se picker de pessoas em Cartões Adaptáveis com a pesquisa da organização:

![Pesquisa organizacional do Selador de Pessoas](../../assets/images/cards/peoplepicker-org-search.png)

Para habilitar a pesquisa em uma lista de membros da conversa, use o conjuntos de dados apropriado definido na tabela [de conjuntos de](#dataset) dados. `isMultiSelect` é usada para habilitar a seleção de vários usuários no controle. Ele é definido como false por padrão e essa configuração permite selecionar apenas um usuário.

### <a name="data-submission"></a>Envio de dados

Você pode usar `Action.Submit` ou `Action.Execute` enviar dados selecionados para seu bot. A carga recebida no bot é uma lista de IDs do Azure AD ou as `invoke` IDs fornecidas na lista estática.
No Seletor de Pessoas, quando um usuário é selecionado no controle, o do `Azure AD ID` usuário é o valor enviado de volta. É `Azure AD ID` uma cadeia de caracteres e identifica exclusivamente um usuário no diretório.

O formato do valor enviado ao bot depende do valor da `isMultiSelect` propriedade:

|valor de `isMultiSelect`|Formatar|
|--|--|
|false _(seleção única)_|<selected_Azure_AD_ID>|
|true _(seleção multi)_|<selected_Azure_AD_ID_1>,<selected_Azure_AD_ID_2>,<selected_Azure_AD_ID_3>|  

Com `Azure AD ID` o , o Seletor de Pessoas pré-seleciona o usuário correspondente. 

## <a name="preselection-of-user"></a>Pré-seleção do usuário

O Seletor de Pessoas dá suporte à pré-seleção do usuário no controle, ao criar e enviar um Cartão Adaptável. `Input.ChoiceSet` dá suporte `value` à propriedade usada para pré-selecionar um usuário. O formato dessa propriedade é o mesmo do formato de valor `value` enviado no envio de [dados.](#data-submission)  
A lista a seguir fornece as informações para pré-selecionar usuários:

* Para um único usuário no controle, especifique o `Azure AD ID` do usuário como `value` . 
* Para vários usuários, como `isMultiSelect` é `true` , especifique uma cadeia de caracteres separada por vírgulas de `Azure AD ID` s.  

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

As opções estáticas suportam cenários em que perfis personalizados devem ser inseridos nos conjuntos de dados predefinidos. `Input.ChoiceSet` oferece suporte à `choices` especificação estática no json. A opção estática é usada para criar as opções das quais o usuário pode selecionar.

> [!NOTE]
> Estáticas `choices` são usadas com conjuntos de dados dinâmicos. 

A escolha consiste em `title` `value` e . Quando usadas junto com o Selador de Pessoas, essas opções são traduzidas para perfis de usuário que têm o nome e `title` `value` o identificador como. Esses perfis personalizados também fazem parte dos resultados da pesquisa quando a consulta de pesquisa corresponde ao `title` determinado .    
O exemplo a seguir descreve opções estáticas: 

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

A imagem a seguir ilustra o Se picker de pessoas em Cartões Adaptáveis com opções estáticas na pesquisa da organização:

![Escolha estática do Selador de Pessoas](../../assets/images/cards/peoplepicker-static-choice.png)


Você pode implementar o People Picker para um gerenciamento eficiente de tarefas em diferentes cenários.  

## <a name="see-also"></a>Confira também

[Referência de cartões](cards-reference.md)

