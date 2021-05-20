## <a name="update-your-application"></a>Atualize seu aplicativo

### <a name="_layoutcshtml"></a>_Layout.cshtml

Para que sua guia seja exibida em Teams, você deve incluir o **Microsoft Teams Cliente JavaScript SDK** e incluir uma chamada para depois que `microsoftTeams.initialize()` sua página for carregada. É assim que sua guia e o aplicativo Teams se comunicam:

- Navegue até a pasta **Compartilhada,** abra **_Layout.cshtml** e adicione o seguinte à `<head>` seção tags:

    ```html
    `<script src="https://ajax.aspnetcdn.com/ajax/jQuery/jquery-3.4.1.min.js"></script>`
    `<script src="https://statics.teams.cdn.office.net/sdk/v1.6.0/js/MicrosoftTeams.min.js"></script>`
    ```

### <a name="personaltabcshtml"></a>PersonalTab.cshtml

Abra **PersonalTab.cshtml** e atualize as `<script>` tags incorporadas ligando `microsoftTeams.initialize()` .

Certifique-se de salvar seu **PersonalTab.cshtml** atualizado .