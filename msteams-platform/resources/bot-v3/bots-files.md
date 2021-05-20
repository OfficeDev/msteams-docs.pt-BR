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
# <a name="send-and-receive-files-through-your-bot"></a><span data-ttu-id="0315b-104">Envie e receba arquivos através do seu bot</span><span class="sxs-lookup"><span data-stu-id="0315b-104">Send and receive files through your bot</span></span>

[!include[v3-to-v4-SDK-pointer](~/includes/v3-to-v4-pointer-bots.md)]

<span data-ttu-id="0315b-105">Existem duas maneiras de enviar arquivos de e para um bot:</span><span class="sxs-lookup"><span data-stu-id="0315b-105">There are two ways to send files to and from a bot:</span></span>

* <span data-ttu-id="0315b-106">Usando as APIs Graph microsoft.</span><span class="sxs-lookup"><span data-stu-id="0315b-106">Using the Microsoft Graph APIs.</span></span> <span data-ttu-id="0315b-107">Este método funciona para bots em todos os escopos em Teams:</span><span class="sxs-lookup"><span data-stu-id="0315b-107">This method works for bots in all scopes in Teams:</span></span>
  * `personal`
  * `channel`
  * `groupchat`
* <span data-ttu-id="0315b-108">Usando as APIs Teams.</span><span class="sxs-lookup"><span data-stu-id="0315b-108">Using the Teams APIs.</span></span> <span data-ttu-id="0315b-109">Estes só suportam arquivos em um contexto:</span><span class="sxs-lookup"><span data-stu-id="0315b-109">These only support files in one context:</span></span>
  * `personal`

## <a name="using-the-microsoft-graph-apis"></a><span data-ttu-id="0315b-110">Usando as APIs de Graph da Microsoft</span><span class="sxs-lookup"><span data-stu-id="0315b-110">Using the Microsoft Graph APIs</span></span>

<span data-ttu-id="0315b-111">Você pode postar mensagens com anexos de cartão fazendo referência aos arquivos SharePoint existentes usando as APIs Graph da Microsoft para [OneDrive e SharePoint](/onedrive/developer/rest-api/).</span><span class="sxs-lookup"><span data-stu-id="0315b-111">You can post messages with card attachments referencing existing SharePoint files using the Microsoft Graph APIs for [OneDrive and SharePoint](/onedrive/developer/rest-api/).</span></span> <span data-ttu-id="0315b-112">O uso do Graph APIs requer obter acesso à pasta OneDrive (para `personal` e `groupchat` arquivos) de um usuário ou aos arquivos nos canais de uma equipe (para `channel` arquivos) através do fluxo padrão de autorização OAuth 2.0.</span><span class="sxs-lookup"><span data-stu-id="0315b-112">Using the Graph APIs requires obtaining access to a user's OneDrive folder (for `personal` and `groupchat` files) or the files in a team's channels (for `channel` files) through the standard OAuth 2.0 authorization flow.</span></span> <span data-ttu-id="0315b-113">Este método funciona em todos os Teams escopos.</span><span class="sxs-lookup"><span data-stu-id="0315b-113">This method works in all Teams scopes.</span></span>

## <a name="using-the-teams-bot-apis"></a><span data-ttu-id="0315b-114">Usando as APIs do Bot Teams</span><span class="sxs-lookup"><span data-stu-id="0315b-114">Using the Teams Bot APIs</span></span>

> [!NOTE]
> <span data-ttu-id="0315b-115">Esse método funciona apenas no `personal` contexto.</span><span class="sxs-lookup"><span data-stu-id="0315b-115">This method works only in the `personal` context.</span></span> <span data-ttu-id="0315b-116">Não funciona no `channel` `groupchat` contexto.</span><span class="sxs-lookup"><span data-stu-id="0315b-116">It does not work in the `channel` or `groupchat` context.</span></span>

<span data-ttu-id="0315b-117">Seu bot pode enviar e receber arquivos diretamente com usuários no `personal` contexto, também conhecidos como chats pessoais, usando Teams APIs.</span><span class="sxs-lookup"><span data-stu-id="0315b-117">Your bot can directly send and receive files with users in the `personal` context, also known as personal chats, using Teams APIs.</span></span> <span data-ttu-id="0315b-118">Isso permite implementar relatórios de despesas, reconhecimento de imagem, arquivamento de arquivos, assinaturas de e e outros cenários envolvendo manipulação direta de conteúdo de arquivo.</span><span class="sxs-lookup"><span data-stu-id="0315b-118">This lets you implement expense reporting, image recognition, file archival, e-signatures, and other scenarios involving direct manipulation of file content.</span></span> <span data-ttu-id="0315b-119">Arquivos compartilhados em Teams normalmente aparecem como cartões e permitem visualização rica no aplicativo.</span><span class="sxs-lookup"><span data-stu-id="0315b-119">Files shared in Teams typically appear as cards, and allow rich in-app viewing.</span></span>

<span data-ttu-id="0315b-120">As seções a seguir descrevem como fazer isso para enviar conteúdo de arquivo como resultado da interação direta do usuário, como enviar uma mensagem.</span><span class="sxs-lookup"><span data-stu-id="0315b-120">The following sections describe how to do this to send file content as a result of direct user interaction, like sending a message.</span></span> <span data-ttu-id="0315b-121">Esta API é fornecida como parte da plataforma bot Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="0315b-121">This API is provided as part of the Microsoft Teams Bot Platform.</span></span>

### <a name="configure-your-bot-to-support-files"></a><span data-ttu-id="0315b-122">Configure seu bot para suportar arquivos</span><span class="sxs-lookup"><span data-stu-id="0315b-122">Configure your bot to support files</span></span>

<span data-ttu-id="0315b-123">Para enviar e receber arquivos em seu bot, você tem que definir a `supportsFiles` propriedade no manifesto para `true` .</span><span class="sxs-lookup"><span data-stu-id="0315b-123">In order to send and receive files in your bot, you have to set the `supportsFiles` property in the manifest to `true`.</span></span> <span data-ttu-id="0315b-124">Esta propriedade está descrita na seção [bots](~/resources/schema/manifest-schema.md#bots) da referência Manifest.</span><span class="sxs-lookup"><span data-stu-id="0315b-124">This property is described in the [bots](~/resources/schema/manifest-schema.md#bots) section of the Manifest reference.</span></span>

<span data-ttu-id="0315b-125">A definição será assim: `"supportsFiles": true` .</span><span class="sxs-lookup"><span data-stu-id="0315b-125">The definition will look like this: `"supportsFiles": true`.</span></span> <span data-ttu-id="0315b-126">Se o bot não `supportsFiles` habilitar, os seguintes recursos não funcionarão.</span><span class="sxs-lookup"><span data-stu-id="0315b-126">If your bot does not enable `supportsFiles`, the following features will not work.</span></span>

### <a name="receiving-files-in-personal-chat"></a><span data-ttu-id="0315b-127">Recebimento de arquivos em chat pessoal</span><span class="sxs-lookup"><span data-stu-id="0315b-127">Receiving files in personal chat</span></span>

<span data-ttu-id="0315b-128">Quando um usuário envia um arquivo para o seu bot, o arquivo é carregado pela primeira vez para o armazenamento OneDrive for Business do usuário.</span><span class="sxs-lookup"><span data-stu-id="0315b-128">When a user sends a file to your bot, the file is first uploaded to the user's OneDrive for Business storage.</span></span> <span data-ttu-id="0315b-129">Em seguida, seu bot receberá uma atividade de mensagem notificando-o do upload do usuário.</span><span class="sxs-lookup"><span data-stu-id="0315b-129">Your bot will then receive a message activity notifying you of the user upload.</span></span> <span data-ttu-id="0315b-130">A atividade conterá metadados de arquivo, como seu nome e a URL de conteúdo.</span><span class="sxs-lookup"><span data-stu-id="0315b-130">The activity will contain file metadata, such as its name and the content URL.</span></span> <span data-ttu-id="0315b-131">Você pode ler diretamente a partir desta URL para buscar seu conteúdo binário.</span><span class="sxs-lookup"><span data-stu-id="0315b-131">You can directly read from this URL to fetch its binary content.</span></span>

#### <a name="message-activity-with-file-attachment-example"></a><span data-ttu-id="0315b-132">Atividade de mensagem com exemplo de anexo de arquivo</span><span class="sxs-lookup"><span data-stu-id="0315b-132">Message activity with file attachment example</span></span>

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

<span data-ttu-id="0315b-133">A tabela a seguir descreve as propriedades de conteúdo do anexo:</span><span class="sxs-lookup"><span data-stu-id="0315b-133">The following table describes the content properties of the attachment:</span></span>

| <span data-ttu-id="0315b-134">Propriedade</span><span class="sxs-lookup"><span data-stu-id="0315b-134">Property</span></span> | <span data-ttu-id="0315b-135">Objetivo</span><span class="sxs-lookup"><span data-stu-id="0315b-135">Purpose</span></span> |
| --- | --- |
| `downloadUrl` | <span data-ttu-id="0315b-136">OneDrive URL para buscar o conteúdo do arquivo.</span><span class="sxs-lookup"><span data-stu-id="0315b-136">OneDrive URL for fetching the content of the file.</span></span> <span data-ttu-id="0315b-137">Você pode emitir um `HTTP GET` diretamente desta URL.</span><span class="sxs-lookup"><span data-stu-id="0315b-137">You can issue an `HTTP GET` directly from this URL.</span></span> |
| `uniqueId` | <span data-ttu-id="0315b-138">ID de arquivo único.</span><span class="sxs-lookup"><span data-stu-id="0315b-138">Unique file ID.</span></span> <span data-ttu-id="0315b-139">Este será o OneDrive iD do item de unidade, no caso do usuário enviar um arquivo para o seu bot.</span><span class="sxs-lookup"><span data-stu-id="0315b-139">This will be the OneDrive drive item ID, in the case of the user sending a file to your bot.</span></span> |
| `fileType` | <span data-ttu-id="0315b-140">Tipo de extensão de arquivo, como pdf ou docx.</span><span class="sxs-lookup"><span data-stu-id="0315b-140">File extension type, such as pdf or docx.</span></span> |

<span data-ttu-id="0315b-141">Como uma prática recomendada, você deve reconhecer o upload do arquivo enviando uma mensagem para o usuário.</span><span class="sxs-lookup"><span data-stu-id="0315b-141">As a best practice, you should acknowledge the file upload by sending back a message to the user.</span></span>

### <a name="uploading-files-to-personal-chat"></a><span data-ttu-id="0315b-142">Upload de arquivos para bate-papo pessoal</span><span class="sxs-lookup"><span data-stu-id="0315b-142">Uploading files to personal chat</span></span>

<span data-ttu-id="0315b-143">O upload de um arquivo para um usuário envolve as seguintes etapas:</span><span class="sxs-lookup"><span data-stu-id="0315b-143">Uploading a file to a user involves the following steps:</span></span>

1. <span data-ttu-id="0315b-144">Envie uma mensagem ao usuário solicitando permissão para escrever o arquivo.</span><span class="sxs-lookup"><span data-stu-id="0315b-144">Send a message to the user requesting permission to write the file.</span></span> <span data-ttu-id="0315b-145">Esta mensagem deve conter um `FileConsentCard` anexo com o nome do arquivo a ser carregado.</span><span class="sxs-lookup"><span data-stu-id="0315b-145">This message must contain a `FileConsentCard` attachment with the name of the file to be uploaded.</span></span>
2. <span data-ttu-id="0315b-146">Se o usuário aceitar o download do arquivo, o bot receberá uma atividade *de Invocação* com uma URL de localização.</span><span class="sxs-lookup"><span data-stu-id="0315b-146">If the user accepts the file download, your bot will receive an *Invoke* activity with a location URL.</span></span>
3. <span data-ttu-id="0315b-147">Para transferir o arquivo, o bot executa um `HTTP POST` diretamente na URL de localização fornecida.</span><span class="sxs-lookup"><span data-stu-id="0315b-147">To transfer the file, your bot performs an `HTTP POST` directly into the provided location URL.</span></span>
4. <span data-ttu-id="0315b-148">Opcionalmente, você pode remover o cartão de consentimento original se não quiser permitir que o usuário aceite uploads adicionais do mesmo arquivo.</span><span class="sxs-lookup"><span data-stu-id="0315b-148">Optionally, you can remove the original consent card if you do not want to allow the user to accept further uploads of the same file.</span></span>

#### <a name="message-requesting-permission-to-upload"></a><span data-ttu-id="0315b-149">Mensagem solicitando permissão para carregar</span><span class="sxs-lookup"><span data-stu-id="0315b-149">Message requesting permission to upload</span></span>

<span data-ttu-id="0315b-150">Esta mensagem de desktop contém um simples objeto de anexo solicitando permissão do usuário para carregar o arquivo:</span><span class="sxs-lookup"><span data-stu-id="0315b-150">This desktop message contains a simple attachment object requesting user permission to upload the file:</span></span>

![Captura de tela do cartão de consentimento solicitando permissão do usuário para carregar arquivo](../../assets/images/bots/bot-file-consent-card.png)

<span data-ttu-id="0315b-152">Esta mensagem móvel contém um objeto de anexo solicitando permissão do usuário para carregar o arquivo:</span><span class="sxs-lookup"><span data-stu-id="0315b-152">This mobile message contains an attachment object requesting user permission to upload the file:</span></span>

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

<span data-ttu-id="0315b-154">A tabela a seguir descreve as propriedades de conteúdo do anexo:</span><span class="sxs-lookup"><span data-stu-id="0315b-154">The following table describes the content properties of the attachment:</span></span>

| <span data-ttu-id="0315b-155">Propriedade</span><span class="sxs-lookup"><span data-stu-id="0315b-155">Property</span></span> | <span data-ttu-id="0315b-156">Objetivo</span><span class="sxs-lookup"><span data-stu-id="0315b-156">Purpose</span></span> |
| --- | --- |
| `description` | <span data-ttu-id="0315b-157">Descrição do arquivo.</span><span class="sxs-lookup"><span data-stu-id="0315b-157">Description of the file.</span></span> <span data-ttu-id="0315b-158">Pode ser mostrado ao usuário para descrever seu propósito ou para resumir seu conteúdo.</span><span class="sxs-lookup"><span data-stu-id="0315b-158">May be shown to the user to describe its purpose or to summarize its content.</span></span> |
| `sizeInBytes` | <span data-ttu-id="0315b-159">Fornece ao usuário uma estimativa do tamanho do arquivo e da quantidade de espaço que ele ocupará OneDrive.</span><span class="sxs-lookup"><span data-stu-id="0315b-159">Provides the user an estimate of the file size and the amount of space it will take in OneDrive.</span></span> |
| `acceptContext` | <span data-ttu-id="0315b-160">Contexto adicional que será transmitido silenciosamente ao seu bot quando o usuário aceitar o arquivo.</span><span class="sxs-lookup"><span data-stu-id="0315b-160">Additional context that will be silently transmitted to your bot when the user accepts the file.</span></span> |
| `declineContext` | <span data-ttu-id="0315b-161">Contexto adicional que será transmitido silenciosamente ao seu bot quando o usuário recusar o arquivo.</span><span class="sxs-lookup"><span data-stu-id="0315b-161">Additional context that will be silently transmitted to your bot when the user declines the file.</span></span> |

#### <a name="invoke-activity-when-the-user-accepts-the-file"></a><span data-ttu-id="0315b-162">Invoque a atividade quando o usuário aceitar o arquivo</span><span class="sxs-lookup"><span data-stu-id="0315b-162">Invoke activity when the user accepts the file</span></span>

<span data-ttu-id="0315b-163">Uma atividade de invocação é enviada ao seu bot se e quando o usuário aceitar o arquivo.</span><span class="sxs-lookup"><span data-stu-id="0315b-163">An invoke activity is sent to your bot if and when the user accepts the file.</span></span> <span data-ttu-id="0315b-164">Ele contém a URL OneDrive for Business espaço reservado que o seu bot pode então `PUT` emitir para transferir o conteúdo do arquivo.</span><span class="sxs-lookup"><span data-stu-id="0315b-164">It contains the OneDrive for Business placeholder URL that your bot can then issue a `PUT` into to transfer the file contents.</span></span> <span data-ttu-id="0315b-165">para informações sobre o upload para a URL OneDrive leia este artigo: [Upload bytes para a sessão de upload](/onedrive/developer/rest-api/api/driveitem_createuploadsession#upload-bytes-to-the-upload-session).</span><span class="sxs-lookup"><span data-stu-id="0315b-165">for information on uploading to the OneDrive URL read this article: [Upload bytes to the upload session](/onedrive/developer/rest-api/api/driveitem_createuploadsession#upload-bytes-to-the-upload-session).</span></span>

<span data-ttu-id="0315b-166">O exemplo a seguir mostra uma versão abreviada da atividade de invocação que seu bot receberá:</span><span class="sxs-lookup"><span data-stu-id="0315b-166">The following example shows an abridged version of the invoke activity that your bot will receive:</span></span>

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

<span data-ttu-id="0315b-167">Da mesma forma, se o usuário recusar o arquivo, o bot receberá o seguinte evento, com o mesmo nome de atividade geral:</span><span class="sxs-lookup"><span data-stu-id="0315b-167">Similarly, if the user declines the file, your bot will receive the following event, with the same overall activity name:</span></span>

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

### <a name="notifying-the-user-about-an-uploaded-file"></a><span data-ttu-id="0315b-168">Notificar o usuário sobre um arquivo carregado</span><span class="sxs-lookup"><span data-stu-id="0315b-168">Notifying the user about an uploaded file</span></span>

<span data-ttu-id="0315b-169">Depois de carregar um arquivo para a OneDrive do usuário, se você usar o mecanismo descrito acima ou OneDrive APIs delegadas pelo usuário, você deve enviar uma mensagem de confirmação ao usuário.</span><span class="sxs-lookup"><span data-stu-id="0315b-169">After uploading a file to the user's OneDrive, whether you use the mechanism described above or OneDrive user delegated APIs, you should send a confirmation message to the user.</span></span> <span data-ttu-id="0315b-170">Esta mensagem deve conter um `FileCard` anexo no qual o usuário pode clicar, seja para visualizá-la, abri-la em OneDrive ou baixar localmente.</span><span class="sxs-lookup"><span data-stu-id="0315b-170">This message should contain  a `FileCard` attachment that the user can click on, either to preview it, open it in OneDrive, or download locally.</span></span>

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

<span data-ttu-id="0315b-171">A tabela a seguir descreve as propriedades de conteúdo do anexo:</span><span class="sxs-lookup"><span data-stu-id="0315b-171">The following table describes the content properties of the attachment:</span></span>

| <span data-ttu-id="0315b-172">Propriedade</span><span class="sxs-lookup"><span data-stu-id="0315b-172">Property</span></span> | <span data-ttu-id="0315b-173">Objetivo</span><span class="sxs-lookup"><span data-stu-id="0315b-173">Purpose</span></span> |
| --- | --- |
| `uniqueId` | <span data-ttu-id="0315b-174">OneDrive/SharePoint iD do item de unidade.</span><span class="sxs-lookup"><span data-stu-id="0315b-174">OneDrive/SharePoint drive item ID.</span></span> |
| `fileType` | <span data-ttu-id="0315b-175">Tipo de arquivo, como pdf ou docx.</span><span class="sxs-lookup"><span data-stu-id="0315b-175">File type, such as pdf or docx.</span></span> |

### <a name="basic-example-in-c"></a><span data-ttu-id="0315b-176">Exemplo básico em C #</span><span class="sxs-lookup"><span data-stu-id="0315b-176">Basic example in C#</span></span>

<span data-ttu-id="0315b-177">A amostra a seguir mostra como você pode lidar com uploads de arquivos e enviar solicitações de consentimento do arquivo na caixa de diálogo do seu bot:</span><span class="sxs-lookup"><span data-stu-id="0315b-177">The following sample shows how you can handle file uploads and send file consent requests in your bot's dialog:</span></span>

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
