<!-- Source: https://learn.microsoft.com/en-us/graph/api/callrecords-callrecord-getpstncalls?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-23 -->

# callRecord: getPstnCalls

Namespace: microsoft.graph.callRecords

Get a log of PSTN calls as a collection of [pstnCallLogRow](https://learn.microsoft.com/en-us/graph/api/resources/callrecords-pstncalllogrow?view=graph-rest-1.0) entries.

Note

This API doesn't return information for **Telstra** calling plans.

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
GET /communications/callRecords/getPstnCalls(fromDateTime={fromDateTime},toDateTime={toDateTime})
```

## Function parameters

In the request URL, provide the following query parameters with values. The following table shows the parameters that can be used with this function.

| Parameter | Type | Description |
| :--- | :--- | :--- |
| fromDateTime | DateTimeOffset | Start of time range to query. UTC, inclusive.  <br>Time range is based on the call start time. |
| toDateTime | DateTimeOffset | End of time range to query. UTC, inclusive. |

Important

The **fromDateTime** and **toDateTime** values cannot be more than a date range of 90 days.

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Response

If successful, this function returns a `200 OK` response code and a collection of [pstnCallLogRow](https://learn.microsoft.com/en-us/graph/api/resources/callrecords-pstncalllogrow?view=graph-rest-1.0) entries in the response body.

If there are more than 1,000 entries in the date range, the body also includes an `@odata.nextLink` with a URL to query the next page of call entries. The last page in the date range doesn't have `@odata.nextLink`. For more information, see [paging Microsoft Graph data in your app](https://learn.microsoft.com/en-us/graph/paging).

## Example

The following example shows getting a collection of records for PSTN calls that occurred in the specified date range. The response includes `"@odata.count": 1000` to enumerate the number of records in this first response, and `@odata.nextLink` to get records beyond the first 1,000. For readability, the response shows only a collection of one record. Assume there are more than 1,000 calls in that date range.

### Request

The following example shows a request.

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [Python](#tabpanel_1_python)

```http
GET https://graph.microsoft.com/v1.0/communications/callRecords/getPstnCalls(fromDateTime=2019-11-01,toDateTime=2019-12-01)
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Communications.CallRecords.MicrosoftGraphCallRecordsGetPstnCallsWithFromDateTimeWithToDateTime(DateTimeOffset.Parse("{fromDateTime}"),DateTimeOffset.Parse("{toDateTime}")).GetAsGetPstnCallsWithFromDateTimeWithToDateTimeGetResponseAsync();
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
fromDateTime , err := time.Parse(time.RFC3339, "{fromDateTime}")
toDateTime , err := time.Parse(time.RFC3339, "{toDateTime}")
microsoftGraphCallRecordsGetPstnCalls, err := graphClient.Communications().CallRecords().MicrosoftGraphCallRecordsGetPstnCallsWithFromDateTimeWithToDateTime(&fromDateTime, &toDateTime).GetAsGetPstnCallsWithFromDateTimeWithToDateTimeGetResponse(context.Background(), nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

var result = graphClient.communications().callRecords().microsoftGraphCallRecordsGetPstnCallsWithFromDateTimeWithToDateTime(OffsetDateTime.parse("{fromDateTime}"), OffsetDateTime.parse("{toDateTime}")).get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let callRecord = await client.api('/communications/callRecords/getPstnCalls(fromDateTime=2019-11-01,toDateTime=2019-12-01)')
	.get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);


$result = $graphServiceClient->communications()->callRecords()->microsoftGraphCallRecordsGetPstnCallsWithFromDateTimeWithToDateTime(new \DateTime('{fromDateTime}'),new \DateTime('{toDateTime}'))->get()->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python

result = await graph_client.communications.call_records.microsoft_graph_call_records_get_pstn_calls_with_from_date_time_with_to_date_time("{fromDateTime}","{toDateTime}").get()
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#Collection(microsoft.graph.callRecords.pstnCallLogRow)",
    "@odata.count": 1000,
    "value": [
        {
            "id": "9c4984c7-6c3c-427d-a30c-bd0b2eacee90",
            "callId": "1835317186_112562680@61.221.3.176",
            "userId": "db03c14b-06eb-4189-939b-7cbf3a20ba27",
            "userPrincipalName": "richard.malk@contoso.com",
            "userDisplayName": "Richard Malk",
            "startDateTime": "2019-11-01T00:00:08.2589935Z",
            "endDateTime": "2019-11-01T00:03:47.2589935Z",
            "duration": 219,
            "charge": 0.00,
            "callType": "user_in",
            "currency": "USD",
            "calleeNumber": "+1234567890",
            "usageCountryCode": "US",
            "tenantCountryCode": "US",
            "connectionCharge": 0.00,
            "callerNumber": "+0123456789",
            "destinationContext": null,
            "destinationName": "United States",
            "conferenceId": null,
            "licenseCapability": "MCOPSTNU",
            "inventoryType": "Subscriber",
            "operator": "Microsoft",
            "callDurationSource": "microsoft"
        }
    ],
    "@odata.nextLink": "https://graph.microsoft.com/v1.0/communications/callRecords/getPstnCalls(from=2019-11-01,to=2019-12-01)?$skip=1000"
}
```

## Related content

- [Microsoft Teams PSTN usage report](https://learn.microsoft.com/en-us/microsoftteams/teams-analytics-and-reports/pstn-usage-report).
- [Direct Routing report in Microsoft Graph](https://learn.microsoft.com/en-us/graph/api/callrecords-callrecord-getdirectroutingcalls?view=graph-rest-1.0).
