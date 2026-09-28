<!-- Source: https://learn.microsoft.com/en-us/graph/api/policyroot-post-permissiongrantpreapprovalpolicies?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-23 -->

# Create permissionGrantPreApprovalPolicy

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Create a new [permissionGrantPreApprovalPolicy](https://learn.microsoft.com/en-us/graph/api/resources/permissiongrantpreapprovalpolicy?view=graph-rest-beta) object.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Policy.ReadWrite.PermissionGrant | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Policy.ReadWrite.PermissionGrant | Not available. |

Important

For delegated access using work or school accounts, the signed-in user must be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) or a custom role that grants the permissions required for this operation. This operation supports the following built-in roles, which provide only the least privilege necessary:

- Application Administrator
- Cloud Application Administrator

## HTTP request

```http
POST /policies/permissionGrantPreApprovalPolicies
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the [permissionGrantPreApprovalPolicy](https://learn.microsoft.com/en-us/graph/api/resources/permissiongrantpreapprovalpolicy?view=graph-rest-beta) object.

You can specify the following properties when creating a **permissionGrantPreApprovalPolicy**.

| Property | Type | Description |
| :--- | :--- | :--- |
| conditions | [preApprovalDetail](https://learn.microsoft.com/en-us/graph/api/resources/preapprovaldetail?view=graph-rest-beta) collection | A list of conditions that are preapproved in the policy. Required. |

## Response

If successful, this method returns a `201 Created` response code and a [permissionGrantPreApprovalPolicy](https://learn.microsoft.com/en-us/graph/api/resources/permissiongrantpreapprovalpolicy?view=graph-rest-beta) object in the response body.

## Examples

### Example 1: Create a preapproval policy for both group and chat scope

In the following example:

- The condition for the `chat` resource type:

  - Indicates that all chats regardless of sensitivity labels are in scope
  - Specifies that all application permissions for all APIs are preapproved

- The condition for the `group` resource type:

  - Specifies two sensitivity labels that are in scope
  - Specifies two application permissions for the `00000003-0000-0000-c000-000000000000` resource app are preapproved

#### Request

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [PowerShell](#tabpanel_1_powershell)
- [Python](#tabpanel_1_python)

```http
POST https://graph.microsoft.com/beta/policies/permissionGrantPreApprovalPolicies
Content-Type: application/json

{
    "conditions": [
        {
            "scopeType": "chat",
            "sensitivityLabels": {
                "@odata.type": "#microsoft.graph.allScopeSensitivityLabels",
                "labelKind": "all"
            },
            "permissions": {
                "@odata.type": "#microsoft.graph.allPreApprovedPermissions",
                "permissionKind": "all",
                "permissionType": "application"
            }
        },
        {
            "scopeType": "group",
            "scopeSensitivityLabels": {
                "@odata.type": "microsoft.graph.enumeratedScopeSensitivityLabels",
                "labelKind": "enumerated",
                "sensitivityLabels": [
                    "d9c43deb-f3e1-4422-9fd6-ccf22a3206b8",
                    "c99dade2-aa54-4890-ac1c-a146fa26bd1e"
                ]
            },
            "permissions": {
                "@odata.type": "#microsoft.graph.enumeratedPreApprovedPermissions",
                "permissionKind": "enumerated",
                "permissionType": "application",
                "resourceApplicationId": "00000003-0000-0000-c000-000000000000",
                "permissionIds": [
                    "134483aa-3dda-4d65-ac91-b8dda1417875",
                    "9d33613d-f855-483b-bca7-ea63ac9f5485"
                ]
            }
        }
    ]
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.Models;

var requestBody = new PermissionGrantPreApprovalPolicy
{
	Conditions = new List<PreApprovalDetail>
	{
		new PreApprovalDetail
		{
			ScopeType = ResourceScopeType.Chat,
			SensitivityLabels = new AllScopeSensitivityLabels
			{
				OdataType = "#microsoft.graph.allScopeSensitivityLabels",
				LabelKind = LabelKind.All,
			},
			Permissions = new AllPreApprovedPermissions
			{
				OdataType = "#microsoft.graph.allPreApprovedPermissions",
				PermissionKind = PermissionKind.All,
				PermissionType = PermissionType.Application,
			},
		},
		new PreApprovalDetail
		{
			ScopeType = ResourceScopeType.Group,
			Permissions = new EnumeratedPreApprovedPermissions
			{
				OdataType = "#microsoft.graph.enumeratedPreApprovedPermissions",
				PermissionKind = PermissionKind.Enumerated,
				PermissionType = PermissionType.Application,
				ResourceApplicationId = "00000003-0000-0000-c000-000000000000",
				PermissionIds = new List<string>
				{
					"134483aa-3dda-4d65-ac91-b8dda1417875",
					"9d33613d-f855-483b-bca7-ea63ac9f5485",
				},
			},
			AdditionalData = new Dictionary<string, object>
			{
				{
					"scopeSensitivityLabels" , new EnumeratedScopeSensitivityLabels
					{
						OdataType = "microsoft.graph.enumeratedScopeSensitivityLabels",
						LabelKind = LabelKind.Enumerated,
						SensitivityLabels = new List<string>
						{
							"d9c43deb-f3e1-4422-9fd6-ccf22a3206b8",
							"c99dade2-aa54-4890-ac1c-a146fa26bd1e",
						},
					}
				},
			},
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Policies.PermissionGrantPreApprovalPolicies.PostAsync(requestBody);
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

requestBody := graphmodels.NewPermissionGrantPreApprovalPolicy()


preApprovalDetail := graphmodels.NewPreApprovalDetail()
scopeType := graphmodels.CHAT_RESOURCESCOPETYPE 
preApprovalDetail.SetScopeType(&scopeType) 
sensitivityLabels := graphmodels.NewAllScopeSensitivityLabels()
labelKind := graphmodels.ALL_LABELKIND 
sensitivityLabels.SetLabelKind(&labelKind) 
preApprovalDetail.SetSensitivityLabels(sensitivityLabels)
permissions := graphmodels.NewAllPreApprovedPermissions()
permissionKind := graphmodels.ALL_PERMISSIONKIND 
permissions.SetPermissionKind(&permissionKind) 
permissionType := graphmodels.APPLICATION_PERMISSIONTYPE 
permissions.SetPermissionType(&permissionType) 
preApprovalDetail.SetPermissions(permissions)
preApprovalDetail1 := graphmodels.NewPreApprovalDetail()
scopeType := graphmodels.GROUP_RESOURCESCOPETYPE 
preApprovalDetail1.SetScopeType(&scopeType) 
permissions := graphmodels.NewEnumeratedPreApprovedPermissions()
permissionKind := graphmodels.ENUMERATED_PERMISSIONKIND 
permissions.SetPermissionKind(&permissionKind) 
permissionType := graphmodels.APPLICATION_PERMISSIONTYPE 
permissions.SetPermissionType(&permissionType) 
resourceApplicationId := "00000003-0000-0000-c000-000000000000"
permissions.SetResourceApplicationId(&resourceApplicationId) 
permissionIds := []string {
	"134483aa-3dda-4d65-ac91-b8dda1417875",
	"9d33613d-f855-483b-bca7-ea63ac9f5485",
}
permissions.SetPermissionIds(permissionIds)
preApprovalDetail1.SetPermissions(permissions)
additionalData := map[string]interface{}{
scopeSensitivityLabels := graphmodels.NewEnumeratedScopeSensitivityLabels()
	labelKind := graphmodels.ENUMERATED_LABELKIND 
	scopeSensitivityLabels.SetLabelKind(&labelKind) 
	sensitivityLabels := []string {
		"d9c43deb-f3e1-4422-9fd6-ccf22a3206b8",
		"c99dade2-aa54-4890-ac1c-a146fa26bd1e",
	}
	scopeSensitivityLabels.SetSensitivityLabels(sensitivityLabels)
	preApprovalDetail1.SetScopeSensitivityLabels(scopeSensitivityLabels)
}
preApprovalDetail1.SetAdditionalData(additionalData)

conditions := []graphmodels.PreApprovalDetailable {
	preApprovalDetail,
	preApprovalDetail1,
}
requestBody.SetConditions(conditions)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
permissionGrantPreApprovalPolicies, err := graphClient.Policies().PermissionGrantPreApprovalPolicies().Post(context.Background(), requestBody, nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

PermissionGrantPreApprovalPolicy permissionGrantPreApprovalPolicy = new PermissionGrantPreApprovalPolicy();
LinkedList<PreApprovalDetail> conditions = new LinkedList<PreApprovalDetail>();
PreApprovalDetail preApprovalDetail = new PreApprovalDetail();
preApprovalDetail.setScopeType(ResourceScopeType.Chat);
AllScopeSensitivityLabels sensitivityLabels = new AllScopeSensitivityLabels();
sensitivityLabels.setOdataType("#microsoft.graph.allScopeSensitivityLabels");
sensitivityLabels.setLabelKind(LabelKind.All);
preApprovalDetail.setSensitivityLabels(sensitivityLabels);
AllPreApprovedPermissions permissions = new AllPreApprovedPermissions();
permissions.setOdataType("#microsoft.graph.allPreApprovedPermissions");
permissions.setPermissionKind(PermissionKind.All);
permissions.setPermissionType(PermissionType.Application);
preApprovalDetail.setPermissions(permissions);
conditions.add(preApprovalDetail);
PreApprovalDetail preApprovalDetail1 = new PreApprovalDetail();
preApprovalDetail1.setScopeType(ResourceScopeType.Group);
EnumeratedPreApprovedPermissions permissions1 = new EnumeratedPreApprovedPermissions();
permissions1.setOdataType("#microsoft.graph.enumeratedPreApprovedPermissions");
permissions1.setPermissionKind(PermissionKind.Enumerated);
permissions1.setPermissionType(PermissionType.Application);
permissions1.setResourceApplicationId("00000003-0000-0000-c000-000000000000");
LinkedList<String> permissionIds = new LinkedList<String>();
permissionIds.add("134483aa-3dda-4d65-ac91-b8dda1417875");
permissionIds.add("9d33613d-f855-483b-bca7-ea63ac9f5485");
permissions1.setPermissionIds(permissionIds);
preApprovalDetail1.setPermissions(permissions1);
HashMap<String, Object> additionalData = new HashMap<String, Object>();
EnumeratedScopeSensitivityLabels scopeSensitivityLabels = new EnumeratedScopeSensitivityLabels();
scopeSensitivityLabels.setOdataType("microsoft.graph.enumeratedScopeSensitivityLabels");
scopeSensitivityLabels.setLabelKind(LabelKind.Enumerated);
LinkedList<String> sensitivityLabels1 = new LinkedList<String>();
sensitivityLabels1.add("d9c43deb-f3e1-4422-9fd6-ccf22a3206b8");
sensitivityLabels1.add("c99dade2-aa54-4890-ac1c-a146fa26bd1e");
scopeSensitivityLabels.setSensitivityLabels(sensitivityLabels1);
additionalData.put("scopeSensitivityLabels", scopeSensitivityLabels);
preApprovalDetail1.setAdditionalData(additionalData);
conditions.add(preApprovalDetail1);
permissionGrantPreApprovalPolicy.setConditions(conditions);
PermissionGrantPreApprovalPolicy result = graphClient.policies().permissionGrantPreApprovalPolicies().post(permissionGrantPreApprovalPolicy);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const permissionGrantPreApprovalPolicy = {
    conditions: [
        {
            scopeType: 'chat',
            sensitivityLabels: {
                '@odata.type': '#microsoft.graph.allScopeSensitivityLabels',
                labelKind: 'all'
            },
            permissions: {
                '@odata.type': '#microsoft.graph.allPreApprovedPermissions',
                permissionKind: 'all',
                permissionType: 'application'
            }
        },
        {
            scopeType: 'group',
            scopeSensitivityLabels: {
                '@odata.type': 'microsoft.graph.enumeratedScopeSensitivityLabels',
                labelKind: 'enumerated',
                sensitivityLabels: [
                    'd9c43deb-f3e1-4422-9fd6-ccf22a3206b8',
                    'c99dade2-aa54-4890-ac1c-a146fa26bd1e'
                ]
            },
            permissions: {
                '@odata.type': '#microsoft.graph.enumeratedPreApprovedPermissions',
                permissionKind: 'enumerated',
                permissionType: 'application',
                resourceApplicationId: '00000003-0000-0000-c000-000000000000',
                permissionIds: [
                    '134483aa-3dda-4d65-ac91-b8dda1417875',
                    '9d33613d-f855-483b-bca7-ea63ac9f5485'
                ]
            }
        }
    ]
};

await client.api('/policies/permissionGrantPreApprovalPolicies')
	.version('beta')
	.post(permissionGrantPreApprovalPolicy);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Models\PermissionGrantPreApprovalPolicy;
use Microsoft\Graph\Beta\Generated\Models\PreApprovalDetail;
use Microsoft\Graph\Beta\Generated\Models\ResourceScopeType;
use Microsoft\Graph\Beta\Generated\Models\AllScopeSensitivityLabels;
use Microsoft\Graph\Beta\Generated\Models\LabelKind;
use Microsoft\Graph\Beta\Generated\Models\AllPreApprovedPermissions;
use Microsoft\Graph\Beta\Generated\Models\PermissionKind;
use Microsoft\Graph\Beta\Generated\Models\PermissionType;
use Microsoft\Graph\Beta\Generated\Models\EnumeratedPreApprovedPermissions;
use Microsoft\Graph\Beta\Generated\Models\EnumeratedScopeSensitivityLabels;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new PermissionGrantPreApprovalPolicy();
$conditionsPreApprovalDetail1 = new PreApprovalDetail();
$conditionsPreApprovalDetail1->setScopeType(new ResourceScopeType('chat'));
$conditionsPreApprovalDetail1SensitivityLabels = new AllScopeSensitivityLabels();
$conditionsPreApprovalDetail1SensitivityLabels->setOdataType('#microsoft.graph.allScopeSensitivityLabels');
$conditionsPreApprovalDetail1SensitivityLabels->setLabelKind(new LabelKind('all'));
$conditionsPreApprovalDetail1->setSensitivityLabels($conditionsPreApprovalDetail1SensitivityLabels);
$conditionsPreApprovalDetail1Permissions = new AllPreApprovedPermissions();
$conditionsPreApprovalDetail1Permissions->setOdataType('#microsoft.graph.allPreApprovedPermissions');
$conditionsPreApprovalDetail1Permissions->setPermissionKind(new PermissionKind('all'));
$conditionsPreApprovalDetail1Permissions->setPermissionType(new PermissionType('application'));
$conditionsPreApprovalDetail1->setPermissions($conditionsPreApprovalDetail1Permissions);
$conditionsArray []= $conditionsPreApprovalDetail1;
$conditionsPreApprovalDetail2 = new PreApprovalDetail();
$conditionsPreApprovalDetail2->setScopeType(new ResourceScopeType('group'));
$conditionsPreApprovalDetail2Permissions = new EnumeratedPreApprovedPermissions();
$conditionsPreApprovalDetail2Permissions->setOdataType('#microsoft.graph.enumeratedPreApprovedPermissions');
$conditionsPreApprovalDetail2Permissions->setPermissionKind(new PermissionKind('enumerated'));
$conditionsPreApprovalDetail2Permissions->setPermissionType(new PermissionType('application'));
$conditionsPreApprovalDetail2Permissions->setResourceApplicationId('00000003-0000-0000-c000-000000000000');
$conditionsPreApprovalDetail2Permissions->setPermissionIds(['134483aa-3dda-4d65-ac91-b8dda1417875', '9d33613d-f855-483b-bca7-ea63ac9f5485', 	]);
$conditionsPreApprovalDetail2->setPermissions($conditionsPreApprovalDetail2Permissions);
$additionalData = [
	'scopeSensitivityLabels' => [
		'@odata.type' => 'microsoft.graph.enumeratedScopeSensitivityLabels',
		'labelKind' => new LabelKind('enumerated'),
		'sensitivityLabels' => [
'd9c43deb-f3e1-4422-9fd6-ccf22a3206b8', 'c99dade2-aa54-4890-ac1c-a146fa26bd1e', ],
	],
];
$conditionsPreApprovalDetail2->setAdditionalData($additionalData);
$conditionsArray []= $conditionsPreApprovalDetail2;
$requestBody->setConditions($conditionsArray);


$result = $graphServiceClient->policies()->permissionGrantPreApprovalPolicies()->post($requestBody)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Beta.Identity.SignIns

$params = @{
	conditions = @(
		@{
			scopeType = "chat"
			sensitivityLabels = @{
				"@odata.type" = "#microsoft.graph.allScopeSensitivityLabels"
				labelKind = "all"
			}
			permissions = @{
				"@odata.type" = "#microsoft.graph.allPreApprovedPermissions"
				permissionKind = "all"
				permissionType = "application"
			}
		}
		@{
			scopeType = "group"
			scopeSensitivityLabels = @{
				"@odata.type" = "microsoft.graph.enumeratedScopeSensitivityLabels"
				labelKind = "enumerated"
				sensitivityLabels = @(
				"d9c43deb-f3e1-4422-9fd6-ccf22a3206b8"
			"c99dade2-aa54-4890-ac1c-a146fa26bd1e"
		)
	}
	permissions = @{
		"@odata.type" = "#microsoft.graph.enumeratedPreApprovedPermissions"
		permissionKind = "enumerated"
		permissionType = "application"
		resourceApplicationId = "00000003-0000-0000-c000-000000000000"
		permissionIds = @(
		"134483aa-3dda-4d65-ac91-b8dda1417875"
	"9d33613d-f855-483b-bca7-ea63ac9f5485"
)
}
}
)
}

New-MgBetaPolicyPermissionGrantPreApprovalPolicy -BodyParameter $params
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.models.permission_grant_pre_approval_policy import PermissionGrantPreApprovalPolicy
from msgraph_beta.generated.models.pre_approval_detail import PreApprovalDetail
from msgraph_beta.generated.models.resource_scope_type import ResourceScopeType
from msgraph_beta.generated.models.all_scope_sensitivity_labels import AllScopeSensitivityLabels
from msgraph_beta.generated.models.label_kind import LabelKind
from msgraph_beta.generated.models.all_pre_approved_permissions import AllPreApprovedPermissions
from msgraph_beta.generated.models.permission_kind import PermissionKind
from msgraph_beta.generated.models.permission_type import PermissionType
from msgraph_beta.generated.models.enumerated_pre_approved_permissions import EnumeratedPreApprovedPermissions
from msgraph_beta.generated.models.enumerated_scope_sensitivity_labels import EnumeratedScopeSensitivityLabels
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = PermissionGrantPreApprovalPolicy(
	conditions = [
		PreApprovalDetail(
			scope_type = ResourceScopeType.Chat,
			sensitivity_labels = AllScopeSensitivityLabels(
				odata_type = "#microsoft.graph.allScopeSensitivityLabels",
				label_kind = LabelKind.All,
			),
			permissions = AllPreApprovedPermissions(
				odata_type = "#microsoft.graph.allPreApprovedPermissions",
				permission_kind = PermissionKind.All,
				permission_type = PermissionType.Application,
			),
		),
		PreApprovalDetail(
			scope_type = ResourceScopeType.Group,
			permissions = EnumeratedPreApprovedPermissions(
				odata_type = "#microsoft.graph.enumeratedPreApprovedPermissions",
				permission_kind = PermissionKind.Enumerated,
				permission_type = PermissionType.Application,
				resource_application_id = "00000003-0000-0000-c000-000000000000",
				permission_ids = [
					"134483aa-3dda-4d65-ac91-b8dda1417875",
					"9d33613d-f855-483b-bca7-ea63ac9f5485",
				],
			),
			additional_data = {
					"scope_sensitivity_labels" : {
							"@odata_type" : "microsoft.graph.enumeratedScopeSensitivityLabels",
							"label_kind" : LabelKind.Enumerated,
							"sensitivity_labels" : [
								"d9c43deb-f3e1-4422-9fd6-ccf22a3206b8",
								"c99dade2-aa54-4890-ac1c-a146fa26bd1e",
							],
					},
			}
		),
	],
)

result = await graph_client.policies.permission_grant_pre_approval_policies.post(request_body)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-Type: application/json

{
    "@odata.context": "https://graph.microsoft.com/beta/$metadata#policies/permissionGrantPreApprovalPolicies/$entity",
    "id": "71ba13dc-5947-4e59-bcc5-0ad5c339a853",
    "deletedDateTime": null,
    "conditions": [
        {
            "scopeType": "chat",
            "sensitivityLabels": {
                "@odata.type": "#microsoft.graph.enumeratedScopeSensitivityLabels",
                "labelKind": "enumerated",
                "sensitivityLabels": [
                    "d9c43deb-f3e1-4422-9fd6-ccf22a3206b8",
                    "c99dade2-aa54-4890-ac1c-a146fa26bd1e"
                ]
            },
            "permissions": {
                "@odata.type": "#microsoft.graph.allPreApprovedPermissions",
                "permissionKind": "all",
                "permissionType": "application"
            }
        },
        {
            "scopeType": "group",
            "sensitivityLabels": {
                "@odata.type": "#microsoft.graph.allScopeSensitivityLabels",
                "labelKind": "all"
            },
            "permissions": {
                "@odata.type": "#microsoft.graph.enumeratedPreApprovedPermissions",
                "permissionKind": "enumerated",
                "resourceApplicationId": "00000003-0000-0000-c000-000000000000",
                "permissionIds": [
                    "134483aa-3dda-4d65-ac91-b8dda1417875",
                    "9d33613d-f855-483b-bca7-ea63ac9f5485"
                ],
                "permissionType": "application"
            }
        }
    ]
}
```

### Example 2: Create a preapproval policy for group scope and preapprove all permissions from a given API

#### Request

- [HTTP](#tabpanel_2_http)
- [C#](#tabpanel_2_csharp)
- [Go](#tabpanel_2_go)
- [Java](#tabpanel_2_java)
- [JavaScript](#tabpanel_2_javascript)
- [PHP](#tabpanel_2_php)
- [PowerShell](#tabpanel_2_powershell)
- [Python](#tabpanel_2_python)

```http
POST https://graph.microsoft.com/beta/policies/permissionGrantPreApprovalPolicies
Content-Type: application/json

{
    "conditions": [
        {
            "scopeType": "group",
            "sensitivityLabels": {
                "@odata.type": "#microsoft.graph.allScopeSensitivityLabels",
                "labelKind": "all"
            },
            "permissions": {
                "@odata.type": "#microsoft.graph.allPermissionsOnResourceApp",
                "permissionKind": "allPermissionsOnResourceApp",
                "permissionType": "application",
                "resourceApplicationId": "00000003-0000-0000-c000-000000000000"
            }
        }
    ]
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.Models;

var requestBody = new PermissionGrantPreApprovalPolicy
{
	Conditions = new List<PreApprovalDetail>
	{
		new PreApprovalDetail
		{
			ScopeType = ResourceScopeType.Group,
			SensitivityLabels = new AllScopeSensitivityLabels
			{
				OdataType = "#microsoft.graph.allScopeSensitivityLabels",
				LabelKind = LabelKind.All,
			},
			Permissions = new PreApprovedPermissions
			{
				OdataType = "#microsoft.graph.allPermissionsOnResourceApp",
				PermissionKind = PermissionKind.AllPermissionsOnResourceApp,
				PermissionType = PermissionType.Application,
				AdditionalData = new Dictionary<string, object>
				{
					{
						"resourceApplicationId" , "00000003-0000-0000-c000-000000000000"
					},
				},
			},
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Policies.PermissionGrantPreApprovalPolicies.PostAsync(requestBody);
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

requestBody := graphmodels.NewPermissionGrantPreApprovalPolicy()


preApprovalDetail := graphmodels.NewPreApprovalDetail()
scopeType := graphmodels.GROUP_RESOURCESCOPETYPE 
preApprovalDetail.SetScopeType(&scopeType) 
sensitivityLabels := graphmodels.NewAllScopeSensitivityLabels()
labelKind := graphmodels.ALL_LABELKIND 
sensitivityLabels.SetLabelKind(&labelKind) 
preApprovalDetail.SetSensitivityLabels(sensitivityLabels)
permissions := graphmodels.NewPreApprovedPermissions()
permissionKind := graphmodels.ALLPERMISSIONSONRESOURCEAPP_PERMISSIONKIND 
permissions.SetPermissionKind(&permissionKind) 
permissionType := graphmodels.APPLICATION_PERMISSIONTYPE 
permissions.SetPermissionType(&permissionType) 
additionalData := map[string]interface{}{
	"resourceApplicationId" : "00000003-0000-0000-c000-000000000000", 
}
permissions.SetAdditionalData(additionalData)
preApprovalDetail.SetPermissions(permissions)

conditions := []graphmodels.PreApprovalDetailable {
	preApprovalDetail,
}
requestBody.SetConditions(conditions)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
permissionGrantPreApprovalPolicies, err := graphClient.Policies().PermissionGrantPreApprovalPolicies().Post(context.Background(), requestBody, nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

PermissionGrantPreApprovalPolicy permissionGrantPreApprovalPolicy = new PermissionGrantPreApprovalPolicy();
LinkedList<PreApprovalDetail> conditions = new LinkedList<PreApprovalDetail>();
PreApprovalDetail preApprovalDetail = new PreApprovalDetail();
preApprovalDetail.setScopeType(ResourceScopeType.Group);
AllScopeSensitivityLabels sensitivityLabels = new AllScopeSensitivityLabels();
sensitivityLabels.setOdataType("#microsoft.graph.allScopeSensitivityLabels");
sensitivityLabels.setLabelKind(LabelKind.All);
preApprovalDetail.setSensitivityLabels(sensitivityLabels);
PreApprovedPermissions permissions = new PreApprovedPermissions();
permissions.setOdataType("#microsoft.graph.allPermissionsOnResourceApp");
permissions.setPermissionKind(PermissionKind.AllPermissionsOnResourceApp);
permissions.setPermissionType(PermissionType.Application);
HashMap<String, Object> additionalData = new HashMap<String, Object>();
additionalData.put("resourceApplicationId", "00000003-0000-0000-c000-000000000000");
permissions.setAdditionalData(additionalData);
preApprovalDetail.setPermissions(permissions);
conditions.add(preApprovalDetail);
permissionGrantPreApprovalPolicy.setConditions(conditions);
PermissionGrantPreApprovalPolicy result = graphClient.policies().permissionGrantPreApprovalPolicies().post(permissionGrantPreApprovalPolicy);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const permissionGrantPreApprovalPolicy = {
    conditions: [
        {
            scopeType: 'group',
            sensitivityLabels: {
                '@odata.type': '#microsoft.graph.allScopeSensitivityLabels',
                labelKind: 'all'
            },
            permissions: {
                '@odata.type': '#microsoft.graph.allPermissionsOnResourceApp',
                permissionKind: 'allPermissionsOnResourceApp',
                permissionType: 'application',
                resourceApplicationId: '00000003-0000-0000-c000-000000000000'
            }
        }
    ]
};

await client.api('/policies/permissionGrantPreApprovalPolicies')
	.version('beta')
	.post(permissionGrantPreApprovalPolicy);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Models\PermissionGrantPreApprovalPolicy;
use Microsoft\Graph\Beta\Generated\Models\PreApprovalDetail;
use Microsoft\Graph\Beta\Generated\Models\ResourceScopeType;
use Microsoft\Graph\Beta\Generated\Models\AllScopeSensitivityLabels;
use Microsoft\Graph\Beta\Generated\Models\LabelKind;
use Microsoft\Graph\Beta\Generated\Models\PreApprovedPermissions;
use Microsoft\Graph\Beta\Generated\Models\PermissionKind;
use Microsoft\Graph\Beta\Generated\Models\PermissionType;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new PermissionGrantPreApprovalPolicy();
$conditionsPreApprovalDetail1 = new PreApprovalDetail();
$conditionsPreApprovalDetail1->setScopeType(new ResourceScopeType('group'));
$conditionsPreApprovalDetail1SensitivityLabels = new AllScopeSensitivityLabels();
$conditionsPreApprovalDetail1SensitivityLabels->setOdataType('#microsoft.graph.allScopeSensitivityLabels');
$conditionsPreApprovalDetail1SensitivityLabels->setLabelKind(new LabelKind('all'));
$conditionsPreApprovalDetail1->setSensitivityLabels($conditionsPreApprovalDetail1SensitivityLabels);
$conditionsPreApprovalDetail1Permissions = new PreApprovedPermissions();
$conditionsPreApprovalDetail1Permissions->setOdataType('#microsoft.graph.allPermissionsOnResourceApp');
$conditionsPreApprovalDetail1Permissions->setPermissionKind(new PermissionKind('allPermissionsOnResourceApp'));
$conditionsPreApprovalDetail1Permissions->setPermissionType(new PermissionType('application'));
$additionalData = [
	'resourceApplicationId' => '00000003-0000-0000-c000-000000000000',
];
$conditionsPreApprovalDetail1Permissions->setAdditionalData($additionalData);
$conditionsPreApprovalDetail1->setPermissions($conditionsPreApprovalDetail1Permissions);
$conditionsArray []= $conditionsPreApprovalDetail1;
$requestBody->setConditions($conditionsArray);


$result = $graphServiceClient->policies()->permissionGrantPreApprovalPolicies()->post($requestBody)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Beta.Identity.SignIns

$params = @{
	conditions = @(
		@{
			scopeType = "group"
			sensitivityLabels = @{
				"@odata.type" = "#microsoft.graph.allScopeSensitivityLabels"
				labelKind = "all"
			}
			permissions = @{
				"@odata.type" = "#microsoft.graph.allPermissionsOnResourceApp"
				permissionKind = "allPermissionsOnResourceApp"
				permissionType = "application"
				resourceApplicationId = "00000003-0000-0000-c000-000000000000"
			}
		}
	)
}

New-MgBetaPolicyPermissionGrantPreApprovalPolicy -BodyParameter $params
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.models.permission_grant_pre_approval_policy import PermissionGrantPreApprovalPolicy
from msgraph_beta.generated.models.pre_approval_detail import PreApprovalDetail
from msgraph_beta.generated.models.resource_scope_type import ResourceScopeType
from msgraph_beta.generated.models.all_scope_sensitivity_labels import AllScopeSensitivityLabels
from msgraph_beta.generated.models.label_kind import LabelKind
from msgraph_beta.generated.models.pre_approved_permissions import PreApprovedPermissions
from msgraph_beta.generated.models.permission_kind import PermissionKind
from msgraph_beta.generated.models.permission_type import PermissionType
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = PermissionGrantPreApprovalPolicy(
	conditions = [
		PreApprovalDetail(
			scope_type = ResourceScopeType.Group,
			sensitivity_labels = AllScopeSensitivityLabels(
				odata_type = "#microsoft.graph.allScopeSensitivityLabels",
				label_kind = LabelKind.All,
			),
			permissions = PreApprovedPermissions(
				odata_type = "#microsoft.graph.allPermissionsOnResourceApp",
				permission_kind = PermissionKind.AllPermissionsOnResourceApp,
				permission_type = PermissionType.Application,
				additional_data = {
						"resource_application_id" : "00000003-0000-0000-c000-000000000000",
				}
			),
		),
	],
)

result = await graph_client.policies.permission_grant_pre_approval_policies.post(request_body)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-Type: application/json

{
    "@odata.context": "https://graph.microsoft.com/beta/$metadata#policies/permissionGrantPreApprovalPolicies/$entity",
    "id": "81cc4c53-1333-47b3-9fa5-1963876e0c5c",
    "deletedDateTime": null,
    "conditions": [
        {
            "scopeType": "group",
            "sensitivityLabels": {
                "@odata.type": "#microsoft.graph.allScopeSensitivityLabels",
                "labelKind": "all"
            },
            "permissions": {
                "@odata.type": "#microsoft.graph.allPermissionsOnResourceApp",
                "permissionKind": "allPermissionsOnResourceApp",
                "permissionType": "application",
                "resourceApplicationId": "00000003-0000-0000-c000-000000000000"
            }
        }
    ]
}
```
