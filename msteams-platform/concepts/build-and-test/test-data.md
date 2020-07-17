---
title: Adicionar dados de teste ao seu locatário de teste do Office 365
description: Configurar sua assinatura do programa de desenvolvedor do Office 365 para testes bem-sucedidos de aplicativos do Microsoft Teams
keywords: testando equipes do programa desenvolvedor de aplicativos
ms.date: 11/01/2019
ms.openlocfilehash: 87e9dc280c192f013098c3e9f604f72238bfafdf
ms.sourcegitcommit: fdc50183f3f4bec9e4b83bcfe5e016b591402f7c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/24/2020
ms.locfileid: "44867087"
---
# <a name="add-test-data-to-your-office-365-test-tenant"></a><span data-ttu-id="f9c14-104">Adicionar dados de teste ao seu locatário de teste do Office 365</span><span class="sxs-lookup"><span data-stu-id="f9c14-104">Add test data to your Office 365 test tenant</span></span>

<span data-ttu-id="f9c14-105">Configure sua assinatura do programa de desenvolvedor do O365 (ou outro locatário de teste) para facilitar o teste dos aplicativos que você criou.</span><span class="sxs-lookup"><span data-stu-id="f9c14-105">Set up your O365 developer program subscription (or other test tenant) to make it easy for you to test the apps that you've built.</span></span>  <span data-ttu-id="f9c14-106">Ele ajudará você a:</span><span class="sxs-lookup"><span data-stu-id="f9c14-106">It will help you:</span></span>

- <span data-ttu-id="f9c14-107">Criar novas equipes e canais em sua organização</span><span class="sxs-lookup"><span data-stu-id="f9c14-107">Create new teams and channels in your organization</span></span>

- <span data-ttu-id="f9c14-108">Adicione os usuários criados por meio do pacote de conteúdo do usuário a essas equipes.</span><span class="sxs-lookup"><span data-stu-id="f9c14-108">Add the users that are created via the User content pack to those teams.</span></span>

## <a name="before-you-start"></a><span data-ttu-id="f9c14-109">Antes de começar</span><span class="sxs-lookup"><span data-stu-id="f9c14-109">Before you start</span></span>

<span data-ttu-id="f9c14-110">Se você ainda não tem um locatário de teste, será necessário participar do programa de desenvolvedor do Office 365 e inscrever-se para uma assinatura de desenvolvedor.</span><span class="sxs-lookup"><span data-stu-id="f9c14-110">If you don't already have a test tenant, you will need to join the Office 365 developer program and sign up for a developer subscription.</span></span> <span data-ttu-id="f9c14-111">Você também precisará instalar os módulos do PowerShell necessários.</span><span class="sxs-lookup"><span data-stu-id="f9c14-111">You'll also need to install the necessary PowerShell modules.</span></span> <span data-ttu-id="f9c14-112">Para qualquer locatário que você usar, precisará ter permissões de administrador global para executar os scripts.</span><span class="sxs-lookup"><span data-stu-id="f9c14-112">For whatever tenant you use you'll need to have global administrator permissions to run the scripts.</span></span>

1. [<span data-ttu-id="f9c14-113">Ingressar no Programa para Desenvolvedores do Office 365</span><span class="sxs-lookup"><span data-stu-id="f9c14-113">Join the Office 365 Developer Program</span></span>](/office/developer-program/office-365-developer-program)
2. [<span data-ttu-id="f9c14-114">Configurar uma assinatura de desenvolvedor do Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="f9c14-114">Set up a Microsoft 365 Developer Subscription</span></span>](/office/developer-program/office-365-developer-program-get-started)
3. [<span data-ttu-id="f9c14-115">Usar pacotes de dados de exemplo com sua assinatura de desenvolvedor do Office 365 para instalar o pacote de conteúdo de usuários</span><span class="sxs-lookup"><span data-stu-id="f9c14-115">Use sample data packs with your Office 365 developer subscription to install the Users content pack</span></span>](/office/developer-program/install-sample-packs)
4. [<span data-ttu-id="f9c14-116">Instalar o módulo do teams PowerShell</span><span class="sxs-lookup"><span data-stu-id="f9c14-116">Install the Teams PowerShell module</span></span>](https://www.powershellgallery.com/packages/MicrosoftTeams/1.0.2)
5. [<span data-ttu-id="f9c14-117">Instalar o módulo PowerShell do Azure AD</span><span class="sxs-lookup"><span data-stu-id="f9c14-117">Install the Azure AD PowerShell module</span></span>](/powershell/azure/active-directory/install-adv2?view=azureadps-2.0#installing-the-azure-ad-module)

### <a name="optional-step-allow-upload-of-custom-apps"></a><span data-ttu-id="f9c14-118">Etapa opcional: permitir o carregamento de aplicativos personalizados</span><span class="sxs-lookup"><span data-stu-id="f9c14-118">Optional step: allow upload of custom apps</span></span>

<span data-ttu-id="f9c14-119">Por padrão, somente administradores globais ou administradores de serviços do teams podem carregar aplicativos personalizados no catálogo de aplicativos do locatário.</span><span class="sxs-lookup"><span data-stu-id="f9c14-119">By default, only global admins or teams service admins can upload custom apps into the tenant app catalog.</span></span>  <span data-ttu-id="f9c14-120">Você também pode permitir que todos os usuários carreguem aplicativos personalizados para uso próprio ou para o Microsoft Teams para testes.</span><span class="sxs-lookup"><span data-stu-id="f9c14-120">You can also enable all users to upload custom apps for their own use or to teams for testing.</span></span>

<span data-ttu-id="f9c14-121">Para habilitar essa configuração, você precisará atualizar a política de instalação do aplicativo global no portal de administração do Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="f9c14-121">To enable this setting, you'll need to update the global App Setup Policy in your Teams Admin Portal.</span></span>

<img width="430px" src="~/assets/images/microsoft-teams-admin-center-screenshot.png" title="Captura de tela da política de configuração de aplicativos" />

<span data-ttu-id="f9c14-123">Para obter mais informações, consulte:</span><span class="sxs-lookup"><span data-stu-id="f9c14-123">For more information see:</span></span>

 - [<span data-ttu-id="f9c14-124">Gerenciar políticas de configuração de aplicativos no Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="f9c14-124">Manage app setup policies in Microsoft Teams</span></span>](/microsoftteams/teams-app-setup-policies)

## <a name="create-teams-and-channels"></a><span data-ttu-id="f9c14-125">Criar equipes e canais</span><span class="sxs-lookup"><span data-stu-id="f9c14-125">Create teams and channels</span></span>

<span data-ttu-id="f9c14-126">Salve o seguinte trecho de código como XML (. xml) e anote onde você o salvou.</span><span class="sxs-lookup"><span data-stu-id="f9c14-126">Save the following snippet as an XML (.xml) and note where you've saved it.</span></span>  <span data-ttu-id="f9c14-127">Este XML define a estrutura das equipes e canais que serão criados-junto com seus membros.</span><span class="sxs-lookup"><span data-stu-id="f9c14-127">This XML defines the structure of the teams and channels that will be created - along with its members.</span></span>

```xml
<?xml version="1.0"?>
<Teams>
  <Team Name="Store Portal" ID="storeportal" Description="" Type="Private" Creator="admin">
    <Members>
      <Member UserName="AlexW" IsOwner="false"/>
      <Member UserName="PattiF" IsOwner="false"/>
      <Member UserName="PradeepG" IsOwner="false"/>
      <Member UserName="JoniS" IsOwner="false"/>
      <Member UserName="JohannaL" IsOwner="false"/>
      <Member UserName="NestorW" IsOwner="false"/>
      <Member UserName="IsaiahL" IsOwner="false"/>
      <Member UserName="AdeleV" IsOwner="false"/>
      <Member UserName="LeeG" IsOwner="false"/>
      <Member UserName="MeganB" IsOwner="true"/>
      <Member UserName="LynneR" IsOwner="false"/>
      <Member UserName="GradyA" IsOwner="false"/>
      <Member UserName="LidiaH" IsOwner="false"/>
      <Member UserName="DiegoS" IsOwner="false"/>
      <Member UserName="MiriamG" IsOwner="true"/>
    </Members>
    <Channels>
      <Channel Name="Sales" ID="sales" Description="" Creator="Admin" />
      <Channel Name="Inventory" ID="inventory" Description="" Creator="Admin" />
      <Channel Name="Los Angeles Store 239" ID="losangelesstore239" Description="" Creator="Admin" />
      <Channel Name="Seattle Store 121" ID="seattlestore121" Description="" Creator="Admin" />
      <Channel Name="Online" ID="online" Description="" Creator="Admin" />
      <Channel Name="Store Layout" ID="storelayout" Description="" Creator="Admin" />
      <Channel Name="Promotions" ID="promotions" Description="" Creator="Admin" />
    </Channels>
  </Team>
  <Team Name="Mark 8 Project Team" ID="Mark8ProjectTeam" Description="Welcome to the team that we've assembled to create the Mark 8." Type="Private" Creator="admin">
    <Members>
      <Member UserName="meganb" IsOwner="true" />
      <Member UserName="alexw" IsOwner="false" />
      <Member UserName="lynner" IsOwner="false" />
      <Member UserName="isaiahl" IsOwner="false" />
      <Member UserName="leeg" IsOwner="false" />
      <Member UserName="pradeepg" IsOwner="false" />
      <Member UserName="lidiah" IsOwner="false" />
      <Member UserName="diegos" IsOwner="false" />
      <Member UserName="johannal" IsOwner="false" />
      <Member UserName="miriamg" IsOwner="false" />
      <Member UserName="adelev" IsOwner="false" />
      <Member UserName="jonis" IsOwner="false" />
      <Member UserName="nestorw" IsOwner="false" />
      <Member UserName="gradya" IsOwner="false" />
      <Member UserName="pattif" IsOwner="false" />
    </Members>
    <Channels>
      <Channel Name="Research and Development" ID="researchanddevelopment" Description="Channel for Research and Development!" Creator="meganb" />
      <Channel Name="Design" ID="design" Description="Discuss design projects." Creator="meganb" />
      <Channel Name="Digital Assets Web" ID="digitalassetsweb" Description="Discuss digital assets." Creator="meganb" />
      <Channel Name="Go to Market Plan" ID="gotomarketplan" Description="Our go-to-market plan!" Creator="meganb" />
    </Channels>
  </Team>
  <Team Name="District 9 Road Safety Audit" ID="district9roadsafetyaudit" Description="" Type="Private" Creator="admin">
    <Members>
      <Member UserName="meganb" IsOwner="true" />
      <Member UserName="alexw" IsOwner="false" />
      <Member UserName="lynner" IsOwner="false" />
      <Member UserName="isaiahl" IsOwner="false" />
      <Member UserName="leeg" IsOwner="false" />
      <Member UserName="pradeepg" IsOwner="false" />
      <Member UserName="lidiah" IsOwner="false" />
      <Member UserName="diegos" IsOwner="false" />
      <Member UserName="johannal" IsOwner="false" />
      <Member UserName="miriamg" IsOwner="false" />
      <Member UserName="adelev" IsOwner="false" />
      <Member UserName="jonis" IsOwner="false" />
      <Member UserName="nestorw" IsOwner="false" />
      <Member UserName="gradya" IsOwner="false" />
      <Member UserName="pattif" IsOwner="false" />
    </Members>
    <Channels>
      <Channel Name="Audit Planning" ID="auditplanning" Description="" Creator="Admin" />
      <Channel Name="Delivery" ID="delivery" Description="" Creator="Admin" />
      <Channel Name="Findings" ID="findings" Description="" Creator="Admin" />
      <Channel Name="Recommended Actions" ID="recommendedactions" Description="" Creator="Admin" />
      <Channel Name="Survey" ID="survey" Description="" Creator="Admin" />
    </Channels>
  </Team>
  <Team Name="ACC-1000 Product Team" ID="acc1000productteam" Description="" Type="Private" Creator="admin" >
    <Members>
      <Member UserName="meganb" IsOwner="true" />
      <Member UserName="alexw" IsOwner="false" />
      <Member UserName="lynner" IsOwner="false" />
      <Member UserName="isaiahl" IsOwner="false" />
      <Member UserName="leeg" IsOwner="false" />
      <Member UserName="pradeepg" IsOwner="false" />
      <Member UserName="lidiah" IsOwner="false" />
      <Member UserName="diegos" IsOwner="false" />
      <Member UserName="johannal" IsOwner="false" />
      <Member UserName="miriamg" IsOwner="false" />
      <Member UserName="adelev" IsOwner="false" />
      <Member UserName="jonis" IsOwner="false" />
      <Member UserName="nestorw" IsOwner="false" />
      <Member UserName="gradya" IsOwner="false" />
      <Member UserName="pattif" IsOwner="false" />
    </Members>
    <Channels>
      <Channel Name="Corporate Communication" ID="corporatecommunication" Description="" Creator="Admin" />
      <Channel Name="Lean Process Improvement" ID="corporatecommunication" Description="" Creator="Admin" />
      <Channel Name="Training and Certification" ID="trainingandcertification" Description="" Creator="Admin" />
      <Channel Name="Production" ID="production" Description="" Creator="Admin" />
      <Channel Name="Research and Development" ID="researchanddevelopment" Description="" Creator="Admin" />
      <Channel Name="Supplier Collaboration" ID="suppliercollaboration" Description="" Creator="Admin" />
    </Channels>
  </Team>
</Teams>
```

<span data-ttu-id="f9c14-128">Salve o trecho de código a seguir como um script do PowerShell (. ps1) e anote onde você o salvou.</span><span class="sxs-lookup"><span data-stu-id="f9c14-128">Save the following snippet as a PowerShell script (.ps1) and note where you've saved it.</span></span>  <span data-ttu-id="f9c14-129">Este script executa as etapas para criar equipes e canais e adicionar membros a eles.</span><span class="sxs-lookup"><span data-stu-id="f9c14-129">This script executes the steps to create the teams and channels and add members to them.</span></span>

```powershell
Param(
    [Parameter(Mandatory = $true)]
    
    # This specifies the location of your configuration XML.
    
    [string] $teamsFilePath 
)
    
[xml]$XmlDocument = Get-Content -Path $teamsFilePath.ToString()

if ($XmlDocument.Teams.Team.Count -gt 0) {

    try {
        
        # 1. Login with the global administrator account for your O365 Developer Program tenant.  This script will then use these credentials to connect to the powershell modules for Azure Active Directory and Microsoft Teams
        
        $creds = Get-Credential

        # Connecting to AAD PowerShell
        Connect-AzureAD -Credential $creds | Out-Null

        # Connect to Microsoft Teams PowerShell
        Connect-MicrosoftTeams -Credential $creds | Out-Null

        Write-Host "Connected to Microsoft 365 and configuring your organization with test teams and channels"

        # 2. Create the teams as specified in the XML.
        
        foreach ($team in $XmlDocument.Teams.Team ) {
            try {
                $group = New-Team -DisplayName $team.Name -Description $teams.description -visibility public 
                Write-Host "Successfully created team: " $group.DisplayName
            }
            catch {
                Write-Host "Unable to create team: $_"
            }
                
            # 3. Add users to the newly created teams.
            foreach ($user in $team.Members.Member) {
                try {
                    $newUserPrincipalName = (Get-AzureADUser -SearchString $user.UserName).UserPrincipalName

                    if($user.IsOwner -eq $true){
                        Add-TeamUser -GroupId $group.GroupId -User $newUserPrincipalName -Role Owner | Out-Null
                    }else{
                        Add-TeamUser -GroupId $group.GroupId -User $newUserPrincipalName | Out-Null
                    }

                    Write-Host "Successfully added user : " $user.UserName
                }
                catch {
                    Write-Host "Unable to add team user: $_"
                }

            }

            # 4. Add a set of channels to each newly created team
            foreach ($channel in $team.Channels.Channel) {
                try {
                    # Adding each team channel
                    New-TeamChannel -GroupId $group.GroupId -DisplayName $channel.Name -Description $channel.Description | Out-Null
                    Write-Host "Successfully created channel: " $channel.Name
                }
                catch {
                    Write-Host "Unable to add new Team Channel: $_"
                }   
            }

            Clear-Variable -Name group
        }

        Clear-Variable -Name creds
        
        # 5. Disconnect from all PowerShell sessions
        
        Write-Host "Completed execution and disconnecting from Microsoft 365 PowerShell sessions."
        Disconnect-MicrosoftTeams
        Disconnect-AzureAD
    }
    catch {
        Write-Host "Unable to complete the operation: $_"
    }
}
else {
    Write-Host "Content file has invalid data."
}
```

<span data-ttu-id="f9c14-130">Abra uma sessão do Windows PowerShell no modo do administrador.</span><span class="sxs-lookup"><span data-stu-id="f9c14-130">Open a Windows PowerShell session in Administrator mode.</span></span>  <span data-ttu-id="f9c14-131">Execute o script que você acabou de salvar.</span><span class="sxs-lookup"><span data-stu-id="f9c14-131">Run the script that you just saved.</span></span>  <span data-ttu-id="f9c14-132">Você será solicitado a fornecer as credenciais – use as credenciais de administrador global que você recebeu quando se inscreveu pela primeira vez em sua assinatura de desenvolvedor.</span><span class="sxs-lookup"><span data-stu-id="f9c14-132">You'll be prompted to provide the credentials - use the Global Administrator credentials you received when you first signed up for your developer subscription.</span></span>

> [!Note]
> <span data-ttu-id="f9c14-133">O script levará vários minutos para executar-não fechar a sessão do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f9c14-133">The script will take several minutes to execute - do not close your PowerShell session.</span></span>  <span data-ttu-id="f9c14-134">Se você modificou os usuários em sua assinatura do que foi criado no pacote de conteúdo padrão, alguns usuários podem não ser adicionados ao Teams.</span><span class="sxs-lookup"><span data-stu-id="f9c14-134">If you've modified the users in your subscription from what is created in the default content pack, some users may not be added to teams.</span></span>  <span data-ttu-id="f9c14-135">À medida que o script é executado, ocorrerá a saída de ações bem-sucedidas ou com falha.</span><span class="sxs-lookup"><span data-stu-id="f9c14-135">As the script executes it will output successful or failed actions.</span></span>

<span data-ttu-id="f9c14-136">Após a execução do script, você pode fazer logon no cliente do Microsoft Teams com uma das contas de usuário e exibir as equipes recém-criadas.</span><span class="sxs-lookup"><span data-stu-id="f9c14-136">Once the script has finished execution, you can login to the Teams client with one of the user accounts and view the newly created teams.</span></span>
