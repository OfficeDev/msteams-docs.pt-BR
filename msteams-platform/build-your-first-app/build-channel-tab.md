---
author: heath-hamilton
description: Saiba como criar uma guia de canal para seu primeiro aplicativo do Microsoft Teams.
ms.author: lajanuar
ms.date: 09/22/2020
ms.topic: tutorial
title: Criar uma guia de canal do teams
ms.openlocfilehash: d0846c3af23fd9df6013f989e9f455f711d05a5f
ms.sourcegitcommit: 1aa0b172931d0f81db346452788c41dc4a6717b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/22/2020
ms.locfileid: "48210090"
---
# <a name="build-a-teams-channel-tab"></a><span data-ttu-id="95058-103">Criar uma guia de canal do teams</span><span class="sxs-lookup"><span data-stu-id="95058-103">Build a Teams channel tab</span></span>

<span data-ttu-id="95058-104">Neste tutorial, você criará uma *guia canal*básico, uma página de conteúdo de tela inteira para um canal de equipe ou chat.</span><span class="sxs-lookup"><span data-stu-id="95058-104">In this tutorial, you'll build a basic *channel tab*, a full-screen content page for a team channel or chat.</span></span> <span data-ttu-id="95058-105">Ao contrário de uma guia pessoal, os usuários podem configurar alguns aspectos de uma guia de canal (por exemplo, renomear a guia de forma que ela seja significativa para o canal).</span><span class="sxs-lookup"><span data-stu-id="95058-105">Unlike a personal tab, users can configure some aspects of a channel tab (for example, rename the tab so it's meaningful to their channel).</span></span>

## <a name="before-you-begin"></a><span data-ttu-id="95058-106">Antes de começar</span><span class="sxs-lookup"><span data-stu-id="95058-106">Before you begin</span></span>

<span data-ttu-id="95058-107">Você precisa de um aplicativo básico em execução para começar.</span><span class="sxs-lookup"><span data-stu-id="95058-107">You need a basic running app to get started.</span></span> <span data-ttu-id="95058-108">Se você não tiver um, siga as [instruções Build e Run Your Teams First app](../build-your-first-app/build-and-run.md).</span><span class="sxs-lookup"><span data-stu-id="95058-108">If you don't have one, follow the [build and run your Teams first app instructions](../build-your-first-app/build-and-run.md).</span></span> <span data-ttu-id="95058-109">Ao criar seu projeto de aplicativo, escolha somente a opção de **guia canal ou grupo Teams** .</span><span class="sxs-lookup"><span data-stu-id="95058-109">When you create your app project, choose only the **Group or Teams channel tab** option.</span></span>

## <a name="your-assignment"></a><span data-ttu-id="95058-110">Sua atribuição</span><span class="sxs-lookup"><span data-stu-id="95058-110">Your assignment</span></span>

<span data-ttu-id="95058-111">Não há muito tempo, sua organização criou uma guia do teams com informações sobre como entrar em contato com funções importantes (Help Desk, HR, etc.).</span><span class="sxs-lookup"><span data-stu-id="95058-111">Not long ago, your organization created a Teams tab with information on how to contact important functions (help desk, HR, etc.).</span></span> <span data-ttu-id="95058-112">No entanto, como a guia era escopoda somente para uso pessoal, cada usuário deve instalar a guia para vê-la e a adoção é menor do que o esperado.</span><span class="sxs-lookup"><span data-stu-id="95058-112">However, since the tab was scoped only for personal use, each user must install the tab to see it and adoption is lower than expected.</span></span> <span data-ttu-id="95058-113">Em outras palavras, muitos trabalhadores ainda não sabem como alcançar o suporte técnico.</span><span class="sxs-lookup"><span data-stu-id="95058-113">In other words, too many workers still don't know how to reach the help desk.</span></span>

<span data-ttu-id="95058-114">Você pode facilitar a localização dessas informações criando uma guia de canal, o que removerá o ônus de exigir que todos instalem um aplicativo.</span><span class="sxs-lookup"><span data-stu-id="95058-114">You can make this information easier to find by building a channel tab, which will remove the burden of requiring everyone to install an app.</span></span> <span data-ttu-id="95058-115">Em vez disso, um usuário pode instalar a guia em um canal ou chat para o benefício de um grupo inteiro.</span><span class="sxs-lookup"><span data-stu-id="95058-115">Instead, one user can install the tab in a channel or chat for the benefit of an entire group.</span></span>

## <a name="what-youll-learn"></a><span data-ttu-id="95058-116">O que você aprenderá</span><span class="sxs-lookup"><span data-stu-id="95058-116">What you'll learn</span></span>

> [!div class="checklist"]
>
> * <span data-ttu-id="95058-117">Identificar algumas das propriedades de manifesto de aplicativo e scaffolding relevantes para as guias de canal</span><span class="sxs-lookup"><span data-stu-id="95058-117">Identify some of the app manifest properties and scaffolding relevant to channel tabs</span></span>
> * <span data-ttu-id="95058-118">Criar conteúdo de guia</span><span class="sxs-lookup"><span data-stu-id="95058-118">Create tab content</span></span>
> * <span data-ttu-id="95058-119">Criar conteúdo para a página de configuração de uma guia</span><span class="sxs-lookup"><span data-stu-id="95058-119">Create content for a tab's configuration page</span></span>
> * <span data-ttu-id="95058-120">Permitir que uma guia seja configurada e instalada</span><span class="sxs-lookup"><span data-stu-id="95058-120">Allow a tab to be configured and installed</span></span>
> * <span data-ttu-id="95058-121">Fornecer um nome de guia sugerido</span><span class="sxs-lookup"><span data-stu-id="95058-121">Provide a suggested tab name</span></span>

## <a name="identify-relevant-app-project-components"></a><span data-ttu-id="95058-122">Identificar componentes de projeto de aplicativo relevantes</span><span class="sxs-lookup"><span data-stu-id="95058-122">Identify relevant app project components</span></span>

<span data-ttu-id="95058-123">Grande parte do manifesto do aplicativo e do scaffolding são configuradas automaticamente quando você cria seu projeto com o Teams Toolkit.</span><span class="sxs-lookup"><span data-stu-id="95058-123">Much of the app manifest and scaffolding are set up automatically when you create your project with the Teams Toolkit.</span></span> <span data-ttu-id="95058-124">Vamos examinar os principais componentes para criar uma guia canal.</span><span class="sxs-lookup"><span data-stu-id="95058-124">Let's look at the main components for building a channel tab.</span></span>

### <a name="app-manifest"></a><span data-ttu-id="95058-125">Manifesto do aplicativo</span><span class="sxs-lookup"><span data-stu-id="95058-125">App manifest</span></span>

<span data-ttu-id="95058-126">O trecho de código a seguir do manifesto de aplicativo mostra [`configurableTabs`](../resources/schema/manifest-schema.md#configurabletabs) , que inclui as propriedades e os valores padrão relevantes para as guias de canal.</span><span class="sxs-lookup"><span data-stu-id="95058-126">The following snippet from the app manifest shows [`configurableTabs`](../resources/schema/manifest-schema.md#configurabletabs), which includes the properties and default values relevant to channel tabs.</span></span>

```JSON
"configurableTabs": [
    {
        "configurationUrl": "{baseUrl0}/config",
        "canUpdateConfiguration": true,
        "scopes": [
            "team",
            "groupchat"
        ]
    }
],
```

* <span data-ttu-id="95058-127">`configurationUrl`: A URL do host para a página de configuração da guia (deve ser HTTPS).</span><span class="sxs-lookup"><span data-stu-id="95058-127">`configurationUrl`: The host URL for your tab configuration page (must be HTTPS).</span></span>
* <span data-ttu-id="95058-128">`canUpdateConfiguration`: Se definido como `true` , os usuários podem alterar as configurações de tabulação, renomear a guia ou removê-la de um canal ou chat.</span><span class="sxs-lookup"><span data-stu-id="95058-128">`canUpdateConfiguration`: If set to `true`, users can change tab settings, rename the tab, or remove it from a channel or chat.</span></span>
* <span data-ttu-id="95058-129">`scopes`: Especifica se os usuários podem instalar o aplicativo em canais ( `team` ) e chats ( `groupchat` ).</span><span class="sxs-lookup"><span data-stu-id="95058-129">`scopes`: Specifies if users can install the app in channels (`team`) and chats (`groupchat`).</span></span> <span data-ttu-id="95058-130">É necessário pelo menos um valor.</span><span class="sxs-lookup"><span data-stu-id="95058-130">At least one value is required.</span></span>

### <a name="app-scaffolding"></a><span data-ttu-id="95058-131">Aplicativo scaffolding</span><span class="sxs-lookup"><span data-stu-id="95058-131">App scaffolding</span></span>

<span data-ttu-id="95058-132">O aplicativo scaffolding fornece um `TabConfig.js` arquivo, localizado no `src/components` diretório do seu projeto, para renderizar a página de configuração da guia (mais sobre isso em breve).</span><span class="sxs-lookup"><span data-stu-id="95058-132">The app scaffolding provides a `TabConfig.js` file, located in the `src/components` directory of your project, for rendering your tab's configuration page (more on this soon).</span></span>

## <a name="create-your-tab-content"></a><span data-ttu-id="95058-133">Criar seu conteúdo de guia</span><span class="sxs-lookup"><span data-stu-id="95058-133">Create your tab content</span></span>

<span data-ttu-id="95058-134">Abra o manifesto do aplicativo ( `manifest.json` ) no `.publish` diretório e defina as seguintes propriedades no [`staticTabs`](../resources/schema/manifest-schema.md#statictabs) , que define a página de conteúdo da guia.</span><span class="sxs-lookup"><span data-stu-id="95058-134">Open the app manifest (`manifest.json`) in the `.publish` directory and set the following properties in [`staticTabs`](../resources/schema/manifest-schema.md#statictabs), which defines your tab's content page.</span></span>

```JSON
"staticTabs": [
    {
        "entityId": "index",
        "name": "My Contacts",
        "contentUrl": "{baseUrl0}/tab",
        "scopes": [ "personal" ]
    }
],
```

<span data-ttu-id="95058-135">Copie e atualize o trecho de código a seguir, com informações relevantes para a sua organização ou, para fins de tempo, use o código como está.</span><span class="sxs-lookup"><span data-stu-id="95058-135">Copy and update the following snippet with information that's relevant to your organization or, for the sake of time, use the code as is.</span></span>

```JSX
<div>
  <h1>Important Contacts</h1>
    <ul>
      <li>Help Desk: <a href="mailto:support@company.com">support@company.com</a></li>
      <li>Human Resources: <a href="mailto:hr@company.com">hr@company.com</a></li>
      <li>Facilities: <a href="mailto:facilities@company.com">facilities@company.com</a></li>
    </ul>
</div>
```

<span data-ttu-id="95058-136">Vá para o `src/components` diretório e abra `Tab.js` .</span><span class="sxs-lookup"><span data-stu-id="95058-136">Go to the `src/components` directory and open `Tab.js`.</span></span> <span data-ttu-id="95058-137">Localize a `render()` função e cole o conteúdo dentro `return()` (conforme mostrado).</span><span class="sxs-lookup"><span data-stu-id="95058-137">Locate the `render()` function and paste your content inside `return()` (as shown).</span></span>

```JavaScript
render() {

    let userName = Object.keys(this.state.context).length > 0 ? this.state.context['upn'] : "";

    return (
    <div>
      <h1>Important Contacts</h1>
        <ul>
          <li>Help Desk: <a href="mailto:support@company.com">support@company.com</a></li>
          <li>Human Resources: <a href="mailto:hr@company.com">hr@company.com</a></li>
          <li>Facilities: <a href="mailto:facilities@company.com">facilities@company.com</a></li>
        </ul>
    </div>
    );
}
```

<span data-ttu-id="95058-138">Adicione a regra a seguir para `App.css` que os links de email sejam mais fáceis de ler, independentemente de qual tema é usado.</span><span class="sxs-lookup"><span data-stu-id="95058-138">Add the following rule to `App.css` so the email links are easier to read no matter which theme is used.</span></span>

```CSS
a {
  color: inherit;
}
```

## <a name="create-your-tab-configuration-page"></a><span data-ttu-id="95058-139">Criar a página de configuração da guia</span><span class="sxs-lookup"><span data-stu-id="95058-139">Create your tab configuration page</span></span>

<span data-ttu-id="95058-140">Cada guia de canal tem uma página de configuração, modal com pelo menos uma opção de configuração que é exibida ao instalar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="95058-140">Every channel tab has a configuration page, a modal with at least one setup option that displays when installing the app.</span></span> <span data-ttu-id="95058-141">A página de configuração, por padrão, pergunta aos usuários se eles desejam notificar o canal ou chat quando a guia é instalada.</span><span class="sxs-lookup"><span data-stu-id="95058-141">The configuration page by default asks users if they want to notify the channel or chat when the tab is installed.</span></span>

<span data-ttu-id="95058-142">Adicione algum conteúdo à sua página de configuração.</span><span class="sxs-lookup"><span data-stu-id="95058-142">Add some content to your configuration page.</span></span> <span data-ttu-id="95058-143">Vá para o diretório do seu projeto `src/components` , abra `TabConfig.js` e insira algum conteúdo dentro `return()` (conforme mostrado).</span><span class="sxs-lookup"><span data-stu-id="95058-143">Go to your project's `src/components` directory, open `TabConfig.js`, and insert some content inside `return()` (as shown).</span></span>

```JavaScript
return (
    <div>
      <h1>Add My Contoso Contacts</h1>
      <div>
        Select <b>Save</b> to add our organization's important contacts to this workspace.
      </div>
    </div>
);
```
 
> [!TIP]
> <span data-ttu-id="95058-144">No mínimo, forneça algumas breves informações sobre o aplicativo nesta página, pois essa pode ser a primeira vez que os usuários estão aprendendo.</span><span class="sxs-lookup"><span data-stu-id="95058-144">At minimum, provide some brief information about your app on this page since this may be the first time users are learning about it.</span></span> <span data-ttu-id="95058-145">Você também pode incluir opções de configuração personalizada ou um [fluxo de trabalho de autenticação](../tabs/how-to/authentication/auth-aad-sso.md), que é comum nas páginas de configuração da guia.</span><span class="sxs-lookup"><span data-stu-id="95058-145">You also could include custom configuration options or an [authentication workflow](../tabs/how-to/authentication/auth-aad-sso.md), which is common on tab configuration pages.</span></span>

## <a name="allow-the-tab-to-be-configured-and-installed"></a><span data-ttu-id="95058-146">Permitir que a guia seja configurada e instalada</span><span class="sxs-lookup"><span data-stu-id="95058-146">Allow the tab to be configured and installed</span></span>

<span data-ttu-id="95058-147">Para que os usuários configurem e instalem com êxito a guia canal, você deve adicionar a URL de host que você configurou ao [criar e executar seu primeiro aplicativo](../build-your-first-app/build-and-run.md) no componente da página de configuração.</span><span class="sxs-lookup"><span data-stu-id="95058-147">For users to successfully configure and install the channel tab, you must add the host URL you set up when [creating and running your first app](../build-your-first-app/build-and-run.md) to the configuration page component.</span></span>

<span data-ttu-id="95058-148">Vá para `TabConfig.js` e localize `microsoftTeams.settings.setSettings` .</span><span class="sxs-lookup"><span data-stu-id="95058-148">Go to `TabConfig.js` and locate `microsoftTeams.settings.setSettings`.</span></span> <span data-ttu-id="95058-149">Para `"contentUrl"` , substitua a `localhost:3000` parte da URL pelo domínio em que você está hospedando o conteúdo da guia (conforme mostrado).</span><span class="sxs-lookup"><span data-stu-id="95058-149">For `"contentUrl"`, replace the `localhost:3000` part of the URL with the domain where you're hosting the tab content (as shown).</span></span>

```JavaScript
microsoftTeams.settings.setSettings({
  "contentUrl": "https://<MY_HOST_DOMAIN>/tab"
});
```

<span data-ttu-id="95058-150">Além disso, certifique-se de que `microsoftTeams.settings.setValidityState(true);` .</span><span class="sxs-lookup"><span data-stu-id="95058-150">Also, make sure that `microsoftTeams.settings.setValidityState(true);`.</span></span> <span data-ttu-id="95058-151">Ele é, por padrão, se definido como `false` , o botão **salvar** está desabilitado na página de configuração.</span><span class="sxs-lookup"><span data-stu-id="95058-151">It is by default, but if set to `false`, the **Save** button is disabled on the configuration page.</span></span>

## <a name="provide-a-suggested-tab-name"></a><span data-ttu-id="95058-152">Fornecer um nome de guia sugerido</span><span class="sxs-lookup"><span data-stu-id="95058-152">Provide a suggested tab name</span></span>

<span data-ttu-id="95058-153">Quando você instala uma guia para uso pessoal, o nome para exibição é a `name` Propriedade na `staticTabs` parte do manifesto do aplicativo (por exemplo, **meus contatos**).</span><span class="sxs-lookup"><span data-stu-id="95058-153">When you install a tab for personal use, the display name is the `name` property in the `staticTabs` portion of of the app manifest (for example, **My Contacts**).</span></span> <span data-ttu-id="95058-154">Quando você instala uma guia canal, por padrão, o nome do aplicativo é exibido (por exemplo, **First-app**).</span><span class="sxs-lookup"><span data-stu-id="95058-154">When you install a channel tab, by default the app name displays (for example, **first-app**).</span></span>

<span data-ttu-id="95058-155">Isso pode ser bem, dependendo do que você chama no seu aplicativo, mas talvez você queira fornecer um nome que faça mais sentido no contexto de colaboração de grupo (por exemplo, **contatos da equipe**).</span><span class="sxs-lookup"><span data-stu-id="95058-155">This may be fine depending on what you call your app, but you may want to provide a name that makes more sense in the context of group collaboration (for example, **Team Contacts**).</span></span>

<span data-ttu-id="95058-156">No `TabConfig.js` , volte para `microsoftTeams.settings.setSettings` .</span><span class="sxs-lookup"><span data-stu-id="95058-156">In `TabConfig.js`, go back to `microsoftTeams.settings.setSettings`.</span></span> <span data-ttu-id="95058-157">Adicione a `suggestedDisplayName` propriedade com o nome da guia que você deseja exibir por padrão (conforme mostrado).</span><span class="sxs-lookup"><span data-stu-id="95058-157">Add the `suggestedDisplayName` property with the tab name you want to display by default (as shown).</span></span> <span data-ttu-id="95058-158">Use o nome fornecido ou crie o seu próprio.</span><span class="sxs-lookup"><span data-stu-id="95058-158">Use the provided name or create your own.</span></span> <span data-ttu-id="95058-159">Lembre-se, no manifesto, de que você está permitindo que os usuários alterem o nome se desejarem.</span><span class="sxs-lookup"><span data-stu-id="95058-159">Remember, in the manifest you're allowing users to change the name if they want.</span></span>

```JavaScript
microsoftTeams.settings.setSettings({
  "contentUrl": "https://<MY_HOST_DOMAIN>/tab",
  "suggestedDisplayName": "Team Contacts"
});
```

## <a name="view-the-channel-tab"></a><span data-ttu-id="95058-160">Exibir a guia canal</span><span class="sxs-lookup"><span data-stu-id="95058-160">View the channel tab</span></span>

<span data-ttu-id="95058-161">Para ver as páginas de configuração e conteúdo da guia canal, você deve instalá-lo em um canal ou chat.</span><span class="sxs-lookup"><span data-stu-id="95058-161">To see your channel tab's configuration and content pages, you must install it in a channel or chat.</span></span>

1. <span data-ttu-id="95058-162">No cliente do Microsoft Teams, selecione **aplicativos**.</span><span class="sxs-lookup"><span data-stu-id="95058-162">In the Teams client, select **Apps**.</span></span>
1. <span data-ttu-id="95058-163">Selecione **carregar um aplicativo personalizado** e escolha o seu aplicativo `Development.zip` .</span><span class="sxs-lookup"><span data-stu-id="95058-163">Select **Upload a custom app** and choose your app's `Development.zip`.</span></span>
1. <span data-ttu-id="95058-164">Escolha **Adicionar a uma equipe** ou **Adicionar a um chat** e localize um canal ou chat que você possa usar para teste.</span><span class="sxs-lookup"><span data-stu-id="95058-164">Choose **Add to a team** or **Add to a chat** and locate a channel or chat you can use for testing.</span></span>
1. <span data-ttu-id="95058-165">Selecione **Configurar uma guia**. A página de configuração é exibida.</span><span class="sxs-lookup"><span data-stu-id="95058-165">Select **Set up a tab**. The configuration page displays.</span></span><br/>
   :::image type="content" source="../assets/images/tabs/channel-tab-tutorial-content.png" alt-text="Captura de tela de uma página de configuração da guia canal.":::
1. <span data-ttu-id="95058-167">Selecione **salvar** para configurar a guia. O conteúdo é exibido.</span><span class="sxs-lookup"><span data-stu-id="95058-167">Select **Save** to configure the tab. The content displays.</span></span><br/>
   :::image type="content" source="../assets/images/tabs/channel-tab-tutorial-content-installed.png" alt-text="Captura de tela de uma guia canal com visualização de conteúdo estático.":::

## <a name="well-done"></a><span data-ttu-id="95058-169">Muito bem</span><span class="sxs-lookup"><span data-stu-id="95058-169">Well done</span></span>

<span data-ttu-id="95058-170">Parabéns!</span><span class="sxs-lookup"><span data-stu-id="95058-170">Congratulations!</span></span> <span data-ttu-id="95058-171">Você tem um aplicativo Teams com uma guia de canal para exibir conteúdo útil em canais e chats.</span><span class="sxs-lookup"><span data-stu-id="95058-171">You have a Teams app with a channel tab for displaying useful content in channels and chats.</span></span>

## <a name="learn-more"></a><span data-ttu-id="95058-172">Saiba mais</span><span class="sxs-lookup"><span data-stu-id="95058-172">Learn more</span></span>

* <span data-ttu-id="95058-173">[Guia autenticar usuários com SSO](../tabs/how-to/authentication/auth-aad-sso.md): se você quiser apenas que usuários autorizados exibam sua guia, configure o logon único (SSO) por meio do Azure Active Directory (AD).</span><span class="sxs-lookup"><span data-stu-id="95058-173">[Authenticate tab users with SSO](../tabs/how-to/authentication/auth-aad-sso.md): If you only want authorized users viewing your tab, set up single sign-on (SSO) through Azure Active Directory (AD).</span></span>
* <span data-ttu-id="95058-174">[Inserir conteúdo de um aplicativo Web existente ou página da Web](../tabs/how-to/add-tab.md#tab-requirements): mostramos como criar novo conteúdo para uma guia pessoal, mas você também pode carregar o conteúdo de uma URL externa.</span><span class="sxs-lookup"><span data-stu-id="95058-174">[Embed content from an existing web app or webpage](../tabs/how-to/add-tab.md#tab-requirements): We showed you how to create new content for a personal tab, but you can also load content from an external URL.</span></span>
* <span data-ttu-id="95058-175">[Criar uma experiência perfeita para sua guia](../tabs/design/tabs.md): consulte as diretrizes recomendadas para a criação de guias do teams.</span><span class="sxs-lookup"><span data-stu-id="95058-175">[Create a seamless experience for your tab](../tabs/design/tabs.md): See the recommended guidelines for designing Teams tabs.</span></span>
* <span data-ttu-id="95058-176">[Criar guias para celular](../tabs/design/tabs-mobile.md): entenda como desenvolver guias para telefones e tablets.</span><span class="sxs-lookup"><span data-stu-id="95058-176">[Build tabs for mobile](../tabs/design/tabs-mobile.md): Understand how to develop tabs for phones and tablets.</span></span>
* [<span data-ttu-id="95058-177">Criar uma guia sem o kit de ferramentas</span><span class="sxs-lookup"><span data-stu-id="95058-177">Create a tab without the toolkit</span></span>](../tabs/how-to/add-tab.md)

## <a name="next-lesson"></a><span data-ttu-id="95058-178">Próxima lição</span><span class="sxs-lookup"><span data-stu-id="95058-178">Next lesson</span></span>

<span data-ttu-id="95058-179">Você sabe como criar uma guia para colaboração.</span><span class="sxs-lookup"><span data-stu-id="95058-179">You know how to build a tab for collaboration.</span></span> <span data-ttu-id="95058-180">Deseja tentar criar um tipo diferente de aplicativo do teams?</span><span class="sxs-lookup"><span data-stu-id="95058-180">Want to try building a different kind of Teams app?</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="95058-181">Criar um bot</span><span class="sxs-lookup"><span data-stu-id="95058-181">Build a bot</span></span>](../build-your-first-app/build-bot.md)
