## <a name="prerequisites"></a><span data-ttu-id="92ac5-101">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="92ac5-101">Prerequisites</span></span>

- <span data-ttu-id="92ac5-102">Para completar este quickstart, você precisará de um inquilino Office 365 e uma equipe configurada com *Permitir o upload de aplicativos personalizados* ativados.</span><span class="sxs-lookup"><span data-stu-id="92ac5-102">To complete this quickstart you will need an Office 365 tenant and a team configured with *Allow uploading custom apps* enabled.</span></span> <span data-ttu-id="92ac5-103">Para saber mais, consulte [Prepare seu inquilino Office 365](~/concepts/build-and-test/prepare-your-o365-tenant.md).</span><span class="sxs-lookup"><span data-stu-id="92ac5-103">To learn more, see [Prepare your Office 365 tenant](~/concepts/build-and-test/prepare-your-o365-tenant.md).</span></span>

  - <span data-ttu-id="92ac5-104">Se você não tiver atualmente uma conta Office 365, você pode se inscrever para uma assinatura gratuita através do programa de desenvolvedor Office 365.</span><span class="sxs-lookup"><span data-stu-id="92ac5-104">If you don't currently have an Office 365 account, you can sign up for a free subscription through the Office 365 Developer Program.</span></span> <span data-ttu-id="92ac5-105">A assinatura permanecerá ativa enquanto você estiver usando-a para o desenvolvimento contínuo.</span><span class="sxs-lookup"><span data-stu-id="92ac5-105">The subscription will remain active as long as you're using it for ongoing development.</span></span> <span data-ttu-id="92ac5-106">Veja [Bem-vindo ao Programa de Desenvolvedores Office 365](/office/developer-program/microsoft-365-developer-program).</span><span class="sxs-lookup"><span data-stu-id="92ac5-106">See [Welcome to the Office 365 Developer Program](/office/developer-program/microsoft-365-developer-program).</span></span>

<span data-ttu-id="92ac5-107">Além disso, este projeto exige que você tenha o seguinte instalado em seu ambiente de desenvolvimento:</span><span class="sxs-lookup"><span data-stu-id="92ac5-107">In addition, this project requires that you have the following installed in your development environment:</span></span>

- <span data-ttu-id="92ac5-108">Qualquer editor de texto ou IDE.</span><span class="sxs-lookup"><span data-stu-id="92ac5-108">Any text editor or IDE.</span></span> <span data-ttu-id="92ac5-109">Você pode instalar e usar [Visual Studio Code](https://code.visualstudio.com/download) gratuitamente.</span><span class="sxs-lookup"><span data-stu-id="92ac5-109">You can install and use [Visual Studio Code](https://code.visualstudio.com/download) for free.</span></span>

- <span data-ttu-id="92ac5-110">[Node.js/npm](https://nodejs.org/en/).</span><span class="sxs-lookup"><span data-stu-id="92ac5-110">[Node.js/npm](https://nodejs.org/en/).</span></span> <span data-ttu-id="92ac5-111">Você deve usar a versão LTS mais recente.</span><span class="sxs-lookup"><span data-stu-id="92ac5-111">You should use the latest LTS version.</span></span> <span data-ttu-id="92ac5-112">O Node Gerenciador de Pacotes (npm) será instalado em seu sistema com a instalação de Node.js.</span><span class="sxs-lookup"><span data-stu-id="92ac5-112">The Node Package Manager (npm) will install into your system with the installation of Node.js.</span></span>

- <span data-ttu-id="92ac5-113">Depois de instalar com sucesso Node.js, instale os pacotes [Yeoman](https://yeoman.io/) e [gulp-cli](https://www.npmjs.com/package/gulp-cli) digitando o seguinte no seu prompt de comando:</span><span class="sxs-lookup"><span data-stu-id="92ac5-113">After you've successfully installed Node.js, install the [Yeoman](https://yeoman.io/) and [gulp-cli](https://www.npmjs.com/package/gulp-cli) packages by typing the following in your command prompt:</span></span>

    ```bash
    npm install yo gulp-cli --global
    ```

- <span data-ttu-id="92ac5-114">Instale o gerador de aplicativos Microsoft Teams digitando o seguinte no prompt de comando:</span><span class="sxs-lookup"><span data-stu-id="92ac5-114">Install the Microsoft Teams Apps generator by typing the following in your command prompt:</span></span>

    ```bash
    npm install generator-teams --global
    ```

## <a name="generate-your-project"></a><span data-ttu-id="92ac5-115">Gere seu projeto</span><span class="sxs-lookup"><span data-stu-id="92ac5-115">Generate your project</span></span>

- <span data-ttu-id="92ac5-116">Abra um prompt de comando e crie um novo diretório para o seu projeto de guia.</span><span class="sxs-lookup"><span data-stu-id="92ac5-116">Open a command prompt and create a new directory for your tab project.</span></span>

- <span data-ttu-id="92ac5-117">Para iniciar o gerador, navegue até o novo diretório e digite o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="92ac5-117">To start the generator, navigate to your new directory and type the following command:</span></span>

    ```bash
    yo teams
    ```

- <span data-ttu-id="92ac5-118">Em seguida, você fornecerá uma série de valores que serão usados nomanifest.jsdo seu aplicativo **no** arquivo:</span><span class="sxs-lookup"><span data-stu-id="92ac5-118">Next, you'll provide a series of values that will be used in your application's **manifest.json** file:</span></span>

    ![captura de tela de abertura do gerador](/microsoftteams/platform/assets/images/tab-images/teamsTabScreenshot.PNG)

    <span data-ttu-id="92ac5-120">**Qual é o nome da sua solução?**</span><span class="sxs-lookup"><span data-stu-id="92ac5-120">**What is your solution name?**</span></span>

    <span data-ttu-id="92ac5-121">Este é o nome do seu projeto.</span><span class="sxs-lookup"><span data-stu-id="92ac5-121">This is your project name.</span></span> <span data-ttu-id="92ac5-122">Você pode aceitar o nome sugerido pressionando enter.</span><span class="sxs-lookup"><span data-stu-id="92ac5-122">You can accept the suggested name by pressing enter.</span></span>

    <span data-ttu-id="92ac5-123">**Onde você deseja colocar os arquivos?**</span><span class="sxs-lookup"><span data-stu-id="92ac5-123">**Where do you want to place the files?**</span></span>

    <span data-ttu-id="92ac5-124">Você está no seu diretório de projetos.</span><span class="sxs-lookup"><span data-stu-id="92ac5-124">You're currently in your project directory.</span></span> <span data-ttu-id="92ac5-125">Pressione enter.</span><span class="sxs-lookup"><span data-stu-id="92ac5-125">Press enter.</span></span>

    <span data-ttu-id="92ac5-126">**Título do seu projeto de aplicativo Microsoft Teams?**</span><span class="sxs-lookup"><span data-stu-id="92ac5-126">**Title of your Microsoft Teams app project?**</span></span>

    <span data-ttu-id="92ac5-127">Este é o nome do seu pacote de aplicativo e será usado no manifesto e descrição do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="92ac5-127">This is your app package name and will be used in the app manifest and description.</span></span>

    <span data-ttu-id="92ac5-128">**Seu nome (empresa) ? (no máximo 32 caracteres)**</span><span class="sxs-lookup"><span data-stu-id="92ac5-128">**Your (company) name? (max 32 characters)**</span></span>

    <span data-ttu-id="92ac5-129">O nome da sua empresa será usado no manifesto do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="92ac5-129">Your company name will be used in the app manifest.</span></span>

    <span data-ttu-id="92ac5-130">**Qual versão manifesto você gostaria de usar?**</span><span class="sxs-lookup"><span data-stu-id="92ac5-130">**Which manifest version would you like to use?**</span></span>

    <span data-ttu-id="92ac5-131">Selecione o esquema padrão.</span><span class="sxs-lookup"><span data-stu-id="92ac5-131">Select the default schema.</span></span>

    <span data-ttu-id="92ac5-132">**Andaimes rápidos? (Y/n)**</span><span class="sxs-lookup"><span data-stu-id="92ac5-132">**Quick scaffolding? (Y/n)**</span></span>

    <span data-ttu-id="92ac5-133">O padrão é sim; enter **n** para inserir seu Microsoft Partner Id.</span><span class="sxs-lookup"><span data-stu-id="92ac5-133">The default is yes; enter **n** to enter your Microsoft Partner Id.</span></span>

    <span data-ttu-id="92ac5-134">**Digite seu Microsoft Partner Id, se você tiver um? (Deixe em branco para pular)**</span><span class="sxs-lookup"><span data-stu-id="92ac5-134">**Enter your Microsoft Partner Id, if you have one? (Leave blank to skip)**</span></span>

    <span data-ttu-id="92ac5-135">Este campo não é necessário e só deve ser usado se você já faz parte da [Microsoft Partner Network](https://partner.microsoft.com).</span><span class="sxs-lookup"><span data-stu-id="92ac5-135">This field isn't required and should only be used if you're already part of the [Microsoft Partner Network](https://partner.microsoft.com).</span></span>

    <span data-ttu-id="92ac5-136">**O que você quer adicionar ao seu projeto?**</span><span class="sxs-lookup"><span data-stu-id="92ac5-136">**What do you want to add to your project?**</span></span>

    <span data-ttu-id="92ac5-137">Selecione ( &ast; ) Uma guia.</span><span class="sxs-lookup"><span data-stu-id="92ac5-137">Select ( &ast; ) A Tab.</span></span>

    <span data-ttu-id="92ac5-138">**A URL onde você vai hospedar esta solução?**</span><span class="sxs-lookup"><span data-stu-id="92ac5-138">**The URL where you will host this solution?**</span></span>

    <span data-ttu-id="92ac5-139">Por padrão, o gerador sugere uma URL do Azure Web Sites.</span><span class="sxs-lookup"><span data-stu-id="92ac5-139">By default the generator suggests an Azure Web Sites URL.</span></span> <span data-ttu-id="92ac5-140">Você só estará testando seu aplicativo localmente, portanto, uma URL válida não é necessária para completar este quickstart.</span><span class="sxs-lookup"><span data-stu-id="92ac5-140">You'll only be testing your app locally, therefore, a valid URL is not necessary to complete this quickstart.</span></span>

    <span data-ttu-id="92ac5-141">**Gostaria de incluir a estrutura de teste e os testes iniciais? (y/N)**</span><span class="sxs-lookup"><span data-stu-id="92ac5-141">**Would you like to include Test framework and initial tests? (y/N)**</span></span>

    <span data-ttu-id="92ac5-142">Escolha **não** incluir uma estrutura de teste para este projeto.</span><span class="sxs-lookup"><span data-stu-id="92ac5-142">Choose **not** to include a test framework for this project.</span></span> <span data-ttu-id="92ac5-143">O padrão é sim; entrar **n**.</span><span class="sxs-lookup"><span data-stu-id="92ac5-143">The default is yes; enter **n**.</span></span>

    <span data-ttu-id="92ac5-144">**Deseja usar o Azure Applications Insights para telemetria? (y/N)**</span><span class="sxs-lookup"><span data-stu-id="92ac5-144">**Would you like to use Azure Applications Insights for telemetry? (y/N)**</span></span>

    <span data-ttu-id="92ac5-145">Escolha **não** incluir [insights de aplicativos do Azure](/azure-docs/articles/azure-monitor/app/app-insights-overview.md).</span><span class="sxs-lookup"><span data-stu-id="92ac5-145">Choose **not** to include [Azure Application Insights](/azure-docs/articles/azure-monitor/app/app-insights-overview.md).</span></span> <span data-ttu-id="92ac5-146">O padrão é não; entrar **n**.</span><span class="sxs-lookup"><span data-stu-id="92ac5-146">The default is no; enter **n**.</span></span>

    <span data-ttu-id="92ac5-147">**Nome da guia padrão (max 16 caracteres)?**</span><span class="sxs-lookup"><span data-stu-id="92ac5-147">**Default Tab Name (max 16 characters)?**</span></span>

    <span data-ttu-id="92ac5-148">Diga sua guia. Este nome da guia será usado em todo o seu projeto como um componente de caminho de arquivo/URL.</span><span class="sxs-lookup"><span data-stu-id="92ac5-148">Name your tab. This tab name will be used throughout your project as a file/URL path component.</span></span>
