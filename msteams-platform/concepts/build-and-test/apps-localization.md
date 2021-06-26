---
title: Localizar o aplicativo
description: Descreve considerações para a localização de seu Microsoft Teams app.
ms.topic: conceptual
localization_priority: Normal
keywords: teams publish store office publishing AppSource localization language
ms.date: 05/15/2018
ms.openlocfilehash: c73188bb24960b9ef0706955d09d23b618c04e5c
ms.sourcegitcommit: 4d9d1542e04abacfb252511c665a7229d8bb7162
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/25/2021
ms.locfileid: "53140037"
---
# <a name="localize-your-app"></a><span data-ttu-id="9343c-104">Localizar o aplicativo</span><span class="sxs-lookup"><span data-stu-id="9343c-104">Localize your app</span></span>

<span data-ttu-id="9343c-105">Você deve considerar os seguintes fatores para localizar seu Microsoft Teams aplicativo:</span><span class="sxs-lookup"><span data-stu-id="9343c-105">You must consider the following factors to localize your Microsoft Teams app:</span></span>

1. <span data-ttu-id="9343c-106">[Localize sua listagem appSource](#localize-your-appsource-listing).</span><span class="sxs-lookup"><span data-stu-id="9343c-106">[Localize your AppSource listing](#localize-your-appsource-listing).</span></span>
1. <span data-ttu-id="9343c-107">[Localize cadeias de caracteres no manifesto do aplicativo.](#localize-strings-in-your-app-manifest)</span><span class="sxs-lookup"><span data-stu-id="9343c-107">[Localize strings in your app manifest](#localize-strings-in-your-app-manifest).</span></span> 
1. <span data-ttu-id="9343c-108">[Manipular envios de texto localizados de seus usuários](#handle-localized-text-submissions-from-your-users).</span><span class="sxs-lookup"><span data-stu-id="9343c-108">[Handle localized text submissions from your users](#handle-localized-text-submissions-from-your-users).</span></span>

## <a name="localize-your-appsource-listing"></a><span data-ttu-id="9343c-109">Localize sua listagem do AppSource</span><span class="sxs-lookup"><span data-stu-id="9343c-109">Localize your AppSource listing</span></span>

<span data-ttu-id="9343c-110">Se você estiver publicando o aplicativo na loja, você deve estar ciente de que ainda não há suporte para a localização da listagem do AppSource.</span><span class="sxs-lookup"><span data-stu-id="9343c-110">If you are publishing the app to the store, you must be aware that localizing your AppSource listing is not yet supported.</span></span> <span data-ttu-id="9343c-111">Para dar suporte a listagens localizadas na loja de aplicativos, você pode adicionar idiomas adicionais à sua listagem.</span><span class="sxs-lookup"><span data-stu-id="9343c-111">To support localized listings in the app store, you can add additional languages to your listing.</span></span> <span data-ttu-id="9343c-112">As informações de idioma padrão fornecidas no [Partner Center](/office/dev/store/submit-to-appsource-via-partner-center) para sua listagem são exibidas na listagem de site do [AppSource](https://appsource.microsoft.com/marketplace/apps?product=office%3Bteams&page=1) para seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="9343c-112">The default language information you provide in [Partner Center](/office/dev/store/submit-to-appsource-via-partner-center) for your listing appears in the [AppSource website](https://appsource.microsoft.com/marketplace/apps?product=office%3Bteams&page=1) listing for your app.</span></span> <span data-ttu-id="9343c-113">Atualmente, o idioma padrão é inglês.</span><span class="sxs-lookup"><span data-stu-id="9343c-113">Currently, the default language is English.</span></span>

### <a name="configure-localization"></a><span data-ttu-id="9343c-114">Configurar localização</span><span class="sxs-lookup"><span data-stu-id="9343c-114">Configure localization</span></span>

<span data-ttu-id="9343c-115">Para configurar um idioma adicional para seu aplicativo, no [Partner Center,](/office/dev/store/submit-to-appsource-via-partner-center)selecione inglês e o idioma adicional do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="9343c-115">To configure an additional language for your app, in [Partner Center](/office/dev/store/submit-to-appsource-via-partner-center), select both English and the additional language of the app.</span></span> <span data-ttu-id="9343c-116">O francês é usado como um idioma adicional no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="9343c-116">French is used as an additional language in the following example:</span></span>

1. <span data-ttu-id="9343c-117">Adicionar idioma inglês</span><span class="sxs-lookup"><span data-stu-id="9343c-117">Add English language</span></span>
    * <span data-ttu-id="9343c-118">Insira o nome do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="9343c-118">Enter the app name.</span></span>
    * <span data-ttu-id="9343c-119">Insira uma breve descrição do aplicativo em inglês.</span><span class="sxs-lookup"><span data-stu-id="9343c-119">Enter a short description of the app in English.</span></span>
    * <span data-ttu-id="9343c-120">Insira a descrição longa do aplicativo em inglês.</span><span class="sxs-lookup"><span data-stu-id="9343c-120">Enter the long description of the app in English.</span></span>
    * <span data-ttu-id="9343c-121">Na descrição longa, digite: **Este aplicativo está disponível em francês**.</span><span class="sxs-lookup"><span data-stu-id="9343c-121">In the long description, enter: **This app is available in French**.</span></span>
    * <span data-ttu-id="9343c-122">Upload as imagens da interface do usuário do aplicativo (em inglês).</span><span class="sxs-lookup"><span data-stu-id="9343c-122">Upload the images of your app UI (in English).</span></span>
2. <span data-ttu-id="9343c-123">Adicionar idioma francês</span><span class="sxs-lookup"><span data-stu-id="9343c-123">Add French language</span></span>
    * <span data-ttu-id="9343c-124">Insira o nome do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="9343c-124">Enter the app name.</span></span>
    * <span data-ttu-id="9343c-125">Insira uma breve descrição do aplicativo em francês.</span><span class="sxs-lookup"><span data-stu-id="9343c-125">Enter a short description of the app in French.</span></span>
    * <span data-ttu-id="9343c-126">Insira a descrição longa do aplicativo em francês.</span><span class="sxs-lookup"><span data-stu-id="9343c-126">Enter the long description of the app in French.</span></span>
    * <span data-ttu-id="9343c-127">Upload as imagens da interface do usuário do aplicativo (em francês).</span><span class="sxs-lookup"><span data-stu-id="9343c-127">Upload the images of your app UI (in French).</span></span>

<span data-ttu-id="9343c-128">As imagens que você carrega com o idioma inglês são usadas no AppSource.</span><span class="sxs-lookup"><span data-stu-id="9343c-128">The images that you upload with the English language are used in AppSource.</span></span>

## <a name="localize-strings-in-your-app-manifest"></a><span data-ttu-id="9343c-129">Localize cadeias de caracteres no manifesto do aplicativo</span><span class="sxs-lookup"><span data-stu-id="9343c-129">Localize strings in your app manifest</span></span>

<span data-ttu-id="9343c-130">Você deve usar o esquema Microsoft Teams aplicativo e `v1.5` posteriormente para localizar seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="9343c-130">You must use the Microsoft Teams app schema `v1.5` and later to localize your app.</span></span> <span data-ttu-id="9343c-131">Você pode fazer isso definindo o atributo em seu arquivo manifest.json ou superior e atualizando a propriedade para `$schema` **https://developer.microsoft.com/en-us/json-schemas/teams/v1.5/MicrosoftTeams.schema.json** versão ( neste `manifestVersion` `$schema` `1.5` caso).</span><span class="sxs-lookup"><span data-stu-id="9343c-131">You can do this by setting the `$schema` attribute in your manifest.json file to **https://developer.microsoft.com/en-us/json-schemas/teams/v1.5/MicrosoftTeams.schema.json** or higher and updating the `manifestVersion` property to `$schema` version (`1.5` in this case).</span></span> 

<span data-ttu-id="9343c-132">Você deve adicionar a `localizationInfo` propriedade com o idioma padrão compatível com o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="9343c-132">You must add the `localizationInfo` property with the default language that your application supports.</span></span> <span data-ttu-id="9343c-133">O idioma padrão é usado como o idioma de fallback final se as configurações do cliente do usuário não corresponderem a nenhum dos seus idiomas adicionais.</span><span class="sxs-lookup"><span data-stu-id="9343c-133">The default language is used as the final fallback language if the user's client settings do not match with any of your additional languages.</span></span>

### <a name="example-manifestjson-change"></a><span data-ttu-id="9343c-134">Exemplo manifest.jsna alteração</span><span class="sxs-lookup"><span data-stu-id="9343c-134">Example manifest.json change</span></span>

<span data-ttu-id="9343c-135">A manifest.jsa seguir ajuda a adicionar a propriedade com o idioma padrão compatível com `localizationInfo` o aplicativo junto com `additionalLanguages` :</span><span class="sxs-lookup"><span data-stu-id="9343c-135">The following manifest.json helps to add the `localizationInfo` property with the default language that your application supports along with `additionalLanguages`:</span></span>

```json
{
  "$schema": "https://developer.microsoft.com/en-us/json-schemas/teams/v1.5/MicrosoftTeams.schema.json",
  "manifestVersion": "1.5",
  "localizationInfo": {
        "defaultLanguageTag": "en",
        "additionalLanguages": [
            {
                "languageTag": "es-mx",
                "file": "es-mx.json"
            }
        ]
    }
  ...
}
```

### <a name="example-localization-json-change"></a><span data-ttu-id="9343c-136">Exemplo de alteração de localização .json</span><span class="sxs-lookup"><span data-stu-id="9343c-136">Example localization .json change</span></span>

<span data-ttu-id="9343c-137">A seguir está um exemplo para localização .json:</span><span class="sxs-lookup"><span data-stu-id="9343c-137">Following is an example for localization .json:</span></span>

```json
{
  "$schema": "https://developer.microsoft.com/en-us/json-schemas/teams/v1.5/MicrosoftTeams.Localization.schema.json",
  "manifestVersion": "1.5",
  "name.short": "Localización",
  "name.full": "Aplicación de localización",
  ...
}
```


<span data-ttu-id="9343c-138">Você pode fornecer arquivos .json adicionais com traduções de todas as cadeias de caracteres voltadas para o usuário em seu manifesto.</span><span class="sxs-lookup"><span data-stu-id="9343c-138">You can provide additional .json files with translations of all the user facing strings in your manifest.</span></span> <span data-ttu-id="9343c-139">Esses arquivos devem aderir ao esquema [JSON](../../resources/schema/localization-schema.md) do arquivo de localização e devem ser adicionados à `localizationInfo` propriedade do manifesto.</span><span class="sxs-lookup"><span data-stu-id="9343c-139">These files must adhere to the [Localization file JSON schema](../../resources/schema/localization-schema.md) and they must be added to the `localizationInfo` property of your manifest.</span></span> <span data-ttu-id="9343c-140">Cada arquivo se correlaciona a uma marca de idioma, que o cliente Teams usa para selecionar as cadeias de caracteres apropriadas.</span><span class="sxs-lookup"><span data-stu-id="9343c-140">Each file correlates to a language tag, which the Teams client uses to select the appropriate strings.</span></span> <span data-ttu-id="9343c-141">A marca de idioma assume a forma de, mas você pode omitir a parte para direcionar todas as regiões que `<language>-<region>` `<region>` suportam o idioma desejado.</span><span class="sxs-lookup"><span data-stu-id="9343c-141">The language tag takes the form of `<language>-<region>` but you can omit the `<region>` portion to target all regions that support the desired language.</span></span>

<span data-ttu-id="9343c-142">O cliente Teams aplica as cadeias de caracteres na seguinte ordem: cadeias de caracteres de idioma padrão -> idioma do usuário somente cadeias de caracteres -> idioma do usuário + cadeias de caracteres de região do usuário.</span><span class="sxs-lookup"><span data-stu-id="9343c-142">The Teams client applies the strings in the following order: default language strings -> user's language only strings -> user's language + user's region strings.</span></span>

<span data-ttu-id="9343c-143">Por exemplo, você fornece um idioma padrão de 'fr' (francês, todas as regiões) e arquivos de idiomas adicionais para 'en' (inglês, todas as regiões) e 'en-gb' (inglês, Grã-Bretanha), o idioma do usuário é definido como 'en-gb'.</span><span class="sxs-lookup"><span data-stu-id="9343c-143">For example, you provide a default language of 'fr' (French, all regions), and additional language files for 'en' (English, all regions) and 'en-gb' (English, Great Britain), the user's language is set to 'en-gb'.</span></span> <span data-ttu-id="9343c-144">As seguintes alterações ocorrem com base na seleção de idioma:</span><span class="sxs-lookup"><span data-stu-id="9343c-144">The following changes take place based on the language selection:</span></span>

1. <span data-ttu-id="9343c-145">O Teams cliente assume as cadeias de caracteres 'fr' e substitui-as com as cadeias de caracteres 'en'.</span><span class="sxs-lookup"><span data-stu-id="9343c-145">The Teams client takes the 'fr' strings and overwrite them with the 'en' strings.</span></span>
1. <span data-ttu-id="9343c-146">Sobrescreva as cadeias de caracteres 'en' com as cadeias de caracteres 'en-gb'.</span><span class="sxs-lookup"><span data-stu-id="9343c-146">Overwrite the 'en' strings with the 'en-gb' strings.</span></span>

<span data-ttu-id="9343c-147">Se o idioma do usuário for definido como 'en-ca', as seguintes alterações ocorrerão com base na seleção de idioma:</span><span class="sxs-lookup"><span data-stu-id="9343c-147">If the user's language is set to 'en-ca', the following changes take place based on the language selection:</span></span> 

1. <span data-ttu-id="9343c-148">O Teams cliente assume as cadeias de caracteres 'fr' e substitui-as com as cadeias de caracteres 'en'.</span><span class="sxs-lookup"><span data-stu-id="9343c-148">The Teams client takes the 'fr' strings and overwrite them with the 'en' strings.</span></span>
1. <span data-ttu-id="9343c-149">Como nenhuma localização 'en-ca' é fornecida, as localizações 'en' são usadas.</span><span class="sxs-lookup"><span data-stu-id="9343c-149">Since no 'en-ca' localization is supplied, the 'en\` localizations are used.</span></span>

<span data-ttu-id="9343c-150">Se o idioma do usuário estiver definido como 'es-es', o cliente Teams assume as cadeias de caracteres 'fr'.</span><span class="sxs-lookup"><span data-stu-id="9343c-150">If the user's language is set to 'es-es', the Teams client takes the 'fr' strings.</span></span> <span data-ttu-id="9343c-151">O Teams cliente não substitui as cadeias de caracteres por nenhum dos arquivos de idioma, pois nenhuma tradução 'es' ou 'es-es' é fornecida.</span><span class="sxs-lookup"><span data-stu-id="9343c-151">The Teams client does not override the strings with any of the language files as no 'es' or 'es-es' translation is provided.</span></span>

<span data-ttu-id="9343c-152">Portanto, você deve fornecer traduções de nível superior, somente de idioma em seu manifesto.</span><span class="sxs-lookup"><span data-stu-id="9343c-152">Therefore, you must provide top level, language only translations in your manifest.</span></span> <span data-ttu-id="9343c-153">Por exemplo, 'en' em vez de 'en-us'.</span><span class="sxs-lookup"><span data-stu-id="9343c-153">For example, 'en' instead of 'en-us'.</span></span> <span data-ttu-id="9343c-154">Você deve fornecer substituições de nível de região apenas para as poucas cadeias de caracteres que precisam delas.</span><span class="sxs-lookup"><span data-stu-id="9343c-154">You must provide region level overrides only for the few strings that need them.</span></span> 

### <a name="example-manifestjson-change"></a><span data-ttu-id="9343c-155">Exemplo manifest.jsna alteração</span><span class="sxs-lookup"><span data-stu-id="9343c-155">Example manifest.json change</span></span>

<span data-ttu-id="9343c-156">A manifest.jssobre a alteração é mostrada no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="9343c-156">The manifest.json change is shown in the following example:</span></span>

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

### <a name="example-localization-json-file"></a><span data-ttu-id="9343c-157">Exemplo de arquivo .json de localização</span><span class="sxs-lookup"><span data-stu-id="9343c-157">Example localization .json file</span></span>

 <span data-ttu-id="9343c-158">A localization.jssobre a alteração é mostrada no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="9343c-158">The localization.json change is shown in the following example:</span></span>

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

## <a name="handle-localized-text-submissions-from-your-users"></a><span data-ttu-id="9343c-159">Manipular envios de texto localizados de seus usuários</span><span class="sxs-lookup"><span data-stu-id="9343c-159">Handle localized text submissions from your users</span></span>

<span data-ttu-id="9343c-160">Se você fornecer versões localizadas do aplicativo, os usuários responderão com o mesmo idioma.</span><span class="sxs-lookup"><span data-stu-id="9343c-160">If your provide localized versions of your application, the users respond with the same language.</span></span> <span data-ttu-id="9343c-161">Como Teams não converte os envios de usuário de volta para o idioma padrão, seu aplicativo deve manipular as respostas de idioma localizado.</span><span class="sxs-lookup"><span data-stu-id="9343c-161">As Teams does not translate the user submissions back to the default language, your app must handle the localized language responses.</span></span> <span data-ttu-id="9343c-162">Por exemplo, se você fornecer um localizado , as respostas ao bot serão o texto localizado do comando, não `commandList` o idioma padrão.</span><span class="sxs-lookup"><span data-stu-id="9343c-162">For example, if you provide a localized `commandList`, the responses to your bot are the localized text of the command, not the default language.</span></span> <span data-ttu-id="9343c-163">Seu aplicativo deve responder adequadamente.</span><span class="sxs-lookup"><span data-stu-id="9343c-163">Your app must respond appropriately.</span></span>

## <a name="code-sample"></a><span data-ttu-id="9343c-164">Exemplo de código</span><span class="sxs-lookup"><span data-stu-id="9343c-164">Code sample</span></span>

| <span data-ttu-id="9343c-165">Exemplo de nome</span><span class="sxs-lookup"><span data-stu-id="9343c-165">Sample name</span></span> | <span data-ttu-id="9343c-166">Descrição</span><span class="sxs-lookup"><span data-stu-id="9343c-166">Description</span></span> | <span data-ttu-id="9343c-167">.NET</span><span class="sxs-lookup"><span data-stu-id="9343c-167">.NET</span></span> | <span data-ttu-id="9343c-168">Node.js</span><span class="sxs-lookup"><span data-stu-id="9343c-168">Node.js</span></span> |
|-------------|-------------|------|------|
| <span data-ttu-id="9343c-169">Localização de aplicativos</span><span class="sxs-lookup"><span data-stu-id="9343c-169">App Localization</span></span> | <span data-ttu-id="9343c-170">Microsoft Teams localização de aplicativo usando bot e guia.</span><span class="sxs-lookup"><span data-stu-id="9343c-170">Microsoft Teams app localization using bot and tab.</span></span> | [<span data-ttu-id="9343c-171">View</span><span class="sxs-lookup"><span data-stu-id="9343c-171">View</span></span>](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/app-localization/csharp) |[<span data-ttu-id="9343c-172">View</span><span class="sxs-lookup"><span data-stu-id="9343c-172">View</span></span>](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/app-localization/nodejs) |

