---
title: Localização para seu aplicativo
description: Descreve considerações para a localização de seu Microsoft Teams app.
ms.topic: conceptual
localization_priority: Normal
keywords: teams publish store office publishing AppSource localization language
ms.date: 05/15/2018
ms.openlocfilehash: 6dbdeb6d16c99aada23f8d74a92d958f9c29b69d
ms.sourcegitcommit: 118f7261d313feeac5b398fef56a44bd90104b2f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/31/2021
ms.locfileid: "52709625"
---
# <a name="localization-for-microsoft-teams-apps"></a><span data-ttu-id="17426-104">Localização para Microsoft Teams aplicativos</span><span class="sxs-lookup"><span data-stu-id="17426-104">Localization for Microsoft Teams apps</span></span>

<span data-ttu-id="17426-105">Ao localização do aplicativo Microsoft Teams, considere o seguinte:</span><span class="sxs-lookup"><span data-stu-id="17426-105">When localizing your Microsoft Teams app, you must consider the following:</span></span>

1. <span data-ttu-id="17426-106">Sua Teams de armazenamento (se aplicável).</span><span class="sxs-lookup"><span data-stu-id="17426-106">Your Teams store listing (if applicable).</span></span>
1. <span data-ttu-id="17426-107">As cadeias de caracteres voltadas para o usuário final no manifesto do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="17426-107">The end-user facing strings in your app manifest.</span></span> <span data-ttu-id="17426-108">Por exemplo, comandos de bot.</span><span class="sxs-lookup"><span data-stu-id="17426-108">For example bot commands.</span></span>
1. <span data-ttu-id="17426-109">Respondendo ao texto localizado enviado de seus usuários.</span><span class="sxs-lookup"><span data-stu-id="17426-109">Responding to localized text submitted from your users.</span></span>

## <a name="localizing-your-appsource-listing"></a><span data-ttu-id="17426-110">Localizando sua listagem do AppSource</span><span class="sxs-lookup"><span data-stu-id="17426-110">Localizing your AppSource listing</span></span>

<span data-ttu-id="17426-111">Se você estiver publicando na loja, você precisa estar ciente de que ainda não há suporte para a localização da listagem do AppSource.</span><span class="sxs-lookup"><span data-stu-id="17426-111">If you're publishing to the store, you need to be aware that localizing your AppSource listing is not yet supported.</span></span> <span data-ttu-id="17426-112">No entanto, em preparação para suporte para listagens localizadas na loja de aplicativos, você pode adicionar idiomas adicionais à sua listagem.</span><span class="sxs-lookup"><span data-stu-id="17426-112">However, in preparation for support for localized listings in the app store you can add additional languages to your listing.</span></span> <span data-ttu-id="17426-113">Atualmente, apenas as informações de idioma padrão (inglês) fornecidas no [Partner Center](/office/dev/store/submit-to-appsource-via-partner-center) para sua listagem serão exibidas na listagem de site do [AppSource](https://appsource.microsoft.com/marketplace/apps?product=office%3Bteams&page=1) para seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="17426-113">Currently only the default (English) language information you provide in [Partner Center](/office/dev/store/submit-to-appsource-via-partner-center) for your listing will appear in the [AppSource website](https://appsource.microsoft.com/marketplace/apps?product=office%3Bteams&page=1) listing for your app.</span></span>

### <a name="example-of-configuring-localization"></a><span data-ttu-id="17426-114">Exemplo de configuração de localização</span><span class="sxs-lookup"><span data-stu-id="17426-114">Example of configuring localization</span></span>

<span data-ttu-id="17426-115">Para configurar um idioma adicional para seu aplicativo, no [Partner Center,](/office/dev/store/submit-to-appsource-via-partner-center)selecione inglês e o idioma adicional do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="17426-115">To configure an additional language for your app, in [Partner Center](/office/dev/store/submit-to-appsource-via-partner-center), select both English and the additional language of the app.</span></span> <span data-ttu-id="17426-116">O francês é usado neste exemplo:</span><span class="sxs-lookup"><span data-stu-id="17426-116">French is used in this example:</span></span>

1. <span data-ttu-id="17426-117">Adicionar idioma inglês</span><span class="sxs-lookup"><span data-stu-id="17426-117">Add English language</span></span>
    * <span data-ttu-id="17426-118">Preencha o nome do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="17426-118">Fill in the app name.</span></span>
    * <span data-ttu-id="17426-119">Preencha uma breve descrição do aplicativo em inglês.</span><span class="sxs-lookup"><span data-stu-id="17426-119">Fill in a short description of the app in English.</span></span>
    * <span data-ttu-id="17426-120">Preencha a longa descrição do aplicativo em inglês.</span><span class="sxs-lookup"><span data-stu-id="17426-120">Fill in the long description of the app in English.</span></span>
    * <span data-ttu-id="17426-121">Na descrição longa, adicione também a linha "Este aplicativo está disponível em "francês".</span><span class="sxs-lookup"><span data-stu-id="17426-121">In the long description, please also add the line “This app is available in “French”.</span></span>
    * <span data-ttu-id="17426-122">Upload as imagens da interface do usuário do aplicativo (em inglês).</span><span class="sxs-lookup"><span data-stu-id="17426-122">Upload the images of your app UI (in English).</span></span>
2. <span data-ttu-id="17426-123">Adicionar idioma francês</span><span class="sxs-lookup"><span data-stu-id="17426-123">Add French language</span></span>
    * <span data-ttu-id="17426-124">Preencha o nome do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="17426-124">Fill in the app name.</span></span>
    * <span data-ttu-id="17426-125">Preencha uma breve descrição do aplicativo em francês.</span><span class="sxs-lookup"><span data-stu-id="17426-125">Fill in a short description of the app in French.</span></span>
    * <span data-ttu-id="17426-126">Preencha a longa descrição do aplicativo em francês.</span><span class="sxs-lookup"><span data-stu-id="17426-126">Fill in the long description of the app in French.</span></span>
    * <span data-ttu-id="17426-127">Upload as imagens da interface do usuário do aplicativo (em francês).</span><span class="sxs-lookup"><span data-stu-id="17426-127">Upload the images of your app UI (in French).</span></span>

<span data-ttu-id="17426-128">As imagens carregadas com o idioma inglês serão as usadas no AppSource.</span><span class="sxs-lookup"><span data-stu-id="17426-128">The images you upload with the English language will be the ones used in AppSource.</span></span>

## <a name="localizing-the-strings-in-your-app-manifest"></a><span data-ttu-id="17426-129">Localizando as cadeias de caracteres no manifesto do aplicativo</span><span class="sxs-lookup"><span data-stu-id="17426-129">Localizing the strings in your app manifest</span></span>

<span data-ttu-id="17426-130">Você deve usar o Microsoft Teams de aplicativo v1.5+ para localização adequada do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="17426-130">You must use the Microsoft Teams app schema v1.5+ to properly localize your app.</span></span> <span data-ttu-id="17426-131">Você pode fazer isso definindo o atributo em seu arquivo manifest.json como ' ' e atualizando a `$schema` https://developer.microsoft.com/en-us/json-schemas/teams/v1.8/MicrosoftTeams.Localization.schema.json propriedade 'manifestVersion' como '1.7'.</span><span class="sxs-lookup"><span data-stu-id="17426-131">You can do this by setting the `$schema` attribute in your manifest.json file to 'https://developer.microsoft.com/en-us/json-schemas/teams/v1.8/MicrosoftTeams.Localization.schema.json' and updating the 'manifestVersion' property to '1.7'.</span></span>

### <a name="example-manifestjson-change"></a><span data-ttu-id="17426-132">Exemplo manifest.jsna alteração</span><span class="sxs-lookup"><span data-stu-id="17426-132">Example manifest.json change</span></span>

```json
{
  "$schema": "https://developer.microsoft.com/en-us/json-schemas/teams/v1.8/MicrosoftTeams.Localization.schema.json",
  "manifestVersion": "1.5",
  ...
}
```

<span data-ttu-id="17426-133">Em seguida, você deseja adicionar a propriedade 'localizationInfo' com o idioma padrão que o aplicativo oferece suporte.</span><span class="sxs-lookup"><span data-stu-id="17426-133">You will then want to add the 'localizationInfo' property with the default language that your application supports.</span></span> <span data-ttu-id="17426-134">O idioma padrão é usado como o idioma de fallback final se as configurações do cliente do usuário não corresponderem a nenhum dos idiomas adicionais.</span><span class="sxs-lookup"><span data-stu-id="17426-134">The default language is used as the final fallback language if the user's client settings do not match any of your additional languages.</span></span>

### <a name="example-manifestjson-change"></a><span data-ttu-id="17426-135">Exemplo manifest.jsna alteração</span><span class="sxs-lookup"><span data-stu-id="17426-135">Example manifest.json change</span></span>

```json
{
  ...
  "localizationInfo": {
    "defaultLanguageTag": "en"
  }
  ...
}
```

<span data-ttu-id="17426-136">Você pode fornecer arquivos .json adicionais com traduções de todas as cadeias de caracteres voltadas para o usuário em seu manifesto.</span><span class="sxs-lookup"><span data-stu-id="17426-136">You can provide additional .json files with translations of all the user facing strings in your manifest.</span></span> <span data-ttu-id="17426-137">Esses arquivos devem aderir ao esquema [JSON](../../resources/schema/localization-schema.md) do arquivo de localização e devem ser adicionados à propriedade 'localizationInfo' do manifesto.</span><span class="sxs-lookup"><span data-stu-id="17426-137">These files must adhere to the [Localization file JSON schema](../../resources/schema/localization-schema.md) and they must be added to the 'localizationInfo' property of your manifest.</span></span> <span data-ttu-id="17426-138">Cada arquivo se correlaciona a uma marca de idioma que o cliente Teams usa para escolher as cadeias de caracteres apropriadas.</span><span class="sxs-lookup"><span data-stu-id="17426-138">Each file correlates to a language tag which the Teams client uses to choose the appropriate strings.</span></span> <span data-ttu-id="17426-139">A marca de idioma assume a forma de, mas é recomendável omitir a parte para direcionar todas as regiões que suportam <language> - <region> o <region> idioma desejado.</span><span class="sxs-lookup"><span data-stu-id="17426-139">The language tag takes the form of <language>-<region> but it is recommended to omit the <region> portion to target all regions that support the desired language.</span></span>

<span data-ttu-id="17426-140">O cliente Teams aplicará as cadeias de caracteres nesta ordem: cadeias de caracteres de idioma padrão -> idioma do usuário somente cadeias de caracteres -> idioma do usuário + cadeias de caracteres de região do usuário.</span><span class="sxs-lookup"><span data-stu-id="17426-140">The Teams client will apply the strings in this order: default language strings -> user's language only strings -> user's language + user's region strings.</span></span>

<span data-ttu-id="17426-141">Por exemplo, você fornece um idioma padrão de 'fr' (francês, todas as regiões) e arquivos de idiomas adicionais para 'en' (inglês, todas as regiões) e 'en-gb' (inglês, Grã-Bretanha).</span><span class="sxs-lookup"><span data-stu-id="17426-141">For example, you provide a default language of 'fr' (French, all regions), and additional language files for 'en' (English, all regions) and 'en-gb' (English, Great Britain).</span></span> <span data-ttu-id="17426-142">Se o idioma do usuário estiver definido como 'en-gb':</span><span class="sxs-lookup"><span data-stu-id="17426-142">If the user's language is set to 'en-gb':</span></span>

1. <span data-ttu-id="17426-143">O Teams cliente levará as cadeias de caracteres 'fr' sobrescrever-as com as cadeias de caracteres 'en'.</span><span class="sxs-lookup"><span data-stu-id="17426-143">The Teams client will take the 'fr' strings overwrite them with the 'en' strings.</span></span>
2. <span data-ttu-id="17426-144">Sobrescreva-os com as cadeias de caracteres 'en-gb'.</span><span class="sxs-lookup"><span data-stu-id="17426-144">Overwrite those with the 'en-gb' strings.</span></span>

<span data-ttu-id="17426-145">Se o idioma do usuário estiver definido como 'en-ca':</span><span class="sxs-lookup"><span data-stu-id="17426-145">If the user's language is set to 'en-ca':</span></span> 

1. <span data-ttu-id="17426-146">O Teams cliente levará as cadeias de caracteres 'fr' sobrescrever-as com as cadeias de caracteres 'en'.</span><span class="sxs-lookup"><span data-stu-id="17426-146">The Teams client will take the 'fr' strings overwrite them with the 'en' strings.</span></span>
2. <span data-ttu-id="17426-147">Como nenhuma localização 'en-ca' é fornecida, as localizações 'en' serão usadas.</span><span class="sxs-lookup"><span data-stu-id="17426-147">Since no 'en-ca' localization is supplied, the 'en' localizations will be used.</span></span>

<span data-ttu-id="17426-148">Se o idioma do usuário estiver definido como 'es-es', o cliente Teams aceitará as cadeias de caracteres 'fr' e não as substituirá por nenhum dos arquivos de idioma.</span><span class="sxs-lookup"><span data-stu-id="17426-148">If the user's language is set to 'es-es', the Teams client will take the 'fr' strings and will not override them with any of the language files.</span></span>

<span data-ttu-id="17426-149">Portanto, é altamente recomendável fornecer traduções de nível superior e somente idioma em seu manifesto ('en' em vez de 'en-us') e fornecer apenas substituições no nível da região para as poucas cadeias de caracteres que precisam delas.</span><span class="sxs-lookup"><span data-stu-id="17426-149">Therefore, it is strongly recommended to provide top-level, language-only translations in your manifest ('en' instead of 'en-us') and only provide region-level overrides for the few strings that need them.</span></span>

### <a name="example-manifestjson-change"></a><span data-ttu-id="17426-150">Exemplo manifest.jsna alteração</span><span class="sxs-lookup"><span data-stu-id="17426-150">Example manifest.json change</span></span>

```json
{
  ...
  "localizationInfo": {
    "defaultLanguageTag": "en",
    "additionalLanguages": [
      {
        "languageTag": "en-gb",
        "file": "en-gb.json"
      },
      {
        "languageTag": "fr",
        "file": "fr.json"
      },
      {
        "languageTag": "pl",
        "file": "pl.json"
      }
    ]
  }
  ...
}
```

### <a name="example-localization-json-file"></a><span data-ttu-id="17426-151">Exemplo de arquivo .json de localização</span><span class="sxs-lookup"><span data-stu-id="17426-151">Example localization .json file</span></span>

```json
{
  "$schema": "https://developer.microsoft.com/en-us/json-schemas/teams/v1.8/MicrosoftTeams.Localization.schema.json",
  "name.short": "Le App",
  "name.full": "App pour Microsoft Teams",
  "description.short": "Créez d'excellentes applications pour Microsoft Teams avec App.",
  "description.full": "Créez de nouvelles applications Microsoft Teams, concevez et prévisualisez des cartes bot, et explorez la documentation avec App.",
  "staticTabs[0].name": "Editeur de manifest",
  "staticTabs[1].name": "Editeur de cartes",
  "staticTabs[2].name": "Bibliothèque de contrôles",
  "bots[0].commandLists[0].commands[0].title": "chercher",
  "bots[0].commandLists[0].commands[0].description": "Rechercher la documentation Teams pertinente"
}
```

## <a name="handling-localized-text-submissions-from-your-users"></a><span data-ttu-id="17426-152">Manipulando envios de texto localizados de seus usuários</span><span class="sxs-lookup"><span data-stu-id="17426-152">Handling localized text submissions from your users</span></span>

<span data-ttu-id="17426-153">Se o seu fornecer versões localizadas do aplicativo, é muito provável que os usuários respondam com o mesmo idioma.</span><span class="sxs-lookup"><span data-stu-id="17426-153">If your provide localized versions of your application it is very likely that your users will respond with the same language.</span></span> <span data-ttu-id="17426-154">Teams não converte os envios de usuário de volta para o idioma padrão, portanto, seu aplicativo precisará lidar com isso.</span><span class="sxs-lookup"><span data-stu-id="17426-154">Teams does not translate the user submissions back to the default language, so your app will need to handle that.</span></span> <span data-ttu-id="17426-155">Por exemplo, se você fornecer uma localização , as respostas ao bot serão o texto localizado do comando, não `commandList` o idioma padrão.</span><span class="sxs-lookup"><span data-stu-id="17426-155">For example, if you provide a localized `commandList`, the responses to your bot will be the localized text of the command, not the default language.</span></span> <span data-ttu-id="17426-156">Seu aplicativo precisará responder adequadamente.</span><span class="sxs-lookup"><span data-stu-id="17426-156">Your app will need to respond appropriately.</span></span>

## <a name="code-sample"></a><span data-ttu-id="17426-157">Exemplo de código</span><span class="sxs-lookup"><span data-stu-id="17426-157">Code sample</span></span>

| <span data-ttu-id="17426-158">Exemplo de nome</span><span class="sxs-lookup"><span data-stu-id="17426-158">Sample name</span></span> | <span data-ttu-id="17426-159">Descrição</span><span class="sxs-lookup"><span data-stu-id="17426-159">Description</span></span> | <span data-ttu-id="17426-160">.NET</span><span class="sxs-lookup"><span data-stu-id="17426-160">.NET</span></span> | <span data-ttu-id="17426-161">Node.js</span><span class="sxs-lookup"><span data-stu-id="17426-161">Node.js</span></span> |
|-------------|-------------|------|------|
| <span data-ttu-id="17426-162">Localização de aplicativos</span><span class="sxs-lookup"><span data-stu-id="17426-162">App Localization</span></span> | <span data-ttu-id="17426-163">Microsoft Teams localização de aplicativo usando bot e guia.</span><span class="sxs-lookup"><span data-stu-id="17426-163">Microsoft Teams app localization using bot and tab.</span></span> | [<span data-ttu-id="17426-164">View</span><span class="sxs-lookup"><span data-stu-id="17426-164">View</span></span>](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/app-localization/csharp) |[<span data-ttu-id="17426-165">View</span><span class="sxs-lookup"><span data-stu-id="17426-165">View</span></span>](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/app-localization/nodejs) |


