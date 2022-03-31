---
title: Pré-requisitos
author: surbhigupta
description: Todas as guias Microsoft Teams devem seguir esses requisitos.
keywords: canal de grupo de guias do teams configurável
ms.localizationpriority: medium
ms.topic: conceptual
ms.author: lajanuar
ms.openlocfilehash: fe72691465ca785cefb6a96c8eb4005a64601a17
ms.sourcegitcommit: 3dc9b539c6f7fbfb844c47a78e3b4d2200dabdad
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/31/2022
ms.locfileid: "64571513"
---
# <a name="prerequisites"></a>Pré-requisitos

Certifique-se de que você adere aos seguintes pré-requisitos durante Teams sua guia pessoal e canal ou grupo:

* Permita que suas páginas de tabulação sejam descobertas em um iFrame, usando cabeçalhos de resposta HTTP X-Frame-Options e Content-Security-Policy.
  * Definir o header: `Content-Security-Policy: frame-ancestors teams.microsoft.com *.teams.microsoft.com *.skype.com`
  * Para compatibilidade com o Internet Explorer 11, de definir `X-Content-Security-Policy`.
  * Como alternativa, de definir o header `X-Frame-Options: ALLOW-FROM https://teams.microsoft.com/`. Esse header é preterido, mas ainda é aceito pela maioria dos navegadores.

* As páginas de logon não são renderizações em iFrames, como uma proteção contra o clickjacking. Sua lógica de autenticação precisa usar um método diferente de redirecionamento. Por exemplo, use autenticação baseada em token ou cookie.

    > [!NOTE]
    > É recomendável definir o uso pretendido para seus cookies em vez de depender do comportamento padrão do navegador. Para obter mais informações, consulte [atributo cookie SameSite](../../resources/samesite-cookie-update.md).

* A restrição de política de mesma origem dos navegadores impede que as páginas da Web fazem solicitações para domínios diferentes da página da Web atendida. Assim, você pode redirecionar a página de configuração ou conteúdo para outro domínio ou subdomínio. Sua lógica de navegação entre domínios precisa permitir que o cliente Teams valide a origem em relação a `validDomains` uma lista estática no manifesto do aplicativo ao carregar ou se comunicar com a guia.

* Estilmente suas guias com base Teams tema, design e intenção do cliente. As guias funcionam melhor quando são criadas para atender a uma necessidade específica e se concentrar em um pequeno conjunto de tarefas ou em um subconjunto de dados relevante para o local do canal da guia.

* Em sua página de conteúdo, adicione uma referência ao [Microsoft Teams SDK do cliente JavaScript](/javascript/api/overview/msteams-client) usando marcas de script. Depois que sua página for carregada, faça uma chamada para `microsoftTeams.initialize()`, caso contrário, sua página não será exibida.

* Para que a autenticação funcione em clientes móveis, você deve atualizar para o Teams JavaScript SDK 1.4.1 e posterior.

* Se você optar por ter seu canal ou guia de grupo para aparecer Teams cliente móvel, `setSettings()` a configuração deve ter um valor para a `websiteUrl` propriedade.

* Microsoft Teams guia não suporta a capacidade de carregar sites da intranet que usam certificados auto-assinados.

## <a name="tools-to-build-tabs"></a>Ferramentas para criar guias

| &nbsp; | Instalar | Para usar... |
| --- | --- | --- |
| **Required** | &nbsp; | &nbsp; |
| &nbsp; | [Node.js](https://nodejs.org/en/download/) | Ambiente de tempo de execução javaScript back-end. Use a versão mais recente do v14 LTS.|
| &nbsp; | [Microsoft Edge](https://www.microsoft.com/edge) (recomendado) ou [Google Chrome](https://www.google.com/chrome/) | Um navegador com ferramentas de desenvolvedor. |
| &nbsp; | [Visual Studio Code](https://code.visualstudio.com/download) | Ambientes de com build javaScript, TypeScript ou Estrutura do SharePoint (SPFx) . |
| &nbsp; | [Visual Studio 2019](https://visualstudio.com/download), ASP.NET **e desenvolvimento da Web** ou carga de trabalho de desenvolvimento entre **plataformas do .NET Core** | .NET. Você pode instalar a edição gratuita da comunidade Visual Studio 2019. |
| &nbsp; | [Git](https://git-scm.com/downloads) | Git para usar o repositório de aplicativos de exemplo GitHub. |
| &nbsp; | [Microsoft Teams](https://www.microsoft.com/en-us/microsoft-teams/download-app) | Microsoft Teams colaborar com todos com os quais você trabalha por meio de aplicativos para chat, reuniões, chamada - tudo em um só lugar. |
| &nbsp; | [ngrok](https://ngrok.com/download) | Ngrok é uma ferramenta de software de proxy reverso. O Ngrok cria um túnel para os pontos de extremidade HTTPS do servidor Web em execução localmente. Os pontos de extremidade da Web do seu servidor estão disponíveis durante a sessão atual em seu computador. Quando o computador é desligado ou vai para o sono, o serviço não está mais disponível. |
| &nbsp; | [Portal do Desenvolvedor do Teams](https://dev.teams.microsoft.com/) | Portal baseado na Web para configurar, gerenciar e distribuir seu aplicativo Teams, incluindo a sua organização ou o Teams store. |

### <a name="build-your-teams-tab"></a>Criar sua Teams guia

Agora vamos criar sua guia. Mas primeiro selecione sua opção de guia para criar:

> [!div class="nextstepaction"]
> [Construir uma guia pessoal](~/tabs/how-to/create-personal-tab.md)
> [!div class="nextstepaction"]
> [Criar um canal ou uma guia de grupo](~/tabs/how-to/create-channel-group-tab.md)

## <a name="see-also"></a>Confira também

* [Teams guias](~/tabs/what-are-tabs.md)
* [Guias em dispositivos móveis](~/tabs/design/tabs-mobile.md)