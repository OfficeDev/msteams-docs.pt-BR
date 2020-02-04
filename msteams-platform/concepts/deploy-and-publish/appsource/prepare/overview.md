---
title: Lista de verificação de envio
description: A lista de verificação a ser usada antes de publicar seu aplicativo do Microsoft Teams no AppSource
keywords: Teams Publish Store publicação Office Publishing Checklist de envio
ms.openlocfilehash: b79e92b5cf8de01ec19c26c63814c6a6ae1e9a09
ms.sourcegitcommit: 4329a94918263c85d6c65ff401f571556b80307b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/01/2020
ms.locfileid: "41672535"
---
# <a name="prepare-for-appsource-submission"></a>Preparar para envio do AppSource  

Para ser listado no AppSource, seu aplicativo deve passar por um processo de aprovação. Este é um serviço gratuito fornecido pelo grupo Microsoft Teams que verifica se seu aplicativo funciona conforme descrito, contém todos os metadados apropriados e fornece conteúdo que seria valioso para um usuário final. Para ajudá-lo a obter uma aprovação rápida, certifique-se de que seu aplicativo atenda aos seguintes requisitos e diretrizes:

* **Método de distribuição:** Certifique-se de que seu aplicativo seja destinado a uma loja. Há [outras opções](../../overview.md) para distribuir o aplicativo sem publicar no AppSource.
* **Página de detalhes do aplicativo:** O aplicativo atende à [lista de verificação de página de detalhes do aplicativo](detail-page-checklist.md)
* **Dicas e casos com falhas freqüentes:** Preste atenção adicional a essas [dicas e casos com falhas freqüentes](frequently-failed-cases.md) para aprimorar o envio de aplicativos para o tempo de aprovação.
* **Manifesto do aplicativo:** Verificar o manifesto do aplicativo em relação à [lista de verificação de manifesto do aplicativo](app-manifest-checklist.md) e ao verificador de manifesto no app Studio
* **Teste e depuração:** Você [testou e depurava completamente o aplicativo](../../../build-and-test/debug.md).
* **Políticas de validação:** Ele deve passar todas as [políticas de validação do AppSource](https://dev.office.com/officestore/docs/validation-policies) atual para os bots e guias do Microsoft Teams. Observe que essas políticas estão sujeitas a alterações.
* **Notas de teste:** Incluir [notas de teste para validação](#test-notes-for-validation)
* **Políticas de privacidade:** Verifique se a [política de privacidade, os termos de uso e URLs de suporte](#privacy-policy-terms-of-use-and-support-urls) seguem nossas diretrizes.

Depois de concluir todos os requisitos acima, você pode enviar seu pacote para a origem do aplicativo por meio do [Partner Center](/office/dev/store/use-partner-center-to-submit-to-appsource).

## <a name="privacy-policy-terms-of-use-and-support-urls"></a>Política de privacidade, termos de uso e URLs de suporte

### <a name="privacy-policy"></a>Política de privacidade

Diretrizes de política de privacidade:
* A política de privacidade pode ser específica ao seu aplicativo e/ou suplemento ou a uma política geral para todos os seus serviços. 
* Se você usar uma política de privacidade genérica, ela deverá fazer referência a "serviços/aplicativos/plataformas" para abranger o aplicativo do Microsoft Teams, bem como seu site. 
* Ele deve incluir como lidar com o armazenamento de dados do usuário, a retenção de dados do usuário, a exclusão e as informações de controles de segurança.
* Deve incluir suas informações de contato.
* Ele não deve conter links desfeitos, URLs beta ou URLs de preparo. 


### <a name="terms-of-use"></a>Termos de uso

A instrução de termos de uso deve ser específica e aplicável à oferta de seu aplicativo e/ou suplemento.

### <a name="support-urls"></a>URLs de suporte

Suas URLs de suporte não devem exigir autenticação ou credencial de logon para entrar em contato com você para qualquer problema com seu aplicativo.

## <a name="test-notes-for-validation"></a>Observações de teste para validação

Você deve fornecer pelo menos duas credenciais de logon, um administrador e outra, para que o aplicativo possa ser validado.

* As contas fornecidas devem ter dados suficientes previamente preenchidos para fins de verificação.
* Para aplicativos corporativos, aplicativos onde uma assinatura é necessária, ou onde há uma dependência de locatário/domínio do Office 365 para teste, você deve fornecer uma conta de 3ª no mesmo domínio que ainda não esteja configurada para usar seu aplicativo, para que possamos validar a experiência do usuário de primeira execução.
* Se seu aplicativo tiver recursos premium/atualizados, uma conta com o acesso necessário deverá ser fornecida para testar essa experiência.
* Você pode optar por carregar suas notas de teste no SharePoint. Nesses casos, forneça um link público para o arquivo.
