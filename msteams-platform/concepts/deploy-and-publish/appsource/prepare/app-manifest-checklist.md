---
title: Lista de verificação do manifesto do aplicativo
description: A lista de verificação do manifesto do aplicativo para publicar seu aplicativo Microsoft Teams no AppSource
ms.topic: reference
keywords: teams publish store office publishing checklist
ms.openlocfilehash: f07c0d2693d12d56d6717724e1ef402cf79d5fff
ms.sourcegitcommit: 976e870cc925f61b76c3830ec04ba6e4bdfde32f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/27/2021
ms.locfileid: "50014394"
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
* Certifique-se de que a descrição do aplicativo, capturas de tela, texto e imagens promocionais descrevam apenas o aplicativo e não contenham anúncios adicionais, promoções ou nomes de marca protegidos por direitos autorais.
* Se o seu produto exigir uma conta em seu serviço ou em outro serviço, liste isso na descrição e verifique se há links para se inscrever, entrar e sair.
* Se seu produto exigir compras adicionais para funcionar corretamente, liste-o na descrição.
* Forneça os links de política de Termos e Privacidade necessários no manifesto e no Partner Center ou no Painel. Verifique se os links são resolvidos corretamente para a documentação correta, o ideal é que o Teams seja específico. Para bots, você deve fornecer essas mesmas informações na seção Envio da página de registro do Bot Framework.
* Verifique se os metadados no manifesto coincidem exatamente com os metadados no Partner Center (e, para bots, no registro do Bot Framework). Observe que sua entrada no Partner Center pode conter uma descrição mais detalhada e formatada para uso na página de produto do AppSource.
* Certifique-se de que o título do aplicativo usado no manifesto seja uma **combinação exata com** o título do aplicativo inserido no envio ao Partner Center. *Confira* [Criar listagem eficaz no Microsoft AppSource](https://docs.microsoft.com/office/dev/store/create-effective-office-store-listings#use-a-consistent-add-in-name)e no Office — Use um nome de complemento consistente.

## <a name="metadata-requirement"></a>Requisito de metadados

Os metadados a seguir são necessários para seu aplicativo.

|Dados|Tipo|Size|Manifesto|Centro de parceria|Descrição|
|---|---|---|---|---|---|
|Pacote do aplicativo|.zip|||✔|O pacote real do aplicativo para upload ou envio ao AppSource.|
|Logotipo de cor|.png|192 &times; 192 pixels|`icon.color`||O ícone a ser exibido na listagem da página do produto na galeria do Teams. Este é o logotipo completo do produto.|
|Contorno do logotipo|.png|32 &times; 32 pixels|`icon.outline`||O ícone a ser exibido no Teams, no canal de chat do Teams e em outros locais. Esse é o seu logotipo renderizado como um contorno branco com plano de fundo transparente.|
|Logotipo do aplicativo|.png, .jpg, .jpeg, .gif|300 &times; 300 pixels||✔|O ícone a ser exibido no AppSource. Este é o logotipo do produto em cores completas e é um arquivo diferente do usado no manifesto para `icon.color` . deve ser menor do que 512 KB.|
|Link de suporte|URL|||✔|Um link para material de suporte para usuários finais que podem não ter instalado seu aplicativo. Link publicamente disponível acessível sem nenhum logon (HTTPS).|
|Link de privacidade|URL||`developer.privacyUrl`|✔|Um link para sua política de privacidade (HTTPS).|
|Link de vídeo|URL|||Opcional|Um link para um vídeo sobre seu aplicativo.|
|EULA|.doc, .pdf, etc.|||Opcional|O AppSource requer um contrato de licenciamento do usuário final (EULA), que você pode fornecer como um anexo. Se você optar por não enviar um EULA, um será fornecido em seu nome.|
|Termos de serviço|URL||`developer.termsOfServiceUrl`||Um link para seus termos de serviço (HTTPS).|
|Notas de teste|Preencher em linha ou vincular a uma URL pública|||Notas de teste detalhadas sobre como testar seu aplicativo passo a passo. Inclua duas credenciais de logon para testar cenários de administrador e não administrador.|

## <a name="localized-content"></a>Conteúdo localizado

> [!NOTE]
> O AppSource planeja dar suporte a conteúdo localizado para os metadados a seguir. Atualmente, a listagem do aplicativo só será exibida em inglês no AppSource, mas será exibida corretamente localizada no cliente do Teams. Consulte [localizando seu aplicativo](~/concepts/build-and-test/apps-localization.md) para obter mais informações.

|Dados|Tipo|Size|Manifesto|Centro de parceria|Descrição|
|---|---|---|---|---|---|
|Nome do aplicativo|Cadeia de Caracteres|30|`name.short`|✔|O nome do seu aplicativo como ele deve aparecer na loja e no produto.|
|Nome longo do aplicativo|Cadeia de Caracteres|30|`name.full`|✔|O nome do seu aplicativo como ele deve aparecer na loja e no produto.|
|Descrição breve|Cadeia de Caracteres|80|`description.short`|✔|Breve descrição do seu aplicativo.|
|Descrição longa|Cadeia de Caracteres|4000|`description.full`|✔|Uma descrição mais detalhada do seu aplicativo. No arquivo de manifesto, um resumo preciso é adequado. No Partner Center, você pode usar uma descrição mais rica e formatada para a página de produto do AppSource.|
|Capturas de tela (1 a 5)|.png, .jpg ou .gif|1366w x 768h e menor que 1024 KB||✔|Pelo menos uma captura de tela que mostre a experiência do aplicativo. Usa na página de detalhes do aplicativo.|

## <a name="submission-extras-for-bots"></a>Envio de extras para bots

Os bots no Microsoft Teams devem ser criados usando o Bot Framework. Consulte [Criar um bot](~/bots/how-to/create-a-bot-for-teams.md) para obter instruções. Use um ícone de cor 96x96 para o ícone do bot no Bot Framework.
