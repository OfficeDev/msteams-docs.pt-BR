---
title: Perguntas frequentes
description: Veja respostas a algumas perguntas comuns.
ms.topic: Frequently asked questions on Moodle LMS
ms.localizationpriority: high
ms.author: Surbhigupta
ms.openlocfilehash: 587451e3a0e89206a4ea49aaca3c682ab290ac5b
ms.sourcegitcommit: 8a0ffd21c800eecfcd6d1b5c4abd8c107fcf3d33
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2022
ms.locfileid: "63453899"
---
# <a name="moodle-faq"></a>Perguntas frequentes sobre o Moodle

Obtenha respostas para algumas de suas consultas ao usar o Moodle LMS.<br>

<br>

<details>

<summary><b>O que devo fazer se uma ou mais equipes do curso do Teams não forem criadas após a sincronização?</b></summary>

Cada curso do Moodle deve ter pelo menos um corpo docente e um aluno correspondentes a uma conta do Microsoft 365 UPN do AAD. A equipe não poderá ser criada se a sincronização não encontrar uma correspondência.

Cada instância do curso de equipe deve ter um proprietário e a sincronização define o corpo docente como o proprietário, supondo que o corpo docente tenha uma licença do Teams.

<br>

</details>

<details>

<summary><b>O que devemos fazer para remover a página de logon do Moodle ao trabalhar no Teams? Podemos forçar o SSO (logon único)?</b></summary>

Os usuários têm várias opções de entrada na página de logon do Moodle.

* Para entrar exclusivamente usando credenciais Microsoft 365, habilite as definições de configuração do **Force redirect** para o plug-in **auth_oidc**. Se o serviço estiver habilitado, o usuário poderá ver a página de entrada da Microsoft.
* Para entrar manualmente no portal do Moodle, consulte [Moodle](https://moodle.org/login/index.php).

<br>

</details>

<details>

<summary><b>Como posso especificar quais usuários sincronizar? Não quero’ que todos os usuários do Azure AD sejam sincronizados com o site do Moodle. </b></summary>

Use a opção **Restrição de criação do usuário** para especificar os usuários sincronizando as opções de configuração do plug-in **local_o365**. O menu suspenso à esquerda do **filtro** oferece opções como País, Nome da Empresa e Idioma.

> [!TIP]
> Crie um grupo dinâmico do Microsoft 365 para habilitar a opção **filtro** com várias propriedades de perfil.

A imagem a seguir mostra as opções de restrições de criação do usuário:

:::image type="content" source="../assets/images/MoodleInstructions/faq-2.png" alt-text="Sincronizar" border="true":::

:::image type="content" source="../assets/images/MoodleInstructions/faq-3.png" alt-text="Azure AD" border="true":::

<br>

</details>

<details>

<summary><b>Queremos que nossos docentes possam sincronizar cursos com o Teams? Os administradores do Moodle são os únicos que podem controlar a sincronização de cursos?</b></summary>

Por padrão, somente os administradores do Moodle podem configurar a sincronização. O proprietário da equipe pode controlar se um curso está sincronizado com o Teams e **Permitir a configuração da sincronização do curso no curso** está habilitado. Nesse caso, o proprietário da equipe é o corpo docente. O bloco exibe a opção de configuração para indivíduos com as permissões de proprietário apropriadas. 

<!-- For more information, see Microsoft 365 block within the Moodle course interface. -->

A imagem a seguir mostra a opção **Permitir configurar a sincronização do curso no curso**:

:::image type="content" source="../assets/images/MoodleInstructions/faq-4.png" alt-text="Administrador" border="true":::

A imagem a seguir mostra a sincronização de cursos:

:::image type="content" source="../assets/images/MoodleInstructions/faq-5.png" alt-text="sincronização" border="true":::

<br>

</details>

<details>

<summary><b>Seguimos a documentação, mas as contas de usuário não sincronizam o AAD e o Moodle. O que devemos fazer?</b></summary>

O problema pode ser resolvido antes que os usuários executem **limpeza do token Delta** como uma etapa final de solução de problemas.

A tabela a seguir fornece as ações e dependências a serem executadas e verificadas:

| Dependência | Action | Referências|
|-------|------------|----------|
| Versão estável| Verifique se a versão do Moodle está listada como **estável**.| Para saber mais, confira[Suporte de versão](https://docs.moodle.org/dev/Releases#Version_support).|
|Permissões| Verifique se o aplicativo do Azure tem as permissões necessárias para executar a sincronização.| Para mais informações, confira [Permissões da Microsoft](https://docs.moodle.org/311/en/Microsoft_365#Permissions).|
| Sincronização Completa| Verifique se **Executar uma sincronização completa a cada execução** está habilitada e examine os **Logs de tarefa** para **Sincronizar com o Azure AD**.| Para obter mais informações, confira [Habilitar a sincronização completa](https://docs.moodle.org/311/en/local_o365).</br>Para obter mais informações, confira[Verificar os logs de tarefa](https://docs.moodle.org/311/en/local_o365#Sync_users_with_Azure_AD). |
|Atualização de token|Limpe o **Token delta de sincronização do usuário** no plug-in local_o365.| Para obter mais informações, confira [Atualizar de token](https://docs.moodle.org/38/en/Office365).|
<!-- |Atualização de token|Limpe o **Token delta de sincronização do usuário** no plug-in local_o365.| {moodle_url}\local_o365\acp.php?Mode=maintenance_cleandeltatoken| -->
<br>

</details>

<details>

<summary><b>Um ou mais usuários não conseguem entrar usando suas credenciais do Microsoft 365, embora a maioria dos usuários possa entrar sem problemas. Qual seria a causa dessa inconsistência?</b></summary>

O motivo para inconsistências com os usuários que não conseguem assinar usando suas credenciais do Microsoft 365 podem estar relacionadas à operação de mapeamento de usuário durante a sincronização. Para resolver esse problema, execute as seguintes etapas:

* Verifique se o tipo de autenticação de usuário do Moodle é **OpenID**.
* Verifique se o **Nome de usuário** do Moodle corresponde ao nome de usuário do AAD.
* Limpe o **Problema do token** e tente novamente.
* Verifique se os usuários têm **Permissões** para acessar o aplicativo do Azure.

<br>

</details>

<details>

<summary><b>Nenhum usuário consegue entrar usando suas credenciais do Microsoft 365. O que podemos fazer para resolver isso?</b></summary>

Os usuários que não conseguiram entrar no início precisam relatar o problema e verificar se o aplicativo **Segredo do cliente** não expirou.

A imagem a seguir mostra a mensagem de erro recebida quando o usuário entra usando suas credenciais do Microsoft 365:

:::image type="content" source="../assets/images/MoodleInstructions/faq-6.png" alt-text="Relatar problema" border="true":::

A imagem a seguir mostra o erro no portal do Azure:

:::image type="content" source="../assets/images/MoodleInstructions/faq-7.png" alt-text="Portal do Azure" border="true":::

Se o **Segredo do cliente** tiver expirado, o usuário precisará gerar um novo **Segredo do cliente** e atualizar a configuração encontrada na página. Os usuários conseguem entrar novamente depois que o **Segredo do cliente** foi atualizado, o que pode levar até 24 horas para provisionar novamente.

<br>

</details>

<details>

<summary><b>Como alterar a instância de equipes vinculada a um curso?</b></summary>

Os administradores podem alterar a instância de equipes associada a um curso por meio da página **Gerenciar conexões do Teams**. Selecione **Conectar** ao lado do curso a ser alterado e selecione a instância de equipes. Se você usar a redefinição de curso para arquivar uma equipe, poderá vinculá-la novamente à equipe anterior.

A imagem a seguir mostra a instância das equipes:

:::image type="content" source="../assets/images/MoodleInstructions/faq-8.png" alt-text="instância de equipes" border="true":::

<br>

</details>

<details>

<summary><b>Por quê a integração de reunião do Atto Teams não está aparecendo no editor do Atto?</b></summary>

O usuário poderá encontrar problemas de reunião do Atto Teams se a referência de ícone estiver ausente na **Configuração da Barra de Ferramentas**, que exibe o ícone do Teams no editor Atto. O usuário precisa adicionar o ícone de reunião do Teams à direita do ícone de links usando as seguintes etapas:

* Para reinstalar o plug-in:
* Atualize **Configuração da Barra de ferramentas** com a **reunião do Teams**.

As imagens a seguir mostram o ícone da Barra de Ferramentas após o ajuste de configuração da Barra de Ferramentas:

:::image type="content" source="../assets/images/MoodleInstructions/faq-9.png" alt-text="barra de ferramentas" border="true":::

:::image type="content" source="../assets/images/MoodleInstructions/faq-10.png" alt-text="ícone de links":::

Para obter mais informações sobre como editar a barra de ferramentas do Atto, consulte:

* [Atto editor-ModdleDocs](https://docs.moodle.org/311/en/Atto_editor)
* [Mapeamento do editor-Icon](https://docs.moodle.org/311/en/Atto_editor#:~:text=in%20the%20editor.-,Atto%20editor%20toolbar,-Atto%20Row%201)
<br>

</details>

<details>

<summary><b>As reuniões agendadas por meio da integração da Microsoft aparecem no Outlook ou nos calendários do Teams? Qual é a linha do tempo padrão para as reuniões serem exibidas?</b></summary>

As reuniões agendadas por meio do aplicativo não aparecem no calendário do agendador do Outlook ou do Teams pois são semelhantes às Reuniões do Canal. Todos os membros no canal do curso podem participar da reunião diretamente do link do canal inserido. Para saber mais, confira [Reuniões de canal](https://www.knowledgewave.com/blog/benefits-of-channel-meetings-in-microsoft-teams).

No entanto, você pode acessar o convite e adicionar manualmente os nomes de participantes aos campos **Obrigatório** ou **Opcional** do convite para reunião para exibir a reunião remota em seus calendários. As linhas do tempo padrão são baseadas na data em que o usuário especifica quando a reunião é criada. Para obter mais informações, confira [Limites e especificações para o Microsoft Teams](/microsoftteams/limits-specifications-teams).

<br>

</details>

<details>

<summary><b>Há algum site de suporte em que possamos obter mais ajuda sobre produtos e outros problemas?</b></summary>

Para obter suporte e ajuda sobre os problemas de produtos e serviços ou ajuda da comunidade de desenvolvedores, consulte [Suporte e comentários](/microsoftteams/platform/feedback).


