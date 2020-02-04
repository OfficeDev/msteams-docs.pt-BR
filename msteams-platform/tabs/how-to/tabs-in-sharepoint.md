---
title: Adicionando uma guia do Microsoft Teams no SharePoint como uma Web Part SPFx
author: laujan
description: Como implantar sua guia do teams existente no SharePoint como uma Web Part da estrutura do SharePoint.
keywords: guias do Microsoft Teams desenvolvimento do SharePoint Framework
ms.topic: conceptual
ms.author: ''
ms.openlocfilehash: b29cd29891779a69a0342f10d383792b3818590a
ms.sourcegitcommit: 4329a94918263c85d6c65ff401f571556b80307b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/01/2020
ms.locfileid: "41672687"
---
# <a name="adding-a-microsoft-teams-tab-in-sharepoint-as-an-spfx-web-part"></a>Adicionando uma guia do Microsoft Teams no SharePoint como uma Web Part SPFx

> [!IMPORTANT]
> Este recurso atualmente está em versão prévia e está sujeito a alterações. Não há suporte para uso em ambientes de produção. Agradecemos por seus comentários sobre essa funcionalidade na [lista de problemas de documentos de desenvolvimento do SharePoint](https://github.com/SharePoint/sp-dev-docs/issues).

## <a name="rich-integration-between-teams-and-sharepoint"></a>Integração avançada entre o Teams e o SharePoint

Com a edição de novembro do Teams e do SharePoint Framework v. 1,7, os desenvolvedores têm dois recursos avançados:

<ul  class="panelContent cardsC">
<li>
    <a href="#introduction">
        <div class="cardSize">
            <div class="cardPadding">
                <div class="card">
                    <div class="cardImageOuter">
                        <div class="cardImage bgdAccent1">
                            <img src="~/assets/images/tabs/tabs-in-sharepoint/image084.png" />
                        </div>
                    </div>
                    <div class="cardText">
                        <h3>Guias do teams no SharePoint</h3>
                        <p>Crie experiências de aplicativos avançados no SharePoint trazendo seu aplicativo do Microsoft Teams para o SharePoint (este artigo).</p>
                    </div>
                </div>
            </div>
        </div>
    </a>
</li>
<li>
    <a href="https://docs.microsoft.com/sharepoint/dev/spfx/web-parts/get-started/using-web-part-as-ms-teams-tab">
        <div class="cardSize">
            <div class="cardPadding">
                <div class="card">
                    <div class="cardImageOuter">
                        <div class="cardImage bgdAccent1">
                            <img src="~/assets/images/tabs/tabs-in-sharepoint/SharePoint-web-part-exposed-as-a-Tab-in-Microsoft-Teams.png" />
                        </div>
                    </div>
                    <div class="cardText">
                        <h3>Estrutura do SharePoint no Teams</h3>
                        <p>Traga suas Web Parts do SharePoint para o Microsoft Teams e permita que o SharePoint gerencie a hospedagem para você.</p>
                    </div>
                </div>
            </div>
        </div>
    </a>
</li>
</ul>

### <a name="teams-tabs-in-sharepoint"></a>Guias do teams no SharePoint

Com o SharePoint Framework v. 1.7, estamos dando suporte à capacidade dos desenvolvedores de usar suas guias de equipes e hospedá-lo no SharePoint. Como guias hospedados no SharePoint, obtenha uma experiência de "página inteira" semelhante, expondo todos os recursos das guias do teams enquanto mantém o contexto e a familiaridade de um site do SharePoint.

### <a name="sharepoint-framework-in-teams"></a>Estrutura do SharePoint no Teams

Você também pode implementar suas guias do Microsoft Teams usando o SharePoint Framework. Para desenvolvedores do SharePoint, isso simplifica significativamente o processo de desenvolvimento para guias do teams porque as Web Parts da estrutura do SharePoint são hospedadas no SharePoint sem necessidade de serviços externos, como o Azure. [Saiba mais sobre como usar a estrutura do SharePoint no Microsoft Teams.](/sharepoint/dev/spfx/web-parts/get-started/using-web-part-as-ms-teams-tab)

## <a name="introduction"></a>Introdução

Estas instruções explicarão como você pode obter uma guia de um aplicativo de exemplo do Microsoft Teams e usá-lo no SharePoint. Usaremos uma guia que já está hospedada no Azure para se concentrar no trabalho de integração necessário.

O aplicativo de exemplo que estamos usando é um aplicativo de gerenciamento de talento. Ele gerencia o processo de contratação de candidatos para posições abertas de uma equipe. (O próprio aplicativo, embora pareça bom, não faz nada. Queremos nos concentrar na criação de um aplicativo do Teams e carregá-lo no Microsoft Teams, não criar um aplicativo de gerenciamento de talento real.

### <a name="benefits-of-this-approach"></a>Benefícios dessa abordagem

- Acessar os usuários do SharePoint com sua guia do teams existente
- Carregue o manifesto do aplicativo diretamente no catálogo de aplicativos do SharePoint. Os pacotes de aplicativos do Microsoft [Teams](~/concepts/build-and-test/apps-package.md) agora são compatíveis com o SharePoint
- Os usuários finais configuram a guia em uma página assim como qualquer outra Web Part do SharePoint
- Sua guia pode acessar seu [contexto](~/tabs/how-to/access-teams-context.md) assim que possível ao executar o no Teams

## <a name="step-1-testing-the-sample-app"></a>Etapa 1: testar o aplicativo de exemplo

Baixe o manifesto do aplicativo de exemplo [**aqui**](https://github.com/MicrosoftDocs/msteams-docs/raw/master/msteams-platform/assets/downloads/TalentMgmt-Azure.zip).

No Microsoft Teams, clique no ícone do repositório no canto inferior esquerdo e, em seguida, em "carregar um aplicativo personalizado" no canto inferior esquerdo. O arquivo a ser carregado estará localizado na pasta downloads; Ele é chamado de TalentMgmt-Azure. zip. Se tudo correr bem, você verá a tela de instalação/consentimento para o aplicativo de gerenciamento de talento. Escolha a equipe que você deseja instalar e clique no botão instalar. Agora você está livre para experimentar o aplicativo.

## <a name="step-2-using-the-teams-tab-in-sharepoint"></a>Etapa 2: usar a guia Teams no SharePoint

Carregue e implante seu pacote de aplicativos do teams no seu catálogo de `https://YOUR_TENANT_NAME.sharepoint.com/sites/apps/AppCatalog/Forms/AllItems.aspx`aplicativos do SharePoint `https://contoso.sharepoint.com/sites/apps/AppCatalog/Forms/AllItems.aspx`, por exemplo,.

Quando solicitado, habilite "tornar esta solução disponível para todos os sites na organização":

![](~/assets/images/tabs/tabs-in-sharepoint/image065.png)

Em seu site, crie uma nova página clicando no botão de engrenagem no canto superior direito e, em seguida, "adicionar uma página":

![](~/assets/images/tabs/tabs-in-sharepoint/image066.png)

Você verá a experiência de criação de páginas do SharePoint. Nomeie a página "guia minhas equipes".

Abra a caixa de ferramentas da Web Part pressionando o botão + e selecione sua guia Teams (chamada "contoso HR"). As Web Parts são classificadas em ordem alfabética; Se for uma lista longa, você poderá usar a barra de pesquisa para encontrá-la. Isso criará uma Web Part na tela de desenho que contém a guia de suas equipes:

![](~/assets/images/tabs/tabs-in-sharepoint/image071.png)

Pressione o botão "publicar" ao concluir a edição.

Talvez você queira clicar em "Adicionar página à navegação" para ter uma referência rápida à página na barra de navegação esquerda:

![](~/assets/images/tabs/tabs-in-sharepoint/image073.png)

## <a name="step-3-explore-app-pages-in-sharepoint"></a>Etapa 3: explorar as páginas do aplicativo no SharePoint

Depois que a página for publicada, você poderá explorar [a ativação do aplicativo do Microsoft Teams para uma experiência mais completa dentro do SharePoint](/sharepoint/dev/spfx/web-parts/single-part-app-pages). Isso converte a página atual em uma página de aplicativo, mostrando o layout de página normal do SharePoint com uma experiência de página inteira para a guia Teams:

![](~/assets/images/tabs/tabs-in-sharepoint/image085.png)

## <a name="more-information"></a>Mais informações

- [Criando guias do Microsoft Teams usando a Estrutura do SharePoint – Tutorial](/sharepoint/dev/spfx/web-parts/get-started/using-web-part-as-ms-teams-tab)
- [Usar páginas de aplicativos de parte única no SharePoint Online](/sharepoint/dev/spfx/web-parts/single-part-app-pages)
