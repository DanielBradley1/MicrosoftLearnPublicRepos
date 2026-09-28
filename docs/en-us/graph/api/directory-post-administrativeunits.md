<!-- Source: https://learn.microsoft.com/en-us/graph/api/directory-post-administrativeunits?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-23 -->

# Create administrativeUnit

Namespace: microsoft.graph

Create a new [administrativeUnit](https://learn.microsoft.com/en-us/graph/api/resources/administrativeunit?view=graph-rest-1.0).

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | AdministrativeUnit.ReadWrite.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | AdministrativeUnit.ReadWrite.All | Not available. |

Important

For delegated access using work or school accounts, the signed-in user must be a member user or be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) or a custom role that grants the permissions required for this operation. *Privileged Role Administrator* is the least privileged role supported for this operation.

## HTTP request

```http
POST /directory/administrativeUnits
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of an [administrativeUnit](https://learn.microsoft.com/en-us/graph/api/resources/administrativeunit?view=graph-rest-1.0) object.

You can specify the following properties when you create an **administrativeUnit**.

| Property | Type | Description |
| :--- | :--- | :--- |
| description | String | Description for the administrative unit. Optional. |
| displayName | String | Display name for the administrative unit. Required. |
| isMemberManagementRestricted | Boolean | `true` if members of this administrative unit should be treated as sensitive, which requires specific permissions to manage. If not set, the default value is `null` and the default behavior is false. Use this property to define administrative units with roles that don't inherit from tenant-level administrators, and where the management of individual member objects is limited to administrators scoped to a restricted management administrative unit. This property is immutable and can't be changed later. Optional. |
| membershipRule | String | The dynamic membership rule for the administrative unit. For more information about the rules you can use for dynamic administrative units and dynamic groups, see [Manage rules for dynamic membership groups in Microsoft Entra ID](https://learn.microsoft.com/en-us/entra/identity/users/groups-dynamic-membership). Optional. |
| membershipRuleProcessingState | String | Controls whether the dynamic membership rule is actively processed. Set to `On` to activate the dynamic membership rule, or `Paused` to stop updating membership dynamically. Optional. |
| membershipType | String | Indicates the membership type for the administrative unit. The possible values are: `dynamic`, `assigned`. If not set, the default value is `null` and the default behavior is assigned. Optional. |
| visibility | String | The visibility of the administrative unit. If not set, the default value is `null` and the default behavior is public. It can be set to `HiddenMembership` to hide the membership from nonmembers. Optional. |

The **administrativeUnit** resource supports [extensions](https://learn.microsoft.com/en-us/graph/extensibility-overview), which allows you to use the `POST` operation to add custom properties with your own data when you create the administrative unit.

## Response

If successful, this method returns a `201 Created` response code and an [administrativeUnit](https://learn.microsoft.com/en-us/graph/api/resources/administrativeunit?view=graph-rest-1.0) object in the response body.

## Examples

### Example 1: Create an administrative unit

The following example shows how to create an administrative unit.

#### Request

The following example shows a request that creates a new administrative unit with a dynamic membership rule to include all users whose country is the United States.

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [PowerShell](#tabpanel_1_powershell)
- [Python](#tabpanel_1_python)

```http
POST https://graph.microsoft.com/v1.0/directory/administrativeUnits
Content-type: application/json

{
    "displayName": "Seattle District Technical Schools",
    "description": "Seattle district technical schools administration",
    "membershipType": "Dynamic",
    "membershipRule": "(user.country -eq \"United States\")",
    "membershipRuleProcessingState": "On",
    "visibility": "HiddenMembership"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new AdministrativeUnit
{
	DisplayName = "Seattle District Technical Schools",
	Description = "Seattle district technical schools administration",
	MembershipType = "Dynamic",
	MembershipRule = "(user.country -eq \"United States\")",
	MembershipRuleProcessingState = "On",
	Visibility = "HiddenMembership",
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Directory.AdministrativeUnits.PostAsync(requestBody);
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

requestBody := graphmodels.NewAdministrativeUnit()
displayName := "Seattle District Technical Schools"
requestBody.SetDisplayName(&displayName) 
description := "Seattle district technical schools administration"
requestBody.SetDescription(&description) 
membershipType := "Dynamic"
requestBody.SetMembershipType(&membershipType) 
membershipRule := "(user.country -eq \"United States\")"
requestBody.SetMembershipRule(&membershipRule) 
membershipRuleProcessingState := "On"
requestBody.SetMembershipRuleProcessingState(&membershipRuleProcessingState) 
visibility := "HiddenMembership"
requestBody.SetVisibility(&visibility) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
administrativeUnits, err := graphClient.Directory().AdministrativeUnits().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

AdministrativeUnit administrativeUnit = new AdministrativeUnit();
administrativeUnit.setDisplayName("Seattle District Technical Schools");
administrativeUnit.setDescription("Seattle district technical schools administration");
administrativeUnit.setMembershipType("Dynamic");
administrativeUnit.setMembershipRule("(user.country -eq \"United States\")");
administrativeUnit.setMembershipRuleProcessingState("On");
administrativeUnit.setVisibility("HiddenMembership");
AdministrativeUnit result = graphClient.directory().administrativeUnits().post(administrativeUnit);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const administrativeUnit = {
    displayName: 'Seattle District Technical Schools',
    description: 'Seattle district technical schools administration',
    membershipType: 'Dynamic',
    membershipRule: '(user.country -eq \"United States\")',
    membershipRuleProcessingState: 'On',
    visibility: 'HiddenMembership'
};

await client.api('/directory/administrativeUnits')
	.post(administrativeUnit);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\AdministrativeUnit;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new AdministrativeUnit();
$requestBody->setDisplayName('Seattle District Technical Schools');
$requestBody->setDescription('Seattle district technical schools administration');
$requestBody->setMembershipType('Dynamic');
$requestBody->setMembershipRule('(user.country -eq \"United States\")');
$requestBody->setMembershipRuleProcessingState('On');
$requestBody->setVisibility('HiddenMembership');

$result = $graphServiceClient->directory()->administrativeUnits()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Identity.DirectoryManagement

$params = @{
	displayName = "Seattle District Technical Schools"
	description = "Seattle district technical schools administration"
	membershipType = "Dynamic"
	membershipRule = "(user.country -eq "United States")"
	membershipRuleProcessingState = "On"
	visibility = "HiddenMembership"
}

New-MgDirectoryAdministrativeUnit -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.administrative_unit import AdministrativeUnit
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = AdministrativeUnit(
	display_name = "Seattle District Technical Schools",
	description = "Seattle district technical schools administration",
	membership_type = "Dynamic",
	membership_rule = "(user.country -eq \"United States\")",
	membership_rule_processing_state = "On",
	visibility = "HiddenMembership",
)

result = await graph_client.directory.administrative_units.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#administrativeUnits/$entity",
    "id": "7a3dc8f3-b3a0-4164-9a99-ed36f3af039f",
    "deletedDateTime": null,
    "displayName": "Seattle District Technical Schools",
    "description": "Seattle district technical schools administration",
    "membershipRule": "(user.country -eq \"United States\")",
    "membershipType": "Dynamic",
    "membershipRuleProcessingState": "On",
    "visibility": "HiddenMembership"
}
```

### Example 2: Create a restricted management administrative unit

The following example shows how to create a new restricted management administrative unit. The **isMemberManagementRestricted** property is immutable and can't be changed later.

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
POST https://graph.microsoft.com/v1.0/directory/administrativeUnits
Content-type: application/json

{
    "displayName": "Executive Division",
    "description": "Executive division administration",
    "isMemberManagementRestricted": true
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new AdministrativeUnit
{
	DisplayName = "Executive Division",
	Description = "Executive division administration",
	IsMemberManagementRestricted = true,
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Directory.AdministrativeUnits.PostAsync(requestBody);
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

requestBody := graphmodels.NewAdministrativeUnit()
displayName := "Executive Division"
requestBody.SetDisplayName(&displayName) 
description := "Executive division administration"
requestBody.SetDescription(&description) 
isMemberManagementRestricted := true
requestBody.SetIsMemberManagementRestricted(&isMemberManagementRestricted) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
administrativeUnits, err := graphClient.Directory().AdministrativeUnits().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

AdministrativeUnit administrativeUnit = new AdministrativeUnit();
administrativeUnit.setDisplayName("Executive Division");
administrativeUnit.setDescription("Executive division administration");
administrativeUnit.setIsMemberManagementRestricted(true);
AdministrativeUnit result = graphClient.directory().administrativeUnits().post(administrativeUnit);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const administrativeUnit = {
    displayName: 'Executive Division',
    description: 'Executive division administration',
    isMemberManagementRestricted: true
};

await client.api('/directory/administrativeUnits')
	.post(administrativeUnit);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\AdministrativeUnit;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new AdministrativeUnit();
$requestBody->setDisplayName('Executive Division');
$requestBody->setDescription('Executive division administration');
$requestBody->setIsMemberManagementRestricted(true);

$result = $graphServiceClient->directory()->administrativeUnits()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Identity.DirectoryManagement

$params = @{
	displayName = "Executive Division"
	description = "Executive division administration"
	isMemberManagementRestricted = $true
}

New-MgDirectoryAdministrativeUnit -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.administrative_unit import AdministrativeUnit
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = AdministrativeUnit(
	display_name = "Executive Division",
	description = "Executive division administration",
	is_member_management_restricted = True,
)

result = await graph_client.directory.administrative_units.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#administrativeUnits/$entity",
    "id": "2sd35b05-ae71-48ab-9e7d-4r41a28te37d",
    "deletedDateTime": null,
    "displayName": "Executive Division",
    "description": "Executive division administration",
    "isMemberManagementRestricted": true,
    "visibility": null
}
```

## Related content

- [Add custom data to resources using extensions](https://learn.microsoft.com/en-us/graph/extensibility-overview)
- [Add custom data to users using open extensions \(preview\)](https://learn.microsoft.com/en-us/graph/extensibility-open-users)
