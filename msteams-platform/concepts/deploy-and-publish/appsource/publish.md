---
title: Noções básicas sobre o processo de envio da loja do Teams
description: Descreve o processo de envio de aprovação para publicar seu aplicativo na loja de aplicativos do Microsoft Teams
ms.topic: overview
keywords: teams publish store office publishing publish AppSource partner center account verification apps account not publish eligible app submission
ms.openlocfilehash: d2dc624c6dd13896397041c5c69ce5c5eb471a5b
ms.sourcegitcommit: 976e870cc925f61b76c3830ec04ba6e4bdfde32f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/27/2021
ms.locfileid: "50014408"
---
# <a name="submit-your-app-to-appsource"></a>Enviar seu aplicativo para o AppSource

## <a name="teams-app-submission"></a>Envio de aplicativo do Teams

Disponibilizar seu aplicativo no catálogo de aplicativos do Microsoft Teams e na Web publicando-o no [AppSource.](https://appsource.microsoft.com) Em um nível alto, o processo para enviar seu aplicativo ao AppSource é o seguinte:

1. Desenvolva seu aplicativo seguindo as [diretrizes de design.](~/concepts/design/understand-use-cases.md) As guias devem seguir as diretrizes de design de guia para área [de trabalho](~/tabs/design/tabs.md) e web e [dispositivos móveis.](~/tabs/design/tabs-mobile.md) Os bots devem seguir as [diretrizes de design de bot.](~/bots/design/bots.md)
1. Certifique-se de que seu aplicativo atenda às políticas [de validação do](/legal/marketplace/certification-policies) aplicativo para o Microsoft Teams. 
1. Teste seu aplicativo com a ferramenta [de validação de manifesto.](prepare/submission-checklist.md#teams-app-validation-tool)
1. Configurar uma conta [de desenvolvedor](/office/dev/store/open-a-developer-account) no [Partner Center.](https://support.microsoft.com/help/4499930/partner-center-overview) *Consulte também* [Como criar uma conta do Partner Center](#how-do-i-create-a-partner-center-account) na seção perguntas frequentes.
1. Prepare seu aplicativo para envio seguindo a lista de [verificação de envio.](prepare/submission-checklist.md)
1. Revise os [casos de teste com mais falhas para uma aprovação de qualidade do aplicativo mais rápida.](prepare/frequently-failed-cases.md)
1. Envie seu pacote para [o AppSource por meio do Partner Center.](/office/dev/store/use-partner-center-to-submit-to-appsource)
1. Acompanhe o processo de aprovação no painel do Partner Center. *Consulte Visão* [geral do Partner Center.](https://support.microsoft.com/help/4499930/partner-center-overview)
1. Após o envio, revise as diretrizes para [manter e dar suporte ao seu aplicativo publicado.](post-publish/overview.md)

>[!NOTE]
>
>- Seu aplicativo teams deve ser responsivo para dispositivos móveis e estar em conformidade com nenhum requisito [de](~/concepts/deploy-and-publish/appsource/prepare/frequently-failed-cases.md#-mobile-responsiveness-no-direct-upsell-or-payment) venda em sistema operacional móvel (iOS e Android). 
>- Se seu aplicativo Teams contiver um bot, você deverá estar em conformidade com o Código de Conduta da Estrutura [do Desenvolvedor de Bot.](https://aka.ms/bf-conduct)
>- Se seu aplicativo contiver um Conector do Office 365, termos adicionais poderão ser aplicados. Consulte [o Painel do Desenvolvedor de Conectores](https://aka.ms/connectorsdashboard) e o Contrato de Desenvolvedor de [Aplicativos.](https://sellerdashboard.microsoft.com/Assets/Content/Agreements/Office_Store_Seller_Agreement_20120927.htm)
>- Para disponibilizar seu aplicativo para usuários do Government Community Cloud (GCC) e evitar listagens de aplicativos duplicadas na loja, o processo ou fluxo de autenticação deve identificar e rotear o usuário para a URL de conteúdo especificada ou esperada para usuários GCC.

## <a name="faqs--teams-apps-and-partner-account-verification-process-in-partner-center"></a>Perguntas frequentes — Aplicativos do Teams e processo de verificação de conta de parceiro no Partner Center

## <a name="how-do-i-create-a-partner-center-account"></a>Como criar uma conta do Partner Center?

Há duas maneiras de criar uma conta do Partner Center:

- Se você for novo no Partner Center e não tiver uma conta na rede da Microsoft, crie uma conta usando a página de registro [do Partner Center.](/office/dev/store/open-a-developer-account#create-an-account-using-an-existing-partner-center-enrollment)
- Se você já estiver inscrito no Partner Network, crie uma conta diretamente no Partner Center usando uma [página de registro existente.](/office/dev/store/)

## <a name="what-if-i-cannot-find-my-office-store-account-in-partner-center"></a>E se eu não encontrar minha conta da Office Store no Partner Center?

Abra um [tíquete de suporte do Partner Center](https://partner.microsoft.com/support/v2/?stage=1) e selecione o seguinte nos menus suspensos:

| Menu | Opção |
| -------   | -------  |
|Categoria| Marketplace Comercial|
| Tópico | General Marketplace Help and How-to questions |
| Subtópico| Suplemento do Office |

## <a name="where-can-i-get-support-for-my-partner-center-account-issues"></a>Onde posso obter suporte para meus problemas de conta do Partner Center?

Visite a [página de suporte de editores](https://aka.ms/marketplacepublishersupport) para pesquisar o tópico do problema e encontrar orientações. Se as orientações fornecidas não são úteis, eleva um tíquete [de suporte do Partner Center.](/azure/marketplace/partner-center-portal/support#how-to-open-a-support-ticket)

## <a name="how-do-i-manage-my-office-store-account-in-partner-center"></a>Como faço para gerenciar minha conta da Office Store no Partner Center?

Visite a [conta Gerenciar a Office Store por meio do Partner Center](/office/dev/store/manage-account-settings-and-profile) para obter orientação.

## <a name="how-do-i-add-my-phone-number-to-the-partner-profile-contact-section"></a>Como adicionar meu número de telefone à seção de contato do perfil de parceiro?

O número de telefone tem três partes, código de país, código de área e número de telefone. Se o número de telefone não incluir um código de área, deixe a segunda caixa vazia e preencha a terceira caixa.

## <a name="how-do-i-manage-my-account-settings-and-partner-profile-in-partner-center"></a>Como faço para gerenciar minhas configurações de conta e perfil de parceiro no Partner Center?

Visite a [página Gerenciar configurações de conta e informações de](/windows/uwp/publish/manage-account-settings-and-profile#additional-settings-and-info) perfil para obter orientação sobre como gerenciar suas configurações de conta do Partner Center.

## <a name="why-do-i-receive-the-message-this-account-is-not-publish-eligible-when-i-try-to-submit-my-add-in-through-partner-center"></a>Por que eu recebo a mensagem "Esta conta não é qualificada para publicação", quando tento enviar meu complemento por meio do Partner Center?

Você recebe a mensagem de erro acima quando o [status de verificação da conta](/partner-center/verification-responses) está pendente. Verifique o status de verificação da sua conta no painel  [do](https://partner.microsoft.com/dashboard)Partner Center. Select **Settings**, the gear icon in the upper-right corner of the page header shell. Escolha **Configurações de desenvolvedor**  =>  **Configurações da** conta de   =>  **conta.**

![Página de configurações da conta do Partner Center](../../../assets/images/partner-center-accts-page.png)

![Status de verificação do Partner Center](../../../assets/images/partner-center-verification-status.png)

O status de cada etapa necessária, como Propriedade do **Email,** Verificação de Emprego e Verificação de **Negócios,** são exibidos no processo de verificação da conta. Após a conclusão do processo de verificação, o status de verificação do registro na página de perfil muda de *pendente* para *autorizado.* As etapas do processo não são mais exibidas.

![Erro de verificação do Partner Center](../../../assets/images/partner-center-acct-verification-error.png)

## <a name="what-is-verified-in-the-partner-center-account-verification-process-and-how-to-respond"></a>O que é verificado no processo de verificação de conta do Partner Center e como responder?
Há três áreas de verificação, **Propriedade de Email**, **Emprego** e **Negócios.** Para obter mais informações sobre o processo de verificação, consulte [O que é verificado e como responder.](/partner-center/verification-responses#what-is-verified-and-how-to-respond)
Se você for o contato principal, administrador global ou administrador de conta, vá para seu Perfil de Parceiro para monitorar o status da verificação e acompanhar o progresso.

Após a conclusão do processo de verificação, o status de verificação do registro na página de perfil muda de *pendente* para *autorizado.* Após a autorização, as etapas do processo e seu status não estarão mais disponíveis na página. O contato principal recebe um email da Microsoft dentro de alguns dias úteis após a conclusão da verificação.

## <a name="my-account-verification-status-has-not-advanced-beyond-email-ownership-in-the-partner-center-how-should-i-proceed"></a>O status de verificação da minha conta não avançou além da Propriedade de Email no Partner Center. Como devo prosseguir?

Durante o **processo de verificação de propriedade** de email, um email de verificação é enviado para o endereço de email principal do contato. Verifique sua caixa de entrada de contato principal para ver um email da **maccount@<span>microsoft.com</span>com** a linha de assunto Ação necessária: verifique sua conta de *email com a Microsoft.* Conclua o processo de verificação de email. O email de verificação é enviado para o endereço de email listado na página de configurações da sua conta no Partner Center.

> [!NOTE]
> * O link de verificação de email só é válido por sete dias. 
> * Você pode solicitar que reendemos o email visitando sua página de perfil de parceiro e selecionando o link de **email Reend verification.**
> * Para garantir que os emails são recebidos, liste os emails da microsoft.com como um domínio seguro e verifique suas pastas de lixo eletrônico.

## <a name="how-do-i-get-further-support-for-my-account-related-issues"></a>Como obter mais suporte para problemas relacionados à minha conta?

Visite a [página Suporte para o programa Marketplace Comercial](/azure/marketplace/partner-center-portal/support) no Partner Center para obter orientações e etapas para criar um tíquete de suporte.

## <a name="ive-checked-my-mail-folders-and-havent-received-the-verification-email-what-must-i-do-next"></a>Eu tenho verificado minhas pastas de email e não recebi o email de verificação. O que devo fazer em seguida?

Tente o seguinte:
* Verifique sua pasta de lixo eletrônico ou spam.
* Limpe o cache do navegador, vá para o painel da sua conta do Partner Center e selecione o link **reend verification email** para que o email de verificação seja reabilite para seu endereço de email.
* Tente acessar o link **de email Reend verification** de um navegador diferente.
* Trabalhe com seu departamento de IT para garantir que os emails de verificação não sejam bloqueados pelo servidor de email.
* Ajuste o filtro de spam do servidor para permitir ou listar todos os emails **maccount@microsoft. <span></span> com**.

## <a name="how-long-does-the-employment-verification-process-usually-take"></a>Quanto tempo o processo de verificação de emprego geralmente leva?

Se todos os detalhes enviados estão corretos, o processo de verificação de emprego leva cerca de duas horas para ser concluído.

## <a name="how-long-does-the-business-verification-process-usually-take"></a>Quanto tempo o processo de verificação de negócios geralmente leva?

Se todos os documentos necessários são enviados, a verificação comercial leva de um a dois dias úteis para ser concluída.

## <a name="if-i-reach-out-to-the-support-team-will-my-ticket-be-expedited"></a>Se eu falar com a equipe de suporte, meu tíquete será expedido?

Os tíquetes de suporte são resolvidos em uma semana. Verifique se há atualizações enviadas para a ID de email fornecida ao aumentar o tíquete de suporte.

## <a name="my-issue-is-not-listed-here-are-there-other-pages-i-can-reference-for-partner-center-issues"></a>Meu problema não está listado aqui. Há outras páginas que posso referenciar para problemas do Partner Center?

Consulte a [documentação do marketplace comercial](/azure/marketplace/) para obter mais ajuda.

## <a name="ive-created-a-support-ticket-it-has-been-7-business-days-and-i-havent-received-an-update-where-can-i-get-additional-help"></a>Criei um tíquete de suporte, já se passou sete dias úteis e ainda não recebi uma atualização. Onde posso obter ajuda adicional?

Envie um email para **<teamsubm@microsoft.com>** ele com os seguintes detalhes:

* **Linha de Assunto:** Problema de conta do Partner Center <App_Name> (especifique o nome do seu aplicativo).
* **Corpo do email:**
    * Número do tíquete de suporte
    * Sua ID de vendedor
    * Uma captura de tela do problema (se possível)
    
## <a name="app-category-mapping"></a>Mapeamento de categorias de aplicativos

| Categoria do Teams       | Categorias de computador  |
|:---------------------|:---------------|
| Análise e BI | Análise, Visualização de Dados e BI |
| Desenvolvedor e IT | Ferramentas de Desenvolvedor, Administrador de IT |
| Educação | Educação |
| Recursos humanos | Recursos humanos e recrutação |
| Produtividade | Gerenciamento de conteúdo, arquivos e documentos, produtividade, treinamentos e tutoriais e utilitários |
| Gerenciamento de projeto | Comunicação, Gerenciamento de Projetos, Fluxo de Trabalho e Gerenciamento de Negócios |
| Vendas e suporte | Gerenciamento de Clientes e Contatos, Suporte ao Cliente, Gerenciamento Financeiro, Vendas e Marketing |
| Social e divertido | Galerias de imagens e vídeo, estilo de vida, notícias e clima, social, viagens e navegação |

>
> [!div class="nextstepaction"]
> [Saiba mais sobre as políticas de validação de aplicativos do Microsoft Teams](/legal/marketplace/certification-policies)
