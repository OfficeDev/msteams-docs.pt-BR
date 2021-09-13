---
title: Resolver problemas com o envio da loja
description: Entenda como solucionar problemas e corrigir problemas com o envio Microsoft Teams store.
ms.topic: how-to
author: heath-hamilton
ms.author: surbhigupta
ms.localizationpriority: none
ms.openlocfilehash: 39ab797bf87638e107f55e8b83d002372a4261f5
ms.sourcegitcommit: fc9f906ea1316028d85b41959980b81f2c23ef2f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/12/2021
ms.locfileid: "59155434"
---
# <a name="resolve-issues-if-your-microsoft-teams-store-submission-fails"></a>Resolver problemas se o envio Microsoft Teams do armazenamento de dados falhar

Os aplicativos publicados no Microsoft Teams devem atender às [diretrizes Teams](~/concepts/deploy-and-publish/appsource/prepare/teams-store-validation-guidelines.md) de validação da loja e políticas [de marketplace comercial.](/legal/marketplace/certification-policies)

Se o envio da loja falhar, a Microsoft fornece um serviço de validação de concierge para ajudar a obter o aplicativo compatível e publicado.

## <a name="get-help-directly-from-microsoft"></a>Obter ajuda diretamente da Microsoft

O serviço de validação de concierge fornecido pela Microsoft ajuda os desenvolvedores a publicarem seus aplicativos no Teams store. Como parte desse serviço, a Microsoft verifica se seu aplicativo funciona conforme descrito, contém todos os metadados apropriados e fornece valor aos usuários.

Se o envio do aplicativo falhar, a Microsoft enviará um relatório de revisão com recomendações dentro de 24 horas após o envio.

## <a name="resolve-issues-and-resubmit-your-app"></a>Resolver problemas e reabrir seu aplicativo

Você deve corrigir todos os problemas relatados pela equipe de validação do concierge da Microsoft antes de reabrir o aplicativo no Partner Center. O relatório da Microsoft inclui as seguintes informações:

* Uma diretriz [de validação correspondente](~/concepts/deploy-and-publish/appsource/prepare/teams-store-validation-guidelines.md) para cada problema.
* Instruções sobre como reproduzir cada problema.
* Recomendações para resolver cada problema com base na documentação de desenvolvedor disponível publicamente.

O processo para resolver problemas e reabrir um aplicativo normalmente é assim:

1. Você corrige todos os problemas no relatório.
1. Você envia o seguinte para a equipe de validação de concierge da Microsoft <a href="mailto:teamsubm@microsoft.com">em teamsubm@microsoft.com</a>:
   * Um pacote de aplicativo atualizado
   * Notas de teste para seu aplicativo, se você não as incluiu no envio original:
      * Credenciais para pelo menos duas contas (um administrador e um não administrador).
      * Instruções para configurar o aplicativo e testar sua funcionalidade.
      * Um vídeo mostrando seu aplicativo usado em Teams.
1. A equipe de validação de concierge da Microsoft testa totalmente seu aplicativo atualizado.
1. Você faz um dos seguintes:
   * Se seu aplicativo não tiver problemas, reapresente seu aplicativo no Partner Center.
   * Se os problemas não são resolvidos ou a Microsoft encontra novos problemas, você recebe outro relatório sobre o que corrigir. Resolva esses problemas e envie uma versão atualizada do aplicativo <a href="mailto:teamsubm@microsoft.com">para</a>teamsubm@microsoft.com .

> [!CAUTION]
> Para evitar várias falhas de envio, não reapresente seu aplicativo no Partner Center até que a equipe de validação do concierge da Microsoft aprove seu aplicativo.

## <a name="faq"></a>Perguntas frequentes

Obter respostas para algumas perguntas comuns ao resolver problemas de envio de aplicativo.

<br>

<details>

<summary><b>Quanto tempo levará para publicar meu aplicativo?</b></summary>

Se o envio da loja não tiver problemas, seu aplicativo será publicado dentro de 1 a 2 dias úteis. Se o aplicativo falhar, uma equipe da Microsoft fornece recomendações para corrigir os problemas. Depois de fazer essas correções e reajustar um aplicativo atualizado para essa equipe, você será notificado em 24 horas se seu aplicativo estiver pronto para publicar ou ainda precisar de mais trabalho.

<br>

</details>

<details>

<summary><b>Como aumentar a probabilidade de meu aplicativo passar no envio?</b></summary>

Fazer o seguinte pode levar a um envio bem-sucedido:

1. Desenvolva seu aplicativo com base nas diretrizes [Teams design.](~/concepts/design/design-teams-app-overview.md)
1. Certifique-se de que seu aplicativo adere às [diretrizes de validação](~/concepts/deploy-and-publish/appsource/prepare/teams-store-validation-guidelines.md) do Teams store e às políticas de [certificação do marketplace comercial da Microsoft.](/legal/marketplace/certification-policies)
1. Teste seu pacote de aplicativos com a [Microsoft Teams de validação de aplicativos](https://dev.teams.microsoft.com/appvalidation.html).
1. [Preparar seu envio Teams de armazenamento de dados.](~/concepts/deploy-and-publish/appsource/prepare/submission-checklist.md)

<br>

</details>

<details>

<summary><b>Meu aplicativo está em teste beta. Posso enviar meu aplicativo de qualquer maneira para economizar tempo no processo de publicação?</b></summary>

Não. A Microsoft valida somente aplicativos prontos para produção.

<br>

</details>

<details>

<summary><b>Posso entrar em contato com o teamsubm@microsoft.com email antes de enviar meu aplicativo pela primeira vez no Partner Center?</b></summary>

Não. A Microsoft não começa a validar seu aplicativo até que você envie seu aplicativo pela primeira vez no Partner Center.

<br>

</details>

<details>

<summary><b>Recebi um email do Partner Center dizendo que meu aplicativo foi aprovado para publicar. Por que meu aplicativo não está na Teams store?</b></summary>

Depois que seu aplicativo é aprovado, a publicação geralmente leva de 1 a 2 dias úteis, dependendo dos recursos do aplicativo.Se seu aplicativo não tiver publicado após dois dias úteis, entre em contato <a href="mailto:teamsubm@microsoft.com">teamsubm@microsoft.com</a>.

<br>

</details>
