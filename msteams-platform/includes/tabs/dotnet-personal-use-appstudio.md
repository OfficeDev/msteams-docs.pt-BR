## <a name="upload-your-tab-to-teams-with-app-studio"></a>Upload sua guia para Teams com o App Studio

>[!NOTE]
> Usamos o App Studio para editar sua **manifest.jsno** arquivo e carregar o pacote completo para Teams. Você também pode editar manualmente **manifest.js** se preferir. Se você fizer isso, certifique-se de construir a solução novamente para criar o **arquivoTab.zip** para carregar.

- Abra o cliente Microsoft Teams. Se você usar a [versão baseada na Web,](https://teams.microsoft.com) você pode inspecionar seu código frontal usando [as ferramentas](~/tabs/how-to/developer-tools.md)de desenvolvedor do seu navegador .

- Abra o estúdio App e selecione a guia **Do editor Manifest.**

- Selecione **a máquina de importar um aplicativo existente** no editor Manifest para começar a atualizar o pacote de aplicativos para sua guia. O código fonte vem com seu próprio manifesto parcialmente completo. O nome do seu pacote de aplicativos é **tab.zip**. Deve ser encontrado aqui:

    ```bash
    /bin/Debug/netcoreapp2.2/Tab.zip
    ```

- Upload **Tab.zip** para o App Studio.

### <a name="update-your-app-package-with-manifest-editor"></a>Atualize seu pacote de aplicativos com o editor manifest

Depois de carregar seu pacote de aplicativos no App Studio, você precisará terminar de configurá-lo.

- Selecione a telha para sua guia recém-importada no painel direito da página de boas-vindas do editor Manifest.

Há uma lista de passos no lado esquerdo do editor do Manifest, e à direita, uma lista de propriedades que precisam ter valores para cada uma dessas etapas. Muitas das informações foram fornecidas pelo seu *manifest.js,* mas existem alguns campos que você precisará atualizar:

#### <a name="details-app-details"></a>Detalhes: Detalhes do aplicativo

Na seção detalhes do **Aplicativo:**

- Em **Identificação** selecione **Gerar** para gerar um novo App ID para o seu aplicativo.

- Em **informações do Desenvolvedor,** atualize a **URL do site** com sua URL **HTTPS ngrok.**

- De acordo com **os URLs** do App, atualize a **declaração** de Privacidade `https://<yourngrokurl>/privacy` e os Termos de **uso** para `https://<yourngrokurl>/tou`>.

#### <a name="capabilities-tabs"></a>Recursos: Guias

Na seção *Guias:*

- Em **Adicionar uma guia pessoal** selecionar **Adicionar**. Você será presenteado com uma janela de diálogo pop-up.

- Complete o campo **Nome.**

- Complete o campo **de identidade da entidade.**

- Atualize o campo **URL de conteúdo** com `https://<yourngrokurl>/personalTab` .

- Deixe o campo url do **site** em branco.

- Selecione **Salvar**.

#### <a name="finish-domains-and-permissions"></a>Acabamento: Domínios e permissões

Na seção **Domínios e permissões,** os domínios do campo **de guias** devem conter sua URL ngrok sem o prefixo HTTPS - `<yourngrokurl>.ngrok.io/` .

##### <a name="finish-test-and-distribute"></a>Acabamento: Teste e distribua

>[!IMPORTANT]
>No campo **Descrição** à direita você verá o seguinte aviso:
>
>&#9888; "**A matriz 'validDomains' não pode conter um local de tunelamento...**"
>
>Este aviso pode ser ignorado durante o teste da sua guia.

Na seção **Teste e distribua:**

- Selecionar **Instalar**.

- Na janela pop-up certifique-se de que **Adicionar para você** está definido como **Sim** e Adicionar a uma equipe **ou bate-papo** está definido como **No**.

- Selecionar **Instalar**.

- Na próxima janela pop-up selecione **Abrir** e sua guia será exibida.

## <a name="view-your-personal-tab"></a>Veja sua guia pessoal

- Na barra de navegação localizada à esquerda do Teams App, selecione o `...` menu. Você será apresentado com uma lista de aplicativos pessoais.

- Selecione sua guia na lista para visualizar.
