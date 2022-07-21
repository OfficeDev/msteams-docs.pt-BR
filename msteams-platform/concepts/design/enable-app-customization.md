---
title: Personalizar seu aplicativo Teams
author: heath-hamilton
description: Neste módulo, entenda como os administradores do Teams podem personalizar seu aplicativo teams para sua organização e ocultar o aplicativo Teams até que o administrador aprove.
ms.localizationpriority: medium
ms.author: surbhigupta
ms.topic: overview
ms.openlocfilehash: 0a7a98c5d981f35bc60a6099873a445b45caa071
ms.sourcegitcommit: 4ba6392eced76ba6baeb6d6dd9ba426ebf4ab24f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/21/2022
ms.locfileid: "66919820"
---
# <a name="customize-your-teams-app"></a>Personalizar seu aplicativo Teams

## <a name="enable-your-microsoft-teams-app-to-be-customized"></a>Permitir que seu aplicativo Microsoft Teams seja personalizado

Você pode permitir que os clientes personalizem alguns aspectos do aplicativo Microsoft Teams no centro de administração do Teams. Esse recurso tem suporte apenas para aplicativos publicados na loja do Teams. Aplicativos e aplicativos com sideload publicados para uma organização não podem ser personalizados.

Alguns exemplos possíveis desse recurso incluem:

* Alterar a cor de destaque do aplicativo para corresponder à marca de uma organização.
* Atualizando o nome do aplicativo de *Contoso* para *Contoso Agent*, que é o nome que os usuários da organização verão. (Observação: os usuários que adicionarem um conector a um chat ou canal ainda verão o nome original do aplicativo, *Contoso*.)

Você pode habilitar [`configurableProperties`](/microsoftteams/platform/resources/schema/manifest-schema#configurableproperties)esse recurso definindo as propriedades do aplicativo que seus clientes podem personalizar na seção no manifesto do aplicativo Teams, começando com a versão 1.11. Isso pode ser feito no Portal do Desenvolvedor para [Teams](https://dev.teams.microsoft.com/home) se você optou por usar o Portal do Desenvolvedor para editar o manifesto do seu aplicativo.

### <a name="test-your-app"></a>Testar seu aplicativo

Você não pode testar esse recurso durante o desenvolvimento. Não há suporte para personalização de aplicativos durante o sideload ou publicação no catálogo de aplicativos de uma organização.

### <a name="user-considerations"></a>Considerações do usuário

Forneça diretrizes para clientes (especificamente administradores do Teams) que desejam personalizar seu aplicativo. Para obter mais informações, [personalizar aplicativos no Teams](/MicrosoftTeams/customize-apps).

## <a name="hide-teams-app-until-admin-approves"></a>Ocultar o aplicativo Teams até que o administrador aprove

Para aprimorar a experiência do aplicativo Teams, você pode ocultar um aplicativo dos usuários por padrão até que o administrador permita reexibir o aplicativo. Por exemplo, a Contoso Electronics criou um aplicativo de suporte técnico para o Teams. Para habilitar o funcionamento apropriado do aplicativo, a Contoso Electronics' quer que os clientes primeiro configurem propriedades específicas do aplicativo. O aplicativo fica oculto por padrão e está disponível para os usuários somente depois que o administrador permitir.

> [!NOTE]
> A loja do Teams evoluiu:
> 
> Anteriormente, os aplicativos LOB eram atualizados selecionando as reticências no bloco. Com a experiência atualizada da loja do Teams, agora você pode atualizar os aplicativos LOB fazendo logon no [Centro de Administrador do Teams](https://admin.teams.microsoft.com).

Para ocultar o aplicativo, no arquivo de manifesto do aplicativo, defina a propriedade `defaultBlockUntilAdminAction` como `true`. Quando a propriedade é definida como `true`, no Centro de administração do Teams > **Gerenciar aplicativos**, **Bloqueado pelo publicador** aparece no **Estado**:

:::image type="content" source="../../assets/images/apps-in-meetings/manageappsblockedapps.png" alt-text="Gerenciar aplicativos bloqueados pelo editor.":::

O administrador obtém uma solicitação para executar uma ação antes que um usuário possa acessar o aplicativo. Em **Gerenciar aplicativos**, os administradores podem selecionar **Permitir** para permitir que o aplicativo com o estado **Bloqueado pelo publicador**:

![Gerenciar aplicativos](../../assets/images/apps-in-meetings/manageapp.png)

Se, por padrão, você não quiser que o aplicativo seja ocultado, poderá atualizar a propriedade `defaultBlockUntilAdminAction` para `false`. Quando a nova versão do aplicativo for aprovada, por padrão, o aplicativo será permitido, desde que o administrador não tenha feito nenhuma ação explícita.

> [!NOTE]
> `defaultBlockUntilAdminAction` não tem suporte para aplicativos LOB. Se você carregar um aplicativo LOB com essa propriedade, o aplicativo não será bloqueado.

## <a name="see-also"></a>Confira também

* [Esquema de manifesto do aplicativo](/microsoftteams/platform/resources/schema/manifest-schema)
* [Personalizar aplicativos no centro de administração do Teams](/MicrosoftTeams/customize-apps)
