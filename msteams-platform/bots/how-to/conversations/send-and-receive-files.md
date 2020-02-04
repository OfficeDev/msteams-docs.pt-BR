---
title: Enviar e receber arquivos
author: clearab
description: Como enviar e receber arquivos com seu bot do Microsoft Teams.
ms.topic: overview
ms.author: anclear
ms.openlocfilehash: e7d703f30dffaf317f22529ab56b76d859ebd8b6
ms.sourcegitcommit: 4329a94918263c85d6c65ff401f571556b80307b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/01/2020
ms.locfileid: "41672851"
---
# <a name="send-and-receive-files-with-a-bot"></a>Enviar e receber arquivos com um bot

[!INCLUDE [v4 to v3 pointer](~/includes/v4-to-v3-pointer-bots.md)]

Este artigo descreve como trocar arquivos com um usuário em um chat de um-para-um com seu bot. Você não pode usar essa funcionalidade para trocar arquivos em uma equipe ou em um chat de grupo.

Há duas abordagens para escolher:

1. **APIs do Microsoft Graph**, que dão suporte a todos os `personal`três `channel`escopos:, e`groupchat`
2. **APIs de bot de equipes**, que só `personal` dão suporte ao escopo.

> [!NOTE] 
> Não há suporte para o envio e o recebimento de arquivos para bots em dispositivos móveis.

## <a name="using-the-microsoft-graph-apis"></a>Usando as APIs do Microsoft Graph

Você pode postar mensagens com anexos de cartão fazendo referência a arquivos existentes do SharePoint usando as APIs do Microsoft Graph para [onedrive e SharePoint](https://docs.microsoft.com/onedrive/developer/rest-api/). Usar as APIs de gráfico requer obter acesso autenticado, por meio do fluxo OAuth 2,0 padrão, para:

- A pasta do OneDrive de um usuário `personal` ( `groupchat` para e arquivos).
- Ou para os arquivos nos canais de uma equipe (para `channel` arquivos). Este método funciona em todos os escopos do Microsoft Teams.

## <a name="using-the-teams-bot-apis"></a>Usando as APIs do bot do teams

O bot pode enviar e receber arquivos diretamente com usuários no `personal` contexto, também conhecido como bate-papos pessoais, usando APIs do teams. Isso permite que você implemente cenários desses relatórios de despesas, reconhecimento de imagem, arquivamento de arquivos, assinaturas e outros cenários que envolvem a manipulação direta do conteúdo do arquivo. Os arquivos compartilhados no Microsoft Teams normalmente aparecem como cartões e permitem uma visualização rica no aplicativo.  A API é fornecida como parte da **plataforma de bot do Microsoft Teams**.

> [!NOTE]
> Este método funciona apenas no `personal` contexto. Ele não funciona no contexto `channel` ou. `groupchat`

### <a name="configure-your-bot-to-support-files"></a>Configurar seu bot para dar suporte a arquivos

Para enviar e receber arquivos no bot, você deve definir a `supportsFiles` Propriedade no manifesto como. `true` Essa propriedade é descrita na seção [bots](https://docs.microsoft.com/microsoftteams/platform/resources/schema/manifest-schema#bots
) da referência do manifesto.

A configuração tem a seguinte aparência `"supportsFiles": true`:.

## <a name="invoke-activity-when-the-user-accepts-the-file-upload"></a>Invocar atividade quando o usuário aceitar o carregamento de arquivo

O arquivo é carregado no armazenamento do **onedrive** do usuário depois que o consentimento para upload é emitido. O bot receberá uma atividade de mensagem que contém metadados do arquivo, como o nome e a URL do conteúdo. Siga estas etapas:

1. Envie uma mensagem para o usuário solicitando permissão para gravar o arquivo. Essa mensagem deve conter um `FileConsentCard` anexo com o nome do arquivo a ser carregado.

    ![cartão de permissão de upload de arquivos bot](../../../assets/images/bots/bot-file-upload-permission-card.png)

2. Se o usuário aceitar o carregamento de arquivo, o bot receberá uma atividade de *invocação* com uma URL de local.
3. Para transferir o arquivo, seu bot executa um `HTTP POST` diretamente na URL de local fornecida.
4. Opcionalmente, você pode remover o cartão de consentimento original se não quiser permitir que o usuário aceite outros carregamentos do mesmo arquivo.
 
O exemplo a seguir mostra uma versão do Abridged da atividade Invoke que seu bot receberá:

```json
{
    "name": "fileConsent/invoke",
    "type": "invoke",
    "timestamp": "2019-10-24T20:22:37.875Z",
    "localTimestamp": "2019-10-24T13:22:37.875-07:00",
    "id": "f:8805947989118514037",

    ...

    "value": {
        "type": "fileUpload",
        "action": "accept",
        "context": {
            "filename": "teams-logo.png"
        },
        "uploadInfo": {
            "contentUrl": "https://contoso.sharepoint.com//personal/<user alias>/Documents/Applications/TeamsFilesBot/teams-logo.png",
            "name": "teams-logo.png",
            "uploadUrl": "https://contoso.sharepoint.com//personal/<user alias>/_api/v2.0/drive/items/01FED6KHQXVVCUCI6XVJCZZMU2WMUSA6JS/uploadSession?guid=<GUID>",
            "uniqueId": "<Unique ID>",
            "fileType": "png"
        }
    },

    "locale": "en-US"
}

```

A tabela a seguir descreve as propriedades de conteúdo do anexo:

| Propriedade | Finalidade |
| --- | --- |
| `uploadUrl` | URL do OneDrive para carregar o conteúdo do arquivo. |
| `uniqueId` | ID de arquivo exclusivo. Esta será a ID de item da unidade do OneDrive. |
| `fileType` | Tipo de extensão de arquivo, como PDF ou * png * *. |

Como prática recomendada, você deve confirmar o carregamento do arquivo enviando de volta uma mensagem para o usuário.

Se o usuário recusar o arquivo, o bot receberá o seguinte evento, com o mesmo nome de atividade geral:

```json
{
  "name": "fileConsent/invoke",
  "value": {
    "type": "fileUpload",
    "action": "decline",
    "context": {
      ...
    }
  }
}
```

### <a name="notifying-the-user-about-an-uploaded-file"></a>Notificar o usuário sobre um arquivo carregado

Após carregar um arquivo no OneDrive do usuário, você deverá enviar uma mensagem de confirmação para o usuário. Esta mensagem deve conter um `FileCard` anexo no qual o usuário pode clicar, para visualizá-lo, abri-lo no onedrive ou baixar localmente. Apresentamos um exemplo a seguir. 

```json
{
  "attachments": [{
    "contentType": "application/vnd.microsoft.teams.card.file.info",
    "contentUrl": "https://contoso.sharepoint.com/personal/johnadams_contoso_com/Documents/Applications/file_example.txt",
    "name": "file_example.txt",
    "content": {
      "uniqueId": "<unique ID>",
      "fileType": "png",
    }
  }]
}

```

A tabela a seguir descreve as propriedades de conteúdo do anexo:

| Propriedade | Finalidade |
| --- | --- |
| `uniqueId` | ID de item da unidade do OneDrive/SharePoint. |
| `fileType` | Tipo de arquivo, como PDF ou docx. |

## <a name="example-using-the-bot-framework-sdk"></a>Exemplo usando o SDK da estrutura de bot

O exemplo a seguir mostra como você pode manipular carregamentos de arquivo e enviar solicitações de consentimento de arquivo para o usuário na caixa de diálogo do bot. Os trechos de código mostrados a seguir, pertencem a um exemplo de executável completo que você pode baixar neste local: [FileUpload](https://github.com/microsoft/botbuilder-dotnet/tree/master/tests/Teams/FileUpload).

# <a name="cnettabdotnet"></a>[C#/.NET](#tab/dotnet)

```csharp
protected override async Task OnMessageActivityAsync(ITurnContext<IMessageActivity> turnContext, CancellationToken cancellationToken)
{
    bool messageWithFileDownloadInfo = turnContext.Activity.Attachments?[0].ContentType == FileDownloadInfo.ContentType;
    if (messageWithFileDownloadInfo)
    {
        var file = turnContext.Activity.Attachments[0];
        var fileDownload = JObject.FromObject(file.Content).ToObject<FileDownloadInfo>();

        string filePath = Path.Combine("Files", file.Name);

        var client = _clientFactory.CreateClient();
        var response = await client.GetAsync(fileDownload.DownloadUrl);
        using (var fileStream = new FileStream(filePath, FileMode.Create, FileAccess.Write, FileShare.None))
        {
            await response.Content.CopyToAsync(fileStream);
        }

        var reply = ((Activity)turnContext.Activity).CreateReply();
        reply.TextFormat = "xml";
        reply.Text = $"Complete downloading <b>{file.Name}</b>";
        await turnContext.SendActivityAsync(reply, cancellationToken);
    }
    else
    {
        string filename = "teams-logo.png";
        string filePath = Path.Combine("Files", filename);
        long fileSize = new FileInfo(filePath).Length;
        await SendFileCardAsync(turnContext, filename, fileSize, cancellationToken);
    }
}

private async Task SendFileCardAsync(ITurnContext turnContext, string filename, long filesize, CancellationToken cancellationToken)
{
    var consentContext = new Dictionary<string, string>
    {
        { "filename", filename },
    };

    var fileCard = new FileConsentCard
    {
        Description = "This is the file I want to send you",
        SizeInBytes = filesize,
        AcceptContext = consentContext,
        DeclineContext = consentContext,
    };

    var asAttachment = new Attachment
    {
        Content = fileCard,
        ContentType = FileConsentCard.ContentType,
        Name = filename,
    };

    var replyActivity = turnContext.Activity.CreateReply();
    replyActivity.Attachments = new List<Attachment>() { asAttachment };

    await turnContext.SendActivityAsync(replyActivity, cancellationToken);
}

protected override async Task OnTeamsFileConsentAcceptAsync(ITurnContext<IInvokeActivity> turnContext, FileConsentCardResponse fileConsentCardResponse, CancellationToken cancellationToken)
{
    try
    {
        JToken context = JObject.FromObject(fileConsentCardResponse.Context);

        string filePath = Path.Combine("Files", context["filename"].ToString());
        long fileSize = new FileInfo(filePath).Length;
        var client = _clientFactory.CreateClient();
        using (var fileStream = File.OpenRead(filePath))
        {
            var fileContent = new StreamContent(fileStream);
            fileContent.Headers.ContentLength = fileSize;
            fileContent.Headers.ContentRange = new ContentRangeHeaderValue(0, fileSize - 1, fileSize);
            await client.PutAsync(fileConsentCardResponse.UploadInfo.UploadUrl, fileContent, cancellationToken);
        }

        await FileUploadCompletedAsync(turnContext, fileConsentCardResponse, cancellationToken);
    }
    catch (Exception e)
    {
        await FileUploadFailedAsync(turnContext, e.ToString(), cancellationToken);
    }
}

protected override async Task OnTeamsFileConsentDeclineAsync(ITurnContext<IInvokeActivity> turnContext, FileConsentCardResponse fileConsentCardResponse, CancellationToken cancellationToken)
{
    JToken context = JObject.FromObject(fileConsentCardResponse.Context);

    var reply = ((Activity)turnContext.Activity).CreateReply();
    reply.TextFormat = "xml";
    reply.Text = $"Declined. We won't upload file <b>{context["filename"]}</b>.";
    await turnContext.SendActivityAsync(reply, cancellationToken);
}
```

# <a name="typescriptnodejstabtypescript"></a>[TypeScript/node. js](#tab/typescript)

<!-- From sample: libraries\botbuilder\tests\teams\fileUpload\src\fileUploadBot.ts-->

```typescript

export class FileUploadBot extends TeamsActivityHandler {
    constructor() {
        super();

        this.onMessage(async (context, next) => {
            await this.sendFileCard(context);
            await next();
        });

        this.onMembersAdded(async (context, next) => {
            const membersAdded = context.activity.membersAdded;
            for (const member of membersAdded) {
                if (member.id !== context.activity.recipient.id) {
                    await context.sendActivity('Hello and welcome!');
                }
            }
            await next();
        });
    }

    private async sendFileCard(context: TurnContext): Promise<void> {
        let filename = "file name";
        let fs = require('fs'); 
        let path = require('path');
        let stats = fs.statSync(path.join('files', filename));
        let fileSizeInBytes = stats['size'];

        let fileContext = {
            filename: filename
        };

        let attachment = {
            content: <FileConsentCard>{
                description: 'This is the file I want to send you',
                fileSizeInBytes: fileSizeInBytes,
                acceptContext: fileContext,
                declineContext: fileContext
            },
            contentType: 'application/vnd.microsoft.teams.card.file.consent',
            name: filename
        } as Attachment;

        var replyActivity = this.createReply(context.activity);
        replyActivity.attachments = [ attachment ];
        await context.sendActivity(replyActivity);
    }

    protected async handleTeamsFileConsentAccept(context: TurnContext, fileConsentCardResponse: FileConsentCardResponse): Promise<void> {
        try {
            await this.sendFile(fileConsentCardResponse);
            await this.fileUploadCompleted(context, fileConsentCardResponse);
        }
        catch (err) {
            await this.fileUploadFailed(context, err.toString());
        }
    }

    protected async handleTeamsFileConsentDecline(context: TurnContext, fileConsentCardResponse: FileConsentCardResponse): Promise<void> {
        let reply = this.createReply(context.activity);
        reply.textFormat = "xml";
        reply.text = `Declined. We won't upload file <b>${fileConsentCardResponse.context["filename"]}</b>.`;
        await context.sendActivity(reply);
    }
...

}

```

<!-- Python samples verify -->

# <a name="pythontabpython"></a>[Python](#tab/python)

```python
class TeamsFileUploadBot(TeamsActivityHandler):
    async def on_message_activity(self, turn_context: TurnContext):
        message_with_file_download = (
            False
            if not turn_context.activity.attachments
            else turn_context.activity.attachments[0].content_type == ContentType.FILE_DOWNLOAD_INFO
        )

        if message_with_file_download:
            # Save an uploaded file locally
            file = turn_context.activity.attachments[0]
            file_download = FileDownloadInfo.deserialize(file.content)
            file_path = "files/" + file.name

            response = requests.get(file_download.download_url, allow_redirects=True)
            open(file_path, "wb").write(response.content)

            reply = self._create_reply(
                turn_context.activity, f"Complete downloading <b>{file.name}</b>", "xml"
            )
            await turn_context.send_activity(reply)
        else:
            # Attempt to upload a file to Teams.  This will display a confirmation to
            # the user (Accept/Decline card).  If they accept, on_teams_file_consent_accept
            # will be called, otherwise on_teams_file_consent_decline.
            filename = "teams-logo.png"
            file_path = "files/" + filename
            file_size = os.path.getsize(file_path)
            await self._send_file_card(turn_context, filename, file_size)

    async def _send_file_card(
            self, turn_context: TurnContext, filename: str, file_size: int
    ):
        """
        Send a FileConsentCard to get permission from the user to upload a file.
        """

        consent_context = {"filename": filename}

        file_card = FileConsentCard(
            description="This is the file I want to send you",
            size_in_bytes=file_size,
            accept_context=consent_context,
            decline_context=consent_context
        )

        as_attachment = Attachment(
            content=file_card.serialize(), content_type=ContentType.FILE_CONSENT_CARD, name=filename
        )

        reply_activity = self._create_reply(turn_context.activity)
        reply_activity.attachments = [as_attachment]
        await turn_context.send_activity(reply_activity)

    async def on_teams_file_consent_accept(
            self,
            turn_context: TurnContext,
            file_consent_card_response: FileConsentCardResponse
    ):
        """
        The user accepted the file upload request.  Do the actual upload now.
        """

        file_path = "files/" + file_consent_card_response.context["filename"]
        file_size = os.path.getsize(file_path)

        headers = {
            "Content-Length": f"\"{file_size}\"",
            "Content-Range": f"bytes 0-{file_size-1}/{file_size}"
        }
        response = requests.put(
            file_consent_card_response.upload_info.upload_url, open(file_path, "rb"), headers=headers
        )

        if response.status_code != 200:
            await self._file_upload_failed(turn_context, "Unable to upload file.")
        else:
            await self._file_upload_complete(turn_context, file_consent_card_response)

    async def on_teams_file_consent_decline(
            self,
            turn_context: TurnContext,
            file_consent_card_response: FileConsentCardResponse
    ):
        """
        The user declined the file upload.
        """

        context = file_consent_card_response.context

        reply = self._create_reply(
            turn_context.activity,
            f"Declined. We won't upload file <b>{context['filename']}</b>.",
            "xml"
        )
        await turn_context.send_activity(reply)

    async def _file_upload_complete(
            self,
            turn_context: TurnContext,
            file_consent_card_response: FileConsentCardResponse
    ):
        """
        The file was uploaded, so display a FileInfoCard so the user can view the
        file in Teams.
        """

        name = file_consent_card_response.upload_info.name

        download_card = FileInfoCard(
            unique_id=file_consent_card_response.upload_info.unique_id,
            file_type=file_consent_card_response.upload_info.file_type
        )

        as_attachment = Attachment(
            content=download_card.serialize(),
            content_type=ContentType.FILE_INFO_CARD,
            name=name,
            content_url=file_consent_card_response.upload_info.content_url
        )

        reply = self._create_reply(
            turn_context.activity,
            f"<b>File uploaded.</b> Your file <b>{name}</b> is ready to download",
            "xml"
        )
        reply.attachments = [as_attachment]

        await turn_context.send_activity(reply)

    async def _file_upload_failed(self, turn_context: TurnContext, error: str):
        reply = self._create_reply(
            turn_context.activity,
            f"<b>File upload failed.</b> Error: <pre>{error}</pre>",
            "xml"
        )
        await turn_context.send_activity(reply)

    def _create_reply(self, activity, text=None, text_format=None):
        return Activity(
            type=ActivityTypes.message,
            timestamp=datetime.utcnow(),
            from_property=ChannelAccount(
                id=activity.recipient.id, name=activity.recipient.name
            ),
            recipient=ChannelAccount(
                id=activity.from_property.id, name=activity.from_property.name
            ),
            reply_to_id=activity.id,
            service_url=activity.service_url,
            channel_id=activity.channel_id,
            conversation=ConversationAccount(
                is_group=activity.conversation.is_group,
                id=activity.conversation.id,
                name=activity.conversation.name,
            ),
            text=text or "",
            text_format=text_format or None,
            locale=activity.locale,
        )


```

---
