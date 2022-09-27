---
title: Visão geral – Publicar seu aplicativo na loja do Microsoft Teams
description: Saiba como enviar seu aplicativo para o Partner Center e publicá-lo na loja do Microsoft Teams (e no AppSource).
ms.topic: overview
author: heath-hamilton
ms.author: surbhigupta
ms.localizationpriority: high
ms.openlocfilehash: f8891edb11134570a79c5483eea722a44ad48b91
ms.sourcegitcommit: 377a4b712b50a211851aeecc1029414939945390
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/27/2022
ms.locfileid: "68044648"
---
# <a name="publish-your-app-to-the-microsoft-teams-store"></a>Publicar seu aplicativo na loja do Microsoft Teams

Você pode distribuir seu aplicativo diretamente na loja do Microsoft Teams e alcançar milhões de usuários em todo o mundo. Se seu aplicativo também estiver em destaque na loja, você poderá alcançar instantaneamente clientes em potencial.

Os aplicativos publicados na loja do Teams também são listados automaticamente no [mercado comercial da Microsoft](https://appsource.microsoft.com), que é o mercado oficial para aplicativos e soluções do Microsoft 365.

## <a name="understand-the-publishing-process"></a>Compreender o processo de publicação

Se seu aplicativo estiver pronto para produção, você poderá começar o processo de listá-lo na loja Teams.

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

  Seu aplicativo é cuidadosamente examinado por um validador para garantir a conformidade com as [políticas de certificação do Marketplace Commercial da Microsoft](/legal/marketplace/certification-policies).
  Haverá um foco em testes funcionais profundos e de experiência do usuário, verificações de usabilidade e verificações de metadados. A validação do aplicativo é executada em clientes móveis, da Web e da área de trabalho. Trabalhamos duro para fornecer a você um relatório de teste detalhado em 24 horas úteis após o envio.

* **Publicação de aplicativo guiado por meio do serviço de concierge**

  Se não houver problemas observados com seu aplicativo, ele será aprovado e publicado na loja do Teams. Por outro lado, se os problemas estiverem presentes, você receberá um relatório de validação automatizado do Partner Center com os detalhes da falha. Para ajudá-lo a publicar com êxito seu aplicativo na loja do Teams e orientá-lo nesse processo, a equipe de validação enviará um e-mail personalizado do nosso serviço de concierge [teamsubm@microsoft.com](mailto:teamsubm@microsoft.com) que inclui as seguintes informações:

  * Resumo de todos os problemas

  * Detalhes de falhas ou problemas com links de política e categorização:

    * Correção obrigatória: os problemas devem ser corrigidos antes que o aplicativo seja aprovado.

    * Correção sugerida: os problemas podem ser corrigidos após a aprovação do aplicativo, pois são recomendações para melhorar a experiência do seu aplicativo.

    * Bloqueador: os problemas impedem a equipe de validação de testar ainda mais a funcionalidade do seu aplicativo e devem ser resolvido para que a validação continue.

    * Consulta: as consultas podem ser compartilhadas para obter respostas para perguntas específicas relacionadas ao seu aplicativo.

  * Etapas para recriar problemas por meio de instruções escritas ou formato de vídeo.

  * Recomendações para corrigir os problemas relatados com links para documentos de orientação.

  Depois de examinar a lista de problemas, corrija todos os problemas relatados e compartilhe o pacote do aplicativo atualizado por email para que a equipe de validação revalida seu aplicativo completamente. Se você tiver alguma consulta relacionada aos problemas relatados, entre em contato com a equipe de validação em [teamsubm@microsoft.com](mailto:teamsubm@microsoft.com).

  Se houver problemas restantes ou de regressão observados em seu aplicativo, a equipe de validação compartilhará um relatório de validação atualizado com você. Se o aplicativo tiver bloqueadores, você poderá ver novos problemas relatados quando o aplicativo for validado depois que os bloqueadores forem resolvidos. Às vezes, a equipe de validação também observou problemas de regressão em aplicativos após a implantação de correções. São necessários alguns reenvios para fechar todos os problemas de um aplicativo que consiste em bugs e obtê-lo aprovado para publicação na loja do Teams.

  Depois que todos os problemas relatados forem encerrados e o envio final for feito no Partner Center, a equipe de validação aprovará e publicará seu aplicativo. Aguarde pelo menos um dia útil para que o aplicativo esteja disponível na loja do Teams.

* **Analisar o uso do aplicativo**

  Depois que seu aplicativo for aprovado e publicado, você poderá acompanhar o uso do aplicativo no [Relatório de uso do aplicativo do Teams](/office/dev/store/teams-apps-usage) no Partner Center. As métricas incluem usuários ativos mensais, diários e semanais e gráficos de retenção e intensidade que permitem acompanhar a variação e a frequência de uso.

  Os dados de aplicativos recém-publicados demoram cerca de uma semana para aparecer no relatório.

## <a name="tips-for-rapid-approval-to-publish-your-app"></a>Dicas para aprovação rápida para publicar seu aplicativo

* **Durante a fase de projeto**

  Revise as diretrizes de [validação do repositório](~/concepts/deploy-and-publish/appsource/prepare/teams-store-validation-guidelines.md) no início do ciclo de vida do seu aplicativo (fase de design) para garantir que você crie seu aplicativo de acordo com os requisitos da loja. Se você criar seu aplicativo de acordo com estas diretrizes, então ele evitará qualquer retrabalho devido à não adesão às políticas de armazenamento.

* **Antes do envio de aplicativo**

  1. [Crie sua conta do Partner Center com antecedência](prepare/create-partner-center-dev-account.md). Se você encontrar algum desafio com sua [conta do Partner Center](prepare/create-partner-center-dev-account.md), crie um [tíquete de suporte](/azure/marketplace/partner-center-portal/support).

  1. Revise as [diretrizes de validação do repositório](prepare/teams-store-validation-guidelines.md) novamente para garantir que seu aplicativo esteja alinhado com os requisitos da loja. A revisão ajuda a reduzir o número de problemas observados em seu aplicativo e, portanto, o tempo necessário para aprovar seu aplicativo.

  1. Teste e teste novamente seu aplicativo:

     1. Valide seu pacote de aplicativo usando o [Portal do Desenvolvedor](https://dev.teams.microsoft.com/home) do Teams para identificar e corrigir erros de pacote.

        :::image type="content" source="../../../assets/images/submission/teams-validation-developer-portal.png" alt-text="Validação do aplicativo da loja do Microsoft Teams no Portal" lightbox="../../../assets/images/submission/teams-validation-developer-portal.png":::

     1. Teste seu aplicativo completamente antes do envio do aplicativo para garantir que ele siga as políticas da loja. Faça o sideload do aplicativo no Teams e teste os fluxos de usuário de ponta a ponta para o seu aplicativo. Verifique se a funcionalidade funciona conforme o esperado, se os links não estão quebrados, se a experiência do usuário não está bloqueada e se há limitações claramente realçadas.

     1. Teste seu aplicativo na área de trabalho, na Web e em clientes móveis. Verifique se o aplicativo está respondendo entre diferentes fatores forma.
  
  1. Conclua a [verificação do editor](/azure/active-directory/develop/publisher-verification-overview) antes de enviar seu aplicativo. Se você tiver algum problema, poderá criar um [tíquete de suporte](/azure/marketplace/partner-center-portal/support) para resolução.

  1. Ao se preparar para o envio do aplicativo, [siga a lista de verificação](/microsoftteams/platform/concepts/deploy-and-publish/appsource/prepare/submission-checklist) e inclua os seguintes detalhes como parte do pacote de envio:

        1. Pacote do aplicativo verificado por completo.

        1. Credenciais de usuário administrador e não administrador em funcionamento para testar a funcionalidade do seu aplicativo (se seu aplicativo oferecer um modelo de assinatura premium).

        1. Instruções de teste detalhando a funcionalidade do aplicativo e os cenários com suporte.

        1. Instruções de configuração se seu aplicativo precisar de mais configurações para acessar a funcionalidade do aplicativo. Como alternativa, se seu aplicativo exigir configuração complexa, você também poderá fornecer um [locatário de demonstração provisionado](/office/developer-program/microsoft-365-developer-program-get-started) com acesso de administrador para que nossos validadores possam pular as etapas de configuração.

        1. Link para um vídeo de demonstração que demonstra o fluxo de usuário principal para seu aplicativo. Isso é altamente recomendado.

* **Postar envio de aplicativo**

  * Depois de examinar o relatório de validação, responda ao thread de email com todas as consultas relacionadas ao relatório de validação ou se precisar de suporte adicional para resolver os problemas relatados.

  * Certifique-se de ter largura de banda adequada para o desenvolvedor para resolver quaisquer problemas relatados até que o aplicativo seja aprovado.

  * Certifique-se de ter resolvido [todos os problemas relatados](/microsoftteams/platform/concepts/deploy-and-publish/appsource/resolve-submission-issues) a você pelo serviço de concierge [teamsubm@microsoft.com](mailto:teamsubm@microsoft.com) antes de compartilhar seu pacote de aplicativos para testes adicionais. Isso ajuda a reduzir o número de iterações necessárias para validar seu aplicativo e, portanto, o tempo necessário para aprová-lo.
  
  * Evite alterar a funcionalidade do aplicativo durante o processo de validação, o que pode levar à descoberta de novos problemas e aumentar o tempo necessário para aprovar o aplicativo.

## <a name="additional-tips-for-rapid-approval-to-publish-your-app-linked-to-a-saas-offer"></a>Dicas adicionais para aprovação rápida ao publicar seu aplicativo vinculado a uma oferta de SaaS

* **Durante a fase de projeto**

  Leia as diretrizes de [validação da loja específicas para aplicativos publicados vinculadas a ofertas de SaaS](~/concepts/deploy-and-publish/appsource/prepare/teams-store-validation-guidelines.md#apps-linked-to-saas-offer) no início do ciclo de vida do aplicativo (fase de design), para garantir que seu aplicativo seja desenvolvido de acordo com os requisitos da loja e com as [políticas do Marketplace Comercial da Microsoft aplicáveis aos aplicativos do Teams vinculados a ofertas de SaaS](/legal/marketplace/certification-policies#11405-teams-app-linked-to-software-as-a-service-saas-offers). Se você criar seu aplicativo de acordo com estas diretrizes, então ele evitará qualquer retrabalho devido à não adesão às políticas de armazenamento.

* **Antes do envio de aplicativo**

  1. Ao se preparar para o envio do aplicativo, verifique:

      1. Se o seu aplicativo está vinculado a uma oferta de SaaS ativa (já publicada) no AppSource com pelo menos um plano contendo informações de preços.

      1. Você mencionou corretamente os `subscriptionOffer`detalhes no seu manifesto do aplicativo no formato`publisherId.offerId`.

      1. Você deve garantir que o seu plano de SaaS vinculado seja projetado para oferecer suporte a licenças atribuídas em um [modelo de preços de SaaS](/azure/marketplace/create-new-saas-offer-plans).

      1. Inclua instruções de teste ou de configuração, ou o link para um vídeo de demonstração detalhando a funcionalidade do aplicativo e as situações com suporte, além de quaisquer informações adicionais para permitir que nossos testadores entendam facilmente os fluxos de trabalho no portal de SaaS.

  1. Você deve [autotestar](~/concepts/deploy-and-publish/appsource/prepare/test-preview-for-monetized-apps.md) minuciosamente os fluxos de trabalho de gerenciamento de licenças e compras de ponta a ponta antes de enviar seu aplicativo vinculado a uma oferta de SaaS para validação, certificando-se de que:

     1. Tanto usuários administradores e não administradores possam fazer um pedido e confirmar a compra da uma assinatura. Os compradores possam navegar até a página inicial do aplicativo de SaaS selecionando **Configurar Agora** no Centro de Administração da Microsoft. Teste e se certifique, ainda, que seus compradores possam ativar e configurar a respectiva assinatura em seu aplicativo de SaaS. As mensagens no seu aplicativo de SaaS devem fornecer informações claras e suficientes sobre o caminho que um comprador deve seguir.

     1. A seção **Gerenciar Assinaturas** no Centro de Administração da Microsoft mostra os detalhes corretos das assinaturas adicionadas pelos usuários de teste. O status da assinatura, o número de licenças e outros detalhes devem ser precisos.

     1. A compra e a remoção de fluxos de trabalho de licenças devem estar funcionando conforme o esperado. Verifique se os compradores conseguem aumentar o número de licenças a partir do Centro de Administração da Microsoft. Certifique-se de que o número de licenças e atribuições do seu aplicativo de SaaS reflitam as respectivas licenças e os destinatários corretos. Além disso, certifique-se de que o aplicativo de SaaS forneça uma maneira de cancelar a licença de um usuário. Após o cancelamento de uma licença, certifique-se de que o número de licenças e atribuições restantes permaneçam intactos no seu aplicativo de SaaS e que os detalhes corretos estejam refletidos no Centro de Administração da Microsoft.

     1. O cancelamento da assinatura deve estar funcionando conforme o esperado. Os compradores devem ser capazes de cancelar uma assinatura. Após o cancelamento, verifique se o status correto da assinatura está refletido no Centro de Administração da Microsoft e no aplicativo de SaaS. Verifique se o comprador perdeu o acesso à assinatura após um cancelamento bem-sucedido.

     1. A recompra de uma assinatura é perfeita. Após o cancelamento de uma assinatura ativa, teste o aplicativo minuciosamente para garantir que os compradores possam comprar a assinatura novamente.

     1. Os compradores devem ser capazes de alterar o plano que assinaram. Após o plano ter sido alterado, os usuários devem poder acessar os recursos do plano incluídos no upgrade ou downgrade.

     1. Seu aplicativo de SaaS deve conter recursos de gerenciamento de licenças. Os compradores devem ser capazes de atribuir, modificar e reatribuir licenças disponíveis aos usuários. Verifique se os compradores podem adicionar ou remover usuários para gerenciar as licenças.
  
  1. Você precisa testar e garantir que tanto os fluxos de compra mínima quanto em massa estejam funcionando conforme o esperado.
  
  1. Você deve garantir que os usuários com licenças atribuídas tenham acesso exatamente aos recursos do plano comprado, conforme descritos na listagem do plano.

## <a name="see-also"></a>Confira também

* [Publicando nas lojas de aplicativos do Microsoft 365](/office/dev/store/)
* [Carregue seu aplicativo Teams](~/concepts/deploy-and-publish/apps-upload.md)
* [Publicar seu aplicativo Teams em sua organização](/MicrosoftTeams/tenant-apps-catalog-teams?toc=/microsoftteams/platform/toc.json&bc=/MicrosoftTeams/breadcrumb/toc.json)
* [Planejar a experiência de integração para os usuários](../../design/planning-checklist.md#plan-beyond-app-building)
* [Distribuindo aplicativos de guia no celular](../../../tabs/design/tabs-mobile.md#distribution)
* [Teste de visualização para aplicativos monetizados](prepare/Test-preview-for-monetized-apps.md)
* [Parâmetros de classificação da loja do Microsoft Teams](post-publish/teams-store-ranking-parameters.md)
