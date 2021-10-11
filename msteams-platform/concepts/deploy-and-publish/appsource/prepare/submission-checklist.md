---
title: Preparar o envio para a Microsoft Store
description: Descreve as etapas finais antes de enviar seu Microsoft Teams aplicativo para ser listado na loja.
ms.topic: how-to
ms.localizationpriority: medium
author: heath-hamilton
ms.author: surbhigupta
ms.openlocfilehash: 8ff8282ae54612c0e1eee1d353777e5dae0b7990
ms.sourcegitcommit: c04a1a792773a9d5c61169c5702d94a8c478ad1c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/11/2021
ms.locfileid: "60260537"
---
# <a name="prepare-your-microsoft-teams-store-submission"></a>Preparar seu envio Microsoft Teams de armazenamento de dados

Você projetou, criou e testou seu Microsoft Teams aplicativo. Agora você está pronto para listá-lo para que as pessoas possam descobrir e começar a usar seu aplicativo.

Antes de enviar seu aplicativo para [o Partner Center,](/office/dev/store/use-partner-center-to-submit-to-appsource)certifique-se de ter feito o seguinte.

## <a name="validate-your-app-package"></a>Validar seu pacote de aplicativos

Embora seu aplicativo possa estar funcionando em um ambiente de teste, você deve verificar o pacote do aplicativo para evitar problemas durante o processo de envio.

> [!NOTE]
>  O App Studio será preterido em breve. Configurar, distribuir e gerenciar seus aplicativos Teams com o novo [Portal do Desenvolvedor](https://dev.teams.microsoft.com/)

A Microsoft Teams de validação de aplicativo ajuda você a identificar e corrigir problemas antes de enviar ao Partner Center. A ferramenta verifica automaticamente as configurações do aplicativo em relação aos mesmos casos de teste usados durante a validação do armazenamento.

1. Vá para [Microsoft Teams de validação de aplicativos](https://dev.teams.microsoft.com/validation) no portal do desenvolvedor. 
    > [!NOTE]
    > A ferramenta de validação de aplicativo também está disponível no [App Studio.](../../../build-and-test/app-studio-overview.md)
1. Upload pacote do aplicativo para executar os testes automatizados.
1. Vá para **a lista de verificação Preliminar** e revise os casos de teste difíceis de automatizar.
1. [Correção de problemas com suas configurações](~/resources/schema/manifest-schema.md) ou aplicativos em geral. Esses problemas ocorrerão se os testes automatizados lhe deem erros ou se você não tiver atendido a todos os critérios na lista de verificação.

## <a name="compile-testing-instructions"></a>Compilar instruções de teste

Forneça instruções e recursos para ajudar os revisadores a testar seu aplicativo, incluindo:
* Contas de teste
* Credenciais
* Chaves de licença

Você pode adicionar instruções no Partner Center ou enviá-las para um local disponível publicamente SharePoint.

### <a name="feature-list"></a>Lista de recursos

Forneça detalhes sobre os recursos do seu aplicativo em Teams e etapas para testar cada um deles.

### <a name="accounts"></a>Contas

Forneça contas de teste se seu aplicativo exigir uma licença ou listagem segura de back-end. Todas as contas fornecidas devem incluir dados pré-preenchidos para ajudar no teste.

Dependendo dos recursos do aplicativo, talvez seja necessário fornecer todas as seguintes contas:

* Conta de administrador (necessária)
* Conta não administrativa (necessária)
* Uma conta que não está pré-configurada para testar corretamente a experiência de login da primeira vez (necessária)
* Uma conta com acesso a recursos premium ou atualizados (se aplicável)
* Duas contas no mesmo locatário para testar a experiência de colaboração para aplicativos que funcionam em contextos compartilhados (se aplicável)

### <a name="tenant-configurations"></a>Configurações de locatário

Se você deve configurar um locatário Teams usar seu aplicativo, inclua essas instruções e contas de administrador e não administrador para validação.

### <a name="video-optional"></a>Vídeo (opcional)

Forneça uma gravação do seu aplicativo para que a Microsoft possa entender totalmente sua funcionalidade.

## <a name="create-your-store-listing-details"></a>Criar detalhes de listagem da loja

As informações que você envia ao [Partner Center](https://partner.microsoft.com)&#8212;incluindo seu nome, descrições, ícones e imagens&#8212;se tornam a Teams store e a listagem do Microsoft AppSource para seu aplicativo.

Uma listagem da loja pode ser a primeira impressão de alguém do seu aplicativo. Aumente as instalações com uma listagem que transmite efetivamente os benefícios, a funcionalidade e a marca do seu aplicativo.

### <a name="specify-a-short-name"></a>Especificar um nome curto

O nome do seu aplicativo (especificamente, seu [*nome*](~/resources/schema/manifest-schema.md#name)curto ) desempenha uma função crucial na forma como os usuários o descobrem na loja.

:::row:::

   :::column span="3":::
      :::image type="content" source="../../../../assets/images/store-detail-page/AppName-02.png" alt-text="Exemplo de captura de tela realça onde o nome curto de um aplicativo é exibido em uma listagem da loja.":::
   :::column-end:::
   :::column span="1":::
   :::column-end:::

:::row-end:::

Certifique-se de que seu nome curto adera às diretrizes [de validação da loja.](~/concepts/deploy-and-publish/appsource/prepare/teams-store-validation-guidelines.md#app-name)

### <a name="write-descriptions"></a>Descrições de gravação

Você deve ter uma descrição curta e longa do seu aplicativo.

#### <a name="short-description"></a>Descrição breve

Um resumo conciso do seu aplicativo que deve ser original, envolvente e direcionado para seu público-alvo. Manter a descrição curta em uma frase.

:::row:::

   :::column span="3":::
      :::image type="content" source="~/assets/images/store-detail-page/ShortDescription-02.png" alt-text="Exemplo de captura de tela realça onde a descrição curta de um aplicativo é exibida em uma listagem da loja.":::
   :::column-end:::
   :::column span="1":::
   :::column-end:::

:::row-end:::

Certifique-se de que sua breve descrição segue as diretrizes [de validação da loja.](~/concepts/deploy-and-publish/appsource/prepare/teams-store-validation-guidelines.md#short-description)

#### <a name="long-description"></a>Descrição longa

A descrição longa pode fornecer uma narração que realça seus aplicativos':

* Principais recursos
* Os problemas que ele resolve
* Público-alvo

Embora essa descrição possa ter até 4.000 caracteres, a maioria dos usuários lerá apenas entre 300 e 500 palavras.

:::row:::

   :::column span="3":::
      :::image type="content" source="~/assets/images/store-detail-page/LongDescription-02.png" alt-text="Exemplo de captura de tela realça onde a descrição longa de um aplicativo é exibida em uma listagem da loja.":::
   :::column-end:::
   :::column span="1":::
   :::column-end:::

:::row-end:::

Certifique-se de que sua descrição longa segue as diretrizes de validação [da loja.](~/concepts/deploy-and-publish/appsource/prepare/teams-store-validation-guidelines.md#long-description)

### <a name="adhere-to-icon-design-guidelines"></a>Seguir as diretrizes de design de ícones

Os ícones são um dos principais elementos que os usuários veem ao navegar na loja. Seus ícones devem comunicar a marca e a finalidade do seu aplicativo enquanto também aderem aos requisitos Teams.

Para obter mais informações, consulte [diretrizes sobre como criar Teams ícones de aplicativo.](~/concepts/build-and-test/apps-package.md#app-icons)

### <a name="capture-screenshots"></a>Capturar capturas de tela

As capturas de tela fornecem uma visualização panorâmica proeminente do seu aplicativo para complementar seu nome, ícone e descrições.

:::row:::

   :::column span="3":::
      :::image type="content" source="~/assets/images/store-detail-page/Screenshot-01.png" alt-text="Exemplo de realçamentos de captura de tela onde as capturas de tela do aplicativo são exibidas em uma listagem da loja.":::
   :::column-end:::
   :::column span="1":::
   :::column-end:::

:::row-end:::

Lembre-se das seguintes práticas recomendadas sobre capturas de tela:

* Você pode ter até cinco capturas de tela por lista.
* Os tipos de arquivo com suporte incluem PNG, JPEG e GIF.
* As dimensões devem ter 1366x768 pixels.
* Tamanho máximo de 1.024 KB.

Para ver as práticas recomendadas, consulte os seguintes recursos:

* [Teams Diretrizes de validação da Loja](~/concepts/deploy-and-publish/appsource/prepare/teams-store-validation-guidelines.md#screenshots)
* [Criar imagens efetivas para os armazenamentos de aplicativos da Microsoft](/office/dev/store/craft-effective-appsource-store-images)

### <a name="create-a-video"></a>Criar um vídeo

Um vídeo em sua listagem pode ser a maneira mais eficaz de comunicar por que as pessoas devem usar seu aplicativo. Resolver as seguintes perguntas em um vídeo:

* Who seu aplicativo é para?
* Quais problemas seu aplicativo pode resolver?
* Como seu aplicativo funciona?
* Quais outros benefícios você obter com o uso do aplicativo?

Você pode adicionar uma URL para seu vídeo do YouTube ou vimeo.

#### <a name="best-practices-for-videos"></a>Práticas recomendadas para vídeos

* Mantenha seu vídeo entre 60 e 90 segundos.
* Aponte para a qualidade. Em uma listagem, os usuários verão seu vídeo antes das capturas de tela.
* Comunicar o valor do produto em forma de narração.
* Demonstre como o produto funciona.

### <a name="select-a-category-for-your-app"></a>Selecione uma categoria para seu aplicativo

Durante o envio, você é solicitado a categorizar seu aplicativo. A tabela a seguir mapeia Teams categorias da Loja para as categorias listadas no [Partner Center](https://aka.ms/PartnerCenterHomePage).

| Teams categorias       | Categorias do Partner Center  |
|:---------------------|:---------------|
| Análise e BI | Análise, Visualização de Dados e BI |
| Desenvolvedor e IT | Ferramentas de Desenvolvedor, Administrador de IT |
| Educação | Educação |
| Recursos humanos | Recursos Humanos e Recrutamento |
| Produtividade | Gerenciamento de Conteúdo, Arquivos e documentos, Produtividade, Treinamento e Tutoriais e Utilitários |
| Gerenciamento de projeto | Comunicação, Project Gerenciamento, Fluxo de Trabalho e Gerenciamento de Negócios |
| Vendas e suporte | Gerenciamento de Clientes e Contatos, Suporte ao Cliente, Gerenciamento Financeiro e Vendas e Marketing |
| Social e divertido | Galerias de imagem e vídeo, estilo de vida, notícias e clima, social, viagem e navegação |

### <a name="localize-your-store-listing"></a>Localize sua listagem da loja

O Partner Center dá [suporte a listagens de armazenamento localizado.](/office/dev/store/prepare-localized-solutions) Para obter mais informações, [consulte como localizar sua Teams de aplicativos](../../../../concepts/build-and-test/apps-localization.md).

## <a name="complete-publisher-verification"></a>Concluir Publisher Verificação

[Publisher Verificação](/azure/active-directory/develop/publisher-verification-overview) é necessária para Teams aplicativos listados na loja. Para obter mais informações, consulte [perguntas frequentes](/azure/active-directory/develop/publisher-verification-overview#frequently-asked-questions), [como marcar seu aplicativo como publicador verificado](/azure/active-directory/develop/mark-app-as-publisher-verified)e [solução de problemas de verificação do editor](/azure/active-directory/develop/troubleshoot-publisher-verification).

## <a name="complete-publisher-attestation"></a>Concluir Publisher Atestado

[Publisher Atestado](/microsoft-365-app-certification/docs/attestation) também é necessário para aplicativos Teams listados na Loja. O processo inclui a conclusão de uma autoavaliação das práticas de segurança, tratamento de dados e conformidade do aplicativo. O processo pode ajudar os clientes em potencial a tomar decisões informadas sobre como usar seu aplicativo.

> [!NOTE]
> Se você estiver enviando um novo aplicativo, não poderá concluir oficialmente Publisher Atestado até que seu aplicativo seja listado na Teams store. Se você estiver atualizando um aplicativo listado, conclua Publisher Atestado antes de enviar a versão mais recente do aplicativo para validação.

## <a name="next-step"></a>Próxima etapa

> [!div class="nextstepaction"]
> [Enviar seu aplicativo](/office/dev/store/add-in-submission-guide)
