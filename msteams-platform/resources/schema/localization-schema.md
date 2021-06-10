---
title: Referência de esquema JSON do arquivo de localização
description: Descreve o esquema de localização suportado pelo arquivo de localização para Microsoft Teams
ms.topic: reference
localization_priority: Normal
keywords: Localização de esquema de manifesto do teams
ms.date: 05/20/2019
ms.openlocfilehash: 3e4207fb3e862eac18c80ffc49e7c5648ae05c28
ms.sourcegitcommit: 825abed2f8784d2bab7407ba7a4455ae17bbd28f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2021
ms.locfileid: "52019703"
---
# <a name="reference-localization-file-json-schema"></a><span data-ttu-id="2d07d-104">Referência: esquema JSON do arquivo de localização</span><span class="sxs-lookup"><span data-stu-id="2d07d-104">Reference: Localization file JSON schema</span></span>

<span data-ttu-id="2d07d-105">O Microsoft Teams de localização descreve traduções de idioma que serão atendidas com base nas configurações de idioma do cliente.</span><span class="sxs-lookup"><span data-stu-id="2d07d-105">The Microsoft Teams localization file describes language translations that will be served based on the client language settings.</span></span> <span data-ttu-id="2d07d-106">Seu arquivo deve estar em conformidade com o esquema hospedado em [`https://developer.microsoft.com/en-us/json-schemas/teams/v1.8/MicrosoftTeams.Localization.schema.json`](https://developer.microsoft.com/en-us/json-schemas/teams/v1.8/MicrosoftTeams.Localization.schema.json) .</span><span class="sxs-lookup"><span data-stu-id="2d07d-106">Your file must conform to the schema hosted at [`https://developer.microsoft.com/en-us/json-schemas/teams/v1.8/MicrosoftTeams.Localization.schema.json`](https://developer.microsoft.com/en-us/json-schemas/teams/v1.8/MicrosoftTeams.Localization.schema.json).</span></span> <span data-ttu-id="2d07d-107">Para obter informações adicionais, [consulte localização do aplicativo](~/concepts/build-and-test/apps-localization.md).</span><span class="sxs-lookup"><span data-stu-id="2d07d-107">For additional information see [app localization](~/concepts/build-and-test/apps-localization.md).</span></span>

## <a name="sample"></a><span data-ttu-id="2d07d-108">Amostra</span><span class="sxs-lookup"><span data-stu-id="2d07d-108">Sample</span></span>

```json
{
  "$schema": "https://developer.microsoft.com/json-schemas/teams/v1.8/MicrosoftTeams.schema.json",
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

<span data-ttu-id="2d07d-109">O esquema define as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="2d07d-109">The schema defines the following properties:</span></span>

## <a name="schema"></a><span data-ttu-id="2d07d-110">$schema</span><span class="sxs-lookup"><span data-stu-id="2d07d-110">$schema</span></span>

<span data-ttu-id="2d07d-111">**URI**</span><span class="sxs-lookup"><span data-stu-id="2d07d-111">**URI**</span></span>

<span data-ttu-id="2d07d-112">A https:// URL de referência do Esquema JSON para o manifesto.</span><span class="sxs-lookup"><span data-stu-id="2d07d-112">The https:// URL referencing the JSON Schema for the manifest.</span></span>

> [!TIP]
> <span data-ttu-id="2d07d-113">Especifique o esquema no início do manifesto para habilitar IntelliSense suporte semelhante do editor de código:`"$schema": "https://developer.microsoft.com/json-schemas/teams/v1.8/MicrosoftTeams.schema.json",`</span><span class="sxs-lookup"><span data-stu-id="2d07d-113">Specify the schema at the beginning of your manifest to enable IntelliSense or similar support from your code editor: `"$schema": "https://developer.microsoft.com/json-schemas/teams/v1.8/MicrosoftTeams.schema.json",`</span></span>

## <a name="nameshort"></a><span data-ttu-id="2d07d-114">name.short</span><span class="sxs-lookup"><span data-stu-id="2d07d-114">name.short</span></span>

<span data-ttu-id="2d07d-115">**String, Comprimento Máximo 30**</span><span class="sxs-lookup"><span data-stu-id="2d07d-115">**String, Max Length 30**</span></span>

<span data-ttu-id="2d07d-116">Substitui a cadeia de caracteres correspondente do manifesto do aplicativo pelo valor fornecido aqui.</span><span class="sxs-lookup"><span data-stu-id="2d07d-116">Replaces the corresponding string from the app manifest with the value provided here.</span></span>

## <a name="namefull"></a><span data-ttu-id="2d07d-117">name.full</span><span class="sxs-lookup"><span data-stu-id="2d07d-117">name.full</span></span>

<span data-ttu-id="2d07d-118">**String, Comprimento Máximo 100**</span><span class="sxs-lookup"><span data-stu-id="2d07d-118">**String, Max Length 100**</span></span>

<span data-ttu-id="2d07d-119">Substitui a cadeia de caracteres correspondente do manifesto do aplicativo pelo valor fornecido aqui.</span><span class="sxs-lookup"><span data-stu-id="2d07d-119">Replaces the corresponding string from the app manifest with the value provided here.</span></span>

## <a name="descriptionshort"></a><span data-ttu-id="2d07d-120">description.short</span><span class="sxs-lookup"><span data-stu-id="2d07d-120">description.short</span></span>

<span data-ttu-id="2d07d-121">**String, Comprimento Máximo 80**</span><span class="sxs-lookup"><span data-stu-id="2d07d-121">**String, Max Length 80**</span></span>

<span data-ttu-id="2d07d-122">Substitui a cadeia de caracteres correspondente do manifesto do aplicativo pelo valor fornecido aqui.</span><span class="sxs-lookup"><span data-stu-id="2d07d-122">Replaces the corresponding string from the app manifest with the value provided here.</span></span>

## <a name="descriptionfull"></a><span data-ttu-id="2d07d-123">description.full</span><span class="sxs-lookup"><span data-stu-id="2d07d-123">description.full</span></span>

<span data-ttu-id="2d07d-124">**String, Comprimento Máximo 4000**</span><span class="sxs-lookup"><span data-stu-id="2d07d-124">**String, Max Length 4000**</span></span>

<span data-ttu-id="2d07d-125">Substitui a cadeia de caracteres correspondente do manifesto do aplicativo pelo valor fornecido aqui.</span><span class="sxs-lookup"><span data-stu-id="2d07d-125">Replaces the corresponding string from the app manifest with the value provided here.</span></span>

## <a name="statictabs0-910-5name"></a><span data-ttu-id="2d07d-126">staticTabs \\ [([0-9]|1[0-5]) \\ ] \\ .name</span><span class="sxs-lookup"><span data-stu-id="2d07d-126">staticTabs\\[([0-9]|1[0-5])\\]\\.name</span></span>

<span data-ttu-id="2d07d-127">**String, Comprimento Máximo 128**</span><span class="sxs-lookup"><span data-stu-id="2d07d-127">**String, Max Length 128**</span></span>

<span data-ttu-id="2d07d-128">Substitui as cadeias de caracteres correspondentes do manifesto do aplicativo pelo valor fornecido aqui.</span><span class="sxs-lookup"><span data-stu-id="2d07d-128">Replaces the corresponding string(s) from the app manifest with the value provided here.</span></span>

## <a name="bots0commandlists0-2commands0-9title"></a><span data-ttu-id="2d07d-129">bots \\ [0 \\ ] \\ .commandLists \\ [[0-2] \\ ] \\ .commands \\ [[0-9] \\ ] \\ .title</span><span class="sxs-lookup"><span data-stu-id="2d07d-129">bots\\[0\\]\\.commandLists\\[[0-2]\\]\\.commands\\[[0-9]\\]\\.title</span></span>

<span data-ttu-id="2d07d-130">**String, Comprimento Máximo 32**</span><span class="sxs-lookup"><span data-stu-id="2d07d-130">**String, Max Length 32**</span></span>

<span data-ttu-id="2d07d-131">Substitui as cadeias de caracteres correspondentes do manifesto do aplicativo pelo valor fornecido aqui.</span><span class="sxs-lookup"><span data-stu-id="2d07d-131">Replaces the corresponding string(s) from the app manifest with the value provided here.</span></span>

## <a name="bots0commandlists0-2commands0-9description"></a><span data-ttu-id="2d07d-132">bots \\ [0 \\ ] \\ .commandLists \\ [[0-2] \\ ] \\ .commands \\ [[0-9] \\ ] \\ .description</span><span class="sxs-lookup"><span data-stu-id="2d07d-132">bots\\[0\\]\\.commandLists\\[[0-2]\\]\\.commands\\[[0-9]\\]\\.description</span></span>

<span data-ttu-id="2d07d-133">**String, Comprimento Máximo 128**</span><span class="sxs-lookup"><span data-stu-id="2d07d-133">**String, Max Length 128**</span></span>

<span data-ttu-id="2d07d-134">Substitui as cadeias de caracteres correspondentes do manifesto do aplicativo pelo valor fornecido aqui.</span><span class="sxs-lookup"><span data-stu-id="2d07d-134">Replaces the corresponding string(s) from the app manifest with the value provided here.</span></span>

## <a name="composeextensions0commands0-9title"></a><span data-ttu-id="2d07d-135">composeExtensions \\ [0 \\ ] \\ .commands \\ [[0-9] \\ ] \\ .title</span><span class="sxs-lookup"><span data-stu-id="2d07d-135">composeExtensions\\[0\\]\\.commands\\[[0-9]\\]\\.title</span></span>

<span data-ttu-id="2d07d-136">**String, Comprimento Máximo 32**</span><span class="sxs-lookup"><span data-stu-id="2d07d-136">**String, Max Length 32**</span></span>

<span data-ttu-id="2d07d-137">Substitui as cadeias de caracteres correspondentes do manifesto do aplicativo pelo valor fornecido aqui.</span><span class="sxs-lookup"><span data-stu-id="2d07d-137">Replaces the corresponding string(s) from the app manifest with the value provided here.</span></span>

## <a name="composeextensions0commands0-9description"></a><span data-ttu-id="2d07d-138">composeExtensions \\ [0 \\ ] \\ .commands \\ [[0-9] \\ ] \\ .description</span><span class="sxs-lookup"><span data-stu-id="2d07d-138">composeExtensions\\[0\\]\\.commands\\[[0-9]\\]\\.description</span></span>

<span data-ttu-id="2d07d-139">**String, Comprimento Máximo 128**</span><span class="sxs-lookup"><span data-stu-id="2d07d-139">**String, Max Length 128**</span></span>

<span data-ttu-id="2d07d-140">Substitui as cadeias de caracteres correspondentes do manifesto do aplicativo pelo valor fornecido aqui.</span><span class="sxs-lookup"><span data-stu-id="2d07d-140">Replaces the corresponding string(s) from the app manifest with the value provided here.</span></span>

## <a name="composeextensions0commands0-9parameters0-4title"></a><span data-ttu-id="2d07d-141">composeExtensions \\ [0 \\ ] \\ .commands \\ [[0-9] \\ ] \\ .parameters \\ [[0-4] \\ ] \\ .title</span><span class="sxs-lookup"><span data-stu-id="2d07d-141">composeExtensions\\[0\\]\\.commands\\[[0-9]\\]\\.parameters\\[[0-4]\\]\\.title</span></span>

<span data-ttu-id="2d07d-142">**String, Comprimento Máximo 32**</span><span class="sxs-lookup"><span data-stu-id="2d07d-142">**String, Max Length 32**</span></span>

<span data-ttu-id="2d07d-143">Substitui as cadeias de caracteres correspondentes do manifesto do aplicativo pelo valor fornecido aqui.</span><span class="sxs-lookup"><span data-stu-id="2d07d-143">Replaces the corresponding string(s) from the app manifest with the value provided here.</span></span>

## <a name="composeextensions0commands0-9parameters0-4description"></a><span data-ttu-id="2d07d-144">composeExtensions \\ [0 \\ ] \\ .commands \\ [[0-9] \\ ] \\ .parameters \\ [[0-4] \\ ] \\ .description</span><span class="sxs-lookup"><span data-stu-id="2d07d-144">composeExtensions\\[0\\]\\.commands\\[[0-9]\\]\\.parameters\\[[0-4]\\]\\.description</span></span>

<span data-ttu-id="2d07d-145">**String, Comprimento Máximo 128**</span><span class="sxs-lookup"><span data-stu-id="2d07d-145">**String, Max Length 128**</span></span>

<span data-ttu-id="2d07d-146">Substitui as cadeias de caracteres correspondentes do manifesto do aplicativo pelo valor fornecido aqui.</span><span class="sxs-lookup"><span data-stu-id="2d07d-146">Replaces the corresponding string(s) from the app manifest with the value provided here.</span></span>

## <a name="composeextensions0commands0-9parameters0-4value"></a><span data-ttu-id="2d07d-147">composeExtensions \\ [0 \\ ] \\ .commands \\ [[0-9] \\ ] \\ .parameters \\ [[0-4] \\ ] \\ .value</span><span class="sxs-lookup"><span data-stu-id="2d07d-147">composeExtensions\\[0\\]\\.commands\\[[0-9]\\]\\.parameters\\[[0-4]\\]\\.value</span></span>

<span data-ttu-id="2d07d-148">**String, Comprimento Máximo 512**</span><span class="sxs-lookup"><span data-stu-id="2d07d-148">**String, Max Length 512**</span></span>

<span data-ttu-id="2d07d-149">Substitui as cadeias de caracteres correspondentes do manifesto do aplicativo pelo valor fornecido aqui.</span><span class="sxs-lookup"><span data-stu-id="2d07d-149">Replaces the corresponding string(s) from the app manifest with the value provided here.</span></span>

## <a name="composeextensions0commands0-9parameters0-4choices0-9title"></a><span data-ttu-id="2d07d-150">composeExtensions \\ [0 \\ ] \\ .commands \\ [[0-9] \\ ] \\ .parameters \\ [[0-4] \\ ] \\ .choices \\ [[0-9] \\ ] \\ .title</span><span class="sxs-lookup"><span data-stu-id="2d07d-150">composeExtensions\\[0\\]\\.commands\\[[0-9]\\]\\.parameters\\[[0-4]\\]\\.choices\\[[0-9]\\]\\.title</span></span>

<span data-ttu-id="2d07d-151">**String, Comprimento Máximo 128**</span><span class="sxs-lookup"><span data-stu-id="2d07d-151">**String, Max Length 128**</span></span>

<span data-ttu-id="2d07d-152">Substitui as cadeias de caracteres correspondentes do manifesto do aplicativo pelo valor fornecido aqui.</span><span class="sxs-lookup"><span data-stu-id="2d07d-152">Replaces the corresponding string(s) from the app manifest with the value provided here.</span></span>

## <a name="composeextensions0commands0-9taskinfotitle"></a><span data-ttu-id="2d07d-153">composeExtensions \\ [0 \\ ] \\ .commands \\ [[0-9] \\ ] \\ .taskInfo \\ .title</span><span class="sxs-lookup"><span data-stu-id="2d07d-153">composeExtensions\\[0\\]\\.commands\\[[0-9]\\]\\.taskInfo\\.title</span></span>

<span data-ttu-id="2d07d-154">**String, Comprimento Máximo 64**</span><span class="sxs-lookup"><span data-stu-id="2d07d-154">**String, Max Length 64**</span></span>

<span data-ttu-id="2d07d-155">Substitui as cadeias de caracteres correspondentes do manifesto do aplicativo pelo valor fornecido aqui.</span><span class="sxs-lookup"><span data-stu-id="2d07d-155">Replaces the corresponding string(s) from the app manifest with the value provided here.</span></span>
