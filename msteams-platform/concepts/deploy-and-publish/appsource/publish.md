---
title: Diretrizes do processo de envio de aprovação de aplicativos do Microsoft Teams
description: Descreve o processo de aprovação de envio para publicar seu aplicativo na loja de aplicativos do Microsoft Teams
keywords: teams publish store office publishing publish AppSource partner center account verification apps account not publish eligible
ms.openlocfilehash: 6268d408cc4c44633b9b3629c902044815639176
ms.sourcegitcommit: db19fee033b41152267bb524d67aee5b7f64b04a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/12/2021
ms.locfileid: "49797479"
---
# <a name="submit-your-app-to-appsource"></a>Enviar seu aplicativo para o AppSource

## <a name="teams-app-submission"></a>Envio de aplicativo do Teams

Publicar seu aplicativo no [AppSource](https://appsource.microsoft.com) o disponibiliza no catálogo de aplicativos do Teams e na Web. Em um nível alto, o processo para enviar seu aplicativo ao AppSource é:

1. Desenvolva seu aplicativo seguindo as [diretrizes de design.](~/concepts/design/understand-use-cases.md) As guias devem seguir as diretrizes de design de guia para área [de trabalho](~/tabs/design/tabs.md) e web e [dispositivos móveis.](~/tabs/design/tabs-mobile.md) Os bots devem seguir as [diretrizes de design de bot.](~/bots/design/bots.md)
1. Certifique-se de que seu aplicativo atenda às políticas [de validação do](/legal/marketplace/certification-policies) aplicativo para o Microsoft Teams. 
1. Teste seu aplicativo com a ferramenta [de validação de manifesto.](prepare/submission-checklist.md#teams-app-validation-tool)
1. [Configurar uma conta de desenvolvedor](/office/dev/store/open-a-developer-account) no Partner [Center.](https://support.microsoft.com/help/4499930/partner-center-overview) *Consulte também* [Como criar uma conta do Partner Center](#how-do-i-create-a-partner-center-account) na seção perguntas frequentes, abaixo.
1. Prepare seu aplicativo para envio seguindo nossa lista de [verificação de envio.](prepare/submission-checklist.md)
1. Revise os [casos de teste com mais falhas para uma aprovação de qualidade de aplicativo mais rápida.](prepare/frequently-failed-cases.md)
1. Envie seu pacote para [o AppSource por meio do Partner Center.](/office/dev/store/use-partner-center-to-submit-to-appsource)
1. Acompanhe o processo de aprovação no painel do Partner Center. *Consulte Visão* [geral do Partner Center.](https://support.microsoft.com/help/4499930/partner-center-overview)
1. Post submission — revise nossas diretrizes para [manter e dar suporte ao seu aplicativo publicado.](post-publish/overview.md)

>[!NOTE]
>
>- Seu aplicativo teams deve ser responsivo para dispositivos móveis e estar em conformidade com nenhum requisito [de](~/concepts/deploy-and-publish/appsource/prepare/frequently-failed-cases.md#-mobile-responsiveness-no-direct-upsell-or-payment) venda em sistema operacional móvel (iOS e Android). 
>- Se seu aplicativo teams contém um bot, você deve estar em conformidade com o Código de Conduta da Estrutura [do Desenvolvedor de Bot.](https://aka.ms/bf-conduct)
>- Se seu aplicativo contiver um Conector do Office 365, termos adicionais poderão ser aplicados. *Consulte o* [Painel do Desenvolvedor de Conectores](https://aka.ms/connectorsdashboard) e o Contrato de Desenvolvedor de [Aplicativos.](https://sellerdashboard.microsoft.com/Assets/Content/Agreements/Office_Store_Seller_Agreement_20120927.htm)
>- Para disponibilizar seu aplicativo para usuários GCC e evitar listagens de aplicativos duplicadas na loja, o processo/fluxo de autenticação deve identificar e rotear o usuário para a URL de conteúdo especificada/esperada para usuários GCC.

## <a name="faqs--teams-apps-and-partner-account-verification-process-in-partner-center"></a>Perguntas frequentes — Aplicativos do Teams e processo de verificação de conta de parceiro no Partner Center

## <a name="how-do-i-create-a-partner-center-account"></a>Como criar uma conta do Partner Center?

Há duas maneiras de criar uma conta do Partner Center:

- Se você for novo no Partner Center e não tiver uma conta na rede da Microsoft, crie uma conta usando a página de registro [do Partner Center.](/office/dev/store/open-a-developer-account#create-an-account-using-an-existing-partner-center-enrollment)
- Se você já estiver inscrito no Partner Network, crie uma conta diretamente no [Partner Center usando um registro existente.](/office/dev/store/)

## <a name="what-if-i-cannot-find-my-office-store-account-in-partner-center"></a>E se eu não encontrar minha conta da Office Store no Partner Center?

Abra um [tíquete de suporte do Partner Center](https://partner.microsoft.com/support/v2/?stage=1) e selecione o seguinte nos menus suspensos:

| Menu | Opção |
| -------   | -------  |
|Categoria| Marketplace Comercial|
| Tópico | General Marketplace Help and How-to questions |
| Subtópico| Suplemento do Office |

## <a name="where-can-i-get-support-for-my-partner-center-account-issues"></a>Onde posso obter suporte para meus problemas de conta do Partner Center?

Visite nossa página [de suporte de editores](https://aka.ms/marketplacepublishersupport) para pesquisar o tópico do problema e encontrar orientações. Se a orientação fornecida não for útil, [abra um tíquete de](/azure/marketplace/partner-center-portal/support#how-to-open-a-support-ticket)suporte do Partner Center.

## <a name="how-do-i-manage-my-office-store-account-in-partner-center"></a>Como faço para gerenciar minha conta da Office Store no Partner Center?

Visite nossa conta  [gerenciar a Office Store no Partner Center para](/office/dev/store/manage-account-settings-and-profile) obter orientação sobre como gerenciar sua conta da Office Store por meio do Partner Center.

## <a name="how-do-i-add-my-phone-number-to-the-partner-profile-contact-section"></a>Como adicionar meu número de telefone à seção de contato do perfil de parceiro?

O número de telefone tem três partes : código de país, código de área e número de telefone. Se o número de telefone não incluir um código de área, deixe a segunda caixa vazia e preencha a terceira caixa.

## <a name="how-do-i-manage-my-account-settings-and-partner-profile-in-partner-center"></a>Como faço para gerenciar minhas configurações de conta e perfil de parceiro no Partner Center?

Visite nossa página [Gerenciar configurações de conta](/windows/uwp/publish/manage-account-settings-and-profile#additional-settings-and-info) e informações de perfil para obter orientação sobre como gerenciar suas configurações de conta do Partner Center.

## <a name="why-do-i-receive-the-message-this-account-is-not-publish-eligible-when-i-try-to-submit-my-add-in-through-partner-center"></a>Por que eu recebo a mensagem "Esta conta não é qualificada para publicação", quando tento enviar meu complemento por meio do Partner Center?

Você receberá a mensagem de erro acima quando o [status de](/partner-center/verification-responses) verificação da conta estiver pendente. Você pode verificar o status de verificação da  conta no painel do Partner [Center](https://partner.microsoft.com/dashboard) selecionando a opção Configurações (o ícone de engrenagem) no canto superior direito do shell de controle da página e escolhendo configurações de Desenvolvedor Configurações da conta Configurações da  =>     =>   conta.

![Página de configurações da conta do Partner Center](../../../assets/images/partner-center-accts-page.png)

![Status de verificação do Partner Center](../../../assets/images/partner-center-verification-status.png)

Durante o processo de verificação de conta, o status de cada etapa necessária — Propriedade do Email, Verificação de Emprego e Verificação de Negócios — será exibido. Depois que o processo de verificação for concluído com êxito, o status de verificação do registro na página de perfil mudará de "pendente" para "autorizado", e as etapas do processo não serão mais exibidas.

![Erro de verificação do Partner Center](../../../assets/images/partner-center-acct-verification-error.png)

## <a name="what-is-verified-in-partner-center-account-verification-process-and-how-to-respond"></a>O que é verificado no processo de verificação de conta do Partner Center e como responder?
Há três áreas de verificação: Propriedade de Email, Emprego e Negócios. Confira os detalhes [](/partner-center/verification-responses#what-is-verified-and-how-to-respond) do que é verificado e como responder Se você for o contato principal (Administrador global ou administrador de conta), recomendamos que você acesse seu Perfil de Parceiro para monitorar o status da verificação e acompanhar o progresso.

Quando o processo de verificação for concluído, o status de  verificação  do seu registro na página de perfil mudará de pendente para autorizado e as etapas do processo com status, exibidas nessa página, desaparecerão. O contato principal receberá um email da Microsoft dentro de alguns dias úteis após a conclusão da verificação.

## <a name="my-account-verification-status-has-not-advanced-beyond-email-ownership-in-partner-center-how-should-i-proceed"></a>O status de verificação da minha conta não avançou além da Propriedade de Email no Partner Center. Como devo prosseguir?

Durante o **processo de verificação de propriedade** de email, um email de verificação é enviado para o endereço de email principal do contato. Verifique sua caixa de entrada de contato principal em busca de um email da **maccount@<span>microsoft.com</span>com a** linha de assunto Ação necessária: verifique sua conta de email com a *Microsoft,* solicitando que você conclua o processo de verificação de email. O email de verificação será enviado para o endereço de email listado na página de configurações da sua conta no Partner Center.

> [!NOTE]
 >O link de verificação de email só é válido por sete dias. Você pode solicitar que reendemos o email para você visitando sua página de perfil de parceiro e selecionando o link de **email Resend verification.** Para garantir que o email seja recebido, a lista segura de emails da microsoft.com como um domínio seguro e verifique suas pastas de lixo eletrônico.

## <a name="how-i-do-get-further-support-for-my-account-related-issues"></a>Como obter mais suporte para problemas relacionados à minha conta?

Visite nosso Programa [de Suporte do Marketplace Comercial](/azure/marketplace/partner-center-portal/support) na página do Partner Center para obter orientações e etapas para criar um tíquete de suporte.

## <a name="ive-checked-my-mail-folders-and-havent-received-the-verification-email-what--should-i-do-next"></a>Eu tenho verificado minhas pastas de email e não recebi o email de verificação. O que devo fazer em seguida?

Experimente o seguinte:

1. Verifique sua pasta de lixo eletrônico/spam.
1. Limpe o cache do navegador, vá para o painel da sua conta do Partner Center e selecione o link **reend verification email** para que o email de verificação seja reabilite para seu endereço de email.
1. Tente acessar o link  **de email Reend verification** de um navegador diferente.
1. Trabalhe com seu departamento de IT para garantir que os emails de verificação não sejam bloqueados pelo servidor de email.
1. Ajuste o filtro de spam do servidor para permitir/listar todos os emails **maccount@microsoft. <span></span> com**.

## <a name="how-long-does-the-employment-verification-process-usually-take"></a>Quanto tempo o processo de verificação de emprego geralmente leva?

Se todos os detalhes enviados estão corretos, a verificação de emprego é concluída em 1 a 2 horas.

## <a name="how-long-does-the-business-verification-process-usually-take"></a>Quanto tempo o processo de "Verificação de Negócios" geralmente leva?

A Verificação De Negócios leva de 1 a 2 dias úteis para ser concluída, desde que todos os documentos necessários tenham sido enviados.

## <a name="if-i-reach-out-to-the-support-team-will-my-ticket-be-expedited"></a>Se eu falar com a equipe de suporte, meu tíquete será expedido?

Os tíquetes de suporte serão resolvidos dentro de uma semana. Procure as atualizações que serão enviadas para o email fornecido quando o tíquete de suporte foi gerado.

## <a name="my-issue-is-not-listed-here--are-there-other-pages-i-can-reference-for-partner-center-issues"></a>Meu problema não está listado aqui.  Há outras páginas que posso referenciar para problemas do Partner Center?

Consulte nossa documentação [do marketplace comercial](/azure/marketplace/) para obter mais ajuda.

## <a name="ive-created-a-support-ticket-it-has-been-7-business-days-and-i-havent-received-an-update-where-can-i-get-additional-help"></a>Criei um tíquete de suporte, faz sete dias úteis e ainda não recebi uma atualização. Onde posso obter ajuda adicional?

Envie um email para ele **<teamsubm@microsoft.com>** com os seguintes detalhes:

1. **Linha de assunto**. *Problema de conta do Partner Center para <App_Name>* (especifique o nome do seu aplicativo).
1. **Corpo do email:**
    * Número do tíquete de suporte:
    * Sua ID de vendedor:
    * Uma captura de tela do problema (se possível):
    
## <a name="app-category-mapping"></a>Mapeamento de categorias de aplicativos

| Categoria do Teams       | Categorias de computador  |
|:---------------------|:---------------|
| Análise e BI | Análise, visualização de dados e BI |
| Desenvolvedor e IT | Ferramentas de Desenvolvedor, Administrador de IT |
| Educação | Educação |
| Recursos humanos | Recursos humanos e recrutação |
| Produtividade | Gerenciamento de conteúdo, arquivos e documentos, produtividade, treinamento e tutoriais e utilitários |
| Gerenciamento de projeto | Comunicação, Gerenciamento de Projetos, Fluxo de Trabalho e Gerenciamento de Negócios |
| Vendas e suporte | Gerenciamento de Clientes e Contatos, Suporte ao Cliente, Gerenciamento Financeiro, Vendas e Marketing |
| Social e divertido | Galerias de imagens e vídeo, estilo de vida, notícias e clima, social, viagens e navegação |

>
> [!div class="nextstepaction"]
> [Saiba mais sobre as políticas de validação de aplicativos do Microsoft Teams](/legal/marketplace/certification-policies)
