---
title: Localizar referências do esquema JSON
description: Descreve o esquema de localização suportado pelo arquivo de localização para Microsoft Teams
ms.topic: reference
ms.localizationpriority: medium
keywords: Localização de esquema de manifesto do teams
ms.date: 05/20/2019
ms.openlocfilehash: 7b9853772996764e185ed4de44683df9f5f57711
ms.sourcegitcommit: 6573881f7e69d8e5ec8861f54df84e7d519f0511
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/04/2021
ms.locfileid: "60096532"
---
# <a name="localize-json-schema-reference"></a>Localizar referências do esquema JSON

O Microsoft Teams de localização descreve traduções de idioma que são atendidas com base nas configurações de idioma do cliente. Seu arquivo deve estar em conformidade com o esquema hospedado em [`https://developer.microsoft.com/en-us/json-schemas/teams/v1.5/MicrosoftTeams.Localization.schema.json`](https://developer.microsoft.com/en-us/json-schemas/teams/v1.5/MicrosoftTeams.Localization.schema.json) . 

> [!TIP]
> Especifique o esquema no início do manifesto para habilitar `IntelliSense` ou suporte semelhante do editor de código: `"$schema": "https://developer.microsoft.com/json-schemas/teams/v1.5/MicrosoftTeams.schema.json",`

## <a name="example"></a>Exemplo 

Exemplo de esquema JSON de localização é o seguinte:

```json
{
  "$schema": "https://developer.microsoft.com/json-schemas/teams/v1.5/MicrosoftTeams.schema.json",
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

> [!NOTE]
>  O App Studio será preterido em breve. Configure, distribua e gerencie seus aplicativos Teams com o novo [Portal do Desenvolvedor.](https://dev.teams.microsoft.com/)

O esquema define as seguintes propriedades:

|Propriedade|Tipo|Tamanho máximo|Descrição|
|---------------|--------|---------|------------------|
|`$schema`|URI|NA|A https:// URL de referência do Esquema JSON para o manifesto.|
|`name.short`|String|30|Substitui a cadeia de caracteres correspondente do manifesto do aplicativo pelo valor fornecido aqui.|
|`name.full`|Cadeia de caracteres|100|Substitui a cadeia de caracteres correspondente do manifesto do aplicativo pelo valor fornecido aqui.|
|`description.short`|Cadeia de caracteres|80|Substitui a cadeia de caracteres correspondente do manifesto do aplicativo pelo valor fornecido aqui.|
|`description.full`|String|4000|Substitui a cadeia de caracteres correspondente do manifesto do aplicativo pelo valor fornecido aqui.|
|`staticTabs\\[([0-9]|1[0-5])\\]\\.name`|String|128|Substitui as cadeias de caracteres correspondentes do manifesto do aplicativo pelo valor fornecido aqui.|
|`bots\\[0\\]\\.commandLists\\[[0-2]\\]\\.commands\\[[0-9]\\]\\.title`|String|32|Substitui as cadeias de caracteres correspondentes do manifesto do aplicativo pelo valor fornecido aqui.|
|`## bots\\[0\\]\\.commandLists\\[[0-2]\\]\\.commands\\[[0-9]\\]\\.description`|Cadeia de caracteres|128|Substitui as cadeias de caracteres correspondentes do manifesto do aplicativo pelo valor fornecido aqui.|
|`composeExtensions\\[0\\]\\.commands\\[[0-9]\\]\\.title`|Cadeia de caracteres|32|Substitui as cadeias de caracteres correspondentes do manifesto do aplicativo pelo valor fornecido aqui.|
|`composeExtensions\\[0\\]\\.commands\\[[0-9]\\]\\.description`|Cadeia de caracteres|128|Substitui as cadeias de caracteres correspondentes do manifesto do aplicativo pelo valor fornecido aqui.|
|`composeExtensions\\[0\\]\\.commands\\[[0-9]\\]\\.parameters\\[[0-4]\\]\\.title`|Cadeia de caracteres|32|Substitui a cadeia de caracteres correspondente do manifesto do aplicativo pelo valor fornecido aqui.|
|`composeExtensions\\[0\\]\\.commands\\[[0-9]\\]\\.parameters\\[[0-4]\\]\\.description`|Cadeia de caracteres|128|Substitui as cadeias de caracteres correspondentes do manifesto do aplicativo pelo valor fornecido aqui.|
|`composeExtensions\\[0\\]\\.commands\\[[0-9]\\]\\.parameters\\[[0-4]\\]\\.value`|Cadeia de caracteres|512|Substitui a cadeia de caracteres correspondente do manifesto do aplicativo pelo valor fornecido aqui.|
|`composeExtensions\\[0\\]\\.commands\\[[0-9]\\]\\.parameters\\[[0-4]\\]\\.choices\\[[0-9]\\]\\.title`|Cadeia de caracteres|128|Substitui as cadeias de caracteres correspondentes do manifesto do aplicativo pelo valor fornecido aqui.|
|`composeExtensions\\[0\\]\\.commands\\[[0-9]\\]\\.taskInfo\\.title`|Cadeia de caracteres|64|Substitui as cadeias de caracteres correspondentes do manifesto do aplicativo pelo valor fornecido aqui.|

## <a name="see-also"></a>Confira também

> [Localizar o aplicativo](~/concepts/build-and-test/apps-localization.md)
