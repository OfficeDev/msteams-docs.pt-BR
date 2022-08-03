---
title: Configurar tarefas para clientes externos no aplicativo de controle de colaboração
author: surbhigupta
description: Neste módulo, saiba como configurar tarefas para clientes externos no aplicativo de controle colaboração no Microsoft Teams.
ms.localizationpriority: medium
ms.author: v-npaladugu
ms.topic: conceptual
ms.openlocfilehash: bb98ab632b335717a61499600aef01e652fd0dee
ms.sourcegitcommit: 0bb822b30739e4a532a36764dad2dbf35a81ba29
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/03/2022
ms.locfileid: "67178747"
---
# <a name="configure-tasks-for-external-clients"></a>Configurar tarefas para clientes externos

Tarefas externas que podem ser atribuídas a usuários que não fazem parte da sua organização ou que não têm acesso ao seu aplicativo, como atribuir uma tarefa a um cliente.

Para habilitar, você precisará de uma etapa extra para passar uma cadeia de caracteres XML para cada instância do controle PCF de Tarefas anexado ao componente de sub-grade no formulário MDA desejado. A cadeia de caracteres XML é uma consulta parametrizada que permite ao controle extrair os dados necessários de uma tabela que contém informações do cliente.

> [!NOTE]
> Atualmente, os controles de colaboração estão disponíveis apenas na [versão prévia do desenvolvedor público](~/resources/dev-preview/developer-preview-intro.md).

A seguir estão as etapas para criar tarefas externas:

1. Crie uma nova entidade personalizada, como Cliente, ou reutilize uma entidade de cliente existente, como Contatos.

1. Crie novos campos que conterão as seguintes informações:
    1. Nome
    1. Email
    1. Pai (Pesquisa na tabela pai, como Inspeções)
    > [!NOTE]
    > A entidade do cliente criada acima será, onde o controle de tarefas extrai as informações do cliente ao atribuir uma tarefa externa. O campo Pai garante que a entidade do cliente esteja vinculada a um registro de inspeção.

1. Gere um arquivo XML fetch para permitir que o controle PCF efetue pull das informações corretas do cliente.

    **Configurar esquema XML**

    A seguir está a definição de esquema para a configuração de tarefas Buscar XML. Qualquer XML fetch precisa ser projetado para atender aos seguintes requisitos:

    * O resultado da consulta deve retornar as seguintes propriedades para cada objeto de usuário:
      * ID
      * displayname
      * email, use o alias, se necessário.
    * A consulta deve conter o **@top** para permitir que o chamador limite o número de resultados.
    * A consulta deve ter **@rootEntityId** parâmetro para filtrar os resultados apenas por registros relacionados, se necessário.
    * A consulta deve ter **um @useName** para permitir a filtragem de resultados por nome
    * A consulta deve ter **um @useIdentifier** para permitir a busca somente de usuários selecionados.

    **Esquema XML de configuração e exemplo**

    A configuração do esquema XML efetua pull de dados da tabela do cliente. Você pode ajustar o nó `<fetch/>` para especificar sua própria consulta para exibir usuários de qualquer outra tabela personalizada.

    > [!NOTE]
    > A entidade e o atributo de atributo acima e o atributo order no XML estão **PublisherPrefix_TableColumn** formato.

    ```xml
    
    <custom-tasks> 
    <custom-task id="external" name="External" for="guest"> 
    <fetch top="@top"> 
    <entity name="[Name of table, e.g. Crb2891_customer]"> 
    <attribute name="[Name of ID column, e.g. Crb2891_customerid]" alias="id" /> 
    <attribute name="[Name of primary name column, e.g. Crb2891_name]" alias="displayname" /> 
    <attribute name="[Name of email column, e.g. Crb2891_email]" alias="email" /> 
    <order attribute ="[Name of primary name column, e.g. Crb2891_name]" descending="false" /> 
    <filter type="and"> 
    <condition attribute="[Name of parent lookup column, e.g. Crb2891_parent]" operator="eq" value="@rootEntityId" /> 
    <condition attribute="[Name of primary name column, e.g. Crb2891_name]" operator="like" value="@userName" /> 
    <condition attribute="[Name of email column, e.g. Crb2891_email]" operator="like" value="@userIdentifier" /> 
    </filter> 
    </link-entity> 
    </entity> 
    </fetch> 
    </custom-task> 
    </custom-tasks> 
    
    ```

1. Associe os controles Task à subgrid dentro do designer de formulário clássico. Selecione **Salvar** e, em seguida, **alterne para clássico**.

1. Mova-se no designer de formulário clássico até encontrar a **guia** Tarefas. Clique duas vezes na subgrid para abrir a caixa de diálogo de propriedade.

    :::image type="content" source="~/assets/images/collaboration-control/subgrid-property.png" alt-text="Caixa de diálogo da propriedade Tasks":::

1. Na caixa de diálogo de propriedade, defina as propriedades conforme mostrado na imagem a seguir:

    :::image type="content" source="~/assets/images/collaboration-control/tasks-property.png" alt-text="Configurações da propriedade Tasks":::

1. Vá para a guia Controles e selecione :::image type="icon" source="~/assets/images/collaboration-control/edit-icon.png" alt-text="editar tarefas"::: na propriedade Tarefas Personalizadas para adicionar o XML de Busca gerado acima.

1. Colar o XML fetch

    :::image type="content" source="~/assets/images/collaboration-control/set-fetchproperties.png" alt-text="Buscar configurações de propriedade XML":::

    :::image type="content" source="~/assets/images/collaboration-control/custom-tasksproperty.png" alt-text="Buscar configurações de propriedade personalizada XML":::

1. Selecione **OK em** Configurar Propriedade "Tarefas Personalizadas" e Defina Janelas de Propriedades.

1. Salvar e publicar.
