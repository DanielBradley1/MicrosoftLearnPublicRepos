<!-- Source: https://learn.microsoft.com/en-us/graph/api/insights-list-shared?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-02-06 -->

# List shared \(deprecated\)

Namespace: microsoft.graph

Caution

The `/insights/shared` API is deprecated and will stop returning data after November 2026.

Calculated insight that includes the list of documents shared with a user.

This insight includes documents hosted on OneDrive/SharePoint in the user's Microsoft 365 tenant that are shared with the user, and documents that are attached as files and sent to the user.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Sites.Read.All | Sites.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Not supported. | Not supported. |

## HTTP request

Get a list of documents shared with the signed-in user.

> **Note**: Only the user can make requests using the user's ID or principal name.

```http
GET /me/insights/shared
GET /users/{id | userPrincipalName}/insights/shared
```

Expand the resource referenced by a **shared** insight:

```http
GET /me/insights/shared/{id}/resource
```

## Optional query parameters

This method supports the [OData Query Parameters](https://learn.microsoft.com/en-us/graph/query-parameters) to help customize the response.

You can use the `$filter` query parameter to filter shared items. For example, based on **type**:

`https://graph.microsoft.com/v1.0/me/insights/shared?$filter=ResourceVisualization/Type eq 'PowerPoint'`

See the available container types and types you can filter by in [resourceVisualization](https://learn.microsoft.com/en-us/graph/api/resources/insights-resourcevisualization?view=graph-rest-1.0).

You can also retrieve files shared by a specific user. For example, by specifying the `lastshared/sharedby/address` property:

`https://graph.microsoft.com/v1.0/me/insights/shared?$filter=lastshared/sharedby/address eq 'kellygraham@contoso.com'`

See the [sharingDetail](https://learn.microsoft.com/en-us/graph/api/resources/insights-sharingdetail?view=graph-rest-1.0) complex type.

## Request headers

| Header | Value |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Accept | application/json |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and a list of [shared](https://learn.microsoft.com/en-us/graph/api/resources/insights-shared?view=graph-rest-1.0) items in the response body.

## Example

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
GET https://graph.microsoft.com/v1.0/me/insights/shared
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Me.Insights.Shared.GetAsync();
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
shared, err := graphClient.Me().Insights().Shared().Get(context.Background(), nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

SharedInsightCollectionResponse result = graphClient.me().insights().shared().get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let shared = await client.api('/me/insights/shared')
	.get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);


$result = $graphServiceClient->me()->insights()->shared()->get()->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Users

# A UPN can also be used as -UserId.
Get-MgUserInsightShared -UserId $userId
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python

result = await graph_client.me.insights.shared.get()
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-type: application/json

{
    "value": [
        {
            "id": "AWb0Qy4TEA1KhLW-k1L5mSjtxZAcxDFkTKiTNA-2kZDTXzrMX_4FhECOU0bKZVj1uReivYoYYoJNqTeuC-x1Agtm9EMuExANSoS1vpNS-ZkoBA",
            "lastShared": {
                "sharedDateTime": "2021-03-23T08:41:05Z",
                "sharingType": "Direct",
                "sharedBy": {
                    "displayName": "Megan Bowen",
                    "address": "MeganB@contoso.com",
                    "id": "3e0c9f05-b9b8-4cf5-9b35-a4e11b24b5b7"
                },
                "sharingReference": {}
            },
            "resourceVisualization": {
                "title": "CE Annual Report",
                "type": "Word",
                "mediaType": "application/vnd.openxmlformats-officedocument.wordprocessingml.document",
                "previewImageUrl": "https://contoso-my.sharepoint.com/_api/v2.0/drives/b!ZvRDLhMQDUqEtb6TUvmZKO3FkBzEMWRMqJM0D7aRkNNfOsxf_gWEQI5TRsplWPW5/items/01K6ZMU4QXUK6YUGDCQJG2SN5OBPWHKAQL/thumbnails/0/small/thumbnailContent",
                "previewText": "Contoso Annual Report Anne Wallace Sales Contoso today announced financial results for its most recent fi",
                "containerWebUrl": "https://contoso-my.sharepoint.com/personal/meganb_m365x841051_onmicrosoft_com/Documents/Forms/All.aspx",
                "containerDisplayName": "Megan Bowen",
                "containerType": "OneDriveBusiness"
            },
            "resourceReference": {
                "webUrl": "https://contoso-my.sharepoint.com/personal/meganb_m365x841051_onmicrosoft_com/_layouts/15/Doc.aspx?sourcedoc=%7B8ABDA217-6218-4D82-A937-AE0BEC75020B%7D&file=CE%20Annual%20Report.docx&action=default&mobileredirect=true&DefaultItemOpen=1",
                "id": "drives/b!ZvRDLhMQDUqEtb6TUvmZKO3FkBzEMWRMqJM0D7aRkNNfOsxf_gWEQI5TRsplWPW5/items/01K6ZMU4QXUK6YUGDCQJG2SN5OBPWHKAQL",
                "type": "microsoft.graph.driveItem"
            }
        }
    ]
}
```
