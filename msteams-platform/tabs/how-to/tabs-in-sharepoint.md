---
title: Adicionar uma guia do Teams ao SharePoint
author: surbhigupta
description: Saiba como implantar sua guia de Teams existente para SharePoint como uma web part Estrutura do SharePoint usando exemplos de código.
keywords: teams tabs sharepoint framework development
ms.localizationpriority: medium
ms.topic: conceptual
ms.author: lajanuar
ms.openlocfilehash: 766b9974419a6b4bfeb273a0d9d682a685b2da2d
ms.sourcegitcommit: af1d0a4041ce215e7863ac12c71b6f1fa3e3ba81
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/10/2021
ms.locfileid: "60887870"
---
# <a name="add-teams-tab-to-sharepoint"></a>Adicionar uma guia do Teams ao SharePoint

Você pode obter uma experiência de integração rica entre Microsoft Teams e SharePoint adicionando uma guia Microsoft Teams no SharePoint como uma web part SPFx web part. Este documento orienta você sobre como você deve pegar uma guia de um aplicativo de exemplo Microsoft Teams e usá-lo em SharePoint. 

## <a name="rich-integration-between-teams-and-sharepoint"></a>Integração rica entre Teams e SharePoint

Com a versão de novembro do Teams e Estrutura do SharePoint v.1.7, os desenvolvedores têm dois recursos avançados:

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
                        <h3>Teams Guias no SharePoint</h3>
                        <p>Crie experiências de aplicativos rich SharePoint trazendo seu aplicativo Teams para SharePoint (este artigo).</p>
                    </div>
                </div>
            </div>
        </div>
    </a>
</li>
<li>
    <a href="/sharepoint/dev/spfx/web-parts/get-started/using-web-part-as-ms-teams-tab">
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
                        <p>Traga suas SharePoint web parts para Teams e deixe SharePoint gerenciar a hospedagem para você.</p>
                    </div>
                </div>
            </div>
        </div>
    </a>
</li>
</ul>

### <a name="teams-tabs-in-sharepoint"></a>Teams guias no SharePoint

Com Estrutura do SharePoint v.1.7, você pode hospedar suas Teams de SharePoint. À medida que as guias hospedadas  no SharePoint obter uma experiência de página inteira semelhante, expondo todos os recursos das guias Teams enquanto mantém o contexto e a familiaridade de um site SharePoint.

### <a name="sharepoint-framework-in-teams"></a>Estrutura do SharePoint no Teams

Você também pode implementar suas guias Microsoft Teams usando Estrutura do SharePoint. Estrutura do SharePoint web parts são hospedadas em SharePoint sem qualquer necessidade de serviços externos, como o Azure. Para SharePoint desenvolvedores, isso simplifica significativamente o processo de desenvolvimento para Teams guias. Para obter mais informações sobre Estrutura do SharePoint em Teams, consulte como usar o Estrutura do SharePoint [em Teams.](/sharepoint/dev/spfx/web-parts/get-started/using-web-part-as-ms-teams-tab)

## <a name="introduction"></a>Introdução

A guia usada aqui já está hospedada no Azure, para se concentrar no trabalho de integração necessário.

O aplicativo de exemplo que está sendo usado é um aplicativo de Gerenciamento de Talentos. Ele gerencia o processo de contratação de candidatos para posições abertas em uma equipe. Crie um aplicativo Teams exemplo e carregue-o em Teams. Não crie um aplicativo de gerenciamento de talentos real.

### <a name="benefits-of-this-approach"></a>Benefícios dessa abordagem

* Entre SharePoint usuários com sua guia Teams existente.
* Upload seu manifesto do aplicativo diretamente para seu catálogo SharePoint aplicativo. [Teams pacotes de aplicativos](~/concepts/build-and-test/apps-package.md) agora são suportados por SharePoint.
* Os usuários configuram a guia em uma página como qualquer outra web part SharePoint web part.
* Sua guia pode acessar seu [contexto](~/tabs/how-to/access-teams-context.md) da mesma forma que pode, ao executar dentro Teams.

**Para adicionar Teams guia SharePoint**

Execute as seguintes etapas para adicionar Teams guia SharePoint:

## <a name="1-test-the-sample-app"></a>1. Teste o aplicativo de exemplo

Baixe o [manifesto do aplicativo de exemplo](https://github.com/MicrosoftDocs/msteams-docs/raw/master/msteams-platform/assets/downloads/TalentMgmt-Azure.zip).

1. Abra o Microsoft Teams.
1. Selecione o **ícone Appstore** no canto inferior esquerdo da guia lateral.
1. Selecione **Upload um aplicativo personalizado** no canto inferior esquerdo. A imagem a seguir exibe a tela correspondente:  

    ![carregar um aplicativo personalizado](~/assets/images/tabs/tabs-in-sharepoint/upload-custom-app.png)

1. O arquivo a ser carregado está localizado na pasta **Downloads.** Ele é chamado TalentMgmt-Azure.zip. A imagem a seguir exibe a tela correspondente:
 
    ![TalentMgmt no Azure](~/assets/images/tabs/tabs-in-sharepoint/talentmgmt-azure.png)

1. Você pode ver a tela de instalação ou consentimento do aplicativo de gerenciamento de talentos. Selecione a equipe que deseja instalar. 
1. Selecione Instalar **e** comece a experimentar com o aplicativo.

## <a name="2-use-teams-tab-in-sharepoint"></a>2. Use Teams guia no SharePoint

1. Upload e implante seu pacote de aplicativos Teams no catálogo de aplicativos SharePoint, visitando `https://YOUR_TENANT_NAME.sharepoint.com/sites/apps/AppCatalog/Forms/AllItems.aspx` . Por exemplo, `https://contoso.sharepoint.com/sites/apps/AppCatalog/Forms/AllItems.aspx`.

1. Quando solicitado, **habilitar Tornar essa solução disponível para todos os sites da organização**.
A imagem a seguir exibe a tela correspondente:

   ![Guias no exibição do Sharepoint](~/assets/images/tabs/tabs-in-sharepoint/image065.png)

1. Em seu site, crie uma nova página selecionando o botão de engrenagem no canto superior direito e selecione **Adicionar uma página**.
A imagem a seguir exibe a tela correspondente:

   ![Exibição do Sharepoint](~/assets/images/tabs/tabs-in-sharepoint/image066.png)

1. Você pode ver a experiência de SharePoint de autoria de páginas. Nomeia sua página como **My Teams Tab.**

1. Abra a caixa de ferramentas da Web Part selecionando o `+` botão e selecione sua guia Teams, chamada **Contoso HR**. As Web Parts são classificação alfabética. Se for uma lista longa, você poderá usar a barra de pesquisa para encontrá-la. Isso cria uma Web Part na tela que contém sua guia Teams. A imagem a seguir exibe o visor de tabulação:

   ![Exibição de tabulação](~/assets/images/tabs/tabs-in-sharepoint/image071.png)

1. Selecione o **botão Publicar** depois de concluir a edição.

1. Selecione **Adicionar página à navegação** para ter uma referência rápida à sua página na barra de navegação esquerda. A imagem a seguir exibe a guia no Sharepoint: 

   ![Guia na imagem do Sharepoint](~/assets/images/tabs/tabs-in-sharepoint/image073.png)

## <a name="3-explore-app-pages-in-sharepoint"></a>3. Explorar páginas de aplicativo no SharePoint

Depois que sua página for publicada, você poderá explorar transformar seu aplicativo Teams em uma experiência mais [completa dentro SharePoint](/sharepoint/dev/spfx/web-parts/single-part-app-pages). Isso converte a página atual em uma Página do Aplicativo, mostrando o layout de página SharePoint normal com uma experiência de página inteira para a guia Teams. 

A imagem a seguir exibe a experiência completa do aplicativo Teams no SharePoint: ![ Imagem de guias no Sharepoint](~/assets/images/tabs/tabs-in-sharepoint/image085.png)

## <a name="code-sample"></a>Exemplo de código
| **Nome do exemplo** | **Descrição** | **SPFx** |
|-----------------|-----------------|----------|
| SPFx Web Part | SPFx exemplos de Web Part para guias, canais e grupos. | [Exibir](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/tab-channel-group/spfx)

## <a name="see-also"></a>Confira também

* [Criando guias do Microsoft Teams usando a Estrutura do SharePoint – Tutorial](/sharepoint/dev/spfx/web-parts/get-started/using-web-part-as-ms-teams-tab)
* [Usar páginas de aplicativos de parte única no SharePoint Online](/sharepoint/dev/spfx/web-parts/single-part-app-pages)
* [Integrar aplicativos Web](~/samples/integrate-web-apps-overview.md)
