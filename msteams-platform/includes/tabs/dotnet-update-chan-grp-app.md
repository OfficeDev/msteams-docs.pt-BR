### <a name="_layoutcshtml"></a>_Layout.cshtml

Para que sua guia seja exibida Teams, você deve incluir o **SDK** do cliente JavaScript Microsoft Teams e incluir uma chamada depois que a página `microsoftTeams.initialize()` for carregada. É assim que sua guia e o cliente Teams se comunicam:

- Navegue até **a pasta Shared,** **abra _Layout.cshtml** e adicione o seguinte à `<head>` marca:

    ```html
    <script src="https://ajax.aspnetcdn.com/ajax/jQuery/jquery-3.4.1.min.js"></script>
    <script src="https://statics.teams.cdn.office.net/sdk/v1.6.0/js/MicrosoftTeams.min.js"></script>
    ```

>[!IMPORTANT]
>Não copie/colar as `<script src="...">` URLs desta página, pois elas podem não representar a versão mais recente. Para obter a versão mais recente do SDK, sempre vá para: Microsoft Teams [API JavaScript](https://www.npmjs.com/package/@microsoft/teams-js).

### <a name="tabcshtml"></a>Tab.cshtml

Abra **Tab.cshtml** e atualize o incorporado `<script>` da seguinte forma:

- Na parte superior do script, chame `microsoftTeams.initialize()` .

- Atualize `websiteUrl` os valores e em cada função com a URL de `contentUrl` ngrok HTTPS para sua guia.

Seu código agora deve ter a seguinte aparência com **y8rCgT2b** substituído pela URL do ngrok:

```javascript
    microsoftTeams.initialize();

    let saveGray = () => {
        microsoftTeams.settings.registerOnSaveHandler(function (saveEvent) {
            microsoftTeams.settings.setSettings({
                websiteUrl: `https://y8rCgT2b.ngrok.io`,
                contentUrl: `https://y8rCgT2b.ngrok.io/gray/`,
                entityId: "grayIconTab",
                suggestedDisplayName: "MyNewTab"
            });
            saveEvent.notifySuccess();
        });
    }

    let saveRed = () => {
        microsoftTeams.settings.registerOnSaveHandler(function (saveEvent) {
            microsoftTeams.settings.setSettings({
                websiteUrl: `https://y8rCgT2b.ngrok.io`,
                contentUrl: `https://y8rCgT2b.ngrok.io/red/`,
                entityId: "redIconTab",
                suggestedDisplayName: "MyNewTab"
            });
            saveEvent.notifySuccess();
        });
    }
```

Certifique-se de salvar **o Tab.cshtml atualizado.**

## <a name="build-and-run-your-application"></a>Criar e executar seu aplicativo

- Em Visual Studio pressione **F5** ou escolha **Iniciar Depuração** no menu **Depurar.** Verifique se **o ngrok** está sendo executado e funcionando corretamente abrindo seu navegador e indo para sua página de conteúdo por meio da URL HTTPS ngrok fornecida na janela do prompt de comando.

>[!TIP]
>Você precisa ter seu aplicativo em Visual Studio e ngrok em execução para concluir esse início rápido. Se você precisar parar de executar seu aplicativo Visual Studio para trabalhar **nele, mantenha o ngrok em execução.** Ele continuará escutando e retomará o roteamento da solicitação do aplicativo quando ele for reiniciado no Visual Studio. Se você precisar reiniciar o serviço ngrok, ele retornará uma nova URL e você terá que atualizar seu aplicativo com a nova URL.

## <a name="upload-your-tab-to-teams"></a>Upload sua guia para Teams

>[!Note]
> Usamos o App Studio para editar seu **manifest.jsno** arquivo e carregar o pacote concluído para Teams. Você também pode editar manualmente o **manifest.jsno** arquivo, se preferir. Se fizer isso, certifique-se de criar a solução novamente para criar o arquivo **tab.zip** para carregar.

- Abra o Microsoft Teams cliente. Se você usar a [versão baseada na Web,](https://teams.microsoft.com) poderá inspecionar seu código front-end usando as ferramentas de [desenvolvedor do navegador.](~/tabs/how-to/developer-tools.md)

- Abra o studio app e selecione a **guia Editor de manifesto.**

- Selecione o **pacote Importar um aplicativo existente** no editor de Manifesto para começar a atualizar o pacote de aplicativos para sua guia. O código-fonte vem com seu próprio manifesto parcialmente completo. O nome do pacote do aplicativo é **tab.zip**. Ele deve ser encontrado aqui:

    ```bash
    /bin/Debug/netcoreapp2.2/tab.zip
    ```

- Upload **tab.zip** App Studio.

### <a name="update-your-app-package-with-manifest-editor"></a>Atualizar seu pacote de aplicativos com o editor de manifesto

Depois de carregar seu pacote de aplicativos no App Studio, você precisará terminar de configurá-lo.

- Selecione o azulejo para sua guia recém-importada no painel direito da página de boas-vindas do editor de manifesto.

Há uma lista de etapas no lado esquerdo do editor de Manifesto e, à direita, uma lista de propriedades que precisam ter valores para cada uma dessas etapas. Grande parte das informações foram fornecidas pelo seumanifest.js *on,* mas há alguns campos que você precisará atualizar:

#### <a name="details-app-details"></a>Detalhes: Detalhes do aplicativo

Na seção *Detalhes do* aplicativo:

- *Identificação*: selecione **Gerar** para substituir a id de espaço reservado pelo GUID necessário para sua guia.

- *Informações do* desenvolvedor : atualize o **campo URL do** site com sua URL HTTPS *ngrok.*

- *URLs do aplicativo:* atualize a **instrução Privacy** para `https://<yourngrokurl>/privacy` e Os Termos de **uso** para `https://<yourngrokurl>/tou`>.

#### <a name="capabilities-tabs"></a>Recursos: guias

Na seção *Guias:*

- *Guia Equipe*: selecione **Adicionar**.

- Na janela pop-up da guia Equipe atualize a *URL de Configuração* para `https://<yourngrokurl>/tab` .

- Por fim, certifique-se de que *a configuração pode ser atualizada? As* caixas de chat Equipe *e Grupo* são verificadas e selecione **Salvar**.

#### <a name="finish-domains-and-permissions"></a>Concluir: domínios e permissões

Na seção *Domínios e permissões:*

- Os *domínios do campo guias* devem conter sua URL ngrok sem o prefixo HTTPS - `<yourngrokurl>.ngrok.io/` .

#### <a name="finish-test-and-distribute"></a>Concluir: Testar e distribuir

>[!IMPORTANT]
>No campo **Descrição** à direita, você verá o seguinte aviso:
>
>&#9888; "**A matriz 'validDomains' não pode conter um site de tunelamento...**"
>
>Esse aviso pode ser ignorado durante o teste da guia.

Na seção *Testar e distribuir:*

- Selecionar **Instalar**.

- Na janela pop-up, Adicione a uma equipe ou *campo de chat* insira sua equipe e selecione **Instalar**.

- Na próxima janela pop-up, escolha o canal de equipe onde você gostaria que a guia fosse exibida e selecione **Configurar**.

- Na janela pop-up final, selecione um valor para a página de tabulação (um ícone vermelho ou cinza) e selecione **Salvar**.

Para exibir sua guia, navegue até a equipe em que você a instalou e selecione-a na barra de guias. A página escolhida durante a configuração deve ser exibida.
