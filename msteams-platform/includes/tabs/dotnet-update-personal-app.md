## <a name="update-your-application"></a>Atualizar seu aplicativo

### <a name="_layoutcshtml"></a>_Layout.cshtml

Para que sua guia seja exibida Teams, você deve incluir o **SDK** do cliente JavaScript Microsoft Teams e incluir uma chamada depois que a página `microsoftTeams.initialize()` for carregada. É assim que sua guia e o aplicativo Teams se comunicam:

Vá para **a pasta Shared,** **abra _Layout.cshtml** e adicione o seguinte à seção `<head>` tags:

```html
<script src="https://ajax.aspnetcdn.com/ajax/jQuery/jquery-3.4.1.min.js"></script>
<script src="https://statics.teams.cdn.office.net/sdk/v1.6.0/js/MicrosoftTeams.min.js"></script>
```

### <a name="personaltabcshtml"></a>PersonalTab.cshtml

Abra **PersonalTab.cshtml** e atualize as `<script>` marcas incorporadas chamando `microsoftTeams.initialize()` .

Certifique-se de salvar o **arquivo PersonalTab.cshtml** atualizado.