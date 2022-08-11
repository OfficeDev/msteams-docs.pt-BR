---
title: Manifesto do aplicativo Teams no Kit de Ferramentas do Teams para Visual Studio
author: surbhigupta
description: Neste módulo, saiba como editar, visualizar e personalizar o Manifesto do Aplicativo teams em um ambiente diferente para o Visual Studio.
ms.author: v-amprasad
ms.localizationpriority: medium
ms.topic: overview
ms.date: 05/13/2022
ms.openlocfilehash: c391df383c97638d3c8ff5944afab75db2400580
ms.sourcegitcommit: 52a11f7614c43172bc2d57401a60d569db5310a9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/09/2022
ms.locfileid: "67291650"
---
# <a name="edit-teams-app-manifest-using-visual-studio"></a>Editar manifesto do aplicativo Teams usando o Visual Studio

O Kit de Ferramentas do Teams no Visual Studio `manifest.template.json` `state.{env}.json` carrega o manifesto com configurações de e `config.{env}.json` durante o provisionamento e a preparação de dependências de aplicativo. Você também pode criar o aplicativo Microsoft Teams no [Portal do Desenvolvedor](https://dev.teams.microsoft.com/apps) com o manifesto.

Após o scaffolding, no arquivo de modelo de manifesto `templates/appPackage` na pasta, `manifest.template.json` é compartilhado entre o ambiente local e remoto.

No modelo de manifesto, selecione **Arquivo de** Manifesto Aberto do Kit de **Ferramentas** >  do Project  >  Teams **.**

:::image type="content" source="../assets/images/Tools-and-SDK-revamp/edit-manifest-for-visual-studio/vs-open-manifest.png" alt-text="Abrir arquivo de manifesto":::

### <a name="customize-app-manifest-in-teams-toolkit"></a>Personalizar o manifesto do aplicativo no Kit de Ferramentas do Teams

Há dois tipos de espaços reservados em `manifest.template.json`:

- `{{state.xx}}` é um espaço reservado predefinido, cujo valor é resolvido pelo Kit de Ferramentas do Teams, definido em `state.{env}.json`. É recomendável não modificar os valores em `state.{env}.json`.
- `{{config.manifest.xx}}` é um espaço reservado personalizado, cujo valor é resolvido de `config.{env}.json`.

Você pode adicionar um parâmetro personalizado:

- Adicionando um espaço reservado com `manifest.template.json` padrão: `{{config.manifest.xx}}`.
- Adicionando um valor de configuração em `config.{env}.json`.

    ```
        {
            "manifest": {
            "KEY": "VALUE"
            }
    }
    ```

### <a name="preview-app-manifest-in-teams-toolkit"></a>Visualizar manifesto do aplicativo no Kit de Ferramentas do Teams

Você pode visualizar valores no manifesto do aplicativo de duas maneiras:

- Quando você passa o mouse sobre o espaço reservado `manifest.template.json`, os valores **para desenvolvimento** e **ambiente local** podem ser vistos.

   :::image type="content" source="../assets/images/Tools-and-SDK-revamp/edit-manifest-for-visual-studio/vs-hover-placeholder1.png" alt-text="Passar o mouse sobre o espaço reservado":::

- Você também pode passar o mouse sobre a chave além `manifest.template.json`de cada espaço reservado, os mesmos valores para **desenvolvimento** e ambiente **local** podem ser vistos.

   :::image type="content" source="../assets/images/Tools-and-SDK-revamp/edit-manifest-for-visual-studio/vs-hover-key-placeholder.png" alt-text="Passar o mouse sobre a tecla ao lado do espaço reservado":::

   > [!NOTE]
   > Se o ambiente não tiver sido provisionado ou as dependências do aplicativo Teams não tiverem sido preparadas, isso indicará que os valores de espaço reservado não foram gerados. Siga as diretrizes dentro do foco para gerar valores correspondentes.

### <a name="preview-manifest-file"></a>Visualizar arquivo de manifesto

Você pode visualizar o arquivo de manifesto executando as seguintes etapas:

- Selecione **o menu Kit** de **Ferramentas do** Project  >  Teams e dispare Preparar Dependências de Aplicativos do **Teams** ou **Provisionar** na Nuvem que gera a configuração para o aplicativo Teams local ou remoto.

   :::image type="content" source="../assets/images/Tools-and-SDK-revamp/edit-manifest-for-visual-studio/vs-preview-manifest1.png" alt-text="Visualizar arquivo de manifesto":::

- Para visualizar o manifesto com conteúdo real, o Kit de Ferramentas do Teams gera os arquivos de manifesto de visualização, clique com o botão direito do mouse em **manifest.template.json** na **pasta appPackage** . Selecione **Visualizar arquivo de manifesto** > **para local** **ou para o Azure**.

   :::image type="content" source="../assets/images/Tools-and-SDK-revamp/edit-manifest-for-visual-studio/vs-preview1.png" alt-text="Menu de contexto de visualização":::

Há duas outras maneiras de visualizar o arquivo de manifesto:

- Selecione Pacote **do Aplicativo Zip do Kit** >  de Ferramentas **do** **Project** >  Teams e, em seguida, **selecione Para Local** **ou Para o Azure**.

    :::image type="content" source="../assets/images/Tools-and-SDK-revamp/edit-manifest-for-visual-studio/vs-zip1.png" alt-text="Pacote do aplicativo zip":::

- Você também pode ver a mesma lista de menus que estão em Project > Teams Toolkit, se você clicar com o botão direito do mouse no nome do projeto e, em seguida, selecionar o Kit de Ferramentas do **Teams** em **Gerenciador de Soluções**.

    :::image type="content" source="../assets/images/Tools-and-SDK-revamp/edit-manifest-for-visual-studio/vs-solution-explorer1.png" alt-text="Lista de menus do Kit de Ferramentas do Teams no Gerenciador de Soluções":::

    > [!NOTE]
    >Nesse cenário, o nome do projeto **é MyTeamsApp1**.

### <a name="sync-local-changes-to-developer-portal"></a>Sincronizar alterações locais no Portal do Desenvolvedor

As alterações locais podem ser sincronizadas com o Portal do Desenvolvedor, depois que você tiver visualizado o arquivo de manifesto. Selecione **o Manifesto de****Atualização do Kit de** >  Ferramentas do Project  >  Teams no **Portal do Desenvolvedor do Teams** ou o menu de contexto Gerenciador de Soluções.

:::image type="content" source="../assets/images/Tools-and-SDK-revamp/edit-manifest-for-visual-studio/vs-update-manifest1.png" alt-text="Atualizar manifesto no portal do desenvolvedor do Teams":::

> [!NOTE]
> As alterações são atualizadas no Portal do Desenvolvedor do Teams. Se você tiver algumas atualizações manuais no Portal do Desenvolvedor, isso poderá ser substituído. Na caixa **de diálogo** Aviso, você pode selecionar **Substituir e atualizar ou** **Cancelar**.

:::image type="content" source="../assets/images/Tools-and-SDK-revamp/edit-manifest-for-visual-studio/vs-overwrite.png" alt-text="Aviso de atualização":::

## <a name="see-also"></a>Confira também

- [Provisionar recursos de nuvem usando o Visual Studio](provision-cloud-resources.md)
- [Implantar o aplicativo Teams na nuvem usando o Visual Studio](deploy-teams-app.md)
