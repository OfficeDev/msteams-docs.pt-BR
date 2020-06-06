---
title: Localização para aplicativos da equipe
description: Descreve problemas em relação à localização do aplicativo
keywords: publicação do Microsoft Teams armazenar o idioma de localização do Office Publishing AppSource
ms.date: 05/15/2018
ms.openlocfilehash: 30e4a2589bf5c1093723406c78cff2258554c486
ms.sourcegitcommit: 6c786434b56cc8c2765a14aa1f6149870245f309
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "44590855"
---
# <a name="localization-for-microsoft-teams-apps"></a>Localização para aplicativos do Microsoft Teams

Ao localizar seu aplicativo do Microsoft Teams, há três áreas principais que você precisa considerar.

1. Sua listagem de AppSource (se você estiver publicando na loja de aplicativos).
1. As cadeias de caracteres voltadas para o usuário final em seu manifesto de aplicativo (por exemplo, comandos de bot).
1. Responder ao texto localizado enviado de seus usuários.

## <a name="localizing-your-appsource-listing"></a>Localizando sua listagem do AppSource

Se você estiver publicando na loja de aplicativos, precisará estar ciente de que não há suporte para localizar sua listagem de AppSource ainda. No entanto, em preparação para suporte para listagens localizadas na loja de aplicativos, você pode adicionar outros idiomas à sua listagem. Atualmente, apenas as informações de idioma padrão (inglês) fornecidas no [Partner Center](/dev/store/use-partner-center-to-submit-to-appsource) para sua listagem aparecerão na lista de [sites do AppSource](https://appsource.microsoft.com/marketplace/apps?product=office%3Bteams&page=1) para o seu aplicativo.

Para configurar um idioma adicional para seu aplicativo, no [centro de parceria](/dev/store/use-partner-center-to-submit-to-appsource), selecione tanto o inglês quanto o idioma adicional do aplicativo. Francês é usado neste exemplo.

1. Adicionar idioma inglês
    * Preencha o nome do aplicativo.
    * Preencha uma breve descrição do aplicativo em inglês.
    * Preencha a descrição longa do aplicativo em inglês.
    * Na descrição longa, adicione também a linha "este aplicativo está disponível em" francês ".
    * Carregar as imagens da sua interface do usuário do aplicativo (em inglês).
2. Adicionar idioma francês
    * Preencha o nome do aplicativo.
    * Preencha uma breve descrição do aplicativo em francês.
    * Preencha a descrição longa do aplicativo em francês.
    * Carregar as imagens da sua interface do usuário do aplicativo (em francês).

As imagens carregadas com o idioma inglês serão aquelas usadas no AppSource.

## <a name="localizing-the-strings-in-your-app-manifest"></a>Localizando as cadeias de caracteres em seu manifesto de aplicativo

Você deve usar o esquema de aplicativos do Microsoft Teams v 1.5 + para localizar corretamente seu aplicativo. Você pode fazer isso Configurando o `$schema` atributo no arquivo manifest. JSON como ' https://developer.microsoft.com/json-schemas/teams/v1.7/MicrosoftTeams.schema.json ' e atualizando a propriedade ' manifestVersion ' para ' 1,5 '.

### <a name="example-manifestjson-change"></a>Alteração de manifesto de exemplo. JSON

```json
{
  "$schema": "https://developer.microsoft.com/json-schemas/teams/v1.7/MicrosoftTeams.schema.json",
  "manifestVersion": "1.5",
  ...
}
```

Em seguida, você poderá adicionar a propriedade ' localizationInfo ' com o idioma padrão ao qual seu aplicativo oferece suporte. O idioma padrão é usado como o idioma de fallback final se as configurações de cliente do usuário não corresponderem a nenhum dos seus idiomas adicionais.

### <a name="example-manifestjson-change"></a>Alteração de manifesto de exemplo. JSON

```json
{
  ...
  "localizationInfo": {
    "defaultLanguageTag": "en"
  }
  ...
}
```

Você pode fornecer arquivos. JSON adicionais com traduções de todas as cadeias de caracteres voltadas para o usuário em seu manifesto. Esses arquivos devem aderir ao [esquema JSON do arquivo de localização](../../resources/schema/localization-schema.md) e devem ser adicionados à propriedade "localizationInfo" do manifesto. Cada arquivo se correlaciona com uma marca de idioma que o cliente do teams usa para escolher as cadeias de caracteres apropriadas. A marca de idioma tem a forma de <language> - <region> mas é recomendável omitir a <region> parte para direcionar todas as regiões que dão suporte ao idioma desejado.

O cliente Teams aplicará as cadeias de caracteres nesta ordem: cadeias de caracteres de idioma padrão-> cadeias de caracteres de idiomas do usuário-> idioma do usuário + cadeia de caracteres de região do usuário.

Por exemplo, você fornece um idioma padrão de ' fr ' (francês, todas as regiões) e arquivos de idioma adicionais para ' en ' (Inglês, todas as regiões) e ' en-GB ' (Inglês, Grã-Bretanha). Se o idioma do usuário estiver definido como "en-GB":

1. O cliente Teams usará as cadeias de caracteres ' fr ' substituí-las pelas cadeias de caracteres ' en '.
2. Substitua-os com as cadeias de caracteres "en-GB".

Se o idioma do usuário estiver definido como ' en-CA ': 

1. O cliente Teams usará as cadeias de caracteres ' fr ' substituí-las pelas cadeias de caracteres ' en '.
2. Como nenhuma localização "en-AC" é fornecida, as localizações de "en" serão usadas.

Se o idioma do usuário estiver definido como ' es-es ', o cliente do Microsoft Teams usará as cadeias de caracteres ' fr ' e não as substituirá por nenhum dos arquivos de idioma.

Portanto, é altamente recomendável fornecer traduções de nível superior, somente de idioma em seu manifesto (' en ' em vez de "en-US ') e fornecer apenas substituições de nível de região para as poucas cadeias de caracteres que precisam delas.

### <a name="example-manifestjson-change"></a>Alteração de manifesto de exemplo. JSON

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

### <a name="example-localization-json-file"></a>Exemplo de arquivo de localização. JSON

```json
{
  "$schema": "https://developer.microsoft.com/json-schemas/teams/v1.7/MicrosoftTeams.schema.json",
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

## <a name="handling-localized-text-submissions-from-your-users"></a>Lidando com envios de texto localizado de seus usuários

Se você fornecer versões localizadas de seu aplicativo, é provável que seus usuários respondam com o mesmo idioma. O Microsoft Teams não traduz os envios do usuário de volta para o idioma padrão, para que seu aplicativo precise lidar com isso. Por exemplo, se você fornecer um localizado `commandList` , as respostas para o bot serão o texto localizado do comando, e não o idioma padrão. Seu aplicativo precisará responder de forma adequada.
