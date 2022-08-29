---
title: Tabelas virtuais para tarefas, reuniões e arquivos no aplicativo de controle de colaboração
author: surbhigupta
description: Neste módulo, saiba mais sobre tabelas virtuais para tarefas, reuniões e arquivos no aplicativo de controle colaboração no Microsoft Teams.
ms.localizationpriority: medium
ms.author: v-npaladugu
ms.topic: conceptual
ms.openlocfilehash: 1913b379e9f24d36948a05190a4ae1804a8ec728
ms.sourcegitcommit: 442d2c8e80a2605b6d0215c973557471f18f8121
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/11/2022
ms.locfileid: "67314592"
---
# <a name="virtual-tables-for-tasks-meetings-files"></a>Tabelas virtuais para tarefas, reuniões, arquivos

Uma nova funcionalidade com esta versão é um conjunto de tabelas virtuais. Eles permitem que os desenvolvedores interajam com o Graph por meio de APIs OData.

A solução principal de controles de colaboração inclui um conjunto de tabelas [virtuais, que](/power-apps/developer/data-platform/virtual-entities/get-started-ve) pode ser usado para acesso programático aos dados criados pelos controles de Colaboração.

> [!NOTE]
> Atualmente, os controles de colaboração estão disponíveis apenas na [versão prévia do desenvolvedor público](~/resources/dev-preview/developer-preview-intro.md).

> [!TIP]
> [](/power-apps/developer/data-platform/virtual-entities/get-started-ve) As tabelas virtuais também conhecidas como entidades virtuais permitem a integração de dados que residem em sistemas externos, representando perfeitamente esses dados como tabelas no Microsoft Dataverse, sem replicação de dados e, muitas vezes, sem codificação personalizada.

O sistema externo usado pelos controles de Colaboração é o Microsoft Graph. Há tabelas virtuais para eventos de calendário de grupo, compromissos de reserva, planos de planejador ou tarefas e unidades, pastas e arquivos do SharePoint.

Este artigo fornece exemplos que demonstram como acessar as tabelas virtuais usando a API REST do Dataverse para executar operações CRUD (Criar, Ler, Atualizar e Excluir).

> [!TIP]
> Para obter mais informações sobre a API REST do Dataverse, [consulte usar a API Web do Microsoft Dataverse](/power-apps/developer/data-platform/webapi/overview).

* As tabelas virtuais usam a API Web padrão do Dataverse, o que facilita o uso das tabelas virtuais para preencher dados em seu aplicativo.
* As tabelas virtuais implementam fluxos de trabalho complexos necessários para dar suporte a controles de colaboração e eles são executados em data centers da Microsoft para obter um desempenho ideal.  
* As tabelas virtuais usam os recursos padrão de registro em log e monitoramento do Dataverse.

Depois de instalar os controles de Colaboração, as tabelas virtuais podem ser tratadas como outro serviço para seu aplicativo que pode depender.

:::image type="content" source="~/assets/images/collaboration-control/vt-overview.png" alt-text="Visão geral das tabelas virtuais":::

**Pré-requisitos**

Para acompanhar este artigo, você precisará de:

1. Um ambiente do Dataverse em que os controles de Colaboração foram instalados.
1. Uma conta de usuário no ambiente do Dataverse, que tem a função De usuário de **controles** de colaboração atribuída a ela.
1. Uma ferramenta de terceiros, por exemplo: Post man ou algum código C# personalizado que permite que você se autentique em instâncias do Microsoft Dataverse e para compor e enviar solicitações de API Web e exibir respostas.  

> [!TIP]
> A Microsoft fornece informações sobre como configurar um ambiente do Postman que se conecta à instância do Dataverse e usar o Postman para executar operações com a API Web. Consulte [Usar o Postman com a API Web do Microsoft Dataverse](/power-apps/developer/data-platform/webapi/use-postman-web-api).

## <a name="virtual-tables-sample-scenario"></a>Cenário de exemplo de tabelas virtuais

O cenário descrito neste guia usa as tabelas virtuais Plano do Planner e Tarefa. O cenário descrito é o mesmo usado pelo controle colaboração de tarefas. Da perspectiva do usuário, o cenário mostra como um Plano do Planner e várias Tarefas são criadas e associadas a um registro comercial específico. O cenário continua a mostrar como recuperar as tarefas associadas ao registro comercial e como ler, atualizar e excluir uma tarefa específica do planejador.

O diagrama de sequência a seguir explica a interação entre o cliente, que pode ser o controle de colaboração Tarefas, a [API](/rest/api/industry/collaboration-controls/) de Colaboração e as tabelas virtuais Plano planejador e tarefa.

:::image type="content" source="~/assets/images/collaboration-control/vt-sequence.png" alt-text="Diagrama de sequência para tabelas virtuais":::

## <a name="virtual-tables-basic-operations"></a>Operações básicas de tabelas virtuais

Esta seção descreve as solicitações e respostas HTTP para cada etapa no cenário de exemplo.

**Tarefa 1: Recuperar a ID do Grupo**

Recupere a ID do Grupo usada [nas configurações da Colaboração](~/samples/app-with-collaboration-controls.md#define-settings-for-your-collaboration).

> [!NOTE]
> O usuário que você usa para criar o Plano nas tarefas subsequentes deve ser um membro desse grupo. Caso contrário, você receberá a resposta 403 Proibido.

**Tarefa 2: Iniciar uma sessão de Colaboração**

Uma sessão de colaboração é um registro na tabela raiz de colaboração, que permite associar várias colaborações, por exemplo, tarefas, eventos, compromissos com um registro comercial.

Uma sessão de colaboração permite executar operações como a lista de eventos de calendário associados a um registro comercial, por exemplo, um aplicativo de inspeções.

# <a name="request"></a>[Solicitação](#tab/request)

```http
    HTTP/1.1 POST https://[Organization URI]/api/data/v9.0/m365_begincollaborationsession  
```

```json
{
    "applicationName": "{{applicationName}}", 
    "collaborationRootEntityId": "{{collaborationRootEntityId}}", 
    "collaborationRootEntityName": "{{entityName}}" 
}
```

* `applicationName`: nome exclusivo para o aplicativo
* `collaborationRootEntityName`: nome da entidade de registro comercial  
* `collaborationRootEntityId`: ID (chave primária) do registro comercial específico

# <a name="response"></a>[Response](#tab/response)

```http
    HTTP/1.1 200 OK 
```

```json
{ 
    "@odata.context": "https:// [Organization URI]/api/data/v9.0/$metadata#Microsoft.Dynamics.CRM.m365_begincollaborationsessionResponse", 
    "collaborationRootId": "72fc6b52-39d5-ec11-a7b6-0022481bfe8f" 
}
```

---

Mantenha o controle do `collaborationRootId` que será necessário em solicitações subsequentes.

**Tarefa 3: Criar um plano do Planner**

Crie um Plano do Planner e associá-lo à sessão de colaboração criada acima com `Group ID` e `collaborationRootId`.

# <a name="request"></a>[Solicitação](#tab/request1)

```http
    HTTP/1.1 POST https://[Organization URI]/api/data/v9.0/m365_graphplannerplans  
```

```json

{ 
    "m365_collaborationrootid": "{{collaborationRootId}}", 
    "m365_owner": "{{groupId}}", 
    "m365_title": "{{planTitle}}" 
}

```

* `collaborationRootId`: identifica a sessão de colaboração à qual desejamos associar esse plano, use o valor da tarefa 2

* `groupId`: identifica o grupo que será o proprietário desse plano, use o valor da etapa 1

* `planTitle`: título do plano

# <a name="response"></a>[Response](#tab/response1)

```http
    HTTP/1.1 201 Created 
```

```json

{ 
    "@odata.context": "https:// [Organization URI]/api/data/v9.0/$metadata#m365_graphplannerplans/$entity", 
    "@odata.etag": "W/\"JzEtUGxhbiAgQEBAQEBAQEBAQEBAQEBARCc=\"", 
    "m365_createdby": "{\"user\":{\"displayName\":null,\"email\":null,\"id\":\"be330617-0e2b-48e9-8bf7-429a09c78e65\"},\"group\":null}", 
    "m365_createddatetime": "2022-05-16T16:58:33.1833561Z", 
    "m365_owner": "03614cef-8f5b-4265-9944-080d013c55d6", 
    "m365_title": "Multi-byte plan", 
    "m365_id": "8I6fu1kNS0elsbTxd67bi2UADnJu", 
    "m365_collaborationrootid": "72fc6b52-39d5-ec11-a7b6-0022481bfe8f", 
    "m365_graphplannerplanid": "5c9c3ecf-f157-0f67-dcd9-733a77ad593e", 
    "m365_details": null 
} 

```

---

Mantenha o controle do`m365_id` que será necessário em solicitações subsequentes.

**Tarefa 4: Criar uma tarefa do Planner**

Criar uma tarefa do Planner com `PlanId` e `collaborationRootId`. você pode criar várias Tarefas do Planner e associá-las à sessão de colaboração criada anteriormente.

# <a name="request"></a>[Solicitação](#tab/request2)

```http
    HTTP/1.1 POST https://[Organization URI]/api/data/v9.0/m365_graphplannertasks  
```

```json
{ 
    "m365_collaborationrootid": "{{collaborationRootId}}", 
    "m365_planid": "{{planId}}", 
    "m365_title": "{{taskTitle}}", 
    "m365_duedatetime": "2022-05-04T08:00:00Z", 
    "m365_assignments": "{\"me\":{\"orderHint\":\" !\",\"@odata.type\":\"#microsoft.graph.plannerAssignment\"}}" 
} 

```

* `collaborationRootId`: identifica a sessão de colaboração à qual desejamos associar esse plano, o valor da tarefa 2
* `planId`: identifica o plano ao qual essa tarefa será atribuída, use o valor da etapa anterior
* `taskTitle`: título da tarefa

# <a name="response"></a>[Response](#tab/response2)

```http
    HTTP/1.1 201 Created 
```

```json

{ 
    "@odata.context": "https://mwtmarkwallaceunmanaged.crm10.dynamics.com/api/data/v9.0/$metadata#m365_graphplannertasks/$entity", 
    "@odata.etag": "W/\"JzEtVGFzayAgQEBAQEBAQEBAQEBAQEBARCc=\"", 
    "m365_activechecklistitemcount": 0, 
    "m365_appliedcategories": "{}", 
    "m365_assigneepriority": "8585488865579062167", 
    "m365_assignments": "{\"be330617-0e2b-48e9-8bf7-429a09c78e65\":{\"assignedBy\":{\"user\":{\"displayName\":null,\"email\":null,\"id\":\"be330617-0e2b-48e9-8bf7-429a09c78e65\"},\"group\":null},\"assignedDateTime\":\"2022-05-16T16:58:47.571364+00:00\",\"orderHint\":\"8585488866179218449P`\",\"@odata.type\":\"#microsoft.graph.plannerAssignment\"}}", 
    "m365_checklistitemcount": 0, 
    "m365_createdby": "{\"user\":{\"displayName\":null,\"email\":null,\"id\":\"be330617-0e2b-48e9-8bf7-429a09c78e65\"},\"group\":null}", 
    "m365_createddatetime": "2022-05-16T16:58:47Z", 
    "m365_duedatetime": "2022-05-04T08:00:00Z", 
    "m365_hasdescription": false, 
    "m365_orderhint": "8585488865579062167", 
    "m365_percentcomplete": 0, 
    "m365_priority": 5, 
    "m365_planid": "8I6fu1kNS0elsbTxd67bi2UADnJu", 
    "m365_previewtype": "automatic", 
    "m365_referencecount": 0, 
    "m365_title": "Team-oriented discrete time-frame", 
    "m365_id": "8WSKWaEqAU-aZV4h9VUn0GUALXbH", 
    "m365_collaborationrootid": "72fc6b52-39d5-ec11-a7b6-0022481bfe8f", 
    "m365_graphplannertaskid": "0a2115b9-8b03-90ee-b450-42005d906ce8", 
    "m365_completedby": null, 
    "m365_details": null, 
    "m365_completeddatetime": null, 
    "m365_conversationthreadid": null, 
    "m365_bucketid": null, 
    "m365_startdatetime": null 
} 

```

---

Mantenha o controle do `m365_graphplannertaskid` que será necessário em solicitações subsequentes.

> [!NOTE]
> A `m365_graphplannertaskid` chave primária do registro na tabela virtual da Tarefa do Planner. Todas as solicitações subsequentes à tabela virtual para interagir com esse registro devem usar essa chave primária. Isso será conhecido como as etapas `plannerTaskId` subsequentes neste documento.

Você deve repetir essa etapa para criar várias tarefas no plano.

**Tarefa 5: Recuperar tarefas associadas do Planner**

Recupere tarefas associadas do Planner associadas `collaborationRootId` à sessão de colaboração criada anteriormente.

# <a name="request"></a>[Solicitação](#tab/request3)

```http
    HTTP/1.1 GET https://[Organization URI]/api/data/v9.0/ m365_graphplannertasks?$filter=m365_collaborationrootid eq '{{collaborationRootId}}'&$select=m365_graphplannertaskid,m365_title,m365_createddatetime  
```

* `$filter`: use a $filter do sistema para solicitar registros associados à sessão de colaboração (especificando a ID do registro raiz de colaboração).
* `$select`: use a $select de consulta do sistema para solicitar propriedades específicas.

# <a name="response"></a>[Response](#tab/response3)

```http
    HTTP/1.1 200 OK 
```

```json

{ 

    "@odata.context": "https://mwtmarkwallaceunmanaged.crm10.dynamics.com/api/data/v9.0/$metadata#m365_graphplannertasks(m365_graphplannertaskid,m365_title,m365_createddatetime)", 
    "value": [ 
        { 
            "@odata.etag": "W/\"JzEtVGFzayAgQEBAQEBAQEBAQEBAQEBARCc=\"", 
            "m365_graphplannertaskid": "8537731e-9414-1091-8d7d-ce5b74fc2477", 
            "m365_title": "Diverse executive core", 
            "m365_createddatetime": "2022-05-16T16:58:45Z", 
            "m365_id": "N_A2qmo3j0uvZZY1yd6V_GUADDEg", 
            "m365_collaborationrootid": "72fc6b52-39d5-ec11-a7b6-0022481bfe8f" 
        }, 
        { 
            "@odata.etag": "W/\"JzEtVGFzayAgQEBAQEBAQEBAQEBAQEBARCc=\"", 
            "m365_graphplannertaskid": "4a89895a-050e-9165-a6e4-19c3850f22ec", 
            "m365_title": "Cloned didactic open architecture", 
            "m365_createddatetime": "2022-05-16T16:58:41Z", 
            "m365_id": "--U0zbgsO0us084C0yCyEWUALbWw", 
            "m365_collaborationrootid": "72fc6b52-39d5-ec11-a7b6-0022481bfe8f" 
        }, 
        { 
            "@odata.etag": "W/\"JzEtVGFzayAgQEBAQEBAQEBAQEBAQEBARCc=\"", 
            "m365_graphplannertaskid": "20a08b8c-394b-b3fb-f9d1-47496df7a67b", 
            "m365_title": "Synergized zero defect interface", 
            "m365_createddatetime": "2022-05-16T16:58:43Z", 
            "m365_id": "AMn3RtbmV0m6cvkp5HKDCWUAKI0_", 
            "m365_collaborationrootid": "72fc6b52-39d5-ec11-a7b6-0022481bfe8f" 
        } 
    ] 
} 

```

---

Acompanhe as IDs `m365_id‘s` que serão necessárias em solicitações subsequentes.

**Tarefa 6: Recuperar uma tarefa do Planner**

Recupere uma tarefa do Planner com `PlannerTaskID` a qual executar uma operação de leitura em uma das tarefas do planejador criadas anteriormente.

# <a name="request"></a>[Solicitação](#tab/request4)

```http
    HTTP/1.1 GET https://[Organization URI]/api/data/v9.0/m365_graphplannertasks({{plannerTaskId}})  
```

* `plannerTaskId`: a chave primária para o registro de tarefa do planejador é a `m365_graphplannertaskid` propriedade.

# <a name="response"></a>[Response](#tab/response4)

```http
    HTTP/1.1 200 OK 
```

```json
{ 
    "@odata.context": "https://mwtmarkwallaceunmanaged.crm10.dynamics.com/api/data/v9.0/$metadata#m365_graphplannertasks/$entity", 
    "@odata.etag": "W/\"JzEtVGFzayAgQEBAQEBAQEBAQEBAQEBARCc=\"", 
    "m365_activechecklistitemcount": 0, 
    "m365_appliedcategories": "{}", 
    "m365_assigneepriority": "8585488204334528131", 
    "m365_assignments": "{\"be330617-0e2b-48e9-8bf7-429a09c78e65\":{\"assignedBy\":{\"user\":{\"displayName\":null,\"email\":null,\"id\":\"be330617-0e2b-48e9-8bf7-429a09c78e65\"},\"group\":null},\"assignedDateTime\":\"2022-05-17T11:20:52.0247676+00:00\",\"orderHint\":\"8585488204934840644P2\",\"@odata.type\":\"#microsoft.graph.plannerAssignment\"}}", 
    "m365_checklistitemcount": 0, 
    "m365_createdby": "{\"user\":{\"displayName\":null,\"email\":null,\"id\":\"be330617-0e2b-48e9-8bf7-429a09c78e65\"},\"group\":null}", 
    "m365_createddatetime": "2022-05-17T11:20:52Z", 
    "m365_duedatetime": "2022-05-04T08:00:00Z", 
    "m365_orderhint": "8585488204334528131", 
    "m365_percentcomplete": 0, 
    "m365_priority": 5, 
    "m365_planid": "8I6fu1kNS0elsbTxd67bi2UADnJu", 
    "m365_previewtype": "automatic", 
    "m365_referencecount": 0, 
    "m365_title": "Secured content-based customer loyalty", 
    "m365_id": "SXmz1hxiOk-E3MKJUyhj0mUABvix", 
    "m365_details": "{\"@odata.context\":\"https://graph.microsoft.com/beta/$metadata#planner/tasks('SXmz1hxiOk-E3MKJUyhj0mUABvix')/details/$entity\",\"@odata.etag\":\"W/\\\"JzEtVGFza0RldGFpbHMgQEBAQEBAQEBAQEBAQEBARCc=\\\"\",\"description\":null,\"previewType\":\"automatic\",\"id\":\"SXmz1hxiOk-E3MKJUyhj0mUABvix\",\"references\":{},\"checklist\":{}}", 
    "m365_graphplannertaskid": "1b326015-bb43-945c-85bc-9b2a4ed16c73", 
    "m365_completedby": null, 
    "m365_hasdescription": null, 
    "m365_collaborationrootid": null, 
    "m365_completeddatetime": null, 
    "m365_conversationthreadid": null, 
    "m365_bucketid": null, 
    "m365_startdatetime": null 
}

```

---

Mantenha o controle da propriedade `@odata.etag` e da propriedade`m365_graphplannertaskid` , pois eles serão necessários para executar operações de atualização ou exclusão.

**Tarefa 7: Atualizar uma tarefa do Planner**

Atualize uma Tarefa do Planner para `PlannerTask ID` executar uma operação de atualização em uma das tarefas do planejador criadas na etapa anterior. Para atualizar uma tarefa do planejador, execute a seguinte solicitação:

# <a name="request"></a>[Solicitação](#tab/request5)

```http
    HTTP/1.1 PATCH https://[Organization URI]/api/data/v9.0/m365_graphplannertasks({{plannerTaskId}})
```

* Cabeçalho: If-Match: {{@odata.etag}}

```json

{
    "m365_title": "{{$planTitle}}" 
}   

```

* `@odata.etag`: Etag para a tarefa, você deve executar uma leitura para recuperar a versão mais atualizada.

* `planTitle`: título atualizado para a tarefa

# <a name="response"></a>[Response](#tab/response5)

```http
    HTTP/1.1 204 No Content 
```

---

**Tarefa 8: Excluir uma tarefa do Planner**

Exclua uma tarefa do Planner com `PlannerTask ID` a qual executar uma operação Excluir em uma das tarefas do planejador criadas na etapa anterior. Para excluir uma tarefa do planejador, execute a seguinte solicitação:

# <a name="request"></a>[Solicitação](#tab/request6)

```http
    HTTP/1.1 DELETE https://[Organization URI]/api/data/v9.0/m365_graphplannertasks({{plannerTaskId}})
```

* `@odata.etag`: Etag para a tarefa, você deve executar uma leitura para recuperar a versão mais atualizada.

# <a name="response"></a>[Response](#tab/response6)

```http
    HTTP/1.1 204 No Content
```

---

**Tarefa 9: Atualizar detalhes de uma tarefa do Planner**

Atualize uma Tarefa do Planner para `PlannerTask ID` executar uma operação de atualização em uma das tarefas do planejador criadas na etapa anterior.

# <a name="request"></a>[Solicitação](#tab/request7)

```http
    HTTP/1.1 PATCH https://[Organization URI]/api/data/v9.0/m365_graphplannertasks({{plannerTaskId}})
```

Cabeçalho: If-Match: {{@odata.etag}}

```json

{ 

    "m365_title": "{{$planTitle}}", 
    "m365_details": "{\"@odata.etag\":\"{{details.etag}}\",\"description\":\"Updated Task Description\"}" 

}   
```

* `@odata.etag`: Etag para a tarefa, você deve executar uma leitura para recuperar a versão mais atualizada.
* `planTitle`: título atualizado para a tarefa.
* `@details.etag`: Etag para os detalhes da tarefa, você deve executar uma leitura usando o parâmetro de consulta $select consulta para incluir a `m365_details` coluna para recuperar a versão mais atualizada. Esse valor será incluído na coluna `m365_details` da resposta. Esse valor não é o mesmo que `@odata.etag` o porque, no back-end do Planner, a Tarefa e seus detalhes são armazenados separadamente.

# <a name="response"></a>[Response](#tab/response7)

```http
HTTP/1.1 204 No Content 
```

---

> [!NOTE]
> Você pode definir `If-Match` o cabeçalho como '*' e, em seguida, não precisará fornecer nenhum valor de etag, mas suas alterações sempre substituirão a tarefa e serão detalhes.

## <a name="virtual-tables-authorization"></a>Autorização de tabelas virtuais

A seguir estão as etapas de autorização necessárias para fazer solicitações HTTP usando as tabelas virtuais na solução de controles de colaboração.

### <a name="azure-app-registration"></a>Registro de aplicativo do Azure

Para adquirir o token de portador correto, é necessário um registro de aplicativo no Azure. Para obter mais informações sobre registros de aplicativo, [consulte registrar um aplicativo](/azure/active-directory/develop/quickstart-register-app).

1. Crie um registro de aplicativo no portal do Azure autenticar.
1. Navegue **até Certificados & segredos**.
1. Crie um novo segredo do cliente.

     > [!IMPORTANT]
     > Copie o valor do segredo e armazene-o para uso posterior. Você não poderá acessar novamente depois de sair da página atual.

1. Navegue até **permissões de API**.
1. Adicione a **user_impersonation** delegada do Dynamics CRM.
1. Conceda consentimento do administrador para essa permissão.

     :::image type="content" source="../assets/images/collaboration-control/power-automate-api-permission.png" alt-text="A captura de tela é um exemplo que mostra a permissão da API do Power Automate":::

1. Navegue até **Manifesto**.
1. Defina o valor dos seguintes atributos como true:

   * oauth2AllowIdTokenImplicitFlow
   * oauth2AllowImplicitFlow

1. Selecione Salvar.

     :::image type="content" source="../assets/images/collaboration-control/power-automate-manifest.png" alt-text="A captura de tela é um exemplo que mostra o manifesto do Power Automate":::

### <a name="powerapps-environment-permissions"></a>Permissões de ambiente do PowerApps

Depois que o registro do aplicativo for configurado, você deverá configurar um usuário do aplicativo no ambiente do PowerApps. Isso permitirá que você se autentique com os escopos corretos do Dynamics configurados anteriormente.

1. Abra o [Power Platform Administração Center](https://admin.powerplatform.microsoft.com/).
1. Navegue **até Ambientes Your_Environment** >  > **Usuários da** > **Lista de Usuários do Aplicativo**.
1. Selecione **Novo Usuário do Aplicativo** e selecione seu registro de aplicativo do Azure.
1. Selecione **Editar Funções de Segurança** e atribua a **função de Administrador do** Sistema ao usuário do aplicativo.

   1. A **função administrador do** sistema é aplicada para permitir a autenticação para todos os usuários que têm uma função de segurança inferior. Por exemplo, **a Colaboração controla o Usuário**.
   1. Isso pode ser restrito aplicando uma função inferior ao aplicativo. Por exemplo, **a Colaboração controla o Administrador**.

     :::image type="content" source="../assets/images/collaboration-control/power-automate-admin-center.png" alt-text="A captura de tela é um exemplo que mostra o Centro de administração do Power Automate":::

### <a name="getting-the-bearer-token"></a>Obtendo o token de portador

Após a conclusão do registro de aplicativo do Azure e das permissões de ambiente do PowerApps, envie a solicitação HTTP a seguir para obter o token de portador.

```http
POST https://login.microsoftonline.com/<AZURE_APP_TENANT_ID>/oauth2/token
```

* **Content-Type**: application/x-www-form-urlencoded
* **client_id**: <AZURE_APP_CLIENT_ID>
* **&client_secret**: <AZURE_APP_CLIENT_ID>
* **&: https://**\<RESOURCEURL\>/
* **&nome de usuário**: \<USERNAME\>
* **&senha**: \<PASSWORD\>
* **&grant_type**: Senha

> [!IMPORTANT]
> Inclua a barra à direita no parâmetro de recurso. Caso contrário, você receberá um erro relacionado aos escopos do Graph ao chamar a tabela virtual.

No conteúdo da resposta, copie o valor da propriedade **access_token** dados. Em seguida, você pode passar esse token de portador como parte do cabeçalho de autorização ao fazer solicitações para as tabelas virtuais.

:::image type="content" source="../assets/images/collaboration-control/power-automate-authorization.png" alt-text="A captura de tela é um exemplo que mostra a autorização do Power Automate":::

## <a name="virtual-tables-error-handling"></a>Tratamento de erros de tabelas virtuais

O tratamento de erros de tabelas virtuais descreve cenários de erro comuns e como as tabelas virtuais responderão.

### <a name="attempt-to-create-a-virtual-record-without-a-collaboration-session"></a>Tentativa de criar um registro virtual sem uma sessão de Colaboração

Uma sessão de colaboração válida é necessária para cada solicitação para criar um registro virtual.  Quando um registro virtual é criado, a tabela virtual criará um registro de mapa de colaboração, que inclui a chave primária do registro virtual, o nome da entidade e a ID externa, ou seja, a ID de recurso do Graph. Esse mapa de colaboração está associado a uma sessão de colaboração e é assim que os controles de Colaboração manterão o controle das colaborações associadas a um registro comercial.

# <a name="request"></a>[Solicitação](#tab/request8)

```http
    HTTP/1.1 POST https://[Organization URI]/api/data/v9.0/m365_graphplannertasks  
```

```json

{ 
    "m365_planid": "{{planId}}", 
    "m365_title": "{{taskTitle}}", 
    "m365_duedatetime": "2022-05-04T08:00:00Z", 
    "m365_assignments": "{\"me\":{\"orderHint\":\" !\",\"@odata.type\":\"#microsoft.graph.plannerAssignment\"}}" 
}

```

A `collaborationRootId` propriedade está ausente da solicitação.

# <a name="response"></a>[Response](#tab/response8)

```http
    HTTP/1.1 400 Bad Request 
```

```json

{ 
    "error": { 
        "code": "0x80048d0b", 
        "message": "Parameter 'm365_collaborationrootid' is null, empty, or white-space." 
    } 
} 

```

---

Para resolver esse problema, você sempre deve fornecer uma propriedade `collaborationRootId` válida ao criar um registro virtual.

### <a name="attempt-to-read-a-virtual-record-without-a-collaboration-map"></a>Tentativa de ler um registro virtual sem um mapa de colaboração

As tabelas virtuais permitem que você execute solicitações, que retornam coleções de registros virtuais. Vimos isso anteriormente neste documento em que solicitamos todas as tarefas do planejador associadas a uma sessão de colaboração específica. Também é possível solicitar todas as tarefas do planejador associadas a um plano planejador específico usando uma consulta do sistema $filter como esta: $filter=m365_planid eq`{{planId}}`. Um problema que ocorrerá se você usar essa consulta é que os registros serão retornados para tarefas do planejador, que não estão associados a uma sessão de colaboração, ou seja, tarefas do planejador que foram criadas por um meio diferente de usar um controle de colaboração. Se você tentar ler, atualizar ou excluir esse registro, a solicitação falhará porque a tabela virtual não pode encontrar o mapa de colaboração associado.  

# <a name="request"></a>[Solicitação](#tab/request9)

```http
    HTTP/1.1 GET https://[Organization URI]/api/data/v9.0/m365_graphplannertasks({{plannerTaskId}})
```

A `plannerTaskId` propriedade está associada a uma tarefa do planejador, que foi criada usando a interface da Web do Planner e, portanto, não tem um registro de mapa de colaboração.

# <a name="response"></a>[Response](#tab/response9)

```http
    HTTP/1.1 404 Not Found 
```

```json
{ 
    "error": { 
        "code": "0x80048d02", 
        "message": "A record with the specified key values does not exist in m365_collaborationmap entity" 
    }
} 
```

---

Para resolver esse problema, você deve verificar a mensagem de erro na resposta e, se ela estiver definida como a mensagem mostrada acima, isso significa que o registro virtual não está associado. Para criar uma associação para esse registro, você deve chamar [Associar Mapa de Colaboração – API REST](/rest/api/industry/collaboration-controls/collaboration-custom-ap-is/associate-collaboration-map).

### <a name="attempt-to-read-a-virtual-record-and-the-graph-resource-has-been-deleted"></a>Tentativa de ler um registro virtual e o recurso do Graph foi excluído

Relacionado ao erro anterior, você precisa lidar com o caso em que um recurso do Graph foi excluído, mas o cliente ainda tem uma referência ao registro virtual excluído. Isso pode acontecer se outro usuário excluiu o registro. Se você tentar ler, atualizar ou excluir esse registro, a solicitação falhará porque a tabela virtual não poderá recuperar o recurso do Graph.

# <a name="request"></a>[Solicitação](#tab/request10)

```http
    HTTP/1.1 GET https://[Organization URI]/api/data/v9.0/m365_graphplannertasks({{plannerTaskId}})
```

A `plannerTaskId` propriedade está associada a uma tarefa do planejador, que foi excluída.

# <a name="response"></a>[Response](#tab/response10)

```http
    HTTP/1.1 404 Not Found 
```

```json
{ 
    "error": { 
        "code": "0x80048d02", 
        "message": "REST call failed because: Reason - NotFound, Full error - {\"error\":{\"code\":\"\",\"message\":\"The requested item is not found.\",\"innerError\":{\"date\":\"2022-05-17T16:30:51\",\"request-id\":\"b692a31a-312d-490c-8dce-d258459a0211\",\"client-request-id\":\"b692a31a-312d-490c-8dce-d258459a0211\"}}}." 
    } 
} 
```

---

Esse caso deve ser tratado por qualquer código de cliente, que recupera registros virtuais, pois outro usuário pode excluir o recurso do Graph associado a qualquer momento.

### <a name="attempt-to-update-a-virtual-record-with-an-invalid-odataetag"></a>Tentativa de atualizar um registro virtual com um @odata.etag inválido

A `@odata.etag` propriedade é usada para simultaneidade de dados e para impedir a gravação em cima do mesmo registro se tiver sido atualizada por outro usuário. Quando um registro é lido, a etag atual é retornada e permanece válida até que o registro seja alterado. A etag deve ser incluída em qualquer solicitação de atualização e será verificada antes que a operação seja concluída. Se o registro tiver sido alterado por outro usuário desde que o usuário atual leu o registro, a solicitação de atualização dos usuários atuais falhará.

Se você executar duas solicitações de atualizações usando o mesmo @odata.etag, a segunda solicitação falhará:

# <a name="request"></a>[Solicitação](#tab/request11)

```http
    HTTP/1.1 PATCH https://[Organization URI]/api/data/v9.0/m365_graphplannertasks({{plannerTaskId}})
```

Cabeçalho: If-Match: {{@odata.etag}}

```json
{
    "m365_title": "{{$planTitle}}" 
}

```

# <a name="response"></a>[Response](#tab/response11)

```http
    HTTP/1.1 409 Conflict 
```

```json
{ 
    "error": { 
        "code": "0x80048d08", 
        "message": "REST call failed because: Reason - Conflict, Full error - {\"error\":{\"code\":\"\",\"message\":\"The attempted changes conflicted with already accepted changes. Read the latest state and resolve differences.\",\"innerError\":{\"date\":\"2022-05-18T06:54:55\",\"request-id\":\"dc6cd2b7-1509-4e81-91ff-22cf35b86e18\",\"client-request-id\":\"dc6cd2b7-1509-4e81-91ff-22cf35b86e18\"}}}." 
    }
} 
```

---

### <a name="querying-for-associated-virtual-records"></a>Consultando registros virtuais associados

Na Tarefa 5 acima, descrevi como recuperar tarefas associadas do Planner. Essa operação tem suporte para todas as tabelas virtuais. Ao executar essa solicitação, você deve incluir uma consulta, que especifica a `$filter` ID raiz de colaboração, conforme mostrado abaixo:

# <a name="request"></a>[Solicitação](#tab/request12)

```http
    HTTP/1.1 GET https://[Organization URI]/api/data/v9.0/ m365_graphplannertasks?$filter=m365_collaborationrootid eq '{{collaborationRootId}}'&$select=m365_graphplannertaskid,m365_title,m365_createddatetime  
```

---

* Outras opções de filtragem não podem ser combinadas com essa `$filter` consulta e, se lá, elas serão ignoradas.
* Outra filtragem deve ser executada diretamente na resposta da solicitação.

### <a name="querying-for-virtual-records-with-required-key-attributes"></a>Consultando registros virtuais com atributos de chave necessários

Quando a API Web do Dataverse é chamada para recuperar vários registros das tabelas virtuais a seguir, um atributo de chave obrigatório é necessário. Os Compromissos de Reserva do Graph exigem que `m365_bookingbusinessid` um válido seja incluído na consulta. Se o atributo de chave não for fornecido, a solicitação falhará da seguinte maneira:

# <a name="response"></a>[Response](#tab/response13)

```http
    HTTP/1.1 400 Bad Request 
```

```json

{ 
  "error": { 
    "code": "0x80048d0b", 
    "message": "Key attribute is missing: 'm365_bookingbusinessid'.", 
    ….
  } 
} 

```

---

Para corrigir esse problema, altere a solicitação para este formato:

# <a name="request"></a>[Solicitação](#tab/request14)

```http
    HTTP/1.1 GET https://[Organization URI]/api/data/v9.0/ m365_graphbookingappointments?$filter=m365_bookingbusinessid eq '{{bookingBusinessId}}'
```

---

### <a name="creating-virtual-records-and-graph-access-control"></a>Criando registros virtuais e controle de acesso do Graph

As tabelas virtuais respeitam o controle de acesso especificado para o Microsoft Graph. As tabelas virtuais não permitirão operações que o usuário não pôde executar usando o Microsoft API do Graph. Por exemplo, se o usuário usado para criar o Plano for a Tarefa 3 e não for um membro do grupo usado, você receberá 403 Respostas proibidas.
