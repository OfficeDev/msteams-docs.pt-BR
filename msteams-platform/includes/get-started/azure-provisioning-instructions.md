## <a name="deploy-your-app-to-azure"></a>Implantar seu aplicativo no Azure

A implantação consiste em duas etapas.  Primeiro, os recursos de nuvem necessários são criados (também conhecidos como provisionamento). Em seguida, o código do aplicativo é copiado para os recursos de nuvem criados.

# <a name="visual-studio-code"></a>[Visual Studio Code](#tab/vscode)

Selecione o Teams Toolkit :::image type="icon" source="~/assets/images/teams-toolkit-v2/teams-toolkit-sidebar-icon.png"::: na barra Visual Studio Code lateral.

1. Selecione **Provisionamento na Nuvem**.

   :::image type="content" source="~/assets/images/teams-toolkit-v2/deploy-azure/deploy-provision.png" alt-text="Captura de tela mostrando os comandos de provisionamento" border="false":::

1. Selecione uma assinatura a ser usada para os recursos do Azure, se solicitado.

   > [!NOTE]
   > Sempre há alguns recursos do Azure usados para hospedar seu aplicativo.

    Uma caixa de diálogo avisa que os custos podem ser incorridos ao executar recursos no Azure.

1. Selecione **Provision**.

   :::image type="content" source="~/assets/images/teams-toolkit-v2/provision-warning.png" alt-text="Captura de tela da caixa de diálogo de provisionamento." border="false":::

   O processo de provisionamento cria recursos na nuvem do Azure. Pode levar algum tempo. Você pode monitorar o progresso observando as caixas de diálogo no canto inferior direito. Após alguns minutos, você verá o seguinte aviso:

   :::image type="content" source="~/assets/images/teams-toolkit-v2/deploy-azure/deploy-provision-success.png" alt-text="Captura de tela mostrando a caixa de diálogo completa de provisionamento." border="false":::

1. Selecione **Implantar na Nuvem no** painel **Implantação** depois que o provisionamento for concluído.

   :::image type="content" source="~/assets/images/teams-toolkit-v2/deploy-azure/deploy-cloud.png" alt-text="Captura de tela mostrando onde clicar para implantar na nuvem." border="false":::

   Assim como no provisionamento, a implantação leva algum tempo. Você pode monitorar o processo observando as caixas de diálogo no canto inferior direito. Após alguns minutos, você verá um aviso de conclusão.

Agora, você pode usar o mesmo processo para implantar seus aplicativos de Bot e Extensão de Mensagem no Azure. 

# <a name="command-line"></a>[Linha de comando](#tab/cli)

Em sua janela de terminal:

1. Execute `teamsfx provision`.

   ``` bash
   teamsfx provision
   ```

   Quando solicitado, selecione uma assinatura do Azure para usar recursos do Azure.

   > [!NOTE]
   > Sempre há alguns recursos do Azure usados para hospedar seu aplicativo.

1. Execute `teamsfx deploy`.

   ``` bash
   teamsfx deploy
   ```

---

> [!NOTE]
> **Qual é a diferença entre Provisionar e Implantar?**
>
> A **etapa Provision** cria recursos no Azure e Microsoft 365 para seu aplicativo, mas nenhum código (HTML, CSS, JavaScript, etc.) é copiado para os recursos. A **etapa Implantar** copia o código do aplicativo para os recursos criados durante a etapa de provisionamento. É comum implantar várias vezes sem provisionar novos recursos. Como a etapa de provisionamento pode levar algum tempo para ser concluída, ela é separada da etapa de implantação.

Depois que as etapas de provisionamento e implantação são concluídas:

1. Abra o painel de depuração (**Ctrl+Shift+D**  /  **⌘⇧-D** ou **Exibir > Executar**) Visual Studio Code.
1. Selecione **Iniciar Remoto (Borda)** no drop-down de configuração de início.
1. Selecione o botão Reproduzir para iniciar seu aplicativo - agora em execução remotamente no Azure!

   :::image type="content" source="~/assets/images/teams-toolkit-v2/deploy-azure/launch-remote.png" alt-text="Captura de tela mostrando o aplicativo de início remotamente." border="false":::

   Agora, o aplicativo em execução no Azure será instalado no seu cliente!

   :::image type="content" source="~/assets/images/teams-toolkit-v2/deploy-azure/remote-app-client.png" alt-text="Captura de tela mostrando o aplicativo que está sendo instalado." border="false":::