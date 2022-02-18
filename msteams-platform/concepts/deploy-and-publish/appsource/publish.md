---
title: Visão geral – Processo de publicação da loja de aplicativos do Teams
description: Descreve o processo para enviar seu aplicativo ao Partner Center e publicá-lo na loja do Microsoft Teams (e AppSource).
ms.topic: overview
author: heath-hamilton
ms.author: surbhigupta
ms.localizationpriority: high
ms.openlocfilehash: fd7d2075d79e5c54e9257b71f8bf351fe3cd6823
ms.sourcegitcommit: fb10a8b14acdba5cc48d2b31dec6f8e6d4ad99ba
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/18/2022
ms.locfileid: "62896317"
---
# <a name="publish-your-app-to-the-microsoft-teams-store"></a>Publicar seu aplicativo na loja do Microsoft Teams

Você pode distribuir seu aplicativo diretamente na loja do Microsoft Teams e alcançar milhões de usuários em todo o mundo. Se seu aplicativo também estiver em destaque na loja, você poderá alcançar instantaneamente clientes em potencial.

Os aplicativos publicados na loja do Teams também são listados automaticamente no [Microsoft AppSource](https://appsource.microsoft.com), que é o marketplace oficial para aplicativos e soluções do Microsoft 365.

## <a name="understand-the-publishing-process"></a>Compreender o processo de publicação

Quando achar que seu aplicativo está pronto para produção, você poderá começar o processo de listá-lo na loja do Teams.

> [!TIP]
> Seguir as etapas de pré-envio pode aumentar a possibilidade de que a Microsoft aprove seu aplicativo para publicação.

:::row:::
   :::column span="":::
      
   :::column-end:::
   :::column span="3":::
      :::image type="content" source="../../../assets/images/submission/teams-app-store-publish-process.png" alt-text="Processo de publicação da loja de aplicativos do Teams" lightbox="../../../assets/images/submission/teams-app-store-publish-process.png":::
   :::column-end:::
   :::column span="":::
      
   :::column-end:::
:::row-end:::

1. [Revise as diretrizes Teams de validação do repositório](~/concepts/deploy-and-publish/appsource/prepare/teams-store-validation-guidelines.md) para garantir que seu aplicativo atenda Teams padrões de aplicativo e loja.

1. [Criar uma conta de desenvolvedor do Partner Center](~/concepts/deploy-and-publish/appsource/prepare/create-partner-center-dev-account.md).

1. [Prepare o envio do seu repositório](~/concepts/deploy-and-publish/appsource/prepare/submission-checklist.md), que inclui a execução de testes automatizados, a compilação de notas de teste, a criação de uma listagem da loja, entre outras tarefas importantes para ajudar a agilizar o processo de revisão.

1. [Envie seu aplicativo](/office/dev/store/add-in-submission-guide) por meio do Partner Center.

1. Se o envio falhar, trabalhe diretamente com a Microsoft para [resolver os problemas e reenvie seu aplicativo](~/concepts/deploy-and-publish/appsource/resolve-submission-issues.md).

## <a name="what-to-expect-after-you-submit-your-app"></a>O que esperar depois de enviar seu aplicativo ou?

* **Testes funcionais e de experiência profundos**

  Seu aplicativo é completamente revisado por um validador para garantir a conformidade com as [políticas de certificação do Microsoft Commercial Marketplace](/legal/marketplace/certification-policies) com foco em testes profundos funcionais e de experiência do usuário, verificações de usabilidade e verificações de metadados. A validação do aplicativo é executada em clientes móveis, da Web e da área de trabalho.

* **Publicação de aplicativo guiado por meio do serviço de concierge**

  Se não houver problemas observados com seu aplicativo, seu aplicativo será aprovado e publicado na loja do Teams. Se houver problemas, você receberá um relatório de validação automatizado do Partner Center com os detalhes da falha. Para ajudá-lo a publicar com êxito seu aplicativo na loja do Teams e orientá-lo nesse processo, a equipe de validação enviará um e-mail personalizado do nosso serviço de concierge [teamsubm@microsoft.com](mailto:teamsubm@microsoft.com) que inclui as seguintes informações:

   * Resumo de todos os problemas

   * Detalhes de falhas ou problemas com links de política e categorização: 

     * Correção obrigatória: esses problemas devem ser corrigidos antes da aprovação do aplicativo.

     * Correção sugerida: esses problemas podem ser corrigidos após a aprovação do aplicativo, pois são recomendações para melhorar a experiência dos aplicativos.

     * Bloqueador: esses problemas impedem que a equipe de validação teste ainda mais a funcionalidade do aplicativo e devem ser resolvidos para que a validação continue.

     * Consulta: essas consultas podem ser compartilhadas para obter respostas a perguntas específicas relacionadas ao seu aplicativo.

   * Etapas para recriar problemas por meio de instruções escritas ou formato de vídeo.

   * Recomendações para corrigir os problemas relatados com links para documentos de orientação.
 
  Depois de examinar a lista de problemas, corrija todos os problemas relatados e compartilhe o pacote de aplicativo atualizado por email, para que a equipe de validação valide seu aplicativo completamente. Se você tiver alguma consulta relacionada aos problemas relatados, entre em contato com a equipe de validação em [teamsubm@microsoft.com](mailto:teamsubm@microsoft.com).

  Se houver problemas restantes ou de regressão observados em seu aplicativo, a equipe de validação compartilhará um relatório de validação atualizado com você. Se o aplicativo tiver bloqueadores, você poderá ver novos problemas relatados quando o aplicativo for validado depois que os bloqueadores forem resolvidos. Às vezes, a equipe de validação também observou problemas de regressão em aplicativos após a implantação de correções. São necessários alguns reenvios para fechar todos os problemas de um aplicativo que consiste em bugs e obtê-lo aprovado para publicação na loja do Teams.

  Depois que todos os problemas relatados forem encerrados e o envio final for feito no Partner Center, a equipe de validação aprovará e publicará seu aplicativo. Aguarde pelo menos um dia útil para que o aplicativo esteja disponível na loja do Teams.

## <a name="tips-for-rapid-approval-to-publish-your-app"></a>Dicas para aprovação rápida para publicar seu aplicativo

* **Durante a fase de projeto**

  Revise as diretrizes de [validação do repositório](prepare/teams-store-validation-guidelines.md) no início do ciclo de vida do seu aplicativo (fase de design) para garantir que você crie seu aplicativo de acordo com os requisitos da loja. Se você criar seu aplicativo de acordo com essas diretrizes, isso impedirá qualquer retrabalho devido à não adesão às políticas de armazenamento.

* **Antes do envio de aplicativo**

  1. [Crie sua conta do Partner Center com antecedência](prepare/create-partner-center-dev-account.md). Se você encontrar algum desafio com sua [conta do Partner Center](prepare/create-partner-center-dev-account.md), crie um [tíquete de suporte](/azure/marketplace/partner-center-portal/support).

  1. Revise as [diretrizes de validação do repositório](prepare/teams-store-validation-guidelines.md) novamente para garantir que seu aplicativo esteja alinhado com os requisitos da loja. Isso ajuda a reduzir o número de problemas observados em seu aplicativo e, consequentemente, o tempo necessário para aprovar seu aplicativo.

  1. Teste e teste novamente seu aplicativo:

     1. Valide seu pacote de aplicativo usando o [Portal do Desenvolvedor](https://dev.teams.microsoft.com/home) do Teams para identificar e corrigir erros de pacote.

        :::image type="content" source="../../../assets/images/submission/teams-validation-developer-portal.png" alt-text="validação do repositório":::
 
     1. Teste seu aplicativo completamente antes do envio do aplicativo para garantir que ele siga as políticas da loja. Faça sideload do aplicativo no Teams e teste os fluxos de usuário de ponta a ponta para seu aplicativo. Verifique se a funcionalidade funciona conforme o esperado, se os links não estão quebrados, se a experiência do usuário não está bloqueada e se há limitações claramente realçadas.

     1. Teste seu aplicativo na área de trabalho, na Web e em clientes móveis. Verifique se o aplicativo está respondendo entre diferentes fatores forma.

  1. Conclua a [verificação do editor](/azure/active-directory/develop/publisher-verification-overview) antes de enviar seu aplicativo. Se você tiver algum problema, poderá criar um [tíquete de suporte](/azure/marketplace/partner-center-portal/support) para resolução.

  1. Ao se preparar para o envio do aplicativo, [siga a lista de verificação](/microsoftteams/platform/concepts/deploy-and-publish/appsource/prepare/submission-checklist) e inclua os seguintes detalhes como parte do pacote de envio:

      1. Pacote do aplicativo verificado por completo.

      1. Credenciais de usuário administrador e não administrador em funcionamento para testar a funcionalidade do seu aplicativo (se seu aplicativo oferecer um modelo de assinatura premium).

      1. Instruções de teste detalhando a funcionalidade do aplicativo e os cenários com suporte.

      1. Instruções de configuração se seu aplicativo exigir configuração adicional para acessar a funcionalidade do aplicativo. Como alternativa, se seu aplicativo exigir configuração complexa, você também poderá fornecer um [locatário de demonstração provisionado](/office/developer-program/microsoft-365-developer-program-get-started) com acesso de administrador para que nossos validadores possam pular as etapas de configuração.

      1. Link para um fluxo de usuário chave de gravação de vídeo de demonstração para seu aplicativo. Isso é altamente recomendado.

* **Postar envio de aplicativo**

  * Depois de examinar o relatório de validação, responda ao thread de email com todas as consultas relacionadas ao relatório de validação ou se precisar de suporte adicional para resolver os problemas relatados.

  * Verifique se você tem largura de banda de desenvolvedor adequada para resolver quaisquer problemas relatados até que o aplicativo seja aprovado.

  * Certifique-se de ter resolvido [todos os problemas relatados](/microsoftteams/platform/concepts/deploy-and-publish/appsource/resolve-submission-issues) a você pelo serviço de concierge [teamsubm@microsoft.com](mailto:teamsubm@microsoft.com) antes de compartilhar seu pacote de aplicativos para testes adicionais. Isso ajuda a reduzir o número de iterações necessárias para validar seu aplicativo e, consequentemente, o tempo necessário para aprovar seu aplicativo.
  
  * Evite alterar a funcionalidade do aplicativo durante o processo de validação. Isso pode levar à descoberta de novos problemas e aumentar o tempo necessário para aprovar seu aplicativo.

## <a name="see-also"></a>Confira também

* [Publicando nas lojas de aplicativos do Microsoft 365](/office/dev/store/)
* [Carregue seu aplicativo Teams](~/concepts/deploy-and-publish/apps-upload.md)
* [Publicar seu aplicativo Teams em sua organização](/MicrosoftTeams/tenant-apps-catalog-teams?toc=/microsoftteams/platform/toc.json&bc=/MicrosoftTeams/breadcrumb/toc.json)
* [Planejar a experiência de integração para os usuários](../../design/understand-use-cases.md#plan-the-onboarding-experience)
* [Distribuindo aplicativos de guia no celular](../../../tabs/design/tabs-mobile.md#distribution)
* [Teste de visualização para aplicativos monetizados](prepare/Test-preview-for-monetized-apps.md)
