---
title: Manter e dar suporte ao seu aplicativo publicado
description: O que pensar quando sua loja for listada na Teams store e no AppSource.
ms.topic: conceptual
localization_priority: Normal
author: heath-hamilton
ms.author: surbhigupta
ms.openlocfilehash: 57b57e268a4f2eafc14d0372b8b8383e410a80d5
ms.sourcegitcommit: 25c9ad27f99682caaa7347840578b118c63b8f69
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/30/2021
ms.locfileid: "52101748"
---
# <a name="maintain-your-published-microsoft-teams-app"></a>Manter seu aplicativo Microsoft Teams publicado

Com seu aplicativo listado na Microsoft Teams, comece a pensar em como você manterá o aplicativo em frente e aumentará os downloads e o uso.

## <a name="publish-updates-to-your-app"></a>Publicar atualizações em seu aplicativo

Você pode enviar alterações ao seu aplicativo (como novos recursos ou até mesmo metadados) no Partner Center. Essas alterações exigem um novo processo de revisão.

Verifique o seguinte ao publicar atualizações:

* Não altere a ID do aplicativo.
* Incremente o número da versão do aplicativo.
* No Partner Center, não selecione **Adicionar um novo aplicativo** para fazer a atualização. Vá para a página do seu aplicativo.

### <a name="app-updates-requiring-user-consent"></a>Atualizações de aplicativo que exigem consentimento do usuário

Quando um usuário instala seu aplicativo, ele deve dar ao aplicativo permissão para acessar os serviços e informações que o aplicativo exige para funcionar. Na maioria dos casos, os usuários só têm que fazer isso uma vez e novas versões do aplicativo são instaladas automaticamente.

No entanto, se você fizer qualquer uma das seguintes alterações em seu aplicativo, seus usuários existentes devem aceitar outra solicitação de permissão para instalar a atualização:

* Adicionar ou remover um bot.
* Altere a ID do bot.
* Modificar a configuração de notificação one-way de um bot.
* Modifique o suporte de um bot para carregar e baixar arquivos.
* Adicione ou remova uma extensão de mensagens.
* Adicione uma guia pessoal.
* Adicione um canal e uma guia de grupo.
* Adicione um conector.
* Modificar configurações relacionadas ao seu Azure Active Directory (registro do aplicativo do Azure AD). Para obter mais informações, consulte [`webApplicationInfo`](~/resources/schema/manifest-schema.md#webapplicationinfo) .

## <a name="fix-issues-with-your-published-app"></a>Corrigir problemas com seu aplicativo publicado

A Microsoft executa testes diários de automação em aplicativos listados no Teams store. Se os problemas com seu aplicativo são identificados, entraremos em contato com um relatório detalhado sobre como reproduzir os problemas e recomendações para resolvê-los. Se você não puder corrigir os problemas em uma linha do tempo afirmada, a listagem do aplicativo poderá ser removida da loja.

## <a name="promote-your-app-on-another-site"></a>Promover seu aplicativo em outro site

Quando seu aplicativo é listado na Teams, você pode criar um link que inicia Teams e exibe uma caixa de diálogo para instalar seu aplicativo. Você pode incluir esse link, por exemplo, com um botão de download na página de marketing do produto.

Crie o link usando a seguinte URL anexada à ID do aplicativo: `https://teams.microsoft.com/l/app/<your-app-id>` .

## <a name="complete-microsoft-365-certification"></a>Concluir Microsoft 365 Certificação

[Microsoft 365 Certificação](/microsoft-365-app-certification/docs/certification) oferece garantias de que os dados e a privacidade são adequadamente protegidos e protegidos quando um Aplicativo do Office ou um Aplicativo do Office de terceiros é instalado em seu ecossistema Microsoft 365 de terceiros. A certificação confirma que seu aplicativo é compatível com tecnologias da Microsoft, compatível com as práticas recomendadas de segurança do aplicativo na nuvem e com suporte da Microsoft.

## <a name="see-also"></a>Confira também

* [Monetize seu aplicativo por meio do Marketplace Comercial da Microsoft](/office/dev/store/monetize-addins-through-microsoft-commercial-marketplace)
