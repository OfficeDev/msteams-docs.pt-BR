---
title: Enviar e receber arquivos de um bot
description: Saiba como enviar e receber arquivos por meio do bot usando APIs do Graph para escopos pessoais, de canal e de chat de grupo. Use AS APIs de bot do Teams usando exemplos de código com base no SDK de Bot Framework v3.
keywords: enviar e receber de arquivos de bots do teams
ms.topic: how-to
ms.localizationpriority: medium
ms.date: 05/20/2019
ms.openlocfilehash: 1bc04d2dfde200917c9faeb9fcb1c91b145463de
ms.sourcegitcommit: c398dfdae9ed96f12e1401ac7c8d0228ff9c0a2b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/30/2022
ms.locfileid: "66558286"
---
# <a name="send-and-receive-files-using-bots"></a>Enviar e receber arquivos usando bots

[!include[v3-to-v4-SDK-pointer](~/includes/v3-to-v4-pointer-bots.md)]

Há duas maneiras de enviar arquivos de e para um bot:

* Usando as APIs do Microsoft Graph. Esse método funciona para bots em todos os escopos no Teams:
  * `personal`
  * `channel`
  * `groupchat`
* Usando as APIs do Teams. Eles só dão suporte a arquivos em um contexto:
  * `personal`

## <a name="using-the-microsoft-graph-apis"></a>Usando as APIs do Microsoft Graph

Você pode postar mensagens com anexos de cartão referenciando arquivos existentes do SharePoint usando as APIs do Microsoft Graph para [OneDrive e SharePoint](/onedrive/developer/rest-api/). O uso das APIs do Graph requer a obtenção de acesso à pasta do OneDrive de um usuário (para arquivos `personal` e `groupchat`) ou os arquivos nos canais de uma equipe (para arquivos `channel`) por meio do fluxo de autorização OAuth 2.0 padrão. Esse método funciona em todos os escopos do Teams.

## <a name="using-the-teams-bot-apis"></a>Usando as APIs de Bot do Teams

> [!NOTE]
> Esse método funciona somente no contexto `personal`. Ele não funciona no contexto `channel` ou `groupchat`.

Seu bot pode enviar e receber arquivos diretamente com usuários no contexto `personal`, também conhecido como chats pessoais, usando APIs do Teams. Isso permite implementar relatórios de despesas, reconhecimento de imagem, arquivamento de arquivos, assinaturas eletrônicas e outros cenários que envolvem manipulação direta do conteúdo do arquivo. Os arquivos compartilhados no Teams normalmente aparecem como cartões e permitem a exibição avançada no aplicativo.

As seções a seguir descrevem como fazer isso para enviar conteúdo de arquivo como resultado da interação direta do usuário, como enviar uma mensagem. Essa API é fornecida como parte da Plataforma de Bot do Microsoft Teams.

### <a name="configure-your-bot-to-support-files"></a>Configurar seu bot para dar suporte a arquivos

Para enviar e receber arquivos em seu bot, você precisa definir a propriedade `supportsFiles` no manifesto como `true`. Essa propriedade é descrita na seção [bots](~/resources/schema/manifest-schema.md#bots) da referência de manifesto.

A definição terá esta aparência: `"supportsFiles": true`. Se o bot não habilitar `supportsFiles`, os recursos a seguir não funcionarão.

### <a name="receiving-files-in-personal-chat"></a>Recebendo arquivos no chat pessoal

Quando um usuário envia um arquivo para o bot, o arquivo é carregado pela primeira vez no armazenamento do OneDrive for Business do usuário. Em seguida, seu bot receberá uma atividade de mensagem notificando sobre o upload do usuário. A atividade conterá metadados de arquivo, como seu nome e a URL de conteúdo. Você pode ler diretamente dessa URL para buscar seu conteúdo binário.

#### <a name="message-activity-with-file-attachment-example"></a>Exemplo de atividade de mensagem com anexo de arquivo

```json
{
  "attachments": [{
    "contentType": "application/vnd.microsoft.teams.file.download.info",
    "contentUrl": "https://contoso.sharepoint.com/personal/johnadams_contoso_com/Documents/Applications/file_example.txt",
    "name": "file_example.txt",
    "content": {
      "downloadUrl" : "https://download.link",
      "uniqueId": "1150D938-8870-4044-9F2C-5BBDEBA70C9D",
      "fileType": "txt",
      "etag": "123"
    }
  }]
}
```

A tabela a seguir descreve as propriedades de conteúdo do anexo:

| Propriedade | Objetivo |
| --- | --- |
| `downloadUrl` | URL do OneDrive para buscar o conteúdo do arquivo. Você pode emitir um `HTTP GET` diretamente dessa URL. |
| `uniqueId` | ID de arquivo exclusiva. Essa será a ID do item de unidade do OneDrive, no caso do usuário enviar um arquivo para o bot. |
| `fileType` | Tipo de extensão de arquivo, como pdf ou docx. |

Como prática recomendada, você deve reconhecer o upload do arquivo enviando uma mensagem de volta para o usuário.

### <a name="uploading-files-to-personal-chat"></a>Carregando arquivos no chat pessoal

Carregar um arquivo para um usuário envolve as seguintes etapas:

1. Envie uma mensagem para o usuário solicitando permissão para gravar o arquivo. Esta mensagem deve conter um anexo `FileConsentCard` com o nome do arquivo a ser carregado.
2. Se o usuário aceitar o download do arquivo, seu bot receberá uma atividade *Invoke* com uma URL de local.
3. Para transferir o arquivo, o bot executa um `HTTP POST` diretamente na URL de local fornecida.
4. Opcionalmente, você pode remover o cartão de consentimento original se não quiser permitir que o usuário aceite uploads adicionais do mesmo arquivo.

#### <a name="message-requesting-permission-to-upload"></a>Mensagem solicitando permissão para carregar

Esta mensagem da área de trabalho contém um objeto de anexo simples solicitando permissão de usuário para carregar o arquivo:

:::image type="content" source="../../assets/images/bots/bot-file-consent-card.png" alt-text="Captura de tela do cartão de consentimento solicitando permissão do usuário para carregar o arquivo":::

Esta mensagem móvel contém um objeto de anexo solicitando permissão de usuário para carregar o arquivo:

![Captura de tela do cartão de consentimento solicitando permissão do usuário para carregar o arquivo no celular](../../assets/images/bots/mobile-bot-file-consent-card.png)

```json
{
  "attachments": [{
    "contentType": "application/vnd.microsoft.teams.card.file.consent",
    "name": "file_example.txt",
    "content": {
      "description": "<Purpose of the file, such as: this is your monthly expense report>",
      "sizeInBytes": 1029393,
      "acceptContext": {
      },
      "declineContext": {
      }
    }
  }]
}
```

A tabela a seguir descreve as propriedades de conteúdo do anexo:

| Propriedade | Objetivo |
| --- | --- |
| `description` | Descrição do recurso. Pode ser mostrado ao usuário para descrever sua finalidade ou resumir seu conteúdo. |
| `sizeInBytes` | Fornece ao usuário uma estimativa do tamanho do arquivo e da quantidade de espaço que ele levará no OneDrive. |
| `acceptContext` | Contexto adicional que será transmitido silenciosamente para o bot quando o usuário aceitar o arquivo. |
| `declineContext` | Contexto adicional que será transmitido silenciosamente para o bot quando o usuário recusar o arquivo. |

#### <a name="invoke-activity-when-the-user-accepts-the-file"></a>Atividade de invocação quando o usuário aceitar o arquivo

Uma atividade de invocação é enviada ao bot se e quando o usuário aceita o arquivo. Ele contém OneDrive for Business URL de espaço reservado para a qual o bot pode emitir um `PUT` para transferir o conteúdo do arquivo. para obter informações sobre como carregar para a URL do OneDrive, leia este artigo: [Carregue bytes para a sessão de upload](/onedrive/developer/rest-api/api/driveitem_createuploadsession#upload-bytes-to-the-upload-session).

O exemplo a seguir mostra uma versão resumida da atividade de invocação que seu bot receberá:

```json
{
  ...

  "name": "fileConsent/invoke",
  "value": {
    "type": "fileUpload",
    "action": "accept",
    "context": {
    },
    "uploadInfo": {
      "contentUrl": "https://contoso.sharepoint.com/personal/johnadams_contoso_com/Documents/Applications/file_example.txt",
      "name": "file_example.txt",
      "uploadUrl": "https://upload.link",
      "uniqueId": "1150D938-8870-4044-9F2C-5BBDEBA70C8C",
      "fileType": "txt",
      "etag": "123"
    }
  }
}
```

Da mesma forma, se o usuário recusar o arquivo, seu bot receberá o seguinte evento, com o mesmo nome de atividade geral:

```json
{
  "name": "fileConsent/invoke",
  "value": {
    "type": "fileUpload",
    "action": "decline",
    "context": {
    }
  }
}
```

### <a name="notifying-the-user-about-an-uploaded-file"></a>Notificando o usuário sobre um arquivo carregado

Depois de carregar um arquivo no OneDrive do usuário, se você usar o mecanismo descrito acima ou as APIs delegadas pelo usuário do OneDrive, deverá enviar uma mensagem de confirmação ao usuário. Essa mensagem deve conter um `FileCard` anexo no qual o usuário pode selecionar, seja para visualizar, abri-lo no OneDrive ou baixá-lo localmente.

```json
{
  "attachments": [{
    "contentType": "application/vnd.microsoft.teams.card.file.info",
    "contentUrl": "https://contoso.sharepoint.com/personal/johnadams_contoso_com/Documents/Applications/file_example.txt",
    "name": "file_example.txt",
    "content": {
      "uniqueId": "1150D938-8870-4044-9F2C-5BBDEBA70C8C",
      "fileType": "txt",
    }
  }]
}
```

A tabela a seguir descreve as propriedades de conteúdo do anexo:

| Propriedade | Objetivo |
| --- | --- |
| `uniqueId` | ID do item da unidade do OneDrive/SharePoint. |
| `fileType` | Tipo de arquivo, como pdf ou docx. |

### <a name="basic-example-in-c"></a>Exemplo básico em C #

O exemplo a seguir mostra como você pode lidar com uploads de arquivos e enviar solicitações de consentimento de arquivo na caixa de diálogo do bot:

```csharp

// This sample dialog shows two simple flows:
// 1) A silly example of receiving a file from the user, processing the key elements,
//    and then constructing the attachment and sending it back.
// 2) Creating a new file consent card requesting user permission to upload a file.
private async Task MessageReceivedAsync(IDialogContext context, IAwaitable<object> result)
{
    var replyMessage = context.MakeMessage();
    Attachment returnCard;

    var message = await result as Activity;

    // Check to see if the user is sending the bot a file.
    if (message.Attachments != null && message.Attachments.Any())
    {
        var attachment = message.Attachments.First();

        if (attachment.ContentType == FileDownloadInfo.ContentType)
        {
            FileDownloadInfo downloadInfo = (attachment.Content as JObject).ToObject<FileDownloadInfo>();
            if (downloadInfo != null)
            {
                returnCard = CreateFileInfoAttachment(downloadInfo, attachment.Name, attachment.ContentUrl);
                replyMessage.Attachments.Add(returnCard);
            }
        }
    }
    else
    {
        // Illustrates creating a file consent card.
        returnCard = CreateFileConsentAttachment();
        replyMessage.Attachments.Add(returnCard);
    }
    await context.PostAsync(replyMessage);
}


private static Attachment CreateFileInfoAttachment(FileDownloadInfo downloadInfo, string name, string contentUrl)
{
    FileInfoCard card = new FileInfoCard()
    {
        FileType = downloadInfo.FileType,
        UniqueId = downloadInfo.UniqueId
    };

    Attachment att = card.ToAttachment();
    att.ContentUrl = contentUrl;
    att.Name = name;

    return att;
}

private static Attachment CreateFileConsentAttachment()
{
    JObject acceptContext = new JObject();
    // Fill in any additional context to be sent back when the user accepts the file.

    JObject declineContext = new JObject();
    // Fill in any additional context to be sent back when the user declines the file.

    FileConsentCard card = new FileConsentCard()
    {
        AcceptContext = acceptContext,
        DeclineContext = declineContext,
        SizeInBytes = 102635,
        Description = "File description"
    };

    Attachment att = card.ToAttachment();
    att.Name = "Example file";

    return att;
}
```

## <a name="see-also"></a>Confira também

[Trabalhando com arquivos no Microsoft Graph](/graph/api/resources/onedrive)
