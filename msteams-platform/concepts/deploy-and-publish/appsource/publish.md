---
title: Visão geral - Teams de publicação da loja de aplicativos
description: Descreve o processo para enviar seu aplicativo para o Partner Center e publicá-lo no Microsoft Teams store (e AppSource).
ms.topic: overview
author: heath-hamilton
ms.author: surbhigupta
ms.localizationpriority: none
ms.openlocfilehash: eaebde76a3d1f387ba16c9fdc77670144d22fa61
ms.sourcegitcommit: 40aade608ee21f5d7d813bd145bef5736dc647f1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/17/2022
ms.locfileid: "62881648"
---
# <a name="publish-your-app-to-the-microsoft-teams-store"></a>Publicar seu aplicativo no Microsoft Teams store

Você pode distribuir seu aplicativo diretamente para a loja dentro Microsoft Teams e alcançar milhões de usuários em todo o mundo. Se seu aplicativo também estiver em destaque na loja, você poderá alcançar instantaneamente clientes em potencial.

Os aplicativos publicados na Teams store também listam automaticamente no [Microsoft AppSource](https://appsource.microsoft.com), que é o marketplace oficial para Microsoft 365 aplicativos e soluções.

## <a name="understand-the-publishing-process"></a>Compreender o processo de publicação

Quando você acha que seu aplicativo está pronto para produção, você pode começar o processo de listá-lo no Teams store.

> [!TIP]
> Seguir as etapas de pré-envio de perto pode aumentar a possibilidade de que a Microsoft aprove seu aplicativo para publicação.

:::row:::
   :::column span="":::
      
   :::column-end:::
   :::column span="3":::
      :::image type="content" source="../../../assets/images/submission/teams-app-store-publish-process.png" alt-text="Teams de publicação da loja de aplicativos" lightbox="../../../assets/images/submission/teams-app-store-publish-process.png":::
   :::column-end:::
   :::column span="":::
      
   :::column-end:::
:::row-end:::

1. [Revise as diretrizes Teams de validação da loja](~/concepts/deploy-and-publish/appsource/prepare/teams-store-validation-guidelines.md) para garantir que seu aplicativo atenda Teams padrões de aplicativo e loja.

1. [Crie uma conta de desenvolvedor do Partner Center](~/concepts/deploy-and-publish/appsource/prepare/create-partner-center-dev-account.md).

1. [Prepare o envio da loja](~/concepts/deploy-and-publish/appsource/prepare/submission-checklist.md), que inclui a execução de testes automatizados, a compilação de notas de teste, a criação de uma listagem de loja, entre outras tarefas importantes para ajudar a acelerar o processo de revisão.

1. [Envie seu aplicativo por](/office/dev/store/add-in-submission-guide) meio do Partner Center.

1. Se o envio falhar, trabalhe diretamente com a Microsoft para [resolver os problemas e reabrir seu aplicativo](~/concepts/deploy-and-publish/appsource/resolve-submission-issues.md).

## <a name="what-to-expect-after-you-submit-your-app"></a>O que esperar depois de enviar seu aplicativo?

* **Testes de experiência e funcional profundos**

  Seu aplicativo é completamente revisado por um validador para garantir a conformidade com as políticas de certificação do [Microsoft Commercial Marketplace](/legal/marketplace/certification-policies) com foco em testes de experiência funcional e de usuário profundos, verificações de usabilidade e verificações de metadados. A validação de aplicativo é realizada em clientes desktop, web e móveis.

* **Publicação de aplicativos guiados por meio do serviço de concierge**

  Se não houver problemas observados com seu aplicativo, seu aplicativo será aprovado e publicado no Teams store. Se houver problemas, você receberá um relatório de validação automatizado do Partner Center com os detalhes de falha. Para ajudá-lo a publicar seu aplicativo com êxito no Teams store e orientá-lo durante esse processo, a equipe de validação enviará um email personalizado do nosso serviço de teamsubm@microsoft.com que [](mailto:teamsubm@microsoft.com) inclui as seguintes informações:

   * Resumo de todos os problemas

   * Detalhes de falhas ou problemas com links de política e categorização: 

     * Correção obrigatória: esses problemas devem ser corrigidos antes da aprovação do aplicativo.

     * Correção sugerida: esses problemas podem ser corrigidos após a aprovação do aplicativo, pois são recomendações para melhorar a experiência do aplicativo.

     * Bloqueador: esses problemas impedem que a equipe de validação teste ainda mais a funcionalidade do aplicativo e devem ser resolvidos para que a validação continue.

     * Consulta: Essas consultas podem ser compartilhadas para obter respostas a perguntas específicas relacionadas ao seu aplicativo.

   * Etapas para recriar problemas por meio de instruções escritas ou formato de vídeo.

   * Recomendações corrigir os problemas relatados com links para documentos de orientação.
 
  Depois de revisar a lista de problemas, corrige todos os problemas relatados e compartilhe o pacote de aplicativo atualizado por email, para que a equipe de validação valide completamente seu aplicativo. Se você tiver alguma consulta relacionada aos problemas relatados, entre em contato com a equipe de validação em [teamsubm@microsoft.com](mailto:teamsubm@microsoft.com).

  Se houver problemas restantes ou problemas de regressão observados em seu aplicativo, a equipe de validação compartilhará um relatório de validação atualizado com você. Se o aplicativo tiver bloqueadores, você poderá ver novos problemas relatados quando o aplicativo for validado depois que os bloqueadores são resolvidos. Às vezes, a equipe de validação também reparou em problemas de regressão em aplicativos após a implantação de correções. É necessário alguns re-envios para fechar todos os problemas de um aplicativo que consiste em bugs e ser aprovado para publicar no Teams store.

  Depois que todos os problemas relatados são fechados e o envio final é feito no Partner Center, a equipe de validação aprovará e publicará seu aplicativo. Permitir que pelo menos um dia útil para o aplicativo estar disponível no Teams store.

## <a name="tips-for-rapid-approval-to-publish-your-app"></a>Dicas aprovação rápida para publicar seu aplicativo

* **Durante a fase de design**

  Revise as [diretrizes](prepare/teams-store-validation-guidelines.md) de validação da loja no início do ciclo de vida do aplicativo (fase de design) para garantir que você crie seu aplicativo em alinhamento com os requisitos da loja. Se você criar seu aplicativo de acordo com essas diretrizes, isso impedirá qualquer retrabalho devido à não adesão às políticas de armazenamento.

* **Antes do envio do aplicativo**

  1. [Crie sua conta do Partner Center](prepare/create-partner-center-dev-account.md) com antecedência. Se você enfrentar quaisquer desafios com sua [conta do Partner Center](prepare/create-partner-center-dev-account.md), crie um [tíquete de suporte](/azure/marketplace/partner-center-portal/support).

  1. Revise as [diretrizes de validação da](prepare/teams-store-validation-guidelines.md) loja novamente para garantir que seu aplicativo está em alinhamento com os requisitos da loja. Isso ajuda a reduzir o número de problemas observados em seu aplicativo e, consequentemente, o tempo gasto para aprovar seu aplicativo.

  1. Teste e teste seu aplicativo de novo:

     1. Valide seu pacote de aplicativos usando o [Teams Portal do Desenvolvedor](https://dev.teams.microsoft.com/home) para identificar e corrigir quaisquer erros de pacote.

        :::image type="content" source="../../../assets/images/submission/teams-validation-developer-portal.png" alt-text="validação da loja":::
 
     1. Teste seu aplicativo completamente antes do envio do aplicativo para garantir que ele adere às políticas da loja. Fazer sideload do aplicativo Teams e testar os fluxos de usuário de ponta a ponta para seu aplicativo. Verifique se a funcionalidade funciona conforme o esperado, os links não são quebrados, a experiência do usuário não é bloqueada e se as limitações são claramente realçadas.

     1. Teste seu aplicativo em clientes desktop, web e móveis. Verifique se o aplicativo está respondendo entre diferentes fatores de formulário.

  1. [Conclua a verificação do](/azure/active-directory/develop/publisher-verification-overview) editor antes de enviar seu aplicativo. Se você tiver problemas, poderá criar um tíquete [de suporte para](/azure/marketplace/partner-center-portal/support) resolução.

  1. Ao se preparar para o envio do aplicativo, [siga a lista de](/microsoftteams/platform/concepts/deploy-and-publish/appsource/prepare/submission-checklist) verificação e inclua os seguintes detalhes como parte do pacote de envio:

      1. Pacote de aplicativo totalmente verificado.

      1. Trabalhando com credenciais de usuário de administrador e não administrador para testar a funcionalidade do aplicativo (se seu aplicativo oferecer um modelo de assinatura premium).

      1. Instruções de teste detalhando a funcionalidade do aplicativo e cenários com suporte.

      1. Instruções de instalação se seu aplicativo exigir configuração adicional para acessar a funcionalidade do aplicativo. Como alternativa, se seu aplicativo exigir configuração complexa, você também poderá fornecer acesso de administrador a um locatário [de demonstração](/office/developer-program/microsoft-365-developer-program-get-started) provisionado para que nossos validadores possam ignorar as etapas de configuração.

      1. Vincule a um fluxo de usuário chave de gravação de vídeo de demonstração para seu aplicativo. Isso é altamente recomendado.

* **Post app submission**

  * Depois de revisar o relatório de validação, responda ao thread de email com quaisquer consultas relacionadas ao relatório de validação ou se você precisar de suporte adicional para resolver os problemas relatados.

  * Verifique se você tem largura de banda adequada do desenvolvedor para resolver quaisquer problemas relatados até que o aplicativo seja aprovado.

  * Certifique-se de ter resolvido [todos os problemas](/microsoftteams/platform/concepts/deploy-and-publish/appsource/resolve-submission-issues) relatados pelo serviço de teamsubm@microsoft.com antes de [](mailto:teamsubm@microsoft.com) compartilhar seu pacote de aplicativos para testes posteriores. Isso ajuda a reduzir o número de iterações necessárias para validar seu aplicativo e, consequentemente, o tempo necessário para aprovar seu aplicativo.
  
  * Evite alterar a funcionalidade do aplicativo durante o processo de validação. Isso pode levar à descoberta de novos problemas e aumentar o tempo necessário para aprovar seu aplicativo.

## <a name="see-also"></a>Confira também

* [Publicação para Microsoft 365 App Stores](/office/dev/store/)
* [Upload seu Teams app](~/concepts/deploy-and-publish/apps-upload.md)
* [Publicar seu Teams aplicativo em sua organização](/MicrosoftTeams/tenant-apps-catalog-teams?toc=/microsoftteams/platform/toc.json&bc=/MicrosoftTeams/breadcrumb/toc.json)
* [Planejar a experiência de integração para usuários](../../design/understand-use-cases.md#plan-the-onboarding-experience)
* [Distribuindo aplicativos de guia em dispositivos móveis](../../../tabs/design/tabs-mobile.md#distribution)
* [Teste de visualização para aplicativos monetizados](prepare/Test-preview-for-monetized-apps.md)
