---
title: Localizar o aplicativo
description: Descreve considerações para a localização de seu Microsoft Teams app.
ms.topic: conceptual
ms.localizationpriority: medium
keywords: teams publish store office publishing AppSource localization language
ms.date: 05/15/2018
ms.openlocfilehash: 7d9b805f54d4040ff83b0fd0e704dd349a025fa4
ms.sourcegitcommit: fc9f906ea1316028d85b41959980b81f2c23ef2f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/12/2021
ms.locfileid: "59155230"
---
# <a name="localize-your-app"></a>Localizar o aplicativo

Você deve considerar os seguintes fatores para localizar seu Microsoft Teams aplicativo:

1. [Localize sua listagem appSource](#localize-your-appsource-listing).
1. [Localize cadeias de caracteres no manifesto do aplicativo.](#localize-strings-in-your-app-manifest) 
1. [Manipular envios de texto localizados de seus usuários](#handle-localized-text-submissions-from-your-users).

## <a name="localize-your-appsource-listing"></a>Localize sua listagem do AppSource

Se você estiver publicando o aplicativo na loja, você deve estar ciente de que ainda não há suporte para a localização da listagem do AppSource. Para dar suporte a listagens localizadas na loja de aplicativos, você pode adicionar idiomas adicionais à sua listagem. As informações de idioma padrão fornecidas no [Partner Center](/office/dev/store/submit-to-appsource-via-partner-center) para sua listagem são exibidas na listagem de site do [AppSource](https://appsource.microsoft.com/marketplace/apps?product=office%3Bteams&page=1 "AppSource é um local para todas as necessidades da sua equipe. reúne tudo, incluindo chats, reuniões, chamadas, arquivos e ferramentas para habilitar o trabalho em equipe mais produtivo.") para seu aplicativo. Atualmente, o idioma padrão é inglês.

### <a name="configure-localization"></a>Configurar localização

Para configurar um idioma adicional para seu aplicativo, no [Partner Center,](/office/dev/store/submit-to-appsource-via-partner-center)selecione inglês e o idioma adicional do aplicativo. O francês é usado como um idioma adicional no exemplo a seguir:

1. Adicionar idioma inglês
    * Insira o nome do aplicativo.
    * Insira uma breve descrição do aplicativo em inglês.
    * Insira a descrição longa do aplicativo em inglês.
    * Na descrição longa, digite: **Este aplicativo está disponível em francês**.
    * Upload as imagens da interface do usuário do aplicativo (em inglês).
2. Adicionar idioma francês
    * Insira o nome do aplicativo.
    * Insira uma breve descrição do aplicativo em francês.
    * Insira a descrição longa do aplicativo em francês.
    * Upload as imagens da interface do usuário do aplicativo (em francês).

As imagens que você carrega com o idioma inglês são usadas no AppSource.

## <a name="localize-strings-in-your-app-manifest"></a>Localize cadeias de caracteres no manifesto do aplicativo

Você deve usar o esquema Microsoft Teams aplicativo e `v1.5` posteriormente para localizar seu aplicativo. Você pode fazer isso definindo o atributo em seu arquivo manifest.json ou superior e atualizando a propriedade para `$schema` **https://developer.microsoft.com/en-us/json-schemas/teams/v1.5/MicrosoftTeams.schema.json** versão ( neste `manifestVersion` `$schema` `1.5` caso). 

Você deve adicionar a `localizationInfo` propriedade com o idioma padrão compatível com o aplicativo. O idioma padrão é usado como o idioma de fallback final se as configurações do cliente do usuário não corresponderem a nenhum dos seus idiomas adicionais.

### <a name="example-manifestjson-change"></a>Exemplo manifest.jsna alteração

A manifest.jsa seguir ajuda a adicionar a propriedade com o idioma padrão compatível com `localizationInfo` o aplicativo junto com `additionalLanguages` :

```json
{
  "$schema": "https://developer.microsoft.com/en-us/json-schemas/teams/v1.5/MicrosoftTeams.schema.json",
  "manifestVersion": "1.5",
  "localizationInfo": {
        "defaultLanguageTag": "en",
        "additionalLanguages": [
            {
                "languageTag": "es-mx",
                "file": "es-mx.json"
            }
        ]
    }
  ...
}
```

### <a name="example-localization-json-change"></a>Exemplo de alteração de localização .json

A seguir está um exemplo para localização .json:

```json
{
  "$schema": "https://developer.microsoft.com/en-us/json-schemas/teams/v1.5/MicrosoftTeams.Localization.schema.json",
  "manifestVersion": "1.5",
  "name.short": "Localización",
  "name.full": "Aplicación de localización",
  ...
}
```


Você pode fornecer arquivos .json adicionais com traduções de todas as cadeias de caracteres voltadas para o usuário em seu manifesto. Esses arquivos devem aderir ao esquema [JSON](../../resources/schema/localization-schema.md) do arquivo de localização e devem ser adicionados à `localizationInfo` propriedade do manifesto. Cada arquivo se correlaciona a uma marca de idioma, que o cliente Teams usa para selecionar as cadeias de caracteres apropriadas. A marca de idioma assume a forma de, mas você pode omitir a parte para direcionar todas as regiões que `<language>-<region>` `<region>` suportam o idioma desejado.

O cliente Teams aplica as cadeias de caracteres na seguinte ordem: cadeias de caracteres de idioma padrão -> idioma do usuário somente cadeias de caracteres -> idioma do usuário + cadeias de caracteres de região do usuário.

Por exemplo, você fornece um idioma padrão de 'fr' (francês, todas as regiões) e arquivos de idiomas adicionais para 'en' (inglês, todas as regiões) e 'en-gb' (inglês, Grã-Bretanha), o idioma do usuário é definido como 'en-gb'. As seguintes alterações ocorrem com base na seleção de idioma:

1. O Teams cliente assume as cadeias de caracteres 'fr' e substitui-as com as cadeias de caracteres 'en'.
1. Sobrescreva as cadeias de caracteres 'en' com as cadeias de caracteres 'en-gb'.

Se o idioma do usuário for definido como 'en-ca', as seguintes alterações ocorrerão com base na seleção de idioma: 

1. O Teams cliente assume as cadeias de caracteres 'fr' e substitui-as com as cadeias de caracteres 'en'.
1. Como nenhuma localização 'en-ca' é fornecida, as localizações 'en' são usadas.

Se o idioma do usuário estiver definido como 'es-es', o cliente Teams assume as cadeias de caracteres 'fr'. O Teams cliente não substitui as cadeias de caracteres por nenhum dos arquivos de idioma, pois nenhuma tradução 'es' ou 'es-es' é fornecida.

Portanto, você deve fornecer traduções de nível superior, somente de idioma em seu manifesto. Por exemplo, 'en' em vez de 'en-us'. Você deve fornecer substituições de nível de região apenas para as poucas cadeias de caracteres que precisam delas. 

### <a name="example-manifestjson-change"></a>Exemplo manifest.jsna alteração

A manifest.jssobre a alteração é mostrada no exemplo a seguir:

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

 A localization.jssobre a alteração é mostrada no exemplo a seguir:

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

## <a name="handle-localized-text-submissions-from-your-users"></a>Manipular envios de texto localizados de seus usuários

Se você fornecer versões localizadas do aplicativo, os usuários responderão com o mesmo idioma. Como Teams não converte os envios de usuário de volta para o idioma padrão, seu aplicativo deve manipular as respostas de idioma localizado. Por exemplo, se você fornecer um localizado , as respostas ao bot serão o texto localizado do comando, não `commandList` o idioma padrão. Seu aplicativo deve responder adequadamente.

## <a name="code-sample"></a>Exemplo de código

| Nome do exemplo | Descrição | .NET | Node.js |
|-------------|-------------|------|------|
| Localização de aplicativos | Microsoft Teams localização de aplicativo usando bot e guia. | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/app-localization/csharp) |[View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/app-localization/nodejs) |

