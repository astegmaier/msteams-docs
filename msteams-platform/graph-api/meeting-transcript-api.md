---
title: Access meeting transcript using Graph API
description: How to access meeting transcript using Graph API
ms.localizationpriority: medium
author: akjo
ms.author: Surbhigupta12
ms.topic: Overview
keywords: Access meeting transcript using Graph API
---

# Access meeting transcript using Graph API

Teams Graph Service allows you to access post- meeting transcript.

## Permissions

> [!NOTE]
> For information on how to choose permissions, see [Permissions](/graph/permissions-reference?branch=main)

Teams Graph Service allows you to access post- meeting transcript using APIs. To call the APIs any one of the permission listed in the following table is required:

|Permission type      | Permissions (from least to most privileged)              |
|--------------------|---------------------------------------------------------|
|Delegated (work or school account) | OnlineMeetingTranscript.Read.All |
|Delegated (personal Microsoft account) | Not supported.    |
|Application | OnlineMeetingTranscript.Read.All |

To use application permission for the API, tenant administrators must create an application access policy for the user. This authorizes that the app configured in the policy gets online meetings or online meeting artifacts on behalf of the user. The user ID is specified in the request path). For more information, see [how to to access online meetings on behalf of a user](/graph/cloud-communication-online-meeting-application-access-policy?branch=main). 

## List of APIs

Teams Graph Service will leverage Meeting Artifacts Service (https://aka.ms/meetingArtifactsApi) using the following APIs to get meeting’s transcripts. 

<br>

<details>
<summary><b>List callTranscripts</b></summary>

**HTTP request**

```http
GET /me/onlineMeetings({meetingId})/transcripts
GET /users({userId})/onlineMeetings({meetingId})/transcripts
```

**Optional query parameters**

This method supports the `$skipToken` and `$top` [OData query parameters](/graph/query-parameters) to help customize the response.

**Supported query patterns**

| Pattern                | Supported | Syntax                                 | Notes |
| ---------------------- | ------- | -------------------------------------- | ----- |
| Server-side pagination |     ✓     | `@odata.nextLink`                      | You will get a continuation token in the response, when a result set spans multiple pages. |
| Page limit             |     ✓     | `/transcripts?$top=20` | Get transcripts with page size 20. Default page limit is 10. Max page limit is 100. |

**Request headers**

| Header       | Value |
|:---------------|:--------|
| Authorization  | Bearer {token}. Required.  |

**Request body**

Do not supply a request body for this method.

**Response**

If successful, this method returns a `200 OK` response code and a collection of [callTranscript](../resources/callTranscript.md) objects in the response body.

**Example**

**Request**

``` http
GET https://graph.microsoft.com/beta/users/ba321e0d-79ee-478d-8e28-85a19507f456/onlineMeetings/MSo1N2Y5ZGFjYy03MWJmLTQ3NDMtYjQxMy01M2EdFGkdRWHJlQ/transcripts
```

**Response**

> [!Note]
> The response object shown here might be shortened for readability.


``` http
HTTP/1.1 200 OK
Content-Type: application/json

{
    "@odata.context": "https://graph.microsoft.com/beta/$metadata#users('ba321e0d-79ee-478d-8e28-85a19507f456')/onlineMeetings('MSo1N2Y5ZGFjYy03MWJmLTQ3NDMtYjQxMy01M2EdFGkdRWHJlQ')/transcripts",
    "@odata.count": 3,
    "@odata.nextLink": "https://graph.microsoft.com/beta/users('ba321e0d-79ee-478d-8e28-85a19507f456')/onlineMeetings('MSo1N2Y5ZGFjYy03MWJmLTQ3NDMtYjQxMy01M2EdFGkdRWHJlQ')/transcripts?$skiptoken=MSMjMCMjMjAyMS0wOS0xNlQxMzo1OToyNy4xMjEwMzgzWg%3d%3d",
    "value": [
        {
            "id": "MSMjMCMjZDAwYWU3NjUtNmM2Yi00NjQxLTgwMWQtMTkzMmFmMjEzNzdh",
            "createdDateTime": "2021-09-17T06:09:24.8968037Z"
        },
        {
            "id": "MSMjMCMjMzAxNjNhYTctNWRmZi00MjM3LTg5MGQtNWJhYWZjZTZhNWYw",
            "createdDateTime": "2021-09-16T18:58:58.6760692Z"
        },
        {
            "id": "MSMjMCMjNzU3ODc2ZDYtOTcwMi00MDhkLWFkNDItOTE2ZDNmZjkwZGY4",
            "createdDateTime": "2021-09-16T18:56:00.9038309Z"
        }        
    ]
}
```

<br>

</details>

<br>

<details>
<summary><b>Get callTranscript</b></summary>


<br>

</details>

<br>

<details>
<summary><b>Get callTranscript content</b></summary>


<br>

</details>