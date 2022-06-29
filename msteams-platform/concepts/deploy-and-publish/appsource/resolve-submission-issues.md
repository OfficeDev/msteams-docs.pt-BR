---
title: Resolver problemas com o envio da loja
description: Neste artigo, saiba como solucionar problemas e corrigir problemas com o envio da loja do Microsoft Teams.
ms.topic: how-to
author: heath-hamilton
ms.author: surbhigupta
ms.localizationpriority: medium
ms.openlocfilehash: 5faf2d3622e88febe9522f5e2df6716ec2680cca
ms.sourcegitcommit: ffc57e128f0ae21ad2144ced93db7c78a5ae25c4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/29/2022
ms.locfileid: "66503869"
---
# <a name="resolve-issues-if-your-teams-store-submission-fails"></a>Resolver problemas se o envio da loja do Teams falhar

Os aplicativos publicados na loja do Microsoft Teams devem atender às [diretrizes de validação da loja do Teams](~/concepts/deploy-and-publish/appsource/prepare/teams-store-validation-guidelines.md) e às [políticas do marketplace comercial](/legal/marketplace/certification-policies).

Se o envio da loja falhar, a Microsoft fornecerá um serviço de validação de concierge para ajudar a fazer com que seu aplicativo seja compatível e publicado.

## <a name="get-help-directly-from-microsoft"></a>Obter ajuda diretamente da Microsoft

O serviço de validação de concierge fornecido pela Microsoft ajuda os desenvolvedores a publicar seus aplicativos na loja do Teams. Como parte desse serviço, a Microsoft verifica se seu aplicativo funciona conforme descrito, contém todos os metadados apropriados e fornece valor aos usuários.

Se o envio do aplicativo falhar, a Microsoft enviará um relatório de revisão com recomendações dentro de 24 horas após o envio.

## <a name="resolve-issues-and-resubmit-your-app"></a>Resolver problemas e reenviar seu aplicativo

Você deve corrigir todos os problemas relatados pela equipe de validação do Concierge da Microsoft antes de reenviar seu aplicativo no Partner Center. O relatório da Microsoft inclui as seguintes informações:

* Uma diretriz [de validação correspondente](~/concepts/deploy-and-publish/appsource/prepare/teams-store-validation-guidelines.md) para cada problema.
* Instruções sobre como reproduzir cada problema.
* Recomendações para resolver cada problema com base na documentação do desenvolvedor disponível publicamente.

O processo para resolver problemas e reenviar um aplicativo normalmente é assim:

1. Corrija todos os problemas no relatório.
1. Você envia o seguinte para a equipe de validação do Concierge da Microsoft <a href="mailto:teamsubm@microsoft.com">em teamsubm@microsoft.com</a>:
   * Um pacote de aplicativo atualizado
   * Notas de teste para seu aplicativo, se você não as incluir no envio original:
      * Credenciais para pelo menos duas contas (um administrador e um não administrador).
      * Instruções para configurar o aplicativo e testar sua funcionalidade.
      * Um vídeo mostrando seu aplicativo usado no Teams.
1. A equipe de validação do Microsoft Concierge testa totalmente seu aplicativo atualizado.
1. Siga um dos seguintes procedimentos:
   * Se seu aplicativo estiver livre de problemas, reenvie seu aplicativo no Partner Center.
   * Se os problemas não forem resolvidos ou a Microsoft encontrar novos problemas, você receberá outro relatório sobre o que corrigir. Resolva esses problemas e envie uma versão atualizada do aplicativo para <a href="mailto:teamsubm@microsoft.com">teamsubm@microsoft.com</a>.

> [!CAUTION]
> Para evitar várias falhas de envio, não reenvie seu aplicativo no Partner Center até que a equipe de validação do microsoft concierge aprove seu aplicativo.

## <a name="faq"></a>Perguntas frequentes

Obtenha respostas para algumas perguntas comuns ao resolver problemas de envio de aplicativo.

<br>

<details>

<summary><b>Quanto tempo levará para publicar meu aplicativo?</b></summary>

Se o envio da loja não tiver problemas, seu aplicativo será publicado dentro de 1 a 2 dias úteis. Se o aplicativo falhar, uma equipe da Microsoft fornecerá recomendações para corrigir os problemas. Depois de fazer essas correções e reenviar um aplicativo atualizado para essa equipe, você será notificado em 24 horas se seu aplicativo estiver pronto para publicar ou ainda precisar de mais trabalho.

<br>

</details>

<details>

<summary><b>Como fazer aumentar a probabilidade de meu aplicativo passar no envio?</b></summary>

Fazer o seguinte pode levar a um envio bem-sucedido:

1. Desenvolva seu aplicativo com base nas [diretrizes de design do Teams](~/concepts/design/design-teams-app-overview.md).
1. Verifique se seu aplicativo segue as diretrizes de validação da [loja do Teams e](~/concepts/deploy-and-publish/appsource/prepare/teams-store-validation-guidelines.md) as [políticas de certificação do marketplace comercial da Microsoft](/legal/marketplace/certification-policies).
1. Teste o pacote do aplicativo com a ferramenta [de validação de aplicativo do Microsoft Teams](https://dev.teams.microsoft.com/appvalidation.html).
1. [Prepare o envio da loja do Teams](~/concepts/deploy-and-publish/appsource/prepare/submission-checklist.md).

<br>

</details>

<details>

<summary><b>Meu aplicativo está em teste beta. Posso enviar meu aplicativo de qualquer maneira para economizar tempo no processo de publicação?</b></summary>

Não. A Microsoft valida apenas aplicativos prontos para produção.

<br>

</details>

<details>

<summary><b>Posso entrar em contato com o teamsubm@microsoft.com email antes de enviar meu aplicativo pela primeira vez no Partner Center?</b></summary>

Não. A Microsoft não começa a validar seu aplicativo até que você envie seu aplicativo pela primeira vez no Partner Center.

<br>

</details>

<details>

<summary><b>Recebi um email do Partner Center informando que meu aplicativo foi aprovado para publicação. Por que meu aplicativo não está na loja do Teams?</b></summary>

Depois que seu aplicativo é aprovado, a publicação geralmente leva de 1 a 2 dias úteis, dependendo dos recursos do aplicativo.Se seu aplicativo não tiver sido publicado após dois dias úteis, entre em contato <a href="mailto:teamsubm@microsoft.com">com teamsubm@microsoft.com</a>.

<br>

</details>
