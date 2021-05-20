## <a name="add-a-messaging-extension-to-your-app"></a>Adicione uma extensão de mensagens ao seu aplicativo

Uma extensão de mensagens é um serviço hospedado na nuvem que ouve solicitações do usuário e responde com dados estruturados, como um [cartão](~/task-modules-and-cards/what-are-cards.md). Você integra seu serviço com Microsoft Teams através de objetos Bot `Activity` Framework. Nossas extensões .NET e Node.js para o Bot Builder SDK podem ajudá-lo a adicionar a funcionalidade de extensão de mensagens ao seu aplicativo.

![Diagrama do fluxo de mensagens para extensões de mensagens](~/assets/images/compose-extensions/ceflow.png)

### <a name="register-in-the-bot-framework"></a>Registre-se no Quadro de Bots

Se você ainda não fez isso, você deve primeiro registrar um bot com o Microsoft Bot Framework. O ID do aplicativo da Microsoft e os pontos finais de retorno de chamada para o seu bot, conforme definido lá, serão usados na sua extensão de mensagens para receber e responder às solicitações do usuário. Lembre-se de ativar o canal Microsoft Teams para o seu bot.

Registo o ID do aplicativo do bot e a senha do aplicativo, você precisará fornecer o ID do aplicativo no seu manifesto do aplicativo.

### <a name="update-your-app-manifest"></a>Atualize seu manifesto de aplicativo

Assim como bots e guias, você atualiza o [manifesto](~/resources/schema/manifest-schema.md#composeextensions) do seu aplicativo para incluir as propriedades de extensão de mensagens. Essas propriedades regem como sua extensão de mensagens aparece e se comporta no Microsoft Teams cliente. As extensões de mensagens são suportadas a partir do v1.0 do manifesto.

#### <a name="declare-your-messaging-extension"></a>Declare sua extensão de mensagens

Para adicionar uma extensão de mensagens, inclua uma nova estrutura JSON de alto nível em seu manifesto com a `composeExtensions` propriedade. Atualmente, você está limitado a criar uma única extensão de mensagens para o seu aplicativo.

> [!NOTE]
> O manifesto refere-se a extensões de mensagens como `composeExtensions` . Isto é para manter a compatibilidade retrógrada.

A definição de extensão é um objeto que tem a seguinte estrutura:

| Nome da propriedade | Objetivo | Obrigatório? |
|---|---|---|
| `botId` | O ID exclusivo do aplicativo Microsoft para o bot conforme registrado na estrutura do bot. Isso normalmente deve ser o mesmo que o ID para o seu aplicativo de Teams geral. | Sim |
| `scopes` | Matriz declarando se essa extensão pode ser adicionada `personal` ou `team` escopos (ou ambos). | Sim |
| `canUpdateConfiguration` | Habilita **Configurações** item do menu. | Não |
| `commands` | Matriz de comandos que esta extensão de mensagens suporta. Você está limitado a 10 comandos. | Sim |

#### <a name="define-commands"></a>Definir comandos

Sua extensão de mensagens deve declarar um comando, que aparece quando o usuário seleciona seu aplicativo a partir do botão **Mais opções** **(&#8943;)** na caixa de composição.

![Captura de tela da lista de extensões de mensagens em Teams](~/assets/images/compose-extensions/compose-extension-list.png)

No manifesto do aplicativo, o item de comando é um objeto com a seguinte estrutura:

| Nome da propriedade | Objetivo | Obrigatório? | Versão mínima do manifesto |
|---|---|---|---|
| `id` | ID único que você atribui a este comando. A solicitação do usuário incluirá este ID. | Sim | 1.0 |
| `title` | Nome do comando. Este valor aparece na interface do usuário. | Sim | 1.0 |
| `description` | Ajude o texto indicando o que este comando faz. Este valor aparece na interface do usuário. | Sim | 1.0 |
| `type` | Defina o tipo de comando. Os valores possíveis incluem `query` e `action`. Se não apresentar o valor padrão é definido para `query` . | Não | 1.4 |
| `initialRun` | Parâmetro opcional, usado com `query` comandos. Se definido **como verdadeiro,** indica que este comando deve ser executado assim que o usuário escolher este comando na interface do usuário. | Não | 1.0 |
| `fetchTask` | Parâmetro opcional, usado com `action` comandos. Definido como **true** para buscar o cartão adaptativo ou url web para exibir dentro do [módulo de tarefa](~/task-modules-and-cards/what-are-task-modules.md). Isso é usado quando as entradas para o `action` comando são dinâmicas em oposição a um conjunto estático de parâmetros. Observe que o se definido para **realizar** a lista de parâmetros estáticos para o comando é ignorado. | Não | 1.4 |
| `parameters` | Lista estática de parâmetros para o comando. | Sim | 1.0 |
| `parameter.name` | O nome do parâmetro. Isso é enviado para o seu serviço na solicitação do usuário. | Sim | 1.0 |
| `parameter.description` | Descreve os propósitos deste parâmetro ou exemplo do valor que deve ser fornecido. Este valor aparece na interface do usuário. | Sim | 1.0 |
| `parameter.title` | Título ou rótulo de parâmetro curto para usuário. | Sim | 1.0 |
| `parameter.inputType` | Definido para o tipo de entrada necessária. Os valores possíveis `text` `textarea` incluem, `number` , , `date` , `time` `toggle` . O padrão está definido para `text` . | Não | 1.4 |
| `context` | Matriz opcional de valores que define o contexto em que a ação da mensagem está disponível. Os valores possíveis `message` `compose` são, ou `commandBox` . O padrão é `["compose", "commandBox"]`. | Não | 1,5 |
