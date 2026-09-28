<!-- Source: https://learn.microsoft.com/en-us/graph/api/application-post-extensionproperty?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-23 -->

# Create extensionProperty \(directory extension\)

Namespace: microsoft.graph

Create a new directory extension definition, represented by an [extensionProperty](https://learn.microsoft.com/en-us/graph/api/resources/extensionproperty?view=graph-rest-1.0) object.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Application.ReadWrite.All | Directory.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Application.ReadWrite.All | Not available. |
| Application | Application.ReadWrite.OwnedBy | Application.ReadWrite.All, Directory.ReadWrite.All |

Important

For delegated access using work or school accounts, the signed-in user must be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) or a custom role that grants the permissions required for this operation. This operation supports the following built-in roles, which provide only the least privilege necessary:

- Directory Writers
- Cloud Application Administrator
- Application Administrator

## HTTP request

```http
POST /applications/{application ObjectId}/extensionProperties
POST /applications(appId='{appId}')/extensionProperties
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, provide an [extensionProperty](https://learn.microsoft.com/en-us/graph/api/resources/extensionproperty?view=graph-rest-1.0) object with the following properties.

| Property | Type | Description |
| :--- | :--- | :--- |
| dataType | String | Specifies the data type of the value the extension property can hold. Following values are supported.<br><br>- `Binary` - 256 bytes maximum<br>- `Boolean`<br>- `DateTime` - Must be specified in ISO 8601 format. Will be stored in UTC.<br>- `Integer` - 32-bit value.<br>- `LargeInteger` - 64-bit value.<br>- `String` - 256 characters maximum<br><br>Not nullable. For multivalued directory extensions, these limits apply per value in the collection. |
| name | String | Name of the extension property. Not nullable. |
| isMultiValued | Boolean | Defines the directory extension as a multi-valued property. When `true`, the directory extension property can store a collection of objects of the **dataType**; for example, a collection of string types such as `"extension_b7b1c57b532f40b8b5ed4b7a7ba67401_jobGroupTracker": ["String 1", "String 2"]`. The default value is `false`. |
| targetObjects | String collection | The Microsoft Graph resources that can use the extension property. All values must be in PascalCase. The following values are supported. Not nullable.<br><br>- `User`<br>- `Group`<br>- `AdministrativeUnit`<br>- `Application`<br>- `Device`<br>- `Organization` |

## Response

If successful, this method returns a `201 Created` response code and a new [extensionProperty](https://learn.microsoft.com/en-us/graph/api/resources/extensionproperty?view=graph-rest-1.0) object in the response body.

## Examples

### Request

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
POST https://graph.microsoft.com/v1.0/applications/fd918e4b-c821-4efb-b50a-5eddd23afc6f/extensionProperties
Content-type: application/json

{
    "name": "jobGroup",
    "dataType": "String",
    "isMultiValued": true,
    "targetObjects": [
        "User"
    ]
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new ExtensionProperty
{
	Name = "jobGroup",
	DataType = "String",
	IsMultiValued = true,
	TargetObjects = new List<string>
	{
		"User",
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Applications["{application-id}"].ExtensionProperties.PostAsync(requestBody);
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

requestBody := graphmodels.NewExtensionProperty()
name := "jobGroup"
requestBody.SetName(&name) 
dataType := "String"
requestBody.SetDataType(&dataType) 
isMultiValued := true
requestBody.SetIsMultiValued(&isMultiValued) 
targetObjects := []string {
	"User",
}
requestBody.SetTargetObjects(targetObjects)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
extensionProperties, err := graphClient.Applications().ByApplicationId("application-id").ExtensionProperties().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

ExtensionProperty extensionProperty = new ExtensionProperty();
extensionProperty.setName("jobGroup");
extensionProperty.setDataType("String");
extensionProperty.setIsMultiValued(true);
LinkedList<String> targetObjects = new LinkedList<String>();
targetObjects.add("User");
extensionProperty.setTargetObjects(targetObjects);
ExtensionProperty result = graphClient.applications().byApplicationId("{application-id}").extensionProperties().post(extensionProperty);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const extensionProperty = {
    name: 'jobGroup',
    dataType: 'String',
    isMultiValued: true,
    targetObjects: [
        'User'
    ]
};

await client.api('/applications/fd918e4b-c821-4efb-b50a-5eddd23afc6f/extensionProperties')
	.post(extensionProperty);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\ExtensionProperty;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new ExtensionProperty();
$requestBody->setName('jobGroup');
$requestBody->setDataType('String');
$requestBody->setIsMultiValued(true);
$requestBody->setTargetObjects(['User', 	]);

$result = $graphServiceClient->applications()->byApplicationId('application-id')->extensionProperties()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Applications

$params = @{
	name = "jobGroup"
	dataType = "String"
	isMultiValued = $true
	targetObjects = @(
	"User"
)
}

New-MgApplicationExtensionProperty -ApplicationId $applicationId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.extension_property import ExtensionProperty
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = ExtensionProperty(
	name = "jobGroup",
	data_type = "String",
	is_multi_valued = True,
	target_objects = [
		"User",
	],
)

result = await graph_client.applications.by_application_id('application-id').extension_properties.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

If successful, this method returns `201 Created` response code and [extensionProperty](https://learn.microsoft.com/en-us/graph/api/resources/extensionproperty?view=graph-rest-1.0) object in the response body.

```http
HTTP/1.1 201 Created
Content-type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#applications('fd918e4b-c821-4efb-b50a-5eddd23afc6f')/extensionProperties/$entity",
    "id": "da38c7b1-133e-4a79-abcd-e2fd586ce621",
    "deletedDateTime": null,
    "appDisplayName": "b2c-extensions-app. Do not modify. Used by AADB2C for storing user data.",
    "dataType": "String",
    "isMultiValued": true,
    "isSyncedFromOnPremises": false,
    "name": "extension_25883231668a43a780b25685c3f874bc_jobGroup",
    "targetObjects": [
        "User"
    ]
}
```
