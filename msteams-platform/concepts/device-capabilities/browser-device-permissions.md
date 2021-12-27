---
title: Permissões do dispositivo para o navegador
keywords: Permissões de recursos de aplicativos do teams
description: Trazer de volta com segurança o suporte a permissões de dispositivo para aplicativos em nosso cliente Web
localization_priority: Normal
ms.topic: how-to
ms.openlocfilehash: a7517a5d393495ae64a43f08f7201f45a994c770
ms.sourcegitcommit: 4892d8d0fa38a472edab047754ef85b1a85be495
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/27/2021
ms.locfileid: "61608381"
---
# <a name="device-permissions-for-the-browser"></a>Permissões do dispositivo para o navegador

> [!NOTE]
> A atualização mais recente sobre como as permissões de dispositivo são manipuladas no navegador está disponível apenas na visualização do [desenvolvedor](../../resources/dev-preview/developer-preview-intro.md) público. Essa atualização estará geralmente disponível (GA) até 01 de fevereiro de 2022.


Teams aplicativo que exigem permissões de dispositivo, como acesso a câmera ou microfone, agora exigem que os usuários concedam permissão manualmente em um nível de aplicativo no navegador da Web. Anteriormente, o navegador manipulava como conceder permissões de acesso, mas agora essas permissões são tratadas em Microsoft Teams. Isso tem implicações sobre como você projeta seu aplicativo e se eles exigem essas permissões no navegador.

## <a name="enable-apps-device-permissions"></a>Habilitar permissões de dispositivo do aplicativo
Se o aplicativo Teams tiver declarado [](native-device-permissions.md#specify-permissions) no manifesto do aplicativo que ele  precisa de permissões de dispositivo, a opção Permissões do aplicativo será exibida para os usuários habilitarem as permissões de dispositivo do aplicativo. A **opção Permissões do** aplicativo está disponível nos seguintes recursos: 

* **Caixas de diálogo aplicativos** pessoais e módulos de tarefa : A opção **Permissões do** aplicativo está disponível no canto superior direito da página.
<img src="../../assets/images/tabs/apppermissions.png" alt="App permissions button" width="800"/>

* **Chats, canais ou guias de reunião:** a opção **Permissões do** aplicativo está disponível no menu suspenso da guia. ![ Drop-down de permissões do aplicativo](../../assets/images/tabs/drop-downapppermissions.png)

Depois que **a opção Permissões do** aplicativo é selecionada, um pop-up aparece onde o usuário pode habilitar o botão permissões.

Um usuário precisará habilitar essas permissões no navegador para que essas permissões entre em vigor. Depois que o usuário altera as permissões de dispositivo do aplicativo no navegador, ele é solicitado a recarregar o aplicativo Teams.

> [!IMPORTANT]
> Você deve tornar os usuários cientes de onde ir para habilitar essas **permissões de** aplicativo em Microsoft Teams.

## <a name="recommendation"></a>Recomendação
Teams aplicativo que exigem permissões de dispositivo no navegador deve mostrar instruções aos usuários sobre onde encontrar e habilitar essas permissões na interface do usuário Teams usuário. Dependendo do contexto em que seu aplicativo está sendo executado, você precisa garantir que suas instruções estão apontando para o usuário a localização correta para acessar essas permissões, pois elas diferem para aplicativos pessoais, caixas de diálogo do módulo de tarefas, guias em chats e canais ou reuniões.

</br>
<img src="../../assets/images/tabs/enable-access.png" alt="Enable camera access" width="800"/>

## <a name="code-sample"></a>Exemplo de código

|Nome do exemplo | Descrição | Node.js |
|----------------|-----------------|--------------|
| Permissões de dispositivo tab para navegador | O código de exemplo demonstra como mostrar as permissões do dispositivo para o navegador. | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/tab-device-permissions/nodejs) |

## <a name="step-by-step-guide"></a>Guias passo a passo

Siga o [guia passo a passo para](../../sbs-tab-device-permissions.yml) conceder permissão de dispositivo de tabulação Microsoft Teams.

## <a name="see-also"></a>Confira também

* [Visão geral dos recursos do dispositivo](device-capabilities-overview.md)
* [Solicitar permissões do dispositivo](native-device-permissions.md)
