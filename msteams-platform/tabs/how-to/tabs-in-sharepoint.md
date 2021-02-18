---
title: Adding a Microsoft Teams tab in SharePoint as an SPFx web part
author: laujan
description: Como implantar sua guia existente do Teams no SharePoint como uma Web Part da Estrutura do SharePoint.
keywords: teams tabs sharepoint framework development
ms.topic: conceptual
ms.author: lajanuar
ms.openlocfilehash: 2e5d1b01aa5f7566e25c7720d6a0539386226576
ms.sourcegitcommit: 6caf503de5544fb8b9c8c6bef8eff4ff5a46068c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/17/2021
ms.locfileid: "50270788"
---
# <a name="adding-a-microsoft-teams-tab-in-sharepoint-as-an-spfx-web-part"></a>Adding a Microsoft Teams tab in SharePoint as an SPFx web part

## <a name="rich-integration-between-teams-and-sharepoint"></a>Integração rica entre o Teams e o SharePoint

Com a versão de novembro do Teams e da Estrutura do SharePoint v. 1.7, os desenvolvedores têm dois recursos poderosos:

<ul  class="panelContent cardsC">
<li>
    <a href="#introduction">
        <div class="cardSize">
            <div class="cardPadding">
                <div class="card">
                    <div class="cardImageOuter">
                        <div class="cardImage bgdAccent1">
                            <img src="~/assets/images/tabs/tabs-in-sharepoint/image084.png" alt="tab-in-sharepoint view"/>
                        </div>
                    </div>
                    <div class="cardText">
                        <h3>Guias do Teams no SharePoint</h3>
                        <p>Crie experiências de aplicativos ricos no SharePoint, trazendo seu aplicativo teams para o SharePoint (este artigo).</p>
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
                            <img src="~/assets/images/tabs/tabs-in-sharepoint/SharePoint-web-part-exposed-as-a-Tab-in-Microsoft-Teams.png" alt="web-part-exposed-as-a-tab" />
                        </div>
                    </div>
                    <div class="cardText">
                        <h3>Estrutura do SharePoint no Teams</h3>
                        <p>Traga suas Web Parts do SharePoint para o Teams e deixe que o SharePoint gerencie a hospedagem para você.</p>
                    </div>
                </div>
            </div>
        </div>
    </a>
</li>
</ul>

### <a name="teams-tabs-in-sharepoint"></a>Guias do Teams no SharePoint

Com a Estrutura do SharePoint v.1.7, agora estamos dando suporte à capacidade de os desenvolvedores usarem suas guias do Teams e hospedá-los no SharePoint. As Guias hospedadas no SharePoint têm uma experiência semelhante de "página inteira", expondo todos os recursos das guias do Teams, mantendo o contexto e a familiaridade de um site do SharePoint.

### <a name="sharepoint-framework-in-teams"></a>Estrutura do SharePoint no Teams

Você também pode implementar as guias do Microsoft Teams usando a Estrutura do SharePoint. Para os desenvolvedores do SharePoint, isso simplifica significativamente o processo de desenvolvimento para as guias do Teams porque as Web Parts da Estrutura do SharePoint são hospedadas no SharePoint sem a necessidade de serviços externos, como o Azure. [Saiba mais sobre como usar a Estrutura do SharePoint no Teams.](/sharepoint/dev/spfx/web-parts/get-started/using-web-part-as-ms-teams-tab)

## <a name="introduction"></a>Introdução

Essas instruções explicarão como você pode fazer uma guia de um aplicativo de exemplo do Microsoft Teams e usá-lo no SharePoint. Vamos usar uma guia que já está hospedada no Azure para se concentrar no trabalho de integração necessário.

O aplicativo de exemplo que estamos usando é um aplicativo de Gerenciamento de Talentos. Ele gerencia o processo de contratação de candidatos para posições abertas em uma equipe. (O aplicativo em si, embora pareça bom, na verdade não faz nada. Queremos nos concentrar na criação de um aplicativo do Teams e no carregamento dele no Teams, não na criação de um aplicativo de gerenciamento de talentos reais.)

### <a name="benefits-of-this-approach"></a>Benefícios dessa abordagem

- Alcance os usuários do SharePoint com a guia do Teams existente
- Carregue o manifesto do aplicativo diretamente no catálogo de aplicativos do SharePoint. [Os pacotes de aplicativos](~/concepts/build-and-test/apps-package.md) do Teams agora são suportados pelo SharePoint
- Os usuários finais configuram a guia em uma página como qualquer outra Web Part do SharePoint
- Sua guia pode acessar seu [contexto da](~/tabs/how-to/access-teams-context.md) mesma forma que pode ao executar no Teams

## <a name="step-1-testing-the-sample-app"></a>Etapa 1: testar o aplicativo de exemplo

Baixe o manifesto do aplicativo de exemplo [**a partir daqui.**](https://github.com/MicrosoftDocs/msteams-docs/raw/master/msteams-platform/assets/downloads/TalentMgmt-Azure.zip)

No Microsoft Teams, clique no ícone da Loja no canto inferior esquerdo e, em seguida, em "Carregar um aplicativo personalizado" no canto inferior esquerdo. O arquivo a ser carregado estará localizado em sua pasta Downloads; ele é chamado de TalentMgmt-Azure.zip. Se tudo correr bem, você verá a tela de instalação/consentimento do aplicativo de gerenciamento de talentos. Escolha a equipe que você deseja instalar e clique no botão Instalar. Agora você está livre para experimentar o aplicativo.

## <a name="step-2-using-the-teams-tab-in-sharepoint"></a>Etapa 2: Usar a guia Teams no SharePoint

Carregue e implante o pacote de aplicativos do Teams no catálogo de aplicativos do SharePoint `https://YOUR_TENANT_NAME.sharepoint.com/sites/apps/AppCatalog/Forms/AllItems.aspx` visitando, por exemplo, `https://contoso.sharepoint.com/sites/apps/AppCatalog/Forms/AllItems.aspx` .

Quando solicitado, habilita "Disponibilizar esta solução para todos os sites da organização":

![Guias no exibição do SharePoint](~/assets/images/tabs/tabs-in-sharepoint/image065.png)

Em seu site, crie uma nova página clicando no botão de engrenagem no canto superior direito e, em seguida, em "Adicionar uma página":

![Exibição do SharePoint](~/assets/images/tabs/tabs-in-sharepoint/image066.png)

Você verá a experiência de autoria de Páginas do SharePoint. Nomeia sua página como "Guia Minhas Equipes".

Abra a caixa de ferramentas da Web Part pressionando o botão + e selecione a guia Do Teams (chamada "Contoso HR"). As Web Parts são ordenadas em ordem alfabética; se for uma lista longa, você poderá usar a barra de pesquisa para encontrá-la. Isso criará uma Web Part na tela que contém a guia do Teams:

![Exibição de guia](~/assets/images/tabs/tabs-in-sharepoint/image071.png)

Pressione o botão "Publicar" quando terminar de editar.

Você pode clicar em "Adicionar página à navegação" para ter uma referência rápida à sua página na barra de navegação esquerda:

![Tab in Sharepoint image](~/assets/images/tabs/tabs-in-sharepoint/image073.png)

## <a name="step-3-explore-app-pages-in-sharepoint"></a>Etapa 3: Explorar páginas de aplicativos no SharePoint

Depois que sua página for publicada, você poderá explorar como [transformar seu aplicativo teams em uma experiência mais completa no SharePoint.](/sharepoint/dev/spfx/web-parts/single-part-app-pages) Isso converte a página atual em uma página de aplicativo, mostrando o layout normal da página do SharePoint com uma experiência de página inteira para a guia do Teams:

![Imagem de guias no SharePoint](~/assets/images/tabs/tabs-in-sharepoint/image085.png)

## <a name="code-sample"></a>Exemplo de código
| **Nome do exemplo** | **Descrição** | **SPFx** |
|-----------------|-----------------|----------|
| Web Part SPFx | Exemplos de Web Part SPFx para guias, canais e grupos. | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/tab-channel-group/spfx)

## <a name="more-information"></a>Mais informações

- [Criando guias do Microsoft Teams usando a Estrutura do SharePoint – Tutorial](/sharepoint/dev/spfx/web-parts/get-started/using-web-part-as-ms-teams-tab)
- [Usar páginas de aplicativos de parte única no SharePoint Online](/sharepoint/dev/spfx/web-parts/single-part-app-pages)
