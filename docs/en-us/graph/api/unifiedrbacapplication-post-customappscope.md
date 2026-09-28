<!-- Source: https://learn.microsoft.com/en-us/graph/api/unifiedrbacapplication-post-customappscope?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-23 -->

# Create customAppScope

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Create a new [customAppScope](https://learn.microsoft.com/en-us/graph/api/resources/customappscope?view=graph-rest-beta) object for an RBAC provider.

Currently only the Exchange Online RBAC provider is supported.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | RoleManagement.ReadWrite.Exchange | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | RoleManagement.ReadWrite.Exchange | Not available. |

## HTTP request

For an Exchange Online provider:

```http
POST /roleManagement/exchange/customAppScopes
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of a [customAppScope](https://learn.microsoft.com/en-us/graph/api/resources/customappscope?view=graph-rest-beta) object.

## Response

If successful, this method returns a `201 Created` response code and a new [customAppScope](https://learn.microsoft.com/en-us/graph/api/resources/customappscope?view=graph-rest-beta) object in the response body.

## Examples

### Request

The following example shows how to create a **customAppScope** object with **type** `RecipientScope` for an Exchange Online provider.

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [PowerShell](#tabpanel_1_powershell)
- [Python](#tabpanel_1_python)

```http
POST https://graph.microsoft.com/beta/roleManagement/exchange/customAppScopes
Content-type: application/json

{
    "type": "RecipientScope",
    "displayName": "Protected Exec Users",
    "customAttributes": {
        "Exclusive": false,
        "RecipientFilter": "Title -like 'VP*'"
    }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.Models;

var requestBody = new CustomAppScope
{
	Type = "RecipientScope",
	DisplayName = "Protected Exec Users",
	CustomAttributes = new CustomAppScopeAttributesDictionary
	{
		AdditionalData = new Dictionary<string, object>
		{
			{
				"Exclusive" , false
			},
			{
				"RecipientFilter" , "Title -like 'VP*'"
			},
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.RoleManagement.Exchange.CustomAppScopes.PostAsync(requestBody);
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

requestBody := graphmodels.NewCustomAppScope()
type := "RecipientScope"
requestBody.SetType(&type) 
displayName := "Protected Exec Users"
requestBody.SetDisplayName(&displayName) 
customAttributes := graphmodels.NewCustomAppScopeAttributesDictionary()
additionalData := map[string]interface{}{
	exclusive := false
customAttributes.SetExclusive(&exclusive) 
	"RecipientFilter" : "Title -like 'VP*'", 
}
customAttributes.SetAdditionalData(additionalData)
requestBody.SetCustomAttributes(customAttributes)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
customAppScopes, err := graphClient.RoleManagement().Exchange().CustomAppScopes().Post(context.Background(), requestBody, nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

CustomAppScope customAppScope = new CustomAppScope();
customAppScope.setType("RecipientScope");
customAppScope.setDisplayName("Protected Exec Users");
CustomAppScopeAttributesDictionary customAttributes = new CustomAppScopeAttributesDictionary();
HashMap<String, Object> additionalData = new HashMap<String, Object>();
additionalData.put("Exclusive", false);
additionalData.put("RecipientFilter", "Title -like 'VP*'");
customAttributes.setAdditionalData(additionalData);
customAppScope.setCustomAttributes(customAttributes);
CustomAppScope result = graphClient.roleManagement().exchange().customAppScopes().post(customAppScope);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const customAppScope = {
    type: 'RecipientScope',
    displayName: 'Protected Exec Users',
    customAttributes: {
        Exclusive: false,
        RecipientFilter: 'Title -like \'VP*\''
    }
};

await client.api('/roleManagement/exchange/customAppScopes')
	.version('beta')
	.post(customAppScope);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Models\CustomAppScope;
use Microsoft\Graph\Beta\Generated\Models\CustomAppScopeAttributesDictionary;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new CustomAppScope();
$requestBody->setType('RecipientScope');
$requestBody->setDisplayName('Protected Exec Users');
$customAttributes = new CustomAppScopeAttributesDictionary();
$additionalData = [
	'Exclusive' => false,
	'RecipientFilter' => 'Title -like \'VP*\'',
];
$customAttributes->setAdditionalData($additionalData);
$requestBody->setCustomAttributes($customAttributes);

$result = $graphServiceClient->roleManagement()->exchange()->customAppScopes()->post($requestBody)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Beta.DeviceManagement.Enrollment

$params = @{
	type = "RecipientScope"
	displayName = "Protected Exec Users"
	customAttributes = @{
		Exclusive = $false
		RecipientFilter = "Title -like 'VP*'"
	}
}

New-MgBetaRoleManagementExchangeCustomAppScope -BodyParameter $params
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.models.custom_app_scope import CustomAppScope
from msgraph_beta.generated.models.custom_app_scope_attributes_dictionary import CustomAppScopeAttributesDictionary
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = CustomAppScope(
	type = "RecipientScope",
	display_name = "Protected Exec Users",
	custom_attributes = CustomAppScopeAttributesDictionary(
		additional_data = {
				"exclusive" : False,
				"recipient_filter" : "Title -like 'VP*'",
		}
	),
)

result = await graph_client.role_management.exchange.custom_app_scopes.post(request_body)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

```http
HTTP/1.1 201 Created
Content-type: application/json

{
    "@odata.context": "https://graph.microsoft.com/beta/$metadata#roleManagement/exchange/customAppScopes/$entity",
    "id": "ae242973-f38a-471f-bffd-f111451e940b",
    "type": "RecipientScope",
    "displayName": "Protected Exec Users",
    "customAttributes": {
        "Exclusive": false,
        "RecipientFilter": "Title -like 'VP*'"
    }
}
```
