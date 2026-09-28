<!-- Source: https://learn.microsoft.com/en-us/graph/api/b2xidentityuserflow-post-userattributeassignments?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-23 -->

# Create userAttributeAssignments

Namespace: microsoft.graph

Create a new identityUserFlowAttributeAssignment object in a [b2xIdentityUserFlow](https://learn.microsoft.com/en-us/graph/api/resources/b2xidentityuserflow?view=graph-rest-1.0).

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ✅ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | IdentityUserFlow.ReadWrite.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | IdentityUserFlow.ReadWrite.All | Not available. |

Important

For delegated access using work or school accounts, the signed-in user must be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) or a custom role that grants the permissions required for this operation. *External ID User Flow Administrator* is the least privileged role supported for this operation.

## HTTP request

```http
POST /identity/b2xUserFlows/{id}/userAttributeAssignments
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the [identityUserFlowAttributeAssignment](https://learn.microsoft.com/en-us/graph/api/resources/identityuserflowattributeassignment?view=graph-rest-1.0) object.

The following table lists the properties that are required when you create the [identityUserFlowAttributeAssignment](https://learn.microsoft.com/en-us/graph/api/resources/identityuserflowattributeassignment?view=graph-rest-1.0).

| Property | Type | Description |
| :--- | :--- | :--- |
| displayName | String | The display name of the identityUserFlowAttribute within a user flow. |
| isOptional | Boolean | Determines whether the identityUserFlowAttribute is optional. `true` means the user doesn't have to provide a value. `false` means the user cannot complete sign-up without providing a value. |
| requiresVerification | Boolean | Determines whether the identityUserFlowAttribute requires verification. This is only used for verifying the user's phone number or email address. |
| userAttributeValues | [userAttributeValuesItem](https://learn.microsoft.com/en-us/graph/api/resources/userattributevaluesitem?view=graph-rest-1.0) collection | The input options for the user flow attribute. Only applicable when the userInputType is `radioSingleSelect`, `dropdownSingleSelect`, or `checkboxMultiSelect`. |
| userInputType | identityUserFlowAttributeInputType | The input type of the user flow attribute. The possible values are: `textBox`, `dateTimeDropdown`, `radioSingleSelect`, `dropdownSingleSelect`, `emailBox`, `checkboxMultiSelect`. |
| userAttribute | [identityUserFlowAttribute](https://learn.microsoft.com/en-us/graph/api/resources/identityuserflowattribute?view=graph-rest-1.0) | The identifier for the user flow attribute to include in the user flow assignment. |

## Response

If successful, this method returns a `201 Created` response code and an [identityUserFlowAttributeAssignment](https://learn.microsoft.com/en-us/graph/api/resources/identityuserflowattributeassignment?view=graph-rest-1.0) object in the response body.

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
POST https://graph.microsoft.com/v1.0/identity/b2xUserFlows/B2X_1_Partner/userAttributeAssignments
Content-Type: application/json

{
    "isOptional": false,
    "requiresVerification": false,
    "userInputType": "TextBox",
    "displayName": "Shoe size",
    "userAttributeValues": [],
    "userAttribute": {
        "id": "extension_guid_shoeSize"
    }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new IdentityUserFlowAttributeAssignment
{
	IsOptional = false,
	RequiresVerification = false,
	UserInputType = IdentityUserFlowAttributeInputType.TextBox,
	DisplayName = "Shoe size",
	UserAttributeValues = new List<UserAttributeValuesItem>
	{
	},
	UserAttribute = new IdentityUserFlowAttribute
	{
		Id = "extension_guid_shoeSize",
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Identity.B2xUserFlows["{b2xIdentityUserFlow-id}"].UserAttributeAssignments.PostAsync(requestBody);
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

requestBody := graphmodels.NewIdentityUserFlowAttributeAssignment()
isOptional := false
requestBody.SetIsOptional(&isOptional) 
requiresVerification := false
requestBody.SetRequiresVerification(&requiresVerification) 
userInputType := graphmodels.TEXTBOX_IDENTITYUSERFLOWATTRIBUTEINPUTTYPE 
requestBody.SetUserInputType(&userInputType) 
displayName := "Shoe size"
requestBody.SetDisplayName(&displayName) 
userAttributeValues := []graphmodels.UserAttributeValuesItemable {

}
requestBody.SetUserAttributeValues(userAttributeValues)
userAttribute := graphmodels.NewIdentityUserFlowAttribute()
id := "extension_guid_shoeSize"
userAttribute.SetId(&id) 
requestBody.SetUserAttribute(userAttribute)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
userAttributeAssignments, err := graphClient.Identity().B2xUserFlows().ByB2xIdentityUserFlowId("b2xIdentityUserFlow-id").UserAttributeAssignments().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

IdentityUserFlowAttributeAssignment identityUserFlowAttributeAssignment = new IdentityUserFlowAttributeAssignment();
identityUserFlowAttributeAssignment.setIsOptional(false);
identityUserFlowAttributeAssignment.setRequiresVerification(false);
identityUserFlowAttributeAssignment.setUserInputType(IdentityUserFlowAttributeInputType.TextBox);
identityUserFlowAttributeAssignment.setDisplayName("Shoe size");
LinkedList<UserAttributeValuesItem> userAttributeValues = new LinkedList<UserAttributeValuesItem>();
identityUserFlowAttributeAssignment.setUserAttributeValues(userAttributeValues);
IdentityUserFlowAttribute userAttribute = new IdentityUserFlowAttribute();
userAttribute.setId("extension_guid_shoeSize");
identityUserFlowAttributeAssignment.setUserAttribute(userAttribute);
IdentityUserFlowAttributeAssignment result = graphClient.identity().b2xUserFlows().byB2xIdentityUserFlowId("{b2xIdentityUserFlow-id}").userAttributeAssignments().post(identityUserFlowAttributeAssignment);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const identityUserFlowAttributeAssignment = {
    isOptional: false,
    requiresVerification: false,
    userInputType: 'TextBox',
    displayName: 'Shoe size',
    userAttributeValues: [],
    userAttribute: {
        id: 'extension_guid_shoeSize'
    }
};

await client.api('/identity/b2xUserFlows/B2X_1_Partner/userAttributeAssignments')
	.post(identityUserFlowAttributeAssignment);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\IdentityUserFlowAttributeAssignment;
use Microsoft\Graph\Generated\Models\IdentityUserFlowAttributeInputType;
use Microsoft\Graph\Generated\Models\UserAttributeValuesItem;
use Microsoft\Graph\Generated\Models\IdentityUserFlowAttribute;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new IdentityUserFlowAttributeAssignment();
$requestBody->setIsOptional(false);
$requestBody->setRequiresVerification(false);
$requestBody->setUserInputType(new IdentityUserFlowAttributeInputType('textBox'));
$requestBody->setDisplayName('Shoe size');
$requestBody->setUserAttributeValues([	]);
$userAttribute = new IdentityUserFlowAttribute();
$userAttribute->setId('extension_guid_shoeSize');
$requestBody->setUserAttribute($userAttribute);

$result = $graphServiceClient->identity()->b2xUserFlows()->byB2xIdentityUserFlowId('b2xIdentityUserFlow-id')->userAttributeAssignments()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Identity.SignIns

$params = @{
	isOptional = $false
	requiresVerification = $false
	userInputType = "TextBox"
	displayName = "Shoe size"
	userAttributeValues = @(
	)
	userAttribute = @{
		id = "extension_guid_shoeSize"
	}
}

New-MgIdentityB2XUserFlowUserAttributeAssignment -B2xIdentityUserFlowId $b2xIdentityUserFlowId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.identity_user_flow_attribute_assignment import IdentityUserFlowAttributeAssignment
from msgraph.generated.models.identity_user_flow_attribute_input_type import IdentityUserFlowAttributeInputType
from msgraph.generated.models.user_attribute_values_item import UserAttributeValuesItem
from msgraph.generated.models.identity_user_flow_attribute import IdentityUserFlowAttribute
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = IdentityUserFlowAttributeAssignment(
	is_optional = False,
	requires_verification = False,
	user_input_type = IdentityUserFlowAttributeInputType.TextBox,
	display_name = "Shoe size",
	user_attribute_values = [
	],
	user_attribute = IdentityUserFlowAttribute(
		id = "extension_guid_shoeSize",
	),
)

result = await graph_client.identity.b2x_user_flows.by_b2x_identity_user_flow_id('b2xIdentityUserFlow-id').user_attribute_assignments.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

**Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Location: https://graph.microsoft.com/v1.0/identity/b2xUserFlows/B2X_1_Partner/userAttributeAssignments/extension_guid_shoeSize
Content-Type: application/json

{
    "id": "extension_guid_shoeSize",
    "isOptional": false,
    "requiresVerification": false,
    "userInputType": "TextBox",
    "displayName": "Shoe size",
    "userAttributeValues": []
}
```
