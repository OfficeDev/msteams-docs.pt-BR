## <a name="deploy-your-app-to-azure"></a>Implantar seu aplicativo no Azure.

A implantação consiste em duas etapas.  Primeiro, os recursos de nuvem necessários são criados (também conhecidos como provisionamento). Em seguida, o código do aplicativo é copiado para os recursos de nuvem criados. Para este tutorial, você implantará o aplicativo guia.

> <details>
> <summary>Qual é a diferença entre Provisionar e Implantar?</summary>
>
> A **etapa Provisionar** cria recursos no Azure e Microsoft 365 para seu aplicativo, mas nenhum código (HTML, CSS, JavaScript etc.) é copiado para os recursos. A **etapa** Implantar copia o código do aplicativo para os recursos criados durante a etapa de provisionamento. É comum implantar várias vezes sem provisionar novos recursos. Como a etapa de provisionamento pode levar algum tempo para ser concluída, ela é separada da etapa de implantação.
</details>

# <a name="visual-studio-code"></a>[Visual Studio Code](#tab/vscode)

Selecione o ícone do Kit de Ferramentas do Teams:::image type="icon" source="~/assets/images/teams-toolkit-v2/teams-toolkit-sidebar-icon.png"::: na barra Visual Studio Code lateral.

1. Selecione **Provisionar na Nuvem**.

   :::image type="content" source="~/assets/images/teams-toolkit-v2/provisioning-commands.png" alt-text="Captura de tela mostrando os comandos de provisionamento" border="false":::

1. Selecione uma assinatura a ser usada para os recursos do Azure.

    :::image type="content" source="~/assets/images/teams-toolkit-v2/deploy-azure/select-resource.png" alt-text="Captura de tela mostrando recursos para provisionamento" border="false":::

   > [!NOTE]
   > Sempre há alguns recursos do Azure usados para hospedar seu aplicativo.

    Uma caixa de diálogo avisa que os custos podem ser incorridos ao executar recursos no Azure.

1. Selecione **Provisionar**.

   :::image type="content" source="~/assets/images/teams-toolkit-v2/deploy-azure/provision-warning.png" alt-text="Captura de tela da caixa de diálogo de provisionamento." border="true":::

   O processo de provisionamento cria recursos na nuvem do Azure. Pode levar algum tempo. Você pode monitorar o progresso observando as caixas de diálogo no canto inferior direito. Após alguns minutos, você verá o seguinte aviso:

   :::image type="content" source="~/assets/images/teams-toolkit-v2/deploy-azure/deploy-provision-success.png" alt-text="Captura de tela mostrando a caixa de diálogo de provisionamento concluída." border="false":::

    Se desejar, você poderá exibir os recursos provisionados. Para este tutorial, você não precisa exibir recursos.

    O recurso provisionado aparece na **seção Ambiente** .

    :::image type="content" source="~/assets/images/teams-toolkit-v2/deploy-azure/provisioned-resources-env.png" alt-text="Captura de tela mostrando a caixa de diálogo de provisionamento concluída." border="false":::

1. Selecione **Implantar na nuvem no** painel **Implantação** após a conclusão do provisionamento.

   :::image type="content" source="~/assets/images/teams-toolkit-v2/deploy-azure/deploy-cloud.png" alt-text="Captura de tela mostrando onde clicar para implantar na nuvem." border="false":::

   Assim como acontece com o provisionamento, a implantação leva algum tempo. Você pode monitorar o processo observando as caixas de diálogo no canto inferior direito. Após alguns minutos, você verá um aviso de conclusão.


# <a name="command-line"></a>[Linha de comando](#tab/cli)

Na janela do terminal:

1. Execute `teamsfx provision`.

   ``` bash
   teamsfx provision
   ```

   Quando solicitado, selecione uma assinatura do Azure para usar os recursos do Azure.

   > [!NOTE]
   > Sempre há alguns recursos do Azure usados para hospedar seu aplicativo.

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

   :::image type="content" source="~/assets/images/teams-toolkit-v2/deploy-azure/launch-remote.png" alt-text="Captura de tela mostrando o aplicativo de inicialização remotamente." border="false":::

1. Selecione **Adicionar**.

   :::image type="content" source="~/assets/images/teams-toolkit-v2/deploy-azure/remote-app-client.png" alt-text="Captura de tela mostrando o aplicativo que está sendo instalado." border="false":::

   Seu aplicativo é carregado no site do Azure.

   :::image type="content" source="~/assets/images/teams-toolkit-v2/deploy-azure/azure-deployed-app.png" alt-text="Captura de tela mostrando o aplicativo que está sendo instalado." border="false":::

    Parabéns! Seu aplicativo de guia agora está sendo executado remotamente no Azure!
