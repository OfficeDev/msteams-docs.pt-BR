## <a name="deploy-your-app-to-azure"></a>Implantar seu aplicativo no Azure.

A implantação consiste em duas etapas.  Primeiro, os recursos de nuvem necessários são criados (também conhecidos como provisionamento). Em seguida, o código do aplicativo é copiado para os recursos de nuvem criados. Para este tutorial, você implantará o aplicativo guia.
<br>
<br>
<details>
<summary>Qual é a diferença entre Provisionar e Implantar?</summary>
<br>
A <b>etapa Provisionar</b> cria recursos no Azure e no Microsoft 365 para seu aplicativo, mas nenhum código (HTML, CSS, JavaScript etc.) é copiado para os recursos. A <b>etapa</b> Implantar copia o código do aplicativo para os recursos criados durante a etapa de provisionamento. É comum implantar várias vezes sem provisionar novos recursos. Como a etapa de provisionamento pode levar algum tempo para ser concluída, ela é separada da etapa de implantação.
</details>
<br>

# <a name="visual-studio-code"></a>[Código do Visual Studio](#tab/vscode)

Selecione o ícone do Kit de Ferramentas do Teams:::image type="icon" source="~/assets/images/teams-toolkit-v2/teams-toolkit-sidebar-icon.png"::: na barra Visual Studio Code lateral.

1. Selecione **Provisionar na Nuvem**.

   :::image type="content" source="~/assets/images/teams-toolkit-v2/provisioning-commands.png" alt-text="Captura de tela mostrando a seleção de provisionamento na nuvem no Kit de ferramentas do Teams.":::

1. Selecione uma assinatura a ser usada para os recursos do Azure.

    :::image type="content" source="~/assets/images/teams-toolkit-v2/deploy-azure/select-resource.png" alt-text="Captura de tela mostrando a assinatura a ser usada para os recursos do Azure.":::

   > [!NOTE]
   > Seu aplicativo é hospedado usando recursos do Azure.

    Uma caixa de diálogo avisa que os custos podem ser incorridos ao executar recursos no Azure.

1. Selecione **Provisionar**.

   :::image type="content" source="~/assets/images/teams-toolkit-v2/deploy-azure/provision-warning.png" alt-text="Captura de tela mostrando uma caixa de diálogo em que os custos podem ser incorridos ao executar recursos no Azure.":::

   O processo de provisionamento cria recursos na nuvem do Azure. Pode levar algum tempo. Você pode monitorar o progresso observando as caixas de diálogo no canto inferior direito. Após alguns minutos, você verá o seguinte aviso:

   :::image type="content" source="~/assets/images/teams-toolkit-v2/deploy-azure/deploy-provision-successmsgext.png" alt-text="Captura de tela mostrando um aviso que exibe &quot;hellomsg&quot; provisionado com êxito na nuvem.":::

    Se desejar, você poderá exibir os recursos provisionados. Para este tutorial, você não precisa exibir recursos.

    O recurso provisionado aparece na **seção Ambiente** .

    :::image type="content" source="~/assets/images/teams-toolkit-v2/deploy-azure/provisioned-resources-env.png" alt-text="Captura de tela mostrando o recurso que está sendo provisionado na seção de ambiente.":::

1. Selecione **Implantar na nuvem no** painel **Implantação** após a conclusão do provisionamento.

   :::image type="content" source="~/assets/images/teams-toolkit-v2/deploy-azure/deploy-cloud.png" alt-text="Captura de tela mostrando a implantação na nuvem.":::

   Assim como acontece com o provisionamento, a implantação leva algum tempo. Você pode monitorar o processo observando as caixas de diálogo no canto inferior direito. Após alguns minutos, você verá um aviso de conclusão.

Agora, você pode usar o mesmo processo para implantar seus aplicativos de Bot e Extensão de Mensagem no Azure.

# <a name="command-line"></a>[Linha de comando](#tab/cli)

Na janela do terminal:

1. Execute `teamsfx provision`.

   ``` bash
   teamsfx provision
   ```

   Quando solicitado, selecione uma assinatura do Azure para usar os recursos do Azure.

   > [!NOTE]
   > Seu aplicativo é hospedado usando recursos do Azure.

1. Execute `teamsfx deploy`.

   ``` bash
   teamsfx deploy
   ```

---

## <a name="run-the-deployed-app"></a>Executar o aplicativo implantado

Depois que as etapas de provisionamento e implantação forem concluídas:

1. Abra o painel de depuração (**Ctrl+Shift+D** / **⌘⇧-D** ou **View > Run**) Visual Studio Code.
1. Selecione **Iniciar Remoto (Borda)** na lista suspensa de configuração de inicialização.
1. Selecione a **depuração Iniciar (F5)** para iniciar seu aplicativo no Azure.

   :::image type="content" source="~/assets/images/teams-toolkit-v2/deploy-azure/launch-remote.png" alt-text="Captura de tela mostrando o aplicativo de inicialização remotamente.":::

1. Selecione **Adicionar**.

   :::image type="content" source="~/assets/images/teams-toolkit-v2/deploy-azure/add-mex-app.png" alt-text="Captura de tela mostrando o aplicativo que está sendo instalado.":::

   O kit de ferramentas exibe uma mensagem para indicar que o aplicativo foi adicionado ao Teams.

   :::image type="content" source="~/assets/images/teams-toolkit-v2/deploy-azure/mex-added-msg.png" alt-text="Captura de tela mostrando uma mensagem para experimentar o aplicativo agora ou mais tarde":::

    - Se você selecionar **Obter,** poderá experimentar o aplicativo mais tarde na lista de aplicativos de Sideload.
    - Se você selecionar **Experimentar**, o Teams carregará seu aplicativo.

   Seu aplicativo é carregado no site do Azure.

1. Selecione **Experimentar**.

   O aplicativo extensão de mensagem é carregado em um aplicativo de chatbot.

   :::image type="content" source="~/assets/images/teams-toolkit-v2/deploy-azure/app-added-mex1.png" alt-text="Captura de tela mostrando um aplicativo com sideload no Teams":::
