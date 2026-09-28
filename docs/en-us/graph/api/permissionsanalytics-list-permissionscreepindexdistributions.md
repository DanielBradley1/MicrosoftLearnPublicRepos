<!-- Source: https://learn.microsoft.com/en-us/graph/api/permissionsanalytics-list-permissionscreepindexdistributions?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-05-07 -->

# List permissionsCreepIndexDistributions

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Note

Effective April 1, 2025, Microsoft Entra Permissions Management will no longer be available for purchase, and on October 1, 2025, we'll retire and discontinue support of this product. More information can be found [here](https://aka.ms/MEPMretire).

Get a list of the [permissionsCreepIndexDistribution](https://learn.microsoft.com/en-us/graph/api/resources/permissionscreepindexdistribution?view=graph-rest-beta) objects and their properties.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Not supported. | Not supported. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Not supported. | Not supported. |

## HTTP request

List the Permissions Creep Index distribution for identities and resources in AWS:

```http
GET /identityGovernance/permissionsAnalytics/aws/permissionsCreepIndexDistributions
```

List the Permissions Creep Index distribution for identities and resources in Azure:

```http
GET /identityGovernance/permissionsAnalytics/azure/permissionsCreepIndexDistributions
```

List the Permissions Creep Index distribution for identities and resources in GCP:

```http
GET /identityGovernance/permissionsAnalytics/gcp/permissionsCreepIndexDistributions
```

## Optional query parameters

This method supports some of the OData query parameters to help customize the response. For general information, see [OData query parameters](https://learn.microsoft.com/en-us/graph/query-parameters).

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and a collection of [permissionsCreepIndexDistribution](https://learn.microsoft.com/en-us/graph/api/resources/permissionscreepindexdistribution?view=graph-rest-beta) objects in the response body.

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
GET https://graph.microsoft.com/beta/identityGovernance/permissionsAnalytics/aws/permissionsCreepIndexDistributions
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.IdentityGovernance.PermissionsAnalytics.Aws.PermissionsCreepIndexDistributions.GetAsync();
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
permissionsCreepIndexDistributions, err := graphClient.IdentityGovernance().PermissionsAnalytics().Aws().PermissionsCreepIndexDistributions().Get(context.Background(), nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

PermissionsCreepIndexDistributionCollectionResponse result = graphClient.identityGovernance().permissionsAnalytics().aws().permissionsCreepIndexDistributions().get();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let permissionsCreepIndexDistributions = await client.api('/identityGovernance/permissionsAnalytics/aws/permissionsCreepIndexDistributions')
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


$result = $graphServiceClient->identityGovernance()->permissionsAnalytics()->aws()->permissionsCreepIndexDistributions()->get()->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Beta.Identity.Governance

Get-MgBetaIdentityGovernancePermissionAnalyticAwPermissionCreepIndexDistribution
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python

result = await graph_client.identity_governance.permissions_analytics.aws.permissions_creep_index_distributions.get()
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
    "@odata.context": "https://graph.microsoft.com/beta/$metadata#identityGovernance/permissionsAnalytics/aws/permissionsCreepIndexDistributions",
    "value": [
        {
            "id": "MSxQZXJtaXNzaW9uc0NyZWVwSW5kZXhEaXN0cmlidXRpb24sMjM4MTcxLTIzODE3Mi0yMzgxNzM",
            "createdDateTime": "2023-11-08T22:31:11.518839Z",
            "lowRiskProfile": {
                "humanCount": 30,
                "nonHumanCount": 187
            },
            "mediumRiskProfile": {
                "humanCount": 0,
                "nonHumanCount": 0
            },
            "highRiskProfile": {
                "humanCount": 35,
                "nonHumanCount": 14
            },
            "authorizationSystem": {
                "authorizationSystemId": "377596131774",
                "authorizationSystemName": "cloudknox-staging",
                "authorizationSystemType": "Aws",
                "id": "MSxBd3MsMzc3NTk2MTMxNzc0"
            }
        },
        {
            "id": "MSxQZXJtaXNzaW9uc0NyZWVwSW5kZXhEaXN0cmlidXRpb24sMTA4MzEzLTEwODMxNC0xMDgzMTU",
            "createdDateTime": "2023-01-12T19:59:04.087998Z",
            "lowRiskProfile": {
                "humanCount": 4,
                "nonHumanCount": 51
            },
            "mediumRiskProfile": {
                "humanCount": 0,
                "nonHumanCount": 0
            },
            "highRiskProfile": {
                "humanCount": 0,
                "nonHumanCount": 1
            },
            "authorizationSystem": {
                "authorizationSystemId": "912000090514",
                "authorizationSystemName": "ck-test-stack",
                "authorizationSystemType": "Aws",
                "id": "MSxBd3MsOTEyMDAwMDkwNTE0"
            }
        },
        {
            "id": "MSxQZXJtaXNzaW9uc0NyZWVwSW5kZXhEaXN0cmlidXRpb24sMjM4MDgxLTIzODA4Mi0yMzgwODM",
            "createdDateTime": "2023-11-08T20:01:53.554943Z",
            "lowRiskProfile": {
                "humanCount": 9,
                "nonHumanCount": 164
            },
            "mediumRiskProfile": {
                "humanCount": 0,
                "nonHumanCount": 0
            },
            "highRiskProfile": {
                "humanCount": 19,
                "nonHumanCount": 11
            },
            "authorizationSystem": {
                "authorizationSystemId": "956987887735",
                "authorizationSystemName": "956987887735",
                "authorizationSystemType": "Aws",
                "id": "MSxBd3MsOTU2OTg3ODg3NzM1"
            }
        }
    ]
}
```
