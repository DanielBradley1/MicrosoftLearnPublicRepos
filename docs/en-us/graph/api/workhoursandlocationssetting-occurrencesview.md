<!-- Source: https://learn.microsoft.com/en-us/graph/api/workhoursandlocationssetting-occurrencesview?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-03-21 -->

# workHoursAndLocationsSetting: occurrencesView

Namespace: microsoft.graph

Get [work plan occurrences](https://learn.microsoft.com/en-us/graph/api/resources/workplanoccurrence?view=graph-rest-1.0) from a user's work plan within a specified date range. This function requires the **startDateTime** and **endDateTime** parameters.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Calendars.Read | Calendars.ReadWrite |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Calendars.Read.All | Calendars.ReadWrite.All |

> **Note:** Application permissions are supported only when using the `/users/{id}` endpoint.

## HTTP request

```http
GET /me/settings/workHoursAndLocations/occurrencesView(startDateTime='{startDateTime}',endDateTime='{endDateTime}')
```

Note

Calling the `/me` endpoint requires a signed-in user and therefore a delegated permission. Application permissions aren't supported when using the `/me` endpoint.

When using delegated permissions with the `/users/{id}` endpoint, the ID must be the signed-in user's ID.

```http
GET /users/{id | userPrincipalName}/settings/workHoursAndLocations/occurrencesView(startDateTime='{startDateTime}',endDateTime='{endDateTime}')
```

## Function parameters

In the request URL, provide the following required function parameters with values.

| Parameter | Type | Description |
| :--- | :--- | :--- |
| endDateTime | String | The end date and time of the time range, represented in ISO 8601 format. |
| startDateTime | String | The start date and time of the time range, represented in ISO 8601 format. |

## Optional query parameters

This method supports the `$select` and `$top` [OData query parameters](https://learn.microsoft.com/en-us/graph/query-parameters) to help customize the response.

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this function returns a `200 OK` response code and a collection of [workPlanOccurrence](https://learn.microsoft.com/en-us/graph/api/resources/workplanoccurrence?view=graph-rest-1.0) objects in the response body.

## Examples

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

```msgraph
GET https://graph.microsoft.com/v1.0/me/settings/workHoursAndLocations/occurrencesView(startDateTime='2025-12-01T00:00:00Z',endDateTime='2025-12-01T23:59:59Z')
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Me.Settings.WorkHoursAndLocations.OccurrencesViewWithStartDateTimeWithEndDateTime("{endDateTime}","{startDateTime}").GetAsOccurrencesViewWithStartDateTimeWithEndDateTimeGetResponseAsync();
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
startDateTime := "{startDateTime}"
endDateTime := "{endDateTime}"
occurrencesView, err := graphClient.Me().Settings().WorkHoursAndLocations().OccurrencesViewWithStartDateTimeWithEndDateTime(&startDateTime, &endDateTime).GetAsOccurrencesViewWithStartDateTimeWithEndDateTimeGetResponse(context.Background(), nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

var result = graphClient.me().settings().workHoursAndLocations().occurrencesViewWithStartDateTimeWithEndDateTime("{endDateTime}", "{startDateTime}").get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let occurrencesView = await client.api('/me/settings/workHoursAndLocations/occurrencesView(startDateTime='2025-12-01T00:00:00Z',endDateTime='2025-12-01T23:59:59Z')')
	.get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);


$result = $graphServiceClient->me()->settings()->workHoursAndLocations()->occurrencesViewWithStartDateTimeWithEndDateTime('{endDateTime}', '{startDateTime}', )->get()->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Users

# A UPN can also be used as -UserId.
Invoke-MgViewUserSettingWorkHourAndLocationOccurrence -UserId $userId
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python

result = await graph_client.me.settings.work_hours_and_locations.occurrences_view_with_start_date_time_with_end_date_time("{endDateTime}","{startDateTime}").get()
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-type: application/json

{
  "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#Collection(microsoft.graph.workPlanOccurrence)",
  "value": [
    {
      "id": "AAkBOQAICN4wbJIpwAAuAAAAAB2EAxGqZhHNm8gAqgAvxFoNAOtpUxZW-2ZHr9tjSZTO0jMAA2pPCT8AABA=",
      "recurrenceId": "AAkALgAAAAAAHYQDEapmEc2byACqAC-EWg0A62lTFlb-Zkev22NJlM7SMwADak8JPwAA",
      "workLocationType": "remote",
      "start": {
        "dateTime": "2025-12-01T09:00:00.0000000",
        "timeZone": "Pacific Standard Time"
      },
      "end": {
        "dateTime": "2025-12-01T18:00:00.0000000",
        "timeZone": "Pacific Standard Time"
      }
    }
  ]
}
```
