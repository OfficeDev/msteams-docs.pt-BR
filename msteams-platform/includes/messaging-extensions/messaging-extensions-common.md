## <a name="add-a-messaging-extension-to-your-app"></a>Adicionar uma extensão de mensagem ao seu aplicativo

Uma extensão de mensagens é um serviço hospedado na nuvem que escuta solicitações de usuário e responde com dados estruturados, como um [cartão](~/task-modules-and-cards/what-are-cards.md). Você integra seu serviço ao Microsoft Teams via objetos `Activity` da estrutura de bot. As extensões .NET e node. js para o SDK do bot Builder podem ajudá-lo a adicionar a funcionalidade de extensão de mensagens ao seu aplicativo.

![Diagrama do fluxo de mensagens para extensões de mensagens](~/assets/images/compose-extensions/ceflow.png)

### <a name="register-in-the-bot-framework"></a>Registrar-se na estrutura de bot

Se ainda não tiver feito isso, primeiro você deve registrar um bot com a Microsoft bot Framework. A ID do aplicativo da Microsoft e os pontos de extremidade de retorno de chamada do bot, conforme definido aqui, serão usados em sua extensão de mensagens para receber e responder às solicitações do usuário. Lembre-se de habilitar o canal do Microsoft Teams para o bot.

Registre sua ID de aplicativo do bot e a senha do aplicativo, você precisará fornecer a ID do aplicativo em seu manifesto do aplicativo.

### <a name="update-your-app-manifest"></a>Atualizar o manifesto do aplicativo

Como com bots e guias, você atualiza o [manifesto](~/resources/schema/manifest-schema.md#composeextensions) do seu aplicativo para incluir as propriedades de extensão de mensagens. Essas propriedades controlam como sua extensão de mensagens aparece e se comporta no cliente Microsoft Teams. As extensões de mensagens têm suporte a partir da versão v 1.0 do manifesto.

#### <a name="declare-your-messaging-extension"></a>Declarar sua extensão de mensagens

Para adicionar uma extensão de mensagens, inclua uma nova estrutura JSON de nível superior no manifesto com a `composeExtensions` propriedade. Atualmente, você está limitado a criar uma única extensão de mensagens para o seu aplicativo.

> [!NOTE]
> O manifesto se refere a extensões de `composeExtensions`mensagens como. Isso é para manter a compatibilidade com versões anteriores.

A definição de extensão é um objeto que tem a seguinte estrutura:

| Nome da propriedade | Finalidade | Obrigatório? |
|---|---|---|
| `botId` | A ID exclusiva do aplicativo da Microsoft para o bot, conforme registrado na estrutura do bot. Isso deve ser normalmente o mesmo que a ID do aplicativo de suas equipes gerais. | Sim |
| `scopes` | Matriz que declara se essa extensão pode ser adicionada `personal` a `team` ou escopos (ou ambos). | Sim |
| `canUpdateConfiguration` | Habilita o item de menu **configurações** . | Não |
| `commands` | Matriz de comandos que esta extensão de mensagens suporta. Você está limitado a 10 comandos. | Sim |

#### <a name="define-commands"></a>Definir comandos

Sua extensão de mensagens deve declarar um comando, que aparece quando o usuário seleciona seu aplicativo no botão **mais opções** (**&#8943;**) na caixa de composição.

![Captura de tela da lista de extensões de mensagens no Microsoft Teams](~/assets/images/compose-extensions/compose-extension-list.png)

No manifesto do aplicativo, seu item de comando é um objeto com a seguinte estrutura:

| Nome da propriedade | Finalidade | Obrigatório? | Versão mínima do manifesto |
|---|---|---|---|
| `id` | ID exclusiva que você atribui a este comando. A solicitação do usuário incluirá essa ID. | Sim | 1.0 |
| `title` | Nome do comando. Esse valor é exibido na interface do usuário. | Sim | 1.0 |
| `description` | Texto de ajuda que indica o que esse comando faz. Esse valor é exibido na interface do usuário. | Sim | 1.0 |
| `type` | Defina o tipo de comando. Os valores possíveis incluem `query` e `action`. Se não estiver presente, o valor padrão será definido como`query` | Não | 1.4 |
| `initialRun` | Parâmetro opcional, usado com `query` comandos. Se definido como **true**, indica que este comando deve ser executado assim que o usuário escolhe este comando na interface do usuário. | Não | 1.0 |
| `fetchTask` | Parâmetro opcional, usado com `action` comandos. Defina como **true** para buscar o cartão adaptável ou a URL da Web a serem exibidos no [módulo de tarefa](~/task-modules-and-cards/what-are-task-modules.md). Isso é usado quando as entradas do `action` comando são dinâmicas, em vez de um conjunto estático de parâmetros. Observe que, se definido como **true** , a lista de parâmetros estáticos do comando é ignorada | Não | 1.4 |
| `parameters` | Lista estática de parâmetros para o comando. | Sim | 1.0 |
| `parameter.name` | O nome do parâmetro. Isso é enviado para o serviço na solicitação do usuário. | Sim | 1.0 |
| `parameter.description` | Descreve os fins deste parâmetro ou o exemplo do valor que deve ser fornecido. Esse valor é exibido na interface do usuário. | Sim | 1.0 |
| `parameter.title` | Título ou rótulo curto de parâmetro amigável. | Sim | 1.0 |
| `parameter.inputType` | Defina como o tipo de entrada obrigatória. Os valores possíveis `text`incluem `textarea`, `number` `date` `time`,,, `toggle`. O padrão é definido como`text` | Não | 1.4 |
| `context` | Matriz opcional de valores que define o contexto no qual a ação de mensagem está disponível. Os valores possíveis `message`são `compose`,, `commandBox`ou. O padrão é `["compose", "commandBox"]`. | Não | 1,5 |
