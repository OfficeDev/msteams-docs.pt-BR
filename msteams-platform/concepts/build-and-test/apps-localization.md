---
title: Localização para aplicativos da equipe
description: Descreve problemas em relação à localização do aplicativo
keywords: publicação do Microsoft Teams armazenar o idioma de localização do Office Publishing AppSource
ms.date: 05/15/2018
ms.openlocfilehash: c7d8ff47d370badcc75e3ad5d10a2ca298b80195
ms.sourcegitcommit: 058b7bbd817af5f513e0e018f2ef562dc3086a84
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/03/2020
ms.locfileid: "43120274"
---
# <a name="localization-for-microsoft-teams-apps"></a><span data-ttu-id="493b7-104">Localização para aplicativos do Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="493b7-104">Localization for Microsoft Teams apps</span></span>

<span data-ttu-id="493b7-105">Ao localizar seu aplicativo do Microsoft Teams, há três áreas principais que você precisa considerar.</span><span class="sxs-lookup"><span data-stu-id="493b7-105">When localizing your Microsoft Teams app there are three major areas you need to consider.</span></span>

1. <span data-ttu-id="493b7-106">Sua listagem de AppSource (se você estiver publicando na loja de aplicativos).</span><span class="sxs-lookup"><span data-stu-id="493b7-106">Your AppSource listing (if you're publishing to the app store).</span></span>
1. <span data-ttu-id="493b7-107">As cadeias de caracteres voltadas para o usuário final em seu manifesto de aplicativo (por exemplo, comandos de bot).</span><span class="sxs-lookup"><span data-stu-id="493b7-107">The end-user facing strings in your app manifest (for example bot commands).</span></span>
1. <span data-ttu-id="493b7-108">Responder ao texto localizado enviado de seus usuários.</span><span class="sxs-lookup"><span data-stu-id="493b7-108">Responding to localized text submitted from your users.</span></span>

## <a name="localizing-your-appsource-listing"></a><span data-ttu-id="493b7-109">Localizando sua listagem do AppSource</span><span class="sxs-lookup"><span data-stu-id="493b7-109">Localizing your AppSource listing</span></span>

<span data-ttu-id="493b7-110">Se você estiver publicando na loja de aplicativos, precisará estar ciente de que não há suporte para localizar sua listagem de AppSource ainda.</span><span class="sxs-lookup"><span data-stu-id="493b7-110">If you're publishing to the app store, you need to be aware that localizing your AppSource listing is not yet supported.</span></span> <span data-ttu-id="493b7-111">No entanto, em preparação para suporte para listagens localizadas na loja de aplicativos, você pode adicionar outros idiomas à sua listagem.</span><span class="sxs-lookup"><span data-stu-id="493b7-111">However, in preparation for support for localized listings in the app store you can add additional languages to your listing.</span></span> <span data-ttu-id="493b7-112">Atualmente, apenas as informações de idioma padrão (inglês) fornecidas no [Partner Center](/dev/store/use-partner-center-to-submit-to-appsource) para sua listagem aparecerão na lista de [sites do AppSource](https://appsource.microsoft.com/marketplace/apps?product=office%3Bteams&page=1) para o seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="493b7-112">Currently only the default (English) language information you provide in [Partner Center](/dev/store/use-partner-center-to-submit-to-appsource) for your listing will appear in the [AppSource website](https://appsource.microsoft.com/marketplace/apps?product=office%3Bteams&page=1) listing for your app.</span></span>

<span data-ttu-id="493b7-113">Para configurar um idioma adicional para seu aplicativo, no [centro de parceria](/dev/store/use-partner-center-to-submit-to-appsource), selecione tanto o inglês quanto o idioma adicional do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="493b7-113">To configure an additional language for your app, in [Partner Center](/dev/store/use-partner-center-to-submit-to-appsource), select both English and the additional language of the app.</span></span> <span data-ttu-id="493b7-114">Francês é usado neste exemplo.</span><span class="sxs-lookup"><span data-stu-id="493b7-114">French is used in this example.</span></span>

1. <span data-ttu-id="493b7-115">Adicionar idioma inglês</span><span class="sxs-lookup"><span data-stu-id="493b7-115">Add English language</span></span>
    * <span data-ttu-id="493b7-116">Preencha o nome do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="493b7-116">Fill in the app name.</span></span>
    * <span data-ttu-id="493b7-117">Preencha uma breve descrição do aplicativo em inglês.</span><span class="sxs-lookup"><span data-stu-id="493b7-117">Fill in a short description of the app in English.</span></span>
    * <span data-ttu-id="493b7-118">Preencha a descrição longa do aplicativo em inglês.</span><span class="sxs-lookup"><span data-stu-id="493b7-118">Fill in the long description of the app in English.</span></span>
    * <span data-ttu-id="493b7-119">Na descrição longa, adicione também a linha "este aplicativo está disponível em" francês ".</span><span class="sxs-lookup"><span data-stu-id="493b7-119">In the long description, please also add the line “This app is available in “French”.</span></span>
    * <span data-ttu-id="493b7-120">Carregar as imagens da sua interface do usuário do aplicativo (em inglês).</span><span class="sxs-lookup"><span data-stu-id="493b7-120">Upload the images of your app UI (in English).</span></span>
2. <span data-ttu-id="493b7-121">Adicionar idioma francês</span><span class="sxs-lookup"><span data-stu-id="493b7-121">Add French language</span></span>
    * <span data-ttu-id="493b7-122">Preencha o nome do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="493b7-122">Fill in the app name.</span></span>
    * <span data-ttu-id="493b7-123">Preencha uma breve descrição do aplicativo em francês.</span><span class="sxs-lookup"><span data-stu-id="493b7-123">Fill in a short description of the app in French.</span></span>
    * <span data-ttu-id="493b7-124">Preencha a descrição longa do aplicativo em francês.</span><span class="sxs-lookup"><span data-stu-id="493b7-124">Fill in the long description of the app in French.</span></span>
    * <span data-ttu-id="493b7-125">Carregar as imagens da sua interface do usuário do aplicativo (em francês).</span><span class="sxs-lookup"><span data-stu-id="493b7-125">Upload the images of your app UI (in French).</span></span>

<span data-ttu-id="493b7-126">As imagens carregadas com o idioma inglês serão aquelas usadas no AppSource.</span><span class="sxs-lookup"><span data-stu-id="493b7-126">The images you upload with the English language will be the ones used in AppSource.</span></span>

## <a name="localizing-the-strings-in-your-app-manifest"></a><span data-ttu-id="493b7-127">Localizando as cadeias de caracteres em seu manifesto de aplicativo</span><span class="sxs-lookup"><span data-stu-id="493b7-127">Localizing the strings in your app manifest</span></span>

<span data-ttu-id="493b7-128">Você deve usar o esquema de aplicativos do Microsoft Teams v 1.5 + para localizar corretamente seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="493b7-128">You must use the Microsoft Teams app schema v1.5+ to properly localize your app.</span></span> <span data-ttu-id="493b7-129">Você pode fazer isso Configurando `$schema` o atributo no arquivo manifest. JSON como 'https://developer.microsoft.com/json-schemas/teams/v1.5/MicrosoftTeams.schema.json' e atualizando a propriedade ' manifestVersion ' para ' 1,5 '.</span><span class="sxs-lookup"><span data-stu-id="493b7-129">You can do this by setting the `$schema` attribute in your manifest.json file to 'https://developer.microsoft.com/json-schemas/teams/v1.5/MicrosoftTeams.schema.json' and updating the 'manifestVersion' property to '1.5'.</span></span>

### <a name="example-manifestjson-change"></a><span data-ttu-id="493b7-130">Alteração de manifesto de exemplo. JSON</span><span class="sxs-lookup"><span data-stu-id="493b7-130">Example manifest.json change</span></span>

```json
{
  "$schema": "https://developer.microsoft.com/json-schemas/teams/v1.5/MicrosoftTeams.schema.json",
  "manifestVersion": "1.5",
  ...
}
```

<span data-ttu-id="493b7-131">Em seguida, você poderá adicionar a propriedade ' localizationInfo ' com o idioma padrão ao qual seu aplicativo oferece suporte.</span><span class="sxs-lookup"><span data-stu-id="493b7-131">You will then want to add the 'localizationInfo' property with the default language that your application supports.</span></span> <span data-ttu-id="493b7-132">O idioma padrão é usado como o idioma de fallback final se as configurações de cliente do usuário não corresponderem a nenhum dos seus idiomas adicionais.</span><span class="sxs-lookup"><span data-stu-id="493b7-132">The default language is used as the final fallback language if the user's client settings do not match any of your additional languages.</span></span>

### <a name="example-manifestjson-change"></a><span data-ttu-id="493b7-133">Alteração de manifesto de exemplo. JSON</span><span class="sxs-lookup"><span data-stu-id="493b7-133">Example manifest.json change</span></span>

```json
{
  ...
  "localizationInfo": {
    "defaultLanguageTag": "en"
  }
  ...
}
```

<span data-ttu-id="493b7-134">Você pode fornecer arquivos. JSON adicionais com traduções de todas as cadeias de caracteres voltadas para o usuário em seu manifesto.</span><span class="sxs-lookup"><span data-stu-id="493b7-134">You can provide additional .json files with translations of all the user facing strings in your manifest.</span></span> <span data-ttu-id="493b7-135">Esses arquivos devem aderir ao [esquema JSON do arquivo de localização](../../resources/schema/localization-schema.md) e devem ser adicionados à propriedade "localizationInfo" do manifesto.</span><span class="sxs-lookup"><span data-stu-id="493b7-135">These files must adhere to the [Localization file JSON schema](../../resources/schema/localization-schema.md) and they must be added to the 'localizationInfo' property of your manifest.</span></span> <span data-ttu-id="493b7-136">Cada arquivo se correlaciona com uma marca de idioma que o cliente do teams usa para escolher as cadeias de caracteres apropriadas.</span><span class="sxs-lookup"><span data-stu-id="493b7-136">Each file correlates to a language tag which the Teams client uses to choose the appropriate strings.</span></span> <span data-ttu-id="493b7-137">A marca de idioma tem a forma <language> - <region> de mas é recomendável omitir <region> a parte para direcionar todas as regiões que dão suporte ao idioma desejado.</span><span class="sxs-lookup"><span data-stu-id="493b7-137">The language tag takes the form of <language>-<region> but it is recommended to omit the <region> portion to target all regions that support the desired language.</span></span>

<span data-ttu-id="493b7-138">O cliente Teams aplicará as cadeias de caracteres nesta ordem: cadeias de caracteres de idioma padrão-> cadeias de caracteres de idiomas do usuário-> idioma do usuário + cadeia de caracteres de região do usuário.</span><span class="sxs-lookup"><span data-stu-id="493b7-138">The Teams client will apply the strings in this order: default language strings -> user's language only strings -> user's language + user's region strings.</span></span>

<span data-ttu-id="493b7-139">Por exemplo, você fornece um idioma padrão de ' fr ' (francês, todas as regiões) e arquivos de idioma adicionais para ' en ' (Inglês, todas as regiões) e ' en-GB ' (Inglês, Grã-Bretanha).</span><span class="sxs-lookup"><span data-stu-id="493b7-139">For example, you provide a default language of 'fr' (French, all regions), and additional language files for 'en' (English, all regions) and 'en-gb' (English, Great Britain).</span></span> <span data-ttu-id="493b7-140">Se o idioma do usuário estiver definido como "en-GB":</span><span class="sxs-lookup"><span data-stu-id="493b7-140">If the user's language is set to 'en-gb':</span></span>

1. <span data-ttu-id="493b7-141">O cliente Teams usará as cadeias de caracteres ' fr ' substituí-las pelas cadeias de caracteres ' en '.</span><span class="sxs-lookup"><span data-stu-id="493b7-141">The Teams client will take the 'fr' strings overwrite them with the 'en' strings.</span></span>
2. <span data-ttu-id="493b7-142">Substitua-os com as cadeias de caracteres "en-GB".</span><span class="sxs-lookup"><span data-stu-id="493b7-142">Overwrite those with the 'en-gb' strings.</span></span>

<span data-ttu-id="493b7-143">Se o idioma do usuário estiver definido como ' en-CA ':</span><span class="sxs-lookup"><span data-stu-id="493b7-143">If the user's language is set to 'en-ca':</span></span> 

1. <span data-ttu-id="493b7-144">O cliente Teams usará as cadeias de caracteres ' fr ' substituí-las pelas cadeias de caracteres ' en '.</span><span class="sxs-lookup"><span data-stu-id="493b7-144">The Teams client will take the 'fr' strings overwrite them with the 'en' strings.</span></span>
2. <span data-ttu-id="493b7-145">Como nenhuma localização "en-AC" é fornecida, as localizações de "en" serão usadas.</span><span class="sxs-lookup"><span data-stu-id="493b7-145">Since no 'en-ca' localization is supplied, the 'en' localizations will be used.</span></span>

<span data-ttu-id="493b7-146">Se o idioma do usuário estiver definido como ' es-es ', o cliente do Microsoft Teams usará as cadeias de caracteres ' fr ' e não as substituirá por nenhum dos arquivos de idioma.</span><span class="sxs-lookup"><span data-stu-id="493b7-146">If the user's language is set to 'es-es', the Teams client will take the 'fr' strings and will not override them with any of the language files.</span></span>

<span data-ttu-id="493b7-147">Portanto, é altamente recomendável fornecer traduções de nível superior, somente de idioma em seu manifesto (' en ' em vez de "en-US ') e fornecer apenas substituições de nível de região para as poucas cadeias de caracteres que precisam delas.</span><span class="sxs-lookup"><span data-stu-id="493b7-147">Therefore, it is strongly recommended to provide top-level, language-only translations in your manifest ('en' instead of 'en-us') and only provide region-level overrides for the few strings that need them.</span></span>

### <a name="example-manifestjson-change"></a><span data-ttu-id="493b7-148">Alteração de manifesto de exemplo. JSON</span><span class="sxs-lookup"><span data-stu-id="493b7-148">Example manifest.json change</span></span>

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

### <a name="example-localization-json-file"></a><span data-ttu-id="493b7-149">Exemplo de arquivo de localização. JSON</span><span class="sxs-lookup"><span data-stu-id="493b7-149">Example localization .json file</span></span>

```json
{
  "$schema": "https://developer.microsoft.com/json-schemas/teams/v1.5/MicrosoftTeams.Localization.schema.json",
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

## <a name="handling-localized-text-submissions-from-your-users"></a><span data-ttu-id="493b7-150">Lidando com envios de texto localizado de seus usuários</span><span class="sxs-lookup"><span data-stu-id="493b7-150">Handling localized text submissions from your users</span></span>

<span data-ttu-id="493b7-151">Se você fornecer versões localizadas de seu aplicativo, é provável que seus usuários respondam com o mesmo idioma.</span><span class="sxs-lookup"><span data-stu-id="493b7-151">If your provide localized versions of your application it is very likely that your users will respond with the same language.</span></span> <span data-ttu-id="493b7-152">O Microsoft Teams não traduz os envios do usuário de volta para o idioma padrão, para que seu aplicativo precise lidar com isso.</span><span class="sxs-lookup"><span data-stu-id="493b7-152">Teams does not translate the user submissions back to the default language, so your app will need to handle that.</span></span> <span data-ttu-id="493b7-153">Por exemplo, se você fornecer um localizado `commandList`, as respostas para o bot serão o texto localizado do comando, e não o idioma padrão.</span><span class="sxs-lookup"><span data-stu-id="493b7-153">For example, if you provide a localized `commandList`, the responses to your bot will be the localized text of the command, not the default language.</span></span> <span data-ttu-id="493b7-154">Seu aplicativo precisará responder de forma adequada.</span><span class="sxs-lookup"><span data-stu-id="493b7-154">Your app will need to respond appropriately.</span></span>
