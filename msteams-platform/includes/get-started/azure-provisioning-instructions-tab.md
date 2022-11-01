## <a name="deploy-your-app-to-azure"></a>Implantar seu aplicativo no Azure.

A implantação consiste em duas etapas. Primeiro, os recursos de nuvem necessários são criados (também conhecidos como provisionamento). Em seguida, o código do aplicativo é copiado para os recursos de nuvem criados. Para este tutorial, você implantará o aplicativo de guias.
<br>
<br>
<details>
<summary>Qual é a diferença entre Provisionar e Implantar?</summary>
<br>
A etapa <b>Provisionar</b> cria recursos no Azure e no Microsoft 365 para seu aplicativo, mas nenhum código (HTML, CSS, JavaScript etc.) é copiado para os recursos. A etapa <b>Implantar</b> copia o código do aplicativo para os recursos criados durante a etapa de provisionamento. É comum implantar várias vezes sem provisionar novos recursos. Como a etapa de provisionamento pode levar algum tempo para ser concluída, ela é separada da etapa de implantação.
</details>
<br>

# <a name="visual-studio-code"></a>[Código do Visual Studio](#tab/vscode)

Selecione o ícone do Kit de Ferramentas do Teams:::image type="icon" source="~/assets/images/teams-toolkit-v2/teams-toolkit-sidebar-icon.png"::: na barra Visual Studio Code lateral.

1. Selecione **Provisionar na Nuvem**.

   :::image type="content" source="~/assets/images/teams-toolkit-v2/provisioning-commands.png" alt-text="Captura de tela mostrando os comandos de provisionamento":::

1. Selecione qualquer um da assinatura existente.

   :::image type="content" source="~/assets/images/teams-toolkit-v2/select-subscription.png" alt-text="Captura de tela mostrando a seleção da Assinatura existente":::

1. Selecione um grupo de recursos a ser usado para os recursos do Azure.

    :::image type="content" source="~/assets/images/teams-toolkit-v2/deploy-azure/select-resource.png" alt-text="Captura de tela mostrando recursos para provisionamento":::

   > [!NOTE]
   > Seu aplicativo está hospedado usando recursos do Azure.
   >
   >Para obter mais informações, consulte [Criar grupo de recursos.](/azure/azure-resource-manager/management/manage-resource-groups-portal)

    Uma caixa de diálogo avisa que os custos podem ser incorridos ao executar recursos no Azure.

1. Selecione **Provisionar**.

   :::image type="content" source="~/assets/images/teams-toolkit-v2/deploy-azure/provision-warning.png" alt-text="A captura de tela mostrando o provisionamento da caixa de diálogo.":::

   :::image type="content" source="~/assets/images/teams-toolkit-v2/provision-confirm1.png" alt-text="Captura de tela mostrando a seleção da assinatura.":::

   O processo de provisionamento cria recursos na nuvem do Azure. Pode levar algum tempo. Você pode monitorar o progresso observando as caixas de diálogo no canto inferior direito. Após alguns minutos, você verá o seguinte aviso:

   :::image type="content" source="~/assets/images/teams-toolkit-v2/deploy-azure/deploy-provision-successmsgext.png" alt-text="A captura de tela mostrando o recurso provisionado com êxito na nuvem.":::

    Se desejar, você pode exibir os recursos provisionados. Para este tutorial, você não precisa exibir recursos.

    O recurso provisionado é exibido na seção **Ambiente** .

    :::image type="content" source="~/assets/images/teams-toolkit-v2/deploy-azure/provisioned-resources-env.png" alt-text="A captura de tela mostrando o recurso provisionado.":::

1. Selecione **Implantar na Nuvem** no painel **Implantação** após a conclusão do provisionamento.

   :::image type="content" source="~/assets/images/teams-toolkit-v2/deploy-azure/deploy-cloud.png" alt-text="A captura de tela mostrando a implantação na nuvem.":::

   Assim como acontece com o provisionamento, a implantação leva algum tempo. Você pode monitorar o processo observando as caixas de diálogo no canto inferior direito. Após alguns minutos, você verá um aviso de conclusão.

Agora, você pode usar o mesmo processo para implantar seus aplicativos Bot e Extensão de Mensagem no Azure.

# <a name="command-line"></a>[Linha de comando](#tab/cli)

Na janela do terminal:

1. Execute `teamsfx provision`.

   ``` bash
   teamsfx provision
   ```

   Quando solicitado, selecione uma assinatura do Azure para usar recursos do Azure.

1. Execute `teamsfx deploy`.

   ``` bash
   teamsfx deploy
   ```

---

> [!NOTE]
> Seu aplicativo está hospedado usando recursos do Azure.

## <a name="run-the-deployed-app"></a>Executar o aplicativo implantado

Depois que as etapas de provisionamento e implantação forem concluídas:

1. Abra o painel de depuração (**Ctrl+Shift+D** / **⌘⇧-D** ou **Exibir > Executar**) de Visual Studio Code.
1. Selecione **Iniciar Remoto (Edge)** na lista suspensa de configuração de inicialização.
1. Selecione o **F5 (Iniciar depuração)** para iniciar seu aplicativo no Azure.

   :::image type="content" source="~/assets/images/teams-toolkit-v2/deploy-azure/launch-remote.png" alt-text="A captura de tela mostrando como iniciar o aplicativo remotamente.":::

1. Selecione **Adicionar** quando solicitado para carregar o aplicativo no Teams.

   :::image type="content" source="~/assets/images/teams-toolkit-v2/deploy-azure/remote-app-client.png" alt-text="A captura de tela mostrando um aplicativo sendo instalado.":::

    Parabéns, seu primeiro aplicativo de guias está em execução em seu ambiente do Azure!

   :::image type="content" source="~/assets/images/teams-toolkit-v2/deploy-azure/azure-deployed-apptab.png" alt-text="A captura de tela mostrando a mensagem para experimentar o aplicativo agora ou posterior.":::
