---
title: Gerenciar permissões de aplicativo do Teams
author: surbhigupta
description: Neste módulo, saiba como os aplicativos do Teams são gerenciados em locais diferentes com base no recurso.
ms.topic: reference
ms.localizationpriority: medium
ms.author: lomeybur
ms.openlocfilehash: 2bc501444e52f31061312c325ddf7dd80370240a
ms.sourcegitcommit: 84747a9e3c561c2ca046eda0b52ada18da04521d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2022
ms.locfileid: "68791837"
---
# <a name="permissions-in-teams-app"></a>Permissões no aplicativo Teams

A permissão para o aplicativo Teams é gerenciada em dois locais, dependendo do recurso do aplicativo:

* [RSC (consentimento específico do recurso)](#resource-specific-consent)
* [Active Directory do Azure (Azure AD)](#azure-active-directory)

:::image type="content" source="../../assets/images/teams-app-permissions.png" alt-text="A captura de tela descreve as diferentes permissões de aplicativo do Teams.":::

## <a name="resource-specific-consent"></a>Consentimento específico do recurso

O RSC é uma integração do Microsoft Teams e microsoft API do Graph que permite que seu aplicativo use pontos de extremidade de API para gerenciar recursos específicos, equipes ou chats, dentro de uma organização. Para obter mais informações, confira [habilitar o consentimento específico do recurso no Teams](../rsc/resource-specific-consent.md).

As permissões RSC só estão disponíveis para aplicativos do Teams instalados no cliente do Teams e atualmente não fazem parte do portal Azure AD e são declaradas no arquivo JSON (manifesto do aplicativo Teams).

## <a name="azure-active-directory"></a>Azure Active Directory

Azure AD é um serviço de gerenciamento de acesso e identidade baseado em nuvem. Esse serviço ajuda seus funcionários a acessar recursos externos, como o Microsoft 365, o portal do Azure e milhares de outros aplicativos SaaS. Para obter mais informações, consulte [Azure Active Directory](/azure/active-directory/fundamentals/active-directory-whatis).

### <a name="microsoft-graph-api-permission"></a>Permissão do Microsoft API do Graph

API do Graph permissões são gerenciadas em Azure AD. Para que o aplicativo acesse os dados no Microsoft Graph, o usuário ou administrador deve conceder a ele as permissões corretas por meio de um processo de consentimento. Para obter mais informações, veja [Permissões do Microsoft Graph](/graph/permissions-reference).

## <a name="capability-wise-management"></a>Gerenciamento sábio de funcionalidade

### <a name="bot-and-messaging-extension"></a>Extensão de bot e mensagens

A ID de extensão de bot ou de mensagens é gerada com base na plataforma de registro a seguir. Essa ID é necessária para adicionar um bot ou uma extensão de mensagens a um aplicativo do Teams.

* portal Azure AD
* Portal do Desenvolvedor ou do Bot Framework

#### <a name="azure-ad-portal"></a>portal Azure AD

Quando um bot ou uma extensão de mensagens for registrado no portal Azure AD, ele terá uma ID do aplicativo Azure AD associada a ele, que pode ser encontrada no portal **Azure AD** > **Registros de Aplicativo**. Pontos de extremidade e outras configurações de bot são gerenciados no portal do Azure.

#### <a name="developer-or-bot-framework-portal"></a>Portal do Desenvolvedor ou do Bot Framework

Quando um bot ou uma extensão de mensagens é registrado no portal do Desenvolvedor ou do Bot Framework, ele não terá uma ID do aplicativo Azure AD. No entanto, a ID do bot ou da extensão de mensagens pode ser encontrada no portal do Bot Framework. Os pontos de extremidade e outras configurações de bot são gerenciados no portal do Bot Framework.

Outra configuração específica do Teams para o bot pode ser gerenciada na seção Portal do Desenvolvedor para o aplicativo.

### <a name="connectors"></a>Conectores

Os conectores têm uma ID do conector e são registrados e gerenciados por meio do Painel do Desenvolvedor do Conector. Essa ID é necessária para introduzir um conector no Aplicativo do Teams. Outra configuração específica do Teams para conectores pode ser gerenciada na seção portal do desenvolvedor para o aplicativo.
