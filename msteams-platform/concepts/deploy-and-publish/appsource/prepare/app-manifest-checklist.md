---
title: Lista de verificação de manifesto de aplicativo
description: A lista de verificação para o manifesto do aplicativo para publicar seu aplicativo do Microsoft Teams no AppSource
keywords: lista de verificação de publicação do repositório de publicação do teams
ms.openlocfilehash: e684bb4f578944c6f37eeb43541a491d42ec3479
ms.sourcegitcommit: 4329a94918263c85d6c65ff401f571556b80307b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/01/2020
ms.locfileid: "41672791"
---
# <a name="app-manifest-checklist"></a>Lista de verificação de manifesto de aplicativo

O manifesto do aplicativo precisa estar em conformidade com as diretrizes descritas abaixo.

>[!Tip]
> Use o app Studio para ajudá-lo a criar o manifesto do aplicativo. Ele validará a maioria dos requisitos abaixo para você e exibirá qualquer erro ou aviso na guia **testar e distribuir** .

## <a name="tips"></a>Dicas 

* Não use "Teams", "Microsoft" ou "app" em seu nome de aplicativo.
* O desenvolvedorname no manifesto do aplicativo deve ser igual ao nome do provedor definido no painel do parceiro central ou do vendedor.
* Certifique-se de que a descrição do aplicativo, capturas de tela, texto e imagens promocionais descrevem apenas o aplicativo e não contêm anúncios adicionais, promoções ou nomes de marca de direitos autorais.
* Se o produto exigir uma conta no serviço ou em outro serviço, liste-a na descrição e assegure-se de que haja links para se inscrever, entrar e sair.
* Se o produto exigir que as compras adicionais funcionem corretamente, liste na descrição.
* Forneça os termos de requisitos e os links de política de privacidade no manifesto e no painel de parceria ou no painel do vendedor. Verifique se os links são resolvidos corretamente para a documentação correta e específico para o Microsoft Teams. Para bots, você deve fornecer as mesmas informações na seção envio da página de registro do bot Framework.
* Certifique-se de que os metadados no manifesto correspondam exatamente aos metadados no painel do centro de parceria ou vendedor (e, para bots, no registro da estrutura do bot). Observe que a entrada de painel do vendedor deve conter uma descrição mais detalhada e formatada para uso na página de produto do AppSource.
* Certifique-se de que o título do aplicativo usado no manifesto corresponde exatamente com o título do aplicativo inserido no centro de parceria ou no envio do painel do vendedor

## <a name="metadata-requirement"></a>Requisitos de metadados

Os metadados a seguir são necessários para seu aplicativo.

|Dados|Tipo|Tamanho|Manifesto|Centro de parceria|Descrição|
|---|---|---|---|---|---|
|Pacote de aplicativos|.zip|||✔|O pacote de aplicativos real para carregar ou AppSource o envio.|
|Logotipo colorido|.png|192&times;192 pixels|`icon.color`||O ícone a ser exibido na lista de páginas de produtos na galeria do teams. Este é o logotipo do produto em quatro cores.|
|Descrição do logotipo|.png|32&times;32 pixels|`icon.outline`||O ícone a ser exibido no Microsoft Teams no canal de chat do Microsoft Teams e em outros locais. Este é o logotipo renderizado como um contorno branco com plano de fundo transparente.|
|Logotipo do aplicativo|. png,. jpg,. jpeg,. gif|300&times;300 pixels||✔|O ícone a ser exibido no AppSource. Este é o logotipo do produto de quatro cores e é um arquivo diferente daquele usado no manifesto para `icon.color`o. deve ser menor do que 512 KB.|
|Link de suporte|URL|||✔|Um link para o material de suporte para usuários finais que podem não ter instalado seu aplicativo. Link disponível publicamente acessível sem qualquer logon (HTTPS).|
|Link de privacidade|URL||`developer.privacyUrl`|✔|Um link para a política de privacidade (HTTPS).|
|Link de vídeo|URL|||Opcional|Um link para um vídeo sobre seu aplicativo.|
|TERMOS|. doc,. pdf, etc.|||Opcional|O AppSource requer um contrato de licença de usuário final (EULA), que você pode fornecer como um anexo. Se você optar por não enviar um EULA, ele será fornecido em seu nome.|
|Termos de serviço|URL||`developer.termsOfServiceUrl`||Um link para os seus termos de serviço (HTTPS).|
|Notas de teste|Preencher inline ou vincular a uma URL pública|||Notas de teste detalhadas sobre como testar seu aplicativo passo a passo. Inclua duas credenciais de logon para testar cenários de administrador e não administrativos.|

## <a name="localized-content"></a>Conteúdo localizado

> [!NOTE]
> Os planos do AppSource para dar suporte ao conteúdo localizado dos seguintes metadados. No momento, sua listagem de aplicativos só será mostrada em inglês no AppSource, mas será exibida corretamente localizada no cliente do teams. Confira como [localizar seu aplicativo](~/concepts/build-and-test/apps-localization.md) para obter mais informações.

|Dados|Tipo|Tamanho|Manifesto|Centro de parceria|Descrição|
|---|---|---|---|---|---|
|Nome do aplicativo|String|até|`name.short`|✔|O nome do seu aplicativo como deve aparecer na loja e no produto.|
|Nome do aplicativo longo|String|até|`name.full`|✔|O nome do seu aplicativo como deve aparecer na loja e no produto.|
|Descrição breve|String|80|`description.short`|✔|Breve descrição do seu aplicativo.|
|Descrição longa|String|4000|`description.full`|✔|Uma descrição mais detalhada do seu aplicativo. No arquivo de manifesto, um resumo preciso é adequado. No Partner Center, você pode usar uma descrição mais rica e formatada para a página de produto do AppSource.|
|Capturas de tela (1-5)|. png,. jpg ou. gif|1366w x 768h e menor que 1024 KB||✔|Pelo menos uma captura de tela que mostra sua experiência de aplicativo. Usa na página de detalhes do aplicativo.|

## <a name="submission-extras-for-bots"></a>Extras de envio para bots

Os bots no Microsoft Teams devem ser criados usando a estrutura de bot. Consulte [criar um bot](~/bots/how-to/create-a-bot-for-teams.md) para obter instruções. Use um ícone de cor 96x96 para o ícone do seu bot na estrutura do bot.
