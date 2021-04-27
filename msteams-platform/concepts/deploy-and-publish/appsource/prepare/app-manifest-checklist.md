---
title: Lista de verificação do manifesto do aplicativo
description: A lista de verificação do manifesto do aplicativo para publicar seu aplicativo do Microsoft Teams no AppSource
ms.topic: reference
localization_priority: Normal
keywords: teams publish store office publishing checklist
ms.openlocfilehash: a8fd57d8050530856fa635f59c0a6ce4f8c2a5cf
ms.sourcegitcommit: 825abed2f8784d2bab7407ba7a4455ae17bbd28f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2021
ms.locfileid: "52019899"
---
# <a name="app-manifest-checklist"></a>Lista de verificação do manifesto do aplicativo

>[!IMPORTANT]
>Estamos migrando o gerenciamento de soluções do Office do Painel do Vendedor para o Partner Center. Para obter detalhes, confira [Migrando do Painel do Vendedor para o Partner Center ](https://developer.microsoft.com/office/blogs/moving-management-of-solutions-from-seller-dashboard-to-partner-center/) e ler as [Perguntas frequentes](https://docs.microsoft.com/office/dev/store/partner-center-faq).

O manifesto do aplicativo precisa estar em conformidade com as diretrizes descritas abaixo.

>[!Tip]
> Use o App Studio para ajudá-lo a criar o manifesto do aplicativo. Ele validará a maioria dos requisitos abaixo para você e exibirá qualquer erro ou aviso na **guia Testar e Distribuir.**

## <a name="tips"></a>Dicas 

* Não use "Teams", "Microsoft" ou "app" no nome do aplicativo.
* O developerName em seu manifesto deve ser igual ao Nome do Provedor definido no Partner Center.
* Certifique-se de que a descrição do aplicativo, capturas de tela, texto e imagens promocionais descrevam apenas o aplicativo e não contenham nenhuma publicidade adicional, promoções ou nomes de marca protegidos por direitos autorais.
* Se o produto exigir uma conta em seu serviço ou em outro serviço, liste que na descrição e verifique se há links para se inscrever, entre e saia.
* Se o produto exigir que compras adicionais funcionem corretamente, liste isso na descrição.
* Forneça os links de política de Termos e Privacidade necessários no manifesto e no Partner Center ou no Painel. Verifique se os links são resolvidos corretamente para a documentação correta, idealmente específico do Teams. Para bots, você deve fornecer essas mesmas informações na seção Envio da página de registro da Estrutura de Bot.
* Verifique se os metadados no manifesto coincidem exatamente com metadados no Partner Center (e, para bots, no registro da Estrutura de Bots). Observe que sua entrada do Partner Center pode conter uma descrição mais detalhada e formatada para uso na página do produto AppSource.
* Verifique se o título do aplicativo usado em seu manifesto é uma combinação **exata com** o título do aplicativo inserido no envio do Partner Center. *Consulte* [Create effective listings in Microsoft AppSource and within Office — Use a consistent add-in name](https://docs.microsoft.com/office/dev/store/create-effective-office-store-listings#use-a-consistent-add-in-name).

## <a name="metadata-requirement"></a>Requisito de metadados

Os metadados a seguir são necessários para seu aplicativo.

|Dados|Tipo|Size|Manifesto|Centro de parceria|Descrição|
|---|---|---|---|---|---|
|Pacote de aplicativos|.zip|||✔|O pacote de aplicativo real para carregamento ou envio do AppSource.|
|Logotipo de cor|.png|192 &times; 192 pixels|`icon.color`||O ícone a ser exibido na listagem de página do produto na galeria do Teams. Esse é o logotipo do produto de cores completas.|
|Contorno de logotipo|.png|32 &times; 32 pixels|`icon.outline`||O ícone a ser exibido no Teams, no canal de chat do Teams e em outros locais. Esse é o logotipo renderizado como um contorno branco com plano de fundo transparente.|
|Logotipo do aplicativo|.png, .jpg, .jpeg, .gif|300 &times; 300 pixels||✔|O ícone a ser exibido no AppSource. Este é o logotipo do produto de cores completas e é um arquivo diferente do usado no manifesto para `icon.color` . deve ser menor que 512 KB.|
|Link de suporte|URL|||✔|Um link para dar suporte a materiais para usuários finais que podem não ter instalado seu aplicativo. Link disponível publicamente acessível sem qualquer logon (HTTPS).|
|Link de privacidade|URL||`developer.privacyUrl`|✔|Um link para sua política de privacidade (HTTPS).|
|Link de vídeo|URL|||Opcional|Um link para um vídeo sobre seu aplicativo.|
|EULA|.doc, .pdf, etc.|||Opcional|O AppSource requer um contrato de licenciamento do usuário final (EULA), que você pode fornecer como um anexo. Se você optar por não enviar um EULA, um será fornecido em seu nome.|
|Termos de serviço|URL||`developer.termsOfServiceUrl`||Um link para seus termos de serviço (HTTPS).|
|Notas de teste|Preencher em linha ou vincular a uma URL pública|||Notas de teste detalhadas sobre como testar seu aplicativo passo a passo. Inclua duas credenciais de logon para testar cenários de Administrador e Não Administrador.|

## <a name="localized-content"></a>Conteúdo localizado

> [!NOTE]
> O AppSource planeja dar suporte ao conteúdo localizado para os metadados a seguir. Atualmente, a listagem do aplicativo só será exibida em inglês no AppSource, mas será exibida corretamente localizada no cliente do Teams. Consulte [localizando seu aplicativo](~/concepts/build-and-test/apps-localization.md) para obter mais informações.

|Dados|Tipo|Size|Manifesto|Centro de parceria|Descrição|
|---|---|---|---|---|---|
|Nome do aplicativo|String|30|`name.short`|✔|O nome do aplicativo como ele deve aparecer na frente de armazenamento e no produto.|
|Nome longo do aplicativo|String|30|`name.full`|✔|O nome do aplicativo como ele deve aparecer na frente de armazenamento e no produto.|
|Descrição breve|String|80|`description.short`|✔|Descrição curta do seu aplicativo.|
|Descrição longa|String|4000|`description.full`|✔|Uma descrição mais detalhada do seu aplicativo. No arquivo de manifesto, um resumo preciso é adequado. No Partner Center, você pode usar uma descrição mais rica e formatada para a página do produto AppSource.|
|Capturas de tela (1 a 5)|.png, .jpg ou .gif|1366w x 768h e menor que 1024 KB||✔|Pelo menos uma captura de tela que mostra a experiência do aplicativo. Usa na página de detalhes do aplicativo.|

## <a name="submission-extras-for-bots"></a>Extras de envio para bots

Os bots no Microsoft Teams devem ser criados usando a Estrutura de Bots. Consulte [Criar um bot para](~/bots/how-to/create-a-bot-for-teams.md) obter instruções. Use um ícone de cor 96x96 para o ícone do bot na Estrutura de Bots.
