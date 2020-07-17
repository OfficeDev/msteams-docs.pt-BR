---
title: Referência de esquema JSON de arquivo de localização
description: Descreve o esquema de localização suportado pelo arquivo de localização para o Microsoft Teams
keywords: Localização do esquema do manifesto do teams
ms.date: 05/20/2019
ms.openlocfilehash: 061729ecb5110c99d8f85f144796f1a78b266c3d
ms.sourcegitcommit: bac0226d9048c363d96bbaf6f5395388c5f5c45a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/06/2020
ms.locfileid: "45039276"
---
# <a name="reference-localization-file-json-schema"></a><span data-ttu-id="b19ef-104">Referência: esquema JSON do arquivo de localização</span><span class="sxs-lookup"><span data-stu-id="b19ef-104">Reference: Localization file JSON schema</span></span>

<span data-ttu-id="b19ef-105">O arquivo de localização do Microsoft Teams descreve as traduções de idioma que serão atendidas com base nas configurações de idioma do cliente.</span><span class="sxs-lookup"><span data-stu-id="b19ef-105">The Microsoft Teams localization file describes language translations that will be served based on the client language settings.</span></span> <span data-ttu-id="b19ef-106">O arquivo deve estar em conformidade com o esquema hospedado em [`https://developer.microsoft.com/en-us/json-schemas/teams/v1.7/MicrosoftTeams.Localization.schema.json`](https://developer.microsoft.com/en-us/json-schemas/teams/v1.7/MicrosoftTeams.Localization.schema.json) .</span><span class="sxs-lookup"><span data-stu-id="b19ef-106">Your file must conform to the schema hosted at [`https://developer.microsoft.com/en-us/json-schemas/teams/v1.7/MicrosoftTeams.Localization.schema.json`](https://developer.microsoft.com/en-us/json-schemas/teams/v1.7/MicrosoftTeams.Localization.schema.json).</span></span> <span data-ttu-id="b19ef-107">Para obter informações adicionais, consulte [localização de aplicativos](~/concepts/build-and-test/apps-localization.md).</span><span class="sxs-lookup"><span data-stu-id="b19ef-107">For additional information see [app localization](~/concepts/build-and-test/apps-localization.md).</span></span>

## <a name="sample"></a><span data-ttu-id="b19ef-108">Amostra</span><span class="sxs-lookup"><span data-stu-id="b19ef-108">Sample</span></span>

```json
{
  "$schema": "https://developer.microsoft.com/json-schemas/teams/v1.7/MicrosoftTeams.schema.json",
  "name.short": "Le App Studio",
  "name.full": "App Studio pour Microsoft Teams",
  "description.short": "Créez d'excellentes applications pour Microsoft Teams avec App Studio.",
  "description.full": "Créez de nouvelles applications Microsoft Teams, concevez et prévisualisez des cartes bot, et explorez la documentation avec App Studio.",
  "staticTabs[0].name": "Editeur de manifest",
  "staticTabs[1].name": "Editeur de cartes",
  "staticTabs[2].name": "Bibliothèque de contrôles",
  "bots[0].commandLists[0].commands[0].title": "chercher",
  "bots[0].commandLists[0].commands[0].description": "Rechercher la documentation Teams pertinente"
}
```

<span data-ttu-id="b19ef-109">O esquema define as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="b19ef-109">The schema defines the following properties:</span></span>

## <a name="schema"></a><span data-ttu-id="b19ef-110">$schema</span><span class="sxs-lookup"><span data-stu-id="b19ef-110">$schema</span></span>

<span data-ttu-id="b19ef-111">**URI**</span><span class="sxs-lookup"><span data-stu-id="b19ef-111">**URI**</span></span>

<span data-ttu-id="b19ef-112">A URL https://que faz referência ao esquema JSON para o manifesto.</span><span class="sxs-lookup"><span data-stu-id="b19ef-112">The https:// URL referencing the JSON Schema for the manifest.</span></span>

> [!TIP]
> <span data-ttu-id="b19ef-113">Especifique o esquema no início do manifesto para habilitar o IntelliSense ou suporte semelhante do editor de código:`"$schema": "https://developer.microsoft.com/json-schemas/teams/v1.7/MicrosoftTeams.schema.json",`</span><span class="sxs-lookup"><span data-stu-id="b19ef-113">Specify the schema at the beginning of your manifest to enable IntelliSense or similar support from your code editor: `"$schema": "https://developer.microsoft.com/json-schemas/teams/v1.7/MicrosoftTeams.schema.json",`</span></span>

## <a name="nameshort"></a><span data-ttu-id="b19ef-114">Name. short</span><span class="sxs-lookup"><span data-stu-id="b19ef-114">name.short</span></span>

<span data-ttu-id="b19ef-115">**Cadeia de caracteres, tamanho máximo 30**</span><span class="sxs-lookup"><span data-stu-id="b19ef-115">**String, Max Length 30**</span></span>

<span data-ttu-id="b19ef-116">Substitui a cadeia de caracteres correspondente do manifesto do aplicativo pelo valor fornecido aqui.</span><span class="sxs-lookup"><span data-stu-id="b19ef-116">Replaces the corresponding string from the app manifest with the value provided here.</span></span>

## <a name="namefull"></a><span data-ttu-id="b19ef-117">nome. Full</span><span class="sxs-lookup"><span data-stu-id="b19ef-117">name.full</span></span>

<span data-ttu-id="b19ef-118">**Cadeia de caracteres, tamanho máximo 100**</span><span class="sxs-lookup"><span data-stu-id="b19ef-118">**String, Max Length 100**</span></span>

<span data-ttu-id="b19ef-119">Substitui a cadeia de caracteres correspondente do manifesto do aplicativo pelo valor fornecido aqui.</span><span class="sxs-lookup"><span data-stu-id="b19ef-119">Replaces the corresponding string from the app manifest with the value provided here.</span></span>

## <a name="descriptionshort"></a><span data-ttu-id="b19ef-120">Descrição. short</span><span class="sxs-lookup"><span data-stu-id="b19ef-120">description.short</span></span>

<span data-ttu-id="b19ef-121">**Cadeia de caracteres, tamanho máximo 80**</span><span class="sxs-lookup"><span data-stu-id="b19ef-121">**String, Max Length 80**</span></span>

<span data-ttu-id="b19ef-122">Substitui a cadeia de caracteres correspondente do manifesto do aplicativo pelo valor fornecido aqui.</span><span class="sxs-lookup"><span data-stu-id="b19ef-122">Replaces the corresponding string from the app manifest with the value provided here.</span></span>

## <a name="descriptionfull"></a><span data-ttu-id="b19ef-123">Descrição. Full</span><span class="sxs-lookup"><span data-stu-id="b19ef-123">description.full</span></span>

<span data-ttu-id="b19ef-124">**Cadeia de caracteres, tamanho máximo 4000**</span><span class="sxs-lookup"><span data-stu-id="b19ef-124">**String, Max Length 4000**</span></span>

<span data-ttu-id="b19ef-125">Substitui a cadeia de caracteres correspondente do manifesto do aplicativo pelo valor fornecido aqui.</span><span class="sxs-lookup"><span data-stu-id="b19ef-125">Replaces the corresponding string from the app manifest with the value provided here.</span></span>

## <a name="statictabs0-910-5name"></a><span data-ttu-id="b19ef-126">staticTabs \\ [([0-9] | 1 [0-5]) \\ ] \\ . nome</span><span class="sxs-lookup"><span data-stu-id="b19ef-126">staticTabs\\[([0-9]|1[0-5])\\]\\.name</span></span>

<span data-ttu-id="b19ef-127">**Cadeia de caracteres, tamanho máximo 128**</span><span class="sxs-lookup"><span data-stu-id="b19ef-127">**String, Max Length 128**</span></span>

<span data-ttu-id="b19ef-128">Substitui a (s) cadeias de caracteres correspondentes do manifesto do aplicativo pelo valor fornecido aqui.</span><span class="sxs-lookup"><span data-stu-id="b19ef-128">Replaces the corresponding string(s) from the app manifest with the value provided here.</span></span>

## <a name="bots0commandlists0-2commands0-9title"></a><span data-ttu-id="b19ef-129">bots \\ [0 \\ ] \\ . commandLists \\ [[0-2] \\ ] \\ . Commands \\ [[0-9] \\ ] \\ . título</span><span class="sxs-lookup"><span data-stu-id="b19ef-129">bots\\[0\\]\\.commandLists\\[[0-2]\\]\\.commands\\[[0-9]\\]\\.title</span></span>

<span data-ttu-id="b19ef-130">**Cadeia de caracteres, tamanho máximo 32**</span><span class="sxs-lookup"><span data-stu-id="b19ef-130">**String, Max Length 32**</span></span>

<span data-ttu-id="b19ef-131">Substitui a (s) cadeias de caracteres correspondentes do manifesto do aplicativo pelo valor fornecido aqui.</span><span class="sxs-lookup"><span data-stu-id="b19ef-131">Replaces the corresponding string(s) from the app manifest with the value provided here.</span></span>

## <a name="bots0commandlists0-2commands0-9description"></a><span data-ttu-id="b19ef-132">bots \\ [0 \\ ] \\ . commandLists \\ [[0-2] \\ ] \\ . Commands \\ [[0-9] \\ ] \\ . Descrição</span><span class="sxs-lookup"><span data-stu-id="b19ef-132">bots\\[0\\]\\.commandLists\\[[0-2]\\]\\.commands\\[[0-9]\\]\\.description</span></span>

<span data-ttu-id="b19ef-133">**Cadeia de caracteres, tamanho máximo 128**</span><span class="sxs-lookup"><span data-stu-id="b19ef-133">**String, Max Length 128**</span></span>

<span data-ttu-id="b19ef-134">Substitui a (s) cadeias de caracteres correspondentes do manifesto do aplicativo pelo valor fornecido aqui.</span><span class="sxs-lookup"><span data-stu-id="b19ef-134">Replaces the corresponding string(s) from the app manifest with the value provided here.</span></span>

## <a name="composeextensions0commands0-9title"></a><span data-ttu-id="b19ef-135">composeExtensions \\ [0 \\ ] \\ . Commands \\ [[0-9] \\ ] \\ . title</span><span class="sxs-lookup"><span data-stu-id="b19ef-135">composeExtensions\\[0\\]\\.commands\\[[0-9]\\]\\.title</span></span>

<span data-ttu-id="b19ef-136">**Cadeia de caracteres, tamanho máximo 32**</span><span class="sxs-lookup"><span data-stu-id="b19ef-136">**String, Max Length 32**</span></span>

<span data-ttu-id="b19ef-137">Substitui a (s) cadeias de caracteres correspondentes do manifesto do aplicativo pelo valor fornecido aqui.</span><span class="sxs-lookup"><span data-stu-id="b19ef-137">Replaces the corresponding string(s) from the app manifest with the value provided here.</span></span>

## <a name="composeextensions0commands0-9description"></a><span data-ttu-id="b19ef-138">composeExtensions \\ [0 \\ ] \\ . Commands \\ [[0-9] \\ ] \\ . Descrição</span><span class="sxs-lookup"><span data-stu-id="b19ef-138">composeExtensions\\[0\\]\\.commands\\[[0-9]\\]\\.description</span></span>

<span data-ttu-id="b19ef-139">**Cadeia de caracteres, tamanho máximo 128**</span><span class="sxs-lookup"><span data-stu-id="b19ef-139">**String, Max Length 128**</span></span>

<span data-ttu-id="b19ef-140">Substitui a (s) cadeias de caracteres correspondentes do manifesto do aplicativo pelo valor fornecido aqui.</span><span class="sxs-lookup"><span data-stu-id="b19ef-140">Replaces the corresponding string(s) from the app manifest with the value provided here.</span></span>

## <a name="composeextensions0commands0-9parameters0-4title"></a><span data-ttu-id="b19ef-141">composeExtensions \\ [0 \\ ] \\ . Commands \\ [[0-9] \\ ] \\ . Parameters \\ [[0-4] \\ ] \\ . title</span><span class="sxs-lookup"><span data-stu-id="b19ef-141">composeExtensions\\[0\\]\\.commands\\[[0-9]\\]\\.parameters\\[[0-4]\\]\\.title</span></span>

<span data-ttu-id="b19ef-142">**Cadeia de caracteres, tamanho máximo 32**</span><span class="sxs-lookup"><span data-stu-id="b19ef-142">**String, Max Length 32**</span></span>

<span data-ttu-id="b19ef-143">Substitui a (s) cadeias de caracteres correspondentes do manifesto do aplicativo pelo valor fornecido aqui.</span><span class="sxs-lookup"><span data-stu-id="b19ef-143">Replaces the corresponding string(s) from the app manifest with the value provided here.</span></span>

## <a name="composeextensions0commands0-9parameters0-4description"></a><span data-ttu-id="b19ef-144">composeExtensions \\ [0 \\ ] \\ . Commands \\ [[0-9] \\ ] \\ . Parameters \\ [[0-4] \\ ] \\ . Descrição</span><span class="sxs-lookup"><span data-stu-id="b19ef-144">composeExtensions\\[0\\]\\.commands\\[[0-9]\\]\\.parameters\\[[0-4]\\]\\.description</span></span>

<span data-ttu-id="b19ef-145">**Cadeia de caracteres, tamanho máximo 128**</span><span class="sxs-lookup"><span data-stu-id="b19ef-145">**String, Max Length 128**</span></span>

<span data-ttu-id="b19ef-146">Substitui a (s) cadeias de caracteres correspondentes do manifesto do aplicativo pelo valor fornecido aqui.</span><span class="sxs-lookup"><span data-stu-id="b19ef-146">Replaces the corresponding string(s) from the app manifest with the value provided here.</span></span>

## <a name="composeextensions0commands0-9parameters0-4value"></a><span data-ttu-id="b19ef-147">composeExtensions \\ [0 \\ ] \\ . Commands \\ [[0-9] \\ ] \\ . Parameters \\ [[0-4] \\ ] \\ . Value</span><span class="sxs-lookup"><span data-stu-id="b19ef-147">composeExtensions\\[0\\]\\.commands\\[[0-9]\\]\\.parameters\\[[0-4]\\]\\.value</span></span>

<span data-ttu-id="b19ef-148">**Cadeia de caracteres, tamanho máximo 512**</span><span class="sxs-lookup"><span data-stu-id="b19ef-148">**String, Max Length 512**</span></span>

<span data-ttu-id="b19ef-149">Substitui a (s) cadeias de caracteres correspondentes do manifesto do aplicativo pelo valor fornecido aqui.</span><span class="sxs-lookup"><span data-stu-id="b19ef-149">Replaces the corresponding string(s) from the app manifest with the value provided here.</span></span>

## <a name="composeextensions0commands0-9parameters0-4choices0-9title"></a><span data-ttu-id="b19ef-150">composeExtensions \\ [0 \\ ] \\ . Commands \\ [[0-9] \\ ] \\ . Parameters \\ [[0-4] \\ ] \\ . Choices \\ [[0-9] \\ ] \\ . title</span><span class="sxs-lookup"><span data-stu-id="b19ef-150">composeExtensions\\[0\\]\\.commands\\[[0-9]\\]\\.parameters\\[[0-4]\\]\\.choices\\[[0-9]\\]\\.title</span></span>

<span data-ttu-id="b19ef-151">**Cadeia de caracteres, tamanho máximo 128**</span><span class="sxs-lookup"><span data-stu-id="b19ef-151">**String, Max Length 128**</span></span>

<span data-ttu-id="b19ef-152">Substitui a (s) cadeias de caracteres correspondentes do manifesto do aplicativo pelo valor fornecido aqui.</span><span class="sxs-lookup"><span data-stu-id="b19ef-152">Replaces the corresponding string(s) from the app manifest with the value provided here.</span></span>

## <a name="composeextensions0commands0-9taskinfotitle"></a><span data-ttu-id="b19ef-153">composeExtensions \\ [0 \\ ] \\ . Commands \\ [[0-9] \\ ] \\ . TaskInfo \\ . title</span><span class="sxs-lookup"><span data-stu-id="b19ef-153">composeExtensions\\[0\\]\\.commands\\[[0-9]\\]\\.taskInfo\\.title</span></span>

<span data-ttu-id="b19ef-154">**Cadeia de caracteres, tamanho máximo 64**</span><span class="sxs-lookup"><span data-stu-id="b19ef-154">**String, Max Length 64**</span></span>

<span data-ttu-id="b19ef-155">Substitui a (s) cadeias de caracteres correspondentes do manifesto do aplicativo pelo valor fornecido aqui.</span><span class="sxs-lookup"><span data-stu-id="b19ef-155">Replaces the corresponding string(s) from the app manifest with the value provided here.</span></span>
