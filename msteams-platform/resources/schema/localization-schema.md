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
# <a name="reference-localization-file-json-schema"></a>Referência: Esquema JSON do arquivo de localização

O arquivo de localização do Microsoft Teams descreve traduções de idioma que serão atendidas com base nas configurações de idioma do cliente. Seu arquivo deve estar em conformidade com o esquema hospedado em [`https://developer.microsoft.com/en-us/json-schemas/teams/v1.8/MicrosoftTeams.Localization.schema.json`](https://developer.microsoft.com/en-us/json-schemas/teams/v1.8/MicrosoftTeams.Localization.schema.json) . Para obter informações adicionais, [consulte localização do aplicativo.](~/concepts/build-and-test/apps-localization.md)

## <a name="sample"></a>Amostra

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

O esquema define as seguintes propriedades:

## <a name="schema"></a>$schema

**URI**

A https:// URL que referencia o esquema JSON para o manifesto.

> [!TIP]
> Especifique o esquema no início do manifesto para habilitar o IntelliSense ou suporte semelhante do seu editor de código: `"$schema": "https://developer.microsoft.com/json-schemas/teams/v1.8/MicrosoftTeams.schema.json",`

## <a name="nameshort"></a>name.short

**Cadeia de caracteres, Comprimento Máximo 30**

Substitui a cadeia de caracteres correspondente do manifesto do aplicativo pelo valor fornecido aqui.

## <a name="namefull"></a>name.full

**Cadeia de caracteres, Comprimento Máximo 100**

Substitui a cadeia de caracteres correspondente do manifesto do aplicativo pelo valor fornecido aqui.

## <a name="descriptionshort"></a>description.short

**Cadeia de caracteres, Comprimento Máximo 80**

Substitui a cadeia de caracteres correspondente do manifesto do aplicativo pelo valor fornecido aqui.

## <a name="descriptionfull"></a>description.full

**String, Max Length 4000**

Substitui a cadeia de caracteres correspondente do manifesto do aplicativo pelo valor fornecido aqui.

## <a name="statictabs0-910-5name"></a>staticTabs \\ [([0-9]|1[0-5]) \\ ] \\ .name

**Cadeia de caracteres, Comprimento Máximo 128**

Substitui as cadeias de caracteres correspondentes do manifesto do aplicativo pelo valor fornecido aqui.

## <a name="bots0commandlists0-2commands0-9title"></a>bots \\ [0 \\ ] \\ .commandLists \\ [[0-2] \\ ] \\ .commands \\ [[0-9] \\ ] \\ .title

**String, Max Length 32**

Substitui as cadeias de caracteres correspondentes do manifesto do aplicativo pelo valor fornecido aqui.

## <a name="bots0commandlists0-2commands0-9description"></a>bots \\ [0 \\ ] \\ .commandLists \\ [[0-2] \\ ] \\ .commands \\ [[0-9] \\ ] \\ .description

**Cadeia de caracteres, Comprimento Máximo 128**

Substitui as cadeias de caracteres correspondentes do manifesto do aplicativo pelo valor fornecido aqui.

## <a name="composeextensions0commands0-9title"></a>composeExtensions \\ [0 \\ ] \\ .commands \\ [[0-9] \\ ] \\ .title

**String, Max Length 32**

Substitui as cadeias de caracteres correspondentes do manifesto do aplicativo pelo valor fornecido aqui.

## <a name="composeextensions0commands0-9description"></a>composeExtensions \\ [0 \\ ] \\ .commands \\ [[0-9] \\ ] \\ .description

**Cadeia de caracteres, Comprimento Máximo 128**

Substitui as cadeias de caracteres correspondentes do manifesto do aplicativo pelo valor fornecido aqui.

## <a name="composeextensions0commands0-9parameters0-4title"></a>composeExtensions \\ [0 \\ ] \\ .commands \\ [[0-9] \\ ] \\ .parameters \\ [[0-4] \\ ] \\ .title

**Cadeia de caracteres, Comprimento Máximo 32**

Substitui as cadeias de caracteres correspondentes do manifesto do aplicativo pelo valor fornecido aqui.

## <a name="composeextensions0commands0-9parameters0-4description"></a>composeExtensions \\ [0 \\ ] \\ .commands \\ [[0-9] \\ ] \\ .parameters \\ [[0-4] \\ ] \\ .description

**Cadeia de caracteres, Comprimento Máximo 128**

Substitui as cadeias de caracteres correspondentes do manifesto do aplicativo pelo valor fornecido aqui.

## <a name="composeextensions0commands0-9parameters0-4value"></a>composeExtensions \\ [0 \\ ] \\ .commands \\ [[0-9] \\ ] \\ .parameters \\ [[0-4] \\ ] \\ .value

**String, Max Length 512**

Substitui as cadeias de caracteres correspondentes do manifesto do aplicativo pelo valor fornecido aqui.

## <a name="composeextensions0commands0-9parameters0-4choices0-9title"></a>composeExtensions \\ [0 \\ ] \\ .commands \\ [[0-9] \\ ] \\ .parameters \\ [[0-4] \\ ] \\ .choices \\ [[0-9] \\ ] \\ .title

**Cadeia de caracteres, Comprimento Máximo 128**

Substitui as cadeias de caracteres correspondentes do manifesto do aplicativo pelo valor fornecido aqui.

## <a name="composeextensions0commands0-9taskinfotitle"></a>composeExtensions \\ [0 \\ ] \\ .commands \\ [[0-9] \\ ] \\ .taskInfo \\ .title

**String, Max Length 64**

Substitui as cadeias de caracteres correspondentes do manifesto do aplicativo pelo valor fornecido aqui.
