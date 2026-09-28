<!-- Source: https://learn.microsoft.com/en-us/graph/api/directory-post-customsecurityattributedefinitions?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-23 -->

# Create customSecurityAttributeDefinition

Namespace: microsoft.graph

Create a new [customSecurityAttributeDefinition](https://learn.microsoft.com/en-us/graph/api/resources/customsecurityattributedefinition?view=graph-rest-1.0) object.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | CustomSecAttributeDefinition.ReadWrite.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | CustomSecAttributeDefinition.ReadWrite.All | Not available. |

Important

For delegated access using work or school accounts, the signed-in user must be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) or a custom role that grants the permissions required for this operation.

- *Attribute Definition Administrator* is the only privileged role supported for this operation.
- By default, *Global Administrator* and other administrator roles don't have permissions to read, define, or assign custom security attributes.

## HTTP request

```http
POST /directory/customSecurityAttributeDefinitions
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the [customSecurityAttributeDefinition](https://learn.microsoft.com/en-us/graph/api/resources/customsecurityattributedefinition?view=graph-rest-1.0) object.

The following table shows the properties that you can configure when you create a [customSecurityAttributeDefinition](https://learn.microsoft.com/en-us/graph/api/resources/customsecurityattributedefinition?view=graph-rest-1.0).

| Property | Type | Description |
| :--- | :--- | :--- |
| attributeSet | String | Name of the attribute set. Case sensitive. Required. |
| description | String | Description of the custom security attribute. Can be up to 128 characters long and include Unicode characters. Cannot contain spaces or special characters. Can be changed later. Optional. |
| isCollection | Boolean | Indicates whether multiple values can be assigned to the custom security attribute. Cannot be changed later. If **type** is set to `Boolean`, **isCollection** cannot be set to `true`. Required. |
| isSearchable | Boolean | Indicates whether custom security attribute values are indexed for searching on objects that are assigned attribute values. Cannot be changed later. Required. |
| name | String | Name of the custom security attribute. Must be unique within an attribute set. Can be up to 32 characters long and include Unicode characters. Cannot contain spaces or special characters. Cannot be changed later. Case sensitive. Required. |
| status | String | Specifies whether the custom security attribute is active or deactivated. Acceptable values are `Available` and `Deprecated`. Can be changed later. Required. |
| type | String | Data type for the custom security attribute values. Supported types are: `Boolean`, `Integer`, and `String`. Cannot be changed later. Required. |
| usePreDefinedValuesOnly | Boolean | Indicates whether only predefined values can be assigned to the custom security attribute. If set to `false`, free-form values are allowed. Can later be changed from `true` to `false`, but cannot be changed from `false` to `true`. If **type** is set to `Boolean`, **usePreDefinedValuesOnly** cannot be set to `true`. Required. |

The **id** property is auto generated and cannot be set.

## Response

If successful, this method returns a `201 Created` response code and a [customSecurityAttributeDefinition](https://learn.microsoft.com/en-us/graph/api/resources/customsecurityattributedefinition?view=graph-rest-1.0) object in the response body.

## Examples

### Example 1: Add a custom security attribute

The following example adds a new custom security attribute definition that is a single free-form value of type String.

- Attribute set: `Engineering`
- Attribute: `ProjectDate`

#### Request

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
POST https://graph.microsoft.com/v1.0/directory/customSecurityAttributeDefinitions
Content-Type: application/json

{
    "attributeSet":"Engineering",
    "description":"Target completion date",
    "isCollection":false,
    "isSearchable":true,
    "name":"ProjectDate",
    "status":"Available",
    "type":"String",
    "usePreDefinedValuesOnly": false
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new CustomSecurityAttributeDefinition
{
	AttributeSet = "Engineering",
	Description = "Target completion date",
	IsCollection = false,
	IsSearchable = true,
	Name = "ProjectDate",
	Status = "Available",
	Type = "String",
	UsePreDefinedValuesOnly = false,
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Directory.CustomSecurityAttributeDefinitions.PostAsync(requestBody);
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

requestBody := graphmodels.NewCustomSecurityAttributeDefinition()
attributeSet := "Engineering"
requestBody.SetAttributeSet(&attributeSet) 
description := "Target completion date"
requestBody.SetDescription(&description) 
isCollection := false
requestBody.SetIsCollection(&isCollection) 
isSearchable := true
requestBody.SetIsSearchable(&isSearchable) 
name := "ProjectDate"
requestBody.SetName(&name) 
status := "Available"
requestBody.SetStatus(&status) 
type := "String"
requestBody.SetType(&type) 
usePreDefinedValuesOnly := false
requestBody.SetUsePreDefinedValuesOnly(&usePreDefinedValuesOnly) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
customSecurityAttributeDefinitions, err := graphClient.Directory().CustomSecurityAttributeDefinitions().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

CustomSecurityAttributeDefinition customSecurityAttributeDefinition = new CustomSecurityAttributeDefinition();
customSecurityAttributeDefinition.setAttributeSet("Engineering");
customSecurityAttributeDefinition.setDescription("Target completion date");
customSecurityAttributeDefinition.setIsCollection(false);
customSecurityAttributeDefinition.setIsSearchable(true);
customSecurityAttributeDefinition.setName("ProjectDate");
customSecurityAttributeDefinition.setStatus("Available");
customSecurityAttributeDefinition.setType("String");
customSecurityAttributeDefinition.setUsePreDefinedValuesOnly(false);
CustomSecurityAttributeDefinition result = graphClient.directory().customSecurityAttributeDefinitions().post(customSecurityAttributeDefinition);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const customSecurityAttributeDefinition = {
    attributeSet: 'Engineering',
    description: 'Target completion date',
    isCollection: false,
    isSearchable: true,
    name: 'ProjectDate',
    status: 'Available',
    type: 'String',
    usePreDefinedValuesOnly: false
};

await client.api('/directory/customSecurityAttributeDefinitions')
	.post(customSecurityAttributeDefinition);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\CustomSecurityAttributeDefinition;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new CustomSecurityAttributeDefinition();
$requestBody->setAttributeSet('Engineering');
$requestBody->setDescription('Target completion date');
$requestBody->setIsCollection(false);
$requestBody->setIsSearchable(true);
$requestBody->setName('ProjectDate');
$requestBody->setStatus('Available');
$requestBody->setType('String');
$requestBody->setUsePreDefinedValuesOnly(false);

$result = $graphServiceClient->directory()->customSecurityAttributeDefinitions()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Identity.DirectoryManagement

$params = @{
	attributeSet = "Engineering"
	description = "Target completion date"
	isCollection = $false
	isSearchable = $true
	name = "ProjectDate"
	status = "Available"
	type = "String"
	usePreDefinedValuesOnly = $false
}

New-MgDirectoryCustomSecurityAttributeDefinition -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.custom_security_attribute_definition import CustomSecurityAttributeDefinition
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = CustomSecurityAttributeDefinition(
	attribute_set = "Engineering",
	description = "Target completion date",
	is_collection = False,
	is_searchable = True,
	name = "ProjectDate",
	status = "Available",
	type = "String",
	use_pre_defined_values_only = False,
)

result = await graph_client.directory.custom_security_attribute_definitions.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

```http
HTTP/1.1 201 Created
Content-Type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#directory/customSecurityAttributeDefinitions/$entity",
    "attributeSet": "Engineering",
    "description": "Target completion date",
    "id": "Engineering_ProjectDate",
    "isCollection": false,
    "isSearchable": true,
    "name": "ProjectDate",
    "status": "Available",
    "type": "String",
    "usePreDefinedValuesOnly": false
}
```

### Example 2: Add a custom security attribute that supports multiple predefined values

The following example adds a new custom security attribute definition that supports multiple values of type String that are predefined.

- Attribute set: `Engineering`
- Attribute: `Project`

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
POST https://graph.microsoft.com/v1.0/directory/customSecurityAttributeDefinitions
Content-Type: application/json
Content-length: 310

{
    "attributeSet":"Engineering",
    "description":"Active projects for user",
    "isCollection":true,
    "isSearchable":true,
    "name":"Project",
    "status":"Available",
    "type":"String",
    "usePreDefinedValuesOnly": true
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new CustomSecurityAttributeDefinition
{
	AttributeSet = "Engineering",
	Description = "Active projects for user",
	IsCollection = true,
	IsSearchable = true,
	Name = "Project",
	Status = "Available",
	Type = "String",
	UsePreDefinedValuesOnly = true,
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Directory.CustomSecurityAttributeDefinitions.PostAsync(requestBody);
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

requestBody := graphmodels.NewCustomSecurityAttributeDefinition()
attributeSet := "Engineering"
requestBody.SetAttributeSet(&attributeSet) 
description := "Active projects for user"
requestBody.SetDescription(&description) 
isCollection := true
requestBody.SetIsCollection(&isCollection) 
isSearchable := true
requestBody.SetIsSearchable(&isSearchable) 
name := "Project"
requestBody.SetName(&name) 
status := "Available"
requestBody.SetStatus(&status) 
type := "String"
requestBody.SetType(&type) 
usePreDefinedValuesOnly := true
requestBody.SetUsePreDefinedValuesOnly(&usePreDefinedValuesOnly) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
customSecurityAttributeDefinitions, err := graphClient.Directory().CustomSecurityAttributeDefinitions().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

CustomSecurityAttributeDefinition customSecurityAttributeDefinition = new CustomSecurityAttributeDefinition();
customSecurityAttributeDefinition.setAttributeSet("Engineering");
customSecurityAttributeDefinition.setDescription("Active projects for user");
customSecurityAttributeDefinition.setIsCollection(true);
customSecurityAttributeDefinition.setIsSearchable(true);
customSecurityAttributeDefinition.setName("Project");
customSecurityAttributeDefinition.setStatus("Available");
customSecurityAttributeDefinition.setType("String");
customSecurityAttributeDefinition.setUsePreDefinedValuesOnly(true);
CustomSecurityAttributeDefinition result = graphClient.directory().customSecurityAttributeDefinitions().post(customSecurityAttributeDefinition);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const customSecurityAttributeDefinition = {
    attributeSet: 'Engineering',
    description: 'Active projects for user',
    isCollection: true,
    isSearchable: true,
    name: 'Project',
    status: 'Available',
    type: 'String',
    usePreDefinedValuesOnly: true
};

await client.api('/directory/customSecurityAttributeDefinitions')
	.post(customSecurityAttributeDefinition);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\CustomSecurityAttributeDefinition;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new CustomSecurityAttributeDefinition();
$requestBody->setAttributeSet('Engineering');
$requestBody->setDescription('Active projects for user');
$requestBody->setIsCollection(true);
$requestBody->setIsSearchable(true);
$requestBody->setName('Project');
$requestBody->setStatus('Available');
$requestBody->setType('String');
$requestBody->setUsePreDefinedValuesOnly(true);

$result = $graphServiceClient->directory()->customSecurityAttributeDefinitions()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Identity.DirectoryManagement

$params = @{
	attributeSet = "Engineering"
	description = "Active projects for user"
	isCollection = $true
	isSearchable = $true
	name = "Project"
	status = "Available"
	type = "String"
	usePreDefinedValuesOnly = $true
}

New-MgDirectoryCustomSecurityAttributeDefinition -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.custom_security_attribute_definition import CustomSecurityAttributeDefinition
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = CustomSecurityAttributeDefinition(
	attribute_set = "Engineering",
	description = "Active projects for user",
	is_collection = True,
	is_searchable = True,
	name = "Project",
	status = "Available",
	type = "String",
	use_pre_defined_values_only = True,
)

result = await graph_client.directory.custom_security_attribute_definitions.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

```http
HTTP/1.1 201 Created
Content-Type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#directory/customSecurityAttributeDefinitions/$entity",
    "attributeSet": "Engineering",
    "description": "Active projects for user",
    "id": "Engineering_Project",
    "isCollection": true,
    "isSearchable": true,
    "name": "Project",
    "status": "Available",
    "type": "String",
    "usePreDefinedValuesOnly": true
}
```

### Example 3: Add a custom security attribute with a list of predefined values

The following example adds a new custom security attribute definition with a list of predefined values as a collection of Strings.

- Attribute set: `Engineering`
- Attribute: `Project`
- Attribute data type: Collection of Strings
- Predefined values: `Alpine`, `Baker`, `Cascade`

#### Request

The following example shows a request.

- [HTTP](#tabpanel_3_http)
- [C#](#tabpanel_3_csharp)
- [Go](#tabpanel_3_go)
- [Java](#tabpanel_3_java)
- [JavaScript](#tabpanel_3_javascript)
- [PHP](#tabpanel_3_php)
- [PowerShell](#tabpanel_3_powershell)
- [Python](#tabpanel_3_python)

```http
POST https://graph.microsoft.com/v1.0/directory/customSecurityAttributeDefinitions
Content-Type: application/json

{
    "attributeSet": "Engineering",
    "description": "Active projects for user",
    "isCollection": true,
    "isSearchable": true,
    "name": "Project",
    "status": "Available",
    "type": "String",
    "usePreDefinedValuesOnly": true,
    "allowedValues": [
        {
            "id": "Alpine",
            "isActive": true
        },
        {
            "id": "Baker",
            "isActive": true
        },
        {
            "id": "Cascade",
            "isActive": true
        }
    ]
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new CustomSecurityAttributeDefinition
{
	AttributeSet = "Engineering",
	Description = "Active projects for user",
	IsCollection = true,
	IsSearchable = true,
	Name = "Project",
	Status = "Available",
	Type = "String",
	UsePreDefinedValuesOnly = true,
	AllowedValues = new List<AllowedValue>
	{
		new AllowedValue
		{
			Id = "Alpine",
			IsActive = true,
		},
		new AllowedValue
		{
			Id = "Baker",
			IsActive = true,
		},
		new AllowedValue
		{
			Id = "Cascade",
			IsActive = true,
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Directory.CustomSecurityAttributeDefinitions.PostAsync(requestBody);
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

requestBody := graphmodels.NewCustomSecurityAttributeDefinition()
attributeSet := "Engineering"
requestBody.SetAttributeSet(&attributeSet) 
description := "Active projects for user"
requestBody.SetDescription(&description) 
isCollection := true
requestBody.SetIsCollection(&isCollection) 
isSearchable := true
requestBody.SetIsSearchable(&isSearchable) 
name := "Project"
requestBody.SetName(&name) 
status := "Available"
requestBody.SetStatus(&status) 
type := "String"
requestBody.SetType(&type) 
usePreDefinedValuesOnly := true
requestBody.SetUsePreDefinedValuesOnly(&usePreDefinedValuesOnly) 


allowedValue := graphmodels.NewAllowedValue()
id := "Alpine"
allowedValue.SetId(&id) 
isActive := true
allowedValue.SetIsActive(&isActive) 
allowedValue1 := graphmodels.NewAllowedValue()
id := "Baker"
allowedValue1.SetId(&id) 
isActive := true
allowedValue1.SetIsActive(&isActive) 
allowedValue2 := graphmodels.NewAllowedValue()
id := "Cascade"
allowedValue2.SetId(&id) 
isActive := true
allowedValue2.SetIsActive(&isActive) 

allowedValues := []graphmodels.AllowedValueable {
	allowedValue,
	allowedValue1,
	allowedValue2,
}
requestBody.SetAllowedValues(allowedValues)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
customSecurityAttributeDefinitions, err := graphClient.Directory().CustomSecurityAttributeDefinitions().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

CustomSecurityAttributeDefinition customSecurityAttributeDefinition = new CustomSecurityAttributeDefinition();
customSecurityAttributeDefinition.setAttributeSet("Engineering");
customSecurityAttributeDefinition.setDescription("Active projects for user");
customSecurityAttributeDefinition.setIsCollection(true);
customSecurityAttributeDefinition.setIsSearchable(true);
customSecurityAttributeDefinition.setName("Project");
customSecurityAttributeDefinition.setStatus("Available");
customSecurityAttributeDefinition.setType("String");
customSecurityAttributeDefinition.setUsePreDefinedValuesOnly(true);
LinkedList<AllowedValue> allowedValues = new LinkedList<AllowedValue>();
AllowedValue allowedValue = new AllowedValue();
allowedValue.setId("Alpine");
allowedValue.setIsActive(true);
allowedValues.add(allowedValue);
AllowedValue allowedValue1 = new AllowedValue();
allowedValue1.setId("Baker");
allowedValue1.setIsActive(true);
allowedValues.add(allowedValue1);
AllowedValue allowedValue2 = new AllowedValue();
allowedValue2.setId("Cascade");
allowedValue2.setIsActive(true);
allowedValues.add(allowedValue2);
customSecurityAttributeDefinition.setAllowedValues(allowedValues);
CustomSecurityAttributeDefinition result = graphClient.directory().customSecurityAttributeDefinitions().post(customSecurityAttributeDefinition);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const customSecurityAttributeDefinition = {
    attributeSet: 'Engineering',
    description: 'Active projects for user',
    isCollection: true,
    isSearchable: true,
    name: 'Project',
    status: 'Available',
    type: 'String',
    usePreDefinedValuesOnly: true,
    allowedValues: [
        {
            id: 'Alpine',
            isActive: true
        },
        {
            id: 'Baker',
            isActive: true
        },
        {
            id: 'Cascade',
            isActive: true
        }
    ]
};

await client.api('/directory/customSecurityAttributeDefinitions')
	.post(customSecurityAttributeDefinition);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\CustomSecurityAttributeDefinition;
use Microsoft\Graph\Generated\Models\AllowedValue;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new CustomSecurityAttributeDefinition();
$requestBody->setAttributeSet('Engineering');
$requestBody->setDescription('Active projects for user');
$requestBody->setIsCollection(true);
$requestBody->setIsSearchable(true);
$requestBody->setName('Project');
$requestBody->setStatus('Available');
$requestBody->setType('String');
$requestBody->setUsePreDefinedValuesOnly(true);
$allowedValuesAllowedValue1 = new AllowedValue();
$allowedValuesAllowedValue1->setId('Alpine');
$allowedValuesAllowedValue1->setIsActive(true);
$allowedValuesArray []= $allowedValuesAllowedValue1;
$allowedValuesAllowedValue2 = new AllowedValue();
$allowedValuesAllowedValue2->setId('Baker');
$allowedValuesAllowedValue2->setIsActive(true);
$allowedValuesArray []= $allowedValuesAllowedValue2;
$allowedValuesAllowedValue3 = new AllowedValue();
$allowedValuesAllowedValue3->setId('Cascade');
$allowedValuesAllowedValue3->setIsActive(true);
$allowedValuesArray []= $allowedValuesAllowedValue3;
$requestBody->setAllowedValues($allowedValuesArray);


$result = $graphServiceClient->directory()->customSecurityAttributeDefinitions()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Identity.DirectoryManagement

$params = @{
	attributeSet = "Engineering"
	description = "Active projects for user"
	isCollection = $true
	isSearchable = $true
	name = "Project"
	status = "Available"
	type = "String"
	usePreDefinedValuesOnly = $true
	allowedValues = @(
		@{
			id = "Alpine"
			isActive = $true
		}
		@{
			id = "Baker"
			isActive = $true
		}
		@{
			id = "Cascade"
			isActive = $true
		}
	)
}

New-MgDirectoryCustomSecurityAttributeDefinition -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.custom_security_attribute_definition import CustomSecurityAttributeDefinition
from msgraph.generated.models.allowed_value import AllowedValue
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = CustomSecurityAttributeDefinition(
	attribute_set = "Engineering",
	description = "Active projects for user",
	is_collection = True,
	is_searchable = True,
	name = "Project",
	status = "Available",
	type = "String",
	use_pre_defined_values_only = True,
	allowed_values = [
		AllowedValue(
			id = "Alpine",
			is_active = True,
		),
		AllowedValue(
			id = "Baker",
			is_active = True,
		),
		AllowedValue(
			id = "Cascade",
			is_active = True,
		),
	],
)

result = await graph_client.directory.custom_security_attribute_definitions.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

```http
HTTP/1.1 201 Created
Content-Type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#directory/customSecurityAttributeDefinitions/$entity",
    "attributeSet": "Engineering",
    "description": "Active projects for user",
    "id": "Engineering_Project",
    "isCollection": true,
    "isSearchable": true,
    "name": "Project",
    "status": "Available",
    "type": "String",
    "usePreDefinedValuesOnly": true
}
```
