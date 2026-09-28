<!-- Source: https://learn.microsoft.com/en-us/graph/api/schemaextension-update?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-31 -->

# Update schemaExtension

Namespace: microsoft.graph

Update properties in the definition of the specified [schemaExtension](https://learn.microsoft.com/en-us/graph/api/resources/schemaextension?view=graph-rest-1.0). Additive updates to the extension can only be made when the extension is in the `InDevelopment` or `Available` status. This means custom properties or target resource types cannot be removed from the definition, but new custom properties can be added and the description of the extension changed.

The update applies to all the resources that are included in the **targetTypes** property of the extension. These resources are among the [supporting resource types](https://learn.microsoft.com/en-us/graph/extensibility-overview#supported-resources).

For delegated flows, the signed-in user can update a schema extension as long as the **owner** property of the extension is set to the **appId** of an application the signed-in user owns. That application can be the one that initially created the extension, or some other application owned by the signed-in user.

This criteria for the **owner** property allows a signed-in user to make updates through other applications they don't own, such as Microsoft Graph Explorer. When using Graph Explorer to update a **schemaExtension** resource, include the **owner** property in the PATCH request body.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Application.ReadWrite.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Application.ReadWrite.All and Directory.ReadWrite.All | Not available. |

## HTTP request

```http
PATCH /schemaExtensions/{id}
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply the values for relevant fields that should be updated. Existing properties that are not included in the request body will maintain their previous values or be recalculated based on changes to other property values. For best performance you shouldn't include existing values that haven't changed.

| Property | Type | Description |
| :--- | :--- | :--- |
| description | String | Description for the schema extension. |
| properties | [extensionSchemaProperty](https://learn.microsoft.com/en-us/graph/api/resources/extensionschemaproperty?view=graph-rest-1.0) collection | The collection of property names and types that make up the schema extension definition. Only additive changes are permitted. |
| status | String | The lifecycle state of the schema extension. The initial state upon creation is `InDevelopment`. Possible states transitions are from `InDevelopment` to `Available` and `Available` to `Deprecated`. |
| targetTypes | String collection | Set of Microsoft Graph types \(that can support extensions\) that the schema extension can be applied to. Only additive changes are permitted. |

## Response

If successful, this method returns a `204 No Content` response code. Attempting to run this request from an application which you don't own \(and without setting the **owner** property to the **appId** of an application you own\) returns a `403 Forbidden` response code.

## Example

### Request

The following example shows a request. You must include the **owner** property if you're running the request from an application which you don't own. In this case, set the **owner** property to the **appId** of an application you own.

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [PowerShell](#tabpanel_1_powershell)
- [Python](#tabpanel_1_python)

```http
PATCH https://graph.microsoft.com/v1.0/schemaExtensions/exto6x7sfft_courses
Content-type: application/json

{
    "owner": "ef4cb9a8-97c3-4ca7-854b-5cb5ced376fa",
    "properties": [
        {
            "name": "courseId",
            "type": "Integer"
        },
        {
            "name": "courseName",
            "type": "String"
        },
        {
            "name": "courseType",
            "type": "String"
        },
        {
            "name": "courseSupervisors",
            "type": "String"
        }
    ]
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new SchemaExtension
{
	Owner = "ef4cb9a8-97c3-4ca7-854b-5cb5ced376fa",
	Properties = new List<ExtensionSchemaProperty>
	{
		new ExtensionSchemaProperty
		{
			Name = "courseId",
			Type = "Integer",
		},
		new ExtensionSchemaProperty
		{
			Name = "courseName",
			Type = "String",
		},
		new ExtensionSchemaProperty
		{
			Name = "courseType",
			Type = "String",
		},
		new ExtensionSchemaProperty
		{
			Name = "courseSupervisors",
			Type = "String",
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.SchemaExtensions["{schemaExtension-id}"].PatchAsync(requestBody);
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

requestBody := graphmodels.NewSchemaExtension()
owner := "ef4cb9a8-97c3-4ca7-854b-5cb5ced376fa"
requestBody.SetOwner(&owner) 


extensionSchemaProperty := graphmodels.NewExtensionSchemaProperty()
name := "courseId"
extensionSchemaProperty.SetName(&name) 
type := "Integer"
extensionSchemaProperty.SetType(&type) 
extensionSchemaProperty1 := graphmodels.NewExtensionSchemaProperty()
name := "courseName"
extensionSchemaProperty1.SetName(&name) 
type := "String"
extensionSchemaProperty1.SetType(&type) 
extensionSchemaProperty2 := graphmodels.NewExtensionSchemaProperty()
name := "courseType"
extensionSchemaProperty2.SetName(&name) 
type := "String"
extensionSchemaProperty2.SetType(&type) 
extensionSchemaProperty3 := graphmodels.NewExtensionSchemaProperty()
name := "courseSupervisors"
extensionSchemaProperty3.SetName(&name) 
type := "String"
extensionSchemaProperty3.SetType(&type) 

properties := []graphmodels.ExtensionSchemaPropertyable {
	extensionSchemaProperty,
	extensionSchemaProperty1,
	extensionSchemaProperty2,
	extensionSchemaProperty3,
}
requestBody.SetProperties(properties)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
schemaExtensions, err := graphClient.SchemaExtensions().BySchemaExtensionId("schemaExtension-id").Patch(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

SchemaExtension schemaExtension = new SchemaExtension();
schemaExtension.setOwner("ef4cb9a8-97c3-4ca7-854b-5cb5ced376fa");
LinkedList<ExtensionSchemaProperty> properties = new LinkedList<ExtensionSchemaProperty>();
ExtensionSchemaProperty extensionSchemaProperty = new ExtensionSchemaProperty();
extensionSchemaProperty.setName("courseId");
extensionSchemaProperty.setType("Integer");
properties.add(extensionSchemaProperty);
ExtensionSchemaProperty extensionSchemaProperty1 = new ExtensionSchemaProperty();
extensionSchemaProperty1.setName("courseName");
extensionSchemaProperty1.setType("String");
properties.add(extensionSchemaProperty1);
ExtensionSchemaProperty extensionSchemaProperty2 = new ExtensionSchemaProperty();
extensionSchemaProperty2.setName("courseType");
extensionSchemaProperty2.setType("String");
properties.add(extensionSchemaProperty2);
ExtensionSchemaProperty extensionSchemaProperty3 = new ExtensionSchemaProperty();
extensionSchemaProperty3.setName("courseSupervisors");
extensionSchemaProperty3.setType("String");
properties.add(extensionSchemaProperty3);
schemaExtension.setProperties(properties);
SchemaExtension result = graphClient.schemaExtensions().bySchemaExtensionId("{schemaExtension-id}").patch(schemaExtension);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const schemaExtension = {
    owner: 'ef4cb9a8-97c3-4ca7-854b-5cb5ced376fa',
    properties: [
        {
            name: 'courseId',
            type: 'Integer'
        },
        {
            name: 'courseName',
            type: 'String'
        },
        {
            name: 'courseType',
            type: 'String'
        },
        {
            name: 'courseSupervisors',
            type: 'String'
        }
    ]
};

await client.api('/schemaExtensions/exto6x7sfft_courses')
	.update(schemaExtension);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\SchemaExtension;
use Microsoft\Graph\Generated\Models\ExtensionSchemaProperty;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new SchemaExtension();
$requestBody->setOwner('ef4cb9a8-97c3-4ca7-854b-5cb5ced376fa');
$propertiesExtensionSchemaProperty1 = new ExtensionSchemaProperty();
$propertiesExtensionSchemaProperty1->setName('courseId');
$propertiesExtensionSchemaProperty1->setType('Integer');
$propertiesArray []= $propertiesExtensionSchemaProperty1;
$propertiesExtensionSchemaProperty2 = new ExtensionSchemaProperty();
$propertiesExtensionSchemaProperty2->setName('courseName');
$propertiesExtensionSchemaProperty2->setType('String');
$propertiesArray []= $propertiesExtensionSchemaProperty2;
$propertiesExtensionSchemaProperty3 = new ExtensionSchemaProperty();
$propertiesExtensionSchemaProperty3->setName('courseType');
$propertiesExtensionSchemaProperty3->setType('String');
$propertiesArray []= $propertiesExtensionSchemaProperty3;
$propertiesExtensionSchemaProperty4 = new ExtensionSchemaProperty();
$propertiesExtensionSchemaProperty4->setName('courseSupervisors');
$propertiesExtensionSchemaProperty4->setType('String');
$propertiesArray []= $propertiesExtensionSchemaProperty4;
$requestBody->setProperties($propertiesArray);


$result = $graphServiceClient->schemaExtensions()->bySchemaExtensionId('schemaExtension-id')->patch($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.SchemaExtensions

$params = @{
	owner = "ef4cb9a8-97c3-4ca7-854b-5cb5ced376fa"
	properties = @(
		@{
			name = "courseId"
			type = "Integer"
		}
		@{
			name = "courseName"
			type = "String"
		}
		@{
			name = "courseType"
			type = "String"
		}
		@{
			name = "courseSupervisors"
			type = "String"
		}
	)
}

Update-MgSchemaExtension -SchemaExtensionId $schemaExtensionId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.schema_extension import SchemaExtension
from msgraph.generated.models.extension_schema_property import ExtensionSchemaProperty
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = SchemaExtension(
	owner = "ef4cb9a8-97c3-4ca7-854b-5cb5ced376fa",
	properties = [
		ExtensionSchemaProperty(
			name = "courseId",
			type = "Integer",
		),
		ExtensionSchemaProperty(
			name = "courseName",
			type = "String",
		),
		ExtensionSchemaProperty(
			name = "courseType",
			type = "String",
		),
		ExtensionSchemaProperty(
			name = "courseSupervisors",
			type = "String",
		),
	],
)

result = await graph_client.schema_extensions.by_schema_extension_id('schemaExtension-id').patch(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

```http
HTTP/1.1 204 No Content
```

## Related content

- [Add custom data to resources using extensions](https://learn.microsoft.com/en-us/graph/extensibility-overview)
- [Add custom data to groups using schema extensions](https://learn.microsoft.com/en-us/graph/extensibility-schema-groups)
