---
title: Referências de API REST de controle de colaboração e configurações
author: surbhigupta
description: Neste módulo, saiba mais sobre o controle de colaboração e as configurações de referência da API REST para gerenciar configurações, iniciar, mapear e recuperar atividades de colaboração.
ms.localizationpriority: medium
ms.author: v-npaladugu
ms.topic: conceptual
ms.openlocfilehash: bc0a5e6834077e199c1dff26568ef2acfeb72745
ms.sourcegitcommit: 0bb822b30739e4a532a36764dad2dbf35a81ba29
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/03/2022
ms.locfileid: "67178715"
---
# <a name="collaboration-control-and-settings-rest-api-reference"></a>Referência da API REST de controle de colaboração e configurações

Os desenvolvedores podem usar o controle de Colaboração e a API REST de Configurações para gerenciar configurações, iniciar, mapear e recuperar atividades de colaboração com suas próprias entidades de modelo de negócios.

> [!NOTE]
> Atualmente, os controles de colaboração estão disponíveis apenas na [versão prévia do desenvolvedor público](~/resources/dev-preview/developer-preview-intro.md).

Este artigo fornece referência para a API REST da solução de controle de colaboração.

## <a name="rest-operations-collaboration---custom-api"></a>Operações REST: Colaboração – API personalizada

|Operação|Descrição|
|---------|-----------|
|[Associar Mapa de Colaboração](/rest/api/industry/collaboration-toolkit/collaboration-custom-ap-is/associate-collaboration-map)|Associa uma entidade colaborativa a uma sessão de colaboração.|
|[Iniciar sessão de colaboração](/rest/api/industry/collaboration-toolkit/collaboration-custom-ap-is/begin-collaboration-session)|Cria um registro de sessão de colaboração vinculado a uma entidade de negócios, contexto de aplicativo e metadados opcionais.|
|[Desassociar o mapa de colaboração](/rest/api/industry/collaboration-toolkit/collaboration-custom-ap-is/disassociate-collaboration-map-custom-api)|Desassocia uma entidade mapeada da sessão de colaboração fornecida.|
|[Recuperar mapas de colaboração](/rest/api/industry/collaboration-toolkit/collaboration-custom-ap-is/retrieve-collaboration-maps-custom-api)|Obtém uma lista de mapas de colaboração para uma sessão de um tipo de entidade específico.|
|[Recuperar sessão de colaboração](/rest/api/industry/collaboration-toolkit/collaboration-custom-ap-is/retrieve-collaboration-session-custom-api)|Obtém um registro de sessão de colaboração com base nos parâmetros fornecidos.|
|[Atualizar Mapa de Colaboração](/rest/api/industry/collaboration-toolkit/collaboration-custom-ap-is/update-collaboration-map-custom-api)|Atualizações um registro de mapa de colaboração e seus metadados, se fornecidos.|
|[Atualizar Sessão de Colaboração](/rest/api/industry/collaboration-toolkit/collaboration-custom-ap-is/update-collaboration-session)|Atualizações um registro de sessão de colaboração e, opcionalmente, seus metadados.|

## <a name="rest-operations-collaboration---standard-odata-apis"></a>Operações REST: Colaboração – APIs OData Padrão

|Operação|Descrição|
|---------|-----------|
|[Obter Mapa de Colaboração por ID](/rest/api/industry/collaboration-toolkit/collaboration-standard-o-data-ap-is/get-collaboration-map-by-id)|Obtém os detalhes de um registro de mapa de colaboração.|
|[Obter metadados de colaboração](/rest/api/industry/collaboration-toolkit/collaboration-standard-o-data-ap-is/get-collaboration-metadata)|Obtém uma lista dos registros de metadados de colaboração para um determinado mapa de colaboração ou um nome de entidade raiz de colaboração.|
|[Obter Raiz de Colaboração](/rest/api/industry/collaboration-toolkit/collaboration-standard-o-data-ap-is/get-collaboration-root)|Lista todas as sessões de colaboração criadas.|

## <a name="rest-operations-settings---custom-apis"></a>Operações REST: Configurações – APIs personalizadas

|Operação|Descrição|
|---------|-----------|
|[Criar e atualizar configurações](/rest/api/industry/collaboration-toolkit/settings-custom-ap-is/create-update-setting-custom-api)|Cria ou atualiza uma configuração que corresponde ao caminho do grupo e ao nome da definição de configurações.|
|[Recuperar configurações nulas](/rest/api/industry/collaboration-toolkit/settings-custom-ap-is/retrieve-null-settings-custom-api)|Retorna uma lista de definições de configurações que não têm um valor.|
|[Recuperar configurações](/rest/api/industry/collaboration-toolkit/settings-custom-ap-is/retrieve-settings-custom-api)|Retorna uma lista de configurações ou configurações específicas em grupos.|

## <a name="rest-operations-settings---standard-odata-apis"></a>Operações REST: Configurações – APIs OData Padrão

|Operação|Descrição|
|---------|-----------|
|[Excluir definição de configurações](/rest/api/industry/collaboration-toolkit/settings-standard-o-data-ap-is/delete-settings-definition)|Exclui uma definição de configurações.|
|[Excluir Grupo de Configurações](/rest/api/industry/collaboration-toolkit/settings-standard-o-data-ap-is/delete-settings-group)|Exclui um grupo de configurações.|
|[Excluir Tipo de Configurações](/rest/api/industry/collaboration-toolkit/settings-standard-o-data-ap-is/delete-settings-type)|Exclua um tipo de configuração.|
|[Excluir Valor de Configurações](/rest/api/industry/collaboration-toolkit/settings-standard-o-data-ap-is/delete-settings-value)|Exclui um valor de configurações.|
|[Obter definições de configurações](/rest/api/industry/collaboration-toolkit/settings-standard-o-data-ap-is/get-settings-definitions)|Lista definições de configurações.|
|[Obter grupos de configurações](/rest/api/industry/collaboration-toolkit/settings-standard-o-data-ap-is/get-settings-groups)|Lista grupos de configurações.|
|[Obter tipos de configurações](/rest/api/industry/collaboration-toolkit/settings-standard-o-data-ap-is/get-settings-types)|Lista os tipos de configurações.|
|[Obter valor de configurações](/rest/api/industry/collaboration-toolkit/settings-standard-o-data-ap-is/get-settings-value)|Lista valores de configurações.|
|[Definição de configurações de patch](/rest/api/industry/collaboration-toolkit/settings-standard-o-data-ap-is/patch-settings-definition)|Atualizações definição de configurações.|
|[Grupo de Configurações de Patch](/rest/api/industry/collaboration-toolkit/settings-standard-o-data-ap-is/patch-settings-group)|Atualizações um grupo de configurações.|
|[Tipo de Configurações de Patch](/rest/api/industry/collaboration-toolkit/settings-standard-o-data-ap-is/patch-settings-type)|Atualizações um tipo de configuração.|
|[Valor das Configurações de Patch](/rest/api/industry/collaboration-toolkit/settings-standard-o-data-ap-is/patch-settings-value)|Atualizações um valor de configuração.|
|[Definição pós-configurações](/rest/api/industry/collaboration-toolkit/settings-standard-o-data-ap-is/post-settings-definition)|Cria uma nova definição de configurações.|
|[Post Settings Group](/rest/api/industry/collaboration-toolkit/settings-standard-o-data-ap-is/post-settings-group)|Cria um novo grupo de configurações.|
|[Tipo de pós-configurações](/rest/api/industry/collaboration-toolkit/settings-standard-o-data-ap-is/post-settings-type)|Cria um novo tipo de configuração.|
|[Valor pós-configurações](/rest/api/industry/collaboration-toolkit/settings-standard-o-data-ap-is/post-settings-value)|Cria um novo valor de configuração.|
