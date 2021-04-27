---
title: Enviando e recebendo arquivos de um bot
description: Descreve como enviar e receber arquivos de um bot
keywords: arquivos de bots do teams enviam recebimento
ms.topic: how-to
localization_priority: Normal
ms.date: 05/20/2019
ms.openlocfilehash: c5ee32d10e5a6adc5a08d1a0556a18be8367460a
ms.sourcegitcommit: 825abed2f8784d2bab7407ba7a4455ae17bbd28f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2021
ms.locfileid: "52020650"
---
# <a name="send-and-receive-files-through-your-bot"></a><span data-ttu-id="e3593-104">Enviar e receber arquivos por meio de seu bot</span><span class="sxs-lookup"><span data-stu-id="e3593-104">Send and receive files through your bot</span></span>

[!include[v3-to-v4-SDK-pointer](~/includes/v3-to-v4-pointer-bots.md)]

<span data-ttu-id="e3593-105">Há duas maneiras de enviar arquivos de e para um bot:</span><span class="sxs-lookup"><span data-stu-id="e3593-105">There are two ways to send files to and from a bot:</span></span>

* <span data-ttu-id="e3593-106">Usando as APIs do Microsoft Graph.</span><span class="sxs-lookup"><span data-stu-id="e3593-106">Using the Microsoft Graph APIs.</span></span> <span data-ttu-id="e3593-107">Este método funciona para bots em todos os escopos no Teams:</span><span class="sxs-lookup"><span data-stu-id="e3593-107">This method works for bots in all scopes in Teams:</span></span>
  * `personal`
  * `channel`
  * `groupchat`
* <span data-ttu-id="e3593-108">Usando as APIs do Teams.</span><span class="sxs-lookup"><span data-stu-id="e3593-108">Using the Teams APIs.</span></span> <span data-ttu-id="e3593-109">Esses arquivos só suportam em um contexto:</span><span class="sxs-lookup"><span data-stu-id="e3593-109">These only support files in one context:</span></span>
  * `personal`

## <a name="using-the-microsoft-graph-apis"></a><span data-ttu-id="e3593-110">Usando as APIs do Microsoft Graph</span><span class="sxs-lookup"><span data-stu-id="e3593-110">Using the Microsoft Graph APIs</span></span>

<span data-ttu-id="e3593-111">Você pode postar mensagens com anexos de cartão fazendo referência a arquivos existentes do SharePoint usando as APIs do Microsoft Graph para [OneDrive e SharePoint](/onedrive/developer/rest-api/).</span><span class="sxs-lookup"><span data-stu-id="e3593-111">You can post messages with card attachments referencing existing SharePoint files using the Microsoft Graph APIs for [OneDrive and SharePoint](/onedrive/developer/rest-api/).</span></span> <span data-ttu-id="e3593-112">O uso das APIs do Graph requer a obtenção de acesso à pasta do OneDrive do usuário (para e arquivos) ou aos arquivos nos canais de uma equipe (para arquivos) por meio do fluxo de autorização `personal` `groupchat` `channel` OAuth 2.0 padrão.</span><span class="sxs-lookup"><span data-stu-id="e3593-112">Using the Graph APIs requires obtaining access to a user's OneDrive folder (for `personal` and `groupchat` files) or the files in a team's channels (for `channel` files) through the standard OAuth 2.0 authorization flow.</span></span> <span data-ttu-id="e3593-113">Esse método funciona em todos os escopos do Teams.</span><span class="sxs-lookup"><span data-stu-id="e3593-113">This method works in all Teams scopes.</span></span>

## <a name="using-the-teams-bot-apis"></a><span data-ttu-id="e3593-114">Usando as APIs de Bot do Teams</span><span class="sxs-lookup"><span data-stu-id="e3593-114">Using the Teams Bot APIs</span></span>

> [!NOTE]
> <span data-ttu-id="e3593-115">Esse método só funciona no `personal` contexto.</span><span class="sxs-lookup"><span data-stu-id="e3593-115">This method works only in the `personal` context.</span></span> <span data-ttu-id="e3593-116">Ele não funciona no `channel` contexto `groupchat` ou.</span><span class="sxs-lookup"><span data-stu-id="e3593-116">It does not work in the `channel` or `groupchat` context.</span></span>

<span data-ttu-id="e3593-117">Seu bot pode enviar e receber arquivos diretamente com usuários no contexto, também conhecidos como `personal` chats pessoais, usando APIs do Teams.</span><span class="sxs-lookup"><span data-stu-id="e3593-117">Your bot can directly send and receive files with users in the `personal` context, also known as personal chats, using Teams APIs.</span></span> <span data-ttu-id="e3593-118">Isso permite implementar relatórios de despesas, reconhecimento de imagem, arquivamento de arquivos, assinaturas eletrônicas e outros cenários envolvendo manipulação direta do conteúdo do arquivo.</span><span class="sxs-lookup"><span data-stu-id="e3593-118">This lets you implement expense reporting, image recognition, file archival, e-signatures, and other scenarios involving direct manipulation of file content.</span></span> <span data-ttu-id="e3593-119">Os arquivos compartilhados no Teams normalmente aparecem como cartões e permitem a exibição rica no aplicativo.</span><span class="sxs-lookup"><span data-stu-id="e3593-119">Files shared in Teams typically appear as cards, and allow rich in-app viewing.</span></span>

<span data-ttu-id="e3593-120">As seções a seguir descrevem como fazer isso para enviar conteúdo de arquivo como resultado da interação direta do usuário, como o envio de uma mensagem.</span><span class="sxs-lookup"><span data-stu-id="e3593-120">The following sections describe how to do this to send file content as a result of direct user interaction, like sending a message.</span></span> <span data-ttu-id="e3593-121">Essa API é fornecida como parte da Plataforma bot do Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="e3593-121">This API is provided as part of the Microsoft Teams Bot Platform.</span></span>

### <a name="configure-your-bot-to-support-files"></a><span data-ttu-id="e3593-122">Configurar seu bot para dar suporte a arquivos</span><span class="sxs-lookup"><span data-stu-id="e3593-122">Configure your bot to support files</span></span>

<span data-ttu-id="e3593-123">Para enviar e receber arquivos em seu bot, você precisa definir a `supportsFiles` propriedade no manifesto como `true` .</span><span class="sxs-lookup"><span data-stu-id="e3593-123">In order to send and receive files in your bot, you have to set the `supportsFiles` property in the manifest to `true`.</span></span> <span data-ttu-id="e3593-124">Essa propriedade é descrita na seção [bots](~/resources/schema/manifest-schema.md#bots) da referência manifesto.</span><span class="sxs-lookup"><span data-stu-id="e3593-124">This property is described in the [bots](~/resources/schema/manifest-schema.md#bots) section of the Manifest reference.</span></span>

<span data-ttu-id="e3593-125">A definição será assim: `"supportsFiles": true` .</span><span class="sxs-lookup"><span data-stu-id="e3593-125">The definition will look like this: `"supportsFiles": true`.</span></span> <span data-ttu-id="e3593-126">Se o bot não `supportsFiles` habilitar , os recursos a seguir não funcionarão.</span><span class="sxs-lookup"><span data-stu-id="e3593-126">If your bot does not enable `supportsFiles`, the following features will not work.</span></span>

### <a name="receiving-files-in-personal-chat"></a><span data-ttu-id="e3593-127">Recebimento de arquivos no chat pessoal</span><span class="sxs-lookup"><span data-stu-id="e3593-127">Receiving files in personal chat</span></span>

<span data-ttu-id="e3593-128">Quando um usuário envia um arquivo para seu bot, o arquivo é carregado pela primeira vez no armazenamento do OneDrive for Business do usuário.</span><span class="sxs-lookup"><span data-stu-id="e3593-128">When a user sends a file to your bot, the file is first uploaded to the user's OneDrive for Business storage.</span></span> <span data-ttu-id="e3593-129">Em seguida, o bot receberá uma atividade de mensagem notificando o carregamento do usuário.</span><span class="sxs-lookup"><span data-stu-id="e3593-129">Your bot will then receive a message activity notifying you of the user upload.</span></span> <span data-ttu-id="e3593-130">A atividade conterá metadados de arquivo, como seu nome e a URL de conteúdo.</span><span class="sxs-lookup"><span data-stu-id="e3593-130">The activity will contain file metadata, such as its name and the content URL.</span></span> <span data-ttu-id="e3593-131">Você pode ler diretamente a partir dessa URL para buscar seu conteúdo binário.</span><span class="sxs-lookup"><span data-stu-id="e3593-131">You can directly read from this URL to fetch its binary content.</span></span>

#### <a name="message-activity-with-file-attachment-example"></a><span data-ttu-id="e3593-132">Atividade de mensagem com exemplo de anexo de arquivo</span><span class="sxs-lookup"><span data-stu-id="e3593-132">Message activity with file attachment example</span></span>

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

<span data-ttu-id="e3593-133">A tabela a seguir descreve as propriedades de conteúdo do anexo:</span><span class="sxs-lookup"><span data-stu-id="e3593-133">The following table describes the content properties of the attachment:</span></span>

| <span data-ttu-id="e3593-134">Propriedade</span><span class="sxs-lookup"><span data-stu-id="e3593-134">Property</span></span> | <span data-ttu-id="e3593-135">Objetivo</span><span class="sxs-lookup"><span data-stu-id="e3593-135">Purpose</span></span> |
| --- | --- |
| `downloadUrl` | <span data-ttu-id="e3593-136">URL do OneDrive para buscar o conteúdo do arquivo.</span><span class="sxs-lookup"><span data-stu-id="e3593-136">OneDrive URL for fetching the content of the file.</span></span> <span data-ttu-id="e3593-137">Você pode emitir um `HTTP GET` diretamente a partir dessa URL.</span><span class="sxs-lookup"><span data-stu-id="e3593-137">You can issue an `HTTP GET` directly from this URL.</span></span> |
| `uniqueId` | <span data-ttu-id="e3593-138">ID de arquivo exclusivo.</span><span class="sxs-lookup"><span data-stu-id="e3593-138">Unique file ID.</span></span> <span data-ttu-id="e3593-139">Essa será a ID do item de unidade do OneDrive, no caso do usuário enviar um arquivo para seu bot.</span><span class="sxs-lookup"><span data-stu-id="e3593-139">This will be the OneDrive drive item ID, in the case of the user sending a file to your bot.</span></span> |
| `fileType` | <span data-ttu-id="e3593-140">Tipo de extensão de arquivo, como pdf ou docx.</span><span class="sxs-lookup"><span data-stu-id="e3593-140">File extension type, such as pdf or docx.</span></span> |

<span data-ttu-id="e3593-141">Como prática prática, você deve reconhecer o carregamento de arquivo enviando uma mensagem para o usuário.</span><span class="sxs-lookup"><span data-stu-id="e3593-141">As a best practice, you should acknowledge the file upload by sending back a message to the user.</span></span>

### <a name="uploading-files-to-personal-chat"></a><span data-ttu-id="e3593-142">Carregando arquivos para chat pessoal</span><span class="sxs-lookup"><span data-stu-id="e3593-142">Uploading files to personal chat</span></span>

<span data-ttu-id="e3593-143">Carregar um arquivo para um usuário envolve as seguintes etapas:</span><span class="sxs-lookup"><span data-stu-id="e3593-143">Uploading a file to a user involves the following steps:</span></span>

1. <span data-ttu-id="e3593-144">Envie uma mensagem para o usuário solicitando permissão para gravar o arquivo.</span><span class="sxs-lookup"><span data-stu-id="e3593-144">Send a message to the user requesting permission to write the file.</span></span> <span data-ttu-id="e3593-145">Esta mensagem deve conter `FileConsentCard` um anexo com o nome do arquivo a ser carregado.</span><span class="sxs-lookup"><span data-stu-id="e3593-145">This message must contain a `FileConsentCard` attachment with the name of the file to be uploaded.</span></span>
2. <span data-ttu-id="e3593-146">Se o usuário aceitar o download do arquivo, seu bot receberá uma atividade *Invocar* com uma URL de local.</span><span class="sxs-lookup"><span data-stu-id="e3593-146">If the user accepts the file download, your bot will receive an *Invoke* activity with a location URL.</span></span>
3. <span data-ttu-id="e3593-147">Para transferir o arquivo, seu bot executa um diretamente para a `HTTP POST` URL de local fornecida.</span><span class="sxs-lookup"><span data-stu-id="e3593-147">To transfer the file, your bot performs an `HTTP POST` directly into the provided location URL.</span></span>
4. <span data-ttu-id="e3593-148">Opcionalmente, você pode remover o cartão de consentimento original se não quiser permitir que o usuário aceite mais carregamentos do mesmo arquivo.</span><span class="sxs-lookup"><span data-stu-id="e3593-148">Optionally, you can remove the original consent card if you do not want to allow the user to accept further uploads of the same file.</span></span>

#### <a name="message-requesting-permission-to-upload"></a><span data-ttu-id="e3593-149">Mensagem solicitando permissão para carregar</span><span class="sxs-lookup"><span data-stu-id="e3593-149">Message requesting permission to upload</span></span>

<span data-ttu-id="e3593-150">Esta mensagem da área de trabalho contém um objeto de anexo simples solicitando permissão do usuário para carregar o arquivo:</span><span class="sxs-lookup"><span data-stu-id="e3593-150">This desktop message contains a simple attachment object requesting user permission to upload the file:</span></span>

![Captura de tela do cartão de consentimento solicitando permissão do usuário para carregar arquivo](../../assets/images/bots/bot-file-consent-card.png)

<span data-ttu-id="e3593-152">Esta mensagem móvel contém um objeto attachment solicitando permissão do usuário para carregar o arquivo:</span><span class="sxs-lookup"><span data-stu-id="e3593-152">This mobile message contains an attachment object requesting user permission to upload the file:</span></span>

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

<span data-ttu-id="e3593-154">A tabela a seguir descreve as propriedades de conteúdo do anexo:</span><span class="sxs-lookup"><span data-stu-id="e3593-154">The following table describes the content properties of the attachment:</span></span>

| <span data-ttu-id="e3593-155">Propriedade</span><span class="sxs-lookup"><span data-stu-id="e3593-155">Property</span></span> | <span data-ttu-id="e3593-156">Objetivo</span><span class="sxs-lookup"><span data-stu-id="e3593-156">Purpose</span></span> |
| --- | --- |
| `description` | <span data-ttu-id="e3593-157">Descrição do arquivo.</span><span class="sxs-lookup"><span data-stu-id="e3593-157">Description of the file.</span></span> <span data-ttu-id="e3593-158">Pode ser mostrado ao usuário para descrever sua finalidade ou resumir seu conteúdo.</span><span class="sxs-lookup"><span data-stu-id="e3593-158">May be shown to the user to describe its purpose or to summarize its content.</span></span> |
| `sizeInBytes` | <span data-ttu-id="e3593-159">Fornece ao usuário uma estimativa do tamanho do arquivo e da quantidade de espaço que ele levará no OneDrive.</span><span class="sxs-lookup"><span data-stu-id="e3593-159">Provides the user an estimate of the file size and the amount of space it will take in OneDrive.</span></span> |
| `acceptContext` | <span data-ttu-id="e3593-160">Contexto adicional que será transmitido silenciosamente para o bot quando o usuário aceitar o arquivo.</span><span class="sxs-lookup"><span data-stu-id="e3593-160">Additional context that will be silently transmitted to your bot when the user accepts the file.</span></span> |
| `declineContext` | <span data-ttu-id="e3593-161">Contexto adicional que será transmitido silenciosamente para o bot quando o usuário recusar o arquivo.</span><span class="sxs-lookup"><span data-stu-id="e3593-161">Additional context that will be silently transmitted to your bot when the user declines the file.</span></span> |

#### <a name="invoke-activity-when-the-user-accepts-the-file"></a><span data-ttu-id="e3593-162">Invocar atividade quando o usuário aceitar o arquivo</span><span class="sxs-lookup"><span data-stu-id="e3593-162">Invoke activity when the user accepts the file</span></span>

<span data-ttu-id="e3593-163">Uma atividade de invocação é enviada ao bot se e quando o usuário aceitar o arquivo.</span><span class="sxs-lookup"><span data-stu-id="e3593-163">An invoke activity is sent to your bot if and when the user accepts the file.</span></span> <span data-ttu-id="e3593-164">Ele contém a URL de espaço reservado do OneDrive for Business que seu bot pode emitir para transferir `PUT` o conteúdo do arquivo.</span><span class="sxs-lookup"><span data-stu-id="e3593-164">It contains the OneDrive for Business placeholder URL that your bot can then issue a `PUT` into to transfer the file contents.</span></span> <span data-ttu-id="e3593-165">para obter informações sobre como carregar para a URL do OneDrive leia este artigo: [Carregar bytes para a sessão de carregamento](/onedrive/developer/rest-api/api/driveitem_createuploadsession#upload-bytes-to-the-upload-session).</span><span class="sxs-lookup"><span data-stu-id="e3593-165">for information on uploading to the OneDrive URL read this article: [Upload bytes to the upload session](/onedrive/developer/rest-api/api/driveitem_createuploadsession#upload-bytes-to-the-upload-session).</span></span>

<span data-ttu-id="e3593-166">O exemplo a seguir mostra uma versão resumida da atividade de invocação que seu bot receberá:</span><span class="sxs-lookup"><span data-stu-id="e3593-166">The following example shows an abridged version of the invoke activity that your bot will receive:</span></span>

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

<span data-ttu-id="e3593-167">Da mesma forma, se o usuário recusar o arquivo, seu bot receberá o seguinte evento, com o mesmo nome de atividade geral:</span><span class="sxs-lookup"><span data-stu-id="e3593-167">Similarly, if the user declines the file, your bot will receive the following event, with the same overall activity name:</span></span>

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

### <a name="notifying-the-user-about-an-uploaded-file"></a><span data-ttu-id="e3593-168">Notificar o usuário sobre um arquivo carregado</span><span class="sxs-lookup"><span data-stu-id="e3593-168">Notifying the user about an uploaded file</span></span>

<span data-ttu-id="e3593-169">Depois de carregar um arquivo no OneDrive do usuário, se você usar o mecanismo descrito acima ou as APIs delegadas pelo usuário do OneDrive, você deverá enviar uma mensagem de confirmação ao usuário.</span><span class="sxs-lookup"><span data-stu-id="e3593-169">After uploading a file to the user's OneDrive, whether you use the mechanism described above or OneDrive user delegated APIs, you should send a confirmation message to the user.</span></span> <span data-ttu-id="e3593-170">Esta mensagem deve conter um anexo no qual o usuário pode clicar, para visualiza-la, `FileCard` abri-la no OneDrive ou baixar localmente.</span><span class="sxs-lookup"><span data-stu-id="e3593-170">This message should contain  a `FileCard` attachment that the user can click on, either to preview it, open it in OneDrive, or download locally.</span></span>

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

<span data-ttu-id="e3593-171">A tabela a seguir descreve as propriedades de conteúdo do anexo:</span><span class="sxs-lookup"><span data-stu-id="e3593-171">The following table describes the content properties of the attachment:</span></span>

| <span data-ttu-id="e3593-172">Propriedade</span><span class="sxs-lookup"><span data-stu-id="e3593-172">Property</span></span> | <span data-ttu-id="e3593-173">Objetivo</span><span class="sxs-lookup"><span data-stu-id="e3593-173">Purpose</span></span> |
| --- | --- |
| `uniqueId` | <span data-ttu-id="e3593-174">ID do item de unidade do OneDrive/SharePoint.</span><span class="sxs-lookup"><span data-stu-id="e3593-174">OneDrive/SharePoint drive item ID.</span></span> |
| `fileType` | <span data-ttu-id="e3593-175">Tipo de arquivo, como pdf ou docx.</span><span class="sxs-lookup"><span data-stu-id="e3593-175">File type, such as pdf or docx.</span></span> |

### <a name="basic-example-in-c"></a><span data-ttu-id="e3593-176">Exemplo básico em C #</span><span class="sxs-lookup"><span data-stu-id="e3593-176">Basic example in C#</span></span>

<span data-ttu-id="e3593-177">O exemplo a seguir mostra como você pode lidar com carregamentos de arquivos e enviar solicitações de consentimento de arquivo na caixa de diálogo do bot.</span><span class="sxs-lookup"><span data-stu-id="e3593-177">The following sample shows how you can handle file uploads and send file consent requests in your bot's dialog.</span></span>

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
