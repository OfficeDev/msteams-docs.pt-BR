## <a name="add-a-messaging-extension-to-your-app"></a>Adicionar uma extensão de mensagens ao seu aplicativo

Uma extensão de mensagens é um serviço hospedado na nuvem que escuta solicitações de usuário e responde com dados estruturados, como um [cartão](~/task-modules-and-cards/what-are-cards.md). Você integra seu serviço com Microsoft Teams por meio de objetos da Estrutura de `Activity` Bot. Nossas extensões .NET e Node.js para o SDK do Construtor de Bots podem ajudá-lo a adicionar a funcionalidade de extensão de mensagens ao seu aplicativo.

![Diagrama de fluxo de mensagens para extensões de mensagens](~/assets/images/compose-extensions/ceflow.png)

### <a name="register-in-the-bot-framework"></a>Registrar-se na Estrutura de Bots

Se você ainda não fez isso, primeiro registre um bot com o Microsoft Bot Framework. A ID do aplicativo Microsoft e os pontos de extremidade de retorno de chamada para seu bot, conforme definido lá, serão usados na extensão de mensagens para receber e responder às solicitações do usuário. Lembre-se de habilitar o Microsoft Teams do seu bot.

Grave a ID do aplicativo bot e a senha do aplicativo, você precisará fornecer a ID do aplicativo no manifesto do aplicativo.

### <a name="update-your-app-manifest"></a>Atualizar o manifesto do aplicativo

Assim como com bots e guias, você atualiza o [manifesto](~/resources/schema/manifest-schema.md#composeextensions) do seu aplicativo para incluir as propriedades de extensão de mensagens. Essas propriedades regem como sua extensão de mensagens aparece e se comporta no cliente Microsoft Teams de mensagens. As extensões de mensagens são suportadas começando com v1.0 do manifesto.

#### <a name="declare-your-messaging-extension"></a>Declarar sua extensão de mensagens

Para adicionar uma extensão de mensagens, inclua uma nova estrutura JSON de nível superior em seu manifesto com a `composeExtensions` propriedade. Atualmente, você está limitado a criar uma única extensão de mensagens para seu aplicativo.

> [!NOTE]
> O manifesto refere-se a extensões de mensagens como `composeExtensions` . Isso é para manter a compatibilidade com compatibilidade com backward.

A definição de extensão é um objeto que tem a seguinte estrutura:

| Nome da propriedade | Objetivo | Obrigatório? |
|---|---|---|
| `botId` | O ID exclusivo do aplicativo Microsoft para o bot conforme registrado na estrutura do bot. Normalmente, isso deve ser o mesmo que a ID do seu aplicativo Teams geral. | Sim |
| `scopes` | Matriz declarando se essa extensão pode ser adicionada `personal` ou `team` escopos (ou ambos). | Sim |
| `canUpdateConfiguration` | Habilita **Configurações** item de menu. | Não |
| `commands` | Matriz de comandos compatíveis com essa extensão de mensagens. Você está limitado a 10 comandos. | Sim |

#### <a name="define-commands"></a>Definir comandos

Sua extensão de mensagens deve declarar um comando, que aparece quando o usuário seleciona seu aplicativo no botão **Mais** opções (**&#8943;**) na caixa de redação.

![Captura de tela da lista de extensões de mensagens no Teams](~/assets/images/compose-extensions/compose-extension-list.png)

No manifesto do aplicativo, o item de comando é um objeto com a seguinte estrutura:

| Nome da propriedade | Objetivo | Obrigatório? | Versão mínima do manifesto |
|---|---|---|---|
| `id` | ID exclusiva que você atribui a esse comando. A solicitação do usuário incluirá essa ID. | Sim | 1.0 |
| `title` | Nome do comando. Esse valor aparece na interface do usuário. | Sim | 1.0 |
| `description` | Texto de ajuda que indica o que esse comando faz. Esse valor aparece na interface do usuário. | Sim | 1.0 |
| `type` | De definir o tipo de comando. Os valores possíveis incluem `query` e `action`. Se não estiver presente, o valor padrão será definido como `query` . | Não | 1.4 |
| `initialRun` | Parâmetro opcional, usado com `query` comandos. Se definido como **true**, indica que esse comando deve ser executado assim que o usuário escolher esse comando na interface do usuário. | Não | 1.0 |
| `fetchTask` | Parâmetro opcional, usado com `action` comandos. De definida **como true** para buscar o cartão adaptável ou a URL da Web para exibição no módulo [de tarefa](~/task-modules-and-cards/what-are-task-modules.md). Isso é usado quando as entradas para o comando são dinâmicas em vez `action` de um conjunto estático de parâmetros. Observe que a lista de parâmetros estáticos se definida como **true** para o comando é ignorada. | Não | 1.4 |
| `parameters` | Lista estática de parâmetros para o comando. | Sim | 1.0 |
| `parameter.name` | O nome do parâmetro. Isso é enviado ao seu serviço na solicitação do usuário. | Sim | 1.0 |
| `parameter.description` | Descreve as finalidades desse parâmetro ou o exemplo do valor que deve ser fornecido. Esse valor aparece na interface do usuário. | Sim | 1.0 |
| `parameter.title` | Título ou rótulo de parâmetro fácil de usar curto. | Sim | 1.0 |
| `parameter.inputType` | De acordo com o tipo de entrada necessário. Os valores possíveis `text` `textarea` incluem , `number` , , , , `date` `time` `toggle` . O padrão é definido como `text` . | Não | 1.4 |
| `context` | Matriz opcional de valores que define o contexto em que a ação da mensagem está disponível. Os valores possíveis `message` são `compose` , ou `commandBox` . O padrão é `["compose", "commandBox"]`. | Não | 1,5 |
