---
title: Otimizar seu bot com limitação de fluxo no Teams
description: Saiba mais sobre como lidar com o limite de taxa para bots com o limite de threads por bot e o limite para todos os bots usando exemplos de código. Além disso, aprenda as práticas recomendadas de limitação de taxa no Microsoft Teams.
ms.topic: conceptual
ms.localizationpriority: high
keywords: limitação da taxa de bots do Teams
ms.openlocfilehash: 09b3f0b79737e3da09b34ebe1931a7209632cca1
ms.sourcegitcommit: f15bd0e90eafb00e00cf11183b129038de8354af
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2022
ms.locfileid: "65111805"
---
# <a name="optimize-your-bot-with-rate-limiting-in-teams"></a>Otimizar seu bot com limitação de fluxo no Teams

A limitação de taxa é um método para limitar as mensagens a uma determinada frequência máxima. Como princípio geral, seu aplicativo deve limitar o número de mensagens postadas em um chat individual ou conversa de canal. Isso garante uma experiência ideal e as mensagens não aparecem como spam para seus usuários.

Para proteger o Microsoft Teams e seus usuários, as APIs do bot fornecem um limite de taxa para solicitações de entrada. Os aplicativos que superam esse limite recebem um status de erro `HTTP 429 Too Many Requests`. Todas as solicitações estão sujeitas à mesma política de limitação de taxa, incluindo envio de mensagens, enumerações de canal e buscas de lista de participantes.

Como os valores exatos dos limites de taxa estão sujeitos a alterações, seu aplicativo deve implementar o comportamento de retirada apropriado quando a API retornar `HTTP 429 Too Many Requests`.

## <a name="handle-rate-limits"></a>Lidar com limites de taxa

Ao emitir uma operação SDK do Bot Builder, você pode lidar com `Microsoft.Rest.HttpOperationException` e verificar o código de status.

O código a seguir mostra um exemplo de como lidar com limites de taxa:

```csharp
try
{
    // Perform Bot Framework operation
    // for example, await connector.Conversations.UpdateActivityAsync(reply);
}
catch (HttpOperationException ex)
{
    if (ex.Response != null && (uint)ex.Response.StatusCode ==  429)
    {
        //Perform retry of the above operation/Action method
    }
}
```

Depois de lidar com os limites de taxa para bots, você pode lidar com respostas `HTTP 429` usando uma retirada exponencial.

## <a name="handle-http-429-responses"></a>Lidar com as respostas `HTTP 429`

Em geral, você deve tomar precauções simples para evitar receber respostas `HTTP 429`. Por exemplo, evite emitir várias solicitações para a mesma conversa pessoal ou de canal. Em vez disso, crie um lote de solicitações de API.

Usar uma retirada exponencial com um jitter aleatório é a maneira recomendada de lidar com 429s. Isso garante que várias solicitações não introduzam colisões em repetições.

Depois de lidar com as respostas `HTTP 429`, você pode percorrer o exemplo para detectar exceções transitórias.

> [!NOTE]
> Além de tentar novamente o código de erro **429**, os códigos de erro **412**, **502** e **504** também devem ser repetidos.

## <a name="detect-transient-exceptions-example"></a>Exemplo de detecção de exceções transitórias

O código a seguir mostra um exemplo de uso de retirada exponencial usando o bloco de aplicativos de tratamento de falhas transitórias:

```csharp
public class BotSdkTransientExceptionDetectionStrategy : ITransientErrorDetectionStrategy
    {
        // List of error codes to retry on
        List<int> transientErrorStatusCodes = new List<int>() { 429 };

        public static bool IsTransient(Exception ex)
          {
              if (ex.Message.Contains("429"))
                  return true;

              HttpResponseMessageWrapper? response = null;
              if (ex is HttpOperationException httpOperationException)
              {
                  response = httpOperationException.Response;
              }
              else
              if (ex is ErrorResponseException errorResponseException)
              {
                  response = errorResponseException.Response;
              }
              return response != null && transientErrorStatusCodes.Contains((int)response.StatusCode);
          }
    }
```

Você pode executar retirada e novas tentativas usando o tratamento [de falhas transitórias](/previous-versions/msp-n-p/hh675232%28v%3dpandp.10%29). Para obter diretrizes sobre como obter e instalar o pacote NuGet, consulte [adicionar o bloco de aplicativos de tratamento de falhas transitórias à sua solução](/previous-versions/msp-n-p/dn440719(v=pandp.60)?redirectedfrom=MSDN). Consulte também [tratamento de falhas transitórias](/azure/architecture/best-practices/transient-faults).

Depois de percorrer o exemplo para detectar exceções transitórias, consulte o exemplo de retirada exponencial. Você pode usar retirada exponencial em vez de tentar novamente em caso de falhas.

## <a name="backoff-example"></a>Exemplo de retirada

Além de detectar limites de taxa, você também pode executar uma retirada exponencial.

O código a seguir mostra um exemplo de retirada exponencial:

```csharp
/**
* The first parameter specifies the number of retries before failing the operation.
* The second parameter specifies the minimum and maximum backoff time respectively.
* The last parameter is used to add a randomized  +/- 20% delta to avoid numerous clients retrying simultaneously.
*/
var exponentialBackoffRetryStrategy = new ExponentialBackoff(3, TimeSpan.FromSeconds(2),
                        TimeSpan.FromSeconds(20), TimeSpan.FromSeconds(1));


// Define the Retry Policy
var retryPolicy = new RetryPolicy(new BotSdkTransientExceptionDetectionStrategy(), exponentialBackoffRetryStrategy);

//Execute any bot sdk action
await retryPolicy.ExecuteAsync(() => connector.Conversations.ReplyToActivityAsync( (Activity)reply) ).ConfigureAwait(false);
```

Você também pode executar um método `System.Action` com a política de repetição descrita nesta seção. A biblioteca referenciada também permite que você especifique um intervalo fixo ou um mecanismo de retirada linear.

Armazene o valor e a estratégia em um arquivo de configuração para refinar e ajustar valores em tempo de execução.

Para obter mais informações, consulte [padrões de repetição](/azure/architecture/patterns/retry).

Você também pode lidar com o limite de taxa usando o limite de threads por bot.

## <a name="per-bot-per-thread-limit"></a>Limite de threads por bot

O limite de threads por bot controla o tráfego que um bot tem permissão para gerar em uma única conversa. Uma conversa é 1:1 entre o bot e o usuário, um chat em grupo ou um canal em uma equipe. Portanto, se o aplicativo enviar uma mensagem de bot para cada usuário, o limite de threads não será suprimido.

>[!NOTE]
>
> * O limite de threads de 3.600 segundos e 1800 operações se aplicará somente se várias mensagens de bot forem enviadas para um único usuário.
> * O limite global por aplicativo por locatário é de 50 RPS (Solicitações por Segundo). Portanto, o número total de mensagens de bot por segundo não deve ultrapassar o limite de threads.
> * A divisão de mensagens no nível de serviço resulta em RPS maior do que o esperado. Se você estiver preocupado com a aproximação dos limites, deverá implementar a [estratégia de retirada](#backoff-example). Os valores fornecidos nesta seção são apenas para estimativa.

A tabela a seguir fornece os limites de thread por bot:

| Cenário | Tempo em segundos | Máximo de operações permitidas |
| --- | --- | --- |
| Enviar para conversa | 1 | 7  |
| Enviar para conversa | 2 | 8  |
| Enviar para conversa | 30 | 60 |
| Enviar para conversa | 3600 | 1800 |
| Criar conversa | 1 | 7  |
| Criar conversa | 2 | 8  |
| Criar conversa | 30 | 60 |
| Criar conversa | 3600 | 1800 |
| Obter membros da conversa| 1 | 14  |
| Obter membros da conversa| 2 | 16 |
| Obter membros da conversa| 30 | 120 |
| Obter membros da conversa| 3600 | 3600 |
| Conversas de bot | 1 | 14  |
| Conversas de bot | 2 | 16 |
| Conversas de bot | 30 | 120 |
| Conversas de bot | 3600 | 3600 |

>[!NOTE]
> Versões anteriores de APIs `TeamsInfo.getMembers` e `TeamsInfo.GetMembersAsync` estão sendo preteridas. São limitados a cinco solicitações por minuto e retornam um máximo de 10 mil membros por equipe. Para atualizar o SDK do Bot Framework e o código para usar os pontos de extremidade de API paginados mais recentes, consulte [Alterações de API do Bot para membros de equipe e chat](../../resources/team-chat-member-api-changes.md).

Você também pode lidar com o limite de taxa usando o limite de threads para todos os bots.

## <a name="per-thread-limit-for-all-bots"></a>Limite de threads para todos os bots

O limite de threads para todos os bots controla o tráfego que todos os bots têm permissão para gerar em uma única conversa. Uma conversa aqui é 1:1 entre o bot e o usuário, um chat em grupo ou um canal em uma equipe.

A tabela a seguir fornece o limite de thread para todos os bots:

| Cenário | Tempo em segundos | Máximo de operações permitidas |
| --- | --- | --- |
| Enviar para conversa | 1 | 14  |
| Enviar para conversa | 2 | 16 |
| Criar conversa | 1 | 14  |
| Criar conversa | 2 | 16 |
| Criar conversa| 1 | 14  |
| Criar conversa| 2 | 16 |
| Obter membros da conversa| 1 | 28 |
| Obter membros da conversa| 2 | 32 |
| Conversas de bot | 1 | 28 |
| Conversas de bot | 2 | 32 |

## <a name="next-step"></a>Próxima etapa

> [!div class="nextstepaction"]
> [Bots de chamadas e reuniões](~/bots/calls-and-meetings/calls-meetings-bots-overview.md)
