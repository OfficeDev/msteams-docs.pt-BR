---
title: Reordenar guias de aplicativos pessoais
description: Como reordenar as guias estáticas do aplicativo pessoal no seu aplicativo pessoal
keywords: desenvolvimento de guias do teams
ms.openlocfilehash: a8a7c3d23bac98ef1085a8f3443ca0fc92ae0a31
ms.sourcegitcommit: bfdcd122b6b4ffc52d92320d4741f870c07f0542
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2020
ms.locfileid: "49554823"
---
# <a name="reorder-personal-app-tabs"></a>Reordenar guias de aplicativos pessoais

Começando com o manifesto versão 1,7 os desenvolvedores podem reorganizar todas as guias em seus aplicativos pessoais. Em particular, um desenvolvedor pode mover a guia "chat de bot" (que sempre tem o padrão para a primeira posição) em qualquer lugar no cabeçalho da guia do aplicativo pessoal. Declaramos duas palavras-chave de EntityId da guia reservadas: "conversas" e "sobre".

## <a name="moving-the-chatconversation-tab"></a>Movendo a guia "chat/conversa"

Se você criar um bot com um escopo "pessoal", ele sempre será exibido na primeira posição de tabulação em um aplicativo pessoal. Se quiser movê-lo para outra posição, você precisará adicionar um objeto Tab estático ao manifesto com a palavra-chave reservada "conversas". Sempre que você adicionar a guia "conversas" na matriz "staticTabs", será onde a guia conversa aparecerá na Web e na área de trabalho. 

```json
{
   "staticTabs":[
      {
         
      },
      {
         "entityId":"conversations",
         "scopes":[
            "personal"
         ]
      }
   ]
}
```

> [!NOTE]
> Observe que esse comportamento não é refletido no Mobile, pois o chat do Personal bot já tem um local exclusivo no aplicativo pessoal.

## <a name="moving-the-about-tab"></a>Mover a guia "sobre"

A guia "sobre" sempre é padrão para o final da barra de cabeçalho da guia aplicativo pessoal. Se quiser movê-lo para outra posição, você precisará usar o EntityId "sobre".

```json
{
   "staticTabs":[
      {
         
      },
      {
         "entityId":"about",
         "scopes":[
            "personal"
         ]
      }
   ]
}
```
> [!NOTE]
> Observe que a guia sobre não é mostrada em celular.

## <a name="example-code"></a>Código de exemplo

```json
{
   "staticTabs":[
      {
         "entityId":"homeTab",
         "name":"Home",
         "contentUrl":"https://www.contoso.com",
         "websiteUrl":" https://www.contoso.com ",
         "scopes":[
            "personal"
         ]
      },
      {
         "entityId":"about",
         "scopes":[
            "personal"
         ]
      },
      {
         "entityId":"conversations",
         "scopes":[
            "personal"
         ]
      }
   ]
}
```
