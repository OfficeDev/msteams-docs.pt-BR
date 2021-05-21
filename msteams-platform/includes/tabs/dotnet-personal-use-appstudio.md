## <a name="upload-your-tab-to-teams-with-app-studio"></a>Upload sua guia para Teams com o App Studio

>[!NOTE]
> Usamos o App Studio para editar seu **manifest.jsno** arquivo e carregar o pacote concluído para Teams. Você também pode editar manualmente **manifest.jsem,** se preferir. Se fizer isso, certifique-se de criar a solução novamente para criar o arquivo **Tab.zip** para carregar.

- Abra o Microsoft Teams cliente. Se você usar a [versão baseada na Web,](https://teams.microsoft.com) poderá inspecionar seu código front-end usando as ferramentas de [desenvolvedor do navegador.](~/tabs/how-to/developer-tools.md)

- Abra o studio app e selecione a **guia Editor de manifesto.**

- Selecione o **pacote Importar um aplicativo existente** no editor de Manifesto para começar a atualizar o pacote de aplicativos para sua guia. O código-fonte vem com seu próprio manifesto parcialmente completo. O nome do pacote do aplicativo é **tab.zip**. Ele deve ser encontrado aqui:

    ```bash
    /bin/Debug/netcoreapp2.2/Tab.zip
    ```

- Upload **Tab.zip** App Studio.

### <a name="update-your-app-package-with-manifest-editor"></a>Atualizar seu pacote de aplicativos com o editor de manifesto

Depois de carregar seu pacote de aplicativos no App Studio, você precisará terminar de configurá-lo.

- Selecione o azulejo para sua guia recém-importada no painel direito da página de boas-vindas do editor de manifesto.

Há uma lista de etapas no lado esquerdo do editor de Manifesto e, à direita, uma lista de propriedades que precisam ter valores para cada uma dessas etapas. Grande parte das informações foram fornecidas pelo seumanifest.js *on,* mas há alguns campos que você precisará atualizar:

#### <a name="details-app-details"></a>Detalhes: Detalhes do aplicativo

Na seção **Detalhes do** aplicativo:

- Em **Identificação,** **selecione Gerar** para gerar uma nova ID do aplicativo.

- Em **Informações do desenvolvedor** atualize a URL do **site** com sua URL HTTPS **ngrok.**

- Em **URLs do aplicativo,** atualize a **instrução Privacy** para `https://<yourngrokurl>/privacy` e Os Termos de **uso** para `https://<yourngrokurl>/tou`>.

#### <a name="capabilities-tabs"></a>Recursos: guias

Na seção *Guias:*

- Em **Adicionar uma guia pessoal,** selecione **Adicionar**. Você receberá uma janela de diálogo pop-up.

- Conclua **o campo Nome.**

- Conclua **o campo ID da** entidade.

- Atualize o **campo URL** de conteúdo com `https://<yourngrokurl>/personalTab` para .

- Deixe o **campo URL do site** em branco.

- Selecione **Salvar**.

#### <a name="finish-domains-and-permissions"></a>Concluir: domínios e permissões

Na seção **Domínios e** permissões, o **campo Domínios** de suas guias deve conter sua URL ngrok sem o prefixo HTTPS - `<yourngrokurl>.ngrok.io/` .

##### <a name="finish-test-and-distribute"></a>Concluir: Testar e distribuir

>[!IMPORTANT]
>No campo **Descrição** à direita, você verá o seguinte aviso:
>
>&#9888; "**A matriz 'validDomains' não pode conter um site de tunelamento...**"
>
>Esse aviso pode ser ignorado durante o teste da guia.

Na seção **Testar e distribuir:**

- Selecionar **Instalar**.

- Na janela pop-up, certifique-se de que **Add for you** está definido como **Sim** e Adicionar a uma equipe ou **chat** está definido como **Não**.

- Selecionar **Instalar**.

- Na próxima janela pop-up, selecione **Abrir** e sua guia será exibida.

## <a name="view-your-personal-tab"></a>Exibir sua guia pessoal

- Na barra de navegação localizada à extrema esquerda do Teams App, selecione o `...` menu. Você será apresentado com uma lista de aplicativos pessoais.

- Selecione sua guia na lista a ser visualizada.
