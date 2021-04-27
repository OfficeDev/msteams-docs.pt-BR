---
title: Otimizar seu bot com limitação de fluxo no Teams
description: Limitação de taxas e práticas recomendadas no Microsoft Teams
ms.topic: conceptual
localization_priority: Normal
keywords: limitação da taxa de bots do teams
ms.openlocfilehash: 23d75e7df021a5c746c4dd23d848ac085294c160
ms.sourcegitcommit: 825abed2f8784d2bab7407ba7a4455ae17bbd28f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2021
ms.locfileid: "52020895"
---
# <a name="optimize-your-bot-with-rate-limiting-in-teams"></a>Otimizar seu bot com limitação de fluxo no Teams

Limitação de taxa é um método para limitar as mensagens a uma determinada frequência máxima. Como um princípio geral, seu aplicativo deve limitar o número de mensagens que ele posta em um chat individual ou conversa de canal. Isso garante uma experiência ideal e as mensagens não aparecem como spam para seus usuários.

Para proteger o Microsoft Teams e seus usuários, as APIs de bot fornecem um limite de taxa para solicitações de entrada. Os aplicativos que passar por esse limite recebem um `HTTP 429 Too Many Requests` status de erro. Todas as solicitações estão sujeitas à mesma política de limitação de taxa, incluindo o envio de mensagens, enumerações de canal e buscas de lista.

Como os valores exatos dos limites de taxa estão sujeitos a alterações, seu aplicativo deve implementar o comportamento de backoff apropriado quando a API retornar `HTTP 429 Too Many Requests` .

## <a name="handle-rate-limits"></a>Manipular limites de taxa

Ao emissão de uma operação SDK do Construtor de Bots, você pode manipular e `Microsoft.Rest.HttpOperationException` verificar o código de status.

O código a seguir mostra um exemplo de limites de taxa de manipulação:

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

Depois de manipular os limites de taxa para bots, você pode lidar com respostas usando um `HTTP 429` backoff exponencial.

## <a name="handle-http-429-responses"></a>Manipular `HTTP 429` respostas

Em geral, você deve tomar precauções simples para evitar receber `HTTP 429` respostas. Por exemplo, evite a emissão de várias solicitações para a mesma conversa pessoal ou de canal. Em vez disso, crie um lote de solicitações de API.

Usar um backoff exponencial com um tremeamento aleatório é a maneira recomendada de lidar com 429s. Isso garante que várias solicitações não introduzam colisões em recuperações.

Depois de lidar `HTTP 429` com as respostas, você pode passar pelo exemplo para detectar exceções transitórias.

> [!NOTE]
> Além de retyring error code **429**, os códigos de erro **412**, **502** e **504** também devem ser retridados.

## <a name="detect-transient-exceptions-example"></a>Exemplo de exceções transitórias

O código a seguir mostra um exemplo de uso de backoff exponencial usando o bloco de aplicativos de tratamento transitório de falhas:

```csharp
public class BotSdkTransientExceptionDetectionStrategy : ITransientErrorDetectionStrategy
    {
        // List of error codes to retry on
        List<int> transientErrorStatusCodes = new List<int>() { 429 };

        public bool IsTransient(Exception ex)
        {
            if (ex.Message.Contains("429"))
                return true;

            var httpOperationException = ex as HttpOperationException;
            if (httpOperationException != null)
            {
                return httpOperationException.Response != null &&
                        transientErrorStatusCodes.Contains((int)httpOperationException.Response.StatusCode);
            }

            return false;
        }
    }
```

Você pode executar o backoff e as recuperações usando o tratamento [transitório de falhas](/previous-versions/msp-n-p/hh675232%28v%3dpandp.10%29). Para obter e instalar o pacote NuGet, consulte [adding the transient fault handling application block to your solution](/previous-versions/msp-n-p/dn440719(v=pandp.60)?redirectedfrom=MSDN). Consulte também o [tratamento transitório de falhas](/azure/architecture/best-practices/transient-faults).

Depois de passar pelo exemplo para detectar exceções transitórias, vá pelo exemplo de backoff exponencial. Você pode usar o backoff exponencial em vez de repetir falhas.

## <a name="backoff-example"></a>Exemplo de backoff

Além de detectar limites de taxa, você também pode executar um backoff exponencial.

O código a seguir mostra um exemplo de backoff exponencial:

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

Você também pode executar uma execução `System.Action` de método com a política de nova tentativa descrita nesta seção. A biblioteca referenciada também permite especificar um intervalo fixo ou um mecanismo de backoff linear.

Armazene o valor e a estratégia em um arquivo de configuração para ajustar e ajustar valores em tempo de execução.

Para obter mais informações, consulte [padrões de repetir](/azure/architecture/patterns/retry).

Você também pode manipular o limite de taxa usando o bot por limite de thread.

## <a name="per-bot-per-thread-limit"></a>Por bot por limite de thread

O limite por bot por thread controla o tráfego que um bot tem permissão para gerar em uma única conversa. Uma conversa é 1:1 entre bot e usuário, um chat em grupo ou um canal em uma equipe. Portanto, se o aplicativo enviar uma mensagem bot para cada usuário, o limite de thread não será limitado.

>[!NOTE]
> * O limite de thread de 3600 segundos e 1800 operações só se aplica se várias mensagens de bot são enviadas a um único usuário. 
> * O limite global por aplicativo por locatário é de 30 solicitações por segundo (RPS). Portanto, o número total de mensagens bot por segundo não deve cruzar o limite de thread.
> * A divisão de mensagens no nível de serviço resulta em RPS maior do que o esperado. Se estiver preocupado com a abordagem dos limites, implemente a [estratégia de backoff](#backoff-example). Os valores fornecidos nesta seção são apenas para estimativa.

A tabela a seguir fornece os limites por bot por thread:

| Cenário | Período de tempo em segundos | Operações máximas permitidas |
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
| Obter membros da conversa| 2 | 16  |
| Obter membros da conversa| 30 | 120 |
| Obter membros da conversa| 3600 | 3600 |
| Obter conversas | 1 | 14  |
| Obter conversas | 2 | 16  |
| Obter conversas | 30 | 120 |
| Obter conversas | 3600 | 3600 |

>[!NOTE]
> Versões anteriores `TeamsInfo.getMembers` e `TeamsInfo.GetMembersAsync` APIs estão sendo preterida. Eles são sujeitos a cinco solicitações por minuto e retornam no máximo 10 mil membros por equipe. Para atualizar o SDK da Estrutura de Bots e o código para usar os pontos de extremidade mais recentes da API paginada, consulte Alterações na API bot para membros de equipe [e chat.](../../resources/team-chat-member-api-changes.md)

Você também pode manipular o limite de taxa usando o limite por thread para todos os bots.

## <a name="per-thread-limit-for-all-bots"></a>Por limite de thread para todos os bots

O limite por thread para todos os bots controla o tráfego que todos os bots têm permissão para gerar em uma única conversa. Uma conversa aqui é 1:1 entre bot e usuário, um chat em grupo ou um canal em uma equipe.

A tabela a seguir fornece o limite por thread para todos os bots:

| Cenário | Período de tempo em segundos | Operações máximas permitidas |
| --- | --- | --- |
| Enviar para conversa | 1 | 14  |
| Enviar para conversa | 2 | 16  |
| Criar conversa | 1 | 14  |
| Criar conversa | 2 | 16  |
| Criar conversa| 1 | 14  |
| Criar conversa| 2 | 16  |
| Obter membros da conversa| 1 | 28 |
| Obter membros da conversa| 2 | 32 |
| Obter conversas | 1 | 28 |
| Obter conversas | 2 | 32 |

## <a name="next-step"></a>Próxima etapa

> [!div class="nextstepaction"]
> [Bots de chamadas e reuniões](~/bots/calls-and-meetings/calls-meetings-bots-overview.md)

