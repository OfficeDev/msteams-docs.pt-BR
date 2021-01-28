---
title: Adicionar dados de teste ao locatário de teste do Office 365
description: Configurar sua assinatura do programa de desenvolvedor do Office 365 para testes bem-sucedidos dos Aplicativos do Microsoft Teams
ms.topic: how-to
keywords: testar equipes do programa para desenvolvedores de aplicativos
ms.date: 11/01/2019
ms.openlocfilehash: 97eeb9c35b22adf75ad7f630fb2a621f0330e060
ms.sourcegitcommit: 976e870cc925f61b76c3830ec04ba6e4bdfde32f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/27/2021
ms.locfileid: "50014436"
---
# <a name="add-test-data-to-your-office-365-test-tenant"></a><span data-ttu-id="8f24e-104">Adicionar dados de teste ao locatário de teste do Office 365</span><span class="sxs-lookup"><span data-stu-id="8f24e-104">Add test data to your Office 365 test tenant</span></span>

<span data-ttu-id="8f24e-105">Configurar sua assinatura do programa de desenvolvedor do O365 (ou outro locatário de teste) para facilitar o teste dos aplicativos que você criou.</span><span class="sxs-lookup"><span data-stu-id="8f24e-105">Set up your O365 developer program subscription (or other test tenant) to make it easy for you to test the apps that you've built.</span></span>  <span data-ttu-id="8f24e-106">Isso ajudará você a:</span><span class="sxs-lookup"><span data-stu-id="8f24e-106">It will help you:</span></span>

- <span data-ttu-id="8f24e-107">Criar novas equipes e canais em sua organização</span><span class="sxs-lookup"><span data-stu-id="8f24e-107">Create new teams and channels in your organization</span></span>

- <span data-ttu-id="8f24e-108">Adicione os usuários criados por meio do pacote de conteúdo do Usuário a essas equipes.</span><span class="sxs-lookup"><span data-stu-id="8f24e-108">Add the users that are created via the User content pack to those teams.</span></span>

## <a name="before-you-start"></a><span data-ttu-id="8f24e-109">Antes de começar</span><span class="sxs-lookup"><span data-stu-id="8f24e-109">Before you start</span></span>

<span data-ttu-id="8f24e-110">Se você ainda não tiver um locatário de teste, precisará ingressar no programa de desenvolvedor do Office 365 e se inscrever para uma assinatura de desenvolvedor.</span><span class="sxs-lookup"><span data-stu-id="8f24e-110">If you don't already have a test tenant, you will need to join the Office 365 developer program and sign up for a developer subscription.</span></span> <span data-ttu-id="8f24e-111">Você também precisará instalar os módulos do PowerShell necessários.</span><span class="sxs-lookup"><span data-stu-id="8f24e-111">You'll also need to install the necessary PowerShell modules.</span></span> <span data-ttu-id="8f24e-112">Para qualquer locatário que você usar, você precisará ter permissões de administrador global para executar os scripts.</span><span class="sxs-lookup"><span data-stu-id="8f24e-112">For whatever tenant you use you'll need to have global administrator permissions to run the scripts.</span></span>

1. [<span data-ttu-id="8f24e-113">Ingressar no Programa para Desenvolvedores do Office 365</span><span class="sxs-lookup"><span data-stu-id="8f24e-113">Join the Office 365 Developer Program</span></span>](/office/developer-program/office-365-developer-program)
2. [<span data-ttu-id="8f24e-114">Configurar uma assinatura de desenvolvedor do Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="8f24e-114">Set up a Microsoft 365 Developer Subscription</span></span>](/office/developer-program/office-365-developer-program-get-started)
3. [<span data-ttu-id="8f24e-115">Usar pacotes de dados de exemplo com sua assinatura de desenvolvedor do Office 365 para instalar o pacote de conteúdo Usuários</span><span class="sxs-lookup"><span data-stu-id="8f24e-115">Use sample data packs with your Office 365 developer subscription to install the Users content pack</span></span>](/office/developer-program/install-sample-packs)
4. [<span data-ttu-id="8f24e-116">Instalar o módulo do PowerShell do Teams</span><span class="sxs-lookup"><span data-stu-id="8f24e-116">Install the Teams PowerShell module</span></span>](https://www.powershellgallery.com/packages/MicrosoftTeams/1.0.2)
5. [<span data-ttu-id="8f24e-117">Instalar o módulo do PowerShell do Azure AD</span><span class="sxs-lookup"><span data-stu-id="8f24e-117">Install the Azure AD PowerShell module</span></span>](/powershell/azure/active-directory/install-adv2?view=azureadps-2.0#installing-the-azure-ad-module)

### <a name="optional-step-allow-upload-of-custom-apps"></a><span data-ttu-id="8f24e-118">Etapa opcional: permitir o carregamento de aplicativos personalizados</span><span class="sxs-lookup"><span data-stu-id="8f24e-118">Optional step: allow upload of custom apps</span></span>

<span data-ttu-id="8f24e-119">Por padrão, somente administradores globais ou administradores de serviço de equipes podem carregar aplicativos personalizados no catálogo de aplicativos do locatário.</span><span class="sxs-lookup"><span data-stu-id="8f24e-119">By default, only global admins or teams service admins can upload custom apps into the tenant app catalog.</span></span>  <span data-ttu-id="8f24e-120">Você também pode permitir que todos os usuários carreguem aplicativos personalizados para seu próprio uso ou para equipes para teste.</span><span class="sxs-lookup"><span data-stu-id="8f24e-120">You can also enable all users to upload custom apps for their own use or to teams for testing.</span></span>

<span data-ttu-id="8f24e-121">Para habilitar essa configuração, você precisará atualizar a Política de Configuração de Aplicativo global no Portal de Administração do Teams.</span><span class="sxs-lookup"><span data-stu-id="8f24e-121">To enable this setting, you'll need to update the global App Setup Policy in your Teams Admin Portal.</span></span>

<img width="430px" src="~/assets/images/microsoft-teams-admin-center-screenshot.png" title="Captura de tela da política de configuração do aplicativo" />

<span data-ttu-id="8f24e-123">Para obter mais informações, consulte:</span><span class="sxs-lookup"><span data-stu-id="8f24e-123">For more information see:</span></span>

 - [<span data-ttu-id="8f24e-124">Gerenciar políticas de configuração de aplicativo no Teams</span><span class="sxs-lookup"><span data-stu-id="8f24e-124">Manage app setup policies in Microsoft Teams</span></span>](/microsoftteams/teams-app-setup-policies)

## <a name="create-teams-and-channels"></a><span data-ttu-id="8f24e-125">Criar equipes e canais</span><span class="sxs-lookup"><span data-stu-id="8f24e-125">Create teams and channels</span></span>

<span data-ttu-id="8f24e-126">Salve o trecho de código a seguir como um XML (.xml) e observe onde você o salvou.</span><span class="sxs-lookup"><span data-stu-id="8f24e-126">Save the following snippet as an XML (.xml) and note where you've saved it.</span></span>  <span data-ttu-id="8f24e-127">Esse XML define a estrutura das equipes e canais que serão criados, juntamente com seus membros.</span><span class="sxs-lookup"><span data-stu-id="8f24e-127">This XML defines the structure of the teams and channels that will be created - along with its members.</span></span>

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

<span data-ttu-id="8f24e-128">Salve o trecho de código a seguir como um script do PowerShell (.ps1) e observe onde você o salvou.</span><span class="sxs-lookup"><span data-stu-id="8f24e-128">Save the following snippet as a PowerShell script (.ps1) and note where you've saved it.</span></span>  <span data-ttu-id="8f24e-129">Esse script executa as etapas para criar equipes e canais e adicionar membros a elas.</span><span class="sxs-lookup"><span data-stu-id="8f24e-129">This script executes the steps to create the teams and channels and add members to them.</span></span>

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

<span data-ttu-id="8f24e-130">Abra uma sessão do Windows PowerShell no modo Administrador.</span><span class="sxs-lookup"><span data-stu-id="8f24e-130">Open a Windows PowerShell session in Administrator mode.</span></span>  <span data-ttu-id="8f24e-131">Execute o script que você acabou de salvar.</span><span class="sxs-lookup"><span data-stu-id="8f24e-131">Run the script that you just saved.</span></span>  <span data-ttu-id="8f24e-132">Você será solicitado a fornecer as credenciais: use as credenciais de Administrador Global recebidas quando se inscreveu pela primeira vez em sua assinatura de desenvolvedor.</span><span class="sxs-lookup"><span data-stu-id="8f24e-132">You'll be prompted to provide the credentials - use the Global Administrator credentials you received when you first signed up for your developer subscription.</span></span>

> [!Note]
> <span data-ttu-id="8f24e-133">O script levará vários minutos para ser executado. Não feche sua sessão do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="8f24e-133">The script will take several minutes to execute - do not close your PowerShell session.</span></span>  <span data-ttu-id="8f24e-134">Se você modificou os usuários em sua assinatura do que é criado no pacote de conteúdo padrão, alguns usuários podem não ser adicionados às equipes.</span><span class="sxs-lookup"><span data-stu-id="8f24e-134">If you've modified the users in your subscription from what is created in the default content pack, some users may not be added to teams.</span></span>  <span data-ttu-id="8f24e-135">À medida que o script for executado, as ações bem-sucedidas ou com falha serão executadas.</span><span class="sxs-lookup"><span data-stu-id="8f24e-135">As the script executes it will output successful or failed actions.</span></span>

<span data-ttu-id="8f24e-136">Depois que o script terminar a execução, você poderá fazer logon no cliente do Teams com uma das contas de usuário e exibir as equipes recém-criadas.</span><span class="sxs-lookup"><span data-stu-id="8f24e-136">Once the script has finished execution, you can login to the Teams client with one of the user accounts and view the newly created teams.</span></span>
