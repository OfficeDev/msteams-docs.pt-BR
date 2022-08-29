---
title: Perguntas frequentes do Live Share
author: surbhigupta
description: Neste módulo, saiba mais sobre as Perguntas frequentes do Live Share.
ms.topic: overview
ms.localizationpriority: high
ms.author: v-ypalikila
ms.date: 04/07/2022
ms.openlocfilehash: b53d7c01722faa51824e0df17586bc8a385438b0
ms.sourcegitcommit: 134ce9381891e51e6327f1f611fdfd60c90cca18
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/24/2022
ms.locfileid: "67425607"
---
---

# <a name="live-share-sdk-faq"></a>Perguntas frequentes sobre o SDK do Live Share

Obtenha respostas para dúvidas comuns ao usar o Live Share.<br>

<br>

<details>

<summary><b>Posso usar meu próprio serviço do Azure Fluid Relay?</b></summary>

Sim! Ao construir a classe `TeamsFluidClient`, você pode definir sua própria classe `AzureConnectionConfig`. O Live Share associa os contêineres criados com reuniões, `ITokenProvider` mas você precisará implementar a interface para assinar tokens para seus contêineres. Por exemplo, você pode usar um fornecido `AzureFunctionTokenProvider`, que usa uma função de nuvem do Azure para solicitar um token de acesso de um servidor.

Embora a maioria de vocês ache útil usar nosso serviço hospedado gratuito, ainda pode haver momentos em que é útil usar seu próprio serviço do Azure Fluid Relay para seu aplicativo Live Share. Considere usar uma conexão de serviço AFR personalizada se você:

* Exigir o armazenamento de dados em contêineres Fluid além do tempo de vida de uma reunião.
* Transmita dados confidenciais por meio do serviço que requer uma política de segurança personalizada.
* Desenvolva recursos por meio do Fluid Framework, por exemplo, `SharedMap`para seu aplicativo fora do Teams.

Para obter mais informações, [confira como orientar ou](./teams-live-share-how-to/how-to-custom-azure-fluid-relay.md) visitar a documentação do [Azure Fluid Relay](/azure/azure-fluid-relay/).

<br>

</details>

<details>

<summary><b>Por quanto tempo os dados são armazenados no serviço hospedado do Live Share podem ser acessados?</b></summary>

Todos os dados enviados ou armazenados por meio de contêineres do Fluid criados pelo serviço Azure Fluid Relay hospedado pelo Live Share ficam acessíveis por 24 horas. Se você quiser manter os dados por mais de 24 horas, pode substituir nosso serviço do Azure Fluid Relay hospedado pelo seu. Como alternativa, você pode usar seu próprio provedor de armazenamento em paralelo ao serviço hospedado do Live Share.

<br>

</details>

<details>

<summary><b>Quais tipos de reunião são compatíveis com o Live Share?</b></summary>

Durante a Versão Prévia, há suporte apenas para reuniões agendadas e todos os participantes devem estar no calendário da reunião. Não há suporte para reuniões do tipo Reunir Agora, chamadas individuais, chamadas em grupo.

<br>

</details>

<details>

<summary><b>O pacote de mídia do Live Share funcionará com conteúdo do DRM?</b></summary>

Não. Atualmente, o Teams não dá suporte à mídia criptografada para aplicativos de guia na área de trabalho. Há suporte para clientes Chrome, Edge e móveis. Para obter mais informações, você [pode acompanhar o problema aqui](https://github.com/microsoft/live-share-sdk/issues/14).

<br>

</details>

<details>
<summary><b>Quantas pessoas podem participar de uma sessão do Live Share?</b></summary>

Atualmente, o Live Share oferece suporte a um máximo de 100 participantes por sessão. Se isso é algo em que você está interessado, você pode [iniciar uma discussão aqui](https://github.com/microsoft/live-share-sdk/discussions).

<br>

</details>

<details>
<summary><b>Posso usar as estruturas de dados efêmeros do Live Share fora do Teams?</b></summary>

Atualmente, os pacotes live share exigem que o SDK do Cliente do Teams funcione corretamente. Recursos dentro `@microsoft/live-share` ou `@microsoft/live-share-media` não funcionarão fora do Microsoft Teams. Se isso é algo em que você está interessado, você pode [iniciar uma discussão aqui](https://github.com/microsoft/live-share-sdk/discussions).

<br>

</details>

<details>
<summary><b>Posso usar vários contêineres fluid?</b></summary>

Atualmente, o Live Share dá suporte apenas a ter um contêiner usando nosso serviço do Azure Fluid Relay fornecido. No entanto, é possível usar um contêiner do Live Share e um contêiner criado por sua própria instância do Azure Fluid Relay.

<br>

</details>

<details>
<summary><b>Posso alterar meu esquema de contêiner do Fluid depois de criar o contêiner?</b></summary>

Atualmente, o Live Share não dá suporte à adição de novo `initialObjects` ao Fluid `ContainerSchema` depois de criar ou ingressar em um contêiner. Como as sessões do Live Share têm curta duração, isso geralmente é um problema durante o desenvolvimento depois de adicionar novos recursos ao seu aplicativo.

> [!NOTE]
> Se você estiver usando a `dynamicObjectTypes` propriedade no `ContainerSchema`, poderá adicionar novos tipos a qualquer momento. Se você remover mais tarde os tipos do esquema, as instâncias DDS existentes desses tipos falharão normalmente.

Para corrigir erros resultantes `initialObjects` de alterações ao testar localmente no navegador, remova a ID do contêiner com hash da URL e recarregue a página. Se você estiver testando em uma reunião do Teams, inicie uma nova reunião e tente novamente.

Se você planeja atualizar seu aplicativo com instâncias `SharedObject` `EphemeralObject` novas ou com frequência, considere como implantar novas alterações de esquema na produção. Embora o risco real seja relativamente baixo e de curta duração, pode haver sessões ativas no momento em que você distribuir a alteração. Os usuários existentes na sessão não devem ser afetados, mas os usuários que ingressarem nessa sessão depois que você implantou uma alteração significativa podem ter problemas para se conectar à sessão. Para atenuar isso, você pode considerar algumas das seguintes soluções:

* Implante alterações de esquema para seu aplicativo Web fora do horário comercial normal.
* Use `dynamicObjectTypes` para quaisquer alterações feitas no esquema, em vez de alterar `initialObjects`.

> [!NOTE]
> No momento, o Live Share não dá suporte ao controle `ContainerSchema`de versão, nem tem APIs dedicadas a migrações.

<br>

</details>

<details>
<summary><b>Há limites para quantos eventos de alteração posso emitir por meio do Live Share?</b></summary>

Enquanto o Live Share estiver em versão prévia, qualquer limite de eventos emitidos por meio do Live Share não será imposto. Para obter um desempenho ideal, você deve desmentir as alterações emitidas `SharedObject` `EphemeralObject` por meio ou instâncias para uma mensagem por 50 milissegundos ou mais. Isso é especialmente importante ao enviar alterações com base em coordenadas de toque ou mouse, como ao sincronizar posições de cursor, escrita à tinta e arrastar objetos ao redor de uma página.

<br>

</details>

## <a name="have-more-questions-or-feedback"></a>Tem mais perguntas ou comentários?

Envie problemas e solicitações de recursos para o repositório do SDK do [Live Share SDK](https://github.com/microsoft/live-share-sdk). Use a marca `live-share` e `microsoft-teams` para postar perguntas acerca de instruções sobre o SDK no [Stack Overflow](https://stackoverflow.com/questions/tagged/live-share+microsoft-teams).

## <a name="see-also"></a>Confira também

* [Repositório do GitHub](https://github.com/microsoft/live-share-sdk)
* [Documentos de referência do SDK do Live Share](/javascript/api/@microsoft/live-share/)
* [Documentos de referência do SDK do Live Share Media](/javascript/api/@microsoft/live-share-media/)
* [Aplicativos do Teams em reuniões](teams-apps-in-meetings.md)
