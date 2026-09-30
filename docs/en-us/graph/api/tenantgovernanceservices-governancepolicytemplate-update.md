<!-- Source: https://learn.microsoft.com/en-us/graph/api/tenantgovernanceservices-governancepolicytemplate-update?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-04-15 -->

# Update tenantGovernancePolicyTemplate

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Update the properties of a [tenantGovernancePolicyTemplate](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-tenantgovernancepolicytemplate?view=graph-rest-beta) object.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | TenantGovernance-PolicyTemplate.ReadWrite.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Not supported. | Not supported. |

Important

For delegated access using work or school accounts, the signed-in user must be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json). The following least privileged roles are supported for this operation.

- Tenant Governance Administrator
- Tenant Governance Relationship Administrator

## HTTP request

```http
PATCH /directory/tenantGovernance/governancePolicyTemplates/{governancePolicyTemplateId}
PATCH /directory/tenantGovernance/governancePolicyTemplates/default
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply *only* the values for properties to update. Existing properties that aren't included in the request body maintain their previous values or are recalculated based on changes to other property values.

The following table specifies the properties that can be updated.

| Property | Type | Description |
| :--- | :--- | :--- |
| displayName | String | The display name of the policy template. |
| description | String | A description of the policy template. |
| multiTenantApplicationsToProvision | [microsoft.graph.multiTenantApplicationsToProvision](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-multitenantapplicationstoprovision?view=graph-rest-beta) collection | A collection of multitenant applications to be provisioned in the governed tenant when the governance relationship is established. |
| delegatedAdministrationRoleAssignments | [microsoft.graph.delegatedAdministrationRoleAssignment](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-delegatedadministrationroleassignment?view=graph-rest-beta) collection | A collection of delegated administration role assignments to be applied in the governed tenant when the governance relationship is established. |

## Response

If successful, this method returns a `200 OK` response code and an updated [microsoft.graph.tenantGovernancePolicyTemplate](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-tenantgovernancepolicytemplate?view=graph-rest-beta) object in the response body.

## Examples

### Example 1: Update a custom governance policy template

#### Request

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
PATCH https://graph.microsoft.com/beta/directory/tenantGovernance/governancePolicyTemplates/aaaaaaaa-0000-1111-2222-bbbbbbbbbbbb
Content-Type: application/json

{
  "multiTenantApplicationsToProvision": [
    {
        "appId": "66667777-aaaa-8888-bbbb-9999cccc0000",
        "objectId": "cccccccc-2222-3333-4444-dddddddddddd",
        "displayName": "Mega Monitor",
        "requiredResourceAccesses": [
            {
              "resourceAppId": "00000003-0000-0000-c000-000000000000",
              "permissions": [
              {
                "id": "633e0fce-8c58-4cfb-9495-12bbd5a24f7c",
                "name": "Policy.Read.ConditionalAccess",
                "type": "scope"
              },
              {
                "id": "e1fe6dd8-ba31-4d61-89e7-88639da4683d",
                "name": "User.Read",
                "type": "scope"
              }
              ]
            }
        ]
    }
  ],
  "delegatedAdministrationRoleAssignments": [
    {
        "roleTemplates": [
            {
                "id": "f2ef992c-3afb-46b9-b7cf-a126ee74c451",
                "name": "Global Reader"
            }
        ],
        "group": {
            "id": "ffffffff-5555-6666-7777-aaaaaaaaaaaa"
        }
    }
  ]
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.Models;

var requestBody = new TenantGovernancePolicyTemplate
{
	MultiTenantApplicationsToProvision = new List<MultiTenantApplicationsToProvision>
	{
		new MultiTenantApplicationsToProvision
		{
			AppId = "66667777-aaaa-8888-bbbb-9999cccc0000",
			ObjectId = "cccccccc-2222-3333-4444-dddddddddddd",
			DisplayName = "Mega Monitor",
			RequiredResourceAccesses = new List<ApplicationsRequiredResourceAccess>
			{
				new ApplicationsRequiredResourceAccess
				{
					ResourceAppId = "00000003-0000-0000-c000-000000000000",
					Permissions = new List<ApplicationResourcePermission>
					{
						new ApplicationResourcePermission
						{
							Id = "633e0fce-8c58-4cfb-9495-12bbd5a24f7c",
							Name = "Policy.Read.ConditionalAccess",
							Type = ApplicationPermissionType.Scope,
						},
						new ApplicationResourcePermission
						{
							Id = "e1fe6dd8-ba31-4d61-89e7-88639da4683d",
							Name = "User.Read",
							Type = ApplicationPermissionType.Scope,
						},
					},
				},
			},
		},
	},
	DelegatedAdministrationRoleAssignments = new List<DelegatedAdministrationRoleAssignment>
	{
		new DelegatedAdministrationRoleAssignment
		{
			RoleTemplates = new List<RoleTemplate>
			{
				new RoleTemplate
				{
					Id = "f2ef992c-3afb-46b9-b7cf-a126ee74c451",
					Name = "Global Reader",
				},
			},
			Group = new Group
			{
				Id = "ffffffff-5555-6666-7777-aaaaaaaaaaaa",
			},
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Directory.TenantGovernance.GovernancePolicyTemplates["{tenantGovernancePolicyTemplate-id}"].PatchAsync(requestBody);
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
	  graphmodels "github.com/microsoftgraph/msgraph-beta-sdk-go/models"
	  //other-imports
)

requestBody := graphmodels.NewTenantGovernancePolicyTemplate()


multiTenantApplicationsToProvision := graphmodels.NewMultiTenantApplicationsToProvision()
appId := "66667777-aaaa-8888-bbbb-9999cccc0000"
multiTenantApplicationsToProvision.SetAppId(&appId) 
objectId := "cccccccc-2222-3333-4444-dddddddddddd"
multiTenantApplicationsToProvision.SetObjectId(&objectId) 
displayName := "Mega Monitor"
multiTenantApplicationsToProvision.SetDisplayName(&displayName) 


applicationsRequiredResourceAccess := graphmodels.NewApplicationsRequiredResourceAccess()
resourceAppId := "00000003-0000-0000-c000-000000000000"
applicationsRequiredResourceAccess.SetResourceAppId(&resourceAppId) 


applicationResourcePermission := graphmodels.NewApplicationResourcePermission()
id := "633e0fce-8c58-4cfb-9495-12bbd5a24f7c"
applicationResourcePermission.SetId(&id) 
name := "Policy.Read.ConditionalAccess"
applicationResourcePermission.SetName(&name) 
type := graphmodels.SCOPE_APPLICATIONPERMISSIONTYPE 
applicationResourcePermission.SetType(&type) 
applicationResourcePermission1 := graphmodels.NewApplicationResourcePermission()
id := "e1fe6dd8-ba31-4d61-89e7-88639da4683d"
applicationResourcePermission1.SetId(&id) 
name := "User.Read"
applicationResourcePermission1.SetName(&name) 
type := graphmodels.SCOPE_APPLICATIONPERMISSIONTYPE 
applicationResourcePermission1.SetType(&type) 

permissions := []graphmodels.ApplicationResourcePermissionable {
	applicationResourcePermission,
	applicationResourcePermission1,
}
applicationsRequiredResourceAccess.SetPermissions(permissions)

requiredResourceAccesses := []graphmodels.ApplicationsRequiredResourceAccessable {
	applicationsRequiredResourceAccess,
}
multiTenantApplicationsToProvision.SetRequiredResourceAccesses(requiredResourceAccesses)

multiTenantApplicationsToProvision := []graphmodels.MultiTenantApplicationsToProvisionable {
	multiTenantApplicationsToProvision,
}
requestBody.SetMultiTenantApplicationsToProvision(multiTenantApplicationsToProvision)


delegatedAdministrationRoleAssignment := graphmodels.NewDelegatedAdministrationRoleAssignment()


roleTemplate := graphmodels.NewRoleTemplate()
id := "f2ef992c-3afb-46b9-b7cf-a126ee74c451"
roleTemplate.SetId(&id) 
name := "Global Reader"
roleTemplate.SetName(&name) 

roleTemplates := []graphmodels.RoleTemplateable {
	roleTemplate,
}
delegatedAdministrationRoleAssignment.SetRoleTemplates(roleTemplates)
group := graphmodels.NewGroup()
id := "ffffffff-5555-6666-7777-aaaaaaaaaaaa"
group.SetId(&id) 
delegatedAdministrationRoleAssignment.SetGroup(group)

delegatedAdministrationRoleAssignments := []graphmodels.DelegatedAdministrationRoleAssignmentable {
	delegatedAdministrationRoleAssignment,
}
requestBody.SetDelegatedAdministrationRoleAssignments(delegatedAdministrationRoleAssignments)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
governancePolicyTemplates, err := graphClient.Directory().TenantGovernance().GovernancePolicyTemplates().ByTenantGovernancePolicyTemplateId("tenantGovernancePolicyTemplate-id").Patch(context.Background(), requestBody, nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

TenantGovernancePolicyTemplate tenantGovernancePolicyTemplate = new TenantGovernancePolicyTemplate();
LinkedList<MultiTenantApplicationsToProvision> multiTenantApplicationsToProvision = new LinkedList<MultiTenantApplicationsToProvision>();
MultiTenantApplicationsToProvision multiTenantApplicationsToProvision1 = new MultiTenantApplicationsToProvision();
multiTenantApplicationsToProvision1.setAppId("66667777-aaaa-8888-bbbb-9999cccc0000");
multiTenantApplicationsToProvision1.setObjectId("cccccccc-2222-3333-4444-dddddddddddd");
multiTenantApplicationsToProvision1.setDisplayName("Mega Monitor");
LinkedList<ApplicationsRequiredResourceAccess> requiredResourceAccesses = new LinkedList<ApplicationsRequiredResourceAccess>();
ApplicationsRequiredResourceAccess applicationsRequiredResourceAccess = new ApplicationsRequiredResourceAccess();
applicationsRequiredResourceAccess.setResourceAppId("00000003-0000-0000-c000-000000000000");
LinkedList<ApplicationResourcePermission> permissions = new LinkedList<ApplicationResourcePermission>();
ApplicationResourcePermission applicationResourcePermission = new ApplicationResourcePermission();
applicationResourcePermission.setId("633e0fce-8c58-4cfb-9495-12bbd5a24f7c");
applicationResourcePermission.setName("Policy.Read.ConditionalAccess");
applicationResourcePermission.setType(ApplicationPermissionType.Scope);
permissions.add(applicationResourcePermission);
ApplicationResourcePermission applicationResourcePermission1 = new ApplicationResourcePermission();
applicationResourcePermission1.setId("e1fe6dd8-ba31-4d61-89e7-88639da4683d");
applicationResourcePermission1.setName("User.Read");
applicationResourcePermission1.setType(ApplicationPermissionType.Scope);
permissions.add(applicationResourcePermission1);
applicationsRequiredResourceAccess.setPermissions(permissions);
requiredResourceAccesses.add(applicationsRequiredResourceAccess);
multiTenantApplicationsToProvision1.setRequiredResourceAccesses(requiredResourceAccesses);
multiTenantApplicationsToProvision.add(multiTenantApplicationsToProvision1);
tenantGovernancePolicyTemplate.setMultiTenantApplicationsToProvision(multiTenantApplicationsToProvision);
LinkedList<DelegatedAdministrationRoleAssignment> delegatedAdministrationRoleAssignments = new LinkedList<DelegatedAdministrationRoleAssignment>();
DelegatedAdministrationRoleAssignment delegatedAdministrationRoleAssignment = new DelegatedAdministrationRoleAssignment();
LinkedList<RoleTemplate> roleTemplates = new LinkedList<RoleTemplate>();
RoleTemplate roleTemplate = new RoleTemplate();
roleTemplate.setId("f2ef992c-3afb-46b9-b7cf-a126ee74c451");
roleTemplate.setName("Global Reader");
roleTemplates.add(roleTemplate);
delegatedAdministrationRoleAssignment.setRoleTemplates(roleTemplates);
Group group = new Group();
group.setId("ffffffff-5555-6666-7777-aaaaaaaaaaaa");
delegatedAdministrationRoleAssignment.setGroup(group);
delegatedAdministrationRoleAssignments.add(delegatedAdministrationRoleAssignment);
tenantGovernancePolicyTemplate.setDelegatedAdministrationRoleAssignments(delegatedAdministrationRoleAssignments);
TenantGovernancePolicyTemplate result = graphClient.directory().tenantGovernance().governancePolicyTemplates().byTenantGovernancePolicyTemplateId("{tenantGovernancePolicyTemplate-id}").patch(tenantGovernancePolicyTemplate);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const tenantGovernancePolicyTemplate = {
  multiTenantApplicationsToProvision: [
    {
        appId: '66667777-aaaa-8888-bbbb-9999cccc0000',
        objectId: 'cccccccc-2222-3333-4444-dddddddddddd',
        displayName: 'Mega Monitor',
        requiredResourceAccesses: [
            {
              resourceAppId: '00000003-0000-0000-c000-000000000000',
              permissions: [
              {
                id: '633e0fce-8c58-4cfb-9495-12bbd5a24f7c',
                name: 'Policy.Read.ConditionalAccess',
                type: 'scope'
              },
              {
                id: 'e1fe6dd8-ba31-4d61-89e7-88639da4683d',
                name: 'User.Read',
                type: 'scope'
              }
              ]
            }
        ]
    }
  ],
  delegatedAdministrationRoleAssignments: [
    {
        roleTemplates: [
            {
                id: 'f2ef992c-3afb-46b9-b7cf-a126ee74c451',
                name: 'Global Reader'
            }
        ],
        group: {
            id: 'ffffffff-5555-6666-7777-aaaaaaaaaaaa'
        }
    }
  ]
};

await client.api('/directory/tenantGovernance/governancePolicyTemplates/aaaaaaaa-0000-1111-2222-bbbbbbbbbbbb')
	.version('beta')
	.update(tenantGovernancePolicyTemplate);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Models\TenantGovernancePolicyTemplate;
use Microsoft\Graph\Beta\Generated\Models\MultiTenantApplicationsToProvision;
use Microsoft\Graph\Beta\Generated\Models\ApplicationsRequiredResourceAccess;
use Microsoft\Graph\Beta\Generated\Models\ApplicationResourcePermission;
use Microsoft\Graph\Beta\Generated\Models\ApplicationPermissionType;
use Microsoft\Graph\Beta\Generated\Models\DelegatedAdministrationRoleAssignment;
use Microsoft\Graph\Beta\Generated\Models\RoleTemplate;
use Microsoft\Graph\Beta\Generated\Models\Group;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new TenantGovernancePolicyTemplate();
$multiTenantApplicationsToProvisionMultiTenantApplicationsToProvision1 = new MultiTenantApplicationsToProvision();
$multiTenantApplicationsToProvisionMultiTenantApplicationsToProvision1->setAppId('66667777-aaaa-8888-bbbb-9999cccc0000');
$multiTenantApplicationsToProvisionMultiTenantApplicationsToProvision1->setObjectId('cccccccc-2222-3333-4444-dddddddddddd');
$multiTenantApplicationsToProvisionMultiTenantApplicationsToProvision1->setDisplayName('Mega Monitor');
$requiredResourceAccessesApplicationsRequiredResourceAccess1 = new ApplicationsRequiredResourceAccess();
$requiredResourceAccessesApplicationsRequiredResourceAccess1->setResourceAppId('00000003-0000-0000-c000-000000000000');
$permissionsApplicationResourcePermission1 = new ApplicationResourcePermission();
$permissionsApplicationResourcePermission1->setId('633e0fce-8c58-4cfb-9495-12bbd5a24f7c');
$permissionsApplicationResourcePermission1->setName('Policy.Read.ConditionalAccess');
$permissionsApplicationResourcePermission1->setType(new ApplicationPermissionType('scope'));
$permissionsArray []= $permissionsApplicationResourcePermission1;
$permissionsApplicationResourcePermission2 = new ApplicationResourcePermission();
$permissionsApplicationResourcePermission2->setId('e1fe6dd8-ba31-4d61-89e7-88639da4683d');
$permissionsApplicationResourcePermission2->setName('User.Read');
$permissionsApplicationResourcePermission2->setType(new ApplicationPermissionType('scope'));
$permissionsArray []= $permissionsApplicationResourcePermission2;
$requiredResourceAccessesApplicationsRequiredResourceAccess1->setPermissions($permissionsArray);

$requiredResourceAccessesArray []= $requiredResourceAccessesApplicationsRequiredResourceAccess1;
$multiTenantApplicationsToProvisionMultiTenantApplicationsToProvision1->setRequiredResourceAccesses($requiredResourceAccessesArray);

$multiTenantApplicationsToProvisionArray []= $multiTenantApplicationsToProvisionMultiTenantApplicationsToProvision1;
$requestBody->setMultiTenantApplicationsToProvision($multiTenantApplicationsToProvisionArray);

$delegatedAdministrationRoleAssignmentsDelegatedAdministrationRoleAssignment1 = new DelegatedAdministrationRoleAssignment();
$roleTemplatesRoleTemplate1 = new RoleTemplate();
$roleTemplatesRoleTemplate1->setId('f2ef992c-3afb-46b9-b7cf-a126ee74c451');
$roleTemplatesRoleTemplate1->setName('Global Reader');
$roleTemplatesArray []= $roleTemplatesRoleTemplate1;
$delegatedAdministrationRoleAssignmentsDelegatedAdministrationRoleAssignment1->setRoleTemplates($roleTemplatesArray);

$delegatedAdministrationRoleAssignmentsDelegatedAdministrationRoleAssignment1Group = new Group();
$delegatedAdministrationRoleAssignmentsDelegatedAdministrationRoleAssignment1Group->setId('ffffffff-5555-6666-7777-aaaaaaaaaaaa');
$delegatedAdministrationRoleAssignmentsDelegatedAdministrationRoleAssignment1->setGroup($delegatedAdministrationRoleAssignmentsDelegatedAdministrationRoleAssignment1Group);
$delegatedAdministrationRoleAssignmentsArray []= $delegatedAdministrationRoleAssignmentsDelegatedAdministrationRoleAssignment1;
$requestBody->setDelegatedAdministrationRoleAssignments($delegatedAdministrationRoleAssignmentsArray);


$result = $graphServiceClient->directory()->tenantGovernance()->governancePolicyTemplates()->byTenantGovernancePolicyTemplateId('tenantGovernancePolicyTemplate-id')->patch($requestBody)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Beta.Identity.DirectoryManagement

$params = @{
	multiTenantApplicationsToProvision = @(
		@{
			appId = "66667777-aaaa-8888-bbbb-9999cccc0000"
			objectId = "cccccccc-2222-3333-4444-dddddddddddd"
			displayName = "Mega Monitor"
			requiredResourceAccesses = @(
				@{
					resourceAppId = "00000003-0000-0000-c000-000000000000"
					permissions = @(
						@{
							id = "633e0fce-8c58-4cfb-9495-12bbd5a24f7c"
							name = "Policy.Read.ConditionalAccess"
							type = "scope"
						}
						@{
							id = "e1fe6dd8-ba31-4d61-89e7-88639da4683d"
							name = "User.Read"
							type = "scope"
						}
					)
				}
			)
		}
	)
	delegatedAdministrationRoleAssignments = @(
		@{
			roleTemplates = @(
				@{
					id = "f2ef992c-3afb-46b9-b7cf-a126ee74c451"
					name = "Global Reader"
				}
			)
			group = @{
				id = "ffffffff-5555-6666-7777-aaaaaaaaaaaa"
			}
		}
	)
}

Update-MgBetaDirectoryTenantGovernancePolicyTemplate -TenantGovernancePolicyTemplateId $tenantGovernancePolicyTemplateId -BodyParameter $params
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.models.tenant_governance_policy_template import TenantGovernancePolicyTemplate
from msgraph_beta.generated.models.multi_tenant_applications_to_provision import MultiTenantApplicationsToProvision
from msgraph_beta.generated.models.applications_required_resource_access import ApplicationsRequiredResourceAccess
from msgraph_beta.generated.models.application_resource_permission import ApplicationResourcePermission
from msgraph_beta.generated.models.application_permission_type import ApplicationPermissionType
from msgraph_beta.generated.models.delegated_administration_role_assignment import DelegatedAdministrationRoleAssignment
from msgraph_beta.generated.models.role_template import RoleTemplate
from msgraph_beta.generated.models.group import Group
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = TenantGovernancePolicyTemplate(
	multi_tenant_applications_to_provision = [
		MultiTenantApplicationsToProvision(
			app_id = "66667777-aaaa-8888-bbbb-9999cccc0000",
			object_id = "cccccccc-2222-3333-4444-dddddddddddd",
			display_name = "Mega Monitor",
			required_resource_accesses = [
				ApplicationsRequiredResourceAccess(
					resource_app_id = "00000003-0000-0000-c000-000000000000",
					permissions = [
						ApplicationResourcePermission(
							id = "633e0fce-8c58-4cfb-9495-12bbd5a24f7c",
							name = "Policy.Read.ConditionalAccess",
							type = ApplicationPermissionType.Scope,
						),
						ApplicationResourcePermission(
							id = "e1fe6dd8-ba31-4d61-89e7-88639da4683d",
							name = "User.Read",
							type = ApplicationPermissionType.Scope,
						),
					],
				),
			],
		),
	],
	delegated_administration_role_assignments = [
		DelegatedAdministrationRoleAssignment(
			role_templates = [
				RoleTemplate(
					id = "f2ef992c-3afb-46b9-b7cf-a126ee74c451",
					name = "Global Reader",
				),
			],
			group = Group(
				id = "ffffffff-5555-6666-7777-aaaaaaaaaaaa",
			),
		),
	],
)

result = await graph_client.directory.tenant_governance.governance_policy_templates.by_tenant_governance_policy_template_id('tenantGovernancePolicyTemplate-id').patch(request_body)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.tenantGovernancePolicyTemplate",
  "id": "aaaaaaaa-0000-1111-2222-bbbbbbbbbbbb",
  "displayName": "Monitor Entra resource configurations",
  "description": "Grants Global reader and provisions a custom multi-tenant application to monitor conditional access policies",
  "createdDateTime": "2026-03-06T22:29:00.2110638Z",
  "lastModifiedDateTime": "2026-03-06T22:29:00.2110638Z",
  "version": "1.0",
  "multiTenantApplicationsToProvision": [
    {
        "appId": "66667777-aaaa-8888-bbbb-9999cccc0000",
        "objectId": "cccccccc-2222-3333-4444-dddddddddddd",
        "displayName": "Mega Monitor",
        "requiredResourceAccesses": [
            {
              "resourceAppId": "00000003-0000-0000-c000-000000000000",
              "permissions": [
              {
                "id": "633e0fce-8c58-4cfb-9495-12bbd5a24f7c",
                "name": "Policy.Read.ConditionalAccess",
                "type": "scope"
              },
              {
                "id": "e1fe6dd8-ba31-4d61-89e7-88639da4683d",
                "name": "User.Read",
                "type": "scope"
              }
              ]
            }
        ]
    }
  ],
  "delegatedAdministrationRoleAssignments": [
    {
        "roleTemplates": [
            {
                "id": "f2ef992c-3afb-46b9-b7cf-a126ee74c451",
                "name": "Global Reader"
            }
        ],
        "group": {
            "id": "ffffffff-5555-6666-7777-aaaaaaaaaaaa"
        }
    }
  ]
}
```

### Example 2: Update the default governance policy template

#### Request

The following example shows a request.

- [HTTP](#tabpanel_2_http)
- [C#](#tabpanel_2_csharp)
- [Go](#tabpanel_2_go)
- [Java](#tabpanel_2_java)
- [JavaScript](#tabpanel_2_javascript)
- [PHP](#tabpanel_2_php)
- [PowerShell](#tabpanel_2_powershell)
- [Python](#tabpanel_2_python)

```http
PATCH https://graph.microsoft.com/beta/directory/tenantGovernance/governancePolicyTemplates/default
Content-Type: application/json

{
  "multiTenantApplicationsToProvision": [
    {
        "appId": "66667777-aaaa-8888-bbbb-9999cccc0000",
        "objectId": "cccccccc-2222-3333-4444-dddddddddddd",
        "displayName": "Mega Monitor",
        "requiredResourceAccesses": [
            {
              "resourceAppId": "00000003-0000-0000-c000-000000000000",
              "permissions": [
              {
                "id": "633e0fce-8c58-4cfb-9495-12bbd5a24f7c",
                "name": "Policy.Read.ConditionalAccess",
                "type": "scope"
              },
              {
                "id": "e1fe6dd8-ba31-4d61-89e7-88639da4683d",
                "name": "User.Read",
                "type": "scope"
              }
              ]
            }
        ]
    }
  ],
  "delegatedAdministrationRoleAssignments": [
    {
        "roleTemplates": [
            {
                "id": "f2ef992c-3afb-46b9-b7cf-a126ee74c451",
                "name": "Global Reader"
            }
        ],
        "group": {
            "id": "ffffffff-5555-6666-7777-aaaaaaaaaaaa"
        }
    }
  ]
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.Models;

var requestBody = new TenantGovernancePolicyTemplate
{
	MultiTenantApplicationsToProvision = new List<MultiTenantApplicationsToProvision>
	{
		new MultiTenantApplicationsToProvision
		{
			AppId = "66667777-aaaa-8888-bbbb-9999cccc0000",
			ObjectId = "cccccccc-2222-3333-4444-dddddddddddd",
			DisplayName = "Mega Monitor",
			RequiredResourceAccesses = new List<ApplicationsRequiredResourceAccess>
			{
				new ApplicationsRequiredResourceAccess
				{
					ResourceAppId = "00000003-0000-0000-c000-000000000000",
					Permissions = new List<ApplicationResourcePermission>
					{
						new ApplicationResourcePermission
						{
							Id = "633e0fce-8c58-4cfb-9495-12bbd5a24f7c",
							Name = "Policy.Read.ConditionalAccess",
							Type = ApplicationPermissionType.Scope,
						},
						new ApplicationResourcePermission
						{
							Id = "e1fe6dd8-ba31-4d61-89e7-88639da4683d",
							Name = "User.Read",
							Type = ApplicationPermissionType.Scope,
						},
					},
				},
			},
		},
	},
	DelegatedAdministrationRoleAssignments = new List<DelegatedAdministrationRoleAssignment>
	{
		new DelegatedAdministrationRoleAssignment
		{
			RoleTemplates = new List<RoleTemplate>
			{
				new RoleTemplate
				{
					Id = "f2ef992c-3afb-46b9-b7cf-a126ee74c451",
					Name = "Global Reader",
				},
			},
			Group = new Group
			{
				Id = "ffffffff-5555-6666-7777-aaaaaaaaaaaa",
			},
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Directory.TenantGovernance.GovernancePolicyTemplates["{tenantGovernancePolicyTemplate-id}"].PatchAsync(requestBody);
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
	  graphmodels "github.com/microsoftgraph/msgraph-beta-sdk-go/models"
	  //other-imports
)

requestBody := graphmodels.NewTenantGovernancePolicyTemplate()


multiTenantApplicationsToProvision := graphmodels.NewMultiTenantApplicationsToProvision()
appId := "66667777-aaaa-8888-bbbb-9999cccc0000"
multiTenantApplicationsToProvision.SetAppId(&appId) 
objectId := "cccccccc-2222-3333-4444-dddddddddddd"
multiTenantApplicationsToProvision.SetObjectId(&objectId) 
displayName := "Mega Monitor"
multiTenantApplicationsToProvision.SetDisplayName(&displayName) 


applicationsRequiredResourceAccess := graphmodels.NewApplicationsRequiredResourceAccess()
resourceAppId := "00000003-0000-0000-c000-000000000000"
applicationsRequiredResourceAccess.SetResourceAppId(&resourceAppId) 


applicationResourcePermission := graphmodels.NewApplicationResourcePermission()
id := "633e0fce-8c58-4cfb-9495-12bbd5a24f7c"
applicationResourcePermission.SetId(&id) 
name := "Policy.Read.ConditionalAccess"
applicationResourcePermission.SetName(&name) 
type := graphmodels.SCOPE_APPLICATIONPERMISSIONTYPE 
applicationResourcePermission.SetType(&type) 
applicationResourcePermission1 := graphmodels.NewApplicationResourcePermission()
id := "e1fe6dd8-ba31-4d61-89e7-88639da4683d"
applicationResourcePermission1.SetId(&id) 
name := "User.Read"
applicationResourcePermission1.SetName(&name) 
type := graphmodels.SCOPE_APPLICATIONPERMISSIONTYPE 
applicationResourcePermission1.SetType(&type) 

permissions := []graphmodels.ApplicationResourcePermissionable {
	applicationResourcePermission,
	applicationResourcePermission1,
}
applicationsRequiredResourceAccess.SetPermissions(permissions)

requiredResourceAccesses := []graphmodels.ApplicationsRequiredResourceAccessable {
	applicationsRequiredResourceAccess,
}
multiTenantApplicationsToProvision.SetRequiredResourceAccesses(requiredResourceAccesses)

multiTenantApplicationsToProvision := []graphmodels.MultiTenantApplicationsToProvisionable {
	multiTenantApplicationsToProvision,
}
requestBody.SetMultiTenantApplicationsToProvision(multiTenantApplicationsToProvision)


delegatedAdministrationRoleAssignment := graphmodels.NewDelegatedAdministrationRoleAssignment()


roleTemplate := graphmodels.NewRoleTemplate()
id := "f2ef992c-3afb-46b9-b7cf-a126ee74c451"
roleTemplate.SetId(&id) 
name := "Global Reader"
roleTemplate.SetName(&name) 

roleTemplates := []graphmodels.RoleTemplateable {
	roleTemplate,
}
delegatedAdministrationRoleAssignment.SetRoleTemplates(roleTemplates)
group := graphmodels.NewGroup()
id := "ffffffff-5555-6666-7777-aaaaaaaaaaaa"
group.SetId(&id) 
delegatedAdministrationRoleAssignment.SetGroup(group)

delegatedAdministrationRoleAssignments := []graphmodels.DelegatedAdministrationRoleAssignmentable {
	delegatedAdministrationRoleAssignment,
}
requestBody.SetDelegatedAdministrationRoleAssignments(delegatedAdministrationRoleAssignments)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
governancePolicyTemplates, err := graphClient.Directory().TenantGovernance().GovernancePolicyTemplates().ByTenantGovernancePolicyTemplateId("tenantGovernancePolicyTemplate-id").Patch(context.Background(), requestBody, nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

TenantGovernancePolicyTemplate tenantGovernancePolicyTemplate = new TenantGovernancePolicyTemplate();
LinkedList<MultiTenantApplicationsToProvision> multiTenantApplicationsToProvision = new LinkedList<MultiTenantApplicationsToProvision>();
MultiTenantApplicationsToProvision multiTenantApplicationsToProvision1 = new MultiTenantApplicationsToProvision();
multiTenantApplicationsToProvision1.setAppId("66667777-aaaa-8888-bbbb-9999cccc0000");
multiTenantApplicationsToProvision1.setObjectId("cccccccc-2222-3333-4444-dddddddddddd");
multiTenantApplicationsToProvision1.setDisplayName("Mega Monitor");
LinkedList<ApplicationsRequiredResourceAccess> requiredResourceAccesses = new LinkedList<ApplicationsRequiredResourceAccess>();
ApplicationsRequiredResourceAccess applicationsRequiredResourceAccess = new ApplicationsRequiredResourceAccess();
applicationsRequiredResourceAccess.setResourceAppId("00000003-0000-0000-c000-000000000000");
LinkedList<ApplicationResourcePermission> permissions = new LinkedList<ApplicationResourcePermission>();
ApplicationResourcePermission applicationResourcePermission = new ApplicationResourcePermission();
applicationResourcePermission.setId("633e0fce-8c58-4cfb-9495-12bbd5a24f7c");
applicationResourcePermission.setName("Policy.Read.ConditionalAccess");
applicationResourcePermission.setType(ApplicationPermissionType.Scope);
permissions.add(applicationResourcePermission);
ApplicationResourcePermission applicationResourcePermission1 = new ApplicationResourcePermission();
applicationResourcePermission1.setId("e1fe6dd8-ba31-4d61-89e7-88639da4683d");
applicationResourcePermission1.setName("User.Read");
applicationResourcePermission1.setType(ApplicationPermissionType.Scope);
permissions.add(applicationResourcePermission1);
applicationsRequiredResourceAccess.setPermissions(permissions);
requiredResourceAccesses.add(applicationsRequiredResourceAccess);
multiTenantApplicationsToProvision1.setRequiredResourceAccesses(requiredResourceAccesses);
multiTenantApplicationsToProvision.add(multiTenantApplicationsToProvision1);
tenantGovernancePolicyTemplate.setMultiTenantApplicationsToProvision(multiTenantApplicationsToProvision);
LinkedList<DelegatedAdministrationRoleAssignment> delegatedAdministrationRoleAssignments = new LinkedList<DelegatedAdministrationRoleAssignment>();
DelegatedAdministrationRoleAssignment delegatedAdministrationRoleAssignment = new DelegatedAdministrationRoleAssignment();
LinkedList<RoleTemplate> roleTemplates = new LinkedList<RoleTemplate>();
RoleTemplate roleTemplate = new RoleTemplate();
roleTemplate.setId("f2ef992c-3afb-46b9-b7cf-a126ee74c451");
roleTemplate.setName("Global Reader");
roleTemplates.add(roleTemplate);
delegatedAdministrationRoleAssignment.setRoleTemplates(roleTemplates);
Group group = new Group();
group.setId("ffffffff-5555-6666-7777-aaaaaaaaaaaa");
delegatedAdministrationRoleAssignment.setGroup(group);
delegatedAdministrationRoleAssignments.add(delegatedAdministrationRoleAssignment);
tenantGovernancePolicyTemplate.setDelegatedAdministrationRoleAssignments(delegatedAdministrationRoleAssignments);
TenantGovernancePolicyTemplate result = graphClient.directory().tenantGovernance().governancePolicyTemplates().byTenantGovernancePolicyTemplateId("{tenantGovernancePolicyTemplate-id}").patch(tenantGovernancePolicyTemplate);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const tenantGovernancePolicyTemplate = {
  multiTenantApplicationsToProvision: [
    {
        appId: '66667777-aaaa-8888-bbbb-9999cccc0000',
        objectId: 'cccccccc-2222-3333-4444-dddddddddddd',
        displayName: 'Mega Monitor',
        requiredResourceAccesses: [
            {
              resourceAppId: '00000003-0000-0000-c000-000000000000',
              permissions: [
              {
                id: '633e0fce-8c58-4cfb-9495-12bbd5a24f7c',
                name: 'Policy.Read.ConditionalAccess',
                type: 'scope'
              },
              {
                id: 'e1fe6dd8-ba31-4d61-89e7-88639da4683d',
                name: 'User.Read',
                type: 'scope'
              }
              ]
            }
        ]
    }
  ],
  delegatedAdministrationRoleAssignments: [
    {
        roleTemplates: [
            {
                id: 'f2ef992c-3afb-46b9-b7cf-a126ee74c451',
                name: 'Global Reader'
            }
        ],
        group: {
            id: 'ffffffff-5555-6666-7777-aaaaaaaaaaaa'
        }
    }
  ]
};

await client.api('/directory/tenantGovernance/governancePolicyTemplates/default')
	.version('beta')
	.update(tenantGovernancePolicyTemplate);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Models\TenantGovernancePolicyTemplate;
use Microsoft\Graph\Beta\Generated\Models\MultiTenantApplicationsToProvision;
use Microsoft\Graph\Beta\Generated\Models\ApplicationsRequiredResourceAccess;
use Microsoft\Graph\Beta\Generated\Models\ApplicationResourcePermission;
use Microsoft\Graph\Beta\Generated\Models\ApplicationPermissionType;
use Microsoft\Graph\Beta\Generated\Models\DelegatedAdministrationRoleAssignment;
use Microsoft\Graph\Beta\Generated\Models\RoleTemplate;
use Microsoft\Graph\Beta\Generated\Models\Group;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new TenantGovernancePolicyTemplate();
$multiTenantApplicationsToProvisionMultiTenantApplicationsToProvision1 = new MultiTenantApplicationsToProvision();
$multiTenantApplicationsToProvisionMultiTenantApplicationsToProvision1->setAppId('66667777-aaaa-8888-bbbb-9999cccc0000');
$multiTenantApplicationsToProvisionMultiTenantApplicationsToProvision1->setObjectId('cccccccc-2222-3333-4444-dddddddddddd');
$multiTenantApplicationsToProvisionMultiTenantApplicationsToProvision1->setDisplayName('Mega Monitor');
$requiredResourceAccessesApplicationsRequiredResourceAccess1 = new ApplicationsRequiredResourceAccess();
$requiredResourceAccessesApplicationsRequiredResourceAccess1->setResourceAppId('00000003-0000-0000-c000-000000000000');
$permissionsApplicationResourcePermission1 = new ApplicationResourcePermission();
$permissionsApplicationResourcePermission1->setId('633e0fce-8c58-4cfb-9495-12bbd5a24f7c');
$permissionsApplicationResourcePermission1->setName('Policy.Read.ConditionalAccess');
$permissionsApplicationResourcePermission1->setType(new ApplicationPermissionType('scope'));
$permissionsArray []= $permissionsApplicationResourcePermission1;
$permissionsApplicationResourcePermission2 = new ApplicationResourcePermission();
$permissionsApplicationResourcePermission2->setId('e1fe6dd8-ba31-4d61-89e7-88639da4683d');
$permissionsApplicationResourcePermission2->setName('User.Read');
$permissionsApplicationResourcePermission2->setType(new ApplicationPermissionType('scope'));
$permissionsArray []= $permissionsApplicationResourcePermission2;
$requiredResourceAccessesApplicationsRequiredResourceAccess1->setPermissions($permissionsArray);

$requiredResourceAccessesArray []= $requiredResourceAccessesApplicationsRequiredResourceAccess1;
$multiTenantApplicationsToProvisionMultiTenantApplicationsToProvision1->setRequiredResourceAccesses($requiredResourceAccessesArray);

$multiTenantApplicationsToProvisionArray []= $multiTenantApplicationsToProvisionMultiTenantApplicationsToProvision1;
$requestBody->setMultiTenantApplicationsToProvision($multiTenantApplicationsToProvisionArray);

$delegatedAdministrationRoleAssignmentsDelegatedAdministrationRoleAssignment1 = new DelegatedAdministrationRoleAssignment();
$roleTemplatesRoleTemplate1 = new RoleTemplate();
$roleTemplatesRoleTemplate1->setId('f2ef992c-3afb-46b9-b7cf-a126ee74c451');
$roleTemplatesRoleTemplate1->setName('Global Reader');
$roleTemplatesArray []= $roleTemplatesRoleTemplate1;
$delegatedAdministrationRoleAssignmentsDelegatedAdministrationRoleAssignment1->setRoleTemplates($roleTemplatesArray);

$delegatedAdministrationRoleAssignmentsDelegatedAdministrationRoleAssignment1Group = new Group();
$delegatedAdministrationRoleAssignmentsDelegatedAdministrationRoleAssignment1Group->setId('ffffffff-5555-6666-7777-aaaaaaaaaaaa');
$delegatedAdministrationRoleAssignmentsDelegatedAdministrationRoleAssignment1->setGroup($delegatedAdministrationRoleAssignmentsDelegatedAdministrationRoleAssignment1Group);
$delegatedAdministrationRoleAssignmentsArray []= $delegatedAdministrationRoleAssignmentsDelegatedAdministrationRoleAssignment1;
$requestBody->setDelegatedAdministrationRoleAssignments($delegatedAdministrationRoleAssignmentsArray);


$result = $graphServiceClient->directory()->tenantGovernance()->governancePolicyTemplates()->byTenantGovernancePolicyTemplateId('tenantGovernancePolicyTemplate-id')->patch($requestBody)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Beta.Identity.DirectoryManagement

$params = @{
	multiTenantApplicationsToProvision = @(
		@{
			appId = "66667777-aaaa-8888-bbbb-9999cccc0000"
			objectId = "cccccccc-2222-3333-4444-dddddddddddd"
			displayName = "Mega Monitor"
			requiredResourceAccesses = @(
				@{
					resourceAppId = "00000003-0000-0000-c000-000000000000"
					permissions = @(
						@{
							id = "633e0fce-8c58-4cfb-9495-12bbd5a24f7c"
							name = "Policy.Read.ConditionalAccess"
							type = "scope"
						}
						@{
							id = "e1fe6dd8-ba31-4d61-89e7-88639da4683d"
							name = "User.Read"
							type = "scope"
						}
					)
				}
			)
		}
	)
	delegatedAdministrationRoleAssignments = @(
		@{
			roleTemplates = @(
				@{
					id = "f2ef992c-3afb-46b9-b7cf-a126ee74c451"
					name = "Global Reader"
				}
			)
			group = @{
				id = "ffffffff-5555-6666-7777-aaaaaaaaaaaa"
			}
		}
	)
}

Update-MgBetaDirectoryTenantGovernancePolicyTemplate -TenantGovernancePolicyTemplateId $tenantGovernancePolicyTemplateId -BodyParameter $params
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.models.tenant_governance_policy_template import TenantGovernancePolicyTemplate
from msgraph_beta.generated.models.multi_tenant_applications_to_provision import MultiTenantApplicationsToProvision
from msgraph_beta.generated.models.applications_required_resource_access import ApplicationsRequiredResourceAccess
from msgraph_beta.generated.models.application_resource_permission import ApplicationResourcePermission
from msgraph_beta.generated.models.application_permission_type import ApplicationPermissionType
from msgraph_beta.generated.models.delegated_administration_role_assignment import DelegatedAdministrationRoleAssignment
from msgraph_beta.generated.models.role_template import RoleTemplate
from msgraph_beta.generated.models.group import Group
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = TenantGovernancePolicyTemplate(
	multi_tenant_applications_to_provision = [
		MultiTenantApplicationsToProvision(
			app_id = "66667777-aaaa-8888-bbbb-9999cccc0000",
			object_id = "cccccccc-2222-3333-4444-dddddddddddd",
			display_name = "Mega Monitor",
			required_resource_accesses = [
				ApplicationsRequiredResourceAccess(
					resource_app_id = "00000003-0000-0000-c000-000000000000",
					permissions = [
						ApplicationResourcePermission(
							id = "633e0fce-8c58-4cfb-9495-12bbd5a24f7c",
							name = "Policy.Read.ConditionalAccess",
							type = ApplicationPermissionType.Scope,
						),
						ApplicationResourcePermission(
							id = "e1fe6dd8-ba31-4d61-89e7-88639da4683d",
							name = "User.Read",
							type = ApplicationPermissionType.Scope,
						),
					],
				),
			],
		),
	],
	delegated_administration_role_assignments = [
		DelegatedAdministrationRoleAssignment(
			role_templates = [
				RoleTemplate(
					id = "f2ef992c-3afb-46b9-b7cf-a126ee74c451",
					name = "Global Reader",
				),
			],
			group = Group(
				id = "ffffffff-5555-6666-7777-aaaaaaaaaaaa",
			),
		),
	],
)

result = await graph_client.directory.tenant_governance.governance_policy_templates.by_tenant_governance_policy_template_id('tenantGovernancePolicyTemplate-id').patch(request_body)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.tenantGovernancePolicyTemplate",
  "id": "default",
  "displayName": "Default Policy Template",
  "description": "The system-provided default governance policy template",
  "version": "1.0",
  "createdDateTime": "2026-03-06T22:29:00.2110638Z",
  "lastModifiedDateTime": "2026-03-06T22:29:00.2110638Z",
  "multiTenantApplicationsToProvision": [
    {
        "appId": "66667777-aaaa-8888-bbbb-9999cccc0000",
        "objectId": "cccccccc-2222-3333-4444-dddddddddddd",
        "displayName": "Mega Monitor",
        "requiredResourceAccesses": [
            {
              "resourceAppId": "00000003-0000-0000-c000-000000000000",
              "permissions": [
              {
                "id": "633e0fce-8c58-4cfb-9495-12bbd5a24f7c",
                "name": "Policy.Read.ConditionalAccess",
                "type": "scope"
              },
              {
                "id": "e1fe6dd8-ba31-4d61-89e7-88639da4683d",
                "name": "User.Read",
                "type": "scope"
              }
              ]
            }
        ]
    }
  ],
  "delegatedAdministrationRoleAssignments": [
    {
        "roleTemplates": [
            {
                "id": "f2ef992c-3afb-46b9-b7cf-a126ee74c451",
                "name": "Global Reader"
            }
        ],
        "group": {
            "id": "ffffffff-5555-6666-7777-aaaaaaaaaaaa"
        }
    }
  ]
}
```
