## <a name="update-your-application"></a><span data-ttu-id="4ae64-101">Atualizar seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="4ae64-101">Update your application</span></span>

### <a name="_layoutcshtml"></a><span data-ttu-id="4ae64-102">_Layout.cshtml</span><span class="sxs-lookup"><span data-stu-id="4ae64-102">_Layout.cshtml</span></span>

<span data-ttu-id="4ae64-103">Para que sua guia seja exibida Teams, você deve incluir o **SDK** do cliente JavaScript Microsoft Teams e incluir uma chamada depois que a página `microsoftTeams.initialize()` for carregada.</span><span class="sxs-lookup"><span data-stu-id="4ae64-103">For your tab to display in Teams, you must include the **Microsoft Teams JavaScript client SDK** and include a call to `microsoftTeams.initialize()` after your page loads.</span></span> <span data-ttu-id="4ae64-104">É assim que sua guia e o aplicativo Teams se comunicam:</span><span class="sxs-lookup"><span data-stu-id="4ae64-104">This is how your tab and the Teams app communicate:</span></span>

- <span data-ttu-id="4ae64-105">Navegue até **a pasta Shared,** **abra _Layout.cshtml** e adicione o seguinte à seção `<head>` tags:</span><span class="sxs-lookup"><span data-stu-id="4ae64-105">Navigate to the **Shared** folder, open **_Layout.cshtml**, and add the following to the `<head>` tags section:</span></span>

    ```html
    `<script src="https://ajax.aspnetcdn.com/ajax/jQuery/jquery-3.4.1.min.js"></script>`
    `<script src="https://statics.teams.cdn.office.net/sdk/v1.6.0/js/MicrosoftTeams.min.js"></script>`
    ```

### <a name="personaltabcshtml"></a><span data-ttu-id="4ae64-106">PersonalTab.cshtml</span><span class="sxs-lookup"><span data-stu-id="4ae64-106">PersonalTab.cshtml</span></span>

<span data-ttu-id="4ae64-107">Abra **PersonalTab.cshtml** e atualize as `<script>` marcas incorporadas chamando `microsoftTeams.initialize()` .</span><span class="sxs-lookup"><span data-stu-id="4ae64-107">Open **PersonalTab.cshtml** and update the embedded `<script>` tags by calling `microsoftTeams.initialize()`.</span></span>

<span data-ttu-id="4ae64-108">Certifique-se de salvar **seu PersonalTab.cshtml atualizado.**</span><span class="sxs-lookup"><span data-stu-id="4ae64-108">Make sure to save your updated **PersonalTab.cshtml**.</span></span>