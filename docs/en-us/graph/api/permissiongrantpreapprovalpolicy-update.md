<!-- Source: https://learn.microsoft.com/en-us/graph/api/permissiongrantpreapprovalpolicy-update?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-11-08 -->

# Update permissionGrantPreApprovalPolicy

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Update the properties of a [permissionGrantPreApprovalPolicy](https://learn.microsoft.com/en-us/graph/api/resources/permissiongrantpreapprovalpolicy?view=graph-rest-beta) object.

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
PATCH /policies/permissionGrantPreApprovalPolicies/{id}
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
| conditions | [preApprovalDetail](https://learn.microsoft.com/en-us/graph/api/resources/preapprovaldetail?view=graph-rest-beta) collection | A list of conditions that are preapproved in the policy. Required. |

## Response

If successful, this method returns a `200 OK` response code and an updated [permissionGrantPreApprovalPolicy](https://learn.microsoft.com/en-us/graph/api/resources/permissiongrantpreapprovalpolicy?view=graph-rest-beta) object in the response body.

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
PATCH https://graph.microsoft.com/beta/policies/permissionGrantPreApprovalPolicies/71ba13dc-5947-4e59-bcc5-0ad5c339a853
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
                    "d9c43deb-f3e1-4422-9fd6-ccf22a3206b8"
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

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.Models;

var requestBody = new PermissionGrantPreApprovalPolicy
{
	Id = "71ba13dc-5947-4e59-bcc5-0ad5c339a853",
	DeletedDateTime = null,
	Conditions = new List<PreApprovalDetail>
	{
		new PreApprovalDetail
		{
			ScopeType = ResourceScopeType.Chat,
			SensitivityLabels = new EnumeratedScopeSensitivityLabels
			{
				OdataType = "#microsoft.graph.enumeratedScopeSensitivityLabels",
				LabelKind = LabelKind.Enumerated,
				SensitivityLabels = new List<string>
				{
					"d9c43deb-f3e1-4422-9fd6-ccf22a3206b8",
				},
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
			SensitivityLabels = new AllScopeSensitivityLabels
			{
				OdataType = "#microsoft.graph.allScopeSensitivityLabels",
				LabelKind = LabelKind.All,
			},
			Permissions = new EnumeratedPreApprovedPermissions
			{
				OdataType = "#microsoft.graph.enumeratedPreApprovedPermissions",
				PermissionKind = PermissionKind.Enumerated,
				ResourceApplicationId = "00000003-0000-0000-c000-000000000000",
				PermissionIds = new List<string>
				{
					"134483aa-3dda-4d65-ac91-b8dda1417875",
					"9d33613d-f855-483b-bca7-ea63ac9f5485",
				},
				PermissionType = PermissionType.Application,
			},
		},
	},
	AdditionalData = new Dictionary<string, object>
	{
		{
			"@odata.context" , "https://graph.microsoft.com/beta/$metadata#policies/permissionGrantPreApprovalPolicies/$entity"
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Policies.PermissionGrantPreApprovalPolicies["{permissionGrantPreApprovalPolicy-id}"].PatchAsync(requestBody);
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
id := "71ba13dc-5947-4e59-bcc5-0ad5c339a853"
requestBody.SetId(&id) 
deletedDateTime := null
requestBody.SetDeletedDateTime(&deletedDateTime) 


preApprovalDetail := graphmodels.NewPreApprovalDetail()
scopeType := graphmodels.CHAT_RESOURCESCOPETYPE 
preApprovalDetail.SetScopeType(&scopeType) 
sensitivityLabels := graphmodels.NewEnumeratedScopeSensitivityLabels()
labelKind := graphmodels.ENUMERATED_LABELKIND 
sensitivityLabels.SetLabelKind(&labelKind) 
sensitivityLabels := []string {
	"d9c43deb-f3e1-4422-9fd6-ccf22a3206b8",
}
sensitivityLabels.SetSensitivityLabels(sensitivityLabels)
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
sensitivityLabels := graphmodels.NewAllScopeSensitivityLabels()
labelKind := graphmodels.ALL_LABELKIND 
sensitivityLabels.SetLabelKind(&labelKind) 
preApprovalDetail1.SetSensitivityLabels(sensitivityLabels)
permissions := graphmodels.NewEnumeratedPreApprovedPermissions()
permissionKind := graphmodels.ENUMERATED_PERMISSIONKIND 
permissions.SetPermissionKind(&permissionKind) 
resourceApplicationId := "00000003-0000-0000-c000-000000000000"
permissions.SetResourceApplicationId(&resourceApplicationId) 
permissionIds := []string {
	"134483aa-3dda-4d65-ac91-b8dda1417875",
	"9d33613d-f855-483b-bca7-ea63ac9f5485",
}
permissions.SetPermissionIds(permissionIds)
permissionType := graphmodels.APPLICATION_PERMISSIONTYPE 
permissions.SetPermissionType(&permissionType) 
preApprovalDetail1.SetPermissions(permissions)

conditions := []graphmodels.PreApprovalDetailable {
	preApprovalDetail,
	preApprovalDetail1,
}
requestBody.SetConditions(conditions)
additionalData := map[string]interface{}{
	"@odata.context" : "https://graph.microsoft.com/beta/$metadata#policies/permissionGrantPreApprovalPolicies/$entity", 
}
requestBody.SetAdditionalData(additionalData)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
permissionGrantPreApprovalPolicies, err := graphClient.Policies().PermissionGrantPreApprovalPolicies().ByPermissionGrantPreApprovalPolicyId("permissionGrantPreApprovalPolicy-id").Patch(context.Background(), requestBody, nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

PermissionGrantPreApprovalPolicy permissionGrantPreApprovalPolicy = new PermissionGrantPreApprovalPolicy();
permissionGrantPreApprovalPolicy.setId("71ba13dc-5947-4e59-bcc5-0ad5c339a853");
permissionGrantPreApprovalPolicy.setDeletedDateTime(null);
LinkedList<PreApprovalDetail> conditions = new LinkedList<PreApprovalDetail>();
PreApprovalDetail preApprovalDetail = new PreApprovalDetail();
preApprovalDetail.setScopeType(ResourceScopeType.Chat);
EnumeratedScopeSensitivityLabels sensitivityLabels = new EnumeratedScopeSensitivityLabels();
sensitivityLabels.setOdataType("#microsoft.graph.enumeratedScopeSensitivityLabels");
sensitivityLabels.setLabelKind(LabelKind.Enumerated);
LinkedList<String> sensitivityLabels1 = new LinkedList<String>();
sensitivityLabels1.add("d9c43deb-f3e1-4422-9fd6-ccf22a3206b8");
sensitivityLabels.setSensitivityLabels(sensitivityLabels1);
preApprovalDetail.setSensitivityLabels(sensitivityLabels);
AllPreApprovedPermissions permissions = new AllPreApprovedPermissions();
permissions.setOdataType("#microsoft.graph.allPreApprovedPermissions");
permissions.setPermissionKind(PermissionKind.All);
permissions.setPermissionType(PermissionType.Application);
preApprovalDetail.setPermissions(permissions);
conditions.add(preApprovalDetail);
PreApprovalDetail preApprovalDetail1 = new PreApprovalDetail();
preApprovalDetail1.setScopeType(ResourceScopeType.Group);
AllScopeSensitivityLabels sensitivityLabels2 = new AllScopeSensitivityLabels();
sensitivityLabels2.setOdataType("#microsoft.graph.allScopeSensitivityLabels");
sensitivityLabels2.setLabelKind(LabelKind.All);
preApprovalDetail1.setSensitivityLabels(sensitivityLabels2);
EnumeratedPreApprovedPermissions permissions1 = new EnumeratedPreApprovedPermissions();
permissions1.setOdataType("#microsoft.graph.enumeratedPreApprovedPermissions");
permissions1.setPermissionKind(PermissionKind.Enumerated);
permissions1.setResourceApplicationId("00000003-0000-0000-c000-000000000000");
LinkedList<String> permissionIds = new LinkedList<String>();
permissionIds.add("134483aa-3dda-4d65-ac91-b8dda1417875");
permissionIds.add("9d33613d-f855-483b-bca7-ea63ac9f5485");
permissions1.setPermissionIds(permissionIds);
permissions1.setPermissionType(PermissionType.Application);
preApprovalDetail1.setPermissions(permissions1);
conditions.add(preApprovalDetail1);
permissionGrantPreApprovalPolicy.setConditions(conditions);
HashMap<String, Object> additionalData = new HashMap<String, Object>();
additionalData.put("@odata.context", "https://graph.microsoft.com/beta/$metadata#policies/permissionGrantPreApprovalPolicies/$entity");
permissionGrantPreApprovalPolicy.setAdditionalData(additionalData);
PermissionGrantPreApprovalPolicy result = graphClient.policies().permissionGrantPreApprovalPolicies().byPermissionGrantPreApprovalPolicyId("{permissionGrantPreApprovalPolicy-id}").patch(permissionGrantPreApprovalPolicy);
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
    '@odata.context': 'https://graph.microsoft.com/beta/$metadata#policies/permissionGrantPreApprovalPolicies/$entity',
    id: '71ba13dc-5947-4e59-bcc5-0ad5c339a853',
    deletedDateTime: null,
    conditions: [
        {
            scopeType: 'chat',
            sensitivityLabels: {
                '@odata.type': '#microsoft.graph.enumeratedScopeSensitivityLabels',
                labelKind: 'enumerated',
                sensitivityLabels: [
                    'd9c43deb-f3e1-4422-9fd6-ccf22a3206b8'
                ]
            },
            permissions: {
                '@odata.type': '#microsoft.graph.allPreApprovedPermissions',
                permissionKind: 'all',
                permissionType: 'application'
            }
        },
        {
            scopeType: 'group',
            sensitivityLabels: {
                '@odata.type': '#microsoft.graph.allScopeSensitivityLabels',
                labelKind: 'all'
            },
            permissions: {
                '@odata.type': '#microsoft.graph.enumeratedPreApprovedPermissions',
                permissionKind: 'enumerated',
                resourceApplicationId: '00000003-0000-0000-c000-000000000000',
                permissionIds: [
                    '134483aa-3dda-4d65-ac91-b8dda1417875',
                    '9d33613d-f855-483b-bca7-ea63ac9f5485'
                ],
                permissionType: 'application'
            }
        }
    ]
};

await client.api('/policies/permissionGrantPreApprovalPolicies/71ba13dc-5947-4e59-bcc5-0ad5c339a853')
	.version('beta')
	.update(permissionGrantPreApprovalPolicy);
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
use Microsoft\Graph\Beta\Generated\Models\EnumeratedScopeSensitivityLabels;
use Microsoft\Graph\Beta\Generated\Models\LabelKind;
use Microsoft\Graph\Beta\Generated\Models\AllPreApprovedPermissions;
use Microsoft\Graph\Beta\Generated\Models\PermissionKind;
use Microsoft\Graph\Beta\Generated\Models\PermissionType;
use Microsoft\Graph\Beta\Generated\Models\AllScopeSensitivityLabels;
use Microsoft\Graph\Beta\Generated\Models\EnumeratedPreApprovedPermissions;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new PermissionGrantPreApprovalPolicy();
$requestBody->setId('71ba13dc-5947-4e59-bcc5-0ad5c339a853');
$requestBody->setDeletedDateTime(null);
$conditionsPreApprovalDetail1 = new PreApprovalDetail();
$conditionsPreApprovalDetail1->setScopeType(new ResourceScopeType('chat'));
$conditionsPreApprovalDetail1SensitivityLabels = new EnumeratedScopeSensitivityLabels();
$conditionsPreApprovalDetail1SensitivityLabels->setOdataType('#microsoft.graph.enumeratedScopeSensitivityLabels');
$conditionsPreApprovalDetail1SensitivityLabels->setLabelKind(new LabelKind('enumerated'));
$conditionsPreApprovalDetail1SensitivityLabels->setSensitivityLabels(['d9c43deb-f3e1-4422-9fd6-ccf22a3206b8', 	]);
$conditionsPreApprovalDetail1->setSensitivityLabels($conditionsPreApprovalDetail1SensitivityLabels);
$conditionsPreApprovalDetail1Permissions = new AllPreApprovedPermissions();
$conditionsPreApprovalDetail1Permissions->setOdataType('#microsoft.graph.allPreApprovedPermissions');
$conditionsPreApprovalDetail1Permissions->setPermissionKind(new PermissionKind('all'));
$conditionsPreApprovalDetail1Permissions->setPermissionType(new PermissionType('application'));
$conditionsPreApprovalDetail1->setPermissions($conditionsPreApprovalDetail1Permissions);
$conditionsArray []= $conditionsPreApprovalDetail1;
$conditionsPreApprovalDetail2 = new PreApprovalDetail();
$conditionsPreApprovalDetail2->setScopeType(new ResourceScopeType('group'));
$conditionsPreApprovalDetail2SensitivityLabels = new AllScopeSensitivityLabels();
$conditionsPreApprovalDetail2SensitivityLabels->setOdataType('#microsoft.graph.allScopeSensitivityLabels');
$conditionsPreApprovalDetail2SensitivityLabels->setLabelKind(new LabelKind('all'));
$conditionsPreApprovalDetail2->setSensitivityLabels($conditionsPreApprovalDetail2SensitivityLabels);
$conditionsPreApprovalDetail2Permissions = new EnumeratedPreApprovedPermissions();
$conditionsPreApprovalDetail2Permissions->setOdataType('#microsoft.graph.enumeratedPreApprovedPermissions');
$conditionsPreApprovalDetail2Permissions->setPermissionKind(new PermissionKind('enumerated'));
$conditionsPreApprovalDetail2Permissions->setResourceApplicationId('00000003-0000-0000-c000-000000000000');
$conditionsPreApprovalDetail2Permissions->setPermissionIds(['134483aa-3dda-4d65-ac91-b8dda1417875', '9d33613d-f855-483b-bca7-ea63ac9f5485', 	]);
$conditionsPreApprovalDetail2Permissions->setPermissionType(new PermissionType('application'));
$conditionsPreApprovalDetail2->setPermissions($conditionsPreApprovalDetail2Permissions);
$conditionsArray []= $conditionsPreApprovalDetail2;
$requestBody->setConditions($conditionsArray);

$additionalData = [
'@odata.context' => 'https://graph.microsoft.com/beta/$metadata#policies/permissionGrantPreApprovalPolicies/$entity',
];
$requestBody->setAdditionalData($additionalData);

$result = $graphServiceClient->policies()->permissionGrantPreApprovalPolicies()->byPermissionGrantPreApprovalPolicyId('permissionGrantPreApprovalPolicy-id')->patch($requestBody)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Beta.Identity.SignIns

$params = @{
	"@odata.context" = "https://graph.microsoft.com/beta/$metadata#policies/permissionGrantPreApprovalPolicies/$entity"
	id = "71ba13dc-5947-4e59-bcc5-0ad5c339a853"
	deletedDateTime = $null
	conditions = @(
		@{
			scopeType = "chat"
			sensitivityLabels = @{
				"@odata.type" = "#microsoft.graph.enumeratedScopeSensitivityLabels"
				labelKind = "enumerated"
				sensitivityLabels = @(
				"d9c43deb-f3e1-4422-9fd6-ccf22a3206b8"
			)
		}
		permissions = @{
			"@odata.type" = "#microsoft.graph.allPreApprovedPermissions"
			permissionKind = "all"
			permissionType = "application"
		}
	}
	@{
		scopeType = "group"
		sensitivityLabels = @{
			"@odata.type" = "#microsoft.graph.allScopeSensitivityLabels"
			labelKind = "all"
		}
		permissions = @{
			"@odata.type" = "#microsoft.graph.enumeratedPreApprovedPermissions"
			permissionKind = "enumerated"
			resourceApplicationId = "00000003-0000-0000-c000-000000000000"
			permissionIds = @(
			"134483aa-3dda-4d65-ac91-b8dda1417875"
		"9d33613d-f855-483b-bca7-ea63ac9f5485"
	)
	permissionType = "application"
}
}
)
}

Update-MgBetaPolicyPermissionGrantPreApprovalPolicy -PermissionGrantPreApprovalPolicyId $permissionGrantPreApprovalPolicyId -BodyParameter $params
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
from msgraph_beta.generated.models.enumerated_scope_sensitivity_labels import EnumeratedScopeSensitivityLabels
from msgraph_beta.generated.models.label_kind import LabelKind
from msgraph_beta.generated.models.all_pre_approved_permissions import AllPreApprovedPermissions
from msgraph_beta.generated.models.permission_kind import PermissionKind
from msgraph_beta.generated.models.permission_type import PermissionType
from msgraph_beta.generated.models.all_scope_sensitivity_labels import AllScopeSensitivityLabels
from msgraph_beta.generated.models.enumerated_pre_approved_permissions import EnumeratedPreApprovedPermissions
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = PermissionGrantPreApprovalPolicy(
	id = "71ba13dc-5947-4e59-bcc5-0ad5c339a853",
	deleted_date_time = None,
	conditions = [
		PreApprovalDetail(
			scope_type = ResourceScopeType.Chat,
			sensitivity_labels = EnumeratedScopeSensitivityLabels(
				odata_type = "#microsoft.graph.enumeratedScopeSensitivityLabels",
				label_kind = LabelKind.Enumerated,
				sensitivity_labels = [
					"d9c43deb-f3e1-4422-9fd6-ccf22a3206b8",
				],
			),
			permissions = AllPreApprovedPermissions(
				odata_type = "#microsoft.graph.allPreApprovedPermissions",
				permission_kind = PermissionKind.All,
				permission_type = PermissionType.Application,
			),
		),
		PreApprovalDetail(
			scope_type = ResourceScopeType.Group,
			sensitivity_labels = AllScopeSensitivityLabels(
				odata_type = "#microsoft.graph.allScopeSensitivityLabels",
				label_kind = LabelKind.All,
			),
			permissions = EnumeratedPreApprovedPermissions(
				odata_type = "#microsoft.graph.enumeratedPreApprovedPermissions",
				permission_kind = PermissionKind.Enumerated,
				resource_application_id = "00000003-0000-0000-c000-000000000000",
				permission_ids = [
					"134483aa-3dda-4d65-ac91-b8dda1417875",
					"9d33613d-f855-483b-bca7-ea63ac9f5485",
				],
				permission_type = PermissionType.Application,
			),
		),
	],
	additional_data = {
			"@odata_context" : "https://graph.microsoft.com/beta/$metadata#policies/permissionGrantPreApprovalPolicies/$entity",
	}
)

result = await graph_client.policies.permission_grant_pre_approval_policies.by_permission_grant_pre_approval_policy_id('permissionGrantPreApprovalPolicy-id').patch(request_body)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 204 No Content
```
