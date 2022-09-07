---
title: Visão geral do Kit de ferramentas do Microsoft Teams
author: zyxiaoyuer
description: Neste módulo, aprenda o Kit de Ferramentas do Teams, a Instalação do Kit de Ferramentas do Teams e o percurso do usuário do Kit de Ferramentas do Teams
ms.author: zhany
ms.localizationpriority: medium
ms.topic: overview
ms.date: 05/24/2022
ms.openlocfilehash: b614c73a9d15b058dcd01bb26b15bf35bd3030ce
ms.sourcegitcommit: ed7488415f814d0f60faa15ee8ec3d64ee336380
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2022
ms.locfileid: "67616882"
---
# <a name="teams-toolkit-overview"></a>Visão geral do Kit de ferramentas do Microsoft Teams

O Kit de Ferramentas do Teams permite que você crie, depure e implante seu aplicativo Teams diretamente Visual Studio Code. O desenvolvimento de aplicativos com o kit de ferramentas tem as seguintes vantagens:

* Identidade integrada
* Acesso ao armazenamento em nuvem
* Dados do Microsoft Graph
* Serviços do Azure e do Microsoft 365 com abordagem de configuração zero.

Para o desenvolvimento de aplicativos do Teams, semelhante ao Kit de Ferramentas do Teams para o Visual Studio, você pode usar a [Ferramenta CLI](https://github.com/OfficeDev/TeamsFx/blob/dev/docs/cli/user-manual.md), que consiste no Kit de ferramentas `teamsfx`.

## <a name="user-journey-of-teams-toolkit"></a>Percurso do usuário do Kit de ferramentas do Teams

O Kit de ferramentas do Teams automatiza o trabalho manual e fornece uma ótima integração do Teams com os recursos do Azure. A imagem a seguir mostra o percurso do usuário do Kit de ferramentas do Teams:

:::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/teams-toolkit-user-journey2.png" alt-text="Percurso do usuário do Kit de Ferramentas do Teams" lightbox="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/teams-toolkit-user-journey2.png":::

Os principais marcos desta jornada são:

1. Comece criando um novo projeto ou experimentando um aplicativo Teams de exemplo.
1. Adicione recursos ou edite o arquivo de manifesto conforme necessário.
1. Use a Microsoft 365 para compilar e depurar seu aplicativo Teams.
1. Use a conta do Azure para provisionar e implantar seu aplicativo na nuvem.
1. Publique seu aplicativo no Teams.

A tabela a seguir ajuda você a obter a visão geral do Kit de Ferramentas do Teams Visual Studio Code:

| Processo | Descrição |
| ---- | ---- |
| Instalar o Kit de Ferramentas do Teams | Você pode instalar o Kit de Ferramentas do Teams de duas maneiras: <br> - Usando Visual Studio Code <br> - Usando o Visual Studio Code Marketplace|
| Suporte para ambientes de build | Você tem dois tipos diferentes de ambiente: <br> – Javascript ou Typescript <br> - SPFx |
| Suporte para tipos de aplicativo e função do Azure | Há dois tipos diferentes de aplicativos: <br> – Aplicativo baseado em funcionalidade, como tab, bot, extensão de mensagem  <br> – Aplicativo teams baseado em cenário, como bot de notificação, bot de comando e guia pessoal habilitada para SSO |
| Desenvolver seu aplicativo Teams | Ele contém: <br> – Adicionar e gerenciar o ambiente <br> – Criar um aplicativo de várias funcionalidades <br> – Criar recursos de nuvem baseados em funcionalidade <br> – Integrar API de terceiros <br> – Personalizar o arquivo de manifesto <br> - SDK do TeamsFx |
| Depurar seu aplicativo Teams | Ele contém: <br> – Depurar seu aplicativo teams localmente <br> – Depurar processo em segundo plano|
| Hospedar seu aplicativo Teams | Ele contém: <br> – Provisionar recursos para a nuvem <br> – Implantar na nuvem|
| Testar seu aplicativo Teams | Ele contém: <br> – Integrar e collabrate <br> – Pacote de metadados do Zip Teams <br> - Fazer sideload e testar o aplicativo no ambiente do Teams <br> – Testar o comportamento do aplicativo em um ambiente diferente|
| Publicar seu aplicativo Teams | Ele contém: <br> - Publicar seu aplicativo <br> – Gerenciar a aprovação do administrador <br> - Publicar no repositório <br> – Integrar com o Portal do Desenvolvedor |

### <a name="entities-integrated-with-teams-toolkit"></a>Entidades integradas ao Kit de Ferramentas do Teams

O Kit de Ferramentas do Teams é uma extensão Visual Studio Code. Ele é integrado às seguintes entidades no Kit de Ferramentas do Teams, como o Azure AD e o Microsoft 365, o Portal do Desenvolvedor e o Microsoft Graph. Todas as entidades são integradas ao Kit de Ferramentas do Teams e ajudam os usuários a criar um aplicativo.

| Entidades | Descrição |
| ---- | ---- |
| Microsoft Azure AD  | O Azure Active Directory (Azure AD) é um serviço de gerenciamento de acesso e identidade baseado em nuvem. Esse serviço ajuda seus funcionários a acessar recursos externos, como o Microsoft 365, o portal do Azure e milhares de outros aplicativos SaaS. |
| Microsoft 365  | Conta de desenvolvedor do Teams ao desenvolver um aplicativo.|
| Portal do Desenvolvedor | O Portal do Desenvolvedor para Teams é a principal ferramenta para configurar, distribuir e gerenciar seus aplicativos do Microsoft Teams. Com o Portal do Desenvolvedor, você pode colaborar com colegas em seu aplicativo, configurar ambientes de runtime e muito mais. |
| Microsoft Graph | O Microsoft Graph é o gateway para dados e inteligência no Microsoft 365. Ele fornece um modelo de programação unificado que você pode usar para acessar a enorme quantidade de dados no Microsoft 365, Windows e Enterprise Mobility + Security. |

O Kit de ferramentas do Teams traz todas as ferramentas necessárias para criar um aplicativo do Teams em um só lugar.

## <a name="manage-your-apps-using-developer-portal"></a>Gerenciar seus aplicativos usando o Portal do Desenvolvedor

Como o Kit de Ferramentas do Teams é integrado ao Portal do Desenvolvedor, você pode configurar, distribuir e gerenciar seu aplicativo usando o Portal do Desenvolvedor para [Teams](../concepts/build-and-test/teams-developer-portal.md) em DEPLOYMENT depois de criar um aplicativo. Para obter mais informações, consulte [gerenciar seus aplicativos do Teams usando o Portal do Desenvolvedor](../concepts/build-and-test/manage-your-apps-in-developer-portal.md).

:::image type="content" source="../assets/images/teams-toolkit-v2/build-environment-developer-portal-1.png" alt-text="Portal do Desenvolvedor":::

## <a name="see-also"></a>Confira também

* [Criar um novo projeto do Teams](create-new-project.md)
* [Instalar o Kit de Ferramentas do Teams](install-Teams-Toolkit.md)
* [Explorar o Kit de Ferramentas do Teams](explore-Teams-Toolkit.md)
* [Preparar-se para criar aplicativos usando o Kit de Ferramentas do Microsoft Teams](build-environments.md)
