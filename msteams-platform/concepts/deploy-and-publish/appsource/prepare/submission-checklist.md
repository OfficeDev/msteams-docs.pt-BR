---
title: Preparar o envio para a Microsoft Store
description: Descreve as etapas finais antes de enviar seu Microsoft Teams aplicativo para ser listado na loja.
ms.topic: how-to
localization_priority: Normal
author: heath-hamilton
ms.author: surbhigupta
ms.openlocfilehash: f73e36ca0587768421daf60229d0a241cae171e1
ms.sourcegitcommit: 60561c7cd189c9d6fa5e09e0f2b6c24476f2dff5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/06/2021
ms.locfileid: "52230936"
---
# <a name="prepare-your-microsoft-teams-store-submission"></a>Preparar seu envio Microsoft Teams de armazenamento de dados

Você projetou, criou e testou seu Microsoft Teams aplicativo. Agora você está pronto para listá-lo para que as pessoas possam descobrir e começar a usar seu aplicativo.

Antes de enviar seu aplicativo para [o Partner Center,](/office/dev/store/use-partner-center-to-submit-to-appsource)certifique-se de ter feito o seguinte.

## <a name="validate-your-app-package"></a>Validar seu pacote de aplicativos

Embora seu aplicativo possa estar funcionando em um ambiente de teste, você deve verificar o pacote do aplicativo para evitar problemas durante o processo de envio.

A Microsoft Teams de validação de aplicativo ajuda você a identificar e corrigir problemas antes de enviar ao Partner Center. A ferramenta verifica automaticamente as configurações do aplicativo em relação aos mesmos casos de teste usados durante a validação do armazenamento.

1. Vá para a ferramenta [Microsoft Teams de validação de aplicativos](https://dev.teams.microsoft.com/appvalidation.html). (Observação: a ferramenta também está disponível no [App Studio](../../../build-and-test/app-studio-overview.md).)
1. Upload pacote do aplicativo para executar os testes automatizados.
1. Vá para **a lista de verificação Preliminar** e revise os casos de teste difíceis de automatizar.
1. [Correção de problemas](~/resources/schema/manifest-schema.md) com suas configurações ou aplicativos em geral se os testes automatizados lhe deem erros ou se você não tiver atendido a todos os critérios na lista de verificação.

## <a name="compile-testing-instructions"></a>Compilar instruções de teste

Forneça instruções e recursos para ajudar os revisadores a testar seu aplicativo, incluindo contas de teste, credenciais e chaves de licença. Você pode adicionar instruções no Partner Center ou enviá-las para um local disponível publicamente SharePoint.

### <a name="feature-list"></a>Lista de recursos

Forneça detalhes sobre os recursos do seu aplicativo em Teams e etapas para testar cada um deles.

### <a name="accounts"></a>Contas

Você deve fornecer contas de teste se seu aplicativo exigir uma licença ou uma lista segura de back-end. Todas as contas fornecidas devem incluir dados pré-preenchidos para facilitar o teste.

Dependendo dos recursos do seu aplicativo, talvez seja necessário fornecer todos os seguintes:

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

Certifique-se de que seu nome curto adera às diretrizes [de validação da loja.](~/concepts/deploy-and-publish/appsource/prepare/teams-store-validation-guidelines.md#11-app-name)

### <a name="write-descriptions"></a>Descrições de gravação

Você deve ter uma descrição curta e longa do seu aplicativo.

#### <a name="short-description"></a>Descrição breve

Um resumo conciso do seu aplicativo que deve ser original, envolvente e direcionado para seu público-alvo. Mantenha a descrição curta em uma frase.

:::row:::

   :::column span="3":::
      :::image type="content" source="~/assets/images/store-detail-page/ShortDescription-02.png" alt-text="Exemplo de captura de tela realça onde a descrição curta de um aplicativo é exibida em uma listagem da loja.":::
   :::column-end:::
   :::column span="1":::
   :::column-end:::

:::row-end:::

Certifique-se de que sua breve descrição segue as diretrizes [de validação da loja.](~/concepts/deploy-and-publish/appsource/prepare/teams-store-validation-guidelines.md#431-short-description)

#### <a name="long-description"></a>Descrição longa

A descrição longa pode fornecer uma narração que realça os principais recursos do aplicativo, os problemas que ele resolve e seu público-alvo. Embora essa descrição possa ter até 4.000 caracteres, a maioria dos usuários lerá apenas entre 300 e 500 palavras.

:::row:::

   :::column span="3":::
      :::image type="content" source="~/assets/images/store-detail-page/LongDescription-02.png" alt-text="Exemplo de captura de tela realça onde a descrição longa de um aplicativo é exibida em uma listagem da loja.":::
   :::column-end:::
   :::column span="1":::
   :::column-end:::

:::row-end:::

Certifique-se de que sua descrição longa segue as diretrizes de validação [da loja.](~/concepts/deploy-and-publish/appsource/prepare/teams-store-validation-guidelines.md#432-long-description)

### <a name="adhere-to-icon-design-guidelines"></a>Seguir as diretrizes de design de ícones

Os ícones são um dos principais elementos que os usuários veem ao navegar na loja. Seus ícones devem comunicar a marca e a finalidade do seu aplicativo enquanto também aderem aos requisitos Teams.

Para obter mais informações, consulte [diretrizes sobre como criar Teams ícones de aplicativo.](~/concepts/build-and-test/apps-package.md#app-icons)

### <a name="capture-screenshots"></a>Capturar capturas de tela

As capturas de tela fornecem uma visualização visual proeminente do seu aplicativo para complementar o nome, o ícone e as descrições do aplicativo.

:::row:::

   :::column span="3":::
      :::image type="content" source="~/assets/images/store-detail-page/Screenshot-01.png" alt-text="Exemplo de realçamentos de captura de tela onde as capturas de tela do aplicativo são exibidas em uma listagem da loja.":::
   :::column-end:::
   :::column span="1":::
   :::column-end:::

:::row-end:::

Lembre-se do seguinte sobre capturas de tela:

* Você pode ter até cinco capturas de tela por listagem.
* Os tipos de arquivo com suporte incluem PNG, JPEG e GIF.
* As dimensões devem ter 1366 x 768 pixels.
* Tamanho máximo de 1.024 KB.

Para ver as práticas recomendadas, consulte os seguintes recursos:

* [Teams de validação do armazenamento](~/concepts/deploy-and-publish/appsource/prepare/teams-store-validation-guidelines.md#44-screenshots)
* [Criar imagens efetivas para os armazenamentos de aplicativos da Microsoft](/office/dev/store/craft-effective-appsource-store-images)

### <a name="create-a-video"></a>Criar um vídeo

Um vídeo em sua listagem pode ser a maneira mais eficaz de comunicar por que as pessoas devem usar seu aplicativo. Você deve resolver as seguintes perguntas em um vídeo:

* Who seu aplicativo é para?
* Quais problemas seu aplicativo pode resolver?
* Como seu aplicativo funciona?
* Quais outros benefícios você obter com o uso do aplicativo?

#### <a name="best-practices-for-videos"></a>Práticas recomendadas para vídeos

* Mantenha seu vídeo entre 30 e 90 segundos.
* Aponte para a qualidade. Em uma listagem, os usuários verão seu vídeo antes das capturas de tela.

### <a name="select-a-category-for-your-app"></a>Selecione uma categoria para seu aplicativo

Durante o envio, você é solicitado a categorizar seu aplicativo. A tabela a seguir mapeia Teams categorias de armazenamento para as categorias listadas no [Partner Center](https://aka.ms/PartnerCenterHomePage).

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

### <a name="localize-your-store-listing"></a>Localize sua listagem da loja

O Partner Center dá [suporte a listagens de armazenamento localizado.](https://docs.microsoft.com/office/dev/store/prepare-localized-solutions) Para obter mais informações, [consulte como localizar sua Teams de aplicativos](../../../../concepts/build-and-test/apps-localization.md).

## <a name="complete-publisher-verification"></a>Concluir Publisher Verificação

[Publisher Verificação](/azure/active-directory/develop/publisher-verification-overview) é necessária para Teams aplicativos listados na loja. Para obter mais informações, [consulte perguntas frequentes](/azure/active-directory/develop/publisher-verification-overview#frequently-asked-questions), como marcar seu aplicativo como [editor verificado](/azure/active-directory/develop/mark-app-as-publisher-verified)e solucionar problemas de verificação [do editor.](/azure/active-directory/develop/troubleshoot-publisher-verification)

## <a name="complete-publisher-attestation"></a>Concluir Publisher Atestado

[Publisher Atestado](/microsoft-365-app-certification/docs/attestation) também é necessário para Teams aplicativos listados na loja. O processo inclui a conclusão de uma autoavaliação das práticas de segurança, tratamento de dados e conformidade do seu aplicativo que podem ajudar os clientes em potencial a tomar decisões informadas sobre o uso do aplicativo.

> [!NOTE]
> Se você estiver enviando um novo aplicativo, não poderá concluir oficialmente Publisher Atestado até que seu aplicativo seja listado na Teams store. Se você estiver atualizando um aplicativo listado, conclua Publisher Atestado antes de enviar a versão mais recente do aplicativo para validação.

## <a name="next-step"></a>Próxima etapa

> [!div class="nextstepaction"]
> [Enviar seu aplicativo](https://docs.microsoft.com/office/dev/store/add-in-submission-guide)
