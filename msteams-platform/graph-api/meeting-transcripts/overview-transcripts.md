---
title: Usar o Microsoft Graph para buscar transcrições para uma reunião do Teams
description: Descreve o processo, os cenários e as APIs para buscar transcrições no cenário pós-reunião.
ms.localizationpriority: high
ms.topic: concept
ms.openlocfilehash: 48d94bcfb41caf7bff171e4ae25146578c5d5fd8
ms.sourcegitcommit: 40d4bde10b6820c62e49e2400b10ab3569c8c815
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/20/2022
ms.locfileid: "68615299"
---
# <a name="get-meeting-transcripts-using-graph-apis"></a>Obter transcrições de reunião usando APIs do Graph

Agora você pode configurar seu aplicativo para buscar transcrições de reuniões do Microsoft Teams no cenário pós-reunião. Seu aplicativo pode usar APIs REST do Microsoft Graph para acessar e buscar transcrições geradas para uma reunião do Teams agendada com antecedência.

Aqui estão alguns casos de uso para buscar transcrições de reunião usando API do Graph:

| Caso de uso | Como as APIs de Transcrição ajudam... |
| --- | --- |
| Você precisa obter transcrições para capturar insights significativos de várias reuniões na vertical de Vendas. É demorado e ineficiente controlar todas as reuniões e recuperar anotações da reunião manualmente. Após o fim da reunião, você precisará examinar as conversas em todas essas reuniões para obter informações úteis. | O uso de APIs do Graph em seu aplicativo para buscar transcrições de reunião recupera automaticamente as transcrições de todas as reuniões relevantes para sua finalidade. Seu aplicativo pode receber notificações de reunião e obter a transcrição quando ela é gerada após o término da reunião. Esses dados podem ser usados para obter: <br> • Análise agregada de insights e inteligência <br> • Novos clientes potenciais e destaques <br> • Acompanhamentos e resumos da reunião |
| Como uma iniciativa de RH, você está realizando uma sessão de debate para entender e melhorar a saúde e a produtividade dos funcionários. Ter que fazer anotações continuamente para fornecer um resumo pós-reunião pode impedir o fluxo de pensamentos e você pode não capturar todas as sugestões valiosas. Após a sessão, você precisará analisar a discussão para coletar pontos de dados para planejar melhorias. | O uso de APIs do Graph em seu aplicativo para buscar transcrições pós-reunião permite que você e os participantes se concentrem totalmente na discussão. O conteúdo da transcrição da reunião está disponível para: <br> • Análise de envolvimento e sentimento <br> • Listar tarefas ou problemas <br> • Acompanhamento de reuniões e notificações |

> [!NOTE]
> No futuro, a Microsoft poderá exigir que você ou seus clientes paguem taxas adicionais com base na quantidade de dados acessados pela API.

Para buscar a transcrição de uma reunião específica:

- [Configurar permissões no Azure AD para acessar a transcrição](#configure-permissions-on-azure-ad-to-access-transcript)
- [Obter a ID da reunião e a ID do organizador](fetch-id.md)
- [Usar APIs do Graph para buscar a transcrição](/graph/api/resources/calltranscript)

## <a name="configure-permissions-on-azure-ad-to-access-transcript"></a>Configurar permissões no Azure AD para acessar a transcrição

Seu aplicativo deve ter as permissões necessárias para buscar transcrições. Ele pode acessar e buscar transcrições para uma reunião do Teams usando permissões de aplicativo em toda a organização ou permissões de aplicativo RSC (consentimento específico do recurso) para uma reunião específica.

### <a name="use-organization-wide-application-permissions"></a>Usar permissões de aplicativo em toda a organização

Você pode configurar seu aplicativo para acessar transcrições de reunião em todo o locatário. Nesse caso, o organizador da reunião não precisa instalar seu aplicativo no chat de reunião do Teams. Quando o administrador de locatários autoriza as permissões de aplicativo em toda a organização, seu aplicativo pode ler e acessar transcrições para todas as reuniões no locatário.

Para obter mais informações sobre as permissões de aplicativo em toda a organização que podem ser concedidas ao seu aplicativo, consulte [Permissões de reunião online](/graph/permissions-reference#online-meetings-permissions).

### <a name="use-meeting-specific-rsc-application-permissions"></a>Usar permissões de aplicativo RSC específicas de reunião

Se você quiser que seu aplicativo busque transcrições somente para a reunião do Teams em que ele está instalado, configure a permissão RSC específica da reunião para seu aplicativo. Os usuários autorizados podem instalar seu aplicativo no chat da reunião. Após o término da reunião, seu aplicativo pode fazer a chamada à API para obter a transcrição dessa reunião.

Para obter mais informações sobre as permissões RSC específicas de reunião que podem ser concedidas ao seu aplicativo, consulte o [Consentimento específico do recurso](../rsc/resource-specific-consent.md#resource-specific-permissions-for-a-chat).

Depois de configurar as permissões, configure seu aplicativo para receber notificações de alteração para todos os eventos de reunião relevantes. As notificações contêm a ID da reunião e a ID do organizador que ajudam a acessar o conteúdo da transcrição. Seu aplicativo pode buscar a transcrição de uma reunião quando ela é gerada após o término. O conteúdo da transcrição está disponível como `.vtt` ou arquivo `.docx`.

Para obter mais informações sobre como seu aplicativo pode saber quando as reuniões terminam, consulte [Assinar para alterar notificações](fetch-id.md#subscribe-to-change-notifications) e [Usar o Bot Framework para obter a ID da reunião e a ID do organizador](fetch-id.md#use-bot-framework-to-get-meeting-id-and-organizer-id).

> [!NOTE]
> O processo para chamar APIs do Graph para acessar e recuperar transcrições permanece o mesmo para permissões de aplicativo RSC específicas de reunião ou permissões de aplicativo em toda a organização. Atualmente, essas APIs dão suporte apenas a reuniões agendadas.

## <a name="next-step"></a>Próxima etapa

> [!div class="nextstepaction"]
> [Obter a ID da reunião e a ID do organizador](fetch-id.md)

## <a name="see-also"></a>Confira também

- [APIs de reunião avançadas](../../apps-in-teams-meetings/meeting-apps-apis.md)
