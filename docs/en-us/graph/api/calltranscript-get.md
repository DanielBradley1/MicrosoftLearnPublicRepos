<!-- Source: https://learn.microsoft.com/en-us/graph/api/calltranscript-get?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-09-08 -->

# Get callTranscript

Namespace: microsoft.graph

Retrieve a [callTranscript](https://learn.microsoft.com/en-us/graph/api/resources/calltranscript?view=graph-rest-1.0) object associated with a scheduled [onlineMeeting](https://learn.microsoft.com/en-us/graph/api/resources/onlinemeeting?view=graph-rest-1.0). This API supports the retrieval of call transcripts from all meeting types except live events.

Retrieving the transcript returns the metadata of the single transcript associated with an online meeting or an ad hoc call. Retrieving the content of the transcript returns the stream of text associated with the transcript.

Note

For online meetings:

- This API doesn't support meetings created using the [create onlineMeeting API](https://learn.microsoft.com/en-us/graph/api/application-post-onlinemeetings) that aren't associated with an event on the user's calendar.
- This API works differently in one or more national clouds. For details, see [Implementation differences in national clouds](https://learn.microsoft.com/en-us/graph/teamwork-national-cloud-differences).
- If you want to retrieve meeting transcripts, use the [Create event](https://learn.microsoft.com/en-us/graph/api/user-post-events?view=graph-rest-1.0) API instead.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | OnlineMeetingTranscript.Read.All \(for online meetings\)  <br>  <br>CallTranscripts.Read.All \(for ad hoc calls\) | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | OnlineMeetingTranscript.Read.All,  <br>OnlineMeetingTranscript.Read.Chat \(for online meetings\)  <br>CallTranscripts.Read.All \(for ad hoc calls\) | Not available. |

Note

The application permissions `OnlineMeetingTranscript.Read.Chat` uses [resource-specific consent](https://learn.microsoft.com/en-us/microsoftteams/platform/graph-api/rsc/resource-specific-consent). The `OnlineMeetingTranscript.Read.Chat` permission applies only to scheduled private chat meetings, not to channel meetings. For a channel meeting, use `OnlineMeetingTranscript.Read.All` with an application access policy.

To use application permission for this API, tenant administrators must create an *application access policy* and grant it to a user. It authorizes the app configured in the policy to fetch online meetings and/or online meeting artifacts on behalf of that user \(with the user ID specified in the request path\). For more information, see [Allow applications to access online meetings on behalf of a user](https://learn.microsoft.com/en-us/graph/cloud-communication-online-meeting-application-access-policy).

Note

For online meetings:

- This API works for a meeting only if the meeting hasn't expired. For more information, see [Limits and specifications for Microsoft Teams](https://learn.microsoft.com/en-us/microsoftteams/limits-specifications-teams#meeting-expiration).
- This API is also available to users who are part of the meeting calendar invite, which applies to both private chat meetings and channel meetings.

### Tenant administrator controls for transcript access

Access to transcripts through this API requires the appropriate Graph permissions and is also governed by two independent tenant administrator settings:

- **Graph API access to transcripts.** When disabled, all transcript requests \(metadata, `metadataContent`, and `content`\) return `403 Forbidden` with the `GraphAccessToTranscriptsDisabled` inner-error code, regardless of the requested format.
- **Speaker attribution.** When disabled, transcript content can be retrieved only without speaker information.

A tenant administrator configures these meeting settings in the Teams Admin Center, or by using the `Set-CsTeamsMeetingConfiguration` cmdlet.

The `/content` endpoint supports two formats:

- `text/vtt` \(default\) — WebVTT with timestamped utterances and `<v Speaker>` voice tags \(speaker-attributed\).
- `application/vnd.microsoft.graph.transcript+text` — timestamped utterances without speaker information \(speaker-unattributed\).

Select `text/vtt` with either the `Accept` header or the `$format` query parameter. The `application/vnd.microsoft.graph.transcript+text` format must be selected with the `Accept` header; it isn't supported through the `$format` query parameter.

When the tenant administrator has disabled speaker attribution, requesting the attributed format \(`text/vtt`\) returns `403 Forbidden` with the `SpeakerAttributionNotAllowed` inner-error code. Retry with the unattributed format to retrieve the transcript. The speaker-attribution setting never blocks the unattributed format, but it remains subject to the Graph API access to transcripts setting.

Note

The `application/vnd.microsoft.graph.transcript+text` format and the related tenant administrator controls take effect at the end of July 2026.

## HTTP request

On the `/content` endpoints, select the transcript content format with the `Accept` request header, as described in [Transcript content formats](#transcript-content-formats).

Get a single transcript for an online meeting

```http
GET /me/onlineMeetings/{meetingId}/transcripts/{transcriptId}
GET /users/{userId}/onlineMeetings/{meetingId}/transcripts/{transcriptId}
```

Get the content of a single transcript for an online meeting

- Both transcription and speaker attribution are enabled

```http
GET /me/onlineMeetings/{meetingId}/transcripts/{transcriptId}/content
GET /users/{userId}/onlineMeetings/{meetingId}/transcripts/{transcriptId}/content
```

- Transcription is enabled, but speaker attribution is disabled

```http
GET /me/onlineMeetings/{meetingId}/transcripts/{transcriptId}/content
GET /users/{userId}/onlineMeetings/{meetingId}/transcripts/{transcriptId}/content
```

Get a single transcript for an ad hoc call

```http
GET /me/adhocCalls/{callId}/transcripts/{transcriptId}
GET /users/{userId}/adhocCalls/{callId}/transcripts/{transcriptId}
```

Get the content of a single transcript for an ad hoc call

- Both transcription and speaker attribution are enabled

```http
GET /me/adhocCalls/{callId}/transcripts/{transcriptId}/content
GET /users/{userId}/adhocCalls/{callId}/transcripts/{transcriptId}/content
```

- Transcription is enabled, but speaker attribution is disabled

```http
GET /me/adhocCalls/{callId}/transcripts/{transcriptId}/content
GET /users/{userId}/adhocCalls/{callId}/transcripts/{transcriptId}/content
```

## Optional query parameters

This method supports the `$select` [OData query parameter](https://learn.microsoft.com/en-us/graph/query-parameters) to customize the response.

## Request headers

| Header | Value |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Accept | text/vtt or application/vnd.microsoft.graph.transcript+text. Optional. On the /content endpoints, selects the transcript content format. For text/vtt, this is equivalent to the `$format` query parameter; the application/vnd.microsoft.graph.transcript+text format is supported only through this header. |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and a [callTranscript](https://learn.microsoft.com/en-us/graph/api/resources/calltranscript?view=graph-rest-1.0) object in the response body.

### Transcript content formats

The `/content` endpoint supports the following formats. Select `text/vtt` with either the `$format` query parameter or the `Accept` request header. The `application/vnd.microsoft.graph.transcript+text` format must be selected with the `Accept` request header.

| Format | Speaker attribution | Description |
| --- | --- | --- |
| `text/vtt` | Yes | WebVTT with timestamped utterances and `<v Speaker>` voice tags. Returned by default. |
| `application/vnd.microsoft.graph.transcript+text` | No | Timestamped utterances only, without `<v Speaker>` voice tags. |

If the tenant disallows speaker attribution, requests for `text/vtt` fail with `403 Forbidden` / `SpeakerAttributionNotAllowed`; request `application/vnd.microsoft.graph.transcript+text` instead.

### Error responses

This API is governed by tenant administrator settings for transcript access and speaker attribution. Branch on the `innerError.code` value, not the message text. Messages are subject to change.

#### Graph API access to transcripts is disabled

If a tenant administrator has turned off Graph API access to transcripts for the tenant, all transcript requests — `metadata`, `metadataContent`, and `content` — return `403 Forbidden` with the `GraphAccessToTranscriptsDisabled` inner-error code. There is no request-side workaround; the app receives this response until an administrator re-enables access.

```http
HTTP/1.1 403 Forbidden
Content-Type: application/json

{
  "error": {
    "code": "Forbidden",
    "message": "Graph API access to transcripts is disabled for this tenant.",
    "innerError": {
      "code": "GraphAccessToTranscriptsDisabled"
    }
  }
}
```

#### Speaker-attributed content is disabled

When a tenant administrator disallows speaker attribution, the `/content` endpoints return `403 Forbidden` with the `SpeakerAttributionNotAllowed` inner-error code **only if the request asks for a speaker-attributed format** \(`text/vtt`\). Retry the same request asking for the unattributed format, `application/vnd.microsoft.graph.transcript+text`, which succeeds. This error applies to the `/content` endpoints only \(per-meeting and ad hoc\); transcript metadata requests are unaffected.

```http
HTTP/1.1 403 Forbidden
Content-Type: application/json

{
  "error": {
    "code": "Forbidden",
    "message": "Speaker-attributed transcript content is disabled for this tenant. Retry with Accept 'application/vnd.microsoft.graph.transcript+text'.",
    "innerError": {
      "code": "SpeakerAttributionNotAllowed"
    }
  }
}
```

## Examples

Note

The docx format for transcripts is deprecated as of May 31, 2023.

### Example 1: Get a callTranscript for an online meeting

The following example shows how to get a single transcript of an online meeting.

#### Request

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [PowerShell](#tabpanel_1_powershell)
- [Python](#tabpanel_1_python)

```msgraph
GET https://graph.microsoft.com/v1.0/users/ba321e0d-79ee-478d-8e28-85a19507f456/onlineMeetings/MSo1N2Y5ZGFjYy03MWJmLTQ3NDMtYjQxMy01M2EdFGkdRWHJlQ/transcripts/MSMjMCMjNzU3ODc2ZDYtOTcwMi00MDhkLWFkNDItOTE2ZDNmZjkwZGY4
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Users["{user-id}"].OnlineMeetings["{onlineMeeting-id}"].Transcripts["{callTranscript-id}"].GetAsync();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  //other-imports
)


// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
transcripts, err := graphClient.Users().ByUserId("user-id").OnlineMeetings().ByOnlineMeetingId("onlineMeeting-id").Transcripts().ByCallTranscriptId("callTranscript-id").Get(context.Background(), nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

CallTranscript result = graphClient.users().byUserId("{user-id}").onlineMeetings().byOnlineMeetingId("{onlineMeeting-id}").transcripts().byCallTranscriptId("{callTranscript-id}").get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let callTranscript = await client.api('/users/ba321e0d-79ee-478d-8e28-85a19507f456/onlineMeetings/MSo1N2Y5ZGFjYy03MWJmLTQ3NDMtYjQxMy01M2EdFGkdRWHJlQ/transcripts/MSMjMCMjNzU3ODc2ZDYtOTcwMi00MDhkLWFkNDItOTE2ZDNmZjkwZGY4')
	.get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);


$result = $graphServiceClient->users()->byUserId('user-id')->onlineMeetings()->byOnlineMeetingId('onlineMeeting-id')->transcripts()->byCallTranscriptId('callTranscript-id')->get()->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.CloudCommunications

Get-MgUserOnlineMeetingTranscript -UserId $userId -OnlineMeetingId $onlineMeetingId -CallTranscriptId $callTranscriptId
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python

result = await graph_client.users.by_user_id('user-id').online_meetings.by_online_meeting_id('onlineMeeting-id').transcripts.by_call_transcript_id('callTranscript-id').get()
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#users('ba321e0d-79ee-478d-8e28-85a19507f456')/onlineMeetings('MSo1N2Y5ZGFjYy03MWJmLTQ3NDMtYjQxMy01M2EdFGkdRWHJlQ')/transcripts/$entity",
    "id": "MSMjMCMjNzU3ODc2ZDYtOTcwMi00MDhkLWFkNDItOTE2ZDNmZjkwZGY4",
    "meetingId": "MSo1N2Y5ZGFjYy03MWJmLTQ3NDMtYjQxMy01M2EdFGkdRWHJlQ",
    "callId": "af630fe0-04d3-4559-8cf9-91fe45e36296",
    "createdDateTime": "2021-09-17T06:09:24.8968037Z",
    "endDateTime": "2021-09-17T06:27:25.2346000Z",
    "contentCorrelationId": "bc842d7a-2f6e-4b18-a1c7-73ef91d5c8e3",
    "transcriptContentUrl": "https://graph.microsoft.com/v1.0/$metadata#users('ba321e0d-79ee-478d-8e28-85a19507f456')/onlineMeetings('MSo1N2Y5ZGFjYy03MWJmLTQ3NDMtYjQxMy01M2EdFGkdRWHJlQ')/transcripts/('MSMjMCMjNzU3ODc2ZDYtOTcwMi00MDhkLWFkNDItOTE2ZDNmZjkwZGY4')/content",
    "meetingOrganizer": {
        "application": null,
        "device": null,
        "user": {
            "@odata.type": "#Microsoft.Teams.GraphSvc.teamworkUserIdentity",
            "id": "ba321e0d-79ee-478d-8e28-85a19507f456",
            "displayName": null,
            "userIdentityType": "aadUser",
            "tenantId": "cd6cee19-2d76-4ee0-8f47-9ed12ee44331"
        }
    }
}
```

### Example 2: Get a callTranscript for an ad hoc call

The following example shows how to get a single transcript of an ad hoc call.

#### Request

- [HTTP](#tabpanel_2_http)
- [C#](#tabpanel_2_csharp)
- [Go](#tabpanel_2_go)
- [Java](#tabpanel_2_java)
- [JavaScript](#tabpanel_2_javascript)
- [PHP](#tabpanel_2_php)
- [PowerShell](#tabpanel_2_powershell)
- [Python](#tabpanel_2_python)

```http
GET https://graph.microsoft.com/v1.0/users/f2e8e111-3887-4936-87f8-639292c70d34/adhocCalls/5f3640e7-a59c-4bec-82ca-e66251f795b7/transcripts/MyMjMTk6NWFiOWQ2OGUxNDhlNDgyNThmYmMzOWYwOGUzOTkyN2NAdGhyZWFkLnYyIyM1ZjM2NDBlNy1hNTljLTRiZWMtODJjYS1lNjYyNTFmNzk1YjctMTc1NDg5MjIyMi1UcmFuc2NyaXB0VjIjIzA=
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Users["{user-id}"].AdhocCalls["{adhocCall-id}"].Transcripts["{callTranscript-id}"].GetAsync();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  //other-imports
)


// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
transcripts, err := graphClient.Users().ByUserId("user-id").AdhocCalls().ByAdhocCallId("adhocCall-id").Transcripts().ByCallTranscriptId("callTranscript-id").Get(context.Background(), nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

CallTranscript result = graphClient.users().byUserId("{user-id}").adhocCalls().byAdhocCallId("{adhocCall-id}").transcripts().byCallTranscriptId("{callTranscript-id}").get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let callTranscript = await client.api('/users/f2e8e111-3887-4936-87f8-639292c70d34/adhocCalls/5f3640e7-a59c-4bec-82ca-e66251f795b7/transcripts/MyMjMTk6NWFiOWQ2OGUxNDhlNDgyNThmYmMzOWYwOGUzOTkyN2NAdGhyZWFkLnYyIyM1ZjM2NDBlNy1hNTljLTRiZWMtODJjYS1lNjYyNTFmNzk1YjctMTc1NDg5MjIyMi1UcmFuc2NyaXB0VjIjIzA=')
	.get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);


$result = $graphServiceClient->users()->byUserId('user-id')->adhocCalls()->byAdhocCallId('adhocCall-id')->transcripts()->byCallTranscriptId('callTranscript-id')->get()->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```
Snippet not available
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python

result = await graph_client.users.by_user_id('user-id').adhoc_calls.by_adhoc_call_id('adhocCall-id').transcripts.by_call_transcript_id('callTranscript-id').get()
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

Note

The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-type: application/json

{
  "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#users('f2e8e111-3887-4936-87f8-639292c70d34')/adhocCalls('5f3640e7-a59c-4bec-82ca-e66251f795b7')/transcripts/$entity",
  "id": "MyMjMTk6NWFiOWQ2OGUxNDhlNDgyNThmYmMzOWYwOGUzOTkyN2NAdGhyZWFkLnYyIyM1ZjM2NDBlNy1hNTljLTRiZWMtODJjYS1lNjYyNTFmNzk1YjctMTc1NDg5MjIyMi1UcmFuc2NyaXB0VjIjIzA=",
  "callId": "5f3640e7-a59c-4bec-82ca-e66251f795b7",
  "createdDateTime": "2025-08-11T06:03:42.9757215Z",
  "endDateTime": "2025-08-11T06:04:21.2551933Z",
  "contentCorrelationId": "c316fb26-aed9-4476-8827-b5be74f74051-10002",
  "transcriptContentUrl": "https://graph.microsoft.com/v1.0/users/f2e8e111-3887-4936-87f8-639292c70d34/adhocCalls/5f3640e7-a59c-4bec-82ca-e66251f795b7/transcripts('MyMjMTk6NWFiOWQ2OGUxNDhlNDgyNThmYmMzOWYwOGUzOTkyN2NAdGhyZWFkLnYyIyM1ZjM2NDBlNy1hNTljLTRiZWMtODJjYS1lNjYyNTFmNzk1YjctMTc1NDg5MjIyMi1UcmFuc2NyaXB0VjIjIzA=')/content",
  "meetingOrganizer": {
      "application": null,
      "device": null,
      "user": {
            "@odata.type": "#microsoft.graph.teamworkUserIdentity",
            "id": "f2e8e111-3887-4936-87f8-639292c70d34",
            "displayName": null,
            "userIdentityType": "aadUser",
            "tenantId": "8393309d-9fb7-4cce-aafb-eedc8c5781e2"
      }
   }
}
```

### Example 3: Get a callTranscript content for an online meeting where speaker-attributed content is enabled

#### Request

- [HTTP](#tabpanel_3_http)
- [C#](#tabpanel_3_csharp)
- [Go](#tabpanel_3_go)
- [Java](#tabpanel_3_java)
- [JavaScript](#tabpanel_3_javascript)
- [PHP](#tabpanel_3_php)
- [PowerShell](#tabpanel_3_powershell)
- [Python](#tabpanel_3_python)

```http
GET https://graph.microsoft.com/v1.0/users/ba321e0d-79ee-478d-8e28-85a19507f456/onlineMeetings/MSo1N2Y5ZGFjYy03MWJmLTQ3NDMtYjQxMy01M2EdFGkdRWHJlQ/transcripts/MSMjMCMjNzU3ODc2ZDYtOTcwMi00MDhkLWFkNDItOTE2ZDNmZjkwZGY4/content
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
await graphClient.Users["{user-id}"].OnlineMeetings["{onlineMeeting-id}"].Transcripts["{callTranscript-id}"].Content.GetAsync();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  //other-imports
)


// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
graphClient.Users().ByUserId("user-id").OnlineMeetings().ByOnlineMeetingId("onlineMeeting-id").Transcripts().ByCallTranscriptId("callTranscript-id").Content().Get(context.Background(), nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

graphClient.users().byUserId("{user-id}").onlineMeetings().byOnlineMeetingId("{onlineMeeting-id}").transcripts().byCallTranscriptId("{callTranscript-id}").content().get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let stream = await client.api('/users/ba321e0d-79ee-478d-8e28-85a19507f456/onlineMeetings/MSo1N2Y5ZGFjYy03MWJmLTQ3NDMtYjQxMy01M2EdFGkdRWHJlQ/transcripts/MSMjMCMjNzU3ODc2ZDYtOTcwMi00MDhkLWFkNDItOTE2ZDNmZjkwZGY4/content')
	.get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);


$graphServiceClient->users()->byUserId('user-id')->onlineMeetings()->byOnlineMeetingId('onlineMeeting-id')->transcripts()->byCallTranscriptId('callTranscript-id')->content()->get()->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.CloudCommunications

Get-MgUserOnlineMeetingTranscriptContent -UserId $userId -OnlineMeetingId $onlineMeetingId -CallTranscriptId $callTranscriptId
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python

await graph_client.users.by_user_id('user-id').online_meetings.by_online_meeting_id('onlineMeeting-id').transcripts.by_call_transcript_id('callTranscript-id').content.get()
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The response contains the transcript content in the body as bytes. The `content-type` header specifies the type of the transcript content. Negative offsets indicate that the transcription began while the conversation was ongoing.

Note

The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-type: text/vtt

WEBVTT

00:00:16.246 --> 00:00:17.726
<v User Name>This is a transcript test.</v>
```

### Example 4: Get a callTranscript content for an ad hoc call when speaker-attributed content is disabled

#### Request

- [HTTP](#tabpanel_4_http)
- [C#](#tabpanel_4_csharp)
- [Go](#tabpanel_4_go)
- [Java](#tabpanel_4_java)
- [JavaScript](#tabpanel_4_javascript)
- [PHP](#tabpanel_4_php)
- [PowerShell](#tabpanel_4_powershell)
- [Python](#tabpanel_4_python)

```http
GET https://graph.microsoft.com/v1.0/users/f2e8e111-3887-4936-87f8-639292c70d34/adhocCalls/5f3640e7-a59c-4bec-82ca-e66251f795b7/transcripts/MyMjMTk6NWFiOWQ2OGUxNDhlNDgyNThmYmMzOWYwOGUzOTkyN2NAdGhyZWFkLnYyIyM1ZjM2NDBlNy1hNTljLTRiZWMtODJjYS1lNjYyNTFmNzk1YjctMTc1NDg5MjIyMi1UcmFuc2NyaXB0VjIjIzA=/content
Accept: application/vnd.microsoft.graph.transcript+text
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
await graphClient.Users["{user-id}"].AdhocCalls["{adhocCall-id}"].Transcripts["{callTranscript-id}"].Content.GetAsync((requestConfiguration) =>
{
	requestConfiguration.Headers.Add("Accept", "application/vnd.microsoft.graph.transcript+text");
});
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  abstractions "github.com/microsoft/kiota-abstractions-go"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphusers "github.com/microsoftgraph/msgraph-sdk-go/users"
	  //other-imports
)

headers := abstractions.NewRequestHeaders()
headers.Add("Accept", "application/vnd.microsoft.graph.transcript+text")

configuration := &graphusers.ItemAdhocCallsItemTranscriptsItemContentRequestBuilderGetRequestConfiguration{
	Headers: headers,
}

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
graphClient.Users().ByUserId("user-id").AdhocCalls().ByAdhocCallId("adhocCall-id").Transcripts().ByCallTranscriptId("callTranscript-id").Content().Get(context.Background(), configuration)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

graphClient.users().byUserId("{user-id}").adhocCalls().byAdhocCallId("{adhocCall-id}").transcripts().byCallTranscriptId("{callTranscript-id}").content().get(requestConfiguration -> {
	requestConfiguration.headers.add("Accept", "application/vnd.microsoft.graph.transcript+text");
});
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let stream = await client.api('/users/f2e8e111-3887-4936-87f8-639292c70d34/adhocCalls/5f3640e7-a59c-4bec-82ca-e66251f795b7/transcripts/MyMjMTk6NWFiOWQ2OGUxNDhlNDgyNThmYmMzOWYwOGUzOTkyN2NAdGhyZWFkLnYyIyM1ZjM2NDBlNy1hNTljLTRiZWMtODJjYS1lNjYyNTFmNzk1YjctMTc1NDg5MjIyMi1UcmFuc2NyaXB0VjIjIzA=/content')
	.header('Accept','application/vnd.microsoft.graph.transcript+text')
	.get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Users\Item\AdhocCalls\Item\Transcripts\Item\Content\ContentRequestBuilderGetRequestConfiguration;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestConfiguration = new ContentRequestBuilderGetRequestConfiguration();
$headers = [
		'Accept' => 'application/vnd.microsoft.graph.transcript+text',
	];
$requestConfiguration->headers = $headers;


$graphServiceClient->users()->byUserId('user-id')->adhocCalls()->byAdhocCallId('adhocCall-id')->transcripts()->byCallTranscriptId('callTranscript-id')->content()->get($requestConfiguration)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```
Snippet not available
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.users.item.adhoc_calls.item.transcripts.item.content.content_request_builder import ContentRequestBuilder
from kiota_abstractions.base_request_configuration import RequestConfiguration
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python

request_configuration = RequestConfiguration()
request_configuration.headers.add("Accept", "application/vnd.microsoft.graph.transcript+text")


await graph_client.users.by_user_id('user-id').adhoc_calls.by_adhoc_call_id('adhocCall-id').transcripts.by_call_transcript_id('callTranscript-id').content.get(request_configuration = request_configuration)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The response contains the transcript in the body as bytes. The `content-type` header specifies the type of the transcript content. Negative offsets indicate that the transcription began while the conversation was ongoing.

Note

The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-type: application/vnd.microsoft.graph.transcript+text

00:00:01.500 --> 00:00:04.000 

Hello, thanks for joining. 

00:00:04.000 --> 00:00:07.200 

Glad to be here. 
```

### Example 5: Get a callTranscript content for an online meeting when speaker-attributed content is disabled

The following example shows how to get the content of a single transcript of an online meeting when speaker-attributed content is disabled.

#### Request

- [HTTP](#tabpanel_5_http)
- [C#](#tabpanel_5_csharp)
- [Go](#tabpanel_5_go)
- [Java](#tabpanel_5_java)
- [JavaScript](#tabpanel_5_javascript)
- [PHP](#tabpanel_5_php)
- [PowerShell](#tabpanel_5_powershell)
- [Python](#tabpanel_5_python)

```http
GET https://graph.microsoft.com/v1.0/users/ba321e0d-79ee-478d-8e28-85a19507f456/onlineMeetings/MSo1N2Y5ZGFjYy03MWJmLTQ3NDMtYjQxMy01M2EdFGkdRWHJlQ/transcripts/MSMjMCMjNzU3ODc2ZDYtOTcwMi00MDhkLWFkNDItOTE2ZDNmZjkwZGY4/content
Accept: application/vnd.microsoft.graph.transcript+text
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
await graphClient.Users["{user-id}"].OnlineMeetings["{onlineMeeting-id}"].Transcripts["{callTranscript-id}"].Content.GetAsync((requestConfiguration) =>
{
	requestConfiguration.Headers.Add("Accept", "application/vnd.microsoft.graph.transcript+text");
});
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  abstractions "github.com/microsoft/kiota-abstractions-go"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphusers "github.com/microsoftgraph/msgraph-sdk-go/users"
	  //other-imports
)

headers := abstractions.NewRequestHeaders()
headers.Add("Accept", "application/vnd.microsoft.graph.transcript+text")

configuration := &graphusers.ItemOnlineMeetingsItemTranscriptsItemContentRequestBuilderGetRequestConfiguration{
	Headers: headers,
}

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
graphClient.Users().ByUserId("user-id").OnlineMeetings().ByOnlineMeetingId("onlineMeeting-id").Transcripts().ByCallTranscriptId("callTranscript-id").Content().Get(context.Background(), configuration)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

graphClient.users().byUserId("{user-id}").onlineMeetings().byOnlineMeetingId("{onlineMeeting-id}").transcripts().byCallTranscriptId("{callTranscript-id}").content().get(requestConfiguration -> {
	requestConfiguration.headers.add("Accept", "application/vnd.microsoft.graph.transcript+text");
});
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let stream = await client.api('/users/ba321e0d-79ee-478d-8e28-85a19507f456/onlineMeetings/MSo1N2Y5ZGFjYy03MWJmLTQ3NDMtYjQxMy01M2EdFGkdRWHJlQ/transcripts/MSMjMCMjNzU3ODc2ZDYtOTcwMi00MDhkLWFkNDItOTE2ZDNmZjkwZGY4/content')
	.header('Accept','application/vnd.microsoft.graph.transcript+text')
	.get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Users\Item\OnlineMeetings\Item\Transcripts\Item\Content\ContentRequestBuilderGetRequestConfiguration;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestConfiguration = new ContentRequestBuilderGetRequestConfiguration();
$headers = [
		'Accept' => 'application/vnd.microsoft.graph.transcript+text',
	];
$requestConfiguration->headers = $headers;


$graphServiceClient->users()->byUserId('user-id')->onlineMeetings()->byOnlineMeetingId('onlineMeeting-id')->transcripts()->byCallTranscriptId('callTranscript-id')->content()->get($requestConfiguration)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.CloudCommunications

Get-MgUserOnlineMeetingTranscriptContent -UserId $userId -OnlineMeetingId $onlineMeetingId -CallTranscriptId $callTranscriptId
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.users.item.online_meetings.item.transcripts.item.content.content_request_builder import ContentRequestBuilder
from kiota_abstractions.base_request_configuration import RequestConfiguration
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python

request_configuration = RequestConfiguration()
request_configuration.headers.add("Accept", "application/vnd.microsoft.graph.transcript+text")


await graph_client.users.by_user_id('user-id').online_meetings.by_online_meeting_id('onlineMeeting-id').transcripts.by_call_transcript_id('callTranscript-id').content.get(request_configuration = request_configuration)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The response contains the transcript content in the body as bytes. The `content-type` header specifies the type of the transcript content. Negative offsets indicate that the transcription began while the conversation was ongoing.

Note

The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-type: application/vnd.microsoft.graph.transcript+text

00:00:01.500 --> 00:00:04.000 

Hello, thanks for joining. 

00:00:04.000 --> 00:00:07.200 

Glad to be here. 
```

### Example 6: Get unattributed callTranscript content

The following example shows how to get transcript content without speaker attribution. Request this format using the `Accept` header.

#### Request

```http
GET https://graph.microsoft.com/v1.0/users/ba321e0d-79ee-478d-8e28-85a19507f456/onlineMeetings/MSo1N2Y5ZGFjYy03MWJmLTQ3NDMtYjQxMy01M2EdFGkdRWHJlQ/transcripts/MSMjMCMjNzU3ODc2ZDYtOTcwMi00MDhkLWFkNDItOTE2ZDNmZjkwZGY4/content
Accept: application/vnd.microsoft.graph.transcript+text
```

---

#### Response

The response contains the transcript content in the body as bytes, without `<v Speaker>` voice tags. The content-type header specifies the type of the transcript content.

Note

The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-type: application/vnd.microsoft.graph.transcript+text

00:00:16.246 --> 00:00:17.726
This is a transcript test.
```

### Example 7: Speaker attribution disabled by tenant policy

The following example shows the response when speaker attribution is disabled for the tenant and the request asks for an attributed format \(`text/vtt`\). Retry with `application/vnd.microsoft.graph.transcript+text` to receive the unattributed transcript.

#### Request

```http
GET https://graph.microsoft.com/v1.0/users/ba321e0d-79ee-478d-8e28-85a19507f456/onlineMeetings/MSo1N2Y5ZGFjYy03MWJmLTQ3NDMtYjQxMy01M2EdFGkdRWHJlQ/transcripts/MSMjMCMjNzU3ODc2ZDYtOTcwMi00MDhkLWFkNDItOTE2ZDNmZjkwZGY4/content
Accept: text/vtt
```

#### Response

```http
HTTP/1.1 403 Forbidden
Content-Type: application/json

{
  "error": {
    "code": "Forbidden",
    "message": "Speaker-attributed transcript content is disabled for this tenant. Retry with Accept 'application/vnd.microsoft.graph.transcript+text'.",
    "innerError": {
      "code": "SpeakerAttributionNotAllowed"
    }
  }
}
```

### Example 8: Get a callTranscript content for an ad hoc call when speaker-attributed content is enabled

The following example shows how to get the content of a single transcript of an ad hoc call when speaker-attributed content is enabled.

#### Request

- [HTTP](#tabpanel_6_http)
- [C#](#tabpanel_6_csharp)
- [Go](#tabpanel_6_go)
- [Java](#tabpanel_6_java)
- [JavaScript](#tabpanel_6_javascript)
- [PHP](#tabpanel_6_php)
- [PowerShell](#tabpanel_6_powershell)
- [Python](#tabpanel_6_python)

```http
GET https://graph.microsoft.com/v1.0/users/f2e8e111-3887-4936-87f8-639292c70d34/adhocCalls/5f3640e7-a59c-4bec-82ca-e66251f795b7/transcripts/MyMjMTk6NWFiOWQ2OGUxNDhlNDgyNThmYmMzOWYwOGUzOTkyN2NAdGhyZWFkLnYyIyM1ZjM2NDBlNy1hNTljLTRiZWMtODJjYS1lNjYyNTFmNzk1YjctMTc1NDg5MjIyMi1UcmFuc2NyaXB0VjIjIzA=/content
Accept: text/vtt
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
await graphClient.Users["{user-id}"].AdhocCalls["{adhocCall-id}"].Transcripts["{callTranscript-id}"].Content.GetAsync((requestConfiguration) =>
{
	requestConfiguration.Headers.Add("Accept", "text/vtt");
});
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  abstractions "github.com/microsoft/kiota-abstractions-go"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphusers "github.com/microsoftgraph/msgraph-sdk-go/users"
	  //other-imports
)

headers := abstractions.NewRequestHeaders()
headers.Add("Accept", "text/vtt")

configuration := &graphusers.ItemAdhocCallsItemTranscriptsItemContentRequestBuilderGetRequestConfiguration{
	Headers: headers,
}

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
graphClient.Users().ByUserId("user-id").AdhocCalls().ByAdhocCallId("adhocCall-id").Transcripts().ByCallTranscriptId("callTranscript-id").Content().Get(context.Background(), configuration)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

graphClient.users().byUserId("{user-id}").adhocCalls().byAdhocCallId("{adhocCall-id}").transcripts().byCallTranscriptId("{callTranscript-id}").content().get(requestConfiguration -> {
	requestConfiguration.headers.add("Accept", "text/vtt");
});
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let stream = await client.api('/users/f2e8e111-3887-4936-87f8-639292c70d34/adhocCalls/5f3640e7-a59c-4bec-82ca-e66251f795b7/transcripts/MyMjMTk6NWFiOWQ2OGUxNDhlNDgyNThmYmMzOWYwOGUzOTkyN2NAdGhyZWFkLnYyIyM1ZjM2NDBlNy1hNTljLTRiZWMtODJjYS1lNjYyNTFmNzk1YjctMTc1NDg5MjIyMi1UcmFuc2NyaXB0VjIjIzA=/content')
	.header('Accept','text/vtt')
	.get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Users\Item\AdhocCalls\Item\Transcripts\Item\Content\ContentRequestBuilderGetRequestConfiguration;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestConfiguration = new ContentRequestBuilderGetRequestConfiguration();
$headers = [
		'Accept' => 'text/vtt',
	];
$requestConfiguration->headers = $headers;


$graphServiceClient->users()->byUserId('user-id')->adhocCalls()->byAdhocCallId('adhocCall-id')->transcripts()->byCallTranscriptId('callTranscript-id')->content()->get($requestConfiguration)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```
Snippet not available
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.users.item.adhoc_calls.item.transcripts.item.content.content_request_builder import ContentRequestBuilder
from kiota_abstractions.base_request_configuration import RequestConfiguration
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python

request_configuration = RequestConfiguration()
request_configuration.headers.add("Accept", "text/vtt")


await graph_client.users.by_user_id('user-id').adhoc_calls.by_adhoc_call_id('adhocCall-id').transcripts.by_call_transcript_id('callTranscript-id').content.get(request_configuration = request_configuration)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The response contains the transcript in the body as bytes. The `content-type` header specifies the type of the transcript content. Negative offsets indicate that the transcription began while the conversation was ongoing.

Note

The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-type: text/vtt

WEBVTT

00:00:01.500 --> 00:00:04.000 
<v User Name>Hello, thanks for joining.</v>

00:00:04.000 --> 00:00:07.200 
<v User Name>Glad to be here.</v>
```

### Example 9: Get a callTranscript metadataContent for online meetings

#### Request

- [HTTP](#tabpanel_7_http)
- [C#](#tabpanel_7_csharp)
- [Go](#tabpanel_7_go)
- [Java](#tabpanel_7_java)
- [JavaScript](#tabpanel_7_javascript)
- [PHP](#tabpanel_7_php)
- [PowerShell](#tabpanel_7_powershell)
- [Python](#tabpanel_7_python)

```http
GET https://graph.microsoft.com/v1.0/users/ba321e0d-79ee-478d-8e28-85a19507f456/onlineMeetings/MSo1N2Y5ZGFjYy03MWJmLTQ3NDMtYjQxMy01M2EdFGkdRWHJlQ/transcripts/MSMjMCMjNzU3ODc2ZDYtOTcwMi00MDhkLWFkNDItOTE2ZDNmZjkwZGY4/metadataContent
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
await graphClient.Users["{user-id}"].OnlineMeetings["{onlineMeeting-id}"].Transcripts["{callTranscript-id}"].MetadataContent.GetAsync();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  //other-imports
)


// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
graphClient.Users().ByUserId("user-id").OnlineMeetings().ByOnlineMeetingId("onlineMeeting-id").Transcripts().ByCallTranscriptId("callTranscript-id").MetadataContent().Get(context.Background(), nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

graphClient.users().byUserId("{user-id}").onlineMeetings().byOnlineMeetingId("{onlineMeeting-id}").transcripts().byCallTranscriptId("{callTranscript-id}").metadataContent().get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let stream = await client.api('/users/ba321e0d-79ee-478d-8e28-85a19507f456/onlineMeetings/MSo1N2Y5ZGFjYy03MWJmLTQ3NDMtYjQxMy01M2EdFGkdRWHJlQ/transcripts/MSMjMCMjNzU3ODc2ZDYtOTcwMi00MDhkLWFkNDItOTE2ZDNmZjkwZGY4/metadataContent')
	.get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);


$graphServiceClient->users()->byUserId('user-id')->onlineMeetings()->byOnlineMeetingId('onlineMeeting-id')->transcripts()->byCallTranscriptId('callTranscript-id')->metadataContent()->get()->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.CloudCommunications

Get-MgUserOnlineMeetingTranscriptMetadataContent -UserId $userId -OnlineMeetingId $onlineMeetingId -CallTranscriptId $callTranscriptId
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python

await graph_client.users.by_user_id('user-id').online_meetings.by_online_meeting_id('onlineMeeting-id').transcripts.by_call_transcript_id('callTranscript-id').metadata_content.get()
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-type: text/vtt

WEBVTT
00:00:16.246 --> 00:00:17.726
{"startDateTime":"2023-03-08T08:22:30.0461639+00:00","endDateTime":"2023-03-08T08:22:31.5261639+00:00","speakerName":"User Name","spokenText":"This is a transcription test.","spokenLanguage":"en-us"}
```

### Example 10: Get a callTranscript metadataContent for ad hoc calls

#### Request

- [HTTP](#tabpanel_8_http)
- [C#](#tabpanel_8_csharp)
- [Go](#tabpanel_8_go)
- [Java](#tabpanel_8_java)
- [JavaScript](#tabpanel_8_javascript)
- [PHP](#tabpanel_8_php)
- [PowerShell](#tabpanel_8_powershell)
- [Python](#tabpanel_8_python)

```http
GET https://graph.microsoft.com/v1.0/users/f2e8e111-3887-4936-87f8-639292c70d34/adhocCalls/5f3640e7-a59c-4bec-82ca-e66251f795b7/transcripts/MyMjMTk6NWFiOWQ2OGUxNDhlNDgyNThmYmMzOWYwOGUzOTkyN2NAdGhyZWFkLnYyIyM1ZjM2NDBlNy1hNTljLTRiZWMtODJjYS1lNjYyNTFmNzk1YjctMTc1NDg5MjIyMi1UcmFuc2NyaXB0VjIjIzA=/metadataContent
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
await graphClient.Users["{user-id}"].AdhocCalls["{adhocCall-id}"].Transcripts["{callTranscript-id}"].MetadataContent.GetAsync();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  //other-imports
)


// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
graphClient.Users().ByUserId("user-id").AdhocCalls().ByAdhocCallId("adhocCall-id").Transcripts().ByCallTranscriptId("callTranscript-id").MetadataContent().Get(context.Background(), nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

graphClient.users().byUserId("{user-id}").adhocCalls().byAdhocCallId("{adhocCall-id}").transcripts().byCallTranscriptId("{callTranscript-id}").metadataContent().get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let stream = await client.api('/users/f2e8e111-3887-4936-87f8-639292c70d34/adhocCalls/5f3640e7-a59c-4bec-82ca-e66251f795b7/transcripts/MyMjMTk6NWFiOWQ2OGUxNDhlNDgyNThmYmMzOWYwOGUzOTkyN2NAdGhyZWFkLnYyIyM1ZjM2NDBlNy1hNTljLTRiZWMtODJjYS1lNjYyNTFmNzk1YjctMTc1NDg5MjIyMi1UcmFuc2NyaXB0VjIjIzA=/metadataContent')
	.get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);


$graphServiceClient->users()->byUserId('user-id')->adhocCalls()->byAdhocCallId('adhocCall-id')->transcripts()->byCallTranscriptId('callTranscript-id')->metadataContent()->get()->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```
Snippet not available
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python

await graph_client.users.by_user_id('user-id').adhoc_calls.by_adhoc_call_id('adhocCall-id').transcripts.by_call_transcript_id('callTranscript-id').metadata_content.get()
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

Note

The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-type: text/vtt

WEBVTT
00:00:03.663 --> 00:00:07.903
{"startDateTime":"2025-08-11T06:03:46.6390101+00:00","endDateTime":"2025-08-11T06:03:50.8790101+00:00","speakerName":"MOD Administrator","spokenText":"Hello. Hello. Hello. Hello. Hello. Hello.","spokenLanguage":"en-us"}

00:00:08.063 --> 00:00:08.103
{"startDateTime":"2025-08-11T06:03:51.0390101+00:00","endDateTime":"2025-08-11T06:03:51.0790101+00:00","speakerName":"MOD Administrator","spokenText":"Oh.","spokenLanguage":"en-us"}
```

### Example 11: Get a callTranscript from a corresponding recording using contentCorrelationId

The following example shows how to get a single transcript of an online meeting corresponding to a recording using the **contentCorrelationId** property.

#### Request

The following example shows a request.

- [HTTP](#tabpanel_9_http)
- [C#](#tabpanel_9_csharp)
- [Go](#tabpanel_9_go)
- [Java](#tabpanel_9_java)
- [JavaScript](#tabpanel_9_javascript)
- [PHP](#tabpanel_9_php)
- [PowerShell](#tabpanel_9_powershell)
- [Python](#tabpanel_9_python)

```http
GET https://graph.microsoft.com/v1.0/me/onlineMeetings/MSoxMjczYTAxNi0yMDFkLTRmOTUtODA4My0xYjdmOTliM2VkZWIqMCoqMTk6bWVldGluZ19OV1EwWm1GbFpEY3RORFJqTmkwMFlXRm1MV0U1WXpBdE9UZzJNMk0yTm1Nd1pERTNAdGhyZWFkLnYy/transcripts?$filter=contentcorrelationId+eq+'e87c8cf8-50f7-4252-8b9c-ad08ac0fa88d-0'
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Me.OnlineMeetings["{onlineMeeting-id}"].Transcripts.GetAsync((requestConfiguration) =>
{
	requestConfiguration.QueryParameters.Filter = "contentcorrelationId eq 'e87c8cf8-50f7-4252-8b9c-ad08ac0fa88d-0'";
});
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphusers "github.com/microsoftgraph/msgraph-sdk-go/users"
	  //other-imports
)


requestFilter := "contentcorrelationId eq 'e87c8cf8-50f7-4252-8b9c-ad08ac0fa88d-0'"

requestParameters := &graphusers.OnlineMeetingsItemTranscriptsRequestBuilderGetQueryParameters{
	Filter: &requestFilter,
}
configuration := &graphusers.OnlineMeetingsItemTranscriptsRequestBuilderGetRequestConfiguration{
	QueryParameters: requestParameters,
}

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
transcripts, err := graphClient.Me().OnlineMeetings().ByOnlineMeetingId("onlineMeeting-id").Transcripts().Get(context.Background(), configuration)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

CallTranscriptCollectionResponse result = graphClient.me().onlineMeetings().byOnlineMeetingId("{onlineMeeting-id}").transcripts().get(requestConfiguration -> {
	requestConfiguration.queryParameters.filter = "contentcorrelationId eq 'e87c8cf8-50f7-4252-8b9c-ad08ac0fa88d-0'";
});
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let transcripts = await client.api('/me/onlineMeetings/MSoxMjczYTAxNi0yMDFkLTRmOTUtODA4My0xYjdmOTliM2VkZWIqMCoqMTk6bWVldGluZ19OV1EwWm1GbFpEY3RORFJqTmkwMFlXRm1MV0U1WXpBdE9UZzJNMk0yTm1Nd1pERTNAdGhyZWFkLnYy/transcripts')
	.filter('contentcorrelationId eq \'e87c8cf8-50f7-4252-8b9c-ad08ac0fa88d-0\'')
	.get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Users\Item\OnlineMeetings\Item\Transcripts\TranscriptsRequestBuilderGetRequestConfiguration;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestConfiguration = new TranscriptsRequestBuilderGetRequestConfiguration();
$queryParameters = TranscriptsRequestBuilderGetRequestConfiguration::createQueryParameters();
$queryParameters->filter = "contentcorrelationId eq 'e87c8cf8-50f7-4252-8b9c-ad08ac0fa88d-0'";
$requestConfiguration->queryParameters = $queryParameters;


$result = $graphServiceClient->me()->onlineMeetings()->byOnlineMeetingId('onlineMeeting-id')->transcripts()->get($requestConfiguration)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.CloudCommunications

# A UPN can also be used as -UserId.
Get-MgUserOnlineMeetingTranscript -UserId $userId -OnlineMeetingId $onlineMeetingId -Filter "contentcorrelationId eq 'e87c8cf8-50f7-4252-8b9c-ad08ac0fa88d-0'" 
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.users.item.online_meetings.item.transcripts.transcripts_request_builder import TranscriptsRequestBuilder
from kiota_abstractions.base_request_configuration import RequestConfiguration
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
query_params = TranscriptsRequestBuilder.TranscriptsRequestBuilderGetQueryParameters(
		filter = "contentcorrelationId eq 'e87c8cf8-50f7-4252-8b9c-ad08ac0fa88d-0'",
)

request_configuration = RequestConfiguration(
query_parameters = query_params,
)

result = await graph_client.me.online_meetings.by_online_meeting_id('onlineMeeting-id').transcripts.get(request_configuration = request_configuration)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#users('1273a016-201d-4f95-8083-1b7f99b3edeb')/onlineMeetings('MSoxMjczYTAxNi0yMDFkLTRmOTUtODA4My0xYjdmOTliM2VkZWIqMCoqMTk6bWVldGluZ19OV1EwWm1GbFpEY3RORFJqTmkwMFlXRm1MV0U1WXpBdE9UZzJNMk0yTm1Nd1pERTNAdGhyZWFkLnYy')/transcripts",
    "@odata.count": 1,
    "@microsoft.graph.tips": "Use $select to choose only the properties your app needs, as this can lead to performance improvements. For example: GET me/onlineMeetings('<key>')/transcripts('<key>')?$select=callId,content",
    "value": [
        {
            "id": "VjIjIzExMjczYTAxNi0yMDFkLTRmOTUtODA4My0xYjdmOTliM2VkZWIyNDMyYjU3Yi0wYWJkLTQzZGItYWE3Yi0xNmVhZGQxMTVkMzQwNDAwMDAwMDgyMDBFMDAwNzRDNUI3MTAxQTgyRTAwODAwMDAwMDAwNDA3ZjYyNjg0ZmQ0ZGEwMTAwMDAwMDAwMDAwMDAwMDAxMDAwMDAwMDRiZWQ5YTIzZGMyZmZmNDY4OTc4OTg0NjU2ZjI3MjE5IyNhMTRlZWNiZC0xM2RmLTRjN2EtOWM3ZC1mZDg3OGU0YTU4YTI=",
            "meetingId": "MSoxMjczYTAxNi0yMDFkLTRmOTUtODA4My0xYjdmOTliM2VkZWIqMCoqMTk6bWVldGluZ19OV1EwWm1GbFpEY3RORFJqTmkwMFlXRm1MV0U1WXpBdE9UZzJNMk0yTm1Nd1pERTNAdGhyZWFkLnYy",
            "callId": "26c38520-e74d-4391-8188-cb458d413825",
            "contentCorrelationId": "e87c8cf8-50f7-4252-8b9c-ad08ac0fa88d-0",
            "transcriptContentUrl": "https://graph.microsoft.com/v1.0/users/1273a016-201d-4f95-8083-1b7f99b3edeb/onlineMeetings/MSoxMjczYTAxNi0yMDFkLTRmOTUtODA4My0xYjdmOTliM2VkZWIqMCoqMTk6bWVldGluZ19OV1EwWm1GbFpEY3RORFJqTmkwMFlXRm1MV0U1WXpBdE9UZzJNMk0yTm1Nd1pERTNAdGhyZWFkLnYy/transcripts/VjIjIzExMjczYTAxNi0yMDFkLTRmOTUtODA4My0xYjdmOTliM2VkZWIyNDMyYjU3Yi0wYWJkLTQzZGItYWE3Yi0xNmVhZGQxMTVkMzQwNDAwMDAwMDgyMDBFMDAwNzRDNUI3MTAxQTgyRTAwODAwMDAwMDAwNDA3ZjYyNjg0ZmQ0ZGEwMTAwMDAwMDAwMDAwMDAwMDAxMDAwMDAwMDRiZWQ5YTIzZGMyZmZmNDY4OTc4OTg0NjU2ZjI3MjE5IyNhMTRlZWNiZC0xM2RmLTRjN2EtOWM3ZC1mZDg3OGU0YTU4YTI=/content",
            "createdDateTime": "2024-07-12T11:37:59.0113199Z",
            "endDateTime": "2024-07-12T11:37:59.0113199Z",
            "meetingOrganizer": {
                "application": null,
                "device": null,
                "user": {
                    "@odata.type": "#microsoft.graph.teamworkUserIdentity",
                    "id": "1273a016-201d-4f95-8083-1b7f99b3edeb",
                    "displayName": null,
                    "userIdentityType": "aadUser",
                    "tenantId": "2432b57b-0abd-43db-aa7b-16eadd115d34"
                }
            }
        }
    ]
}
```
