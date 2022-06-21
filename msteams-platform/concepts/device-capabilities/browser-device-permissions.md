---
title: Permissões do dispositivo para o navegador
description: Saiba como trazer permissões de dispositivo de volta com segurança, como acesso à câmera ou microfone para aplicativos no cliente Web.
localization_priority: medium
ms.topic: how-to
ms.openlocfilehash: 72c185257097ec739380bc2cc8390320beb24134
ms.sourcegitcommit: 7bbb7caf729a00b267ceb8af7defffc91903d945
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/21/2022
ms.locfileid: "66190171"
---
# <a name="device-permissions-for-the-browser"></a>Permissões do dispositivo para o navegador

Teams aplicativo que exige permissões de dispositivo, como acesso à câmera ou microfone, agora exige que os usuários concedam permissão manualmente em um nível de aplicativo no navegador da Web. Anteriormente, o navegador tratava de como conceder permissões de acesso, mas agora essas permissões são tratadas no Microsoft Teams. Isso tem implicações sobre como você cria seu aplicativo e se eles exigem essas permissões no navegador.

## <a name="enable-apps-device-permissions"></a>Habilitar permissões de dispositivo do aplicativo

Se o aplicativo do Teams tiver declarado no [manifesto do aplicativo](native-device-permissions.md#specify-permissions) que ele precisa de permissões de dispositivo, a opção **Permissões de aplicativo** será exibida para os usuários habilitarem as permissões de dispositivo do aplicativo. A opção **Permissões do aplicativo** está disponível nos seguintes recursos:

* **Diálogos de módulo de tarefas e aplicativos pessoais**: a opção **Permissões do aplicativo** está disponível no canto superior direito da página.
<img src="../../assets/images/tabs/apppermissions.png" alt="App permissions button" width="800"/>

* **Guias de chats, canais ou reuniões**: a opção **Permissões do aplicativo** está disponível na lista suspensa da guia. ![Menu suspenso Permissões do aplicativo](../../assets/images/tabs/drop-downapppermissions.png)

Depois que a opção **Permissões do aplicativo** for selecionada, um pop-up será exibido onde o usuário poderá habilitar o botão de permissões.

Um usuário precisará habilitar essas permissões no navegador para que essas permissões entrem em vigor. Depois que o usuário alterar as permissões do dispositivo do aplicativo no navegador, ele será solicitado a recarregar o aplicativo no Teams.

> [!IMPORTANT]
> Você deve tornar os usuários cientes de onde ir para habilitar essas **permissões de aplicativo** Teams.

## <a name="recommendation"></a>Recomendação

Teams aplicativo que exige permissões de dispositivo no navegador deve mostrar instruções aos usuários sobre onde localizar e habilitar essas permissões na interface do usuário Teams usuário. Dependendo do contexto no qual o aplicativo está em execução, você precisa garantir que suas instruções estejam apontando o usuário para o local correto para acessar essas permissões. As permissões diferem para aplicativos pessoais, caixas de diálogo do módulo de tarefas, guias em chats e canais ou reuniões.

</br>
<img src="../../assets/images/tabs/enable-access.png" alt="Enable camera access" width="800"/>

## <a name="code-sample"></a>Exemplo de código

|Nome do exemplo | Descrição | Node.js |
|----------------|-----------------|--------------|
| Permissões do dispositivo para o navegador | O código de exemplo demonstra como mostrar as permissões do dispositivo para o navegador. | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/tab-device-permissions/nodejs) |

## <a name="step-by-step-guide"></a>Guias passo a passo

Siga o [guia passo a passo para](../../sbs-tab-device-permissions.yml) conceder permissão de dispositivo guia Teams.

## <a name="see-also"></a>Confira também

* [Visão geral dos recursos de dispositivo adicionados](device-capabilities-overview.md)
* [Solicitar permissões do dispositivo](native-device-permissions.md)
