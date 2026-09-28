<!-- Source: https://learn.microsoft.com/en-us/graph/api/user-assignlicense?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-23 -->

# user: assignLicense

Namespace: microsoft.graph

Add or remove licenses for the user to enable or disable their use of Microsoft cloud offerings that the company has licenses to. For example, an organization can have a Microsoft 365 Enterprise E3 subscription with 100 licenses, and this request assigns one of those licenses to a specific user. You can also enable and disable specific plans associated with a subscription. Direct user licensing method is an alternative to [group-based licensing](https://learn.microsoft.com/en-us/graph/api/group-assignlicense?view=graph-rest-1.0).

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | LicenseAssignment.ReadWrite.All | AgentIdUser.ReadWrite.All, AgentIdUser.ReadWrite.IdentityParentedBy, Directory.ReadWrite.All, User.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | LicenseAssignment.ReadWrite.All | AgentIdUser.ReadWrite.All, AgentIdUser.ReadWrite.IdentityParentedBy, Directory.ReadWrite.All, User.ReadWrite.All |

Important

In delegated scenarios with work or school accounts, the signed-in user must be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) or a custom role with the `microsoft.directory/users/assignLicense` role permission. The following least privileged roles are supported for this operation:

- Directory Writers
- License Administrator
- User Administrator

## HTTP request

```http
POST /users/{id | userPrincipalName}/assignLicense
```

## Request headers

| Header | Value |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json |

## Request body

In the request body, provide a JSON object with the following parameters.

| Parameter | Type | Description |
| :--- | :--- | :--- |
| addLicenses | [assignedLicense](https://learn.microsoft.com/en-us/graph/api/resources/assignedlicense?view=graph-rest-1.0) collection | A collection of [assignedLicense](https://learn.microsoft.com/en-us/graph/api/resources/assignedlicense?view=graph-rest-1.0) objects that specify the licenses to add. You can disable servicePlans associated with a license by setting the **disabledPlans** property on an [assignedLicense](https://learn.microsoft.com/en-us/graph/api/resources/assignedlicense?view=graph-rest-1.0) object. |
| removeLicenses | Guid collection | A collection of skuIds that identify the licenses to remove. Required. Can be an empty collection. |

## Response

If successful, this method returns `200 OK` response code and [user](https://learn.microsoft.com/en-us/graph/api/resources/user?view=graph-rest-1.0) object in the response body.

## Examples

### Example 1: Assign licenses to the signed-in user

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
POST https://graph.microsoft.com/v1.0/me/assignLicense
Content-type: application/json

{
    "addLicenses": [
        {
            "disabledPlans": [
                "8a256a2b-b617-496d-b51b-e76466e88db0"
            ],
            "skuId": "84a661c4-e949-4bd2-a560-ed7766fcaf2b"
        },
        {
            "disabledPlans": [],
            "skuId": "f30db892-07e9-47e9-837c-80727f46fd3d"
        }
    ],
    "removeLicenses": []
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Me.AssignLicense;
using Microsoft.Graph.Models;

var requestBody = new AssignLicensePostRequestBody
{
	AddLicenses = new List<AssignedLicense>
	{
		new AssignedLicense
		{
			DisabledPlans = new List<Guid?>
			{
				Guid.Parse("8a256a2b-b617-496d-b51b-e76466e88db0"),
			},
			SkuId = Guid.Parse("84a661c4-e949-4bd2-a560-ed7766fcaf2b"),
		},
		new AssignedLicense
		{
			DisabledPlans = new List<string>
			{
			},
			SkuId = Guid.Parse("f30db892-07e9-47e9-837c-80727f46fd3d"),
		},
	},
	RemoveLicenses = new List<string>
	{
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Me.AssignLicense.PostAsync(requestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphusers "github.com/microsoftgraph/msgraph-sdk-go/users"
	  graphmodels "github.com/microsoftgraph/msgraph-sdk-go/models"
	  //other-imports
)

requestBody := graphusers.NewItemAssignLicensePostRequestBody()


assignedLicense := graphmodels.NewAssignedLicense()
disabledPlans := []uuid.UUID {
	uuid.MustParse("8a256a2b-b617-496d-b51b-e76466e88db0"),
}
assignedLicense.SetDisabledPlans(disabledPlans)
skuId := uuid.MustParse("84a661c4-e949-4bd2-a560-ed7766fcaf2b")
assignedLicense.SetSkuId(&skuId) 
assignedLicense1 := graphmodels.NewAssignedLicense()
disabledPlans := []string {

}
assignedLicense1.SetDisabledPlans(disabledPlans)
skuId := uuid.MustParse("f30db892-07e9-47e9-837c-80727f46fd3d")
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
assignLicense, err := graphClient.Me().AssignLicense().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.users.item.assignlicense.AssignLicensePostRequestBody assignLicensePostRequestBody = new com.microsoft.graph.users.item.assignlicense.AssignLicensePostRequestBody();
LinkedList<AssignedLicense> addLicenses = new LinkedList<AssignedLicense>();
AssignedLicense assignedLicense = new AssignedLicense();
LinkedList<UUID> disabledPlans = new LinkedList<UUID>();
disabledPlans.add(UUID.fromString("8a256a2b-b617-496d-b51b-e76466e88db0"));
assignedLicense.setDisabledPlans(disabledPlans);
assignedLicense.setSkuId(UUID.fromString("84a661c4-e949-4bd2-a560-ed7766fcaf2b"));
addLicenses.add(assignedLicense);
AssignedLicense assignedLicense1 = new AssignedLicense();
LinkedList<String> disabledPlans1 = new LinkedList<String>();
assignedLicense1.setDisabledPlans(disabledPlans1);
assignedLicense1.setSkuId(UUID.fromString("f30db892-07e9-47e9-837c-80727f46fd3d"));
addLicenses.add(assignedLicense1);
assignLicensePostRequestBody.setAddLicenses(addLicenses);
LinkedList<String> removeLicenses = new LinkedList<String>();
assignLicensePostRequestBody.setRemoveLicenses(removeLicenses);
var result = graphClient.me().assignLicense().post(assignLicensePostRequestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const user = {
    addLicenses: [
        {
            disabledPlans: [
                '8a256a2b-b617-496d-b51b-e76466e88db0'
            ],
            skuId: '84a661c4-e949-4bd2-a560-ed7766fcaf2b'
        },
        {
            disabledPlans: [],
            skuId: 'f30db892-07e9-47e9-837c-80727f46fd3d'
        }
    ],
    removeLicenses: []
};

await client.api('/me/assignLicense')
	.post(user);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Users\Item\AssignLicense\AssignLicensePostRequestBody;
use Microsoft\Graph\Generated\Models\AssignedLicense;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new AssignLicensePostRequestBody();
$addLicensesAssignedLicense1 = new AssignedLicense();
$addLicensesAssignedLicense1->setDisabledPlans(['8a256a2b-b617-496d-b51b-e76466e88db0', 	]);
$addLicensesAssignedLicense1->setSkuId('84a661c4-e949-4bd2-a560-ed7766fcaf2b');
$addLicensesArray []= $addLicensesAssignedLicense1;
$addLicensesAssignedLicense2 = new AssignedLicense();
$addLicensesAssignedLicense2->setDisabledPlans([	]);
$addLicensesAssignedLicense2->setSkuId('f30db892-07e9-47e9-837c-80727f46fd3d');
$addLicensesArray []= $addLicensesAssignedLicense2;
$requestBody->setAddLicenses($addLicensesArray);

$requestBody->setRemoveLicenses([]);

$result = $graphServiceClient->me()->assignLicense()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Users.Actions

$params = @{
	addLicenses = @(
		@{
			disabledPlans = @(
			"8a256a2b-b617-496d-b51b-e76466e88db0"
		)
		skuId = "84a661c4-e949-4bd2-a560-ed7766fcaf2b"
	}
	@{
		disabledPlans = @(
		)
		skuId = "f30db892-07e9-47e9-837c-80727f46fd3d"
	}
)
removeLicenses = @(
)
}

# A UPN can also be used as -UserId.
Set-MgUserLicense -UserId $userId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.users.item.assign_license.assign_license_post_request_body import AssignLicensePostRequestBody
from msgraph.generated.models.assigned_license import AssignedLicense
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = AssignLicensePostRequestBody(
	add_licenses = [
		AssignedLicense(
			disabled_plans = [
				UUID("8a256a2b-b617-496d-b51b-e76466e88db0"),
			],
			sku_id = UUID("84a661c4-e949-4bd2-a560-ed7766fcaf2b"),
		),
		AssignedLicense(
			disabled_plans = [
			],
			sku_id = UUID("f30db892-07e9-47e9-837c-80727f46fd3d"),
		),
	],
	remove_licenses = [
	],
)

result = await graph_client.me.assign_license.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-type: application/json

{
  "accountEnabled": true,
  "assignedLicenses": [
        {
            "disabledPlans": [
                "8a256a2b-b617-496d-b51b-e76466e88db0"
            ],
            "skuId": "84a661c4-e949-4bd2-a560-ed7766fcaf2b"
        },
        {
            "disabledPlans": [],
            "skuId": "f30db892-07e9-47e9-837c-80727f46fd3d"
        }
    ],
  "city": "Nairobi",
  "companyName": "Contoso"
}
```

### Example 2: Remove licenses from the signed-in user

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
POST https://graph.microsoft.com/v1.0/me/assignLicense
Content-type: application/json

{
    "addLicenses": [],
    "removeLicenses": [
        "f30db892-07e9-47e9-837c-80727f46fd3d",
        "84a661c4-e949-4bd2-a560-ed7766fcaf2b"
    ]
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Me.AssignLicense;
using Microsoft.Graph.Models;

var requestBody = new AssignLicensePostRequestBody
{
	AddLicenses = new List<AssignedLicense>
	{
	},
	RemoveLicenses = new List<Guid?>
	{
		Guid.Parse("f30db892-07e9-47e9-837c-80727f46fd3d"),
		Guid.Parse("84a661c4-e949-4bd2-a560-ed7766fcaf2b"),
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Me.AssignLicense.PostAsync(requestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphusers "github.com/microsoftgraph/msgraph-sdk-go/users"
	  graphmodels "github.com/microsoftgraph/msgraph-sdk-go/models"
	  //other-imports
)

requestBody := graphusers.NewItemAssignLicensePostRequestBody()
addLicenses := []graphmodels.AssignedLicenseable {

}
requestBody.SetAddLicenses(addLicenses)
removeLicenses := []uuid.UUID {
	uuid.MustParse("f30db892-07e9-47e9-837c-80727f46fd3d"),
	uuid.MustParse("84a661c4-e949-4bd2-a560-ed7766fcaf2b"),
}
requestBody.SetRemoveLicenses(removeLicenses)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
assignLicense, err := graphClient.Me().AssignLicense().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.users.item.assignlicense.AssignLicensePostRequestBody assignLicensePostRequestBody = new com.microsoft.graph.users.item.assignlicense.AssignLicensePostRequestBody();
LinkedList<AssignedLicense> addLicenses = new LinkedList<AssignedLicense>();
assignLicensePostRequestBody.setAddLicenses(addLicenses);
LinkedList<UUID> removeLicenses = new LinkedList<UUID>();
removeLicenses.add(UUID.fromString("f30db892-07e9-47e9-837c-80727f46fd3d"));
removeLicenses.add(UUID.fromString("84a661c4-e949-4bd2-a560-ed7766fcaf2b"));
assignLicensePostRequestBody.setRemoveLicenses(removeLicenses);
var result = graphClient.me().assignLicense().post(assignLicensePostRequestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const user = {
    addLicenses: [],
    removeLicenses: [
        'f30db892-07e9-47e9-837c-80727f46fd3d',
        '84a661c4-e949-4bd2-a560-ed7766fcaf2b'
    ]
};

await client.api('/me/assignLicense')
	.post(user);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Users\Item\AssignLicense\AssignLicensePostRequestBody;
use Microsoft\Graph\Generated\Models\AssignedLicense;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new AssignLicensePostRequestBody();
$requestBody->setAddLicenses([	]);
$requestBody->setRemoveLicenses(['f30db892-07e9-47e9-837c-80727f46fd3d', '84a661c4-e949-4bd2-a560-ed7766fcaf2b', 	]);

$result = $graphServiceClient->me()->assignLicense()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Users.Actions

$params = @{
	addLicenses = @(
	)
	removeLicenses = @(
	"f30db892-07e9-47e9-837c-80727f46fd3d"
"84a661c4-e949-4bd2-a560-ed7766fcaf2b"
)
}

# A UPN can also be used as -UserId.
Set-MgUserLicense -UserId $userId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.users.item.assign_license.assign_license_post_request_body import AssignLicensePostRequestBody
from msgraph.generated.models.assigned_license import AssignedLicense
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = AssignLicensePostRequestBody(
	add_licenses = [
	],
	remove_licenses = [
		UUID("f30db892-07e9-47e9-837c-80727f46fd3d"),
		UUID("84a661c4-e949-4bd2-a560-ed7766fcaf2b"),
	],
)

result = await graph_client.me.assign_license.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-type: application/json

{
  "accountEnabled": true,
  "assignedLicenses": [],
  "city": "Nairobi",
  "companyName": "Contoso"
}
```
