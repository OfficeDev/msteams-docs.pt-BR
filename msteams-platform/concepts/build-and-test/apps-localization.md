---
title: Localização para o seu aplicativo
description: Descreve considerações para localização do aplicativo Microsoft Teams.
ms.topic: conceptual
localization_priority: Normal
keywords: equipes publicam escritório de loja publicando appSource linguagem de localização
ms.date: 05/15/2018
ms.openlocfilehash: a55b8af97e5306843858e5844a017dd402ab3516
ms.sourcegitcommit: 51e4a1464ea58c254ad6bd0317aca03ebf6bf1f6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2021
ms.locfileid: "52566044"
---
# <a name="localization-for-microsoft-teams-apps"></a><span data-ttu-id="70bf6-104">Localização para aplicativos de Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="70bf6-104">Localization for Microsoft Teams apps</span></span>

<span data-ttu-id="70bf6-105">Ao localizar seu aplicativo Microsoft Teams, você deve considerar o seguinte:</span><span class="sxs-lookup"><span data-stu-id="70bf6-105">When localizing your Microsoft Teams app, you must consider the following:</span></span>

1. <span data-ttu-id="70bf6-106">Sua Teams lista de lojas (se aplicável).</span><span class="sxs-lookup"><span data-stu-id="70bf6-106">Your Teams store listing (if applicable).</span></span>
1. <span data-ttu-id="70bf6-107">O usuário final enfrentando strings no manifesto do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="70bf6-107">The end-user facing strings in your app manifest.</span></span> <span data-ttu-id="70bf6-108">Por exemplo, comandos de bot.</span><span class="sxs-lookup"><span data-stu-id="70bf6-108">For example bot commands.</span></span>
1. <span data-ttu-id="70bf6-109">Respondendo ao texto localizado enviado de seus usuários.</span><span class="sxs-lookup"><span data-stu-id="70bf6-109">Responding to localized text submitted from your users.</span></span>

## <a name="localizing-your-appsource-listing"></a><span data-ttu-id="70bf6-110">Localização de sua listagem AppSource</span><span class="sxs-lookup"><span data-stu-id="70bf6-110">Localizing your AppSource listing</span></span>

<span data-ttu-id="70bf6-111">Se você está publicando na loja, você precisa estar ciente de que a localização da sua listagem appSource ainda não está suportada.</span><span class="sxs-lookup"><span data-stu-id="70bf6-111">If you're publishing to the store, you need to be aware that localizing your AppSource listing is not yet supported.</span></span> <span data-ttu-id="70bf6-112">No entanto, em preparação para o suporte para listagens localizadas na loja de aplicativos, você pode adicionar idiomas adicionais à sua listagem.</span><span class="sxs-lookup"><span data-stu-id="70bf6-112">However, in preparation for support for localized listings in the app store you can add additional languages to your listing.</span></span> <span data-ttu-id="70bf6-113">Atualmente, apenas as informações padrão do idioma (inglês) que você fornece no [Partner Center](/office/dev/store/submit-to-appsource-via-partner-center) para sua listagem aparecerão na listagem do [site appSource](https://appsource.microsoft.com/marketplace/apps?product=office%3Bteams&page=1) para o seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="70bf6-113">Currently only the default (English) language information you provide in [Partner Center](/office/dev/store/submit-to-appsource-via-partner-center) for your listing will appear in the [AppSource website](https://appsource.microsoft.com/marketplace/apps?product=office%3Bteams&page=1) listing for your app.</span></span>

### <a name="example-of-configuring-localization"></a><span data-ttu-id="70bf6-114">Exemplo de configuração da localização</span><span class="sxs-lookup"><span data-stu-id="70bf6-114">Example of configuring localization</span></span>

<span data-ttu-id="70bf6-115">Para configurar um idioma adicional para o seu aplicativo, no [Partner Center,](/office/dev/store/submit-to-appsource-via-partner-center)selecione tanto o inglês quanto o idioma adicional do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="70bf6-115">To configure an additional language for your app, in [Partner Center](/office/dev/store/submit-to-appsource-via-partner-center), select both English and the additional language of the app.</span></span> <span data-ttu-id="70bf6-116">O francês é usado neste exemplo:</span><span class="sxs-lookup"><span data-stu-id="70bf6-116">French is used in this example:</span></span>

1. <span data-ttu-id="70bf6-117">Adicionar inglês</span><span class="sxs-lookup"><span data-stu-id="70bf6-117">Add English language</span></span>
    * <span data-ttu-id="70bf6-118">Preencha o nome do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="70bf6-118">Fill in the app name.</span></span>
    * <span data-ttu-id="70bf6-119">Preencha uma breve descrição do aplicativo em inglês.</span><span class="sxs-lookup"><span data-stu-id="70bf6-119">Fill in a short description of the app in English.</span></span>
    * <span data-ttu-id="70bf6-120">Preencha a longa descrição do aplicativo em inglês.</span><span class="sxs-lookup"><span data-stu-id="70bf6-120">Fill in the long description of the app in English.</span></span>
    * <span data-ttu-id="70bf6-121">Na longa descrição, adicione também a linha "Este aplicativo está disponível em "Francês".</span><span class="sxs-lookup"><span data-stu-id="70bf6-121">In the long description, please also add the line “This app is available in “French”.</span></span>
    * <span data-ttu-id="70bf6-122">Upload as imagens do seu aplicativo UI (em inglês).</span><span class="sxs-lookup"><span data-stu-id="70bf6-122">Upload the images of your app UI (in English).</span></span>
2. <span data-ttu-id="70bf6-123">Adicionar língua francesa</span><span class="sxs-lookup"><span data-stu-id="70bf6-123">Add French language</span></span>
    * <span data-ttu-id="70bf6-124">Preencha o nome do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="70bf6-124">Fill in the app name.</span></span>
    * <span data-ttu-id="70bf6-125">Preencha uma breve descrição do aplicativo em francês.</span><span class="sxs-lookup"><span data-stu-id="70bf6-125">Fill in a short description of the app in French.</span></span>
    * <span data-ttu-id="70bf6-126">Preencha a longa descrição do aplicativo em francês.</span><span class="sxs-lookup"><span data-stu-id="70bf6-126">Fill in the long description of the app in French.</span></span>
    * <span data-ttu-id="70bf6-127">Upload as imagens do seu aplicativo UI (em francês).</span><span class="sxs-lookup"><span data-stu-id="70bf6-127">Upload the images of your app UI (in French).</span></span>

<span data-ttu-id="70bf6-128">As imagens que você carrega com o idioma inglês serão as usadas no AppSource.</span><span class="sxs-lookup"><span data-stu-id="70bf6-128">The images you upload with the English language will be the ones used in AppSource.</span></span>

## <a name="localizing-the-strings-in-your-app-manifest"></a><span data-ttu-id="70bf6-129">Localização das cordas no manifesto do aplicativo</span><span class="sxs-lookup"><span data-stu-id="70bf6-129">Localizing the strings in your app manifest</span></span>

<span data-ttu-id="70bf6-130">Você deve usar o esquema de Microsoft Teams aplicativo v1.5+ para localizar corretamente seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="70bf6-130">You must use the Microsoft Teams app schema v1.5+ to properly localize your app.</span></span> <span data-ttu-id="70bf6-131">Você pode fazer isso definindo o `$schema` atributo em seu manifest.jsno arquivo para ' e https://developer.microsoft.com/en-us/json-schemas/teams/v1.8/MicrosoftTeams.Localization.schema.json atualizando a propriedade 'manifestVersion' para '1.7'.</span><span class="sxs-lookup"><span data-stu-id="70bf6-131">You can do this by setting the `$schema` attribute in your manifest.json file to 'https://developer.microsoft.com/en-us/json-schemas/teams/v1.8/MicrosoftTeams.Localization.schema.json' and updating the 'manifestVersion' property to '1.7'.</span></span>

### <a name="example-manifestjson-change"></a><span data-ttu-id="70bf6-132">Exemplo manifest.jssobre a mudança</span><span class="sxs-lookup"><span data-stu-id="70bf6-132">Example manifest.json change</span></span>

```json
{
  "$schema": "https://developer.microsoft.com/en-us/json-schemas/teams/v1.8/MicrosoftTeams.Localization.schema.json",
  "manifestVersion": "1.5",
  ...
}
```

<span data-ttu-id="70bf6-133">Em seguida, você deseja adicionar a propriedade 'localizaçãoInfo' com o idioma padrão que seu aplicativo suporta.</span><span class="sxs-lookup"><span data-stu-id="70bf6-133">You will then want to add the 'localizationInfo' property with the default language that your application supports.</span></span> <span data-ttu-id="70bf6-134">O idioma padrão é usado como o idioma de recuo final se as configurações do cliente do usuário não corresponderem a nenhum de seus idiomas adicionais.</span><span class="sxs-lookup"><span data-stu-id="70bf6-134">The default language is used as the final fallback language if the user's client settings do not match any of your additional languages.</span></span>

### <a name="example-manifestjson-change"></a><span data-ttu-id="70bf6-135">Exemplo manifest.jssobre a mudança</span><span class="sxs-lookup"><span data-stu-id="70bf6-135">Example manifest.json change</span></span>

```json
{
  ...
  "localizationInfo": {
    "defaultLanguageTag": "en"
  }
  ...
}
```

<span data-ttu-id="70bf6-136">Você pode fornecer arquivos .json adicionais com traduções de todas as strings que enfrentam o usuário em seu manifesto.</span><span class="sxs-lookup"><span data-stu-id="70bf6-136">You can provide additional .json files with translations of all the user facing strings in your manifest.</span></span> <span data-ttu-id="70bf6-137">Esses arquivos devem aderir ao [esquema JSON](../../resources/schema/localization-schema.md) do arquivo de localização e devem ser adicionados à propriedade 'localizaçãoInfo' do seu manifesto.</span><span class="sxs-lookup"><span data-stu-id="70bf6-137">These files must adhere to the [Localization file JSON schema](../../resources/schema/localization-schema.md) and they must be added to the 'localizationInfo' property of your manifest.</span></span> <span data-ttu-id="70bf6-138">Cada arquivo se correlaciona com uma tag de idioma que o Teams cliente usa para escolher as strings apropriadas.</span><span class="sxs-lookup"><span data-stu-id="70bf6-138">Each file correlates to a language tag which the Teams client uses to choose the appropriate strings.</span></span> <span data-ttu-id="70bf6-139">A tag de idioma toma a forma <language> - <region> de, mas é recomendado omitir a <region> porção para atingir todas as regiões que suportam a linguagem desejada.</span><span class="sxs-lookup"><span data-stu-id="70bf6-139">The language tag takes the form of <language>-<region> but it is recommended to omit the <region> portion to target all regions that support the desired language.</span></span>

<span data-ttu-id="70bf6-140">O cliente Teams aplicará as strings nesta ordem: strings de idioma padrão -> idioma do usuário apenas strings -> idioma do usuário + sequências regionais do usuário.</span><span class="sxs-lookup"><span data-stu-id="70bf6-140">The Teams client will apply the strings in this order: default language strings -> user's language only strings -> user's language + user's region strings.</span></span>

<span data-ttu-id="70bf6-141">Por exemplo, você fornece um idioma padrão de 'fr' (francês, todas as regiões) e arquivos adicionais de idiomas para 'en' (inglês, todas as regiões) e 'en-gb' (inglês, Grã-Bretanha).</span><span class="sxs-lookup"><span data-stu-id="70bf6-141">For example, you provide a default language of 'fr' (French, all regions), and additional language files for 'en' (English, all regions) and 'en-gb' (English, Great Britain).</span></span> <span data-ttu-id="70bf6-142">Se o idioma do usuário estiver definido como 'en-gb':</span><span class="sxs-lookup"><span data-stu-id="70bf6-142">If the user's language is set to 'en-gb':</span></span>

1. <span data-ttu-id="70bf6-143">O cliente Teams levará as cordas 'fr' sobregrava-as com as cordas 'en'.</span><span class="sxs-lookup"><span data-stu-id="70bf6-143">The Teams client will take the 'fr' strings overwrite them with the 'en' strings.</span></span>
2. <span data-ttu-id="70bf6-144">Substitua-os com as cordas 'en-gb'.</span><span class="sxs-lookup"><span data-stu-id="70bf6-144">Overwrite those with the 'en-gb' strings.</span></span>

<span data-ttu-id="70bf6-145">Se o idioma do usuário estiver definido como 'en-ca':</span><span class="sxs-lookup"><span data-stu-id="70bf6-145">If the user's language is set to 'en-ca':</span></span> 

1. <span data-ttu-id="70bf6-146">O cliente Teams levará as cordas 'fr' sobregrava-as com as cordas 'en'.</span><span class="sxs-lookup"><span data-stu-id="70bf6-146">The Teams client will take the 'fr' strings overwrite them with the 'en' strings.</span></span>
2. <span data-ttu-id="70bf6-147">Como não é fornecida uma localização 'en-ca', as localizações 'en' serão utilizadas.</span><span class="sxs-lookup"><span data-stu-id="70bf6-147">Since no 'en-ca' localization is supplied, the 'en' localizations will be used.</span></span>

<span data-ttu-id="70bf6-148">Se o idioma do usuário estiver definido como 'es-es', o cliente Teams pegará as strings 'fr' e não irá substituí-las com nenhum dos arquivos de idioma.</span><span class="sxs-lookup"><span data-stu-id="70bf6-148">If the user's language is set to 'es-es', the Teams client will take the 'fr' strings and will not override them with any of the language files.</span></span>

<span data-ttu-id="70bf6-149">Portanto, é fortemente recomendável fornecer traduções de alto nível, somente para idiomas em seu manifesto ('en' em vez de 'en-us') e apenas fornecer substituições de nível de região para as poucas strings que precisam delas.</span><span class="sxs-lookup"><span data-stu-id="70bf6-149">Therefore, it is strongly recommended to provide top-level, language-only translations in your manifest ('en' instead of 'en-us') and only provide region-level overrides for the few strings that need them.</span></span>

### <a name="example-manifestjson-change"></a><span data-ttu-id="70bf6-150">Exemplo manifest.jssobre a mudança</span><span class="sxs-lookup"><span data-stu-id="70bf6-150">Example manifest.json change</span></span>

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

### <a name="example-localization-json-file"></a><span data-ttu-id="70bf6-151">Arquivo de localização de exemplo .json</span><span class="sxs-lookup"><span data-stu-id="70bf6-151">Example localization .json file</span></span>

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

## <a name="handling-localized-text-submissions-from-your-users"></a><span data-ttu-id="70bf6-152">Manipulação de envios de texto localizados de seus usuários</span><span class="sxs-lookup"><span data-stu-id="70bf6-152">Handling localized text submissions from your users</span></span>

<span data-ttu-id="70bf6-153">Se você fornecer versões localizadas do seu aplicativo é muito provável que seus usuários respondam com o mesmo idioma.</span><span class="sxs-lookup"><span data-stu-id="70bf6-153">If your provide localized versions of your application it is very likely that your users will respond with the same language.</span></span> <span data-ttu-id="70bf6-154">Teams não traduz os envios do usuário de volta para o idioma padrão, então seu aplicativo precisará lidar com isso.</span><span class="sxs-lookup"><span data-stu-id="70bf6-154">Teams does not translate the user submissions back to the default language, so your app will need to handle that.</span></span> <span data-ttu-id="70bf6-155">Por exemplo, se você fornecer um `commandList` localizado, as respostas ao seu bot serão o texto localizado do comando, não o idioma padrão.</span><span class="sxs-lookup"><span data-stu-id="70bf6-155">For example, if you provide a localized `commandList`, the responses to your bot will be the localized text of the command, not the default language.</span></span> <span data-ttu-id="70bf6-156">Seu aplicativo precisará responder adequadamente.</span><span class="sxs-lookup"><span data-stu-id="70bf6-156">Your app will need to respond appropriately.</span></span>

## <a name="code-sample"></a><span data-ttu-id="70bf6-157">Exemplo de código</span><span class="sxs-lookup"><span data-stu-id="70bf6-157">Code sample</span></span>

| <span data-ttu-id="70bf6-158">Nome da amostra</span><span class="sxs-lookup"><span data-stu-id="70bf6-158">Sample name</span></span> | <span data-ttu-id="70bf6-159">Descrição</span><span class="sxs-lookup"><span data-stu-id="70bf6-159">Description</span></span> | <span data-ttu-id="70bf6-160">.NET</span><span class="sxs-lookup"><span data-stu-id="70bf6-160">.NET</span></span> |
|-------------|-------------|------|
| <span data-ttu-id="70bf6-161">Localização de aplicativos</span><span class="sxs-lookup"><span data-stu-id="70bf6-161">App Localization</span></span> | <span data-ttu-id="70bf6-162">Microsoft Teams localização do aplicativo usando bot e guia.</span><span class="sxs-lookup"><span data-stu-id="70bf6-162">Microsoft Teams app localization using bot and tab.</span></span> | [<span data-ttu-id="70bf6-163">View</span><span class="sxs-lookup"><span data-stu-id="70bf6-163">View</span></span>](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/app-localization/csharp) |


