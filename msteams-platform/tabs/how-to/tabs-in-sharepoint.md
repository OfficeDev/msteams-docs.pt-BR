---
title: Adicionar uma guia do Teams ao SharePoint
author: surbhigupta
description: Saiba como implantar sua guia do Teams existente no SharePoint como uma Web part da Estrutura do SharePoint usando exemplos de código.
ms.localizationpriority: medium
ms.topic: conceptual
ms.author: lajanuar
ms.openlocfilehash: f889a4e1932feb02eeb502ab2f85f051093a5b58
ms.sourcegitcommit: 5070746e736edb4ae77cd3efcb2ab8bb2e5819a0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/16/2022
ms.locfileid: "66123644"
---
# <a name="add-teams-tab-to-sharepoint"></a>Adicionar uma guia do Teams ao SharePoint

Você pode obter uma experiência de integração rica entre o Microsoft Teams e o SharePoint adicionando uma guia do Microsoft Teams no SharePoint como uma Web part SPFx. Este documento orienta você sobre como usar a guia de um aplicativo de exemplo do Microsoft Teams e usá-la no SharePoint.

## <a name="rich-integration-between-teams-and-sharepoint"></a>Integração avançada entre o Teams e o SharePoint

Com a versão de novembro do Teams e da Estrutura do SharePoint v.1.7, os desenvolvedores têm duas funcionalidades poderosas:

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
                        <p>Crie ricas experiências de aplicativos no SharePoint trazendo seu aplicativo do Teams para o SharePoint (este artigo).</p>
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
                        <p>Traga suas Web parts do SharePoint para o Teams e permita que o SharePoint gerencie a hospedagem para você.</p>
                    </div>
                </div>
            </div>
        </div>
    </a>
</li>
</ul>

### <a name="teams-tabs-in-sharepoint"></a>Guias do Teams no SharePoint

Com a Estrutura do SharePoint v.1.7, você pode hospedar suas guias do Teams no SharePoint. À medida que as guias hospedadas no SharePoint obtêm uma experiência semelhante de **página inteira**, expondo todos os recursos das guias do Teams, mantendo o contexto e a familiaridade de um site do SharePoint.

### <a name="sharepoint-framework-in-teams"></a>Estrutura do SharePoint no Teams

Você também pode implementar suas guias do Microsoft Teams usando a Estrutura do SharePoint. As Web Parts da Estrutura do SharePoint são hospedadas dentro do SharePoint sem qualquer necessidade de serviços externos, como o Azure. Para desenvolvedores do SharePoint, isso simplifica significativamente o processo de desenvolvimento das guias do Teams. Para obter mais informações sobre a Estrutura do SharePoint no Teams, consulte [como usar a Estrutura do SharePoint no Teams.](/sharepoint/dev/spfx/web-parts/get-started/using-web-part-as-ms-teams-tab)

## <a name="introduction"></a>Introdução

A guia usada aqui já está hospedada no Azure, para se concentrar no trabalho de integração necessário.

O aplicativo de exemplo que está sendo utilizado é um aplicativo de Gerenciamento de Talentos. Ele gerencia o processo de contratação de candidatos para cargos em aberto em uma equipe. Crie um aplicativo de exemplo do Teams e carregue-o no Teams. Não crie um aplicativo de gerenciamento de talentos de verdade.

### <a name="benefits-of-this-approach"></a>Benefícios desta abordagem

* Alcance os usuários do SharePoint com sua guia do Teams existente.
* Carregar o manifesto do aplicativo diretamente no seu catálogo de aplicativos do SharePoint. [Os pacotes de aplicativos do Teams](~/concepts/build-and-test/apps-package.md) agora são suportados pelo SharePoint.
* Os usuários configuram a guia em uma página como em qualquer outra Web part do SharePoint.
* Sua guia pode acessar seu [contexto](~/tabs/how-to/access-teams-context.md) da mesma forma que ela pode, ao executar dentro do Teams.

Para adicionar a guia do Teams ao SharePoint, execute as seguintes etapas para adicionar uma guia do Teams ao SharePoint:

## <a name="1-test-the-sample-app"></a>1. Teste o aplicativo de amostra

Baixe o [exemplo de manifesto do aplicativo ](https://github.com/MicrosoftDocs/msteams-docs/raw/master/msteams-platform/assets/downloads/TalentMgmt-Azure.zip).

1. Abra o Microsoft Teams.
1. Selecione o ícone **Appstore** no canto inferior esquerdo da guia lateral.
1. Selecione **Carregar um aplicativo personalizado** no canto inferior esquerdo. A imagem a seguir exibe a tela correspondente:  

    ![carregar um aplicativo personalizado](~/assets/images/tabs/tabs-in-sharepoint/upload-custom-app.png)

1. O arquivo a ser carregado está localizado na sua pasta de **Downloads**. Chama-se TalentMgmt-Azure.zip. A imagem a seguir exibe a tela correspondente:

    ![TalentMgmt no Azure](~/assets/images/tabs/tabs-in-sharepoint/talentmgmt-azure.png)

1. Você pode ver a tela de instalação ou o consentimento do aplicativo de gerenciamento de talentos. Selecione a equipe que você deseja instalar.
1. Selecione **Instalar** e comece a experimentar com o aplicativo.

## <a name="2-use-teams-tab-in-sharepoint"></a>2. Usar a guia do Teams no SharePoint

1. Carregue e implemente seu pacote do aplicativo do Teams no seu Catálogo de Aplicativos do SharePoint visitando `https://YOUR_TENANT_NAME.sharepoint.com/sites/apps/AppCatalog/Forms/AllItems.aspx`. Por exemplo, `https://contoso.sharepoint.com/sites/apps/AppCatalog/Forms/AllItems.aspx`.

1. Quando solicitado, habilite **Tornar essa solução disponível para todos os sites na organização**.
A imagem a seguir exibe a tela correspondente:

   ![Guias na exibição do Sharepoint](~/assets/images/tabs/tabs-in-sharepoint/image065.png)

1. No seu site, crie uma nova página selecionando o botão de engrenagem no canto superior direito e, em seguida, selecione **Adicionar uma página**.
A imagem a seguir exibe a tela correspondente:

   ![Exibição do Sharepoint](~/assets/images/tabs/tabs-in-sharepoint/image066.png)

1. Você pode ver a experiência de criação de páginas do SharePoint. Nomeie sua página como **Minha Guia do Teams**.

1. Abra a caixa de ferramentas da Web part selecionando o botão `+` e selecione a guia do Teams, chamada **Contoso HR**. As Web parts são classificadas alfabeticamente. Se for uma lista longa, você poderá usar a barra de pesquisa para encontrá-la. Isso cria uma Web part na tela que contém sua guia do Teams. A imagem a seguir exibe a o modo de exibição de guias:

   ![Modo de exibição de guias](~/assets/images/tabs/tabs-in-sharepoint/image071.png)

1. Selecione o botão **Publicar** depois de concluir a  edição.

1. Selecione **Adicionar página à navegação** para ter uma referência rápida para sua página na barra de navegação à esquerda.
A imagem a seguir exibe a guia no Sharepoint:

   ![Guia na imagem do Sharepoint](~/assets/images/tabs/tabs-in-sharepoint/image073.png)

## <a name="3-explore-app-pages-in-sharepoint"></a>3. Explore páginas de aplicativos no SharePoint

Depois que sua página for publicada, você poderá explorar [transformando seu aplicativo do Teams em uma experiência mais completa dentro do SharePoint](/sharepoint/dev/spfx/web-parts/single-part-app-pages). Isso converte a página atual em uma Página de Aplicativo, mostrando o layout normal da página do SharePoint com uma experiência de página inteira para a guia do Teams.

A imagem a seguir mostra a experiência completa do aplicativo Teams no SharePoint: ![Imagem de Guias no Sharepoint](~/assets/images/tabs/tabs-in-sharepoint/image085.png)

## <a name="code-sample"></a>Exemplo de código

| **Nome de exemplo** | **Descrição** | **SPFx** |
|-----------------|-----------------|----------|
| Web part SPFx | Exemplos de Web part SPFx para guias, canais e grupos. | [Exibir](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/tab-channel-group/spfx)

## <a name="see-also"></a>Confira também

* [Criando guias do Microsoft Teams usando a Estrutura do SharePoint – Tutorial](/sharepoint/dev/spfx/web-parts/get-started/using-web-part-as-ms-teams-tab)
* [Usar páginas de aplicativos de parte única no SharePoint Online](/sharepoint/dev/spfx/web-parts/single-part-app-pages)
* [Integrar aplicativos Web](~/samples/integrate-web-apps-overview.md)
