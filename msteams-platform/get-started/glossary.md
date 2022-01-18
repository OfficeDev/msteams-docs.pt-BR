---
title: Microsoft Teams Documentação do Desenvolvedor - Glossário
description: Glossário para documentação Microsoft Teams desenvolvedor
ms.localizationpriority: medium
ms.topic: reference
keywords: Microsoft Teams de desenvolvedor
ms.openlocfilehash: 0858d0cfb246e99871c02f81c82c1eaa30bb6edf
ms.sourcegitcommit: 9e448dcdfd78f4278e9600808228e8158d830ef7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/17/2022
ms.locfileid: "62059825"
---
# <a name="glossary"></a>Glossário

Termos e definições comuns usados na documentação Teams desenvolvedor.
<br>
<br>
<details>
<summary>A</summary>

| Termo | Definição |
| --- | --- |
| Comando Action | Comandos de ação são usados para apresentar aos usuários um pop-up modal para coletar ou exibir informações. <br>**Consulte também**: Extensão de mensagens; Comandos de pesquisa |
| Cartão Adaptável | Um Cartão Adaptável é um trecho de conteúdo acionável que você pode adicionar a uma conversa por meio de um bot ou extensão de mensagens. Usando texto, gráficos e botões, esses cartões fornecem uma comunicação rica para seu público-alvo. |
| Catálogo de Aplicativos | O Catálogo de Aplicativos é usado para armazenar os aplicativos para SharePoint e office para uso interno da nossa organização. |
| Manifesto do aplicativo | O Teams de aplicativo descreve como o aplicativo se integra ao Microsoft Teams produto. Seu manifesto deve estar em conformidade com o esquema hospedado em https://developer.microsoft.com/json-schemas/teams/v1.11/MicrosoftTeams.schema.json . |
| Pacote do aplicativo | Um Teams de aplicativo é um arquivo zip que contém os ícones do arquivo de manifesto do aplicativo e do aplicativo - ícone de cor e ícone de contorno. |
| Permissões de aplicativos | A opção Permissões do aplicativo Teams permite habilitar as permissões de dispositivo do aplicativo para seu aplicativo. Ele só estará disponível quando o arquivo de manifesto do aplicativo declarar que o aplicativo precisa de permissões de dispositivo. <br> **Consulte também**: Permissões de dispositivo |
| Escopo do aplicativo | O escopo do aplicativo determina como seu aplicativo interage com seus usuários. Um aplicativo pode ter escopo pessoal, escopo de canal ou escopo de equipe. Um Teams pode existir entre escopos. |
| App Studio | App Studio é um aplicativo para começar a criar ou integrar seus próprios Microsoft Teams aplicativos. Ele agora evoluiu para o Portal do Desenvolvedor. <br> **Consulte também**: Portal do Desenvolvedor |
| Recurso do Azure | Um serviço que está disponível por meio do Azure que seu aplicativo Teams pode usar para implantação do Azure. Pode ser contas de armazenamento, aplicativos Web, bancos de dados e muito mais. |
| Azure Active Directory | Azure Active Directory (Azure AD) é o serviço de gerenciamento de acesso e identidade baseado em nuvem da Microsoft. Ele ajuda os usuários autenticados a acessar recursos internos e externos do Azure. |
| Autenticação | A autenticação é um processo para autorizar o acesso do usuário para uso do seu aplicativo. pode ser feito usando APIs do Microsoft Graph ou autenticação baseada na Web. <br> **Consulte também**: Provedores de identidade |
| Fluxo de autenticação | No Teams, há dois fluxos de autenticação diferentes para autenticar um usuário para usar um aplicativo: autenticação baseada na Web e fluxo OAuthPrompt. |
|
</details>
<br>
<details>
<summary>B</summary>

| Termo | Definição |
| --- | --- |
| Blazor | O Blazor é uma estrutura web gratuita e de código aberto que permite que os desenvolvedores criem aplicativos Web usando C# e HTML. Ele permite criar UIs da Web interativas usando C# em vez de JavaScript. Os aplicativos Blazor são compostos de componentes de interface do usuário da Web reutilizáveis implementados usando C#, HTML e CSS. Ele está sendo desenvolvido pela Microsoft. |
| Bicep | Bicep é uma linguagem declarativa, o que significa que os elementos podem aparecer em qualquer ordem. Ao contrário dos idiomas imperativos, a ordem dos elementos não afeta como a implantação é processada. |
| Bot | Um bot é um aplicativo que executa tarefas repetitivas programadas. <br> **Consulte também**: bot de conversa; Bot de chat |
| Bot Emulator | Bot Framework Emulator é um aplicativo de área de trabalho que permite testar e depurar bots, localmente ou remotamente. |
| Bot Framework | A Estrutura de Bot é um SDK rico usado para criar bots usando C#, Java, Python e JavaScript. Se você já tiver um bot baseado na Estrutura de Bots, poderá facilmente modificá-lo para funcionar Teams. |
</details>
<br>
<details>
<summary>C</summary>

| Termo | Definição |
| --- | --- |
| Bot de chamada | Um bot que participa de chamadas de áudio ou vídeo e reuniões online. <br> **Consulte também**: bot de chat; Bot de reunião |
| Funcionalidade | O recurso de um Teams app é chamado de Recurso. Um aplicativo pode ter um ou mais recursos principais, como guia, bot, extensões de mensagens. <br>**Consulte também**: Funcionalidade do dispositivo; Funcionalidade de mídia |
| Bot de chat | Um bot também é conhecido como chatbot ou bot de conversa. É um aplicativo que executa tarefas simples e repetitivas por usuários, como atendimento ao cliente ou equipe de suporte. <br> **Consulte também**: bot de conversa. |
| Canal | Um canal é um único local para uma equipe compartilhar mensagens, ferramentas e arquivos. No Teams, o trabalho em equipe e a comunicação ocorrem nos canais.  |
| Segredo do cliente | O segredo/senha do cliente ou um par de chaves públicas ou privadas que é Certificate. Isso não é necessário para aplicativos nativos. <br> **Consulte também**: Bot |
| Recursos de nuvem | Um serviço que está disponível na nuvem por meio da Internet que seu aplicativo Teams pode usar. Pode ser contas de armazenamento, aplicativos Web, bancos de dados e muito mais. |
| Aplicativo de colaboração |  <br> **Consulte também**: Aplicativo autônomo |
| Conectores |  <br> **Consulte também**: Webhooks |
| Conversa | Uma conversa é uma série de mensagens enviadas entre seu Microsoft Teams bot e um ou mais usuários. Uma conversa pode ter três escopos: canal, pessoal e chat em grupo. <br>**Consulte também**: chat um-a-um; Chat em grupo |
| Bot de conversa |  Os bots de conversa permitem que os usuários interajam com seu serviço Web usando texto, cartões interativos e módulos de tarefa. <br>**Consulte aso** Bot de chat |