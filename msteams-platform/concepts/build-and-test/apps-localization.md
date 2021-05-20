---
title: Localização para o seu aplicativo
description: Descreve considerações para localização do aplicativo Microsoft Teams.
ms.topic: conceptual
localization_priority: Normal
keywords: equipes publicam escritório de loja publicando appSource linguagem de localização
ms.date: 05/15/2018
ms.openlocfilehash: a55b8af97e5306843858e5844a017dd402ab3516
ms.sourcegitcommit: 51e4a1464ea58c254ad6bd0317aca03ebf6bf1f6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2021
ms.locfileid: "52566044"
---
# <a name="localization-for-microsoft-teams-apps"></a>Localização para aplicativos de Microsoft Teams

Ao localizar seu aplicativo Microsoft Teams, você deve considerar o seguinte:

1. Sua Teams lista de lojas (se aplicável).
1. O usuário final enfrentando strings no manifesto do aplicativo. Por exemplo, comandos de bot.
1. Respondendo ao texto localizado enviado de seus usuários.

## <a name="localizing-your-appsource-listing"></a>Localização de sua listagem AppSource

Se você está publicando na loja, você precisa estar ciente de que a localização da sua listagem appSource ainda não está suportada. No entanto, em preparação para o suporte para listagens localizadas na loja de aplicativos, você pode adicionar idiomas adicionais à sua listagem. Atualmente, apenas as informações padrão do idioma (inglês) que você fornece no [Partner Center](/office/dev/store/submit-to-appsource-via-partner-center) para sua listagem aparecerão na listagem do [site appSource](https://appsource.microsoft.com/marketplace/apps?product=office%3Bteams&page=1) para o seu aplicativo.

### <a name="example-of-configuring-localization"></a>Exemplo de configuração da localização

Para configurar um idioma adicional para o seu aplicativo, no [Partner Center,](/office/dev/store/submit-to-appsource-via-partner-center)selecione tanto o inglês quanto o idioma adicional do aplicativo. O francês é usado neste exemplo:

1. Adicionar inglês
    * Preencha o nome do aplicativo.
    * Preencha uma breve descrição do aplicativo em inglês.
    * Preencha a longa descrição do aplicativo em inglês.
    * Na longa descrição, adicione também a linha "Este aplicativo está disponível em "Francês".
    * Upload as imagens do seu aplicativo UI (em inglês).
2. Adicionar língua francesa
    * Preencha o nome do aplicativo.
    * Preencha uma breve descrição do aplicativo em francês.
    * Preencha a longa descrição do aplicativo em francês.
    * Upload as imagens do seu aplicativo UI (em francês).

As imagens que você carrega com o idioma inglês serão as usadas no AppSource.

## <a name="localizing-the-strings-in-your-app-manifest"></a>Localização das cordas no manifesto do aplicativo

Você deve usar o esquema de Microsoft Teams aplicativo v1.5+ para localizar corretamente seu aplicativo. Você pode fazer isso definindo o `$schema` atributo em seu manifest.jsno arquivo para ' e https://developer.microsoft.com/en-us/json-schemas/teams/v1.8/MicrosoftTeams.Localization.schema.json atualizando a propriedade 'manifestVersion' para '1.7'.

### <a name="example-manifestjson-change"></a>Exemplo manifest.jssobre a mudança

```json
{
  "$schema": "https://developer.microsoft.com/en-us/json-schemas/teams/v1.8/MicrosoftTeams.Localization.schema.json",
  "manifestVersion": "1.5",
  ...
}
```

Em seguida, você deseja adicionar a propriedade 'localizaçãoInfo' com o idioma padrão que seu aplicativo suporta. O idioma padrão é usado como o idioma de recuo final se as configurações do cliente do usuário não corresponderem a nenhum de seus idiomas adicionais.

### <a name="example-manifestjson-change"></a>Exemplo manifest.jssobre a mudança

```json
{
  ...
  "localizationInfo": {
    "defaultLanguageTag": "en"
  }
  ...
}
```

Você pode fornecer arquivos .json adicionais com traduções de todas as strings que enfrentam o usuário em seu manifesto. Esses arquivos devem aderir ao [esquema JSON](../../resources/schema/localization-schema.md) do arquivo de localização e devem ser adicionados à propriedade 'localizaçãoInfo' do seu manifesto. Cada arquivo se correlaciona com uma tag de idioma que o Teams cliente usa para escolher as strings apropriadas. A tag de idioma toma a forma <language> - <region> de, mas é recomendado omitir a <region> porção para atingir todas as regiões que suportam a linguagem desejada.

O cliente Teams aplicará as strings nesta ordem: strings de idioma padrão -> idioma do usuário apenas strings -> idioma do usuário + sequências regionais do usuário.

Por exemplo, você fornece um idioma padrão de 'fr' (francês, todas as regiões) e arquivos adicionais de idiomas para 'en' (inglês, todas as regiões) e 'en-gb' (inglês, Grã-Bretanha). Se o idioma do usuário estiver definido como 'en-gb':

1. O cliente Teams levará as cordas 'fr' sobregrava-as com as cordas 'en'.
2. Substitua-os com as cordas 'en-gb'.

Se o idioma do usuário estiver definido como 'en-ca': 

1. O cliente Teams levará as cordas 'fr' sobregrava-as com as cordas 'en'.
2. Como não é fornecida uma localização 'en-ca', as localizações 'en' serão utilizadas.

Se o idioma do usuário estiver definido como 'es-es', o cliente Teams pegará as strings 'fr' e não irá substituí-las com nenhum dos arquivos de idioma.

Portanto, é fortemente recomendável fornecer traduções de alto nível, somente para idiomas em seu manifesto ('en' em vez de 'en-us') e apenas fornecer substituições de nível de região para as poucas strings que precisam delas.

### <a name="example-manifestjson-change"></a>Exemplo manifest.jssobre a mudança

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

### <a name="example-localization-json-file"></a>Arquivo de localização de exemplo .json

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

## <a name="handling-localized-text-submissions-from-your-users"></a>Manipulação de envios de texto localizados de seus usuários

Se você fornecer versões localizadas do seu aplicativo é muito provável que seus usuários respondam com o mesmo idioma. Teams não traduz os envios do usuário de volta para o idioma padrão, então seu aplicativo precisará lidar com isso. Por exemplo, se você fornecer um `commandList` localizado, as respostas ao seu bot serão o texto localizado do comando, não o idioma padrão. Seu aplicativo precisará responder adequadamente.

## <a name="code-sample"></a>Exemplo de código

| Nome da amostra | Descrição | .NET |
|-------------|-------------|------|
| Localização de aplicativos | Microsoft Teams localização do aplicativo usando bot e guia. | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/app-localization/csharp) |


