---
title: Perguntas frequentes
author: MuyangAmigo
description: Neste módulo, confira perguntas frequentes sobre o Kit de Ferramentas do Teams usando Visual Studio Code
ms.author: zhany
ms.localizationpriority: medium
ms.topic: overview
ms.date: 11/29/2021
ms.openlocfilehash: 88a1fba1213dce01ed48fccbc72ca02757859033
ms.sourcegitcommit: ed7488415f814d0f60faa15ee8ec3d64ee336380
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2022
ms.locfileid: "67617027"
---
# <a name="faq-for-teams-toolkit-using-visual-studio-code"></a>Perguntas frequentes sobre o Kit de Ferramentas do Teams usando Visual Studio Code

Você pode ver as perguntas frequentes sobre todas as seções do Kit de Ferramentas do Teams para Visual Studio Code.

Perguntas frequentes para [provisionar recursos de nuvem usando o Kit de Ferramentas do Teams](provision.md)

<br>

<details>

<summary><b>Como solucionar problemas?</b></summary>

Se você receber mensagens de erro com o Kit de Ferramentas do Teams no Visual Studio Code, poderá selecionar **Obter Ajuda** na notificação de erro para navegar até o documento relacionado. Se você estiver usando a CLI do TeamsFx, haverá um hiperlink no final da mensagem de erro que aponta para o documento de ajuda. Também é possível visualizar o [documento de ajuda de provisionamento](https://aka.ms/teamsfx-arm-help) diretamente.

<br>

</details>

<details>

<summary><b>Como posso alternar para outra assinatura do Azure durante o provisionamento?</b></summary>

1. Alterne a assinatura na conta atual ou faça logoff e selecione uma nova assinatura.
2. Se você já tiver provisionado o ambiente atual, precisará criar um novo ambiente e executar o provisionamento porque o ARM não dá suporte à movimentação de recursos.
3. Se você não provisionou o ambiente atual, poderá disparar o provisionamento diretamente.

<br>

</details>

<details>

<summary><b>Como posso alterar o grupo de recursos durante o provisionamento?</b></summary>

Antes de provisionar, a ferramenta pergunta se você deseja criar um novo grupo de recursos ou usar um existente. É possível fornecer um novo nome de grupo de recursos ou escolher um existente nesta etapa.

<br>

</details>

<details>

<summary><b>Como posso provisionar um aplicativo baseado no SharePoint?</b></summary>

É possível seguir [provisionar aplicativos baseados no SharePoint](/microsoftteams/platform/sbs-gs-spfx?tabs=vscode%2Cviscode&tutorial-step=4).

> [!NOTE]
> Atualmente, a criação de aplicativos do Teams com a estrutura do SharePoint com o Kit de Ferramentas do Teams não tem integração direta com o Azure, o conteúdo no documento não se aplica a aplicativos baseados em SPFx.

<br>

</details>
