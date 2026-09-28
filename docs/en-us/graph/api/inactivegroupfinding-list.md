<!-- Source: https://learn.microsoft.com/en-us/graph/api/inactivegroupfinding-list?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-05-07 -->

# List inactiveGroupFinding objects

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Note

Effective April 1, 2025, Microsoft Entra Permissions Management will no longer be available for purchase, and on October 1, 2025, we'll retire and discontinue support of this product. More information can be found [here](https://aka.ms/MEPMretire).

Get a list of the [inactiveGroupFinding](https://learn.microsoft.com/en-us/graph/api/resources/inactivegroupfinding?view=graph-rest-beta) objects and their properties in AWS, Azure, and GCP environments.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Not supported. | Not supported. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | PermissionsAnalytics.Read.OwnedBy | Not available. |

## HTTP request

List AWS inactive groups:

```http
GET /identityGovernance/permissionsAnalytics/aws/findings/microsoft.graph.inactiveGroupFinding
```

List Azure inactive groups:

```http
GET /identityGovernance/permissionsAnalytics/azure/findings/microsoft.graph.inactiveGroupFinding
```

List GCP inactive groups:

```http
GET /identityGovernance/permissionsAnalytics/gcp/findings/microsoft.graph.inactiveGroupFinding
```

## Optional query parameters

This method supports the `$filter` and `$orderby` OData query parameters to help customize the response. For general information, see [OData query parameters](https://learn.microsoft.com/en-us/graph/query-parameters).

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and a collection of [inactiveGroupFinding](https://learn.microsoft.com/en-us/graph/api/resources/inactivegroupfinding?view=graph-rest-beta) objects in the response body.

## Examples

### Request

The following example shows a request to list GCP inactive groups.

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [PowerShell](#tabpanel_1_powershell)
- [Python](#tabpanel_1_python)

```msgraph
GET https://graph.microsoft.com/beta/identityGovernance/permissionsAnalytics/gcp/findings/microsoft.graph.inactiveGroupFinding
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.IdentityGovernance.PermissionsAnalytics.Gcp.Findings["{finding-id}"].GetAsync();
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
findings, err := graphClient.IdentityGovernance().PermissionsAnalytics().Gcp().Findings().ByFindingId("finding-id").Get(context.Background(), nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

Finding result = graphClient.identityGovernance().permissionsAnalytics().gcp().findings().byFindingId("{finding-id}").get();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let inactiveGroupFinding = await client.api('/identityGovernance/permissionsAnalytics/gcp/findings/microsoft.graph.inactiveGroupFinding')
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


$result = $graphServiceClient->identityGovernance()->permissionsAnalytics()->gcp()->findings()->byFindingId('finding-id')->get()->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Beta.Identity.Governance

Get-MgBetaIdentityGovernancePermissionAnalyticGcpFinding -FindingId $findingId
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python

result = await graph_client.identity_governance.permissions_analytics.gcp.findings.by_finding_id('finding-id').get()
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
    "@odata.context": "https://graph.microsoft.com/beta/$metadata#identityGovernance/permissionsAnalytics/gcp/findings/microsoft.graph.inactiveGroupFinding",
    "value": [
        {
            "id": "MSxJbmFjdGl2ZUdyb3VwRmluZGluZyw2MDI0NA",
            "createdDateTime": "2023-10-17T15:46:31.448597Z",
            "permissionsCreepIndex": {
                "score": 1
            },
            "actionSummary": {
                "assigned": 3011,
                "exercised": 0,
                "available": 7075
            },
            "group": {
                "@odata.type": "#microsoft.graph.gcpGroup",
                "id": "dGVzdGdyb3VwQGNsb3Vka25veC5pbw",
                "externalId": "testgroup@cloudknox.io",
                "displayName": "testgroup",
                "source": {
                    "@odata.type": "#microsoft.graph.gsuiteSource",
                    "identityProviderType": "gsuite",
                    "domain": "carbide-bonsai-205017"
                },
                "authorizationSystem": {
                    "@odata.type": "#microsoft.graph.gcpAuthorizationSystem",
                    "authorizationSystemId": "carbide-bonsai-205017",
                    "authorizationSystemName": "ck-staging",
                    "authorizationSystemType": "gcp",
                    "id": "MSxnY3AsY2FyYmlkZS1ib25zYWktMjA1MDE3"
                }
            }
        },
        {
            "id": "MSxJbmFjdGl2ZUdyb3VwRmluZGluZyw2MDI0NQ",
            "createdDateTime": "2023-10-17T15:46:31.448597Z",
            "permissionsCreepIndex": {
                "score": 1
            },
            "actionSummary": {
                "assigned": 3061,
                "exercised": 0,
                "available": 7075
            },
            "group": {
                "@odata.type": "#microsoft.graph.gcpGroup",
                "id": "ZW5naW5lZXJpbmdAY2xvdWRrbm94Lmlv",
                "externalId": "engineering@cloudknox.io",
                "displayName": "engineering",
                "source": {
                    "@odata.type": "#microsoft.graph.gsuiteSource",
                    "identityProviderType": "gsuite",
                    "domain": "carbide-bonsai-205017"
                },
                "authorizationSystem": {
                    "@odata.type": "#microsoft.graph.gcpAuthorizationSystem",
                    "authorizationSystemId": "carbide-bonsai-205017",
                    "authorizationSystemName": "ck-staging",
                    "authorizationSystemType": "gcp",
                    "id": "MSxnY3AsY2FyYmlkZS1ib25zYWktMjA1MDE3"
                }
            }
        }
    ]
}
```
