---
title: Adicionar dados de teste ao locatário de teste do Microsoft 365
description: Configurar sua assinatura de programa de desenvolvedor do Office 365 para testes bem-sucedidos do Microsoft Teams Apps
ms.topic: how-to
keywords: testar equipes de programa de desenvolvedores de aplicativos
ms.date: 11/01/2019
ms.openlocfilehash: 9e23b9054f45ccff6c08b97c72f4d5375fef58ea
ms.sourcegitcommit: 5b3ba227c2e5e6f7a2c629961993f168da6a504d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2021
ms.locfileid: "51634717"
---
# <a name="add-test-data-to-your-microsoft-365-test-tenant"></a><span data-ttu-id="e27a0-104">Adicionar dados de teste ao locatário de teste do Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="e27a0-104">Add test data to your Microsoft 365 test tenant</span></span>

<span data-ttu-id="e27a0-105">Com uma assinatura de desenvolvedor do Microsoft 365, você pode usar seu aplicativo do Microsoft Teams com equipes de teste, canais e usuários.</span><span class="sxs-lookup"><span data-stu-id="e27a0-105">With a Microsoft 365 developer subscription, you can use your Microsoft Teams app with test teams, channels, and users.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="e27a0-106">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="e27a0-106">Prerequisites</span></span>

1. <span data-ttu-id="e27a0-107">Participe do Programa de Desenvolvedores do [Microsoft 365](/office/developer-program/office-365-developer-program), se você não tiver um locatário de teste.</span><span class="sxs-lookup"><span data-stu-id="e27a0-107">[Join the Microsoft 365 Developer Program](/office/developer-program/office-365-developer-program), if you do not have a test tenant.</span></span>
2. <span data-ttu-id="e27a0-108">[Configurar uma Assinatura de Desenvolvedor do Microsoft 365.](/office/developer-program/office-365-developer-program-get-started)</span><span class="sxs-lookup"><span data-stu-id="e27a0-108">[Set up a Microsoft 365 Developer Subscription](/office/developer-program/office-365-developer-program-get-started).</span></span>
3. <span data-ttu-id="e27a0-109">Use pacotes de dados de exemplo com sua assinatura de desenvolvedor do [Microsoft 365 para instalar o pacote de conteúdo Usuários.](/office/developer-program/install-sample-packs)</span><span class="sxs-lookup"><span data-stu-id="e27a0-109">[Use sample data packs with your Microsoft 365 developer subscription to install the Users content pack](/office/developer-program/install-sample-packs).</span></span>
4. <span data-ttu-id="e27a0-110">[Instale o módulo do Teams PowerShell](https://www.powershellgallery.com/packages/MicrosoftTeams/1.0.2).</span><span class="sxs-lookup"><span data-stu-id="e27a0-110">[Install the Teams PowerShell module](https://www.powershellgallery.com/packages/MicrosoftTeams/1.0.2).</span></span>
5. <span data-ttu-id="e27a0-111">[Instale o módulo do PowerShell do Azure AD.](/powershell/azure/active-directory/install-adv2?view=azureadps-2.0#installing-the-azure-ad-module&preserve-view=true)</span><span class="sxs-lookup"><span data-stu-id="e27a0-111">[Install the Azure AD PowerShell module](/powershell/azure/active-directory/install-adv2?view=azureadps-2.0#installing-the-azure-ad-module&preserve-view=true).</span></span>

> [!NOTE]
> <span data-ttu-id="e27a0-112">Para qualquer locatário que você usa, você deve obter as permissões de administrador global para executar os scripts.</span><span class="sxs-lookup"><span data-stu-id="e27a0-112">For any tenant that you use, you must get the global administrator permissions to run the scripts.</span></span>

## <a name="enable-custom-app-sideloading"></a><span data-ttu-id="e27a0-113">Habilitar o sideload de aplicativo personalizado</span><span class="sxs-lookup"><span data-stu-id="e27a0-113">Enable custom app sideloading</span></span>

<span data-ttu-id="e27a0-114">Habilenciar o sideload de aplicativo personalizado é opcional.</span><span class="sxs-lookup"><span data-stu-id="e27a0-114">Enabling custom app sideloading is optional.</span></span> <span data-ttu-id="e27a0-115">Por padrão, somente administradores globais ou administradores de serviço do Teams podem carregar aplicativos personalizados no catálogo de aplicativos de locatário.</span><span class="sxs-lookup"><span data-stu-id="e27a0-115">By default, only global admins or Teams service admins can upload custom apps into the tenant app catalog.</span></span> <span data-ttu-id="e27a0-116">Você também pode permitir que os usuários carreguem aplicativos personalizados no Teams.</span><span class="sxs-lookup"><span data-stu-id="e27a0-116">You can also allow users to upload custom apps to Teams.</span></span> <span data-ttu-id="e27a0-117">Para obter mais informações, consulte [manage app setup policies in Teams](/microsoftteams/teams-app-setup-policies).</span><span class="sxs-lookup"><span data-stu-id="e27a0-117">For more information, see [manage app setup policies in Teams](/microsoftteams/teams-app-setup-policies).</span></span>

## <a name="create-teams-and-channels"></a><span data-ttu-id="e27a0-118">Criar equipes e canais</span><span class="sxs-lookup"><span data-stu-id="e27a0-118">Create teams and channels</span></span>

1. <span data-ttu-id="e27a0-119">Salve o trecho a seguir como um **arquivo .xml** e anote o caminho do arquivo.</span><span class="sxs-lookup"><span data-stu-id="e27a0-119">Save the following snippet as a **.xml** file and note the file path.</span></span> <span data-ttu-id="e27a0-120">Este XML define a estrutura da equipe e do canal criado juntamente com seus membros:</span><span class="sxs-lookup"><span data-stu-id="e27a0-120">This XML defines the structure of the team and channel that is created along with its members:</span></span>

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

2. <span data-ttu-id="e27a0-121">Salve o trecho a seguir como um script do PowerShell (.ps1) e observe onde você o salvou.</span><span class="sxs-lookup"><span data-stu-id="e27a0-121">Save the following snippet as a PowerShell script (.ps1) and note where you have saved it.</span></span> <span data-ttu-id="e27a0-122">Este script executa as etapas para criar a equipe e o canal e adicionar membros a eles:</span><span class="sxs-lookup"><span data-stu-id="e27a0-122">This script executes the steps to create the team and channel, and add members to them:</span></span>

    ```powershell
    Param(
        [Parameter(Mandatory = $true)]

        # This specifies the location of your configuration XML.

        [string] $teamsFilePath 
    )

    [xml]$XmlDocument = Get-Content -Path $teamsFilePath.ToString()

    if ($XmlDocument.Teams.Team.Count -gt 0) {

        try {

            # 1. Login with the global administrator account for your O365 Developer Program tenant. This script uses these credentials to connect to the powershell modules for Azure Active Directory and Microsoft Teams

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

3. <span data-ttu-id="e27a0-123">Abra uma Windows PowerShell no modo Administrador e execute o script que você acabou de salvar.</span><span class="sxs-lookup"><span data-stu-id="e27a0-123">Open a Windows PowerShell session in Administrator mode, and run the script that you just saved.</span></span>
4. <span data-ttu-id="e27a0-124">Quando você for solicitado a fornecer as credenciais, insira as credenciais de Administrador Global recebidas quando se inscreveu pela primeira vez na assinatura do desenvolvedor.</span><span class="sxs-lookup"><span data-stu-id="e27a0-124">When you are prompted to provide the credentials, enter the Global Administrator credentials you received when you first signed up for your developer subscription.</span></span>

    > [!Note]
    > <span data-ttu-id="e27a0-125">Não feche sua sessão do PowerShell, pois o script leva vários minutos para ser executado.</span><span class="sxs-lookup"><span data-stu-id="e27a0-125">Do not close your PowerShell session as the script takes several minutes to execute.</span></span> <span data-ttu-id="e27a0-126">Se você modificou os usuários em sua assinatura do que é criado no pacote de conteúdo padrão, alguns usuários podem não ser adicionados ao Teams.</span><span class="sxs-lookup"><span data-stu-id="e27a0-126">If you have modified the users in your subscription from what is created in the default content pack, some users may not be added to Teams.</span></span> <span data-ttu-id="e27a0-127">À medida que o script é executado, ele exibe ações bem-sucedidas ou com falha.</span><span class="sxs-lookup"><span data-stu-id="e27a0-127">As the script executes it displays successful or failed actions.</span></span>

5. <span data-ttu-id="e27a0-128">Após a execução do script, você pode entrar no cliente do Teams com uma das contas de usuário e exibir as equipes recém-criadas.</span><span class="sxs-lookup"><span data-stu-id="e27a0-128">After the script has finished execution, you can sign in to the Teams client with one of the user accounts and view the newly created teams.</span></span>

## <a name="see-also"></a><span data-ttu-id="e27a0-129">Confira também</span><span class="sxs-lookup"><span data-stu-id="e27a0-129">See also</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="e27a0-130">Depurar sua guia</span><span class="sxs-lookup"><span data-stu-id="e27a0-130">Debug your tab</span></span>](~/tabs/how-to/developer-tools.md)
 
> [!div class="nextstepaction"]
> [<span data-ttu-id="e27a0-131">Depurar seus bots</span><span class="sxs-lookup"><span data-stu-id="e27a0-131">Debug your bots</span></span>](~/bots/how-to/debug/locally-with-an-ide.md)

> [!div class="nextstepaction"]
> [<span data-ttu-id="e27a0-132">Testar permissões RSC</span><span class="sxs-lookup"><span data-stu-id="e27a0-132">Test RSC permissions</span></span>](~/graph-api/rsc/test-resource-specific-consent.md)

