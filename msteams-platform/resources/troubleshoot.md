---
title: Solucionar problemas do seu aplicativo
description: Solucionar problemas ou erros ao criar aplicativos para o Microsoft Teams
keywords: solução de problemas de desenvolvimento de aplicativos do Teams
localization_priority: Normal
ms.topic: troubleshooting
ms.date: 07/09/2018
ms.openlocfilehash: 0b3f4f7b3a38b6e61b4fbc7e58c5ed5897ed427e
ms.sourcegitcommit: edfe85e312c73e34aa795922c4b7eb0647528d48
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/30/2022
ms.locfileid: "68243469"
---
# <a name="troubleshoot-your-microsoft-teams-app"></a>Solucionar problemas em seu aplicativo Microsoft Teams

## <a name="troubleshooting-tabs"></a>Guias de solução de problemas

### <a name="accessing-the-devtools"></a>Acessando o DevTools

Você pode abrir [o DevTools no cliente do Teams](~/tabs/how-to/developer-tools.md) para uma experiência semelhante à de pressionar F12 (no Windows) ou Command-Option-I (no MacOS) em um navegador.

### <a name="blank-tab-screen"></a>Tela de guia em branco

Se você não estiver vendo seu conteúdo no modo de exibição de guia, pode ser:

* seu conteúdo não pode ser exibido em um `<iframe>`.
* o domínio de conteúdo não está na [lista validDomains](~/resources/schema/manifest-schema.md#validdomains) no manifesto.

> [!NOTE]
> Uma guia em branco aparece quando a URL da guia fornecida redireciona para a tela de logon. As páginas de logon não são renderizadas em iFrames como uma proteção contra clickjacking. Sua lógica de autenticação deve usar um método diferente de redirecionamento.

### <a name="the-save-button-isnt-enabled-on-the-settings-dialog"></a>O botão Salvar não está habilitado na caixa de diálogo de configurações

Certifique-se de chamar `microsoftTeams.settings.setValidityState(true)` quando o usuário tiver entrada ou selecionado todos os dados necessários na página de configurações para habilitar o botão Salvar.

### <a name="the-tab-settings-cant-be-saved-on-selecting-save"></a>As configurações da guia não podem ser salvas ao selecionar Salvar

Ao adicionar uma guia, se você selecionar  Salvar, mas receber uma mensagem de erro indicando que as configurações não podem ser salvas, o problema poderá ser uma das duas classes de problemas:

* **A mensagem de êxito de salvamento nunca foi recebida**: se um manipulador de salvamento tiver `microsoftTeams.settings.registerOnSaveHandler(handler)`sido registrado usando, o retorno de chamada deverá chamar `saveEvent.notifySuccess()`.

  * Se o retorno de chamada não chamar dentro `saveEvent.notifySuccess()` de 30 segundos ou chamadas `saveEvent.notifyFailure(reason)` , esse erro será mostrado.
  * Se nenhum manipulador de salvamento tiver sido registrado, a `saveEvent.notifySuccess()` chamada será feita automaticamente quando o usuário selecionar **Salvar**.

* **As configurações fornecidas eram inválidas**: o outro motivo pelo qual as configurações podem não ser salvas `microsoftTeams.setSettings(settings)` é se a chamada para fornecer um objeto de configurações inválido ou se a chamada não foi feita. Consulte a próxima seção, Problemas comuns com o objeto de configurações.

### <a name="common-problems-with-the-settings-object"></a>Problemas comuns com o objeto de configurações

* `settings.entityId` está faltando. O campo é obrigatório.
* `settings.contentUrl` está faltando. O campo é obrigatório.
* `settings.contentUrl` ou opcional `settings.removeUrl`, ou `settings.websiteUrl` são fornecidos, mas não são válidos. As URLs devem usar HTTPS e também devem ser o mesmo domínio que a página de configurações ou especificados na lista do `validDomains` manifesto.

### <a name="cant-authenticate-the-user-or-display-your-auth-provider-in-your-tab"></a>Não é possível autenticar o usuário ou exibir seu provedor de autenticação em sua guia

A menos que você esteja fazendo autenticação silenciosa, você deve seguir o processo de autenticação fornecido pelo [SDK do cliente JavaScript do Microsoft Teams](/javascript/api/overview/msteams-client).

> [!NOTE]
> Exigimos que todo o fluxo de autenticação comece e termine em seu domínio, que deve ser listado no `validDomains` objeto em seu manifesto.

Para obter mais informações sobre autenticação, [consulte Autenticar um usuário](~/concepts/authentication/authentication.md).

### <a name="static-tabs-not-showing-up"></a>As guias estáticas não são exibidas

Há um problema conhecido em que a atualização de um aplicativo de bot existente com uma guia estática nova ou atualizada não mostrará essa alteração de guia ao acessar o aplicativo de uma conversa de chat pessoal.  Para ver a alteração, você deve testar em um novo usuário ou instância de teste ou acessar o bot no submenu Aplicativos.

## <a name="troubleshooting-bots"></a>Solução de problemas de bots

### <a name="cant-add-my-bot"></a>Não é possível adicionar meu bot

Os aplicativos devem ser habilitados pelo administrador Office 365 locatário para que eles sejam carregados pelos usuários finais. Em alguns casos, o Office 365 locatário pode ter vários SKUs associados a ele e, para que os bots funcionem em qualquer um, eles devem ser habilitados em todas as SKUs. Para obter mais informações, [consulte Preparar seu Office 365 locatário](~/concepts/build-and-test/prepare-your-o365-tenant.md).

### <a name="cant-add-bot-as-a-member-of-a-team"></a>Não é possível adicionar o bot como membro de uma equipe

Os bots devem primeiro ser carregados em uma equipe antes de serem acessíveis em qualquer canal dessa equipe. Para obter mais informações sobre esse processo, consulte [Carregando seu aplicativo em uma equipe](~/concepts/deploy-and-publish/apps-upload.md).

### <a name="my-bot-doesnt-get-my-message-in-a-channel"></a>Meu bot não obtém minha mensagem em um canal

Os bots em canais recebem mensagens somente quando estão explicitamente @mentioned, mesmo que você esteja respondendo a uma mensagem de bot anterior. A única exceção em que talvez você não veja o nome do bot em uma mensagem é se o bot `imBack` receber uma ação como resultado de uma CardAction que ele enviou originalmente.

### <a name="my-bot-doesnt-understand-my-commands-when-in-a-channel"></a>Meu bot não entende meus comandos quando está em um canal

Como os bots em canais só recebem mensagens quando são @mentioned, todas as mensagens que seu bot recebe em um canal incluem @mention no campo de texto. É uma prática recomendada remover o nome do bot de todas as mensagens de texto de entrada antes de passar para a lógica de análise. Examine [as menções](../bots/how-to/conversations/channel-and-group-conversations.md#work-with-mentions) para obter dicas sobre como lidar com esse caso.

## <a name="issues-with-packaging-and-uploading"></a>Problemas com empacotamento e carregamento

### <a name="error-while-reading-manifestjson"></a>Erro ao ler manifest.json

A maioria dos erros de manifesto fornecerá uma dica sobre qual campo específico está ausente ou inválido. No entanto, se o arquivo JSON não puder ser lido como JSON, essa mensagem de erro genérica será usada.

Motivos comuns para erros de leitura de manifesto:

* JSON inválido. Use um IDE, como [Visual Studio Code](https://code.visualstudio.com) ou [Visual Studio](https://www.visualstudio.com/vs/), que valida automaticamente a sintaxe JSON.
* Problemas de codificação. Use UTF-8 para o *arquivo manifest.json* . Outras codificações, especificamente com a BOM, podem não ser legível.
* Pacote de .zip malformado. O *arquivo manifest.json* deve estar no nível superior do .zip arquivo. Observe que a compactação de arquivo Mac padrão pode colocar *o manifest.json* em um subdiretório, que não será carregado corretamente no Microsoft Teams.

### <a name="another-extension-with-same-id-exists"></a>Existe outra extensão com a mesma ID

Se você estiver tentando carregar um pacote atualizado com a mesma ID novamente, escolha o ícone Substituir  no final da linha da tabela da guia em vez do **botão** Carregar.

Se você não estiver carregando novamente um pacote atualizado, verifique se a ID é exclusiva.
