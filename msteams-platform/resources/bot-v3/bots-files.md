---
title: Enviando e recebendo arquivos de um bot
description: Descreve como enviar e receber arquivos de um bot
keywords: equipes arquivos bots enviar receber receber
ms.topic: how-to
localization_priority: Normal
ms.date: 05/20/2019
ms.openlocfilehash: f69a6ca9cfcdf3b1e559fbe8cf569accf3166f69
ms.sourcegitcommit: 51e4a1464ea58c254ad6bd0317aca03ebf6bf1f6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2021
ms.locfileid: "52566478"
---
# <a name="send-and-receive-files-through-your-bot"></a>Envie e receba arquivos através do seu bot

[!include[v3-to-v4-SDK-pointer](~/includes/v3-to-v4-pointer-bots.md)]

Existem duas maneiras de enviar arquivos de e para um bot:

* Usando as APIs Graph microsoft. Este método funciona para bots em todos os escopos em Teams:
  * `personal`
  * `channel`
  * `groupchat`
* Usando as APIs Teams. Estes só suportam arquivos em um contexto:
  * `personal`

## <a name="using-the-microsoft-graph-apis"></a>Usando as APIs de Graph da Microsoft

Você pode postar mensagens com anexos de cartão fazendo referência aos arquivos SharePoint existentes usando as APIs Graph da Microsoft para [OneDrive e SharePoint](/onedrive/developer/rest-api/). O uso do Graph APIs requer obter acesso à pasta OneDrive (para `personal` e `groupchat` arquivos) de um usuário ou aos arquivos nos canais de uma equipe (para `channel` arquivos) através do fluxo padrão de autorização OAuth 2.0. Este método funciona em todos os Teams escopos.

## <a name="using-the-teams-bot-apis"></a>Usando as APIs do Bot Teams

> [!NOTE]
> Esse método funciona apenas no `personal` contexto. Não funciona no `channel` `groupchat` contexto.

Seu bot pode enviar e receber arquivos diretamente com usuários no `personal` contexto, também conhecidos como chats pessoais, usando Teams APIs. Isso permite implementar relatórios de despesas, reconhecimento de imagem, arquivamento de arquivos, assinaturas de e e outros cenários envolvendo manipulação direta de conteúdo de arquivo. Arquivos compartilhados em Teams normalmente aparecem como cartões e permitem visualização rica no aplicativo.

As seções a seguir descrevem como fazer isso para enviar conteúdo de arquivo como resultado da interação direta do usuário, como enviar uma mensagem. Esta API é fornecida como parte da plataforma bot Microsoft Teams.

### <a name="configure-your-bot-to-support-files"></a>Configure seu bot para suportar arquivos

Para enviar e receber arquivos em seu bot, você tem que definir a `supportsFiles` propriedade no manifesto para `true` . Esta propriedade está descrita na seção [bots](~/resources/schema/manifest-schema.md#bots) da referência Manifest.

A definição será assim: `"supportsFiles": true` . Se o bot não `supportsFiles` habilitar, os seguintes recursos não funcionarão.

### <a name="receiving-files-in-personal-chat"></a>Recebimento de arquivos em chat pessoal

Quando um usuário envia um arquivo para o seu bot, o arquivo é carregado pela primeira vez para o armazenamento OneDrive for Business do usuário. Em seguida, seu bot receberá uma atividade de mensagem notificando-o do upload do usuário. A atividade conterá metadados de arquivo, como seu nome e a URL de conteúdo. Você pode ler diretamente a partir desta URL para buscar seu conteúdo binário.

#### <a name="message-activity-with-file-attachment-example"></a>Atividade de mensagem com exemplo de anexo de arquivo

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
| `downloadUrl` | OneDrive URL para buscar o conteúdo do arquivo. Você pode emitir um `HTTP GET` diretamente desta URL. |
| `uniqueId` | ID de arquivo único. Este será o OneDrive iD do item de unidade, no caso do usuário enviar um arquivo para o seu bot. |
| `fileType` | Tipo de extensão de arquivo, como pdf ou docx. |

Como uma prática recomendada, você deve reconhecer o upload do arquivo enviando uma mensagem para o usuário.

### <a name="uploading-files-to-personal-chat"></a>Upload de arquivos para bate-papo pessoal

O upload de um arquivo para um usuário envolve as seguintes etapas:

1. Envie uma mensagem ao usuário solicitando permissão para escrever o arquivo. Esta mensagem deve conter um `FileConsentCard` anexo com o nome do arquivo a ser carregado.
2. Se o usuário aceitar o download do arquivo, o bot receberá uma atividade *de Invocação* com uma URL de localização.
3. Para transferir o arquivo, o bot executa um `HTTP POST` diretamente na URL de localização fornecida.
4. Opcionalmente, você pode remover o cartão de consentimento original se não quiser permitir que o usuário aceite uploads adicionais do mesmo arquivo.

#### <a name="message-requesting-permission-to-upload"></a>Mensagem solicitando permissão para carregar

Esta mensagem de desktop contém um simples objeto de anexo solicitando permissão do usuário para carregar o arquivo:

![Captura de tela do cartão de consentimento solicitando permissão do usuário para carregar arquivo](../../assets/images/bots/bot-file-consent-card.png)

Esta mensagem móvel contém um objeto de anexo solicitando permissão do usuário para carregar o arquivo:

![Captura de tela do cartão de consentimento solicitando permissão do usuário para carregar arquivo no celular](../../assets/images/bots/mobile-bot-file-consent-card.png)

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
| `description` | Descrição do arquivo. Pode ser mostrado ao usuário para descrever seu propósito ou para resumir seu conteúdo. |
| `sizeInBytes` | Fornece ao usuário uma estimativa do tamanho do arquivo e da quantidade de espaço que ele ocupará OneDrive. |
| `acceptContext` | Contexto adicional que será transmitido silenciosamente ao seu bot quando o usuário aceitar o arquivo. |
| `declineContext` | Contexto adicional que será transmitido silenciosamente ao seu bot quando o usuário recusar o arquivo. |

#### <a name="invoke-activity-when-the-user-accepts-the-file"></a>Invoque a atividade quando o usuário aceitar o arquivo

Uma atividade de invocação é enviada ao seu bot se e quando o usuário aceitar o arquivo. Ele contém a URL OneDrive for Business espaço reservado que o seu bot pode então `PUT` emitir para transferir o conteúdo do arquivo. para informações sobre o upload para a URL OneDrive leia este artigo: [Upload bytes para a sessão de upload](/onedrive/developer/rest-api/api/driveitem_createuploadsession#upload-bytes-to-the-upload-session).

O exemplo a seguir mostra uma versão abreviada da atividade de invocação que seu bot receberá:

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

Da mesma forma, se o usuário recusar o arquivo, o bot receberá o seguinte evento, com o mesmo nome de atividade geral:

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

### <a name="notifying-the-user-about-an-uploaded-file"></a>Notificar o usuário sobre um arquivo carregado

Depois de carregar um arquivo para a OneDrive do usuário, se você usar o mecanismo descrito acima ou OneDrive APIs delegadas pelo usuário, você deve enviar uma mensagem de confirmação ao usuário. Esta mensagem deve conter um `FileCard` anexo no qual o usuário pode clicar, seja para visualizá-la, abri-la em OneDrive ou baixar localmente.

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
| `uniqueId` | OneDrive/SharePoint iD do item de unidade. |
| `fileType` | Tipo de arquivo, como pdf ou docx. |

### <a name="basic-example-in-c"></a>Exemplo básico em C #

A amostra a seguir mostra como você pode lidar com uploads de arquivos e enviar solicitações de consentimento do arquivo na caixa de diálogo do seu bot:

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
