---
title: Referência de esquema JSON de arquivo de localização
description: Descreve o esquema de localização suportado pelo arquivo de localização para o Microsoft Teams
keywords: Localização do esquema do manifesto do teams
ms.date: 05/20/2019
ms.openlocfilehash: 14e08c582f065d1b09ff0f4906ca6788037460f1
ms.sourcegitcommit: 6c786434b56cc8c2765a14aa1f6149870245f309
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "44590862"
---
# <a name="reference-localization-file-json-schema"></a>Referência: esquema JSON do arquivo de localização

O arquivo de localização do Microsoft Teams descreve as traduções de idioma que serão atendidas com base nas configurações de idioma do cliente. O arquivo deve estar em conformidade com o esquema hospedado em [`https://developer.microsoft.com/json-schemas/teams/v1.7/MicrosoftTeams.schema.json`]( https://developer.microsoft.com/json-schemas/teams/v1.7/MicrosoftTeams.schema.json) . Para obter informações adicionais, consulte [localização de aplicativos](~/concepts/build-and-test/apps-localization.md).

## <a name="sample"></a>Amostra

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

O esquema define as seguintes propriedades:

## <a name="schema"></a>$schema

**URI**

A URL https://que faz referência ao esquema JSON para o manifesto.

> [!TIP]
> Especifique o esquema no início do manifesto para habilitar o IntelliSense ou suporte semelhante do editor de código:`"$schema": "https://developer.microsoft.com/json-schemas/teams/v1.7/MicrosoftTeams.schema.json",`

## <a name="nameshort"></a>Name. short

**Cadeia de caracteres, tamanho máximo 30**

Substitui a cadeia de caracteres correspondente do manifesto do aplicativo pelo valor fornecido aqui.

## <a name="namefull"></a>nome. Full

**Cadeia de caracteres, tamanho máximo 100**

Substitui a cadeia de caracteres correspondente do manifesto do aplicativo pelo valor fornecido aqui.

## <a name="descriptionshort"></a>Descrição. short

**Cadeia de caracteres, tamanho máximo 80**

Substitui a cadeia de caracteres correspondente do manifesto do aplicativo pelo valor fornecido aqui.

## <a name="descriptionfull"></a>Descrição. Full

**Cadeia de caracteres, tamanho máximo 4000**

Substitui a cadeia de caracteres correspondente do manifesto do aplicativo pelo valor fornecido aqui.

## <a name="statictabs0-910-5name"></a>staticTabs \\ [([0-9] | 1 [0-5]) \\ ] \\ . nome

**Cadeia de caracteres, tamanho máximo 128**

Substitui a (s) cadeias de caracteres correspondentes do manifesto do aplicativo pelo valor fornecido aqui.

## <a name="bots0commandlists0-2commands0-9title"></a>bots \\ [0 \\ ] \\ . commandLists \\ [[0-2] \\ ] \\ . Commands \\ [[0-9] \\ ] \\ . título

**Cadeia de caracteres, tamanho máximo 32**

Substitui a (s) cadeias de caracteres correspondentes do manifesto do aplicativo pelo valor fornecido aqui.

## <a name="bots0commandlists0-2commands0-9description"></a>bots \\ [0 \\ ] \\ . commandLists \\ [[0-2] \\ ] \\ . Commands \\ [[0-9] \\ ] \\ . Descrição

**Cadeia de caracteres, tamanho máximo 128**

Substitui a (s) cadeias de caracteres correspondentes do manifesto do aplicativo pelo valor fornecido aqui.

## <a name="composeextensions0commands0-9title"></a>composeExtensions \\ [0 \\ ] \\ . Commands \\ [[0-9] \\ ] \\ . title

**Cadeia de caracteres, tamanho máximo 32**

Substitui a (s) cadeias de caracteres correspondentes do manifesto do aplicativo pelo valor fornecido aqui.

## <a name="composeextensions0commands0-9description"></a>composeExtensions \\ [0 \\ ] \\ . Commands \\ [[0-9] \\ ] \\ . Descrição

**Cadeia de caracteres, tamanho máximo 128**

Substitui a (s) cadeias de caracteres correspondentes do manifesto do aplicativo pelo valor fornecido aqui.

## <a name="composeextensions0commands0-9parameters0-4title"></a>composeExtensions \\ [0 \\ ] \\ . Commands \\ [[0-9] \\ ] \\ . Parameters \\ [[0-4] \\ ] \\ . title

**Cadeia de caracteres, tamanho máximo 32**

Substitui a (s) cadeias de caracteres correspondentes do manifesto do aplicativo pelo valor fornecido aqui.

## <a name="composeextensions0commands0-9parameters0-4description"></a>composeExtensions \\ [0 \\ ] \\ . Commands \\ [[0-9] \\ ] \\ . Parameters \\ [[0-4] \\ ] \\ . Descrição

**Cadeia de caracteres, tamanho máximo 128**

Substitui a (s) cadeias de caracteres correspondentes do manifesto do aplicativo pelo valor fornecido aqui.

## <a name="composeextensions0commands0-9parameters0-4value"></a>composeExtensions \\ [0 \\ ] \\ . Commands \\ [[0-9] \\ ] \\ . Parameters \\ [[0-4] \\ ] \\ . Value

**Cadeia de caracteres, tamanho máximo 512**

Substitui a (s) cadeias de caracteres correspondentes do manifesto do aplicativo pelo valor fornecido aqui.

## <a name="composeextensions0commands0-9parameters0-4choices0-9title"></a>composeExtensions \\ [0 \\ ] \\ . Commands \\ [[0-9] \\ ] \\ . Parameters \\ [[0-4] \\ ] \\ . Choices \\ [[0-9] \\ ] \\ . title

**Cadeia de caracteres, tamanho máximo 128**

Substitui a (s) cadeias de caracteres correspondentes do manifesto do aplicativo pelo valor fornecido aqui.

## <a name="composeextensions0commands0-9taskinfotitle"></a>composeExtensions \\ [0 \\ ] \\ . Commands \\ [[0-9] \\ ] \\ . TaskInfo \\ . title

**Cadeia de caracteres, tamanho máximo 64**

Substitui a (s) cadeias de caracteres correspondentes do manifesto do aplicativo pelo valor fornecido aqui.