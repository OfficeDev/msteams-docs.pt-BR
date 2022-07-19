---
title: Integrar o Seletor de Pessoas
description: Neste artigo, saiba como usar o SDK do cliente JavaScript Teams para integrar o controle Seletor de Pessoas e as vantagens de usar o seletor de pessoas.
ms.topic: conceptual
ms.localizationpriority: high
ms.author: surbhigupta
ms.openlocfilehash: 5a45f2c3a7d098bfe95b55620fb5909fb33e3472
ms.sourcegitcommit: 79d525c0be309200e930cdd942bc2c753d0b718c
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/19/2022
ms.locfileid: "66842000"
---
# <a name="integrate-people-picker"></a>Integrar o Seletor de Pessoas

O Seletor de Pessoas é um controle de entrada no Teams que permite aos usuários pesquisar e selecionar pessoas. Você pode integrar o controle de entrada do Seletor de Pessoas em um aplicativo Web, que permite que os usuários finais executem diferentes funções, tais como pesquisar e selecionar pessoas em um chat, canal ou em toda a organização dentro do Teams. O controle do Seletor de Pessoas está disponível em todos os clientes do Teams, como Web, área de trabalho e dispositivo móvel.

Você pode utilizar o [ SDK do cliente JavaScript do Microsoft Teams ](/javascript/api/overview/msteams-client?view=msteams-client-js-latest&preserve-view=true), que fornece a API `selectPeople` para integrar o controle de entrada do Seletor de Pessoas no seu aplicativo da Web.

## <a name="advantages-of-using-people-picker"></a>Vantagens de usar o Seletor de Pessoas

* Funciona em todas as funcionalidades do Teams, como módulo de tarefas, chat, canal, guia de reuniões e aplicativos pessoais.
* Permite que o usuário pesquise e selecione pessoas em um chat, canal ou toda a organização dentro do Teams.
* Ajuda em cenários que envolvem a atribuição de tarefas, marcação e notificação do usuário.
* Economiza tempo e esforços significativos em comparação com a construção de qualquer controle semelhante.

Para integrar o controle de entrada do Seletor de Pessoas no seu aplicativo Teams, use a API [`selectPeople`](#selectpeople-api). Para integrar e chamar a API, você deve ter uma boa compreensão do [trecho de código](#code-snippet) que a acompanha. Você também precisa estar familiarizado com [erros de réplica da API](#error-handling).

## <a name="selectpeople-api"></a>`selectPeople` API

A API `selectPeople` permite que você adicione o controle de entrada do Seletor de Pessoas do Teams para os aplicativos Web e também ajuda você com o seguinte:

* Permite que o usuário pesquise e selecione uma ou mais pessoas da lista.
* Retorna a ID, o nome e o endereço de email dos usuários selecionados para o aplicativo Web.

Em um aplicativo pessoal, o controle pesquisa por nome ou ID de email em toda a organização no Teams. Se o aplicativo for adicionado a um chat ou canal, o contexto de pesquisa será configurado com base no cenário. A pesquisar é restrita aos membros desse chat ou canal.

A API `selectPeople` vem com as seguintes configurações de entrada:

|Parâmetro de Configuração|Tipo|Descrição| Valor padrão|
|-----|------|--------------|------|
|`title`|Cadeia de caracteres| É um parâmetro opcional e define o título para o controle do Seletor de Pessoas.|`selectPeople`|
|`setSelected`|String| É um parâmetro opcional. Você deve passar IDs do Microsoft Azure Active Directory (Microsoft Azure AD) das pessoas a serem pré-selecionadas. Este parâmetro pré-seleciona as pessoas ao iniciar o controle de entrada do Seletor de Pessoas. Em uma única seleção, apenas o primeiro usuário válido é pré-preenchido, ignorando o restante.|**Null**|
|`openOrgWideSearchInChatOrChannel`|Boolean| É um parâmetro opcional e, quando definido como verdadeiro, inicia o Seletor de Pessoas em todo o escopo da organização, mesmo se o aplicativo for adicionado a um chat ou canal.|**Falso**|
|`singleSelect`|Booliano|É um parâmetro opcional e, quando definido como true, ele inicia o Seletor de Pessoas e restringe a seleção a apenas um usuário.|**Falso**|

A imagem a seguir mostra a experiência do Seletor de Pessoas em dispositivos móveis e na área de trabalho:

# <a name="mobile"></a>[Dispositivo móvel](#tab/Samplemobileapp)

O controle de entrada do Seletor de Pessoas permite que o usuário pesquise e adicione pessoas usando as seguintes etapas:

1. Digite o nome da pessoa obrigatória. A lista aparece com sugestões de nome.
1. Selecione o nome da pessoa obrigatória na lista.

   :::image type="content" source="../../assets/images/tabs/people-picker-control-capability-mobile-updated.png" alt-text="Selecionador do Seletor de Dispositivos Móveis":::

# <a name="desktop"></a>[Desktop](#tab/Sampledesktop)

O controle do Seletor de Pessoas na Web ou na área de trabalho é iniciado em uma janela modal na parte superior do aplicativo Web e, para adicionar pessoas, siga as seguintes etapas:

1. Digite o nome da pessoa obrigatória. A lista aparece com sugestões de nome.
1. Selecione o nome da pessoa obrigatória na lista.

   :::image type="content" source="../../assets/images/tabs/select-people-picker-byname.png" alt-text="Seletor de pessoas por nome de área de trabalho":::

---

## <a name="code-snippet"></a>Trecho de código

O trecho de código a seguir exibe o uso das pessoas da API `selectPeople` de uma lista:

# <a name="teamsjs-v2"></a>[TeamsJS v2](#tab/teamsjs-v2)

```javascript
people.selectPeople({ setSelected: ["aad id"], openOrgWideSearchInChatOrChannel: true, singleSelect: false, title: true}).then(people) => 
 {
    output(" People length: " + people.length + " " + JSON.stringify(people));
 }).catch((error) => { /*Unsuccessful operation*/ });
```

# <a name="teamsjs-v1"></a>[TeamsJS v1](#tab/teamsjs-v1)

```javascript
people.selectPeople((error: microsoftTeams.SdkError, people: microsoftTeams.people.PeoplePickerResult[]) => 
 {
    if (error) 
    {
        if (error.message) 
           {
             alert(" ErrorCode: " + error.errorCode + error.message);
           }
            else 
            {
              alert(" ErrorCode: " + error.errorCode);
            }
      }
    if (people)
     {
            output(" People length: " + people.length + " " + JSON.stringify(people));
      }
  },{ setSelected: ["aad id"], openOrgWideSearchInChatOrChannel: true, singleSelect: false, title: true});
```

***

## <a name="error-handling"></a>Tratamento de erros

A tabela a seguir lista os códigos de erro e suas descrições:

|Código de erro |  Nome do erro     | Descrição|
| --------- | --------------- | --------- |
| **100** | NÃO_SUPORTADO_NA_PLATAFORMA | A API não é compatível com a plataforma atual.|
| **500** | INTERNAL_ERROR | Erro interno encontrado ao iniciar o Seletor de Pessoas.|
| **4000** | ARGUMENTOS_INVÁLIDOS | A API foi invocada com argumentos obrigatórios incorretos ou insuficientes.|
| **8000** | ABORTAR_USUÁRIO |O usuário cancelou a operação.|
| **9000** | ANTIGA_PLATAFORMA | O usuário está em uma compilação antiga da plataforma em que a implementação da API não está disponível. Atualize para a versão mais recente da build para resolver o problema.|

## <a name="see-also"></a>Confira também

* [Integrar recursos de mídia](~/concepts/device-capabilities/media-capabilities.md)
* [Integrar a funcionalidade do código QR ou o verificador de código de barras no Teams](qr-barcode-scanner-capability.md)
* [Integrar funcionalidades de localização no Teams](location-capability.md)
