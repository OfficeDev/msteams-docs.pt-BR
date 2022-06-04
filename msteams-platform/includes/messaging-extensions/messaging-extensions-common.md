## <a name="add-a-message-extension-to-your-app"></a>Adicionar uma extensão de mensagem ao seu aplicativo

Uma extensão de mensagem é um serviço hospedado na nuvem que escuta as solicitações do usuário e responde com dados estruturados, como um [cartão](~/task-modules-and-cards/what-are-cards.md). Você integra seu serviço ao Microsoft Teams por meio de objetos do Bot Framework `Activity` . Nossas extensões .NET e Node.js para o SDK do Bot Builder podem ajudá-lo a adicionar a funcionalidade de extensão de mensagem ao seu aplicativo.

![Diagrama do fluxo de mensagens para extensões de mensagem](~/assets/images/compose-extensions/ceflow.png)

### <a name="register-in-the-bot-framework"></a>Registrar-se no Bot Framework

Se você ainda não fez isso, primeiro registre um bot no Microsoft Bot Framework. A ID do aplicativo da Microsoft e os pontos de extremidade de retorno de chamada para o bot, conforme definido lá, serão usados na extensão de mensagem para receber e responder às solicitações do usuário. Lembre-se de habilitar o canal do Microsoft Teams para seu bot.

Registre a ID do aplicativo de bot e a senha do aplicativo, você precisará fornecer a ID do aplicativo no manifesto do aplicativo.

### <a name="update-your-app-manifest"></a>Atualizar o manifesto do aplicativo

Assim como com bots e guias, você atualiza o [manifesto](~/resources/schema/manifest-schema.md#composeextensions) do aplicativo para incluir as propriedades de extensão da mensagem. Essas propriedades regem como sua extensão de mensagem aparece e se comporta no cliente do Microsoft Teams. Há suporte para extensões de mensagem a partir da v1.0 do manifesto.

#### <a name="declare-your-message-extension"></a>Declarar sua extensão de mensagem

Para adicionar uma extensão de mensagem, inclua uma nova estrutura JSON de nível superior em seu manifesto com a `composeExtensions` propriedade. Atualmente, você está limitado a criar uma única extensão de mensagem para seu aplicativo.

> [!NOTE]
> O manifesto refere-se a extensões de mensagem como `composeExtensions`. Isso é para manter a compatibilidade com versões anteriores.

A definição de extensão é um objeto que tem a seguinte estrutura:

| Nome da propriedade | Objetivo | Obrigatório? |
|---|---|---|
| `botId` | O ID exclusivo do aplicativo Microsoft para o bot conforme registrado na estrutura do bot. Normalmente, isso deve ser o mesmo que a ID do aplicativo geral do Teams. | Sim |
| `scopes` | Matriz declarando se essa extensão pode ser adicionada ou `personal` escopos `team` (ou ambos). | Sim |
| `canUpdateConfiguration` | Habilita **o item de menu Configurações** . | Não |
| `commands` | Matriz de comandos compatíveis com essa extensão de mensagem. Você está limitado a 10 comandos. | Sim |

#### <a name="define-commands"></a>Definir comandos

Sua extensão de mensagem deve declarar um comando, que aparece quando o usuário seleciona seu aplicativo no botão Mais **opções (****&#8943;**) na caixa de redação.

![Captura de tela da lista de extensões de mensagem no Teams](~/assets/images/compose-extensions/compose-extension-list.png)

No manifesto do aplicativo, o item de comando é um objeto com a seguinte estrutura:

| Nome da propriedade | Objetivo | Obrigatório? | Versão mínima do manifesto |
|---|---|---|---|
| `id` | ID exclusiva que você atribui a este comando. A solicitação do usuário incluirá essa ID. | Sim | 1.0 |
| `title` | Nome do comando. Esse valor aparece na interface do usuário. | Sim | 1.0 |
| `description` | Texto de ajuda que indica o que esse comando faz. Esse valor aparece na interface do usuário. | Sim | 1.0 |
| `type` | Defina o tipo de comando. Os valores possíveis incluem `query` e `action`. Caso contrário, o valor padrão será definido como `query`. | Não | 1.4 |
| `initialRun` | Parâmetro opcional, usado com `query` comandos. Se definido como **true**, indica que esse comando deve ser executado assim que o usuário escolher esse comando na interface do usuário. | Não | 1.0 |
| `fetchTask` | Parâmetro opcional, usado com `action` comandos. Defina **como true** para buscar o cartão adaptável ou a URL da Web a ser exibida no [módulo de tarefa](~/task-modules-and-cards/what-are-task-modules.md). Isso é usado quando a entrada para o comando `action` é dinâmica em vez de um conjunto estático de parâmetros. Observe que, se definido como **true** , a lista de parâmetros estáticos para o comando será ignorada. | Não | 1.4 |
| `parameters` | Lista estática de parâmetros para o comando. | Sim | 1.0 |
| `parameter.name` | O nome do parâmetro. Isso é enviado ao seu serviço na solicitação do usuário. | Sim | 1.0 |
| `parameter.description` | Descreve as finalidades desse parâmetro ou o exemplo do valor que deve ser fornecido. Esse valor aparece na interface do usuário. | Sim | 1.0 |
| `parameter.title` | Título ou rótulo de parâmetro amigável curto. | Sim | 1.0 |
| `parameter.inputType` | Defina como o tipo de entrada necessário. Os valores possíveis `text`incluem `textarea`, `number`, , `date`, `time`. `toggle` O padrão é definido como `text`. | Não | 1.4 |
| `context` | Matriz opcional de valores que define o contexto em que a ação de mensagem está disponível. Os valores possíveis `message`são , `compose`ou `commandBox`. O padrão é `["compose", "commandBox"]`. | Não | 1,5 |
