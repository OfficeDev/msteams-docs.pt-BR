## <a name="upload-your-tab-to-teams-with-app-studio"></a>Carregar sua guia para o Teams com o app Studio

>[!NOTE]
> Usamos o app Studio para editar o arquivo **manifest. JSON** e carregar o pacote concluído para o Microsoft Teams. Você também pode editar manualmente o arquivo **manifest. JSON** , se preferir. Se você fizer isso, certifique-se de compilar a solução novamente para criar o arquivo **Tab. zip** para carregar.

- Abra o cliente do Microsoft Teams. Se você usar a [versão baseada na Web](https://teams.microsoft.com) , poderá inspecionar seu código de front-end usando as [ferramentas de desenvolvedor](~/tabs/how-to/developer-tools.md)do navegador.

- Abra o aplicativo App Studio e selecione a guia **Editor de manifesto** .

- Selecione o bloco **importar um aplicativo existente** no editor de manifesto para começar a atualizar o pacote de aplicativos para sua guia. O código-fonte vem com seu próprio manifesto parcialmente concluído. O nome do seu pacote de aplicativos é **Tab. zip**. Ele deve ser encontrado aqui:

```bash
/bin/Debug/netcoreapp2.2/tab.zip
```

- Carregar **Tab. zip** para o app Studio.

### <a name="update-your-app-package-with-manifest-editor"></a>Atualizar seu pacote de aplicativos com o editor de manifesto

Depois de carregar seu pacote de aplicativos no app Studio, você precisará concluir a configuração.

- Selecione o bloco para a guia recentemente importada no painel direito da página de boas-vindas do editor de manifesto.

Há uma lista de etapas no lado esquerdo do editor de manifestos e, à direita, uma lista de propriedades que precisam ter valores para cada uma dessas etapas. Muitas das informações foram fornecidas pelo *manifesto. JSON* , mas há alguns campos que você precisará atualizar:

#### <a name="details-app-details"></a>Detalhes: detalhes do aplicativo

- Em *identificação* selecione **gerar** para gerar uma nova ID de aplicativo para seu aplicativo.

- Em *informações do desenvolvedor* , atualize o campo **URL do site** com sua URL https do *ngrok* .

- Em *URLs de aplicativo* `https://<yourngrokurl>/privacy` , atualize a **declaração de privacidade** e **termos de uso** para `https://<yourngrokurl>/tou`>.

#### <a name="capabilities-tabs"></a>Recursos: guias

Na seção *guias* :

- Na *guia equipe* selecione **Adicionar**.

- Na janela pop-up da guia equipe atualizar a *URL* de configuração `https://<yourngrokurl>/tab`para.

- Por fim, certifique-se de que a *configuração pode atualizar? Equipe*e caixas de *chat de grupo* são verificados e selecione **salvar**.

#### <a name="finish-domains-and-permissions"></a>Concluir: domínios e permissões

Na seção *domínios e permissões* , os *domínios do campo Tabs* devem conter a URL do NGROK sem o prefixo HTTPS- `<yourngrokurl>.ngrok.io/`.

#### <a name="finish-test-and-distribute"></a>Concluir: testar e distribuir

>[!IMPORTANT]
>No campo **Descrição** à direita, você verá o seguinte aviso:
>
>&#9888; "**a matriz ' validDomains ' não pode conter um site de tunelamento...**"
>
>Este aviso pode ser ignorado durante o teste da guia.

Na seção *testar e distribuir* :

- Selecionar **Instalar**.

- Na janela pop-up *Adicionar a um campo de equipe ou chat* , insira sua equipe e selecione **instalar**.

- Na próxima janela pop-up, escolha o canal de equipe onde você deseja exibir a guia e selecione **Configurar**.

- Na janela pop-up final, selecione um valor para a página da guia (um ícone vermelho ou cinza) e selecione **salvar**.

Para exibir sua guia, navegue até a equipe na qual você a instalou e selecione-a na barra de guias. A página que você escolheu durante a configuração deve ser exibida.
