---
title: Aplicativo com controles de colaboração
author: surbhigupta
description: Neste módulo, saiba como criar um aplicativo baseado em modelo com controles de colaboração para o Teams e como adicionar controles de colaboração ao aplicativo.
ms.localizationpriority: medium
ms.author: v-npaladugu
ms.topic: conceptual
ms.openlocfilehash: f75f7ea3b014a9373ba1d643cede7055aa333ef5
ms.sourcegitcommit: f2ac771cbd608e872604e9ac8ffec2d08f55ee1a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/04/2022
ms.locfileid: "68373042"
---
# <a name="create-a-new-model-driven-app-with-collaboration-controls-for-teams"></a>Criar um novo aplicativo controlado por modelo com controles de colaboração para o Teams

Os controles de colaboração são projetados para [aplicativos controlados por modelo](/power-apps/maker/model-driven-apps/model-driven-app-overview). A seção a seguir aborda como criar um aplicativo controlado por modelo.

> [!NOTE]
> Atualmente, os controles de colaboração estão disponíveis apenas na versão [prévia do desenvolvedor público](~/resources/dev-preview/developer-preview-intro.md).

## <a name="create-a-model-driven-application"></a>Criar um aplicativo controlado por modelo

1. Abrir [https://make.powerapps.com.](https://make.powerapps.com/) ou [https://make.preview.powerapps.com.](https://make.preview.powerapps.com/)

1. Selecione **Soluções** no painel esquerdo.

1. Selecione **Nova solução** para que você possa fornecer uma casa para todas as suas personalizações futuras.

   :::image type="content" source="../assets/images/collaboration-control/new-solution.png" alt-text="Captura de tela é um exemplo que mostra a nova solução, que fornece uma página inicial para toda a personalização futura.":::

1. Forneça o nome e o editor da sua nova solução. Essa solução conterá o nome personalizado Collaboration Manager.

   :::image type="content" source="../assets/images/collaboration-control/collaboration-manager.png" alt-text="Captura de tela é um exemplo que fornece detalhes do editor da nova solução.":::

1. Selecione **Criar**

1. Depois que a solução é criada, ela aparece em sua lista de soluções. Selecione sua solução para abri-la.

1. Antes de criar seu aplicativo, crie uma página inicial para seus dados. selecione **Nova** > **Tabela** para começar.

     :::image type="content" source="../assets/images/collaboration-control/create-table.png" alt-text="Captura de tela que descreve como criar uma nova tabela.":::

1. Dê um nome à sua tabela. Em **Opções avançadas**, selecione **Criar uma nova atividade**.

   :::image type="content" source="../assets/images/collaboration-control/new-activity.png" alt-text="Captura de tela que descreve como criar uma nova atividade.":::

1. Selecione **Salvar**.

1. Depois de criar a tabela, você pode personalizá-la adicionando colunas extras, relações e muito mais (opcional).

1. Agora você pode criar um novo aplicativo controlado por modelo selecionando **Novo** > **aplicativo** >  controlado **por Modelo de Aplicativo.**

   :::image type="content" source="../assets/images/collaboration-control/model-driven-app.png" alt-text="Captura de tela é um exemplo que mostra como criar um novo aplicativo controlado por modelo.":::

1. Selecione o **novo designer de aplicativo moderno (versão prévia)** para abrir o novo aplicativo.

   :::image type="content" source="../assets/images/collaboration-control/model-driven-app-blank.png" alt-text="Captura de tela é um exemplo que mostra o novo aplicativo controlado por modelo em branco e você pode selecionar uma experiência de criação.":::

1. Selecione **Criar.**

1. Dê um nome ao aplicativo e selecione **Criar.**

   :::image type="content" source="../assets/images/collaboration-control/collaboration-manager-for-inspection.png" alt-text="Captura de tela é um exemplo que mostra a adição do gerenciador de colaboração para inspeção e a criação de um novo aplicativo controlado por modelo.":::

1. Selecione **Adicionar página.**

1. Selecione **a exibição e o formulário baseados em tabela.**

   :::image type="content" source="../assets/images/collaboration-control/table-based.png" alt-text="Captura de tela é um exemplo que mostra o formulário e o modo de exibição baseado em tabela e você pode selecionar um tipo de página.":::

1. Selecione **Avançar.**

1. Pesquise e selecione a tabela que você criou anteriormente.

   :::image type="content" source="../assets/images/collaboration-control/table-view-form-pages.png" alt-text="Captura de tela é um exemplo que mostra as páginas de formulário do modo de exibição de tabela e pode selecionar a tabela que você criou.":::

1. Selecione **Adicionar.**

1. Selecione **Publicar** para salvar e publicar seu aplicativo.

1. Selecione **Reproduzir** para testar seu novo aplicativo.

Agora você criou com êxito um aplicativo controlado por modelo.

## <a name="add-collaboration-controls-to-your-application"></a>Adicionar controles de colaboração ao seu aplicativo

A seguir estão as etapas para adicionar recursos de controle de colaboração, como tarefas, reuniões, arquivos e experiências de anotações ao aplicativo criado:

1. Para incluir as guias Tarefas, Reuniões e Anotações, você precisa editar o formulário Informações Principais. Para começar, volte para o gerenciador e selecione sua solução.

1. Selecione a tabela que você criou [em Criar um novo aplicativo controlado por modelo para o Teams.](#create-a-new-model-driven-app-with-collaboration-controls-for-teams)

1. Vá para a guia Formulários da tabela.

     :::image type="content" source="../assets/images/collaboration-control/forms-tab.png" alt-text="Captura de tela é um exemplo que mostra a guia formulários da tabela.":::

1. Selecione o formulário Informações do tipo de formulário **Principal** para abri-lo no designer de formulário.

1. Quando estiver no designer de formulários, pressione e arraste em uma guia de **1 coluna** da seção **Componentes** .

     :::image type="content" source="../assets/images/collaboration-control/components.png" alt-text="Captura de tela é um exemplo que mostra os componentes dos aplicativos de energia.":::

1. Depois de selecionar a guia, renomeie a guia como "Tarefas" no painel de propriedades.

1. Selecione o nome da guia para selecionar a seção completa e **selecione Expandir primeiro componente para a guia completa** no painel Propriedades. Isso é necessário, pois os controles de colaboração são melhor exibidos em exibições de guia completas.

    :::image type="content" source="../assets/images/collaboration-control/tasks-pane.png" alt-text=" Captura de tela que descreve como selecionar o primeiro componente para a guia completa.":::

     :::image type="content" source="../assets/images/collaboration-control/expand-first-component.png" alt-text=" Captura de tela que descreve como expandir o primeiro componente para a guia completa.":::

1. Expanda a categoria Colaboração (Versão Prévia) na gaveta de controles e arraste o controle Tarefas (Versão Prévia) para a seção no formulário Tarefas.

     :::image type="content" source="../assets/images/collaboration-control/collab-preview.png" alt-text="Captura de tela que descreve como visualizar o controle na seção no formulário de tarefas.":::

3. Defina a tabela como Atividades & selecione Concluído.

     :::image type="content" source="../assets/images/collaboration-control/select-table-activities.png" alt-text="A captura de tela mostra como selecionar a tabela para atividades.":::

5. Selecione "Ocultar Rótulo" nas Propriedades.

     :::image type="content" source="../assets/images/collaboration-control/hide-label-properties.png" alt-text="Captura de tela que mostra como selecionar ocultar rótulo.":::

1. O controle Tarefas é exibido agora.

     :::image type="content" source="../assets/images/collaboration-control/new-collab-control.png" alt-text="A captura de tela mostra um exemplo de exibição de controle de tarefas.":::

1. Repita as etapas tarefas para adicionar controles aprovações, arquivos, reuniões e anotações ao seu aplicativo.
1. Depois de adicionar todos os controles, você verá os controles renderizados abaixo no Designer de Formulários. Se um controle não for renderizado no Designer de Formulários, por exemplo, mostrar um formulário em branco, execute seu aplicativo no Power Apps e a presença de uma página "configurar" ou de um "estado vazio" significa que o controle foi adicionado com êxito.

     :::image type="content" source="../assets/images/collaboration-control/new-collab-approval.png" alt-text="A captura de tela mostra que o designer de formulário Controles foi adicionado com êxito.":::

1. Agora você pode executar seu aplicativo de energia no Power Apps selecionando-o.

     :::image type="content" source="../assets/images/collaboration-control/collaboration-manager-for-inspections-power-apps.png" alt-text="A captura de tela mostra a execução do aplicativo de energia selecionando o Gerenciador de colaboração para inspeções.":::

1. Crie um novo registro selecionando **+ Novo** e, em seguida, abra o registro.

     :::image type="content" source="../assets/images/collaboration-control/power-apps-open-the-record.png" alt-text="A captura de tela mostra a criação de um novo registro.":::

1. Agora você pode ver os modos de exibição de cada guia que são semelhantes à imagem a seguir:

     :::image type="content" source="../assets/images/collaboration-control/tabs.png" alt-text="Captura de tela é um exemplo que mostra o modo de exibição de cada guia.":::

     > [!TIP]
     > Os controles só ficam visíveis depois que um registro é salvo no aplicativo. Se as guias de controle não aparecerem no registro, tente atualizar o navegador ou republicar o aplicativo do Power Apps.

Agora você adicionou com êxito os controles de Colaboração ao seu aplicativo. Agora você pode executar seu aplicativo no Power Apps e iniciar os controles. Como as configurações ainda não foram definidas, você não poderá criar entidades como Tarefas ou Reuniões até que elas sejam adicionadas.

## <a name="define-settings-for-your-collaboration"></a>Definir configurações para sua colaboração

Você pode definir configurações para controles de colaboração para a entidade de negócios, como a tabela criada no [novo aplicativo controlado por modelo](#create-a-new-model-driven-app-with-collaboration-controls-for-teams).

As configurações que você pode aplicar são as seguintes:

|Configurações|Usada por|
|---|---|
|ID do Grupo|Tarefas, Reuniões Internas, Aprovações.|
|ID de negócios do Bookings|Reuniões externas usando o Bookings |
|Site ID|Arquivos do SharePoint |
|ID da unidade|Arquivos do SharePoint|

> [!NOTE]
> As configurações são essenciais para iniciar seu aplicativo, portanto, certifique-se de seguir as etapas conforme sugerido. Se você tiver problemas ao iniciar e salvar os controles, verifique novamente os valores.

Você pode obter a ID do Grupo criando uma nova equipe ou usar uma equipe existente no Microsoft Teams para hospedar seu aplicativo e criar variáveis de configurações.

Para criar uma nova equipe, consulte [criar uma equipe do zero](https://support.microsoft.com/en-us/office/create-a-team-from-scratch-174adf5f-846b-4780-b765-de1a0a737e2b).

Use as instruções a seguir para recuperar a ID do Grupo da sua equipe do Teams para Aprovações, Tarefas e Reuniões internas:

1. Encontre sua equipe na lista de equipes.

1. Selecione a elipse **... e** selecione **Obter link para a equipe**.

     :::image type="content" source="../assets/images/collaboration-control/get-link.png" alt-text="Captura de tela que descreve como obter o vinculado à equipe.":::

1. Copie o link e registre o valor `groupId` da URL. Você usará esse valor em um estágio posterior ao definir as configurações da solução.

     `https://teams.microsoft.com/l/team/19%3akk_TuKhjXu92yJvg4TZ10S6rouLSCgvHIb5NOOTfRjg1%40thread.tacv2/conversations?groupId=4310f270-1aa5-4089-99f3-47eb3b4d69ad&tenantId=b699419b-e0df-47e3-9909-24076fdcf68b`

Use as instruções a seguir para recuperar a ID do Site do SharePoint e a ID da Unidade para Arquivos:

1. Para usar o controle Arquivos, você precisará configurar para um site existente do SharePoint ou criar um novo site do SharePoint. Para criar um novo site, consulte [criar um site](/sharepoint/create-site-collection).

1. Agora, recupere os Valores de Configuração da ID do Site e da ID da Unidade, que podem ser chamados usando os detalhes em seu site do SharePoint.

     1. **ID do Site**: usando [o Explorador do Graph](https://developer.microsoft.com/graph/graph-explorer), entre e concatene permissões para Directory.ReadWrite.All e User.ReadWrite.All

         :::image type="content" source="../assets/images/collaboration-control/graph-permissions.png" alt-text="Captura de tela é um exemplo que mostra o Explorador do Graph.":::

     1. Substitua o nome do host pelo nome do host e o caminho relativo para o caminho do site e faça uma chamada de grafo para `https://graph.microsoft.com/v1.0/sites/{hostname}:/{relative-path-to-site}`. A seguir está um exemplo:
         1. Se a URL do site = `https://myhostname.sharepoint.com/sites/MySiteName`
         1. Nome do host = `myhostname.sharepoint.com`
         1. Caminho relativo para o site = `sites/MySiteName`

              :::image type="content" source="../assets/images/collaboration-control/graph-call.png" alt-text="Captura de tela é um exemplo que mostra a chamada do Graph.":::

            A chamada de grafo seria, `https://graph.microsoft.com/v1.0/sites/myhostname.sharepoint.com:/sites/MySiteName`.

     1. A resposta recebida é um objeto Json que representa o Site, por exemplo, a ID do Site seria `abcdef.sharepoint.com,0abe7394-6fce-4dcc-9884-7eaceb48cd41,8cb86762-16cd-495e-87cb-893cfdf94054`.

     1. Salve o parâmetro de valor da ID do Site.

     1. **ID da unidade**: usando [o Explorador do Graph](https://developer.microsoft.com/graph/graph-explorer), entre e faça a chamada do grafo `https://graph.microsoft.com/v1.0/sites/{site-id}/drives` com o valor da ID do Site que você salvou anteriormente.

     1. Uma resposta JSON é retornada com um valor de parâmetro de matriz de tipo ou lista de objetos de unidade. Examine o Json do objeto Json cujo parâmetro de nome corresponde ao nome da biblioteca de documentos. Salve o valor do parâmetro de ID da unidade.

Para criar reuniões com usuários fora de sua organização, como clientes e usar recursos de visita virtual em seu aplicativo, você precisaria fornecer uma empresa do Bookings. Para obter mais informações, [consulte Microsoft Bookings](/microsoft-365/bookings/bookings-overview?view=o365-worldwide&preserve-view=true).

## <a name="add-settings-to-your-collaboration-manager-app"></a>Adicionar configurações ao seu Collaboration Manager aplicativo

Para aplicar configurações e explorar os recursos colaborativos do seu aplicativo no Power Apps, abra o aplicativo que você criou anteriormente. Você verá uma página de exibição, na qual poderá selecionar os registros existentes ou criar um novo. Para começar, abra ou crie um registro.

Você precisaria adicionar as IDs de Configurações que você salvou anteriormente para seu aplicativo.

|Configurações|Usada por|
|---|---|
|ID do Grupo|Tarefas, Reuniões internas, Aprovações.|
|ID de negócios do Bookings|Reuniões externas usando o Bookings |
|Site ID|Arquivos do SharePoint |
|ID da unidade|Arquivos do SharePoint|

### <a name="add-settings-for-tasks-meetings-and-files"></a>Adicionar configurações para tarefas, reuniões e arquivos

1. Inicie um controle e você poderá ver uma janela da seguinte maneira:

     :::image type="content" source="../assets/images/collaboration-control/launch-window.png" alt-text="Captura de tela é um exemplo que mostra a janela de controle.":::

1. Selecione **Configurar** e vá para a guia Geral para adicionar a ID do Grupo.

     :::image type="content" source="../assets/images/collaboration-control/groupid-general.png" alt-text="Captura de tela que descreve como adicionar a ID do Grupo na guia Geral.":::

1. Guia Abrir Arquivos para adicionar a ID do Site e a ID da Unidade.

     :::image type="content" source="../assets/images/collaboration-control/files-tab.png" alt-text="Captura de tela que descreve como adicionar a ID do site e a ID da unidade na guia arquivos.":::

O controle Anotações não requer um valor de configuração. Agora você pode criar entidades como Tarefas e Reuniões em seu aplicativo. Se você estiver enfrentando problemas ao iniciar e salvar os controles, verifique novamente os valores de configurações.

## <a name="explore-your-new-collaboration-manager-app"></a>Explorar seu novo Collaboration Manager aplicativo

As seções a seguir orientam você sobre como usar os controles Tarefa, Anotações, Reuniões, Arquivos e Aprovações.

### <a name="create-tasks"></a>Criar Tarefas

Explore a colaboração na guia Tarefas selecionando a guia Tarefas, que abre uma página vazia em que os usuários podem adicionar todas as tarefas relevantes que precisam concluir.

1. Para criar uma nova tarefa para a equipe, selecione **Adicionar uma tarefa**. Ele abre uma caixa de diálogo em que você pode fornecer informações específicas sobre a tarefa e atribuí-la às pessoas relevantes na equipe e selecionar Salvar.

     :::image type="content" source="../assets/images/collaboration-control/add-task.png" alt-text="Captura de tela que descreve como adicionar uma tarefa.":::

1. A tarefa salva aparecerá na lista de tarefas.

1. Como todas as tarefas são apoiadas por Microsoft Planner. Os usuários podem usar o aplicativo Tarefas no Microsoft Teams para ver todas as tarefas atribuídas. Para começar, selecione reticências **...** no painel esquerdo do Teams. Pesquise e selecione Tarefas por Planner e Tarefas Pendentes.

     :::image type="content" source="../assets/images/collaboration-control/tasks-planner.png" alt-text="Captura de tela é um exemplo das Tarefas do Planner e do To Do.":::

1. Depois de abrir o aplicativo Tarefas por Planner e Tarefas Pendentes, os usuários podem ver todas as tarefas que foram criadas em  seu aplicativo dentro da seção Atribuído a mim do aplicativo. Os usuários também podem exibir os detalhes de uma tarefa, adicionar anexos e marcá-los como concluídos.

### <a name="create-notes"></a>Criar anotações

Para criar uma anotação, selecione **a** guia Anotações do seu aplicativo, que redirecionaria para uma tela vazia na qual os usuários podem fornecer informações relevantes. Para adicionar uma nova anotação, selecione **Nova anotação**.
Depois de adicionar detalhes relevantes nas anotações, selecione **Salvar**.

### <a name="create-meetings"></a>Criar reuniões

Selecione **a guia** Reuniões em um registro para agendar reuniões internas e externas.

Para agendar uma reunião interna, selecione a lista suspensa ao **lado do botão** Nova reunião e, em seguida, selecione **Reunião interna**.

:::image type="content" source="../assets/images/collaboration-control/new-meeting-tab.png" alt-text="Captura de tela que descreve como agendar reuniões internas.":::

> [!NOTE]
>
> A Reserva de Clientes está habilitada se você tiver configurado o Microsoft Booking com uma configuração válida para seu aplicativo.

Na caixa **de diálogo Nova** reunião, os usuários podem fornecer informações relevantes sobre a reunião e selecionar **Salvar**. A reunião aparece na lista de reuniões.

:::image type="content" source="../assets/images/collaboration-control/new-meeting.png" alt-text="Captura de tela que descreve como agendar uma nova reunião.":::

Para agendar uma reunião externa com o cliente, selecione a lista suspensa ao lado do botão **Nova** reunião e selecione **Reserva do Cliente**. Se a  opção Reserva do Cliente não estiver disponível na lista suspensa  Nova Reunião, confirme se o aplicativo está configurado para Microsoft Bookings nas Configurações e se o usuário tem a função administrador do Bookings. Para obter mais informações, [consulte adicionar funcionários ao Bookings](/microsoft-365/bookings/add-staff?view=o365-worldwide&preserve-view=true). Você pode adicionar tipos de reserva adicionais adicionais ao seu negócio do Bookings.

:::image type="content" source="../assets/images/collaboration-control/customer-booking.png" alt-text="Captura de tela que descreve como agendar o Bookings do cliente.":::

Os usuários podem ver reuniões internas e Reservas de Clientes em sua lista de reuniões. Depois que a reunião for iniciada, os usuários poderão participar selecionando o **botão** Ingressar, que abre a reunião diretamente no Microsoft Teams.

Como as reuniões são apoiadas pelo Outlook, os usuários podem acessar o Bookings ou Calendário do Outlook para ver todas as reuniões listadas em um único calendário. As reuniões internas são listadas no calendário compartilhado.

A seguir estão as etapas para adicionar um calendário compartilhado ao Outlook (opcional):

1. Na guia Página Inicial da faixa de opções, na seção Gerenciar Calendários, selecione Abrir Calendário > Abrir Calendário Compartilhado.

1. Na caixa de diálogo Abrir um Calendário Compartilhado, insira o nome da pessoa. Selecione a pessoa que você está procurando e, em seguida, selecione OK.

No Painel esquerdo, em Calendários Compartilhados, agora você verá um calendário adicional com o nome da pessoa.

:::image type="content" source="../assets/images/collaboration-control/customer-booking.png" alt-text="Captura de tela que descreve como agendar o Bookings do cliente.":::

### <a name="add-files"></a>Adicionar arquivos

Abra a **guia Arquivos** em seu aplicativo e selecione **Carregar** para carregar arquivos OneDrive for Business ou do seu computador. Quando um arquivo é carregado com êxito, o modo de exibição de lista principal é atualizado automaticamente para mostrar os arquivos na lista.

:::image type="content" source="../assets/images/collaboration-control/meeting-calendar.png" alt-text="Captura de tela que descreve como abrir o calendário compartilhado.":::

### <a name="approvals"></a>Aprovações

As aprovações permitem que os usuários solicitem a saída de outras pessoas ao trabalhar em um registro. Por exemplo, solicite uma aprovação para concluir uma tarefa ou fechar um registro.

1. Vá para a **guia Aprovações** do aplicativo.

1. Quando não há solicitações de aprovação, os usuários veem a tela a seguir.

      :::image type="content" source="../assets/images/collaboration-control/no-approvals.png" alt-text="Captura de tela é um exemplo que não mostra nenhuma solicitação de aprovação.":::

1. Selecione a **nova solicitação de aprovação** para abrir o formulário de solicitação de aprovação.

      :::image type="content" source="../assets/images/collaboration-control/approval-request-form.png" alt-text="Captura de tela é um exemplo que mostra o novo formulário de solicitação de aprovação.":::

1. No formulário de solicitação de aprovação, preencha os campos obrigatórios e selecione **Enviar**, que cria uma solicitação e adicionado à lista.

      :::image type="content" source="../assets/images/collaboration-control/approvals-list.png" alt-text="Captura de tela é um exemplo que mostra a lista de aprovações.":::

1. Selecione a aprovação para exibir os detalhes.

Para obter mais informações sobre Aprovações, consulte [criar uma aprovação](https://support.microsoft.com/en-us/office/create-an-approval-6548a338-f837-4e3c-ad02-8214fc165c84).
