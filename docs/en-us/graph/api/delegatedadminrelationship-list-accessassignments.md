<!-- Source: https://learn.microsoft.com/en-us/graph/api/delegatedadminrelationship-list-accessassignments?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-23 -->

# List accessAssignments

Namespace: microsoft.graph

Get a list of the [delegatedAdminAccessAssignment](https://learn.microsoft.com/en-us/graph/api/resources/delegatedadminaccessassignment?view=graph-rest-1.0) objects and their properties.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | DelegatedAdminRelationship.Read.All | DelegatedAdminRelationship.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | DelegatedAdminRelationship.Read.All | DelegatedAdminRelationship.ReadWrite.All |

## HTTP request

```http
GET /tenantRelationships/delegatedAdminRelationships/{delegatedAdminRelationshipId}/accessAssignments
```

## Optional query parameters

This method supports the `$select`, `$filter`, `$top`, `$orderby`, `$count`, and `$skipToken` [OData query parameters](https://learn.microsoft.com/en-us/graph/query-parameters) to help customize the response.

`$top` supports up to 300 objects.

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and a collection of [delegatedAdminAccessAssignment](https://learn.microsoft.com/en-us/graph/api/resources/delegatedadminaccessassignment?view=graph-rest-1.0) objects in the response body.

Each **delegatedAdminAccessAssignment** object contains an **@odata.etag** property as per RFC2616.

## Examples

### Request

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [PowerShell](#tabpanel_1_powershell)
- [Python](#tabpanel_1_python)

```http
GET https://graph.microsoft.com/v1.0/tenantRelationships/delegatedAdminRelationships/72a7ae7e-4887-4e34-9755-2e1e9b26b943-63f017cb-9e0d-4f14-94bd-4871902b3409/accessAssignments
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.TenantRelationships.DelegatedAdminRelationships["{delegatedAdminRelationship-id}"].AccessAssignments.GetAsync();
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
accessAssignments, err := graphClient.TenantRelationships().DelegatedAdminRelationships().ByDelegatedAdminRelationshipId("delegatedAdminRelationship-id").AccessAssignments().Get(context.Background(), nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

DelegatedAdminAccessAssignmentCollectionResponse result = graphClient.tenantRelationships().delegatedAdminRelationships().byDelegatedAdminRelationshipId("{delegatedAdminRelationship-id}").accessAssignments().get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let accessAssignments = await client.api('/tenantRelationships/delegatedAdminRelationships/72a7ae7e-4887-4e34-9755-2e1e9b26b943-63f017cb-9e0d-4f14-94bd-4871902b3409/accessAssignments')
	.get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);


$result = $graphServiceClient->tenantRelationships()->delegatedAdminRelationships()->byDelegatedAdminRelationshipId('delegatedAdminRelationship-id')->accessAssignments()->get()->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Identity.Partner

Get-MgTenantRelationshipDelegatedAdminRelationshipAccessAssignment -DelegatedAdminRelationshipId $delegatedAdminRelationshipId
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python

result = await graph_client.tenant_relationships.delegated_admin_relationships.by_delegated_admin_relationship_id('delegatedAdminRelationship-id').access_assignments.get()
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "@odata.context": "https://graph.microsoft.com/v1.0/tenantRelationships/$metadata#accessAssignments",
  "value": [
    {
      "@odata.type": "#microsoft.graph.delegatedAdminAccessAssignment",
      "@odata.etag": "W/\"JyIwMDAwMDI5OC0wMDAwLTAyMDAtMDAwMC02MjJiZTA0YjAwMDAiJw==\"",
      "id": "84c586df-0943-416e-b95f-7289cb8d3bd5",
      "status": "active",
      "createdDateTime": "2022-03-07T22:55:18.6780449Z",
      "lastModifiedDateTime": "2022-03-11T23:50:35.8970153Z",
      "accessContainer": {
          "accessContainerId": "227a2f44-2682-4831-a021-f8d69a34bcba",
          "accessContainerType": "securityGroup"
      },
      "accessDetails": {
          "unifiedRoles": [
              {
                   "roleDefinitionId": "88d8e3e3-8f55-4a1e-953a-9b9898b8876b"
              },
              {
                  "roleDefinitionId": "44367163-eba1-44c3-98af-f5787879f96a"
              },
              {
                  "roleDefinitionId": "29232cdf-9323-42fd-ade2-1d097af3e4de"
              },
              {
                  "roleDefinitionId": "62e90394-69f5-4237-9190-012177145e10"
              }
          ]
      }
    },
    {
      "@odata.type": "#microsoft.graph.delegatedAdminAccessAssignment",
      "@odata.etag": "W/\"JyIwMDAwMjAwOC0wMDAwLTAyMDAtMDAwMC02MjJhYWQzYjAwMDAiJw==\"",
      "id": "8d56bce3-440f-4b4f-b5c2-cc0bcbd0199c",
      "status": "active",
      "createdDateTime": "2022-03-10T23:50:35.8970153Z",
      "lastModifiedDateTime": "2022-03-11T02:00:27.7912161Z",
      "accessContainer": {
          "accessContainerId": "869713c9-0b28-4d08-8949-ae07ae1bf528",
          "accessContainerType": "securityGroup"
      },
      "accessDetails": {
          "unifiedRoles": [
              {
                  "roleDefinitionId": "29232cdf-9323-42fd-ade2-1d097af3e4de"
              },
              {
                  "roleDefinitionId": "f2ef992c-3afb-46b9-b7cf-a126ee74c451"
              },
              {
                  "roleDefinitionId": "729827e3-9c14-49f7-bb1b-9608f156bbb8"
              },
              {
                  "roleDefinitionId": "3a2c62db-5318-420d-8d74-23affee5d9d5"
              }
          ]
      }
    }
  ]
}
```
