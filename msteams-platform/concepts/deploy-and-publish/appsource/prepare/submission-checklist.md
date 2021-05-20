---
title: Preparar o envio para a Microsoft Store
description: Descreve os passos finais antes de enviar seu aplicativo Microsoft Teams a ser listado na loja.
ms.topic: how-to
localization_priority: Normal
author: heath-hamilton
ms.author: surbhigupta
ms.openlocfilehash: 975d3ef8fc8bdc8d6d7c336cf3a61a3a42ef5315
ms.sourcegitcommit: 51e4a1464ea58c254ad6bd0317aca03ebf6bf1f6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2021
ms.locfileid: "52566030"
---
# <a name="prepare-your-microsoft-teams-store-submission"></a>Prepare sua submissão de loja de Microsoft Teams

Você projetou, construiu e testou seu aplicativo de Microsoft Teams. Agora você está pronto para listá-lo para que as pessoas possam descobrir e começar a usar o seu aplicativo.

Antes de enviar seu aplicativo para o [Partner Center,](/office/dev/store/use-partner-center-to-submit-to-appsource)certifique-se de ter feito o seguinte.

## <a name="validate-your-app-package"></a>Valide seu pacote de aplicativos

Embora seu aplicativo possa estar funcionando em um ambiente de teste, você deve verificar seu pacote de aplicativos para evitar problemas durante o processo de envio.

A ferramenta de validação de aplicativos Microsoft Teams ajuda a identificar e corrigir problemas antes de se submeter à Central de Parceiros. A ferramenta verifica automaticamente as configurações do seu aplicativo em relação aos mesmos casos de teste usados durante a validação da loja.

1. Acesse a [ferramenta de validação de aplicativos Microsoft Teams](https://dev.teams.microsoft.com/appvalidation.html). (Nota: A ferramenta também está disponível no [App Studio](../../../build-and-test/app-studio-overview.md).)
1. Upload seu pacote de aplicativos para executar os testes automatizados.
1. Vá para a **lista preliminar** e revise os casos de teste difíceis de automatizar.
1. [Corrija problemas com suas configurações](~/resources/schema/manifest-schema.md) ou aplicativo em geral se os testes automatizados lhe derem erros ou você não tiver atendido todos os critérios na lista de verificação.

## <a name="compile-testing-instructions"></a>Compilar instruções de teste

Forneça instruções e recursos para ajudar os revisores a testar seu aplicativo, incluindo contas de teste, credenciais e chaves de licença. Você pode adicionar instruções no Partner Center ou enviá-las para um local disponível publicamente em SharePoint.

### <a name="feature-list"></a>Lista de recursos

Forneça detalhes sobre os recursos do seu aplicativo em Teams e passos para testar cada um.

### <a name="accounts"></a>Contas

Você deve fornecer contas de teste se o seu aplicativo exigir uma licença ou fazer backup da lista de segurança. Todas as contas que você fornece devem incluir dados pré-preenchidos para facilitar o teste.

Dependendo dos recursos do seu aplicativo, você pode precisar fornecer todos os seguintes:

* Conta de administração (necessária)
* Conta de administração não (necessária)
* Uma conta que não está pré-configurada para testar adequadamente a experiência de login de primeira execução (necessária)
* Uma conta com acesso a recursos premium ou atualizados (se aplicável)
* Duas contas no mesmo inquilino para testar a experiência de colaboração de aplicativos que funcionam em contextos compartilhados (se aplicável)

### <a name="tenant-configurations"></a>Configurações de inquilinos

Se você deve configurar um inquilino Teams para usar seu aplicativo, inclua essas instruções e contas de administração e não administradores para validação.

### <a name="video-optional"></a>Vídeo (opcional)

Forneça uma gravação do seu aplicativo para que a Microsoft possa entender completamente sua funcionalidade.

## <a name="create-your-store-listing-details"></a>Crie detalhes de listagem de sua loja

As informações que você envia para o [Partner Center](https://partner.microsoft.com)&#8212;incluindo seu nome, descrições, ícones e imagens&#8212;se torna a Teams loja e a listagem do Microsoft AppSource para o seu aplicativo.

Uma lista de lojas pode ser a primeira impressão de alguém do seu aplicativo. Aumente as instalações com uma listagem que transmite efetivamente os benefícios, funcionalidades e marca do seu aplicativo.

### <a name="specify-a-short-name"></a>Especifique um nome curto

O nome do seu aplicativo (especificamente, seu [*nome curto*](~/resources/schema/manifest-schema.md#name)) desempenha um papel crucial na forma como os usuários o descobrem na loja.

:::row:::

   :::column span="3":::
      :::image type="content" source="../../../../assets/images/store-detail-page/AppName-02.png" alt-text="Exemplos de captura de tela destacam onde o nome curto de um aplicativo é exibido em uma listagem de loja.":::
   :::column-end:::
   :::column span="1":::
   :::column-end:::

:::row-end:::

Certifique-se de que seu nome curto adere às [diretrizes de validação](~/concepts/deploy-and-publish/appsource/prepare/teams-store-validation-guidelines.md#11-app-name)da loja .

### <a name="write-descriptions"></a>Escrever descrições

Você deve ter uma descrição curta e longa do seu aplicativo.

#### <a name="short-description"></a>Descrição breve

Um resumo conciso do seu aplicativo que deve ser original, envolvente e direcionado ao seu público-alvo. Mantenha a descrição curta para uma frase.

:::row:::

   :::column span="3":::
      :::image type="content" source="~/assets/images/store-detail-page/ShortDescription-02.png" alt-text="Exemplos de captura de tela destacam onde a descrição curta de um aplicativo é exibida em uma listagem de loja.":::
   :::column-end:::
   :::column span="1":::
   :::column-end:::

:::row-end:::

Certifique-se de que sua descrição curta adere às [diretrizes de validação](~/concepts/deploy-and-publish/appsource/prepare/teams-store-validation-guidelines.md#431-short-description)da loja .

#### <a name="long-description"></a>Descrição longa

A longa descrição pode fornecer uma narrativa que destaca as principais características do seu aplicativo, os problemas que ele resolve e seu público-alvo. Embora esta descrição possa ser de até 4.000 caracteres, a maioria dos usuários só lerá entre 300-500 palavras.

:::row:::

   :::column span="3":::
      :::image type="content" source="~/assets/images/store-detail-page/LongDescription-02.png" alt-text="Exemplos de captura de tela destacam onde a longa descrição de um aplicativo é exibida em uma listagem de loja.":::
   :::column-end:::
   :::column span="1":::
   :::column-end:::

:::row-end:::

Certifique-se de que sua longa descrição adere às [diretrizes de validação](~/concepts/deploy-and-publish/appsource/prepare/teams-store-validation-guidelines.md#432-long-description)da loja .

### <a name="adhere-to-icon-design-guidelines"></a>Adere às diretrizes de design de ícones

Ícones são um dos principais elementos que os usuários vêem ao navegar na loja. Seus ícones devem comunicar a marca e o propósito do seu aplicativo, ao mesmo tempo em que adsuem aos requisitos Teams.

Para obter mais informações, consulte [orientações sobre a criação de ícones de aplicativos Teams](~/concepts/build-and-test/apps-package.md#app-icons).

### <a name="capture-screenshots"></a>Capturar capturas de tela

As capturas de tela fornecem uma visualização visual proeminente do seu aplicativo para complementar o nome do aplicativo, o ícone e as descrições.

:::row:::

   :::column span="3":::
      :::image type="content" source="~/assets/images/store-detail-page/Screenshot-01.png" alt-text="Exemplos de captura de tela destacam onde capturas de tela de aplicativos são exibidas em uma listagem de loja.":::
   :::column-end:::
   :::column span="1":::
   :::column-end:::

:::row-end:::

Lembre-se dos seguintes capturas de tela:

* Você pode ter até cinco capturas de tela por listagem.
* Os tipos de arquivos suportados incluem PNG, JPEG e GIF.
* As dimensões devem ser de 1366x768 pixels.
* Tamanho máximo de 1.024 KB.

Para obter as melhores práticas, consulte os seguintes recursos:

* [Teams diretrizes de validação de lojas](~/concepts/deploy-and-publish/appsource/prepare/teams-store-validation-guidelines.md#44-screenshots)
* [Criar imagens eficazes para lojas de aplicativos da Microsoft](/office/dev/store/craft-effective-appsource-store-images)

### <a name="create-a-video"></a>Crie um vídeo

Um vídeo em sua listagem pode ser a maneira mais eficaz de comunicar por que as pessoas devem usar seu aplicativo. Você deve abordar as seguintes perguntas em um vídeo:

* Who é o seu aplicativo?
* Quais problemas seu aplicativo pode resolver?
* Como funciona seu aplicativo?
* Que outros benefícios você recebe com o uso do seu aplicativo?

#### <a name="best-practices-for-videos"></a>Melhores práticas para vídeos

* Mantenha seu vídeo entre 30 e 90 segundos.
* Mire na qualidade. Em uma listagem, os usuários verão seu vídeo antes das capturas de tela.

### <a name="select-a-category-for-your-app"></a>Selecione uma categoria para o seu aplicativo

Durante a apresentação, você é solicitado a categorizar seu aplicativo. Os mapas de tabela a seguir Teams categorias de loja para as categorias listadas no [Partner Center](https://aka.ms/PartnerCenterHomePage).

| categorias Teams       | Categorias do Centro de Parceiros  |
|:---------------------|:---------------|
| Analytics e BI | Analytics, Visualização de Dados e BI |
| Desenvolvedor e TI | Ferramentas de desenvolvedor, administrador de TI |
| Educação | Educação |
| Recursos humanos | Recursos Humanos e Recrutamento |
| Produtividade | Gerenciamento de Conteúdo, Arquivos e documentos, Produtividade, Treinamento e Tutoriais e Utilidades |
| Gerenciamento de projeto | Comunicação, Gestão de Project, Fluxo de Trabalho e Gestão de Negócios |
| Vendas e suporte | Gestão de Clientes e Contatos, Suporte ao Cliente, Gestão Financeira, Vendas e Marketing |
| Social e divertido | Galerias de Imagens e Vídeos, Estilo de Vida, Notícias e Clima, Social, Viagem e Navegação |

### <a name="localize-your-store-listing"></a>Localize sua lista de lojas

O Partner Center suporta [listagens localizadas de lojas](/office/dev/store/prepare-localized-solutions). Para obter mais informações, consulte [como localizar sua lista de aplicativos Teams](../../../../concepts/build-and-test/apps-localization.md).

## <a name="complete-publisher-verification"></a>Verificação completa de Publisher

[Publisher Verificação](/azure/active-directory/develop/publisher-verification-overview) é necessária para Teams aplicativos listados na loja. Para obter mais informações, consulte [perguntas frequentes,](/azure/active-directory/develop/publisher-verification-overview#frequently-asked-questions) [como marcar seu aplicativo como editor verificado](/azure/active-directory/develop/mark-app-as-publisher-verified)e [solucionar problemas de verificação do editor](/azure/active-directory/develop/troubleshoot-publisher-verification).

## <a name="complete-publisher-attestation"></a>Attestation completo de Publisher

[Publisher Attestation](/microsoft-365-app-certification/docs/attestation) também é necessário para Teams aplicativos listados na loja. O processo inclui completar uma autoavaliação das práticas de segurança, manipulação de dados e conformidade do seu aplicativo que podem ajudar potenciais clientes a tomar decisões informadas sobre o uso do seu aplicativo.

> [!NOTE]
> Se você está enviando um novo aplicativo, você não pode completar oficialmente Publisher Attestation até que seu aplicativo esteja listado na loja Teams. Se você estiver atualizando um aplicativo listado, complete Publisher Attestation antes de enviar a versão mais recente do aplicativo para validação.

## <a name="next-step"></a>Próxima etapa

> [!div class="nextstepaction"]
> [Enviar seu aplicativo](/office/dev/store/add-in-submission-guide)
