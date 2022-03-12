---
title: Plug-ins do Microsoft 365
description: Detalhes dos plug-ins do Microsoft 365
ms.topic: Microsoft 365 plugins
ms.localizationpriority: high
ms.author: Surbhigupta
ms.openlocfilehash: 3a1847a01687d2d363f29938ed589d3a12179c9c
ms.sourcegitcommit: 8a0ffd21c800eecfcd6d1b5c4abd8c107fcf3d33
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2022
ms.locfileid: "63453914"
---
# <a name="microsoft-365-plugins"></a>Plug-ins do Microsoft 365

Os plug-ins do Microsoft 365 fornecem integração entre o site do Moodle e o Teams. Esses plugins facilitam para o usuário agendar, entregar e colaborar com o conteúdo do curso. Os plugins podem ser usados ​​de forma independente ou em parceria conforme a necessidade.

## <a name="plugin-list-and-labels"></a>Lista de plugins e rótulos

A tabela a seguir lista os plug-ins e rótulos do GitHub a serem usados ​​com base nos requisitos.

<!--Old content of the table updated and revamped |Plugins to install |Description |GitHub label(s)|
|-----|-----|----|
|[**OpenID Connect**](#openid-connect)|Enable SSO for users who work using both Moodle and Microsoft Teams|auth_oidc|
|• [**OpenID Connect**](#openid-connect) </br> • [**Microsoft 365 integration**](#microsoft-365-integration) |Create Teams instances for each course in Moodle, and sync faculty as owners, and students as team members|• auth_oidc </br> • local_o365|
|• [**OpenID Connect**](#openid-connect) </br> • [**Microsoft 365 integration**](#microsoft-365-integration) </br> • [**Teams Theme**](#microsoft-365-teams-theme)| Remove Moodle blocks and extra chrome within the Moodle iframes for Teams, which applies while mapping courses to Teams instances | • auth_oidc </br> • local_o365 </br> • themeboost_o365teams |
|• [**OpenID Connect**](#openid-connect) </br> • [**Microsoft 365 integration**](#microsoft-365-integration) </br> • [**Microsoft 365 Repository**](#microsoft-365-repository) |Leverage Microsoft 365 OneDrive content for file repositories to reduce storage needs in Moodle | • auth_oidc </br> * local_o365 </br> • repository_office 365|
|• [**OpenID Connect**](#openid-connect) </br> • [**OneNote**](#onenote-integration) </br> • [**OneNote Submissions**](#onenote-integration) </br> • [**OneNote Feedback**](#onenote-integration) | Enable OneNote to be used for assignment, submission and feedback |• auth_oidc </br> • local_onenote </br> • assignsubmission_onenote </br> • assignfeedback_onenote |  
|• [**OpenID Connect**](#openid-connect) </br> • [**Microsoft 365 integration**](#microsoft-365-integration) • [**Microsoft 365 Repository**](#microsoft-365-repository) </br> • [**Microsoft Block**](#microsoft-365-repository) | Enable 365 quick access blocks within Moodle with links to Microsoft 365 collaboration services and install links for Microsoft Office | • auth_oidc </br> • local_o365 </br> • repository_office365 </br> • block_microsoft |
|[**Teams Meeting**](#teams-meetings) | Enable Atto editor in Moodle to create Teams meeting links |atto_teamsmeeting |
|[**oEmbed Filter**](#oembed-filter) | Enable video links in Moodle | Filter_oembed| -->

|Plugins para instalar |Descrição |Rótulo(s) do GitHub|
|-----|-----|----|
|[**Conexão OpenID**](#openid-connect)|Habilita o SSO para usuários que trabalham usando o Moodle e o Teams.|auth_oidc|
|[**Integração com Microsoft 365**](#microsoft-365-integration)|Crie instâncias do Teams para cada curso no Moodle e sincronize professores como proprietários e alunos como membros da equipe.|local_o365|
|[**Repositório do Microsoft 365**](#microsoft-365-repository) |Oferece suporte ao conteúdo do Microsoft 365 OneDrive para repositórios de arquivos para reduzir as necessidades de armazenamento no Moodle.| repository_office 365|
|[**Reunião do Teams**](#teams-meetings) |Habilita o editor Atto no Moodle para criar links de reunião do Teams.|atto_teamsmeeting |
|[**Tema do Teams**](#microsoft-365-teams-theme)| Remova blocos do Moodle e cromo extra nos iframes do Moodle para equipes, que se aplicam ao mapear cursos para instâncias do Teams.| themeboost_o365teams |
|[**OneNote**](#onenote-integration)| Habilite o OneNote para ser usado para atribuição, envio e comentários.|local_onenote, assignsubmission_onenote e assignfeedback_onenote </br>|  
|[**Bloqueio da Microsoft**](#microsoft-block) | Habilita os blocos de acesso rápido do Microsoft 365 no Moodle com links para os serviços de colaboração do Microsoft 365 e links de instalação para o Microsoft Office.|block_microsoft |
|[**oFiltro incorporado**](#oembed-filter) | Habilite links de vídeo no Moodle.|Filter_oembed|

O Moodle LMS suporta os seguintes plug-ins:

## <a name="openid-connect"></a>Conexão OpenID

O plug-in Open ID Connect permite que os usuários autentiquem qualquer site ou ferramenta que suporte a especificação necessária e forneça suporte de logon único (SSO) com o Microsoft Office 365. O plug-in OpenID Connect oferece às instituições as seguintes opções de login para atender aos seus requisitos específicos:

* Os usuários podem inserir suas credenciais do Office 365, como email e senha para entrar diretamente ou entrar usando os campos de nome de usuário e senha do Moodle, sem entrar no Office 365.
* Os usuários podem selecionar o link para entrar por meio do Office 365 ou do provedor OpenID Connect na página do Moodle.

A imagem a seguir exibe a página de logon do OpenID Connect:

:::image type="content" source="../../assets/images/MoodleInstructions/openid-connect.png" alt-text="Faça login para conexão de ID aberto" border="true":::

## <a name="microsoft-365-integration"></a>Integração com Microsoft 365

A integração do Microsoft 365 consiste em vários aplicativos com várias funcionalidades, o que permite que os usuários permaneçam conectados e executem diferentes ações conforme necessário. O plug-in permite que os administradores verifiquem o seguinte:

* Verifique as funções de integração apropriadas.
* Sincronize usuários entre o Office 365 e o Moodle.
* Configure as permissões necessárias para os usuários.
* Configure o site do Microsoft Office SharePoint Online para os arquivos do curso.

A imagem a seguir exibe a página de configuração de integração do Microsoft 365:

:::image type="content" source="../../assets/images/MoodleInstructions/365-integration.png" alt-text="integração do Microsoft 365" border="true":::

### <a name="user-functions"></a>Funções do usuário

Os usuários podem executar as seguintes ações com a integração do Microsoft 365:

* Verifique o funcionamento geral de todas as integrações de plug-in do Microsoft 365.
* Carregue um arquivo CSV, que compara os usuários do Moodle aos do Office 365.
* Verifique as configurações de permissões do Azure Active Directory.

## <a name="microsoft-365-repository"></a>Repositório do Microsoft 365

O plug-in do repositório do Microsoft 365 permite que os usuários armazenem arquivos de curso no OneDrive. O corpo docente pode adicionar arquivos da seção de arquivos do curso do OneDrive ou de seu próprio espaço pessoal ao repositório.

O repositório do Microsoft 365 permite que o usuário o use como um repositório de arquivos para uma instituição, mantendo a estrutura de dados do Moodle simples. O plug-in do repositório do Microsoft 365 fornece os seguintes serviços:

* O corpo docente pode armazenar os arquivos do curso no OneDrive. Cada curso tem sua própria pasta criada no OneDrive, que permite que os professores adicionem arquivos da área de arquivos do curso do OneDrive ou de seu próprio espaço pessoal.  
* Para adicionar arquivos ao Moodle como uma cópia ou criar um link para o arquivo. O arquivo vinculado é exibido em uma nova janela do aplicativo ou incorporado na página da Web.
* Para carregar arquivos no OneDrive ou Microsoft Office SharePoint Online usando o seletor de arquivos do Moodle.

A imagem a seguir exibe o repositório de arquivos do Microsoft 365:

:::image type="content" source="../../assets/images/MoodleInstructions/microsoft-365- repository.png" alt-text="Repositório M365"  border="true":::

## <a name="teams-meetings"></a>Reuniões de Teams

O plug-in de reuniões do Teams permite que o usuário crie solicitações de reuniões no calendário, atribuições, postagens no fórum e também no editor Atto conforme disponibilidade.

Após a instalação do plug-in, professores e alunos podem criar uma reunião de áudio ou vídeo usando o Moodle, o que requer uma conta Microsoft 365 e permissões do Moodle.

>[!NOTE]
>As reuniões do Teams não aparecem no calendário do Outlook ou do Teams, no entanto, nomes de alunos individuais podem ser adicionados ao convite para o mesmo.

A imagem a seguir exibe a página de entrada da reunião do Teams:

:::image type="content" source="../../assets/images/MoodleInstructions/teams-meeting.png" alt-text="fazer login na reunião de equipes" border="true":::

## <a name="microsoft-365-teams-theme"></a>Tema do Microsoft 365 Teams

O plug-in de tema do Microsoft 365 Teams fornece aos usuários uma exibição personalizada da página inicial do curso do Moodle e está disponível para visualização quando o usuário acessa seus cursos do Moodle no Teams.

O plug-in do tema oferece aos usuários uma experiência aprimorada unificada com os seguintes recursos:

* Adapta-se às alterações de tema do Microsoft Teams, como padrão, escuro e alto contraste.
* Fornece foco nas atividades do curso.
* Remove blocos, navegação, cabeçalho e rodapé do Moodle.
* Fornece elementos da interface do usuário (Interface do Usuário) do Microsoft Team.

A imagem a seguir exibe o tema do Teams configurado pelo usuário:

:::image type="content" source="../../assets/images/MoodleInstructions/teams-theme.png" alt-text="Tema do Microsoft Teams" border="true":::

## <a name="onenote-integration"></a>Integração do OneNote

O plug-in de integração do OneNote oferece aos usuários opções para navegar em blocos de anotações, seções e páginas; onde as tarefas são enviadas e o corpo docente fornece os comentários necessários sobre as tarefas correspondentes no OneNote. O OneNote também aprimora a experiência do usuário adicionando recursos além de testes e links, enquanto estende os recursos para dispositivos móveis usando canetas digitais, mídia de foto ou vídeo e coautoria com grupos.

A integração do OneNote ajuda no acesso a repositórios de textos, gráficos e áudio. O plug-in oferece as seguintes vantagens:

* Inclua cadernos de navegação, seções e páginas, onde os alunos trabalham em tarefas e fornecem comentários sobre essas tarefas no OneNote.
* Combine o fichário digital para anotações, tarefas e comentários para referência e análise.
* Expanda os recursos de desenho além de texto e links e estenda o uso móvel usando canetas digitais, mídia de foto ou vídeo e coautoria com grupos.
* Inclua a página de envio e comentários para cada tarefa na conta do corpo docente. Quando tal é salvo no Moodle, uma cópia do HTML e quaisquer imagens associadas são empacotadas em um arquivo zip.

> [!NOTE]
> Os eventos de envio ou comentários acionam a criação do OneNote com uma seção para cada curso em que o aluno se matriculou.

## <a name="microsoft-block"></a>Bloqueio da Microsoft

O plug-in de bloco da Microsoft permite que o usuário acesse o local do arquivo do Microsoft Office SharePoint Online do curso e visualize o curso no bloco de anotações do OneNote para envios, juntamente com a opção de modificar as preferências de integração do Office 365. Os administradores podem configurar o bloco para aparecer em todas as páginas do curso.

O bloco da Microsoft aprimora a experiência do usuário fornecendo uma interface de usuário para modificar os recursos de integração do Microsoft 365 e o acesso a seus vários recursos. Os administradores podem configurar o bloco para visualizar as alterações modificadas a serem exibidas em cada página do curso. O bloco permite ao usuário realizar as seguintes atividades:

* Acesse o local do arquivo do Microsoft Office SharePoint Online do curso e o bloco de anotações do OneNote.
* Veja o curso no bloco de anotações do OneNote para envios.
* Configure a sincronização do calendário do Outlook.
* Gerencia a conexão com o Office 365.
* Personalize as preferências pessoais de integração do Office 365.

A imagem a seguir mostra a interface do usuário do bloco da Microsoft:

:::image type="content" source="../../assets/images/MoodleInstructions/microsoft-block-1.png" alt-text="bloco microsoft" border="true":::

## <a name="oembed-filter"></a>filtro oEmbed

O plug-in do filtro oEmbed simplifica e aprimora a experiência do usuário, simplificando a inclusão do conteúdo HTML externo no Moodle. A seguir estão as vantagens do filtro oEmbed. 

* Reduz o tempo para incorporar vídeos em uma página HTML.
* Permite a incorporação de vários provedores de conteúdo de vídeo.
* Garante um método mais rápido para copiar e incorporar código de qualquer um dos serviços suportados.
* Permite a incorporação de vídeo sem uma chave de API.

A imagem a seguir mostra a inclusão de conteúdo HTML externo no Moodle:

:::image type="content" source="../../assets/images/MoodleInstructions/oEmbed-filter.png" alt-text="página do filtro oEmbed" border="true":::

## <a name="see-also"></a>Confira também

* [Aplicativos de parceiros para o Moodle](../partner-apps-for-moodle.md)
* [Perguntas frequentes do Moodle](../faqs.md)