---
author: heath-hamilton
description: Saiba como criar uma guia de canal e grupo para seu primeiro aplicativo do Microsoft Teams.
ms.author: lajanuar
ms.date: 09/22/2020
ms.topic: tutorial
title: Criar uma guia de canal e grupo do teams
ms.openlocfilehash: d97d8c13404077bff999db48b24b773aa4bc04ca
ms.sourcegitcommit: f9a2f5cedc9d30ef7a9cf78a47d01cfd277e150d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/23/2020
ms.locfileid: "48237808"
---
# <a name="build-a-teams-channel-and-group-tab"></a><span data-ttu-id="29393-103">Criar uma guia de canal e grupo do teams</span><span class="sxs-lookup"><span data-stu-id="29393-103">Build a Teams channel and group tab</span></span>

<span data-ttu-id="29393-104">Neste tutorial, você criará uma guia de *canal* básica (também conhecida como uma *Guia de grupo*), que é uma página de tela inteira de um canal de equipe ou bate-papo.</span><span class="sxs-lookup"><span data-stu-id="29393-104">In this tutorial, you'll build a basic *channel tab* (also known as a *group tab*), which is a full-screen page for a team channel or chat.</span></span> <span data-ttu-id="29393-105">Ao contrário de uma guia pessoal, os usuários podem configurar alguns aspectos desse tipo de guia (por exemplo, renomear a guia de forma que ela seja significativa para o canal).</span><span class="sxs-lookup"><span data-stu-id="29393-105">Unlike a personal tab, users can configure some aspects of this kind of tab (for example, rename the tab so it's meaningful to their channel).</span></span>

## <a name="your-assignment"></a><span data-ttu-id="29393-106">Sua atribuição</span><span class="sxs-lookup"><span data-stu-id="29393-106">Your assignment</span></span>

<span data-ttu-id="29393-107">Não há muito tempo, sua organização criou uma guia do teams com informações sobre como entrar em contato com funções importantes (Help Desk, HR, etc.).</span><span class="sxs-lookup"><span data-stu-id="29393-107">Not long ago, your organization created a Teams tab with information on how to contact important functions (help desk, HR, etc.).</span></span> <span data-ttu-id="29393-108">No entanto, como a guia era escopoda somente para uso pessoal, cada usuário deve instalar a guia para vê-la e a adoção é menor do que o esperado.</span><span class="sxs-lookup"><span data-stu-id="29393-108">However, since the tab was scoped only for personal use, each user must install the tab to see it and adoption is lower than expected.</span></span> <span data-ttu-id="29393-109">Em outras palavras, muitos trabalhadores ainda não sabem como alcançar o suporte técnico.</span><span class="sxs-lookup"><span data-stu-id="29393-109">In other words, too many workers still don't know how to reach the help desk.</span></span>

<span data-ttu-id="29393-110">Você pode facilitar a localização dessas informações criando uma guia de canal, o que removerá o ônus de exigir que todos instalem um aplicativo.</span><span class="sxs-lookup"><span data-stu-id="29393-110">You can make this information easier to find by building a channel tab, which will remove the burden of requiring everyone to install an app.</span></span> <span data-ttu-id="29393-111">Em vez disso, um usuário pode instalar a guia em um canal ou chat para o benefício de um grupo inteiro.</span><span class="sxs-lookup"><span data-stu-id="29393-111">Instead, one user can install the tab in a channel or chat for the benefit of an entire group.</span></span>

## <a name="what-youll-learn"></a><span data-ttu-id="29393-112">O que você aprenderá</span><span class="sxs-lookup"><span data-stu-id="29393-112">What you'll learn</span></span>

> [!div class="checklist"]
>
> * <span data-ttu-id="29393-113">Criar um projeto de aplicativo usando o Microsoft Teams Toolkit para o Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="29393-113">Create an app project using the Microsoft Teams Toolkit for Visual Studio Code</span></span>
> * <span data-ttu-id="29393-114">Identificar algumas das propriedades de manifesto do aplicativo e scaffolding relevantes para as guias canal e grupo</span><span class="sxs-lookup"><span data-stu-id="29393-114">Identify some of the app manifest properties and scaffolding relevant to channel and group tabs</span></span>
> * <span data-ttu-id="29393-115">Hospedar um aplicativo localmente</span><span class="sxs-lookup"><span data-stu-id="29393-115">Host an app locally</span></span>
> * <span data-ttu-id="29393-116">Criar conteúdo de guia</span><span class="sxs-lookup"><span data-stu-id="29393-116">Create tab content</span></span>
> * <span data-ttu-id="29393-117">Criar conteúdo para a página de configuração de uma guia</span><span class="sxs-lookup"><span data-stu-id="29393-117">Create content for a tab's configuration page</span></span>
> * <span data-ttu-id="29393-118">Permitir que uma guia seja configurada e instalada</span><span class="sxs-lookup"><span data-stu-id="29393-118">Allow a tab to be configured and installed</span></span>
> * <span data-ttu-id="29393-119">Fornecer um nome de guia sugerido</span><span class="sxs-lookup"><span data-stu-id="29393-119">Provide a suggested tab name</span></span>

## <a name="1-create-your-app-project"></a><span data-ttu-id="29393-120">1. criar seu projeto de aplicativo</span><span class="sxs-lookup"><span data-stu-id="29393-120">1. Create your app project</span></span>

<span data-ttu-id="29393-121">O Microsoft Teams Toolkit ajuda você a configurar o manifesto do aplicativo e o scaffolding relevantes para as guias canal e grupo, incluindo uma página de configuração básica e uma página de conteúdo que exibe um "Olá, mundo!"</span><span class="sxs-lookup"><span data-stu-id="29393-121">The Microsoft Teams Toolkit helps you set up the app manifest and scaffolding relevant to channel and group tabs, including a basic configuration page and content page that displays a "Hello, World!"</span></span> <span data-ttu-id="29393-122">Mensagem.</span><span class="sxs-lookup"><span data-stu-id="29393-122">message.</span></span>

> [!TIP]
> <span data-ttu-id="29393-123">Se você ainda não criou um projeto de aplicativos do Microsoft Teams, talvez ache útil seguir [estas instruções](../build-your-first-app/build-and-run.md) para explicar os projetos com mais detalhes.</span><span class="sxs-lookup"><span data-stu-id="29393-123">If you haven't created a Teams app project before, you might find it helpful to follow [these instructions](../build-your-first-app/build-and-run.md) that explain projects in more detail.</span></span>

1. No Visual Studio Code, selecione **Microsoft Teams** :::image type="icon" source="../assets/icons/vsc-toolkit.png"::: na barra de atividades à esquerda e escolha **criar um novo aplicativo Teams**.
1. <span data-ttu-id="29393-125">Insira um nome para seu aplicativo do Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="29393-125">Enter a name for your Teams app.</span></span> <span data-ttu-id="29393-126">(Esse é o nome padrão para seu aplicativo e também o nome do diretório do projeto de aplicativo em sua máquina local.)</span><span class="sxs-lookup"><span data-stu-id="29393-126">(This is the default name for your app and also the name of the app project directory on your local machine.)</span></span>
1. <span data-ttu-id="29393-127">Na tela **Adicionar recursos** , selecione **Tab** , **grupo ou guia canal de equipe**.</span><span class="sxs-lookup"><span data-stu-id="29393-127">On the **Add capabilities** screen, select **Tab** then **Group or Teams channel tab**.</span></span>
1. <span data-ttu-id="29393-128">Selecione **concluir** na parte inferior da tela para configurar seu projeto.</span><span class="sxs-lookup"><span data-stu-id="29393-128">Select **Finish** at the bottom of the screen to configure your project.</span></span>  

## <a name="2-identify-relevant-app-project-components"></a><span data-ttu-id="29393-129">2. identificar componentes de projeto de aplicativo relevantes</span><span class="sxs-lookup"><span data-stu-id="29393-129">2. Identify relevant app project components</span></span>

<span data-ttu-id="29393-130">Grande parte do manifesto do aplicativo e do scaffolding são configuradas automaticamente quando você cria seu projeto com o Teams Toolkit.</span><span class="sxs-lookup"><span data-stu-id="29393-130">Much of the app manifest and scaffolding are set up automatically when you create your project with the Teams Toolkit.</span></span> <span data-ttu-id="29393-131">Vamos examinar os principais componentes para a criação de uma guia canal e grupo.</span><span class="sxs-lookup"><span data-stu-id="29393-131">Let's look at the main components for building a channel and group tab.</span></span>

### <a name="app-manifest"></a><span data-ttu-id="29393-132">Manifesto do aplicativo</span><span class="sxs-lookup"><span data-stu-id="29393-132">App manifest</span></span>

<span data-ttu-id="29393-133">O trecho de código a seguir do manifesto de aplicativo mostra [`configurableTabs`](../resources/schema/manifest-schema.md#configurabletabs) , que inclui as propriedades e os valores padrão relevantes para as guias canal e grupo.</span><span class="sxs-lookup"><span data-stu-id="29393-133">The following snippet from the app manifest shows [`configurableTabs`](../resources/schema/manifest-schema.md#configurabletabs), which includes the properties and default values relevant to channel and group tabs.</span></span>

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

* <span data-ttu-id="29393-134">`configurationUrl`: A URL do host para a página de configuração da guia (deve ser HTTPS).</span><span class="sxs-lookup"><span data-stu-id="29393-134">`configurationUrl`: The host URL for your tab configuration page (must be HTTPS).</span></span>
* <span data-ttu-id="29393-135">`canUpdateConfiguration`: Se definido como `true` , os usuários podem alterar as configurações de tabulação, renomear a guia ou removê-la de um canal ou chat.</span><span class="sxs-lookup"><span data-stu-id="29393-135">`canUpdateConfiguration`: If set to `true`, users can change tab settings, rename the tab, or remove it from a channel or chat.</span></span>
* <span data-ttu-id="29393-136">`scopes`: Especifica se os usuários podem instalar o aplicativo em canais ( `team` ) e chats ( `groupchat` ).</span><span class="sxs-lookup"><span data-stu-id="29393-136">`scopes`: Specifies if users can install the app in channels (`team`) and chats (`groupchat`).</span></span> <span data-ttu-id="29393-137">É necessário pelo menos um valor.</span><span class="sxs-lookup"><span data-stu-id="29393-137">At least one value is required.</span></span>

### <a name="app-scaffolding"></a><span data-ttu-id="29393-138">Aplicativo scaffolding</span><span class="sxs-lookup"><span data-stu-id="29393-138">App scaffolding</span></span>

<span data-ttu-id="29393-139">O aplicativo scaffolding fornece um `TabConfig.js` arquivo, localizado no `src/components` diretório do seu projeto, para renderizar a página de configuração da guia (mais sobre isso em breve).</span><span class="sxs-lookup"><span data-stu-id="29393-139">The app scaffolding provides a `TabConfig.js` file, located in the `src/components` directory of your project, for rendering your tab's configuration page (more on this soon).</span></span>

## <a name="3-run-your-app"></a><span data-ttu-id="29393-140">3. Execute seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="29393-140">3. Run your app</span></span>

<span data-ttu-id="29393-141">Nos juros de tempo, você criará e executará seu aplicativo localmente.</span><span class="sxs-lookup"><span data-stu-id="29393-141">In the interest of time, you'll build and run your app locally.</span></span>

1. <span data-ttu-id="29393-142">Em um terminal, vá para o diretório raiz do seu projeto de aplicativo e execute `npm install` .</span><span class="sxs-lookup"><span data-stu-id="29393-142">In a terminal, go to the root directory of your app project and run `npm install`.</span></span>
1. <span data-ttu-id="29393-143">Executar `npm start` .</span><span class="sxs-lookup"><span data-stu-id="29393-143">Run `npm start`.</span></span>

<span data-ttu-id="29393-144">Após a conclusão, há uma **compilação bem-sucedida!**</span><span class="sxs-lookup"><span data-stu-id="29393-144">Once complete, there's a **Compiled successfully!**</span></span> <span data-ttu-id="29393-145">mensagem no terminal.</span><span class="sxs-lookup"><span data-stu-id="29393-145">message in the terminal.</span></span>

## <a name="4-set-up-a-secure-tunnel-to-your-app"></a><span data-ttu-id="29393-146">4. configurar um túnel seguro para seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="29393-146">4. Set up a secure tunnel to your app</span></span>

<span data-ttu-id="29393-147">Para fins de teste, vamos hospedar sua guia em um servidor Web local (porta 3000).</span><span class="sxs-lookup"><span data-stu-id="29393-147">For testing purposes, let's host your tab on a local web server (port 3000).</span></span>

1. <span data-ttu-id="29393-148">Em um terminal, execute `ngrok http 3000` .</span><span class="sxs-lookup"><span data-stu-id="29393-148">In a terminal, run `ngrok http 3000`.</span></span>
1. <span data-ttu-id="29393-149">Copie a URL HTTPS que você forneceu.</span><span class="sxs-lookup"><span data-stu-id="29393-149">Copy the HTTPS URL you're provided.</span></span>
1. <span data-ttu-id="29393-150">Em seu `.publish` diretório, abra `Development.env` .</span><span class="sxs-lookup"><span data-stu-id="29393-150">In your `.publish` directory, open `Development.env`.</span></span>
1. <span data-ttu-id="29393-151">Substitua o `baseUrl0` valor pela URL copiada.</span><span class="sxs-lookup"><span data-stu-id="29393-151">Replace the `baseUrl0` value with the copied URL.</span></span> <span data-ttu-id="29393-152">(Por exemplo, alterar `baseUrl0=http://localhost:3000` para `baseUrl0=https://85528b2b3ca5.ngrok.io` .)</span><span class="sxs-lookup"><span data-stu-id="29393-152">(For example, change `baseUrl0=http://localhost:3000` to `baseUrl0=https://85528b2b3ca5.ngrok.io`.)</span></span>

<span data-ttu-id="29393-153">O manifesto do aplicativo está apontando para o local em que você está hospedando a guia.</span><span class="sxs-lookup"><span data-stu-id="29393-153">Your app manifest is pointing to where you're hosting the tab.</span></span>

## <a name="5-customize-your-tab-content-page"></a><span data-ttu-id="29393-154">5. personalizar a página de conteúdo da guia</span><span class="sxs-lookup"><span data-stu-id="29393-154">5. Customize your tab content page</span></span>

<span data-ttu-id="29393-155">Abra o manifesto do aplicativo ( `manifest.json` ) no `.publish` diretório e defina as seguintes propriedades no [`staticTabs`](../resources/schema/manifest-schema.md#statictabs) , que define a página de conteúdo da guia.</span><span class="sxs-lookup"><span data-stu-id="29393-155">Open the app manifest (`manifest.json`) in the `.publish` directory and set the following properties in [`staticTabs`](../resources/schema/manifest-schema.md#statictabs), which defines your tab's content page.</span></span>

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

<span data-ttu-id="29393-156">Copie e atualize o trecho de código a seguir, com informações relevantes para a sua organização ou, para fins de tempo, use o código como está.</span><span class="sxs-lookup"><span data-stu-id="29393-156">Copy and update the following snippet with information that's relevant to your organization or, for the sake of time, use the code as is.</span></span>

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

<span data-ttu-id="29393-157">Vá para o `src/components` diretório e abra `Tab.js` .</span><span class="sxs-lookup"><span data-stu-id="29393-157">Go to the `src/components` directory and open `Tab.js`.</span></span> <span data-ttu-id="29393-158">Localize a `render()` função e cole o conteúdo dentro `return()` (conforme mostrado).</span><span class="sxs-lookup"><span data-stu-id="29393-158">Locate the `render()` function and paste your content inside `return()` (as shown).</span></span>

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

<span data-ttu-id="29393-159">Adicione a regra a seguir para `App.css` que os links de email sejam mais fáceis de ler, independentemente de qual tema é usado.</span><span class="sxs-lookup"><span data-stu-id="29393-159">Add the following rule to `App.css` so the email links are easier to read no matter which theme is used.</span></span>

```CSS
a {
  color: inherit;
}
```

## <a name="6-create-your-tab-configuration-page"></a><span data-ttu-id="29393-160">6. criar sua página de configuração de guia</span><span class="sxs-lookup"><span data-stu-id="29393-160">6. Create your tab configuration page</span></span>

<span data-ttu-id="29393-161">Cada guia em um canal ou chat tem uma página de configuração, uma janela restrita com pelo menos uma opção de instalação que é exibida quando os usuários instalam seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="29393-161">Every tab in a channel or chat has a configuration page, a modal with at least one setup option that displays when users install your app.</span></span> <span data-ttu-id="29393-162">A página de configuração, por padrão, pergunta aos usuários se eles desejam notificar o canal ou chat quando a guia é instalada.</span><span class="sxs-lookup"><span data-stu-id="29393-162">The configuration page by default asks users if they want to notify the channel or chat when the tab is installed.</span></span>

<span data-ttu-id="29393-163">Adicione algum conteúdo à sua página de configuração.</span><span class="sxs-lookup"><span data-stu-id="29393-163">Add some content to your configuration page.</span></span> <span data-ttu-id="29393-164">Vá para o diretório do seu projeto `src/components` , abra `TabConfig.js` e insira algum conteúdo dentro `return()` (conforme mostrado).</span><span class="sxs-lookup"><span data-stu-id="29393-164">Go to your project's `src/components` directory, open `TabConfig.js`, and insert some content inside `return()` (as shown).</span></span>

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
> <span data-ttu-id="29393-165">No mínimo, forneça algumas breves informações sobre o aplicativo nesta página, pois essa pode ser a primeira vez que os usuários estão aprendendo.</span><span class="sxs-lookup"><span data-stu-id="29393-165">At minimum, provide some brief information about your app on this page since this may be the first time users are learning about it.</span></span> <span data-ttu-id="29393-166">Você também pode incluir opções de configuração personalizada ou um [fluxo de trabalho de autenticação](../tabs/how-to/authentication/auth-aad-sso.md), que é comum nas páginas de configuração da guia.</span><span class="sxs-lookup"><span data-stu-id="29393-166">You also could include custom configuration options or an [authentication workflow](../tabs/how-to/authentication/auth-aad-sso.md), which is common on tab configuration pages.</span></span>

## <a name="7-allow-the-tab-to-be-configured-and-installed"></a><span data-ttu-id="29393-167">7. permitir que a guia seja configurada e instalada</span><span class="sxs-lookup"><span data-stu-id="29393-167">7. Allow the tab to be configured and installed</span></span>

<span data-ttu-id="29393-168">Para que os usuários configurem e instalem a guia com êxito, você deve adicionar a [URL de host segura que você configurou](#4-set-up-a-secure-tunnel-to-your-app) ao componente da página de configuração.</span><span class="sxs-lookup"><span data-stu-id="29393-168">For users to successfully configure and install the tab, you must add the [secure host URL you set up](#4-set-up-a-secure-tunnel-to-your-app) to the configuration page component.</span></span>

<span data-ttu-id="29393-169">Vá para `TabConfig.js` e localize `microsoftTeams.settings.setSettings` .</span><span class="sxs-lookup"><span data-stu-id="29393-169">Go to `TabConfig.js` and locate `microsoftTeams.settings.setSettings`.</span></span> <span data-ttu-id="29393-170">Para `"contentUrl"` , substitua a `localhost:3000` parte da URL pelo domínio em que você está hospedando o conteúdo da guia (conforme mostrado).</span><span class="sxs-lookup"><span data-stu-id="29393-170">For `"contentUrl"`, replace the `localhost:3000` part of the URL with the domain where you're hosting the tab content (as shown).</span></span>

```JavaScript
microsoftTeams.settings.setSettings({
  "contentUrl": "https://<MY_HOST_DOMAIN>/tab"
});
```

<span data-ttu-id="29393-171">Além disso, certifique-se de que `microsoftTeams.settings.setValidityState(true);` .</span><span class="sxs-lookup"><span data-stu-id="29393-171">Also, make sure that `microsoftTeams.settings.setValidityState(true);`.</span></span> <span data-ttu-id="29393-172">Ele é, por padrão, se definido como `false` , o botão **salvar** está desabilitado na página de configuração.</span><span class="sxs-lookup"><span data-stu-id="29393-172">It is by default, but if set to `false`, the **Save** button is disabled on the configuration page.</span></span>

## <a name="8-provide-a-suggested-tab-name"></a><span data-ttu-id="29393-173">8. fornecer um nome de guia sugerido</span><span class="sxs-lookup"><span data-stu-id="29393-173">8. Provide a suggested tab name</span></span>

<span data-ttu-id="29393-174">Quando você instala uma guia para uso pessoal, o nome para exibição é a `name` Propriedade na `staticTabs` parte do manifesto do aplicativo (por exemplo, **meus contatos**).</span><span class="sxs-lookup"><span data-stu-id="29393-174">When you install a tab for personal use, the display name is the `name` property in the `staticTabs` portion of the app manifest (for example, **My Contacts**).</span></span> <span data-ttu-id="29393-175">Quando você instala uma guia canal, por padrão, o nome do aplicativo é exibido (por exemplo, **First-app**).</span><span class="sxs-lookup"><span data-stu-id="29393-175">When you install a channel tab, by default the app name displays (for example, **first-app**).</span></span>

<span data-ttu-id="29393-176">Isso pode ser bem, dependendo do que você chama no seu aplicativo, mas talvez você queira fornecer um nome que faça mais sentido no contexto de colaboração de grupo (por exemplo, **contatos da equipe**).</span><span class="sxs-lookup"><span data-stu-id="29393-176">This may be fine depending on what you call your app, but you may want to provide a name that makes more sense in the context of group collaboration (for example, **Team Contacts**).</span></span>

<span data-ttu-id="29393-177">No `TabConfig.js` , volte para `microsoftTeams.settings.setSettings` .</span><span class="sxs-lookup"><span data-stu-id="29393-177">In `TabConfig.js`, go back to `microsoftTeams.settings.setSettings`.</span></span> <span data-ttu-id="29393-178">Adicione a `suggestedDisplayName` propriedade com o nome da guia que você deseja exibir por padrão (conforme mostrado).</span><span class="sxs-lookup"><span data-stu-id="29393-178">Add the `suggestedDisplayName` property with the tab name you want to display by default (as shown).</span></span> <span data-ttu-id="29393-179">Use o nome fornecido ou crie o seu próprio.</span><span class="sxs-lookup"><span data-stu-id="29393-179">Use the provided name or create your own.</span></span> <span data-ttu-id="29393-180">Lembre-se, no manifesto, de que você está permitindo que os usuários alterem o nome se desejarem.</span><span class="sxs-lookup"><span data-stu-id="29393-180">Remember, in the manifest you're allowing users to change the name if they want.</span></span>

```JavaScript
microsoftTeams.settings.setSettings({
  "contentUrl": "https://<MY_HOST_DOMAIN>/tab",
  "suggestedDisplayName": "Team Contacts"
});
```

## <a name="9-view-the-tab"></a><span data-ttu-id="29393-181">9. exibir a guia</span><span class="sxs-lookup"><span data-stu-id="29393-181">9. View the tab</span></span>

<span data-ttu-id="29393-182">Para ver as páginas de configuração e conteúdo da guia, você deve instalá-lo em um canal ou chat.</span><span class="sxs-lookup"><span data-stu-id="29393-182">To see your tab's configuration and content pages, you must install it in a channel or chat.</span></span>

1. <span data-ttu-id="29393-183">No cliente do Microsoft Teams, selecione **aplicativos**.</span><span class="sxs-lookup"><span data-stu-id="29393-183">In the Teams client, select **Apps**.</span></span>
1. <span data-ttu-id="29393-184">Selecione **carregar um aplicativo personalizado** e escolha o seu aplicativo `Development.zip` .</span><span class="sxs-lookup"><span data-stu-id="29393-184">Select **Upload a custom app** and choose your app's `Development.zip`.</span></span>
1. <span data-ttu-id="29393-185">Escolha **Adicionar a uma equipe** ou **Adicionar a um chat** e localize um canal ou chat que você possa usar para teste.</span><span class="sxs-lookup"><span data-stu-id="29393-185">Choose **Add to a team** or **Add to a chat** and locate a channel or chat you can use for testing.</span></span>
1. <span data-ttu-id="29393-186">Selecione **Configurar uma guia**. A página de configuração é exibida.</span><span class="sxs-lookup"><span data-stu-id="29393-186">Select **Set up a tab**. The configuration page displays.</span></span><br/>
   :::image type="content" source="../assets/images/tabs/channel-tab-tutorial-content.png" alt-text="Captura de tela de uma página de configuração da guia canal.":::
1. <span data-ttu-id="29393-188">Selecione **salvar** para configurar a guia. O conteúdo é exibido.</span><span class="sxs-lookup"><span data-stu-id="29393-188">Select **Save** to configure the tab. The content displays.</span></span><br/>
   :::image type="content" source="../assets/images/tabs/channel-tab-tutorial-content-installed.png" alt-text="Captura de tela de uma guia canal com visualização de conteúdo estático.":::

## <a name="well-done"></a><span data-ttu-id="29393-190">Muito bem</span><span class="sxs-lookup"><span data-stu-id="29393-190">Well done</span></span>

<span data-ttu-id="29393-191">Parabéns!</span><span class="sxs-lookup"><span data-stu-id="29393-191">Congratulations!</span></span> <span data-ttu-id="29393-192">Você tem um aplicativo do teams com uma guia para exibir conteúdo útil em canais e chats.</span><span class="sxs-lookup"><span data-stu-id="29393-192">You have a Teams app with a tab for displaying useful content in channels and chats.</span></span>

## <a name="learn-more"></a><span data-ttu-id="29393-193">Saiba mais</span><span class="sxs-lookup"><span data-stu-id="29393-193">Learn more</span></span>

* <span data-ttu-id="29393-194">[Guia autenticar usuários com SSO](../tabs/how-to/authentication/auth-aad-sso.md): se você quiser apenas que usuários autorizados exibam sua guia, configure o logon único (SSO) por meio do Azure Active Directory (AD).</span><span class="sxs-lookup"><span data-stu-id="29393-194">[Authenticate tab users with SSO](../tabs/how-to/authentication/auth-aad-sso.md): If you only want authorized users viewing your tab, set up single sign-on (SSO) through Azure Active Directory (AD).</span></span>
* <span data-ttu-id="29393-195">[Inserir conteúdo de um aplicativo Web existente ou página da Web](../tabs/how-to/add-tab.md#tab-requirements): mostramos como criar novo conteúdo para uma guia pessoal, mas você também pode carregar o conteúdo de uma URL externa.</span><span class="sxs-lookup"><span data-stu-id="29393-195">[Embed content from an existing web app or webpage](../tabs/how-to/add-tab.md#tab-requirements): We showed you how to create new content for a personal tab, but you can also load content from an external URL.</span></span>
* <span data-ttu-id="29393-196">[Criar uma experiência perfeita para sua guia](../tabs/design/tabs.md): consulte as diretrizes recomendadas para a criação de guias do teams.</span><span class="sxs-lookup"><span data-stu-id="29393-196">[Create a seamless experience for your tab](../tabs/design/tabs.md): See the recommended guidelines for designing Teams tabs.</span></span>
* <span data-ttu-id="29393-197">[Criar guias para celular](../tabs/design/tabs-mobile.md): entenda como desenvolver guias para telefones e tablets.</span><span class="sxs-lookup"><span data-stu-id="29393-197">[Build tabs for mobile](../tabs/design/tabs-mobile.md): Understand how to develop tabs for phones and tablets.</span></span>
* [<span data-ttu-id="29393-198">Criar uma guia sem o kit de ferramentas</span><span class="sxs-lookup"><span data-stu-id="29393-198">Create a tab without the toolkit</span></span>](../tabs/how-to/add-tab.md)

## <a name="next-lesson"></a><span data-ttu-id="29393-199">Próxima lição</span><span class="sxs-lookup"><span data-stu-id="29393-199">Next lesson</span></span>

<span data-ttu-id="29393-200">Você sabe como criar uma guia para colaboração.</span><span class="sxs-lookup"><span data-stu-id="29393-200">You know how to build a tab for collaboration.</span></span> <span data-ttu-id="29393-201">Deseja tentar criar um tipo diferente de aplicativo do teams?</span><span class="sxs-lookup"><span data-stu-id="29393-201">Want to try building a different kind of Teams app?</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="29393-202">Construir um bot</span><span class="sxs-lookup"><span data-stu-id="29393-202">Build a bot</span></span>](../build-your-first-app/build-bot.md)
