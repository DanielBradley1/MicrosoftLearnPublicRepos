<!-- Source: https://learn.microsoft.com/en-us/graph/api/delegatedadminrelationship-post-accessassignments?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-23 -->

# Create accessAssignments

Namespace: microsoft.graph

Create a new [delegatedAdminAccessAssignment](https://learn.microsoft.com/en-us/graph/api/resources/delegatedadminaccessassignment?view=graph-rest-1.0) object.

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

Important

To call this API using application permissions, you must provision the service principal identified by **appId** `2832473f-ec63-45fb-976f-5d45a7d4bb91` and named **Partner Customer Delegated Administration** in the partner tenant. To provision the service principal in the partner tenant, call the [Create servicePrincipal](https://learn.microsoft.com/en-us/graph/api/serviceprincipal-post-serviceprincipals) API.

## HTTP request

```http
POST /tenantRelationships/delegatedAdminRelationships/{delegatedAdminRelationshipId}/accessAssignments
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the [delegatedAdminAccessAssignment](https://learn.microsoft.com/en-us/graph/api/resources/delegatedadminaccessassignment?view=graph-rest-1.0) object.

You can specify the following properties when creating a **delegatedAdminAccessAssignment**.

| Property | Type | Description |
| :--- | :--- | :--- |
| accessContainer | [delegatedAdminAccessContainer](https://learn.microsoft.com/en-us/graph/api/resources/delegatedadminaccesscontainer?view=graph-rest-1.0) | The access container through which members are assigned access. For example, a security group. |
| accessDetails | [delegatedAdminAccessDetails](https://learn.microsoft.com/en-us/graph/api/resources/delegatedadminaccessdetails?view=graph-rest-1.0) | The identifiers of the administrative roles that the partner is assigned in the customer tenant. |

## Response

If successful, this method returns a `201 Created` response code and a [delegatedAdminAccessAssignment](https://learn.microsoft.com/en-us/graph/api/resources/delegatedadminaccessassignment?view=graph-rest-1.0) object in the response body. A **Location** header in the response points to the created **delegatedAdminAccessAssignment** object.

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
POST https://graph.microsoft.com/v1.0/tenantRelationships/delegatedAdminRelationships/72a7ae7e-4887-4e34-9755-2e1e9b26b943-63f017cb-9e0d-4f14-94bd-4871902b3409/accessAssignments
Content-Type: application/json

{
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
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new DelegatedAdminAccessAssignment
{
	AccessContainer = new DelegatedAdminAccessContainer
	{
		AccessContainerId = "869713c9-0b28-4d08-8949-ae07ae1bf528",
		AccessContainerType = DelegatedAdminAccessContainerType.SecurityGroup,
	},
	AccessDetails = new DelegatedAdminAccessDetails
	{
		UnifiedRoles = new List<UnifiedRole>
		{
			new UnifiedRole
			{
				RoleDefinitionId = "29232cdf-9323-42fd-ade2-1d097af3e4de",
			},
			new UnifiedRole
			{
				RoleDefinitionId = "f2ef992c-3afb-46b9-b7cf-a126ee74c451",
			},
			new UnifiedRole
			{
				RoleDefinitionId = "729827e3-9c14-49f7-bb1b-9608f156bbb8",
			},
			new UnifiedRole
			{
				RoleDefinitionId = "3a2c62db-5318-420d-8d74-23affee5d9d5",
			},
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.TenantRelationships.DelegatedAdminRelationships["{delegatedAdminRelationship-id}"].AccessAssignments.PostAsync(requestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphmodels "github.com/microsoftgraph/msgraph-sdk-go/models"
	  //other-imports
)

requestBody := graphmodels.NewDelegatedAdminAccessAssignment()
accessContainer := graphmodels.NewDelegatedAdminAccessContainer()
accessContainerId := "869713c9-0b28-4d08-8949-ae07ae1bf528"
accessContainer.SetAccessContainerId(&accessContainerId) 
accessContainerType := graphmodels.SECURITYGROUP_DELEGATEDADMINACCESSCONTAINERTYPE 
accessContainer.SetAccessContainerType(&accessContainerType) 
requestBody.SetAccessContainer(accessContainer)
accessDetails := graphmodels.NewDelegatedAdminAccessDetails()


unifiedRole := graphmodels.NewUnifiedRole()
roleDefinitionId := "29232cdf-9323-42fd-ade2-1d097af3e4de"
unifiedRole.SetRoleDefinitionId(&roleDefinitionId) 
unifiedRole1 := graphmodels.NewUnifiedRole()
roleDefinitionId := "f2ef992c-3afb-46b9-b7cf-a126ee74c451"
unifiedRole1.SetRoleDefinitionId(&roleDefinitionId) 
unifiedRole2 := graphmodels.NewUnifiedRole()
roleDefinitionId := "729827e3-9c14-49f7-bb1b-9608f156bbb8"
unifiedRole2.SetRoleDefinitionId(&roleDefinitionId) 
unifiedRole3 := graphmodels.NewUnifiedRole()
roleDefinitionId := "3a2c62db-5318-420d-8d74-23affee5d9d5"
unifiedRole3.SetRoleDefinitionId(&roleDefinitionId) 

unifiedRoles := []graphmodels.UnifiedRoleable {
	unifiedRole,
	unifiedRole1,
	unifiedRole2,
	unifiedRole3,
}
accessDetails.SetUnifiedRoles(unifiedRoles)
requestBody.SetAccessDetails(accessDetails)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
accessAssignments, err := graphClient.TenantRelationships().DelegatedAdminRelationships().ByDelegatedAdminRelationshipId("delegatedAdminRelationship-id").AccessAssignments().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

DelegatedAdminAccessAssignment delegatedAdminAccessAssignment = new DelegatedAdminAccessAssignment();
DelegatedAdminAccessContainer accessContainer = new DelegatedAdminAccessContainer();
accessContainer.setAccessContainerId("869713c9-0b28-4d08-8949-ae07ae1bf528");
accessContainer.setAccessContainerType(DelegatedAdminAccessContainerType.SecurityGroup);
delegatedAdminAccessAssignment.setAccessContainer(accessContainer);
DelegatedAdminAccessDetails accessDetails = new DelegatedAdminAccessDetails();
LinkedList<UnifiedRole> unifiedRoles = new LinkedList<UnifiedRole>();
UnifiedRole unifiedRole = new UnifiedRole();
unifiedRole.setRoleDefinitionId("29232cdf-9323-42fd-ade2-1d097af3e4de");
unifiedRoles.add(unifiedRole);
UnifiedRole unifiedRole1 = new UnifiedRole();
unifiedRole1.setRoleDefinitionId("f2ef992c-3afb-46b9-b7cf-a126ee74c451");
unifiedRoles.add(unifiedRole1);
UnifiedRole unifiedRole2 = new UnifiedRole();
unifiedRole2.setRoleDefinitionId("729827e3-9c14-49f7-bb1b-9608f156bbb8");
unifiedRoles.add(unifiedRole2);
UnifiedRole unifiedRole3 = new UnifiedRole();
unifiedRole3.setRoleDefinitionId("3a2c62db-5318-420d-8d74-23affee5d9d5");
unifiedRoles.add(unifiedRole3);
accessDetails.setUnifiedRoles(unifiedRoles);
delegatedAdminAccessAssignment.setAccessDetails(accessDetails);
DelegatedAdminAccessAssignment result = graphClient.tenantRelationships().delegatedAdminRelationships().byDelegatedAdminRelationshipId("{delegatedAdminRelationship-id}").accessAssignments().post(delegatedAdminAccessAssignment);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const delegatedAdminAccessAssignment = {
  accessContainer: {
    accessContainerId: '869713c9-0b28-4d08-8949-ae07ae1bf528',
    accessContainerType: 'securityGroup'
  },
  accessDetails: {
    unifiedRoles: [
      {
        roleDefinitionId: '29232cdf-9323-42fd-ade2-1d097af3e4de'
      },
      {
        roleDefinitionId: 'f2ef992c-3afb-46b9-b7cf-a126ee74c451'
      },
      {
        roleDefinitionId: '729827e3-9c14-49f7-bb1b-9608f156bbb8'
      },
      {
        roleDefinitionId: '3a2c62db-5318-420d-8d74-23affee5d9d5'
      }
    ]
  }
};

await client.api('/tenantRelationships/delegatedAdminRelationships/72a7ae7e-4887-4e34-9755-2e1e9b26b943-63f017cb-9e0d-4f14-94bd-4871902b3409/accessAssignments')
	.post(delegatedAdminAccessAssignment);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\DelegatedAdminAccessAssignment;
use Microsoft\Graph\Generated\Models\DelegatedAdminAccessContainer;
use Microsoft\Graph\Generated\Models\DelegatedAdminAccessContainerType;
use Microsoft\Graph\Generated\Models\DelegatedAdminAccessDetails;
use Microsoft\Graph\Generated\Models\UnifiedRole;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new DelegatedAdminAccessAssignment();
$accessContainer = new DelegatedAdminAccessContainer();
$accessContainer->setAccessContainerId('869713c9-0b28-4d08-8949-ae07ae1bf528');
$accessContainer->setAccessContainerType(new DelegatedAdminAccessContainerType('securityGroup'));
$requestBody->setAccessContainer($accessContainer);
$accessDetails = new DelegatedAdminAccessDetails();
$unifiedRolesUnifiedRole1 = new UnifiedRole();
$unifiedRolesUnifiedRole1->setRoleDefinitionId('29232cdf-9323-42fd-ade2-1d097af3e4de');
$unifiedRolesArray []= $unifiedRolesUnifiedRole1;
$unifiedRolesUnifiedRole2 = new UnifiedRole();
$unifiedRolesUnifiedRole2->setRoleDefinitionId('f2ef992c-3afb-46b9-b7cf-a126ee74c451');
$unifiedRolesArray []= $unifiedRolesUnifiedRole2;
$unifiedRolesUnifiedRole3 = new UnifiedRole();
$unifiedRolesUnifiedRole3->setRoleDefinitionId('729827e3-9c14-49f7-bb1b-9608f156bbb8');
$unifiedRolesArray []= $unifiedRolesUnifiedRole3;
$unifiedRolesUnifiedRole4 = new UnifiedRole();
$unifiedRolesUnifiedRole4->setRoleDefinitionId('3a2c62db-5318-420d-8d74-23affee5d9d5');
$unifiedRolesArray []= $unifiedRolesUnifiedRole4;
$accessDetails->setUnifiedRoles($unifiedRolesArray);

$requestBody->setAccessDetails($accessDetails);

$result = $graphServiceClient->tenantRelationships()->delegatedAdminRelationships()->byDelegatedAdminRelationshipId('delegatedAdminRelationship-id')->accessAssignments()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Identity.Partner

$params = @{
	accessContainer = @{
		accessContainerId = "869713c9-0b28-4d08-8949-ae07ae1bf528"
		accessContainerType = "securityGroup"
	}
	accessDetails = @{
		unifiedRoles = @(
			@{
				roleDefinitionId = "29232cdf-9323-42fd-ade2-1d097af3e4de"
			}
			@{
				roleDefinitionId = "f2ef992c-3afb-46b9-b7cf-a126ee74c451"
			}
			@{
				roleDefinitionId = "729827e3-9c14-49f7-bb1b-9608f156bbb8"
			}
			@{
				roleDefinitionId = "3a2c62db-5318-420d-8d74-23affee5d9d5"
			}
		)
	}
}

New-MgTenantRelationshipDelegatedAdminRelationshipAccessAssignment -DelegatedAdminRelationshipId $delegatedAdminRelationshipId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.delegated_admin_access_assignment import DelegatedAdminAccessAssignment
from msgraph.generated.models.delegated_admin_access_container import DelegatedAdminAccessContainer
from msgraph.generated.models.delegated_admin_access_container_type import DelegatedAdminAccessContainerType
from msgraph.generated.models.delegated_admin_access_details import DelegatedAdminAccessDetails
from msgraph.generated.models.unified_role import UnifiedRole
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = DelegatedAdminAccessAssignment(
	access_container = DelegatedAdminAccessContainer(
		access_container_id = "869713c9-0b28-4d08-8949-ae07ae1bf528",
		access_container_type = DelegatedAdminAccessContainerType.SecurityGroup,
	),
	access_details = DelegatedAdminAccessDetails(
		unified_roles = [
			UnifiedRole(
				role_definition_id = "29232cdf-9323-42fd-ade2-1d097af3e4de",
			),
			UnifiedRole(
				role_definition_id = "f2ef992c-3afb-46b9-b7cf-a126ee74c451",
			),
			UnifiedRole(
				role_definition_id = "729827e3-9c14-49f7-bb1b-9608f156bbb8",
			),
			UnifiedRole(
				role_definition_id = "3a2c62db-5318-420d-8d74-23affee5d9d5",
			),
		],
	),
)

result = await graph_client.tenant_relationships.delegated_admin_relationships.by_delegated_admin_relationship_id('delegatedAdminRelationship-id').access_assignments.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

```http
HTTP/1.1 201 Created
Content-Type: application/json
Location: https://graph.microsoft.com/v1.0/tenantRelationships/delegatedAdminRelationships/72a7ae7e-4887-4e34-9755-2e1e9b26b943-63f017cb-9e0d-4f14-94bd-4871902b3409/accessAssignments/a9d6cf90-083a-47dc-ace2-1da98be3f344

{

  "@odata.type": "#microsoft.graph.delegatedAdminAccessAssignment",
  "@odata.context": "https://graph.microsoft.com/v1.0/tenantRelationships/$metadata#accessAssignments",
  "@odata.etag": "W/\"JyIxODAwZTY4My0wMDAwLTAyMDAtMDAwMC02MTU0OWFmMDAwMDAiJw==\"",
  "id": "a9d6cf90-083a-47dc-ace2-1da98be3f344",
  "status": "pending",
  "createdDateTime": "2022-02-13T10:33:52.3182097Z",
  "lastModifiedDateTime": "2022-02-13T10:33:52.3182097Z",
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
```
