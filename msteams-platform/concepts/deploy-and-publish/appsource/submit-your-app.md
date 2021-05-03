---
title: Enviar seu aplicativo para o Partner Center
description: Saiba como criar uma conta do Partner Center e enviar seu aplicativo para validação da loja.
author: heath-hamilton
ms.author: lajanuar
ms.topic: how-to
ms.openlocfilehash: 732e283bffc253743e890b0c45dc7b0689108716
ms.sourcegitcommit: 25c9ad27f99682caaa7347840578b118c63b8f69
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/30/2021
ms.locfileid: "52101867"
---
# <a name="submit-your-microsoft-teams-app-to-partner-center"></a>Enviar seu Microsoft Teams para o Partner Center

Depois de preparar o envio da loja, você pode enviar oficialmente seu aplicativo para revisão.

## <a name="create-a-partner-center-account"></a>Criar uma conta do Partner Center

Para publicar seu aplicativo na Teams store e no AppSource, você deve primeiro [configurar uma conta de desenvolvedor.](https://docs.microsoft.com/office/dev/store/open-a-developer-account)

## <a name="submit-your-app"></a>Enviar seu aplicativo

Para enviar seu aplicativo, siga estas instruções de envio passo a passo [do armazenamento.](https://docs.microsoft.com/office/dev/store/add-in-submission-guide) Ao criar um novo envio, especifique que você está enviando um Teams aplicativo.

### <a name="app-category-mapping"></a>Mapeamento de categorias de aplicativo

Durante o envio, você é solicitado a categorizar seu aplicativo. A tabela a seguir mapeia Teams de armazenamento para as categorias listadas no Partner Center.

| Teams categorias       | Categorias do Partner Center  |
|:---------------------|:---------------|
| Análise e BI | Análise, Visualização de Dados e BI |
| Desenvolvedor e IT | Ferramentas de Desenvolvedor, Administrador de IT |
| Educação | Educação |
| Recursos humanos | Recursos Humanos e Recrutamento |
| Produtividade | Gerenciamento de Conteúdo, Arquivos e documentos, Produtividade, Treinamento e Tutoriais e Utilitários |
| Gerenciamento de projeto | Comunicação, Project Gerenciamento, Fluxo de Trabalho e Gerenciamento de Negócios |
| Vendas e suporte | Gerenciamento de Clientes e Contatos, Suporte ao Cliente, Gerenciamento Financeiro, Vendas e Marketing |
| Social e divertido | Galerias de imagem e vídeo, estilo de vida, notícias e clima, social, viagem e navegação |

### <a name="3-fix-issues-with-your-submission"></a>3. Corrigir problemas com seu envio

Se o aplicativo falhar no envio, você receberá um relatório de falha para saber o que corrigir e reabrir. A Microsoft também fornece um serviço de white-glove para ajudar a listar seu aplicativo.

## <a name="faqs"></a>Perguntas Frequentes

### <a name="how-do-i-create-a-partner-center-account"></a>Como criar uma conta do Partner Center?

Você pode criar uma conta do Partner Center de uma das seguintes maneiras:

- Se você for novo no Partner Center e não tiver uma conta na rede da Microsoft, crie uma conta usando a página de registro [do Partner Center](/office/dev/store/open-a-developer-account#create-an-account-using-the-partner-center-enrollment-page).
- Se você já estiver inscrito na Rede de Parceiros, crie uma conta diretamente no Partner Center usando [uma página de registro existente.](/office/dev/store/open-a-developer-account#create-an-account-using-an-existing-partner-center-enrollment)

### <a name="what-if-i-cant-find-my-office-store-account-in-partner-center"></a>E se eu não conseguir encontrar minha conta Office Store no Partner Center?

Abra um [tíquete de](https://partner.microsoft.com/support/v2/?stage=1) suporte do Partner Center e selecione o seguinte nos menus suspensos:

| Menu | Opção |
| -------   | -------  |
|Categoria| Marketplace Comercial|
| Tópico | Perguntas gerais sobre Ajuda do Marketplace e Como fazer perguntas |
| Subtópico| Suplemento do Office |

### <a name="where-can-i-get-support-for-my-partner-center-account-issues"></a>Onde posso obter suporte para problemas de conta do Partner Center?

Visite a [página de suporte de editores](https://aka.ms/marketplacepublishersupport) para pesquisar seu tópico de problema e encontrar orientações. Se as orientações fornecidas não são úteis, aduza um tíquete de suporte [do Partner Center](/azure/marketplace/partner-center-portal/support#how-to-open-a-support-ticket).

### <a name="how-do-i-manage-my-office-store-account-in-partner-center"></a>Como faço para gerenciar minha conta Office Store no Partner Center?

Visite a [conta Gerenciar sua Office Store por meio do Partner Center](/office/dev/store/manage-account-settings-and-profile) para obter orientação.

### <a name="how-do-i-add-my-phone-number-to-the-partner-profile-contact-section"></a>Como adicionar meu número de telefone à seção de contato de perfil de parceiro?

O número de telefone tem três partes, código de país, código de área e número de telefone. Se o número de telefone não incluir um código de área, deixe a segunda caixa vazia e conclua a terceira caixa.

### <a name="how-do-i-manage-my-account-settings-and-partner-profile-in-partner-center"></a>Como gerencie minhas configurações de conta e perfil de parceiro no Partner Center?

Visite a [página Gerenciar configurações de conta](/windows/uwp/publish/manage-account-settings-and-profile#additional-settings-and-info) e informações de perfil para obter orientações sobre como gerenciar as configurações da conta do Partner Center.

### <a name="why-do-i-receive-the-message-this-account-is-not-publish-eligible-when-i-try-to-submit-my-app"></a>Por que recebo a mensagem"Essa conta não é qualificada para publicar", quando tento enviar meu aplicativo?

Você recebe a mensagem de erro acima quando o [status de](/partner-center/verification-responses) verificação da conta está pendente. Verifique o status de verificação da sua conta no painel do Partner [Center.](https://partner.microsoft.com/dashboard) Selecione **Configurações**, o ícone de engrenagem no canto superior direito do shell do header da página. Escolha **Configurações do desenvolvedor**  =>  **Configurações** da conta De   =>  **conta**.

![Página de configurações da conta do Partner Center](../../../assets/images/partner-center-accts-page.png)

![Status de verificação do Partner Center](../../../assets/images/partner-center-verification-status.png)

O status de cada etapa necessária, como Propriedade de **Email,** Verificação de **Emprego** e Verificação de **Negócios,** são exibidos no processo de verificação da conta. Após a conclusão do processo de verificação, o status de verificação do seu registro na página de perfil muda *de pendente* para *autorizado*. As etapas do processo não são mais exibidas.

![Erro de verificação do Partner Center](../../../assets/images/partner-center-acct-verification-error.png)

### <a name="what-is-verified-in-the-partner-center-account-verification-process-and-how-to-respond"></a>O que é verificado no processo de verificação de conta do Partner Center e como responder?

Há três áreas de verificação, **Propriedade de Email,** **Emprego** e **Negócios.** Para obter mais informações sobre o processo de verificação, consulte [O que é verificado e como responder](/partner-center/verification-responses#what-is-verified-and-how-to-respond).
Se você for o contato principal, administrador global ou administrador de conta, vá até seu Perfil de Parceiro para monitorar o status de verificação e acompanhar o progresso.

Após a conclusão do processo de verificação, o status de verificação do seu registro na página de perfil muda *de pendente* para *autorizado*. Após a autorização, as etapas do processo e seu status não estão mais disponíveis na página. O contato principal recebe um email da Microsoft dentro de alguns dias úteis após a conclusão da verificação.

### <a name="my-account-verification-status-hasnt-advanced-beyond-email-ownership-how-should-i-proceed"></a>O status de verificação da minha conta não avançou além da Propriedade de Email. Como devo continuar?

Durante o **processo de verificação de Propriedade de** Email, um email de verificação é enviado para o endereço de email de contato principal. Verifique sua caixa de entrada de contato principal para um email maccount@ **<span>microsoft</span>.com com** a linha de assunto *Ação necessária: Verificar* sua conta de email com a Microsoft . Conclua o processo de verificação de email. O email de verificação é enviado para o endereço de email listado na página de configurações da sua conta no Partner Center.

> [!NOTE]
> * O link de verificação de email só é válido por sete dias. 
> * Você pode solicitar que enviemos o email de novo visitando a página de perfil do parceiro e selecionando o link **Resend verification email.**
> * Para garantir que o email seja recebido, liste com segurança o email do microsoft.com como um domínio seguro e verifique suas pastas de lixo eletrônico.

### <a name="how-do-i-get-further-support-for-my-account-related-issues"></a>Como obter mais suporte para meus problemas relacionados à conta?

Visite a [página Suporte para o programa do Marketplace](/azure/marketplace/partner-center-portal/support) Comercial no Partner Center para obter orientações e etapas para criar um tíquete de suporte.

### <a name="ive-checked-my-mail-folders-and-havent-received-the-verification-email-what-must-i-do-next"></a>Eu chequei minhas pastas de email e não recebi o email de verificação. O que devo fazer em seguida?

Tente o seguinte:
* Verifique sua pasta de lixo eletrônico ou spam.
* Limpe o cache do navegador, vá para o painel da conta do Partner Center e selecione o **link** Enviar email de verificação de resendê-lo para que o email de verificação se ressente ao seu endereço de email.
* Tente acessar o **link Enviar novamente** o email de verificação de um navegador diferente.
* Trabalhe com seu departamento de IT para garantir que os emails de verificação não sejam bloqueados pelo servidor de email.
* Ajuste o filtro de spam do servidor para permitir ou listar todos os emails de **maccount@microsoft. <span></span> com**.

### <a name="how-long-does-the-employment-verification-process-usually-take"></a>Quanto tempo o processo de verificação de emprego geralmente leva?

Se todos os detalhes enviados estão corretos, o processo de verificação de emprego leva cerca de duas horas para ser concluído.

### <a name="how-long-does-the-business-verification-process-usually-take"></a>Quanto tempo o processo de verificação comercial geralmente leva?

Se todos os documentos necessários são enviados, a verificação de negócios leva de um a dois dias úteis para ser concluída.

### <a name="if-i-reach-out-to-the-support-team-will-my-ticket-be-expedited"></a>Se eu falar com a equipe de suporte, meu tíquete será expedido?

Os tíquetes de suporte são resolvidos em uma semana. Verifique se há atualizações enviadas para a ID de email fornecida ao levantar o tíquete de suporte.

### <a name="my-issue-is-not-listed-here-are-there-other-pages-i-can-reference-for-partner-center-issues"></a>Meu problema não está listado aqui. Há outras páginas que posso fazer referência a problemas do Partner Center?

Consulte a [documentação do marketplace comercial](/azure/marketplace/) para obter mais ajuda.

### <a name="ive-created-a-support-ticket-and-i-havent-received-an-update-in-7-business-days-where-can-i-get-help"></a>Criei um tíquete de suporte e não recebi uma atualização em 7 dias úteis. Onde posso obter ajuda?

Envie um email **<teamsubm@microsoft.com>** para com os seguintes detalhes:

* **Linha de Assunto**: Problema de conta do Partner Center para <App_Name> (especifique o nome do seu aplicativo).
* **Corpo do email**:
    * Número do tíquete de suporte
    * Sua ID do vendedor
    * Uma captura de tela do problema (se possível)

## <a name="next-step"></a>Próxima etapa

> [!div class="nextstepaction"]
> [Manter e dar suporte ao aplicativo](~/concepts/deploy-and-publish/appsource/post-publish/overview.md)
