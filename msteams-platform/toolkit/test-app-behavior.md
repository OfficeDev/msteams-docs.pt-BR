---
title: Testar o comportamento do aplicativo em um ambiente diferente
author: surbhigupta
description: Neste módulo, saiba como testar o comportamento do aplicativo em um ambiente diferente
ms.author: v-amprasad
ms.localizationpriority: high
ms.topic: overview
ms.date: 03/03/2022
ms.openlocfilehash: 187219fec76830119e795d1dd60a36b2374c65ac
ms.sourcegitcommit: ed7488415f814d0f60faa15ee8ec3d64ee336380
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2022
ms.locfileid: "67617053"
---
# <a name="test-app-behavior-in-different-environment"></a>Testar o comportamento do aplicativo em um ambiente diferente

Você pode testar seu aplicativo Teams após a integração com o Microsoft Teams. Para testar seu aplicativo teams, você precisa criar pelo menos um workspace em seu ambiente. Você pode usar o Kit de Ferramentas do Teams para testar seu aplicativo do Teams:

* **Hospedado localmente no Teams**: o Kit de Ferramentas do Teams hospeda localmente seu aplicativo do Teams ao fazer sideload dele no Teams para teste no ambiente local.

* **Hospedado na nuvem no Teams**: para testar seu aplicativo teams remotamente, você precisa hospedá-lo na nuvem usando o provisionamento e a implantação no Microsoft Azure Active Directory(Azure AD). Isso envolve carregar sua solução no Azure AD e, em seguida, carregar no Teams.

> [!NOTE]
> Para depuração e teste em escala de produção, recomendamos que você siga as diretrizes de sua própria empresa para garantir que possa dar suporte a testes, preparação e implantação por meio de seus próprios processos.

## <a name="locally-hosted-environment"></a>Ambiente hospedado localmente

O Teams é um produto baseado em nuvem que requer que todos os serviços acessados por ele sejam disponibilizados publicamente usando pontos de extremidade HTTPS. A hospedagem local trata do sideload no Teams para teste no ambiente local.

> [!NOTE]
> Embora você possa usar qualquer ferramenta de sua escolha para teste, recomendamos que você use [o ngrok](https://ngrok.com/download)

## <a name="cloud-hosted-environment"></a>Ambiente hospedado na nuvem

Para hospedar seu código de desenvolvimento e produção e seus pontos de extremidade HTTPS, você precisa testar remotamente seu aplicativo de equipes usando o provisionamento e a implantação em Azure AD. Você precisa garantir que todos os domínios estejam acessíveis no aplicativo Teams listado no [`validDomains`](~/resources/schema/manifest-schema.md#validdomains) objeto no `manifest.jason` arquivo

> [!NOTE]
> Para garantir um ambiente seguro, seja claro sobre o domínio e os subdomínios exatos que você referencia e esses domínios devem estar em seu controle. Por exemplo, `*.azurewebsites.net` não é recomendado, mas `contoso.azurewebsites.net` é recomendado.

## <a name="see-also"></a>Confira também

* [Depurar seu aplicativo Microsoft Teams localmente](debug-local.md)
* [Depurar processo em segundo plano](debug-background-process.md)
* [Usar o Kit de Ferramentas do Teams para provisionar recursos de nuvem](provision.md)
* [Implantar na nuvem](deploy.md)
* [Visualizar e personalizar o manifesto do aplicativo Teams](TeamsFx-preview-and-customize-app-manifest.md)
* [Gerenciar vários ambientes](TeamsFx-multi-env.md)
