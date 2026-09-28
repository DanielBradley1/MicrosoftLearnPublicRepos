<!-- Source: https://learn.microsoft.com/en-us/graph/custom-security-attributes-examples -->
<!-- Sitemap-Last-Modified: 2023-06-08 -->

# Manage custom security attribute assignments

[Custom security attributes](https://learn.microsoft.com/en-us/graph/api/resources/custom-security-attributes-overview) in Microsoft Entra ID are business-specific attributes \(key-value pairs\) that you can define and assign to Microsoft Entra objects. These attributes can be used to store information, categorize objects, or enforce fine-grained access control over specific Azure resources through Azure attribute-based access control \(Azure ABAC\).

Custom security attributes are supported for users and service principals only. This article provides examples of how to assign, update, list, or remove different types of custom security attributes for users and applications using Microsoft Graph.

## Prerequisites

- Create custom security attributes. For more information about how to define and manage custom security attribute definitions, see [Overview of custom security attributes using Microsoft Graph](https://learn.microsoft.com/en-us/graph/api/resources/custom-security-attributes-overview).
- For delegated scenarios, the calling must be assigned the following permissions and administrative roles.

  - To assign, update, or remove:

    - Microsoft Entra roles: [Attribute Assignment Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json#attribute-assignment-administrator)
    - Microsoft Graph permissions:

      - Users: CustomSecAttributeAssignment.ReadWrite.All and User.Read.All
      - Service principals: CustomSecAttributeAssignment.ReadWrite.All and Application.Read.All

  - To read:

    - Microsoft Entra roles: [Attribute Assignment Reader](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json#attribute-reader) or [Attribute Assignment Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json#attribute-assignment-administrator)
    - Microsoft Graph permissions:

      - Users: CustomSecAttributeAssignment.Read.All and User.Read.All
      - Service principals: CustomSecAttributeAssignment.Read.All and Application.Read.All

## Assign custom security attributes

### Example 1: Assign a custom security attribute with a string value to a user

The following example shows how to use the [Update user](https://learn.microsoft.com/en-us/graph/api/user-update) API to assign a custom security attribute with a string value to a user.

- Attribute set: `Engineering`
- Attribute: `ProjectDate`
- Attribute data type: String
- Attribute value: `"2022-10-01"`

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
PATCH https://graph.microsoft.com/v1.0/users/{id}
Content-type: application/json

{
    "customSecurityAttributes":
    {
        "Engineering":
        {
            "@odata.type":"#Microsoft.DirectoryServices.CustomSecurityAttributeValue",
            "ProjectDate":"2022-10-01"
        }
    }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;
using Microsoft.Kiota.Abstractions.Serialization;

var requestBody = new User
{
	CustomSecurityAttributes = new CustomSecurityAttributeValue
	{
		AdditionalData = new Dictionary<string, object>
		{
			{
				"Engineering" , new UntypedObject(new Dictionary<string, UntypedNode>
				{
					{
						"@odata.type", new UntypedString("#Microsoft.DirectoryServices.CustomSecurityAttributeValue")
					},
					{
						"projectDate", new UntypedString("2022-10-01")
					},
				})
			},
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Users["{user-id}"].PatchAsync(requestBody);
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

requestBody := graphmodels.NewUser()
customSecurityAttributes := graphmodels.NewCustomSecurityAttributeValue()
additionalData := map[string]interface{}{
engineering := graph.New()
projectDate := "2022-10-01"
engineering.SetProjectDate(&projectDate) 
	customSecurityAttributes.SetEngineering(engineering)
}
customSecurityAttributes.SetAdditionalData(additionalData)
requestBody.SetCustomSecurityAttributes(customSecurityAttributes)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
users, err := graphClient.Users().ByUserId("user-id").Patch(context.Background(), requestBody, nil)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

User user = new User();
CustomSecurityAttributeValue customSecurityAttributes = new CustomSecurityAttributeValue();
HashMap<String, Object> additionalData = new HashMap<String, Object>();
 engineering = new ();
engineering.setOdataType("#Microsoft.DirectoryServices.CustomSecurityAttributeValue");
engineering.setProjectDate("2022-10-01");
additionalData.put("Engineering", engineering);
customSecurityAttributes.setAdditionalData(additionalData);
user.setCustomSecurityAttributes(customSecurityAttributes);
User result = graphClient.users().byUserId("{user-id}").patch(user);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const user = {
    customSecurityAttributes: 
    {
        Engineering: 
        {
            '@odata.type':'#Microsoft.DirectoryServices.CustomSecurityAttributeValue',
            ProjectDate: '2022-10-01'
        }
    }
};

await client.api('/users/{id}')
	.update(user);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\User;
use Microsoft\Graph\Generated\Models\CustomSecurityAttributeValue;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new User();
$customSecurityAttributes = new CustomSecurityAttributeValue();
$additionalData = [
	'Engineering' => [
		'@odata.type' => '#Microsoft.DirectoryServices.CustomSecurityAttributeValue',
		'projectDate' => '2022-10-01',
	],
];
$customSecurityAttributes->setAdditionalData($additionalData);
$requestBody->setCustomSecurityAttributes($customSecurityAttributes);

$result = $graphServiceClient->users()->byUserId('user-id')->patch($requestBody)->wait();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```powershell

Import-Module Microsoft.Graph.Users

$params = @{
	customSecurityAttributes = @{
		Engineering = @{
			"@odata.type" = "#Microsoft.DirectoryServices.CustomSecurityAttributeValue"
			ProjectDate = "2022-10-01"
		}
	}
}

Update-MgUser -UserId $userId -BodyParameter $params
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.user import User
from msgraph.generated.models.custom_security_attribute_value import CustomSecurityAttributeValue
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = User(
	custom_security_attributes = CustomSecurityAttributeValue(
		additional_data = {
				"engineering" : {
						"@odata_type" : "#Microsoft.DirectoryServices.CustomSecurityAttributeValue",
						"project_date" : "2022-10-01",
				},
		}
	),
)

result = await graph_client.users.by_user_id('user-id').patch(request_body)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

#### Response

```http
HTTP/1.1 204 No Content
```

### Example 2: Assign a custom security attribute with a string value to a service principal

The following example shows how to use the [Update servicePrincipal](https://learn.microsoft.com/en-us/graph/api/serviceprincipal-update) API to assign a custom security attribute with a string value to a service principal.

- Attribute set: `Engineering`
- Attribute: `ProjectDate`
- Attribute data type: String
- Attribute value: `"2022-10-01"`

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
PATCH https://graph.microsoft.com/v1.0/servicePrincipals/{id}
Content-type: application/json

{
    "customSecurityAttributes":
    {
        "Engineering":
        {
            "@odata.type":"#Microsoft.DirectoryServices.CustomSecurityAttributeValue",
            "ProjectDate":"2022-10-01"
        }
    }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;
using Microsoft.Kiota.Abstractions.Serialization;

var requestBody = new ServicePrincipal
{
	CustomSecurityAttributes = new CustomSecurityAttributeValue
	{
		AdditionalData = new Dictionary<string, object>
		{
			{
				"Engineering" , new UntypedObject(new Dictionary<string, UntypedNode>
				{
					{
						"@odata.type", new UntypedString("#Microsoft.DirectoryServices.CustomSecurityAttributeValue")
					},
					{
						"projectDate", new UntypedString("2022-10-01")
					},
				})
			},
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.ServicePrincipals["{servicePrincipal-id}"].PatchAsync(requestBody);
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

requestBody := graphmodels.NewServicePrincipal()
customSecurityAttributes := graphmodels.NewCustomSecurityAttributeValue()
additionalData := map[string]interface{}{
engineering := graph.New()
projectDate := "2022-10-01"
engineering.SetProjectDate(&projectDate) 
	customSecurityAttributes.SetEngineering(engineering)
}
customSecurityAttributes.SetAdditionalData(additionalData)
requestBody.SetCustomSecurityAttributes(customSecurityAttributes)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
servicePrincipals, err := graphClient.ServicePrincipals().ByServicePrincipalId("servicePrincipal-id").Patch(context.Background(), requestBody, nil)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

ServicePrincipal servicePrincipal = new ServicePrincipal();
CustomSecurityAttributeValue customSecurityAttributes = new CustomSecurityAttributeValue();
HashMap<String, Object> additionalData = new HashMap<String, Object>();
 engineering = new ();
engineering.setOdataType("#Microsoft.DirectoryServices.CustomSecurityAttributeValue");
engineering.setProjectDate("2022-10-01");
additionalData.put("Engineering", engineering);
customSecurityAttributes.setAdditionalData(additionalData);
servicePrincipal.setCustomSecurityAttributes(customSecurityAttributes);
ServicePrincipal result = graphClient.servicePrincipals().byServicePrincipalId("{servicePrincipal-id}").patch(servicePrincipal);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const servicePrincipal = {
    customSecurityAttributes: 
    {
        Engineering: 
        {
            '@odata.type':'#Microsoft.DirectoryServices.CustomSecurityAttributeValue',
            ProjectDate: '2022-10-01'
        }
    }
};

await client.api('/servicePrincipals/{id}')
	.update(servicePrincipal);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\ServicePrincipal;
use Microsoft\Graph\Generated\Models\CustomSecurityAttributeValue;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new ServicePrincipal();
$customSecurityAttributes = new CustomSecurityAttributeValue();
$additionalData = [
	'Engineering' => [
		'@odata.type' => '#Microsoft.DirectoryServices.CustomSecurityAttributeValue',
		'projectDate' => '2022-10-01',
	],
];
$customSecurityAttributes->setAdditionalData($additionalData);
$requestBody->setCustomSecurityAttributes($customSecurityAttributes);

$result = $graphServiceClient->servicePrincipals()->byServicePrincipalId('servicePrincipal-id')->patch($requestBody)->wait();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```powershell

Import-Module Microsoft.Graph.Applications

$params = @{
	customSecurityAttributes = @{
		Engineering = @{
			"@odata.type" = "#Microsoft.DirectoryServices.CustomSecurityAttributeValue"
			ProjectDate = "2022-10-01"
		}
	}
}

Update-MgServicePrincipal -ServicePrincipalId $servicePrincipalId -BodyParameter $params
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.service_principal import ServicePrincipal
from msgraph.generated.models.custom_security_attribute_value import CustomSecurityAttributeValue
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = ServicePrincipal(
	custom_security_attributes = CustomSecurityAttributeValue(
		additional_data = {
				"engineering" : {
						"@odata_type" : "#Microsoft.DirectoryServices.CustomSecurityAttributeValue",
						"project_date" : "2022-10-01",
				},
		}
	),
)

result = await graph_client.service_principals.by_service_principal_id('servicePrincipal-id').patch(request_body)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

#### Response

```http
HTTP/1.1 204 No Content
```

### Example 3: Assign a custom security attribute with a multi-string value to a user

The following example shows how to use the [Update user](https://learn.microsoft.com/en-us/graph/api/user-update) API to assign a custom security attribute with a multi-string value to a user.

- Attribute set: `Engineering`
- Attribute: `Project`
- Attribute data type: Collection of Strings
- Attribute value: `["Baker","Cascade"]`

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
PATCH https://graph.microsoft.com/v1.0/users/{id}
Content-type: application/json

{
    "customSecurityAttributes":
    {
        "Engineering":
        {
            "@odata.type":"#Microsoft.DirectoryServices.CustomSecurityAttributeValue",
            "Project@odata.type":"#Collection(String)",
            "Project":["Baker","Cascade"]
        }
    }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;
using Microsoft.Kiota.Abstractions.Serialization;

var requestBody = new User
{
	CustomSecurityAttributes = new CustomSecurityAttributeValue
	{
		AdditionalData = new Dictionary<string, object>
		{
			{
				"Engineering" , new UntypedObject(new Dictionary<string, UntypedNode>
				{
					{
						"@odata.type", new UntypedString("#Microsoft.DirectoryServices.CustomSecurityAttributeValue")
					},
					{
						"project@odata.type", new UntypedString("#Collection(String)")
					},
					{
						"project", new UntypedArray(new List<UntypedNode>
						{
							new UntypedString("Baker"),
							new UntypedString("Cascade"),
						})
					},
				})
			},
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Users["{user-id}"].PatchAsync(requestBody);
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

requestBody := graphmodels.NewUser()
customSecurityAttributes := graphmodels.NewCustomSecurityAttributeValue()
additionalData := map[string]interface{}{
engineering := graph.New()
odataType := "#Collection(String)"
engineering.SetOdataType(&odataType) 
	project := []string {
		"Baker",
		"Cascade",
	}
	engineering.SetProject(project)
	customSecurityAttributes.SetEngineering(engineering)
}
customSecurityAttributes.SetAdditionalData(additionalData)
requestBody.SetCustomSecurityAttributes(customSecurityAttributes)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
users, err := graphClient.Users().ByUserId("user-id").Patch(context.Background(), requestBody, nil)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

User user = new User();
CustomSecurityAttributeValue customSecurityAttributes = new CustomSecurityAttributeValue();
HashMap<String, Object> additionalData = new HashMap<String, Object>();
 engineering = new ();
engineering.setOdataType("#Microsoft.DirectoryServices.CustomSecurityAttributeValue");
engineering.setProjectOdataType("#Collection(String)");
LinkedList<String> project = new LinkedList<String>();
project.add("Baker");
project.add("Cascade");
engineering.setProject(project);
additionalData.put("Engineering", engineering);
customSecurityAttributes.setAdditionalData(additionalData);
user.setCustomSecurityAttributes(customSecurityAttributes);
User result = graphClient.users().byUserId("{user-id}").patch(user);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const user = {
    customSecurityAttributes: 
    {
        Engineering: 
        {
            '@odata.type':'#Microsoft.DirectoryServices.CustomSecurityAttributeValue',
            'Project@odata.type':'#Collection(String)',
            Project: ['Baker','Cascade']
        }
    }
};

await client.api('/users/{id}')
	.update(user);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\User;
use Microsoft\Graph\Generated\Models\CustomSecurityAttributeValue;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new User();
$customSecurityAttributes = new CustomSecurityAttributeValue();
$additionalData = [
	'Engineering' => [
		'@odata.type' => '#Microsoft.DirectoryServices.CustomSecurityAttributeValue',
		'project@odata.type' => '#Collection(String)',
		'project' => [
'Baker', 'Cascade', ],
	],
];
$customSecurityAttributes->setAdditionalData($additionalData);
$requestBody->setCustomSecurityAttributes($customSecurityAttributes);

$result = $graphServiceClient->users()->byUserId('user-id')->patch($requestBody)->wait();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```powershell

Import-Module Microsoft.Graph.Users

$params = @{
	customSecurityAttributes = @{
		Engineering = @{
			"@odata.type" = "#Microsoft.DirectoryServices.CustomSecurityAttributeValue"
			"Project@odata.type" = "#Collection(String)"
			Project = @(
			"Baker"
		"Cascade"
	)
}
}
}

Update-MgUser -UserId $userId -BodyParameter $params
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.user import User
from msgraph.generated.models.custom_security_attribute_value import CustomSecurityAttributeValue
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = User(
	custom_security_attributes = CustomSecurityAttributeValue(
		additional_data = {
				"engineering" : {
						"@odata_type" : "#Microsoft.DirectoryServices.CustomSecurityAttributeValue",
						"project@odata_type" : "#Collection(String)",
						"project" : [
							"Baker",
							"Cascade",
						],
				},
		}
	),
)

result = await graph_client.users.by_user_id('user-id').patch(request_body)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

#### Response

```http
HTTP/1.1 204 No Content
```

### Example 4: Assign a custom security attribute with an integer value to a user

The following example shows how to use the [Update user](https://learn.microsoft.com/en-us/graph/api/user-update) API to assign a custom security attribute with an integer value to a user.

- Attribute set: `Engineering`
- Attribute: `NumVendors`
- Attribute data type: Integer
- Attribute value: `4`

#### Request

- [HTTP](#tabpanel_4_http)
- [C#](#tabpanel_4_csharp)
- [Go](#tabpanel_4_go)
- [Java](#tabpanel_4_java)
- [JavaScript](#tabpanel_4_javascript)
- [PHP](#tabpanel_4_php)
- [PowerShell](#tabpanel_4_powershell)
- [Python](#tabpanel_4_python)

```http
PATCH https://graph.microsoft.com/v1.0/users/{id}
Content-type: application/json

{
    "customSecurityAttributes":
    {
        "Engineering":
        {
            "@odata.type":"#Microsoft.DirectoryServices.CustomSecurityAttributeValue",
            "NumVendors@odata.type":"#Int32",
            "NumVendors":4
        }
    }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;
using Microsoft.Kiota.Abstractions.Serialization;

var requestBody = new User
{
	CustomSecurityAttributes = new CustomSecurityAttributeValue
	{
		AdditionalData = new Dictionary<string, object>
		{
			{
				"Engineering" , new UntypedObject(new Dictionary<string, UntypedNode>
				{
					{
						"@odata.type", new UntypedString("#Microsoft.DirectoryServices.CustomSecurityAttributeValue")
					},
					{
						"numVendors@odata.type", new UntypedString("#Int32")
					},
					{
						"numVendors", new UntypedString("4")
					},
				})
			},
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Users["{user-id}"].PatchAsync(requestBody);
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

requestBody := graphmodels.NewUser()
customSecurityAttributes := graphmodels.NewCustomSecurityAttributeValue()
additionalData := map[string]interface{}{
engineering := graph.New()
odataType := "#Int32"
engineering.SetOdataType(&odataType) 
numVendors := int32(4)
engineering.SetNumVendors(&numVendors) 
	customSecurityAttributes.SetEngineering(engineering)
}
customSecurityAttributes.SetAdditionalData(additionalData)
requestBody.SetCustomSecurityAttributes(customSecurityAttributes)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
users, err := graphClient.Users().ByUserId("user-id").Patch(context.Background(), requestBody, nil)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

User user = new User();
CustomSecurityAttributeValue customSecurityAttributes = new CustomSecurityAttributeValue();
HashMap<String, Object> additionalData = new HashMap<String, Object>();
 engineering = new ();
engineering.setOdataType("#Microsoft.DirectoryServices.CustomSecurityAttributeValue");
engineering.setNumVendorsOdataType("#Int32");
engineering.setNumVendors(4);
additionalData.put("Engineering", engineering);
customSecurityAttributes.setAdditionalData(additionalData);
user.setCustomSecurityAttributes(customSecurityAttributes);
User result = graphClient.users().byUserId("{user-id}").patch(user);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const user = {
    customSecurityAttributes: 
    {
        Engineering: 
        {
            '@odata.type':'#Microsoft.DirectoryServices.CustomSecurityAttributeValue',
            'NumVendors@odata.type':'#Int32',
            NumVendors: 4
        }
    }
};

await client.api('/users/{id}')
	.update(user);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\User;
use Microsoft\Graph\Generated\Models\CustomSecurityAttributeValue;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new User();
$customSecurityAttributes = new CustomSecurityAttributeValue();
$additionalData = [
	'Engineering' => [
		'@odata.type' => '#Microsoft.DirectoryServices.CustomSecurityAttributeValue',
		'numVendors@odata.type' => '#Int32',
		'numVendors' => 4,
	],
];
$customSecurityAttributes->setAdditionalData($additionalData);
$requestBody->setCustomSecurityAttributes($customSecurityAttributes);

$result = $graphServiceClient->users()->byUserId('user-id')->patch($requestBody)->wait();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```powershell

Import-Module Microsoft.Graph.Users

$params = @{
	customSecurityAttributes = @{
		Engineering = @{
			"@odata.type" = "#Microsoft.DirectoryServices.CustomSecurityAttributeValue"
			"NumVendors@odata.type" = "#Int32"
			NumVendors = 
		}
	}
}

Update-MgUser -UserId $userId -BodyParameter $params
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.user import User
from msgraph.generated.models.custom_security_attribute_value import CustomSecurityAttributeValue
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = User(
	custom_security_attributes = CustomSecurityAttributeValue(
		additional_data = {
				"engineering" : {
						"@odata_type" : "#Microsoft.DirectoryServices.CustomSecurityAttributeValue",
						"num_vendors@odata_type" : "#Int32",
						"num_vendors" : 4,
				},
		}
	),
)

result = await graph_client.users.by_user_id('user-id').patch(request_body)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

#### Response

```http
HTTP/1.1 204 No Content
```

### Example 5: Assign a custom security attribute with a multi-integer value to a user

The following example shows how to use the [Update user](https://learn.microsoft.com/en-us/graph/api/user-update) API to assign a custom security attribute with a multi-integer value to a user.

- Attribute set: `Engineering`
- Attribute: `CostCenter`
- Attribute data type: Collection of Integers
- Attribute value: `[1001,1003]`

#### Request

- [HTTP](#tabpanel_5_http)
- [C#](#tabpanel_5_csharp)
- [Go](#tabpanel_5_go)
- [Java](#tabpanel_5_java)
- [JavaScript](#tabpanel_5_javascript)
- [PHP](#tabpanel_5_php)
- [PowerShell](#tabpanel_5_powershell)
- [Python](#tabpanel_5_python)

```http
PATCH https://graph.microsoft.com/v1.0/users/{id}
Content-type: application/json

{
    "customSecurityAttributes":
    {
        "Engineering":
        {
            "@odata.type":"#Microsoft.DirectoryServices.CustomSecurityAttributeValue",
            "CostCenter@odata.type":"#Collection(Int32)",
            "CostCenter":[1001,1003]
        }
    }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;
using Microsoft.Kiota.Abstractions.Serialization;

var requestBody = new User
{
	CustomSecurityAttributes = new CustomSecurityAttributeValue
	{
		AdditionalData = new Dictionary<string, object>
		{
			{
				"Engineering" , new UntypedObject(new Dictionary<string, UntypedNode>
				{
					{
						"@odata.type", new UntypedString("#Microsoft.DirectoryServices.CustomSecurityAttributeValue")
					},
					{
						"costCenter@odata.type", new UntypedString("#Collection(Int32)")
					},
					{
						"costCenter", new UntypedArray(new List<UntypedNode>
						{
							new UntypedString("1001"),
							new UntypedString("1003"),
						})
					},
				})
			},
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Users["{user-id}"].PatchAsync(requestBody);
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

requestBody := graphmodels.NewUser()
customSecurityAttributes := graphmodels.NewCustomSecurityAttributeValue()
additionalData := map[string]interface{}{
engineering := graph.New()
odataType := "#Collection(Int32)"
engineering.SetOdataType(&odataType) 
	costCenter := []graph.Numberable {
 := int32(1001)
engineering.Set(&) 
 := int32(1003)
engineering.Set(&)
	}
	engineering.SetCostCenter(costCenter)
	customSecurityAttributes.SetEngineering(engineering)
}
customSecurityAttributes.SetAdditionalData(additionalData)
requestBody.SetCustomSecurityAttributes(customSecurityAttributes)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
users, err := graphClient.Users().ByUserId("user-id").Patch(context.Background(), requestBody, nil)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

User user = new User();
CustomSecurityAttributeValue customSecurityAttributes = new CustomSecurityAttributeValue();
HashMap<String, Object> additionalData = new HashMap<String, Object>();
 engineering = new ();
engineering.setOdataType("#Microsoft.DirectoryServices.CustomSecurityAttributeValue");
engineering.setCostCenterOdataType("#Collection(Int32)");
LinkedList<Number> costCenter = new LinkedList<Number>();
costCenter.add(1001);
costCenter.add(1003);
engineering.setCostCenter(costCenter);
additionalData.put("Engineering", engineering);
customSecurityAttributes.setAdditionalData(additionalData);
user.setCustomSecurityAttributes(customSecurityAttributes);
User result = graphClient.users().byUserId("{user-id}").patch(user);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const user = {
    customSecurityAttributes: 
    {
        Engineering: 
        {
            '@odata.type':'#Microsoft.DirectoryServices.CustomSecurityAttributeValue',
            'CostCenter@odata.type':'#Collection(Int32)',
            CostCenter: [1001,1003]
        }
    }
};

await client.api('/users/{id}')
	.update(user);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\User;
use Microsoft\Graph\Generated\Models\CustomSecurityAttributeValue;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new User();
$customSecurityAttributes = new CustomSecurityAttributeValue();
$additionalData = [
	'Engineering' => [
		'@odata.type' => '#Microsoft.DirectoryServices.CustomSecurityAttributeValue',
		'costCenter@odata.type' => '#Collection(Int32)',
		'costCenter' => [
1001,1003],
	],
];
$customSecurityAttributes->setAdditionalData($additionalData);
$requestBody->setCustomSecurityAttributes($customSecurityAttributes);

$result = $graphServiceClient->users()->byUserId('user-id')->patch($requestBody)->wait();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```powershell

Import-Module Microsoft.Graph.Users

$params = @{
	customSecurityAttributes = @{
		Engineering = @{
			"@odata.type" = "#Microsoft.DirectoryServices.CustomSecurityAttributeValue"
			"CostCenter@odata.type" = "#Collection(Int32)"
			CostCenter = @(
			
		
	)
}
}
}

Update-MgUser -UserId $userId -BodyParameter $params
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.user import User
from msgraph.generated.models.custom_security_attribute_value import CustomSecurityAttributeValue
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = User(
	custom_security_attributes = CustomSecurityAttributeValue(
		additional_data = {
				"engineering" : {
						"@odata_type" : "#Microsoft.DirectoryServices.CustomSecurityAttributeValue",
						"cost_center@odata_type" : "#Collection(Int32)",
						"cost_center" : [
							1001,
							1003,
						],
				},
		}
	),
)

result = await graph_client.users.by_user_id('user-id').patch(request_body)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

#### Response

```http
HTTP/1.1 204 No Content
```

### Example 6: Assign a custom security attribute with a Boolean value to a user

The following example shows how to use the [Update user](https://learn.microsoft.com/en-us/graph/api/user-update) API to assign a custom security attribute with a Boolean value to a user.

- Attribute set: `Engineering`
- Attribute: `Certification`
- Attribute data type: Boolean
- Attribute value: `true`

#### Request

- [HTTP](#tabpanel_6_http)
- [C#](#tabpanel_6_csharp)
- [Go](#tabpanel_6_go)
- [Java](#tabpanel_6_java)
- [JavaScript](#tabpanel_6_javascript)
- [PHP](#tabpanel_6_php)
- [PowerShell](#tabpanel_6_powershell)
- [Python](#tabpanel_6_python)

```http
PATCH https://graph.microsoft.com/v1.0/users/{id}
Content-type: application/json

{
    "customSecurityAttributes":
    {
        "Engineering":
        {
            "@odata.type":"#Microsoft.DirectoryServices.CustomSecurityAttributeValue",
            "Certification":true
        }
    }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;
using Microsoft.Kiota.Abstractions.Serialization;

var requestBody = new User
{
	CustomSecurityAttributes = new CustomSecurityAttributeValue
	{
		AdditionalData = new Dictionary<string, object>
		{
			{
				"Engineering" , new UntypedObject(new Dictionary<string, UntypedNode>
				{
					{
						"@odata.type", new UntypedString("#Microsoft.DirectoryServices.CustomSecurityAttributeValue")
					},
					{
						"certification", new UntypedBoolean(true)
					},
				})
			},
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Users["{user-id}"].PatchAsync(requestBody);
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

requestBody := graphmodels.NewUser()
customSecurityAttributes := graphmodels.NewCustomSecurityAttributeValue()
additionalData := map[string]interface{}{
engineering := graph.New()
	certification := true
engineering.SetCertification(&certification) 
	customSecurityAttributes.SetEngineering(engineering)
}
customSecurityAttributes.SetAdditionalData(additionalData)
requestBody.SetCustomSecurityAttributes(customSecurityAttributes)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
users, err := graphClient.Users().ByUserId("user-id").Patch(context.Background(), requestBody, nil)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

User user = new User();
CustomSecurityAttributeValue customSecurityAttributes = new CustomSecurityAttributeValue();
HashMap<String, Object> additionalData = new HashMap<String, Object>();
 engineering = new ();
engineering.setOdataType("#Microsoft.DirectoryServices.CustomSecurityAttributeValue");
engineering.setCertification(true);
additionalData.put("Engineering", engineering);
customSecurityAttributes.setAdditionalData(additionalData);
user.setCustomSecurityAttributes(customSecurityAttributes);
User result = graphClient.users().byUserId("{user-id}").patch(user);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const user = {
    customSecurityAttributes: 
    {
        Engineering: 
        {
            '@odata.type':'#Microsoft.DirectoryServices.CustomSecurityAttributeValue',
            Certification: true
        }
    }
};

await client.api('/users/{id}')
	.update(user);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\User;
use Microsoft\Graph\Generated\Models\CustomSecurityAttributeValue;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new User();
$customSecurityAttributes = new CustomSecurityAttributeValue();
$additionalData = [
	'Engineering' => [
		'@odata.type' => '#Microsoft.DirectoryServices.CustomSecurityAttributeValue',
		'certification' => true,
	],
];
$customSecurityAttributes->setAdditionalData($additionalData);
$requestBody->setCustomSecurityAttributes($customSecurityAttributes);

$result = $graphServiceClient->users()->byUserId('user-id')->patch($requestBody)->wait();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```powershell

Import-Module Microsoft.Graph.Users

$params = @{
	customSecurityAttributes = @{
		Engineering = @{
			"@odata.type" = "#Microsoft.DirectoryServices.CustomSecurityAttributeValue"
			Certification = $true
		}
	}
}

Update-MgUser -UserId $userId -BodyParameter $params
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.user import User
from msgraph.generated.models.custom_security_attribute_value import CustomSecurityAttributeValue
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = User(
	custom_security_attributes = CustomSecurityAttributeValue(
		additional_data = {
				"engineering" : {
						"@odata_type" : "#Microsoft.DirectoryServices.CustomSecurityAttributeValue",
						"certification" : True,
				},
		}
	),
)

result = await graph_client.users.by_user_id('user-id').patch(request_body)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

#### Response

```http
HTTP/1.1 204 No Content
```

## Update custom security attribute assignments

### Example 1: Update a custom security attribute assignment with an integer value for a user

The following example shows how to use the [Update user](https://learn.microsoft.com/en-us/graph/api/user-update) API to update a custom security attribute assignment with an integer value for a user.

- Attribute set: `Engineering`
- Attribute: `NumVendors`
- Attribute data type: Integer
- Attribute value: `8`

#### Request

- [HTTP](#tabpanel_7_http)
- [C#](#tabpanel_7_csharp)
- [Go](#tabpanel_7_go)
- [Java](#tabpanel_7_java)
- [JavaScript](#tabpanel_7_javascript)
- [PHP](#tabpanel_7_php)
- [PowerShell](#tabpanel_7_powershell)
- [Python](#tabpanel_7_python)

```http
PATCH https://graph.microsoft.com/v1.0/users/{id}
Content-type: application/json

{
    "customSecurityAttributes":
    {
        "Engineering":
        {
            "@odata.type":"#Microsoft.DirectoryServices.CustomSecurityAttributeValue",
            "NumVendors@odata.type":"#Int32",
            "NumVendors":8
        }
    }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;
using Microsoft.Kiota.Abstractions.Serialization;

var requestBody = new User
{
	CustomSecurityAttributes = new CustomSecurityAttributeValue
	{
		AdditionalData = new Dictionary<string, object>
		{
			{
				"Engineering" , new UntypedObject(new Dictionary<string, UntypedNode>
				{
					{
						"@odata.type", new UntypedString("#Microsoft.DirectoryServices.CustomSecurityAttributeValue")
					},
					{
						"numVendors@odata.type", new UntypedString("#Int32")
					},
					{
						"numVendors", new UntypedString("8")
					},
				})
			},
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Users["{user-id}"].PatchAsync(requestBody);
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

requestBody := graphmodels.NewUser()
customSecurityAttributes := graphmodels.NewCustomSecurityAttributeValue()
additionalData := map[string]interface{}{
engineering := graph.New()
odataType := "#Int32"
engineering.SetOdataType(&odataType) 
numVendors := int32(8)
engineering.SetNumVendors(&numVendors) 
	customSecurityAttributes.SetEngineering(engineering)
}
customSecurityAttributes.SetAdditionalData(additionalData)
requestBody.SetCustomSecurityAttributes(customSecurityAttributes)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
users, err := graphClient.Users().ByUserId("user-id").Patch(context.Background(), requestBody, nil)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

User user = new User();
CustomSecurityAttributeValue customSecurityAttributes = new CustomSecurityAttributeValue();
HashMap<String, Object> additionalData = new HashMap<String, Object>();
 engineering = new ();
engineering.setOdataType("#Microsoft.DirectoryServices.CustomSecurityAttributeValue");
engineering.setNumVendorsOdataType("#Int32");
engineering.setNumVendors(8);
additionalData.put("Engineering", engineering);
customSecurityAttributes.setAdditionalData(additionalData);
user.setCustomSecurityAttributes(customSecurityAttributes);
User result = graphClient.users().byUserId("{user-id}").patch(user);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const user = {
    customSecurityAttributes: 
    {
        Engineering: 
        {
            '@odata.type':'#Microsoft.DirectoryServices.CustomSecurityAttributeValue',
            'NumVendors@odata.type':'#Int32',
            NumVendors: 8
        }
    }
};

await client.api('/users/{id}')
	.update(user);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\User;
use Microsoft\Graph\Generated\Models\CustomSecurityAttributeValue;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new User();
$customSecurityAttributes = new CustomSecurityAttributeValue();
$additionalData = [
	'Engineering' => [
		'@odata.type' => '#Microsoft.DirectoryServices.CustomSecurityAttributeValue',
		'numVendors@odata.type' => '#Int32',
		'numVendors' => 8,
	],
];
$customSecurityAttributes->setAdditionalData($additionalData);
$requestBody->setCustomSecurityAttributes($customSecurityAttributes);

$result = $graphServiceClient->users()->byUserId('user-id')->patch($requestBody)->wait();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```powershell

Import-Module Microsoft.Graph.Users

$params = @{
	customSecurityAttributes = @{
		Engineering = @{
			"@odata.type" = "#Microsoft.DirectoryServices.CustomSecurityAttributeValue"
			"NumVendors@odata.type" = "#Int32"
			NumVendors = 
		}
	}
}

Update-MgUser -UserId $userId -BodyParameter $params
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.user import User
from msgraph.generated.models.custom_security_attribute_value import CustomSecurityAttributeValue
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = User(
	custom_security_attributes = CustomSecurityAttributeValue(
		additional_data = {
				"engineering" : {
						"@odata_type" : "#Microsoft.DirectoryServices.CustomSecurityAttributeValue",
						"num_vendors@odata_type" : "#Int32",
						"num_vendors" : 8,
				},
		}
	),
)

result = await graph_client.users.by_user_id('user-id').patch(request_body)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

#### Response

```http
HTTP/1.1 204 No Content
```

### Example 2: Update a custom security attribute assignment with a Boolean value for a user

The following example shows how to use the [Update user](https://learn.microsoft.com/en-us/graph/api/user-update) API to update a custom security attribute assignment with a Boolean value for a user.

- Attribute set: `Engineering`
- Attribute: `Certification`
- Attribute data type: Boolean
- Attribute value: `false`

#### Request

- [HTTP](#tabpanel_8_http)
- [C#](#tabpanel_8_csharp)
- [Go](#tabpanel_8_go)
- [Java](#tabpanel_8_java)
- [JavaScript](#tabpanel_8_javascript)
- [PHP](#tabpanel_8_php)
- [PowerShell](#tabpanel_8_powershell)
- [Python](#tabpanel_8_python)

```http
PATCH https://graph.microsoft.com/v1.0/users/{id}
Content-type: application/json

{
    "customSecurityAttributes":
    {
        "Engineering":
        {
            "@odata.type":"#Microsoft.DirectoryServices.CustomSecurityAttributeValue",
            "Certification":false
        }
    }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;
using Microsoft.Kiota.Abstractions.Serialization;

var requestBody = new User
{
	CustomSecurityAttributes = new CustomSecurityAttributeValue
	{
		AdditionalData = new Dictionary<string, object>
		{
			{
				"Engineering" , new UntypedObject(new Dictionary<string, UntypedNode>
				{
					{
						"@odata.type", new UntypedString("#Microsoft.DirectoryServices.CustomSecurityAttributeValue")
					},
					{
						"certification", new UntypedBoolean(false)
					},
				})
			},
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Users["{user-id}"].PatchAsync(requestBody);
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

requestBody := graphmodels.NewUser()
customSecurityAttributes := graphmodels.NewCustomSecurityAttributeValue()
additionalData := map[string]interface{}{
engineering := graph.New()
	certification := false
engineering.SetCertification(&certification) 
	customSecurityAttributes.SetEngineering(engineering)
}
customSecurityAttributes.SetAdditionalData(additionalData)
requestBody.SetCustomSecurityAttributes(customSecurityAttributes)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
users, err := graphClient.Users().ByUserId("user-id").Patch(context.Background(), requestBody, nil)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

User user = new User();
CustomSecurityAttributeValue customSecurityAttributes = new CustomSecurityAttributeValue();
HashMap<String, Object> additionalData = new HashMap<String, Object>();
 engineering = new ();
engineering.setOdataType("#Microsoft.DirectoryServices.CustomSecurityAttributeValue");
engineering.setCertification(false);
additionalData.put("Engineering", engineering);
customSecurityAttributes.setAdditionalData(additionalData);
user.setCustomSecurityAttributes(customSecurityAttributes);
User result = graphClient.users().byUserId("{user-id}").patch(user);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const user = {
    customSecurityAttributes: 
    {
        Engineering: 
        {
            '@odata.type':'#Microsoft.DirectoryServices.CustomSecurityAttributeValue',
            Certification: false
        }
    }
};

await client.api('/users/{id}')
	.update(user);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\User;
use Microsoft\Graph\Generated\Models\CustomSecurityAttributeValue;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new User();
$customSecurityAttributes = new CustomSecurityAttributeValue();
$additionalData = [
	'Engineering' => [
		'@odata.type' => '#Microsoft.DirectoryServices.CustomSecurityAttributeValue',
		'certification' => false,
	],
];
$customSecurityAttributes->setAdditionalData($additionalData);
$requestBody->setCustomSecurityAttributes($customSecurityAttributes);

$result = $graphServiceClient->users()->byUserId('user-id')->patch($requestBody)->wait();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```powershell

Import-Module Microsoft.Graph.Users

$params = @{
	customSecurityAttributes = @{
		Engineering = @{
			"@odata.type" = "#Microsoft.DirectoryServices.CustomSecurityAttributeValue"
			Certification = $false
		}
	}
}

Update-MgUser -UserId $userId -BodyParameter $params
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.user import User
from msgraph.generated.models.custom_security_attribute_value import CustomSecurityAttributeValue
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = User(
	custom_security_attributes = CustomSecurityAttributeValue(
		additional_data = {
				"engineering" : {
						"@odata_type" : "#Microsoft.DirectoryServices.CustomSecurityAttributeValue",
						"certification" : False,
				},
		}
	),
)

result = await graph_client.users.by_user_id('user-id').patch(request_body)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

#### Response

```http
HTTP/1.1 204 No Content
```

## List custom security attribute assignments

### Example 1: Get the custom security attribute assignments for a user

The following example shows how to use the [Get user](https://learn.microsoft.com/en-us/graph/api/user-get) API to get the custom security attribute assignments for a user.

Attribute #1

- Attribute set: `Engineering`
- Attribute: `Project`
- Attribute data type: Collection of Strings
- Attribute value: `["Baker","Cascade"]`

Attribute #2

- Attribute set: `Engineering`
- Attribute: `CostCenter`
- Attribute data type: Collection of Integers
- Attribute value: `[1001]`

Attribute #3

- Attribute set: `Engineering`
- Attribute: `Certification`
- Attribute data type: Boolean
- Attribute value: `true`

Attribute #4

- Attribute set: `Marketing`
- Attribute: `EmployeeId`
- Attribute data type: String
- Attribute value: `"QN26904"`

#### Request

- [HTTP](#tabpanel_9_http)
- [C#](#tabpanel_9_csharp)
- [Go](#tabpanel_9_go)
- [Java](#tabpanel_9_java)
- [JavaScript](#tabpanel_9_javascript)
- [PHP](#tabpanel_9_php)
- [PowerShell](#tabpanel_9_powershell)
- [Python](#tabpanel_9_python)

```msgraph
GET https://graph.microsoft.com/v1.0/users/{id}?$select=customSecurityAttributes
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Users["{user-id}"].GetAsync((requestConfiguration) =>
{
	requestConfiguration.QueryParameters.Select = new string []{ "customSecurityAttributes" };
});
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphusers "github.com/microsoftgraph/msgraph-sdk-go/users"
	  //other-imports
)

requestParameters := &graphusers.UserItemRequestBuilderGetQueryParameters{
	Select: [] string {"customSecurityAttributes"},
}
configuration := &graphusers.UserItemRequestBuilderGetRequestConfiguration{
	QueryParameters: requestParameters,
}

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
users, err := graphClient.Users().ByUserId("user-id").Get(context.Background(), configuration)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

User result = graphClient.users().byUserId("{user-id}").get(requestConfiguration -> {
	requestConfiguration.queryParameters.select = new String []{"customSecurityAttributes"};
});
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let user = await client.api('/users/{id}')
	.select('customSecurityAttributes')
	.get();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Users\Item\UserItemRequestBuilderGetRequestConfiguration;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestConfiguration = new UserItemRequestBuilderGetRequestConfiguration();
$queryParameters = UserItemRequestBuilderGetRequestConfiguration::createQueryParameters();
$queryParameters->select = ["customSecurityAttributes"];
$requestConfiguration->queryParameters = $queryParameters;


$result = $graphServiceClient->users()->byUserId('user-id')->get($requestConfiguration)->wait();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```powershell

Import-Module Microsoft.Graph.Users

Get-MgUser -UserId $userId -Property "customSecurityAttributes" 
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.users.item.user_item_request_builder import UserItemRequestBuilder
from kiota_abstractions.base_request_configuration import RequestConfiguration
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
query_params = UserItemRequestBuilder.UserItemRequestBuilderGetQueryParameters(
		select = ["customSecurityAttributes"],
)

request_configuration = RequestConfiguration(
query_parameters = query_params,
)

result = await graph_client.users.by_user_id('user-id').get(request_configuration = request_configuration)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

#### Response

```http
HTTP/1.1 200 OK

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#users(customSecurityAttributes)/$entity",
    "customSecurityAttributes": {
        "Marketing": {
            "@odata.type": "#microsoft.graph.customSecurityAttributeValue",
            "EmployeeId": "QN26904"
        },
        "Engineering": {
            "@odata.type": "#microsoft.graph.customSecurityAttributeValue",
            "Project@odata.type": "#Collection(String)",
            "Project": [
                "Baker",
                "Cascade"
            ],
            "CostCenter@odata.type": "#Collection(Int32)",
            "CostCenter": [
                1001
            ],
            "Certification": true
        }
    }
}
```

If there are no custom security attributes assigned to the user or if the calling principal does not have access, the following will be the response:

```http
HTTP/1.1 200 OK
Content-type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#users(customSecurityAttributes)/$entity",
    "customSecurityAttributes": null
}
```

### Example 2: List all users with a custom security attribute assignment that equals a value

The following example shows how to use the [List users](https://learn.microsoft.com/en-us/graph/api/user-list) API to list all users with a custom security attribute assignment that equals a value. The example retrieves users with a custom security attribute named `AppCountry` with a value that equals `Canada`. The filter value is case sensitive. You must add `ConsistencyLevel=eventual` in the request or the header. You must also include `$count=true` to ensure the request is routed correctly.

User #1

- Attribute set: `Marketing`
- Attribute: `AppCountry`
- Attribute data type: Collection of Strings
- Attribute value: `["India","Canada"]`

User #2

- Attribute set: `Marketing`
- Attribute: `AppCountry`
- Attribute data type: Collection of Strings
- Attribute value: `["Canada","Mexico"]`

#### Request

- [HTTP](#tabpanel_10_http)
- [C#](#tabpanel_10_csharp)
- [Go](#tabpanel_10_go)
- [Java](#tabpanel_10_java)
- [JavaScript](#tabpanel_10_javascript)
- [PHP](#tabpanel_10_php)
- [PowerShell](#tabpanel_10_powershell)
- [Python](#tabpanel_10_python)

```msgraph
GET https://graph.microsoft.com/v1.0/users?$count=true&$select=id,displayName,customSecurityAttributes&$filter=customSecurityAttributes/Marketing/AppCountry eq 'Canada'
ConsistencyLevel: eventual
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Users.GetAsync((requestConfiguration) =>
{
	requestConfiguration.QueryParameters.Count = true;
	requestConfiguration.QueryParameters.Select = new string []{ "id","displayName","customSecurityAttributes" };
	requestConfiguration.QueryParameters.Filter = "customSecurityAttributes/Marketing/AppCountry eq 'Canada'";
	requestConfiguration.Headers.Add("ConsistencyLevel", "eventual");
});
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  abstractions "github.com/microsoft/kiota-abstractions-go"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphusers "github.com/microsoftgraph/msgraph-sdk-go/users"
	  //other-imports
)

headers := abstractions.NewRequestHeaders()
headers.Add("ConsistencyLevel", "eventual")


requestCount := true
requestFilter := "customSecurityAttributes/Marketing/AppCountry eq 'Canada'"

requestParameters := &graphusers.UsersRequestBuilderGetQueryParameters{
	Count: &requestCount,
	Select: [] string {"id","displayName","customSecurityAttributes"},
	Filter: &requestFilter,
}
configuration := &graphusers.UsersRequestBuilderGetRequestConfiguration{
	Headers: headers,
	QueryParameters: requestParameters,
}

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
users, err := graphClient.Users().Get(context.Background(), configuration)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

UserCollectionResponse result = graphClient.users().get(requestConfiguration -> {
	requestConfiguration.queryParameters.count = true;
	requestConfiguration.queryParameters.select = new String []{"id", "displayName", "customSecurityAttributes"};
	requestConfiguration.queryParameters.filter = "customSecurityAttributes/Marketing/AppCountry eq 'Canada'";
	requestConfiguration.headers.add("ConsistencyLevel", "eventual");
});
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let users = await client.api('/users')
	.header('ConsistencyLevel','eventual')
	.filter('customSecurityAttributes/Marketing/AppCountry eq \'Canada\'')
	.select('id,displayName,customSecurityAttributes')
	.get();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Users\UsersRequestBuilderGetRequestConfiguration;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestConfiguration = new UsersRequestBuilderGetRequestConfiguration();
$headers = [
		'ConsistencyLevel' => 'eventual',
	];
$requestConfiguration->headers = $headers;

$queryParameters = UsersRequestBuilderGetRequestConfiguration::createQueryParameters();
$queryParameters->count = true;
$queryParameters->select = ["id","displayName","customSecurityAttributes"];
$queryParameters->filter = "customSecurityAttributes/Marketing/AppCountry eq 'Canada'";
$requestConfiguration->queryParameters = $queryParameters;


$result = $graphServiceClient->users()->get($requestConfiguration)->wait();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```powershell

Import-Module Microsoft.Graph.Users

Get-MgUser -CountVariable CountVar -Property "id,displayName,customSecurityAttributes" -Filter "customSecurityAttributes/Marketing/AppCountry eq 'Canada'"  -ConsistencyLevel eventual 
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.users.users_request_builder import UsersRequestBuilder
from kiota_abstractions.base_request_configuration import RequestConfiguration
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
query_params = UsersRequestBuilder.UsersRequestBuilderGetQueryParameters(
		count = True,
		select = ["id","displayName","customSecurityAttributes"],
		filter = "customSecurityAttributes/Marketing/AppCountry eq 'Canada'",
)

request_configuration = RequestConfiguration(
query_parameters = query_params,
)
request_configuration.headers.add("ConsistencyLevel", "eventual")


result = await graph_client.users.get(request_configuration = request_configuration)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

#### Response

```http
HTTP/1.1 200 OK

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#users(id,displayName,customSecurityAttributes)",
    "@odata.count": 2,
    "value": [
        {
            "id": "dbaf3778-4f81-4ea0-ac1c-502a293c12ac",
            "displayName": "Jiya",
            "customSecurityAttributes": {
                "Engineering": {
                    "@odata.type": "#microsoft.graph.customSecurityAttributeValue",
                    "Datacenter@odata.type": "#Collection(String)",
                    "Datacenter": [
                        "India"
                    ]
                },
                "Marketing": {
                    "@odata.type": "#microsoft.graph.customSecurityAttributeValue",
                    "AppCountry@odata.type": "#Collection(String)",
                    "AppCountry": [
                        "India",
                        "Canada"
                    ],
                    "EmployeeId": "KX19476"
                }
            }
        },
        {
            "id": "6bac433c-48c6-4213-a316-1428de32701b",
            "displayName": "Jana",
            "customSecurityAttributes": {
                "Marketing": {
                    "@odata.type": "#microsoft.graph.customSecurityAttributeValue",
                    "AppCountry@odata.type": "#Collection(String)",
                    "AppCountry": [
                        "Canada",
                        "Mexico"
                    ],
                    "EmployeeId": "GS46982"
                }
            }
        }
    ]
}
```

### Example 3: List all users with a custom security attribute assignment that starts with a value

The following example shows how to use the [List users](https://learn.microsoft.com/en-us/graph/api/user-list) API to list all users with a custom security attribute assignment that starts with a value. The example retrieves users with a custom security attribute named `EmployeeId` with a value that starts with `GS`. The filter value is case sensitive. You must add `ConsistencyLevel=eventual` in the request or the header. You must also include `$count=true` to ensure the request is routed correctly.

User #1

- Attribute set: `Marketing`
- Attribute: `EmployeeId`
- Attribute data type: String
- Attribute value: `"KX19476"`

User #2

- Attribute set: `Marketing`
- Attribute: `EmployeeId`
- Attribute data type: String
- Attribute value: `"GS46982"`

#### Request

- [HTTP](#tabpanel_11_http)
- [C#](#tabpanel_11_csharp)
- [Go](#tabpanel_11_go)
- [Java](#tabpanel_11_java)
- [JavaScript](#tabpanel_11_javascript)
- [PHP](#tabpanel_11_php)
- [PowerShell](#tabpanel_11_powershell)
- [Python](#tabpanel_11_python)

```msgraph
GET https://graph.microsoft.com/v1.0/users?$count=true&$select=id,displayName,customSecurityAttributes&$filter=startsWith(customSecurityAttributes/Marketing/EmployeeId,'GS')
ConsistencyLevel: eventual
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Users.GetAsync((requestConfiguration) =>
{
	requestConfiguration.QueryParameters.Count = true;
	requestConfiguration.QueryParameters.Select = new string []{ "id","displayName","customSecurityAttributes" };
	requestConfiguration.QueryParameters.Filter = "startsWith(customSecurityAttributes/Marketing/EmployeeId,'GS')";
	requestConfiguration.Headers.Add("ConsistencyLevel", "eventual");
});
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  abstractions "github.com/microsoft/kiota-abstractions-go"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphusers "github.com/microsoftgraph/msgraph-sdk-go/users"
	  //other-imports
)

headers := abstractions.NewRequestHeaders()
headers.Add("ConsistencyLevel", "eventual")


requestCount := true
requestFilter := "startsWith(customSecurityAttributes/Marketing/EmployeeId,'GS')"

requestParameters := &graphusers.UsersRequestBuilderGetQueryParameters{
	Count: &requestCount,
	Select: [] string {"id","displayName","customSecurityAttributes"},
	Filter: &requestFilter,
}
configuration := &graphusers.UsersRequestBuilderGetRequestConfiguration{
	Headers: headers,
	QueryParameters: requestParameters,
}

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
users, err := graphClient.Users().Get(context.Background(), configuration)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

UserCollectionResponse result = graphClient.users().get(requestConfiguration -> {
	requestConfiguration.queryParameters.count = true;
	requestConfiguration.queryParameters.select = new String []{"id", "displayName", "customSecurityAttributes"};
	requestConfiguration.queryParameters.filter = "startsWith(customSecurityAttributes/Marketing/EmployeeId,'GS')";
	requestConfiguration.headers.add("ConsistencyLevel", "eventual");
});
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let users = await client.api('/users')
	.header('ConsistencyLevel','eventual')
	.filter('startsWith(customSecurityAttributes/Marketing/EmployeeId,\'GS\')')
	.select('id,displayName,customSecurityAttributes')
	.get();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Users\UsersRequestBuilderGetRequestConfiguration;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestConfiguration = new UsersRequestBuilderGetRequestConfiguration();
$headers = [
		'ConsistencyLevel' => 'eventual',
	];
$requestConfiguration->headers = $headers;

$queryParameters = UsersRequestBuilderGetRequestConfiguration::createQueryParameters();
$queryParameters->count = true;
$queryParameters->select = ["id","displayName","customSecurityAttributes"];
$queryParameters->filter = "startsWith(customSecurityAttributes/Marketing/EmployeeId,'GS')";
$requestConfiguration->queryParameters = $queryParameters;


$result = $graphServiceClient->users()->get($requestConfiguration)->wait();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```powershell

Import-Module Microsoft.Graph.Users

Get-MgUser -CountVariable CountVar -Property "id,displayName,customSecurityAttributes" -Filter "startsWith(customSecurityAttributes/Marketing/EmployeeId,'GS')"  -ConsistencyLevel eventual 
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.users.users_request_builder import UsersRequestBuilder
from kiota_abstractions.base_request_configuration import RequestConfiguration
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
query_params = UsersRequestBuilder.UsersRequestBuilderGetQueryParameters(
		count = True,
		select = ["id","displayName","customSecurityAttributes"],
		filter = "startsWith(customSecurityAttributes/Marketing/EmployeeId,'GS')",
)

request_configuration = RequestConfiguration(
query_parameters = query_params,
)
request_configuration.headers.add("ConsistencyLevel", "eventual")


result = await graph_client.users.get(request_configuration = request_configuration)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

#### Response

```http
HTTP/1.1 200 OK

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#users(id,displayName,customSecurityAttributes)",
    "@odata.count": 1,
    "value": [
        {
            "id": "6bac433c-48c6-4213-a316-1428de32701b",
            "displayName": "Jana",
            "customSecurityAttributes": {
                "Marketing": {
                    "@odata.type": "#microsoft.graph.customSecurityAttributeValue",
                    "AppCountry@odata.type": "#Collection(String)",
                    "AppCountry": [
                        "Canada",
                        "Mexico"
                    ],
                    "EmployeeId": "GS46982"
                }
            }
        }
    ]
}
```

### Example 4: List all users with a custom security attribute assignment that does not equal a value

The following example shows how to use the [List users](https://learn.microsoft.com/en-us/graph/api/user-list) API to list all users with a custom security attribute assignment that does not equal a value. The example retrieves users with a custom security attribute named `AppCountry` with a value that does not equal `Canada`. The filter value is case sensitive. You must add `ConsistencyLevel=eventual` in the request or the header. You must also include `$count=true` to ensure the request is routed correctly.

User #1

- Attribute set: `Marketing`
- Attribute: `AppCountry`
- Attribute data type: Collection of Strings
- Attribute value: `["France"]`

All other users

- `AppCountry` attribute not added

#### Request

- [HTTP](#tabpanel_12_http)
- [C#](#tabpanel_12_csharp)
- [Go](#tabpanel_12_go)
- [Java](#tabpanel_12_java)
- [JavaScript](#tabpanel_12_javascript)
- [PHP](#tabpanel_12_php)
- [PowerShell](#tabpanel_12_powershell)
- [Python](#tabpanel_12_python)

```msgraph
GET https://graph.microsoft.com/v1.0/users?$count=true&$select=id,displayName,customSecurityAttributes&$filter=customSecurityAttributes/Marketing/AppCountry ne 'Canada'
ConsistencyLevel: eventual
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Users.GetAsync((requestConfiguration) =>
{
	requestConfiguration.QueryParameters.Count = true;
	requestConfiguration.QueryParameters.Select = new string []{ "id","displayName","customSecurityAttributes" };
	requestConfiguration.QueryParameters.Filter = "customSecurityAttributes/Marketing/AppCountry ne 'Canada'";
	requestConfiguration.Headers.Add("ConsistencyLevel", "eventual");
});
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  abstractions "github.com/microsoft/kiota-abstractions-go"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphusers "github.com/microsoftgraph/msgraph-sdk-go/users"
	  //other-imports
)

headers := abstractions.NewRequestHeaders()
headers.Add("ConsistencyLevel", "eventual")


requestCount := true
requestFilter := "customSecurityAttributes/Marketing/AppCountry ne 'Canada'"

requestParameters := &graphusers.UsersRequestBuilderGetQueryParameters{
	Count: &requestCount,
	Select: [] string {"id","displayName","customSecurityAttributes"},
	Filter: &requestFilter,
}
configuration := &graphusers.UsersRequestBuilderGetRequestConfiguration{
	Headers: headers,
	QueryParameters: requestParameters,
}

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
users, err := graphClient.Users().Get(context.Background(), configuration)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

UserCollectionResponse result = graphClient.users().get(requestConfiguration -> {
	requestConfiguration.queryParameters.count = true;
	requestConfiguration.queryParameters.select = new String []{"id", "displayName", "customSecurityAttributes"};
	requestConfiguration.queryParameters.filter = "customSecurityAttributes/Marketing/AppCountry ne 'Canada'";
	requestConfiguration.headers.add("ConsistencyLevel", "eventual");
});
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let users = await client.api('/users')
	.header('ConsistencyLevel','eventual')
	.filter('customSecurityAttributes/Marketing/AppCountry ne \'Canada\'')
	.select('id,displayName,customSecurityAttributes')
	.get();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Users\UsersRequestBuilderGetRequestConfiguration;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestConfiguration = new UsersRequestBuilderGetRequestConfiguration();
$headers = [
		'ConsistencyLevel' => 'eventual',
	];
$requestConfiguration->headers = $headers;

$queryParameters = UsersRequestBuilderGetRequestConfiguration::createQueryParameters();
$queryParameters->count = true;
$queryParameters->select = ["id","displayName","customSecurityAttributes"];
$queryParameters->filter = "customSecurityAttributes/Marketing/AppCountry ne 'Canada'";
$requestConfiguration->queryParameters = $queryParameters;


$result = $graphServiceClient->users()->get($requestConfiguration)->wait();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```powershell

Import-Module Microsoft.Graph.Users

Get-MgUser -CountVariable CountVar -Property "id,displayName,customSecurityAttributes" -Filter "customSecurityAttributes/Marketing/AppCountry ne 'Canada'"  -ConsistencyLevel eventual 
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.users.users_request_builder import UsersRequestBuilder
from kiota_abstractions.base_request_configuration import RequestConfiguration
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
query_params = UsersRequestBuilder.UsersRequestBuilderGetQueryParameters(
		count = True,
		select = ["id","displayName","customSecurityAttributes"],
		filter = "customSecurityAttributes/Marketing/AppCountry ne 'Canada'",
)

request_configuration = RequestConfiguration(
query_parameters = query_params,
)
request_configuration.headers.add("ConsistencyLevel", "eventual")


result = await graph_client.users.get(request_configuration = request_configuration)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

#### Response

```http
HTTP/1.1 200 OK

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#users(id,displayName,customSecurityAttributes)",
    "@odata.count": 32,
    "value": [
        {
            "id": "c4f9ecd3-d3c1-4544-b49a-bc9bb62beb67",
            "displayName": "Alain",
            "customSecurityAttributes": null
        },
        {
            "id": "de4f1218-b0fb-4449-b3a0-1e1dd193e6e7",
            "displayName": "Joe",
            "customSecurityAttributes": {
                "Engineering": {
                    "@odata.type": "#microsoft.graph.customSecurityAttributeValue",
                    "Project3@odata.type": "#Collection(String)",
                    "Project3": [
                        "Baker",
                        "Cascade"
                    ],
                    "CostCenter@odata.type": "#Collection(Int32)",
                    "CostCenter": [
                        1001
                    ],
                    "Certification": true
                },
                "Marketing": {
                    "@odata.type": "#microsoft.graph.customSecurityAttributeValue",
                    "EmployeeId": "QN26904"
                }
            }
        },
        {
            "id": "f24d1474-ded5-432d-be08-8abd39921aac",
            "displayName": "Isabella",
            "customSecurityAttributes": {
                "Marketing": {
                    "@odata.type": "#microsoft.graph.customSecurityAttributeValue",
                    "AppCountry@odata.type": "#Collection(String)",
                    "AppCountry": [
                        "France"
                    ]
                }
            }
        },
        {
            "id": "849e81fe-1109-4d57-9536-a25d537eec1f",
            "displayName": "Dara",
            "customSecurityAttributes": {
                "Engineering": {
                    "@odata.type": "#microsoft.graph.customSecurityAttributeValue",
                    "ProjectDate": "2023-04-12"
                }
            }
        },
        {
            "id": "42c88239-db99-45f0-85af-cbb6c8acb2a3",
            "displayName": "Chandra",
            "customSecurityAttributes": null
        }
    ]
}
```

## Remove custom security attribute assignments

### Example 1: Remove a single-valued custom security attribute assignment from a user

The following example shows how to use the [Update user](https://learn.microsoft.com/en-us/graph/api/user-update) API to remove a custom security attribute assignment that supports a single value from a user.

- Attribute set: `Engineering`
- Attribute: `ProjectDate`
- Attribute value: `null`

#### Request

- [HTTP](#tabpanel_13_http)
- [C#](#tabpanel_13_csharp)
- [Go](#tabpanel_13_go)
- [Java](#tabpanel_13_java)
- [JavaScript](#tabpanel_13_javascript)
- [PHP](#tabpanel_13_php)
- [PowerShell](#tabpanel_13_powershell)
- [Python](#tabpanel_13_python)

```http
PATCH https://graph.microsoft.com/v1.0/users/{id}
Content-type: application/json

{
    "customSecurityAttributes":
    {
        "Engineering":
        {
            "@odata.type":"#Microsoft.DirectoryServices.CustomSecurityAttributeValue",
            "ProjectDate":null
        }
    }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;
using Microsoft.Kiota.Abstractions.Serialization;

var requestBody = new User
{
	CustomSecurityAttributes = new CustomSecurityAttributeValue
	{
		AdditionalData = new Dictionary<string, object>
		{
			{
				"Engineering" , new UntypedObject(new Dictionary<string, UntypedNode>
				{
					{
						"@odata.type", new UntypedString("#Microsoft.DirectoryServices.CustomSecurityAttributeValue")
					},
					{
						"projectDate", new UntypedNull()
					},
				})
			},
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Users["{user-id}"].PatchAsync(requestBody);
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

requestBody := graphmodels.NewUser()
customSecurityAttributes := graphmodels.NewCustomSecurityAttributeValue()
additionalData := map[string]interface{}{
engineering := graph.New()
	projectDate := null
engineering.SetProjectDate(&projectDate) 
	customSecurityAttributes.SetEngineering(engineering)
}
customSecurityAttributes.SetAdditionalData(additionalData)
requestBody.SetCustomSecurityAttributes(customSecurityAttributes)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
users, err := graphClient.Users().ByUserId("user-id").Patch(context.Background(), requestBody, nil)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

User user = new User();
CustomSecurityAttributeValue customSecurityAttributes = new CustomSecurityAttributeValue();
HashMap<String, Object> additionalData = new HashMap<String, Object>();
 engineering = new ();
engineering.setOdataType("#Microsoft.DirectoryServices.CustomSecurityAttributeValue");
engineering.setProjectDate(null);
additionalData.put("Engineering", engineering);
customSecurityAttributes.setAdditionalData(additionalData);
user.setCustomSecurityAttributes(customSecurityAttributes);
User result = graphClient.users().byUserId("{user-id}").patch(user);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const user = {
    customSecurityAttributes: 
    {
        Engineering: 
        {
            '@odata.type':'#Microsoft.DirectoryServices.CustomSecurityAttributeValue',
            ProjectDate: null
        }
    }
};

await client.api('/users/{id}')
	.update(user);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\User;
use Microsoft\Graph\Generated\Models\CustomSecurityAttributeValue;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new User();
$customSecurityAttributes = new CustomSecurityAttributeValue();
$additionalData = [
	'Engineering' => [
		'@odata.type' => '#Microsoft.DirectoryServices.CustomSecurityAttributeValue',
		'projectDate' => null,
	],
];
$customSecurityAttributes->setAdditionalData($additionalData);
$requestBody->setCustomSecurityAttributes($customSecurityAttributes);

$result = $graphServiceClient->users()->byUserId('user-id')->patch($requestBody)->wait();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```powershell

Import-Module Microsoft.Graph.Users

$params = @{
	customSecurityAttributes = @{
		Engineering = @{
			"@odata.type" = "#Microsoft.DirectoryServices.CustomSecurityAttributeValue"
			ProjectDate = $null
		}
	}
}

Update-MgUser -UserId $userId -BodyParameter $params
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.user import User
from msgraph.generated.models.custom_security_attribute_value import CustomSecurityAttributeValue
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = User(
	custom_security_attributes = CustomSecurityAttributeValue(
		additional_data = {
				"engineering" : {
						"@odata_type" : "#Microsoft.DirectoryServices.CustomSecurityAttributeValue",
						"project_date" : None,
				},
		}
	),
)

result = await graph_client.users.by_user_id('user-id').patch(request_body)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

#### Response

```http
HTTP/1.1 204 No Content
```

### Example 2: Remove a multi-valued custom security attribute assignment from a user

The following example shows how to use the [Update user](https://learn.microsoft.com/en-us/graph/api/user-update) API to remove a custom security attribute assignment that supports multiple values from a user.

- Attribute set: `Engineering`
- Attribute: `Project`
- Attribute value: `[]`

#### Request

- [HTTP](#tabpanel_14_http)
- [C#](#tabpanel_14_csharp)
- [Go](#tabpanel_14_go)
- [Java](#tabpanel_14_java)
- [JavaScript](#tabpanel_14_javascript)
- [PHP](#tabpanel_14_php)
- [PowerShell](#tabpanel_14_powershell)
- [Python](#tabpanel_14_python)

```http
PATCH https://graph.microsoft.com/v1.0/users/{id}
Content-type: application/json

{
    "customSecurityAttributes":
    {
        "Engineering":
        {
            "@odata.type":"#Microsoft.DirectoryServices.CustomSecurityAttributeValue",
            "Project":[]
        }
    }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;
using Microsoft.Kiota.Abstractions.Serialization;

var requestBody = new User
{
	CustomSecurityAttributes = new CustomSecurityAttributeValue
	{
		AdditionalData = new Dictionary<string, object>
		{
			{
				"Engineering" , new UntypedObject(new Dictionary<string, UntypedNode>
				{
					{
						"@odata.type", new UntypedString("#Microsoft.DirectoryServices.CustomSecurityAttributeValue")
					},
					{
						"project", new UntypedArray(new List<UntypedNode>
						{
						})
					},
				})
			},
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Users["{user-id}"].PatchAsync(requestBody);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

User user = new User();
CustomSecurityAttributeValue customSecurityAttributes = new CustomSecurityAttributeValue();
HashMap<String, Object> additionalData = new HashMap<String, Object>();
 engineering = new ();
engineering.setOdataType("#Microsoft.DirectoryServices.CustomSecurityAttributeValue");
LinkedList<Object> project = new LinkedList<Object>();
engineering.setProject(project);
additionalData.put("Engineering", engineering);
customSecurityAttributes.setAdditionalData(additionalData);
user.setCustomSecurityAttributes(customSecurityAttributes);
User result = graphClient.users().byUserId("{user-id}").patch(user);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const user = {
    customSecurityAttributes: 
    {
        Engineering: 
        {
            '@odata.type':'#Microsoft.DirectoryServices.CustomSecurityAttributeValue',
            Project: []
        }
    }
};

await client.api('/users/{id}')
	.update(user);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\User;
use Microsoft\Graph\Generated\Models\CustomSecurityAttributeValue;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new User();
$customSecurityAttributes = new CustomSecurityAttributeValue();
$additionalData = [
	'Engineering' => [
		'@odata.type' => '#Microsoft.DirectoryServices.CustomSecurityAttributeValue',
		'project' => [],
	],
];
$customSecurityAttributes->setAdditionalData($additionalData);
$requestBody->setCustomSecurityAttributes($customSecurityAttributes);

$result = $graphServiceClient->users()->byUserId('user-id')->patch($requestBody)->wait();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```powershell

Import-Module Microsoft.Graph.Users

$params = @{
	customSecurityAttributes = @{
		Engineering = @{
			"@odata.type" = "#Microsoft.DirectoryServices.CustomSecurityAttributeValue"
			Project = @(
			)
		}
	}
}

Update-MgUser -UserId $userId -BodyParameter $params
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.user import User
from msgraph.generated.models.custom_security_attribute_value import CustomSecurityAttributeValue
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = User(
	custom_security_attributes = CustomSecurityAttributeValue(
		additional_data = {
				"engineering" : {
						"@odata_type" : "#Microsoft.DirectoryServices.CustomSecurityAttributeValue",
						"project" : [
						],
				},
		}
	),
)

result = await graph_client.users.by_user_id('user-id').patch(request_body)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

#### Response

```http
HTTP/1.1 204 No Content
```

## Next step

[Overview of custom security attributes using the Microsoft Graph API](https://learn.microsoft.com/en-us/graph/api/resources/custom-security-attributes-overview)
