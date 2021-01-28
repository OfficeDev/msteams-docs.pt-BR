---
title: Localização para seu aplicativo
description: Descreve considerações para a localização do aplicativo Microsoft Teams.
ms.topic: conceptual
keywords: teams publish store office publishing AppSource localization language
ms.date: 05/15/2018
ms.openlocfilehash: 69bee0ee11238dc0e461e4fddf8ed01f0cfcccde
ms.sourcegitcommit: 976e870cc925f61b76c3830ec04ba6e4bdfde32f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/27/2021
ms.locfileid: "50014296"
---
# <a name="localization-for-microsoft-teams-apps"></a>Localização de aplicativos do Microsoft Teams

Ao localização do aplicativo Microsoft Teams, há três áreas principais que você precisa considerar.

1. Listagem do AppSource (se você estiver publicando na loja de aplicativos).
1. As cadeias de caracteres voltadas para o usuário final no manifesto do aplicativo (por exemplo, comandos de bot).
1. Responder ao texto localizado enviado por seus usuários.

## <a name="localizing-your-appsource-listing"></a>Localizando sua listagem do AppSource

Se estiver publicando na loja de aplicativos, você precisa estar ciente de que a localização da listagem do AppSource ainda não é suportada. No entanto, em preparação para suporte para listagens localizadas na loja de aplicativos, você pode adicionar idiomas adicionais à sua listagem. Atualmente, apenas as informações de idioma padrão (inglês) fornecidas no [Partner Center](/office/dev/store/submit-to-appsource-via-partner-center) para sua listagem serão exibidas na listagem de site do [AppSource](https://appsource.microsoft.com/marketplace/apps?product=office%3Bteams&page=1) para seu aplicativo.

Para configurar um idioma adicional para seu aplicativo, no [Partner Center,](/office/dev/store/submit-to-appsource-via-partner-center)selecione inglês e o idioma adicional do aplicativo. O francês é usado neste exemplo.

1. Adicionar idioma inglês
    * Preencha o nome do aplicativo.
    * Preencha uma breve descrição do aplicativo em inglês.
    * Preencha a descrição longa do aplicativo em inglês.
    * Na descrição longa, adicione também a linha "Este aplicativo está disponível em "Francês".
    * Carregue as imagens da interface do usuário do seu aplicativo (em inglês).
2. Adicionar idioma francês
    * Preencha o nome do aplicativo.
    * Preencha uma breve descrição do aplicativo em francês.
    * Preencha a descrição longa do aplicativo em francês.
    * Carregue as imagens da interface do usuário do seu aplicativo (em francês).

As imagens carregadas com o idioma inglês serão as usadas no AppSource.

## <a name="localizing-the-strings-in-your-app-manifest"></a>Localizando as cadeias de caracteres no manifesto do aplicativo

Você deve usar o esquema de aplicativo do Microsoft Teams v1.5+ para localizado corretamente seu aplicativo. Você pode fazer isso definindo o atributo no arquivo manifest.json como ' ' e atualizando a propriedade `$schema` https://developer.microsoft.com/en-us/json-schemas/teams/v1.8/MicrosoftTeams.Localization.schema.json 'manifestVersion' para '1.7'.

### <a name="example-manifestjson-change"></a>Exemplo manifest.jsna alteração

```json
{
  "$schema": "https://developer.microsoft.com/en-us/json-schemas/teams/v1.8/MicrosoftTeams.Localization.schema.json",
  "manifestVersion": "1.5",
  ...
}
```

Em seguida, você vai querer adicionar a propriedade 'localizationInfo' com o idioma padrão compatível com seu aplicativo. O idioma padrão será usado como o idioma de fallback final se as configurações de cliente do usuário não corresponderem a nenhum dos idiomas adicionais.

### <a name="example-manifestjson-change"></a>Exemplo manifest.jsna alteração

```json
{
  ...
  "localizationInfo": {
    "defaultLanguageTag": "en"
  }
  ...
}
```

Você pode fornecer arquivos .json adicionais com traduções de todas as cadeias de caracteres voltadas para o usuário em seu manifesto. Esses arquivos devem aderir ao esquema [JSON](../../resources/schema/localization-schema.md) do arquivo de localização e devem ser adicionados à propriedade 'localizationInfo' do manifesto. Cada arquivo se correlaciona a uma marca de idioma que o cliente do Teams usa para escolher as cadeias de caracteres apropriadas. A marca de idioma tem a forma, mas é recomendável omitir a parte para todas as regiões que suportam <language> - <region> o <region> idioma desejado.

O cliente do Teams aplicará as cadeias de caracteres nesta ordem: cadeias de caracteres de idioma padrão -> cadeias de caracteres somente de idioma do usuário -> idioma do usuário + cadeias de caracteres de região do usuário.

Por exemplo, você fornece um idioma padrão "fr" (francês, todas as regiões) e arquivos de idioma adicionais para 'en' (inglês, todas as regiões) e 'en-gb' (inglês, Great Britain). Se o idioma do usuário estiver definido como 'en-gb':

1. O cliente do Teams assumirá as cadeias de caracteres "fr" que as substituirão pelas cadeias de caracteres "en".
2. Sobrescreva-os com as cadeias de caracteres 'en-gb'.

Se o idioma do usuário estiver definido como 'en-ca': 

1. O cliente do Teams assumirá as cadeias de caracteres "fr" que as substituirão pelas cadeias de caracteres "en".
2. Como nenhuma localização 'en-ca' é fornecida, as localizações 'en' serão usadas.

Se o idioma do usuário estiver definido como "es-es", o cliente do Teams pegará as cadeias de caracteres 'fr' e não as substituirá por nenhum dos arquivos de idioma.

Portanto, é altamente recomendável fornecer traduções de nível superior somente de idioma em seu manifesto ('en' em vez de 'en-us') e fornecer apenas substituições de nível de região para as poucas cadeias de caracteres que precisam delas.

### <a name="example-manifestjson-change"></a>Exemplo manifest.jsna alteração

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

### <a name="example-localization-json-file"></a>Exemplo de arquivo .json de localização

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

## <a name="handling-localized-text-submissions-from-your-users"></a>Manipulando envios de texto localizados de seus usuários

Se você fornecer versões localizadas do seu aplicativo, é muito provável que os usuários respondam com o mesmo idioma. O Teams não traduz os envios de usuário de volta para o idioma padrão, portanto, seu aplicativo precisará lidar com isso. Por exemplo, se você fornecer uma localização , as respostas ao seu bot serão o texto localizado do comando, não `commandList` o idioma padrão. Seu aplicativo precisará responder adequadamente.
