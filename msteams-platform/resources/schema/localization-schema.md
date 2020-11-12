---
title: Referência de esquema JSON de arquivo de localização
description: Descreve o esquema de localização suportado pelo arquivo de localização para o Microsoft Teams
keywords: Localização do esquema do manifesto do teams
ms.date: 05/20/2019
ms.openlocfilehash: 2c0f449ef0b018e0ed377ea8f5d79b285b36e829
ms.sourcegitcommit: 0aeb60027f423d8ceff3b377db8c3efbb6da4d17
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/11/2020
ms.locfileid: "48997962"
---
# <a name="reference-localization-file-json-schema"></a><span data-ttu-id="b5fb9-104">Referência: esquema JSON do arquivo de localização</span><span class="sxs-lookup"><span data-stu-id="b5fb9-104">Reference: Localization file JSON schema</span></span>

<span data-ttu-id="b5fb9-105">O arquivo de localização do Microsoft Teams descreve as traduções de idioma que serão atendidas com base nas configurações de idioma do cliente.</span><span class="sxs-lookup"><span data-stu-id="b5fb9-105">The Microsoft Teams localization file describes language translations that will be served based on the client language settings.</span></span> <span data-ttu-id="b5fb9-106">O arquivo deve estar em conformidade com o esquema hospedado em [`https://developer.microsoft.com/en-us/json-schemas/teams/v1.8/MicrosoftTeams.Localization.schema.json`](https://developer.microsoft.com/en-us/json-schemas/teams/v1.8/MicrosoftTeams.Localization.schema.json) .</span><span class="sxs-lookup"><span data-stu-id="b5fb9-106">Your file must conform to the schema hosted at [`https://developer.microsoft.com/en-us/json-schemas/teams/v1.8/MicrosoftTeams.Localization.schema.json`](https://developer.microsoft.com/en-us/json-schemas/teams/v1.8/MicrosoftTeams.Localization.schema.json).</span></span> <span data-ttu-id="b5fb9-107">Para obter informações adicionais, consulte [localização de aplicativos](~/concepts/build-and-test/apps-localization.md).</span><span class="sxs-lookup"><span data-stu-id="b5fb9-107">For additional information see [app localization](~/concepts/build-and-test/apps-localization.md).</span></span>

## <a name="sample"></a><span data-ttu-id="b5fb9-108">Amostra</span><span class="sxs-lookup"><span data-stu-id="b5fb9-108">Sample</span></span>

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

<span data-ttu-id="b5fb9-109">O esquema define as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="b5fb9-109">The schema defines the following properties:</span></span>

## <a name="schema"></a><span data-ttu-id="b5fb9-110">$schema</span><span class="sxs-lookup"><span data-stu-id="b5fb9-110">$schema</span></span>

<span data-ttu-id="b5fb9-111">**URI**</span><span class="sxs-lookup"><span data-stu-id="b5fb9-111">**URI**</span></span>

<span data-ttu-id="b5fb9-112">A URL https://que faz referência ao esquema JSON para o manifesto.</span><span class="sxs-lookup"><span data-stu-id="b5fb9-112">The https:// URL referencing the JSON Schema for the manifest.</span></span>

> [!TIP]
> <span data-ttu-id="b5fb9-113">Especifique o esquema no início do manifesto para habilitar o IntelliSense ou suporte semelhante do editor de código: `"$schema": "https://developer.microsoft.com/json-schemas/teams/v1.8/MicrosoftTeams.schema.json",`</span><span class="sxs-lookup"><span data-stu-id="b5fb9-113">Specify the schema at the beginning of your manifest to enable IntelliSense or similar support from your code editor: `"$schema": "https://developer.microsoft.com/json-schemas/teams/v1.8/MicrosoftTeams.schema.json",`</span></span>

## <a name="nameshort"></a><span data-ttu-id="b5fb9-114">Name. short</span><span class="sxs-lookup"><span data-stu-id="b5fb9-114">name.short</span></span>

<span data-ttu-id="b5fb9-115">**Cadeia de caracteres, tamanho máximo 30**</span><span class="sxs-lookup"><span data-stu-id="b5fb9-115">**String, Max Length 30**</span></span>

<span data-ttu-id="b5fb9-116">Substitui a cadeia de caracteres correspondente do manifesto do aplicativo pelo valor fornecido aqui.</span><span class="sxs-lookup"><span data-stu-id="b5fb9-116">Replaces the corresponding string from the app manifest with the value provided here.</span></span>

## <a name="namefull"></a><span data-ttu-id="b5fb9-117">nome. Full</span><span class="sxs-lookup"><span data-stu-id="b5fb9-117">name.full</span></span>

<span data-ttu-id="b5fb9-118">**Cadeia de caracteres, tamanho máximo 100**</span><span class="sxs-lookup"><span data-stu-id="b5fb9-118">**String, Max Length 100**</span></span>

<span data-ttu-id="b5fb9-119">Substitui a cadeia de caracteres correspondente do manifesto do aplicativo pelo valor fornecido aqui.</span><span class="sxs-lookup"><span data-stu-id="b5fb9-119">Replaces the corresponding string from the app manifest with the value provided here.</span></span>

## <a name="descriptionshort"></a><span data-ttu-id="b5fb9-120">Descrição. short</span><span class="sxs-lookup"><span data-stu-id="b5fb9-120">description.short</span></span>

<span data-ttu-id="b5fb9-121">**Cadeia de caracteres, tamanho máximo 80**</span><span class="sxs-lookup"><span data-stu-id="b5fb9-121">**String, Max Length 80**</span></span>

<span data-ttu-id="b5fb9-122">Substitui a cadeia de caracteres correspondente do manifesto do aplicativo pelo valor fornecido aqui.</span><span class="sxs-lookup"><span data-stu-id="b5fb9-122">Replaces the corresponding string from the app manifest with the value provided here.</span></span>

## <a name="descriptionfull"></a><span data-ttu-id="b5fb9-123">Descrição. Full</span><span class="sxs-lookup"><span data-stu-id="b5fb9-123">description.full</span></span>

<span data-ttu-id="b5fb9-124">**Cadeia de caracteres, tamanho máximo 4000**</span><span class="sxs-lookup"><span data-stu-id="b5fb9-124">**String, Max Length 4000**</span></span>

<span data-ttu-id="b5fb9-125">Substitui a cadeia de caracteres correspondente do manifesto do aplicativo pelo valor fornecido aqui.</span><span class="sxs-lookup"><span data-stu-id="b5fb9-125">Replaces the corresponding string from the app manifest with the value provided here.</span></span>

## <a name="statictabs0-910-5name"></a><span data-ttu-id="b5fb9-126">staticTabs \\ [([0-9] | 1 [0-5]) \\ ] \\ . nome</span><span class="sxs-lookup"><span data-stu-id="b5fb9-126">staticTabs\\[([0-9]|1[0-5])\\]\\.name</span></span>

<span data-ttu-id="b5fb9-127">**Cadeia de caracteres, tamanho máximo 128**</span><span class="sxs-lookup"><span data-stu-id="b5fb9-127">**String, Max Length 128**</span></span>

<span data-ttu-id="b5fb9-128">Substitui a (s) cadeias de caracteres correspondentes do manifesto do aplicativo pelo valor fornecido aqui.</span><span class="sxs-lookup"><span data-stu-id="b5fb9-128">Replaces the corresponding string(s) from the app manifest with the value provided here.</span></span>

## <a name="bots0commandlists0-2commands0-9title"></a><span data-ttu-id="b5fb9-129">bots \\ [0 \\ ] \\ . commandLists \\ [[0-2] \\ ] \\ . Commands \\ [[0-9] \\ ] \\ . título</span><span class="sxs-lookup"><span data-stu-id="b5fb9-129">bots\\[0\\]\\.commandLists\\[[0-2]\\]\\.commands\\[[0-9]\\]\\.title</span></span>

<span data-ttu-id="b5fb9-130">**Cadeia de caracteres, tamanho máximo 32**</span><span class="sxs-lookup"><span data-stu-id="b5fb9-130">**String, Max Length 32**</span></span>

<span data-ttu-id="b5fb9-131">Substitui a (s) cadeias de caracteres correspondentes do manifesto do aplicativo pelo valor fornecido aqui.</span><span class="sxs-lookup"><span data-stu-id="b5fb9-131">Replaces the corresponding string(s) from the app manifest with the value provided here.</span></span>

## <a name="bots0commandlists0-2commands0-9description"></a><span data-ttu-id="b5fb9-132">bots \\ [0 \\ ] \\ . commandLists \\ [[0-2] \\ ] \\ . Commands \\ [[0-9] \\ ] \\ . Descrição</span><span class="sxs-lookup"><span data-stu-id="b5fb9-132">bots\\[0\\]\\.commandLists\\[[0-2]\\]\\.commands\\[[0-9]\\]\\.description</span></span>

<span data-ttu-id="b5fb9-133">**Cadeia de caracteres, tamanho máximo 128**</span><span class="sxs-lookup"><span data-stu-id="b5fb9-133">**String, Max Length 128**</span></span>

<span data-ttu-id="b5fb9-134">Substitui a (s) cadeias de caracteres correspondentes do manifesto do aplicativo pelo valor fornecido aqui.</span><span class="sxs-lookup"><span data-stu-id="b5fb9-134">Replaces the corresponding string(s) from the app manifest with the value provided here.</span></span>

## <a name="composeextensions0commands0-9title"></a><span data-ttu-id="b5fb9-135">composeExtensions \\ [0 \\ ] \\ . Commands \\ [[0-9] \\ ] \\ . title</span><span class="sxs-lookup"><span data-stu-id="b5fb9-135">composeExtensions\\[0\\]\\.commands\\[[0-9]\\]\\.title</span></span>

<span data-ttu-id="b5fb9-136">**Cadeia de caracteres, tamanho máximo 32**</span><span class="sxs-lookup"><span data-stu-id="b5fb9-136">**String, Max Length 32**</span></span>

<span data-ttu-id="b5fb9-137">Substitui a (s) cadeias de caracteres correspondentes do manifesto do aplicativo pelo valor fornecido aqui.</span><span class="sxs-lookup"><span data-stu-id="b5fb9-137">Replaces the corresponding string(s) from the app manifest with the value provided here.</span></span>

## <a name="composeextensions0commands0-9description"></a><span data-ttu-id="b5fb9-138">composeExtensions \\ [0 \\ ] \\ . Commands \\ [[0-9] \\ ] \\ . Descrição</span><span class="sxs-lookup"><span data-stu-id="b5fb9-138">composeExtensions\\[0\\]\\.commands\\[[0-9]\\]\\.description</span></span>

<span data-ttu-id="b5fb9-139">**Cadeia de caracteres, tamanho máximo 128**</span><span class="sxs-lookup"><span data-stu-id="b5fb9-139">**String, Max Length 128**</span></span>

<span data-ttu-id="b5fb9-140">Substitui a (s) cadeias de caracteres correspondentes do manifesto do aplicativo pelo valor fornecido aqui.</span><span class="sxs-lookup"><span data-stu-id="b5fb9-140">Replaces the corresponding string(s) from the app manifest with the value provided here.</span></span>

## <a name="composeextensions0commands0-9parameters0-4title"></a><span data-ttu-id="b5fb9-141">composeExtensions \\ [0 \\ ] \\ . Commands \\ [[0-9] \\ ] \\ . Parameters \\ [[0-4] \\ ] \\ . title</span><span class="sxs-lookup"><span data-stu-id="b5fb9-141">composeExtensions\\[0\\]\\.commands\\[[0-9]\\]\\.parameters\\[[0-4]\\]\\.title</span></span>

<span data-ttu-id="b5fb9-142">**Cadeia de caracteres, tamanho máximo 32**</span><span class="sxs-lookup"><span data-stu-id="b5fb9-142">**String, Max Length 32**</span></span>

<span data-ttu-id="b5fb9-143">Substitui a (s) cadeias de caracteres correspondentes do manifesto do aplicativo pelo valor fornecido aqui.</span><span class="sxs-lookup"><span data-stu-id="b5fb9-143">Replaces the corresponding string(s) from the app manifest with the value provided here.</span></span>

## <a name="composeextensions0commands0-9parameters0-4description"></a><span data-ttu-id="b5fb9-144">composeExtensions \\ [0 \\ ] \\ . Commands \\ [[0-9] \\ ] \\ . Parameters \\ [[0-4] \\ ] \\ . Descrição</span><span class="sxs-lookup"><span data-stu-id="b5fb9-144">composeExtensions\\[0\\]\\.commands\\[[0-9]\\]\\.parameters\\[[0-4]\\]\\.description</span></span>

<span data-ttu-id="b5fb9-145">**Cadeia de caracteres, tamanho máximo 128**</span><span class="sxs-lookup"><span data-stu-id="b5fb9-145">**String, Max Length 128**</span></span>

<span data-ttu-id="b5fb9-146">Substitui a (s) cadeias de caracteres correspondentes do manifesto do aplicativo pelo valor fornecido aqui.</span><span class="sxs-lookup"><span data-stu-id="b5fb9-146">Replaces the corresponding string(s) from the app manifest with the value provided here.</span></span>

## <a name="composeextensions0commands0-9parameters0-4value"></a><span data-ttu-id="b5fb9-147">composeExtensions \\ [0 \\ ] \\ . Commands \\ [[0-9] \\ ] \\ . Parameters \\ [[0-4] \\ ] \\ . Value</span><span class="sxs-lookup"><span data-stu-id="b5fb9-147">composeExtensions\\[0\\]\\.commands\\[[0-9]\\]\\.parameters\\[[0-4]\\]\\.value</span></span>

<span data-ttu-id="b5fb9-148">**Cadeia de caracteres, tamanho máximo 512**</span><span class="sxs-lookup"><span data-stu-id="b5fb9-148">**String, Max Length 512**</span></span>

<span data-ttu-id="b5fb9-149">Substitui a (s) cadeias de caracteres correspondentes do manifesto do aplicativo pelo valor fornecido aqui.</span><span class="sxs-lookup"><span data-stu-id="b5fb9-149">Replaces the corresponding string(s) from the app manifest with the value provided here.</span></span>

## <a name="composeextensions0commands0-9parameters0-4choices0-9title"></a><span data-ttu-id="b5fb9-150">composeExtensions \\ [0 \\ ] \\ . Commands \\ [[0-9] \\ ] \\ . Parameters \\ [[0-4] \\ ] \\ . Choices \\ [[0-9] \\ ] \\ . title</span><span class="sxs-lookup"><span data-stu-id="b5fb9-150">composeExtensions\\[0\\]\\.commands\\[[0-9]\\]\\.parameters\\[[0-4]\\]\\.choices\\[[0-9]\\]\\.title</span></span>

<span data-ttu-id="b5fb9-151">**Cadeia de caracteres, tamanho máximo 128**</span><span class="sxs-lookup"><span data-stu-id="b5fb9-151">**String, Max Length 128**</span></span>

<span data-ttu-id="b5fb9-152">Substitui a (s) cadeias de caracteres correspondentes do manifesto do aplicativo pelo valor fornecido aqui.</span><span class="sxs-lookup"><span data-stu-id="b5fb9-152">Replaces the corresponding string(s) from the app manifest with the value provided here.</span></span>

## <a name="composeextensions0commands0-9taskinfotitle"></a><span data-ttu-id="b5fb9-153">composeExtensions \\ [0 \\ ] \\ . Commands \\ [[0-9] \\ ] \\ . TaskInfo \\ . title</span><span class="sxs-lookup"><span data-stu-id="b5fb9-153">composeExtensions\\[0\\]\\.commands\\[[0-9]\\]\\.taskInfo\\.title</span></span>

<span data-ttu-id="b5fb9-154">**Cadeia de caracteres, tamanho máximo 64**</span><span class="sxs-lookup"><span data-stu-id="b5fb9-154">**String, Max Length 64**</span></span>

<span data-ttu-id="b5fb9-155">Substitui a (s) cadeias de caracteres correspondentes do manifesto do aplicativo pelo valor fornecido aqui.</span><span class="sxs-lookup"><span data-stu-id="b5fb9-155">Replaces the corresponding string(s) from the app manifest with the value provided here.</span></span>
