---
title: Lista de verificação de envio
description: A lista de verificação a ser usada antes de publicar seu aplicativo Microsoft Teams no AppSource
keywords: teams publish store office publishing checklist submission Teams apps appsource validation
ms.openlocfilehash: 8d20d0106c1b2d8da38c5802b977634925afffcc
ms.sourcegitcommit: db19fee033b41152267bb524d67aee5b7f64b04a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/12/2021
ms.locfileid: "49797472"
---
# <a name="prepare-for-appsource-submission"></a>Preparar-se para o envio do AppSource  

Para ser listado no AppSource, seu aplicativo deve passar por um processo de aprovação. Este é um serviço gratuito fornecido pelo grupo do Microsoft Teams que verifica se seu aplicativo funciona conforme descrito, contém todos os metadados apropriados e fornece conteúdo que seria valioso para um usuário final. Para ajudá-lo a obter aprovação rápida, certifique-se de que seu aplicativo atenda aos seguintes requisitos e diretrizes:

* **Método de distribuição:** Certifique-se de que seu aplicativo foi feito para publicação em uma plataforma da loja. Há outras [opções para](../../overview.md) distribuir seu aplicativo sem publicar no AppSource.
* **Políticas de validação:** Seu aplicativo deve passar todas as políticas [de validação atuais do AppSource antes](https://docs.microsoft.com/legal/marketplace/certification-policies#1140-teams) do envio. 
  > [!NOTE] 
  > As políticas de validação do Appsource estão sujeitas a alterações.
* **Preparação para dispositivos móveis:** Seu aplicativo deve ser responsivo móvel. Se seu aplicativo contiver guias, elas deverão seguir as diretrizes de [design](~/tabs/design/tabs-mobile.md) móvel e seu aplicativo não deverá atender aos [requisitos](~/concepts/deploy-and-publish/appsource/prepare/frequently-failed-cases.md#-mobile-responsiveness-no-direct-upsell-or-payment) de venda em sistema operacional móvel (iOS e Android).
* **Teste seu aplicativo:** Teste seu aplicativo usando a ferramenta [de validação de manifesto.](#teams-app-validation-tool)
* **Página de detalhes do aplicativo:** Seu aplicativo deve se alinhar à lista [de verificação da página de detalhes do aplicativo.](detail-page-checklist.md)
* **Dicas e casos com falha frequente:** Preste atenção especial às Dicas listadas [e casos com falha frequentes](frequently-failed-cases.md)  para melhorar o envio e o tempo de aprovação do aplicativo.
* **Manifesto do aplicativo:** Verifique o manifesto do aplicativo em relação à [lista de verificação do manifesto do aplicativo.](app-manifest-checklist.md)
* **Teste e depuração:** Certifique-se de que você [testou e depurou completamente seu aplicativo.](../../../build-and-test/debug.md)
* **Notas de teste:** Incluir suas [notas de teste para validação](#test-notes-for-validation)
* **Políticas de privacidade:** [Certifique-se de que sua política de privacidade, termos de uso e URLs de suporte](#privacy-policy-terms-of-use-and-support-urls) siga nossas diretrizes.

Depois de concluir todos os requisitos acima, envie seu pacote para o AppSource por meio do [Partner Center.](/office/dev/store/use-partner-center-to-submit-to-appsource)

## <a name="teams-app-validation-tool"></a>Ferramenta de Validação de Aplicativos do Teams

A ferramenta de validação de aplicativo consiste em um [validador de aplicativo](#teams-app-validator) e uma [lista de verificação preliminar.](#preliminary-checklist) A ferramenta replica os mesmos casos de teste usados pelo [AppSource](/office/dev/store/submit-to-appsource-via-partner-center) para avaliar o envio do aplicativo. Portanto, é essencial passar em todos os casos de teste antes de enviar sua solução ao AppSource para aprovação. A ferramenta pode ser encontrada em várias áreas dentro da plataforma do Teams:

> [!div class="checklist"]
>
> * [**Home page do Validador de Aplicativo**](https://dev.teams.microsoft.com/appvalidation.html)
> * [**Kit de ferramentas do Visual Studio Code do Teams**](/toolkit/visual-studio-code-overview.md)
> * [**App Studio**](/concepts/build-and-test/app-studio-overview.md)

### <a name="teams-app-validator"></a>Validador de aplicativo do Teams

A **página Validar** permite que você verifique o pacote do aplicativo antes de ser envio para o AppSource. Basta carregar o pacote do aplicativo e a ferramenta de validação verificará seu aplicativo em relação a todos os casos de teste relacionados ao manifesto. Para cada teste com falha, a descrição fornece um link de documentação para ajudá-lo a corrigir o erro.

![Ferramenta de validação](../../../../assets/images/validation-tool/validator.png)

### <a name="preliminary-checklist"></a>Lista de verificação preliminar

Para cenários de teste difíceis de automatizar, a lista de verificação preliminar superfície sete dos casos de teste com falha mais comumente.

![Lista de verificação preliminar](../../../../assets/images/validation-tool/preliminary-checklist.png)

## <a name="privacy-policy-terms-of-use-and-support-urls"></a>Política de privacidade, termos de uso e URLs de suporte

### <a name="privacy-policy"></a>Política de privacidade

Diretrizes de política de privacidade:

> [!div class="checklist"]
>
> * A política de privacidade pode ser específica para seu aplicativo e/ou uma política geral para todos os seus serviços.
> * Se você usar uma política de privacidade genérica, ela deverá fazer referência a "serviços", "aplicativos" e "plataformas" para incluir seu aplicativo do Teams, bem como seu site.
> * Ele deve incluir como você lida com o armazenamento de dados do usuário, a retenção de dados do usuário, a exclusão e os controles de segurança.
> * Ele deve incluir suas informações de contato.
> * Ele não deve conter links quebrados, URLs beta ou URLs de preparação.

### <a name="terms-of-use"></a>Termos de uso

Sua declaração de termos de uso deve ser específica e aplicável ao seu aplicativo e/ou oferta de complemento.

### <a name="support-urls"></a>URLs de suporte

As URLs de suporte não devem exigir autenticação ou credencial de logon para entrar em contato com você em caso de problemas com seu aplicativo.

## <a name="test-notes-for-validation"></a>Notas de teste para validação

Inclua o seguinte:

* Você deve fornecer pelo menos duas credenciais de logon, um administrador e um não administrador.

* Para fins de verificação, as contas fornecidas devem ter dados pré-preenchidos suficientes.

* Para aplicativos corporativos, aplicativos em que uma assinatura é necessária ou aplicativos em que há uma dependência de locatário/domínio do Office 365, você deve fornecer uma terceira conta no mesmo domínio que não está pré-configurado para seu aplicativo para que possamos validar a experiência de usuário de primeira executar.

* Se seu aplicativo tiver recursos premium/atualizados, uma conta com o acesso necessário deverá ser fornecida para testar essa experiência.

* Você pode optar por carregar suas notas de teste no SharePoint. Se sim, forneça um link público para o arquivo.

* **Contas de teste.** Uma conta de teste será necessária se seu aplicativo permitir apenas contas licenciadas ou a lista segura do back-end. Além disso, se houver um escopo de chat de equipe/grupo permitido em seu aplicativo, duas contas de teste no mesmo locatário serão necessárias para validar o cenário de colaboração em equipe.

* **Etapas de integração.** Se a pré-configuração de um administrador de locatários for necessária para usar o aplicativo, inclua as etapas e/ou forneça contas de administrador e não administrador configuradas para validação. Observação: você pode se inscrever para uma assinatura do Programa para Desenvolvedores do [Office 365.](https://developer.microsoft.com/microsoft-365/dev-program) Ele é *gratuito por* 90 dias e será renovado continuamente, desde que você o esteja usando para atividades de desenvolvimento.

* **Observações sobre os recursos do aplicativo no Teams:** detalhe todos os recursos que o aplicativo oferece no Teams e as etapas para testar cada recurso.

* **Vídeo mostrando a funcionalidade do aplicativo (opcional)**: você pode fornecer uma gravação em vídeo do produto para entendermos totalmente a funcionalidade do aplicativo.
