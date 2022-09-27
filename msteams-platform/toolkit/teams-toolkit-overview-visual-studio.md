---
title: Visão geral do Kit de Ferramentas do Teams para Visual Studio
author: surbhigupta
description: Neste módulo, aprenda a Visão geral do Kit de Ferramentas do Teams para Visual Studio
ms.author: v-amprasad
ms.localizationpriority: medium
ms.topic: overview
ms.date: 05/24/2022
ms.openlocfilehash: 3685d105f13024507b880c35040b9d798a6d845f
ms.sourcegitcommit: 65ae3ccc2312ddc6cdaa05096e30bdf9dca10c3f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/27/2022
ms.locfileid: "68027417"
---
# <a name="teams-toolkit-overview-for-visual-studio"></a>Visão geral do Kit de Ferramentas do Teams para Visual Studio

O Kit de Ferramentas do Teams para Visual Studio ajuda você a criar, depurar e implantar aplicativos do Microsoft Teams. O Kit de Ferramentas do Teams para Visual Studio é GA no Visual Studio 2022 versão 17.3. O desenvolvimento de aplicativos com o Kit de Ferramentas do Teams tem as vantagens de:

* Identidade integrada
* Acesso ao armazenamento em nuvem
* Dados do Microsoft Graph
* Azure e serviços Microsoft 365 com abordagem de configuração zero

Para o desenvolvimento de aplicativos do Teams, você também pode usar a [ferramenta CLI](https://github.com/OfficeDev/TeamsFx/blob/dev/docs/cli/user-manual.md), semelhante ao Kit de Ferramentas do Teams para o código do Microsoft Visual Studio que inclui o Kit de Ferramentas `teamsfx`.

O Kit de Ferramentas do Teams traz todas as ferramentas necessárias para criar um aplicativo do Teams em um só lugar.

> [!NOTE]
> O Kit de Ferramentas do Teams não está disponível em outras versões.

## <a name="user-journey-of-teams-toolkit"></a>Percurso do usuário do Kit de Ferramentas do Teams

O Kit de Ferramentas do Teams automatiza o trabalho manual e fornece uma excelente integração do Teams com os recursos do Azure. A imagem a seguir mostra o percurso do usuário:

:::image type="content" source="../assets/images/teams-toolkit-overview/teams-toolkit-user-journey.png" alt-text="Percurso do usuário do kit de ferramentas do Teams":::

Os principais marcos desta jornada são:

1. Você pode começar criando um novo projeto ou tentar criar um aplicativo teams de exemplo.
1. Em seguida, você pode editar o código ou o arquivo de manifesto conforme necessário.
1. Para criar e depurar o aplicativo Teams, você pode usar sua conta do Microsoft 365.
1. Para provisionar e implantar seu aplicativo na nuvem, você pode usar sua conta do Azure.
1. Por fim, você pode publicar seu aplicativo no Teams.

## <a name="install-teams-toolkit-for-visual-studio"></a>Instalar o Kit de ferramentas do Teams para Visual Studio

Você pode baixar o instalador mais recente do Visual Studio na página [de download do Visual Studio](https://visualstudio.microsoft.com).

> [!NOTE]
> Primeiro, você precisará instalar o instalador do Visual Studio antes de instalar o Visual Studio.

Depois de abrir o instalador do Visual Studio, na janela pop-up Cargas de Trabalho.

1. Selecione a caixa de ASP.NET **e a carga de trabalho de desenvolvimento na** Web.
1. Selecione a caixa ferramentas **de desenvolvimento do Microsoft Teams** no painel de detalhes da instalação.
1. Selecione **Instalar**.

   :::image type="content" source="../assets/images/teams-toolkit-overview/visual-studio-install1.png" alt-text="Instalação do Visual Studio":::

1. Selecione **Iniciar** para abrir o Visual Studio.

    :::image type="content" source="../assets/images/teams-toolkit-overview/visual-studio-launch.png" alt-text="Iniciar o Visual Studio":::

   > [!IMPORTANT]
   > É recomendável baixar o Visual Studio 2022 versão 17.3.0, pois o Kit de Ferramentas do Teams para Visual Studio é GA nesta versão. Este artigo foi escrito para o Visual Studio 2022 versão 17.3.0. Kit de Ferramentas do Teams versão 17.3.* ou superior.

## <a name="take-a-tour-of-teams-toolkit"></a>Faça um tour pelo Kit de ferramentas do Teams

Depois de instalar o Kit de Ferramentas do Teams, você pode dar uma breve olhada nas diferentes opções de menu do Kit de Ferramentas do Teams:

1. Selecione **Projeto**.
1. Selecione **o Kit de Ferramentas do Teams**.
1. Agora você pode acessar as opções **de menu do Kit de Ferramentas do Teams** .

   :::image type="content" source="../assets/images/teams-toolkit-overview/teams-toolkit-operations-menu.png" alt-text="Menu de operações do kit de ferramentas do Teams":::

   Você também pode acessar o menu kit de ferramentas do Teams Gerenciador de Soluções.

4. Clique com o botão direito do mouse em seu **Projeto**.
5. Selecione **as opções de menu do** >  Kit de Ferramentas **do Teams.**

   :::image type="content" source="../assets/images/teams-toolkit-overview/teams-toolkit-operations-menu1.png" alt-text="Operações do kit de ferramentas do Teams do Project":::

   > [!NOTE]
   > Nesse cenário, o nome do projeto **é MyTeamsApp1**.

Você pode executar as seguintes funções no Kit de Ferramentas do Teams para Visual Studio:

|Função  |Descrição  |
|---------|---------|
|Criar projeto do Teams     |Criar um projeto do Teams usando o modelo do Teams no Visual Studio         |
|Preparar dependências de aplicativos do Teams     |Antes de executar uma depuração local, essa etapa ajuda você a configurar as dependências de depuração local e registrar o aplicativo Teams na plataforma Teams. Você precisa de uma conta do Microsoft 365. Para obter mais informações, consulte [Depurar seu aplicativo teams localmente usando o Visual Studio](debug-teams-app-visual-studio.md)         |
|Abrir Arquivo de Manifesto     |Para abrir o arquivo de manifesto do Teams, você pode passar o mouse sobre os parâmetros para visualizar os valores. Para obter mais informações, consulte [Editar manifesto do aplicativo Teams usando o Visual Studio](VS-TeamsFx-preview-and-customize-app-manifest.md)         |
|Atualizar manifesto no Portal do Desenvolvedor do Teams     |Quando você atualiza o arquivo de manifesto, só pode reimplantar o arquivo de manifesto no Azure sem implantar todo o projeto novamente. Use este comando para atualizar suas alterações para remoto. Para obter mais informações, consulte [Editar manifesto do aplicativo Teams usando o Visual Studio](VS-TeamsFx-preview-and-customize-app-manifest.md)       |
|Provisionar para a nuvem     |Essa opção ajuda você a criar recursos do Azure que hospedam seu aplicativo teams. Para obter mais informações, consulte [Provisionar recursos de nuvem usando o Visual Studio](provision-cloud-resources.md)        |
|Implantar na nuvem     |Essa opção ajuda você a copiar seu código para os recursos do Azure criados quando você fez "Provisionar para a nuvem". Para obter mais informações, [consulte Implantar o aplicativo Teams na nuvem usando o Visual Studio](deploy-teams-app.md)        |
|Visualização no Teams     |Essa opção inicia o cliente Web do Teams e permite que você visualize o aplicativo Teams em seu navegador.         |
|Pacote do Aplicativo Zip     |Essa opção gera um pacote de aplicativos do Teams na `Build` pasta no projeto. Você pode carregar o pacote no cliente do Teams e executar o aplicativo Teams.         |

As operações a seguir ainda não têm suporte no Kit de Ferramentas do Teams para Visual Studio em comparação com o Kit de Ferramentas do Teams para Visual Studio Code, no entanto, elas estão planejadas no roteiro do produto futuro.

* Adicione outros recursos do Teams ao seu aplicativo do Teams.
* Adicionar mais recursos do Azure ao aplicativo Teams
* Adicione o logon único ao aplicativo Teams.
* Adicione uma conexão de API ao aplicativo Teams.
* Personalize Azure AD manifesto.
* Adicione pipelines de CI/CD.
* Gerenciar vários ambientes de nuvem.
* Colabore em projetos do Teams.
* Publique o aplicativo Teams.

### <a name="teamsfx-net-sdk-reference-docs"></a>Documentos de referência do SDK do .NET do TeamsFx

* [Microsoft.Extensions.DependencyInjection Namespace](/../dotnet/api/Microsoft.Extensions.DependencyInjection)
* [Microsoft.TeamsFx Namespace](/../dotnet/api/Microsoft.TeamsFx)
* [Microsoft.TeamsFx.Configuration Namespace](/../dotnet/api/Microsoft.TeamsFx.Configuration)
* [Microsoft.TeamsFx.Conversation Namespace](/../dotnet/api/Microsoft.TeamsFx.Conversation)
* [Microsoft.TeamsFx.Helper Namespace](/../dotnet/api/Microsoft.TeamsFx.Helper)

## <a name="see-also"></a>Confira também

* [Criar um novo aplicativo teams no Visual Studio](create-new-teams-app-for-Visual-Studio.md)
* [Provisionar recursos de nuvem usando o Visual Studio](provision-cloud-resources.md)
* [Implantar o aplicativo Teams na nuvem usando o Visual Studio](deploy-teams-app.md)
