---
title: Permitir que seu aplicativo seja personalizado
author: heath-hamilton
description: Entenda como Teams administradores podem personalizar seu aplicativo para sua organização.
localization_priority: Normal
ms.author: surbhigupta
ms.topic: overview
ms.openlocfilehash: 8d7cad42bcb8e6892c25c3c24b50f938624e665a50274395bad00c07f0f1576c
ms.sourcegitcommit: 3ab1cbec41b9783a7abba1e0870a67831282c3b5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/07/2021
ms.locfileid: "57703597"
---
# <a name="enable-your-microsoft-teams-app-to-be-customized"></a>Permitir que seu Microsoft Teams aplicativo seja personalizado

Você pode permitir que os clientes personalizem alguns aspectos do seu aplicativo Microsoft Teams no centro de Teams de administração. Esse recurso só é suportado para aplicativos publicados no Teams store. Aplicativos e aplicativos com sideload publicados para uma organização não podem ser personalizados.

> [!IMPORTANT]
> Atualmente, os aplicativos de sideload estão disponíveis no Nuvem da Comunidade Governamental (GCC), mas não estão disponíveis para GCC-High e Departamento de Defesa (DOD).

Alguns exemplos possíveis desse recurso incluem:

* Alterar a cor de destaque do aplicativo para corresponder à marca de uma organização.
* Atualizando o nome do aplicativo da *Contoso* para *o Agente Contoso*, que é o nome que os usuários da organização verão. (Observação: os usuários adicionando um conector a um chat ou canal ainda verão o nome original do aplicativo, *Contoso*.)

Você pode habilitar esse recurso no Portal do [Desenvolvedor para Teams](https://dev.teams.microsoft.com/home). Isso configura , que não estão disponíveis em versões anteriores `configurableProperties` a 1,10 do manifesto Teams aplicativo.

## <a name="test-your-app"></a>Testar seu aplicativo

Não é possível testar esse recurso durante o desenvolvimento. A personalização do aplicativo não é suportada para sideload ou publicação no catálogo de aplicativos de uma organização.

## <a name="user-considerations"></a>Considerações do usuário

Como o editor de aplicativos, forneça as seguintes informações aos clientes em Teams administradores:
* Inclua uma observação recomendando testar alterações de personalização em um Teams de teste antes de fazer alterações em seu ambiente de produção. 
* Forneça práticas recomendadas para personalizar seu aplicativo.

## <a name="see-also"></a>Confira também

* [Personalizar aplicativos no Teams de administração](/MicrosoftTeams/customize-apps)
