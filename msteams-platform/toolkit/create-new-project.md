---
title: Criar um novo aplicativo de Equipes usando o Kit de Ferramentas do Teams
author: zyxiaoyuer
description: Criar novo aplicativo de Equipes usando o Kit de Ferramentas do Teams
ms.author: surbhigupta
ms.localizationpriority: high
ms.topic: overview
ms.date: 03/14/2022
ms.openlocfilehash: d44f757141d31faaf4639a58fbbd31e5729e6f02
ms.sourcegitcommit: 1e77573e47fad51a19545949fdac1241b13052e2
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/24/2022
ms.locfileid: "65656149"
---
# <a name="create-a-new-teams-app-using-teams-toolkit"></a>Criar um novo aplicativo de Equipes usando o Kit de Ferramentas do Teams

Para criar um novo aplicativo de Equipes usando o Kit de Ferramentas do Teams, você pode selecionar uma das seguintes opções:

* [Criar um novo aplicativo do Teams](create-new-project.md#create-a-new-teams-app)
* [Exibir amostras](create-new-project.md#create-a-new-teams-app-using-view-samples)

### <a name="create-a-new-teams-app"></a>Criar um novo aplicativo do Teams

1. Abra o Visual Studio Code.
1. Selecione o ícone do Kit de Ferramentas do Teams:::image type="icon" source="../assets/images/teams-toolkit-v2/teams-toolkit-sidebar-icon.PNG" border="true"::: na barra Visual Studio Code lateral.
1. Selecione **Criar um novo aplicativo do Teams**.

   :::image type="content" source="../assets/images/teams-toolkit-v2/teams-toolkit-sidebar.png" alt-text="Barra lateral do kit de ferramentas do Teams":::

1. Você pode selecionar **Criar um novo aplicativo Teams** ou **Iniciar a partir de um exemplo**.
   
   :::image type="content" source="../assets/images/teams-toolkit-v2/select-create-app.png" alt-text="Criar um aplicativo":::
   
1. Se você selecionar **Criar um novo aplicativo Teams,** a imagem a seguir será exibida com modelos de três categorias: Aplicativo Teams baseado em cenário, Aplicativo Teams básico e Aplicativos Teams estendidos no Microsoft 365: 

   :::image type="content" source="../assets/images/teams-toolkit-v2/teams-capabilities.png" alt-text="Recursos para aplicativo Teams":::

1. Selecione pelo menos uma opção para começar a criar o aplicativo Teams.


### <a name="create-a-new-teams-app-using-view-samples"></a>Criar um novo aplicativo do Teams usando exemplos de exibição

Você pode criar um novo aplicativo explorando **Exibir amostras** e selecionando uma amostra existente. O exemplo selecionado já pode ter alguma funcionalidade, por exemplo, uma lista de tarefas com um back-end do Azure ou uma integração com o Kit de ferramentas do Microsoft Graph.

 1. Abra o **Kit de ferramentas do Teams** do Microsoft Visual Studio Code.
 1. Selecione a seção **DESENVOLVIMENTO** em Treeview.
 1. Selecione **Exibir amostras**. 

    :::image type="content" source="../assets/images/teams-toolkit-v2/view-samples.png" alt-text="Exibir amostras":::

    A galeria de amostra aparece conforme mostrado na imagem a seguir:
   
    :::image type="content" source="../assets/images/teams-toolkit-v2/sample-gallery.png" alt-text="Galeria de exemplos":::

  Você pode explorar a galeria de exemplo da seguinte maneira:

  1. Selecione um exemplo para procurar informações detalhadas.
  1. Selecione **Criar** na página de informações de cada exemplo para baixá-lo. 
  1. Execute seu aplicativo localmente ou remotamente para visualizar o cliente Web do Teams seguindo as instruções abertas automaticamente após o download do exemplo.
  1. Se você não quiser baixar os exemplos, poderá selecionar **Exibir no GitHub** para abrir o exemplo no repositório GitHub Samples e procurar o código-fonte.

## <a name="step-by-step-guides-using-teams-toolkit"></a>Guias passo a passo usando o Kit de Ferramentas do Teams

* [Criar um aplicativo do Teams com o Blazor](../sbs-gs-blazorupdate.yml)
* [Criar um Teams com JavaScript usando React](../sbs-gs-javascript.yml)
* [Criar um aplicativo Teams com SPFx](../sbs-gs-spfx.yml)
* [Criar um aplicativo Teams com C# ou .NET](../sbs-gs-csharp.yml)
* [Enviar notificação para o Teams](../sbs-gs-notificationbot.yml)
* [Criar bot de comando](../sbs-gs-commandbot.yml)

## <a name="see-also"></a>Confira também

* [Provisionar recursos de nuvem](provision.md)
* [Implantar o aplicativo Teams na nuvem](deploy.md)
* [Publicar seu aplicativo Teams](../concepts/deploy-and-publish/appsource/publish.md)
* [Gerenciar vários ambientes](TeamsFx-multi-env.md)
* [Colaborar com outros desenvolvedores no projeto do Teams](TeamsFx-collaboration.md)