## <a name="update-your-application"></a>Atualizar seu aplicativo

### <a name="_layoutcshtml"></a>_Layout. cshtml

Para que sua guia seja exibida no Teams, você deve incluir o **SDK do cliente JavaScript do Microsoft Teams** e incluir uma chamada para depois que `microsoftTeams.initialize()` a página for carregada. É assim que sua guia e o aplicativo Teams se comunicam:

- Navegue até a pasta **compartilhada** , abra **_Layout. cshtml**e adicione o seguinte à seção `<head>` marcas:

```html
`<script src="https://ajax.aspnetcdn.com/ajax/jQuery/jquery-3.4.1.min.js"></script>`
`<script src="https://statics.teams.cdn.office.net/sdk/v1.6.0/js/MicrosoftTeams.min.js"></script>`
```

### <a name="personaltabcshtml"></a>PersonalTab. cshtml

Abra **PersonalTab. cshtml** e atualize as marcas `<script>` inseridas chamando `microsoftTeams.initialize()`.

Certifique-se de salvar o *PersonalTab. cshtml*atualizado.