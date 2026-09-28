<!-- Source: https://learn.microsoft.com/en-us/graph/api/calendar-delta?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-06-14 -->

# calendar: delta

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Get a set of [calendar](https://learn.microsoft.com/en-us/graph/api/resources/calendar?view=graph-rest-beta) resources added, deleted, or updated in one or more calendars.

Typically, synchronizing calendars in a mailbox in a local store entails a round of multiple **delta** function calls. The initial call is a full synchronization, and every subsequent **delta** call in the same round gets the incremental changes \(additions, deletions, or updates\). Using deltas allows you to incrementally maintain and synchronize a local store of calendars in the specified mailbox.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Calendars.Read | Calendars.ReadBasic, Calendars.ReadWrite |
| Delegated \(personal Microsoft account\) | Calendars.Read | Calendars.ReadBasic, Calendars.ReadWrite |
| Application | Calendars.Read | Calendars.ReadBasic, Calendars.ReadWrite |

## HTTP request

To begin tracking changes, you make a request including the delta function on the calendara resource.

- To get incremental changes of the calendar list *in the user's mailbox*:

```http
GET /me/calendars/delta
GET /users/{usersId}/calendars/delta
```

## Query parameters

Tracking changes in groups incurs a round of one or more **delta** function calls. If you use any query parameter \(other than `$deltatoken` and `$skiptoken`\), you must specify it in the initial **delta** request. Microsoft Graph automatically encodes any specified parameters into the token portion of the `@odata.nextLink` or `@odata.deltaLink` URL provided in the response.

You only need to specify any desired query parameters once upfront.

In subsequent requests, copy and apply the `@odata.nextLink` or `@odata.deltaLink` URL from the previous response, as that URL already includes the encoded, desired parameters.

| Query parameter | Type | Description |
| :--- | :--- | :--- |
| $deltatoken | string | A [state token](https://learn.microsoft.com/en-us/graph/delta-query-overview) returned in the `@odata.deltaLink` URL of the previous **delta** function call for the same calendar list, indicating the completion of that round of change tracking. Save and apply the entire `@odata.deltaLink` URL including this token in the first request of the next round of change tracking for that calendar list. |
| $skiptoken | string | A [state token](https://learn.microsoft.com/en-us/graph/delta-query-overview) returned in the `@odata.nextLink` URL of the previous **delta** function call, indicating there are further changes to be tracked in the same calendar list. |

### OData query parameters

This method supports optional OData query parameters to help customize the response.

- You can use a `$select` query parameter as in any GET request to specify only the properties your need for best performance.
- The **delta** function doesn't support the following query parameters: `$expand`, `$filter`,`$orderby`, `$search`, and `$select`.

## Request headers

| Name | Type | Description |
| :--- | :--- | :--- |
| Authorization | string | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | string | application/json. Required. |
| Prefer | string | odata.maxpagesize={x}. Optional. |

## Request body

Don't supply a request body for this method.

## Response

If successful, this function returns a `200 OK` response code and a [calendar](https://learn.microsoft.com/en-us/graph/api/resources/calendar?view=graph-rest-beta) collection in the response body.

## Examples

### Request

The following example shows a request. There's no `$select` parameter, so a default set of properties is tracked and returned.

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [PowerShell](#tabpanel_1_powershell)
- [Python](#tabpanel_1_python)

```msgraph
GET https://graph.microsoft.com/beta/me/calendars/delta
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Me.Calendars.Delta.GetAsDeltaGetResponseAsync();
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
delta, err := graphClient.Me().Calendars().Delta().GetAsDeltaGetResponse(context.Background(), nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

var result = graphClient.me().calendars().delta().get();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let delta = await client.api('/me/calendars/delta')
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


$result = $graphServiceClient->me()->calendars()->delta()->get()->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Beta.Calendar

# A UPN can also be used as -UserId.
Get-MgBetaUserCalendarDelta -UserId $userId
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python

result = await graph_client.me.calendars.delta.get()
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

If the request is successful, the response includes a state token, which is either a *skipToken* \(in an *@odata.nextLink* response header\) or a *deltaToken* \(in an *@odata.deltaLink* response header\). Respectively, they indicate whether you should continue with the round or you have completed getting all the changes for that round.

The response below shows a *deltaToken* in an *@odata.deltaLink* response header.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
    "@odata.context": "https://graph.microsoft.com/beta/$metadata#Collection(calendar)",
    "value": [
        {
            "@odata.type": "#microsoft.graph.calendar",
            "id": "AQMkADRhZThkMDVjLTJmNDctNDUyZC05YjA2LTI2YzRmMTIxOWJhZQBGAAADVDIMnvGkNkGo5_ASLe7iUQcAvXegGcyc-0O1dA1ftrtB6QAAAgEGAAAAvXegGcyc-0O1dA1ftrtB6QAAAUSwewAAAA==",
            "name": "Calendar",
            "color": "auto",
            "hexColor": "",
            "groupClassId": "0006f0b7-0000-0000-c000-000000000046",
            "isDefaultCalendar": true,
            "changeKey": "vXegGcyc/0O1dA1ftrtB6QAAAEO+6Q==",
            "canShare": true,
            "canViewPrivateItems": true,
            "isShared": false,
            "isSharedWithMe": false,
            "canEdit": true,
            "calendarGroupId": null,
            "allowedOnlineMeetingProviders": [
                "teamsForBusiness"
            ],
            "defaultOnlineMeetingProvider": "teamsForBusiness",
            "isTallyingResponses": true,
            "isRemovable": false,
            "owner": {
                "name": "Samantha Booth",
                "address": "samanthab@contoso.com"
            }
        },
        {
            "@odata.type": "#microsoft.graph.calendar",
            "id": "AQMkADRhZThkMDVjLTJmNDctNDUyZC05YjA2LTI2YzRmMTIxOWJhZQBGAAADVDIMnvGkNkGo5_ASLe7iUQcAvXegGcyc-0O1dA1ftrtB6QAAAgEGAAAAvXegGcyc-0O1dA1ftrtB6QAAAU4pOwAAAA==",
            "name": "Birthdays",
            "color": "auto",
            "hexColor": "",
            "groupClassId": "0006f0b7-0000-0000-c000-000000000046",
            "isDefaultCalendar": false,
            "changeKey": "vXegGcyc/0O1dA1ftrtB6QAAAEzvog==",
            "canShare": false,
            "canViewPrivateItems": true,
            "isShared": false,
            "isSharedWithMe": false,
            "canEdit": false,
            "calendarGroupId": null,
            "allowedOnlineMeetingProviders": [],
            "defaultOnlineMeetingProvider": "unknown",
            "isTallyingResponses": false,
            "isRemovable": true,
            "owner": {
                "name": "Samantha Booth",
                "address": "samanthab@contoso.com"
            }
        }
    ],
    "@odata.deltaLink": "https://graph.microsoft.com/beta/me/calendars/delta?$deltatoken=LztZwWjo5IivWBhyxw5rAIPrk_3pGHcZr4U33FHo0HpyBLqdo9QZIWfEL4AW1jMLBmo-o1ybmYCWlzQ5elO2bEDejh9Z8kYv_z4nhmHoC5Y.7Wdj3MWiils6M--JMM9dMyiLCh-1he4AZCqBu-8i42o"
}
```
