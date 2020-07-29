---
title: Solicitar permissões de dispositivo para a guia do Microsoft Teams
description: Como atualizar seu manifesto de aplicativo para solicitar acesso a recursos nativos que geralmente exigem o consentimento do usuário
keywords: desenvolvimento de guias do teams
ms.openlocfilehash: e69c7540730307e62035c48ac64cd977419ea5f2
ms.sourcegitcommit: 1b909fb9ccf6cdd84ed0d8f9ea0463243a802a23
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/28/2020
ms.locfileid: "45434549"
---
# <a name="request-device-permissions-for-your-microsoft-teams-tab"></a>Solicitar permissões de dispositivo para a guia do Microsoft Teams

Você pode querer enriquecer sua guia com recursos que exigem o acesso de funcionalidade de dispositivo nativo, como:

> [!div class="checklist"]
>
> * Câmara
> * Microfone
> * Local
> * Notificações

> [!IMPORTANT]
>
> * Atualmente, o cliente do teams Mobile só oferece suporte `camera` `location` a recursos de dispositivos nativos e está disponível em todas as construções de aplicativos, incluindo guias. </br>
> * O suporte para `camera` captura de imagem está habilitado pela [**API captureImage**](/javascript/api/@microsoft/teams-js/microsoftteams?view=msteams-client-js-latest#captureimage--error--sdkerror--files--file-------void-).
> * Atualmente, a [**API de localização geográfica**](../../resources/schema/manifest-schema.md#devicepermissions) não tem suporte total em todos os clientes de desktop.

## <a name="device-permissions"></a>Permissões de dispositivos

O acesso às permissões de dispositivo de um usuário permite que você construa experiências muito mais ricas, por exemplo:

* Gravar e compartilhar vídeos curtos
* Gravar memorandos de áudio curtos e salvá-los para mais tarde
* Usar informações de local de usuário para exibir informações relevantes

Embora o acesso a esses recursos seja padrão nos navegadores da Web mais modernos, você precisa permitir que as equipes saibam quais recursos você gostaria de usar atualizando o manifesto do aplicativo. Isso permitirá que você solicite permissões, da mesma forma que faria em um navegador, enquanto seu aplicativo está sendo executado no cliente de área de trabalho do Microsoft Teams.

## <a name="manage-permissions"></a>Gerenciar permissões

# <a name="desktop"></a>[Desktop](#tab/desktop)

1. Abra o Microsoft Teams.
1. No canto superior direito da janela, selecione o ícone do seu perfil.
1. Selecione **Settings**  ->  **permissões** de configurações no menu suspenso.
1. Escolha as configurações desejadas.

![Tela de configurações da área de trabalho de permissões de dispositivo](../../assets/images/tabs/device-permissions.png)

# <a name="mobile"></a>[Mobile](#tab/mobile)

1. Abra o Microsoft Teams.
1. No canto superior esquerdo da tela, selecione o ícone de menu &#9776;.
1. Selecione **configurações**de  ->  **dispositivos**.
1. Escolha as configurações desejadas.

![Tela de configurações móveis de permissões de dispositivo](../../assets/images/tabs/mobile-device-permissions-screen.png)

---

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
> [!Note]
>
> A mídia também é usada para permissões de câmera no celular.

Cada propriedade permitirá que o usuário solicite o consentimento dele

| Propriedade      | Descrição   |
| --- | --- |
| mídia         | permissão para usar câmera, microfone e alto-falantes |
| localização geográfica   | permissão para retornar o local do usuário      |
| por | permissão para enviar as notificações de usuário      |
| Midi          | permissão para enviar e receber informações de Midi de um instrumento musical digital   |
| openExternal  | permissão para abrir links em aplicativos externos  |

## <a name="checking-permissions-from-your-tab"></a>Verificando permissões na sua guia

Depois de adicionar o `devicePermissions` manifesto do aplicativo, você poderá verificar as permissões usando a API "permissões" do HTML5 sem causar um aviso.

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

Para mostrar um prompt para obter consentimento para acessar permissões de dispositivo, você precisa aproveitar a API do HTML5 ou do teams apropriada. Por exemplo, para solicitar que o usuário acesse a câmera que você precisa chamar`getCurrentPosition`

```Javascript
navigator.geolocation.getCurrentPosition(function (position) { /*... */ });
```

Para usar a câmera na área de trabalho ou na Web, o Microsoft Teams mostrará um prompt de permissão ao chamar getUserMedia

```Javascript
navigator.mediaDevices.getUserMedia({ audio: true, video: true });
```

Para capturar imagem em dispositivos móveis, o Microsoft Teams solicitará permissão ao chamar captureImage ()

```Typescript
function captureImage(callback: (error: SdkError, files: File[]) => void)
```

As notificações solicitarão o usuário quando você ligar`requestPermission`

```Javascript
Notification.requestPermission(function(result) { /* ... */ });
```

![Prompt de permissões de dispositivo de guias](~/assets/images/tabs/device-permissions-prompt.png)

## <a name="permission-behavior-across-login-sessions"></a>Comportamento de permissão nas sessões de logon

As permissões de dispositivo nativo são armazenadas por sessão de logon. Isso significa que, se você fizer logon em outra instância do Microsoft Teams (por exemplo, em outro computador), suas permissões de dispositivo de suas sessões anteriores não estarão disponíveis. Em vez disso, você precisará consentir novamente as permissões de dispositivo para a nova sessão de logon. Isso também significa que, se você fizer logout de equipes (ou mudar locatários dentro do Teams), suas permissões de dispositivo serão excluídas para essa sessão de logon anterior. Tenha isso em mente ao desenvolver permissões de dispositivo nativo: os recursos nativos que você concorda para são apenas para sua sessão de login _atual_ .
