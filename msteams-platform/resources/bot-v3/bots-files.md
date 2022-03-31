---
title: Enviando e recebendo arquivos de um bot
description: Saiba como enviar e receber arquivos por meio do bot usando Graph APIs para escopos pessoais, de canal e de groupchat. Use Teams de bot usando exemplos de código com base no SDK da Estrutura de Bots v3.
keywords: arquivos de bots do teams enviam recebimento
ms.topic: how-to
ms.localizationpriority: medium
ms.date: 05/20/2019
ms.openlocfilehash: c95ddbc4bfe0d491f48101b12d8658f7714c0075
ms.sourcegitcommit: 52af681132e496a57b18f468c5b73265a49a5f44
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/31/2022
ms.locfileid: "64590749"
---
# <a name="send-and-receive-files-through-your-bot"></a>Enviar e receber arquivos por meio do seu bot

[!include[v3-to-v4-SDK-pointer](~/includes/v3-to-v4-pointer-bots.md)]

Há duas maneiras de enviar arquivos de e para um bot:

* Usando as APIs Graph Microsoft. Este método funciona para bots em todos os escopos em Teams:
  * `personal`
  * `channel`
  * `groupchat`
* Usando as APIs Teams de usuário. Esses arquivos só suportam em um contexto:
  * `personal`

## <a name="using-the-microsoft-graph-apis"></a>Usando as APIs Graph Microsoft

Você pode postar mensagens com anexos de cartão fazendo referência SharePoint arquivos existentes usando as APIs do Microsoft Graph para OneDrive [e SharePoint](/onedrive/developer/rest-api/). O uso das APIs Graph requer a obtenção de acesso à pasta de OneDrive do usuário (para `personal` `groupchat` e arquivos) ou aos arquivos nos canais de uma equipe (`channel`para arquivos) por meio do fluxo de autorização padrão do OAuth 2.0. Esse método funciona em todos os Teams escopos.

## <a name="using-the-teams-bot-apis"></a>Usando as APIs Teams Bot

> [!NOTE]
> Esse método só funciona no `personal` contexto. Ele não funciona no contexto `channel` ou `groupchat` .

Seu bot pode enviar e receber `personal` arquivos diretamente com usuários no contexto, também conhecidos como chats pessoais, usando Teams APIs. Isso permite implementar relatórios de despesas, reconhecimento de imagem, arquivamento de arquivos, assinaturas eletrônicas e outros cenários envolvendo manipulação direta do conteúdo do arquivo. Os arquivos compartilhados Teams normalmente são exibidos como cartões e permitem a exibição rica no aplicativo.

As seções a seguir descrevem como fazer isso para enviar conteúdo de arquivo como resultado da interação direta do usuário, como o envio de uma mensagem. Essa API é fornecida como parte da plataforma Microsoft Teams Bot.

### <a name="configure-your-bot-to-support-files"></a>Configurar seu bot para dar suporte a arquivos

Para enviar e receber arquivos em seu bot, você precisa `supportsFiles` definir a propriedade no manifesto como `true`. Essa propriedade é descrita na seção [bots](~/resources/schema/manifest-schema.md#bots) da referência manifesto.

A definição será assim: `"supportsFiles": true`. Se o bot não habilitar `supportsFiles`, os recursos a seguir não funcionarão.

### <a name="receiving-files-in-personal-chat"></a>Recebimento de arquivos no chat pessoal

Quando um usuário envia um arquivo para o bot, o arquivo é carregado pela primeira vez no armazenamento OneDrive for Business usuário. Em seguida, o bot receberá uma atividade de mensagem notificando o carregamento do usuário. A atividade conterá metadados de arquivo, como seu nome e a URL de conteúdo. Você pode ler diretamente a partir dessa URL para buscar seu conteúdo binário.

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
| `downloadUrl` | OneDrive URL para buscar o conteúdo do arquivo. Você pode emitir um `HTTP GET` diretamente a partir dessa URL. |
| `uniqueId` | ID de arquivo exclusivo. Essa será a OneDrive ID do item da unidade, no caso do usuário enviar um arquivo para o bot. |
| `fileType` | Tipo de extensão de arquivo, como pdf ou docx. |

Como prática prática, você deve reconhecer o carregamento de arquivo enviando uma mensagem para o usuário.

### <a name="uploading-files-to-personal-chat"></a>Carregando arquivos para chat pessoal

Carregar um arquivo para um usuário envolve as seguintes etapas:

1. Envie uma mensagem para o usuário solicitando permissão para gravar o arquivo. Esta mensagem deve conter um `FileConsentCard` anexo com o nome do arquivo a ser carregado.
2. Se o usuário aceitar o download do arquivo, seu bot receberá uma atividade *Invocar* com uma URL de local.
3. Para transferir o arquivo, seu bot executa um diretamente para a `HTTP POST` URL de local fornecida.
4. Opcionalmente, você pode remover o cartão de consentimento original se não quiser permitir que o usuário aceite mais carregamentos do mesmo arquivo.

#### <a name="message-requesting-permission-to-upload"></a>Mensagem solicitando permissão para carregar

Esta mensagem da área de trabalho contém um objeto de anexo simples solicitando permissão do usuário para carregar o arquivo:

![Captura de tela do cartão de consentimento solicitando permissão do usuário para carregar arquivo](../../assets/images/bots/bot-file-consent-card.png)

Esta mensagem móvel contém um objeto attachment solicitando permissão do usuário para carregar o arquivo:

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
| `description` | Descrição do arquivo. Pode ser mostrado ao usuário para descrever sua finalidade ou resumir seu conteúdo. |
| `sizeInBytes` | Fornece ao usuário uma estimativa do tamanho do arquivo e da quantidade de espaço que ele levará em OneDrive. |
| `acceptContext` | Contexto adicional que será transmitido silenciosamente para o bot quando o usuário aceitar o arquivo. |
| `declineContext` | Contexto adicional que será transmitido silenciosamente para o bot quando o usuário recusar o arquivo. |

#### <a name="invoke-activity-when-the-user-accepts-the-file"></a>Invocar atividade quando o usuário aceitar o arquivo

Uma atividade de invocação é enviada ao bot se e quando o usuário aceitar o arquivo. Ele contém a URL OneDrive for Business espaço reservado que seu bot pode emitir para `PUT` transferir o conteúdo do arquivo. para obter informações sobre como carregar na URL OneDrive leia este artigo: Upload [bytes para a sessão de carregamento](/onedrive/developer/rest-api/api/driveitem_createuploadsession#upload-bytes-to-the-upload-session).

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

### <a name="notifying-the-user-about-an-uploaded-file"></a>Notificar o usuário sobre um arquivo carregado

Depois de carregar um arquivo no OneDrive do usuário, se você usar o mecanismo descrito acima ou OneDrive APIs delegadas pelo usuário, deverá enviar uma mensagem de confirmação ao usuário. Esta mensagem deve conter um `FileCard` anexo no qual o usuário pode clicar, para visualiza-la, abri-la OneDrive ou baixar localmente.

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
| `uniqueId` | OneDrive/SharePoint ID do item da unidade. |
| `fileType` | Tipo de arquivo, como pdf ou docx. |

### <a name="basic-example-in-c"></a>Exemplo básico em C #

O exemplo a seguir mostra como você pode lidar com carregamentos de arquivos e enviar solicitações de consentimento de arquivo na caixa de diálogo do bot:

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
