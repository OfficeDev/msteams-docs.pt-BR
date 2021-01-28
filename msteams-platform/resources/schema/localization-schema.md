---
title: Referência de esquema JSON do arquivo de localização
description: Descreve o esquema de localização suportado pelo arquivo de localização do Microsoft Teams
ms.topic: reference
keywords: localização do esquema de manifesto do teams
ms.date: 05/20/2019
ms.openlocfilehash: 696a65de70a63e767f8fcdb040364fe90cde8716
ms.sourcegitcommit: 976e870cc925f61b76c3830ec04ba6e4bdfde32f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/27/2021
ms.locfileid: "50014597"
---
# <a name="reference-localization-file-json-schema"></a><span data-ttu-id="5d70a-104">Referência: Esquema JSON do arquivo de localização</span><span class="sxs-lookup"><span data-stu-id="5d70a-104">Reference: Localization file JSON schema</span></span>

<span data-ttu-id="5d70a-105">O arquivo de localização do Microsoft Teams descreve traduções de idioma que serão atendidas com base nas configurações de idioma do cliente.</span><span class="sxs-lookup"><span data-stu-id="5d70a-105">The Microsoft Teams localization file describes language translations that will be served based on the client language settings.</span></span> <span data-ttu-id="5d70a-106">Seu arquivo deve estar em conformidade com o esquema hospedado em [`https://developer.microsoft.com/en-us/json-schemas/teams/v1.8/MicrosoftTeams.Localization.schema.json`](https://developer.microsoft.com/en-us/json-schemas/teams/v1.8/MicrosoftTeams.Localization.schema.json) .</span><span class="sxs-lookup"><span data-stu-id="5d70a-106">Your file must conform to the schema hosted at [`https://developer.microsoft.com/en-us/json-schemas/teams/v1.8/MicrosoftTeams.Localization.schema.json`](https://developer.microsoft.com/en-us/json-schemas/teams/v1.8/MicrosoftTeams.Localization.schema.json).</span></span> <span data-ttu-id="5d70a-107">Para obter informações adicionais, [consulte localização do aplicativo.](~/concepts/build-and-test/apps-localization.md)</span><span class="sxs-lookup"><span data-stu-id="5d70a-107">For additional information see [app localization](~/concepts/build-and-test/apps-localization.md).</span></span>

## <a name="sample"></a><span data-ttu-id="5d70a-108">Amostra</span><span class="sxs-lookup"><span data-stu-id="5d70a-108">Sample</span></span>

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

<span data-ttu-id="5d70a-109">O esquema define as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="5d70a-109">The schema defines the following properties:</span></span>

## <a name="schema"></a><span data-ttu-id="5d70a-110">$schema</span><span class="sxs-lookup"><span data-stu-id="5d70a-110">$schema</span></span>

<span data-ttu-id="5d70a-111">**URI**</span><span class="sxs-lookup"><span data-stu-id="5d70a-111">**URI**</span></span>

<span data-ttu-id="5d70a-112">A https:// URL que referencia o esquema JSON para o manifesto.</span><span class="sxs-lookup"><span data-stu-id="5d70a-112">The https:// URL referencing the JSON Schema for the manifest.</span></span>

> [!TIP]
> <span data-ttu-id="5d70a-113">Especifique o esquema no início do manifesto para habilitar o IntelliSense ou suporte semelhante do seu editor de código: `"$schema": "https://developer.microsoft.com/json-schemas/teams/v1.8/MicrosoftTeams.schema.json",`</span><span class="sxs-lookup"><span data-stu-id="5d70a-113">Specify the schema at the beginning of your manifest to enable IntelliSense or similar support from your code editor: `"$schema": "https://developer.microsoft.com/json-schemas/teams/v1.8/MicrosoftTeams.schema.json",`</span></span>

## <a name="nameshort"></a><span data-ttu-id="5d70a-114">name.short</span><span class="sxs-lookup"><span data-stu-id="5d70a-114">name.short</span></span>

<span data-ttu-id="5d70a-115">**Cadeia de caracteres, Comprimento Máximo 30**</span><span class="sxs-lookup"><span data-stu-id="5d70a-115">**String, Max Length 30**</span></span>

<span data-ttu-id="5d70a-116">Substitui a cadeia de caracteres correspondente do manifesto do aplicativo pelo valor fornecido aqui.</span><span class="sxs-lookup"><span data-stu-id="5d70a-116">Replaces the corresponding string from the app manifest with the value provided here.</span></span>

## <a name="namefull"></a><span data-ttu-id="5d70a-117">name.full</span><span class="sxs-lookup"><span data-stu-id="5d70a-117">name.full</span></span>

<span data-ttu-id="5d70a-118">**Cadeia de caracteres, Comprimento Máximo 100**</span><span class="sxs-lookup"><span data-stu-id="5d70a-118">**String, Max Length 100**</span></span>

<span data-ttu-id="5d70a-119">Substitui a cadeia de caracteres correspondente do manifesto do aplicativo pelo valor fornecido aqui.</span><span class="sxs-lookup"><span data-stu-id="5d70a-119">Replaces the corresponding string from the app manifest with the value provided here.</span></span>

## <a name="descriptionshort"></a><span data-ttu-id="5d70a-120">description.short</span><span class="sxs-lookup"><span data-stu-id="5d70a-120">description.short</span></span>

<span data-ttu-id="5d70a-121">**Cadeia de caracteres, Comprimento Máximo 80**</span><span class="sxs-lookup"><span data-stu-id="5d70a-121">**String, Max Length 80**</span></span>

<span data-ttu-id="5d70a-122">Substitui a cadeia de caracteres correspondente do manifesto do aplicativo pelo valor fornecido aqui.</span><span class="sxs-lookup"><span data-stu-id="5d70a-122">Replaces the corresponding string from the app manifest with the value provided here.</span></span>

## <a name="descriptionfull"></a><span data-ttu-id="5d70a-123">description.full</span><span class="sxs-lookup"><span data-stu-id="5d70a-123">description.full</span></span>

<span data-ttu-id="5d70a-124">**String, Max Length 4000**</span><span class="sxs-lookup"><span data-stu-id="5d70a-124">**String, Max Length 4000**</span></span>

<span data-ttu-id="5d70a-125">Substitui a cadeia de caracteres correspondente do manifesto do aplicativo pelo valor fornecido aqui.</span><span class="sxs-lookup"><span data-stu-id="5d70a-125">Replaces the corresponding string from the app manifest with the value provided here.</span></span>

## <a name="statictabs0-910-5name"></a><span data-ttu-id="5d70a-126">staticTabs \\ [([0-9]|1[0-5]) \\ ] \\ .name</span><span class="sxs-lookup"><span data-stu-id="5d70a-126">staticTabs\\[([0-9]|1[0-5])\\]\\.name</span></span>

<span data-ttu-id="5d70a-127">**Cadeia de caracteres, Comprimento Máximo 128**</span><span class="sxs-lookup"><span data-stu-id="5d70a-127">**String, Max Length 128**</span></span>

<span data-ttu-id="5d70a-128">Substitui as cadeias de caracteres correspondentes do manifesto do aplicativo pelo valor fornecido aqui.</span><span class="sxs-lookup"><span data-stu-id="5d70a-128">Replaces the corresponding string(s) from the app manifest with the value provided here.</span></span>

## <a name="bots0commandlists0-2commands0-9title"></a><span data-ttu-id="5d70a-129">bots \\ [0 \\ ] \\ .commandLists \\ [[0-2] \\ ] \\ .commands \\ [[0-9] \\ ] \\ .title</span><span class="sxs-lookup"><span data-stu-id="5d70a-129">bots\\[0\\]\\.commandLists\\[[0-2]\\]\\.commands\\[[0-9]\\]\\.title</span></span>

<span data-ttu-id="5d70a-130">**String, Max Length 32**</span><span class="sxs-lookup"><span data-stu-id="5d70a-130">**String, Max Length 32**</span></span>

<span data-ttu-id="5d70a-131">Substitui as cadeias de caracteres correspondentes do manifesto do aplicativo pelo valor fornecido aqui.</span><span class="sxs-lookup"><span data-stu-id="5d70a-131">Replaces the corresponding string(s) from the app manifest with the value provided here.</span></span>

## <a name="bots0commandlists0-2commands0-9description"></a><span data-ttu-id="5d70a-132">bots \\ [0 \\ ] \\ .commandLists \\ [[0-2] \\ ] \\ .commands \\ [[0-9] \\ ] \\ .description</span><span class="sxs-lookup"><span data-stu-id="5d70a-132">bots\\[0\\]\\.commandLists\\[[0-2]\\]\\.commands\\[[0-9]\\]\\.description</span></span>

<span data-ttu-id="5d70a-133">**Cadeia de caracteres, Comprimento Máximo 128**</span><span class="sxs-lookup"><span data-stu-id="5d70a-133">**String, Max Length 128**</span></span>

<span data-ttu-id="5d70a-134">Substitui as cadeias de caracteres correspondentes do manifesto do aplicativo pelo valor fornecido aqui.</span><span class="sxs-lookup"><span data-stu-id="5d70a-134">Replaces the corresponding string(s) from the app manifest with the value provided here.</span></span>

## <a name="composeextensions0commands0-9title"></a><span data-ttu-id="5d70a-135">composeExtensions \\ [0 \\ ] \\ .commands \\ [[0-9] \\ ] \\ .title</span><span class="sxs-lookup"><span data-stu-id="5d70a-135">composeExtensions\\[0\\]\\.commands\\[[0-9]\\]\\.title</span></span>

<span data-ttu-id="5d70a-136">**String, Max Length 32**</span><span class="sxs-lookup"><span data-stu-id="5d70a-136">**String, Max Length 32**</span></span>

<span data-ttu-id="5d70a-137">Substitui as cadeias de caracteres correspondentes do manifesto do aplicativo pelo valor fornecido aqui.</span><span class="sxs-lookup"><span data-stu-id="5d70a-137">Replaces the corresponding string(s) from the app manifest with the value provided here.</span></span>

## <a name="composeextensions0commands0-9description"></a><span data-ttu-id="5d70a-138">composeExtensions \\ [0 \\ ] \\ .commands \\ [[0-9] \\ ] \\ .description</span><span class="sxs-lookup"><span data-stu-id="5d70a-138">composeExtensions\\[0\\]\\.commands\\[[0-9]\\]\\.description</span></span>

<span data-ttu-id="5d70a-139">**Cadeia de caracteres, Comprimento Máximo 128**</span><span class="sxs-lookup"><span data-stu-id="5d70a-139">**String, Max Length 128**</span></span>

<span data-ttu-id="5d70a-140">Substitui as cadeias de caracteres correspondentes do manifesto do aplicativo pelo valor fornecido aqui.</span><span class="sxs-lookup"><span data-stu-id="5d70a-140">Replaces the corresponding string(s) from the app manifest with the value provided here.</span></span>

## <a name="composeextensions0commands0-9parameters0-4title"></a><span data-ttu-id="5d70a-141">composeExtensions \\ [0 \\ ] \\ .commands \\ [[0-9] \\ ] \\ .parameters \\ [[0-4] \\ ] \\ .title</span><span class="sxs-lookup"><span data-stu-id="5d70a-141">composeExtensions\\[0\\]\\.commands\\[[0-9]\\]\\.parameters\\[[0-4]\\]\\.title</span></span>

<span data-ttu-id="5d70a-142">**Cadeia de caracteres, Comprimento Máximo 32**</span><span class="sxs-lookup"><span data-stu-id="5d70a-142">**String, Max Length 32**</span></span>

<span data-ttu-id="5d70a-143">Substitui as cadeias de caracteres correspondentes do manifesto do aplicativo pelo valor fornecido aqui.</span><span class="sxs-lookup"><span data-stu-id="5d70a-143">Replaces the corresponding string(s) from the app manifest with the value provided here.</span></span>

## <a name="composeextensions0commands0-9parameters0-4description"></a><span data-ttu-id="5d70a-144">composeExtensions \\ [0 \\ ] \\ .commands \\ [[0-9] \\ ] \\ .parameters \\ [[0-4] \\ ] \\ .description</span><span class="sxs-lookup"><span data-stu-id="5d70a-144">composeExtensions\\[0\\]\\.commands\\[[0-9]\\]\\.parameters\\[[0-4]\\]\\.description</span></span>

<span data-ttu-id="5d70a-145">**Cadeia de caracteres, Comprimento Máximo 128**</span><span class="sxs-lookup"><span data-stu-id="5d70a-145">**String, Max Length 128**</span></span>

<span data-ttu-id="5d70a-146">Substitui as cadeias de caracteres correspondentes do manifesto do aplicativo pelo valor fornecido aqui.</span><span class="sxs-lookup"><span data-stu-id="5d70a-146">Replaces the corresponding string(s) from the app manifest with the value provided here.</span></span>

## <a name="composeextensions0commands0-9parameters0-4value"></a><span data-ttu-id="5d70a-147">composeExtensions \\ [0 \\ ] \\ .commands \\ [[0-9] \\ ] \\ .parameters \\ [[0-4] \\ ] \\ .value</span><span class="sxs-lookup"><span data-stu-id="5d70a-147">composeExtensions\\[0\\]\\.commands\\[[0-9]\\]\\.parameters\\[[0-4]\\]\\.value</span></span>

<span data-ttu-id="5d70a-148">**String, Max Length 512**</span><span class="sxs-lookup"><span data-stu-id="5d70a-148">**String, Max Length 512**</span></span>

<span data-ttu-id="5d70a-149">Substitui as cadeias de caracteres correspondentes do manifesto do aplicativo pelo valor fornecido aqui.</span><span class="sxs-lookup"><span data-stu-id="5d70a-149">Replaces the corresponding string(s) from the app manifest with the value provided here.</span></span>

## <a name="composeextensions0commands0-9parameters0-4choices0-9title"></a><span data-ttu-id="5d70a-150">composeExtensions \\ [0 \\ ] \\ .commands \\ [[0-9] \\ ] \\ .parameters \\ [[0-4] \\ ] \\ .choices \\ [[0-9] \\ ] \\ .title</span><span class="sxs-lookup"><span data-stu-id="5d70a-150">composeExtensions\\[0\\]\\.commands\\[[0-9]\\]\\.parameters\\[[0-4]\\]\\.choices\\[[0-9]\\]\\.title</span></span>

<span data-ttu-id="5d70a-151">**Cadeia de caracteres, Comprimento Máximo 128**</span><span class="sxs-lookup"><span data-stu-id="5d70a-151">**String, Max Length 128**</span></span>

<span data-ttu-id="5d70a-152">Substitui as cadeias de caracteres correspondentes do manifesto do aplicativo pelo valor fornecido aqui.</span><span class="sxs-lookup"><span data-stu-id="5d70a-152">Replaces the corresponding string(s) from the app manifest with the value provided here.</span></span>

## <a name="composeextensions0commands0-9taskinfotitle"></a><span data-ttu-id="5d70a-153">composeExtensions \\ [0 \\ ] \\ .commands \\ [[0-9] \\ ] \\ .taskInfo \\ .title</span><span class="sxs-lookup"><span data-stu-id="5d70a-153">composeExtensions\\[0\\]\\.commands\\[[0-9]\\]\\.taskInfo\\.title</span></span>

<span data-ttu-id="5d70a-154">**String, Max Length 64**</span><span class="sxs-lookup"><span data-stu-id="5d70a-154">**String, Max Length 64**</span></span>

<span data-ttu-id="5d70a-155">Substitui as cadeias de caracteres correspondentes do manifesto do aplicativo pelo valor fornecido aqui.</span><span class="sxs-lookup"><span data-stu-id="5d70a-155">Replaces the corresponding string(s) from the app manifest with the value provided here.</span></span>
