---
title: Obter ID de reunião e ID de organizador para buscar transcrições de reunião
description: Descreve o processo para obtenção de ID de reunião e ID de organizador para buscar transcrições de reunião
ms.localizationpriority: high
ms.topic: concept
ms.openlocfilehash: 316eabb77eb440a171ca6f357e1db8a2f3b18b6b
ms.sourcegitcommit: d5628e0d50c3f471abd91c3a3c2f99783b087502
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/25/2022
ms.locfileid: "67434982"
---
# <a name="obtain-meeting-id-and-organizer-id"></a>Obter ID de reunião e ID de organizador

Seu aplicativo pode buscar transcrições de uma reunião usando a ID de reunião e a ID de usuário do organizador da reunião, também conhecida como ID de organizador. As APIs REST do Graph buscam transcrições com base na ID de reunião e na ID de organizador que são passadas como parâmetros na API.

> [!NOTE]
> A ID de reunião para reuniões agendadas poderá expirar em alguns dias se ela não for usada. Ela pode ser revivida usando a URL da reunião para ingressar na reunião. Para obter mais informações sobre a linha do tempo de expiração da reunião para diferentes tipos de reunião, confira [Expiração da reunião](/microsoftteams/limits-specifications-teams#meeting-expiration).

Para obter a ID de reunião e a ID de organizador para buscar a transcrição, escolha uma das duas maneiras:

- [Inscreva-se para alterar as notificações](#subscribe-to-change-notifications)
- [Usar Bot Framework](#use-bot-framework-to-get-meeting-id-and-organizer-id)

### <a name="subscribe-to-change-notifications"></a>Inscreva-se para alterar as notificações

Você pode inscrever seu aplicativo para receber notificações de alteração para eventos de reunião agendados. Quando seu aplicativo é notificado sobre os eventos de reunião inscritos, ele pode obter transcrições, se estiver autorizado por meio das permissões necessárias do Azure AD.

Seu aplicativo recebe uma notificação sobre o tipo de eventos de reunião para os quais ele está inscrito:

- [Notificação no nível do usuário](#obtain-meeting-details-using-user-level-notification)
- [Notificação no nível do locatário](#obtain-meeting-details-using-tenant-level-notification)

Quando seu aplicativo é notificado de um evento de reunião inscrito, ele pode recuperar a ID de reunião e a ID de organizador da mensagem de notificação. Com base nos detalhes da reunião obtidos, seu aplicativo pode buscar as transcrições da reunião após o fim da reunião.

#### <a name="obtain-meeting-details-using-user-level-notification"></a>Obter detalhes da reunião usando a notificação no nível do usuário

Escolha inscrever seu aplicativo em notificações no nível do usuário para obter transcrições do evento de reunião de um usuário específico. Seu aplicativo é notificado quando uma reunião for agendada para esse usuário. Seu aplicativo também pode receber notificações de reunião usando eventos de calendário.

Para inscrever seu aplicativo em eventos de calendário, confira [Notificações de alteração para recursos do Outlook no Microsoft Graph](/graph/outlook-change-notifications-overview).

Use o exemplo a seguir para se inscrever para notificações no nível do usuário:

```http
    
POST https://graph.microsoft.com/v1.0/subscriptions/
{
    "changeType": "created,updated,deleted",
    "notificationUrl": "https://webhook.azurewebsites.net/api/send/myNotifyClient",
    "resource": "users('1273a016-201d-4f95-8083-1b7f99b3edeb')/events",
    "expirationDateTime": "2022-05-05T14:58:56.7951795+00:00",
    "clientState": "ClientSecret",
    "includeResourceData": false
}
```

Quando seu aplicativo é notificado sobre um evento de reunião inscrito, ele procura a ID de evento do calendário na notificação. Use a ID de evento para obter `JoinWebUrl` para recuperar uma ID de chat específica e se inscrever para suas mensagens. Depois que seu aplicativo tiver inscrito para as mensagens de chat, siga as etapas fornecidas para [notificações no nível do locatário](#obtain-meeting-details-using-tenant-level-notification) para obter a ID de reunião e a ID de organizador.

Para obter a ID de reunião e a ID de organizador da notificação no nível do usuário:

1. **Obter ID de evento**: seu aplicativo obtém a propriedade `eventId` da carga de notificação.

    <details>
    <summary><b>Exemplo</b>: conteúdo da notificação</summary>

    ```json
    {
        "subscriptionId": "ef30cdc6-b5ae-4702-b924-f458fd9e5fc3",
        "changeType": "created",
        "tenantId": "2432b57b-0abd-43db-aa7b-16eadd115d34",
        "clientState": "ClientSecret",
        "subscriptionExpirationDateTime": "2022-05-05T07:54:53.1886542-07:00",
        "resource": "Users/1273a016-201d-4f95-8083-1b7f99b3edeb/Events/AAMkADY0NjM1MjRhLTNiNjAtNDBiOC1hYTQxLThkMjAxN2QzMjZhYQBGAAAAAAC03Gz8aL_JQp2Kxvw5a29SBwDFFWHjtoMRTqdrVyQ1h8yLAAAAAAENAADFFWHjtoMRTqdrVyQ1h8yLAAFwC7nAAAA=",
        "resourceData": {}
    }
    ```

    Neste exemplo, o `eventID` contido em `resource` é *AAMkADY0NjM1MjRhLTNiNjAtNDBiOC1hYTQxLThkMjAxN2QzMjZhYQBGAAAAAAC03Gz8aL_JQp2Kxvw5a29SBwDFFWHjtoMRTqdrVyQ1h8yLAAAAAAENAADFFWHjtoMRTqdrVyQ1h8yLAAFwC7nAAAA=*.
    </details>

2. **Obter URL da reunião**: use a ID de evento para recuperar `joinUrl` que contém a URL da reunião.

    Para mais informações, confira [Obter evento](/graph/api/event-get).

    Use o exemplo a seguir para solicitar a URL da reunião:

    ```http
    GET https://graph.microsoft.com/v1.0/users/1273a016-201d-4f95-8083-1b7f99b3edeb/events/AAMkADY0NjM1MjRhLTNiNjAtNDBiOC1hYTQxLThkMjAxN2QzMjZhYQBGAAAAAAC03Gz8aL_JQp2Kxvw5a29SBwDFFWHjtoMRTqdrVyQ1h8yLAAAAAAENAADFFWHjtoMRTqdrVyQ1h8yLAAFwC7nAAAA=
    ```

    O conteúdo de resposta contém `joinURL`.

    <details>
    <summary><b>Exemplo</b>: conteúdo de resposta para obter a URL da reunião</summary>

    ```json
    {
        "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#users('1273a016-201d-4f95-8083-1b7f99b3edeb')/events/$entity",
        "@odata.etag": "W/\"xRVh47aDEU6na1ckNYfMiwABb2Twsg==\"",
        "id": "AAMkADY0NjM1MjRhLTNiNjAtNDBiOC1hYTQxLThkMjAxN2QzMjZhYQBGAAAAAAC03Gz8aL_JQp2Kxvw5a29SBwDFFWHjtoMRTqdrVyQ1h8yLAAAAAAENAADFFWHjtoMRTqdrVyQ1h8yLAAFwC7nAAAA=",    
        "start": {
            "dateTime": "2022-05-06T15:00:00.0000000",
            "timeZone": "UTC"
        },
        "end": {
            "dateTime": "2022-05-06T15:30:00.0000000",
            "timeZone": "UTC"
        },
            
        "onlineMeeting": {
            "joinUrl": "https://teams.microsoft.com/l/meetup-join/19%3ameeting_MjExYzJiMTItZDY1MS00ZGZkLWE5YzQtZTBmNWI1MDg2M2Uw%40thread.v2/0?context=%7b%22Tid%22%3a%222432b57b-0abd-43db-aa7b-16eadd115d34%22%2c%22Oid%22%3a%221273a016-201d-4f95-8083-1b7f99b3edeb%22%7d",
            "conferenceId": "438824583",
            "tollNumber": "+1 213-279-1007"
        }    
    }
    ```

    </details>

    A URL da reunião está contida em `joinUrl`.

3. **Obter ID da conversa de chat**: use a URL da reunião obtida em `joinUrl` para obter a ID da conversa de chat. Especifique essa URL de reunião como valor para o parâmetro `joinWebUrl` ao buscar a reunião relacionada.

    Use o exemplo a seguir para solicitar a ID da conversa de chat:

    ``` http
    GET https://graph.microsoft.com/v1.0/users('14b779ae-cb64-47e7-a512-52fd50a4154d')/onlineMeetings?$filter=JoinWebUrl%20eq%20'https://teams.microsoft.com/l/meetup-join/19%3ameeting_MTM5OTY3MGUtNmY4Mi00Yjg4LTk2MDUtY2IyZGRlNmU1ZjA2%40thread.v2/0?context=%7b%22Tid%22%3a%222432b57b-0abd-43db-aa7b-16eadd115d34%22%2c%22Oid%22%3a%2214b779ae-cb64-47e7-a512-52fd50a4154d%22%7d'
    ```

    O conteúdo de resposta contém o membro `threadID` na propriedade `chatInfo`.
    <br>
    <details>
    <summary><b>Exemplo</b>: conteúdo da resposta com ID de conversa</summary>

    ```json
    {
        "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#users('14b779ae-cb64-47e7-a512-52fd50a4154d')/onlineMeetings",
        "value": [
            {
                "id": "MSoxNGI3NzlhZS1jYjY0LTQ3ZTctYTUxMi01MmZkNTBhNDE1NGQqMCoqMTk6bWVldGluZ19NVE01T1RZM01HVXRObVk0TWkwMFlqZzRMVGsyTURVdFkySXlaR1JsTm1VMVpqQTJAdGhyZWFkLnYy",
                "creationDateTime": "2022-04-26T07:41:17.3736455Z",
                "startDateTime": "2022-04-26T10:30:00Z",
                "endDateTime": "2022-04-26T11:00:00Z",
                "joinUrl": "https://teams.microsoft.com/l/meetup-join/19%3ameeting_MTM5OTY3MGUtNmY4Mi00Yjg4LTk2MDUtY2IyZGRlNmU1ZjA2%40thread.v2/0?context=%7b%22Tid%22%3a%222432b57b-0abd-43db-aa7b-16eadd115d34%22%2c%22Oid%22%3a%2214b779ae-cb64-47e7-a512-52fd50a4154d%22%7d",
                "joinWebUrl": "https://teams.microsoft.com/l/meetup-join/19%3ameeting_MTM5OTY3MGUtNmY4Mi00Yjg4LTk2MDUtY2IyZGRlNmU1ZjA2%40thread.v2/0?context=%7b%22Tid%22%3a%222432b57b-0abd-43db-aa7b-16eadd115d34%22%2c%22Oid%22%3a%2214b779ae-cb64-47e7-a512-52fd50a4154d%22%7d",
                "chatInfo": {
                    "threadId": "19:meeting_MTM5OTY3MGUtNmY4Mi00Yjg4LTk2MDUtY2IyZGRlNmU1ZjA2@thread.v2",
                    "messageId": "0",
                    "replyChainMessageId": null
                }
            }
        ]
    }
    ```

    </details>

    A ID de chat está contida em `threadId`.

4. **Inscrever-se para mensagens de chat**: use a ID de chat para inscrever seu aplicativo e receber mensagens de chat para essa reunião específica. Para obter mais informações, confira [Inscrever-se para mensagens em um chat](/graph/teams-changenotifications-chatmessage#subscribe-to-messages-in-a-chat).

    Se você quiser que seu aplicativo se inscreva para mensagens com texto específico, confira [Inscrever-se para mensagens em um chat que contenha determinado texto](/graph/teams-changenotifications-chatmessage#example-2-subscribe-to-messages-in-a-chat-that-contain-certain-text).

5. Siga as etapas para [notificações no nível do locatário](#obtain-meeting-details-using-tenant-level-notification) para obter a ID de reunião e a ID de organizador.

#### <a name="obtain-meeting-details-using-tenant-level-notification"></a>Obter detalhes da reunião usando a notificação no nível do locatário

As notificações no nível do locatário serão úteis se o aplicativo estiver autorizado a acessar todas as transcrições de reunião no locatário. Inscreva seu aplicativo para ser notificado sobre eventos quando a transcrição for iniciada ou a chamada terminar para reuniões agendadas online do Teams. Depois que a reunião terminar, seu aplicativo poderá acessar e recuperar a transcrição da reunião.

Para inscrever seu aplicativo para notificações no nível do locatário, confira [Obter notificações de alteração](/graph/teams-changenotifications-chatmessage#subscribe-to-messages-across-all-chats).

Quando seu aplicativo é notificado sobre eventos de reunião inscritos, ele pesquisa as notificações de transcrição iniciada e eventos encerrados da reunião. Esses eventos contêm a ID de chat, que é usada para obter a entidade de chat e, eventualmente, a ID de reunião e a ID de organizador.

Para obter a ID de reunião e a ID de organizador da notificação no nível do locatário:

1. **Obter ID de chat**: seu aplicativo obtém a propriedade `chatId` da notificação para fazer chamadas subsequentes. Seu aplicativo pode obter a ID de chat dos conteúdos de:

    - Evento de transcrição iniciada: tipo de evento `callTranscriptEventMessageDetail`

        <details>
        <summary><b>Exemplo</b>: conteúdo do evento de transcrição iniciado</summary>

        ```json
        {
        "subscriptionId": "1217470f-564c-4fe3-b51f-ebd962cb8797",
        "changeType": "created",
        "tenantId": "2432b57b-0abd-43db-aa7b-16eadd115d34",
        "resource": "chats('19:meeting_ZjVkMjc0ZWYtNThkMy00ZGI1LWFiYjAtYjg3ZGU0ZWI3MzZk@thread.v2')/messages('1649787549174')",
        "contentDecryptedBySimulator": {
            "@odata.context": "https://graph.microsoft.com/$metadata#chats('19%3Ameeting_ZjVkMjc0ZWYtNThkMy00ZGI1LWFiYjAtYjg3ZGU0ZWI3MzZk%40thread.v2')/messages/$entity",
            "messageType": "systemEventMessage",
            "createdDateTime": "2022-04-12T18:19:09.174Z",
            "lastModifiedDateTime": "2022-04-12T18:19:09.174Z",
            "chatId": "19:meeting_ZjVkMjc0ZWYtNThkMy00ZGI1LWFiYjAtYjg3ZGU0ZWI3MzZk@thread.v2",
            "body": {
                "contentType": "html",
                "content": "<systemEventMessage/>"
            },
            "channelIdentity": null,
            "eventDetail": {
                "@odata.type": "#Microsoft.Teams.GraphSvc.callTranscriptEventMessageDetail",
                "callId": "16481de8-3262-419b-abc7-0139e6239515",
                "callTranscriptICalUid": "",
                "meetingOrganizer": {
                    "application": null,
                    "device": null,
                    "user": {
                    "userIdentityType": "aadUser",
                        "id": "14b779ae-cb64-47e7-a512-52fd50a4154d",
                        "displayName": null
                        }
                    }
                }
            },
            "encryptedContent": {}
        }
        ```

        </details>

    - Evento de chamada encerrada: tipo de evento `callEndedEventMessageDetail`

        <details>
        <summary><b>Exemplo</b>: conteúdo do evento de chamada encerrada</summary>

        ```json
        {
            "subscriptionId": "1217470f-564c-4fe3-b51f-ebd962cb8797",
            "changeType": "created",
            "tenantId": "2432b57b-0abd-43db-aa7b-16eadd115d34",
            "resource": "chats('19:meeting_ZjVkMjc0ZWYtNThkMy00ZGI1LWFiYjAtYjg3ZGU0ZWI3MzZk@thread.v2')/messages('1649787585457')",
            "resourceData": {},
            "contentDecryptedBySimulator": {
                "@odata.context": "https://graph.microsoft.com/$metadata#chats('19%3Ameeting_ZjVkMjc0ZWYtNThkMy00ZGI1LWFiYjAtYjg3ZGU0ZWI3MzZk%40thread.v2')/messages/$entity",
                "createdDateTime": "2022-04-12T18:19:45.457Z",
                "lastModifiedDateTime": "2022-04-12T18:19:45.457Z",     
                "chatId": "19:meeting_ZjVkMjc0ZWYtNThkMy00ZGI1LWFiYjAtYjg3ZGU0ZWI3MzZk@thread.v2",
                "eventDetail": {
                    "@odata.type": "#Microsoft.Teams.GraphSvc.callEndedEventMessageDetail",
                    "callId": null,
                    "callDuration": "PT1M44S",
                    "callEventType": "meeting",
                    "callParticipants": [
                    ],
                    "initiator": {
        
                    }
                }
            },
            "encryptedContent": {
                    
            }
        }
        ```

        </details>

2. **Obter entidade de chat**: seu aplicativo pode recuperar a entidade de chat usando a ID de chat obtida na etapa 1. Use a entidade de chat para obter a URL para ingressar na chamada. O membro `joinWebUrl` da propriedade `onlineMeetingInfo` contém essa URL e é usada para obter a ID de reunião eventualmente. A ID de organizador também faz parte do conteúdo de resposta.

    Para obter mais informações sobre a entidade de chat, confira [Obter chat](/graph/api/chat-get).

    Use o exemplo a seguir para solicitar a entidade de chat com base na ID de chat:

    ``` http
    GET https://graph.microsoft.com/v1.0/chats/19:meeting_NmU0NTkxYzMtM2Y2My00NzRlLWFmN2YtNTFiMGM5OWM3ZjY2@thread.v2
    ```

    O conteúdo da resposta contém os seguintes elementos:

    - **ID de organizador**: ela está contida no membro `id` da propriedade `organizer` na conteúdo da resposta.
    - **URL para chamada de reunião**: essa URL é usada para recuperar a ID de reunião e está disponível no conteúdo da resposta em um dos dois cenários:
        - Se a reunião for uma reunião online do Teams, o membro `joinWebUrl` da propriedade `onlineMeetingInfo` conterá essa URL.
        - Se a reunião não tiver sido criada como uma reunião online do cliente do Teams ou do cliente do Outlook, ela conterá o membro `calendarEventId` na propriedade `onlineMeetingInfo`. Seu aplicativo pode usar o `calendarEventId` para obter `joinUrl`, que é o mesmo que `joinWebUrl`.

      Para obter mais informações sobre eventos, confira [Obter evento](/graph/api/event-get?view=graph-rest-1.0&tabs=http&preserve-view=true).

      Exemplos de cenários de conteúdo da resposta dependendo do tipo de URL de reunião de ingresso:

        - Reunião online do Teams onde `joinWebUrl` está disponível

            <details>
            <summary><b>Exemplo</b>: conteúdo da resposta para reunião online</b></summary>

            ```json
            {
                "@odata.context": "https://graph.microsoft.com/beta/$metadata#chats/$entity",
                "id": "19:meeting_NmU0NTkxYzMtM2Y2My00NzRlLWFmN2YtNTFiMGM5OWM3ZjY2@thread.v2",
                "topic": "Test Meet Create Online Meeting",
                "createdDateTime": "2022-04-14T11:30:45.903Z",
                "lastUpdatedDateTime": "2022-04-26T06:27:45.265Z",
                "chatType": "meeting",
                "webUrl": "https://teams.microsoft.com/l/chat/19%3Ameeting_NmU0NTkxYzMtM2Y2My00NzRlLWFmN2YtNTFiMGM5OWM3ZjY2%40thread.v2/0?tenantId=2432b57b-0abd-43db-aa7b-16eadd115d34",
                "tenantId": "2432b57b-0abd-43db-aa7b-16eadd115d34",
                "viewpoint": null,
                "onlineMeetingInfo": {
                "calendarEventId": null,
                    "joinWebUrl": "https://teams.microsoft.com/l/meetup-join/19%3ameeting_NmU0NTkxYzMtM2Y2My00NzRlLWFmN2YtNTFiMGM5OWM3ZjY2%40thread.v2/0?context=%7b%22Tid%22%3a%222432b57b-0abd-43db-aa7b-16eadd115d34%22%2c%22Oid%22%3a%2214b779ae-cb64-47e7-a512-52fd50a4154d%22%7d",
                    "organizer": {
                        "id": "14b779ae-cb64-47e7-a512-52fd50a4154d",
                        "displayName": null,
                        "userIdentityType": "aadUser"
                    }
                }
            }
            ```

            </details>

        - Reunião agendada por meio do cliente do Teams ou cliente do Outlook, não marcada como uma reunião online onde `calendarEventId` está disponível

            <details>
            <summary><b>Exemplo</b>: conteúdo da resposta para reunião não marcada como online</summary>

            ```json
            {
                "@odata.context": "https://graph.microsoft.com/beta/$metadata#chats/$entity",
                "id": "19:meeting_YzM1NGFiZWYtOGFiOS00NjM5LTg4OTktYmU0MjI4NTQyNGZm@thread.v2",
                "topic": "Non Online Meeting Teams Client",
                "createdDateTime": "2022-04-26T09:43:23.711Z",
                "lastUpdatedDateTime": "2022-04-26T09:43:46.157Z",
                "chatType": "meeting",
                "webUrl": "https://teams.microsoft.com/l/chat/19%3Ameeting_YzM1NGFiZWYtOGFiOS00NjM5LTg4OTktYmU0MjI4NTQyNGZm%40thread.v2/0?tenantId=2432b57b-0abd-43db-aa7b-16eadd115d34",
                "tenantId": "2432b57b-0abd-43db-aa7b-16eadd115d34",
                "viewpoint": null,
                "onlineMeetingInfo": {
                    "calendarEventId": "AAMkAGE3NjJhOTVhLTNkZDQtNDE2OS05ZjU0LTJmOGQ0YTY2YTdiZQBGAAAAAAD3AG5jNnlgQJvdCL_KgXJIBwBsww5BlIxtT7iFyYWrXV3AAAAAAAENAABsww5BlIxtT7iFyYWrXV3AAACSDwYeAAA=",
                    "joinWebUrl": null,
                    "organizer": {
                        "id": "14b779ae-cb64-47e7-a512-52fd50a4154d",
                        "displayName": null,
                        "userIdentityType": "aadUser"
                    }
                }
            }
            ```

            </details>

            - Use o exemplo a seguir para obter `joinWebUrl` a partir de `calendarEventId`:

              ``` http
                GET https://graph.microsoft.com/beta/users/14b779ae-cb64-47e7-a512-52fd50a4154d/events/AAMkAGE3NjJhOTVhLTNkZDQtNDE2OS05ZjU0LTJmOGQ0YTY2YTdiZQBGAAAAAAD3AG5jNnlgQJvdCL_KgXJIBwBsww5BlIxtT7iFyYWrXV3AAAAAAAENAABsww5BlIxtT7iFyYWrXV3AAACSDwYdAAA=
              ```

              Neste exemplo:

                - A ID de organizador é *14b779ae-cb64-47e7-a512-52fd50a4154d*.

              O conteúdo da resposta dessa solicitação contém `joinUrl` na propriedade `onlineMeeting`.

                > [!NOTE]
                > Por exemplo, `joinUrl` é o mesmo que `joinWebUrl`.

              <br>
              <details>
              <summary><b>Exemplo</b>: conteúdo da resposta que contém a URL para ingressar na reunião</summary>

              ```json
              {
                "@odata.context": "https://graph.microsoft.com/beta/$metadata#users('14b779ae-cb64-47e7-a512-52fd50a4154d')/events/$entity",
                "@odata.etag": "W/\"bMMOQZSMbU+4hcmFq11dwAAAkc3Tmw==\"",
                "id": "AAMkAGE3NjJhOTVhLTNkZDQtNDE2OS05ZjU0LTJmOGQ0YTY2YTdiZQBGAAAAAAD3AG5jNnlgQJvdCL_KgXJIBwBsww5BlIxtT7iFyYWrXV3AAAAAAAENAABsww5BlIxtT7iFyYWrXV3AAACSDwYdAAA=",    
                "start": {
                    "dateTime": "2022-04-26T10:30:00.0000000",
                    "timeZone": "UTC"
                },
                "end": {
                    "dateTime": "2022-04-26T11:00:00.0000000",
                    "timeZone": "UTC"
                },    
                "onlineMeeting": {
                    "joinUrl": "https://teams.microsoft.com/l/meetup-join/19%3ameeting_MTM5OTY3MGUtNmY4Mi00Yjg4LTk2MDUtY2IyZGRlNmU1ZjA2%40thread.v2/0?context=%7b%22Tid%22%3a%222432b57b-0abd-43db-aa7b-16eadd115d34%22%2c%22Oid%22%3a%2214b779ae-cb64-47e7-a512-52fd50a4154d%22%7d"
                },
                "calendar@odata.associationLink": "https://graph.microsoft.com/beta/users('14b779ae-cb64-47e7-a512-52fd50a4154d')/calendars('AAMkAGE3NjJhOTVhLTNkZDQtNDE2OS05ZjU0LTJmOGQ0YTY2YTdiZQAuAAAAAAD3AG5jNnlgQJvdCL_KgXJIAQBsww5BlIxtT7iFyYWrXV3AAAAAAAENAAA=')/$ref",
                "calendar@odata.navigationLink": "https://graph.microsoft.com/beta/users('14b779ae-cb64-47e7-a512-52fd50a4154d')/calendars('AAMkAGE3NjJhOTVhLTNkZDQtNDE2OS05ZjU0LTJmOGQ0YTY2YTdiZQAuAAAAAAD3AG5jNnlgQJvdCL_KgXJIAQBsww5BlIxtT7iFyYWrXV3AAAAAAAENAAA=')"
                }
                ```

              </details>

3. **Obter ID de reunião**: agora, seu aplicativo pode usar `joinWebUrl` para obter a ID de reunião.

    Use o exemplo a seguir para solicitar a ID de reunião online:

    ``` http
    GET https://graph.microsoft.com/beta/users('14b779ae-cb64-47e7-a512-52fd50a4154d')/onlineMeetings?$filter=JoinWebUrl%20eq%20'https://teams.microsoft.com/l/meetup-join/19%3ameeting_MTM5OTY3MGUtNmY4Mi00Yjg4LTk2MDUtY2IyZGRlNmU1ZjA2%40thread.v2/0?context=%7b%22Tid%22%3a%222432b57b-0abd-43db-aa7b-16eadd115d34%22%2c%22Oid%22%3a%2214b779ae-cb64-47e7-a512-52fd50a4154d%22%7d'
    ```

    O conteúdo da resposta contém a ID de reunião no membro `id` da propriedade `value`.
    <br>
    <details>
    <summary><b>Exemplo</b>: conteúdo da resposta com a ID de reunião</summary>

    ```json
    {
        "@odata.context": "https://graph.microsoft.com/beta/$metadata#users('14b779ae-cb64-47e7-a512-52fd50a4154d')/onlineMeetings",
        "value": [
            {
                "id": "MSoxNGI3NzlhZS1jYjY0LTQ3ZTctYTUxMi01MmZkNTBhNDE1NGQqMCoqMTk6bWVldGluZ19NVE01T1RZM01HVXRObVk0TWkwMFlqZzRMVGsyTURVdFkySXlaR1JsTm1VMVpqQTJAdGhyZWFkLnYy",
                "creationDateTime": "2022-04-26T07:41:17.3736455Z",
                "startDateTime": "2022-04-26T10:30:00Z",
                "endDateTime": "2022-04-26T11:00:00Z",
                "joinUrl": "https://teams.microsoft.com/l/meetup-join/19%3ameeting_MTM5OTY3MGUtNmY4Mi00Yjg4LTk2MDUtY2IyZGRlNmU1ZjA2%40thread.v2/0?context=%7b%22Tid%22%3a%222432b57b-0abd-43db-aa7b-16eadd115d34%22%2c%22Oid%22%3a%2214b779ae-cb64-47e7-a512-52fd50a4154d%22%7d",
                "joinWebUrl": "https://teams.microsoft.com/l/meetup-join/19%3ameeting_MTM5OTY3MGUtNmY4Mi00Yjg4LTk2MDUtY2IyZGRlNmU1ZjA2%40thread.v2/0?context=%7b%22Tid%22%3a%222432b57b-0abd-43db-aa7b-16eadd115d34%22%2c%22Oid%22%3a%2214b779ae-cb64-47e7-a512-52fd50a4154d%22%7d",
                "chatInfo": {
                    "threadId": "19:meeting_MTM5OTY3MGUtNmY4Mi00Yjg4LTk2MDUtY2IyZGRlNmU1ZjA2@thread.v2",
                    "messageId": "0",
                    "replyChainMessageId": null
                }
            }
        ]
    }
    ```

    </details>

4. **Buscar transcrição**: a ID de organizador e a ID de reunião obtidas nas etapas 2 e 3 permitem que seu aplicativo busque as transcrições para esse evento de reunião específico.

    Para buscar transcrições, você precisará:

    1. **Recupere a ID de transcrição com base na ID de organizador e na ID de reunião**:

       Use o exemplo a seguir para solicitar a ID de transcrição:

        ```http
        GET https://graph.microsoft.com/beta/users('14b779ae-cb64-47e7-a512-52fd50a4154d')/onlineMeetings('MSoxNGI3NzlhZS1jYjY0LTQ3ZTctYTUxMi01MmZkNTBhNDE1NGQqMCoqMTk6bWVldGluZ19ObVUwTlRreFl6TXRNMlkyTXkwME56UmxMV0ZtTjJZdE5URmlNR001T1dNM1pqWTJAdGhyZWFkLnYy')/transcripts
        ```

        Neste exemplo:

        - A ID de reunião está incluída como o valor para `onlineMeetings`: *MSoxNGI3NzlhZS1jYjY0LTQ3ZTctYTUxMi01MmZkNTBhNDE1NGQqMCoqMTk6bW VldGluZ19ObVUwTlRreFl6TXRNMlkyTXkwME56UmxMV0ZtTjJZdE5URmlNR001T1dNM 1pqWTJAdGhyZWFkLnYy*.
        - A ID de organizador é *14b779ae-cb64-47e7-a512-52fd50a4154d*.

        O conteúdo da resposta contém a ID de transcrição para a ID de reunião e a ID de organizador no membro `id` da propriedade `value`.
        <br>
        <details>
        <summary><b>Exemplo</b>: conteúdo da resposta para obter a ID de transcrição</summary>

        ```json
        {
            "@odata.context": "https://graph.microsoft.com/beta/$metadata#users('14b779ae-cb64-47e7-a512-52fd50a4154d')/onlineMeetings('MSoxNGI3NzlhZS1jYjY0LTQ3ZTctYTUxMi01MmZkNTBhNDE1NGQqMCoqMTk6bWVldGluZ19ObVUwTlRreFl6TXRNMlkyTXkwME56UmxMV0ZtTjJZdE5URmlNR001T1dNM1pqWTJAdGhyZWFkLnYy')/transcripts",
            "@odata.count": 1,
            "value": [
                {
                    "id": "MSMjMCMjMDEyNjJmNjgtOTc2Zi00MzIxLTlhNDQtYThmMmY4ZjQ1ZjVh",
                    "createdDateTime": "2022-04-14T11:34:39.5662792Z"
                }
            ]
        }
        ```

        Neste exemplo, a ID de transcrição é *MSMjMCMjMDEyNjJmNjgtOTc2Zi00MzIxLTlhNDQtYThmMmY4ZjQ1ZjVh*.

        </details>

    1. **Acesse e obtenha a transcrição da reunião com base na ID de transcrição**:

        Use o exemplo a seguir para solicitar as transcrições de uma reunião específica no formato `.vtt` :

        ```http
        GET https://graph.microsoft.com/beta/users('14b779ae-cb64-47e7-a512-52fd50a4154d')/onlineMeetings('MSoxNGI3NzlhZS1jYjY0LTQ3ZTctYTUxMi01MmZkNTBhNDE1NGQqMCoqMTk6bWVldGluZ19ObVUwTlRreFl6TXRNMlkyTXkwME56UmxMV0ZtTjJZdE5URmlNR001T1dNM1pqWTJAdGhyZWFkLnYy')/transcripts('MSMjMCMjMDEyNjJmNjgtOTc2Zi00MzIxLTlhNDQtYThmMmY4ZjQ1ZjVh')/content?$format=text/vtt
        ```

        O conteúdo da resposta conterá as transcrições no formato `.vtt`.

### <a name="use-bot-framework-to-get-meeting-id-and-organizer-id"></a>Usar o Bot Framework para obter a ID de reunião e a ID de organizador

Seu aplicativo pode usar o Bot Framework para obter a ID de reunião e a ID de organizador. O bot pode receber eventos de início ou término de reunião automaticamente de todas as reuniões online agendadas.

Use o exemplo a seguir para obter a ID de reunião e a ID de organizador usando um aplicativo de bot:

```json
GET /v1/meetings/{meetingId}
```

O conteúdo da resposta contém:

- A ID de reunião no membro `msGraphResourceId` da propriedade `details`.
- A ID de organizador no membro `id` da propriedade `organizer`.
<br>
<details>
<summary><b>Exemplo</b>: conteúdo da resposta para obter detalhes da reunião</b></summary>

```json
{
  details: {
    id: "MCMxOTptZWV0aW5nX05XTTFNVEk1TnpNdE5qZ3pNeTAwWVdRNExUaG1PV1F0WlRnM01UQm1PVGczWW1VekB0aHJlYWQudjIjMA==",
    msGraphResourceId: "MSo2NzAyYWZiNi0xMDliLTRjMzItYTE0MS02ZTY1NDY5NTAyYjkqMCoqMTk6bWVldGluZ19OV00xTVRJNU56TXROamd6TXkwMFlXUTRMVGhtT1dRdFpUZzNNVEJtT1RnM1ltVXpAdGhyZWFkLnYy",
    scheduledStartTime: {
    },
    scheduledEndTime: {
    },
    joinUrl: "https://teams.microsoft.com/l/meetup-join/19%3ameeting_NWM1MTI5NzMtNjgzMy00YWQ4LThmOWQtZTg3MTBmOTg3YmUz%40thread.v2/0?context=%7b%22Tid%22%3a%22b3cdf1c8-024a-49e2-a994-f67f830b02f3%22%2c%22Oid%22%3a%226702afb6-109b-4c32-a141-6e65469502b9%22%7d",
    title: "Testing meeting bot 1 - Hun",
    type: "Scheduled",
  },
  conversation: {
    id: "19:meeting_NWM1MTI5NzMtNjgzMy00YWQ4LThmOWQtZTg3MTBmOTg3YmUz@thread.v2",
    isGroup: true,
    conversationType: "groupChat",
  },
  organizer: {
    id: "29:1VZkVr77S3GW_RdAXKrfgFeytpqMegL3tkKvEbwrPqoCVvmqrlKtVrfKWUY7xIM-bZIx4Sq-p1MjdjSZnb5W20w",
    tenantId: "b3cdf1c8-024a-49e2-a994-f67f830b02f3",
    aadObjectId: "6702afb6-109b-4c32-a141-6e65469502b9",
  },
}
```

Neste exemplo:

- A ID de reunião está incluída como o valor para `msGraphResourceId`: *MSo2NzAyYWZiNi0xMDliLTRjMzItYTE0MS02ZTY1NDY5NTAyYjkqMCoqMTk6bWVl dGluZ19OV00xTVRJNU56TXROamd6TXkwMFlXUTRMVGhtT1dRdFpUZzNNVEJtT1RnM 1ltVXpAdGhyZWFkLnYy*.
- A ID de organizador está contida como o valor para `id` de `organizer`:  *29:1VZkVr77S3GW_RdAXKrfgFeytpqMegL3tkKvEbwrPqoCVvmqrlKtVrfKWUY7xIM-bZIx4Sq-p1MjdjSZnb5W20w*.

</details>

Depois que seu aplicativo obtém a ID de reunião e a ID de organizador, ele dispara as APIs do Graph para buscar conteúdo de transcrição usando esses detalhes da reunião.

### <a name="code-samples"></a>Exemplos de código

Você pode experimentar o exemplo de código a seguir para um aplicativo de bot:

| **Nome de exemplo** | **Descrição** | **C#** | **Node.js** |
|----------------|-----------------|--------------|--------------|--------------|
| Transcrição de reunião | Este é um aplicativo de exemplo que demonstra como obter transcrição usando API do Graph e exibi-la no módulo de tarefa. | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meetings-transcription/csharp) | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meetings-transcription/nodejs) |

## <a name="next-step"></a>Próxima etapa

> [!div class="nextstepaction"]
> [APIs do Graph para buscar transcrições](/graph/api/resources/calltranscript)
