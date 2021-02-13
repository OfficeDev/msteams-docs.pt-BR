### <a name="use-app-studio-to-update-the-app-package"></a>Usar o App Studio para atualizar o pacote do aplicativo

O App Studio é um aplicativo do Teams que você pode instalar na loja do Teams. Isso simplifica a criação e o registro de um aplicativo.

Para instalar o App Studio  no Teams, selecione o ícone Aplicativos na parte inferior da barra esquerda e procure o **App Studio.**

<img  width="450px" alt="Finding App Studio in the Store View" src="~/assets/images/get-started/searchforAppStudio.png"/>

Selecione o **tile do App Studio** e escolha **Instalar.** O App Studio está instalado.

<img  width="450px" alt="Installing App Studio" src="~/assets/images/get-started/InstallingAppStudio.png"/>

Selecione a **guia Editor de** manifesto para criar o pacote do aplicativo para seu aplicativo do Teams.

<img  width="450px" alt="App Studio" src="~/assets/images/get-started/AppStudio.png"/>

O exemplo vem com seu próprio manifesto pré-criado e foi projetado para criar um pacote do aplicativo quando o projeto é criado. No .NET, isso é feito no Visual Studio e, no Nó JS, isso é feito digitando na linha de comando no diretório `gulp` raiz do projeto.

```bash
$ gulp
[13:39:27] Using gulpfile ~\documents\github\msteams-samples-hello-world-nodejs\gulpfile.js
[13:39:27] Starting 'clean'...
[13:39:27] Starting 'generate-manifest'...
[13:39:27] Finished 'generate-manifest' after 11 ms
[13:39:27] Finished 'clean' after 21 ms
[13:39:27] Starting 'default'...
Build completed. Output in manifest folder
[13:39:27] Finished 'default' after 62 μs
```

O nome do pacote do aplicativo gerado é **helloworldapp.zip**. Você pode procurar esse arquivo se o local não estiver claro na ferramenta que está usando.

Agora, para modificar esse pacote do aplicativo, selecione o pacote Importar um **aplicativo** existente no **editor de manifesto.**

<img  width="450px" alt="Importing an existing app" src="~/assets/images/get-started/Importinganapp.png"/>

Clique no **lado do lado** hello world do aplicativo recém-importado.

<img  width="450px" alt="Newly imported app view" src="~/assets/images/get-started/HelloWorldappdetails.png"/>

A imagem a seguir mostra o pacote do aplicativo importado no App Studio:

<img  width="450px" alt="Importing the app package" src="~/assets/images/get-started/Importinganapp2.png"/>

Há uma lista de etapas no lado esquerdo do editor de Manifesto e no lado direito, uma lista de propriedades que precisam ser preenchidas para cada uma dessas etapas. Desde que você começou com um aplicativo de exemplo, grande parte das informações já está preenchida. As próximas etapas o ajudarão a alterar as partes que ainda precisam ser atualizadas.

#### <a name="app-details"></a>Detalhes do aplicativo

Clique na entrada *de detalhes do* aplicativo em *Detalhes.* Clique no *botão Gerar* para criar uma nova ID de aplicativo.

Sua nova ID de aplicativo deve se parecer com: `2322041b-72bf-459d-b107-f4f335bc35bd` .

Procure o restante dos detalhes do aplicativo no painel à direita e familiarize-se  com algumas das entradas, como informações do desenvolvedor e *identidade visual.* Essas seções são importantes se você estiver escrevendo um novo aplicativo para distribuição.

#### <a name="capabilities-tabs"></a>Recursos: guias

As guias estão entre os elementos mais simples a adicionar a um aplicativo do Teams. O aplicativo de exemplo já dá suporte a várias guias, e você pode habilita-las da seguinte forma.

##### <a name="team-tab"></a>Guia Equipe

Seu aplicativo só pode ter uma guia Equipe.

<img  width="450px" alt="Adding a Teams tab" src="~/assets/images/get-started/TeamTab.png"/>

Neste exemplo, a guia Equipe é onde sua página de configuração vai. Clique no *símbolo ...* no final da entrada e escolha *Editar* no drop-down. Altere a URL `https://yourteamsapp.ngrok.io/configure` para onde deve ser substituída pela URL que você usou acima ao hospedar seu `yourteamsapp.ngrok.io` aplicativo.

##### <a name="personal-tabs"></a>Guias pessoais

Seu aplicativo pode ter até 16 guias, incluindo a guia da equipe.

As guias pessoais são representadas de forma diferente da guia da equipe. Você deverá ver *a guia Hello* já listada na lista de guias pessoais. No momento, ele tem um valor de espaço `com.contoso.helloworld.hellotab` reservado. Clique no *símbolo ...* no final da entrada e escolha *Editar* no drop-down. A caixa de diálogo a seguir será exibida.

<img  width="450px" alt="Adding a personal tab dialog" src="~/assets/images/get-started/PersonalTab.png"/>

Há dois campos que você precisa atualizar com a URL do aplicativo.

- Alterar a URL de Conteúdo para `https://yourteamsapp.ngrok.io/hello`
- Alterar a URL do site para `https://yourteamsapp.ngrok.io/hello`

Onde deve ser substituído pela URL que você `yourteamsapp.ngrok.io` usou acima ao hospedar seu aplicativo.

#### <a name="bots"></a>Bots

Os bots são a maneira mais comum de adicionar funcionalidade ao seu aplicativo. O exemplo hello world já tem um bot como parte do exemplo, mas ele ainda não foi registrado com a Microsoft.

<img  width="450px" alt="Adding a bot" src="~/assets/images/get-started/Bots.png"/>

O bot que foi importado da amostra ainda não tem uma ID de aplicativo associada a ele. Você terá que criar um novo bot para que o App Studio possa criar uma nova ID de aplicativo e registrá-la na Microsoft. Observe que essa é a ID do aplicativo para o bot, que é diferente da ID do aplicativo criada para o aplicativo. Cada bot em um aplicativo requer sua própria ID de aplicativo.

Clique no *botão excluir* ao lado do *bot importado* na lista de bots.

Agora não há bots a mostrar. Clique *em Instalação.* Isso exibirá a caixa de diálogo Configurar *um bot.*

<img  width="450px" alt="Adding a bot dialog" src="~/assets/images/get-started/Setupbot.png"/>

Adicione um nome de bot, como `Contoso bot` , e selecione todos os três botões em **Escopo**.

Escolha *Criar bot* para sair da caixa de diálogo. O App Studio registra seu bot na Microsoft e exibe seu novo bot na lista de bots. Agora seria um bom momento para abrir um arquivo de texto no bloco de notas e copiar e colar sua nova ID de bot nele. Você precisará dessa ID mais tarde.

Clique *em Gerar* Nova Senha e anote a senha no mesmo arquivo de texto em que você anotou sua ID de aplicativo bot. Esta é a única vez que sua senha será mostrada, portanto, certifique-se de fazer isso agora.

Atualize *o endereço do ponto* de extremidade bot para , onde deve ser substituído pela URL que você usou acima ao hospedar seu `https://yourteamsapp.ngrok.io/api/messages` `yourteamsapp.ngrok.io` aplicativo.

Agora seria um bom momento para salvar seu arquivo de texto se você ainda não tiver feito isso. Você adicionará essas informações ao seu aplicativo hospedado posteriormente neste passo a passo, o que permitirá uma comunicação segura com seu bot.

#### <a name="messaging-extensions"></a>Extensões de mensagens

As extensões de mensagens permitem que os usuários peçam informações do seu serviço e postem essas informações, na forma de cartões, direto para a conversa do canal. As extensões de mensagens aparecem na parte inferior da caixa de redação.

Selecione **extensões de Mensagens** em **Funcionalidades** na coluna à esquerda do App Studio para configurar a extensão de mensagens.

<img  width="450px" alt="Adding a messaging extension" src="~/assets/images/get-started/Messagingextensions.png"/>

A extensão de mensagens de exemplo está listada no painel à direita em **Extensões de Mensagens.** Selecione **Excluir** novamente para remover essa  entrada e clique no botão Configurar seguindo as mesmas etapas que você seguiu para bots. Isso exibirá a caixa *de diálogo Extensão de* Mensagens.

Selecione a *guia Usar bot* existente e selecione de um dos meus *bots existentes.* No menu suspenso, selecione o bot que você criou na seção acima. Adicione um *nome de bot e* clique em *Salvar* para fechar a caixa de diálogo.

Na seção *Comando,* clique em *Adicionar*. Estamos adicionando um comando baseado em pesquisa, portanto, escolha a opção Permitir que os usuários *consultem seu serviço...*

Na caixa **de diálogo Novo** comando, insira os seguintes valores.

Em *Novo comando:*

- *ID do comando*  = getRandomText
- *Title*       = Obter algum texto aleatório por diversão
- *Descrição* = obtém texto aleatório e imagens

Sob *Parâmetro:*

- *Name*        = cardTitle
- *Título*       = Título do cartão
- *Descrição* = Título do cartão a ser usado

Quando você for inserido nas informações, clique em *Salvar* para fechar a caixa de diálogo.

#### <a name="register-your-app-in-teams"></a>Registrar seu aplicativo no Teams

Agora você concluiu a inserção dos detalhes do seu aplicativo, mas as duas etapas a seguir permanecem:
1. Use a seção Testar e Distribuir do App Studio para instalar seu aplicativo no Teams.
1. Atualize seu aplicativo hospedado com a ID do aplicativo e a senha do seu bot. Lembre-se de que o exemplo espera usar a mesma ID de aplicativo e senha para o bot e a extensão de mensagens.

Selecione o **teste e distribua** o item **em Concluir** na coluna à esquerda do App Studio.

<img  width="450px" alt="Testing your app" src="~/assets/images/get-started/Testanddistribute.png"/>

Para carregar seu aplicativo no Teams, clique no botão *Instalar* em *Testar e Distribuir.*

<img  width="450px" alt="Adding a messaging extension dialog" src="~/assets/images/get-started/InstallingHelloWorld.png"/>

Selecione a **caixa Pesquisar** na seção Adicionar a **uma equipe** e selecione uma equipe para adicionar o aplicativo de exemplo. Normalmente, você pode configurar uma equipe especial para teste.

Selecione o **botão** Instalar na parte inferior da caixa de diálogo.

Isso finaliza a parte do App Studio deste passo a passo. Agora você deve ver seu aplicativo em execução no Teams, no entanto, o bot e a extensão de mensagens não funcionarão até que você atualize o ambiente de aplicativos hospedados para saber quais são as IDs de aplicativo e senhas.

<img  width="450px" alt="The finished app" src="~/assets/images/get-started/Finishedhelloworld.png"/>
