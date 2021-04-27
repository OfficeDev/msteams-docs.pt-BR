---
title: Solucionar problemas de seu aplicativo
description: Solucionar problemas ou erros ao criar aplicativos para o Microsoft Teams
keywords: Solução de problemas de desenvolvimento de aplicativos do teams
localization_priority: Normal
ms.topic: troubleshooting
ms.date: 07/09/2018
ms.openlocfilehash: ce45a75869e8b6694cd84c10f8fac1f9bd55bad4
ms.sourcegitcommit: 825abed2f8784d2bab7407ba7a4455ae17bbd28f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2021
ms.locfileid: "52020426"
---
# <a name="troubleshoot-your-microsoft-teams-app"></a>Solucionar problemas do seu aplicativo do Microsoft Teams

## <a name="troubleshooting-tabs"></a>Guias de solução de problemas

### <a name="accessing-the-devtools"></a>Acessando o DevTools

Você pode abrir [o DevTools](~/tabs/how-to/developer-tools.md) no cliente do Teams para uma experiência semelhante a pressionar F12 (no Windows) ou Command-Option-I (no MacOS) em um navegador.

### <a name="blank-tab-screen"></a>Tela de guia em branco

Se você não estiver vendo seu conteúdo na exibição de tabulação, pode ser:

* seu conteúdo não pode ser exibido em `<iframe>` um .
* o domínio de conteúdo não está na [lista validDomains](~/resources/schema/manifest-schema.md#validdomains) no manifesto.

### <a name="the-save-button-isnt-enabled-on-the-settings-dialog"></a>O botão Salvar não está habilitado na caixa de diálogo configurações

Certifique-se de chamar depois que o usuário tiver entrada ou selecionado todos os dados necessários na página de configurações `microsoftTeams.settings.setValidityState(true)` para habilitar o botão salvar.

### <a name="after-selecting-the-save-button-the-tab-settings-cannot-be-saved"></a>Depois de selecionar o botão Salvar, as configurações de tabulação não podem ser salvas

Ao adicionar uma guia, se você clicar nos botões salvar, mas for apresentado com uma mensagem de erro indicando que as configurações não podem ser salvas, o problema pode ser uma das duas classes de problemas:

* A mensagem de sucesso salvar nunca foi recebida. Se um manipulador de salvar foi registrado usando `microsoftTeams.settings.registerOnSaveHandler(handler)` , o retorno de chamada deve chamar `saveEvent.notifySuccess()` . Se o retorno de chamada não chamar isso dentro de 30 segundos ou chamar em vez disso, esse `saveEvent.notifyFailure(reason)` erro será mostrado.

* Se nenhum manipulador de salvar foi registrado, a chamada será automaticamente feita imediatamente após o `saveEvent.notifySuccess()` usuário selecionar o botão salvar.

* As configurações fornecidas eram inválidas. O outro motivo pelo qual as configurações podem não ser salvas é se a chamada para um objeto de configuração inválido foi fornecida ou se a chamada não `microsoftTeams.setSettings(settings)` foi feita. Consulte a próxima seção, Problemas comuns com o objeto settings.

### <a name="common-problems-with-the-settings-object"></a>Problemas comuns com o objeto settings

* `settings.entityId` está faltando. O campo é obrigatório.
* `settings.contentUrl` está faltando. O campo é obrigatório.
* `settings.contentUrl` ou opcional `settings.removeUrl` , ou são `settings.websiteUrl` fornecidos, mas não válidos. As URLs devem usar HTTPS e também devem ser o mesmo domínio da página de configurações ou especificado na lista do `validDomains` manifesto.

### <a name="cant-authenticate-the-user-or-display-your-auth-provider-in-your-tab"></a>Não é possível autenticar o usuário ou exibir seu provedor de autenticação em sua guia

A menos que você esteja fazendo autenticação silenciosa, você deve seguir o processo de autenticação fornecido pelo [SDK](/javascript/api/overview/msteams-client.md)do cliente JavaScript do Microsoft Teams.

> [!NOTE]
>Exigimos que todo o fluxo de autenticação inicie e termine em seu domínio, que deve estar listado no `validDomains` objeto em seu manifesto.

Para obter mais informações sobre autenticação, consulte [Authenticate a user](~/concepts/authentication/authentication.md).

### <a name="static-tabs-not-showing-up"></a>Guias estáticas não aparecendo

Há um problema conhecido em que a atualização de um aplicativo bot existente com uma guia estática nova ou atualizada não mostrará essa alteração de tabulação ao acessar o aplicativo de uma conversa de chat pessoal.  Para ver a alteração, você deve testar em um novo usuário ou instância de teste ou acessar o bot do flyout Apps.

## <a name="troubleshooting-bots"></a>Solução de problemas de bots

### <a name="cant-add-my-bot"></a>Não é possível adicionar meu bot

Os aplicativos devem ser habilitados pelo administrador de locatários do Office 365 para que eles sejam carregados pelos usuários finais. Observe que, em alguns casos, o locatário do Office 365 pode ter várias SKUs associadas a ele e, para que os bots funcionem em qualquer, eles devem estar habilitados em todas as SKUs. Confira Preparar seu locatário do [Office 365](~/concepts/build-and-test/prepare-your-o365-tenant.md) para obter mais informações.

### <a name="cant-add-bot-as-a-member-of-a-team"></a>Não é possível adicionar bot como membro de uma equipe

Os bots devem primeiro ser carregados em uma equipe antes de serem acessíveis em qualquer canal dessa equipe. Confira [Carregar seu aplicativo em uma equipe para](~/concepts/deploy-and-publish/apps-upload.md) obter mais informações sobre esse processo.

### <a name="my-bot-doesnt-get-my-message-in-a-channel"></a>Meu bot não consegue receber minha mensagem em um canal

Os bots nos canais recebem mensagens somente quando estão explicitamente @mentioned, mesmo se você estiver respondendo a uma mensagem de bot anterior. A única exceção em que você pode não ver o nome do bot em uma mensagem é se o bot receber uma ação como resultado de um `imBack` CardAction que ele enviou originalmente.

### <a name="my-bot-doesnt-understand-my-commands-when-in-a-channel"></a>Meu bot não entende meus comandos quando em um canal

Como os bots nos canais só recebem mensagens quando @mentioned, todas as mensagens que seu bot recebe em um canal incluem esse @mention no campo de texto. É uma prática prática tirar o nome do bot em si de todas as mensagens de texto de entrada antes de passar para sua lógica de análise. Revise [as menções](../bots/how-to/conversations/channel-and-group-conversations.md#work-with-mentions) para saber como lidar com esse caso.

## <a name="issues-with-packaging-and-uploading"></a>Problemas com empacotamento e carregamento

### <a name="error-while-reading-manifestjson"></a>Erro ao ler manifest.json

A maioria dos erros de manifesto fornecerá uma dica sobre qual campo específico está ausente ou inválido. No entanto, se o arquivo JSON não puder ser lido como JSON, essa mensagem de erro genérica será usada.

Motivos comuns para erros de leitura de manifesto:

* JSON inválido. Use um IDE, como [Visual Studio Código](https://code.visualstudio.com) [ou Visual Studio](https://www.visualstudio.com/vs/) que valida automaticamente a sintaxe JSON.
* Problemas de codificação. Use UTF-8 para o *arquivomanifest.json.* Outras codificações, especificamente com o BOM, podem não ser acessível.
* Pacote .zip malformado. O *manifest.jsno* arquivo on deve estar no nível superior do arquivo .zip. Observe que a compactação  de arquivo mac padrão pode colocar amanifest.jsem um subdiretório, que não carregará corretamente no Microsoft Teams.

### <a name="another-extension-with-same-id-exists"></a>Existe outra extensão com a mesma ID

Se você estiver tentando carregar um pacote atualizado com a  mesma ID, escolha o ícone Substituir no final da linha de tabela da guia em vez do **botão Carregar.**

Se você não estiver carregando um pacote atualizado, verifique se a ID é exclusiva.
