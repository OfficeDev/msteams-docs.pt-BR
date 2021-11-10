---
title: Custom Together Mode Scenes
description: Trabalhar com cenas personalizadas do modo Juntos
ms.topic: conceptual
ms.localizationpriority: none
ms.openlocfilehash: 051924aa8a8f02c6e9a075639014e4fc3290d8c0
ms.sourcegitcommit: af1d0a4041ce215e7863ac12c71b6f1fa3e3ba81
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/10/2021
ms.locfileid: "60887627"
---
# <a name="custom-together-mode-scenes-in-teams"></a>Cenas personalizadas no Modo Conferência no Teams

As cenas do Modo Personalizado em Conjunto Microsoft Teams um ambiente de reunião imersivo e envolvente com as seguintes ações:

* Reunir pessoas e incentivá-las a ativar seu vídeo. 
* Combine os participantes digitalmente em uma única cena virtual. 
* Coloque os fluxos de vídeo dos participantes em assentos pré-determinados projetados e corrigidos pelo criador da cena.

> [!VIDEO https://www.youtube-nocookie.com/embed/MGsNmYKgeTA]

Em cenas personalizadas do modo Juntos, a cena é um artefato. A cena é criada pelo desenvolvedor de cena usando o estúdio do Microsoft Scene. Em uma configuração de cena concebida, os participantes têm bancos com fluxos de vídeo. Os vídeos são renderizados nesses bancos. Somente aplicativos de cena são recomendados, pois a experiência para esses aplicativos é clara.

O processo a seguir fornece uma visão geral para criar um aplicativo somente de cena:

:::image type="content" source="../assets/images/apps-in-meetings/create-together-mode-scene-flow.png" alt-text="Criar aplicativo somente cena" border="false":::

Um aplicativo somente de cena ainda é um aplicativo Microsoft Teams. O estúdio Scene lida com a criação do pacote de aplicativos em segundo plano. Várias cenas em um único pacote de aplicativos aparecem como uma lista simples para os usuários.

> [!NOTE]
> Os usuários não podem iniciar o Modo Juntos a partir do celular. No entanto, depois que um usuário ingressar em uma reunião por meio de dispositivo móvel e o modo Juntos for ligado da área de trabalho, os usuários móveis que tenham ligado o vídeo aparecerão no Modo Juntos na área de trabalho. 

## <a name="prerequisites"></a>Pré-requisitos

Você deve ter uma compreensão básica do seguinte para usar cenas personalizadas do modo Juntos:

* Defina cena e assentos em uma cena.
* Tenha uma conta do Desenvolvedor da Microsoft e conheça o Microsoft Teams Portal do [Desenvolvedor](../concepts/build-and-test/teams-developer-portal.md) e o App Studio.
* Entenda o [conceito de sideload de aplicativo.](../concepts/deploy-and-publish/apps-upload.md)
* Verifique se o Administrador concedeu permissão para Upload um aplicativo personalizado e selecione todos os filtros como parte das políticas de Configuração de Aplicativo e Reunião, respectivamente. [](../concepts/deploy-and-publish/apps-upload.md)

## <a name="best-practices"></a>Práticas recomendadas

Considere as seguintes práticas para uma experiência de construção de cena:

* Verifique se todas as imagens estão no formato PNG.
* Verifique se o pacote final com todas as imagens reunidas não deve exceder a resolução 1920x1080. A resolução é um número even. Essa resolução é um requisito para que as cenas sejam mostradas com êxito.
* Verifique se o tamanho máximo da cena é de 10 MB.
* Verifique se o tamanho máximo de cada imagem é de 5 MB. Uma cena é uma coleção de várias imagens. O limite é para cada imagem individual.
* Certifique-se de **selecionar Transparente** conforme necessário. Essa caixa de seleção está disponível no painel direito quando uma imagem é selecionada. As imagens sobrepostas devem ser marcadas como **Transparentes** para indicar que estão sobrepostas imagens na cena.

## <a name="build-a-scene-using-the-scene-studio"></a>Criar uma cena usando o estúdio scene

A Microsoft tem um estúdio scene que permite que você crie cenas. Ele está disponível no Editor de Cenas - Teams Portal do [Desenvolvedor.](https://dev.teams.microsoft.com/scenes) Este documento refere-se ao Scene studio no Microsoft Teams Portal do Desenvolvedor. A interface e as funcionalidades são todas iguais no Designer de Cena do App Studio.

Uma cena no contexto do studio Scene é um artefato que contém os seguintes elementos:

* Assentos reservados para organizadores de reunião e apresentadores de reunião. O apresentador não se refere ao usuário que está compartilhando ativamente. Refere-se à função [de reunião](https://support.microsoft.com/en-us/office/roles-in-a-teams-meeting-c16fa7d0-1666-4dde-8686-0a0bfe16e019).

* Assento e imagem para cada participante com largura e altura ajustáveis. Somente o formato PNG é suportado para a imagem.

* Coordenadas XYZ de todos os bancos e imagens.

* Coleção de imagens que são mascaradas como uma imagem.

A imagem a seguir mostra cada assento representado como um avatar para a criação das cenas:

![Estúdio de cena](../assets/images/apps-in-meetings/scene-design-studio.png)

**Para criar uma cena usando o estúdio scene**

1. Vá para [Editor de Cenas - Teams Portal do Desenvolvedor.](https://dev.teams.microsoft.com/scenes)

    Como alternativa, para abrir o Estúdio de Cena, você pode ir para a home page do [Teams Portal](https://dev.teams.microsoft.com/home)do Desenvolvedor :
    * Selecione **Criar cenas personalizadas para reuniões**.
    * Selecione **Ferramentas** na seção à esquerda e selecione **Cena de estúdio** na **seção** Ferramentas.

1. No **Editor de Cenas,** selecione **Criar uma nova cena.**

1. Em **Nome da Cena,** insira um nome para a cena.

    * Você pode selecionar **Fechar** para alternar entre fechar ou reabrir o painel direito.
    * Você pode ampliar ou diminuir o zoom da cena usando a barra de zoom para uma melhor exibição da cena.

1. Selecione **Adicionar imagens** para adicionar a imagem ao ambiente:

    ![Adicionar imagens ao ambiente](../assets/images/apps-in-meetings/addimages.png)

    >[!NOTE]
    > * Você pode baixar os [ arquivosSampleScene.zip](https://github.com/MicrosoftDocs/msteams-docs/tree/master/msteams-platform/apps-in-teams-meetings/SampleScene.zip) e [SampleApp.zip](https://github.com/MicrosoftDocs/msteams-docs/tree/master/msteams-platform/apps-in-teams-meetings/SampleApp.zip) com as imagens.

1. Selecione a imagem que você adicionou.

1. No painel direito, selecione um alinhamento para a imagem ou use **Resize** para ajustar o tamanho da imagem:

    ![Alinhamento para imagens](../assets/images/apps-in-meetings/image-alignment.png)

1. Selecione uma área fora da imagem.

1. No canto superior direito, selecione **Participantes em Camadas** . 

1. Selecione o número de participantes para a cena na caixa **Número** de participantes e selecione **Adicionar**. Depois que a cena é enviada, os posicionamentos de avatar são substituídos pelos fluxos de vídeo reais do participante. Você pode arrastar as imagens dos participantes ao redor da cena e posicioná-las na posição necessária. Você pode reessá-los usando a seta de ressize.

1. Selecione qualquer imagem de participante e selecione **Atribuir Local** para atribuir o local ao participante.

1. Selecione **Organizador da Reunião** ou Função **de** Apresentador para o participante. Em uma reunião, um participante deve ter a função de organizador da reunião:

    ![Atribuir ponto](../assets/images/apps-in-meetings/assign-spot.png)

1. Selecione **Salvar** e selecione **Exibir em Teams** para testar rapidamente sua cena em Microsoft Teams.

    * Selecionar **Exibir no Teams** cria automaticamente um aplicativo Microsoft Teams que pode ser exibido na página **Aplicativos** no portal Teams Desenvolvedor.
    * Selecionar **Exibir no Teams** cria automaticamente um pacote de aplicativos que é appmanifest.json atrás da cena. Você pode acessar  **Aplicativos** no menu e acessar o pacote de aplicativos criado automaticamente.
    * Para excluir uma cena criada, selecione **Excluir cena** na barra superior.

1. Em **Exibir em Teams**, selecione Visualizar em **Teams**.
1. Na caixa de diálogo exibida, selecione **Adicionar**.

    A cena é testada ou acessada criando uma reunião de teste e iniciando cenas personalizadas do modo Juntos. Para obter mais informações, consulte [ativar cenas personalizadas do modo Juntos:](#activate-custom-together-mode-scenes)

    ![Iniciar cenas personalizadas do modo Juntos](../assets/images/apps-in-meetings/launchtogethermode.png)

    Em seguida, a cena pode ser exibida na galeria de cenas do Modo Juntos personalizada.

Opcionalmente, você pode selecionar **Compartilhar** no **menu** suspenso Salvar. Você pode criar um link compartilhável para distribuir suas cenas para outras pessoas usarem. O usuário pode abrir o link para instalar a cena e começar a usá-la.

Após a visualização, a cena é enviada como um aplicativo para Teams seguindo as etapas para envio do aplicativo. Esta etapa requer o pacote do aplicativo. O pacote do aplicativo é diferente do pacote de cena, para a cena que foi projetada. O pacote de aplicativos criado automaticamente é encontrado na seção **Aplicativos** no Centro Teams desenvolvedores.

Opcionalmente, o pacote de cena é  recuperado **selecionando Exportar** no menu suspenso Salvar. Um **.zip,** que é o pacote de cena, é baixado. O pacote de cena inclui um scene.json e os ativos PNG usados para criar uma cena. O pacote de cena é revisado para incorporar outras alterações:

![Exportar uma cena](../assets/images/apps-in-meetings/build-a-scene.png)

Uma cena complexa que usa o eixo Z é demonstrada no exemplo passo a passo de início.

## <a name="sample-scenejson"></a>Sample scene.json

Scene.json juntamente com as imagens indicam a posição exata dos bancos. Uma cena consiste em imagens bitmap, sprites e retângulos para colocar vídeos de participantes. Esses sprites e caixas de participantes são definidos em um sistema de coordenadas do mundo. O eixo X aponta para a direita e o eixo Y aponta para baixo.

As cenas do Modo Juntos Personalizados suportam o zoom nos participantes atuais. Esse recurso é útil para pequenas reuniões em uma cena grande. Um sprite é uma imagem de bitmap estática posicionada no mundo. O valor Z do sprite determina a posição do sprite. A renderização começa com o sprite com o menor valor Z, portanto, o valor Z mais alto significa que está mais próximo da câmera. Cada participante tem seu próprio feed de vídeo, que é segmentado para que apenas o primeiro plano seja renderizado.

O código a seguir é o exemplo scene.json:

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

Cada cena tem uma ID e um nome exclusivos. A cena JSON também contém informações sobre todos os ativos usados para a cena. Cada ativo contém um nome de arquivo, largura, altura e posição no eixo X e Y. Da mesma forma, cada assento contém uma ID de assento, largura, altura e posição no eixo X e Y. A ordem de assento é gerada automaticamente e é alterada de acordo com a preferência. O número da ordem de assento corresponde à ordem de pessoas que ingressaram na chamada.

Representa `zOrder` a ordem de colocação de imagens e bancos ao longo do eixo Z. Ele dá uma noção de profundidade ou partição, se necessário. Consulte o exemplo passo a passo de início. O exemplo usa `zOrder` o .

Agora que você já passou pela amostra scene.json, você pode ativar as cenas personalizadas do modo Juntos para participar de cenas.

## <a name="activate-custom-together-mode-scenes"></a>Ativar cenas personalizadas do modo Juntos

Obter mais informações sobre como um usuário se envolve com cenas em cenas personalizadas do modo Juntos.

**Para selecionar cenas e ativar cenas personalizadas do modo Juntos**

1. Crie uma nova reunião de teste.

    >[!NOTE]
    > Ao selecionar **Visualização** no estúdio scene, a cena é instalada como um aplicativo no Microsoft Teams. Este é o modelo para um desenvolvedor testar e experimentar cenas do estúdio scene. Depois que uma cena é enviada como um aplicativo, os usuários veem essas cenas na galeria de cena.

1. No drop-down **Galeria** no canto superior esquerdo, selecione **Modo Juntos**. A **caixa de diálogo** Selador é exibida e a cena adicionada está disponível.

1. Selecione **Alterar cena** para alterar a cena padrão.

1. Na Galeria **de Cena,** selecione a cena que você deseja usar para sua reunião.

    Opcionalmente, o organizador da reunião e o apresentador podem alterar a cena **de todos** os participantes da reunião.

    >[!NOTE]
    > A qualquer momento, apenas uma cena é usada de forma homogênea para a reunião. Se um apresentador ou organizador altera uma cena, ela muda para todos. Alternar para dentro ou fora de cenas personalizadas do Modo Juntos é com participantes individuais, mas enquanto em cenas do modo Juntos personalizadas, todos os participantes têm a mesma cena.

1. Selecione **Aplicar**. Teams instala o aplicativo para o usuário e aplica a cena.

## <a name="open-a-custom-together-mode-scenes-scene-package"></a>Abrir um pacote de cenas do modo juntos personalizado

Você pode compartilhar o Pacote de Cena que é um arquivo .zip recuperado do estúdio scene para outros criadores para aprimorar ainda mais a cena. A **funcionalidade Importar uma Cena** ajuda a desembrulhar um pacote de cena para permitir que o criador continue criando a cena.

![Arquivo zip de cena](../assets/images/apps-in-meetings/scene-zip-file.png)

## <a name="see-also"></a>Confira também

[Aplicativos para Teams reuniões](teams-apps-in-meetings.md) 
 [Bots de chamadas e reuniões](~/bots/calls-and-meetings/calls-meetings-bots-overview.md) 
 [Chamadas de mídia em tempo real e reuniões com Microsoft Teams](~/bots/calls-and-meetings/real-time-media-concepts.md)
