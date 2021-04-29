---
title: Localização para seu aplicativo
description: Descreve considerações para a localização do aplicativo do Microsoft Teams.
ms.topic: conceptual
localization_priority: Normal
keywords: teams publish store office publishing AppSource localization language
ms.date: 05/15/2018
ms.openlocfilehash: 6c63bd5c71934d0a3342b31bc10feda38b8ae0d1
ms.sourcegitcommit: d90c5dafea09e2893dea8da46ee49516bbaa04b0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2021
ms.locfileid: "52075742"
---
# <a name="localization-for-microsoft-teams-apps"></a><span data-ttu-id="f9fc6-104">Localização para aplicativos do Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="f9fc6-104">Localization for Microsoft Teams apps</span></span>

<span data-ttu-id="f9fc6-105">Ao localização do seu aplicativo do Microsoft Teams, há três áreas principais que você precisa considerar.</span><span class="sxs-lookup"><span data-stu-id="f9fc6-105">When localizing your Microsoft Teams app there are three major areas you need to consider.</span></span>

1. <span data-ttu-id="f9fc6-106">Sua listagem appSource (se você estiver publicando na loja de aplicativos).</span><span class="sxs-lookup"><span data-stu-id="f9fc6-106">Your AppSource listing (if you're publishing to the app store).</span></span>
1. <span data-ttu-id="f9fc6-107">As cadeias de caracteres voltadas para o usuário final no manifesto do aplicativo (por exemplo, comandos de bot).</span><span class="sxs-lookup"><span data-stu-id="f9fc6-107">The end-user facing strings in your app manifest (for example bot commands).</span></span>
1. <span data-ttu-id="f9fc6-108">Respondendo ao texto localizado enviado de seus usuários.</span><span class="sxs-lookup"><span data-stu-id="f9fc6-108">Responding to localized text submitted from your users.</span></span>

## <a name="localizing-your-appsource-listing"></a><span data-ttu-id="f9fc6-109">Localizando sua listagem do AppSource</span><span class="sxs-lookup"><span data-stu-id="f9fc6-109">Localizing your AppSource listing</span></span>

<span data-ttu-id="f9fc6-110">Se você estiver publicando na loja de aplicativos, você precisa estar ciente de que ainda não há suporte para a localização da listagem do AppSource.</span><span class="sxs-lookup"><span data-stu-id="f9fc6-110">If you're publishing to the app store, you need to be aware that localizing your AppSource listing is not yet supported.</span></span> <span data-ttu-id="f9fc6-111">No entanto, em preparação para suporte para listagens localizadas na loja de aplicativos, você pode adicionar idiomas adicionais à sua listagem.</span><span class="sxs-lookup"><span data-stu-id="f9fc6-111">However, in preparation for support for localized listings in the app store you can add additional languages to your listing.</span></span> <span data-ttu-id="f9fc6-112">Atualmente, apenas as informações de idioma padrão (inglês) fornecidas no [Partner Center](/office/dev/store/submit-to-appsource-via-partner-center) para sua listagem serão exibidas na listagem de site do [AppSource](https://appsource.microsoft.com/marketplace/apps?product=office%3Bteams&page=1) para seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="f9fc6-112">Currently only the default (English) language information you provide in [Partner Center](/office/dev/store/submit-to-appsource-via-partner-center) for your listing will appear in the [AppSource website](https://appsource.microsoft.com/marketplace/apps?product=office%3Bteams&page=1) listing for your app.</span></span>

<span data-ttu-id="f9fc6-113">Para configurar um idioma adicional para seu aplicativo, no [Partner Center,](/office/dev/store/submit-to-appsource-via-partner-center)selecione inglês e o idioma adicional do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="f9fc6-113">To configure an additional language for your app, in [Partner Center](/office/dev/store/submit-to-appsource-via-partner-center), select both English and the additional language of the app.</span></span> <span data-ttu-id="f9fc6-114">O francês é usado neste exemplo.</span><span class="sxs-lookup"><span data-stu-id="f9fc6-114">French is used in this example.</span></span>

1. <span data-ttu-id="f9fc6-115">Adicionar idioma inglês</span><span class="sxs-lookup"><span data-stu-id="f9fc6-115">Add English language</span></span>
    * <span data-ttu-id="f9fc6-116">Preencha o nome do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="f9fc6-116">Fill in the app name.</span></span>
    * <span data-ttu-id="f9fc6-117">Preencha uma breve descrição do aplicativo em inglês.</span><span class="sxs-lookup"><span data-stu-id="f9fc6-117">Fill in a short description of the app in English.</span></span>
    * <span data-ttu-id="f9fc6-118">Preencha a longa descrição do aplicativo em inglês.</span><span class="sxs-lookup"><span data-stu-id="f9fc6-118">Fill in the long description of the app in English.</span></span>
    * <span data-ttu-id="f9fc6-119">Na descrição longa, adicione também a linha "Este aplicativo está disponível em "francês".</span><span class="sxs-lookup"><span data-stu-id="f9fc6-119">In the long description, please also add the line “This app is available in “French”.</span></span>
    * <span data-ttu-id="f9fc6-120">Carregue as imagens da interface do usuário do aplicativo (em inglês).</span><span class="sxs-lookup"><span data-stu-id="f9fc6-120">Upload the images of your app UI (in English).</span></span>
2. <span data-ttu-id="f9fc6-121">Adicionar idioma francês</span><span class="sxs-lookup"><span data-stu-id="f9fc6-121">Add French language</span></span>
    * <span data-ttu-id="f9fc6-122">Preencha o nome do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="f9fc6-122">Fill in the app name.</span></span>
    * <span data-ttu-id="f9fc6-123">Preencha uma breve descrição do aplicativo em francês.</span><span class="sxs-lookup"><span data-stu-id="f9fc6-123">Fill in a short description of the app in French.</span></span>
    * <span data-ttu-id="f9fc6-124">Preencha a longa descrição do aplicativo em francês.</span><span class="sxs-lookup"><span data-stu-id="f9fc6-124">Fill in the long description of the app in French.</span></span>
    * <span data-ttu-id="f9fc6-125">Carregue as imagens da interface do usuário do aplicativo (em francês).</span><span class="sxs-lookup"><span data-stu-id="f9fc6-125">Upload the images of your app UI (in French).</span></span>

<span data-ttu-id="f9fc6-126">As imagens carregadas com o idioma inglês serão as usadas no AppSource.</span><span class="sxs-lookup"><span data-stu-id="f9fc6-126">The images you upload with the English language will be the ones used in AppSource.</span></span>

## <a name="localizing-the-strings-in-your-app-manifest"></a><span data-ttu-id="f9fc6-127">Localizando as cadeias de caracteres no manifesto do aplicativo</span><span class="sxs-lookup"><span data-stu-id="f9fc6-127">Localizing the strings in your app manifest</span></span>

<span data-ttu-id="f9fc6-128">Você deve usar o esquema de aplicativo do Microsoft Teams v1.5+ para localização adequada do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="f9fc6-128">You must use the Microsoft Teams app schema v1.5+ to properly localize your app.</span></span> <span data-ttu-id="f9fc6-129">Você pode fazer isso definindo o atributo em seu arquivo manifest.json como ' ' e atualizando a `$schema` https://developer.microsoft.com/en-us/json-schemas/teams/v1.8/MicrosoftTeams.Localization.schema.json propriedade 'manifestVersion' como '1.7'.</span><span class="sxs-lookup"><span data-stu-id="f9fc6-129">You can do this by setting the `$schema` attribute in your manifest.json file to 'https://developer.microsoft.com/en-us/json-schemas/teams/v1.8/MicrosoftTeams.Localization.schema.json' and updating the 'manifestVersion' property to '1.7'.</span></span>

### <a name="example-manifestjson-change"></a><span data-ttu-id="f9fc6-130">Exemplo manifest.jsna alteração</span><span class="sxs-lookup"><span data-stu-id="f9fc6-130">Example manifest.json change</span></span>

```json
{
  "$schema": "https://developer.microsoft.com/en-us/json-schemas/teams/v1.8/MicrosoftTeams.Localization.schema.json",
  "manifestVersion": "1.5",
  ...
}
```

<span data-ttu-id="f9fc6-131">Em seguida, você deseja adicionar a propriedade 'localizationInfo' com o idioma padrão que o aplicativo oferece suporte.</span><span class="sxs-lookup"><span data-stu-id="f9fc6-131">You will then want to add the 'localizationInfo' property with the default language that your application supports.</span></span> <span data-ttu-id="f9fc6-132">O idioma padrão é usado como o idioma de fallback final se as configurações do cliente do usuário não corresponderem a nenhum dos idiomas adicionais.</span><span class="sxs-lookup"><span data-stu-id="f9fc6-132">The default language is used as the final fallback language if the user's client settings do not match any of your additional languages.</span></span>

### <a name="example-manifestjson-change"></a><span data-ttu-id="f9fc6-133">Exemplo manifest.jsna alteração</span><span class="sxs-lookup"><span data-stu-id="f9fc6-133">Example manifest.json change</span></span>

```json
{
  ...
  "localizationInfo": {
    "defaultLanguageTag": "en"
  }
  ...
}
```

<span data-ttu-id="f9fc6-134">Você pode fornecer arquivos .json adicionais com traduções de todas as cadeias de caracteres voltadas para o usuário em seu manifesto.</span><span class="sxs-lookup"><span data-stu-id="f9fc6-134">You can provide additional .json files with translations of all the user facing strings in your manifest.</span></span> <span data-ttu-id="f9fc6-135">Esses arquivos devem aderir ao esquema [JSON](../../resources/schema/localization-schema.md) do arquivo de localização e devem ser adicionados à propriedade 'localizationInfo' do manifesto.</span><span class="sxs-lookup"><span data-stu-id="f9fc6-135">These files must adhere to the [Localization file JSON schema](../../resources/schema/localization-schema.md) and they must be added to the 'localizationInfo' property of your manifest.</span></span> <span data-ttu-id="f9fc6-136">Cada arquivo se correlaciona a uma marca de idioma que o cliente teams usa para escolher as cadeias de caracteres apropriadas.</span><span class="sxs-lookup"><span data-stu-id="f9fc6-136">Each file correlates to a language tag which the Teams client uses to choose the appropriate strings.</span></span> <span data-ttu-id="f9fc6-137">A marca de idioma assume a forma de, mas é recomendável omitir a parte para direcionar todas as regiões que suportam <language> - <region> o <region> idioma desejado.</span><span class="sxs-lookup"><span data-stu-id="f9fc6-137">The language tag takes the form of <language>-<region> but it is recommended to omit the <region> portion to target all regions that support the desired language.</span></span>

<span data-ttu-id="f9fc6-138">O cliente do Teams aplicará as cadeias de caracteres nesta ordem: cadeias de caracteres de idioma padrão -> idioma do usuário somente cadeias de caracteres -> idioma do usuário + cadeias de caracteres de região do usuário.</span><span class="sxs-lookup"><span data-stu-id="f9fc6-138">The Teams client will apply the strings in this order: default language strings -> user's language only strings -> user's language + user's region strings.</span></span>

<span data-ttu-id="f9fc6-139">Por exemplo, você fornece um idioma padrão de 'fr' (francês, todas as regiões) e arquivos de idiomas adicionais para 'en' (inglês, todas as regiões) e 'en-gb' (inglês, Grã-Bretanha).</span><span class="sxs-lookup"><span data-stu-id="f9fc6-139">For example, you provide a default language of 'fr' (French, all regions), and additional language files for 'en' (English, all regions) and 'en-gb' (English, Great Britain).</span></span> <span data-ttu-id="f9fc6-140">Se o idioma do usuário estiver definido como 'en-gb':</span><span class="sxs-lookup"><span data-stu-id="f9fc6-140">If the user's language is set to 'en-gb':</span></span>

1. <span data-ttu-id="f9fc6-141">O cliente do Teams assumirá as cadeias de caracteres 'fr' sobrescreve-as com as cadeias de caracteres 'en'.</span><span class="sxs-lookup"><span data-stu-id="f9fc6-141">The Teams client will take the 'fr' strings overwrite them with the 'en' strings.</span></span>
2. <span data-ttu-id="f9fc6-142">Sobrescreva-os com as cadeias de caracteres 'en-gb'.</span><span class="sxs-lookup"><span data-stu-id="f9fc6-142">Overwrite those with the 'en-gb' strings.</span></span>

<span data-ttu-id="f9fc6-143">Se o idioma do usuário estiver definido como 'en-ca':</span><span class="sxs-lookup"><span data-stu-id="f9fc6-143">If the user's language is set to 'en-ca':</span></span> 

1. <span data-ttu-id="f9fc6-144">O cliente do Teams assumirá as cadeias de caracteres 'fr' sobrescreve-as com as cadeias de caracteres 'en'.</span><span class="sxs-lookup"><span data-stu-id="f9fc6-144">The Teams client will take the 'fr' strings overwrite them with the 'en' strings.</span></span>
2. <span data-ttu-id="f9fc6-145">Como nenhuma localização 'en-ca' é fornecida, as localizações 'en' serão usadas.</span><span class="sxs-lookup"><span data-stu-id="f9fc6-145">Since no 'en-ca' localization is supplied, the 'en' localizations will be used.</span></span>

<span data-ttu-id="f9fc6-146">Se o idioma do usuário estiver definido como 'es-es', o cliente do Teams assumirá as cadeias de caracteres 'fr' e não as substituirá por nenhum dos arquivos de idioma.</span><span class="sxs-lookup"><span data-stu-id="f9fc6-146">If the user's language is set to 'es-es', the Teams client will take the 'fr' strings and will not override them with any of the language files.</span></span>

<span data-ttu-id="f9fc6-147">Portanto, é altamente recomendável fornecer traduções de nível superior e somente idioma em seu manifesto ('en' em vez de 'en-us') e fornecer apenas substituições no nível da região para as poucas cadeias de caracteres que precisam delas.</span><span class="sxs-lookup"><span data-stu-id="f9fc6-147">Therefore, it is strongly recommended to provide top-level, language-only translations in your manifest ('en' instead of 'en-us') and only provide region-level overrides for the few strings that need them.</span></span>

### <a name="example-manifestjson-change"></a><span data-ttu-id="f9fc6-148">Exemplo manifest.jsna alteração</span><span class="sxs-lookup"><span data-stu-id="f9fc6-148">Example manifest.json change</span></span>

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

### <a name="example-localization-json-file"></a><span data-ttu-id="f9fc6-149">Exemplo de arquivo .json de localização</span><span class="sxs-lookup"><span data-stu-id="f9fc6-149">Example localization .json file</span></span>

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

## <a name="handling-localized-text-submissions-from-your-users"></a><span data-ttu-id="f9fc6-150">Manipulando envios de texto localizados de seus usuários</span><span class="sxs-lookup"><span data-stu-id="f9fc6-150">Handling localized text submissions from your users</span></span>

<span data-ttu-id="f9fc6-151">Se o seu fornecer versões localizadas do aplicativo, é muito provável que os usuários respondam com o mesmo idioma.</span><span class="sxs-lookup"><span data-stu-id="f9fc6-151">If your provide localized versions of your application it is very likely that your users will respond with the same language.</span></span> <span data-ttu-id="f9fc6-152">O Teams não converte os envios de usuário de volta para o idioma padrão, portanto, seu aplicativo precisará lidar com isso.</span><span class="sxs-lookup"><span data-stu-id="f9fc6-152">Teams does not translate the user submissions back to the default language, so your app will need to handle that.</span></span> <span data-ttu-id="f9fc6-153">Por exemplo, se você fornecer uma localização , as respostas ao bot serão o texto localizado do comando, não `commandList` o idioma padrão.</span><span class="sxs-lookup"><span data-stu-id="f9fc6-153">For example, if you provide a localized `commandList`, the responses to your bot will be the localized text of the command, not the default language.</span></span> <span data-ttu-id="f9fc6-154">Seu aplicativo precisará responder adequadamente.</span><span class="sxs-lookup"><span data-stu-id="f9fc6-154">Your app will need to respond appropriately.</span></span>

## <a name="code-sample"></a><span data-ttu-id="f9fc6-155">Exemplo de código</span><span class="sxs-lookup"><span data-stu-id="f9fc6-155">Code sample</span></span>

| <span data-ttu-id="f9fc6-156">Exemplo de nome</span><span class="sxs-lookup"><span data-stu-id="f9fc6-156">Sample name</span></span> | <span data-ttu-id="f9fc6-157">Descrição</span><span class="sxs-lookup"><span data-stu-id="f9fc6-157">Description</span></span> | <span data-ttu-id="f9fc6-158">.NET</span><span class="sxs-lookup"><span data-stu-id="f9fc6-158">.NET</span></span> |
|-------------|-------------|------|
| <span data-ttu-id="f9fc6-159">Localização de aplicativos</span><span class="sxs-lookup"><span data-stu-id="f9fc6-159">App Localization</span></span> | <span data-ttu-id="f9fc6-160">Localização de aplicativos do Microsoft Teams usando bot e guia.</span><span class="sxs-lookup"><span data-stu-id="f9fc6-160">Microsoft Teams app localization using bot and tab.</span></span> | [<span data-ttu-id="f9fc6-161">View</span><span class="sxs-lookup"><span data-stu-id="f9fc6-161">View</span></span>](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/app-localization/csharp) |


