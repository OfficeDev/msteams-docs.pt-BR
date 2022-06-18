---
title: Localizar o aplicativo
description: Conheça as considerações para localizar seu aplicativo Microsoft Teams e localizar cadeias de caracteres no manifesto do aplicativo.
ms.topic: conceptual
ms.localizationpriority: medium
ms.date: 05/15/2018
ms.openlocfilehash: 5c3d0612f0e7ce0e183d097469165cf2f9c337d0
ms.sourcegitcommit: 9d318eda5589ea8f5519d05cb83e0acf3e13e2f4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/17/2022
ms.locfileid: "66150663"
---
# <a name="localize-your-app"></a>Localizar o aplicativo

Considere os seguintes fatores para localizar seu aplicativo do Microsoft Teams:

1. [Localize sua listagem do AppSource](#localize-your-appsource-listing).
1. [Localize cadeias de caracteres no manifesto do aplicativo](#localize-strings-in-your-app-manifest).
1. [Trate envios de texto localizados de seus usuários](#handle-localized-text-submissions-from-your-users).

## <a name="localize-your-appsource-listing"></a>Criar sua listagem do AppSource

Se você estiver publicando o aplicativo na loja, forneça metadados (descrições, capturas de tela, nome) nos idiomas em que deseja que seu aplicativo seja listado e especifique explicitamente esses idiomas na página **de listagem do Marketplace** no Partner Center. Para obter mais informações, consulte as [frentes do Microsoft AppSource localizadas](/office/dev/store/prepare-localized-solutions#localized-microsoft-appsource-fronts). Para dar suporte a listagem localizada na loja de aplicativos, você pode adicionar idiomas adicionais à sua listagem. As informações de idioma padrão fornecidas no [Partner Center](/office/dev/store/submit-to-appsource-via-partner-center) para sua listagem aparecem na listagem do [site do AppSource](https://appsource.microsoft.com/marketplace/apps?product=office%3Bteams&page=1 "O AppSource é um local para todas as necessidades da sua equipe. Reúna tudo, incluindo chats, reuniões, chamadas, arquivos e ferramentas para habilitar o trabalho em equipe mais produtivo.") para seu aplicativo. Atualmente, o idioma padrão é inglês.

### <a name="configure-localization"></a>Configurar localização

Para configurar um idioma adicional para seu aplicativo, no [Partner Center](/office/dev/store/submit-to-appsource-via-partner-center), selecione inglês e o idioma adicional do aplicativo. O francês é usado como um idioma adicional no exemplo a seguir:

1. Adicionar idioma inglês
    * Insira o nome do aplicativo.
    * Insira uma breve descrição do aplicativo em inglês.
    * Insira a descrição longa do aplicativo em inglês.
    * Na descrição longa, insira: **Este aplicativo está disponível em francês**.
    * Carregue as imagens da interface do usuário do aplicativo (em inglês).
2. Adicione o idioma francês
    * Insira o nome do aplicativo.
    * Insira uma breve descrição do aplicativo em francês.
    * Insira a descrição longa do aplicativo em francês.
    * Carregue as imagens da interface do usuário do aplicativo (em francês).

As imagens carregadas com o idioma inglês são usadas no AppSource.

## <a name="localize-strings-in-your-app-manifest"></a>Localizar cadeias de caracteres no manifesto do aplicativo

Use o esquema de aplicativo do Microsoft Teams `v1.5` e posterior para localizar seu aplicativo. Você pode fazer isso definindo o atributo `$schema` no arquivo manifest.json como `https://developer.microsoft.com/json-schemas/teams/v1.5/MicrosoftTeams.schema.json` ou superior e atualizando a propriedade `manifestVersion` para a versão`$schema` (`1.5` nesse caso).

Adicione a propriedade `localizationInfo` com o idioma padrão ao qual seu aplicativo dá suporte. O idioma padrão será usado como o idioma de fallback final se as configurações do cliente do usuário não corresponderem a nenhum dos seus idiomas adicionais.

### <a name="example-manifestjson-change"></a>Exemplo de alteração de manifest.json

O seguinte `manifest.json` ajuda a adicionar a propriedade `localizationInfo` com o idioma padrão ao qual seu aplicativo dá suporte, juntamente com `additionalLanguages`:

```json
{
  "$schema": "https://developer.microsoft.com/json-schemas/teams/v1.5/MicrosoftTeams.schema.json",
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

A seguir está um exemplo de localização .json:

```json
{
  "$schema": "https://developer.microsoft.com/json-schemas/teams/v1.5/MicrosoftTeams.Localization.schema.json",
  "manifestVersion": "1.5",
  "name.short": "Localización",
  "name.full": "Aplicación de localización",
  ...
}
```

Você pode fornecer arquivos .json adicionais com traduções de todas as cadeias de caracteres voltadas para o usuário em seu manifesto. Esses arquivos devem aderir ao [esquema JSON do arquivo de localização](../../resources/schema/localization-schema.md) e devem ser adicionados `localizationInfo`à propriedade do manifesto. Cada arquivo se correlaciona a uma marca de idioma, que o Teams cliente usa para selecionar as cadeias de caracteres apropriadas. A marca de idioma assume a forma `<language>-<region>` mas você pode a parte `<region>` para direcionar todas as regiões que dão suporte ao idioma desejado.

O cliente do Teams aplica as cadeias de caracteres na seguinte ordem: cadeias de caracteres de idioma padrão -> cadeias de caracteres somente de idioma do usuário -> idioma do usuário + cadeias de caracteres de região do usuário.

Por exemplo, você fornece um idioma padrão de 'fr' (francês, todas as regiões) e arquivos de idioma adicionais para 'en' (inglês, todas as regiões) e 'en-gb' (inglês, Inglaterra), o idioma do usuário é definido como 'en-gb'. As seguintes alterações ocorrem com base na seleção de idioma:

1. O Teams cliente usa as cadeias de caracteres 'fr' e as substitui com as cadeias de caracteres 'en'.
1. Substitua as cadeias de caracteres 'en' com as cadeias de caracteres 'en-gb'.

Se o idioma do usuário estiver definido como 'en-ca', as seguintes alterações ocorrerão com base na seleção do idioma:

1. O Teams cliente usa as cadeias de caracteres 'fr' e as substitui com as cadeias de caracteres 'en'.
1. Como nenhuma localização 'en-ca' é fornecida, as localizações 'en' são usadas.

Se o idioma do usuário estiver definido como 'es-es', o Teams cliente usa as cadeias de caracteres 'fr'. O Teams cliente não substitui as cadeias de caracteres por nenhum dos arquivos de idioma, pois nenhuma tradução 'es' ou 'es-es' é fornecida.

Portanto, você deve fornecer traduções somente de idioma de nível superior em seu manifesto. Por exemplo, `en` em vez de `en-us`. Você deve fornecer substituições no nível da região somente para as poucas cadeias de caracteres que precisam delas.

### <a name="example-manifestjson-change"></a>Exemplo de alteração de manifest.json

O `manifest.json` é mostrado no exemplo a seguir:

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

 O `localization.json` é mostrado no exemplo a seguir:

```json
{
  "$schema": "https://developer.microsoft.com/json-schemas/teams/v1.8/MicrosoftTeams.Localization.schema.json",
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

Se você fornecer versões localizadas do seu aplicativo, os usuários responderão com o mesmo idioma. Como Teams não converte os envios de usuário de volta para o idioma padrão, seu aplicativo deve lidar com as respostas de idioma localizadas. Por exemplo, se você fornecer `commandList` um localizado, as respostas ao bot serão o texto localizado do comando, não o idioma padrão. Seu aplicativo deve responder adequadamente.

## <a name="code-sample"></a>Exemplo de código

| Nome do exemplo | Descrição | .NET | Node.js |
|-------------|-------------|------|------|
| Localização de aplicativo | Teams localização do aplicativo usando bot e guia. | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/app-localization/csharp) |[Exibir](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/app-localization/nodejs) |

## <a name="see-also"></a>Confira também

[Localizar referências do esquema JSON](~/resources/schema/localization-schema.md)
