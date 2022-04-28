---
title: Manter e dar suporte ao seu aplicativo publicado
description: O que pensar depois que sua loja estiver listada na loja do Teams e no AppSource.
ms.topic: conceptual
ms.localizationpriority: high
author: heath-hamilton
ms.author: surbhigupta
ms.openlocfilehash: 2a85739a5a94109aae87de4579f17fe99df8d28b
ms.sourcegitcommit: 0117c4e750a388a37cc189bba8fc0deafc3fd230
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65104529"
---
# <a name="maintain-your-published-microsoft-teams-app"></a>Mantenha seu aplicativo Microsoft Teams publicado

Com seu aplicativo listado na loja do Microsoft Teams, comece a pensar em como você manterá o aplicativo no futuro e aumentará os downloads e o uso.

## <a name="analyze-app-usage"></a>Analisar o uso do aplicativo

Você pode acompanhar o uso do aplicativo no [Relatório de uso do Teams](/office/dev/store/teams-apps-usage) no Partner Center. As métricas incluem usuários ativos mensais, diários e semanais e gráficos de retenção e intensidade que permitem acompanhar a variação e a frequência de uso.

Os dados de aplicativos recém-publicados demoram cerca de uma semana para aparecer no relatório.

## <a name="publish-updates-to-your-app"></a>Publicar atualizações em seu aplicativo

> [!NOTE]
> A loja do Teams evoluiu:
>
> Anteriormente, os links eram copiados selecionando reticências no bloco do aplicativo. Com a experiência atualizada da loja do Teams, você acessará o mesmo na guia de detalhes dos aplicativos. Esta atualização estará disponível para o público geral (GA) até 1º de março de 2022.

Você pode enviar alterações ao seu aplicativo (como novos recursos ou até mesmo metadados) no Partner Center. Essas alterações exigem um novo processo de revisão.

Verifique o seguinte ao publicar atualizações:

* Não altere a ID do aplicativo.
* Incremente o número de versão do aplicativo.
* No Partner Center, não selecione **Adicionar um novo aplicativo** para fazer a atualização. Vá para a página do seu aplicativo.

### <a name="app-updates-requiring-user-consent"></a>Atualizações de aplicativo que exigem consentimento do usuário

Quando um usuário instala seu aplicativo, ele deve conceder ao aplicativo permissão para acessar os serviços e as informações que o aplicativo requer para funcionar. Na maioria dos casos, os usuários devem fazer isso uma vez e as novas versões do aplicativo são instaladas automaticamente.
No entanto, se você fizer qualquer uma das seguintes alterações em seu aplicativo, os usuários existentes deverão aceitar outra solicitação de permissão para instalar a atualização:

* Adicionar ou remover um bot.
* Altere a ID do bot.
* Modifique a configuração de notificação unidirecional de um bot.
* Modifique o suporte de um bot para carregar e baixar arquivos.
* Adicionar ou remover uma extensão de mensagem.
* Adicionar uma guia pessoal.
* Adicionar um canal e guia do grupo.
* Adicionar um conector.
* Modifique as configurações relacionadas ao seu registro de aplicativo do Microsoft Azure Active Directory (Azure AD). Para mais informações, veja [`webApplicationInfo`](~/resources/schema/manifest-schema.md#webapplicationinfo).

## <a name="fix-issues-with-your-published-app"></a>Corrigir problemas com seu aplicativo publicado

A Microsoft executa testes diários de automação em aplicativos listados na loja do Teams. Se forem identificados problemas com seu aplicativo, entraremos em contato com um relatório detalhado sobre como reproduzir os problemas e as recomendações para resolvê-los. Se você não puder corrigir os problemas em uma linha do tempo declarada, a listagem de aplicativos poderá ser removida da loja.

## <a name="promote-your-app-on-another-site"></a>Promover seu aplicativo em outro site

Quando seu aplicativo é listado na loja do Teams, você pode criar um link que inicia o Teams e exibe uma caixa de diálogo para instalar seu aplicativo. Você pode incluir esse link, por exemplo, com um botão de download na página de marketing do seu produto.

Crie o link usando a seguinte URL acrescentada à ID do aplicativo: `https://teams.microsoft.com/l/app/<your-app-id>`.

## <a name="complete-microsoft-365-certification"></a>Certificação Microsoft 365 Completa

[Certificação Microsoft 365](/microsoft-365-app-certification/docs/certification) oferece garantias de que os dados e a privacidade são adequadamente protegidos e protegidos quando um aplicativo ou suplemento do Office de terceiros é instalado em seu ecossistema Microsoft 365. A certificação confirma que uma solução de aplicativo é compatível com as tecnologias da Microsoft, compatível com as práticas recomendadas de segurança de aplicativos na nuvem e com suporte da Microsoft.

## <a name="see-also"></a>Confira também

[Monetize seu aplicativo por meio do Marketplace Comercial da Microsoft](/office/dev/store/monetize-addins-through-microsoft-commercial-marketplace)
