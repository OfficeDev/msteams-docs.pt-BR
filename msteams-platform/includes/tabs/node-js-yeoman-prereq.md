## <a name="prerequisites"></a><span data-ttu-id="61861-101">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="61861-101">Prerequisites</span></span>

- <span data-ttu-id="61861-102">Para concluir esse início rápido, você precisará de um locatário Office 365 e uma equipe configurada com Permitir o carregamento de *aplicativos personalizados* habilitados.</span><span class="sxs-lookup"><span data-stu-id="61861-102">To complete this quickstart you will need an Office 365 tenant and a team configured with *Allow uploading custom apps* enabled.</span></span> <span data-ttu-id="61861-103">Para saber mais, consulte [Prepare your Office 365 tenant](~/concepts/build-and-test/prepare-your-o365-tenant.md).</span><span class="sxs-lookup"><span data-stu-id="61861-103">To learn more, see [Prepare your Office 365 tenant](~/concepts/build-and-test/prepare-your-o365-tenant.md).</span></span>

  - <span data-ttu-id="61861-104">Se você não tiver uma conta Office 365, poderá inscrever-se para uma assinatura gratuita por meio do programa Office 365 Desenvolvedor.</span><span class="sxs-lookup"><span data-stu-id="61861-104">If you don't currently have an Office 365 account, you can sign up for a free subscription through the Office 365 Developer Program.</span></span> <span data-ttu-id="61861-105">A assinatura permanecerá ativa enquanto você a estiver usando para desenvolvimento contínuo.</span><span class="sxs-lookup"><span data-stu-id="61861-105">The subscription will remain active as long as you're using it for ongoing development.</span></span> <span data-ttu-id="61861-106">Consulte [Welcome to the Office 365 Developer Program](/office/developer-program/microsoft-365-developer-program).</span><span class="sxs-lookup"><span data-stu-id="61861-106">See [Welcome to the Office 365 Developer Program](/office/developer-program/microsoft-365-developer-program).</span></span>

<span data-ttu-id="61861-107">Além disso, este projeto exige que você tenha o seguinte instalado em seu ambiente de desenvolvimento:</span><span class="sxs-lookup"><span data-stu-id="61861-107">In addition, this project requires that you have the following installed in your development environment:</span></span>

- <span data-ttu-id="61861-108">Qualquer editor de texto ou IDE.</span><span class="sxs-lookup"><span data-stu-id="61861-108">Any text editor or IDE.</span></span> <span data-ttu-id="61861-109">Você pode instalar e usar [Visual Studio Code](https://code.visualstudio.com/download) gratuitamente.</span><span class="sxs-lookup"><span data-stu-id="61861-109">You can install and use [Visual Studio Code](https://code.visualstudio.com/download) for free.</span></span>

- <span data-ttu-id="61861-110">[Node.js/npm](https://nodejs.org/en/).</span><span class="sxs-lookup"><span data-stu-id="61861-110">[Node.js/npm](https://nodejs.org/en/).</span></span> <span data-ttu-id="61861-111">Você deve usar a versão LTS mais recente.</span><span class="sxs-lookup"><span data-stu-id="61861-111">You should use the latest LTS version.</span></span> <span data-ttu-id="61861-112">O nó Gerenciador de Pacotes (npm) será instalado em seu sistema com a instalação de Node.js.</span><span class="sxs-lookup"><span data-stu-id="61861-112">The Node Package Manager (npm) will install into your system with the installation of Node.js.</span></span>

- <span data-ttu-id="61861-113">Depois de instalar o Node.js, instale os pacotes [Yeoman](https://yeoman.io/) e [gulp-cli](https://www.npmjs.com/package/gulp-cli) digitando o seguinte no prompt de comando:</span><span class="sxs-lookup"><span data-stu-id="61861-113">After you've successfully installed Node.js, install the [Yeoman](https://yeoman.io/) and [gulp-cli](https://www.npmjs.com/package/gulp-cli) packages by typing the following in your command prompt:</span></span>

    ```bash
    npm install yo gulp-cli --global
    ```

- <span data-ttu-id="61861-114">Instale o Microsoft Teams aplicativos digitando o seguinte no prompt de comando:</span><span class="sxs-lookup"><span data-stu-id="61861-114">Install the Microsoft Teams Apps generator by typing the following in your command prompt:</span></span>

    ```bash
    npm install generator-teams --global
    ```

## <a name="generate-your-project"></a><span data-ttu-id="61861-115">Gerar seu projeto</span><span class="sxs-lookup"><span data-stu-id="61861-115">Generate your project</span></span>

- <span data-ttu-id="61861-116">Abra um prompt de comando e crie um novo diretório para seu projeto de guia.</span><span class="sxs-lookup"><span data-stu-id="61861-116">Open a command prompt and create a new directory for your tab project.</span></span>

- <span data-ttu-id="61861-117">Para iniciar o gerador, navegue até o novo diretório e digite o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="61861-117">To start the generator, navigate to your new directory and type the following command:</span></span>

    ```bash
    yo teams
    ```

- <span data-ttu-id="61861-118">Em seguida, você fornecerá uma série de valores que serão usados no arquivomanifest.js **no** aplicativo:</span><span class="sxs-lookup"><span data-stu-id="61861-118">Next, you'll provide a series of values that will be used in your application's **manifest.json** file:</span></span>

    ![captura de tela de abertura do gerador](/microsoftteams/platform/assets/images/tab-images/teamsTabScreenshot.PNG)

    <span data-ttu-id="61861-120">**Qual é o nome da solução?**</span><span class="sxs-lookup"><span data-stu-id="61861-120">**What is your solution name?**</span></span>

    <span data-ttu-id="61861-121">Esse é o nome do seu projeto.</span><span class="sxs-lookup"><span data-stu-id="61861-121">This is your project name.</span></span> <span data-ttu-id="61861-122">Você pode aceitar o nome sugerido pressionando enter.</span><span class="sxs-lookup"><span data-stu-id="61861-122">You can accept the suggested name by pressing enter.</span></span>

    <span data-ttu-id="61861-123">**Onde você deseja colocar os arquivos?**</span><span class="sxs-lookup"><span data-stu-id="61861-123">**Where do you want to place the files?**</span></span>

    <span data-ttu-id="61861-124">No momento, você está no diretório do projeto.</span><span class="sxs-lookup"><span data-stu-id="61861-124">You're currently in your project directory.</span></span> <span data-ttu-id="61861-125">Pressione Enter.</span><span class="sxs-lookup"><span data-stu-id="61861-125">Press enter.</span></span>

    <span data-ttu-id="61861-126">**Título do seu projeto Microsoft Teams aplicativo?**</span><span class="sxs-lookup"><span data-stu-id="61861-126">**Title of your Microsoft Teams app project?**</span></span>

    <span data-ttu-id="61861-127">Esse é o nome do pacote do aplicativo e será usado no manifesto e na descrição do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="61861-127">This is your app package name and will be used in the app manifest and description.</span></span>

    <span data-ttu-id="61861-128">**Seu nome (empresa) ? (máx. 32 caracteres)**</span><span class="sxs-lookup"><span data-stu-id="61861-128">**Your (company) name? (max 32 characters)**</span></span>

    <span data-ttu-id="61861-129">O nome da empresa será usado no manifesto do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="61861-129">Your company name will be used in the app manifest.</span></span>

    <span data-ttu-id="61861-130">**Qual versão de manifesto você gostaria de usar?**</span><span class="sxs-lookup"><span data-stu-id="61861-130">**Which manifest version would you like to use?**</span></span>

    <span data-ttu-id="61861-131">Selecione o esquema padrão.</span><span class="sxs-lookup"><span data-stu-id="61861-131">Select the default schema.</span></span>

    <span data-ttu-id="61861-132">**Scaffolding rápido? (Y/n)**</span><span class="sxs-lookup"><span data-stu-id="61861-132">**Quick scaffolding? (Y/n)**</span></span>

    <span data-ttu-id="61861-133">O padrão é sim; insira **n** para inserir sua ID do Microsoft Partner.</span><span class="sxs-lookup"><span data-stu-id="61861-133">The default is yes; enter **n** to enter your Microsoft Partner Id.</span></span>

    <span data-ttu-id="61861-134">**Insira sua ID do Microsoft Partner, se você tiver uma? (Deixe em branco para ignorar)**</span><span class="sxs-lookup"><span data-stu-id="61861-134">**Enter your Microsoft Partner Id, if you have one? (Leave blank to skip)**</span></span>

    <span data-ttu-id="61861-135">Esse campo não é obrigatório e só deve ser usado se você já faz parte da [Rede de Parceiros da Microsoft.](https://partner.microsoft.com)</span><span class="sxs-lookup"><span data-stu-id="61861-135">This field isn't required and should only be used if you're already part of the [Microsoft Partner Network](https://partner.microsoft.com).</span></span>

    <span data-ttu-id="61861-136">**O que você deseja adicionar ao seu projeto?**</span><span class="sxs-lookup"><span data-stu-id="61861-136">**What do you want to add to your project?**</span></span>

    <span data-ttu-id="61861-137">Selecione ( &ast; ) Uma guia.</span><span class="sxs-lookup"><span data-stu-id="61861-137">Select ( &ast; ) A Tab.</span></span>

    <span data-ttu-id="61861-138">**A URL onde você hospedará essa solução?**</span><span class="sxs-lookup"><span data-stu-id="61861-138">**The URL where you will host this solution?**</span></span>

    <span data-ttu-id="61861-139">Por padrão, o gerador sugere uma URL de Sites do Azure.</span><span class="sxs-lookup"><span data-stu-id="61861-139">By default the generator suggests an Azure Web Sites URL.</span></span> <span data-ttu-id="61861-140">Você só estará testando seu aplicativo localmente, portanto, uma URL válida não é necessária para concluir esse início rápido.</span><span class="sxs-lookup"><span data-stu-id="61861-140">You'll only be testing your app locally, therefore, a valid URL is not necessary to complete this quickstart.</span></span>

    <span data-ttu-id="61861-141">**Você gostaria de incluir a estrutura de teste e testes iniciais? (y/N)**</span><span class="sxs-lookup"><span data-stu-id="61861-141">**Would you like to include Test framework and initial tests? (y/N)**</span></span>

    <span data-ttu-id="61861-142">Escolha **não** incluir uma estrutura de teste para este projeto.</span><span class="sxs-lookup"><span data-stu-id="61861-142">Choose **not** to include a test framework for this project.</span></span> <span data-ttu-id="61861-143">O padrão é sim; enter **n**.</span><span class="sxs-lookup"><span data-stu-id="61861-143">The default is yes; enter **n**.</span></span>

    <span data-ttu-id="61861-144">**Você gostaria de usar o Azure Applications Insights para telemetria? (y/N)**</span><span class="sxs-lookup"><span data-stu-id="61861-144">**Would you like to use Azure Applications Insights for telemetry? (y/N)**</span></span>

    <span data-ttu-id="61861-145">Escolha **não incluir** o [Azure Application Insights.](/azure/azure-monitor/app/app-insights-overview)</span><span class="sxs-lookup"><span data-stu-id="61861-145">Choose **not** to include [Azure Application Insights](/azure/azure-monitor/app/app-insights-overview).</span></span> <span data-ttu-id="61861-146">O padrão é não; enter **n**.</span><span class="sxs-lookup"><span data-stu-id="61861-146">The default is no; enter **n**.</span></span>

    <span data-ttu-id="61861-147">**Nome da guia padrão (máx. 16 caracteres)?**</span><span class="sxs-lookup"><span data-stu-id="61861-147">**Default Tab Name (max 16 characters)?**</span></span>

    <span data-ttu-id="61861-148">Nomeia sua guia. Esse nome de guia será usado em todo o seu projeto como um componente de caminho de arquivo/URL.</span><span class="sxs-lookup"><span data-stu-id="61861-148">Name your tab. This tab name will be used throughout your project as a file/URL path component.</span></span>
