---
title: Estender o aplicativo do Microsoft Teams com uma guia personalizada
author: laujan
description: Um guia para criar uma guia
keywords: guias do teams com o canal de grupo configurável
ms.topic: conceptual
ms.author: ''
ms.openlocfilehash: 9f12f9eb39e4dfac4d5b725638bdbd2d7c2b4de6
ms.sourcegitcommit: b8b06929981ebbeef4ae489f338271bf09d349a2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2020
ms.locfileid: "43537268"
---
# <a name="extend-your-teams-app-with-a-custom-tab"></a>Estender o aplicativo do Microsoft Teams com uma guia personalizada

As guias personalizadas permitem que você sirva o conteúdo da Web que hospeda para o canal, o chat de grupo e os usuários pessoais. Em um nível alto, você precisará concluir as etapas a seguir para criar uma guia:

1. Preparar seu ambiente de desenvolvimento.
1. Crie suas páginas.
1. Hospede seu serviço de aplicativo.
1. Crie seu pacote de aplicativos e carregue para o Microsoft Teams.

[!include[prepare environment](~/includes/prepare-environment.md)]

## <a name="create-your-pages"></a>Criar sua (s) página (s)

Se você apresentar sua guia no escopo pessoal ou de canal/grupo, ele será composto por uma ou mais páginas HTML que você hospeda. Guias com um escopo pessoal consistem em uma única página de conteúdo, enquanto guias com um escopo de canal ou grupo exigirão uma página de configuração que define a URL da página de conteúdo com base na entrada do usuário no momento da instalação.

Há três tipos de páginas de guia. Consulte a página de documentação correspondente para obter detalhes completos sobre como criá-los.

1. [Página de conteúdo](~/tabs/how-to/create-tab-pages/content-page.md), a página exibida em uma guia.
1. [Página de configuração](~/tabs/how-to/create-tab-pages/configuration-page.md), a página usada para definir ou atualizar a URL da página de conteúdo e adicioná-la a uma guia de canal/grupo.
1. [Página de remoção](~/tabs/how-to/create-tab-pages/removal-page.md), uma página opcional que é exibida quando uma guia canal/grupo é removida.

### <a name="tab-requirements"></a>Requisitos de guia

Seja qual for o tipo de página, você precisará aderir aos seguintes requisitos:

* Você deve permitir que as suas páginas sejam servidas em um IFrame, por meio de opções X-frame-frame e/ou de dados de resposta HTTP de política de segurança de conteúdo.
  * Definir cabeçalho:`Content-Security-Policy: frame-ancestors teams.microsoft.com *.teams.microsoft.com *.skype.com`        
  * Para compatibilidade com o Internet Explorer 11 `X-Content-Security-Policy` , configure também.    
  * Como alternativa, defina o `X-Frame-Options: ALLOW-FROM https://teams.microsoft.com/`cabeçalho. Esse cabeçalho é preterido, mas ainda respeitado pela maioria dos navegadores.
* Normalmente, como uma proteção contra o clique na tomada, as páginas de logon não são renderizadas em IFrames. Portanto, a lógica de autenticação precisa usar um método diferente de redirecionar (por exemplo, usar autenticação baseada em token ou baseada em cookies).

> [!NOTE]
> O Chrome 80, agendado para lançamento no início de 2020, apresenta novos valores de cookie e impõe políticas de cookies por padrão. É recomendável que você defina o uso pretendido para seus cookies, em vez de confiar no comportamento padrão do navegador. *Confira* o [atributo SameSite cookie (atualização 2020)](../../resources/samesite-cookie-update.md).

* Os navegadores aderem a uma restrição de política de mesma origem que impede que uma página da Web faça solicitações para um domínio diferente daquele que atuou em uma página da Web. No entanto, talvez seja necessário redirecionar a configuração ou a página de conteúdo para um outro domínio ou subdomínio. A lógica de navegação entre domínios deve permitir que o cliente do teams valide a origem em uma lista validDomains estática no manifesto do aplicativo ao carregar ou se comunicar com a guia.

* Para criar uma experiência perfeita, você deve estilizar suas guias com base no tema, design e intenção do cliente da equipe. Normalmente, as guias funcionam melhor quando são criadas para tratar de uma necessidade específica e se concentrar em um pequeno conjunto de tarefas ou em um subconjunto de dados relevante para o local do canal da guia.

* Dentro de sua página de conteúdo, adicione uma referência ao [SDK do cliente JavaScript do Microsoft Teams](/javascript/api/overview/msteams-client) usando marcas de script. Após a sua carga de página, faça uma `microsoftTeams.initialize()`chamada para. A página não será exibida se você não.

## <a name="host-your-app-service"></a>Hospedar o serviço de aplicativo

Seu conteúdo precisa ser hospedado em uma URL disponível publicamente disponível usando HTTPS. Para testes, você pode usar um proxy reverso, como o [ngrok](https://ngrok.com/), para expor sua porta local a uma URL voltada para a Internet.

## <a name="create-your-app-package-with-app-studio"></a>Criar seu pacote de aplicativos com o app Studio

Você pode usar o aplicativo App Studio no cliente Microsoft Teams para ajudar a criar seu manifesto de aplicativo. Se você não tiver o app Studio instalado no Teams, **Apps** ![selecione aplicativo](/microsoftteams/platform/assets/images/tab-images/storeApp.png) da loja de aplicativos no canto inferior esquerdo do aplicativo Teams e pesquise o app Studio. Depois de localizar o bloco, selecione-o e escolha instalar na caixa de diálogo janela pop-up.

1. Abrir o cliente do Microsoft Teams usando a [versão baseada na Web](https://teams.microsoft.com) permitirá inspecionar o código de front-end usando as [ferramentas de desenvolvedor](~/tabs/how-to/developer-tools.md)do navegador.
1. Abra o app Studio e selecione a guia **Editor do manifesto** .
1. Escolha o bloco **criar um novo aplicativo** .
1. Adicione os detalhes do aplicativo (consulte a [definição de esquema de manifesto](~/resources/schema/manifest-schema.md) para obter uma descrição completa de cada campo).
1. Na seção recursos, selecione **guias**.
    * Para obter uma guia pessoal, escolha *Adicionar uma guia pessoal* e selecione **Adicionar**. Você receberá uma janela de diálogo pop-up onde você pode adicionar os detalhes da guia.
    * Para uma guia canal/grupo, em *guia equipe* , selecione **Adicionar** e preencha os campos guia detalhes na janela pop-up da guia equipe. Certifique-se de que a *configuração pode atualizar? *Caixas de *chat* de equipe e grupo são verificadas e selecione **salvar**.
1. Na seção *domínios e permissões* , os *domínios do campo Tabs* devem conter sua URL de host ou de proxy reverso sem o prefixo HTTPS.
1. Na guia **Finish** => **teste de término e distribuição** , você pode **baixar** seu pacote de aplicativos, **instalar** o pacote em uma equipe ou **Enviar** para a loja de aplicativos do teams para aprovação. *Se você estiver usando um proxy reverso, receberá um aviso no campo **Descrição** à direita. O aviso pode ser ignorado durante o teste da guia*.

## <a name="create-your-app-package-manually"></a>Crie seu pacote de aplicativos manualmente

Como com as extensões de bots e mensagens, você atualiza o [manifesto do aplicativo](~/resources/schema/manifest-schema.md) de seu aplicativo para incluir as propriedades da guia. Essas propriedades controlam os escopos em que sua guia está disponível, as URLs a serem usadas e várias outras propriedades.

### <a name="personal-tabs"></a>Guias pessoais

O conteúdo exibido para guias pessoais é o mesmo para todos os usuários e é configurado na `staticTabs` matriz. Você pode declarar até dezesseis (16) Guias pessoais em um aplicativo.

|Nome| Tipo| Tamanho máximo | Obrigatório | Descrição|
|---|---|---|---|---|
|`entityId`|String|64 caracteres|✔|Um identificador exclusivo para a entidade que a guia exibe.|
|`name`|String|128 caracteres|✔|O nome de exibição da guia na interface de canal.|
|`contentUrl`|String|2048 caracteres|✔|A URL https://que aponta para a interface do usuário da entidade a ser exibida na tela do teams.|
|`websiteUrl`|String|2048 caracteres||A URL do https://para apontar para o modo de exibição de um usuário em um navegador.|
|`scopes`|Matriz de enumeração|1|✔|As guias estáticas oferecem `personal` suporte somente ao escopo, o que significa que ela pode ser configurada somente como parte de um aplicativo pessoal.|

#### <a name="simple-personal-tab-manifest-example"></a>Exemplo de manifesto de guia pessoal simples

O exemplo abaixo mostra apenas a `staticTabs` matriz de um manifesto de aplicativo.

```json
...
"staticTabs": [
    {
      "entityId": "idForPage",
      "name": "Display name for tab",
      "contentUrl": "https:// yourURL.com/content ",
      "websiteUrl": "https://yourURL.com/website",
      "scopes": [ "personal" ]
    }
...
```

### <a name="channelgroup-tabs"></a>Guias de canal/grupo

As guias canal/grupo são adicionadas `configurableTabs` à matriz. Você pode declarar apenas uma guia de canal/grupo na `configurableTabs` matriz.

|Nome| Tipo| Tamanho máximo | Obrigatório | Descrição|
|---|---|---|---|---|
|`configurationUrl`|String|2048 caracteres|✔|A URL do https://para a página de configuração.|
|`canUpdateConfiguration`|Booliano|||Um valor que indica se uma instância da configuração da guia pode ser atualizada pelo usuário após a criação. Será`true`|
|`scopes`|Matriz de enumeração|1|✔|As guias configuráveis dão `team` suporte `groupchat` somente a e os escopos. |

#### <a name="simple-channelgroup-tab-manifest-example"></a>Exemplo de manifesto de guia de canal/grupo simples

O exemplo abaixo mostra apenas a `configurableTabs` matriz de um manifesto de aplicativo.

```json
...
"configurableTabs": [
    {
      "configurationUrl": "https://yourURL.com/configure",
      "canUpdateConfiguration": true,
      "scopes": [ "team", "groupchat" ]
    }
...
```

Depois de concluir o seu `manifest.json` pacote, em uma pasta zip, juntamente com seus dois ícones necessários.

### <a name="upload-app-package-directly-to-a-team"></a>Carregar o pacote de aplicativos diretamente para uma equipe

1. Abra o cliente do Microsoft Teams. Se você usar a [versão baseada na Web](https://teams.microsoft.com) , poderá inspecionar seu código de front-end usando as [ferramentas de desenvolvedor](~/tabs/how-to/developer-tools.md)do navegador.
1. No painel *YourTeams* à esquerda, selecione o `...` menu ao lado da equipe que você está usando para testar sua guia e escolha **Gerenciar equipe**.
1. No painel principal, selecione **aplicativos** na barra de guias e escolha **carregar um aplicativo personalizado** localizado no canto inferior direito da página.
1. Abra o diretório do projeto, navegue até a pasta **./Package** , selecione a pasta zip do pacote de aplicativos e escolha **abrir**. Sua guia será carregada no Microsoft Teams.

### <a name="view-your-tab-in-teams"></a>Exibir sua guia no Teams

1. Exibir sua guia pessoal:
    * Na barra de navegação localizada na extrema esquerda do cliente Teams, selecione o `...` menu e escolha seu aplicativo na lista.

1. Exiba a guia canal/Grupo:
    * Retorne à sua equipe, escolha o canal onde você deseja exibir a guia, selecione ➕ na barra de guias e escolha sua guia na galeria.
    * Siga as instruções para adicionar uma guia. Observe que há uma caixa de diálogo de configuração personalizada para a guia canal/grupo. Selecione **salvar** e sua guia será adicionada à barra de guias do canal.

## <a name="learn-more"></a>Saiba mais

* [Criar uma página de conteúdo para sua guia](~/tabs/how-to/create-tab-pages/content-page.md)
* [Criar uma página de configuração para sua guia](~/tabs/how-to/create-tab-pages/configuration-page.md)
* [Atualizar ou remover uma guia](~/tabs/how-to/create-tab-pages/removal-page.md)
