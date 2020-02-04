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
# <a name="send-and-receive-files-with-a-bot"></a><span data-ttu-id="dbb6a-103">Enviar e receber arquivos com um bot</span><span class="sxs-lookup"><span data-stu-id="dbb6a-103">Send and receive files with a bot</span></span>

[!INCLUDE [v4 to v3 pointer](~/includes/v4-to-v3-pointer-bots.md)]

<span data-ttu-id="dbb6a-104">Este artigo descreve como trocar arquivos com um usuário em um chat de um-para-um com seu bot.</span><span class="sxs-lookup"><span data-stu-id="dbb6a-104">This article describe how to exchange files with a user in a one-to-one chat with your bot.</span></span> <span data-ttu-id="dbb6a-105">Você não pode usar essa funcionalidade para trocar arquivos em uma equipe ou em um chat de grupo.</span><span class="sxs-lookup"><span data-stu-id="dbb6a-105">You cannot use this functionality to exchange files in a team or group chat.</span></span>

<span data-ttu-id="dbb6a-106">Há duas abordagens para escolher:</span><span class="sxs-lookup"><span data-stu-id="dbb6a-106">There are two approaches to choose from:</span></span>

1. <span data-ttu-id="dbb6a-107">**APIs do Microsoft Graph**, que dão suporte a todos os `personal`três `channel`escopos:, e`groupchat`</span><span class="sxs-lookup"><span data-stu-id="dbb6a-107">**Microsoft Graph APIs**, which supports all three scopes: `personal`, `channel`, and `groupchat`</span></span>
2. <span data-ttu-id="dbb6a-108">**APIs de bot de equipes**, que só `personal` dão suporte ao escopo.</span><span class="sxs-lookup"><span data-stu-id="dbb6a-108">**Teams bot APIs**, which only support the `personal` scope.</span></span>

> [!NOTE] 
> <span data-ttu-id="dbb6a-109">Não há suporte para o envio e o recebimento de arquivos para bots em dispositivos móveis.</span><span class="sxs-lookup"><span data-stu-id="dbb6a-109">Sending and receiving files to bots on mobile devices is not supported.</span></span>

## <a name="using-the-microsoft-graph-apis"></a><span data-ttu-id="dbb6a-110">Usando as APIs do Microsoft Graph</span><span class="sxs-lookup"><span data-stu-id="dbb6a-110">Using the Microsoft Graph APIs</span></span>

<span data-ttu-id="dbb6a-111">Você pode postar mensagens com anexos de cartão fazendo referência a arquivos existentes do SharePoint usando as APIs do Microsoft Graph para [onedrive e SharePoint](https://docs.microsoft.com/onedrive/developer/rest-api/).</span><span class="sxs-lookup"><span data-stu-id="dbb6a-111">You can post messages with card attachments referencing existing SharePoint files using the Microsoft Graph APIs for [OneDrive and SharePoint](https://docs.microsoft.com/onedrive/developer/rest-api/).</span></span> <span data-ttu-id="dbb6a-112">Usar as APIs de gráfico requer obter acesso autenticado, por meio do fluxo OAuth 2,0 padrão, para:</span><span class="sxs-lookup"><span data-stu-id="dbb6a-112">Using the Graph APIs requires obtaining authenticated access, through the standard OAuth 2.0 flow, to:</span></span>

- <span data-ttu-id="dbb6a-113">A pasta do OneDrive de um usuário `personal` ( `groupchat` para e arquivos).</span><span class="sxs-lookup"><span data-stu-id="dbb6a-113">A user's OneDrive folder (for `personal` and `groupchat` files).</span></span>
- <span data-ttu-id="dbb6a-114">Ou para os arquivos nos canais de uma equipe (para `channel` arquivos).</span><span class="sxs-lookup"><span data-stu-id="dbb6a-114">Or to the files in a team's channels (for `channel` files).</span></span> <span data-ttu-id="dbb6a-115">Este método funciona em todos os escopos do Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="dbb6a-115">This method works in all Teams scopes.</span></span>

## <a name="using-the-teams-bot-apis"></a><span data-ttu-id="dbb6a-116">Usando as APIs do bot do teams</span><span class="sxs-lookup"><span data-stu-id="dbb6a-116">Using the Teams Bot APIs</span></span>

<span data-ttu-id="dbb6a-117">O bot pode enviar e receber arquivos diretamente com usuários no `personal` contexto, também conhecido como bate-papos pessoais, usando APIs do teams.</span><span class="sxs-lookup"><span data-stu-id="dbb6a-117">Your bot can directly send and receive files with users in the `personal` context, also known as personal chats, using Teams APIs.</span></span> <span data-ttu-id="dbb6a-118">Isso permite que você implemente cenários desses relatórios de despesas, reconhecimento de imagem, arquivamento de arquivos, assinaturas e outros cenários que envolvem a manipulação direta do conteúdo do arquivo.</span><span class="sxs-lookup"><span data-stu-id="dbb6a-118">This lets you implement scenarios such expense reporting, image recognition, file archival, e-signatures, and other scenarios involving direct manipulation of file content.</span></span> <span data-ttu-id="dbb6a-119">Os arquivos compartilhados no Microsoft Teams normalmente aparecem como cartões e permitem uma visualização rica no aplicativo.</span><span class="sxs-lookup"><span data-stu-id="dbb6a-119">Files shared in Teams typically appear as cards, and allow rich in-app viewing.</span></span>  <span data-ttu-id="dbb6a-120">A API é fornecida como parte da **plataforma de bot do Microsoft Teams**.</span><span class="sxs-lookup"><span data-stu-id="dbb6a-120">The API is provided as part of the **Microsoft Teams Bot Platform**.</span></span>

> [!NOTE]
> <span data-ttu-id="dbb6a-121">Este método funciona apenas no `personal` contexto.</span><span class="sxs-lookup"><span data-stu-id="dbb6a-121">This method works only in the `personal` context.</span></span> <span data-ttu-id="dbb6a-122">Ele não funciona no contexto `channel` ou. `groupchat`</span><span class="sxs-lookup"><span data-stu-id="dbb6a-122">It does not work in the `channel` or `groupchat` context.</span></span>

### <a name="configure-your-bot-to-support-files"></a><span data-ttu-id="dbb6a-123">Configurar seu bot para dar suporte a arquivos</span><span class="sxs-lookup"><span data-stu-id="dbb6a-123">Configure your bot to support files</span></span>

<span data-ttu-id="dbb6a-124">Para enviar e receber arquivos no bot, você deve definir a `supportsFiles` Propriedade no manifesto como. `true`</span><span class="sxs-lookup"><span data-stu-id="dbb6a-124">To send and receive files in your bot, you must set the `supportsFiles` property in the manifest to `true`.</span></span> <span data-ttu-id="dbb6a-125">Essa propriedade é descrita na seção [bots](https://docs.microsoft.com/microsoftteams/platform/resources/schema/manifest-schema#bots
) da referência do manifesto.</span><span class="sxs-lookup"><span data-stu-id="dbb6a-125">This property is described in the [bots](https://docs.microsoft.com/microsoftteams/platform/resources/schema/manifest-schema#bots
) section of the Manifest reference.</span></span>

<span data-ttu-id="dbb6a-126">A configuração tem a seguinte aparência `"supportsFiles": true`:.</span><span class="sxs-lookup"><span data-stu-id="dbb6a-126">The setting looks like this: `"supportsFiles": true`.</span></span>

## <a name="invoke-activity-when-the-user-accepts-the-file-upload"></a><span data-ttu-id="dbb6a-127">Invocar atividade quando o usuário aceitar o carregamento de arquivo</span><span class="sxs-lookup"><span data-stu-id="dbb6a-127">Invoke activity when the user accepts the file upload</span></span>

<span data-ttu-id="dbb6a-128">O arquivo é carregado no armazenamento do **onedrive** do usuário depois que o consentimento para upload é emitido.</span><span class="sxs-lookup"><span data-stu-id="dbb6a-128">The file is uploaded to the user's **OneDrive** storage after the consent to upload is issued.</span></span> <span data-ttu-id="dbb6a-129">O bot receberá uma atividade de mensagem que contém metadados do arquivo, como o nome e a URL do conteúdo.</span><span class="sxs-lookup"><span data-stu-id="dbb6a-129">The bot will receive a message activity which contains file metadata, such as its name and the content URL.</span></span> <span data-ttu-id="dbb6a-130">Siga estas etapas:</span><span class="sxs-lookup"><span data-stu-id="dbb6a-130">Follow these steps:</span></span>

1. <span data-ttu-id="dbb6a-131">Envie uma mensagem para o usuário solicitando permissão para gravar o arquivo.</span><span class="sxs-lookup"><span data-stu-id="dbb6a-131">Send a message to the user requesting permission to write the file.</span></span> <span data-ttu-id="dbb6a-132">Essa mensagem deve conter um `FileConsentCard` anexo com o nome do arquivo a ser carregado.</span><span class="sxs-lookup"><span data-stu-id="dbb6a-132">This message must contain a `FileConsentCard` attachment with the name of the file to be uploaded.</span></span>

    ![cartão de permissão de upload de arquivos bot](../../../assets/images/bots/bot-file-upload-permission-card.png)

2. <span data-ttu-id="dbb6a-134">Se o usuário aceitar o carregamento de arquivo, o bot receberá uma atividade de *invocação* com uma URL de local.</span><span class="sxs-lookup"><span data-stu-id="dbb6a-134">If the user accepts the file upload, your bot will receive an *Invoke* activity with a location URL.</span></span>
3. <span data-ttu-id="dbb6a-135">Para transferir o arquivo, seu bot executa um `HTTP POST` diretamente na URL de local fornecida.</span><span class="sxs-lookup"><span data-stu-id="dbb6a-135">To transfer the file, your bot performs an `HTTP POST` directly into the provided location URL.</span></span>
4. <span data-ttu-id="dbb6a-136">Opcionalmente, você pode remover o cartão de consentimento original se não quiser permitir que o usuário aceite outros carregamentos do mesmo arquivo.</span><span class="sxs-lookup"><span data-stu-id="dbb6a-136">Optionally, you can remove the original consent card if you do not want to allow the user to accept further uploads of the same file.</span></span>
 
<span data-ttu-id="dbb6a-137">O exemplo a seguir mostra uma versão do Abridged da atividade Invoke que seu bot receberá:</span><span class="sxs-lookup"><span data-stu-id="dbb6a-137">The following example shows an abridged version of the invoke activity that your bot will receive:</span></span>

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

<span data-ttu-id="dbb6a-138">A tabela a seguir descreve as propriedades de conteúdo do anexo:</span><span class="sxs-lookup"><span data-stu-id="dbb6a-138">The following table describes the content properties of the attachment:</span></span>

| <span data-ttu-id="dbb6a-139">Propriedade</span><span class="sxs-lookup"><span data-stu-id="dbb6a-139">Property</span></span> | <span data-ttu-id="dbb6a-140">Finalidade</span><span class="sxs-lookup"><span data-stu-id="dbb6a-140">Purpose</span></span> |
| --- | --- |
| `uploadUrl` | <span data-ttu-id="dbb6a-141">URL do OneDrive para carregar o conteúdo do arquivo.</span><span class="sxs-lookup"><span data-stu-id="dbb6a-141">OneDrive URL for uploading the content of the file.</span></span> |
| `uniqueId` | <span data-ttu-id="dbb6a-142">ID de arquivo exclusivo.</span><span class="sxs-lookup"><span data-stu-id="dbb6a-142">Unique file ID.</span></span> <span data-ttu-id="dbb6a-143">Esta será a ID de item da unidade do OneDrive.</span><span class="sxs-lookup"><span data-stu-id="dbb6a-143">This will be the OneDrive drive item ID.</span></span> |
| `fileType` | <span data-ttu-id="dbb6a-144">Tipo de extensão de arquivo, como PDF ou \* png \* \*.</span><span class="sxs-lookup"><span data-stu-id="dbb6a-144">File extension type, such as pdf or \*png\*\*.</span></span> |

<span data-ttu-id="dbb6a-145">Como prática recomendada, você deve confirmar o carregamento do arquivo enviando de volta uma mensagem para o usuário.</span><span class="sxs-lookup"><span data-stu-id="dbb6a-145">As a best practice, you should acknowledge the file upload by sending back a message to the user.</span></span>

<span data-ttu-id="dbb6a-146">Se o usuário recusar o arquivo, o bot receberá o seguinte evento, com o mesmo nome de atividade geral:</span><span class="sxs-lookup"><span data-stu-id="dbb6a-146">If the user declines the file, your bot will receive the following event, with the same overall activity name:</span></span>

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

### <a name="notifying-the-user-about-an-uploaded-file"></a><span data-ttu-id="dbb6a-147">Notificar o usuário sobre um arquivo carregado</span><span class="sxs-lookup"><span data-stu-id="dbb6a-147">Notifying the user about an uploaded file</span></span>

<span data-ttu-id="dbb6a-148">Após carregar um arquivo no OneDrive do usuário, você deverá enviar uma mensagem de confirmação para o usuário.</span><span class="sxs-lookup"><span data-stu-id="dbb6a-148">After uploading a file to the user's OneDrive, you should send a confirmation message to the user.</span></span> <span data-ttu-id="dbb6a-149">Esta mensagem deve conter um `FileCard` anexo no qual o usuário pode clicar, para visualizá-lo, abri-lo no onedrive ou baixar localmente.</span><span class="sxs-lookup"><span data-stu-id="dbb6a-149">This message should contain  a `FileCard` attachment that the user can click on, either to preview it, open it in OneDrive, or download locally.</span></span> <span data-ttu-id="dbb6a-150">Apresentamos um exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="dbb6a-150">The following is an example.</span></span> 

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

<span data-ttu-id="dbb6a-151">A tabela a seguir descreve as propriedades de conteúdo do anexo:</span><span class="sxs-lookup"><span data-stu-id="dbb6a-151">The following table describes the content properties of the attachment:</span></span>

| <span data-ttu-id="dbb6a-152">Propriedade</span><span class="sxs-lookup"><span data-stu-id="dbb6a-152">Property</span></span> | <span data-ttu-id="dbb6a-153">Finalidade</span><span class="sxs-lookup"><span data-stu-id="dbb6a-153">Purpose</span></span> |
| --- | --- |
| `uniqueId` | <span data-ttu-id="dbb6a-154">ID de item da unidade do OneDrive/SharePoint.</span><span class="sxs-lookup"><span data-stu-id="dbb6a-154">OneDrive/SharePoint drive item ID.</span></span> |
| `fileType` | <span data-ttu-id="dbb6a-155">Tipo de arquivo, como PDF ou docx.</span><span class="sxs-lookup"><span data-stu-id="dbb6a-155">File type, such as pdf or docx.</span></span> |

## <a name="example-using-the-bot-framework-sdk"></a><span data-ttu-id="dbb6a-156">Exemplo usando o SDK da estrutura de bot</span><span class="sxs-lookup"><span data-stu-id="dbb6a-156">Example using the Bot Framework SDK</span></span>

<span data-ttu-id="dbb6a-157">O exemplo a seguir mostra como você pode manipular carregamentos de arquivo e enviar solicitações de consentimento de arquivo para o usuário na caixa de diálogo do bot.</span><span class="sxs-lookup"><span data-stu-id="dbb6a-157">The following example shows how you can handle file uploads and send file consent requests to the user in the bot's dialog.</span></span> <span data-ttu-id="dbb6a-158">Os trechos de código mostrados a seguir, pertencem a um exemplo de executável completo que você pode baixar neste local: [FileUpload](https://github.com/microsoft/botbuilder-dotnet/tree/master/tests/Teams/FileUpload).</span><span class="sxs-lookup"><span data-stu-id="dbb6a-158">The code snippets shown next, belong to a complete runnable example you can download at this location: [FileUpload](https://github.com/microsoft/botbuilder-dotnet/tree/master/tests/Teams/FileUpload).</span></span>

# <a name="cnettabdotnet"></a>[<span data-ttu-id="dbb6a-159">C#/.NET</span><span class="sxs-lookup"><span data-stu-id="dbb6a-159">C#/.NET</span></span>](#tab/dotnet)

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

# <a name="typescriptnodejstabtypescript"></a>[<span data-ttu-id="dbb6a-160">TypeScript/node. js</span><span class="sxs-lookup"><span data-stu-id="dbb6a-160">TypeScript/Node.js</span></span>](#tab/typescript)

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

# <a name="pythontabpython"></a>[<span data-ttu-id="dbb6a-161">Python</span><span class="sxs-lookup"><span data-stu-id="dbb6a-161">Python</span></span>](#tab/python)

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
