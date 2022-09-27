---
title: Criar um novo aplicativo teams no Visual Studio
author: surbhigupta
description: Neste módulo, saiba como criar um novo aplicativo do Teams usando o Kit de Ferramentas do Teams para Visual Studio
ms.author: v-amprasad
ms.localizationpriority: high
ms.topic: overview
ms.date: 07/29/2022
ms.openlocfilehash: 12f0b74726aed8cdca50d9f5c078acd0f22cbeaa
ms.sourcegitcommit: 65ae3ccc2312ddc6cdaa05096e30bdf9dca10c3f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/27/2022
ms.locfileid: "68027419"
---
# <a name="create-new-teams-app-in-visual-studio"></a>Criar um novo aplicativo teams no Visual Studio

O Kit de Ferramentas do Teams fornece modelos de aplicativo do Microsoft Teams no Visual Studio para criar o aplicativo Teams.  Você pode pesquisar e selecionar o modelo de aplicativo do Teams que você precisa ao criar um novo projeto. Você pode ter modelos de aplicativo do Teams para criar.

* Aplicativo tab
* Bot de comando
* Bot de notificação
* Extensão de mensagem

## <a name="prerequisites"></a>Pré-requisitos

| &nbsp; | Instalar | Para usar... |
| --- | --- | --- |
| &nbsp; | **Required** | &nbsp; |
| &nbsp; | Visual Studio versão 17.3 | Você pode instalar a edição enterprise do Visual Studio e instalar a carga de trabalho "ASP.NET" e as Ferramentas de Desenvolvimento do Microsoft Teams. |
| &nbsp; | Kit de ferramentas do Teams | Uma extensão do Visual Studio que cria um scaffolding de projeto para seu aplicativo. Use a versão mais recente. |
| &nbsp; | [Microsoft Teams](https://www.microsoft.com/microsoft-teams/download-app) | O Microsoft Teams para colaborar com todos com quem você trabalha por meio de aplicativos para chats, reuniões, chamadas - tudo em um só lugar. |
 | &nbsp; | [Preparar o locatário do Microsoft 365](../concepts/build-and-test/prepare-your-o365-tenant.md) | Acesso à conta do Teams com as permissões apropriadas para instalar um aplicativo. |

1. Selecione **Criar um novo projeto na** **seção Introdução** ao iniciar o Visual Studio.

   :::image type="content" source="../assets/images/Tools-and-SDK-revamp/Create-new-app-VS/vs-create-new-project1.png" alt-text="Criar um novo projeto desde a introdução":::

   Você também pode criar um novo projeto diretamente do aplicativo.

1. Selecione **o** menu Arquivo.
1. Selecione  **Novo**.
1. Selecione **Projeto**.

   :::image type="content" source="../assets/images/Tools-and-SDK-revamp/Create-new-app-VS/vs-create-new-project2.png" alt-text="Criar novo projeto no menu arquivo":::

1. Pesquise o **aplicativo Microsoft Teams** na lista.
1. Selecione **o aplicativo Microsoft Teams**.
1. Selecione **Avançar**.

   :::image type="content" source="../assets/images/Tools-and-SDK-revamp/Create-new-app-VS/vs-ms-teams-app.png" alt-text="Pesquisar e escolher o aplicativo Microsoft Teams":::

1. Selecione **o nome do projeto** e insira o nome do projeto.
1. Selecionar **Criar**.

   :::image type="content" source="../assets/images/Tools-and-SDK-revamp/Create-new-app-VS/vs-ms-teams-app-project-name.png" alt-text="Nomear seu aplicativo":::

1. Selecione o **tipo de aplicativo do Teams** que você deseja criar.
1. Selecionar **Criar**.

   :::image type="content" source="../assets/images/Tools-and-SDK-revamp/Create-new-app-VS/vs-ms-teams-app-type.png" alt-text="Selecionar o tipo de aplicativo do Teams":::

## <a name="teams-app-templates-in-teams-toolkit-for-visual-studio"></a>Modelos de aplicativo do Teams no Kit de Ferramentas do Teams para Visual Studio

Você pode ver os modelos de aplicativo do Teams já preenchidos no Kit de Ferramentas do Teams para vários tipos de aplicativos do Teams. A tabela a seguir lista todos os modelos disponíveis:

|Modelo de aplicativo do Teams  |Descrição  |
|---------|---------|
|Bot de notificação     |O aplicativo bot de notificação pode enviar notificação ao cliente do Teams. Há várias maneiras de disparar a notificação. Por exemplo, dispare a notificação por solicitação HTTP ou por tempo. Você também pode selecionar a notificação disparada com base em seu cenário de negócios.         |
|Bot de comando     |Os usuários podem digitar um comando para interagir com o bot usando o aplicativo Bot de Comando.         |
|Tab     |O aplicativo Tab mostra uma página da Web dentro do Teams e permite o logon único usando a conta do Teams.         |
|Extensão de Mensagem     |O aplicativo extensão de mensagem implementa recursos simples, como criar cartão adaptável, pesquisar pacotes DoCker, desfralização de links para o domínio "dev.botframework.com".         |

> [!NOTE]
>Depois que o projeto é criado, o Kit de Ferramentas do Teams abre automaticamente a Introdução. Agora você pode ver as instruções em Introdução e conferir os diferentes recursos no Kit de Ferramentas do Teams.

## <a name="see-also"></a>Confira também

* [Provisionar recursos de nuvem usando o Visual Studio](provision-cloud-resources.md)
* [Implantar o aplicativo Teams na nuvem usando o Visual Studio](deploy-teams-app.md)
