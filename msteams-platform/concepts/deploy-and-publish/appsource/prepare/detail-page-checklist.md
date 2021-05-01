---
title: Criar uma listagem de loja para seu aplicativo
description: Descreve como criar uma listagem de loja para seu Microsoft Teams app.
ms.topic: how-to
localization_priority: Normal
author: heath-hamilton
ms.author: surbhigupta
ms.openlocfilehash: 270936ca967c17caaa8a56f85057b20ca3d6a409
ms.sourcegitcommit: 25c9ad27f99682caaa7347840578b118c63b8f69
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/30/2021
ms.locfileid: "52101426"
---
# <a name="create-a-store-listing-for-your-microsoft-teams-app"></a>Criar uma listagem da loja para seu Microsoft Teams app

As informações que você envia ao [Partner Center](https://partner.microsoft.com)&#8212;incluindo seu nome, descrições, ícones e imagens&#8212;se tornam o Microsoft Teams store e a listagem do Microsoft AppSource para seu aplicativo.

Uma listagem da loja pode ser a primeira impressão de alguém do seu aplicativo. Aumente suas instalações com uma listagem que transmite efetivamente os benefícios, a funcionalidade e a marca do seu aplicativo.

## <a name="specify-a-short-name"></a>Especificar um nome curto

O nome do seu aplicativo (especificamente, seu [*nome*](~/resources/schema/manifest-schema.md#name)curto ) desempenha uma função crucial na forma como os usuários o descobrem na loja.

O exemplo a seguir destaca onde o nome curto de um aplicativo é exibido em uma listagem da loja.

:::image type="content" source="../../../../assets/images/store-detail-page/AppName-02.png" alt-text="Exemplo de captura de tela realça onde o nome curto de um aplicativo é exibido em uma listagem da loja.":::

### <a name="best-practices-for-names"></a>Práticas recomendadas para nomes

**Faça:**

* Escolha um nome simples e memorável que indica o que seu aplicativo faz.
* Seja distinto.
* Evite erros de digitação e gramatical.

**Não faça:**

* Use termos profano ou depreciativo.
* Use linguagem racial ou culturalmente insensível.
* Use termos genéricos ou nomes semelhantes aos aplicativos existentes.
* Inclua "Teams", "Microsoft", nomes de produtos da Microsoft existentes/futuros ou "aplicativo" no nome.

> [!NOTE]
> Se seu aplicativo faz parte de uma parceria oficial com a Microsoft, o nome do seu aplicativo deve vir primeiro (por exemplo, *Salesforce Connector para* Microsoft Teams ).

## <a name="write-descriptions"></a>Descrições de gravação

Você precisa de uma descrição curta e longa do seu aplicativo.

### <a name="short-description"></a>Descrição breve

Um resumo conciso do seu aplicativo que deve ser original, envolvente e direcionado para seu público-alvo. O ideal é manter a descrição curta em uma frase.

O exemplo a seguir destaca onde a descrição curta de um aplicativo é exibida em uma listagem da loja:

:::image type="content" source="~/assets/images/store-detail-page/ShortDescription-02.png" alt-text="Exemplo de captura de tela realça onde a descrição curta de um aplicativo é exibida em uma listagem da loja.":::

#### <a name="best-practices-for-short-descriptions"></a>Práticas recomendadas para descrições curtas

**Faça:**

* Fale primeiro as informações mais importantes.
* Inclua palavras-chave que os clientes provavelmente procurarão.

**Não faça:**

* Repita o nome do aplicativo.
* Conte com jargão ou terminologia especializada. (Não é possível supor que os usuários saibam o que procurar.)

### <a name="long-description"></a>Descrição longa

A descrição longa pode fornecer uma narração envolvente que realça os principais recursos do seu aplicativo, os problemas que ele resolve e seu público-alvo. Embora essa descrição possa ter até 4.000 caracteres, a maioria dos usuários lerá apenas entre 300 e 500 palavras.

O exemplo a seguir destaca onde a descrição longa de um aplicativo é exibida em uma listagem da loja:

:::image type="content" source="~/assets/images/store-detail-page/ShortDescription-02.png" alt-text="Exemplo de captura de tela realça onde a descrição longa de um aplicativo é exibida em uma listagem da loja.":::

#### <a name="usage-examples"></a>Exemplos de uso

As frases a seguir são exemplos do que é permitido ao escrever descrições longas:

* "<seu *nome de aplicativo*> funciona com Microsoft Teams"
* "... um <*tipo de aplicativo>* para Microsoft Teams"
* "<seu *nome de aplicativo*> se integra ao Microsoft Teams"
* "... integrado ao Microsoft Teams"
* "... para usuários que trabalham com Microsoft Teams"
* "... para <*tarefa específica>* dentro Microsoft Teams"
* "... built on ..."
* "... é executado em ..."
* "... habilitado por ..."
* "... desenvolvido para ..."
* "... projetado para ..."

#### <a name="best-practices-for-long-descriptions"></a>Práticas recomendadas para descrições longas

**Faça:**

* Use [Markdown](https://support.office.com/article/use-markdown-formatting-in-teams-4d10bd65-55e2-4b2d-a1f3-2bebdcd2c772) para formatar sua descrição.
* List features with bullet points so it's easier to scan the description.
* Use voz ativa e fale diretamente com os usuários (por exemplo, *você pode ...*).
* Inclua uma ajuda ou um link de suporte.
* Identifique o seguinte, se aplicável: limitações, configurar informações, dependências de conta e atualizações de versão.

**Não faça:**

* Exceder 500 palavras.
* Inclua muitas palavras-chave. (Isso distrai e não ajuda as pessoas a encontrar seu aplicativo.)
* Use o seguinte idioma, a menos que o aplicativo tenha passado por um processo de certificação oficial:
  * "... certificado para ..."
  * " ... alimentado por ..."

### <a name="best-practices-for-all-descriptions"></a>Práticas recomendadas para todas as descrições

**Faça:**

* Fazer referência a nomes de produtos da Microsoft somente quando necessário. Para obter mais informações sobre as diretrizes, consulte [Diretrizes de Marca](https://www.microsoft.com/en-us/legal/intellectualproperty/trademarks/usage/general)e Marca da Microsoft.
* Se você precisar fazer referência **Teams,** escreva a primeira referência como **Microsoft Teams**. Referências subsequentes podem ser reduzidas **para Teams**.
* Consulte **Microsoft 365** em vez de **Office 365**.
* Evite erros de digitação e gramatical.
* Evite maiúsculas desnecessárias (por exemplo, **Usuários** em vez de **usuários**).
* Evite acrônimos.

**Não faça:**

* Abreviar a Microsoft como **MS** ou **MSFT**.
* Indique que o aplicativo é uma oferta da Microsoft, incluindo o uso de lemas ou linhas de marcação da Microsoft.
* Use nomes de marca protegidos por direitos autorais que você não possui.

## <a name="adhere-to-icon-design-guidelines"></a>Seguir as diretrizes de design de ícones

Os ícones são um dos principais elementos que os usuários veem ao navegar na loja. Seus ícones devem comunicar a finalidade da marca do seu aplicativo enquanto também aderem aos Teams requisitos.

Para obter mais informações, [consulte orientações específicas sobre como projetar Teams ícones do aplicativo.](~/concepts/build-and-test/apps-package.md#app-icons)

## <a name="capture-screenshots"></a>Capturar capturas de tela

As capturas de tela fornecem uma visualização visual proeminente do seu aplicativo para complementar o nome, o ícone e as descrições do aplicativo.

### <a name="requirements-for-screenshots"></a>Requisitos para capturas de tela

* Até cinco capturas de tela por listagem.
* Os tipos de arquivo com suporte incluem PNG, JPEG e GIF.
* As dimensões devem ter 1366 x 768 pixels.
* Tamanho máximo de 1.024 KB.

### <a name="best-practices-for-screenshots"></a>Práticas recomendadas para capturas de tela

**Faça:**

* Concentre-se nos recursos do seu aplicativo (por exemplo, como as pessoas podem se comunicar com seu bot).
* Inclua conteúdo que represente com precisão seu aplicativo.
* Use texto criteriosamente.
* Capturas de tela de quadro com uma cor que reflete sua marca e incluem conteúdo de marketing, semelhante ao exemplo do [Freshdesk](https://appsource.microsoft.com/product/office/WA104381505?src=office&tab=Overview) a seguir (requisitos de dimensão se aplicam a toda a imagem e não apenas à captura de tela): Exemplo de captura de tela do aplicativo de terceiros   :::image type="content" source="../../../../assets/images/freshdesk.png" alt-text="Freshdesk":::

**Não faça:**

* Mostrar dispositivos específicos, como telefones ou laptops.
* Exibe o cromado ou a interface do usuário que não está em seu aplicativo.
* Capture qualquer Teams ou interface do usuário do navegador em suas capturas de tela.
* Inclua simulações que refletem imprecisamente a interface do usuário real do aplicativo, como mostrar seu aplicativo em um navegador em vez de uma guia Teams.

Para obter mais práticas recomendadas, consulte [craft effective images for Microsoft app stores](/office/dev/store/craft-effective-appsource-store-images).

## <a name="create-a-video"></a>Criar um vídeo

Um vídeo pode ser a maneira mais eficaz de comunicar por que as pessoas devem usar seu aplicativo. Você deve resolver as seguintes perguntas em um vídeo:

* Who seu aplicativo é para?
* Quais problemas seu aplicativo pode resolver?
* Como seu aplicativo funciona?
* Quais outros benefícios você obter com o uso do aplicativo?

Se você incluir um vídeo, ele aparecerá antes das capturas de tela na listagem.

### <a name="best-practices-for-videos"></a>Práticas recomendadas para vídeos

* Mantenha seu vídeo entre 30 e 90 segundos.
* Aponte para a qualidade. Em uma listagem, os usuários verão seu vídeo antes das capturas de tela.

## <a name="localize-your-store-listing"></a>Localize sua listagem da loja

O Partner Center dá [suporte a listagens de armazenamento localizado.](https://docs.microsoft.com/office/dev/store/prepare-localized-solutions) Para obter mais informações, [consulte como localizar sua Teams de aplicativos](../../../../concepts/build-and-test/apps-localization.md).

## <a name="see-also"></a>Confira também

* [Criar listagens Microsoft 365 Stores eficazes](/office/dev/store/create-effective-office-store-listings)
* Teams de design de aplicativos para [cópia e conteúdo e](~/concepts/design/design-teams-app-fundamentals.md#copy-and-content) expressão de [marca](~/concepts/design/design-teams-app-fundamentals.md#brand-expression)
* [Diretrizes de marca e marca da Microsoft](https://www.microsoft.com/en-us/legal/intellectualproperty/trademarks/usage/general)

## <a name="next-step"></a>Próxima etapa

> [!div class="nextstepaction"]
> [Preparar o envio da loja](~/concepts/deploy-and-publish/appsource/prepare/submission-checklist.md)
