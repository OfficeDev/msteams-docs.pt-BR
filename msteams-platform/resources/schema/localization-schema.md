---
title: Localizar referências do esquema JSON
description: Descreve o esquema de localização compatível com o arquivo de localização do Microsoft Teams usando um esquema de exemplo
ms.topic: reference
ms.localizationpriority: medium
ms.date: 05/20/2019
ms.openlocfilehash: 23d02e845e4fcdc1c2fc76d8e9c376479fe1fa1f
ms.sourcegitcommit: ca84b5fe5d3b97f377ce5cca41c48afa95496e28
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/17/2022
ms.locfileid: "66144273"
---
# <a name="localize-json-schema-reference"></a>Localizar referências do esquema JSON

O arquivo de localização do Microsoft Teams descreve traduções de idioma que são atendidas com base nas configurações de idioma do cliente. O arquivo deve estar em conformidade com o esquema hospedado em [`https://developer.microsoft.com/en-us/json-schemas/teams/v1.8/MicrosoftTeams.Localization.schema.json`](https://developer.microsoft.com/en-us/json-schemas/teams/v1.8/MicrosoftTeams.Localization.schema.json).

> [!TIP]
> Especifique o esquema no início do manifesto para habilitar `IntelliSense` ou suporte semelhante do editor de código: `"$schema": "https://developer.microsoft.com/json-schemas/teams/v1.8/MicrosoftTeams.schema.json",`

## <a name="example"></a>Exemplo

O exemplo de esquema JSON de localização é o seguinte:

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

|Propriedade|Tipo|Tamanho máximo|Descrição|
|---------------|--------|---------|------------------|
|`$schema`|URI|NA|A URL https:// referenciando o esquema JSON para o manifesto.|
|`name.short`|Cadeia de caracteres|30|Substitui a cadeia de caracteres correspondente do manifesto do aplicativo pelo valor fornecido aqui.|
|`name.full`|Cadeia de caracteres|100|Substitui a cadeia de caracteres correspondente do manifesto do aplicativo pelo valor fornecido aqui.|
|`description.short`|Cadeia de caracteres|80|Substitui a cadeia de caracteres correspondente do manifesto do aplicativo pelo valor fornecido aqui.|
|`description.full`|Cadeia de caracteres|4000|Substitui a cadeia de caracteres correspondente do manifesto do aplicativo pelo valor fornecido aqui.|
|`staticTabs\\[([0-9]|1[0-5])\\]\\.name`|Cadeia de caracteres|128|Substitui as cadeias de caracteres correspondentes do manifesto do aplicativo pelo valor fornecido aqui.|
|`bots\\[0\\]\\.commandLists\\[[0-2]\\]\\.commands\\[[0-9]\\]\\.title`|Cadeia de caracteres|32|Substitui as cadeias de caracteres correspondentes do manifesto do aplicativo pelo valor fornecido aqui.|
|`bots\\[0\\]\\.commandLists\\[[0-2]\\]\\.commands\\[[0-9]\\]\\.description`|Cadeia de caracteres|128|Substitui as cadeias de caracteres correspondentes do manifesto do aplicativo pelo valor fornecido aqui.|
|`composeExtensions\\[0\\]\\.commands\\[[0-9]\\]\\.title`|Cadeia de caracteres|32|Substitui as cadeias de caracteres correspondentes do manifesto do aplicativo pelo valor fornecido aqui.|
|`composeExtensions\\[0\\]\\.commands\\[[0-9]\\]\\.description`|Cadeia de caracteres|128|Substitui as cadeias de caracteres correspondentes do manifesto do aplicativo pelo valor fornecido aqui.|
|`composeExtensions\\[0\\]\\.commands\\[[0-9]\\]\\.parameters\\[[0-4]\\]\\.title`|Cadeia de caracteres|32|Substitui a cadeia de caracteres correspondente do manifesto do aplicativo pelo valor fornecido aqui.|
|`composeExtensions\\[0\\]\\.commands\\[[0-9]\\]\\.parameters\\[[0-4]\\]\\.description`|Cadeia de caracteres|128|Substitui as cadeias de caracteres correspondentes do manifesto do aplicativo pelo valor fornecido aqui.|
|`composeExtensions\\[0\\]\\.commands\\[[0-9]\\]\\.parameters\\[[0-4]\\]\\.value`|Cadeia de caracteres|512|Substitui a cadeia de caracteres correspondente do manifesto do aplicativo pelo valor fornecido aqui.|
|`composeExtensions\\[0\\]\\.commands\\[[0-9]\\]\\.parameters\\[[0-4]\\]\\.choices\\[[0-9]\\]\\.title`|Cadeia de caracteres|128|Substitui as cadeias de caracteres correspondentes do manifesto do aplicativo pelo valor fornecido aqui.|
|`composeExtensions\\[0\\]\\.commands\\[[0-9]\\]\\.taskInfo\\.title`|Cadeia de caracteres|64|Substitui as cadeias de caracteres correspondentes do manifesto do aplicativo pelo valor fornecido aqui.|
|`activities.activityTypes\\[\\b([0-9]|[1-8][0-9]|9[0-9]|1[01][0-9]|12[0-7])\\b]\\.description`|Cadeia de caracteres|128|Uma breve descrição da notificação|
|`activities.activityTypes\\[\\b([0-9]|[1-8][0-9]|9[0-9]|1[01][0-9]|12[0-7])\\b]\\.templateText`|Cadeia de caracteres|128|Ex: "{actor} criou a tarefa {taskId} para você"|

## <a name="see-also"></a>Confira também

[Localizar o aplicativo](~/concepts/build-and-test/apps-localization.md)
