---
title: Solicitar permissões de dispositivo para a guia do Microsoft Teams
description: Como atualizar seu manifesto de aplicativo para solicitar acesso a recursos nativos que geralmente exigem o consentimento do usuário
keywords: desenvolvimento de guias do teams
ms.openlocfilehash: f0e19c0ed716147c097137c4ef0bf3454783b2eb
ms.sourcegitcommit: c4a7bc638e848a702cce92798cba84917fcecc35
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/24/2020
ms.locfileid: "42928514"
---
# <a name="request-device-permissions-for-your-microsoft-teams-tab"></a>Solicitar permissões de dispositivo para a guia do Microsoft Teams

Você pode querer enriquecer sua guia com recursos que exigem o acesso de funcionalidade de dispositivo nativo, como:

* Câmara
* Microfone
* Local
* Notificações

![Tela de configurações de permissões de dispositivo](~/assets/images/tabs/device-permissions.png)

> [!IMPORTANT]
> Atualmente, a funcionalidade de dispositivo nativo não é suportada para guias em clientes móveis, mas o suporte completo estará disponível em breve. Para se preparar para essa alteração, você deve seguir as [orientações para guias em celular](~/tabs/design/tabs-mobile.md) ao criar suas guias. Os aplicativos pessoais (guias estáticas) estão disponíveis atualmente na [visualização do desenvolvedor](~/resources/dev-preview/developer-preview-intro.md).
>
> Quando o suporte completo para guias é liberado:
>
> * Todas as guias sempre estarão disponíveis em dispositivos móveis
> * O `contentUrl` **será carregado no cliente do Mobile Teams**.
> * Para guias de canal/grupo, os usuários ainda podem abrir sua guia em um navegador separado `websiteUrl`por meio de `contentUrl` seu, no entanto, seu primeiro será carregado.  

## <a name="device-permissions"></a>Permissões de dispositivos

O acesso às permissões de dispositivo de um usuário permite que você construa experiências muito mais ricas, por exemplo:

* Gravar e compartilhar vídeos curtos
* Gravar memorandos de áudio curtos e salvá-los para mais tarde
* Usar informações de local de usuário para exibir informações relevantes

Embora o acesso a esses recursos seja padrão nos navegadores da Web mais modernos, você precisa permitir que as equipes saibam quais recursos você gostaria de usar atualizando o manifesto do aplicativo. Isso permitirá que você solicite permissões, da mesma forma que faria em um navegador, enquanto seu aplicativo está sendo executado no cliente de área de trabalho do Microsoft Teams.

## <a name="properties"></a>Propriedades

Atualize o seu aplicativo `manifest.json` adicionando `devicePermissions` e especificando quais das cinco Propriedades você gostaria de usar em seu aplicativo:

``` json
"devicePermissions": [
    "media",
    "geolocation",
    "notifications",
    "midi",
    "openExternal"
],
```

Cada propriedade permitirá que o usuário solicite o consentimento dele

| Propriedade      | Descrição   |
| --- | --- |
| corre         | permissão para usar câmera, microfone e alto-falantes |
| localização geográfica   | permissão para retornar o local do usuário      |
| por | permissão para enviar as notificações de usuário      |
| Midi          | permissão para enviar e receber informações de Midi de um instrumento musical digital   |
| openExternal  | permissão para abrir links em aplicativos externos  |

## <a name="checking-permissions-from-your-tab"></a>Verificando permissões na sua guia

Depois de adicionar `devicePermissions` o manifesto do aplicativo, você poderá verificar as permissões usando a API "permissões" do HTML5 sem causar um aviso.

``` Javascript
// Different query options:
navigator.permissions.query({ name: 'camera' });
navigator.permissions.query({ name: 'microphone' });
navigator.permissions.query({ name: 'geolocation' });
navigator.permissions.query({ name: 'notifications' });
navigator.permissions.query({ name: 'midi', sysex: true });

// Example:
navigator.permissions.query({name:'geolocation'}).then(function(result) {
  if (result.state == 'granted') {
    // Access granted
  } else if (result.state == 'prompt') {
    // Access has not been granted
  }
});
```

## <a name="prompting-the-user"></a>Avisar o usuário

Para mostrar um prompt para obter consentimento para acessar permissões de dispositivo, você precisará aproveitar a API HTML5 apropriada. Por exemplo, para solicitar que o usuário acesse a câmera que você precisa chamar`getUserMedia`

```Javascript
navigator.mediaDevices.getUserMedia({ audio: true, video: true });
```

A localização geográfica mostrará um prompt de permissão ao chamar`getCurrentPosition`

```Javascript
navigator.geolocation.getCurrentPosition(function (position) { /*... */ });
```

As notificações solicitarão o usuário quando você ligar`requestPermission`

```Javascript
Notification.requestPermission(function(result) { /* ... */ });
```

![Prompt de permissões de dispositivo de guias](~/assets/images/tabs/device-permissions-prompt.png)

## <a name="permission-behavior-across-login-sessions"></a>Comportamento de permissão nas sessões de logon

As permissões de dispositivo nativo são armazenadas por sessão de logon. Isso significa que, se você fizer logon em outra instância do Microsoft Teams (por exemplo, em outro computador), suas permissões de dispositivo de suas sessões anteriores não estarão disponíveis. Em vez disso, você precisará consentir novamente as permissões de dispositivo para a nova sessoin de logon. Isso também significa que, se você fizer logout de equipes (ou mudar locatários dentro do Teams), suas permissões de dispositivo serão excluídas para essa sessão de logon anterior. Tenha isso em mente ao desenvolver permissões de dispositivo nativo: os recursos nativos que você concorda para são apenas para seu sessoin de logon _atual_ .