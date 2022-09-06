---
title: Habilitar a personalização do aplicativo e bloquear aplicativos até que o administrador permita
author: heath-hamilton
description: Neste módulo, entenda como os administradores do Teams podem personalizar seu aplicativo teams para sua organização e ocultar o aplicativo Teams até que o administrador aprove.
ms.localizationpriority: medium
ms.author: surbhigupta
ms.topic: overview
ms.openlocfilehash: 7d71e341bd1613e9efe6c900f29e1bd340006b49
ms.sourcegitcommit: d92e14fad6567fe91fd52ee6c213836740316683
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2022
ms.locfileid: "67604945"
---
# <a name="enable-app-customization-and-block-apps-till-admin-allows"></a>Habilitar a personalização do aplicativo e bloquear aplicativos até que o administrador permita

O Microsoft Teams permite que os administradores personalizem o aplicativo Teams para aprimorar a experiência da loja e aderir à identidade visual da organização. Um desenvolvedor de aplicativos pode permitir que seu aplicativo seja personalizado por um administrador do Teams. Para obter mais informações, consulte [Personalizar aplicativos no centro de administração do Teams](/MicrosoftTeams/customize-apps).

## <a name="enable-customization-for-your-microsoft-teams-app"></a>Habilitar a personalização para o aplicativo Microsoft Teams

Você pode permitir que os clientes personalizem alguns aspectos do aplicativo Microsoft Teams no centro de administração do Teams. Esse recurso tem suporte apenas para aplicativos publicados na loja do Teams. Aplicativos e aplicativos com sideload publicados para uma organização não podem ser personalizados.

Alguns exemplos possíveis desse recurso incluem:

* Alterar a cor de destaque do aplicativo para corresponder à marca de uma organização.
* Atualizando o nome do aplicativo de *Contoso* para *Contoso Agent*, que é o nome que os usuários da organização verão.
(Observação: os usuários que adicionarem um conector a um chat ou canal ainda verão o nome original do aplicativo, *Contoso*.)

Você pode habilitar [`configurableProperties`](/microsoftteams/platform/resources/schema/manifest-schema#configurableproperties)esse recurso definindo as propriedades do aplicativo que seus clientes podem personalizar na seção no manifesto do aplicativo Teams, começando com a versão 1.11. Isso pode ser feito no Portal do Desenvolvedor para [Teams](https://dev.teams.microsoft.com/home) se você optou por usar o Portal do Desenvolvedor para editar o manifesto do seu aplicativo.

> [!IMPORTANT]
> Você não pode testar esse recurso durante o desenvolvimento. Não há suporte para personalização de aplicativos durante o sideload ou publicação no catálogo de aplicativos de uma organização.

### <a name="user-considerations"></a>Considerações do usuário

Forneça diretrizes para clientes (especificamente administradores do Teams) que desejam personalizar seu aplicativo. Para obter mais informações, [personalizar aplicativos no Teams](/MicrosoftTeams/customize-apps).

## <a name="block-apps-by-default-for-users-until-an-admin-approves"></a>Bloquear aplicativos por padrão para usuários até que um administrador aprove

Para aprimorar a experiência do aplicativo Teams, você pode ocultar um aplicativo dos usuários por padrão até que o administrador permita reexibir o aplicativo. Por exemplo, a Contoso Electronics criou um aplicativo de suporte técnico para o Teams. Para habilitar o funcionamento apropriado do aplicativo, a Contoso Electronics' quer que os clientes primeiro configurem propriedades específicas do aplicativo. O aplicativo fica oculto por padrão e está disponível para os usuários somente depois que o administrador permitir.

Para ocultar o aplicativo, no arquivo de manifesto do aplicativo, defina a propriedade `defaultBlockUntilAdminAction` como `true`. Quando a propriedade é definida como `true`, no Centro de administração do Teams > **Gerenciar aplicativos**, **Bloqueado pelo publicador** aparece no **Estado**:

:::image type="content" source="../../assets/images/manage-apps-status.png" alt-text="A captura de tela é um exemplo que mostra um aplicativo bloqueado pelo editor." lightbox="../../assets/images/manage-apps-status-expanded.png":::

O administrador obtém uma solicitação para executar uma ação antes que um usuário possa acessar o aplicativo. Em **Gerenciar aplicativos**, os administradores podem selecionar **Permitir** para permitir que o aplicativo com o estado **Bloqueado pelo publicador**:

:::image type="content" source="../../assets/images/manage-apps-allow.png" alt-text="A captura de tela é um exemplo que mostra a opção permitir para o aplicativo bloqueado pelo editor." lightbox="../../assets/images/manage-apps-allow-expanded.png":::

Se, por padrão, você não quiser que o aplicativo seja ocultado, poderá atualizar a propriedade `defaultBlockUntilAdminAction` para `false`. Quando a nova versão do aplicativo for aprovada, por padrão, o aplicativo será permitido, desde que o administrador não tenha feito nenhuma ação explícita.

> [!NOTE]
> Para aplicativos LOB, `defaultBlockUntilAdminAction` não há suporte. O aplicativo não será bloqueado se você carregar um aplicativo LOB com essa propriedade.

## <a name="see-also"></a>Confira também

* [Esquema de manifesto do aplicativo](/microsoftteams/platform/resources/schema/manifest-schema)
* [Personalizar aplicativos no centro de administração do Teams](/MicrosoftTeams/customize-apps)
