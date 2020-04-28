---
title: Diretrizes de processo de aprovação do Microsoft Teams app
description: Descreve o processo de aprovação para obter seu aplicativo publicado no Microsoft Teams App Store
keywords: Editor de publicação do Microsoft Teams AppSource
ms.openlocfilehash: 70f81f40ff424ab28e7129da7b947be0b1fcf469
ms.sourcegitcommit: 61edf47c9dd1dbc1df03d0d9fb83bfedca4c423b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2020
ms.locfileid: "43914543"
---
# <a name="submit-your-app-to-appsource"></a>Envie seu aplicativo para o AppSource

## <a name="teams-app-submission"></a>Envio de aplicativos do teams

Publicar seu aplicativo no [AppSource](https://appsource.microsoft.com) o disponibiliza no catálogo de aplicativos do Microsoft Teams e na Web. Em um nível alto, o processo de envio de seu aplicativo para o AppSource é:

1. Desenvolva seu aplicativo seguindo as [diretrizes de design](~/concepts/design/understand-use-cases.md). As guias devem seguir as [diretrizes de design de guia](~/tabs/design/tabs.md). Os bots devem seguir as [diretrizes de design de bot](~/bots/design/bots.md).
1. [Configurar uma conta de desenvolvedor](/office/dev/store/open-a-developer-account) no [Partner Center](https://support.microsoft.com/help/4499930/partner-center-overview).
1. Prepare seu aplicativo para envio, seguindo nossa [lista de verificação de envio](~/concepts/deploy-and-publish/appsource/prepare/submission-checklist.md).
1. Revise nossas [dicas para um envio de aplicativo bem-sucedido](~/concepts/deploy-and-publish/appsource/prepare/frequently-failed-cases.md).
1. Envie seu pacote para o [AppSource por meio do Partner Center](/office/dev/store/use-partner-center-to-submit-to-appsource).
1. Acompanhe o processo de aprovação no painel do seu centro de parceria. *Consulte* [visão geral do Partner Center](https://support.microsoft.com/help/4499930/partner-center-overview).
1. Envio de postagem — revise nossas orientações para [manter e dar suporte ao seu aplicativo publicado](~/concepts/deploy-and-publish/appsource/post-publish/overview.md).

>[!NOTE]
>
> * Se seu aplicativo do Microsoft Teams contiver um bot, você deverá estar em conformidade com o [código de conduta do](https://aka.ms/bf-conduct)bot Developer Framework.
> * Se seu aplicativo contiver um conector do Office 365, termos adicionais poderão ser aplicados. *Consulte* [Connectors Dashboard de desenvolvedor](https://aka.ms/connectorsdashboard) e [contrato de desenvolvedor de aplicativos](https://sellerdashboard.microsoft.com/Assets/Content/Agreements/Office_Store_Seller_Agreement_20120927.htm).

## <a name="faqs--teams-apps-and-partner-accounts"></a>Perguntas frequentes: aplicativos de equipe e contas de parceiros

## <a name="how-do-i-create-a-partner-center-account"></a>Como faço para criar uma conta do Partner Center?

Há duas maneiras de criar uma conta de centro de parceiros:

* Se você é novo no Partner Center e não tem uma conta na rede da Microsoft, [crie uma conta usando a página de registro do Partner Center](/office/dev/store/open-a-developer-account#create-an-account-using-an-existing-partner-center-enrollment).
* Se você já estiver inscrito na rede de parceiros, [crie uma conta diretamente no Partner Center usando um registro existente](/office/dev/store/).

## <a name="how-do-i-add-my-phone-number-to-the-contact-info-section"></a>Como adiciono meu número de telefone à seção informações de contato?

O número de telefone tem três partes: código do país, código de área e número de telefone. Se nenhuma seção for aplicável, insira o número `0`.

## <a name="why-do-i-get-the-message-this-account-is-not-publish-eligible-when-i-try-to-submit-my-add-in-through-partner-center"></a>Por que recebo a mensagem "esta conta não está publicando qualificada" quando tento enviar meu suplemento por meio do Partner Center?

Você receberá a mensagem de erro acima quando o [status da verificação da conta](/partner-center/verification-responses) estiver pendente. Você pode verificar o status de verificação da sua conta no [painel](https://partner.microsoft.com/dashboard) do centro de parceiro selecionando a opção **configurações** (o ícone de engrenagem) no canto superior direito do Shell de cabeçalho de página e escolhendo**configurações de conta** de**conta**  => de **configurações** => do desenvolvedor.

![Página de configurações de conta do centro de parceiros](../../../assets/images/partner-center-accts-page.png)

![Status de verificação do centro de parceiros](../../../assets/images/partner-center-verification-status.png)

Durante o processo de verificação da conta, o status de cada etapa obrigatória: propriedade de email, verificação de emprego e verificação de negócios — será exibida. Depois que o processo de verificação for concluído com êxito, o status de verificação do registro na página de perfil mudará de "pendente" para "autorizado" e as etapas do processo não serão mais exibidas.

![Erro de verificação da central de parceiros](../../../assets/images/partner-center-acct-verification-error.png)

## <a name="how-i-do-get-further-support-for-my-account-related-issues"></a>Como eu obteria mais suporte para as minhas questões relacionadas à conta?

Visite a [página de ajuda e suporte para parceiros](https://aka.ms/marketplacepublishersupport) e procure soluções úteis para a documentação relacionada ao seu problema. Se as soluções ou documentos de autoatendimento fornecidos não forem úteis para resolver seu problema, registre um tíquete de suporte selecionando **fornecer detalhes do problema** na seção **próxima etapa** . Você pode procurar seu tópico de problema na caixa de pesquisa ou selecionar **Tópicos de navegação**, abaixo da caixa de pesquisa, para detalhar.

> [!TIP]
> Se você estiver procurando ajuda com um problema de **verificação de conta** :
>
>1. Abaixo da **caixa de pesquisa**, selecione **Procurar tópicos**.
>1. Selecione **todos os programas** no menu suspenso **categoria** .
> 1. Selecione **conta, integração, acesso** no menu suspenso **tópico** .
>1. **Selecione uma opção** no menu suspenso **subtópico** .
>1. Para obter mais assistência. Selecione **fornecer detalhes do problema** na seção **próxima etapa** .
>

## <a name="ive-checked-my-mail-folders-and-havent-received-the-verification-email-what--should-i-do-next"></a>Verifiquei minhas pastas de email e não recebi o email de verificação. O que devo fazer em seguida?

Tente o seguinte:

1. Verifique a pasta de lixo eletrônico/spam.
1. Limpe o cache do navegador, vá para o painel de conta do centro de parceiros e selecione o link **reenviar email de verificação** para que o email de verificação seja enviado novamente ao seu endereço de email.
1. Tente acessar o link de **email de verificação de reenvio** de outro navegador.
1. Trabalhe com seu departamento de ti para garantir que os emails de verificação não sejam bloqueados pelo servidor de email.
1. Ajuste o filtro de spam do seu servidor para permitir/listar todos os emails de **maccount@microsoft.<span> </span> com**.

## <a name="how-long-does-the-employment-verification-process-usually-take"></a>Quanto tempo o processo de verificação de emprego geralmente leva?

Se todos os detalhes forem fornecidos corretamente, a verificação de emprego será concluída em 1 a 2 horas.

## <a name="ive-already-reached-out-to-support-is-there-a-way-to-expedite-my-case"></a>Já tenho chegado ao suporte, existe uma maneira de agilizar o meu caso?

Os tíquetes de suporte serão resolvidos dentro do horário da semana. Procure as atualizações que serão enviadas para o email fornecido quando o tíquete de suporte foi gerado.

## <a name="ive-created-a-support-ticket-it-has-been-7-business-days-and-i-havent-received-an-update-where-can-i-get-additional-help"></a>Criei um tíquete de suporte, ele tem sete dias úteis e não recebi uma atualização. Onde posso obter ajuda adicional?

Envie um email para **<teamsubm@microsoft.com>** com os seguintes detalhes:

1. **Linha de assunto**. *Problema de conta do centro de parceria para <App_Name>* (especifique o nome do seu aplicativo).
2. **Corpo do email:**
    * Número do tíquete de suporte:
    * Sua ID de vendedor:
    * Uma captura de tela do problema.

> [!div class="nextstepaction"]
> [Saiba mais sobre as políticas de validação de aplicativos para o Microsoft Teams](https://docs.microsoft.com/legal/marketplace/certification-policies)
