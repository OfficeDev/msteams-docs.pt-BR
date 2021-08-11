---
title: Custom Together Mode Scenes
description: Trabalhar com cenas personalizadas do modo Juntos
ms.topic: conceptual
ms.openlocfilehash: 24b350341c7503569504bffa41f715ff87caa7db49cd890482688353e7f0493f
ms.sourcegitcommit: 569ff24cc41c46d886b913a916401b18e0eb1439
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/10/2021
ms.locfileid: "57823232"
---
# <a name="custom-together-mode-scenes-in-teams"></a>Cenas personalizadas no Modo Conferência no Teams

> [!NOTE]
> Esse recurso está disponível apenas na [visualização de desenvolvedor](../resources/dev-preview/developer-preview-intro.md) público.

As cenas do modo Personalizado Em Conjunto Microsoft Teams fornece um ambiente de reunião imersivo e envolvente que reúne as pessoas e as incentiva a ativar seu vídeo. Ele combina digitalmente os participantes em uma única cena virtual e coloca seus fluxos de vídeo em bancos pré-determinados projetados e corrigidos pelo criador da cena.

> [!VIDEO https://www.youtube-nocookie.com/embed/MGsNmYKgeTA]

Uma cena em cenas personalizadas do Modo Juntos é um artefato criado pelo desenvolvedor de cena usando o microsoft scene studio. Em uma configuração de cena concebida, os participantes têm assentos designados com fluxos de vídeo renderizados nesses bancos.

> [!NOTE]
> Somente aplicativos de cena são recomendados, pois a experiência de aquisição para esses aplicativos é mais perfeita.

O processo a seguir fornece uma visão geral para criar um aplicativo somente de cena:

:::image type="content" source="../assets/images/apps-in-meetings/create-together-mode-scene-flow.png" alt-text="Criar aplicativo somente cena" border="false":::

> [!NOTE]
> * Um aplicativo somente de cena ainda é um aplicativo Microsoft Teams. O estúdio Scene lida com a criação do pacote de aplicativos em segundo plano.
> * Várias cenas em um único pacote de aplicativos aparecem como uma lista simples de cenas para os usuários.

## <a name="prerequisites"></a>Pré-requisitos

Você deve ter uma compreensão básica do seguinte para usar cenas personalizadas do modo Juntos:

* Definição de cena e bancos em uma cena.
* Tenha uma conta do Desenvolvedor da Microsoft e conheça o Microsoft Teams Portal do [Desenvolvedor](../concepts/build-and-test/teams-developer-portal.md) e o App Studio.
* [Conceito de sideload de aplicativo.](../concepts/deploy-and-publish/apps-upload.md)
* Verifique se o Administrador concedeu permissão para Upload um aplicativo personalizado e selecionar todos os filtros como parte das políticas de Configuração de Aplicativo e Reunião, respectivamente. [](../concepts/deploy-and-publish/apps-upload.md)

## <a name="best-practices"></a>Práticas recomendadas

Antes de criar uma cena, considere o seguinte para ter uma experiência perfeita de construção de cena:

* Verifique se todas as imagens estão no formato PNG.
* Verifique se o pacote final com todas as imagens reunidas não deve exceder a resolução 1920x1080.

    > [!NOTE]
    > A resolução é um número even. Esse é um requisito para que as cenas sejam iluminadas com êxito.

* Verifique se o tamanho máximo da cena é de 10 MB.
* Verifique se o tamanho máximo de cada imagem é de 5 MB.

    > [!NOTE]
    > * Uma cena é uma coleção de várias imagens. O limite é para cada imagem individual.
    > * A resolução de imagem individual também deve ser um número único.
  
* Verifique se a **caixa de** seleção Transparente está selecionada se a imagem for transparente. Essa caixa de seleção está disponível no painel direito quando uma imagem é selecionada.

    > [!NOTE]
    > As imagens sobrepostas precisam ser marcadas como **Transparentes** para indicar que estão sobrepostas imagens na cena.

## <a name="build-a-scene-using-the-scene-studio"></a>Criar uma cena usando o estúdio scene

A Microsoft tem um estúdio scene que permite que você crie cenas. Ele está disponível no [Editor de Cenas - Teams Portal do Desenvolvedor.](https://dev.teams.microsoft.com/scenes)

> [!NOTE]
> Este documento está se referindo ao Scene studio no Microsoft Teams Portal do Desenvolvedor. A interface e as funcionalidades são todas iguais no Designer de Cena do App Studio.

Uma cena no contexto do estúdio scene é um artefato que contém o seguinte:

* Assentos reservados para organizadores de reunião e apresentadores de reunião.

    > [!NOTE]
    > O apresentador não se refere ao usuário que está compartilhando ativamente. Refere-se à função [de reunião](https://support.microsoft.com/en-us/office/roles-in-a-teams-meeting-c16fa7d0-1666-4dde-8686-0a0bfe16e019).

* Assento e imagem para cada participante com largura e altura ajustáveis.

    > [!NOTE]
    > PNG é o único formato com suporte.

* Coordenadas XYZ de todos os bancos e imagens.
* Coleção de imagens que são mascaradas como uma imagem.

As dimensões de assento se tornam a tela para renderizar o fluxo de vídeo do participante. A imagem a seguir mostra cada assento representado como um avatar para criar cenas:

![Estúdio de cena](../assets/images/apps-in-meetings/scene-design-studio.png)

**Para criar uma cena usando o estúdio scene**

1. Vá para [Editor de Cenas - Teams Portal do Desenvolvedor.](https://dev.teams.microsoft.com/scenes)

    >[!NOTE]
    > * Para abrir o Estúdio de Cena, você pode navegar até a home page do [Teams Portal do](https://dev.teams.microsoft.com/home) Desenvolvedor e selecionar Criar cenas **personalizadas para reuniões.**
    > * Para abrir o Estúdio de Cena, você pode navegar até  a home page do [Teams Portal](https://dev.teams.microsoft.com/home)do Desenvolvedor, selecione Ferramentas na seção à esquerda e selecione **Cena studio** na seção **Ferramentas.**

1. Na página **Editor de Cenas,** selecione **Criar uma nova cena**.

1. Na caixa **Cena,** insira um nome para a cena.

    >[!NOTE]
    > * Você pode selecionar **Fechar** para alternar entre fechar ou reabrir o painel direito.
    > * Você pode ampliar ou diminuir o zoom da cena usando a barra de zoom para uma melhor exibição da cena.

1. Arraste e solte a imagem no ambiente conforme exibido na imagem a seguir:

    >[!NOTE]
    > * Você pode baixar os [ arquivosSampleScene.zip](https://github.com/MicrosoftDocs/msteams-docs/tree/master/msteams-platform/apps-in-teams-meetings/SampleScene.zip) e [SampleApp.zip](https://github.com/MicrosoftDocs/msteams-docs/tree/master/msteams-platform/apps-in-teams-meetings/SampleApp.zip) com as imagens.
    > * Como alternativa, você pode adicionar imagens em segundo plano à cena usando **Adicionar imagens**.

    ![Arrastar para a cena](../assets/images/apps-in-meetings/drag-and-drop-scene.png)

1. Selecione a imagem que você colocou.

1. No painel direito, selecione um alinhamento para a imagem ou use o controle deslizante **Resize** para ajustar o tamanho da imagem.

    ![Alinhamento para imagens](../assets/images/apps-in-meetings/image-alignment.png)

1. Selecione uma área fora da imagem.

1. No canto superior direito, selecione **Participantes em Camadas** . 

1. Selecione o número de participantes para a cena na caixa **Número** de participantes e selecione **Adicionar**.

    >[!NOTE]
    > * Depois que a cena é enviada, os posicionamentos de avatar são substituídos pelos fluxos de vídeo reais do participante.
    > * Você pode arrastar as imagens do participante ao redor da cena e posicioná-las na posição necessária e ressize-las usando a seta de ressize.

1. Selecione qualquer imagem de participante e marque a caixa de seleção **Atribuir Ponto** para atribuir o local ao participante.

1. Selecione **Organizador da Reunião** ou Função **de** Apresentador para o participante.

    >[!NOTE]
    > Em uma reunião, um participante deve ter a função de organizador da reunião.

    ![Atribuir ponto](../assets/images/apps-in-meetings/assign-spot.png)

1. Selecione **Salvar** e selecione **Exibir em Teams** para testar rapidamente sua cena em Microsoft Teams.

    >[!NOTE]
    > * Selecionar **Exibir no Teams** cria automaticamente um aplicativo Microsoft Teams que pode ser exibido na página **Aplicativos** no portal Teams Desenvolvedor.
    > * Selecionar **Exibir no Teams** cria automaticamente um pacote de aplicativos que appmanifest.jspor trás da cena. Como dito anteriormente, isso é abstraído, mas você pode acessar o pacote de aplicativos criado automaticamente navegando para **Aplicativos** no menu.
    > * Para excluir uma cena criada, selecione **Excluir cena** na barra superior.

1. Na caixa de diálogo exibida, selecione **Adicionar**.

    A cena pode ser testada ou acessada criando uma reunião de teste e iniciando cenas personalizadas do modo Juntos. Para obter mais informações, consulte [activate custom Together Mode scenes](#activate-custom-together-mode-scenes).

    ![Iniciar cenas personalizadas do modo Juntos](../assets/images/apps-in-meetings/launchtogethermode.png)

    >[!NOTE]
    > * A cena pode ser exibida na galeria de cenas do Modo Juntos personalizada.

1. Opcionalmente, você pode selecionar  **Compartilhar** no menu suspenso Salvar para criar um link compartilhável para distribuir facilmente suas cenas para outras pessoas usarem. Abrir esse link instala a cena para o usuário e eles podem começar a usá-la.

1. Após a visualização, a cena pode ser enviada como um aplicativo para Teams indo para a seção Aplicativos no Centro de Desenvolvedores Teams. A partir daí, você pode baixar o pacote de aplicativos ou publicar diretamente em sua organização.

    >[!NOTE]
    > Esta etapa requer o pacote de aplicativo que é diferente do pacote de cena, para a cena que foi projetada. O pacote de aplicativos criado automaticamente pode ser encontrado na seção **Aplicativos** no Teams Desenvolvedor.

1. Opcionalmente, o pacote de cena pode ser salvo **selecionando Exportar** no **menu** suspenso Salvar. Um .zip, que é o pacote de cena, é baixado.

    ![Exportar uma cena](../assets/images/apps-in-meetings/build-a-scene.png)

    >[!NOTE]
    > O pacote de cena inclui uma scene.jse os ativos PNG usados para criar uma cena. O pacote de cena pode ser revisado para incorporar outras alterações, conforme descrito na seção Exemplo scene.jsna seção deste documento.

Uma cena mais complexa que aproveita o eixo Z é demonstrada no exemplo passo a passo de início.

## <a name="sample-scenejson"></a>Exemplo scene.json

Scene.jsem junto com as imagens indicam a posição exata dos bancos. Uma cena consiste em imagens bitmap, sprites e retângulos para colocar vídeos de participantes. Esses sprites e caixas de participantes são definidos em um sistema de coordenadas do mundo com o eixo X apontando para a direita e o eixo Y apontando para baixo. As cenas do Modo Personalizado em Conjunto suportam o zoom nos participantes atuais. Isso é útil para pequenas reuniões em uma cena grande. Um sprite é uma imagem de bitmap estática posicionada no mundo. O valor Z do sprite determina a posição do sprite. A renderização começa com o sprite com o menor valor Z, portanto, o valor Z mais alto significa que ele está mais próximo da câmera. Cada participante tem seu próprio feed de vídeo, que é segmentado para que apenas o primeiro plano seja renderizado.

Veja a seguir o scene.jsexemplo:

```json
{
   "protocolVersion": "1.0",
   "id": "A",
   "autoZoom": true,
   "mirrorParticipants ": true,
   "extent":{
      "left":0.0,
      "top":0.0,
      "width":16.0,
      "height":9.0
   },
   "sprites":[
      {
         "filename":"background.png",
         "cx":8.0,
         "cy":4.5,
         "width":16.0,
         "height":9.0,
         "zOrder":0.0,
   "isAlpha":false
      },
      {
         "filename":"table.png",
         "cx":8.0,
         "cy":7.0,
         "width":12.0,
         "height":4.0,
         "zOrder":3.0,
   "isAlpha":true
      },
      {
         "filename":"row0.png",
         "cx":12.0,
         "cy":15.0,
         "width":8.0,
         "height":4.0,
         "zOrder":2.0,
   "isAlpha":true
      }

   ],
   "participants":[
      {
         "cx":5.0,
         "cy":4.0,
         "width":4.0,
         "height":2.25,
         "zOrder":1.0,
         "seatingOrder":0
      },
      {
         "cx":11.0,
         "cy":4.0,
         "width":4.0,
         "height":2.25,
         "zOrder":1.0,
         "seatingOrder":1
      }
   ]
}
```

Cada cena tem uma ID e um nome exclusivos. A cena JSON também contém informações sobre todos os ativos usados para a cena. Cada ativo contém um nome de arquivo, largura, altura e posição no eixo X e Y. Da mesma forma, cada assento contém uma ID de assento, largura, altura e posição no eixo X e Y. A ordem de assento é gerada automaticamente e pode ser alterada de acordo com a preferência.

> [!NOTE]
> O número do pedido de assento corresponde à ordem de pessoas que ingressaram na chamada.

O zOrder representa a ordem de colocação de imagens e bancos ao longo do eixo Z. Em muitos casos, ele dá uma noção de profundidade ou partição, se necessário. Para obter mais informações, consulte o exemplo passo a passo sobre como começar. O exemplo aproveita o zOrder.

Agora que você passou pelo exemplo de scene.jsativado, você pode ativar as cenas personalizadas do modo Juntos para participar de cenas.

## <a name="activate-custom-together-mode-scenes"></a>Ativar cenas personalizadas do modo Juntos

Obter informações de ponta a ponta de como um usuário final se envolve com cenas em cenas personalizadas do modo Juntos.

**Para selecionar cenas e ativar cenas personalizadas do modo Juntos**

1. Crie uma nova reunião de teste.

    >[!NOTE]
    > Ao selecionar **Visualização** no estúdio scene, a cena é instalada como um aplicativo no Microsoft Teams. Este é o modelo para um desenvolvedor testar e experimentar cenas do estúdio scene. Depois que uma cena é enviada como um aplicativo, os usuários veem essas cenas na galeria de cena.

1. No drop-down **Galeria** no canto superior esquerdo, selecione **Modo Juntos**. A **caixa de diálogo** Selador é exibida e a cena adicionada está disponível.

1. Selecione **Alterar cena** para alterar a cena padrão.

1. Na Galeria **de Cena,** selecione a cena que você deseja usar para sua reunião.

1. Opcionalmente, o organizador da reunião e o apresentador podem alterar a cena **de todos** os participantes da reunião.

    >[!NOTE]
    > A qualquer momento, apenas uma cena pode ser usada de forma homogênea para a reunião. Se um apresentador ou organizador altera uma cena, ela muda para todos. Alternar para dentro ou fora de cenas personalizadas do Modo Juntos é com participantes individuais, mas enquanto em cenas do modo Juntos personalizadas, todos os participantes têm a mesma cena.

1. Selecione **Aplicar**. Teams instala o aplicativo para o usuário e aplica a cena.

## <a name="open-a-custom-together-mode-scenes-scene-package"></a>Abrir um pacote de cenas do modo juntos personalizado

Você pode compartilhar o Pacote de Cena que é um arquivo .zip recuperado do estúdio scene para outros criadores para aprimorar ainda mais a cena. A **funcionalidade Importar uma Cena** pode ser aproveitada. Essa ferramenta ajuda a desembrulhar um pacote de cena para permitir que o criador continue criando a cena.

![Arquivo zip de cena](../assets/images/apps-in-meetings/scene-zip-file.png)

## <a name="see-also"></a>Confira também

[Aplicativos para Teams reuniões](teams-apps-in-meetings.md)
