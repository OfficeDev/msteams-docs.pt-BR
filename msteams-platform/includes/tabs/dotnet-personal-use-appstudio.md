## <a name="upload-your-tab-with-app-studio"></a>Upload sua guia com o App Studio

>[!NOTE]
> Usamos **o App Studio** para editar seumanifest.js **no** arquivo e carregar o pacote concluído para Teams. Você também pode editar manualmente **manifest.jsem**. Se fizer isso, certifique-se de criar a solução novamente para criar o arquivo **Tab.zip** para carregar.

**Para carregar sua guia com o App Studio**

1. Vá para Microsoft Teams. Se você usar a [versão baseada na Web,](https://teams.microsoft.com) poderá inspecionar seu código front-end usando as ferramentas de [desenvolvedor do navegador.](~/tabs/how-to/developer-tools.md)

1. Vá para **o App Studio** e selecione a guia Editor **de** manifesto.

1. Selecione **Importar um aplicativo existente** no editor de **Manifesto** para começar a atualizar o pacote de aplicativos para sua guia. O código-fonte vem com seu próprio manifesto parcialmente completo. O nome do pacote do aplicativo é **tab.zip**. Ele está disponível no seguinte caminho:

    ```bash
    /bin/Debug/netcoreapp2.2/tab.zip
    ```

1. Upload **tab.zip** App **Studio.**

### <a name="update-your-app-package-with-manifest-editor"></a>Atualizar seu pacote de aplicativos com o editor de manifesto

Depois de carregar seu pacote de aplicativos no App Studio, você deve configurá-lo.

Selecione o azulejo para sua guia recém-importada no painel direito da página de boas-vindas do editor de manifesto.

Há uma lista de etapas no lado esquerdo do editor de Manifesto e, à direita, uma lista de propriedades que devem ter valores para cada uma dessas etapas. Grande parte das informações foi fornecida pelo seumanifest.js **em,** mas há campos que você deve atualizar.

#### <a name="details-app-details"></a>Detalhes: Detalhes do aplicativo

Na seção **Detalhes do** aplicativo:

1. Em **Identificação**, selecione **Gerar** para gerar uma nova ID do aplicativo.

1. Em **Informações do desenvolvedor,** atualize o **Site** com sua URL HTTPS **ngrok.**

1. Em **URLs do aplicativo,** atualize a **instrução Privacy** para `https://<yourngrokurl>/privacy` e Termos de **uso** para `https://<yourngrokurl>/tou`>.

#### <a name="capabilities-tabs"></a>Recursos: guias

Na seção **Guias:**

1. Em **Adicionar uma guia pessoal,** selecione **Adicionar**. Uma caixa de diálogo pop-up é exibida.

1. Insira um nome para a guia pessoal em **Nome**.

1. Insira a **ID da entidade**.

1. Atualizar **a URL de conteúdo** com `https://<yourngrokurl>/personalTab` .

    Deixe o **campo URL do site** em branco.

1. Selecione **Salvar**.

#### <a name="finish-domains-and-permissions"></a>Concluir: domínios e permissões

Na seção **Domínios e** permissões, o **campo Domínios** de suas guias deve conter sua URL ngrok sem o prefixo HTTPS `<yourngrokurl>.ngrok.io/` .

##### <a name="finish-test-and-distribute"></a>Concluir: Testar e distribuir

>[!IMPORTANT]
> À direita, em **Descrição,** você verá o seguinte aviso:
>
> &#9888; A **matriz 'validDomains' não pode conter um site de tunelamento...**
>
>Esse aviso pode ser ignorado durante o teste da guia.

1. Na seção **Testar e Distribuir,** selecione **Instalar**.

1. Na caixa de diálogo pop-up, selecione **Adicionar** e sua guia é exibida com duas opções.

1. Nas opções na guia, escolha **Selecionar Cinza** ou **Selecionar Vermelho**. A guia é exibida de acordo com a cor selecionada.
 
    ![Guia pessoal ASPNETMVC carregada](../../assets/images/tab-images/personaltabaspnetmvcuploaded.png)

## <a name="view-your-personal-tab"></a>Exibir sua guia pessoal

1. Na barra de navegação localizada à extrema esquerda do aplicativo Teams, selecione as releições &#x25CF;&#x25CF;&#x25CF;. Uma lista de aplicativos pessoais é mostrada.

1. Selecione sua guia na lista para exibi-la.
