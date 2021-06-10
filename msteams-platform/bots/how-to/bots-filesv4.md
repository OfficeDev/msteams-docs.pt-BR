---
title: Enviar e receber arquivos por meio do bot
description: Descreve como enviar e receber arquivos por meio do bot
keywords: arquivos de bots do teams enviam recebimento
ms.date: 05/20/2019
localization_priority: Normal
ms.topic: how-to
ms.openlocfilehash: 7d5ea3434b10d60e20574ca6d1935943c687f4d7
ms.sourcegitcommit: 825abed2f8784d2bab7407ba7a4455ae17bbd28f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2021
ms.locfileid: "52020937"
---
# <a name="send-and-receive-files-through-the-bot"></a><span data-ttu-id="d1e3c-104">Enviar e receber arquivos por meio do bot</span><span class="sxs-lookup"><span data-stu-id="d1e3c-104">Send and receive files through the bot</span></span>

> [!IMPORTANT]
> <span data-ttu-id="d1e3c-105">Os artigos neste documento são baseados no SDK da Estrutura de Bots v4.</span><span class="sxs-lookup"><span data-stu-id="d1e3c-105">The articles in this document are based on the v4 Bot Framework SDK.</span></span>

<span data-ttu-id="d1e3c-106">Há duas maneiras de enviar arquivos para e receber arquivos de um bot:</span><span class="sxs-lookup"><span data-stu-id="d1e3c-106">There are two ways to send files to and receive files from a bot:</span></span>

* <span data-ttu-id="d1e3c-107">[**Use as APIs do Microsoft Graph:**](#use-the-graph-apis) Este método funciona para bots em todos os Microsoft Teams escopos:</span><span class="sxs-lookup"><span data-stu-id="d1e3c-107">[**Use the Microsoft Graph APIs:**](#use-the-graph-apis) This method works for bots in all Microsoft Teams scopes:</span></span>
  * `personal`
  * `channel`
  * `groupchat`

* <span data-ttu-id="d1e3c-108">[**Use as APIs Teams bot:**](#use-the-teams-bot-apis) Esses somente suportam arquivos no `personal` contexto.</span><span class="sxs-lookup"><span data-stu-id="d1e3c-108">[**Use the Teams bot APIs:**](#use-the-teams-bot-apis) These only support files in `personal` context.</span></span>

## <a name="use-the-graph-apis"></a><span data-ttu-id="d1e3c-109">Usar as APIs Graph de usuário</span><span class="sxs-lookup"><span data-stu-id="d1e3c-109">Use the Graph APIs</span></span>

<span data-ttu-id="d1e3c-110">Poste mensagens com anexos de cartão que se referem a arquivos SharePoint existentes, usando as APIs Graph de OneDrive [e SharePoint](/onedrive/developer/rest-api/).</span><span class="sxs-lookup"><span data-stu-id="d1e3c-110">Post messages with card attachments that refer to existing SharePoint files, using the Graph APIs for [OneDrive and SharePoint](/onedrive/developer/rest-api/).</span></span> <span data-ttu-id="d1e3c-111">Para usar as APIs Graph, obtenha acesso a uma das seguintes informações por meio do fluxo de autorização OAuth 2.0 padrão:</span><span class="sxs-lookup"><span data-stu-id="d1e3c-111">To use the Graph APIs, obtain access to either of the following through the standard OAuth 2.0 authorization flow:</span></span>

* <span data-ttu-id="d1e3c-112">A pasta de OneDrive de um `personal` usuário e `groupchat` arquivos.</span><span class="sxs-lookup"><span data-stu-id="d1e3c-112">A user's OneDrive folder for `personal` and `groupchat` files.</span></span>
* <span data-ttu-id="d1e3c-113">Os arquivos no canal de uma equipe para `channel` arquivos.</span><span class="sxs-lookup"><span data-stu-id="d1e3c-113">The files in a team's channel for `channel` files.</span></span>

<span data-ttu-id="d1e3c-114">Graph As APIs funcionam em todos os Teams escopos.</span><span class="sxs-lookup"><span data-stu-id="d1e3c-114">Graph APIs work in all Teams scopes.</span></span> <span data-ttu-id="d1e3c-115">Para obter mais informações, [consulte send chat message file attachments](/graph/api/chatmessage-post?view=graph-rest-beta&tabs=http#example-4-file-attachments&preserve-view=true).</span><span class="sxs-lookup"><span data-stu-id="d1e3c-115">For more information, see [send chat message file attachments](/graph/api/chatmessage-post?view=graph-rest-beta&tabs=http#example-4-file-attachments&preserve-view=true).</span></span>

<span data-ttu-id="d1e3c-116">Como alternativa, você pode enviar arquivos para e receber arquivos de um bot usando as APIs Teams bot.</span><span class="sxs-lookup"><span data-stu-id="d1e3c-116">Alternately, you can send files to and receive files from a bot using the Teams bot APIs.</span></span>

## <a name="use-the-teams-bot-apis"></a><span data-ttu-id="d1e3c-117">Usar as APIs Teams bot</span><span class="sxs-lookup"><span data-stu-id="d1e3c-117">Use the Teams bot APIs</span></span>

> [!NOTE]
> <span data-ttu-id="d1e3c-118">Teams APIs de bot funcionam somente no `personal` contexto.</span><span class="sxs-lookup"><span data-stu-id="d1e3c-118">Teams bot APIs work only in the `personal` context.</span></span> <span data-ttu-id="d1e3c-119">Eles não funcionam no `channel` contexto `groupchat` ou.</span><span class="sxs-lookup"><span data-stu-id="d1e3c-119">They do not work in the `channel` or `groupchat` context.</span></span>

<span data-ttu-id="d1e3c-120">Usando Teams APIs, o bot pode enviar e receber arquivos diretamente com usuários no contexto, também `personal` conhecidos como chats pessoais.</span><span class="sxs-lookup"><span data-stu-id="d1e3c-120">Using Teams APIs, the bot can directly send and receive files with users in the `personal` context, also known as personal chats.</span></span> <span data-ttu-id="d1e3c-121">Implemente recursos, como relatórios de despesas, reconhecimento de imagem, arquivamento de arquivos e assinaturas eletrônicas envolvendo a edição de conteúdo de arquivo.</span><span class="sxs-lookup"><span data-stu-id="d1e3c-121">Implement features, such as expense reporting, image recognition, file archival, and e-signatures involving the editing of file content.</span></span> <span data-ttu-id="d1e3c-122">Os arquivos compartilhados Teams normalmente aparecem como cartões e permitem a exibição rica no aplicativo.</span><span class="sxs-lookup"><span data-stu-id="d1e3c-122">Files shared in Teams typically appear as cards and allow rich in-app viewing.</span></span>

<span data-ttu-id="d1e3c-123">As próximas seções descrevem como enviar conteúdo de arquivo como interação direta do usuário, como o envio de uma mensagem.</span><span class="sxs-lookup"><span data-stu-id="d1e3c-123">The next sections describe how to send file content as direct user interaction, like sending a message.</span></span> <span data-ttu-id="d1e3c-124">Essa API é fornecida como parte da plataforma Teams bot.</span><span class="sxs-lookup"><span data-stu-id="d1e3c-124">This API is provided as part of the Teams bot platform.</span></span>

### <a name="configure-the-bot-to-support-files"></a><span data-ttu-id="d1e3c-125">Configurar o bot para dar suporte a arquivos</span><span class="sxs-lookup"><span data-stu-id="d1e3c-125">Configure the bot to support files</span></span>

<span data-ttu-id="d1e3c-126">Para enviar e receber arquivos no bot, de definir a `supportsFiles` propriedade no manifesto como `true` .</span><span class="sxs-lookup"><span data-stu-id="d1e3c-126">To send and receive files in the bot, set the `supportsFiles` property in the manifest to `true`.</span></span> <span data-ttu-id="d1e3c-127">Essa propriedade é descrita na seção [bots](~/resources/schema/manifest-schema.md#bots) da referência manifesto.</span><span class="sxs-lookup"><span data-stu-id="d1e3c-127">This property is described in the [bots](~/resources/schema/manifest-schema.md#bots) section of the Manifest reference.</span></span>

<span data-ttu-id="d1e3c-128">A definição tem esta aparência, `"supportsFiles": true` .</span><span class="sxs-lookup"><span data-stu-id="d1e3c-128">The definition looks like this, `"supportsFiles": true`.</span></span> <span data-ttu-id="d1e3c-129">Se o bot não `supportsFiles` habilitar , os recursos listados nesta seção não funcionarão.</span><span class="sxs-lookup"><span data-stu-id="d1e3c-129">If the bot does not enable `supportsFiles`, the features listed in this section do not work.</span></span>

### <a name="receive-files-in-personal-chat"></a><span data-ttu-id="d1e3c-130">Receber arquivos no chat pessoal</span><span class="sxs-lookup"><span data-stu-id="d1e3c-130">Receive files in personal chat</span></span>

<span data-ttu-id="d1e3c-131">Quando um usuário envia um arquivo para o bot, o arquivo é carregado pela primeira vez no OneDrive do usuário para armazenamento comercial.</span><span class="sxs-lookup"><span data-stu-id="d1e3c-131">When a user sends a file to the bot, the file is first uploaded to the user's OneDrive for business storage.</span></span> <span data-ttu-id="d1e3c-132">Em seguida, o bot recebe uma atividade de mensagem notificando o usuário sobre o carregamento do usuário.</span><span class="sxs-lookup"><span data-stu-id="d1e3c-132">The bot then receives a message activity notifying the user about the user upload.</span></span> <span data-ttu-id="d1e3c-133">A atividade contém metadados de arquivo, como seu nome e a URL de conteúdo.</span><span class="sxs-lookup"><span data-stu-id="d1e3c-133">The activity contains file metadata, such as its name and the content URL.</span></span> <span data-ttu-id="d1e3c-134">O usuário pode ler diretamente a partir dessa URL para buscar seu conteúdo binário.</span><span class="sxs-lookup"><span data-stu-id="d1e3c-134">The user can directly read from this URL to fetch its binary content.</span></span>

#### <a name="message-activity-with-file-attachment-example"></a><span data-ttu-id="d1e3c-135">Atividade de mensagem com exemplo de anexo de arquivo</span><span class="sxs-lookup"><span data-stu-id="d1e3c-135">Message activity with file attachment example</span></span>

<span data-ttu-id="d1e3c-136">O código a seguir mostra um exemplo de atividade de mensagem com anexo de arquivo:</span><span class="sxs-lookup"><span data-stu-id="d1e3c-136">The following code shows an example of message activity with file attachment:</span></span>

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

<span data-ttu-id="d1e3c-137">A tabela a seguir descreve as propriedades de conteúdo do anexo:</span><span class="sxs-lookup"><span data-stu-id="d1e3c-137">The following table describes the content properties of the attachment:</span></span>

| <span data-ttu-id="d1e3c-138">Propriedade</span><span class="sxs-lookup"><span data-stu-id="d1e3c-138">Property</span></span> | <span data-ttu-id="d1e3c-139">Finalidade</span><span class="sxs-lookup"><span data-stu-id="d1e3c-139">Purpose</span></span> |
| --- | --- |
| `downloadUrl` | <span data-ttu-id="d1e3c-140">OneDrive URL para buscar o conteúdo do arquivo.</span><span class="sxs-lookup"><span data-stu-id="d1e3c-140">OneDrive URL for fetching the content of the file.</span></span> <span data-ttu-id="d1e3c-141">O usuário pode emitir um `HTTP GET` diretamente a partir dessa URL.</span><span class="sxs-lookup"><span data-stu-id="d1e3c-141">The user can issue an `HTTP GET` directly from this URL.</span></span> |
| `uniqueId` | <span data-ttu-id="d1e3c-142">ID de arquivo exclusivo.</span><span class="sxs-lookup"><span data-stu-id="d1e3c-142">Unique file ID.</span></span> <span data-ttu-id="d1e3c-143">Essa é a OneDrive ID do item da unidade, caso o usuário envie um arquivo para o bot.</span><span class="sxs-lookup"><span data-stu-id="d1e3c-143">This is the OneDrive drive item ID, in case the user sends a file to the bot.</span></span> |
| `fileType` | <span data-ttu-id="d1e3c-144">Tipo de arquivo, como .pdf ou .docx.</span><span class="sxs-lookup"><span data-stu-id="d1e3c-144">Type of file, such as .pdf or .docx.</span></span> |

<span data-ttu-id="d1e3c-145">Como prática prática, confirme o carregamento de arquivo enviando uma mensagem de volta para o usuário.</span><span class="sxs-lookup"><span data-stu-id="d1e3c-145">As a best practice, acknowledge the file upload by sending a message back to the user.</span></span>

### <a name="upload-files-to-personal-chat"></a><span data-ttu-id="d1e3c-146">Upload arquivos para chat pessoal</span><span class="sxs-lookup"><span data-stu-id="d1e3c-146">Upload files to personal chat</span></span>

<span data-ttu-id="d1e3c-147">**Para carregar um arquivo em um usuário**</span><span class="sxs-lookup"><span data-stu-id="d1e3c-147">**To upload a file to a user**</span></span>

1. <span data-ttu-id="d1e3c-148">Envie uma mensagem para o usuário solicitando permissão para gravar o arquivo.</span><span class="sxs-lookup"><span data-stu-id="d1e3c-148">Send a message to the user requesting permission to write the file.</span></span> <span data-ttu-id="d1e3c-149">Esta mensagem deve conter `FileConsentCard` um anexo com o nome do arquivo a ser carregado.</span><span class="sxs-lookup"><span data-stu-id="d1e3c-149">This message must contain a `FileConsentCard` attachment with the name of the file to be uploaded.</span></span>
2. <span data-ttu-id="d1e3c-150">Se o usuário aceitar o download do arquivo, o bot receberá uma atividade de invocação com uma URL de local.</span><span class="sxs-lookup"><span data-stu-id="d1e3c-150">If the user accepts the file download, the bot receives an invoke activity with a location URL.</span></span>
3. <span data-ttu-id="d1e3c-151">Para transferir o arquivo, o bot executa um diretamente para a `HTTP POST` URL de local fornecida.</span><span class="sxs-lookup"><span data-stu-id="d1e3c-151">To transfer the file, the bot performs an `HTTP POST` directly into the provided location URL.</span></span>
4. <span data-ttu-id="d1e3c-152">Opcionalmente, remova o cartão de consentimento original se você não quiser que o usuário aceite mais carregamentos do mesmo arquivo.</span><span class="sxs-lookup"><span data-stu-id="d1e3c-152">Optionally, remove the original consent card if you do not want the user to accept further uploads of the same file.</span></span>

#### <a name="message-requesting-permission-to-upload"></a><span data-ttu-id="d1e3c-153">Mensagem solicitando permissão para carregar</span><span class="sxs-lookup"><span data-stu-id="d1e3c-153">Message requesting permission to upload</span></span>

<span data-ttu-id="d1e3c-154">A seguinte mensagem da área de trabalho contém um objeto de anexo simples solicitando permissão do usuário para carregar o arquivo:</span><span class="sxs-lookup"><span data-stu-id="d1e3c-154">The following desktop message contains a simple attachment object requesting user permission to upload the file:</span></span>

![Cartão de consentimento solicitando permissão do usuário para carregar arquivo](../../assets/images/bots/bot-file-consent-card.png)

<span data-ttu-id="d1e3c-156">A seguinte mensagem móvel contém um objeto de anexo solicitando permissão do usuário para carregar o arquivo:</span><span class="sxs-lookup"><span data-stu-id="d1e3c-156">The following mobile message contains an attachment object requesting user permission to upload the file:</span></span>

<img src="../../assets/images/bots/mobile-bot-file-consent-card.png" alt="Consent card requesting user permission to upload file on mobile" width="350"/>

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

<span data-ttu-id="d1e3c-157">A tabela a seguir descreve as propriedades de conteúdo do anexo:</span><span class="sxs-lookup"><span data-stu-id="d1e3c-157">The following table describes the content properties of the attachment:</span></span>

| <span data-ttu-id="d1e3c-158">Propriedade</span><span class="sxs-lookup"><span data-stu-id="d1e3c-158">Property</span></span> | <span data-ttu-id="d1e3c-159">Finalidade</span><span class="sxs-lookup"><span data-stu-id="d1e3c-159">Purpose</span></span> |
| --- | --- |
| `description` | <span data-ttu-id="d1e3c-160">Descreve a finalidade do arquivo ou resume seu conteúdo.</span><span class="sxs-lookup"><span data-stu-id="d1e3c-160">Describes the purpose of the file or summarizes its content.</span></span> |
| `sizeInBytes` | <span data-ttu-id="d1e3c-161">Fornece ao usuário uma estimativa do tamanho do arquivo e da quantidade de espaço necessário OneDrive.</span><span class="sxs-lookup"><span data-stu-id="d1e3c-161">Provides the user an estimate of the file size and the amount of space it takes in OneDrive.</span></span> |
| `acceptContext` | <span data-ttu-id="d1e3c-162">Contexto adicional que é transmitido silenciosamente para o bot quando o usuário aceita o arquivo.</span><span class="sxs-lookup"><span data-stu-id="d1e3c-162">Additional context that is silently transmitted to the bot when the user accepts the file.</span></span> |
| `declineContext` | <span data-ttu-id="d1e3c-163">Contexto adicional que é transmitido silenciosamente para o bot quando o usuário recusa o arquivo.</span><span class="sxs-lookup"><span data-stu-id="d1e3c-163">Additional context that is silently transmitted to the bot when the user declines the file.</span></span> |

#### <a name="invoke-activity-when-the-user-accepts-the-file"></a><span data-ttu-id="d1e3c-164">Invocar atividade quando o usuário aceitar o arquivo</span><span class="sxs-lookup"><span data-stu-id="d1e3c-164">Invoke activity when the user accepts the file</span></span>

<span data-ttu-id="d1e3c-165">Uma atividade de invocação é enviada ao bot se e quando o usuário aceitar o arquivo.</span><span class="sxs-lookup"><span data-stu-id="d1e3c-165">An invoke activity is sent to the bot if and when the user accepts the file.</span></span> <span data-ttu-id="d1e3c-166">Ele contém a URL OneDrive for Business espaço reservado que o bot pode emitir para `PUT` transferir o conteúdo do arquivo.</span><span class="sxs-lookup"><span data-stu-id="d1e3c-166">It contains the OneDrive for Business placeholder URL that the bot can then issue a `PUT` to transfer the file contents.</span></span> <span data-ttu-id="d1e3c-167">Para obter informações sobre como carregar na URL OneDrive, consulte [upload bytes para a sessão de carregamento](/onedrive/developer/rest-api/api/driveitem_createuploadsession#upload-bytes-to-the-upload-session).</span><span class="sxs-lookup"><span data-stu-id="d1e3c-167">For information on uploading to the OneDrive URL, see [upload bytes to the upload session](/onedrive/developer/rest-api/api/driveitem_createuploadsession#upload-bytes-to-the-upload-session).</span></span>

<span data-ttu-id="d1e3c-168">O código a seguir mostra um exemplo de uma versão concisa da atividade de invocação que o bot recebe:</span><span class="sxs-lookup"><span data-stu-id="d1e3c-168">The following code shows an example of a concise version of the invoke activity that the bot receives:</span></span>

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

<span data-ttu-id="d1e3c-169">Da mesma forma, se o usuário recusar o arquivo, o bot receberá o seguinte evento com o mesmo nome de atividade geral:</span><span class="sxs-lookup"><span data-stu-id="d1e3c-169">Similarly, if the user declines the file, the bot receives the following event with the same overall activity name:</span></span>

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

### <a name="notifying-the-user-about-an-uploaded-file"></a><span data-ttu-id="d1e3c-170">Notificar o usuário sobre um arquivo carregado</span><span class="sxs-lookup"><span data-stu-id="d1e3c-170">Notifying the user about an uploaded file</span></span>

<span data-ttu-id="d1e3c-171">Depois de carregar um arquivo na OneDrive do usuário, envie uma mensagem de confirmação para o usuário.</span><span class="sxs-lookup"><span data-stu-id="d1e3c-171">After uploading a file to the user's OneDrive, send a confirmation message to the user.</span></span> <span data-ttu-id="d1e3c-172">A mensagem deve conter o seguinte anexo que o usuário pode selecionar, para visualizar ou abri-la em OneDrive `FileCard` ou baixar localmente:</span><span class="sxs-lookup"><span data-stu-id="d1e3c-172">The message must contain the following `FileCard` attachment that the user can select, either to preview or open it in OneDrive, or download locally:</span></span>

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

<span data-ttu-id="d1e3c-173">A tabela a seguir descreve as propriedades de conteúdo do anexo:</span><span class="sxs-lookup"><span data-stu-id="d1e3c-173">The following table describes the content properties of the attachment:</span></span>

| <span data-ttu-id="d1e3c-174">Propriedade</span><span class="sxs-lookup"><span data-stu-id="d1e3c-174">Property</span></span> | <span data-ttu-id="d1e3c-175">Finalidade</span><span class="sxs-lookup"><span data-stu-id="d1e3c-175">Purpose</span></span> |
| --- | --- |
| `uniqueId` | <span data-ttu-id="d1e3c-176">OneDrive ou SharePoint ID do item da unidade.</span><span class="sxs-lookup"><span data-stu-id="d1e3c-176">OneDrive or SharePoint drive item ID.</span></span> |
| `fileType` | <span data-ttu-id="d1e3c-177">Tipo de arquivo, como .pdf ou .docx.</span><span class="sxs-lookup"><span data-stu-id="d1e3c-177">Type of file, such as .pdf or .docx.</span></span> |

### <a name="fetch-inline-images-from-message"></a><span data-ttu-id="d1e3c-178">Buscar imagens em linha da mensagem</span><span class="sxs-lookup"><span data-stu-id="d1e3c-178">Fetch inline images from message</span></span>

<span data-ttu-id="d1e3c-179">Buscar imagens em linha que fazem parte da mensagem usando o token de acesso do Bot.</span><span class="sxs-lookup"><span data-stu-id="d1e3c-179">Fetch inline images that are part of the message using the Bot's access token.</span></span>

![Imagem em linha](../../assets/images/bots/inline-image.png)

<span data-ttu-id="d1e3c-181">O código a seguir mostra um exemplo de busca de imagens em linha da mensagem:</span><span class="sxs-lookup"><span data-stu-id="d1e3c-181">The following code shows an example of fetching inline images from message:</span></span>

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

### <a name="basic-example-in-c"></a><span data-ttu-id="d1e3c-182">Exemplo básico em C #</span><span class="sxs-lookup"><span data-stu-id="d1e3c-182">Basic example in C#</span></span>

<span data-ttu-id="d1e3c-183">O código a seguir mostra um exemplo de como lidar com carregamentos de arquivo e enviar solicitações de consentimento de arquivo na caixa de diálogo do bot:</span><span class="sxs-lookup"><span data-stu-id="d1e3c-183">The following code shows an example of how to handle file uploads and send file consent requests in the bot's dialog:</span></span>

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

## <a name="code-sample"></a><span data-ttu-id="d1e3c-184">Exemplo de código</span><span class="sxs-lookup"><span data-stu-id="d1e3c-184">Code sample</span></span>

<span data-ttu-id="d1e3c-185">O exemplo de código a seguir demonstra como obter o consentimento do arquivo e carregar arquivos para Teams de um bot:</span><span class="sxs-lookup"><span data-stu-id="d1e3c-185">The following code sample demonstrates how to obtain file consent and upload files to Teams from a bot:</span></span>

|<span data-ttu-id="d1e3c-186">**Exemplo de nome**</span><span class="sxs-lookup"><span data-stu-id="d1e3c-186">**Sample name**</span></span> | <span data-ttu-id="d1e3c-187">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="d1e3c-187">**Description**</span></span> | <span data-ttu-id="d1e3c-188">**.NET**</span><span class="sxs-lookup"><span data-stu-id="d1e3c-188">**.NET**</span></span> | <span data-ttu-id="d1e3c-189">**Javascript**</span><span class="sxs-lookup"><span data-stu-id="d1e3c-189">**Javascript**</span></span> | <span data-ttu-id="d1e3c-190">**Python**</span><span class="sxs-lookup"><span data-stu-id="d1e3c-190">**Python**</span></span>|
|----------------|-----------------|--------------|----------------|-----------|
| <span data-ttu-id="d1e3c-191">Upload de arquivos</span><span class="sxs-lookup"><span data-stu-id="d1e3c-191">File upload</span></span> | <span data-ttu-id="d1e3c-192">Demonstra como obter o consentimento do arquivo e carregar arquivos para Teams de um bot.</span><span class="sxs-lookup"><span data-stu-id="d1e3c-192">Demonstrates how to obtain file consent and upload files to Teams from a bot.</span></span> <span data-ttu-id="d1e3c-193">Além disso, como receber um arquivo enviado para um bot.</span><span class="sxs-lookup"><span data-stu-id="d1e3c-193">Also, how to receive a file sent to a bot.</span></span> | [<span data-ttu-id="d1e3c-194">View</span><span class="sxs-lookup"><span data-stu-id="d1e3c-194">View</span></span>](https://github.com/microsoft/BotBuilder-Samples/blob/main/samples/csharp_dotnetcore/56.teams-file-upload) | [<span data-ttu-id="d1e3c-195">View</span><span class="sxs-lookup"><span data-stu-id="d1e3c-195">View</span></span>](https://github.com/microsoft/BotBuilder-Samples/blob/main/samples/javascript_nodejs/56.teams-file-upload) | [<span data-ttu-id="d1e3c-196">View</span><span class="sxs-lookup"><span data-stu-id="d1e3c-196">View</span></span>](https://github.com/microsoft/BotBuilder-Samples/blob/main/samples/python/56.teams-file-upload) |

## <a name="next-step"></a><span data-ttu-id="d1e3c-197">Próxima etapa</span><span class="sxs-lookup"><span data-stu-id="d1e3c-197">Next step</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="d1e3c-198">Otimizar seu bot com limitação de fluxo no Teams</span><span class="sxs-lookup"><span data-stu-id="d1e3c-198">Optimize your bot with rate limiting in Teams</span></span>](~/bots/how-to/rate-limit.md)
