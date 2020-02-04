---
title: Envio e recebimento de arquivos de um bot
description: Descreve como enviar e receber arquivos de um bot
keywords: arquivos de bots de equipes enviar recebimento
ms.date: 05/20/2019
ms.openlocfilehash: ee26b4031c6022ab30ec5b2b58b42105c2dc6b0f
ms.sourcegitcommit: 4329a94918263c85d6c65ff401f571556b80307b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/01/2020
ms.locfileid: "41672935"
---
# <a name="send-and-receive-files-through-your-bot"></a>Enviar e receber arquivos através do bot

[!include[v3-to-v4-SDK-pointer](~/includes/v3-to-v4-pointer-bots.md)]

Há duas maneiras de enviar arquivos para e de um bot:

* Usando as APIs do Microsoft Graph. Este método funciona para bots em todos os escopos no Teams:
  * `personal`
  * `channel`
  * `groupchat`
* Usando as APIs do teams. Eles só dão suporte a arquivos em um contexto:
  * `personal`

## <a name="using-the-microsoft-graph-apis"></a>Usando as APIs do Microsoft Graph

Você pode postar mensagens com anexos de cartão fazendo referência a arquivos existentes do SharePoint usando as APIs do Microsoft Graph para [onedrive e SharePoint](/onedrive/developer/rest-api/). O uso das APIs de gráfico requer a obtenção de acesso à pasta do OneDrive `personal` de `groupchat` um usuário (para arquivos) ou dos arquivos em um canal `channel` de equipe (para arquivos) por meio do fluxo de autorização OAuth 2,0 padrão. Este método funciona em todos os escopos do Microsoft Teams.

## <a name="using-the-teams-bot-apis"></a>Usando as APIs do bot do teams

> [!NOTE]
> Este método funciona apenas no `personal` contexto. Ele não funciona no contexto `channel` ou. `groupchat`

O bot pode enviar e receber arquivos diretamente com usuários no `personal` contexto, também conhecido como bate-papos pessoais, usando APIs do teams. Isso permite que você implemente relatórios de despesas, reconhecimento de imagens, arquivamento, assinaturas e outros cenários que envolvem a manipulação direta do conteúdo do arquivo. Os arquivos compartilhados no Microsoft Teams normalmente aparecem como cartões e permitem uma visualização rica no aplicativo.

As seções a seguir descrevem como fazer isso para enviar conteúdo de arquivo como resultado de interação direta do usuário, como enviar uma mensagem. Essa API é fornecida como parte da plataforma de bot do Microsoft Teams.

### <a name="configure-your-bot-to-support-files"></a>Configurar seu bot para dar suporte a arquivos

Para enviar e receber arquivos no bot, você precisa definir a `supportsFiles` Propriedade no manifesto como. `true` Essa propriedade é descrita na seção [bots](~/resources/schema/manifest-schema.md#bots) da referência do manifesto.

A definição terá a seguinte aparência: `"supportsFiles": true`. Se o seu bot não habilitar `supportsFiles`, os seguintes recursos não funcionarão.

### <a name="receiving-files-in-personal-chat"></a>Recebendo arquivos no chat pessoal

Quando um usuário envia um arquivo para o bot, o arquivo é carregado primeiro no armazenamento do OneDrive for Business do usuário. O bot receberá uma atividade de mensagem notificando você sobre o carregamento do usuário. A atividade conterá metadados de arquivo, como o nome e a URL do conteúdo. Você pode ler diretamente desta URL para buscar o conteúdo binário.

### <a name="send-and-receive-files-through-bot-on-teams-mobile-app"></a>Enviar e receber arquivos por meio de bot no aplicativo móvel do Microsoft Teams
> [!NOTE] 
> Não há suporte para o envio e o recebimento de arquivos para bots em dispositivos móveis.

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

| Propriedade | Finalidade |
| --- | --- |
| `downloadUrl` | URL do OneDrive para buscar o conteúdo do arquivo. Você pode emitir um `HTTP GET` diretamente desta URL. |
| `uniqueId` | ID de arquivo exclusivo. Essa será a ID de item da unidade do OneDrive, no caso do usuário que está enviando um arquivo para o bot. |
| `fileType` | Tipo de extensão de arquivo, como PDF ou docx. |

Como prática recomendada, você deve confirmar o carregamento do arquivo enviando de volta uma mensagem para o usuário.

### <a name="uploading-files-to-personal-chat"></a>Carregando arquivos para o chat pessoal

Carregar um arquivo para um usuário envolve as seguintes etapas:

1. Envie uma mensagem para o usuário solicitando permissão para gravar o arquivo. Essa mensagem deve conter um `FileConsentCard` anexo com o nome do arquivo a ser carregado.
2. Se o usuário aceitar o download de arquivo, o bot receberá uma atividade de *invocação* com uma URL de local.
3. Para transferir o arquivo, seu bot executa um `HTTP POST` diretamente na URL de local fornecida.
4. Opcionalmente, você pode remover o cartão de consentimento original se não quiser permitir que o usuário aceite outros carregamentos do mesmo arquivo.

#### <a name="message-requesting-permission-to-upload"></a>Mensagem solicitando permissão para carregar

Esta mensagem contém um objeto Attachment simples solicitando permissão de usuário para carregar o arquivo.

![Captura de tela do cartão de consentimento solicitando permissão do usuário para carregar o arquivo](~/assets/images/bots/bot-file-consent-card.png)

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

| Propriedade | Finalidade |
| --- | --- |
| `description` | Descrição do arquivo. Pode ser exibido para o usuário descrever sua finalidade ou resumir seu conteúdo. |
| `sizeInBytes` | Fornece ao usuário uma estimativa do tamanho do arquivo e a quantidade de espaço que ele levará no OneDrive. |
| `acceptContext` | Contexto adicional que será transmitido silenciosamente ao bot quando o usuário aceitar o arquivo. |
| `declineContext` | Contexto adicional que será transmitido silenciosamente ao bot quando o usuário recusar o arquivo. |

#### <a name="invoke-activity-when-the-user-accepts-the-file"></a>Invocar atividade quando o usuário aceitar o arquivo

Uma atividade de invocação será enviada ao seu bot se e quando o usuário aceitar o arquivo. Ele contém a URL do espaço reservado do OneDrive for Business que o seu bot `PUT` pode emitir para para transferir o conteúdo do arquivo. para obter informações sobre como carregar para a URL do OneDrive, leia este artigo: [carregar bytes na sessão de upload](/onedrive/developer/rest-api/api/driveitem_createuploadsession#upload-bytes-to-the-upload-session).

O exemplo a seguir mostra uma versão do Abridged da atividade Invoke que seu bot receberá:

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

Após carregar um arquivo para o OneDrive do usuário, quer você use o mecanismo descrito acima ou APIs delegadas do usuário do OneDrive, você deve enviar uma mensagem de confirmação para o usuário. Esta mensagem deve conter um `FileCard` anexo no qual o usuário pode clicar, para visualizá-lo, abri-lo no onedrive ou baixar localmente.

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

| Propriedade | Finalidade |
| --- | --- |
| `uniqueId` | ID de item da unidade do OneDrive/SharePoint. |
| `fileType` | Tipo de arquivo, como PDF ou docx. |

### <a name="basic-example-in-c"></a>Exemplo básico em C #

O exemplo a seguir mostra como você pode lidar com carregamentos de arquivo e enviar solicitações de consentimento de arquivo na caixa de diálogo de seu bot.

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
