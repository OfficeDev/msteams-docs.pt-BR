## <a name="prerequisites"></a><span data-ttu-id="e1c4c-101">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="e1c4c-101">Prerequisites</span></span>

- <span data-ttu-id="e1c4c-102">Para concluir este QuickStart, você precisará de um locatário do Office 365 e de uma equipe configurada para *permitir o carregamento de aplicativos personalizados* habilitados.</span><span class="sxs-lookup"><span data-stu-id="e1c4c-102">To complete this quickstart you will need an Office 365 tenant and a team configured with *Allow uploading custom apps* enabled.</span></span> <span data-ttu-id="e1c4c-103">Para saber mais, confira [preparar seu locatário do Office 365](~/concepts/build-and-test/prepare-your-o365-tenant.md).</span><span class="sxs-lookup"><span data-stu-id="e1c4c-103">To learn more, see [Prepare your Office 365 tenant](~/concepts/build-and-test/prepare-your-o365-tenant.md).</span></span>

  - <span data-ttu-id="e1c4c-104">Se você não tiver uma conta do Office 365, você poderá inscrever-se em uma assinatura gratuita por meio do programa de desenvolvedor do Office 365.</span><span class="sxs-lookup"><span data-stu-id="e1c4c-104">If you don't currently have an Office 365 account, you can sign up for a free subscription through the Office 365 Developer Program.</span></span> <span data-ttu-id="e1c4c-105">A assinatura permanecerá ativa, contanto que você esteja usando-a para desenvolvimento contínuo.</span><span class="sxs-lookup"><span data-stu-id="e1c4c-105">The subscription will remain active as long as you're using it for ongoing development.</span></span> <span data-ttu-id="e1c4c-106">Confira [Bem-vindo ao programa para desenvolvedores do Office 365](/OfficeDev/office-dev-program-docs/docs/office-365-developer-program.md).</span><span class="sxs-lookup"><span data-stu-id="e1c4c-106">See [Welcome to the Office 365 Developer Program](/OfficeDev/office-dev-program-docs/docs/office-365-developer-program.md).</span></span>

<span data-ttu-id="e1c4c-107">Além disso, este projeto requer que você tenha o seguinte instalado em seu ambiente de desenvolvimento:</span><span class="sxs-lookup"><span data-stu-id="e1c4c-107">In addition, this project requires that you have the following installed in your development environment:</span></span>

- <span data-ttu-id="e1c4c-108">Qualquer editor de texto ou IDE.</span><span class="sxs-lookup"><span data-stu-id="e1c4c-108">Any text editor or IDE.</span></span> <span data-ttu-id="e1c4c-109">Você pode instalar e usar o [Visual Studio Code](https://code.visualstudio.com/download) gratuitamente.</span><span class="sxs-lookup"><span data-stu-id="e1c4c-109">You can install and use [Visual Studio Code](https://code.visualstudio.com/download) for free.</span></span>

- <span data-ttu-id="e1c4c-110">[Node. js/NPM](https://nodejs.org/en/).</span><span class="sxs-lookup"><span data-stu-id="e1c4c-110">[Node.js/npm](https://nodejs.org/en/).</span></span> <span data-ttu-id="e1c4c-111">Você deve usar a versão mais recente do LTS.</span><span class="sxs-lookup"><span data-stu-id="e1c4c-111">You should use the latest LTS version.</span></span> <span data-ttu-id="e1c4c-112">O Gerenciador de pacotes de nó (NPM) será instalado no seu sistema com a instalação do node. js.</span><span class="sxs-lookup"><span data-stu-id="e1c4c-112">The Node Package Manager (npm) will install into your system with the installation of Node.js.</span></span>

- <span data-ttu-id="e1c4c-113">Depois de instalar o Node. js com êxito, instale os pacotes do [Yeoman](https://yeoman.io/) e do [Gulp-CLI](https://www.npmjs.com/package/gulp-cli) digitando o seguinte no prompt de comando:</span><span class="sxs-lookup"><span data-stu-id="e1c4c-113">After you've successfully installed Node.js, install the [Yeoman](https://yeoman.io/) and [gulp-cli](https://www.npmjs.com/package/gulp-cli) packages by typing the following in your command prompt:</span></span>

```bash
npm install yo gulp-cli --global
```

- <span data-ttu-id="e1c4c-114">Instale o gerador de aplicativos do Microsoft Teams digitando o seguinte no prompt de comando:</span><span class="sxs-lookup"><span data-stu-id="e1c4c-114">Install the Microsoft Teams Apps generator by typing the following in your command prompt:</span></span>

```bash
npm install generator-teams --global
```

## <a name="generate-your-project"></a><span data-ttu-id="e1c4c-115">Gerar seu projeto</span><span class="sxs-lookup"><span data-stu-id="e1c4c-115">Generate your project</span></span>

- <span data-ttu-id="e1c4c-116">Abra um prompt de comando e crie um novo diretório para o projeto de tabulação.</span><span class="sxs-lookup"><span data-stu-id="e1c4c-116">Open a command prompt and create a new directory for your tab project.</span></span>

- <span data-ttu-id="e1c4c-117">Para iniciar o gerador, navegue até o novo diretório e digite o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="e1c4c-117">To start the generator, navigate to your new directory and type the following command:</span></span>

```bash
yo teams
```

- <span data-ttu-id="e1c4c-118">Em seguida, você fornecerá uma série de valores que serão usados no arquivo **manifest. JSON** do aplicativo:</span><span class="sxs-lookup"><span data-stu-id="e1c4c-118">Next, you'll provide a series of values that will be used in your application's **manifest.json** file:</span></span>

![captura de tela de abertura do gerador](/microsoftteams/platform/assets/images/tab-images/teamsTabScreenshot.PNG)

<span data-ttu-id="e1c4c-120">**Qual é o nome da sua solução?**</span><span class="sxs-lookup"><span data-stu-id="e1c4c-120">**What is your solution name?**</span></span>

<span data-ttu-id="e1c4c-121">Este é o nome do projeto.</span><span class="sxs-lookup"><span data-stu-id="e1c4c-121">This is your project name.</span></span> <span data-ttu-id="e1c4c-122">Você pode aceitar o nome sugerido pressionando ENTER.</span><span class="sxs-lookup"><span data-stu-id="e1c4c-122">You can accept the suggested name by pressing enter.</span></span>

<span data-ttu-id="e1c4c-123">**Onde você deseja colocar os arquivos?**</span><span class="sxs-lookup"><span data-stu-id="e1c4c-123">**Where do you want to place the files?**</span></span>

<span data-ttu-id="e1c4c-124">No momento, você está no diretório do projeto.</span><span class="sxs-lookup"><span data-stu-id="e1c4c-124">You're currently in your project directory.</span></span> <span data-ttu-id="e1c4c-125">Pressione Enter.</span><span class="sxs-lookup"><span data-stu-id="e1c4c-125">Press enter.</span></span>

<span data-ttu-id="e1c4c-126">**Título do seu projeto de aplicativo do Microsoft Teams?**</span><span class="sxs-lookup"><span data-stu-id="e1c4c-126">**Title of your Microsoft Teams app project?**</span></span>

<span data-ttu-id="e1c4c-127">Este é o nome do pacote de aplicativos e será usado no manifesto do aplicativo e na descrição.</span><span class="sxs-lookup"><span data-stu-id="e1c4c-127">This is your app package name and will be used in the app manifest and description.</span></span>

<span data-ttu-id="e1c4c-128">**Seu nome (empresa)? (máximo de 32 caracteres)**</span><span class="sxs-lookup"><span data-stu-id="e1c4c-128">**Your (company) name? (max 32 characters)**</span></span>

<span data-ttu-id="e1c4c-129">O nome da sua empresa será usado no manifesto do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="e1c4c-129">Your company name will be used in the app manifest.</span></span>

<br><span data-ttu-id="e1c4c-130">**Qual versão do manifesto você gostaria de usar?**</span><span class="sxs-lookup"><span data-stu-id="e1c4c-130">**Which manifest version would you like to use?**</span></span>

<span data-ttu-id="e1c4c-131">Selecione o esquema padrão.</span><span class="sxs-lookup"><span data-stu-id="e1c4c-131">Select the default schema.</span></span>

<span data-ttu-id="e1c4c-132">**Insira sua ID de parceiro da Microsoft, se você tiver uma? (Deixe em branco para ignorar)**</span><span class="sxs-lookup"><span data-stu-id="e1c4c-132">**Enter your Microsoft Partner Id, if you have one? (Leave blank to skip)**</span></span>

<span data-ttu-id="e1c4c-133">Este campo não é obrigatório e só deve ser usado se você já faz parte da [rede de parceiros da Microsoft](https://partner.microsoft.com).</span><span class="sxs-lookup"><span data-stu-id="e1c4c-133">This field isn't required and should only be used if you're already part of the [Microsoft Partner Network](https://partner.microsoft.com).</span></span>

<span data-ttu-id="e1c4c-134">**O que você deseja adicionar ao seu projeto?**</span><span class="sxs-lookup"><span data-stu-id="e1c4c-134">**What do you want to add to your project?**</span></span>

<span data-ttu-id="e1c4c-135">Selecione ( &ast; ) uma tabulação.</span><span class="sxs-lookup"><span data-stu-id="e1c4c-135">Select ( &ast; ) A Tab.</span></span>

<span data-ttu-id="e1c4c-136">**A URL na qual você hospedará esta solução?**</span><span class="sxs-lookup"><span data-stu-id="e1c4c-136">**The URL where you will host this solution?**</span></span>

<span data-ttu-id="e1c4c-137">Por padrão, o gerador sugere uma URL de sites do Azure.</span><span class="sxs-lookup"><span data-stu-id="e1c4c-137">By default the generator suggests an Azure Web Sites URL.</span></span> <span data-ttu-id="e1c4c-138">Você só testará seu aplicativo localmente, portanto, uma URL válida não é necessária para concluir este QuickStart.</span><span class="sxs-lookup"><span data-stu-id="e1c4c-138">You'll only be testing your app locally, therefore, a valid URL is not necessary to complete this quickstart.</span></span>

<span data-ttu-id="e1c4c-139">**Deseja incluir a estrutura de teste e os testes iniciais? (s/N)**</span><span class="sxs-lookup"><span data-stu-id="e1c4c-139">**Would you like to include Test framework and initial tests? (y/N)**</span></span>

<span data-ttu-id="e1c4c-140">Escolha **não** incluir uma estrutura de teste para este projeto.</span><span class="sxs-lookup"><span data-stu-id="e1c4c-140">Choose **not** to include a test framework for this project.</span></span> <span data-ttu-id="e1c4c-141">O padrão é sim; Digite **n**.</span><span class="sxs-lookup"><span data-stu-id="e1c4c-141">The default is yes; enter **n**.</span></span>

<span data-ttu-id="e1c4c-142">**Gostaria de usar o Azure Application insights para telemetria? (s/N)**</span><span class="sxs-lookup"><span data-stu-id="e1c4c-142">**Would you like to use Azure Applications Insights for telemetry? (y/N)**</span></span>

<span data-ttu-id="e1c4c-143">Escolha **não** incluir o [Azure Application insights](/azure-docs/articles/azure-monitor/app/app-insights-overview.md).</span><span class="sxs-lookup"><span data-stu-id="e1c4c-143">Choose **not** to include [Azure Application Insights](/azure-docs/articles/azure-monitor/app/app-insights-overview.md).</span></span> <span data-ttu-id="e1c4c-144">O padrão é não; Digite **n**.</span><span class="sxs-lookup"><span data-stu-id="e1c4c-144">The default is no; enter **n**.</span></span>

<span data-ttu-id="e1c4c-145">**Nome da guia padrão (máximo de 16 caracteres)?**</span><span class="sxs-lookup"><span data-stu-id="e1c4c-145">**Default Tab Name (max 16 characters)?**</span></span>

<span data-ttu-id="e1c4c-146">Nomeie sua guia. Este nome de guia será usado em todo o projeto como um componente de caminho de arquivo/URL.</span><span class="sxs-lookup"><span data-stu-id="e1c4c-146">Name your tab. This tab name will be used throughout your project as a file/URL path component.</span></span>
