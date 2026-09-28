<!-- Source: https://learn.microsoft.com/en-us/graph/api/callrecords-callrecord-list-participants_v2?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-01-12 -->

# List participants\_v2

Namespace: microsoft.graph.callRecords

Get the list of [participant](https://learn.microsoft.com/en-us/graph/api/resources/callrecords-participant?view=graph-rest-1.0) objects associated with a [callRecord](https://learn.microsoft.com/en-us/graph/api/resources/callrecords-callrecord?view=graph-rest-1.0).

Note

A known issue related to missing participants is associated with this API. For details, see [Known issues](https://developer.microsoft.com/graph/known-issues?search=31852).

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
GET /communications/callRecords/{id}/participants_v2
```

## Optional query parameters

This method supports the following OData query parameter to help customize the response. For general information, see [OData query parameters](https://learn.microsoft.com/en-us/graph/query-parameters).

| Name | Description |
| :--- | :--- |
| $select | Use the `$select` query parameter to return a set of properties that are different than the default set for an individual resource or a collection of resources. |

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Prefer: odata.maxpagesize={x} | Specifies a preferred integer {x} page size for paginated results. This value must be equal to or less than the maximum allowable page size. Optional. |
| Prefer: include-unknown-enum-members | Enables evolvable enum values beyond the sentinel value. For more information, see [Best practices for working with Microsoft Graph](https://learn.microsoft.com/en-us/graph/best-practices-concept#handling-future-members-in-evolvable-enumerations). Optional. |
| Prefer: omit-values=nulls | Removes null or empty values from the response. Optional. |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and a collection of [microsoft.graph.callRecords.participant](https://learn.microsoft.com/en-us/graph/api/resources/callrecords-participant?view=graph-rest-1.0) objects in the response body.

When a result set spans multiple pages, Microsoft Graph returns that page with an **@odata.nextLink** property in the response that contains a URL to the next page of results. If that property is present, continue making additional requests with the **@odata.nextLink** URL in each response, until all the results are returned. For more information, see [Paging Microsoft Graph data in your app](https://learn.microsoft.com/en-us/graph/paging). The maximum page size for participants is 130 entries.

## Examples

### Request

The following example shows a request to get the list of [participant](https://learn.microsoft.com/en-us/graph/api/resources/callrecords-participant?view=graph-rest-1.0) objects for a [callRecord](https://learn.microsoft.com/en-us/graph/api/resources/callrecords-callrecord?view=graph-rest-1.0).

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [PowerShell](#tabpanel_1_powershell)
- [Python](#tabpanel_1_python)

```msgraph
GET https://graph.microsoft.com/v1.0/communications/callRecords/614e3ff0-4728-4394-8c03-52fb3b967fde/participants_v2
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Communications.CallRecords["{callRecord-id}"].Participants_v2.GetAsync();
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
participants_v2, err := graphClient.Communications().CallRecords().ByCallRecordId("callRecord-id").Participants_v2().Get(context.Background(), nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.models.callrecords.ParticipantCollectionResponse result = graphClient.communications().callRecords().byCallRecordId("{callRecord-id}").participantsV2().get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let participants_v2 = await client.api('/communications/callRecords/614e3ff0-4728-4394-8c03-52fb3b967fde/participants_v2')
	.get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);


$result = $graphServiceClient->communications()->callRecords()->byCallRecordId('callRecord-id')->participants_v2()->get()->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.CloudCommunications

Get-MgCommunicationCallRecordParticipantV2 -CallRecordId $callRecordId
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python

result = await graph_client.communications.call_records.by_call_record_id('callRecord-id').participants_v2.get()
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-type: application/json

{
  "@odata.context": "https://graph.microsoft.com/$metadata#communications/callRecords('614e3ff0-4728-4394-8c03-52fb3b967fde')/participants_v2",
  "@odata.nextLink": "https://graph.microsoft.com/v1.0/communications/callRecords/614e3ff0-4728-4394-8c03-52fb3b967fde/participants_v2",
  "value": [
    {
      "id": "00005994-851d-4988-bbc3-413bbf089e13",
      "identity": {
        "acsUser": null,
        "spoolUser": null,
        "phone": null,
        "guest": null,
        "encrypted": null,
        "onPremises": null,
        "acsApplicationInstance": null,
        "spoolApplicationInstance": null,
        "applicationInstance": null,
        "application": null,
        "device": null,
        "user": {
          "@odata.type": "#microsoft.graph.userIdentity",
          "id": "00005994-851d-4988-bbc3-413bbf089e13",
          "displayName": "Anette Thomsen",
          "tenantId": "dc368399-474c-4d40-900c-6265431fd81f",
          "userPrincipalName": "anette.thomsen@contoso.com"
        }
      }
    },
    {
      "id": "13fd6bf0-f646-4b82-b0ad-cd28ce10d6e3",
      "identity": {
        "acsUser": null,
        "spoolUser": null,
        "phone": null,
        "guest": null,
        "encrypted": null,
        "onPremises": null,
        "acsApplicationInstance": null,
        "spoolApplicationInstance": null,
        "applicationInstance": null,
        "application": null,
        "device": null,
        "user": {
          "@odata.type": "#microsoft.graph.userIdentity",
          "id": "13fd6bf0-f646-4b82-b0ad-cd28ce10d6e3",
          "displayName": "Daichi Maruyama",
          "tenantId": "dc368399-474c-4d40-900c-6265431fd81f",
          "userPrincipalName": "daichi.maruyama@contoso.com"
        }
      }
    }
  ]
}
```
