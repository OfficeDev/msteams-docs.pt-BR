---
title: Solucionar problemas de seu aplicativo
description: Solucionar problemas ou erros durante a criação de aplicativos para o Microsoft Teams
keywords: solução de problemas de desenvolvimento de aplicativos do teams
ms.date: 07/09/2018
ms.openlocfilehash: f7fe42e7c1f3ff2c4d8d1cbe81ed8f71e6c04384
ms.sourcegitcommit: 4329a94918263c85d6c65ff401f571556b80307b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/01/2020
ms.locfileid: "41672474"
---
# <a name="troubleshoot-your-microsoft-teams-app"></a>Solucionar problemas do aplicativo Microsoft Teams

## <a name="troubleshooting-tabs"></a>Guias de solução de problemas

### <a name="accessing-the-devtools"></a>Acessar o DevTools

Você pode abrir [o devtools no cliente do Microsoft Teams](~/tabs/how-to/developer-tools.md) para obter uma experiência semelhante à medida que pressionar F12 (no Windows) ou Command-Option-I (no MacOS) em um navegador.

### <a name="blank-tab-screen"></a>Tela em branco

Se você não estiver vendo o conteúdo no modo de exibição de tabulação, pode ser:

* o conteúdo não pode ser exibido em `<iframe>`um.
* o domínio de conteúdo não está na lista [validDomains](~/resources/schema/manifest-schema.md#validdomains) no manifesto.

### <a name="the-save-button-isnt-enabled-on-the-settings-dialog"></a>O botão salvar não está habilitado na caixa de diálogo de configurações

Não se esqueça de `microsoftTeams.settings.setValidityState(true)` chamar uma vez que o usuário tenha inserido ou selecionado todos os dados necessários na página de configurações para habilitar o botão salvar.

### <a name="after-selecting-the-save-button-the-tab-settings-cannot-be-saved"></a>Após selecionar o botão salvar, as configurações da guia não poderão ser salvas

Ao adicionar uma guia, se você clicar nos botões salvar, mas receber uma mensagem de erro indicando que as configurações não podem ser salvas, o problema pode ser uma das duas classes de problemas:

* A mensagem de êxito na gravação nunca foi recebida. Se um manipulador de gravação tiver sido `microsoftTeams.settings.registerOnSaveHandler(handler)`registrado usando o, o `saveEvent.notifySuccess()`retorno de chamada deverá chamar. Se o retorno de chamada não chamá-lo em 30 `saveEvent.notifyFailure(reason)` segundos ou chamadas, esse erro será exibido.

* Se nenhum manipulador de salvamento foi registrado, `saveEvent.notifySuccess()` a chamada é automaticamente feita imediatamente após o usuário selecionando o botão salvar.

* As configurações fornecidas eram inválidas. O outro motivo pelo qual as configurações não podem ser salvas é se `microsoftTeams.setSettings(settings)` a chamada para fornecer um objeto de configurações inválido ou a chamada não foi feita. Consulte a próxima seção, problemas comuns com o objeto Settings.

### <a name="common-problems-with-the-settings-object"></a>Problemas comuns com o objeto Settings

* `settings.entityId`está ausente. O campo é obrigatório.
* `settings.contentUrl`está ausente. O campo é obrigatório.
* `settings.contentUrl`ou o opcional `settings.removeUrl`, ou `settings.websiteUrl` é fornecido, mas não é válido. As URLs devem usar HTTPS e também devem ser o mesmo domínio que a página de configurações ou especificado na lista do `validDomains` manifesto.

### <a name="cant-authenticate-the-user-or-display-your-auth-provider-in-your-tab"></a>Não é possível autenticar o usuário ou exibir seu provedor de autenticação na sua guia

A menos que você esteja realizando uma autenticação silenciosa, deverá seguir o processo de autenticação fornecido pelo [SDK do cliente Microsoft Teams JavaScript](/javascript/api/overview/msteams-client.md).

> [!NOTE]
>Exigimos que todo o fluxo de autenticação inicie e termine em seu domínio, que deve ser listado `validDomains` no objeto no seu manifesto.

Para obter mais informações sobre autenticação, confira [autenticar um usuário](~/concepts/authentication/authentication.md).

### <a name="static-tabs-not-showing-up"></a>Guias estáticas não aparecem

Há um problema conhecido em que atualizar um aplicativo bot existente com uma guia estática nova ou atualizada não mostrará essa alteração de guia ao acessar o aplicativo de uma conversa de chat pessoal.  Para ver a alteração, você deve testar um novo usuário ou instância de teste ou acessar o bot do submenu aplicativos.

## <a name="troubleshooting-bots"></a>Solucionando problemas de bots

### <a name="cant-add-my-bot"></a>Não é possível adicionar meu bot

Os aplicativos devem ser habilitados pelo administrador de locatários do Office 365 para serem carregados por usuários finais. Observe que, em alguns casos, o locatário do Office 365 pode ter vários SKUs associados a ele e para que os bots funcionem em qualquer um, eles devem ser habilitados em todos os SKUs. Consulte [Prepare Your Office 365 locatário](~/concepts/build-and-test/prepare-your-o365-tenant.md) para obter mais informações.

### <a name="cant-add-bot-as-a-member-of-a-team"></a>Não é possível adicionar bot como um membro de uma equipe

Os bots devem ser carregados primeiro em uma equipe antes que eles possam ser acessados em qualquer canal da equipe. Examine [o carregamento do aplicativo em uma equipe](~/concepts/deploy-and-publish/apps-upload.md) para obter mais informações sobre esse processo.

### <a name="my-bot-doesnt-get-my-message-in-a-channel"></a>Meu bot não recebe minha mensagem em um canal

Os bots nos canais recebem mensagens somente quando são explicitamente @mentioned, mesmo que você esteja respondendo a uma mensagem de bot anterior. A única exceção em que você pode não ver o nome do bot em uma mensagem é se o bot `imBack` receber uma ação como resultado de um cartão remetido originalmente.

### <a name="my-bot-doesnt-understand-my-commands-when-in-a-channel"></a>Meu bot não entende meus comandos quando em um canal

Como os bots nos canais só recebem mensagens quando são @mentioned, todas as mensagens que seu bot recebe em um canal incluem que @mention no campo de texto. É uma prática recomendada remover o próprio nome de bot de todas as mensagens de texto de entrada antes de passar à sua lógica de análise. A revisão [menciona](~/bots/how-to/conversations/channel-and-group-conversations.md#working-with--mentions) dicas sobre como lidar com esse caso.

## <a name="issues-with-packaging-and-uploading"></a>Problemas com o empacotamento e carregamento

### <a name="error-while-reading-manifestjson"></a>Erro ao ler manifest. JSON

A maioria dos erros de manifesto fornecerá uma dica em qual campo específico está ausente ou inválido. No entanto, se o arquivo JSON não puder ser lido como JSON, esta mensagem de erro genérica será usada.

Motivos comuns para erros de leitura de manifesto:

* JSON inválido. Use um IDE como o [Visual Studio Code](https://code.visualstudio.com) ou o [Visual Studio](https://www.visualstudio.com/vs/) que valida automaticamente a sintaxe JSON.
* Problemas de codificação. Use UTF-8 para o arquivo *manifest. JSON* . Outras codificações, especificamente com a BOM, podem não ser legíveis.
* Pacote. zip malformado. O arquivo *manifest. JSON* deve estar no nível superior do arquivo. zip. Observe que a compactação de arquivo Mac padrão pode colocar o *manifest. JSON* em um subdiretório, que não será carregado corretamente no Microsoft Teams.

### <a name="another-extension-with-same-id-exists"></a>Outra extensão com a mesma ID existe

Se você estiver tentando carregar novamente um pacote atualizado com a mesma ID, escolha o ícone **substituir** no final da linha da tabela da guia, em vez do botão **carregar** .

Se você não estiver carregando um pacote atualizado, verifique se o ID é exclusivo.
