---
title: Pré-requisitos
author: surbhigupta
description: Neste artigo, conheça os pré-requisitos para criar a guia pessoal, canal ou grupo do Microsoft Teams. Conheça as ferramentas necessárias para criar sua guia.
ms.localizationpriority: high
ms.topic: conceptual
ms.author: lajanuar
ms.openlocfilehash: e1160566f73a63a7de87653900cdc64ba7cb0e52
ms.sourcegitcommit: 87bba925d005eb331d876a0b9b75154f8100e911
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/27/2022
ms.locfileid: "67450412"
---
# <a name="prerequisites"></a>Pré-requisitos

Certifique-se de aderir aos seguintes pré-requisitos ao criar sua guia pessoal e de canal ou grupo do Teams:

* Permitir que suas páginas da guia sejam descobertas em um iFrame, usando cabeçalhos de réplica HTTP Content-Security-Policy e X-Frame-Options.
  * Definir cabeçalho: `Content-Security-Policy: frame-ancestors teams.microsoft.com *.teams.microsoft.com *.skype.com`
  * Para compatibilidade com o Internet Explorer 11, defina `X-Content-Security-Policy`.
  * Alternativamente, defina o cabeçalho `X-Frame-Options: ALLOW-FROM https://teams.microsoft.com/`. Este cabeçalho foi preterido, mas ainda é aceito pela maioria dos navegadores.

* As páginas de logon não são renderizadas em iFrames, como uma proteção contra clickjacking. Sua lógica de autenticação precisa usar um método diferente de redirecionamento. Por exemplo, utilize a autenticação baseada em token ou em cookie.

    > [!NOTE]
    > É recomendável que você defina o uso pretendido para seus cookies em vez de confiar no comportamento padrão do navegador. Para obter mais informações, confira [Atributos do cookie SameSite](../../resources/samesite-cookie-update.md).

* A restrição da política de mesma origem dos navegadores impede que as páginas da Web façam solicitações para domínios diferentes da página da Web atendida. Assim, você pode redirecionar a página de configuração ou conteúdo para outro domínio ou subdomínio. Sua lógica de navegação entre domínios precisa permitir que o cliente do Teams valide a origem em relação a uma lista estática de `validDomains` no manifesto do aplicativo ao carregar ou se comunicar com a guia.

* Estilize suas guias com base no tema, design e intenção do cliente do Teams. As guias funcionam melhor quando são criadas para atender a uma necessidade específica e se concentram em um pequeno conjunto de tarefas ou um subconjunto de dados relevantes para o local do canal da guia.

* Dentro da sua página de conteúdo, adicione uma referência ao [SDK do cliente JavaScript do Microsoft Teams ](/javascript/api/overview/msteams-client) usando marcas de script. Depois que a página for carregada, faça uma chamada `app.initialize()`para, caso contrário, sua página não será exibida.

* Para que a autenticação funcione em clientes móveis, você deve atualizar para o SDK JavaScript 1.4.1 do Teams e posterior.

* Se você optar por fazer com que seu canal ou guia de grupo apareça no cliente móvel do Teams, a configuração de `setConfig()` deve ter um valor para a propriedade `websiteUrl`.

* A guia Microsoft Teams não dá suporte à capacidade de carregar sites da intranet que usam certificados autoassinados.

[!INCLUDE [sdk-include](~/includes/sdk-include.md)]

## <a name="tools-to-build-tabs"></a>Ferramentas para criar guias

| &nbsp; | Instalar | Para usar... |
| --- | --- | --- |
| **Required** | &nbsp; | &nbsp; |
| &nbsp; | [Node.js](https://nodejs.org/en/download/) | Ambiente de runtime do JavaScript de back-end. Use a versão mais recente do v16 LTS.|
| &nbsp; | [Microsoft Edge](https://www.microsoft.com/edge) (recomendado) ou [Google Chrome](https://www.google.com/chrome/) | Um navegador com ferramentas de desenvolvedor. |
| &nbsp; | [Visual Studio Code](https://code.visualstudio.com/download) | Ambientes de compilação JavaScript, TypeScript ou Estrutura do SharePoint (SPFx). |
| &nbsp; | [Visual Studio 2019](https://visualstudio.com/download), **ASP.NET e desenvolvimento Web** ou carga de trabalho de **desenvolvimento de Plataforma Cruzada .NET Core** | .NET. Você pode instalar a edição gratuita da comunidade do Visual Studio 2019. |
| &nbsp; | [Git](https://git-scm.com/downloads) | Git para usar o repositório de aplicativos de exemplo do GitHub. |
| &nbsp; | [Microsoft Teams](https://www.microsoft.com/en-us/microsoft-teams/download-app) | O Microsoft Teams para colaborar com todos com quem você trabalha por meio de aplicativos para chats, reuniões, chamadas - tudo em um só lugar. |
| &nbsp; | [ngrok](https://ngrok.com/download) | Ngrok é uma ferramenta de software de proxy reverso. A Ngrok cria um túnel para os pontos de extremidade HTTPS disponíveis publicamente do seu servidor Web em execução local. Os pontos de extremidade da Web do seu servidor estão disponíveis durante a sessão atual no seu computador. Quando o computador é desligado ou entra no modo de suspensão, o serviço não está mais disponível. |
| &nbsp; | [Portal do Desenvolvedor do Teams](https://dev.teams.microsoft.com/) | Portal baseado na Web para configurar, gerenciar e distribuir seu aplicativo do Teams, inclusive para sua organização ou para a loja do Teams. |

### <a name="build-your-teams-tab"></a>Criar sua guia do Teams

Agora vamos criar sua guia. Mas primeiro selecione sua escolha de guia para compilar:

> [!div class="nextstepaction"]
> [Construir uma guia pessoal](~/tabs/how-to/create-personal-tab.md)
> [!div class="nextstepaction"]
> [Criar uma guia de grupo ou canal](~/tabs/how-to/create-channel-group-tab.md)

## <a name="see-also"></a>Confira também

* [Guias do Teams](~/tabs/what-are-tabs.md)
* [Guias em dispositivos móveis](~/tabs/design/tabs-mobile.md)
