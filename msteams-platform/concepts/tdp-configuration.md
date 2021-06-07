---
title: Configuração de aplicativo no Portal do Desenvolvedor
description: Saiba como configurar e gerenciar seus aplicativos usando o Portal do Desenvolvedor para Microsoft Teams
keywords: iniciando equipes do portal do desenvolvedor
localization_priority: Normal
ms.topic: conceptual
ms.openlocfilehash: ce290bd7daa46467be279aae7c608321e75e2d57
ms.sourcegitcommit: 25539046d408c4270b988fd826d7cf1275f4b9dd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2021
ms.locfileid: "52763121"
---
# <a name="app-configuration"></a><span data-ttu-id="cf342-104">Configuração do aplicativo</span><span class="sxs-lookup"><span data-stu-id="cf342-104">App configuration</span></span>

<span data-ttu-id="cf342-105">A parte mais significativa de um pacote Microsoft Teams aplicativo é sua manifest.jsno arquivo.</span><span class="sxs-lookup"><span data-stu-id="cf342-105">The most significant part of a Microsoft Teams app package is its manifest.json file.</span></span> <span data-ttu-id="cf342-106">Esse arquivo deve estar em conformidade com [o esquema Teams App](~/resources/schema/manifest-schema.md).</span><span class="sxs-lookup"><span data-stu-id="cf342-106">This file must conform to the [Teams App schema](~/resources/schema/manifest-schema.md).</span></span> <span data-ttu-id="cf342-107">O manifest.jsno arquivo contém metadados, o que permite Teams apresentar corretamente seu aplicativo aos usuários.</span><span class="sxs-lookup"><span data-stu-id="cf342-107">The manifest.json file contains metadata, which allows Teams to correctly present your app to users.</span></span>

<span data-ttu-id="cf342-108">Você pode executar as seguintes ações na seção **Configurar** do Portal do Desenvolvedor:</span><span class="sxs-lookup"><span data-stu-id="cf342-108">You can perform the following actions in the **Configure** section of the Developer Portal:</span></span>

* <span data-ttu-id="cf342-109">Crie um pacote de aplicativo facilmente.</span><span class="sxs-lookup"><span data-stu-id="cf342-109">Create an app package easily.</span></span>
* <span data-ttu-id="cf342-110">Descreva o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="cf342-110">Describe the app.</span></span>
* <span data-ttu-id="cf342-111">Upload seus ícones.</span><span class="sxs-lookup"><span data-stu-id="cf342-111">Upload your icons.</span></span>
* <span data-ttu-id="cf342-112">Produza um .zip para facilitar a distribuição.</span><span class="sxs-lookup"><span data-stu-id="cf342-112">Produce a .zip file for easy distribution.</span></span>

> [!NOTE]
> <span data-ttu-id="cf342-113">O Portal do Desenvolvedor não produz código funcional para seu aplicativo ou hospeda seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="cf342-113">Developer Portal does not produce functional code for your app, or host your app.</span></span> <span data-ttu-id="cf342-114">Seu aplicativo já deve estar hospedado e sendo executado na URL listada no manifesto para que o processo de carregamento do aplicativo resulte em um aplicativo funcional.</span><span class="sxs-lookup"><span data-stu-id="cf342-114">Your app must already be hosted and running at the URL listed in the manifest for the app upload process to result in a working app.</span></span>

:::image type="content" source="~/assets/images/tdp/tdp_configure_1.png" alt-text="Captura de tela mostrando a página Configurar Teams Portal do Desenvolvedor.":::

## <a name="basic-information-and-branding"></a><span data-ttu-id="cf342-116">Informações básicas e identidade visual</span><span class="sxs-lookup"><span data-stu-id="cf342-116">Basic information and Branding</span></span>

<span data-ttu-id="cf342-117">As **seções Informações** básicas e **Identidade** Visual definem a descrição de alto nível do aplicativo que você está criando.</span><span class="sxs-lookup"><span data-stu-id="cf342-117">The **Basic information** and **Branding** sections define the high-level description of the app you are making.</span></span> <span data-ttu-id="cf342-118">Isso inclui o nome, a descrição e a identidade visual do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="cf342-118">This includes the app’s name, description, and visual branding.</span></span> <span data-ttu-id="cf342-119">As informações nesta seção serão usadas na listagem de Teams do aplicativo e no diálogo de instalação do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="cf342-119">The information in this section will be used in your app's Teams store listing and app installation dialogue.</span></span>

## <a name="capabilities"></a><span data-ttu-id="cf342-120">Recursos</span><span class="sxs-lookup"><span data-stu-id="cf342-120">Capabilities</span></span>

<span data-ttu-id="cf342-121">A **seção Recursos** da Configuração tem os detalhes de recursos do aplicativo listados.</span><span class="sxs-lookup"><span data-stu-id="cf342-121">The **Capabilities** section of Configuration has the app's capabilities details listed.</span></span>

> [!NOTE]
> <span data-ttu-id="cf342-122">O recurso de personalização do aplicativo está disponível apenas na visualização do desenvolvedor.</span><span class="sxs-lookup"><span data-stu-id="cf342-122">The app customization feature is currently available in the developer preview only.</span></span>
> 
> <span data-ttu-id="cf342-123">Como prática prática prática, você deve fornecer diretrizes de personalização para usuários de aplicativos e clientes a seguir ao personalizar seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="cf342-123">As a best practice, you must provide customization guidelines for app users and customers to follow when customizing your app.</span></span> <span data-ttu-id="cf342-124">Para obter mais informações, consulte [personalizar aplicativos em Microsoft Teams](/MicrosoftTeams/customize-apps).</span><span class="sxs-lookup"><span data-stu-id="cf342-124">For more information, see [customize apps in Microsoft Teams](/MicrosoftTeams/customize-apps).</span></span>

<span data-ttu-id="cf342-125">A seguir estão os recursos:</span><span class="sxs-lookup"><span data-stu-id="cf342-125">Following are the capabilities:</span></span>

:::image type="content" source="~/assets/images/tdp/tdp_capabilities.png" alt-text="Captura de tela mostrando a página Configurar Teams Portal do Desenvolvedor.":::

* <span data-ttu-id="cf342-127">**Aplicativo pessoal**</span><span class="sxs-lookup"><span data-stu-id="cf342-127">**Personal app**</span></span> 

  <span data-ttu-id="cf342-128">Esta seção permite definir um conjunto de guias que são apresentadas por padrão na experiência do aplicativo pessoal, ou seja, a experiência que um usuário tem com seu aplicativo fora do contexto de uma equipe ou canal.</span><span class="sxs-lookup"><span data-stu-id="cf342-128">This section lets you define a set of tabs that are presented by default in the personal app experience, that is, the experience a user has with your app outside the context of a team or channel.</span></span> <span data-ttu-id="cf342-129">Nesta seção, forneça os seguintes detalhes:</span><span class="sxs-lookup"><span data-stu-id="cf342-129">In this section, provide the following details:</span></span>

  * <span data-ttu-id="cf342-130">O nome da guia.</span><span class="sxs-lookup"><span data-stu-id="cf342-130">The tab name.</span></span>
  * <span data-ttu-id="cf342-131">Um identificador exclusivo.</span><span class="sxs-lookup"><span data-stu-id="cf342-131">A unique identifier.</span></span>
  * <span data-ttu-id="cf342-132">A URL que aponta para a interface do usuário a ser exibida Teams.</span><span class="sxs-lookup"><span data-stu-id="cf342-132">The URL that points to the UI to be displayed in Teams.</span></span>
  * <span data-ttu-id="cf342-133">A URL a ser usada se um usuário optar por exibir a guia em um navegador.</span><span class="sxs-lookup"><span data-stu-id="cf342-133">The URL to use if a user opts to view the tab in a browser.</span></span> <span data-ttu-id="cf342-134">Esta é uma informação opcional.</span><span class="sxs-lookup"><span data-stu-id="cf342-134">This is an optional information.</span></span>
  * <span data-ttu-id="cf342-135">Quaisquer domínios adicionais dos quais a guia espera carregar ou vincular.</span><span class="sxs-lookup"><span data-stu-id="cf342-135">Any additional domains from which the tab expects to load from or link to.</span></span>

* <span data-ttu-id="cf342-136">**Aplicativo de grupo e canal**</span><span class="sxs-lookup"><span data-stu-id="cf342-136">**Group and channel app**</span></span>

  <span data-ttu-id="cf342-137">Uma Teams se torna parte de um canal e fornece acesso rápido às informações e recursos da equipe.</span><span class="sxs-lookup"><span data-stu-id="cf342-137">A Teams tab becomes part of a channel and provides quick access to team information and resources.</span></span> <span data-ttu-id="cf342-138">Por exemplo, a guia Planner para um canal contém um único plano, Power BI guia mapeia para um relatório específico.</span><span class="sxs-lookup"><span data-stu-id="cf342-138">For example, the Planner tab for a channel contains a single plan, the Power BI tab maps to a specific report.</span></span> <span data-ttu-id="cf342-139">Os usuários podem fazer uma busca detalhada pelo contexto relevante, mas eles não devem ser capazes de navegar fora da guia. Por exemplo, a guia Power BI não habilita a navegação para outros relatórios do Power BI, mas habilita o botão **Ir para o site** que inicia o relatório no site principal do Power BI.</span><span class="sxs-lookup"><span data-stu-id="cf342-139">Users can drill down to the relevant context, but they should not be able to navigate outside the tab. The Power BI tab, for instance, doesn't enable navigation to other Power BI reports, but it does enable the **Go to website** button that launches the report in the main Power BI website.</span></span>

    > [!NOTE]
    > <span data-ttu-id="cf342-140">Para as guias de equipe, você deve fornecer uma URL de Configuração para apresentar opções e coletar informações, que o ajudarão a personalizar o conteúdo e a experiência de sua guia. Esta página HTML iframed é exibida quando um usuário adiciona a guia pela primeira vez a um canal.</span><span class="sxs-lookup"><span data-stu-id="cf342-140">For team tabs, you must provide a Configuration URL to present options and gather information, that would help you to customize the content and experience of your tab. This iframed HTML page is displayed when a user first adds the tab to a channel.</span></span>
    > <span data-ttu-id="cf342-141">Você também deve fornecer outros domínios a partir dos quais a guia espera carregar ou se vincular. </span><span class="sxs-lookup"><span data-stu-id="cf342-141">You must also provide any additional domains that the tab expects to load from or link to.</span></span>

* <span data-ttu-id="cf342-142">**Bot**</span><span class="sxs-lookup"><span data-stu-id="cf342-142">**Bot**</span></span>

  <span data-ttu-id="cf342-143">Esta seção permite que você adicione um [bot de conversação](~/bots/what-are-bots.md) ao seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="cf342-143">This section allows you to add a [conversational bot](~/bots/what-are-bots.md) to your app.</span></span> <span data-ttu-id="cf342-144">Se você já tiver um bot registrado com o Bot Framework, poderá adicionar esse bot clicando em **Configurar** e fornecendo o nome do bot, a ID do Bot Framework e definindo os escopos em que o bot funcionará.</span><span class="sxs-lookup"><span data-stu-id="cf342-144">If you already have a bot registered with Bot Framework, you can add that bot by clicking **Set Up** and supplying the bot's name, Bot Framework ID, and defining the scopes in which the bot will work.</span></span>

  <span data-ttu-id="cf342-145">Se você ainda não registrou o bot com a Estrutura de Bot, clique **em Registrar** para criar um novo.</span><span class="sxs-lookup"><span data-stu-id="cf342-145">If you have not registered the bot with the Bot Framework yet, click **Register** to create a new one.</span></span> <span data-ttu-id="cf342-146">Depois de registrar seu bot, volte para esta seção do Editor de Manifesto para inserir seu nome e a ID da Estrutura de Bot.</span><span class="sxs-lookup"><span data-stu-id="cf342-146">After you have registered your bot, come back to this section of the Manifest Editor to enter its name and Bot Framework ID.</span></span>

  <span data-ttu-id="cf342-147">Depois de fornecer as informações do bot, agora você pode definir opcionalmente uma lista de comandos que seu bot pode sugerir aos usuários.</span><span class="sxs-lookup"><span data-stu-id="cf342-147">After you have supplied your bot's information, you can now optionally define a list of commands that your bot can suggest to users.</span></span> <span data-ttu-id="cf342-148">Adicione o nome do comando, uma descrição do comando que indica sua sintaxe e argumentos, e o(s) escopo(s) ao qual este comando deve ser aplicado.</span><span class="sxs-lookup"><span data-stu-id="cf342-148">Add the name of the command, a description of the command which indicates its syntax and arguments, and the scope(s) to which this command should apply.</span></span>

  <span data-ttu-id="cf342-149">Observe que se você tiver definido seu bot para dar suporte apenas a um escopo, os comandos especificados para o escopo sem suporte serão ignorados.</span><span class="sxs-lookup"><span data-stu-id="cf342-149">Note that if you have defined your bot to only support one scope, commands specified for the unsupported scope will be ignored.</span></span> <span data-ttu-id="cf342-150">Você pode editar os escopos que seu bot oferece suporte a qualquer momento.</span><span class="sxs-lookup"><span data-stu-id="cf342-150">You can edit the scopes your bot supports at any time.</span></span>

* <span data-ttu-id="cf342-151">**Connector**</span><span class="sxs-lookup"><span data-stu-id="cf342-151">**Connector**</span></span>

  <span data-ttu-id="cf342-152">Esta seção permite adicionar um conector ao aplicativo.</span><span class="sxs-lookup"><span data-stu-id="cf342-152">This section allows you to add a connector to your app.</span></span> <span data-ttu-id="cf342-153">Se você já tiver registrado um conector Office 365, selecione **Configurar** e insira o nome e a ID do conector.</span><span class="sxs-lookup"><span data-stu-id="cf342-153">If you already have registered an Office 365 connector, select **Set up** and enter the name and ID of the connector.</span></span> <span data-ttu-id="cf342-154">Se quiser um novo conector clique em **Registrar** para ser levado até o Painel do Desenvolvedor do Conector em seu navegador.</span><span class="sxs-lookup"><span data-stu-id="cf342-154">If you want a new connector click **Register** to be taken to the Connector Developer Dashboard in your browser.</span></span>

  > [!NOTE]
  > <span data-ttu-id="cf342-155">A personalização do aplicativo permite que os administradores alterem a aparência dos aplicativos carregados por meio de bots, extensões de mensagens, guias e conectores.</span><span class="sxs-lookup"><span data-stu-id="cf342-155">App customization enables admins to change the look-and-feel of the apps loaded through bots, messaging extensions, tabs, and connectors.</span></span> <span data-ttu-id="cf342-156">Por exemplo, se o administrador Teams personalizar o nome de um aplicativo de até , o aplicativo aparecerá com o novo `Contoso` `Contoso Agent` nome para os `Contoso Agent` usuários.</span><span class="sxs-lookup"><span data-stu-id="cf342-156">For example, if the Teams admin customizes the name of an app from `Contoso` to `Contoso Agent`, then the app will appear with the new name `Contoso Agent` to the users.</span></span> <span data-ttu-id="cf342-157">No entanto, ao adicionar um conector a um chat, na lista, os conectores ainda mostrarão o nome do aplicativo como `Contoso` .</span><span class="sxs-lookup"><span data-stu-id="cf342-157">However, while adding a connector to a chat, in the list, the connectors will still show the name of the app as `Contoso`.</span></span>

* <span data-ttu-id="cf342-158">**Extensões de Mensagens**</span><span class="sxs-lookup"><span data-stu-id="cf342-158">**Messaging Extensions**</span></span>

  <span data-ttu-id="cf342-159">[As extensões de mensagens](~/messaging-extensions/what-are-messaging-extensions.md) são uma maneira eficiente para os usuários se envolverem com seu aplicativo no Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="cf342-159">[Messaging extensions](~/messaging-extensions/what-are-messaging-extensions.md) are a powerful way for users to engage with your app within Microsoft Teams.</span></span> <span data-ttu-id="cf342-160">Os usuários podem consultar informações do seu serviço e postar essas informações na forma de cartões, bem no canal ou na conversa de chat.</span><span class="sxs-lookup"><span data-stu-id="cf342-160">Users can query for information from your service and post that information in the form of cards, right into the channel or chat conversation.</span></span>

  <span data-ttu-id="cf342-161">As extensões de mensagens são da plataforma Bot Framework e exigem que um bot configurado funcione.</span><span class="sxs-lookup"><span data-stu-id="cf342-161">Messaging extensions are powered by Bot Framework bots, so they require a configured bot to operate.</span></span> <span data-ttu-id="cf342-162">Se você tiver o nome e a ID do Bot Framework do bot que você gostaria que guiasse a extensão de mensagem, insira-os.</span><span class="sxs-lookup"><span data-stu-id="cf342-162">If you have the name and Bot Framework ID of the bot you would like to power the messaging extension, enter it.</span></span> <span data-ttu-id="cf342-163">Caso contrário, clique em *Registrar* para criar um registro e insira as informações posteriormente.</span><span class="sxs-lookup"><span data-stu-id="cf342-163">Otherwise, click *Register* to create one and enter the information afterward.</span></span> <span data-ttu-id="cf342-164">Selecione se a configuração de uma extensão de mensagens pode ser atualizada pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="cf342-164">Select whether the configuration of a messaging extension can be updated by the user.</span></span>

  <span data-ttu-id="cf342-165">Depois de configurar o bot subjacente, defina os comandos e parâmetros que a extensão de mensagens pode aceitar.</span><span class="sxs-lookup"><span data-stu-id="cf342-165">After you have the underlying bot configured, define the commands and parameters which the messaging extension can accept.</span></span>

  <span data-ttu-id="cf342-166">Cada comando requer um título e uma ID.</span><span class="sxs-lookup"><span data-stu-id="cf342-166">Each command requires a title and an ID.</span></span> <span data-ttu-id="cf342-167">O comando pode conter, opcionalmente, uma descrição para o usuário.</span><span class="sxs-lookup"><span data-stu-id="cf342-167">The command can optionally contain a description for the user.</span></span> <span data-ttu-id="cf342-168">Cada comando pode dar suporte a até cinco parâmetros, cada um deles requer o seguinte:</span><span class="sxs-lookup"><span data-stu-id="cf342-168">Each command can support up to five parameters, each of which requires the following:</span></span>

  * <span data-ttu-id="cf342-169">O nome do parâmetro como ele aparece no cliente Teams e está incluído na solicitação do usuário.</span><span class="sxs-lookup"><span data-stu-id="cf342-169">The name of the parameter as it appears in the Teams client and is included in the user request.</span></span>
  * <span data-ttu-id="cf342-170">Um título amigável.</span><span class="sxs-lookup"><span data-stu-id="cf342-170">A user-friendly title.</span></span>
  * <span data-ttu-id="cf342-171">Uma descrição opcional.</span><span class="sxs-lookup"><span data-stu-id="cf342-171">An optional description.</span></span>

  > [!NOTE]
  > <span data-ttu-id="cf342-172">Para criar extensão de mensagens usando o app studio, consulte [create messaging extension using app studio](~/resources/create-messaging-extension-using-appstudio.md).</span><span class="sxs-lookup"><span data-stu-id="cf342-172">To create messaging extension using app studio, see [create messaging extension using app studio](~/resources/create-messaging-extension-using-appstudio.md).</span></span>

* <span data-ttu-id="cf342-173">**Extensão de reunião**</span><span class="sxs-lookup"><span data-stu-id="cf342-173">**Meeting extension**</span></span>

  <span data-ttu-id="cf342-174">TODO: Rajesh R.</span><span class="sxs-lookup"><span data-stu-id="cf342-174">//TODO: Rajesh R.</span></span>

* <span data-ttu-id="cf342-175">**Cena**</span><span class="sxs-lookup"><span data-stu-id="cf342-175">**Scene**</span></span>

  <span data-ttu-id="cf342-176">Cenas no Modo Juntos é um artefato criado pelo desenvolvedor de cena usando o estúdio do Microsoft Scene que reúne as pessoas junto com seu fluxo de vídeo em uma configuração criativa como concebida pelo criador da cena.</span><span class="sxs-lookup"><span data-stu-id="cf342-176">Scenes in Together Mode is an artifact created by the scene developer using the Microsoft Scene studio that brings people together along with their video stream in a creative setting as conceived by the scene creator.</span></span> <span data-ttu-id="cf342-177">Em uma configuração de cena concebida, os participantes têm assentos designados com fluxos de vídeo renderizados nesses bancos.</span><span class="sxs-lookup"><span data-stu-id="cf342-177">In a conceived scene setting, participants have designated seats with video streams rendered in those seats.</span></span> <span data-ttu-id="cf342-178">Para obter mais informações, [consulte Teams Modo Juntos](~/apps-in-teams-meetings/teams-together-mode.md).</span><span class="sxs-lookup"><span data-stu-id="cf342-178">For more information, see [Teams Together Mode](~/apps-in-teams-meetings/teams-together-mode.md).</span></span>

## <a name="permissions"></a><span data-ttu-id="cf342-179">Permissões</span><span class="sxs-lookup"><span data-stu-id="cf342-179">Permissions</span></span>

<span data-ttu-id="cf342-180">Você pode enriquecer seu Teams com recursos de dispositivo nativos, como câmera, microfone e local.</span><span class="sxs-lookup"><span data-stu-id="cf342-180">You can enrich your Teams app with native device capabilities, such as camera, microphone, and location.</span></span>

## <a name="languages"></a><span data-ttu-id="cf342-181">Idiomas</span><span class="sxs-lookup"><span data-stu-id="cf342-181">Languages</span></span>

<span data-ttu-id="cf342-182">Configurar ou alterar os idiomas que seu aplicativo oferece suporte.</span><span class="sxs-lookup"><span data-stu-id="cf342-182">Set up or change the languages that your app supports.</span></span>

## <a name="single-sign-on"></a><span data-ttu-id="cf342-183">Logon Único</span><span class="sxs-lookup"><span data-stu-id="cf342-183">Single Sign-On</span></span>

<span data-ttu-id="cf342-184">Configure seu aplicativo para autenticar usuários com SSO (login único).</span><span class="sxs-lookup"><span data-stu-id="cf342-184">Configure your app to authenticate users with single sign-on (SSO).</span></span>

## <a name="domains"></a><span data-ttu-id="cf342-185">Domínios</span><span class="sxs-lookup"><span data-stu-id="cf342-185">Domains</span></span>

<span data-ttu-id="cf342-186">Uma lista de domínios válidos para sites que o aplicativo espera carregar no Teams cliente.</span><span class="sxs-lookup"><span data-stu-id="cf342-186">A list of valid domains for websites the app expects to load within the Teams client.</span></span> <span data-ttu-id="cf342-187">Listagem de domínio pode incluir caracteres curinga, por exemplo, `*.example.com` .</span><span class="sxs-lookup"><span data-stu-id="cf342-187">Domain listings can include wildcards, for example, `*.example.com`.</span></span> <span data-ttu-id="cf342-188">Isso corresponde a exatamente um segmento do domínio; se você precisar corresponder, `a.b.example.com` use `*.*.example.com` .</span><span class="sxs-lookup"><span data-stu-id="cf342-188">This matches exactly one segment of the domain; if you need to match `a.b.example.com` then use `*.*.example.com`.</span></span> <span data-ttu-id="cf342-189">Se a configuração de tabulação ou a interface do usuário de conteúdo precisar navegar para qualquer outro domínio além do uso para configuração de tabulação, esse domínio deve ser especificado aqui.</span><span class="sxs-lookup"><span data-stu-id="cf342-189">If your tab configuration or content UI needs to navigate to any other domain besides the one use for tab configuration, that domain must be specified here.</span></span>

<span data-ttu-id="cf342-190">Não é necessário incluir os domínios dos provedores de identidade que você deseja suportar em seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="cf342-190">It is not necessary to include the domains of the identity providers you want to support in your app.</span></span> <span data-ttu-id="cf342-191">Por exemplo, para autenticar usando uma ID do Google, é necessário redirecionar para accounts.google.com, no entanto, você não deve incluir accounts.google.com em `validDomains[]` .</span><span class="sxs-lookup"><span data-stu-id="cf342-191">For example, to authenticate using a Google ID, it is required to redirect to accounts.google.com, however, you must not include accounts.google.com in `validDomains[]`.</span></span>

<span data-ttu-id="cf342-192">Teams aplicativos que exigem que suas próprias URLs do sharepoint funcionem bem, inclui "{teamsitedomain}" em sua lista de domínios válida.</span><span class="sxs-lookup"><span data-stu-id="cf342-192">Teams apps that require their own sharepoint URLs to function well, includes "{teamsitedomain}" in their valid domain list.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="cf342-193">Não adicione domínios que estão fora do seu controle, diretamente ou por meio de caracteres curinga.</span><span class="sxs-lookup"><span data-stu-id="cf342-193">Do not add domains that are outside your control, either directly or through wildcards.</span></span> <span data-ttu-id="cf342-194">Por exemplo, `yourapp.onmicrosoft.com` é válido, no entanto, `*.onmicrosoft.com` não é válido.</span><span class="sxs-lookup"><span data-stu-id="cf342-194">For example, `yourapp.onmicrosoft.com` is valid, however, `*.onmicrosoft.com` is not valid.</span></span>

<span data-ttu-id="cf342-195">O objeto é uma matriz com todos os elementos do tipo `string` .</span><span class="sxs-lookup"><span data-stu-id="cf342-195">The object is an array with all elements of the type `string`.</span></span>

## <a name="advanced"></a><span data-ttu-id="cf342-196">Advanced</span><span class="sxs-lookup"><span data-stu-id="cf342-196">Advanced</span></span>
<span data-ttu-id="cf342-197">Todo por Karthig</span><span class="sxs-lookup"><span data-stu-id="cf342-197">//Todo by Karthig</span></span>

### <a name="app-content"></a><span data-ttu-id="cf342-198">Conteúdo do aplicativo</span><span class="sxs-lookup"><span data-stu-id="cf342-198">App content</span></span>
<span data-ttu-id="cf342-199">Todo por Karthig</span><span class="sxs-lookup"><span data-stu-id="cf342-199">//Todo by Karthig</span></span>

### <a name="first-party-settings"></a><span data-ttu-id="cf342-200">Configurações de primeira parte</span><span class="sxs-lookup"><span data-stu-id="cf342-200">First party settings</span></span>
<span data-ttu-id="cf342-201">Todo por Karthig</span><span class="sxs-lookup"><span data-stu-id="cf342-201">//Todo by Karthig</span></span>

## <a name="see-also"></a><span data-ttu-id="cf342-202">Confira também</span><span class="sxs-lookup"><span data-stu-id="cf342-202">See also</span></span>

* [<span data-ttu-id="cf342-203">Visão geral do Teams Portal do Desenvolvedor</span><span class="sxs-lookup"><span data-stu-id="cf342-203">Overview of Teams Developer Portal</span></span>](~/concepts/build-and-test/teams-developer-portal.md)
* [<span data-ttu-id="cf342-204">Distribuir Teams Portal do Desenvolvedor</span><span class="sxs-lookup"><span data-stu-id="cf342-204">Distribute Teams Developer Portal</span></span>](~/concepts/tdp-distribute.md)
* [<span data-ttu-id="cf342-205">Ferramentas no Teams Portal do Desenvolvedor</span><span class="sxs-lookup"><span data-stu-id="cf342-205">Tools in Teams Developer Portal</span></span>](~/concepts/tdp-tools.md)