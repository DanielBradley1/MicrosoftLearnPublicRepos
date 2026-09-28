<!-- Source: https://learn.microsoft.com/en-us/graph/api/group-assignlicense?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-11-30 -->

# group: assignLicense

Namespace: microsoft.graph

Add or remove licenses on a [group](https://learn.microsoft.com/en-us/graph/api/resources/group?view=graph-rest-1.0). Licenses assigned to the group will be assigned to all users in the group. Group-based licensing is an alternative to [direct user licensing](https://learn.microsoft.com/en-us/graph/api/user-assignlicense?view=graph-rest-1.0). To learn more about group-based licensing, see [What is group-based licensing in Microsoft Entra ID](https://learn.microsoft.com/en-us/azure/active-directory/fundamentals/active-directory-licensing-whatis-azure-portal).

To get the subscriptions available in the directory, perform a [GET subscribedSkus request](https://learn.microsoft.com/en-us/graph/api/resources/subscribedsku?view=graph-rest-1.0).

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | LicenseAssignment.ReadWrite.All | Directory.ReadWrite.All, Group.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | LicenseAssignment.ReadWrite.All | Directory.ReadWrite.All, Group.ReadWrite.All |

Important

In delegated scenarios with work or school accounts, the signed-in user must be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) or a custom role with the `microsoft.directory/groups/assignLicense` role permission. The following least privileged roles are supported for this operation:

- Directory Writers
- Groups Administrator
- License Administrator
- User Administrator

## HTTP request

```http
POST /groups/{id}/assignLicense
```

## Request headers

| Header | Value |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, provide a JSON object with the following parameters.

| Parameter | Type | Description |
| :--- | :--- | :--- |
| addLicenses | [assignedLicense](https://learn.microsoft.com/en-us/graph/api/resources/assignedlicense?view=graph-rest-1.0) collection | A collection of [assignedLicense](https://learn.microsoft.com/en-us/graph/api/resources/assignedlicense?view=graph-rest-1.0) objects that specify the licenses to add. You can disable servicePlans associated with a license by setting the **disabledPlans** property on an [assignedLicense](https://learn.microsoft.com/en-us/graph/api/resources/assignedlicense?view=graph-rest-1.0) object. |
| removeLicenses | Guid collection | A collection of skuIds that identify the licenses to remove. Required. Can be an empty collection. |

## Response

If successful, this method returns a `202 Accepted` response code and a target [group](https://learn.microsoft.com/en-us/graph/api/resources/group?view=graph-rest-1.0) object in the response body.

## Examples

### Example 1: Add licenses to the group

The following example adds licenses to the group.

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
POST https://graph.microsoft.com/v1.0/groups/1132b215-826f-42a9-8cfe-1643d19d17fd/assignLicense
Content-type: application/json

{
  "addLicenses": [
    {
      "disabledPlans": [
        "113feb6c-3fe4-4440-bddc-54d774bf0318",
        "14ab5db5-e6c4-4b20-b4bc-13e36fd2227f"
      ],
      "skuId": "b05e124f-c7cc-45a0-a6aa-8cf78c946968"
    },
    {
      "disabledPlans": [
        "a413a9ff-720c-4822-98ef-2f37c2a21f4c"
      ],
      "skuId": "c7df2760-2c81-4ef7-b578-5b5392b571df"
    }
  ],
  "removeLicenses": []
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Groups.Item.AssignLicense;
using Microsoft.Graph.Models;

var requestBody = new AssignLicensePostRequestBody
{
	AddLicenses = new List<AssignedLicense>
	{
		new AssignedLicense
		{
			DisabledPlans = new List<Guid?>
			{
				Guid.Parse("113feb6c-3fe4-4440-bddc-54d774bf0318"),
				Guid.Parse("14ab5db5-e6c4-4b20-b4bc-13e36fd2227f"),
			},
			SkuId = Guid.Parse("b05e124f-c7cc-45a0-a6aa-8cf78c946968"),
		},
		new AssignedLicense
		{
			DisabledPlans = new List<Guid?>
			{
				Guid.Parse("a413a9ff-720c-4822-98ef-2f37c2a21f4c"),
			},
			SkuId = Guid.Parse("c7df2760-2c81-4ef7-b578-5b5392b571df"),
		},
	},
	RemoveLicenses = new List<string>
	{
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Groups["{group-id}"].AssignLicense.PostAsync(requestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphgroups "github.com/microsoftgraph/msgraph-sdk-go/groups"
	  graphmodels "github.com/microsoftgraph/msgraph-sdk-go/models"
	  //other-imports
)

requestBody := graphgroups.NewAssignLicensePostRequestBody()


assignedLicense := graphmodels.NewAssignedLicense()
disabledPlans := []uuid.UUID {
	uuid.MustParse("113feb6c-3fe4-4440-bddc-54d774bf0318"),
	uuid.MustParse("14ab5db5-e6c4-4b20-b4bc-13e36fd2227f"),
}
assignedLicense.SetDisabledPlans(disabledPlans)
skuId := uuid.MustParse("b05e124f-c7cc-45a0-a6aa-8cf78c946968")
assignedLicense.SetSkuId(&skuId) 
assignedLicense1 := graphmodels.NewAssignedLicense()
disabledPlans := []uuid.UUID {
	uuid.MustParse("a413a9ff-720c-4822-98ef-2f37c2a21f4c"),
}
assignedLicense1.SetDisabledPlans(disabledPlans)
skuId := uuid.MustParse("c7df2760-2c81-4ef7-b578-5b5392b571df")
assignedLicense1.SetSkuId(&skuId) 

addLicenses := []graphmodels.AssignedLicenseable {
	assignedLicense,
	assignedLicense1,
}
requestBody.SetAddLicenses(addLicenses)
removeLicenses := []string {

}
requestBody.SetRemoveLicenses(removeLicenses)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
assignLicense, err := graphClient.Groups().ByGroupId("group-id").AssignLicense().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.groups.item.assignlicense.AssignLicensePostRequestBody assignLicensePostRequestBody = new com.microsoft.graph.groups.item.assignlicense.AssignLicensePostRequestBody();
LinkedList<AssignedLicense> addLicenses = new LinkedList<AssignedLicense>();
AssignedLicense assignedLicense = new AssignedLicense();
LinkedList<UUID> disabledPlans = new LinkedList<UUID>();
disabledPlans.add(UUID.fromString("113feb6c-3fe4-4440-bddc-54d774bf0318"));
disabledPlans.add(UUID.fromString("14ab5db5-e6c4-4b20-b4bc-13e36fd2227f"));
assignedLicense.setDisabledPlans(disabledPlans);
assignedLicense.setSkuId(UUID.fromString("b05e124f-c7cc-45a0-a6aa-8cf78c946968"));
addLicenses.add(assignedLicense);
AssignedLicense assignedLicense1 = new AssignedLicense();
LinkedList<UUID> disabledPlans1 = new LinkedList<UUID>();
disabledPlans1.add(UUID.fromString("a413a9ff-720c-4822-98ef-2f37c2a21f4c"));
assignedLicense1.setDisabledPlans(disabledPlans1);
assignedLicense1.setSkuId(UUID.fromString("c7df2760-2c81-4ef7-b578-5b5392b571df"));
addLicenses.add(assignedLicense1);
assignLicensePostRequestBody.setAddLicenses(addLicenses);
LinkedList<String> removeLicenses = new LinkedList<String>();
assignLicensePostRequestBody.setRemoveLicenses(removeLicenses);
var result = graphClient.groups().byGroupId("{group-id}").assignLicense().post(assignLicensePostRequestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const group = {
  addLicenses: [
    {
      disabledPlans: [
        '113feb6c-3fe4-4440-bddc-54d774bf0318',
        '14ab5db5-e6c4-4b20-b4bc-13e36fd2227f'
      ],
      skuId: 'b05e124f-c7cc-45a0-a6aa-8cf78c946968'
    },
    {
      disabledPlans: [
        'a413a9ff-720c-4822-98ef-2f37c2a21f4c'
      ],
      skuId: 'c7df2760-2c81-4ef7-b578-5b5392b571df'
    }
  ],
  removeLicenses: []
};

await client.api('/groups/1132b215-826f-42a9-8cfe-1643d19d17fd/assignLicense')
	.post(group);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Groups\Item\AssignLicense\AssignLicensePostRequestBody;
use Microsoft\Graph\Generated\Models\AssignedLicense;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new AssignLicensePostRequestBody();
$addLicensesAssignedLicense1 = new AssignedLicense();
$addLicensesAssignedLicense1->setDisabledPlans(['113feb6c-3fe4-4440-bddc-54d774bf0318', '14ab5db5-e6c4-4b20-b4bc-13e36fd2227f', 	]);
$addLicensesAssignedLicense1->setSkuId('b05e124f-c7cc-45a0-a6aa-8cf78c946968');
$addLicensesArray []= $addLicensesAssignedLicense1;
$addLicensesAssignedLicense2 = new AssignedLicense();
$addLicensesAssignedLicense2->setDisabledPlans(['a413a9ff-720c-4822-98ef-2f37c2a21f4c', 	]);
$addLicensesAssignedLicense2->setSkuId('c7df2760-2c81-4ef7-b578-5b5392b571df');
$addLicensesArray []= $addLicensesAssignedLicense2;
$requestBody->setAddLicenses($addLicensesArray);

$requestBody->setRemoveLicenses([]);

$result = $graphServiceClient->groups()->byGroupId('group-id')->assignLicense()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Groups

$params = @{
	addLicenses = @(
		@{
			disabledPlans = @(
			"113feb6c-3fe4-4440-bddc-54d774bf0318"
		"14ab5db5-e6c4-4b20-b4bc-13e36fd2227f"
	)
	skuId = "b05e124f-c7cc-45a0-a6aa-8cf78c946968"
}
@{
	disabledPlans = @(
	"a413a9ff-720c-4822-98ef-2f37c2a21f4c"
)
skuId = "c7df2760-2c81-4ef7-b578-5b5392b571df"
}
)
removeLicenses = @(
)
}

Set-MgGroupLicense -GroupId $groupId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.groups.item.assign_license.assign_license_post_request_body import AssignLicensePostRequestBody
from msgraph.generated.models.assigned_license import AssignedLicense
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = AssignLicensePostRequestBody(
	add_licenses = [
		AssignedLicense(
			disabled_plans = [
				UUID("113feb6c-3fe4-4440-bddc-54d774bf0318"),
				UUID("14ab5db5-e6c4-4b20-b4bc-13e36fd2227f"),
			],
			sku_id = UUID("b05e124f-c7cc-45a0-a6aa-8cf78c946968"),
		),
		AssignedLicense(
			disabled_plans = [
				UUID("a413a9ff-720c-4822-98ef-2f37c2a21f4c"),
			],
			sku_id = UUID("c7df2760-2c81-4ef7-b578-5b5392b571df"),
		),
	],
	remove_licenses = [
	],
)

result = await graph_client.groups.by_group_id('group-id').assign_license.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The response is the updated group object.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 202 Accepted
Content-type: application/json
location: https://graph.microsoft.com/v2/e8e96c2a-d787-4eb1-98d7-9e57c965f1de/directoryObjects/1132b215-826f-42a9-8cfe-1643d19d17fd/Microsoft.DirectoryServices.Group

{
  "id": "1132b215-826f-42a9-8cfe-1643d19d17fd",
  "createdDateTime": "2021-03-12T11:15:03Z",
  "groupTypes": [],
  "securityEnabled": true
}
```

### Example 2: Remove licenses from the group

The following example removes licenses from the group.

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
POST https://graph.microsoft.com/v1.0/groups/1132b215-826f-42a9-8cfe-1643d19d17fd/assignLicense
Content-type: application/json

{
  "addLicenses": [],
  "removeLicenses": [
    "c7df2760-2c81-4ef7-b578-5b5392b571df",
    "b05e124f-c7cc-45a0-a6aa-8cf78c946968"
  ]
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Groups.Item.AssignLicense;
using Microsoft.Graph.Models;

var requestBody = new AssignLicensePostRequestBody
{
	AddLicenses = new List<AssignedLicense>
	{
	},
	RemoveLicenses = new List<Guid?>
	{
		Guid.Parse("c7df2760-2c81-4ef7-b578-5b5392b571df"),
		Guid.Parse("b05e124f-c7cc-45a0-a6aa-8cf78c946968"),
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Groups["{group-id}"].AssignLicense.PostAsync(requestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphgroups "github.com/microsoftgraph/msgraph-sdk-go/groups"
	  graphmodels "github.com/microsoftgraph/msgraph-sdk-go/models"
	  //other-imports
)

requestBody := graphgroups.NewAssignLicensePostRequestBody()
addLicenses := []graphmodels.AssignedLicenseable {

}
requestBody.SetAddLicenses(addLicenses)
removeLicenses := []uuid.UUID {
	uuid.MustParse("c7df2760-2c81-4ef7-b578-5b5392b571df"),
	uuid.MustParse("b05e124f-c7cc-45a0-a6aa-8cf78c946968"),
}
requestBody.SetRemoveLicenses(removeLicenses)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
assignLicense, err := graphClient.Groups().ByGroupId("group-id").AssignLicense().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.groups.item.assignlicense.AssignLicensePostRequestBody assignLicensePostRequestBody = new com.microsoft.graph.groups.item.assignlicense.AssignLicensePostRequestBody();
LinkedList<AssignedLicense> addLicenses = new LinkedList<AssignedLicense>();
assignLicensePostRequestBody.setAddLicenses(addLicenses);
LinkedList<UUID> removeLicenses = new LinkedList<UUID>();
removeLicenses.add(UUID.fromString("c7df2760-2c81-4ef7-b578-5b5392b571df"));
removeLicenses.add(UUID.fromString("b05e124f-c7cc-45a0-a6aa-8cf78c946968"));
assignLicensePostRequestBody.setRemoveLicenses(removeLicenses);
var result = graphClient.groups().byGroupId("{group-id}").assignLicense().post(assignLicensePostRequestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const group = {
  addLicenses: [],
  removeLicenses: [
    'c7df2760-2c81-4ef7-b578-5b5392b571df',
    'b05e124f-c7cc-45a0-a6aa-8cf78c946968'
  ]
};

await client.api('/groups/1132b215-826f-42a9-8cfe-1643d19d17fd/assignLicense')
	.post(group);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Groups\Item\AssignLicense\AssignLicensePostRequestBody;
use Microsoft\Graph\Generated\Models\AssignedLicense;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new AssignLicensePostRequestBody();
$requestBody->setAddLicenses([	]);
$requestBody->setRemoveLicenses(['c7df2760-2c81-4ef7-b578-5b5392b571df', 'b05e124f-c7cc-45a0-a6aa-8cf78c946968', 	]);

$result = $graphServiceClient->groups()->byGroupId('group-id')->assignLicense()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Groups

$params = @{
	addLicenses = @(
	)
	removeLicenses = @(
	"c7df2760-2c81-4ef7-b578-5b5392b571df"
"b05e124f-c7cc-45a0-a6aa-8cf78c946968"
)
}

Set-MgGroupLicense -GroupId $groupId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.groups.item.assign_license.assign_license_post_request_body import AssignLicensePostRequestBody
from msgraph.generated.models.assigned_license import AssignedLicense
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = AssignLicensePostRequestBody(
	add_licenses = [
	],
	remove_licenses = [
		UUID("c7df2760-2c81-4ef7-b578-5b5392b571df"),
		UUID("b05e124f-c7cc-45a0-a6aa-8cf78c946968"),
	],
)

result = await graph_client.groups.by_group_id('group-id').assign_license.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The response is the updated group object.

> **Note:** The response object shown here might be shortened for readability..

```http
HTTP/1.1 202 Accepted
Content-type: application/json
location: https://graph.microsoft.com/v2/d056d009-17b3-4106-8173-cd3978ada898/directoryObjects/1ad75eeb-7e5a-4367-a493-9214d90d54d0/Microsoft.DirectoryServices.Group


{
  "id": "1ad75eeb-7e5a-4367-a493-9214d90d54d0",
  "deletedDateTime": null,
  "classification": null,
  "createdDateTime": "2018-04-18T22:05:03Z",
  "securityEnabled": true

}
```
