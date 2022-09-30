---
title: API Web de tabelas virtuais
author: surbhigupta
description: Neste módulo, saiba mais sobre a API Web de Tabelas Virtuais para o aplicativo de controle de colaboração, a classificação de tabelas virtuais e a filtragem no Microsoft Teams.
ms.localizationpriority: medium
ms.author: v-npaladugu
ms.topic: conceptual
ms.openlocfilehash: b15c7972dfc0152d458e4ad895ed6d4f7e45cd4c
ms.sourcegitcommit: edfe85e312c73e34aa795922c4b7eb0647528d48
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/30/2022
ms.locfileid: "68243546"
---
# <a name="virtual-tables-web-api"></a>API Web de tabelas virtuais

Ao usar a API Web do Dataverse para recuperar vários registros de uma tabela virtual, parâmetros de consulta adicionais podem ser incluídos para dar suporte à classificação, filtragem e paginação. Esses recursos não têm suporte uniforme nas tabelas virtuais de controles de colaboração porque dependem do suporte fornecido pelo Microsoft API do Graph. Consulte a Referência de Entidade de Tabelas Virtuais para obter detalhes sobre o que cada tabela virtual dá suporte.

> [!NOTE]
> Atualmente, os controles de colaboração estão disponíveis apenas na versão [prévia do desenvolvedor público](~/resources/dev-preview/developer-preview-intro.md).

## <a name="virtual-table-sorting"></a>Classificação de tabela virtual

Com as tabelas virtuais, você pode usar o parâmetro de consulta $orderby OData para definir critérios de como o conjunto de resultados deve ser classificados. Use o sufixo asc ou desc para especificar ordem crescente ou decrescente, respectivamente. O padrão será crescente se o sufixo não for aplicado.  

**Tabelas com suporte**: cada tabela virtual dá suporte à mesma funcionalidade de classificação que seu respectivo recurso do Graph. As tabelas virtuais, que dão suporte à classificação são:  

* Item de Unidade de Grafo
* Evento Graph

> [!NOTE]
> Não há suporte para a classificação em todos os atributos dos respectivos recursos do Graph. Se um usuário tentar classificar em uma tabela virtual com um atributo sem suporte, esse conjunto de resultados terá sua ordem padrão. Esse é o mesmo comportamento que a API Web do Dataverse em colunas que não dão suporte à classificação.

Exemplos:

* GET [URI da organização]/api/data/v9.2/m365_graphdriveitems?$filter=m365_collaborationrootid eq '000000000-0000-0000-00000000000'&$orderby=m365_name desc
* GET [URI da organização]/api/data/v9.2/m365_graphevents?$filter=m365_groupid eq '000000000-0000-0000-000000000000'$orderby=m365_subject asc

## <a name="virtual-table-filtering"></a>Filtragem de tabela virtual

Com as tabelas virtuais, você pode usar o parâmetro de $filter OData para definir critérios para os quais as linhas são retornadas. As tabelas virtuais são consultadas usando os mesmos operadores OData compatíveis com a API Web do Dataverse.

* **Operadores de comparação**

  |Operador|Descrição|Exemplo|
  |----|----|----|
  |eq|Igual a|$filter=m365_name eq 'Contoso'|
  |ne|Não é igual a|$filter=m365_name ne 'Contoso'|
  |gt|Maior que|$filter=m365_price gt 50.0|
  |ge|Maior ou Igual a|$filter=m365_price ge 50.0|
  |lt|Menor que|$filter=m365_price lt 50.0|
  |le|Menor ou igual a|$filter=m365_price le 50.0|

* **Operadores lógicos**

  |Operador|Descrição|Exemplo|
  |----|----|----|
  |e|E lógico |$filter=m365_name eq 'Contoso' e m365_price eq 50.0|
  |ou|Ou lógico |$filter=m365_name ne 'Contoso' ou m365_price eq 50.0|
  |not|Negociação lógica |$filter=not contains(m365_name,'Contoso')|

* **Operadores de agrupamento**

  |Operador|Descrição|Exemplo|
  |----|----|----|
  |( )|Agrupamento de precedência |$filter=(m365_name eq 'Contoso' e m365_price eq 50.0) ou contains(m365_subject,'Team Sync')|

* **Funções de consulta**

  |Função |Exemplo |
  |----|----|
  |contains|$filter=contains(m365_name,'Contoso')|
  |endswith|$filter=endswith(m365_name,'Contoso')|
  |startswith|$filter=startswith(m365_name,'Contoso')|

**Tabelas com suporte**: cada tabela virtual dá suporte à mesma funcionalidade de filtragem que seu respectivo recurso do Graph. As tabelas virtuais, que dão suporte à filtragem são:

* Compromisso de reserva do Graph
* Item de Unidade de Grafo
* Evento Graph

> [!Note]
> Não há suporte para filtragem em todos os atributos dos respectivos recursos do Graph. Se um usuário tentar filtrar em uma tabela virtual com um atributo sem suporte, esse filtro será ignorado. Esse é o mesmo comportamento que a API Web do Dataverse em colunas que não dão suporte à filtragem.

Exemplos:

* GET [URI da organização]/api/data/v9.2/m365_graphbookingappointments?$filter=m365_bookingbusinessid eq 'ContosoBank@Contoso.onmicrosoft.com' e m365_price eq 100.0
* GET [URI da organização]/api/data/v9.2/m365_graphdriveitems?$filter=m365_collaborationrootid eq '000000000-0000-0000-000000000000' e m365_name eq 'Meeting Notes.docx'
* GET [URI da organização]/api/data/v9.2/m365_graphevents?$filter=m365_groupid eq '000000000-0000-0000-00000000000' e m365_subject eq 'Monthly Sync'

## <a name="virtual-table-pagination"></a>Paginação de tabela virtual

A paginação é um recurso útil para buscar um grande conjunto de registros. A paginação de Tabela Virtual pode ser obtida de três maneiras diferentes.

Você pode especificar o tamanho da página usando o valor `odata.maxpagesize` de preferência no cabeçalho da solicitação. Se o conjunto de resultados abranger várias páginas, a resposta incluirá a `@odata.nextLink` propriedade. A solicitação e a resposta de exemplo são as seguintes:

# <a name="request"></a>[Solicitação](#tab/request)

```http
  GET [Organization URI]/api/data/v9.2/m365_graphdriveitems 
  Accept: application/json 
  Prefer: odata.maxpagesize=2 
```

# <a name="response"></a>[Response](#tab/response)

```json
{ 

  "@odata.context": "[Organization URI]/api/data/v9.0/$metadata#m365_graphdriveitems", 
  "value": [ 
   { 
      "@odata.etag": "W/\"{FA93AF7C-1F45-4714-85A5-BB95EB86E1E5}\"", 
      "m365_name": "Review.doc", 
      "m365_graphdriveitemid": "f50aae23-6644-3d35-66d7-e3c5a979dad3", 
      …
      },
      {
      "@odata.etag": "W/\"{3938D549-1AEF-46A5-BF3C-38472AD934C2}\"", 
      "m365_name": "Review.doc", 
      "m365_graphdriveitemid": "3d59a7e2-ec83-d0b3-270e-8ad676622027", 
      … 
      } 
      ],
      "@odata.nextLink": "[Organization URI]/api/data/v9.0/m365_graphdriveitems &$skiptoken=%3Ccookie%20pagenumber=%222%22%20pagingcookie=%22UGFnZWQ9VFJVRSZwX1NvcnRCZWhhdmlvcj0xJnBfRmlsZUxlYWZSZWY9dGVzdCZwX0lEPTI5%22%20istracking=%22False%22%20/%3E" 
} 
```

---

Atualmente, as seguintes Tabelas Virtuais dão suporte à `odata.maxpagesize` preferência:

* Compromisso de reserva do Graph
* Evento De Calendário do Graph
* Unidade do Graph
* Item de Unidade de Grafo

Você pode especificar o número de registros a serem retornados passando a `$top` opção na URL. Se você também precisar especificar o número da página, poderá fazer isso passando um cookie de paginação como uma cadeia de caracteres codificada em XML como a `$skiptoken` opção. Para buscar um número de página específico, você pode passar o cookie de paginação no seguinte formato:

  `<cookie pagenumber=3 />`

# <a name="request"></a>[Solicitação](#tab/request1)

```http
     GET [Organization URL]/api/data/v9.2/m365_graphevents?$top=2&$skiptoken=<cookie pagenumber='3' /> 
```

# <a name="response"></a>[Response](#tab/response1)

```json

{
  "@odata.context": "[Organization URI]/api/data/v9.0/$metadata#m365_graphevents", 
  "value": [
   { 
      "@odata.etag": "W/\"{FA93AF7C-1F45-4714-85A5-BB95EB86E1E5}\"", 
      "m365_graphdeventid": "3d59a7e2-ec83-d0b3-270e-8ad676622027", 
      "m365_subject": "Important meeting", 
      …
    }, 
    {
      "@odata.etag": "W/\"{3938D549-1AEF-46A5-BF3C-38472AD934C2}\"", 
      "m365_graphdeventid": "f50aae23-6644-3d35-66d7-e3c5a979dad3", 
      "m365_subject": "Another important meeting", 
      …
    } 
  ] 
}

```

---

> [!Note]
> A resposta não incluirá a `@nextLink` propriedade. Se o caso de uso exigir que o próximo link de página seja retornado, você poderá usar o cabeçalho de preferência odata.maxpagesize descrito na seção 1 em vez de passar o parâmetro $top URI.

Atualmente, as tabelas virtuais a seguir dão suporte à busca de uma página específica:

* Compromisso de reserva do Graph
* Evento De Calendário do Graph

Você pode passar um XML de busca como uma cadeia de caracteres codificada em XML. Com a opção buscar XML, você pode especificar várias preferências de consulta. As opções específicas de paginação são página (número de página) e contagem (tamanho da página). O XML a seguir especifica o número e o tamanho da página:

  `<fetch version="1.0" mapping="logical" returntotalrecordcount="true" page="<Page Number>" count="<Page Size>"></fetch>`

# <a name="request"></a>[Solicitação](#tab/request2)

```http
GET [Organization URL]/api/data/v9.2/m365_graphevents?$fetchXml=<fetch version="1.0" mapping="logical" returntotalrecordcount="true" page="3" count="2"></fetch> 

```

# <a name="response"></a>[Response](#tab/response2)

```json
{ 

    "@odata.context": "[Organization URI]/api/data/v9.0/$metadata#m365_graphdevents", 
    "@Microsoft.Dynamics.CRM.fetchxmlpagingcookie": "<cookie pagenumber=\"3\" pagingcookie=\"\" istracking=\"False\" />", 
    "value": [ 
        { 
            "@odata.etag": "W/\"{FA93AF7C-1F45-4714-85A5-BB95EB86E1E5}\"", 
            "m365_graphdeventid": "3d59a7e2-ec83-d0b3-270e-8ad676622027", 
            "m365_subject": "Important meeting", 
            …
        }, 
        { 
            "@odata.etag": "W/\"{3938D549-1AEF-46A5-BF3C-38472AD934C2}\"", 
            "m365_graphdeventid": "f50aae23-6644-3d35-66d7-e3c5a979dad3", 
            "m365_subject": "Another important meeting", 
            …
        } 
    ] 
} 

```

---

As tabelas virtuais a seguir dão suporte à propriedade count a ser passada como parte da opção fetchXml:

* Unidade do Graph
* Item de Unidade de Grafo

As tabelas virtuais a seguir dão suporte à propriedade de página como parte da opção fetchXml:

* Compromisso de reserva do Graph
* Evento De Calendário do Graph
