---
title: Preparar o envio para a Microsoft Store
description: Aprenda as etapas finais antes de enviar seu aplicativo do Microsoft Teams para ser listado na loja. Saiba como validar seu pacote de aplicativos e muito mais.
ms.topic: how-to
ms.localizationpriority: high
author: heath-hamilton
ms.author: surbhigupta
ms.openlocfilehash: 95d30f025856b7466fd66a71b3dcbba4b4738452
ms.sourcegitcommit: 4d1740b235000d51711a9170ac0f026c63c945ac
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/04/2022
ms.locfileid: "66611503"
---
# <a name="prepare-your-teams-store-submission"></a>Preparar o envio do repositório do Teams

Você projetou, compilou e testou seu aplicativo do Microsoft Teams. Agora você está pronto para listá-lo e permitir que as pessoas descubram e comecem a usar seu aplicativo.

Veja o vídeo a seguir para saber mais sobre a publicação de seu aplicativo na loja de aplicativos do Microsoft Teams:
<br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4WG3l]
<br>

Antes de enviar seu aplicativo para a [Central de Parceiros](/office/dev/store/use-partner-center-to-submit-to-appsource), certifique-se de ter feito o seguinte.

## <a name="validate-your-app-package"></a>Validar seu pacote de aplicativos

Embora seu aplicativo possa estar funcionando em um ambiente de teste, você deve verificar o pacote do aplicativo para evitar ter problemas durante o processo de envio.

> [!WARNING]
> Se você estiver usando o App Studio, recomendamos que você tente o [Portal do Desenvolvedor](https://dev.teams.microsoft.com/) para configurar, distribuir e gerenciar seus aplicativos do Teams. O App Studio será preterido até 30 de junho de 2022.

A ferramenta de validação de aplicativos do Microsoft Teams ajuda você a identificar e corrigir problemas antes de enviar para o Partner Center. A ferramenta verifica automaticamente as configurações do aplicativo comparando-as aos mesmos casos de teste usados durante a validação do repositório.

1. Vá para a [Ferramenta de validação de aplicativos do Microsoft Teams](https://dev.teams.microsoft.com/appvalidation.html). (Observação: a ferramenta também está disponível no [App Studio](../../../build-and-test/app-studio-overview.md).)
1. Carregue o pacote do aplicativo para executar os testes automatizados.
1. Vá para a **Lista de verificação preliminar** e analise os casos de teste que são difíceis de automatizar.
1. [Corrigir problemas com suas configurações](~/resources/schema/manifest-schema.md) ou aplicativo em geral. Esses problemas ocorrerão se os testes automatizados apresentarem erros ou se você não tiver atendido a todos os critérios da lista de verificação.

## <a name="compile-testing-instructions"></a>Compilar as instruções de teste

Forneça instruções e recursos para ajudar os revisores a testarem seu aplicativo, incluindo:

* Contas de teste
* Credenciais
* Chaves de licença

Você pode adicionar instruções no Partner Center ou carregá-las em um local disponível publicamente no SharePoint.

### <a name="feature-list"></a>Lista de recursos

Forneça detalhes sobre os recursos do seu aplicativo no Teams e as etapas para testar cada um deles.

### <a name="accounts"></a>Contas

Forneça contas de teste se o seu aplicativo exigir uma licença ou uma listagem de segurança do back-end. Todas as contas fornecidas devem incluir dados preenchidos previamente para ajudar no teste.

Dependendo dos recursos do aplicativo, talvez seja necessário fornecer todas as contas a seguir:

* Conta de administrador (obrigatória)
* Conta de usuário não administrador (obrigatória)
* Uma conta que não esteja pré-configurada para testar corretamente a primeira experiência de entrada no aplicativo (obrigatória)
* Uma conta com acesso a recursos premium ou atualizados (se aplicável)
* Duas contas no mesmo locatário para testar a experiência de colaboração para aplicativos que funcionam em contextos compartilhados (se aplicável)

### <a name="tenant-configurations"></a>Configurações de locatário

Se você precisar configurar um locatário do Teams para usar seu aplicativo, inclua essas instruções e contas de administrador e não administrador para validação.

### <a name="video-optional"></a>Vídeo (opcional)

Forneça uma gravação do seu aplicativo para que a Microsoft possa entender totalmente sua funcionalidade.

## <a name="create-your-store-listing-details"></a>Criar os detalhes da sua listagem na loja

As informações que você envia para o [Partner Center](https://partner.microsoft.com)&#8212;incluindo seu nome, descrições, ícones e imagens&#8212;se transformam na listagem do seu aplicativo na Teams Store e no AppSource da Microsoft.

A listagem na loja pode ser a primeira impressão que uma pessoa tem do seu aplicativo. Aumente o número de instalações com uma listagem que transmita as vantagens, a funcionalidade e a marca do seu aplicativo de forma eficaz.

### <a name="specify-a-short-name"></a>Especificar um nome curto

O nome do seu aplicativo (especificamente o *[nome curto](~/resources/schema/manifest-schema.md#name)*) desempenha um papel crucial na forma como os usuários irão descobri-lo na loja.

:::row:::

:::column span="3":::
:::image type="content" source="../../../../assets/images/store-detail-page/AppName-02.png" alt-text="A amostra de captura de tela destaca onde o nome curto de um aplicativo é exibido em uma listagem da loja.":::
:::column-end:::
:::column span="1":::
:::column-end:::

:::row-end:::

Certifique-se de que seu nome curto cumpra as [diretrizes de validação da loja](~/concepts/deploy-and-publish/appsource/prepare/teams-store-validation-guidelines.md#app-name).

### <a name="write-descriptions"></a>Redação das descrições

Você deve ter uma descrição curta e longa do seu aplicativo.

#### <a name="short-description"></a>Descrição curta

Um resumo conciso do seu aplicativo que deve ser original, envolvente e direcionado ao seu público-alvo. Mantenha a descrição curta em uma frase.

:::row:::

:::column span="3":::
:::image type="content" source="~/assets/images/store-detail-page/ShortDescription-02.png" alt-text="A amostra de captura de tela destaca onde a descrição curta de um aplicativo aparece em uma listagem na loja.":::
:::column-end:::
:::column span="1":::
:::column-end:::

:::row-end:::

Certifique-se de que sua descrição curta cumpra as [diretrizes de validação da loja](~/concepts/deploy-and-publish/appsource/prepare/teams-store-validation-guidelines.md#short-description).

#### <a name="long-description"></a>Descrição longa

A descrição longa pode fornecer uma narrativa que dê destaque às seguintes características dos seus aplicativos:

* Principais recursos
* Os problemas que soluciona
* Público-alvo

Embora essa descrição possa ter até 4.000 caracteres, a maioria dos usuários lerá apenas entre 300 e 500 palavras.

:::row:::

:::column span="3":::
:::image type="content" source="~/assets/images/store-detail-page/LongDescription-02.png" alt-text="A amostra de captura de tela destaca onde a descrição longa de um aplicativo aparece em uma listagem na loja.":::
:::column-end:::
:::column span="1":::
:::column-end:::

:::row-end:::

Certifique-se de que sua descrição longa cumpra as [diretrizes de validação da loja](~/concepts/deploy-and-publish/appsource/prepare/teams-store-validation-guidelines.md#long-description).

### <a name="adhere-to-icon-design-guidelines"></a>Cumprir as diretrizes de design de ícones

O ícone é um dos principais elementos que os usuários veem ao navegar na loja. Seus ícones devem comunicar a marca e a finalidade do seu aplicativo e, ao mesmo tempo, cumprir os requisitos do Teams.

Para obter mais informações, consulte as [diretrizes para a criação de ícones de aplicativos do Teams](~/concepts/build-and-test/apps-package.md#app-icons).

### <a name="capture-screenshots"></a>Fazer capturas de tela

As capturas de tela fornecem uma visualização panorâmica proeminente do seu aplicativo para complementar seu nome, ícone e descrições.

:::row:::

:::column span="3":::
:::image type="content" source="~/assets/images/store-detail-page/Screenshot-01.png" alt-text="A amostra de captura de tela destaca onde as capturas de tela do aplicativo aparecem em uma listagem na loja.":::
:::column-end:::
:::column span="1":::
:::column-end:::

:::row-end:::

Lembre-se de seguir as práticas recomendadas para capturas de tela:

* Você pode ter até cinco capturas de tela por listagem.
* Os tipos de arquivo com suporte incluem os formatos de imagem .png, .jpeg e gif.
* As dimensões devem ser 1366 x 768 pixels.
* Tamanho máximo de 1.024 KB.

Para obter informações sobre práticas recomendadas, consulte os seguintes recursos:

* [Diretrizes de validação da Teams Store](~/concepts/deploy-and-publish/appsource/prepare/teams-store-validation-guidelines.md#screenshots)
* [Elaborar imagens eficazes para as lojas de aplicativos da Microsoft](/office/dev/store/craft-effective-appsource-store-images)

### <a name="create-a-video"></a>Criar um vídeo

Um vídeo em sua listagem pode ser a maneira mais eficaz de comunicar por que as pessoas devem usar seu aplicativo. Responda as seguintes perguntas em um vídeo:

* A quem seu aplicativo se destina?
* Quais problemas seu aplicativo pode resolver?
* Como seu aplicativo funciona?
* Quais são as outras vantagens do uso de seu aplicativo?

Você pode adicionar um URL para o seu vídeo no YouTube ou no Vimeo.

#### <a name="best-practices-for-videos"></a>Práticas recomendadas para vídeos

* Limite seu vídeo a uma duração entre 60 e 90 segundos.
* Garanta a qualidade. Em uma listagem, os usuários verão seu vídeo antes das capturas de tela.
* Comunique o valor do produto de forma narrativa.
* Demonstre como o produto funciona.

### <a name="select-a-category-for-your-app"></a>Selecionar uma categoria para o seu aplicativo

Durante o envio, você será solicitado a categorizar seu aplicativo. A tabela a seguir mapeia as categorias da Teams Store e as compara às categorias listadas no [Partner Center](https://aka.ms/PartnerCenterHomePage).

| Categorias do Teams       | Categorias do Partner Center  |
|:---------------------|:---------------|
| Análise e BI | Análise, Visualização de Dados e BI |
| Desenvolvedor e TI | Ferramentas para Desenvolvedores, Administrador de TI |
| Educação | Educação |
| Recursos humanos | Recursos Humanos e Recrutamento |
| Produtividade | Gerenciamento de Conteúdo, Arquivos e documentos, Produtividade, Treinamento e Tutoriais e Utilitários |
| Gerenciamento de projeto | Comunicação, Gerenciamento de Projeto, Fluxo de Trabalho e Gerenciamento de Negócios |
| Vendas e suporte | Gerenciamento de Clientes e Contatos, Atendimento ao Cliente, Gerenciamento Financeiro e Vendas e Marketing |
| Redes sociais e diversão | Galerias de Imagens e Vídeos, Estilo de Vida, Notícias e Previsão do Tempo, Redes Sociais, Viagens e Navegação |

### <a name="localize-your-store-listing"></a>Localizar sua listagem na loja

O Partner Center dá suporte a [listagens de loja localizadas](/office/dev/store/prepare-localized-solutions). Para obter mais informações, consulte [como localizar sua listagem de aplicativos do Teams](../../../../concepts/build-and-test/apps-localization.md).

## <a name="complete-publisher-verification"></a>Executar a Verificação do Publisher

A [Verificação do Publisher](/azure/active-directory/develop/publisher-verification-overview) é obrigatória para os aplicativos do Teams listados na loja. Para obter mais informações, consulte [perguntas frequentes](/azure/active-directory/develop/publisher-verification-overview#frequently-asked-questions), [como marcar seu aplicativo como verificado pelo publisher](/azure/active-directory/develop/mark-app-as-publisher-verified)e [solução de problemas da verificação do publisher](/azure/active-directory/develop/troubleshoot-publisher-verification).

## <a name="complete-publisher-attestation"></a>Obter um Atestado do Publisher

Um [Atestado do Publisher](/microsoft-365-app-certification/docs/attestation) também é obrigatório para os aplicativos do Teams listados na loja. O processo inclui o preenchimento de uma autoavaliação das práticas de segurança, manipulação de dados e conformidade do seu aplicativo. O processo pode ajudar os possíveis clientes a tomarem decisões bem fundamentadas sobre como usar seu aplicativo.

> [!NOTE]
> Se estiver enviando um aplicativo novo, você não pode obter oficialmente o Atestado do Publisher antes de seu aplicativo estar listado na Teams Store. Se estiver atualizando um aplicativo listado, obtenha o Atestado do Publisher antes de enviar a versão mais recente do aplicativo para validação.

## <a name="next-step"></a>Próxima etapa

> [!div class="nextstepaction"]
> [Enviar seu aplicativo](/office/dev/store/add-in-submission-guide)

## <a name="see-also"></a>Confira também

[Resolver problemas se seu envio para a loja do Microsoft Teams falhar](~/concepts/deploy-and-publish/appsource/resolve-submission-issues.md)
