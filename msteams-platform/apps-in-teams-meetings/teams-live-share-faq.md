---
title: Perguntas frequentes do Live Share
author: surbhigupta
description: Neste módulo, saiba mais sobre as Perguntas frequentes do Live Share.
ms.topic: overview
ms.localizationpriority: high
ms.author: v-ypalikila
ms.date: 04/07/2022
ms.openlocfilehash: d29318397e388faca93695040914493ecae369a5
ms.sourcegitcommit: 79d525c0be309200e930cdd942bc2c753d0b718c
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/19/2022
ms.locfileid: "66841866"
---
---

# <a name="live-share-sdk-faq"></a>Perguntas frequentes sobre o SDK do Live Share

Obtenha respostas para dúvidas comuns ao usar o Live Share.<br>

<br>

<details>

<summary><b>Posso usar meu próprio serviço do Azure Fluid Relay?</b></summary>

Sim. Ao construir a classe `TeamsFluidClient`, você pode definir sua própria classe `AzureConnectionConfig`. O Live Share associa os contêineres que você cria a reuniões, mas você precisará criar seu próprio `ITokenProvider` do Azure para assinar tokens aos seus contêineres e requisitos regionais. Para obter mais informações, confira [documentação do Fluid Relay](/azure/azure-fluid-relay/).

<br>

</details>

<details>

<summary><b>Por quanto tempo os dados são armazenados no serviço hospedado do Live Share podem ser acessados?</b></summary>

Todos os dados enviados ou armazenados por meio de contêineres do Fluid criados pelo serviço Azure Fluid Relay hospedado pelo Live Share ficam acessíveis por 24 horas. Se você quiser manter os dados por mais de 24 horas, pode substituir nosso serviço do Azure Fluid Relay hospedado pelo seu. Como alternativa, você pode usar seu próprio provedor de armazenamento em paralelo ao serviço hospedado do Live Share.

<br>

</details>

<details>

<summary><b>Quais tipos de reunião são compatíveis com o Live Share?</b></summary>

Atualmente, há suporte apenas para reuniões agendadas e todos os participantes devem estar no calendário da reunião. Não há suporte para reuniões do tipo Reunir Agora, chamadas individuais, chamadas em grupo.

<br>

</details>

<details>

<summary><b>O pacote de mídia do Live Share funcionará com conteúdo do DRM?</b></summary>

Não. Atualmente, o Teams não oferece suporte a mídia criptografada para aplicativos de guia.

<br>

</details>

<details>
<summary><b>Quantas pessoas podem participar de uma sessão do Live Share?</b></summary>

Atualmente, o Live Share oferece suporte a um máximo de 100 participantes por sessão.

<br>

</details>

## <a name="have-more-questions-or-feedback"></a>Tem mais perguntas ou comentários?

Envie problemas e solicitações de recursos para o repositório do SDK do [Live Share SDK](https://github.com/microsoft/live-share-sdk). Use a marca `live-share` e `microsoft-teams` para postar perguntas acerca de instruções sobre o SDK no [Stack Overflow](https://stackoverflow.com/questions/tagged/live-share+microsoft-teams).

## <a name="see-also"></a>Confira também

- [Repositório do GitHub](https://github.com/microsoft/live-share-sdk)
- [Documentos de referência do SDK do Live Share](/javascript/api/@microsoft/live-share/)
- [Documentos de referência do SDK do Live Share Media](/javascript/api/@microsoft/live-share-media/)
- [Aplicativos do Teams em reuniões](teams-apps-in-meetings.md)
