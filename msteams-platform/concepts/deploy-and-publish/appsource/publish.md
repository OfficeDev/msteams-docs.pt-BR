---
title: Noções básicas sobre o processo de envio do Armazenamento do Teams
description: Descreve o processo de envio de aprovação para obter seu aplicativo publicado na loja de aplicativos do Microsoft Teams
ms.topic: overview
localization_priority: Normal
keywords: teams publish store office publishing publish AppSource partner center account verification apps account not publish eligible app submission
ms.openlocfilehash: 79584ae1eb0be24b4a66e2421f23dd694f8d610f
ms.sourcegitcommit: 825abed2f8784d2bab7407ba7a4455ae17bbd28f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2021
ms.locfileid: "52019892"
---
# <a name="submit-your-app-to-appsource"></a>Enviar seu aplicativo para AppSource

## <a name="teams-app-submission"></a>Envio de aplicativo do Teams

Disponibilizar seu aplicativo no catálogo de aplicativos do Microsoft Teams e na Web publicando-o no [AppSource](https://appsource.microsoft.com). Em um nível alto, o processo para enviar seu aplicativo ao AppSource é o seguinte:

1. Desenvolva seu aplicativo seguindo as [diretrizes de design.](~/concepts/design/understand-use-cases.md) As guias devem seguir as diretrizes de design de tabulação para desktop [e web](~/tabs/design/tabs.md) e [mobile.](~/tabs/design/tabs-mobile.md) Os bots devem seguir as diretrizes [de design de bot.](~/bots/design/bots.md)
1. Verifique se o aplicativo atende às políticas de [validação de aplicativos](/legal/marketplace/certification-policies) do Microsoft Teams. 
1. Teste seu aplicativo com a [ferramenta de validação de manifesto](prepare/submission-checklist.md#teams-app-validation-tool).
1. Configurar uma conta [de desenvolvedor](/office/dev/store/open-a-developer-account) no [Partner Center](https://support.microsoft.com/help/4499930/partner-center-overview). *Consulte também* [Como criar uma conta do Partner Center](#how-do-i-create-a-partner-center-account) na seção Perguntas frequentes.
1. Prepare seu aplicativo para envio seguindo a lista [de verificação de envio.](prepare/submission-checklist.md)
1. Revise os [casos de teste com mais falhas para uma aprovação de qualidade de aplicativo](prepare/frequently-failed-cases.md)mais rápida.
1. Envie seu pacote para [AppSource por meio do Partner Center](/office/dev/store/use-partner-center-to-submit-to-appsource).
1. Acompanhe o processo de aprovação no painel do Partner Center. *Consulte Visão* [geral do Partner Center](https://support.microsoft.com/help/4499930/partner-center-overview).
1. Após o envio, revise as diretrizes para [Manter e dar suporte ao seu aplicativo publicado.](post-publish/overview.md)

>[!NOTE]
>
>- Seu aplicativo do Teams deve ser responsivo para dispositivos móveis e estar em conformidade com nenhum requisito [de upsell](~/concepts/deploy-and-publish/appsource/prepare/frequently-failed-cases.md#-mobile-responsiveness-no-direct-upsell-or-payment) no sistema operacional móvel (iOS e Android). 
>- Se o aplicativo do Teams contiver um bot, você deverá estar em conformidade com o Código de Conduta da Estrutura do [Desenvolvedor do](https://aka.ms/bf-conduct)Bot.
>- Se seu aplicativo contiver um Conector do Office 365, outros termos poderão ser aplicados. Consulte [Connectors Developer Dashboard](https://aka.ms/connectorsdashboard) and App Developer [Agreement](https://sellerdashboard.microsoft.com/Assets/Content/Agreements/Office_Store_Seller_Agreement_20120927.htm).
>- Para disponibilizar seu aplicativo para usuários do GCC (Government Community Cloud) e evitar listagens de aplicativos duplicadas na loja, o processo de autenticação ou fluxo deve identificar e encaminhar o usuário para a URL de conteúdo especificada ou esperada para usuários GCC.

## <a name="faqs--teams-apps-and-partner-account-verification-process-in-partner-center"></a>Perguntas frequentes — Aplicativos do Teams e processo de verificação de conta de parceiro no Partner Center

## <a name="how-do-i-create-a-partner-center-account"></a>Como criar uma conta do Partner Center?

Há duas maneiras de criar uma conta do Partner Center:

- Se você for novo no Partner Center e não tiver uma conta na rede da Microsoft, crie uma conta usando a página de registro [do Partner Center](/office/dev/store/open-a-developer-account#create-an-account-using-an-existing-partner-center-enrollment).
- Se você já estiver inscrito na Rede de Parceiros, crie uma conta diretamente no Partner Center usando uma [página de registro existente.](/office/dev/store/)

## <a name="what-if-i-cannot-find-my-office-store-account-in-partner-center"></a>E se eu não conseguir encontrar minha conta da Office Store no Partner Center?

Abra um [tíquete de](https://partner.microsoft.com/support/v2/?stage=1) suporte do Partner Center e selecione o seguinte nos menus suspensos:

| Menu | Opção |
| -------   | -------  |
|Categoria| Marketplace Comercial|
| Tópico | Perguntas gerais sobre Ajuda do Marketplace e Como fazer perguntas |
| Subtópico| Suplemento do Office |

## <a name="where-can-i-get-support-for-my-partner-center-account-issues"></a>Onde posso obter suporte para problemas de conta do Partner Center?

Visite a [página de suporte de editores](https://aka.ms/marketplacepublishersupport) para pesquisar seu tópico de problema e encontrar orientações. Se as orientações fornecidas não são úteis, aduza um tíquete de suporte [do Partner Center](/azure/marketplace/partner-center-portal/support#how-to-open-a-support-ticket).

## <a name="how-do-i-manage-my-office-store-account-in-partner-center"></a>Como gerenciar minha conta da Office Store no Partner Center?

Visite a [conta Gerenciar sua Office Store por meio do Partner Center](/office/dev/store/manage-account-settings-and-profile) para obter orientações.

## <a name="how-do-i-add-my-phone-number-to-the-partner-profile-contact-section"></a>Como adicionar meu número de telefone à seção de contato de perfil de parceiro?

O número de telefone tem três partes, código de país, código de área e número de telefone. Se o número de telefone não incluir um código de área, deixe a segunda caixa vazia e conclua a terceira caixa.

## <a name="how-do-i-manage-my-account-settings-and-partner-profile-in-partner-center"></a>Como gerencie minhas configurações de conta e perfil de parceiro no Partner Center?

Visite a [página Gerenciar configurações de conta](/windows/uwp/publish/manage-account-settings-and-profile#additional-settings-and-info) e informações de perfil para obter orientações sobre como gerenciar as configurações da conta do Partner Center.

## <a name="why-do-i-receive-the-message-this-account-is-not-publish-eligible-when-i-try-to-submit-my-add-in-through-partner-center"></a>Por que recebo a mensagem"Essa conta não é qualificada para publicar", quando tento enviar meu complemento por meio do Partner Center?

Você recebe a mensagem de erro acima quando o [status de](/partner-center/verification-responses) verificação da conta está pendente. Verifique o status de verificação da sua conta no painel do Partner [Center.](https://partner.microsoft.com/dashboard) Selecione **Configurações**, o ícone de engrenagem no canto superior direito do shell do header da página. Escolha **Configurações do desenvolvedor**  =>  **Configurações** da conta De   =>  **conta**.

![Página de configurações da conta do Partner Center](../../../assets/images/partner-center-accts-page.png)

![Status de verificação do Partner Center](../../../assets/images/partner-center-verification-status.png)

O status de cada etapa necessária, como Propriedade de **Email,** Verificação de **Emprego** e Verificação de **Negócios,** são exibidos no processo de verificação da conta. Após a conclusão do processo de verificação, o status de verificação do seu registro na página de perfil muda *de pendente* para *autorizado*. As etapas do processo não são mais exibidas.

![Erro de verificação do Partner Center](../../../assets/images/partner-center-acct-verification-error.png)

## <a name="what-is-verified-in-the-partner-center-account-verification-process-and-how-to-respond"></a>O que é verificado no processo de verificação de conta do Partner Center e como responder?
Há três áreas de verificação, **Propriedade de Email,** **Emprego** e **Negócios.** Para obter mais informações sobre o processo de verificação, consulte [O que é verificado e como responder](/partner-center/verification-responses#what-is-verified-and-how-to-respond).
Se você for o contato principal, administrador global ou administrador de conta, vá até seu Perfil de Parceiro para monitorar o status de verificação e acompanhar o progresso.

Após a conclusão do processo de verificação, o status de verificação do seu registro na página de perfil muda *de pendente* para *autorizado*. Após a autorização, as etapas do processo e seu status não estão mais disponíveis na página. O contato principal recebe um email da Microsoft dentro de alguns dias úteis após a conclusão da verificação.

## <a name="my-account-verification-status-has-not-advanced-beyond-email-ownership-in-the-partner-center-how-should-i-proceed"></a>O status de Verificação de Minha Conta não avançou além da Propriedade de Email no Partner Center. Como devo continuar?

Durante o **processo de verificação de Propriedade de** Email, um email de verificação é enviado para o endereço de email de contato principal. Verifique sua caixa de entrada de contato principal para um email maccount@ **<span>microsoft</span>.com com** a linha de assunto *Ação necessária: Verificar* sua conta de email com a Microsoft . Conclua o processo de verificação de email. O email de verificação é enviado para o endereço de email listado na página de configurações da sua conta no Partner Center.

> [!NOTE]
> * O link de verificação de email só é válido por sete dias. 
> * Você pode solicitar que enviemos o email de novo visitando a página de perfil do parceiro e selecionando o link **Resend verification email.**
> * Para garantir que o email seja recebido, liste com segurança o email do microsoft.com como um domínio seguro e verifique suas pastas de lixo eletrônico.

## <a name="how-do-i-get-further-support-for-my-account-related-issues"></a>Como obter mais suporte para problemas relacionados à minha conta?

Visite a [página Suporte para o programa do Marketplace](/azure/marketplace/partner-center-portal/support) Comercial no Partner Center para obter orientações e etapas para criar um tíquete de suporte.

## <a name="ive-checked-my-mail-folders-and-havent-received-the-verification-email-what-must-i-do-next"></a>Eu chequei minhas pastas de email e não recebi o email de verificação. O que devo fazer em seguida?

Tente o seguinte:
* Verifique sua pasta de lixo eletrônico ou spam.
* Limpe o cache do navegador, vá para o painel da conta do Partner Center e selecione o **link** Enviar email de verificação de resendê-lo para que o email de verificação se ressente ao seu endereço de email.
* Tente acessar o **link Enviar novamente** o email de verificação de um navegador diferente.
* Trabalhe com seu departamento de IT para garantir que os emails de verificação não sejam bloqueados pelo servidor de email.
* Ajuste o filtro de spam do servidor para permitir ou listar todos os emails de **maccount@microsoft. <span></span> com**.

## <a name="how-long-does-the-employment-verification-process-usually-take"></a>Quanto tempo o processo de verificação de emprego geralmente leva?

Se todos os detalhes enviados estão corretos, o processo de verificação de emprego leva cerca de duas horas para ser concluído.

## <a name="how-long-does-the-business-verification-process-usually-take"></a>Quanto tempo o processo de verificação comercial geralmente leva?

Se todos os documentos necessários são enviados, a verificação de negócios leva de um a dois dias úteis para ser concluída.

## <a name="if-i-reach-out-to-the-support-team-will-my-ticket-be-expedited"></a>Se eu falar com a equipe de suporte, meu tíquete será expedido?

Os tíquetes de suporte são resolvidos em uma semana. Verifique se há atualizações enviadas para a ID de email fornecida ao levantar o tíquete de suporte.

## <a name="my-issue-is-not-listed-here-are-there-other-pages-i-can-reference-for-partner-center-issues"></a>Meu problema não está listado aqui. Há outras páginas que posso fazer referência a problemas do Partner Center?

Consulte a [documentação do marketplace comercial](/azure/marketplace/) para obter mais ajuda.

## <a name="ive-created-a-support-ticket-it-has-been-7-business-days-and-i-havent-received-an-update-where-can-i-get-additional-help"></a>Criei um tíquete de suporte, foram sete dias úteis e ainda não recebi uma atualização. Onde posso obter ajuda adicional?

Envie um email **<teamsubm@microsoft.com>** para com os seguintes detalhes:

* **Linha de Assunto**: Problema de conta do Partner Center para <App_Name> (especifique o nome do seu aplicativo).
* **Corpo do email**:
    * Número do tíquete de suporte
    * Sua ID do vendedor
    * Uma captura de tela do problema (se possível)
    
## <a name="app-category-mapping"></a>Mapeamento de categorias de aplicativo

| Categoria do Teams       | Categorias de computador  |
|:---------------------|:---------------|
| Análise e BI | Análise, Visualização de Dados e BI |
| Desenvolvedor e IT | Ferramentas de Desenvolvedor, Administrador de IT |
| Educação | Educação |
| Recursos humanos | Recursos Humanos e Recrutamento |
| Produtividade | Gerenciamento de Conteúdo, Arquivos e documentos, Produtividade, Treinamento e Tutoriais e Utilitários |
| Gerenciamento de projeto | Comunicação, Gerenciamento de Projetos, Fluxo de Trabalho e Gerenciamento de Negócios |
| Vendas e suporte | Gerenciamento de Clientes e Contatos, Suporte ao Cliente, Gerenciamento Financeiro, Vendas e Marketing |
| Social e divertido | Galerias de imagem e vídeo, estilo de vida, notícias e clima, social, viagem e navegação |

>
> [!div class="nextstepaction"]
> [Saiba mais sobre políticas de validação de aplicativos para o Microsoft Teams](/legal/marketplace/certification-policies)
