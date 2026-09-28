<!-- Source: https://learn.microsoft.com/en-us/graph/extensibility-schema-groups -->
<!-- Sitemap-Last-Modified: 2025-07-23 -->

# Add custom data to groups using schema extensions

In this tutorial, you learn how to use [schema extensions](https://learn.microsoft.com/en-us/graph/api/resources/schemaextension).

Imagine you're a developer in a Learning Management Software company called **Bellows College** that builds training courses and materials for businesses. You use the collaborative experience of Microsoft 365 groups to deliver course content and record exercises among participants for both online courses and instructor-led courses. You want to make the Microsoft 365 groups used for training courses easily identifiable as training courses, which allows other developers to discover your groups and build rich experiences on top of your learning courses.

For this scenario, this article shows you how to:

- Discover available schema extension definitions that you could use.
- Register a schema extension definition that targets groups for training courses.
- Create a new group with custom data based on the schema extension definition that you registered.
- Add, update, or remove custom data in an existing group based on a schema extension definition.
- Read a group and the extension data.
- Delete the schema extension definition and the extension data.

Note

Apart from groups, schema extensions are also supported and can be managed for [other resource types](https://learn.microsoft.com/en-us/graph/extensibility-overview#comparison-of-extension-types).

## Prerequisites

To reproduce the steps in this article, you need the following privileges:

- Sign in to an API client such as [Graph Explorer](https://aka.ms/ge).
- Grant the app the *Group.ReadWrite.All* and *Application.ReadWrite.All* delegated permissions for the signed-in user.
- Be the owner of an application that you assign ownership of the schema extension definition in this tutorial. In this tutorial, the application is named *extensions-application* and has **appId** `d1e6f196-fca3-48ad-8cd3-1a98e3bd46d2`.

## Step 1. View available schema extensions

First, as a developer, you might want the app to reuse any existing schema extension definitions if they're fit for purpose. In the following example, you query schema extensions that are named \(by the **id**\) `bellowscollege_courses`. Assume that the response shows there are no schema extensions that are named `bellowscollege_courses` in your tenant.

### Request

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [PowerShell](#tabpanel_1_powershell)
- [Python](#tabpanel_1_python)

```msgraph
GET https://graph.microsoft.com/v1.0/schemaExtensions?$filter=id eq 'bellowscollege_courses'
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.SchemaExtensions.GetAsync((requestConfiguration) =>
{
	requestConfiguration.QueryParameters.Filter = "id eq 'bellowscollege_courses'";
});
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphschemaextensions "github.com/microsoftgraph/msgraph-sdk-go/schemaextensions"
	  //other-imports
)


requestFilter := "id eq 'bellowscollege_courses'"

requestParameters := &graphschemaextensions.SchemaExtensionsRequestBuilderGetQueryParameters{
	Filter: &requestFilter,
}
configuration := &graphschemaextensions.SchemaExtensionsRequestBuilderGetRequestConfiguration{
	QueryParameters: requestParameters,
}

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
schemaExtensions, err := graphClient.SchemaExtensions().Get(context.Background(), configuration)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

SchemaExtensionCollectionResponse result = graphClient.schemaExtensions().get(requestConfiguration -> {
	requestConfiguration.queryParameters.filter = "id eq 'bellowscollege_courses'";
});
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let schemaExtensions = await client.api('/schemaExtensions')
	.filter('id eq \'bellowscollege_courses\'')
	.get();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\SchemaExtensions\SchemaExtensionsRequestBuilderGetRequestConfiguration;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestConfiguration = new SchemaExtensionsRequestBuilderGetRequestConfiguration();
$queryParameters = SchemaExtensionsRequestBuilderGetRequestConfiguration::createQueryParameters();
$queryParameters->filter = "id eq 'bellowscollege_courses'";
$requestConfiguration->queryParameters = $queryParameters;


$result = $graphServiceClient->schemaExtensions()->get($requestConfiguration)->wait();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```powershell

Import-Module Microsoft.Graph.SchemaExtensions

Get-MgSchemaExtension -Filter "id eq 'bellowscollege_courses'" 
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.schema_extensions.schema_extensions_request_builder import SchemaExtensionsRequestBuilder
from kiota_abstractions.base_request_configuration import RequestConfiguration
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
query_params = SchemaExtensionsRequestBuilder.SchemaExtensionsRequestBuilderGetQueryParameters(
		filter = "id eq 'bellowscollege_courses'",
)

request_configuration = RequestConfiguration(
query_parameters = query_params,
)

result = await graph_client.schema_extensions.get(request_configuration = request_configuration)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

### Response

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#schemaExtensions",
    "@microsoft.graph.tips": "Use $select to choose only the properties your app needs, as this can lead to performance improvements. For example: GET schemaExtensions?$select=description,owner",
    "value": []
}
```

You can also query by the **id** as a path parameter as follows: `GET https://graph.microsoft.com/v1.0/schemaExtensions/bellowscollege_courses`. If there are no schema extensions that match the ID, the response is `404 Not Found`.

## Step 2. Register a schema extension definition

You want to create and register a new extension definition for training courses on the **group** resource. Specify the following properties:

- **id**: *Required.* Provide a string for this property following one of two ways:

  - Option 1: Concatenate a *verified* vanity domain name for your tenant with a name for the schema extension. For example, if the domain is `bellowscollege.com`, and the name of the schema extension is `courses`, then you can use the **id** `bellowscollege_courses`. The request fails if you use a domain name that isn't verified with your tenant.
  - Option 2: An alternative way is to provide only a schema name, such as `courses`, and let Microsoft Graph automatically generate the **id** for you by prefixing the provided name with a random alphanumeric string.

    This **id** becomes the name of the schema extension property on a group.

- **description**: *Optional.*
- **targetTypes**: *Required*. Specify the resource types that the schema extension can be applied to. In this example, the resource type is `Group`. You can add more resource types by updating the schema extension definition later. Only additive changes are permitted after you create the schema extension definition.
- **properties**: *Required*. Specify the custom properties that make up the schema. In this example, specify the `courseId`, `courseName`, and `courseType` custom properties and their types. Only additive changes are permitted after you create the schema extension definition.
- **owner**: *Conditional*. Specify the application that owns the schema extension definition. If you're running this example from an app that you're not assigned as owner, specify the **appId** of the application that you're assigned in the **owner** property.

### Request

- [HTTP](#tabpanel_2_http)
- [C#](#tabpanel_2_csharp)
- [Go](#tabpanel_2_go)
- [Java](#tabpanel_2_java)
- [JavaScript](#tabpanel_2_javascript)
- [PHP](#tabpanel_2_php)
- [PowerShell](#tabpanel_2_powershell)
- [Python](#tabpanel_2_python)

```http
POST https://graph.microsoft.com/v1.0/schemaExtensions
Content-type: application/json

{
    "id": "bellowscollege_courses",
    "description": "Bellows College training courses extensions",
    "targetTypes": [
        "Group"
    ],
    "owner": "d1e6f196-fca3-48ad-8cd3-1a98e3bd46d2",
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
	Id = "bellowscollege_courses",
	Description = "Bellows College training courses extensions",
	TargetTypes = new List<string>
	{
		"Group",
	},
	Owner = "d1e6f196-fca3-48ad-8cd3-1a98e3bd46d2",
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
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.SchemaExtensions.PostAsync(requestBody);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

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
id := "bellowscollege_courses"
requestBody.SetId(&id) 
description := "Bellows College training courses extensions"
requestBody.SetDescription(&description) 
targetTypes := []string {
	"Group",
}
requestBody.SetTargetTypes(targetTypes)
owner := "d1e6f196-fca3-48ad-8cd3-1a98e3bd46d2"
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

properties := []graphmodels.ExtensionSchemaPropertyable {
	extensionSchemaProperty,
	extensionSchemaProperty1,
	extensionSchemaProperty2,
}
requestBody.SetProperties(properties)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
schemaExtensions, err := graphClient.SchemaExtensions().Post(context.Background(), requestBody, nil)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

SchemaExtension schemaExtension = new SchemaExtension();
schemaExtension.setId("bellowscollege_courses");
schemaExtension.setDescription("Bellows College training courses extensions");
LinkedList<String> targetTypes = new LinkedList<String>();
targetTypes.add("Group");
schemaExtension.setTargetTypes(targetTypes);
schemaExtension.setOwner("d1e6f196-fca3-48ad-8cd3-1a98e3bd46d2");
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
schemaExtension.setProperties(properties);
SchemaExtension result = graphClient.schemaExtensions().post(schemaExtension);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const schemaExtension = {
    id: 'bellowscollege_courses',
    description: 'Bellows College training courses extensions',
    targetTypes: [
        'Group'
    ],
    owner: 'd1e6f196-fca3-48ad-8cd3-1a98e3bd46d2',
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
        }
    ]
};

await client.api('/schemaExtensions')
	.post(schemaExtension);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\SchemaExtension;
use Microsoft\Graph\Generated\Models\ExtensionSchemaProperty;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new SchemaExtension();
$requestBody->setId('bellowscollege_courses');
$requestBody->setDescription('Bellows College training courses extensions');
$requestBody->setTargetTypes(['Group', 	]);
$requestBody->setOwner('d1e6f196-fca3-48ad-8cd3-1a98e3bd46d2');
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
$requestBody->setProperties($propertiesArray);


$result = $graphServiceClient->schemaExtensions()->post($requestBody)->wait();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```powershell

Import-Module Microsoft.Graph.SchemaExtensions

$params = @{
	id = "bellowscollege_courses"
	description = "Bellows College training courses extensions"
	targetTypes = @(
	"Group"
)
owner = "d1e6f196-fca3-48ad-8cd3-1a98e3bd46d2"
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
)
}

New-MgSchemaExtension -BodyParameter $params
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.schema_extension import SchemaExtension
from msgraph.generated.models.extension_schema_property import ExtensionSchemaProperty
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = SchemaExtension(
	id = "bellowscollege_courses",
	description = "Bellows College training courses extensions",
	target_types = [
		"Group",
	],
	owner = "d1e6f196-fca3-48ad-8cd3-1a98e3bd46d2",
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
	],
)

result = await graph_client.schema_extensions.post(request_body)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

### Response

The following example shows the response.

In the response, the default initial status of the schema extension is `InDevelopment`. While you're developing the extension, you can keep it in this status, during which only the app that created it can update it with additive changes or delete it. When you're ready to share the extension for use by other apps, set **status** to **Available**.

```http
HTTP/1.1 201 Created
Content-Type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#schemaExtensions/$entity",
    "id": "bellowscollege_courses",
    "description": "Bellows College training courses extensions",
    "targetTypes": [
        "Group"
    ],
    "status": "InDevelopment",
    "owner": "d1e6f196-fca3-48ad-8cd3-1a98e3bd46d2",
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
        }
    ]
}
```

## Step 3. Extend a group with custom data

You can extend a group with custom data either during group creation or by updating an existing group.

### Option 1: Create a new group with extended data

The following request creates a new group and uses the `bellowscollege_courses` schema extension to extend the group with custom data. If you have an existing group, you can also extend it with custom data by updating the group with the extension data.

The response doesn't mirror back any data extensions. You need to explicitly `$select` the extension by name using a `GET /group/{id}` operation.

#### Request

- [HTTP](#tabpanel_3_http)
- [C#](#tabpanel_3_csharp)
- [Go](#tabpanel_3_go)
- [Java](#tabpanel_3_java)
- [JavaScript](#tabpanel_3_javascript)
- [PHP](#tabpanel_3_php)
- [PowerShell](#tabpanel_3_powershell)
- [Python](#tabpanel_3_python)

```http
POST https://graph.microsoft.com/v1.0/groups
Content-type: application/json

{
    "displayName": "New Managers March 2024",
    "description": "New Managers training course for March 2024",
    "groupTypes": [
        "Unified"
    ],
    "mailEnabled": true,
    "mailNickname": "newMan202403",
    "securityEnabled": false,
    "bellowscollege_courses": {
        "courseId": "123",
        "courseName": "New Managers",
        "courseType": "Online"
    }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;
using Microsoft.Kiota.Abstractions.Serialization;

var requestBody = new Group
{
	DisplayName = "New Managers March 2024",
	Description = "New Managers training course for March 2024",
	GroupTypes = new List<string>
	{
		"Unified",
	},
	MailEnabled = true,
	MailNickname = "newMan202403",
	SecurityEnabled = false,
	AdditionalData = new Dictionary<string, object>
	{
		{
			"bellowscollege_courses" , new UntypedObject(new Dictionary<string, UntypedNode>
			{
				{
					"courseId", new UntypedString("123")
				},
				{
					"courseName", new UntypedString("New Managers")
				},
				{
					"courseType", new UntypedString("Online")
				},
			})
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Groups.PostAsync(requestBody);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphmodels "github.com/microsoftgraph/msgraph-sdk-go/models"
	  //other-imports
)

requestBody := graphmodels.NewGroup()
displayName := "New Managers March 2024"
requestBody.SetDisplayName(&displayName) 
description := "New Managers training course for March 2024"
requestBody.SetDescription(&description) 
groupTypes := []string {
	"Unified",
}
requestBody.SetGroupTypes(groupTypes)
mailEnabled := true
requestBody.SetMailEnabled(&mailEnabled) 
mailNickname := "newMan202403"
requestBody.SetMailNickname(&mailNickname) 
securityEnabled := false
requestBody.SetSecurityEnabled(&securityEnabled) 
additionalData := map[string]interface{}{
bellowscollege_courses := graph.New()
courseId := "123"
bellowscollege_courses.SetCourseId(&courseId) 
courseName := "New Managers"
bellowscollege_courses.SetCourseName(&courseName) 
courseType := "Online"
bellowscollege_courses.SetCourseType(&courseType) 
	requestBody.SetBellowscollege_courses(bellowscollege_courses)
}
requestBody.SetAdditionalData(additionalData)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
groups, err := graphClient.Groups().Post(context.Background(), requestBody, nil)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

Group group = new Group();
group.setDisplayName("New Managers March 2024");
group.setDescription("New Managers training course for March 2024");
LinkedList<String> groupTypes = new LinkedList<String>();
groupTypes.add("Unified");
group.setGroupTypes(groupTypes);
group.setMailEnabled(true);
group.setMailNickname("newMan202403");
group.setSecurityEnabled(false);
HashMap<String, Object> additionalData = new HashMap<String, Object>();
 bellowscollegeCourses = new ();
bellowscollegeCourses.setCourseId("123");
bellowscollegeCourses.setCourseName("New Managers");
bellowscollegeCourses.setCourseType("Online");
additionalData.put("bellowscollege_courses", bellowscollegeCourses);
group.setAdditionalData(additionalData);
Group result = graphClient.groups().post(group);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const group = {
    displayName: 'New Managers March 2024',
    description: 'New Managers training course for March 2024',
    groupTypes: [
        'Unified'
    ],
    mailEnabled: true,
    mailNickname: 'newMan202403',
    securityEnabled: false,
    bellowscollege_courses: {
        courseId: '123',
        courseName: 'New Managers',
        courseType: 'Online'
    }
};

await client.api('/groups')
	.post(group);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\Group;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new Group();
$requestBody->setDisplayName('New Managers March 2024');
$requestBody->setDescription('New Managers training course for March 2024');
$requestBody->setGroupTypes(['Unified', 	]);
$requestBody->setMailEnabled(true);
$requestBody->setMailNickname('newMan202403');
$requestBody->setSecurityEnabled(false);
$additionalData = [
	'bellowscollege_courses' => [
		'courseId' => '123',
		'courseName' => 'New Managers',
		'courseType' => 'Online',
	],
];
$requestBody->setAdditionalData($additionalData);

$result = $graphServiceClient->groups()->post($requestBody)->wait();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```powershell

Import-Module Microsoft.Graph.Groups

$params = @{
	displayName = "New Managers March 2024"
	description = "New Managers training course for March 2024"
	groupTypes = @(
	"Unified"
)
mailEnabled = $true
mailNickname = "newMan202403"
securityEnabled = $false
bellowscollege_courses = @{
	courseId = "123"
	courseName = "New Managers"
	courseType = "Online"
}
}

New-MgGroup -BodyParameter $params
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.group import Group
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = Group(
	display_name = "New Managers March 2024",
	description = "New Managers training course for March 2024",
	group_types = [
		"Unified",
	],
	mail_enabled = True,
	mail_nickname = "newMan202403",
	security_enabled = False,
	additional_data = {
			"bellowscollege_courses" : {
					"course_id" : "123",
					"course_name" : "New Managers",
					"course_type" : "Online",
			},
	}
)

result = await graph_client.groups.post(request_body)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

#### Response

The following example shows the response. The response doesn't include the new extension. You need to explicitly `$select` the extension by name using a `GET /group/{id}` operation.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-Type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#groups/$entity",
    "id": "8fb45944-4085-449f-b95d-f7dd74a1b081",
    "createdDateTime": "2024-01-24T09:09:03Z",
    "description": "New Managers training course for March 2024",
    "displayName": "New Managers March 2024",
    "groupTypes": [
        "Unified"
    ],
    "mail": "newMan202403@bellowscollege.com",
    "mailEnabled": true,
    "mailNickname": "newMan202403"
}
```

### Option 2: Update an existing group with extended data

If you have an existing group, you can also extend it with custom data as follows. The request returns a `204 No Content` response.

- [HTTP](#tabpanel_4_http)
- [C#](#tabpanel_4_csharp)
- [Go](#tabpanel_4_go)
- [Java](#tabpanel_4_java)
- [JavaScript](#tabpanel_4_javascript)
- [PHP](#tabpanel_4_php)
- [PowerShell](#tabpanel_4_powershell)
- [Python](#tabpanel_4_python)

```http
PATCH https://graph.microsoft.com/v1.0/groups/dfc8016f-db97-4c47-a582-49cb8f849355
Content-type: application/json

{
    "bellowscollege_courses": {
        "courseId": "123",
        "courseName": "New Managers",
        "courseType": "Online"
    }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;
using Microsoft.Kiota.Abstractions.Serialization;

var requestBody = new Group
{
	AdditionalData = new Dictionary<string, object>
	{
		{
			"bellowscollege_courses" , new UntypedObject(new Dictionary<string, UntypedNode>
			{
				{
					"courseId", new UntypedString("123")
				},
				{
					"courseName", new UntypedString("New Managers")
				},
				{
					"courseType", new UntypedString("Online")
				},
			})
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Groups["{group-id}"].PatchAsync(requestBody);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphmodels "github.com/microsoftgraph/msgraph-sdk-go/models"
	  //other-imports
)

requestBody := graphmodels.NewGroup()
additionalData := map[string]interface{}{
bellowscollege_courses := graph.New()
courseId := "123"
bellowscollege_courses.SetCourseId(&courseId) 
courseName := "New Managers"
bellowscollege_courses.SetCourseName(&courseName) 
courseType := "Online"
bellowscollege_courses.SetCourseType(&courseType) 
	requestBody.SetBellowscollege_courses(bellowscollege_courses)
}
requestBody.SetAdditionalData(additionalData)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
groups, err := graphClient.Groups().ByGroupId("group-id").Patch(context.Background(), requestBody, nil)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

Group group = new Group();
HashMap<String, Object> additionalData = new HashMap<String, Object>();
 bellowscollegeCourses = new ();
bellowscollegeCourses.setCourseId("123");
bellowscollegeCourses.setCourseName("New Managers");
bellowscollegeCourses.setCourseType("Online");
additionalData.put("bellowscollege_courses", bellowscollegeCourses);
group.setAdditionalData(additionalData);
Group result = graphClient.groups().byGroupId("{group-id}").patch(group);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const group = {
    bellowscollege_courses: {
        courseId: '123',
        courseName: 'New Managers',
        courseType: 'Online'
    }
};

await client.api('/groups/dfc8016f-db97-4c47-a582-49cb8f849355')
	.update(group);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\Group;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new Group();
$additionalData = [
	'bellowscollege_courses' => [
		'courseId' => '123',
		'courseName' => 'New Managers',
		'courseType' => 'Online',
	],
];
$requestBody->setAdditionalData($additionalData);

$result = $graphServiceClient->groups()->byGroupId('group-id')->patch($requestBody)->wait();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```powershell

Import-Module Microsoft.Graph.Groups

$params = @{
	bellowscollege_courses = @{
		courseId = "123"
		courseName = "New Managers"
		courseType = "Online"
	}
}

Update-MgGroup -GroupId $groupId -BodyParameter $params
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.group import Group
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = Group(
	additional_data = {
			"bellowscollege_courses" : {
					"course_id" : "123",
					"course_name" : "New Managers",
					"course_type" : "Online",
			},
	}
)

result = await graph_client.groups.by_group_id('group-id').patch(request_body)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

## Step 4. Update custom data in a group

The following request updates the **courseType** property in the `bellowscollege_courses` extension for the group to `Hybrid`. Though you want to update only the **courseType** property, you must include the other properties and their existing values in the request body as well. Otherwise, Microsoft Graph sets them to `null` and removes their data.

The following request returns a `204 No Content` response.

- [HTTP](#tabpanel_5_http)
- [C#](#tabpanel_5_csharp)
- [Go](#tabpanel_5_go)
- [Java](#tabpanel_5_java)
- [JavaScript](#tabpanel_5_javascript)
- [PHP](#tabpanel_5_php)
- [PowerShell](#tabpanel_5_powershell)
- [Python](#tabpanel_5_python)

```http
PATCH https://graph.microsoft.com/v1.0/groups/dfc8016f-db97-4c47-a582-49cb8f849355
Content-type: application/json

{
    "bellowscollege_courses": {
        "courseId": "123",
        "courseName": "New Managers",
        "courseType": "Hybrid"
    }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;
using Microsoft.Kiota.Abstractions.Serialization;

var requestBody = new Group
{
	AdditionalData = new Dictionary<string, object>
	{
		{
			"bellowscollege_courses" , new UntypedObject(new Dictionary<string, UntypedNode>
			{
				{
					"courseId", new UntypedString("123")
				},
				{
					"courseName", new UntypedString("New Managers")
				},
				{
					"courseType", new UntypedString("Hybrid")
				},
			})
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Groups["{group-id}"].PatchAsync(requestBody);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphmodels "github.com/microsoftgraph/msgraph-sdk-go/models"
	  //other-imports
)

requestBody := graphmodels.NewGroup()
additionalData := map[string]interface{}{
bellowscollege_courses := graph.New()
courseId := "123"
bellowscollege_courses.SetCourseId(&courseId) 
courseName := "New Managers"
bellowscollege_courses.SetCourseName(&courseName) 
courseType := "Hybrid"
bellowscollege_courses.SetCourseType(&courseType) 
	requestBody.SetBellowscollege_courses(bellowscollege_courses)
}
requestBody.SetAdditionalData(additionalData)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
groups, err := graphClient.Groups().ByGroupId("group-id").Patch(context.Background(), requestBody, nil)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

Group group = new Group();
HashMap<String, Object> additionalData = new HashMap<String, Object>();
 bellowscollegeCourses = new ();
bellowscollegeCourses.setCourseId("123");
bellowscollegeCourses.setCourseName("New Managers");
bellowscollegeCourses.setCourseType("Hybrid");
additionalData.put("bellowscollege_courses", bellowscollegeCourses);
group.setAdditionalData(additionalData);
Group result = graphClient.groups().byGroupId("{group-id}").patch(group);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const group = {
    bellowscollege_courses: {
        courseId: '123',
        courseName: 'New Managers',
        courseType: 'Hybrid'
    }
};

await client.api('/groups/dfc8016f-db97-4c47-a582-49cb8f849355')
	.update(group);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\Group;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new Group();
$additionalData = [
	'bellowscollege_courses' => [
		'courseId' => '123',
		'courseName' => 'New Managers',
		'courseType' => 'Hybrid',
	],
];
$requestBody->setAdditionalData($additionalData);

$result = $graphServiceClient->groups()->byGroupId('group-id')->patch($requestBody)->wait();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```powershell

Import-Module Microsoft.Graph.Groups

$params = @{
	bellowscollege_courses = @{
		courseId = "123"
		courseName = "New Managers"
		courseType = "Hybrid"
	}
}

Update-MgGroup -GroupId $groupId -BodyParameter $params
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.group import Group
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = Group(
	additional_data = {
			"bellowscollege_courses" : {
					"course_id" : "123",
					"course_name" : "New Managers",
					"course_type" : "Hybrid",
			},
	}
)

result = await graph_client.groups.by_group_id('group-id').patch(request_body)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

## Step 5. Get a group and its extension data

To get the custom data in a group, use `$select` to include the extension by name.

Apart from filtering by the **id** of the schema extension, you can also filter by the extension property values. The following example looks for the group that has the `bellowscollege_courses` extension with a `courseId` property value matching `123`, and gets the extension data and the **displayName**, **id**, and **description** properties of the group.

### Request

- [HTTP](#tabpanel_6_http)
- [C#](#tabpanel_6_csharp)
- [Go](#tabpanel_6_go)
- [Java](#tabpanel_6_java)
- [JavaScript](#tabpanel_6_javascript)
- [PHP](#tabpanel_6_php)
- [PowerShell](#tabpanel_6_powershell)
- [Python](#tabpanel_6_python)

```msgraph
GET https://graph.microsoft.com/v1.0/groups?$filter=bellowscollege_courses/courseId eq '123'&$select=displayName,id,description,bellowscollege_courses
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Groups.GetAsync((requestConfiguration) =>
{
	requestConfiguration.QueryParameters.Filter = "bellowscollege_courses/courseId eq '123'";
	requestConfiguration.QueryParameters.Select = new string []{ "displayName","id","description","bellowscollege_courses" };
});
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphgroups "github.com/microsoftgraph/msgraph-sdk-go/groups"
	  //other-imports
)


requestFilter := "bellowscollege_courses/courseId eq '123'"

requestParameters := &graphgroups.GroupsRequestBuilderGetQueryParameters{
	Filter: &requestFilter,
	Select: [] string {"displayName","id","description","bellowscollege_courses"},
}
configuration := &graphgroups.GroupsRequestBuilderGetRequestConfiguration{
	QueryParameters: requestParameters,
}

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
groups, err := graphClient.Groups().Get(context.Background(), configuration)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

GroupCollectionResponse result = graphClient.groups().get(requestConfiguration -> {
	requestConfiguration.queryParameters.filter = "bellowscollege_courses/courseId eq '123'";
	requestConfiguration.queryParameters.select = new String []{"displayName", "id", "description", "bellowscollege_courses"};
});
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let groups = await client.api('/groups')
	.filter('bellowscollege_courses/courseId eq \'123\'')
	.select('displayName,id,description,bellowscollege_courses')
	.get();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Groups\GroupsRequestBuilderGetRequestConfiguration;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestConfiguration = new GroupsRequestBuilderGetRequestConfiguration();
$queryParameters = GroupsRequestBuilderGetRequestConfiguration::createQueryParameters();
$queryParameters->filter = "bellowscollege_courses/courseId eq '123'";
$queryParameters->select = ["displayName","id","description","bellowscollege_courses"];
$requestConfiguration->queryParameters = $queryParameters;


$result = $graphServiceClient->groups()->get($requestConfiguration)->wait();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```powershell

Import-Module Microsoft.Graph.Groups

Get-MgGroup -Filter "bellowscollege_courses/courseId eq '123'" -Property "displayName,id,description,bellowscollege_courses" 
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.groups.groups_request_builder import GroupsRequestBuilder
from kiota_abstractions.base_request_configuration import RequestConfiguration
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
query_params = GroupsRequestBuilder.GroupsRequestBuilderGetQueryParameters(
		filter = "bellowscollege_courses/courseId eq '123'",
		select = ["displayName","id","description","bellowscollege_courses"],
)

request_configuration = RequestConfiguration(
query_parameters = query_params,
)

result = await graph_client.groups.get(request_configuration = request_configuration)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

### Response

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#groups(displayName,id,description,bellowscollege_courses)",
    "value": [
        {
            "displayName": "New Managers March 2024",
            "id": "8fb45944-4085-449f-b95d-f7dd74a1b081",
            "description": "New Managers training course for March 2024",
            "bellowscollege_courses": {
                "@odata.type": "#microsoft.graph.ComplexExtensionValue",
                "courseType": "Hybrid",
                "courseName": "New Managers",
                "courseId": 123
            }
        }
    ]
}
```

## Step 6: Delete extension data and schema extension definition

You can delete a schema extension definition if you no longer need it. If resource instances have the extension property applied, deleting the schema extension definition doesn't delete the extension data in the resource instances. Instead, the extension data is available but no longer accessible. You can recreate the schema extension definition with the same configuration - if you used the verified domain for the schema extension **id** - to be able to delete the extension data.

The following request deletes the `bellowscollege_courses` schema extension property and its associated data from the group. The request returns a `204 No Content` response.

- [HTTP](#tabpanel_7_http)
- [C#](#tabpanel_7_csharp)
- [Go](#tabpanel_7_go)
- [Java](#tabpanel_7_java)
- [JavaScript](#tabpanel_7_javascript)
- [PHP](#tabpanel_7_php)
- [PowerShell](#tabpanel_7_powershell)
- [Python](#tabpanel_7_python)

```http
PATCH https://graph.microsoft.com/v1.0/groups/8fb45944-4085-449f-b95d-f7dd74a1b081

{
    "bellowscollege_courses": null
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new Group
{
	AdditionalData = new Dictionary<string, object>
	{
		{
			"bellowscollege_courses" , null
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Groups["{group-id}"].PatchAsync(requestBody);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphmodels "github.com/microsoftgraph/msgraph-sdk-go/models"
	  //other-imports
)

requestBody := graphmodels.NewGroup()
additionalData := map[string]interface{}{
	bellowscollege_courses := null
requestBody.SetBellowscollege_courses(&bellowscollege_courses) 
}
requestBody.SetAdditionalData(additionalData)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
groups, err := graphClient.Groups().ByGroupId("group-id").Patch(context.Background(), requestBody, nil)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

Group group = new Group();
HashMap<String, Object> additionalData = new HashMap<String, Object>();
additionalData.put("bellowscollege_courses", null);
group.setAdditionalData(additionalData);
Group result = graphClient.groups().byGroupId("{group-id}").patch(group);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const group = {
    bellowscollege_courses: null
};

await client.api('/groups/8fb45944-4085-449f-b95d-f7dd74a1b081')
	.update(group);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\Group;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new Group();
$additionalData = [
	'bellowscollege_courses' => null,
];
$requestBody->setAdditionalData($additionalData);

$result = $graphServiceClient->groups()->byGroupId('group-id')->patch($requestBody)->wait();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```powershell

Import-Module Microsoft.Graph.Groups

$params = @{
	bellowscollege_courses = $null
}

Update-MgGroup -GroupId $groupId -BodyParameter $params
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.group import Group
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = Group(
	additional_data = {
			"bellowscollege_courses" : None,
	}
)

result = await graph_client.groups.by_group_id('group-id').patch(request_body)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

The following request deletes the `bellowscollege_courses` schema extension definition. The request returns a `204 No Content` response.

- [HTTP](#tabpanel_8_http)
- [C#](#tabpanel_8_csharp)
- [Go](#tabpanel_8_go)
- [Java](#tabpanel_8_java)
- [JavaScript](#tabpanel_8_javascript)
- [PHP](#tabpanel_8_php)
- [PowerShell](#tabpanel_8_powershell)
- [Python](#tabpanel_8_python)

```http
DELETE https://graph.microsoft.com/v1.0/schemaExtensions/bellowscollege_courses
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
await graphClient.SchemaExtensions["{schemaExtension-id}"].DeleteAsync();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  //other-imports
)


// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
graphClient.SchemaExtensions().BySchemaExtensionId("schemaExtension-id").Delete(context.Background(), nil)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

graphClient.schemaExtensions().bySchemaExtensionId("{schemaExtension-id}").delete();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

await client.api('/schemaExtensions/bellowscollege_courses')
	.delete();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```php

<?php
use Microsoft\Graph\GraphServiceClient;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);


$graphServiceClient->schemaExtensions()->bySchemaExtensionId('schemaExtension-id')->delete()->wait();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```powershell

Import-Module Microsoft.Graph.SchemaExtensions

Remove-MgSchemaExtension -SchemaExtensionId $schemaExtensionId
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python

await graph_client.schema_extensions.by_schema_extension_id('schemaExtension-id').delete()
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

## Related content

- [Add custom data to resources using extensions](https://learn.microsoft.com/en-us/graph/extensibility-overview)
- [Add custom data to users using open extensions \(preview\)](https://learn.microsoft.com/en-us/graph/extensibility-open-users)
- [schemaExtension resource type](https://learn.microsoft.com/en-us/graph/api/resources/schemaextension)
