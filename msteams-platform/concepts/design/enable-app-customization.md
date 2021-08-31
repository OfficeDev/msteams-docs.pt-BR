---
title: Permitir que seu aplicativo seja personalizado
author: heath-hamilton
description: Entenda como Teams administradores podem personalizar seu aplicativo para sua organização.
localization_priority: Normal
ms.author: surbhigupta
ms.topic: overview
ms.openlocfilehash: ffc429d3dee0ab05e65951233b60ec17ae659b0e
ms.sourcegitcommit: 306b6e8cb3aac8bfda10ef3999467a797d64539d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/20/2021
ms.locfileid: "58408661"
---
# <a name="enable-your-microsoft-teams-app-to-be-customized"></a>Permitir que seu Microsoft Teams aplicativo seja personalizado

Você pode permitir que os clientes personalizem alguns aspectos do seu aplicativo Microsoft Teams no centro de Teams de administração. Esse recurso só é suportado para aplicativos publicados no Teams store. Aplicativos e aplicativos com sideload publicados para uma organização não podem ser personalizados.

Alguns exemplos possíveis desse recurso incluem:

* Alterar a cor de destaque do aplicativo para corresponder à marca de uma organização.
* Atualizando o nome do aplicativo da *Contoso* para *o Agente Contoso*, que é o nome que os usuários da organização verão. (Observação: os usuários adicionando um conector a um chat ou canal ainda verão o nome original do aplicativo, *Contoso*.)

Você pode habilitar esse recurso no Portal do [Desenvolvedor para Teams](https://dev.teams.microsoft.com/home). Isso configura , que não está disponível em versões anteriores `configurableProperties` a 1,10 do manifesto Teams aplicativo.

## <a name="test-your-app"></a>Testar seu aplicativo

Não é possível testar esse recurso durante o desenvolvimento. A personalização do aplicativo não é suportada ao fazer sideload ou publicação no catálogo de aplicativos de uma organização.

## <a name="user-considerations"></a>Considerações do usuário

Forneça diretrizes para clientes (especificamente Teams administradores) que querem personalizar seu aplicativo. Para obter mais informações, consulte [personalizar aplicativos em Teams](/MicrosoftTeams/customize-apps).

## <a name="see-also"></a>Confira também

* [Personalizar aplicativos no Teams de administração](/MicrosoftTeams/customize-apps)
