---
title: Permissões de dispositivo para o navegador
keywords: Permissões de recursos de aplicativos do teams
description: Trazer de volta com segurança o suporte a permissões de dispositivo para aplicativos em nosso cliente Web
localization_priority: Normal
ms.topic: how-to
ms.openlocfilehash: b2e83ca784e5459edfd80a3862610ebab2f8df30
ms.sourcegitcommit: ce956267b620f807e15e6d2df7afa022ffacc22f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2021
ms.locfileid: "60496222"
---
# <a name="device-permissions-for-the-browser"></a>Permissões de dispositivo para o navegador

> [!NOTE]
> A alteração de como as permissões de dispositivo são manipuladas no navegador está disponível apenas na visualização de [desenvolvedor](../../resources/dev-preview/developer-preview-intro.md) público. Essa alteração estará geralmente disponível (GA) até 21 de janeiro de 2022.

Os aplicativos que exigem permissões de dispositivo - como acesso a câmera ou microfone - agora exigem que os usuários concedam o consentimento manualmente em um nível de aplicativo no navegador da Web. Anteriormente, o navegador manipulava como essas permissões eram concedidas, mas agora essas permissões serão tratadas em Microsoft Teams. Isso tem implicações sobre como você projeta seu aplicativo se eles exigirem essas permissões no navegador.

## <a name="change-in-behavior"></a>Mudança no comportamento
Se seu aplicativo tiver declarado que precisa de permissões de dispositivo no manifesto do [aplicativo,](native-device-permissions.md)os usuários receberão uma opção de "permissões de aplicativo", onde poderão habilitar as permissões de dispositivo de um aplicativo. A opção "permissões de aplicativo" pode ser encontrada em aplicativos pessoais, caixas de diálogo do módulo de tarefas e guias em chats, canais ou reuniões.

### <a name="personal-apps-and-task-module-dialogs"></a>Caixas de diálogo de aplicativos pessoais e módulos de tarefas
A configuração "permissões de aplicativo" pode ser encontrada na parte superior direita.
<img src="../../assets/images/tabs/apppermissions.png" alt="App permissions button" width="800"/>

### <a name="chat-channel-or-meeting-tabs"></a>Guias de chat, canal ou reunião
A configuração "permissões de aplicativo" pode ser encontrada no menu suspenso de tabulação.
![Drop-down de permissões do aplicativo](../../assets/images/tabs/drop-downapppermissions.png)

Um usuário precisará habilitar essas permissões no navegador para que essas permissões entre em vigor. Depois que um usuário altera as permissões de dispositivo de um aplicativo no navegador, ele será solicitado a recarregar o aplicativo Teams. É importante que você faça os usuários saberem para onde ir para habilitar essas permissões Microsoft Teams.

## <a name="recommendation"></a>Recomendação
Microsoft Teams aplicativos que exigem permissões de dispositivo no navegador devem mostrar instruções aos usuários sobre onde encontrar e habilitar essas permissões na interface do usuário Teams. Dependendo do contexto em que seu aplicativo está sendo executado, você precisará garantir que suas instruções estão apontando para o usuário para o local correto para acessar essas permissões, pois elas diferem para aplicativos pessoais, caixas de diálogo do módulo de tarefas e guias em chats, canais ou reuniões.

<img src="../../assets/images/tabs/enable-access.png" alt="Enable camera access" width="800"/>

## <a name="see-also"></a>Confira também

* [Visão geral dos recursos do dispositivo](device-capabilities-overview.md)
* [Solicitar permissões do dispositivo](native-device-permissions.md)
