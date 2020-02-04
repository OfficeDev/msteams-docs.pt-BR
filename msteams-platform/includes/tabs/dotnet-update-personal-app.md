## <a name="update-your-application"></a><span data-ttu-id="34dc0-101">Atualizar seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="34dc0-101">Update your application</span></span>

### <a name="_layoutcshtml"></a><span data-ttu-id="34dc0-102">_Layout. cshtml</span><span class="sxs-lookup"><span data-stu-id="34dc0-102">_Layout.cshtml</span></span>

<span data-ttu-id="34dc0-103">Para que sua guia seja exibida no Teams, você deve incluir o **SDK do cliente JavaScript do Microsoft Teams** e incluir uma chamada para depois que `microsoftTeams.initialize()` a página for carregada.</span><span class="sxs-lookup"><span data-stu-id="34dc0-103">For your tab to display in Teams, you must include the **Microsoft Teams JavaScript client SDK** and include a call to `microsoftTeams.initialize()` after your page loads.</span></span> <span data-ttu-id="34dc0-104">É assim que sua guia e o aplicativo Teams se comunicam:</span><span class="sxs-lookup"><span data-stu-id="34dc0-104">This is how your tab and the Teams app communicate:</span></span>

- <span data-ttu-id="34dc0-105">Navegue até a pasta **compartilhada** , abra **_Layout. cshtml**e adicione o seguinte à seção `<head>` marcas:</span><span class="sxs-lookup"><span data-stu-id="34dc0-105">Navigate to the **Shared** folder, open **_Layout.cshtml**, and add the following to the `<head>` tags section:</span></span>

```html
`<script src="https://ajax.aspnetcdn.com/ajax/jQuery/jquery-3.4.1.min.js"></script>`
`<script src="https://statics.teams.cdn.office.net/sdk/v1.6.0/js/MicrosoftTeams.min.js"></script>`
```

### <a name="personaltabcshtml"></a><span data-ttu-id="34dc0-106">PersonalTab. cshtml</span><span class="sxs-lookup"><span data-stu-id="34dc0-106">PersonalTab.cshtml</span></span>

<span data-ttu-id="34dc0-107">Abra **PersonalTab. cshtml** e atualize as marcas `<script>` inseridas chamando `microsoftTeams.initialize()`.</span><span class="sxs-lookup"><span data-stu-id="34dc0-107">Open **PersonalTab.cshtml** and update the embedded `<script>` tags by calling `microsoftTeams.initialize()`.</span></span>

<span data-ttu-id="34dc0-108">Certifique-se de salvar o *PersonalTab. cshtml*atualizado.</span><span class="sxs-lookup"><span data-stu-id="34dc0-108">Make sure to save your updated *PersonalTab.cshtml*.</span></span>