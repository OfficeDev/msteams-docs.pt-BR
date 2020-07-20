---
title: Criar aplicativos com o Microsoft Teams Toolkit e o Visual Studio
description: Introdução ao desenvolvimento de aplicativos personalizados de grande parte diretamente no Visual Studio com o Microsoft Teams Toolkit
keywords: Kit de ferramentas do Visual Studio Teams
ms.date: 06/30/2020
ms.openlocfilehash: e5715cf23cfd221b65afe0e6258ce06ff98770aa
ms.sourcegitcommit: 694babb79d379360a20cf928a9d2b88dd6d3bdd0
ms.translationtype: Auto
ms.contentlocale: pt-BR
ms.lasthandoff: 07/07/2020
ms.locfileid: "45051704"
---
# <a name="build-apps-with-the-microsoft-teams-toolkit-and-visual-studio"></a>Criar aplicativos com o Microsoft Teams Toolkit e o Visual Studio

O Microsoft Teams Toolkit permite que você crie aplicativos personalizados do teams diretamente no ambiente do Visual Studio. O kit de ferramentas orienta você durante o processo e oferece tudo o que você precisa para criar, depurar e iniciar o aplicativo Teams.

## <a name="installing-the-teams-toolkit"></a>Instalando o Teams Toolkit

O Microsoft Teams Toolkit para Visual Studio está disponível para download no [Visual Studio Marketplace](https://aka.ms/teams-toolkit) ou diretamente como uma extensão no Visual Studio.

## <a name="using-the-toolkit"></a>Usando o kit de ferramentas

- [Configurar um novo projeto](#set-up-a-new-teams-project)
- [Configurar seu aplicativo](#configure-your-app)
- [Empacotar seu aplicativo](#package-your-app)
- [Executar o aplicativo no Microsoft Teams](#install-and-run-your-app-locally)
- [Validar seu aplicativo](#validate-your-app)
- [Publicar seu aplicativo](#publish-your-app-to-teams)

## <a name="set-up-a-new-teams-project"></a>Configurar um novo projeto do teams

1. Crie um novo projeto e selecione o modelo Microsoft Terams Toolkit.
1. Você chegará à tela **Adicionar recursos** para configurar as propriedades do novo aplicativo.
1. Selecione o botão **concluir** para concluir o processo de configuração.

## <a name="configure-your-app"></a>Configurar seu aplicativo

Em seu núcleo, o aplicativo Teams engloba três componentes:

  1. O cliente Microsoft Teams (Web, desktop ou celular) onde os usuários interagem com seu aplicativo.
  1. Um servidor que responde às solicitações de conteúdo que será exibido no Microsoft Teams, por exemplo, o conteúdo da guia HTML ou um cartão adaptável de bot.
  1. Um [pacote de aplicativos](/concepts/build-and-test/apps-package.md) do teams que consiste em três arquivos:

  > [!div class="checklist"]
  >
  > - O manifest.jsem 
  > - Um [ícone de cor](../resources/schema/manifest-schema.md#icons) para seu aplicativo exibir no catálogo de aplicativos públicos ou de organização
 > - Um [ícone de estrutura de tópicos](../resources/schema/manifest-schema.md#icons) para exibição na barra de atividades do Microsoft Teams.

Quando um aplicativo é instalado, o cliente do teams analisa o arquivo de manifesto para determinar as informações necessárias, como o nome do seu aplicativo e a URL onde os serviços estão localizados.

1. Para configurar seu aplicativo, navegue até a janela extensão do **Kit de ferramentas do Microsoft Teams** .
1. Selecione **Editar pacote de aplicativos** para exibir a página de **detalhes do aplicativo** .
1. A edição dos campos na página de detalhes do aplicativo atualiza o conteúdo do manifest.jsem um arquivo que será fornecido como parte do pacote de aplicativos. [Saiba mais](https://aka.ms/teams-toolkit-manifest)

## <a name="package-your-app"></a>Empacotar seu aplicativo

Modificar você é a página de **detalhes do aplicativo** ou atualizar o **manifesto**, ou arquivos **. env** na pasta do seu aplicativo **. publish** irá gerar automaticamente seu arquivo de **Development.zip** . Você precisará incluir [dois ícones](../concepts/build-and-test/apps-package.md#icons) na mesma pasta.

## <a name="install-and-run-your-app-locally"></a>Instalar e executar o aplicativo localmente

No menu suspenso de *configurações de soluções* , selecione *implantar*. Pressione o botão *ISS Express + Teams* . O Microsoft Teams será iniciado e a caixa de diálogo de instalação do aplicativo deverá aparecer no cliente do teams.

## <a name="validate-your-app"></a>Validar seu aplicativo

A página **validar** permite verificar o pacote do aplicativo antes de enviar o aplicativo para o AppSource. Basta carregar o pacote de manifesto e a ferramenta de validação verificará seu aplicativo em todos os casos de teste relacionados ao manifesto. Para cada teste com falha, a descrição fornece um link de documentação para ajudá-lo a corrigir o erro. Para os testes difíceis de automatizar, a lista de **verificação preliminar** detalha 7 dos casos de teste com falha mais comuns, bem como vincular a uma lista de verificação de envio completa.

## <a name="publish-your-app-to-teams"></a>Publicar seu aplicativo no Teams

Na home page do seu projeto, você pode carregar seu aplicativo para uma equipe, enviar seu aplicativo para o repositório de aplicativos personalizado da empresa para usuários em sua organização ou enviar seu aplicativo para a origem do aplicativo para todos os usuários do teams. Seu administrador de ti revisará esses envios. Você pode retornar à página *publicar* para verificar seu status de envio e saber se seu aplicativo foi aprovado ou rejeitado pelo seu administrador de ti. Este também é o local em que você vai enviar atualizações para seu aplicativo ou cancelar qualquer envio ativo no momento.

> [!div class="nextstepaction"]
> [Próxima etapa: manutenção e suporte do seu aplicativo publicado](../concepts/deploy-and-publish/appsource/post-publish/overview.md)
