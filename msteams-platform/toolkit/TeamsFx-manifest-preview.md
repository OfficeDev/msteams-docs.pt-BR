---
title: Visualizar Teams Manifesto do Aplicativo no Teams Toolkit
author: zyxiaoyuer
description: Visualizar Manifesto do Aplicativo Teams
ms.author: nliu
ms.localizationpriority: medium
ms.topic: overview
ms.date: 11/29/2021
---

# <a name="preview-teams-app-manifest-in-teams-toolkit"></a>Visualizar Teams manifesto do aplicativo no Teams Toolkit

Após o scaffolding, os seguintes são os arquivos de modelo de manifesto disponíveis na `templates/appPackage` pasta:

- `manifest.local.template.json` - aplicativo de equipes de depuração local.
- `manifest.remote.template.json` - compartilhado entre todos os ambientes remotos.

Os arquivos Template que consistem em espaço reservados e os valores reais Teams Toolkit são resolvidos em arquivos em `.fx/configs` e `.fx/states`.

## <a name="prerequisite"></a>Pré-requisito

* [Instale Teams Toolkit](https://marketplace.visualstudio.com/items?itemName=TeamsDevApp.ms-teams-vscode-extension) versão v3.0.0+.

> [!TIP]
> Verifique se você Teams projeto de aplicativo aberto Visual Studio código.

## <a name="preview-manifest"></a>Manifesto de visualização

Para visualizar o manifesto com conteúdo real, Teams Toolkit gera arquivos de manifesto de visualização na `build/appPackage` pasta:

```text
└───build
    └───appPackage
        ├───appPackage.{env}.zip - Zipped app package of remote teams app
        ├───appPackage.local.zip - Zipped app package of local team app
        ├───manifest.{env}.json  - Previewed manifest of remote teams app
        └───manifest.local.json  - Previewed manifest of local teams app
```

### <a name="preview-local-manifest-file"></a>Visualizar o arquivo de manifesto local

Para visualizar o arquivo de manifesto do aplicativo de equipes locais, você precisa pressionar **F5** para executar a depuração local. Ele gera configurações locais padrão para você e, em seguida, o pacote do aplicativo e os builds de manifesto de visualização sob **a pasta build/appPackage** .

Você também pode visualizar o manifesto local seguindo as etapas:

1. Selecione **Visualizar** nos codelens do **arquivo manifest.local.template.json** .
2. Selecione **Visualizar arquivo de manifesto** na barra de menus **do arquivo manifest.local.template.json** .
3. Selecione **Zip Teams pacote de metadados** em Treeview e selecione **Local**.
O local de visualização aparece como mostrado na imagem:

:::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/preview-1.png" alt-text="Visualização":::

### <a name="preview-manifest-in-remote-environment"></a>Manifesto de visualização em ambiente remoto

Para visualizar o arquivo de manifesto do aplicativo de equipes remotas, selecione Provisionar na nuvem no painel **DESENVOLVIMENTO** do Treeview de extensão Teams Toolkit ou acionar Teams **: Provisionar** na nuvem da paleta de comandos. Ele gera configuração para o aplicativo de equipes remotas e cria o pacote e o manifesto de visualização na **pasta build/appPackage** .

Você também pode visualizar o manifesto em ambiente remoto seguindo as etapas:

1. Selecione **Visualizar** nos codelens do **arquivo manifest.remote.template.json** .
2. Selecione **Visualizar arquivo de manifesto** na barra de menus **do arquivo manifest.remote.template.json** .
3. Selecione **Zip Teams pacote de metadados** em Treeview.
4. Selecione seu ambiente.

Se houver mais de um ambiente, você precisará selecionar o ambiente que deseja visualizar, conforme mostrado na imagem:

:::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/manifest preview-1.png" alt-text="Adicionar env":::

## <a name="sync-local-changes-to-dev-portal"></a>Sincronizar alterações locais no portal de desenvolvimento

Depois de visualizar o arquivo de manifesto, você pode sincronizar as alterações locais no portal de desenvolvimento seguindo as etapas:

1.  Selecione **Atualizar para Teams plataforma** no canto superior esquerdo da`manifest.{env}.json`
2. Selecione **Teams: Atualizar manifesto para Teams plataforma na** barra de menus de`manifest.{env}.json`

 Você também pode disparar **Teams: atualizar manifesto para Teams plataforma da** paleta de comandos

   :::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/pre.png" alt-text="modo de exibição em árvore":::

> [!NOTE]
> O gatilho de codelens ou **título** do editor atualizará o arquivo de manifesto atual para Teams plataforma. O gatilho da paleta de comandos requer a seleção do ambiente de destino.

Se o arquivo de manifesto estiver desatualizado devido à alteração do arquivo de configuração ou à alteração do modelo, confirme a seguinte ação:

:::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/manifest preview -3.png" alt-text="pre":::

- **Somente visualização**: o arquivo de manifesto local será substituído de acordo com a configuração atual
- **Visualização e atualização**: o arquivo de manifesto local será substituído de acordo com a configuração atual e também atualizado para Teams plataforma
- **Cancelar**: não fazer nada

> [!NOTE]
> As alterações serão atualizadas para o portal de dev. Se você tiver algumas atualizações manuais no portal de dev, ela será substituída.

## <a name="see-also"></a>Confira também

[Personalizar Teams Manifesto do Aplicativo no Teams Toolkit](TeamsFx-manifest-customization.md)
