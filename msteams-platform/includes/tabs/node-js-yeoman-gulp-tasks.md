## <a name="create-the-app-package"></a><span data-ttu-id="2a20b-101">Criar o pacote de aplicativos</span><span class="sxs-lookup"><span data-stu-id="2a20b-101">Create the app package</span></span>

<span data-ttu-id="2a20b-102">Você precisará de um pacote de aplicativos para testar sua guia no Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="2a20b-102">You'll need an app package to test your tab in Teams.</span></span> <span data-ttu-id="2a20b-103">É uma pasta zip que contém os seguintes arquivos necessários:</span><span class="sxs-lookup"><span data-stu-id="2a20b-103">It's a zip folder that contains the following required files:</span></span>

- <span data-ttu-id="2a20b-104">Um **ícone de cor completa** medindo 192 x 192 pixels.</span><span class="sxs-lookup"><span data-stu-id="2a20b-104">A **full color icon** measuring 192 x 192 pixels.</span></span>
- <span data-ttu-id="2a20b-105">Um **ícone de contorno transparente** medindo 32 x 32 pixels.</span><span class="sxs-lookup"><span data-stu-id="2a20b-105">A **transparent outline icon** measuring 32 x 32 pixels.</span></span>
- <span data-ttu-id="2a20b-106">Um arquivo **manifest. JSON** que especifica os atributos do seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="2a20b-106">A **manifest.json** file that specifies the attributes of your app.</span></span>

<span data-ttu-id="2a20b-107">O pacote é criado por meio de uma tarefa Gulp que valida o arquivo manifest. JSON e gera a pasta zip no `./package directory`.</span><span class="sxs-lookup"><span data-stu-id="2a20b-107">The package is created via a gulp task that validates the manifest.json file and generates the zip folder in the `./package directory`.</span></span> <span data-ttu-id="2a20b-108">No prompt de comando, digite:</span><span class="sxs-lookup"><span data-stu-id="2a20b-108">In the command prompt enter:</span></span>

```bash
gulp manifest
```

## <a name="build-your-application"></a><span data-ttu-id="2a20b-109">Criar seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="2a20b-109">Build your application</span></span>

<span data-ttu-id="2a20b-110">O comando Build compila sua solução na pasta *. pasta/dist.* .</span><span class="sxs-lookup"><span data-stu-id="2a20b-110">The build command transpiles your solution into the *./dist* folder.</span></span> <span data-ttu-id="2a20b-111">Em seguida, digite:</span><span class="sxs-lookup"><span data-stu-id="2a20b-111">Next,enter:</span></span>

```bash
gulp build
```

## <a name="run-your-application-in-localhost"></a><span data-ttu-id="2a20b-112">Executar o aplicativo no localhost</span><span class="sxs-lookup"><span data-stu-id="2a20b-112">Run your application in localhost</span></span>

<span data-ttu-id="2a20b-113">Inicie um servidor Web local, inserindo o seguinte:</span><span class="sxs-lookup"><span data-stu-id="2a20b-113">Start a local web server by entering the following:</span></span>

```bash
gulp serve
```

<span data-ttu-id="2a20b-114">Insira `http://localhost:3007/<yourDefaultAppNameTab>/` no navegador e exiba a página inicial do aplicativo:</span><span class="sxs-lookup"><span data-stu-id="2a20b-114">Enter `http://localhost:3007/<yourDefaultAppNameTab>/` in your browser and view your application's home page:</span></span>

![captura de tela da Home Page](~/assets/images/tab-images/homePage.png)