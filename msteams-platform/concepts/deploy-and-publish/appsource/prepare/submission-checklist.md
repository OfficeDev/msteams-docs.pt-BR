---
title: Lista de verificação de envio
description: A lista de verificação a ser usada antes de publicar seu aplicativo do Microsoft Teams no AppSource
keywords: Teams Publish Store publicação Office Publishing Checklist de envio
ms.openlocfilehash: 86217cef542cc3f3a09e0dc64e429a675011a0c1
ms.sourcegitcommit: 7a2da3b65246a125d441a971e7e6a6418355adbe
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/07/2020
ms.locfileid: "46587745"
---
# <a name="prepare-for-appsource-submission"></a>Preparar para envio do AppSource  

Para ser listado no AppSource, seu aplicativo deve passar por um processo de aprovação. Este é um serviço gratuito fornecido pelo grupo Microsoft Teams que verifica se seu aplicativo funciona conforme descrito, contém todos os metadados apropriados e fornece conteúdo que seria valioso para um usuário final. Para ajudá-lo a obter uma aprovação rápida, certifique-se de que seu aplicativo atenda aos seguintes requisitos e diretrizes:

* **Método de distribuição:** Certifique-se de que seu aplicativo destina-se à publicação em uma plataforma de armazenamento. Há [outras opções](../../overview.md) para distribuir o aplicativo sem publicar no AppSource.
* **Políticas de validação:** Seu aplicativo deve passar por todas as [políticas de validação do AppSource](https://docs.microsoft.com/legal/marketplace/certification-policies#1140-teams)atual. Verifique seu aplicativo na [ferramenta de validação](#teams-app-validation-tool) antes do envio. Observe que essas políticas estão sujeitas a alterações.
* **Página de detalhes do aplicativo:** Seu aplicativo deve alinhar com a [lista de verificação de página de detalhes do aplicativo](detail-page-checklist.md).
* **Dicas e casos com falhas freqüentes:** Preste atenção especial às dicas listadas [e às ocorrências com falhas freqüentes](frequently-failed-cases.md) para aprimorar o envio de aplicativos e o tempo de aprovação.
* **Manifesto do aplicativo:** Verifique o manifesto do aplicativo na [lista de verificação do manifesto do aplicativo](app-manifest-checklist.md).
* **Teste e depuração:** Certifique-se de que você tenha [testado e depurado o aplicativo](../../../build-and-test/debug.md)completamente.
* **Notas de teste:** Incluir suas [notas de teste para validação](#test-notes-for-validation)
* **Políticas de privacidade:** Verifique se a [política de privacidade, os termos de uso e URLs de suporte](#privacy-policy-terms-of-use-and-support-urls) seguem nossas diretrizes.

Após concluir todos os requisitos acima, envie seu pacote para o AppSource por meio do [Partner Center](/office/dev/store/use-partner-center-to-submit-to-appsource).

## <a name="teams-app-validation-tool"></a>Ferramenta de validação de aplicativos do teams

A ferramenta de validação de aplicativos consiste em um [validador de aplicativos](#teams-app-validator) e uma [lista de verificação preliminar](#preliminary-checklist). A ferramenta replica os mesmos casos de teste usados pelo [AppSource](/office/dev/store/submit-to-appsource-via-partner-center) para avaliar seu envio de aplicativo. Portanto, é crucial transmitir todos os casos de teste antes de enviar sua solução ao AppSource para aprovação. A ferramenta pode ser encontrada em várias áreas dentro da plataforma do Microsoft Teams:

> [!div class="checklist"]
>
> * [**Home Page do validador de aplicativos**](https://dev.teams.microsoft.com/appvalidation.html)
> * [**Kit de ferramentas de código do Visual Studio**](/toolkit/visual-studio-code-overview.md)
> * [**App Studio**](/concepts/build-and-test/app-studio-overview.md)

### <a name="teams-app-validator"></a>Validador de aplicativos do teams

A página **validar** permite verificar o pacote do aplicativo antes de enviá-lo para o AppSource. Basta carregar seu pacote de aplicativos e a ferramenta de validação verificará seu aplicativo em relação a todos os casos de teste relacionados ao manifesto. Para cada teste com falha, a descrição fornece um link de documentação para ajudá-lo a corrigir o erro.

![Ferramenta de validação](../../../../assets/images/validation-tool/validator.png)

### <a name="preliminary-checklist"></a>Lista de verificação preliminar

Para cenários de teste difíceis de automatizar, a lista de verificação preliminar superfícies sete dos casos de teste com falha mais comuns.

![Lista de verificação preliminar](../../../../assets/images/validation-tool/preliminary-checklist.png)

## <a name="privacy-policy-terms-of-use-and-support-urls"></a>Política de privacidade, termos de uso e URLs de suporte

### <a name="privacy-policy"></a>Política de privacidade

Diretrizes de política de privacidade:

> [!div class="checklist"]
>
> * A política de privacidade pode ser específica para seu aplicativo e/ou uma política geral para todos os seus serviços.
> * Se você usar uma política de privacidade genérica, ela deverá fazer referência a "serviços", "aplicativos" e "plataformas" para incluir o aplicativo do Microsoft Teams, bem como seu site.
> * Deve incluir como lidar com o armazenamento de dados do usuário, a retenção de dados do usuário, a exclusão e os controles de segurança.
> * Deve incluir suas informações de contato.
> * Ele não deve conter links desfeitos, URLs beta ou URLs de preparo.

### <a name="terms-of-use"></a>Termos de uso

A instrução de termos de uso deve ser específica e aplicável à oferta de seu aplicativo e/ou suplemento.

### <a name="support-urls"></a>URLs de suporte

Suas URLs de suporte não devem exigir autenticação ou credencial de logon para entrar em contato com você para qualquer problema com seu aplicativo.

## <a name="test-notes-for-validation"></a>Observações de teste para validação

Inclua o seguinte:

* Você deve fornecer pelo menos duas credenciais de logon, um administrador e um não-administrador.

* Para fins de verificação, as contas que você fornece devem ter dados previamente preenchidos.

* Para aplicativos corporativos, aplicativos onde uma assinatura é necessária ou aplicativos onde há uma dependência de locatário/domínio do Office 365, você deve fornecer uma terceira conta no mesmo domínio que não esteja pré-configurada para seu aplicativo, para que possamos validar a experiência do usuário de primeira execução.

* Se seu aplicativo tiver recursos premium/atualizados, uma conta com o acesso necessário deverá ser fornecida para testar essa experiência.

* Você pode optar por carregar suas notas de teste no SharePoint. Em caso afirmativo, forneça um link público para o arquivo.

* **Contas de teste**. Uma conta de teste será necessária se o aplicativo permitir apenas contas licenciadas ou lista negra do back-end. Além disso, se houver um escopo de chat de equipe/grupo permitido em seu aplicativo, duas contas de teste no mesmo locatário serão necessárias para validar o cenário de colaboração de equipe.

* **Etapas de integração**. Se a configuração prévia por um administrador de locatários for necessária para usar o aplicativo, inclua as etapas e/ou forneça contas de administrador e de não administração configuradas para validação. Observação: você pode se inscrever para uma assinatura do [programa de desenvolvedor do Office 365](https://developer.microsoft.com/microsoft-365/dev-program) . É *grátis* por 90 dias e será renovado continuamente, desde que você o esteja usando para a atividade de desenvolvimento.

* **Observações sobre os recursos do aplicativo no Teams**: detalhe todos os recursos que o aplicativo oferece no Teams e as etapas para testar cada recurso.

* **Vídeo mostrando a funcionalidade do aplicativo (opcional)**: você pode fornecer uma gravação de vídeo do produto para que possamos entender totalmente a funcionalidade do aplicativo.
