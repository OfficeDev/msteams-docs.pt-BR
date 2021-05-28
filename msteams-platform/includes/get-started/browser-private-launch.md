### <a name="optional-adjust-your-browser-launch-settings"></a><span data-ttu-id="3ab28-101">(Opcional) Ajustar as configurações de início do navegador</span><span class="sxs-lookup"><span data-stu-id="3ab28-101">(Optional) Adjust your browser launch settings</span></span>

<span data-ttu-id="3ab28-102">Ao desenvolver um Teams, é comum executar seu aplicativo em um locatário de desenvolvedor alternativo ou com credenciais alternativas.</span><span class="sxs-lookup"><span data-stu-id="3ab28-102">When developing a Teams app, it is common to run your app in an alternate developer tenant or with alternate credentials.</span></span>  <span data-ttu-id="3ab28-103">Tanto Microsoft Edge quanto o Google Chrome fornecem instalações para ajustar as configurações de início do navegador.</span><span class="sxs-lookup"><span data-stu-id="3ab28-103">Both Microsoft Edge and Google Chrome provide facilities to adjust the launch settings for your browser.</span></span>  <span data-ttu-id="3ab28-104">Por exemplo, para atualizar o projeto para dar suporte ao modo InPrivate (Microsoft Edge), abra o `.vscode/launch.json` arquivo em seu projeto.</span><span class="sxs-lookup"><span data-stu-id="3ab28-104">For example, to update the project to support InPrivate mode (Microsoft Edge), open the `.vscode/launch.json` file in your project.</span></span>  <span data-ttu-id="3ab28-105">Procure as configurações de início apropriadas e adicione o seguinte bloco a cada um:</span><span class="sxs-lookup"><span data-stu-id="3ab28-105">Look for the appropriate launch settings, and add the following block to each one:</span></span>

``` json
"runtimeArgs": [ "--inprivate" ]
```

<span data-ttu-id="3ab28-106">Por exemplo, a configuração de início para execução local tem a mesma aparência:</span><span class="sxs-lookup"><span data-stu-id="3ab28-106">For instance, the launch setting for running locally looks like this:</span></span>

``` json
{
   "name": "Start and Attach to Frontend (Edge)",
   "type": "pwa-msedge",
   "request": "launch",
   "url": "https://teams.microsoft.com/_#/l/app/${localTeamsAppId}?installAppPackage=true",
   "preLaunchTask": "Start Frontend",
   "postDebugTask": "Stop All Services",
   "presentation": {
         "group": "all",
         "hidden": true
   },
   "runtimeArgs": [ "--inprivate" ]
},
```

<span data-ttu-id="3ab28-107">Como alternativa, você pode configurar seu navegador para usar o último perfil conhecido.</span><span class="sxs-lookup"><span data-stu-id="3ab28-107">Alternatively, you can configure your browser to use the last known profile.</span></span> <span data-ttu-id="3ab28-108">[Crie um novo perfil em](https://support.microsoft.com/topic/sign-in-and-create-multiple-profiles-in-microsoft-edge-df94e622-2061-49ae-ad1d-6f0e43ce6435) Microsoft Edge.</span><span class="sxs-lookup"><span data-stu-id="3ab28-108">[Create a new profile](https://support.microsoft.com/topic/sign-in-and-create-multiple-profiles-in-microsoft-edge-df94e622-2061-49ae-ad1d-6f0e43ce6435) in Microsoft Edge.</span></span>  <span data-ttu-id="3ab28-109">Em seguida, ajuste as configurações para usar o último perfil conhecido para novos links:</span><span class="sxs-lookup"><span data-stu-id="3ab28-109">Then adjust the settings to use the last known profile for new links:</span></span>

- <span data-ttu-id="3ab28-110">Em Microsoft Edge, abra `edge://settings/profiles/multiProfileSettings` .</span><span class="sxs-lookup"><span data-stu-id="3ab28-110">In Microsoft Edge, open `edge://settings/profiles/multiProfileSettings`.</span></span>
- <span data-ttu-id="3ab28-111">Desativar **a alternação automática de perfil**.</span><span class="sxs-lookup"><span data-stu-id="3ab28-111">Turn off **Automatic profile switching**.</span></span>
- <span data-ttu-id="3ab28-112">Para o **perfil Padrão para links externos,** selecione Último usado **(padrão)**.</span><span class="sxs-lookup"><span data-stu-id="3ab28-112">For the **Default profile for external links**, select **Last used (default)**.</span></span>

<span data-ttu-id="3ab28-113">Verifique se o navegador está aberto ao perfil correto antes de depurar seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="3ab28-113">Ensure your browser is opened to the correct profile before debugging your app.</span></span>
