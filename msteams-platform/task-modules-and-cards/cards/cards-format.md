---
title: Formatação de texto em cartões
description: Descreve a formatação de texto dos cartões no Microsoft Teams
keywords: formato de cartões de bots do teams
ms.localizationpriority: high
ms.topic: reference
ms.date: 06/25/2021
ms.openlocfilehash: 9598ea8f241388e982d0ce0e05de0e5ed0b9e407
ms.sourcegitcommit: 0117c4e750a388a37cc189bba8fc0deafc3fd230
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65103948"
---
# <a name="format-cards-in-microsoft-teams"></a>Formatar cartões no Microsoft Teams

A seguir temos duas maneiras de adicionar uma formatação em rich text aos seus cartões:

* [Markdown](#format-cards-with-markdown)
* [HTML](#format-cards-with-html)

Os cartões aceitam formatação somente na propriedade texto, excluindo as propriedades título ou subtítulo. A formatação pode ser especificada usando-se um subconjunto de formatação XML ou HTML ou em Markdown, dependendo do tipo de cartão. Para o desenvolvimento atual e futuro de Cartões Adaptáveis, recomendamos a formatação Markdown.

O suporte à formatação difere entre os tipos de cartão. A renderização do cartão pode diferir ligeiramente entre os clientes de desktop e do aplicativo móvel do Microsoft Teams e também do Teams no navegador para desktop.

Você pode incluir uma imagem embutida em qualquer cartão do Teams. Os formatos de imagem com suporte são os formatos .png, .jpg ou .gif. Mantenha as dimensões dentro de 1024 x 1024 px e tamanho de arquivo menor que 1 MB. Não há suporte para imagens .gif animadas. Para obter mais informações, consulte [tipos de cartões](./cards-reference.md#inline-card-images).

Você pode formatar Cartões Adaptáveis e cartões do Conector do Office 365 em Markdown, o que inclui o suporte a determinados estilos.

## <a name="format-cards-with-markdown"></a>Formatar cartões em Markdown

Os seguintes tipos de cartão aceitam a formatação Markdown no Teams:

* Cartões Adaptáveis: há suporte para Markdown no campo `Textblock` do Cartão Adaptável e também nos campos `Fact.Title` e `Fact.Value`. Não há suporte para HTML nos Cartões Adaptáveis.
* Cartões do Conector do Office 365: os cartões do Conector do Office 365 aceitam Markdown e um HTML limitado nos campos de texto.

Você pode usar quebra de linha nos Cartões Adaptáveis usando as sequências de escape `\r` ou `\n` para quebras de linha nas listas. A formatação é diferente para as versões desktop e móvel do Teams para Cartões Adaptáveis. Há suporte para menções baseadas em cartões de clientes com as versões para web, desktop e móvel. Você pode usar a propriedade de mascaramento de informações para mascarar informações específicas, como senha ou informações confidenciais de usuários dentro do elemento de entrada `Input.Text` do Cartão Adaptável. Você pode expandir a largura de um Cartão Adaptável usando o objeto `width`. Você pode habilitar o suporte ao typeahead nos Cartões Adaptáveis e filtrar o conjunto de opções de entrada à medida que o usuário digita a entrada. Você pode usar a propriedade `msteams` para adicionar a capacidade de exibir seletivamente imagens no modo exibição estendida.

A formatação é diferente para as versões desktop e móvel do Teams para Cartões Adaptáveis e cartões de conector. Nesta seção, você pode analisar um exemplo do formato Markdown para Cartões Adaptáveis e cartões de conector.

# <a name="markdown-format-for-adaptive-cards"></a>[Formato Markdown para Cartões Adaptáveis](#tab/adaptive-md)

 A tabela a seguir fornece os estilos compatíveis para `Textblock`, `Fact.Title` e `Fact.Value`:

| Estilo | Exemplo | Markdown |
| --- | --- | --- |
| Negrito | **Negrito** | ```**Bold**``` |
| Itálico | _Itálico_ | ```_Italic_``` |
| Lista não ordenada | <ul><li>texto</li><li>texto</li></ul> | ```- Item 1\r- Item 2\r- Item 3``` |
| Lista ordenada | <ol><li>texto</li><li>texto</li></ol> | ```1. Green\r2. Orange\r3. Blue``` |
| Hiperlinks |[Bing](https://www.bing.com/)| ```[Title](url)``` |

Não há suporte para os seguintes rótulos do Markdown:

* Cabeçalhos
* Tabelas
* Imagens
* Texto pré-formatado
* Blockquotes

### <a name="newlines-for-adaptive-cards"></a>Quebras de linha para Cartões Adaptáveis

Você pode usar as sequências de escape `\r` ou `\n` para quebras de linha em listas. O uso de `\n\n` em listas faz com que o próximo elemento da lista fique recuado. Se você precisar de quebras de linha em outro lugar do TextBlock, use `\n\n`.

### <a name="mobile-and-desktop-differences-for-adaptive-cards"></a>Diferenças entre as versões desktop e móvel para Cartões Adaptáveis

Na versão desktop, a formatação Markdown para Cartões Adaptáveis aparece conforme mostrado na imagem a seguir, tanto em navegadores web quanto no aplicativo cliente do Teams:

:::image type="content" source="../../assets/images/Cards/Adaptive-markdown-desktop-client.png" alt-text="cliente área de trabalho markdown adaptável":::

No iOS, a formatação Markdown para Cartões Adaptáveis aparece conforme mostrado na imagem a seguir:

:::image type="content" source="../../assets/images/Cards/Adaptive-markdown-iOS-75.png" alt-text="Formatação Markdown para Cartões Adaptáveis no iOS":::

No Android, a formatação Markdown para Cartões Adaptáveis aparece conforme mostrado na imagem a seguir:

:::image type="content" source="../../assets/images/Cards/Adaptive-markdown-Android.png" alt-text="Formatação Markdown para Cartões Adaptáveis no Android":::

Para obter mais informações, consulte [recursos de texto nos Cartões Adaptáveis](/adaptive-cards/create/textfeatures).

> [!NOTE]
> Não há suporte no Teams para os recursos de data e localização mencionados nesta seção.

### <a name="adaptive-cards-format-sample"></a>Amostra do formato para Cartões Adaptáveis

O código a seguir mostra um exemplo de formatação de Cartões Adaptáveis:

``` json
{
    "$schema": "https://adaptivecards.io/schemas/adaptive-card.json",
    "type": "AdaptiveCard",
    "version": "1.0",
    "body": [
        {
            "type": "TextBlock",
            "text": "This is some **bold** text"
        },
        {
            "type": "TextBlock",
            "text": "This is some _italic_ text"
        },
        {
            "type": "TextBlock",
            "text": "- Bullet \r- List \r",
            "wrap": true
        },
        {
            "type": "TextBlock",
            "text": "1. Numbered\r2. List\r",
            "wrap": true
        },
        {
            "type": "TextBlock",
            "text": "Check out [Adaptive Cards](https://adaptivecards.io)"
        }
    ]
}
```

Os Cartões Adaptáveis oferecem suporte aos emojis. O código a seguir mostra um exemplo de Cartões Adaptáveis com um emoji:

``` json
{ "$schema": "http://adaptivecards.io/schemas/adaptive-card.json", "type": "AdaptiveCard", "version": "1.0", "body": [ { "type": "Container", "items": [ { "type": "TextBlock", "text": "Publish Adaptive Card with emojis 🥰 ", "weight": "bolder", "size": "medium" }, ] }, ], }
```

:::image type="content" source="../../assets/images/Cards/adaptive-card-emoji.png" alt-text="Cartão adaptável com um emoji":::

### <a name="mention-support-within-adaptive-cards"></a>Suporte a menções dentro dos Cartões Adaptáveis

Você pode adicionar @menções dentro de um corpo de Cartão Adaptável para respostas de bots e extensão de mensagem. Para adicionar @mentions nos cartões, siga a mesma lógica de notificação e renderização das [menções baseadas em mensagens nas conversas do canal e do chat em grupo](../../bots/how-to/conversations/channel-and-group-conversations.md#work-with-mentions).

Bots e extensões de mensagens podem incluir menções dentro do conteúdo do cartão nos elementos [TextBlock](https://adaptivecards.io/explorer/TextBlock.html) e [FactSet](https://adaptivecards.io/explorer/FactSet.html).

> [!NOTE]
>
> * Atualmente, não há suporte para [elementos de mídia](https://adaptivecards.io/explorer/Media.html) em Cartões Adaptáveis na plataforma do Teams.
> * Não há suporte para menções de canal e de equipe nas mensagens de bot.

Para incluir uma menção em um Cartão Adaptável, seu aplicativo precisa incluir os seguintes elementos:

* `<at>username</at>` nos elementos com suporte do Cartão Adaptável.
* O objeto `mention` dentro de uma propriedade `msteams` no conteúdo do cartão inclui a ID do usuário do Teams que está sendo mencionado.
* A`userId` é exclusiva da ID do seu bot e de um usuário específico. Pode ser usada para @mention um usuário específico. A `userId` pode ser recuperada usando uma das opções mencionadas em [como obter a ID do usuário](/microsoftteams/platform/bots/how-to/conversations/send-proactive-messages?tabs=dotnet#get-the-user-id-team-id-or-channel-id).

#### <a name="sample-adaptive-card-with-a-mention"></a>Amostra de um Cartão Adaptável com uma menção

O código a seguir mostra um exemplo de Cartão Adaptável com uma menção:

``` json
{
  "contentType": "application/vnd.microsoft.card.adaptive",
  "content": {
    "type": "AdaptiveCard",
    "body": [
      {
        "type": "TextBlock",
        "text": "Hi <at>John Doe</at>"
      }
    ],
    "$schema": "https://adaptivecards.io/schemas/adaptive-card.json",
    "version": "1.0",
    "msteams": {
      "entities": [
        {
          "type": "mention",
          "text": "<at>John Doe</at>",
          "mentioned": {
            "id": "29:123124124124",
            "name": "John Doe"
          }
        }
      ]
    }
  }
}
```

### <a name="microsoft-azure-active-directory-azure-ad-object-id-and-upn-in-user-mention"></a>ID de Objeto e UPN do Microsoft Azure Active Directory (Azure AD) na menção do usuário

A plataforma Teams permite mencionar usuários com a ID de Objeto do Microsoft Azure AD e o UPN (Nome de Princípio do Usuário), além das IDs de menção existentes. Bots com Cartões Adaptáveis e Conectores com Webhooks de Entrada oferecem suporte às duas IDs de menção de usuário.

A tabela a seguir descreve as IDs de menção de usuário que passaram a ter suporte recentemente:

|IDs  | Recursos que oferecem suporte | Descrição | Exemplo |
|----------|--------|---------------|---------|
| ID do objeto do Microsoft Azure AD | Bot, Conector |  ID de objeto do usuário do Microsoft Azure AD | 49c4641c-ab91-4248-aebb-6a7de286397b |
| UPN | Bot, Conector | UPN do usuário do Microsoft Azure AD | john.smith@microsoft.com |

#### <a name="user-mention-in-bots-with-adaptive-cards"></a>Menção de usuário em bots com Cartões Adaptáveis

Os bots dão suporte à menção de usuário com a ID de objeto e o UPN do Microsoft Azure AD, além das IDs existentes. O suporte para duas novas IDs está disponível em bots para mensagens de texto, corpo de Cartões Adaptáveis e resposta de extensão de mensagem. Os bots oferecem suporte às IDs de menção em conversas e cenários `invoke`. O usuário recebe uma notificação do feed de atividades quando estiver sendo mencionado (@mentioned) com as IDs.

> [!NOTE]
> As atualizações de esquema e as alterações da interface do usuário/experiência do usuário não são obrigatórias para menções do usuário com Cartões Adaptáveis em Bots.

##### <a name="example"></a>Exemplo

Exemplo de menção de usuário em bots com Cartões Adaptáveis como se segue:

```json
{
  "$schema": "http://adaptivecards.io/schemas/adaptive-card.json",
  "version": "1.0",
  "type": "AdaptiveCard",
  "body": [
    {
      "type": "TextBlock",
      "text": "Hi <at>Adele UPN</at>, <at>Adele Azure AD</at>"
    }
  ],
  "msteams": {
    "entities": [
      {
        "type": "mention",
        "text": "<at>Adele UPN</at>",
        "mentioned": {
          "id": "AdeleV@contoso.onmicrosoft.com",
          "name": "Adele Vance"
        }
      },
      {
        "type": "mention",
        "text": "<at>Adele Azure AD</at>",
        "mentioned": {
          "id": "87d349ed-44d7-43e1-9a83-5f2406dee5bd",
          "name": "Adele Vance"
        }
      }
    ]
  }
}
```

A imagem a seguir ilustra a menção do usuário com Cartão Adaptável no Bot:

:::image type="content" source="../../assets/images/authentication/user-mention-in-bot.png" alt-text="Menção do usuário em bot com Cartão Adaptável":::

#### <a name="user-mention-in-incoming-webhook-with-adaptive-cards"></a>Menção de usuário em um Webhook de Entrada com Cartões Adaptáveis

Os webhooks de entrada começam a dar suporte à menção de usuário Cartões Adaptáveis com a ID de objeto e o UPN do Microsoft Azure AD.

> [!NOTE]
>
> * Habilite a menção de usuário no esquema para webhooks de entrada para dar suporte à ID de Objeto e UPN do Microsoft Azure AD.
> * As alterações de interface do usuário/experiência do usuário não são necessárias para menções de usuário com a ID de Objeto do Microsoft Azure AD e o UPN.

##### <a name="example"></a>Exemplo

Exemplo de menção de usuário em Webhooks de Entrada como se segue:

```json
{
    "type": "message",
    "attachments": [
        {
        "contentType": "application/vnd.microsoft.card.adaptive",
        "content": {
            "type": "AdaptiveCard",
            "body": [
                {
                    "type": "TextBlock",
                    "size": "Medium",
                    "weight": "Bolder",
                    "text": "Sample Adaptive Card with User Mention"
                },
                {
                    "type": "TextBlock",
                    "text": "Hi <at>Adele UPN</at>, <at>Adele Azure AD</at>"
                }
            ],
            "$schema": "http://adaptivecards.io/schemas/adaptive-card.json",
            "version": "1.0",
            "msteams": {
                "entities": [
                    {
                        "type": "mention",
                        "text": "<at>Adele UPN</at>",
                        "mentioned": {
                          "id": "AdeleV@contoso.onmicrosoft.com",
                          "name": "Adele Vance"
                        }
                      },
                      {
                        "type": "mention",
                        "text": "<at>Adele Azure AD</at>",
                        "mentioned": {
                          "id": "87d349ed-44d7-43e1-9a83-5f2406dee5bd",
                          "name": "Adele Vance"
                        }
                      }
                ]
            }
        }
    }]
}
```

A imagem a seguir ilustra a menção do usuário em Webhooks de Entrada:

:::image type="content" source="../../assets/images/authentication/user-mention-in-incoming-webhook.png" alt-text="Menção do usuário em Webhooks de Entrada":::

### <a name="information-masking-in-adaptive-cards"></a>Mascaramento de informações em Cartões Adaptáveis

Use a propriedade “mascarar informações” para mascarar informações específicas, como senha ou informações confidenciais de usuários, dentro do elemento de entrada [`Input.Text`](https://adaptivecards.io/explorer/Input.Text.html) do Cartão Adaptável.

> [!NOTE]
> O recurso oferece suporte apenas ao mascaramento de informações do lado do cliente. O texto de entrada mascarado é enviado como texto claro para o endereço HTTPS do ponto de extremidade especificado durante a [configuração do bot](../../build-your-first-app/build-bot.md#4-register-your-bot-endpoint).

Para mascarar informações nos Cartões Adaptáveis, adicione a propriedade `style` para **digitar** `input.text` e defina o valor como **Password**.

#### <a name="sample-adaptive-card-with-masking-property"></a>Amostra de Cartão Adaptável com a propriedade de mascaramento

O código a seguir mostra um exemplo de Cartão Adaptável com a propriedade de mascaramento:

```json
{
    "type": "Input.Text",
    "id": "secretThing",
    "style": "password",
},
```

A imagem a seguir é um exemplo de mascaramento de informações em Cartões Adaptáveis:

:::image type="content" source="../../assets/images/Cards/masking-information-view.png" alt-text="Modo de exibição de informações de mascaramento":::

### <a name="full-width-adaptive-card"></a>Cartão Adaptável com largura total

Você pode usar a propriedade `msteams` para expandir a largura de um Cartão Adaptável e aproveitar um espaço de tela adicional. A próxima seção fornece informações sobre como usar a propriedade.

#### <a name="construct-full-width-cards"></a>Como construir cartões com largura total

Para criar um Cartão Adaptável com largura total, o objeto `width` na propriedade `msteams` do conteúdo do cartão deve ser definido como `Full`.

#### <a name="sample-adaptive-card-with-full-width"></a>Amostra de Cartão Adaptável com largura total

Para criar um Cartão Adaptável com largura total, seu aplicativo precisa incluir os elementos da amostra de código a seguir:

``` json
{
    "type": "AdaptiveCard",
    "body": [{
        "type": "Container",
        "items": [{
            "type": "TextBlock",
            "text": "Digest card",
            "size": "Large",
            "weight": "Bolder"
        }]
    }],

    "msteams": {
        "width": "Full"
    },
    "$schema": "http://adaptivecards.io/schemas/adaptive-card.json",
    "version": "1.2"
}
```

A imagem a seguir mostra um Cartão Adaptável com largura total:

:::image type="content" source="../../assets/images/Cards/full-width-adaptive-card.png" alt-text="Modo de exibição de um Cartão Adaptável com largura total":::

A imagem a seguir mostra o modo de exibição padrão do Cartão Adaptável quando a propriedade `width` não foi definida como **Full**:

:::image type="content" source="../../assets/images/Cards/small-width-adaptive-card.png" alt-text="Modo de exibição de um Cartão Adaptável com largura pequena":::

### <a name="typeahead-support"></a>Suporte ao typeahead

Dentro do elemento [`Input.Choiceset`](https://adaptivecards.io/explorer/Input.ChoiceSet.html) do esquema, pedir que os usuários filtrem e selecionem um número considerável de opções pode aumentar de forma significativa o tempo necessário para a conclusão da tarefa. O suporte ao typeahead nos Cartões Adaptáveis pode simplificar a seleção de entradas ao restringir ou filtrar o conjunto de opções de entrada à medida que o usuário digita a entrada.

Para habilitar o typeahead dentro do `Input.Choiceset`, defina o `style` como `filtered` e certifique-se de definir `isMultiSelect` como `false`.

#### <a name="sample-adaptive-card-with-typeahead-support"></a>Amostra de Cartão Adaptável com suporte ao typeahead

O código a seguir mostra um exemplo de Cartão Adaptável com suporte ao typeahead:

``` json
{
   "type": "Input.ChoiceSet",
   "label": "Select a user",
   "isMultiSelect": false,
   "choices":  [
      { "title": "User 1", "value": "User1" },
      { "title": "User 2", "value": "User2" }
    ],
   "style": "filtered"
}
```

### <a name="stage-view-for-images-in-adaptive-cards"></a>Modo exibição estendida para imagens nos Cartões Adaptáveis

Em um Cartão Adaptável, você pode usar a propriedade `msteams` para adicionar a capacidade de exibir seletivamente as imagens no modo exibição estendida. Quando passam o mouse sobre as imagens, os usuários podem ver um ícone de expansão para o qual o atributo `allowExpand` está definido como `true`. Para obter informações sobre como usar a propriedade, veja o exemplo a seguir:

``` json
{
    "type": "AdaptiveCard",
     "body": [
          {
            "type": "Image",
            "url": "https://picsum.photos/200/200?image=110",
            "msTeams": {
              "allowExpand": true
            }
          }
     ],
    "$schema": "http://adaptivecards.io/schemas/adaptive-card.json",
    "version": "1.2"
}
```

Quando os usuários passam o mouse sobre a imagem, um ícone de expansão aparece no canto superior direito, conforme mostrado na imagem a seguir:

:::image type="content" source="../../assets/images/Cards/adaptivecard-hover-expand-icon.png" alt-text="Cartão Adaptável com imagem expansível":::

A imagem aparece no modo de exibição estendida quando o usuário seleciona o ícone de expansão, conforme mostrado na imagem a seguir:

:::image type="content" source="../../assets/images/Cards/adaptivecard-expand-image.png" alt-text="Imagem expandida para a exibição estendida":::

Na exibição estendida, os usuários podem ampliar e reduzir a imagem. Você pode selecionar as imagens do seu Cartão Adaptável que precisam ter essa capacidade.

> [!NOTE]
>
> * A capacidade de ampliar e reduzir se aplica somente aos elementos de imagem com o tipo de imagem de um Cartão Adaptável.
> * No caso dos aplicativos móveis do Teams, a funcionalidade de exibição estendida para as imagens nos Cartões Adaptáveis está disponível por padrão. Os usuários podem visualizar as imagens do Cartão Adaptável no modo exibição estendida simplesmente tocando na imagem, independentemente de o atributo `allowExpand` estar presente ou não.

# <a name="markdown-format-for-office-365-connector-cards"></a>[Formato Markdown para cartões do Conector do Office 365](#tab/connector-md)

Os cartões de conector oferecem um suporte limitado à formatação Markdown e HTML.

| Estilo | Exemplo | Markdown |
| --- | --- | --- |
| Negrito | **text** | `**text**` |
| Itálico | _text_ | `*text*` |
| Cabeçalho (níveis 1&ndash;3) | **Texto** | `### Text`|
| Tachado | ~~text~~ | `~~text~~` |
| Lista não ordenada | <ul><li>texto</li><li>texto</li></ul> | ```- Item 1\r- Item 2\r- Item 3``` |
| Lista ordenada | <ol><li>texto</li><li>texto</li></ol> | ```1. Green\r2. Orange\r3. Blue``` |
| Texto pré-formatado | `text` | ``preformatted text`` |
| Blockquote | texto >blockquote | `>blockquote text` |
| Hiperlink | [Bing](https://www.bing.com/) | `[Bing](https://www.bing.com/)` |
| Link da imagem |![Pato em uma pedra](https://aka.ms/Fo983c) | `![Duck](https://aka.ms/Fo983c)` |

Nos cartões de conector, as quebras de linha são renderizadas para `\n\n`, mas não para `\n` ou `\r`.

### <a name="mobile-and-desktop-differences-for-connector-cards"></a>Diferenças entre as versões desktop e móvel para cartões de conector

Na versão desktop, a formatação Markdown para cartões de conector aparece conforme mostrado na imagem a seguir:

:::image type="content" source="../../assets/images/Cards/connector-desktop-markdown-combined.png" alt-text="Formatação markdown para cartões conectores":::

Na versão iOS, a formatação Markdown para cartões de conector aparece conforme mostrado na imagem a seguir:

:::image type="content" source="../../assets/images/Cards/connector-iphone-html-combined-80.png" alt-text="Formatação Markdown para cartões de conector no cliente iOS":::

Os cartões de conector que usam Markdown para iOS incluem os seguintes problemas:

* O cliente iOS para Teams não renderiza imagens embutidas com Markdown ou HTML nos cartões de conector.
* Os blockquotes são renderizados como recuados, mas sem fundo cinza.

No Android, a formatação Markdown para cartões de conector aparece conforme mostrado na imagem a seguir:

:::image type="content" source="../../assets/images/Cards/connector-android-markdown-combined.png" alt-text="Formatação Markdown para cartões de conector no cliente Android":::

### <a name="format-example-for-markdown-connector-cards"></a>Exemplo de formatação Markdown para cartões de conector

O código a seguir mostra um exemplo de formatação para cartões de conector em Markdown:

``` json
{
  "contentType": "application/vnd.microsoft.teams.card.o365connector",
  "content": {
    "@type": "MessageCard",
    "@context": "https://schema.org/extensions",
    "summary": "Summary",
    "title": "Connector Card Markdown formatting",
    "sections": [
        {
            "text": "This is some **bold** text"
        },
        {
            "text": "This is some _italic_ text"
        },
        {
            "text": "# Header 1\r## Header 2\r### Header 3"
        },
        {
            "text": "- Bullet \r- List \r"
        },
        {
            "text": "1. Numbered\r1. List \r"
        },
        {
            "text": "Link: [Bing](https://www.bing.com)"
        },
        {
            "text": "embedded image link: ![Duck on a rock](https://aka.ms/Fo983c)"
        },
        {
            "text": "`preformatted text`"
        },
        {
            "text": "Newlines (backslash n, backslash n):\n\nline a\n\nline b\n\nline c"
        },
        {
            "text": ">This is a blockquote"
        }
     ]
  }
}

```

---

## <a name="format-cards-with-html"></a>Formatar cartões em HTML

Os seguintes tipos de cartão oferecem suporte à formatação HTML no Teams:

* Cartões do Conector do Office 365: os cartões do Conector do Office 365 oferecem suporte limitado à formatação Markdown e HTML.
* Cartões com imagem em destaque e em miniatura: os cartões simples, como cartões com imagem em destaque e em miniatura, oferecem suporte aos rótulos HTML.

A formatação é diferente para as versões desktop e móvel do Teams para cartões do Conector do Office 365 e cartões simples. Nesta seção, você pode analisar um exemplo do formato HTML para cartões de conector e cartões simples.

# <a name="html-format-for-office-365-connector-cards"></a>[Formato HTML para cartões do Conector do Office 365](#tab/connector-html)

Os cartões de conector oferecem um suporte limitado à formatação Markdown e HTML.

| Estilo | Exemplo | HTML |
| --- | --- | --- |
| Negrito | **text** | `<strong>text</strong>` |
| Itálico | _text_ | `<em>text</em>` |
| Cabeçalho (níveis 1&ndash;3) | **Texto** | `<h3>Text</h3>` |
| Tachado | ~~text~~ | `<strike>text</strike>` |
| Lista não ordenada | <ul><li>texto</li><li>texto</li></ul> | `<ul><li>text</li><li>text</li></ul>` |
| Lista ordenada | <ol><li>texto</li><li>texto</li></ol> | `<ol><li>text</li><li>text</li></ol>` |
| Texto pré-formatado | `text` | `<pre>text</pre>` |
| Blockquote | <blockquote>texto</blockquote> | `<blockquote>text</blockquote>` |
| Hiperlink | [Bing](https://www.bing.com/) | `<a href="https://www.bing.com/">Bing</a>` |
| Link da imagem | <img src="https://aka.ms/Fo983c" alt="Duck on a rock"></img> | `<img src="https://aka.ms/Fo983c" alt="Duck on a rock"></img>` |

Nos cartões de conector, as quebras de linha são renderizadas em HTML usando o rótulo `<p>`.

### <a name="mobile-and-desktop-differences-for-connector-cards"></a>Diferenças entre as versões desktop e móvel para cartões de conector

Na versão desktop, a formatação HTML para cartões de conector aparece conforme mostrado na imagem a seguir:

:::image type="content" source="../../assets/images/Cards/Connector-desktop-html-combined.png" alt-text="Formatação HTML para cartões de conector no cliente desktop":::

No iOS, a formatação HTML aparece conforme mostrado na imagem a seguir:

:::image type="content" source="../../assets/images/Cards/connector-iphone-html-combined-80.png" alt-text="Formatação HTML para cartões de conector no cliente iOS":::

Os cartões de conector que usam HTML para iOS incluem os seguintes problemas:

* As imagens embutidas não são renderizadas nos cartões de conector em iOS usando Markdown ou HTML.
* O texto pré-formatado é renderizado, mas não tem fundo cinza.

No Android, a formatação HTML aparece conforme mostrado na imagem a seguir:

:::image type="content" source="../../assets/images/Cards/connector-android-html-combined.png" alt-text="Formatação HTML para cartões de conector no cliente Android":::

### <a name="format-sample-for-html-connector-cards"></a>Amostra de formatação HTML para cartões de conector

O código a seguir mostra um exemplo de formatação HTML para cartões de conector:

``` json
{
  "contentType": "application/vnd.microsoft.teams.card.o365connector",
  "content": {
    "@type": "MessageCard",
    "@context": "https://schema.org/extensions",
    "summary": "Summary",
    "title": "Connector Card HTML formatting",
    "sections": [
        {
            "text": "This is some <strong>bold</strong> text"
        },
        {
            "text": "This is some <em>italic</em> text"
        },
        {
            "text": "This is some <strike>strikethrough</strike> text"
        },
        {
            "text": "<h1>Header 1</h1>\r<h2>Header 2</h2>\r <h3>Header 3</h3>"
        },
        {
            "text": "bullet list <ul><li>text</li><li>text</li></ul>"
        },
        {
            "text": "ordered list <ol><li>text</li><li>text</li></ol>"
        },
        {
            "text": "hyperlink <a href=\"https://www.bing.com/\">Bing</a>"
        },
        {
            "text": "embedded image <img src=\"https://aka.ms/Fo983c\" alt=\"Duck on a rock\"></img>"
        },
        {
            "text": "preformatted text <pre>text</pre>"
        },
        {
            "text": "Paragraphs <p>Line a</p><p>Line b</p>"
        },
        {
            "text": "<blockquote>Blockquote text</blockquote>"
        }
     ]
  }
}

```

# <a name="html-format-for-hero-and-thumbnail-cards"></a>[Formato HTML para cartões com imagens em destaque e em miniatura](#tab/simple-html)

Os cartões simples, como cartões com imagem em destaque e em miniatura, oferecem suporte aos rótulos HTML. Não há suporte para Markdown.

| Estilo | Exemplo | HTML |
| --- | --- | --- |
| Negrito | **text** | `<strong>text</strong>` |
| Itálico | _text_ | `<em>text</em>` |
| Cabeçalho (níveis 1&ndash;3) | **Texto** | `<h3>Text</h3>` |
| Tachado | ~~text~~ | `<strike>text</strike>` |
| Lista não ordenada | <ul><li>texto</li><li>texto</li></ul> | `<ul><li>text</li><li>text</li></ul>` |
| Lista ordenada | <ol><li>texto</li><li>texto</li></ol> | `<ol><li>text</li><li>text</li></ol>` |
| Texto pré-formatado | `text` | `<pre>text</pre>` |
| Blockquote | <blockquote>texto</blockquote> | `<blockquote>text</blockquote>` |
| Hiperlink | [Bing](https://www.bing.com/) | `<a href="https://www.bing.com/">Bing</a>` |
| Link da imagem |<img src="https://aka.ms/Fo983c" alt="Duck on a rock"></img>| `<img src="https://aka.ms/Fo983c" alt="Duck on a rock"></img>` |

### <a name="mobile-and-desktop-differences-for-simple-cards"></a>Diferenças entre as versões desktop e móvel para cartões simples

Como existem diferenças de resolução entre as plataformas desktop e móvel, a formatação é diferente para as versões desktop e móvel do Teams.

Na versão desktop, a formatação HTML aparece conforme mostrado na imagem a seguir:

:::image type="content" source="../../assets/images/Cards/card-formatting-xml-desktop-v2.png" alt-text="Formatação HTML no cliente desktop":::

No iOS, a formatação HTML aparece conforme mostrado na imagem a seguir:

:::image type="content" source="../../assets/images/Cards/card-formatting-xml-mobile-v2.png" alt-text="Formatação HTML no cliente iOS":::

A formatação de caracteres, como negrito e itálico, não é renderizada no iOS.

No Android, a formatação HTML aparece conforme mostrado na imagem a seguir:

:::image type="content" source="../../assets/images/Cards/card-formatting-xml-android-60.png" alt-text="Formatação HTML no cliente Android":::

A formatação de caracteres, como negrito e itálico, aparece corretamente no Android.

### <a name="format-example-for-simple-cards"></a>Exemplo de formatação para cartões simples

As imagens na seção anterior foram criadas usando o **App Studio** do Teams, no qual a propriedade de texto de um cartão com imagem em destaque é definida como a seguinte cadeia de caracteres:

`<p>bold: <strong>Bold Text</strong></p><p>italic: <em>Italic Text</em></p><p>strikethrough: <strike>Strikethrough text</strike></p><h1>Header 1</h1><h2>Header 2</h2><h3>Header 3</h3><p>bullet list: <ul><li>text</li><li>text</li></ul></p><p>ordered list: <ol><li>text</li><li>text</li></ol></p><pre>preformatted text</pre><blockquote>blockquote text</blockquote></p><p>hyperlink: <a href=\"https://www.bing.com/\">Bing</a></p><p>embedded image: <img src=\"https://aka.ms/Fo983c\" alt=\"Duck on a rock\"></img></p>`

Você pode testar a formatação nos seus próprios cartões modificando esse código.

---

## <a name="see-also"></a>Confira também

* [Ações do cartão](./cards-actions.md)
* [Usar módulos de tarefas dos bots](~/task-modules-and-cards/task-modules/task-modules-bots.md)
* [Módulos de tarefas](~/task-modules-and-cards/cards/cards-format.md)
* [Formatar suas mensagens de bot](~/bots/how-to/format-your-bot-messages.md)
* [Explorador de Esquema para Cartões Adaptáveis](https://adaptivecards.io/explorer/TextBlock.html)
