---
title: Permissões do dispositivo para o navegador
keywords: Permissões de recursos de aplicativos do teams
description: Trazer de volta com segurança o suporte a permissões de dispositivo para aplicativos em nosso cliente Web
localization_priority: medium
ms.topic: how-to
ms.openlocfilehash: 02a3602f17923506cba6aa6e83548595aac60852
ms.sourcegitcommit: 3dc9b539c6f7fbfb844c47a78e3b4d2200dabdad
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/31/2022
ms.locfileid: "64571471"
---
# <a name="device-permissions-for-the-browser"></a>Permissões do dispositivo para o navegador

Teams aplicativo que exigem permissões de dispositivo, como acesso a câmera ou microfone, agora exigem que os usuários concedam permissão manualmente em um nível de aplicativo no navegador da Web. Anteriormente, o navegador manipulava como conceder permissões de acesso, mas agora essas permissões são tratadas em Microsoft Teams. Isso tem implicações sobre como você projeta seu aplicativo e se eles exigem essas permissões no navegador.

## <a name="enable-apps-device-permissions"></a>Habilitar permissões de dispositivo do aplicativo

Se seu Teams app tiver declarado no manifesto do aplicativo que [](native-device-permissions.md#specify-permissions) ele precisa de permissões de dispositivo, a opção Permissões do  aplicativo será exibida para os usuários habilitarem as permissões de dispositivo do aplicativo. A **opção Permissões do** aplicativo está disponível nos seguintes recursos:

* **Caixas de diálogo aplicativos pessoais e módulos** de tarefa: a opção **Permissões do** aplicativo está disponível no canto superior direito da página.
<img src="../../assets/images/tabs/apppermissions.png" alt="App permissions button" width="800"/>

* **Chats, canais ou guias de reunião**: a opção **Permissões do** aplicativo está disponível no menu suspenso da guia. ![ Drop-down de permissões do aplicativo](../../assets/images/tabs/drop-downapppermissions.png)

Depois que **a opção Permissões do** aplicativo é selecionada, um pop-up aparece onde o usuário pode habilitar o botão permissões.

Um usuário precisará habilitar essas permissões no navegador para que essas permissões entre em vigor. Depois que o usuário altera as permissões de dispositivo do aplicativo no navegador, ele é solicitado a recarregar o aplicativo Teams.

> [!IMPORTANT]
> Você deve tornar os usuários cientes de onde ir para habilitar essas **permissões de** aplicativo em Microsoft Teams.

## <a name="recommendation"></a>Recomendação

Teams aplicativo que exigem permissões de dispositivo no navegador deve mostrar instruções aos usuários sobre onde encontrar e habilitar essas permissões na interface do usuário Teams. Dependendo do contexto em que seu aplicativo está sendo executado, você precisa garantir que suas instruções estão apontando para o usuário a localização correta para acessar essas permissões, pois elas diferem para aplicativos pessoais, caixas de diálogo do módulo de tarefas, guias em chats e canais ou reuniões.

</br>
<img src="../../assets/images/tabs/enable-access.png" alt="Enable camera access" width="800"/>

## <a name="code-sample"></a>Exemplo de código

|Nome do exemplo | Descrição | Node.js |
|----------------|-----------------|--------------|
| Permissões de dispositivo tab para navegador | O código de exemplo demonstra como mostrar as permissões do dispositivo para o navegador. | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/tab-device-permissions/nodejs) |

## <a name="step-by-step-guide"></a>Guias passo a passo

Siga o [guia passo a passo para](../../sbs-tab-device-permissions.yml) conceder permissão de dispositivo de guia Microsoft Teams.

## <a name="see-also"></a>Confira também

* [Visão geral dos recursos do dispositivo](device-capabilities-overview.md)
* [Solicitar permissões do dispositivo](native-device-permissions.md)
