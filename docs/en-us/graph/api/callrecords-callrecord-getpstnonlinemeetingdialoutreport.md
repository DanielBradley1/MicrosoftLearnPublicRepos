<!-- Source: https://learn.microsoft.com/en-us/graph/api/callrecords-callrecord-getpstnonlinemeetingdialoutreport?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-03-21 -->

# callRecord: getPstnOnlineMeetingDialoutReport

Namespace: microsoft.graph.callRecords

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Get aggregated report of usage and money spent for the audio conferencing dial-out service over a selected period as a collection of [pstnOnlineMeetingDialoutReport](https://learn.microsoft.com/en-us/graph/api/resources/callrecords-pstnonlinemeetingdialoutreport?view=graph-rest-beta) entries. The report is aggregated by user, user location, destination context \(domestic/international\), and currency.

The report includes:

- Cost: Communication credits spent over the selected period
- Dial-out calls: Total number of dial-out calls over the selected period
- Time of use: Total dial-out time \(in seconds\) over the selected period

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
GET /communications/callRecords/getPstnOnlineMeetingDialoutReport(fromDateTime={fromDateTime},toDateTime={toDateTime})
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

If successful, this function returns a `200 OK` response code and a collection of [microsoft.graph.callRecords.pstnOnlineMeetingDialoutReport](https://learn.microsoft.com/en-us/graph/api/resources/callrecords-pstnonlinemeetingdialoutreport?view=graph-rest-beta) entries in the response body.

If the function returns more than 1,000 entries for the specified date range, the body also includes an `@odata.nextLink` with a URL to query the next page of entries. The last page in the date range doesn't have an `@odata.nextLink`. For more information, see [paging Microsoft Graph data in your app](https://learn.microsoft.com/en-us/graph/paging).

## Example

The following example shows how to get the aggregated report for the audio conferencing dial-out service over a specified date range. The response includes `"@odata.count": 1000` to enumerate the number of records in this first response, and an `@odata.nextLink` to get records beyond the first 1,000. For readability, the response object contains only a collection of one record.

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
GET https://graph.microsoft.com/beta/communications/callRecords/getPstnOnlineMeetingDialoutReport(fromDateTime=2022-11-01,toDateTime=2022-12-01)
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Communications.CallRecords.MicrosoftGraphCallRecordsGetPstnOnlineMeetingDialoutReportWithFromDateTimeWithToDateTime(DateTimeOffset.Parse("{fromDateTime}"),DateTimeOffset.Parse("{toDateTime}")).GetAsGetPstnOnlineMeetingDialoutReportWithFromDateTimeWithToDateTimeGetResponseAsync();
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
microsoftGraphCallRecordsGetPstnOnlineMeetingDialoutReport, err := graphClient.Communications().CallRecords().MicrosoftGraphCallRecordsGetPstnOnlineMeetingDialoutReportWithFromDateTimeWithToDateTime(&fromDateTime, &toDateTime).GetAsGetPstnOnlineMeetingDialoutReportWithFromDateTimeWithToDateTimeGetResponse(context.Background(), nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

var result = graphClient.communications().callRecords().microsoftGraphCallRecordsGetPstnOnlineMeetingDialoutReportWithFromDateTimeWithToDateTime(OffsetDateTime.parse("{fromDateTime}"), OffsetDateTime.parse("{toDateTime}")).get();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let getPstnOnlineMeetingDialoutReport = await client.api('/communications/callRecords/getPstnOnlineMeetingDialoutReport(fromDateTime=2022-11-01,toDateTime=2022-12-01)')
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


$result = $graphServiceClient->communications()->callRecords()->microsoftGraphCallRecordsGetPstnOnlineMeetingDialoutReportWithFromDateTimeWithToDateTime(new \DateTime('{fromDateTime}'),new \DateTime('{toDateTime}'))->get()->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Beta.CloudCommunications

Get-MgBetaCommunicationCallRecordPstnOnlineMeetingDialoutReport
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python

result = await graph_client.communications.call_records.microsoft_graph_call_records_get_pstn_online_meeting_dialout_report_with_from_date_time_with_to_date_time("{fromDateTime}","{toDateTime}").get()
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
    "@odata.context": "https://graph.microsoft.com/beta/$metadata#Collection(microsoft.graph.callRecords.pstnOnlineMeetingDialoutReport)",
    "@odata.count": 1000,
    "@odata.nextLink": "https://graph.microsoft.com/beta/communications/callRecords/getPstnOnlineMeetingDialoutReport(fromDateTime=2022-11-01,toDateTime=2022-12-01)?$skip=1000",
    "value": [
        {
            "userId": "03de33bb-51df-40de-889a-61949faae24f",
            "userPrincipalName": "ruwini.perera@contoso.com",
            "userDisplayName": "Ruwini Perera",
            "usageLocation": "US",
            "destinationContext": "International",
            "currency": "USD",
            "totalCalls": 12,
            "totalCallCharge": 12.83,
            "totalCallSeconds": 723
        }
    ]
}
```

## Related content

- [Get log of PSTN calls](https://learn.microsoft.com/en-us/graph/api/callrecords-callrecord-getpstncalls?view=graph-rest-beta)
- [Get log of sent/received SMS](https://learn.microsoft.com/en-us/graph/api/callrecords-callrecord-getsmslog?view=graph-rest-beta)
- [Get log of direct routing calls](https://learn.microsoft.com/en-us/graph/api/callrecords-callrecord-getdirectroutingcalls?view=graph-rest-beta)
- [Microsoft Teams PSTN usage report](https://learn.microsoft.com/en-us/microsoftteams/teams-analytics-and-reports/pstn-usage-report)
