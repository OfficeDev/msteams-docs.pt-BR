## <a name="deploy-your-app-to-azure"></a>Implantar seu aplicativo no Azure

A implantação consiste em duas etapas.  Primeiro, os recursos de nuvem necessários são criados (também conhecidos como provisionamento), em seguida, o código que com o seu aplicativo é copiado para os recursos de nuvem criados.

# <a name="visual-studio-code"></a>[Visual Studio Code](#tab/vscode)

1. Abra o Visual Studio Code.
1. Selecione a Teams Toolkit na barra lateral selecionando o ícone Teams.
1. Selecione **Provisionamento na Nuvem**.

   :::image type="content" source="~/assets/images/teams-toolkit-v2/provisioning-commands.png" alt-text="Captura de tela mostrando os comandos de provisionamento":::

1. Se necessário, selecione uma assinatura a ser usada para os recursos do Azure.

   > [!NOTE]
   > Sempre há alguns recursos do Azure usados para hospedar seu aplicativo.

1. Uma caixa de diálogo avisa que os custos podem ser incorridos ao executar recursos no Azure.  Pressione **Provision**.

   :::image type="content" source="~/assets/images/teams-toolkit-v2/provision-warning.png" alt-text="Captura de tela da caixa de diálogo de provisionamento.":::

   O processo de provisionamento cria recursos na nuvem do Azure. Isso leva algum tempo. Você pode monitorar o progresso observando as caixas de diálogo no canto inferior direito. Após alguns minutos, você verá o seguinte aviso:

   :::image type="content" source="~/assets/images/teams-toolkit-v2/provision-complete.png" alt-text="Captura de tela mostrando a caixa de diálogo completa de provisionamento.":::

1. Depois que o provisionamento for concluído, selecione **Implantar na Nuvem**.  Assim como no provisionamento, esse processo leva algum tempo.  Você pode monitorar o processo observando as caixas de diálogo no canto inferior direito. Após alguns minutos, você verá um aviso de conclusão.

# <a name="command-line"></a>[Linha de comando](#tab/cli)

Em sua janela de terminal:

1. Executar `teamsfx provision` .

   ``` bash
   teamsfx provision
   ```

   Você pode ser solicitado a fazer logoff na sua assinatura do Azure. Se necessário, você será solicitado a selecionar uma assinatura do Azure a ser usada para os recursos do Azure.

   > [!NOTE]
   > Sempre há alguns recursos do Azure usados para hospedar seu aplicativo.

1. Executar `teamsfx deploy` .

   ``` bash
   teamsfx deploy
   ```

---

> [!NOTE]
> **Qual é a diferença entre Provisionar e Implantar?**
>
> A **etapa Provision** cria recursos no Azure e no M365 para seu aplicativo, mas nenhum código (HTML, CSS, JavaScript, etc.) é copiado para os recursos. A **etapa Implantar** copia o código do aplicativo para os recursos criados durante a etapa de provisionamento. É comum implantar várias vezes sem provisionar novos recursos. Como a etapa de provisionamento pode levar algum tempo para ser concluída, ela é separada da etapa de implantação.

Depois que as etapas de provisionamento e implantação são concluídas:

1. No Visual Studio Code, abra o painel de depuração (**Ctrl+Shift+D**  /  **⌘⇧-D** ou **Exibir > Executar**)
1. Selecione **Iniciar Remoto (Borda)** no drop-down de configuração de início.
1. Pressione o botão Reproduzir para iniciar seu aplicativo - agora em execução remotamente no Azure!
