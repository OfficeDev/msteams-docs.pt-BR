---
title: Enviar e receber arquivos por meio do bot
description: Descreve como enviar e receber arquivos por meio do bot
keywords: envio de arquivos de bots do Teams
ms.date: 05/20/2019
ms.topic: how-to
ms.openlocfilehash: 07967ba4ce6d7e15e64c6f925fa588585f5a2c1d
ms.sourcegitcommit: f74b74d5bed1df193e59f46121ada443fb57277b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2021
ms.locfileid: "50093270"
---
# <a name="send-and-receive-files-through-the-bot"></a><span data-ttu-id="28060-104">Enviar e receber arquivos por meio do bot</span><span class="sxs-lookup"><span data-stu-id="28060-104">Send and receive files through the bot</span></span>

> [!IMPORTANT]
> <span data-ttu-id="28060-105">Os artigos deste documento são baseados no SDK da Estrutura de Bot v4.</span><span class="sxs-lookup"><span data-stu-id="28060-105">The articles in this document are based on the v4 Bot Framework SDK.</span></span>

<span data-ttu-id="28060-106">Há duas maneiras de enviar e receber arquivos de um bot:</span><span class="sxs-lookup"><span data-stu-id="28060-106">There are two ways to send files to and receive files from a bot:</span></span>

* <span data-ttu-id="28060-107">**Usando as APIs do Microsoft Graph:** Esse método funciona para bots em todos os escopos do Microsoft Teams:</span><span class="sxs-lookup"><span data-stu-id="28060-107">**Using the Microsoft Graph APIs:** This method works for bots in all Microsoft Teams scopes:</span></span>
  * `personal`
  * `channel`
  * `groupchat`

* <span data-ttu-id="28060-108">**Usando as APIs de bot do Teams:** Esses arquivos só são suportados em `personal` contexto.</span><span class="sxs-lookup"><span data-stu-id="28060-108">**Using the Teams bot APIs:** These only support files in `personal` context.</span></span>

## <a name="using-the-graph-apis"></a><span data-ttu-id="28060-109">Usando as APIs do Graph</span><span class="sxs-lookup"><span data-stu-id="28060-109">Using the Graph APIs</span></span>

<span data-ttu-id="28060-110">Postar mensagens com anexos de cartão que se referem a arquivos existentes do SharePoint, usando as APIs do Graph para [OneDrive e SharePoint.](/onedrive/developer/rest-api/)</span><span class="sxs-lookup"><span data-stu-id="28060-110">Post messages with card attachments that refer to existing SharePoint files, using the Graph APIs for [OneDrive and SharePoint](/onedrive/developer/rest-api/).</span></span> <span data-ttu-id="28060-111">Para usar as APIs do Graph, obtenha acesso a um dos seguintes por meio do fluxo de autorização padrão do OAuth 2.0:</span><span class="sxs-lookup"><span data-stu-id="28060-111">To use the Graph APIs, obtain access to either of the following through the standard OAuth 2.0 authorization flow:</span></span>
* <span data-ttu-id="28060-112">Pasta e arquivos do OneDrive de `personal` `groupchat` um usuário.</span><span class="sxs-lookup"><span data-stu-id="28060-112">A user's OneDrive folder for `personal` and `groupchat` files.</span></span>
* <span data-ttu-id="28060-113">Os arquivos no canal de uma equipe para `channel` arquivos.</span><span class="sxs-lookup"><span data-stu-id="28060-113">The files in a team's channel for `channel` files.</span></span>

<span data-ttu-id="28060-114">As APIs do Graph funcionam em todos os escopos do Teams.</span><span class="sxs-lookup"><span data-stu-id="28060-114">Graph APIs work in all Teams scopes.</span></span>

## <a name="using-the-teams-bot-apis"></a><span data-ttu-id="28060-115">Usando as APIs de bot do Teams</span><span class="sxs-lookup"><span data-stu-id="28060-115">Using the Teams bot APIs</span></span>

> [!NOTE]
> <span data-ttu-id="28060-116">As APIs de bot do Teams funcionam somente no `personal` contexto.</span><span class="sxs-lookup"><span data-stu-id="28060-116">Teams bot APIs work only in the `personal` context.</span></span> <span data-ttu-id="28060-117">Eles não funcionam no `channel` contexto `groupchat` ou no contexto.</span><span class="sxs-lookup"><span data-stu-id="28060-117">They do not work in the `channel` or `groupchat` context.</span></span>

<span data-ttu-id="28060-118">Usando as APIs do Teams, o bot pode enviar e receber arquivos diretamente com os usuários no contexto, também `personal` conhecido como chats pessoais.</span><span class="sxs-lookup"><span data-stu-id="28060-118">Using Teams APIs, the bot can directly send and receive files with users in the `personal` context, also known as personal chats.</span></span> <span data-ttu-id="28060-119">Implemente recursos, como relatórios de despesas, reconhecimento de imagem, arquivamento de arquivos e assinaturas eletrônicas envolvendo a edição do conteúdo do arquivo.</span><span class="sxs-lookup"><span data-stu-id="28060-119">Implement features, such as expense reporting, image recognition, file archival, and e-signatures involving the editing of file content.</span></span> <span data-ttu-id="28060-120">Os arquivos compartilhados no Teams normalmente aparecem como cartões e permitem a exibição rica no aplicativo.</span><span class="sxs-lookup"><span data-stu-id="28060-120">Files shared in Teams typically appear as cards and allow rich in-app viewing.</span></span>

<span data-ttu-id="28060-121">As seções a seguir descrevem como enviar conteúdo de arquivo como uma interação direta do usuário, como enviar uma mensagem.</span><span class="sxs-lookup"><span data-stu-id="28060-121">The following sections describe how to send file content as a direct user interaction, like sending a message.</span></span> <span data-ttu-id="28060-122">Essa API é fornecida como parte da plataforma de bot do Teams.</span><span class="sxs-lookup"><span data-stu-id="28060-122">This API is provided as part of the Teams bot platform.</span></span>

### <a name="configuring-the-bot-to-support-files"></a><span data-ttu-id="28060-123">Configurando o bot para dar suporte a arquivos</span><span class="sxs-lookup"><span data-stu-id="28060-123">Configuring the bot to support files</span></span>

<span data-ttu-id="28060-124">Para enviar e receber arquivos no bot, de definida `supportsFiles` a propriedade no manifesto como `true` .</span><span class="sxs-lookup"><span data-stu-id="28060-124">To send and receive files in the bot, set the `supportsFiles` property in the manifest to `true`.</span></span> <span data-ttu-id="28060-125">Essa propriedade é descrita na seção [bots](~/resources/schema/manifest-schema.md#bots) da referência do manifesto.</span><span class="sxs-lookup"><span data-stu-id="28060-125">This property is described in the [bots](~/resources/schema/manifest-schema.md#bots) section of the Manifest reference.</span></span>

<span data-ttu-id="28060-126">A definição tem esta aparência, `"supportsFiles": true` .</span><span class="sxs-lookup"><span data-stu-id="28060-126">The definition looks like this, `"supportsFiles": true`.</span></span> <span data-ttu-id="28060-127">Se o bot não `supportsFiles` habilitar, os recursos listados nesta seção não funcionarão.</span><span class="sxs-lookup"><span data-stu-id="28060-127">If the bot does not enable `supportsFiles`, the features listed in this section do not work.</span></span>

### <a name="receiving-files-in-personal-chat"></a><span data-ttu-id="28060-128">Recebendo arquivos em bate-papo pessoal</span><span class="sxs-lookup"><span data-stu-id="28060-128">Receiving files in personal chat</span></span>

<span data-ttu-id="28060-129">Quando um usuário envia um arquivo para o bot, o arquivo é carregado pela primeira vez no armazenamento do OneDrive for Business do usuário.</span><span class="sxs-lookup"><span data-stu-id="28060-129">When a user sends a file to the bot, the file is first uploaded to the user's OneDrive for Business storage.</span></span> <span data-ttu-id="28060-130">Em seguida, o bot recebe uma atividade de mensagem notificando o usuário sobre o carregamento do usuário.</span><span class="sxs-lookup"><span data-stu-id="28060-130">The bot then receives a message activity notifying the user about the user upload.</span></span> <span data-ttu-id="28060-131">A atividade contém metadados de arquivo, como seu nome e a URL de conteúdo.</span><span class="sxs-lookup"><span data-stu-id="28060-131">The activity contains file metadata, such as its name and the content URL.</span></span> <span data-ttu-id="28060-132">O usuário pode ler diretamente dessa URL para buscar seu conteúdo binário.</span><span class="sxs-lookup"><span data-stu-id="28060-132">The user can directly read from this URL to fetch its binary content.</span></span>

#### <a name="message-activity-with-file-attachment-example"></a><span data-ttu-id="28060-133">Exemplo de atividade de mensagem com anexo de arquivo</span><span class="sxs-lookup"><span data-stu-id="28060-133">Message activity with file attachment example</span></span>

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

<span data-ttu-id="28060-134">A tabela a seguir descreve as propriedades de conteúdo do anexo:</span><span class="sxs-lookup"><span data-stu-id="28060-134">The following table describes the content properties of the attachment:</span></span>

| <span data-ttu-id="28060-135">Propriedade</span><span class="sxs-lookup"><span data-stu-id="28060-135">Property</span></span> | <span data-ttu-id="28060-136">Finalidade</span><span class="sxs-lookup"><span data-stu-id="28060-136">Purpose</span></span> |
| --- | --- |
| `downloadUrl` | <span data-ttu-id="28060-137">URL do OneDrive para buscar o conteúdo do arquivo.</span><span class="sxs-lookup"><span data-stu-id="28060-137">OneDrive URL for fetching the content of the file.</span></span> <span data-ttu-id="28060-138">O usuário pode emitir uma `HTTP GET` diretamente dessa URL.</span><span class="sxs-lookup"><span data-stu-id="28060-138">The user can issue an `HTTP GET` directly from this URL.</span></span> |
| `uniqueId` | <span data-ttu-id="28060-139">ID exclusiva do arquivo.</span><span class="sxs-lookup"><span data-stu-id="28060-139">Unique file ID.</span></span> <span data-ttu-id="28060-140">Essa é a ID do item de unidade do OneDrive, caso o usuário envie um arquivo para o bot.</span><span class="sxs-lookup"><span data-stu-id="28060-140">This is the OneDrive drive item ID, in case the user sends a file to the bot.</span></span> |
| `fileType` | <span data-ttu-id="28060-141">Tipo de arquivo, como .pdf ou .docx.</span><span class="sxs-lookup"><span data-stu-id="28060-141">Type of file, such as .pdf or .docx.</span></span> |

<span data-ttu-id="28060-142">Como prática melhor, confirme o carregamento do arquivo enviando uma mensagem de volta para o usuário.</span><span class="sxs-lookup"><span data-stu-id="28060-142">As a best practice, acknowledge the file upload by sending a message back to the user.</span></span>

### <a name="uploading-files-to-personal-chat"></a><span data-ttu-id="28060-143">Carregando arquivos para chat pessoal</span><span class="sxs-lookup"><span data-stu-id="28060-143">Uploading files to personal chat</span></span>

<span data-ttu-id="28060-144">As etapas a seguir são necessárias para carregar um arquivo para um usuário:</span><span class="sxs-lookup"><span data-stu-id="28060-144">The following steps are required to upload a file to a user:</span></span>

1. <span data-ttu-id="28060-145">Envie uma mensagem para o usuário solicitando permissão para gravar o arquivo.</span><span class="sxs-lookup"><span data-stu-id="28060-145">Send a message to the user requesting permission to write the file.</span></span> <span data-ttu-id="28060-146">Essa mensagem deve conter `FileConsentCard` um anexo com o nome do arquivo a ser carregado.</span><span class="sxs-lookup"><span data-stu-id="28060-146">This message must contain a `FileConsentCard` attachment with the name of the file to be uploaded.</span></span>
2. <span data-ttu-id="28060-147">Se o usuário aceitar o download do arquivo, o bot receberá uma atividade de invocação com uma URL de local.</span><span class="sxs-lookup"><span data-stu-id="28060-147">If the user accepts the file download, the bot receives an invoke activity with a location URL.</span></span>
3. <span data-ttu-id="28060-148">Para transferir o arquivo, o bot executa uma `HTTP POST` ação diretamente para a URL de local fornecida.</span><span class="sxs-lookup"><span data-stu-id="28060-148">To transfer the file, the bot performs an `HTTP POST` directly into the provided location URL.</span></span>
4. <span data-ttu-id="28060-149">Opcionalmente, remova o cartão de consentimento original se não quiser que o usuário aceite uploads posteriores do mesmo arquivo.</span><span class="sxs-lookup"><span data-stu-id="28060-149">Optionally, remove the original consent card if you do not want the user to accept further uploads of the same file.</span></span>

#### <a name="message-requesting-permission-to-upload"></a><span data-ttu-id="28060-150">Mensagem solicitando permissão para carregar</span><span class="sxs-lookup"><span data-stu-id="28060-150">Message requesting permission to upload</span></span>

<span data-ttu-id="28060-151">A seguinte mensagem da área de trabalho contém um objeto anexo simples solicitando permissão do usuário para carregar o arquivo:</span><span class="sxs-lookup"><span data-stu-id="28060-151">The following desktop message contains a simple attachment object requesting user permission to upload the file:</span></span>

![Cartão de consentimento solicitando permissão do usuário para carregar o arquivo](../../assets/images/bots/bot-file-consent-card.png)

<span data-ttu-id="28060-153">A seguinte mensagem móvel contém um objeto anexo solicitando permissão do usuário para carregar o arquivo:</span><span class="sxs-lookup"><span data-stu-id="28060-153">The following mobile message contains an attachment object requesting user permission to upload the file:</span></span>

![Cartão de consentimento solicitando permissão do usuário para carregar o arquivo no celular](../../assets/images/bots/mobile-bot-file-consent-card.png)

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

<span data-ttu-id="28060-155">A tabela a seguir descreve as propriedades de conteúdo do anexo:</span><span class="sxs-lookup"><span data-stu-id="28060-155">The following table describes the content properties of the attachment:</span></span>

| <span data-ttu-id="28060-156">Propriedade</span><span class="sxs-lookup"><span data-stu-id="28060-156">Property</span></span> | <span data-ttu-id="28060-157">Finalidade</span><span class="sxs-lookup"><span data-stu-id="28060-157">Purpose</span></span> |
| --- | --- |
| `description` | <span data-ttu-id="28060-158">Descreve a finalidade do arquivo ou resume seu conteúdo.</span><span class="sxs-lookup"><span data-stu-id="28060-158">Describes the purpose of the file or summarizes its content.</span></span> |
| `sizeInBytes` | <span data-ttu-id="28060-159">Fornece ao usuário uma estimativa do tamanho do arquivo e da quantidade de espaço que ele ocupa no OneDrive.</span><span class="sxs-lookup"><span data-stu-id="28060-159">Provides the user an estimate of the file size and the amount of space it takes in OneDrive.</span></span> |
| `acceptContext` | <span data-ttu-id="28060-160">Contexto adicional que é transmitido silenciosamente para o bot quando o usuário aceita o arquivo.</span><span class="sxs-lookup"><span data-stu-id="28060-160">Additional context that is silently transmitted to the bot when the user accepts the file.</span></span> |
| `declineContext` | <span data-ttu-id="28060-161">Contexto adicional que é transmitido silenciosamente para o bot quando o usuário recusa o arquivo.</span><span class="sxs-lookup"><span data-stu-id="28060-161">Additional context that is silently transmitted to the bot when the user declines the file.</span></span> |

#### <a name="invoke-activity-when-the-user-accepts-the-file"></a><span data-ttu-id="28060-162">Invocar atividade quando o usuário aceita o arquivo</span><span class="sxs-lookup"><span data-stu-id="28060-162">Invoke activity when the user accepts the file</span></span>

<span data-ttu-id="28060-163">Uma atividade de invocação é enviada para o bot se e quando o usuário aceita o arquivo.</span><span class="sxs-lookup"><span data-stu-id="28060-163">An invoke activity is sent to the bot if and when the user accepts the file.</span></span> <span data-ttu-id="28060-164">Ele contém a URL de espaço reservado do OneDrive for Business que o bot pode emitir para `PUT` transferir o conteúdo do arquivo.</span><span class="sxs-lookup"><span data-stu-id="28060-164">It contains the OneDrive for Business placeholder URL that the bot can then issue a `PUT` to transfer the file contents.</span></span> <span data-ttu-id="28060-165">Para obter informações sobre como carregar para a URL do OneDrive, confira [carregar bytes na sessão de carregamento.](/onedrive/developer/rest-api/api/driveitem_createuploadsession#upload-bytes-to-the-upload-session)</span><span class="sxs-lookup"><span data-stu-id="28060-165">For information on uploading to the OneDrive URL, see [upload bytes to the upload session](/onedrive/developer/rest-api/api/driveitem_createuploadsession#upload-bytes-to-the-upload-session).</span></span>

<span data-ttu-id="28060-166">O exemplo a seguir mostra uma versão concisa da atividade de invocação que o bot recebe:</span><span class="sxs-lookup"><span data-stu-id="28060-166">The following example shows a concise version of the invoke activity that the bot receives:</span></span>

```json
{
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

<span data-ttu-id="28060-167">Da mesma forma, se o usuário recusar o arquivo, o bot receberá o seguinte evento com o mesmo nome de atividade geral:</span><span class="sxs-lookup"><span data-stu-id="28060-167">Similarly, if the user declines the file, the bot receives the following event with the same overall activity name:</span></span>

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

### <a name="notifying-the-user-about-an-uploaded-file"></a><span data-ttu-id="28060-168">Notificar o usuário sobre um arquivo carregado</span><span class="sxs-lookup"><span data-stu-id="28060-168">Notifying the user about an uploaded file</span></span>

<span data-ttu-id="28060-169">Depois de carregar um arquivo no OneDrive do usuário, envie uma mensagem de confirmação para o usuário.</span><span class="sxs-lookup"><span data-stu-id="28060-169">After uploading a file to the user's OneDrive, send a confirmation message to the user.</span></span> <span data-ttu-id="28060-170">A mensagem deve conter o seguinte anexo que o usuário pode selecionar, para visualizar ou `FileCard` abri-la no OneDrive, ou baixar localmente:</span><span class="sxs-lookup"><span data-stu-id="28060-170">The message must contain the following `FileCard` attachment that the user can select, either to preview or open it in OneDrive, or download locally:</span></span>

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

<span data-ttu-id="28060-171">A tabela a seguir descreve as propriedades de conteúdo do anexo:</span><span class="sxs-lookup"><span data-stu-id="28060-171">The following table describes the content properties of the attachment:</span></span>

| <span data-ttu-id="28060-172">Propriedade</span><span class="sxs-lookup"><span data-stu-id="28060-172">Property</span></span> | <span data-ttu-id="28060-173">Finalidade</span><span class="sxs-lookup"><span data-stu-id="28060-173">Purpose</span></span> |
| --- | --- |
| `uniqueId` | <span data-ttu-id="28060-174">ID do item de unidade do OneDrive ou do SharePoint.</span><span class="sxs-lookup"><span data-stu-id="28060-174">OneDrive or SharePoint drive item ID.</span></span> |
| `fileType` | <span data-ttu-id="28060-175">Tipo de arquivo, como .pdf ou .docx.</span><span class="sxs-lookup"><span data-stu-id="28060-175">Type of file, such as .pdf or .docx.</span></span> |

### <a name="fetching-inline-images-from-message"></a><span data-ttu-id="28060-176">Buscar imagens em linha da mensagem</span><span class="sxs-lookup"><span data-stu-id="28060-176">Fetching inline images from message</span></span>

<span data-ttu-id="28060-177">Buscar imagens em linha que fazem parte da mensagem usando o token de acesso do Bot.</span><span class="sxs-lookup"><span data-stu-id="28060-177">Fetch inline images that are part of the message using the Bot's access token.</span></span>

![Imagem em linha](../../assets/images/bots/inline-image.png)

```csharp
private async Task ProcessInlineImage(ITurnContext<IMessageActivity> turnContext, CancellationToken cancellationToken)
{
    var attachment = turnContext.Activity.Attachments[0];
    var client = _clientFactory.CreateClient();
    // Get Bot's access token to fetch inline image. 
    var token = await new MicrosoftAppCredentials(microsoftAppId, microsoftAppPassword).GetTokenAsync();
    client.DefaultRequestHeaders.Authorization = new AuthenticationHeaderValue("Bearer", token);
    var responseMessage = await client.GetAsync(attachment.ContentUrl);
    // Save the inline image to Files directory.
    var filePath = Path.Combine("Files", "ImageFromUser.png");
    using (var fileStream = new FileStream(filePath, FileMode.Create, FileAccess.Write, FileShare.None))
    {
        await responseMessage.Content.CopyToAsync(fileStream);
    }
    // Create reply with image.
    var reply = MessageFactory.Text($"Attachment of {attachment.ContentType} type and size of {responseMessage.Content.Headers.ContentLength} bytes received.");
    reply.Attachments = new List<Attachment>() { 
        GetInlineAttachment() 
    };
    await turnContext.SendActivityAsync(reply, cancellationToken);
}
private static Attachment GetInlineAttachment()
{
    var imagePath = Path.Combine("Files", "ImageFromUser.png");
    var imageData = Convert.ToBase64String(File.ReadAllBytes(imagePath));
    return new Attachment
    {
        Name = @"ImageFromUser.png",
        ContentType = "image/png",
        ContentUrl = $"data:image/png;base64,{imageData}",
    };
}
```

### <a name="basic-example-in-c"></a><span data-ttu-id="28060-179">Exemplo básico em C #</span><span class="sxs-lookup"><span data-stu-id="28060-179">Basic example in C#</span></span>

<span data-ttu-id="28060-180">O exemplo a seguir mostra como manipular carregamentos de arquivos e enviar solicitações de consentimento de arquivo na caixa de diálogo do bot:</span><span class="sxs-lookup"><span data-stu-id="28060-180">The following sample shows how to handle file uploads and send file consent requests in the bot's dialog:</span></span>

```csharp

protected override async Task OnMessageActivityAsync(ITurnContext<IMessageActivity> turnContext, CancellationToken cancellationToken)
{
    if (turnContext.Activity.Attachments?[0].ContentType.Contains("image/*") == true)
    {
        // Inline image.
        await ProcessInlineImage(turnContext, cancellationToken);
    }
    else
    {
        string filename = "teams-logo.png";
        string filePath = Path.Combine("Files", filename);
        long fileSize = new FileInfo(filePath).Length;
        await SendFileCardAsync(turnContext, filename, fileSize, cancellationToken);
    }
}
private async Task ProcessInlineImage(ITurnContext<IMessageActivity> turnContext, CancellationToken cancellationToken)
{
    var attachment = turnContext.Activity.Attachments[0];
    var client = _clientFactory.CreateClient();
    // Get Bot's access token to fetch inline image. 
    var token = await new MicrosoftAppCredentials(microsoftAppId, microsoftAppPassword).GetTokenAsync();
    client.DefaultRequestHeaders.Authorization = new AuthenticationHeaderValue("Bearer", token);
    var responseMessage = await client.GetAsync(attachment.ContentUrl);
    // Save the inline image to Files directory.
    var filePath = Path.Combine("Files", "ImageFromUser.png");
    using (var fileStream = new FileStream(filePath, FileMode.Create, FileAccess.Write, FileShare.None))
    {
        await responseMessage.Content.CopyToAsync(fileStream);
    }
    // Create reply with image.
    var reply = MessageFactory.Text($"Attachment of {attachment.ContentType} type and size of {responseMessage.Content.Headers.ContentLength} bytes received.");
    reply.Attachments = new List<Attachment>() { GetInlineAttachment() };
    await turnContext.SendActivityAsync(reply, cancellationToken);
}
private static Attachment GetInlineAttachment()
{
    var imagePath = Path.Combine("Files", "ImageFromUser.png");
    var imageData = Convert.ToBase64String(File.ReadAllBytes(imagePath));
    return new Attachment
    {
        Name = @"ImageFromUser.png",
        ContentType = "image/png",
        ContentUrl = $"data:image/png;base64,{imageData}",
    };
}
private async Task SendFileCardAsync(ITurnContext turnContext, string filename, long filesize, CancellationToken cancellationToken)
{
    var consentContext = new Dictionary<string, string>
    {
        { 
            "filename", filename 
        },
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
```

### <a name="code-sample"></a><span data-ttu-id="28060-181">Exemplo de código</span><span class="sxs-lookup"><span data-stu-id="28060-181">Code sample</span></span>

|<span data-ttu-id="28060-182">**Nome do exemplo**</span><span class="sxs-lookup"><span data-stu-id="28060-182">**Sample name**</span></span> | <span data-ttu-id="28060-183">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="28060-183">**Description**</span></span> | <span data-ttu-id="28060-184">**. NETCore**</span><span class="sxs-lookup"><span data-stu-id="28060-184">**.NETCore**</span></span> | <span data-ttu-id="28060-185">**Javascript**</span><span class="sxs-lookup"><span data-stu-id="28060-185">**Javascript**</span></span> | <span data-ttu-id="28060-186">**Python**</span><span class="sxs-lookup"><span data-stu-id="28060-186">**Python**</span></span>|
|----------------|-----------------|--------------|----------------|-----------|
| <span data-ttu-id="28060-187">Upload de arquivos</span><span class="sxs-lookup"><span data-stu-id="28060-187">File upload</span></span> | <span data-ttu-id="28060-188">Demonstra como obter o consentimento do arquivo e carregar arquivos no Teams de um bot.</span><span class="sxs-lookup"><span data-stu-id="28060-188">Demonstrates how to obtain file consent and upload files to Teams from a bot.</span></span> <span data-ttu-id="28060-189">Além disso, como receber um arquivo enviado para um bot.</span><span class="sxs-lookup"><span data-stu-id="28060-189">Also, how to receive a file sent to a bot.</span></span> | [<span data-ttu-id="28060-190">View</span><span class="sxs-lookup"><span data-stu-id="28060-190">View</span></span>](https://github.com/microsoft/BotBuilder-Samples/blob/main/samples/csharp_dotnetcore/56.teams-file-upload) | [<span data-ttu-id="28060-191">View</span><span class="sxs-lookup"><span data-stu-id="28060-191">View</span></span>](https://github.com/microsoft/BotBuilder-Samples/blob/main/samples/javascript_nodejs/56.teams-file-upload) | [<span data-ttu-id="28060-192">View</span><span class="sxs-lookup"><span data-stu-id="28060-192">View</span></span>](https://github.com/microsoft/BotBuilder-Samples/blob/main/samples/python/56.teams-file-upload) |
