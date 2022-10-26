---
title: Usar APIs do Graph para buscar a transcrição
description: Descreve as APIs para buscar transcrições de reunião
ms.localizationpriority: high
ms.topic: conceptual
ms.openlocfilehash: 2142bc1346a032f27d8612f6081156d2c4927e8f
ms.sourcegitcommit: 372aade09e62ac7e5936215173a6632fbb042c9d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/26/2022
ms.locfileid: "68699175"
---
# <a name="use-graph-apis-to-fetch-transcript"></a>Usar APIs do Graph para buscar a transcrição

Use as APIs REST do Graph para obter transcrições de uma reunião específica. Seu aplicativo busca as transcrições com base na ID de usuário do organizador da reunião e na ID da reunião.

As seguintes APIs são usadas para buscar transcrições:

- [Listar callTranscripts](#list-calltranscripts)
- [Obter callTranscript](#get-calltranscript)
- [Obter conteúdo callTranscript](#get-calltranscript-content)

### <a name="list-calltranscripts"></a>Listar callTranscripts

Essa API é usada para obter uma lista de todos os objetos `callTranscript` com base na ID de usuário e na ID da reunião. Ela retorna os metadados das transcrições da reunião, que contém a ID da transcrição e a data e hora de criação dessa transcrição.

**Solicitação HTTP**

```http
GET /me/onlineMeetings('{meetingId}')/transcripts
GET /users('{userId}')/onlineMeetings('{meetingId}')/transcripts
```

**Parâmetros de consulta opcionais**

Este método oferece suporte aos parâmetros de consulta `$skipToken` e `$top` [OData](/graph/query-parameters) para ajudar a personalizar a resposta.

**Padrões de consulta com suporte**

| Padrão                | Compatível | Sintaxe                                 | Observações |
| ---------------------- | ------- | -------------------------------------- | ----- |
| Paginação do lado do servidor |     ✓     | `@odata.nextLink`                      | Obtenha um token de continuação na resposta, quando um conjunto de resultados abrange várias páginas. |
| Limite de página             |     ✓     | `/transcripts?$top=20` | Obter transcrições com tamanho de página 20. O limite de página padrão é 10. O limite máximo de páginas é 100. |

**Cabeçalhos da Solicitação**

| Cabeçalho       | Valor |
|:---------------|:--------|
| Autorização  | Bearer {token}. Required.  |

**Corpo da solicitação**

Não forneça um corpo de solicitação para esse método.

**Response**

Se bem-sucedido, este método retorna um código de resposta `200 OK` e uma coleção de objetos `callTranscript` no corpo da resposta.

<br>
<details>
<summary><b>Exemplo: lista de callTranscript</b></summary>
<br>
<b>Solicitação</b>
<br>

```http
GET https://graph.microsoft.com/beta/users/ba321e0d-79ee-478d-8e28-85a19507f456/onlineMeetings/MSo1N2Y5ZGFjYy03MWJmLTQ3NDMtYjQxMy01M2EdFGkdRWHJlQ/transcripts
```

<br>
<b>Response</b>
<br>

> [!NOTE]
> O objeto de resposta mostrado aqui pode ser reduzido para facilitar a leitura.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
    "@odata.context": "https://graph.microsoft.com/beta/$metadata#users('ba321e0d-79ee-478d-8e28-85a19507f456')/onlineMeetings('MSo1N2Y5ZGFjYy03MWJmLTQ3NDMtYjQxMy01M2EdFGkdRWHJlQ')/transcripts",
    "@odata.count": 3,
    "@odata.nextLink": "https://graph.microsoft.com/beta/users('ba321e0d-79ee-478d-8e28-85a19507f456')/onlineMeetings('MSo1N2Y5ZGFjYy03MWJmLTQ3NDMtYjQxMy01M2EdFGkdRWHJlQ')/transcripts?$skiptoken=MSMjMCMjMjAyMS0wOS0xNlQxMzo1OToyNy4xMjEwMzgzWg%3d%3d",
    "value": [
        {
            "id": "MSMjMCMjZDAwYWU3NjUtNmM2Yi00NjQxLTgwMWQtMTkzMmFmMjEzNzdh",
            "createdDateTime": "2021-09-17T06:09:24.8968037Z"
        },
        {
            "id": "MSMjMCMjMzAxNjNhYTctNWRmZi00MjM3LTg5MGQtNWJhYWZjZTZhNWYw",
            "createdDateTime": "2021-09-16T18:58:58.6760692Z"
        },
        {
            "id": "MSMjMCMjNzU3ODc2ZDYtOTcwMi00MDhkLWFkNDItOTE2ZDNmZjkwZGY4",
            "createdDateTime": "2021-09-16T18:56:00.9038309Z"
        }        
    ]
}
```

</details>

### <a name="get-calltranscript"></a>Obter callTranscript

Seu aplicativo analisa a lista de IDs de transcrição, recebidas como a resposta da API `List callTranscripts`, para obter a ID de transcrição necessária. Essa API é usada para obter um único metadados de transcrição com base na ID de usuário, na ID da reunião e na ID da transcrição.

**Solicitação HTTP**

```http
GET me/onlineMeetings('{meetingId}')/transcripts('{transcriptId}')
GET users('{userId}')/onlineMeetings('{meetingId}')/transcripts('{transcriptId}')
```

**Cabeçalhos da Solicitação**

| Cabeçalho       | Valor |
|:---------------|:--------|
| Autorização  | Bearer {token}. Required.  |

**Corpo da solicitação**

Não forneça um corpo de solicitação para esse método.

**Response**

Se bem-sucedido, este método retorna um código de resposta `200 OK` e o objeto `callTranscript` no corpo da resposta.

<br>
<details>
<summary><b>Exemplo: obter um callTranscript</b></summary>
<br>
<b>Solicitação</b>
<br>

```http
GET https://graph.microsoft.com/beta/users/ba321e0d-79ee-478d-8e28-85a19507f456/onlineMeetings/MSo1N2Y5ZGFjYy03MWJmLTQ3NDMtYjQxMy01M2EdFGkdRWHJlQ/transcripts/MSMjMCMjNzU3ODc2ZDYtOTcwMi00MDhkLWFkNDItOTE2ZDNmZjkwZGY4
```

<br>
<b>Response</b>
<br>

> [!NOTE]
> O objeto de resposta mostrado aqui pode ser reduzido para facilitar a leitura.

```http
HTTP/1.1 200 OK
Content-type: application/json

{
    "@odata.context": "https://graph.microsoft.com/beta/$metadata#users('ba321e0d-79ee-478d-8e28-85a19507f456')/onlineMeetings('MSo1N2Y5ZGFjYy03MWJmLTQ3NDMtYjQxMy01M2EdFGkdRWHJlQ')/transcripts/$entity",
    "id": "MSMjMCMjNzU3ODc2ZDYtOTcwMi00MDhkLWFkNDItOTE2ZDNmZjkwZGY4",
    "createdDateTime": "2021-09-17T06:09:24.8968037Z"
}
```

</details>

### <a name="get-calltranscript-content"></a>Obter conteúdo callTranscript

Essa API é usada para obter a transcrição da ID de transcrição selecionada que foi obtida na resposta da API `Get callTranscript`. Ela retorna o conteúdo da transcrição.

**Solicitação HTTP**

```http
GET me/onlineMeetings('{meetingId}')/transcripts('{transcriptId}')/content
GET users('{userId}')/onlineMeetings('{meetingId}')/transcripts('{transcriptId}')/content
```

**Parâmetros de consulta opcionais**

Esse método dá suporte ao `$format` [parâmetro de consulta OData](/graph/query-parameters) que permite a personalização de resposta.

Os tipos de formato com suporte são `text/vtt` para vtt OU `application/vnd.openxmlformats-officedocument.wordprocessingml.document` para o formato docx.

**Cabeçalhos da Solicitação**

| Cabeçalho       | Valor |
|:---------------|:--------|
| Autorização  | Bearer {token}. Required.  |
| Aceitar  | text/vtt OU application/vnd.openxmlformats-officedocument.wordprocessingml.document. Opcional.  |

**Corpo da solicitação**

Não forneça um corpo de solicitação para esse método.

**Response**

Se bem-sucedido, este método retorna um código de resposta `200 OK` e contém bytes para o objeto callTranscript no corpo da resposta. O cabeçalho `content-type` especifica o tipo do conteúdo da transcrição.

**Exemplos**
<br>
<details>
<summary><b>Exemplo: obter um conteúdo callTranscript</b></summary>
<br>
<b>Solicitação</b>
<br>

```http
GET https://graph.microsoft.com/beta/users/ba321e0d-79ee-478d-8e28-85a19507f456/onlineMeetings/MSo1N2Y5ZGFjYy03MWJmLTQ3NDMtYjQxMy01M2EdFGkdRWHJlQ/transcripts/MSMjMCMjNzU3ODc2ZDYtOTcwMi00MDhkLWFkNDItOTE2ZDNmZjkwZGY4/content
```

<br>
<b>Response</b>
<br>

A resposta contém bytes para a transcrição no corpo. O cabeçalho `content-type` especifica o tipo do conteúdo da transcrição.

> [!NOTE]
> O objeto de resposta mostrado aqui pode ser reduzido para facilitar a leitura.

```http
HTTP/1.1 200 OK
Content-type: text/vtt

WEBVTT
    
0:0:0.0 --> 0:0:5.320
<v User Name>This is a transcript test.</v>
```

</details>
<br>
<details>
<summary><b>Exemplo: obter um conteúdo callTranscript especificando o parâmetro de consulta $format</b></summary>
<br>
<b>Solicitação</b>
<br>

```http
GET https://graph.microsoft.com/beta/users/ba321e0d-79ee-478d-8e28-85a19507f456/onlineMeetings/MSo1N2Y5ZGFjYy03MWJmLTQ3NDMtYjQxMy01M2EdFGkdRWHJlQ/transcripts/MSMjMCMjNzU3ODc2ZDYtOTcwMi00MDhkLWFkNDItOTE2ZDNmZjkwZGY4/content?$format=text/vtt
 ```

<br>
<b>Response</b>
<br>

A resposta contém bytes para a transcrição no corpo. O cabeçalho `content-type` especifica o tipo do conteúdo da transcrição.

> [!NOTE]
> O objeto de resposta mostrado aqui pode ser reduzido para facilitar a leitura.

```http
HTTP/1.1 200 OK
Content-type: text/vtt
    
WEBVTT
    
0:0:0.0 --> 0:0:5.320
<v User Name>This is a transcript test.</v>
```

</details>
<br>
<details>
<summary><b>Exemplo: obter um conteúdo callTranscript especificando o cabeçalho Accept</b></summary>
<br>
<b>Solicitação</b>
<br>

```http
GET https://graph.microsoft.com/beta/users/ba321e0d-79ee-478d-8e28-85a19507f456/onlineMeetings/MSo1N2Y5ZGFjYy03MWJmLTQ3NDMtYjQxMy01M2EdFGkdRWHJlQ/transcripts/MSMjMCMjNzU3ODc2ZDYtOTcwMi00MDhkLWFkNDItOTE2ZDNmZjkwZGY4/content
Accept: application/vnd.openxmlformats-officedocument.wordprocessingml.document
```

<br>
<b>Response</b>
<br>

A resposta contém bytes para a transcrição no corpo. O cabeçalho `content-Type` especifica o tipo do conteúdo da transcrição.

> [!NOTE]
> O objeto de resposta mostrado aqui pode ser reduzido para facilitar a leitura.

```http
HTTP/1.1 200 OK
Content-type: application/vnd.openxmlformats-officedocument.wordprocessingml.document
    
0:0:0.0 --> 0:0:5.320
User Name
This is a transcript test.
```

</details>
<br>
<details>
<summary><b>Exemplo: obter um conteúdo callTranscript com $format obtendo precedência sobre o cabeçalho accept</b></summary>
<br>
<b>Solicitação</b>
<br>

```http
GET https://graph.microsoft.com/beta/users/ba321e0d-79ee-478d-8e28-85a19507f456/onlineMeetings/MSo1N2Y5ZGFjYy03MWJmLTQ3NDMtYjQxMy01M2EdFGkdRWHJlQ/transcripts/MSMjMCMjNzU3ODc2ZDYtOTcwMi00MDhkLWFkNDItOTE2ZDNmZjkwZGY4/content?$format=text/vtt
Accept: application/vnd.openxmlformats-officedocument.wordprocessingml.document
```

<br>
<b>Response</b>
<br>

A resposta contém bytes para a transcrição no corpo. O cabeçalho `content-Type` especifica o tipo do conteúdo da transcrição.

> [!NOTE]
> O objeto de resposta mostrado aqui pode ser reduzido para facilitar a leitura.

```http
HTTP/1.1 200 OK
Content-type: text/vtt
    
WEBVTT
   
0:0:0.0 --> 0:0:5.320
<v User Name>This is a transcript test.</v>
```

</details>

