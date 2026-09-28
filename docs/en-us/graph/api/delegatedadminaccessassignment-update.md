<!-- Source: https://learn.microsoft.com/en-us/graph/api/delegatedadminaccessassignment-update?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-04-05 -->

# Update delegatedAdminAccessAssignment

Namespace: microsoft.graph

Update the properties of a [delegatedAdminAccessAssignment](https://learn.microsoft.com/en-us/graph/api/resources/delegatedadminaccessassignment?view=graph-rest-1.0) object.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | DelegatedAdminRelationship.ReadWrite.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | DelegatedAdminRelationship.ReadWrite.All | Not available. |

## HTTP request

```http
PATCH /tenantRelationships/delegatedAdminRelationships/{delegatedAdminRelationshipId}/accessAssignments/{delegatedAdminAccessAssignmentId}
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| If-Match | If-match: etag}. Last known ETag value for the **delegatedAdminAccessAssignment** to be updated. Required. |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply *only* the values for properties to update. Existing properties that aren't included in the request body maintain their previous values or are recalculated based on changes to other property values.

The following table specifies the properties that can be updated.

| Property | Type | Description |
| :--- | :--- | :--- |
| accessDetails | [delegatedAdminAccessDetails](https://learn.microsoft.com/en-us/graph/api/resources/delegatedadminaccessdetails?view=graph-rest-1.0) | The identifiers of the administrative roles that the partner is assigned in the customer tenant |

## Response

If successful, this method returns a `200 OK` or a `202 Accepted` response code.

### Response headers

| Name | Description |
| :--- | :--- |
| Content-Type | application/json. |
| Location | The location of the long-running operation. |
| Retry-After | The time after which a subsequent API call can be made to the Location URL to check the status of the long-running operation. |

This method typically returns a `202 Accepted` response code with a URL to a long-running operation in the **Location** response header that can be monitored for completion. If the values specified in the call are identical to the values in the existing object, the API returns a `200 OK` response code with the original [delegatedAdminAccessAssignment](https://learn.microsoft.com/en-us/graph/api/resources/delegatedadminaccessassignment?view=graph-rest-1.0) object in the response body.

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
PATCH https://graph.microsoft.com/v1.0/tenantRelationships/delegatedAdminRelationships/5e5594d3-6f82-458b-b567-77db4811f0cd-00000000-0000-0000-0000-000000001234/accessAssignments/da9d6cf90-083a-47dc-ace2-1da98be3f344
If-Match: W/"JyI0NzAwNjg0NS0wMDAwLTE5MDAtMDAwMC02MGY0Yjg4MzAwMDAiJw=="
Content-Type: application/json

{
  "accessDetails": {
    "unifiedRoles": [
      {
        "roleDefinitionId": "88d8e3e3-8f55-4a1e-953a-9b9898b8876b"
      },
      {
        "roleDefinitionId": "44367163-eba1-44c3-98af-f5787879f96a"
      },
      {
        "roleDefinitionId": "729827e3-9c14-49f7-bb1b-9608f156bbb8"
      }
    ]
  }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new DelegatedAdminAccessAssignment
{
	AccessDetails = new DelegatedAdminAccessDetails
	{
		UnifiedRoles = new List<UnifiedRole>
		{
			new UnifiedRole
			{
				RoleDefinitionId = "88d8e3e3-8f55-4a1e-953a-9b9898b8876b",
			},
			new UnifiedRole
			{
				RoleDefinitionId = "44367163-eba1-44c3-98af-f5787879f96a",
			},
			new UnifiedRole
			{
				RoleDefinitionId = "729827e3-9c14-49f7-bb1b-9608f156bbb8",
			},
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.TenantRelationships.DelegatedAdminRelationships["{delegatedAdminRelationship-id}"].AccessAssignments["{delegatedAdminAccessAssignment-id}"].PatchAsync(requestBody, (requestConfiguration) =>
{
	requestConfiguration.Headers.Add("If-Match", "W/\"JyI0NzAwNjg0NS0wMDAwLTE5MDAtMDAwMC02MGY0Yjg4MzAwMDAiJw==\"");
});
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  abstractions "github.com/microsoft/kiota-abstractions-go"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphmodels "github.com/microsoftgraph/msgraph-sdk-go/models"
	  graphtenantrelationships "github.com/microsoftgraph/msgraph-sdk-go/tenantrelationships"
	  //other-imports
)

headers := abstractions.NewRequestHeaders()
headers.Add("If-Match", "W/\"JyI0NzAwNjg0NS0wMDAwLTE5MDAtMDAwMC02MGY0Yjg4MzAwMDAiJw==\"")

configuration := &graphtenantrelationships.DelegatedAdminRelationshipsItemAccessAssignmentsItemRequestBuilderPatchRequestConfiguration{
	Headers: headers,
}
requestBody := graphmodels.NewDelegatedAdminAccessAssignment()
accessDetails := graphmodels.NewDelegatedAdminAccessDetails()


unifiedRole := graphmodels.NewUnifiedRole()
roleDefinitionId := "88d8e3e3-8f55-4a1e-953a-9b9898b8876b"
unifiedRole.SetRoleDefinitionId(&roleDefinitionId) 
unifiedRole1 := graphmodels.NewUnifiedRole()
roleDefinitionId := "44367163-eba1-44c3-98af-f5787879f96a"
unifiedRole1.SetRoleDefinitionId(&roleDefinitionId) 
unifiedRole2 := graphmodels.NewUnifiedRole()
roleDefinitionId := "729827e3-9c14-49f7-bb1b-9608f156bbb8"
unifiedRole2.SetRoleDefinitionId(&roleDefinitionId) 

unifiedRoles := []graphmodels.UnifiedRoleable {
	unifiedRole,
	unifiedRole1,
	unifiedRole2,
}
accessDetails.SetUnifiedRoles(unifiedRoles)
requestBody.SetAccessDetails(accessDetails)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
accessAssignments, err := graphClient.TenantRelationships().DelegatedAdminRelationships().ByDelegatedAdminRelationshipId("delegatedAdminRelationship-id").AccessAssignments().ByDelegatedAdminAccessAssignmentId("delegatedAdminAccessAssignment-id").Patch(context.Background(), requestBody, configuration)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

DelegatedAdminAccessAssignment delegatedAdminAccessAssignment = new DelegatedAdminAccessAssignment();
DelegatedAdminAccessDetails accessDetails = new DelegatedAdminAccessDetails();
LinkedList<UnifiedRole> unifiedRoles = new LinkedList<UnifiedRole>();
UnifiedRole unifiedRole = new UnifiedRole();
unifiedRole.setRoleDefinitionId("88d8e3e3-8f55-4a1e-953a-9b9898b8876b");
unifiedRoles.add(unifiedRole);
UnifiedRole unifiedRole1 = new UnifiedRole();
unifiedRole1.setRoleDefinitionId("44367163-eba1-44c3-98af-f5787879f96a");
unifiedRoles.add(unifiedRole1);
UnifiedRole unifiedRole2 = new UnifiedRole();
unifiedRole2.setRoleDefinitionId("729827e3-9c14-49f7-bb1b-9608f156bbb8");
unifiedRoles.add(unifiedRole2);
accessDetails.setUnifiedRoles(unifiedRoles);
delegatedAdminAccessAssignment.setAccessDetails(accessDetails);
DelegatedAdminAccessAssignment result = graphClient.tenantRelationships().delegatedAdminRelationships().byDelegatedAdminRelationshipId("{delegatedAdminRelationship-id}").accessAssignments().byDelegatedAdminAccessAssignmentId("{delegatedAdminAccessAssignment-id}").patch(delegatedAdminAccessAssignment, requestConfiguration -> {
	requestConfiguration.headers.add("If-Match", "W/\"JyI0NzAwNjg0NS0wMDAwLTE5MDAtMDAwMC02MGY0Yjg4MzAwMDAiJw==\"");
});
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const delegatedAdminAccessAssignment = {
  accessDetails: {
    unifiedRoles: [
      {
        roleDefinitionId: '88d8e3e3-8f55-4a1e-953a-9b9898b8876b'
      },
      {
        roleDefinitionId: '44367163-eba1-44c3-98af-f5787879f96a'
      },
      {
        roleDefinitionId: '729827e3-9c14-49f7-bb1b-9608f156bbb8'
      }
    ]
  }
};

await client.api('/tenantRelationships/delegatedAdminRelationships/5e5594d3-6f82-458b-b567-77db4811f0cd-00000000-0000-0000-0000-000000001234/accessAssignments/da9d6cf90-083a-47dc-ace2-1da98be3f344')
	.update(delegatedAdminAccessAssignment);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\TenantRelationships\DelegatedAdminRelationships\Item\AccessAssignments\Item\DelegatedAdminAccessAssignmentItemRequestBuilderPatchRequestConfiguration;
use Microsoft\Graph\Generated\Models\DelegatedAdminAccessAssignment;
use Microsoft\Graph\Generated\Models\DelegatedAdminAccessDetails;
use Microsoft\Graph\Generated\Models\UnifiedRole;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new DelegatedAdminAccessAssignment();
$accessDetails = new DelegatedAdminAccessDetails();
$unifiedRolesUnifiedRole1 = new UnifiedRole();
$unifiedRolesUnifiedRole1->setRoleDefinitionId('88d8e3e3-8f55-4a1e-953a-9b9898b8876b');
$unifiedRolesArray []= $unifiedRolesUnifiedRole1;
$unifiedRolesUnifiedRole2 = new UnifiedRole();
$unifiedRolesUnifiedRole2->setRoleDefinitionId('44367163-eba1-44c3-98af-f5787879f96a');
$unifiedRolesArray []= $unifiedRolesUnifiedRole2;
$unifiedRolesUnifiedRole3 = new UnifiedRole();
$unifiedRolesUnifiedRole3->setRoleDefinitionId('729827e3-9c14-49f7-bb1b-9608f156bbb8');
$unifiedRolesArray []= $unifiedRolesUnifiedRole3;
$accessDetails->setUnifiedRoles($unifiedRolesArray);

$requestBody->setAccessDetails($accessDetails);
$requestConfiguration = new DelegatedAdminAccessAssignmentItemRequestBuilderPatchRequestConfiguration();
$headers = [
	'If-Match' => 'W/"JyI0NzAwNjg0NS0wMDAwLTE5MDAtMDAwMC02MGY0Yjg4MzAwMDAiJw=="',
];
$requestConfiguration->headers = $headers;


$result = $graphServiceClient->tenantRelationships()->delegatedAdminRelationships()->byDelegatedAdminRelationshipId('delegatedAdminRelationship-id')->accessAssignments()->byDelegatedAdminAccessAssignmentId('delegatedAdminAccessAssignment-id')->patch($requestBody, $requestConfiguration)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Identity.Partner

$params = @{
	accessDetails = @{
		unifiedRoles = @(
			@{
				roleDefinitionId = "88d8e3e3-8f55-4a1e-953a-9b9898b8876b"
			}
			@{
				roleDefinitionId = "44367163-eba1-44c3-98af-f5787879f96a"
			}
			@{
				roleDefinitionId = "729827e3-9c14-49f7-bb1b-9608f156bbb8"
			}
		)
	}
}

Update-MgTenantRelationshipDelegatedAdminRelationshipAccessAssignment -DelegatedAdminRelationshipId $delegatedAdminRelationshipId -DelegatedAdminAccessAssignmentId $delegatedAdminAccessAssignmentId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.tenant_relationships.delegated_admin_relationships.item.access_assignments.item.delegated_admin_access_assignment_item_request_builder import DelegatedAdminAccessAssignmentItemRequestBuilder
from kiota_abstractions.base_request_configuration import RequestConfiguration
from msgraph.generated.models.delegated_admin_access_assignment import DelegatedAdminAccessAssignment
from msgraph.generated.models.delegated_admin_access_details import DelegatedAdminAccessDetails
from msgraph.generated.models.unified_role import UnifiedRole
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = DelegatedAdminAccessAssignment(
	access_details = DelegatedAdminAccessDetails(
		unified_roles = [
			UnifiedRole(
				role_definition_id = "88d8e3e3-8f55-4a1e-953a-9b9898b8876b",
			),
			UnifiedRole(
				role_definition_id = "44367163-eba1-44c3-98af-f5787879f96a",
			),
			UnifiedRole(
				role_definition_id = "729827e3-9c14-49f7-bb1b-9608f156bbb8",
			),
		],
	),
)

request_configuration = RequestConfiguration()
request_configuration.headers.add("If-Match", "W/\"JyI0NzAwNjg0NS0wMDAwLTE5MDAtMDAwMC02MGY0Yjg4MzAwMDAiJw==\"")


result = await graph_client.tenant_relationships.delegated_admin_relationships.by_delegated_admin_relationship_id('delegatedAdminRelationship-id').access_assignments.by_delegated_admin_access_assignment_id('delegatedAdminAccessAssignment-id').patch(request_body, request_configuration = request_configuration)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following is an example response that returns a `202 Accepted` response code along with **Location** and **Retry-After** headers.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 202 Accepted
Location: https://graph.microsoft.com/v1.0/tenantRelationships/delegatedAdminRelationships/5e5594d3-6f82-458b-b567-77db4811f0cd-00000000-0000-0000-0000-000000001234/operations/d8dbb27b-7fe7-4523-a3df-f766355fe0f2
Retry-After: 10
Content-Type: application/json

{
}
```
