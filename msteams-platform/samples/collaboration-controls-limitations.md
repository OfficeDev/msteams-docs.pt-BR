---
title: Limitações e problemas conhecidos no aplicativo de controle de colaboração
author: surbhigupta
description: Neste módulo, saiba mais sobre limitações e problemas conhecidos no aplicativo Controles de colaboração para o Microsoft Teams.
ms.localizationpriority: medium
ms.author: v-npaladugu
ms.topic: conceptual
ms.openlocfilehash: fe403c566b47be6509ff0d11113c34a8fc667cc9
ms.sourcegitcommit: edfe85e312c73e34aa795922c4b7eb0647528d48
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/30/2022
ms.locfileid: "68243385"
---
# <a name="limitations-and-known-issues"></a>Limitações e problemas conhecidos

> [!NOTE]
> Atualmente, os controles de colaboração estão disponíveis apenas na versão [prévia do desenvolvedor público](~/resources/dev-preview/developer-preview-intro.md).

A seguir estão as limitações para controles de colaboração:

* Os componentes não podem ser usados em aplicativos canvas.
* Os componentes só dão suporte a exibições de tabulação completas.

     :::image type="content" source="../assets/images/collaboration-control/tasks-tab.png" alt-text="A captura de tela mostra as tarefas." border="true":::

* A exibição de subgrid selecionada não é respeitada. Todas as tarefas, reuniões ou anotações para o registro colaborativo são exibidas.

     :::image type="content" source="../assets/images/collaboration-control/subgrid-view.png" alt-text="A captura de tela mostra a exibição de subgrid das tarefas." border= "true":::

* As atividades adicionadas ao controle de linha do tempo não aparecem nos componentes, tarefas, reuniões e anotações criadas nos componentes não estão incluídas no controle de linha do tempo.
* Novos registros devem ser salvos antes de acessar os componentes; caso contrário, você verá uma tela vazia.
* Os componentes não herdam temas do formulário ou aplicativo ao qual são adicionados.
* A localização só está disponível ao executar o aplicativo dentro do Microsoft Teams.
* Não há suporte para o modo estrito do Microsoft Edge e cookies entre sites são necessários.

**Administração Center não é atualizado quando a instalação ou atualização é concluída**

Ao seguir as etapas de instalação nos [controles de](~/samples/install-collaboration-control.md) colaboração de instalação, você será redirecionado para o centro de administração do Power Platform. Uma faixa é exibida quando a instalação é iniciada, mas não é atualizada quando a instalação é concluída. O status é listado durante a instalação e, quando concluído, ele pode não estar disponível na lista. Você pode exibir a lista de soluções para [https://make.powerapps.com/](https://make.preview.powerapps.com/) confirmar se a instalação foi concluída.

**Exibição durante a instalação:** :::image type="content" source="../assets/images/collaboration-control/view-during-installation.png" alt-text="a captura de tela mostra o processo durante a instalação." border="true":::

**Exibição após a instalação:** :::image type="content" source="../assets/images/collaboration-control/view-after-installation.png" alt-text="a captura de tela mostra a conclusão da instalação." border="true":::

Ao atualizar os controles para uma versão posterior, a mesma faixa de instalação iniciada é exibida, mas o status do controle permanece sendo instalado mesmo após a conclusão da atualização. Você pode confirmar que a atualização foi concluída verificando a lista de soluções em [https://make.powerapps.com/](https://make.preview.powerapps.com/), ele deve levar aproximadamente 15 minutos.

Você também pode ver no histórico soluções específicas que a versão posterior foi instalada e, em seguida, a versão anterior foi removida: a captura de tela mostra o histórico de soluções específicas das versões instaladas e removidas :::image type="content" source="../assets/images/collaboration-control/history.png" alt-text="." border="true":::

## <a name="bookings-meetings"></a>Reuniões do Bookings

O controle Reuniões dá suporte a uma em uma reunião ao usar o Bookings para interagir com usuários fora da sua organização. No momento, não há suporte para uma ou várias reuniões usando controles de colaboração.

**O status do participante da reunião está incorreto**

Quando um participante RSVPs para uma reunião, seu status de resposta pode não ser exibido corretamente no modo de exibição de agenda e nos detalhes da reunião. Selecionar o botão recusar pode retornar uma mensagem de erro na tela.

## <a name="tasks"></a>Tarefas

**Tarefas: o texto "limpar" do filtro não é traduzido**

O texto no botão "limpar" exibido no filtro Tarefas não é traduzido.

**Tarefas: o menu de contexto de grade aparece cortado**

Quando a grade Tarefas é preenchida por um número baixo de Tarefas, o menu de contexto da grade pode aparecer cortado e exigir o uso de barras de rolagem.

**Tarefas: o filtro de pesquisa de palavra-chave usa o operador "BeginsWith" para tarefas "Convidado"**

Ao pesquisar Tarefas usando o filtro de texto de palavra-chave, as tarefas "Convidado" são retornadas usando o operador "BeginsWith". As tarefas "Membro" são retornadas usando o operador "Contains".

## <a name="files"></a>Arquivos

Ao navegar até a pasta Arquivo Morto após o arquivamento de arquivos, os usuários podem experimentar pastas de arquivo morto duplicadas.  Navegar das pastas de arquivos para a exibição principal de arquivos resolve o problema e os arquivos arquivados não serão removidos.

## <a name="controls"></a>Controles

**Os controles falham ao salvar**

Se um controle não conseguir salvar uma tarefa ou reunião, a causa provável será a ID do Grupo ou a ID do Canal configurada incorretamente.  

Solução 1: confirme se as IDs estão corretas e se as configurações são aplicadas de acordo com o exercício de configurações.  

Solução 2: verifique se o ambiente do Power Apps e o ambiente do Teams estão no mesmo locatário.  

**Os controles não são carregados ou mostram um erro**

Se os controles não carregarem ou mostrarem um erro, pode ser um problema transitório.

Exemplo:

:::image type="content" source="../assets/images/collaboration-control/sync-fail.png" alt-text="Captura de tela que mostra a falha na sincronização de controle.":::

Isso seria renderizado no log do console como:

:::image type="content" source="../assets/images/collaboration-control/control-fail.png" alt-text="Captura de tela é um exemplo de falha de controle do log consol." border="true":::

Solução: atualize o navegador ou, se estiver no aplicativo Teams, recarregue a guia.

Se você quiser alterar o nome, o ícone ou a descrição do aplicativo depois de carregá-lo no Teams, confira [personalizar a aparência dos aplicativos](/MicrosoftTeams/customize-apps#customize-details-of-an-app)

## <a name="error-logging"></a>Log de erros

Os controles fornecem os métodos a seguir para depurar seu aplicativo.

1. **Registro em log** de eventos de plug-in quando uma API é invocada. Essas informações são armazenadas em seu ambiente do Dataverse.

    1. Para habilitar o log de rastreamento, siga estas etapas em [log e rastreamento](/power-apps/developer/data-platform/logging-tracing?WT.mc_id=email).

1. **Log do navegador** para controles de interface do usuário. Esse é o registro em log do console padrão.

    1. Ele tem suporte ao usar um navegador para executar o aplicativo Collaboration Manager por meio do Power Platform e do Teams Web.
    1. Na guia do console, você pode pesquisar erros usando Collaboration Manager mensagem de erro ou pesquisando Collaboration Manager de controle, como Tarefas.

> [!TIP]
> Se ocorrer um erro em um cliente da área de trabalho do Teams, tente replicar na Web do Teams para capturar o log de erros.

## <a name="faq"></a>Perguntas frequentes

<br>

<details>

<summary><b>Quais são os controles de colaboração (versão prévia)?</b></summary>

Os controles de colaboração (versão prévia) permitem que você adicione recursos do Microsoft 365 aos seus aplicativos personalizados de linha de negócios do Power Apps para simplificar os fluxos de trabalho do usuário ao colaborar em processos de negócios no Teams ou no Power Apps.

<br>

</details>

<br>

<details>

<summary><b>Qual é o benefício dos controles de colaboração (versão prévia) para criadores?</b></summary>

Com esses novos controles, você, como criador, pode arrastar e soltar controles que trazem a colaboração do Microsoft 365 para seu aplicativo.

<br>

</details>

<br>

<details>

<summary><b>Qual é o benefício dos controles de colaboração (versão prévia) para os usuários?</b></summary>

Os usuários podem experimentar ganhos de produtividade e permanecer em seu fluxo colaborando em aprovações, arquivos, reuniões, anotações e tarefas sem sair do contexto do seu aplicativo.

<br>

</details>

<br>

<details>

<summary><b>Como fazer acesso aos controles de colaboração (versão prévia)?</b></summary>

Solicite que o administrador do Power Platform instale os controles do AppSource em seu ambiente do Power Apps.

<br>

</details>

<br>

<details>

<summary><b>Como fazer adicionar os controles a um aplicativo controlado por modelo?</b></summary>

Vá para o Designer de Formulários e arraste os controles do painel Componente para um formulário.

<br>

</details>
