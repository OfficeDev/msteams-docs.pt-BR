---
title: Power Automate no aplicativo de controle de colaboração
author: surbhigupta
description: Neste módulo, saiba mais sobre o Power Automate no aplicativo de controle de colaboração no Microsoft Teams e como criar um aplicativo do Azure.
ms.localizationpriority: medium
ms.author: v-npaladugu
ms.topic: conceptual
ms.openlocfilehash: deda9f0178c51410e2208e81263b315de4ca1da4
ms.sourcegitcommit: 0bb822b30739e4a532a36764dad2dbf35a81ba29
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/03/2022
ms.locfileid: "67178743"
---
# <a name="power-automate"></a>Power Automate

O Power Automate pode ser usado para automatizar fluxos de trabalho em seu Collaboration Manager aplicativo. Por exemplo, crie tarefas automaticamente quando um novo registro é criado.

O conector de controle de colaboração permite que os desenvolvedores acessem APIs de controle de colaboração por gatilhos ou ações em fluxos de trabalho automatizados no Microsoft Power Automate, no Microsoft Power Apps e nos Aplicativos Lógicos do Azure.

> [!NOTE]
> Atualmente, os controles de colaboração estão disponíveis apenas na [versão prévia do desenvolvedor público](~/resources/dev-preview/developer-preview-intro.md).

Nesta versão, o conector permite que os criadores configurem gatilhos:

1. Quando uma sessão de Colaboração é criada.
1. Quando uma tarefa do planejador é criada ou modificada.

Ele também inclui um conjunto de APIs de controles de colaboração e tarefas que podem ser invocadas com um fluxo. As ações do conector são encontradas em seleções de etapa de fluxo de trabalho. O conector em si seria encontrado em conectores personalizados com opções configuráveis. Para usar o conector em sua solução, é necessário criar um Azure App confiável para seu ambiente executar os fluxos.

## <a name="create-an-azure-app"></a>Criar um Azure App

No [portal do Azure para](https://ms.portal.azure.com/#home) gerenciamento do Azure Active Directory, entre em sua conta com as permissões adequadas para adicionar um aplicativo de usuário ao seu ambiente com as seguintes etapas:

1. Na home page do portal do Azure, selecione **Azure Active Directory**. No Azure Active Directory, selecione a lista suspensa para **Adicionar** e selecione **Registro de aplicativo**.

   :::image type="content" source="../assets/images/collaboration-control/azure-active-directory-home-portal.png" alt-text="A captura de tela é um exemplo que mostra como adicionar um novo Registro de Aplicativo":::

   :::image type="content" source="../assets/images/collaboration-control/new-app-registration.png" alt-text="A captura de tela é um exemplo que mostra como adicionar um novo registro de aplicativo":::

1. No registro do aplicativo, defina o nome do aplicativo e adicione o URI de redirecionamento da Web a `https://global.consent.azure-apim.net/redirect`.

   :::image type="content" source="../assets/images/collaboration-control/register-an-application.png" alt-text="A captura de tela é um exemplo que mostra como registrar um aplicativo":::

1. Na seção Concessão Implícita e fluxos híbridos, selecione tokens de acesso e tokens de ID.

   :::image type="content" source="../assets/images/collaboration-control/authorisation-endpoint-tokens.png" alt-text="A captura de tela é um exemplo que mostra os tokens e os tokens de ID":::

1. Selecione a Permissão de API no painel esquerdo, **selecione Adicionar uma permissão** e, em seguida, pesquise a **permissão do Dynamic CRM** .

   :::image type="content" source="../assets/images/collaboration-control/dynamic-crm.png" alt-text="A captura de tela é um exemplo que mostra como adicionar uma permissão":::

1. Certifique-se de **selecionar user_impersonation** permissões depois de selecionar o Dynamics CRM.

   :::image type="content" source="../assets/images/collaboration-control/admin-consent-required.png" alt-text="A captura de tela é um exemplo que mostra como habilitar a caixa de seleção user_impersonation":::

1. Na página Certificados & Segredos, adicione um novo segredo do cliente e salve o valor para uso posterior **durante a** configuração da segurança do conector.

   :::image type="content" source="../assets/images/collaboration-control/copy-new-secret-value.png" alt-text="A captura de tela é um exemplo que mostra como copiar um novo valor secreto":::

1. Na página Visão geral do aplicativo, copie a **ID** do aplicativo (cliente) e salve-a para uso posterior durante a configuração da segurança do conector.

   :::image type="content" source="../assets/images/collaboration-control/application-client-ID.png" alt-text="A captura de tela é um exemplo que mostra como salvar a ID do cliente":::

Agora seu aplicativo do Azure está pronto e você precisa adicioná-lo como um aplicativo de usuário em seu ambiente.

## <a name="add-azure-app-to-power-automate-environment"></a>Adicionar aplicativo do Azure ao ambiente do Power Automate

1. Abra o portal do Power Apps, no canto superior direito, selecione **as configurações** e abra **Administração central**.

   :::image type="content" source="../assets/images/collaboration-control/power-apps-interface.png" alt-text="A captura de tela é um exemplo que mostra a interface do Power Apps":::

1. No centro de administração, selecione **Ambiente** no painel esquerdo e selecione seu ambiente na lista que você deseja adicionar ao aplicativo do conector.

   :::image type="content" source="../assets/images/collaboration-control/power-platform-admin-center.png" alt-text="A captura de tela é um exemplo que mostra como adicionar o aplicativo conector":::

1. Na página de detalhes do ambiente, selecione **Configurações**.

   :::image type="content" source="../assets/images/collaboration-control/settings-environment.png" alt-text="A captura de tela é um exemplo que mostra como selecionar configurações":::

1. Na página de detalhes das configurações, selecione **a seção Usuários + permissões** e selecione **Usuários do aplicativo**.

   :::image type="content" source="../assets/images/collaboration-control/users-link.png" alt-text="A captura de tela é um exemplo que mostra o link do usuário do aplicativo":::

1. Na página Usuários do aplicativo, selecione **o + Novo usuário do aplicativo**. **A janela Criar um usuário do** aplicativo é exibida.

   :::image type="content" source="../assets/images/collaboration-control/new-app-user.png" alt-text="A captura de tela é um exemplo que mostra o novo usuário do aplicativo":::

1. Selecione **+ Adicionar um aplicativo**.

   :::image type="content" source="../assets/images/collaboration-control/create-new-app-user.png" alt-text="A captura de tela é um exemplo que mostra como criar um novo usuário de aplicativo":::

1. Selecione seu aplicativo na caixa de pesquisa e selecione Adicionar novamente.

   :::image type="content" source="../assets/images/collaboration-control/add-app-aad.png" alt-text="A captura de tela é um exemplo que mostra como adicionar aplicativo do Azure Active Directory":::

Depois que o aplicativo for adicionado, defina a **unidade de negócios e** as funções **de** segurança para seu aplicativo conector. Selecione **Criar** e seu aplicativo estará na lista. Com o usuário do aplicativo definido no ambiente, podemos prosseguir para a configuração personalizada do conector.

## <a name="custom-connector-configuration"></a>Configuração personalizada do conector

1. Abra o PowerApps ou o Power Automate e selecione o menu **Conectores Personalizados** . Selecione **editar para** o conector de Colaboração.

   :::image type="content" source="../assets/images/collaboration-control/collaboration-connector.png" alt-text="menu do conector personalizado":::

1. Na guia Informações Gerais, insira o host com o endereço do domínio de instância do Dynamic 365 (sem o https://).

   :::image type="content" source="../assets/images/collaboration-control/general-information.png" alt-text="A captura de tela é um exemplo que mostra as informações gerais":::

1. Na guia Segurança, insira as seguintes entradas:

   * Segredo do cliente: use o valor do segredo do aplicativo salvo na entrada.
   * ID do cliente: seu aplicativo do Azure (ID do cliente).
   * URL do recurso: a URL da sua instância do Dynamic 365 (`https://org.crm.dynamics.com/`).
   * Escopo: igual ao mostrado acima. Sufixo padrão (`https://org.crm.dynamics.com/.default`).

   :::image type="content" source="../assets/images/collaboration-control/dynamic-365-instance.png" alt-text="A captura de tela é um exemplo que mostra a instância do Dynamic 365.":::

1. Selecione **Atualizar conector para** salvar as alterações e permitir que seu fluxo estabeleça conexões.

   :::image type="content" source="../assets/images/collaboration-control/custom-connector.png" alt-text="captura de tela é um exemplo que mostra o conector personalizado.":::

## <a name="how-to-invoke-the-connector"></a>Como invocar o conector  

Gatilhos e ações são predefinido com entrada e saída configuráveis como uma etapa de fluxo de trabalho. Adicionar a etapa de fluxo de trabalho à posição correta do fluxo de trabalho com a configuração correta de entrada e saída para definir quando o gatilho ou a ação deve ser invocado.

  :::image type="content" source="../assets/images/collaboration-control/invoke-the-connector.png" alt-text="A captura de tela é um exemplo que mostra como invocar o conector.":::

### <a name="triggers-and-actions-supported-with-connector"></a>Gatilhos e ações compatíveis com o conector

Os seguintes gatilhos e ações têm suporte em um fluxo:

* **Gatilhos**

  1. Quando uma sessão de colaboração é criada.

      :::image type="content" source="../assets/images/collaboration-control/colab-session-created-preview.png" alt-text="Sessão de colaboração criada":::

      **Âmbito:** Um escopo a ser limitado, quais linhas podem disparar o fluxo.

      **Execute como:** O usuário em execução para etapas em que as conexões de invocador são usadas.

  1. Quando uma tarefa é criada ou modificada

      :::image type="content" source="../assets/images/collaboration-control/task-created.png" alt-text="A captura de tela é um exemplo que mostra que a tarefa foi criada ou modificada":::

      Por padrão, a tarefa do Planejador de gatilhos será desabilitada e não será disparada. Para habilita-lo, as seguintes etapas devem ser concluídas pelo administrador do locatário:

      * Crie um tíquete de suporte no caminho Power Apps/Controles/Configurações de colaboração.
      * Solicite que seu ambiente esteja habilitado para o conector de Colaboração e forneça a URL do Ambiente (preferencial) ou a ID da Organização.  
      * Você pode adicionar o seguinte texto de exemplo à solicitação de suporte: "Habilitar a URL do Ambiente: `url` para o Conector de Colaboração".
      * Para abrir um tíquete de suporte, consulte [Obter Ajuda + Suporte](/power-platform/admin/get-help-support)

* **Ações**

  1. Iniciar sessão de colaboração

      :::image type="content" source="../assets/images/collaboration-control/begin-collab-session.png" alt-text="A captura de tela é um exemplo que mostra como iniciar a sessão de colaboração":::

     Esta ação de etapa cria uma nova sessão de colaboração para sua entidade de negócios do dataverse:

      * **Nome do Aplicativo:** O nome do aplicativo associado, por exemplo, pode ser "Collaboration Manager para empréstimos" ou "Collaboration Manager auditoria de empréstimo fechado".
      * **Nome da entidade raiz de colaboração:** O tipo de registro de aplicativo (nome da tabela), por exemplo, pode ser "msfi_loanapplication" para um aplicativo Collaboration Manager for Loan.
      * **ID da entidade raiz de colaboração:** ID do registro de aplicativo associado, por exemplo, pode ser a ID de um registro de aplicativo de empréstimo.  

      ***Opções avançadas***

      **Metadados (Avançado):** Adiciona metadados para uma sessão de colaboração.

        * **Tipo OData:** Esse campo precisará ser fornecido se a outra chave/valor estiver definida e precisar corresponder exatamente a #Microsoft.Dynamics.CRM.m365_collaborationmetadata.
        * **Chave:** Chave associada ao atributo de metadados.
        * **Valor:** Valor associado ao atributo de metadados.

  1. Recuperar sessão de colaboração

      ::image type="content" source=".. /assets/images/collaboration-control/retrieve-collab-session.png" alt-text="A captura de tela é um exemplo que mostra como recuperar a sessão de colaboração.":::

     Esta ação de etapa retorna a sessão de colaboração que corresponde às entradas fornecidas:

     * **Nome do Aplicativo:** O contexto do nome do aplicativo para a sessão de colaboração.
     * **ID da entidade raiz de colaboração:** A ID da entidade de negócios para a sessão de colaboração.  
     * **Nome da entidade raiz de colaboração:** O tipo de entidade de negócios para a sessão de colaboração.

  1. Atualizar sessão de Colaboração

      :::image type="content" source="../assets/images/collaboration-control/update-collab-session.png" alt-text="A captura de tela é um exemplo que mostra como atualizar a sessão de colaboração.":::

     Esta ação de etapa atualiza uma sessão de colaboração existente:

     * **ID raiz da colaboração:** O GUID para a sessão de colaboração de destino/registro raiz.
     * **ID da entidade raiz de colaboração:** A ID da entidade de negócios à qual a sessão de colaboração se refere.
     * **Nome da entidade raiz de colaboração:** O nome do tipo de entidade de negócios ao qual a sessão de colaboração se refere.

     ***Opções avançadas:***

      **Criar metadados (avançado):** Adiciona mais metadados a um registro de sessão de colaboração.

      * **Tipo OData:** Esse campo precisará ser fornecido se a outra chave/valor estiver definida e precisar corresponder exatamente a #Microsoft.Dynamics.CRM.m365_collaborationmetadata.
      * **Chave:** Chave associada ao atributo de metadados.
      * **Valor:** Valor associado ao atributo de metadados.

      **Atualizar metadados (avançado): Atualizações** metadados existentes em um registro de sessão de colaboração.

      * **Tipo OData:** Esse campo precisará ser fornecido se a outra chave/valor estiver definida e precisar corresponder exatamente a #Microsoft.Dynamics.CRM.m365_collaborationmetadata.
      * **Chave:** Chave associada ao atributo de metadados a ser atualizado.
      * **Valor:** Valor associado ao atributo de metadados.

      **Excluir metadados (avançado):** Remove todos os metadados existentes em um registro de sessão de colaboração.

      * **Tipo OData:** Esse campo precisará ser fornecido se a outra chave/valor estiver definida e precisar corresponder exatamente a #Microsoft.Dynamics.CRM.m365_collaborationmetadata.
      * **Chave:** Chave associada ao atributo de metadados a ser removido.

  1. Associar Mapa de Colaboração (externo)

      :::image type="content" source="../assets/images/collaboration-control/associate-collab-map.png" alt-text="A captura de tela é um exemplo que mostra como associar o mapa de colaboração.":::

     Esta ação de etapa cria um mapeamento de uma entidade de colaboração externa (fora do dataverso) com sua sessão de colaboração:

     * **ID raiz da colaboração:** O identificador exclusivo da sessão de colaboração a ser mapeado para uma entidade colaborativa.
     * **ID Externa do Mapa de Colaboração:** A ID de recurso colaborativo externo a ser mapeada.
     * **Nome da Entidade do Mapa de Colaboração:** O nome do tipo de entidade colaborativa externa a ser mapeado.

     ***Opções avançadas:***

     **Metadados:** Adicione metadados para um mapa de colaboração.
     * **Tipo OData:** Esse campo precisará ser fornecido se a outra chave/valor estiver definida e precisar corresponder exatamente a #Microsoft.Dynamics.CRM.m365_collaborationmetadata.
     * **Chave:** Chave associada ao atributo de metadados.
     * **Valor:** Valor associado ao atributo de metadados.

  1. Associar Mapa de Colaboração (interno)

      :::image type="content" source="../assets/images/collaboration-control/associate-collab-map-internal.png" alt-text="A captura de tela é um exemplo que mostra como associar o mapa de colaboração interno.":::

     Esta ação de etapa cria um mapeamento de uma entidade de colaboração (tabela de dataverso) com sua sessão de colaboração. Internas destinam-se a criar mapeamentos apenas entre entidades/tabelas internas do Dataverse.

     * **ID raiz da colaboração:** O identificador exclusivo da sessão de colaboração a ser mapeado para uma entidade colaborativa.
     * **ID da Entidade do Mapa de Colaboração:** A ID de entidade colaborativa do Dataverse a ser mapeada.
     * **Nome da Entidade do Mapa de Colaboração:** O nome do tipo de entidade colaborativa do Dataverse a ser mapeado.

     ***Opções avançadas:***

     **Metadados (Avançado)** Adicione metadados para um mapa de colaboração.

     * **Tipo OData:** Esse campo precisará ser fornecido se a outra chave/valor estiver definida e precisar corresponder exatamente a #Microsoft.Dynamics.CRM.m365_collaborationmetadata
     * **Chave:** Chave associada ao atributo de metadados
     * **Valor:** Valor associado ao atributo de metadados

  1. Atualizar Mapa de Colaboração

      :::image type="content" source="../assets/images/collaboration-control/update-collab-map.png" alt-text="A captura de tela é um exemplo que mostra como atualizar o mapa de colaboração.":::

     Esta ação de etapa atualiza um mapa de colaboração existente:

     * **ID do Mapa de Colaboração:** O identificador exclusivo do mapa de colaboração a ser atualizado.
     * **ID da Entidade do Mapa de Colaboração:** A ID da entidade colaborativa a ser mapeada. Esse valor deverá estar vazio se a ID externa for Fornecida
     * **Nome da Entidade do Mapa de Colaboração**
     * **ID Externa do Mapa de Colaboração:** A ID de recurso colaborativo externo a ser mapeada. Esse valor deverá estar vazio se a ID da entidade for fornecida.  

     ***Opções avançadas:***

     **Criar metadados:** Adiciona mais metadados a um registro de mapa de colaboração.

     * **Tipo OData:** Esse campo precisará ser fornecido se a outra chave/valor estiver definida e precisar corresponder exatamente a #Microsoft.Dynamics.CRM.m365_collaborationmetadata.
     * **Chave:** Chave associada ao atributo de metadados.
     * **Valor:** Valor associado ao atributo de metadados.

     **Atualizar metadados: Atualizações** metadados existentes em um registro de mapa de colaboração.

     * **Tipo OData:** Esse campo precisará ser fornecido se a outra chave/valor estiver definida e precisar corresponder exatamente a #Microsoft.Dynamics.CRM.m365_collaborationmetadata
     * **Chave:** Chave associada ao atributo de metadados a ser atualizado
     * **Valor:** Valor associado ao atributo de metadados

     **Excluir metadados:** Remove todos os metadados existentes em um registro de mapa de colaboração.

     * **Tipo OData:** Esse campo precisará ser fornecido se a outra chave/valor estiver definida e precisar corresponder exatamente a #Microsoft.Dynamics.CRM.m365_collaborationmetadata.
     * **Chave:** Chave associada ao atributo de metadados a ser removido.

  1. Obter metadados de colaboração

      :::image type="content" source="../assets/images/collaboration-control/get-collab-metadata.png" alt-text="A captura de tela é um exemplo que mostra como obter metadados de colaboração.":::

     Esta ação de etapa lista todos os metadados correspondentes ao filtro especificado.

     **Filtro:** Um filtro a ser aplicado à consulta de metadados.
     Exemplo de recuperação de todos os metadados relacionados a uma ID de entidade de mapa de colaboração  
     m365_entityname eq 'm365_collaborationmap' e m365_entityid eq 'GUID'

  1. Criar tarefa do Planner

      :::image type="content" source="../assets/images/collaboration-control/create-planner-task.png" alt-text="A captura de tela é um exemplo que mostra como criar uma tarefa do planejador.":::

     Esta ação de etapa cria uma Tarefa do Planejador de Grafo usando a tabela virtual da tarefa Planner dos controles de colaboração:

     * **ID raiz de colaboração (obrigatório):** Identificador exclusivo da sessão de colaboração
     * **ID do plano (obrigatório):** ID do plano à qual a tarefa pertence
     * **Título (Obrigatório):** Título da tarefa
     * **Atribuições:** Um objeto formatado em json que representa todas as atribuições de uma tarefa. Veja, [tipo de recurso plannerAssignments](/graph/api/resources/plannerassignments)
     * **ID do bucket:** ID do bucket à qual as tarefas pertencem.
     * **Prioridade:** Prioridade da tarefa. 0 e 10 (inclusive) aumentando o valor sendo prioridade mais baixa.

     ***Opções avançadas:***

     * **Contagem de Itens da Lista de Verificação Ativa** (Avançado): Número de itens da lista de verificação com valor definido como false que representa itens incompletos.
     * **Categorias Aplicadas:** Um objeto formatador json que representa todas as categorias a serem aplicadas à tarefa. Consulte, [tipo de recurso plannerAppliedCategories](/graph/api/resources/plannerappliedcategories).
     * **Prioridade do destinatário:** Dicas de valor de cadeia de caracteres usadas para ordenar itens desse tipo em uma exibição de lista. Veja, [usando dicas de pedido no Planner](/graph/api/resources/planner-order-hint-format)
     * **Contagem de Itens da Lista de Verificação:** Número de itens da lista de verificação presentes na tarefa.
     * **Concluído por:** Um objeto formatado em json que representa a identidade do usuário que concluiu a tarefa. Veja, tipo [de recurso identitySet](/graph/api/resources/identityset)
     * **ID do thread de conversa:** ID do thread da conversa na tarefa. Essa é a ID do objeto de thread de conversa criado no grupo.
     * **Criado por:** Um objeto formatado em json que representa a identidade do usuário que criou a tarefa. Veja, tipo [de recurso identitySet](/graph/api/resources/identityset)
     * **Data de Conclusão:** Data e hora em que a tarefa deve ser concluída. O tipo Timestamp representa informações de data e hora usando o formato ISO 8601 e está sempre no horário UTC. Por exemplo, meia-noite UTC em 1º de janeiro de 2014 é 01-01-01T00:00:00Z.
     * **Dica de pedido:** Dica usada para ordenar itens desse tipo em um modo de exibição de lista. O formato é definido como descrito usando [dicas de ordem no Planner](/graph/api/resources/planner-order-hint-format).
     * **Porcentagem Concluída:** Porcentagem de conclusão da tarefa (0-100)
     * **Tipo de visualização:** Isso define o tipo de visualização que aparece na tarefa. Os valores possíveis são: automatic, noPreview, checklist, description, reference.
     * **Contagem de referências:** Número de referências externas que existem na tarefa.
     * **Data e hora de início:** Data e hora em que a tarefa é iniciada. O tipo Timestamp representa informações de data e hora usando o formato ISO 8601 e está sempre no horário UTC. Por exemplo, meia-noite UTC em 1º de janeiro de 2014 é 01-01-01T00:00:00Z.

  1. Obter tarefa do Planner

      :::image type="content" source="../assets/images/collaboration-control/get-planner-task.png" alt-text="A captura de tela é um exemplo que mostra a tarefa obter planejador.":::

     Esta ação de etapa retorna dados da Tarefa do Planner usando a tabela virtual da tarefa Planner dos controles de colaboração:

     **ID da tarefa (obrigatório):** Identificador exclusivo da tarefa

  1. Atualizar Tarefa do Planejador

      :::image type="content" source="../assets/images/collaboration-control/update-planner-task-preview.png" alt-text="Atualizar tarefa do planejador":::

     Esta ação de etapa atualiza um registro de tarefa do planejador usando a tabela virtual da tarefa Planner dos controles de colaboração

     * **ID da tarefa (obrigatório):** Identificador exclusivo da tarefa.
     * **Atribuições:** Um objeto formatado em json que representa todas as atribuições de uma tarefa. Ver. Tipo de recurso plannerAssignments – Microsoft Graph v1.0 | Microsoft Docs  
     * **ID do bucket:** ID do bucket ao local em que a tarefa pertence.  
     * **Detalhes da tarefa do Planner:** Representa as informações adicionais sobre uma tarefa.
     * **Data de Conclusão:** Data e hora em que a tarefa deve ser concluída. O tipo Timestamp representa informações de data e hora usando o formato ISO 8601 e está sempre no horário UTC. Por exemplo, meia-noite UTC em 1º de janeiro de 2014 é 01-01-01T00:00:00Z.
     * **Prioridade:** Prioridade da tarefa. 0 e 10 (inclusive) aumentando o valor sendo prioridade mais baixa.  
     * **Porcentagem Concluída:** Porcentagem de conclusão da tarefa (0-100)
     * **Título:** Título da tarefa

     ***Opções avançadas:***

     * **Categorias Aplicadas:** Um objeto formatado em json que representa todas as categorias a serem aplicadas à tarefa. Consulte, [tipo de recurso plannerAppliedCategories](/graph/api/resources/plannerappliedcategories).
     * **Prioridade do destinatário:** Dicas de valor de cadeia de caracteres usadas para ordenar itens desse tipo em uma exibição de lista. Veja, [usando dicas de pedido no Planner](/graph/api/resources/planner-order-hint-format).
     * **ID do thread de conversa:** ID do thread da conversa na tarefa. Essa é a ID do objeto de thread de conversa criado no grupo.
     * **ID raiz da colaboração:** O identificador exclusivo da sessão de colaboração.
     * **Dica de pedido:** Dica usada para ordenar itens desse tipo em um modo de exibição de lista. O formato é definido como estrutura de tópicos aqui.
     * **Data e hora de início:** Data e hora em que a tarefa é iniciada. O tipo Timestamp representa informações de data e hora usando o formato ISO 8601 e está sempre no horário UTC. Por exemplo, meia-noite UTC em 1º de janeiro de 2014 é 01-01-01T00:00:00Z.

**Cenário de fluxo de exemplo**

A seguir estão alguns exemplos de fluxos:

1. Obtendo uma resposta dos formulários da Microsoft, criando uma sessão de Colaboração e uma tarefa associada.

   :::image type="content" source="../assets/images/collaboration-control/response-submitted.png" alt-text="A captura de tela é um exemplo que mostra como enviar uma nova resposta.":::

1. Sempre que uma sessão de colaboração for criada, capture os detalhes e envie uma notificação por email.

   :::image type="content" source="../assets/images/collaboration-control/colab-session-created-preview.png" alt-text="A captura de tela é um exemplo que mostra a sessão de Colaboração criada":::

> [!NOTE]
> Vários fluxos podem ser disparados dessa maneira para executar ações diferentes, usando dados da resposta da criação da sessão de Colaboração.
