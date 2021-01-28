---
title: Localização para seu aplicativo
description: Descreve considerações para a localização do aplicativo Microsoft Teams.
ms.topic: conceptual
keywords: teams publish store office publishing AppSource localization language
ms.date: 05/15/2018
ms.openlocfilehash: 69bee0ee11238dc0e461e4fddf8ed01f0cfcccde
ms.sourcegitcommit: 976e870cc925f61b76c3830ec04ba6e4bdfde32f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/27/2021
ms.locfileid: "50014296"
---
# <a name="localization-for-microsoft-teams-apps"></a><span data-ttu-id="d3c1e-104">Localização de aplicativos do Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="d3c1e-104">Localization for Microsoft Teams apps</span></span>

<span data-ttu-id="d3c1e-105">Ao localização do aplicativo Microsoft Teams, há três áreas principais que você precisa considerar.</span><span class="sxs-lookup"><span data-stu-id="d3c1e-105">When localizing your Microsoft Teams app there are three major areas you need to consider.</span></span>

1. <span data-ttu-id="d3c1e-106">Listagem do AppSource (se você estiver publicando na loja de aplicativos).</span><span class="sxs-lookup"><span data-stu-id="d3c1e-106">Your AppSource listing (if you're publishing to the app store).</span></span>
1. <span data-ttu-id="d3c1e-107">As cadeias de caracteres voltadas para o usuário final no manifesto do aplicativo (por exemplo, comandos de bot).</span><span class="sxs-lookup"><span data-stu-id="d3c1e-107">The end-user facing strings in your app manifest (for example bot commands).</span></span>
1. <span data-ttu-id="d3c1e-108">Responder ao texto localizado enviado por seus usuários.</span><span class="sxs-lookup"><span data-stu-id="d3c1e-108">Responding to localized text submitted from your users.</span></span>

## <a name="localizing-your-appsource-listing"></a><span data-ttu-id="d3c1e-109">Localizando sua listagem do AppSource</span><span class="sxs-lookup"><span data-stu-id="d3c1e-109">Localizing your AppSource listing</span></span>

<span data-ttu-id="d3c1e-110">Se estiver publicando na loja de aplicativos, você precisa estar ciente de que a localização da listagem do AppSource ainda não é suportada.</span><span class="sxs-lookup"><span data-stu-id="d3c1e-110">If you're publishing to the app store, you need to be aware that localizing your AppSource listing is not yet supported.</span></span> <span data-ttu-id="d3c1e-111">No entanto, em preparação para suporte para listagens localizadas na loja de aplicativos, você pode adicionar idiomas adicionais à sua listagem.</span><span class="sxs-lookup"><span data-stu-id="d3c1e-111">However, in preparation for support for localized listings in the app store you can add additional languages to your listing.</span></span> <span data-ttu-id="d3c1e-112">Atualmente, apenas as informações de idioma padrão (inglês) fornecidas no [Partner Center](/office/dev/store/submit-to-appsource-via-partner-center) para sua listagem serão exibidas na listagem de site do [AppSource](https://appsource.microsoft.com/marketplace/apps?product=office%3Bteams&page=1) para seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="d3c1e-112">Currently only the default (English) language information you provide in [Partner Center](/office/dev/store/submit-to-appsource-via-partner-center) for your listing will appear in the [AppSource website](https://appsource.microsoft.com/marketplace/apps?product=office%3Bteams&page=1) listing for your app.</span></span>

<span data-ttu-id="d3c1e-113">Para configurar um idioma adicional para seu aplicativo, no [Partner Center,](/office/dev/store/submit-to-appsource-via-partner-center)selecione inglês e o idioma adicional do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="d3c1e-113">To configure an additional language for your app, in [Partner Center](/office/dev/store/submit-to-appsource-via-partner-center), select both English and the additional language of the app.</span></span> <span data-ttu-id="d3c1e-114">O francês é usado neste exemplo.</span><span class="sxs-lookup"><span data-stu-id="d3c1e-114">French is used in this example.</span></span>

1. <span data-ttu-id="d3c1e-115">Adicionar idioma inglês</span><span class="sxs-lookup"><span data-stu-id="d3c1e-115">Add English language</span></span>
    * <span data-ttu-id="d3c1e-116">Preencha o nome do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="d3c1e-116">Fill in the app name.</span></span>
    * <span data-ttu-id="d3c1e-117">Preencha uma breve descrição do aplicativo em inglês.</span><span class="sxs-lookup"><span data-stu-id="d3c1e-117">Fill in a short description of the app in English.</span></span>
    * <span data-ttu-id="d3c1e-118">Preencha a descrição longa do aplicativo em inglês.</span><span class="sxs-lookup"><span data-stu-id="d3c1e-118">Fill in the long description of the app in English.</span></span>
    * <span data-ttu-id="d3c1e-119">Na descrição longa, adicione também a linha "Este aplicativo está disponível em "Francês".</span><span class="sxs-lookup"><span data-stu-id="d3c1e-119">In the long description, please also add the line “This app is available in “French”.</span></span>
    * <span data-ttu-id="d3c1e-120">Carregue as imagens da interface do usuário do seu aplicativo (em inglês).</span><span class="sxs-lookup"><span data-stu-id="d3c1e-120">Upload the images of your app UI (in English).</span></span>
2. <span data-ttu-id="d3c1e-121">Adicionar idioma francês</span><span class="sxs-lookup"><span data-stu-id="d3c1e-121">Add French language</span></span>
    * <span data-ttu-id="d3c1e-122">Preencha o nome do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="d3c1e-122">Fill in the app name.</span></span>
    * <span data-ttu-id="d3c1e-123">Preencha uma breve descrição do aplicativo em francês.</span><span class="sxs-lookup"><span data-stu-id="d3c1e-123">Fill in a short description of the app in French.</span></span>
    * <span data-ttu-id="d3c1e-124">Preencha a descrição longa do aplicativo em francês.</span><span class="sxs-lookup"><span data-stu-id="d3c1e-124">Fill in the long description of the app in French.</span></span>
    * <span data-ttu-id="d3c1e-125">Carregue as imagens da interface do usuário do seu aplicativo (em francês).</span><span class="sxs-lookup"><span data-stu-id="d3c1e-125">Upload the images of your app UI (in French).</span></span>

<span data-ttu-id="d3c1e-126">As imagens carregadas com o idioma inglês serão as usadas no AppSource.</span><span class="sxs-lookup"><span data-stu-id="d3c1e-126">The images you upload with the English language will be the ones used in AppSource.</span></span>

## <a name="localizing-the-strings-in-your-app-manifest"></a><span data-ttu-id="d3c1e-127">Localizando as cadeias de caracteres no manifesto do aplicativo</span><span class="sxs-lookup"><span data-stu-id="d3c1e-127">Localizing the strings in your app manifest</span></span>

<span data-ttu-id="d3c1e-128">Você deve usar o esquema de aplicativo do Microsoft Teams v1.5+ para localizado corretamente seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="d3c1e-128">You must use the Microsoft Teams app schema v1.5+ to properly localize your app.</span></span> <span data-ttu-id="d3c1e-129">Você pode fazer isso definindo o atributo no arquivo manifest.json como ' ' e atualizando a propriedade `$schema` https://developer.microsoft.com/en-us/json-schemas/teams/v1.8/MicrosoftTeams.Localization.schema.json 'manifestVersion' para '1.7'.</span><span class="sxs-lookup"><span data-stu-id="d3c1e-129">You can do this by setting the `$schema` attribute in your manifest.json file to 'https://developer.microsoft.com/en-us/json-schemas/teams/v1.8/MicrosoftTeams.Localization.schema.json' and updating the 'manifestVersion' property to '1.7'.</span></span>

### <a name="example-manifestjson-change"></a><span data-ttu-id="d3c1e-130">Exemplo manifest.jsna alteração</span><span class="sxs-lookup"><span data-stu-id="d3c1e-130">Example manifest.json change</span></span>

```json
{
  "$schema": "https://developer.microsoft.com/en-us/json-schemas/teams/v1.8/MicrosoftTeams.Localization.schema.json",
  "manifestVersion": "1.5",
  ...
}
```

<span data-ttu-id="d3c1e-131">Em seguida, você vai querer adicionar a propriedade 'localizationInfo' com o idioma padrão compatível com seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="d3c1e-131">You will then want to add the 'localizationInfo' property with the default language that your application supports.</span></span> <span data-ttu-id="d3c1e-132">O idioma padrão será usado como o idioma de fallback final se as configurações de cliente do usuário não corresponderem a nenhum dos idiomas adicionais.</span><span class="sxs-lookup"><span data-stu-id="d3c1e-132">The default language is used as the final fallback language if the user's client settings do not match any of your additional languages.</span></span>

### <a name="example-manifestjson-change"></a><span data-ttu-id="d3c1e-133">Exemplo manifest.jsna alteração</span><span class="sxs-lookup"><span data-stu-id="d3c1e-133">Example manifest.json change</span></span>

```json
{
  ...
  "localizationInfo": {
    "defaultLanguageTag": "en"
  }
  ...
}
```

<span data-ttu-id="d3c1e-134">Você pode fornecer arquivos .json adicionais com traduções de todas as cadeias de caracteres voltadas para o usuário em seu manifesto.</span><span class="sxs-lookup"><span data-stu-id="d3c1e-134">You can provide additional .json files with translations of all the user facing strings in your manifest.</span></span> <span data-ttu-id="d3c1e-135">Esses arquivos devem aderir ao esquema [JSON](../../resources/schema/localization-schema.md) do arquivo de localização e devem ser adicionados à propriedade 'localizationInfo' do manifesto.</span><span class="sxs-lookup"><span data-stu-id="d3c1e-135">These files must adhere to the [Localization file JSON schema](../../resources/schema/localization-schema.md) and they must be added to the 'localizationInfo' property of your manifest.</span></span> <span data-ttu-id="d3c1e-136">Cada arquivo se correlaciona a uma marca de idioma que o cliente do Teams usa para escolher as cadeias de caracteres apropriadas.</span><span class="sxs-lookup"><span data-stu-id="d3c1e-136">Each file correlates to a language tag which the Teams client uses to choose the appropriate strings.</span></span> <span data-ttu-id="d3c1e-137">A marca de idioma tem a forma, mas é recomendável omitir a parte para todas as regiões que suportam <language> - <region> o <region> idioma desejado.</span><span class="sxs-lookup"><span data-stu-id="d3c1e-137">The language tag takes the form of <language>-<region> but it is recommended to omit the <region> portion to target all regions that support the desired language.</span></span>

<span data-ttu-id="d3c1e-138">O cliente do Teams aplicará as cadeias de caracteres nesta ordem: cadeias de caracteres de idioma padrão -> cadeias de caracteres somente de idioma do usuário -> idioma do usuário + cadeias de caracteres de região do usuário.</span><span class="sxs-lookup"><span data-stu-id="d3c1e-138">The Teams client will apply the strings in this order: default language strings -> user's language only strings -> user's language + user's region strings.</span></span>

<span data-ttu-id="d3c1e-139">Por exemplo, você fornece um idioma padrão "fr" (francês, todas as regiões) e arquivos de idioma adicionais para 'en' (inglês, todas as regiões) e 'en-gb' (inglês, Great Britain).</span><span class="sxs-lookup"><span data-stu-id="d3c1e-139">For example, you provide a default language of 'fr' (French, all regions), and additional language files for 'en' (English, all regions) and 'en-gb' (English, Great Britain).</span></span> <span data-ttu-id="d3c1e-140">Se o idioma do usuário estiver definido como 'en-gb':</span><span class="sxs-lookup"><span data-stu-id="d3c1e-140">If the user's language is set to 'en-gb':</span></span>

1. <span data-ttu-id="d3c1e-141">O cliente do Teams assumirá as cadeias de caracteres "fr" que as substituirão pelas cadeias de caracteres "en".</span><span class="sxs-lookup"><span data-stu-id="d3c1e-141">The Teams client will take the 'fr' strings overwrite them with the 'en' strings.</span></span>
2. <span data-ttu-id="d3c1e-142">Sobrescreva-os com as cadeias de caracteres 'en-gb'.</span><span class="sxs-lookup"><span data-stu-id="d3c1e-142">Overwrite those with the 'en-gb' strings.</span></span>

<span data-ttu-id="d3c1e-143">Se o idioma do usuário estiver definido como 'en-ca':</span><span class="sxs-lookup"><span data-stu-id="d3c1e-143">If the user's language is set to 'en-ca':</span></span> 

1. <span data-ttu-id="d3c1e-144">O cliente do Teams assumirá as cadeias de caracteres "fr" que as substituirão pelas cadeias de caracteres "en".</span><span class="sxs-lookup"><span data-stu-id="d3c1e-144">The Teams client will take the 'fr' strings overwrite them with the 'en' strings.</span></span>
2. <span data-ttu-id="d3c1e-145">Como nenhuma localização 'en-ca' é fornecida, as localizações 'en' serão usadas.</span><span class="sxs-lookup"><span data-stu-id="d3c1e-145">Since no 'en-ca' localization is supplied, the 'en' localizations will be used.</span></span>

<span data-ttu-id="d3c1e-146">Se o idioma do usuário estiver definido como "es-es", o cliente do Teams pegará as cadeias de caracteres 'fr' e não as substituirá por nenhum dos arquivos de idioma.</span><span class="sxs-lookup"><span data-stu-id="d3c1e-146">If the user's language is set to 'es-es', the Teams client will take the 'fr' strings and will not override them with any of the language files.</span></span>

<span data-ttu-id="d3c1e-147">Portanto, é altamente recomendável fornecer traduções de nível superior somente de idioma em seu manifesto ('en' em vez de 'en-us') e fornecer apenas substituições de nível de região para as poucas cadeias de caracteres que precisam delas.</span><span class="sxs-lookup"><span data-stu-id="d3c1e-147">Therefore, it is strongly recommended to provide top-level, language-only translations in your manifest ('en' instead of 'en-us') and only provide region-level overrides for the few strings that need them.</span></span>

### <a name="example-manifestjson-change"></a><span data-ttu-id="d3c1e-148">Exemplo manifest.jsna alteração</span><span class="sxs-lookup"><span data-stu-id="d3c1e-148">Example manifest.json change</span></span>

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

### <a name="example-localization-json-file"></a><span data-ttu-id="d3c1e-149">Exemplo de arquivo .json de localização</span><span class="sxs-lookup"><span data-stu-id="d3c1e-149">Example localization .json file</span></span>

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

## <a name="handling-localized-text-submissions-from-your-users"></a><span data-ttu-id="d3c1e-150">Manipulando envios de texto localizados de seus usuários</span><span class="sxs-lookup"><span data-stu-id="d3c1e-150">Handling localized text submissions from your users</span></span>

<span data-ttu-id="d3c1e-151">Se você fornecer versões localizadas do seu aplicativo, é muito provável que os usuários respondam com o mesmo idioma.</span><span class="sxs-lookup"><span data-stu-id="d3c1e-151">If your provide localized versions of your application it is very likely that your users will respond with the same language.</span></span> <span data-ttu-id="d3c1e-152">O Teams não traduz os envios de usuário de volta para o idioma padrão, portanto, seu aplicativo precisará lidar com isso.</span><span class="sxs-lookup"><span data-stu-id="d3c1e-152">Teams does not translate the user submissions back to the default language, so your app will need to handle that.</span></span> <span data-ttu-id="d3c1e-153">Por exemplo, se você fornecer uma localização , as respostas ao seu bot serão o texto localizado do comando, não `commandList` o idioma padrão.</span><span class="sxs-lookup"><span data-stu-id="d3c1e-153">For example, if you provide a localized `commandList`, the responses to your bot will be the localized text of the command, not the default language.</span></span> <span data-ttu-id="d3c1e-154">Seu aplicativo precisará responder adequadamente.</span><span class="sxs-lookup"><span data-stu-id="d3c1e-154">Your app will need to respond appropriately.</span></span>
