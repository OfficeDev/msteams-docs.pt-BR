---
title: Como usar o serviço personalizado do Azure Fluid Relay
author: surbhigupta
description: Neste módulo, saiba como usar um serviço personalizado do Azure Fluid Relay com o Live Share.
ms.topic: overview
ms.localizationpriority: high
ms.author: v-ypalikila
ms.date: 07/21/2022
ms.openlocfilehash: 1bbedae4d8611987bfd90277c487f8aabede868b
ms.sourcegitcommit: 1248901a5e59db67bae091f60710aabe7562016a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/13/2022
ms.locfileid: "68560579"
---
---

# <a name="custom-azure-fluid-relay-service"></a>Serviço personalizado do Azure Fluid Relay

Embora você provavelmente prefira usar nosso serviço hospedado gratuito, há situações em que é útil usar seu próprio serviço do Azure Fluid Relay para seu aplicativo Live Share.

## <a name="pre-requisites"></a>Pré-requisitos

1. Crie um painel lateral de reunião e uma extensão de reunião do aplicativo de estágio, conforme mostrado no [tutorial de rolo de dados](../teams-live-share-tutorial.md).
2. Atualize o manifesto do aplicativo para incluir todas [as permissões necessárias](../teams-live-share-capabilities.md#register-rsc-permissions).
3. Provisione um serviço do Azure Fluid Relay, conforme descrito neste [tutorial](/azure/azure-fluid-relay/how-tos/provision-fluid-azure-portal).

## <a name="connect-to-azure-fluid-relay-service"></a>Conectar-se ao serviço do Azure Fluid Relay

Ao chamar a inicialização `LiveShareClient`, você pode definir seu próprio `AzureConnectionConfig`. O Live Share associa os contêineres criados com reuniões, `ITokenProvider` mas você precisará implementar a interface para assinar tokens para seus contêineres. Este exemplo explica o Azure `AzureFunctionTokenProvider`, que usa uma função de nuvem do Azure para solicitar um token de acesso de um servidor.

# <a name="javascript"></a>[JavaScript](#tab/javascript)

```javascript
import { LiveShareClient, LivePresence } from "@microsoft/live-share";
import { SharedMap } from "fluid-framework";
import { AzureFunctionTokenProvider } from "@fluidframework/azure-client";

// Define a custom connection for your app
const options = {
  connection: {
    tenantId: "MY_TENANT_ID",
    tokenProvider: new AzureFunctionTokenProvider(
      "MY_SERVICE_ENDPOINT_URL" + "/api/GetAzureToken",
      { userId: "userId", userName: "Test User" }
    ),
    endpoint: "MY_SERVICE_ENDPOINT_URL",
    type: "remote",
  },
};
// Join the Fluid container
const liveShare = new LiveShareClient(options);
const schema = {
  initialObjects: {
    presence: LivePresence,
    ticTacToePositions: SharedMap,
  },
};
const { container } = await liveShare.joinContainer(schema);

// ... ready to start app sync logic
```

# <a name="typescript"></a>[TypeScript](#tab/typescript)

```TypeScript
import {
  LiveShareClient,
  ILiveShareClientOptions,
  LivePresence,
} from "@microsoft/live-share";
import { SharedMap } from "fluid-framework";
import { AzureFunctionTokenProvider } from "@fluidframework/azure-client";

// Define a custom connection for your app
const options: ILiveShareClientOptions = {
  connection: {
    tenantId: "MY_TENANT_ID",
    tokenProvider: new AzureFunctionTokenProvider(
      "MY_FUNCTION_ENDPOINT_URL" + "/api/GetAzureToken",
      { userId: "userId", userName: "Test User" }
    ),
    endpoint: "MY_SERVICE_ENDPOINT_URL",
    type: "remote",
  },
};
// Join the Fluid container
const liveShare = new LiveShareClient(options);
const schema = {
  initialObjects: {
    presence: LivePresence,
    ticTacToePositions: SharedMap,
  },
};
const { container } = await liveShare.joinContainer(schema);

// ... ready to start app sync logic
```

---

## <a name="why-use-a-custom-azure-fluid-relay-service"></a>Por que usar um serviço personalizado do Azure Fluid Relay?

Considere usar uma conexão de serviço AFR personalizada se você:

* Exigir o armazenamento de dados em contêineres Fluid além do tempo de vida de uma reunião.
* Transmita dados confidenciais por meio do serviço que requer uma política de segurança personalizada.
* Desenvolva recursos por meio do Fluid Framework para seu aplicativo fora do Teams.

## <a name="why-use-live-share-with-your-custom-service"></a>Por que usar o Live Share com seu serviço personalizado?

O Azure Fluid Relay foi projetado para funcionar com qualquer aplicativo baseado na Web, o que significa que ele funciona com ou sem o Microsoft Teams. Isso gera uma pergunta importante: se eu criar meu próprio serviço do Azure Fluid Relay, ainda preciso do Live Share?

O Live Share tem recursos que são benéficos para cenários comuns de reunião que aumentam outros recursos em seu aplicativo, incluindo:

* [Mapeamento de contêiner](#container-mapping)
* [Verificação de função e objetos dinâmicos](#live-objects-and-role-verification)
* [Sincronização de mídia](#media-synchronization)

### <a name="container-mapping"></a>Mapeamento de contêiner

O `LiveShareClient` in `@microsoft/live-share` é responsável por mapear um identificador de reunião exclusivo para seus contêineres fluid, o que garante que todos os participantes da reunião ingressem no mesmo contêiner. Como parte desse processo, o cliente tenta se conectar a uma `containerId` reunião mapeada que já existe. Se não existir, ele será usado `AzureClient` `AzureConnectionConfig` para criar um contêiner usando o seu e, em seguida, retransmitir para `containerId` outros participantes da reunião.

Se seu aplicativo já tiver um mecanismo para criar contêineres Fluid e compartilhamento deles com outros membros, `containerId` como inserir a URL compartilhada para o estágio de reunião, isso pode não ser necessário para seu aplicativo.

### <a name="live-objects-and-role-verification"></a>Verificação de função e objetos dinâmicos

As estruturas de dados ao vivo do Live Share `LivePresence`, como , `LiveState`e `LiveEvent` são adaptadas à colaboração em reuniões e, portanto, não têm suporte em contêineres Fluid usados fora do Microsoft Teams. Recursos como a verificação de função ajudam seu aplicativo a se alinhar com as expectativas de nossos usuários.

> [!NOTE]
> Como um benefício adicional, os objetos dinâmicos também apresentam latências de mensagem mais rápidas em comparação com estruturas de dados fluid tradicionais.

Para obter mais informações, consulte a [página principais recursos](../teams-live-share-capabilities.md) .

### <a name="media-synchronization"></a>Sincronização de mídia

Não há `@microsoft/live-share-media` suporte para pacotes do Fluid em contêineres usados fora do Microsoft Teams.

Para obter mais informações, consulte a [página de recursos de](../teams-live-share-media-capabilities.md) mídia.

## <a name="see-also"></a>Confira também

* [Repositório do GitHub](https://github.com/microsoft/live-share-sdk)
* [Documentos de referência do SDK do Live Share](/javascript/api/@microsoft/live-share/)
* [Documentos de referência do SDK do Live Share Media](/javascript/api/@microsoft/live-share-media/)
* [Recursos do Live Share ](../teams-live-share-capabilities.md)
* [Funcionalidades de mídia do Live Share](../teams-live-share-media-capabilities.md)
* [Perguntas frequentes do Live Share](../teams-live-share-faq.md)
* [Aplicativos do Teams em reuniões](../teams-apps-in-meetings.md)
