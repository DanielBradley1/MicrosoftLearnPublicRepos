<!-- Source: https://learn.microsoft.com/en-us/graph/api/callrecords-callrecord-getpstnblockeduserslog?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-23 -->

# callRecord: getPstnBlockedUsersLog

Namespace: microsoft.graph.callRecords

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Get the log of users who are blocked/unblocked from making public switched telephone network \(PSTN\) calls in Microsoft Teams as a collection of [pstnBlockedUsersLogRow](https://learn.microsoft.com/en-us/graph/api/resources/callrecords-pstnblockeduserslogrow?view=graph-rest-beta) entries. The log includes information about each blocked user such as their assigned phone number and the reason they were blocked/unblocked from making calls.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Not supported. | Not supported. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | CallRecords.Read.All | Not available. |

## HTTP request

```http
GET /communications/callRecords/getPstnBlockedUsersLog(fromDateTime={fromDateTime},toDateTime={toDateTime})
```

## Function parameters

In the request URL, provide the following query parameters with values.

| Parameter | Type | Description |
| :--- | :--- | :--- |
| fromDateTime | DateTimeOffset | Start of time range to query. The Timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. Required. |
| toDateTime | DateTimeOffset | End of time range to query. The Timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. Required. |

Important

The **fromDateTime** and **toDateTime** values can't be more than a date range of 90 days.

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this function returns a `200 OK` response code and a collection of [microsoft.graph.callRecords.pstnBlockedUsersLogRow](https://learn.microsoft.com/en-us/graph/api/resources/callrecords-pstnblockeduserslogrow?view=graph-rest-beta) entries in the response body.

If the function returns more than 1,000 entries for the specified date range, the body also includes an `@odata.nextLink` with a URL to query the next page of entries. The last page in the date range doesn't have an `@odata.nextLink`. For more information, see [paging Microsoft Graph data in your app](https://learn.microsoft.com/en-us/graph/paging).

## Example

The following example shows how to get a collection of records for PSTN blocked users that occurred in the specified date range. The response includes `"@odata.count": 1000` to enumerate the number of records in the first response, and an `@odata.nextLink` to get records beyond the first 1,000. For readability, the response object contains only a collection of two records.

### Request

The following example shows a request.

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [PowerShell](#tabpanel_1_powershell)
- [Python](#tabpanel_1_python)

```http
GET https://graph.microsoft.com/beta/communications/callRecords/getPstnBlockedUsersLog(fromDateTime=2022-11-01,toDateTime=2022-12-01)
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Communications.CallRecords.MicrosoftGraphCallRecordsGetPstnBlockedUsersLogWithFromDateTimeWithToDateTime(DateTimeOffset.Parse("{fromDateTime}"),DateTimeOffset.Parse("{toDateTime}")).GetAsGetPstnBlockedUsersLogWithFromDateTimeWithToDateTimeGetResponseAsync();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v0.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-beta-sdk-go"
	  //other-imports
)


// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
fromDateTime , err := time.Parse(time.RFC3339, "{fromDateTime}")
toDateTime , err := time.Parse(time.RFC3339, "{toDateTime}")
microsoftGraphCallRecordsGetPstnBlockedUsersLog, err := graphClient.Communications().CallRecords().MicrosoftGraphCallRecordsGetPstnBlockedUsersLogWithFromDateTimeWithToDateTime(&fromDateTime, &toDateTime).GetAsGetPstnBlockedUsersLogWithFromDateTimeWithToDateTimeGetResponse(context.Background(), nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

var result = graphClient.communications().callRecords().microsoftGraphCallRecordsGetPstnBlockedUsersLogWithFromDateTimeWithToDateTime(OffsetDateTime.parse("{fromDateTime}"), OffsetDateTime.parse("{toDateTime}")).get();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let getPstnBlockedUsersLog = await client.api('/communications/callRecords/getPstnBlockedUsersLog(fromDateTime=2022-11-01,toDateTime=2022-12-01)')
	.version('beta')
	.get();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);


$result = $graphServiceClient->communications()->callRecords()->microsoftGraphCallRecordsGetPstnBlockedUsersLogWithFromDateTimeWithToDateTime(new \DateTime('{fromDateTime}'),new \DateTime('{toDateTime}'))->get()->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Beta.CloudCommunications

Get-MgBetaCommunicationCallRecordPstnBlockedUserLog
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python

result = await graph_client.communications.call_records.microsoft_graph_call_records_get_pstn_blocked_users_log_with_from_date_time_with_to_date_time("{fromDateTime}","{toDateTime}").get()
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
    "@odata.context": "https://graph.microsoft.com/beta/$metadata#Collection(microsoft.graph.callRecords.pstnBlockedUsersLogRow)",
    "@odata.count": 1000,
    "@odata.nextLink": "https://graph.microsoft.com/beta/communications/callRecords/getPstnBlockedUsersLog(fromDateTime=2022-11-01,toDateTime=2022-12-01)?$skip=1000",
    "value": [
        {
            "userId": "76efb13c-64ba-4305-9149-4e8f854004a9",
            "userPrincipalName": "andre.lawson@contoso.com",
            "userDisplayName": "Andre Lawson",
            "blockDateTime": "2022-11-23T13:51:09.796Z",
            "userTelephoneNumber": "+37212345678",
            "userBlockMode": "Blocked",
            "blockReason": "High Overall Usage",
            "remediationId": "c98e1515-a937-4b81-b8a8-3992afde64e0",
        },
        {
            "userId": "76efb13c-64ba-4305-9149-4e8f854004a9",
            "userPrincipalName": "ruwini.perera@contoso.com",
            "userDisplayName": "Ruwini Perera",
            "blockDateTime": "2022-11-23T13:51:09.796Z",
            "userTelephoneNumber": "+37212345678",
            "userBlockMode": "Unblocked",
            "blockReason": "Tenant Requested",
            "remediationId": "c98e1515-a937-4b81-b8a8-3992afde64e0",
        }
    ]
}
```

## Related content

- [Get log of PSTN calls in Microsoft Graph](https://learn.microsoft.com/en-us/graph/api/callrecords-callrecord-getpstncalls?view=graph-rest-beta)
- [Microsoft Teams PSTN usage report](https://learn.microsoft.com/en-us/microsoftteams/teams-analytics-and-reports/pstn-usage-report)
