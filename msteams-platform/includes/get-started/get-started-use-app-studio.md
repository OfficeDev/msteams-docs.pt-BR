### <a name="use-app-studio-to-update-the-app-package"></a>Usar o app Studio para atualizar o pacote de aplicativos

O app Studio é um aplicativo do teams que você pode instalar a partir da loja do teams. Ele simplifica a criação e o registro de um aplicativo.

Para instalar o app Studio no Microsoft Teams, clique no ícone do repositório de aplicativos na parte inferior da barra esquerda e pesquise o app Studio.

<img  width="450px" alt="Finding App Studio in the Store View" src="~/assets/images/get-started/searchforAppStudio.png"/>

Depois de encontrar o bloco para o app Studio, clique nele e escolha *instalar* na caixa de diálogo exibida.

<img  width="450px" alt="Installing App Studio" src="~/assets/images/get-started/InstallingAppStudio.png"/>

Após a instalação do App Studio, clique na guia Editor de manifesto para começar a criar o pacote de aplicativos para seu aplicativo do Microsoft Teams.

<img  width="450px" alt="App Studio" src="~/assets/images/get-started/AppStudio.png"/>

O exemplo vem com seu próprio manifesto predefinido e foi projetado para compilar um pacote de aplicativos quando o projeto é criado. No .NET, isso é feito no Visual Studio e no nó JS isso é feito digitando `gulp` na linha de comando no diretório raiz do projeto.

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

O nome do pacote de aplicativos gerado é *helloworldapp.zip*. Você pode pesquisar esse arquivo se o local não estiver limpo na ferramenta que você está usando.

Na próxima parte desta explicação passo a passo, você irá modificar esse pacote de aplicativos selecionando o bloco *importar um aplicativo existente* no editor de manifesto.

<img  width="450px" alt="Importing an existing app" src="~/assets/images/get-started/Importinganapp.png"/>

Depois que o pacote do aplicativo tiver sido importado, o app Studio deverá ter a seguinte aparência:

<img  width="450px" alt="Importing the app package" src="~/assets/images/get-started/Importinganapp2.png"/>

Clique no bloco para seu aplicativo recentemente importado, *Olá mundo*.

<img  width="450px" alt="Newly imported app view" src="~/assets/images/get-started/HelloWorldappdetails.png"/>

Há uma lista de etapas no lado esquerdo do editor de manifestos e, à direita, uma lista de propriedades que precisam ser preenchidas para cada uma dessas etapas. Desde que você começou com um exemplo de aplicativo, muitas das informações já estão preenchidas. As etapas a seguir irão orientá-lo durante a alteração das partes que ainda precisam ser atualizadas.

#### <a name="app-details"></a>Detalhes do aplicativo

Clique na entrada de *detalhes do aplicativo* em *detalhes*. Clique no botão *gerar* para criar uma nova ID de aplicativo.

Sua nova ID de aplicativo deve ser semelhante a: `2322041b-72bf-459d-b107-f4f335bc35bd` .

Examine o restante dos detalhes do aplicativo no painel à direita e familiarize-se com algumas das entradas, como informações de *desenvolvedor* e *identidade visual*. Essas seções são importantes se você estiver escrevendo um novo aplicativo para distribuição.

#### <a name="capabilities-tabs"></a>Recursos: guias

As guias estão entre os elementos mais simples a serem adicionados a um aplicativo do teams. O aplicativo de exemplo já oferece suporte a várias guias, e você pode habilitá-los da seguinte maneira.

##### <a name="team-tab"></a>Guia equipe

Seu aplicativo pode ter apenas uma guia de equipe.

<img  width="450px" alt="Adding a Teams tab" src="~/assets/images/get-started/TeamTab.png"/>

Neste exemplo, a guia equipe é onde a página de configuração vai. Clique no símbolo *...* no final da entrada e escolha *Editar* na lista suspensa. Altere a URL para `https://yourteamsapp.ngrok.io/configure` onde ela `yourteamsapp.ngrok.io` deve ser substituída pela URL que você usou acima ao hospedar seu aplicativo.

##### <a name="personal-tabs"></a>Guias pessoais

Seu aplicativo pode ter até 16 guias, incluindo a guia equipe.

As guias pessoais são representadas de forma diferente da guia equipe. Você deve ver a *guia saudação* já listada na lista guias pessoais. No momento, ele tem um valor de espaço reservado `com.contoso.helloworld.hellotab` . Clique no símbolo *...* no final da entrada e escolha *Editar* na lista suspensa. A caixa de diálogo a seguir será exibida.

<img  width="450px" alt="Adding a personal tab dialog" src="~/assets/images/get-started/PersonalTab.png"/>

Há dois campos que você precisa atualizar com a URL do aplicativo.

- Alterar URL de conteúdo para `https://yourteamsapp.ngrok.io/hello`
- Altere a URL do site para `https://yourteamsapp.ngrok.io/hello`

Onde `yourteamsapp.ngrok.io` o deve ser substituído pela URL que você usou acima ao hospedar seu aplicativo.

#### <a name="bots"></a>Bots

Os bots são a maneira mais comum de adicionar funcionalidade ao seu aplicativo. O exemplo Hello World já tem um bot como parte da amostra, mas ainda não foi registrado com a Microsoft.

<img  width="450px" alt="Adding a bot" src="~/assets/images/get-started/Bots.png"/>

O bot que foi importado do exemplo ainda não tem uma ID de aplicativo associada a ele. Você precisará criar um novo bot para que o app Studio possa criar uma nova ID de aplicativo e registrá-lo com a Microsoft. Observe que esta é a ID do aplicativo do bot, que é diferente da ID do aplicativo que criamos para o aplicativo em uma etapa anterior. Cada bot em um aplicativo requer sua própria ID de aplicativo.

Clique no botão *excluir* ao lado do *bot importado* na lista bot.

Agora não há bots para mostrar. Clique em *Configurar*. Isso exibirá a caixa de diálogo *configurar um bot* .

<img  width="450px" alt="Adding a bot dialog" src="~/assets/images/get-started/Setupbot.png"/>

Adicione um nome de bot, como `Contoso bot` e clique em ambos os botões em *escopo*.

Escolha *criar bot* para sair da caixa de diálogo. O app Studio gastará um momento registrando seu bot com a Microsoft e, em seguida, deverá exibir o novo bot na lista de bot. Agora seria uma boa hora para abrir um arquivo de texto no bloco de notas e copiar e colar sua nova ID de bot nela. Você precisará dessa ID mais tarde.

Clique em *gerar nova senha*e anote a senha no mesmo arquivo de texto em que você ANOTOU a ID do aplicativo do bot. Esta é a única vez que a senha será mostrada, portanto, certifique-se de fazer isso agora.

Atualize o *endereço do ponto de extremidade do bot* para `https://yourteamsapp.ngrok.io/api/messages` , onde `yourteamsapp.ngrok.io` deve ser substituído pela URL que você usou acima ao hospedar seu aplicativo.

Agora seria uma boa hora para salvar seu arquivo de texto se você ainda não tiver feito isso. Você adicionará essas informações ao seu aplicativo hospedado posteriormente nesta explicação passo a passo, que permitirá a comunicação segura com o bot.

#### <a name="messaging-extensions"></a>Extensões de mensagens

As extensões de mensagens permitem aos usuários solicitar informações do seu serviço e postá-las, na forma de cartões, diretamente na conversa do canal. As extensões de mensagens aparecem ao longo da parte inferior da caixa de composição.

Clique em *extensões de mensagens* em *recursos* na coluna esquerda do App Studio para começar a configurar a extensão de mensagens.

<img  width="450px" alt="Adding a messaging extension" src="~/assets/images/get-started/Messagingextensions.png"/>

O exemplo de extensão de mensagens está listado no painel direito em *extensões de mensagens*. Clique em *excluir* novamente para remover essa entrada e clique no botão *Configurar* seguindo as mesmas etapas que você seguiu para os bots. Isso exibirá a caixa de diálogo *extensão de mensagens* .

Selecione a guia *usar bot existente* e, em seguida, *Selecione um dos meus bots existentes*. No menu suspenso, selecione o bot que você criou na seção acima. Adicione um *nome de bot* e clique em *salvar* para fechar a caixa de diálogo.

Na seção *comando* , clique em *Adicionar*. Estamos adicionando um comando baseado em pesquisa, portanto, escolha a opção *permitir que os usuários consultem seu serviço...* .

Na caixa de diálogo *novo comando* , insira os seguintes valores.

Em *novo comando*:

- *ID do comando*  = getRandomText
- *Título*       = obter texto aleatório para diversão
- *Descrição* = Obtém alguns textos e imagens aleatórias

Em *Parameter*:

- *Name*        = cardTitle
- *Título*       = título do cartão
- *Descrição* = título do cartão a ser usado

Depois de inserir as informações, clique em *salvar* para fechar a caixa de diálogo.

#### <a name="register-your-app-in-teams"></a>Registrar seu aplicativo no Microsoft Teams

Você já concluiu a inserção dos detalhes do seu aplicativo, mas duas etapas permanecem. Primeiro, você deve usar a seção testar e distribuir do App Studio para instalar seu aplicativo no Microsoft Teams e, em seguida, você deve atualizar seu aplicativo hospedado com a ID do aplicativo e a senha do bot. Lembre-se de que o exemplo espera usar a mesma ID de aplicativo e senha para o bot e a extensão de mensagens.

Clique no botão *testar e distribuir* item em *concluir* , na coluna esquerda do App Studio.

<img  width="450px" alt="Testing your app" src="~/assets/images/get-started/Testanddistribute.png"/>

Para carregar o aplicativo no Microsoft Teams, clique no botão *instalar* em *testar e distribuir*.

<img  width="450px" alt="Adding a messaging extension dialog" src="~/assets/images/get-started/InstallingHelloWorld.png"/>

Clique na caixa de *pesquisa* na seção *Adicionar a uma equipe* e selecione uma equipe para adicionar o aplicativo de exemplo ao. Normalmente, você deve configurar uma equipe especial para teste.

Clique no botão *instalar* na parte inferior da caixa de diálogo.

Isso termina a parte do App Studio deste passo a passo. Agora você deve ver seu aplicativo em execução no Teams, mas o bot e a extensão de mensagens não funcionarão até que você atualize o ambiente de aplicativos hospedados para saber quais são as IDs de aplicativo e senhas.

<img  width="450px" alt="The finished app" src="~/assets/images/get-started/Finishedhelloworld.png"/>
