---
title: Adicionar guia do Teams ao SharePoint
author: laujan
description: Como implantar sua guia do Teams existente no SharePoint como uma Web Part da Estrutura do SharePoint.
keywords: teams tabs sharepoint framework development
localization_priority: Normal
ms.topic: conceptual
ms.author: lajanuar
ms.openlocfilehash: 08a4aef329d0e5e1d063f05959f0a589581c9c03
ms.sourcegitcommit: 825abed2f8784d2bab7407ba7a4455ae17bbd28f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2021
ms.locfileid: "52020314"
---
# <a name="add-teams-tab-to-sharepoint"></a>Adicionar guia do Teams ao SharePoint 

Você pode obter uma experiência de integração rica entre o Microsoft Teams e o SharePoint adicionando uma guia do Microsoft Teams no SharePoint como uma Web Part SPFx. Este documento orienta você sobre como você deve pegar uma guia de um aplicativo de exemplo do Microsoft Teams e usá-lo no SharePoint. 

## <a name="rich-integration-between-teams-and-sharepoint"></a>Integração rica entre o Teams e o SharePoint

Com a versão de novembro do Teams e da Estrutura do SharePoint v.1.7, os desenvolvedores têm dois recursos poderosos:

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
                        <p>Crie experiências de aplicativos rich no SharePoint trazendo seu aplicativo do Teams para o Sharepoint (este artigo).</p>
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
                        <p>Traga suas Web Parts do SharePoint para o Teams e deixe o SharePoint gerenciar a hospedagem para você.</p>
                    </div>
                </div>
            </div>
        </div>
    </a>
</li>
</ul>

### <a name="teams-tabs-in-sharepoint"></a>Guias do Teams no SharePoint

Com a Estrutura do SharePoint v.1.7, você pode hospedar suas guias do Teams no SharePoint. À medida que as guias hospedadas no SharePoint recebem uma experiência de página inteira semelhante, expondo todos os recursos das guias do Teams enquanto mantém o contexto e a familiaridade de um site do SharePoint. 

### <a name="sharepoint-framework-in-teams"></a>Estrutura do SharePoint no Teams

Você também pode implementar suas guias do Microsoft Teams usando a Estrutura do SharePoint. As Web Parts da Estrutura do SharePoint são hospedadas no SharePoint sem a necessidade de serviços externos, como o Azure. Para desenvolvedores do SharePoint, isso simplifica significativamente o processo de desenvolvimento das guias do Teams. Para obter mais informações sobre a Estrutura do SharePoint no Teams, consulte [como usar a Estrutura do SharePoint no Teams.](/sharepoint/dev/spfx/web-parts/get-started/using-web-part-as-ms-teams-tab)

## <a name="introduction"></a>Introdução

A guia usada aqui já está hospedada no Azure, para se concentrar no trabalho de integração necessário.

O aplicativo de exemplo que está sendo usado é um aplicativo de Gerenciamento de Talentos. Ele gerencia o processo de contratação de candidatos para posições abertas em uma equipe. Crie um aplicativo do Teams de exemplo e carregue-o no Teams. Não crie um aplicativo de gerenciamento de talentos real.

### <a name="benefits-of-this-approach"></a>Benefícios dessa abordagem

* Alcançar usuários do SharePoint com sua guia existente do Teams.
* Carregue o manifesto do aplicativo diretamente no catálogo de aplicativos do SharePoint. [Os pacotes de aplicativos](~/concepts/build-and-test/apps-package.md) do Teams agora são suportados pelo SharePoint.
* Os usuários configuram a guia em uma página como qualquer outra Web Part do SharePoint.
* Sua guia pode acessar seu [contexto](~/tabs/how-to/access-teams-context.md) da mesma forma que pode, ao executar dentro do Teams.

**Para adicionar a guia Teams ao SharePoint**

Execute as seguintes etapas para adicionar a guia Teams ao SharePoint:

## <a name="1-test-the-sample-app"></a>1. Teste o aplicativo de exemplo

Baixe o [manifesto do aplicativo de exemplo](https://github.com/MicrosoftDocs/msteams-docs/raw/master/msteams-platform/assets/downloads/TalentMgmt-Azure.zip).

1. Abra o Microsoft Teams.
1. Selecione o **ícone Appstore** no canto inferior esquerdo da guia lateral.
1. Selecione **Carregar um aplicativo personalizado** no canto inferior esquerdo. A imagem a seguir exibe a tela correspondente:  

    ![carregar um aplicativo personalizado](~/assets/images/tabs/tabs-in-sharepoint/upload-custom-app.png)

1. O arquivo a ser carregado está localizado na pasta **Downloads.** Ele é chamado TalentMgmt-Azure.zip. A imagem a seguir exibe a tela correspondente:
 
    ![TalentMgmt no Azure](~/assets/images/tabs/tabs-in-sharepoint/talentmgmt-azure.png)

1. Você pode ver a tela de instalação ou consentimento do aplicativo de gerenciamento de talentos. Selecione a equipe que deseja instalar. 
1. Selecione Instalar **e** comece a experimentar com o aplicativo.

## <a name="2-use-teams-tab-in-sharepoint"></a>2. Use a guia Teams no SharePoint

1. Carregue e implante seu pacote de aplicativos do Teams no catálogo de aplicativos do SharePoint visitando `https://YOUR_TENANT_NAME.sharepoint.com/sites/apps/AppCatalog/Forms/AllItems.aspx` . Por exemplo, `https://contoso.sharepoint.com/sites/apps/AppCatalog/Forms/AllItems.aspx`.

1. Quando solicitado, **habilitar Tornar essa solução disponível para todos os sites da organização**.
A imagem a seguir exibe a tela correspondente:

   ![Guias no exibição do Sharepoint](~/assets/images/tabs/tabs-in-sharepoint/image065.png)

1. Em seu site, crie uma nova página selecionando o botão de engrenagem no canto superior direito e selecione **Adicionar uma página**.
A imagem a seguir exibe a tela correspondente:

   ![Exibição do Sharepoint](~/assets/images/tabs/tabs-in-sharepoint/image066.png)

1. Você pode ver a experiência de autoria de páginas do SharePoint. Nomeia sua página como **Guia Minhas Equipes.**

1. Abra a caixa de ferramentas da Web Part pressionando o `+` botão e selecione sua Guia do Teams, chamada **Contoso HR**. As Web Parts são classificação alfabética. Se for uma lista longa, você poderá usar a barra de pesquisa para encontrá-la. Isso cria uma Web Part na tela que contém a guia Teams. A imagem a seguir exibe o visor de tabulação:

   ![Exibição de tabulação](~/assets/images/tabs/tabs-in-sharepoint/image071.png)

1. Pressione o **botão Publicar** depois de concluir a edição.

1. Selecione **Adicionar página à navegação** para ter uma referência rápida à sua página na barra de navegação esquerda. A imagem a seguir exibe a guia no Sharepoint: 

   ![Guia na imagem do Sharepoint](~/assets/images/tabs/tabs-in-sharepoint/image073.png)

## <a name="3-explore-app-pages-in-sharepoint"></a>3. Explorar páginas de aplicativos no SharePoint

Depois que sua página for publicada, você poderá explorar transformar seu aplicativo do Teams em uma experiência mais [completa dentro do SharePoint](/sharepoint/dev/spfx/web-parts/single-part-app-pages). Isso converte a página atual em uma Página do Aplicativo, mostrando o layout normal da página do SharePoint com uma experiência de página completa para a guia Teams. 

A imagem a seguir exibe a experiência completa do aplicativo teams no Sharepoint: ![ Imagem de guias no Sharepoint](~/assets/images/tabs/tabs-in-sharepoint/image085.png)

## <a name="code-sample"></a>Exemplo de código
| **Exemplo de nome** | **Descrição** | **SPFx** |
|-----------------|-----------------|----------|
| Web Part SPFx | Exemplos de Web Part SPFx para guias, canais e grupos. | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/tab-channel-group/spfx)

## <a name="see-also"></a>Confira também

> [!div class="nextstepaction"]
> [Criando guias do Microsoft Teams usando a Estrutura do SharePoint – Tutorial](/sharepoint/dev/spfx/web-parts/get-started/using-web-part-as-ms-teams-tab)

> [!div class="nextstepaction"]
> [Usar páginas de aplicativos de parte única no SharePoint Online](/sharepoint/dev/spfx/web-parts/single-part-app-pages)

> [!div class="nextstepaction"]
> [Integrar aplicativos Web](~/samples/integrate-web-apps-overview.md)
