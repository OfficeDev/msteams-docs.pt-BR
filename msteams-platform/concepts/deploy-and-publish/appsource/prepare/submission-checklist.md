---
title: Lista de verificação de envio da Loja
description: A lista de verificação a ser usada antes de publicar seu aplicativo do Microsoft Teams no AppSource
ms.topic: reference
localization_priority: Normal
keywords: teams publish store office publishing checklist submission Teams apps appsource validation
ms.openlocfilehash: 1e7698e143d313ce46b834eada608571e3280b8a
ms.sourcegitcommit: 825abed2f8784d2bab7407ba7a4455ae17bbd28f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2021
ms.locfileid: "52020783"
---
# <a name="prepare-for-appsource-submission"></a>Preparar para envio do AppSource  

Para ser listado no AppSource, seu aplicativo deve passar por um processo de aprovação. Este é um serviço gratuito fornecido pelo grupo do Microsoft Teams que verifica se seu aplicativo funciona conforme descrito, contém todos os metadados apropriados e fornece conteúdo que seria valioso para um usuário final. Para ajudá-lo a obter aprovação rápida, certifique-se de que seu aplicativo atenda aos seguintes requisitos e diretrizes:

* **Método de distribuição:** Certifique-se de que seu aplicativo seja destinado à publicação em uma plataforma da loja. Há outras [opções para](../../overview.md) distribuir seu aplicativo sem publicar no AppSource.
* **Políticas de validação:** Seu aplicativo deve passar todas as políticas atuais de validação do [AppSource antes](https://docs.microsoft.com/legal/marketplace/certification-policies#1140-teams) do envio. 
  > [!NOTE] 
  > As políticas de validação do Appsource estão sujeitas a alterações.
* **Preparação para dispositivos móveis:** Seu aplicativo deve ser responsivo móvel. Se seu aplicativo contiver guias, eles devem seguir as diretrizes de [design](~/tabs/design/tabs-mobile.md) móvel e seu aplicativo deve estar em conformidade com nenhum requisito [de](~/concepts/deploy-and-publish/appsource/prepare/frequently-failed-cases.md#-mobile-responsiveness-no-direct-upsell-or-payment) venda em sistema operacional móvel (iOS e Android).
* **Auto teste seu aplicativo:** Teste seu aplicativo usando a [ferramenta de validação de manifesto](#teams-app-validation-tool).
* **Página de detalhes do aplicativo:** Seu aplicativo deve se alinhar à lista de verificação [de detalhes do aplicativo.](detail-page-checklist.md)
* **Dicas e casos com falha frequente:** Preste atenção extra às Dicas listadas e [frequentemente a](frequently-failed-cases.md)  casos com falha para melhorar o tempo de envio e aprovação do aplicativo.
* **Manifesto do aplicativo:** Verifique o manifesto do aplicativo na lista de verificação [de manifesto do aplicativo](app-manifest-checklist.md).
* **Teste e depuração:** Certifique-se de que você [testou totalmente e depurou seu aplicativo.](../../../build-and-test/debug.md)
* **Notas de teste:** Incluir suas [anotações de teste para validação](#test-notes-for-validation)
* **Políticas de privacidade:** Verifique se [sua política de privacidade, termos de uso e URLs de suporte](#privacy-policy-terms-of-use-and-support-urls) seguem nossas diretrizes.

Depois de concluir todos os requisitos acima, envie seu pacote para o AppSource por meio [do Partner Center](/office/dev/store/use-partner-center-to-submit-to-appsource).

## <a name="teams-app-validation-tool"></a>Ferramenta de Validação de Aplicativos do Teams

A ferramenta de validação de aplicativo consiste em um [validador de](#teams-app-validator) aplicativo e uma [lista de verificação preliminar.](#preliminary-checklist) A ferramenta replica os mesmos casos de teste usados pelo [AppSource](/office/dev/store/submit-to-appsource-via-partner-center) para avaliar o envio do aplicativo. Portanto, é fundamental passar todos os casos de teste antes de enviar sua solução ao AppSource para aprovação. A ferramenta pode ser encontrada em várias áreas dentro da plataforma teams:

> [!div class="checklist"]
>
> * [**Página inicial do Validador de Aplicativos**](https://dev.teams.microsoft.com/appvalidation.html)
> * [**Teams Visual Studio kit de ferramentas de código**](/toolkit/visual-studio-code-overview.md)
> * [**App Studio**](../../../build-and-test/app-studio-overview.md)

### <a name="teams-app-validator"></a>Validador de aplicativos do Teams

A **página Validar** permite que você verifique o pacote do aplicativo antes de ser envio para o AppSource. Basta carregar o pacote do aplicativo e a ferramenta de validação verificará seu aplicativo em relação a todos os casos de teste relacionados ao manifesto. Para cada teste com falha, a descrição fornece um link de documentação para ajudá-lo a corrigir o erro.

![Ferramenta de validação](../../../../assets/images/validation-tool/validator.png)

### <a name="preliminary-checklist"></a>Lista de verificação preliminar

Para cenários de teste difíceis de automatizar, a lista de verificação preliminar superfície sete dos casos de teste mais comumente com falha.

![Lista de verificação preliminar](../../../../assets/images/validation-tool/preliminary-checklist.png)

## <a name="privacy-policy-terms-of-use-and-support-urls"></a>Política de privacidade, termos de uso e URLs de suporte

### <a name="privacy-policy"></a>Política de privacidade

Diretrizes de política de privacidade:

> [!div class="checklist"]
>
> * A política de privacidade pode ser específica para seu aplicativo e/ou uma política geral para todos os seus serviços.
> * Se você usar uma política de privacidade genérica, ela deverá fazer referência a "serviços", "aplicativos" e "plataformas" para incluir seu aplicativo do Teams, bem como seu site.
> * Ele deve incluir como você lida com o armazenamento de dados do usuário, retenção de dados do usuário, exclusão e controles de segurança.
> * Ele deve incluir suas informações de contato.
> * Ele não deve conter links quebrados, URLs beta ou URLs de preparação.

### <a name="terms-of-use"></a>Termos de uso

Sua instrução de termos de uso deve ser específica e aplicável ao seu aplicativo e/ou oferta de complemento.

### <a name="support-urls"></a>Dar suporte a URLs

Suas URLs de suporte não devem exigir autenticação ou credencial de logon para entrar em contato com você para quaisquer problemas com seu aplicativo.

## <a name="test-notes-for-validation"></a>Notas de teste para validação

Inclua o seguinte:

* Você deve fornecer pelo menos duas credenciais de logon, um administrador e um não administrador.

* Para fins de verificação, as contas fornecidas devem ter dados pré-preenchidos suficientes.

* Para aplicativos corporativos, aplicativos em que uma assinatura é necessária ou aplicativos em que há uma dependência de locatário/domínio do Office 365, você deve fornecer uma terceira conta no mesmo domínio que não está pré-configurada para seu aplicativo para que possamos validar a experiência do usuário em primeira fase.

* Se seu aplicativo tiver recursos premium/atualizados, uma conta com o acesso necessário deve ser fornecida para testar essa experiência.

* Você pode optar por carregar suas anotações de teste no SharePoint. Em caso afirmado, forneça um link público para o arquivo.

* **Contas de teste**. Uma conta de teste será necessária se seu aplicativo permitir apenas contas licenciadas ou lista segura do back-end. Além disso, se houver um escopo de chat de equipe/grupo permitido em seu aplicativo, duas contas de teste no mesmo locatário serão necessárias para validar o cenário de colaboração de equipe.

* **Etapas de integração**. Se a pré-configuração de um administrador de locatário for necessária para usar o aplicativo, inclua as etapas e/ou forneça contas de administrador e não administrador configuradas para validação. Observação: você pode se inscrever para uma assinatura do Programa de Desenvolvedor do [Office 365.](https://developer.microsoft.com/microsoft-365/dev-program) Ele é gratuito *por* 90 dias e será continuamente renovado, desde que você esteja usando-o para atividades de desenvolvimento.

* **Observações sobre os recursos do aplicativo no Teams**: Detalhar todos os recursos que o aplicativo oferece no Teams e etapas para testar cada recurso.

* Vídeo mostrando a funcionalidade **do aplicativo (Opcional)**: Você pode fornecer uma gravação em vídeo do produto para que possamos entender totalmente a funcionalidade do aplicativo.
