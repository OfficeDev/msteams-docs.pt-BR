---
title: Localização para seu aplicativo
description: Descreve considerações para a localização do aplicativo do Microsoft Teams.
ms.topic: conceptual
localization_priority: Normal
keywords: teams publish store office publishing AppSource localization language
ms.date: 05/15/2018
ms.openlocfilehash: 8490230ad0b268d402a9ad7deb5f8b1e3f420f9d
ms.sourcegitcommit: 825abed2f8784d2bab7407ba7a4455ae17bbd28f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2021
ms.locfileid: "52020846"
---
# <a name="localization-for-microsoft-teams-apps"></a>Localização para aplicativos do Microsoft Teams

Ao localização do seu aplicativo do Microsoft Teams, há três áreas principais que você precisa considerar.

1. Sua listagem appSource (se você estiver publicando na loja de aplicativos).
1. As cadeias de caracteres voltadas para o usuário final no manifesto do aplicativo (por exemplo, comandos de bot).
1. Respondendo ao texto localizado enviado de seus usuários.

## <a name="localizing-your-appsource-listing"></a>Localizando sua listagem do AppSource

Se você estiver publicando na loja de aplicativos, você precisa estar ciente de que ainda não há suporte para a localização da listagem do AppSource. No entanto, em preparação para suporte para listagens localizadas na loja de aplicativos, você pode adicionar idiomas adicionais à sua listagem. Atualmente, apenas as informações de idioma padrão (inglês) fornecidas no [Partner Center](/office/dev/store/submit-to-appsource-via-partner-center) para sua listagem serão exibidas na listagem de site do [AppSource](https://appsource.microsoft.com/marketplace/apps?product=office%3Bteams&page=1) para seu aplicativo.

Para configurar um idioma adicional para seu aplicativo, no [Partner Center,](/office/dev/store/submit-to-appsource-via-partner-center)selecione inglês e o idioma adicional do aplicativo. O francês é usado neste exemplo.

1. Adicionar idioma inglês
    * Preencha o nome do aplicativo.
    * Preencha uma breve descrição do aplicativo em inglês.
    * Preencha a longa descrição do aplicativo em inglês.
    * Na descrição longa, adicione também a linha "Este aplicativo está disponível em "francês".
    * Carregue as imagens da interface do usuário do aplicativo (em inglês).
2. Adicionar idioma francês
    * Preencha o nome do aplicativo.
    * Preencha uma breve descrição do aplicativo em francês.
    * Preencha a longa descrição do aplicativo em francês.
    * Carregue as imagens da interface do usuário do aplicativo (em francês).

As imagens carregadas com o idioma inglês serão as usadas no AppSource.

## <a name="localizing-the-strings-in-your-app-manifest"></a>Localizando as cadeias de caracteres no manifesto do aplicativo

Você deve usar o esquema de aplicativo do Microsoft Teams v1.5+ para localização adequada do aplicativo. Você pode fazer isso definindo o atributo em seu arquivo manifest.json como ' ' e atualizando a `$schema` https://developer.microsoft.com/en-us/json-schemas/teams/v1.8/MicrosoftTeams.Localization.schema.json propriedade 'manifestVersion' como '1.7'.

### <a name="example-manifestjson-change"></a>Exemplo manifest.jsna alteração

```json
{
  "$schema": "https://developer.microsoft.com/en-us/json-schemas/teams/v1.8/MicrosoftTeams.Localization.schema.json",
  "manifestVersion": "1.5",
  ...
}
```

Em seguida, você deseja adicionar a propriedade 'localizationInfo' com o idioma padrão que o aplicativo oferece suporte. O idioma padrão é usado como o idioma de fallback final se as configurações do cliente do usuário não corresponderem a nenhum dos idiomas adicionais.

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

Você pode fornecer arquivos .json adicionais com traduções de todas as cadeias de caracteres voltadas para o usuário em seu manifesto. Esses arquivos devem aderir ao esquema [JSON](../../resources/schema/localization-schema.md) do arquivo de localização e devem ser adicionados à propriedade 'localizationInfo' do manifesto. Cada arquivo se correlaciona a uma marca de idioma que o cliente teams usa para escolher as cadeias de caracteres apropriadas. A marca de idioma assume a forma de, mas é recomendável omitir a parte para direcionar todas as regiões que suportam <language> - <region> o <region> idioma desejado.

O cliente do Teams aplicará as cadeias de caracteres nesta ordem: cadeias de caracteres de idioma padrão -> idioma do usuário somente cadeias de caracteres -> idioma do usuário + cadeias de caracteres de região do usuário.

Por exemplo, você fornece um idioma padrão de 'fr' (francês, todas as regiões) e arquivos de idiomas adicionais para 'en' (inglês, todas as regiões) e 'en-gb' (inglês, Grã-Bretanha). Se o idioma do usuário estiver definido como 'en-gb':

1. O cliente do Teams assumirá as cadeias de caracteres 'fr' sobrescreve-as com as cadeias de caracteres 'en'.
2. Sobrescreva-os com as cadeias de caracteres 'en-gb'.

Se o idioma do usuário estiver definido como 'en-ca': 

1. O cliente do Teams assumirá as cadeias de caracteres 'fr' sobrescreve-as com as cadeias de caracteres 'en'.
2. Como nenhuma localização 'en-ca' é fornecida, as localizações 'en' serão usadas.

Se o idioma do usuário estiver definido como 'es-es', o cliente do Teams assumirá as cadeias de caracteres 'fr' e não as substituirá por nenhum dos arquivos de idioma.

Portanto, é altamente recomendável fornecer traduções de nível superior e somente idioma em seu manifesto ('en' em vez de 'en-us') e fornecer apenas substituições no nível da região para as poucas cadeias de caracteres que precisam delas.

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

Se o seu fornecer versões localizadas do aplicativo, é muito provável que os usuários respondam com o mesmo idioma. O Teams não converte os envios de usuário de volta para o idioma padrão, portanto, seu aplicativo precisará lidar com isso. Por exemplo, se você fornecer uma localização , as respostas ao bot serão o texto localizado do comando, não `commandList` o idioma padrão. Seu aplicativo precisará responder adequadamente.
