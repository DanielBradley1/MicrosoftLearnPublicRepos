<!-- Source: https://learn.microsoft.com/en-us/graph/extensibility-overview -->
<!-- Sitemap-Last-Modified: 2025-08-29 -->

# Add custom data to resources by using extensions

Microsoft Graph provides a single API endpoint to access rich people-centric data and insights through resources such as [user](https://learn.microsoft.com/en-us/graph/api/resources/user) and [message](https://learn.microsoft.com/en-us/graph/api/resources/message). You can also extend Microsoft Graph by adding custom properties to resource instances without requiring an external data store.

This article describes how Microsoft Graph supports extending its resources, the options available to add custom properties, and when to use them.

Important

Don't use extensions to store sensitive personally identifiable information, such as account credentials, government identification numbers, cardholder data, financial account data, healthcare information, or sensitive background information.

The extensions mentioned in this article aren't similar to the following features:

- [Custom security attributes](https://learn.microsoft.com/en-us/graph/api/resources/custom-security-attributes-overview). To understand their differences, see [How do custom security attributes compare with extensions?](https://learn.microsoft.com/en-us/entra/fundamentals/custom-security-attributes-overview#how-do-custom-security-attributes-compare-with-extensions)
- [Custom authentication extensions](https://learn.microsoft.com/en-us/entra/external-id/customers/concept-custom-extensions) that are supported for token customization and extending authentication flows.

## Why add custom data to Microsoft Graph?

- As an ISV developer, you might decide to keep your app lightweight and store app-specific user profile data in Microsoft Graph by extending the **user** resource.
- Alternatively, you might want to retain your app's existing user profile store, and add an app-specific identifier to the **user** resource.
- As an enterprise developer, the in-house applications that you build might rely on your organization's HR-specific data. Integration within multiple applications can be simplified by storing this custom data in Microsoft Graph.

## Custom data options in Microsoft Graph

Microsoft Graph offers four types of extensions for adding custom data.

- Extension attributes
- Directory \(Microsoft Entra ID\) extensions
- Schema extensions
- Open extensions

## Extension attributes

Microsoft Entra ID offers a set of 15 extension attributes with predefined names on the [user](https://learn.microsoft.com/en-us/graph/api/resources/onpremisesextensionattributes) and [device](https://learn.microsoft.com/en-us/graph/api/resources/onpremisesextensionattributes) resources. These properties were initially custom attributes provided in on-premises Active Directory \(AD\) and Microsoft Exchange. However, you can now use them for more than syncing on-premises AD and Microsoft Exchange data to Microsoft Entra ID through Microsoft Graph.

For more information about these attributes in Microsoft Exchange, see [Custom attributes in Exchange Server](https://learn.microsoft.com/en-us/exchange/recipients/mailbox-custom-attributes).

### Developer experience

You can use the 15 extension attributes to store string values on **user** or **device** resource instances, through the **onPremisesExtensionAttributes** and **extensionAttributes** properties respectively. You can assign the values while creating a new resource instance or while updating an existing resource instance. You can also filter by the values.

#### Add or update data in extension attributes

The following example shows how to store data in **extensionAttribute1** and delete existing data from **extensionAttribute13** through an update operation with a PATCH method.

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [PowerShell](#tabpanel_1_powershell)
- [Python](#tabpanel_1_python)

```http
PATCH https://graph.microsoft.com/v1.0/users/071cc716-8147-4397-a5ba-b2105951cc0b

{
    "onPremisesExtensionAttributes": {
        "extensionAttribute1": "skypeId.adeleVance",
        "extensionAttribute13": null
    }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new User
{
	OnPremisesExtensionAttributes = new OnPremisesExtensionAttributes
	{
		ExtensionAttribute1 = "skypeId.adeleVance",
		ExtensionAttribute13 = null,
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
onPremisesExtensionAttributes := graphmodels.NewOnPremisesExtensionAttributes()
extensionAttribute1 := "skypeId.adeleVance"
onPremisesExtensionAttributes.SetExtensionAttribute1(&extensionAttribute1) 
extensionAttribute13 := null
onPremisesExtensionAttributes.SetExtensionAttribute13(&extensionAttribute13) 
requestBody.SetOnPremisesExtensionAttributes(onPremisesExtensionAttributes)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
users, err := graphClient.Users().ByUserId("user-id").Patch(context.Background(), requestBody, nil)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

User user = new User();
OnPremisesExtensionAttributes onPremisesExtensionAttributes = new OnPremisesExtensionAttributes();
onPremisesExtensionAttributes.setExtensionAttribute1("skypeId.adeleVance");
onPremisesExtensionAttributes.setExtensionAttribute13(null);
user.setOnPremisesExtensionAttributes(onPremisesExtensionAttributes);
User result = graphClient.users().byUserId("{user-id}").patch(user);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const user = {
    onPremisesExtensionAttributes: {
        extensionAttribute1: 'skypeId.adeleVance',
        extensionAttribute13: null
    }
};

await client.api('/users/071cc716-8147-4397-a5ba-b2105951cc0b')
	.update(user);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\User;
use Microsoft\Graph\Generated\Models\OnPremisesExtensionAttributes;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new User();
$onPremisesExtensionAttributes = new OnPremisesExtensionAttributes();
$onPremisesExtensionAttributes->setExtensionAttribute1('skypeId.adeleVance');
$onPremisesExtensionAttributes->setExtensionAttribute13(null);
$requestBody->setOnPremisesExtensionAttributes($onPremisesExtensionAttributes);

$result = $graphServiceClient->users()->byUserId('user-id')->patch($requestBody)->wait();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```powershell

Import-Module Microsoft.Graph.Users

$params = @{
	onPremisesExtensionAttributes = @{
		extensionAttribute1 = "skypeId.adeleVance"
		extensionAttribute13 = $null
	}
}

Update-MgUser -UserId $userId -BodyParameter $params
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.user import User
from msgraph.generated.models.on_premises_extension_attributes import OnPremisesExtensionAttributes
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = User(
	on_premises_extension_attributes = OnPremisesExtensionAttributes(
		extension_attribute1 = "skypeId.adeleVance",
		extension_attribute13 = None,
	),
)

result = await graph_client.users.by_user_id('user-id').patch(request_body)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

The request returns a `204 No Content` response object.

#### Read the extension attributes

##### Request

- [HTTP](#tabpanel_2_http)
- [C#](#tabpanel_2_csharp)
- [Go](#tabpanel_2_go)
- [Java](#tabpanel_2_java)
- [JavaScript](#tabpanel_2_javascript)
- [PHP](#tabpanel_2_php)
- [PowerShell](#tabpanel_2_powershell)
- [Python](#tabpanel_2_python)

```msgraph
GET https://graph.microsoft.com/v1.0/users?$select=id,displayName,onPremisesExtensionAttributes
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Users.GetAsync((requestConfiguration) =>
{
	requestConfiguration.QueryParameters.Select = new string []{ "id","displayName","onPremisesExtensionAttributes" };
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

requestParameters := &graphusers.UsersRequestBuilderGetQueryParameters{
	Select: [] string {"id","displayName","onPremisesExtensionAttributes"},
}
configuration := &graphusers.UsersRequestBuilderGetRequestConfiguration{
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
	requestConfiguration.queryParameters.select = new String []{"id", "displayName", "onPremisesExtensionAttributes"};
});
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let users = await client.api('/users')
	.select('id,displayName,onPremisesExtensionAttributes')
	.get();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Users\UsersRequestBuilderGetRequestConfiguration;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestConfiguration = new UsersRequestBuilderGetRequestConfiguration();
$queryParameters = UsersRequestBuilderGetRequestConfiguration::createQueryParameters();
$queryParameters->select = ["id","displayName","onPremisesExtensionAttributes"];
$requestConfiguration->queryParameters = $queryParameters;


$result = $graphServiceClient->users()->get($requestConfiguration)->wait();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```powershell

Import-Module Microsoft.Graph.Users

Get-MgUser -Property "id,displayName,onPremisesExtensionAttributes" 
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.users.users_request_builder import UsersRequestBuilder
from kiota_abstractions.base_request_configuration import RequestConfiguration
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
query_params = UsersRequestBuilder.UsersRequestBuilderGetQueryParameters(
		select = ["id","displayName","onPremisesExtensionAttributes"],
)

request_configuration = RequestConfiguration(
query_parameters = query_params,
)

result = await graph_client.users.get(request_configuration = request_configuration)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

##### Response

```http
{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#users(id,displayName,onPremisesExtensionAttributes)",
    "value": [
        {
            "id": "071cc716-8147-4397-a5ba-b2105951cc0b",
            "displayName": "Adele Vance",
            "onPremisesExtensionAttributes": {
                "extensionAttribute1": "Contractor",
                "extensionAttribute2": "50",
                "extensionAttribute3": null,
                "extensionAttribute4": "1478354",
                "extensionAttribute5": "10239390",
                "extensionAttribute6": null,
                "extensionAttribute7": null,
                "extensionAttribute8": null,
                "extensionAttribute9": null,
                "extensionAttribute10": "11",
                "extensionAttribute11": null,
                "extensionAttribute12": "/o=ExchangeLabs/ou=Exchange Administrative Group (FYDIBOHF47SPDLT)/cn=Recipients/cn=5ee781fc7egc7aa0b9394bddb44e7f04-Adele Vance",
                "extensionAttribute13": null,
                "extensionAttribute14": null,
                "extensionAttribute15": null
            }
        }
    ]
}
```

### Considerations for using extension attribute properties

You can update the **onPremisesExtensionAttributes** object only for objects that aren't synced from on-premises AD.

Microsoft Graph already defines the 15 extension attributes, and you can't change their property names. Therefore, you can't use custom names such as **SkypeId** for the extension attributes. Your organization must track the extension attribute properties in use to avoid inadvertently overwriting their data.

## Directory \(Microsoft Entra ID\) extensions

[Directory extensions](https://learn.microsoft.com/en-us/graph/api/resources/extensionProperty) provide developers with a strongly typed, discoverable, and filterable extension experience for directory objects.

Register directory extensions on an application through the [Create extensionProperty](https://learn.microsoft.com/en-us/graph/api/application-post-extensionproperty) operation. You must explicitly target specific and supported directory objects. After a user or an admin consents to the application in the tenant, the extension properties become immediately accessible in the tenant. All authorized applications in the tenant can read and write data on any extension properties defined on an instance of the target directory object.

For the list of resource types that you can specify as target objects for a directory extension, see [Comparison of extension types](#comparison-of-extension-types).

### Developer experience

You manage directory extension definitions through the [extensionProperty](https://learn.microsoft.com/en-us/graph/api/resources/extensionproperty) resource and its associated methods. The REST API requests you use to manage the resource instance handle the data.

#### Define the directory extension

Before you can add a directory extension to a resource instance, you must first define the directory extension.

##### Request

In the following request, `30a5435a-1871-485c-8c7b-65f69e287e7b` is the object ID of the application that owns the directory extension. You can create directory extensions that store a collection of values.

- [HTTP](#tabpanel_3_http)
- [C#](#tabpanel_3_csharp)
- [Go](#tabpanel_3_go)
- [Java](#tabpanel_3_java)
- [JavaScript](#tabpanel_3_javascript)
- [PHP](#tabpanel_3_php)
- [PowerShell](#tabpanel_3_powershell)
- [Python](#tabpanel_3_python)

```http
POST https://graph.microsoft.com/v1.0/applications/30a5435a-1871-485c-8c7b-65f69e287e7b/extensionProperties

{
    "name": "jobGroupTracker",
    "dataType": "String",
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
	Name = "jobGroupTracker",
	DataType = "String",
	TargetObjects = new List<string>
	{
		"User",
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Applications["{application-id}"].ExtensionProperties.PostAsync(requestBody);
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

requestBody := graphmodels.NewExtensionProperty()
name := "jobGroupTracker"
requestBody.SetName(&name) 
dataType := "String"
requestBody.SetDataType(&dataType) 
targetObjects := []string {
	"User",
}
requestBody.SetTargetObjects(targetObjects)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
extensionProperties, err := graphClient.Applications().ByApplicationId("application-id").ExtensionProperties().Post(context.Background(), requestBody, nil)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

ExtensionProperty extensionProperty = new ExtensionProperty();
extensionProperty.setName("jobGroupTracker");
extensionProperty.setDataType("String");
LinkedList<String> targetObjects = new LinkedList<String>();
targetObjects.add("User");
extensionProperty.setTargetObjects(targetObjects);
ExtensionProperty result = graphClient.applications().byApplicationId("{application-id}").extensionProperties().post(extensionProperty);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const extensionProperty = {
    name: 'jobGroupTracker',
    dataType: 'String',
    targetObjects: [
        'User'
    ]
};

await client.api('/applications/30a5435a-1871-485c-8c7b-65f69e287e7b/extensionProperties')
	.post(extensionProperty);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\ExtensionProperty;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new ExtensionProperty();
$requestBody->setName('jobGroupTracker');
$requestBody->setDataType('String');
$requestBody->setTargetObjects(['User', 	]);

$result = $graphServiceClient->applications()->byApplicationId('application-id')->extensionProperties()->post($requestBody)->wait();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```powershell

Import-Module Microsoft.Graph.Applications

$params = @{
	name = "jobGroupTracker"
	dataType = "String"
	targetObjects = @(
	"User"
)
}

New-MgApplicationExtensionProperty -ApplicationId $applicationId -BodyParameter $params
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.extension_property import ExtensionProperty
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = ExtensionProperty(
	name = "jobGroupTracker",
	data_type = "String",
	target_objects = [
		"User",
	],
)

result = await graph_client.applications.by_application_id('application-id').extension_properties.post(request_body)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

##### Response

You create a directory extension property named `extension_b7d8e648520f41d3b9c0fdeb91768a0a_jobGroupTracker` with an extension name that follows this naming convention: *extension\_{appId-without-hyphens}\_{extensionProperty-name}*.

```http
HTTP/1.1 201 Created
Content-type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#applications('30a5435a-1871-485c-8c7b-65f69e287e7b')/extensionProperties/$entity",
    "id": "4e3dbc8f-ca32-41b4-825a-346215d7d20f",
    "deletedDateTime": null,
    "appDisplayName": "HR-sync-app",
    "dataType": "String",
    "isMultiValued": false,
    "isSyncedFromOnPremises": false,
    "name": "extension_b7d8e648520f41d3b9c0fdeb91768a0a_jobGroupTracker",
    "targetObjects": [
        "User"
    ]
}
```

#### Add a directory extension property to a target object

After you define the directory extension, add it to an instance of a target object type. You can store data in the directory extension when you create a new instance of the target object or when you update an existing object. The following example shows how to store data in the directory extension when creating a new **user** object.

- [HTTP](#tabpanel_4_http)
- [C#](#tabpanel_4_csharp)
- [Go](#tabpanel_4_go)
- [Java](#tabpanel_4_java)
- [JavaScript](#tabpanel_4_javascript)
- [PHP](#tabpanel_4_php)
- [PowerShell](#tabpanel_4_powershell)
- [Python](#tabpanel_4_python)

```msgraph
POST https://graph.microsoft.com/v1.0/users

{
    "accountEnabled": true,
    "displayName": "Adele Vance",
    "mailNickname": "AdeleV",
    "userPrincipalName": "AdeleV@contoso.com",
    "passwordProfile": {
        "forceChangePasswordNextSignIn": false,
        "password": "xWwvJ]6NMw+bWH-d"
    },
    "extension_b7d8e648520f41d3b9c0fdeb91768a0a_jobGroupTracker": "JobGroupN"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new User
{
	AccountEnabled = true,
	DisplayName = "Adele Vance",
	MailNickname = "AdeleV",
	UserPrincipalName = "AdeleV@contoso.com",
	PasswordProfile = new PasswordProfile
	{
		ForceChangePasswordNextSignIn = false,
		Password = "xWwvJ]6NMw+bWH-d",
	},
	AdditionalData = new Dictionary<string, object>
	{
		{
			"extension_b7d8e648520f41d3b9c0fdeb91768a0a_jobGroupTracker" , "JobGroupN"
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Users.PostAsync(requestBody);
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
accountEnabled := true
requestBody.SetAccountEnabled(&accountEnabled) 
displayName := "Adele Vance"
requestBody.SetDisplayName(&displayName) 
mailNickname := "AdeleV"
requestBody.SetMailNickname(&mailNickname) 
userPrincipalName := "AdeleV@contoso.com"
requestBody.SetUserPrincipalName(&userPrincipalName) 
passwordProfile := graphmodels.NewPasswordProfile()
forceChangePasswordNextSignIn := false
passwordProfile.SetForceChangePasswordNextSignIn(&forceChangePasswordNextSignIn) 
password := "xWwvJ]6NMw+bWH-d"
passwordProfile.SetPassword(&password) 
requestBody.SetPasswordProfile(passwordProfile)
additionalData := map[string]interface{}{
	"extension_b7d8e648520f41d3b9c0fdeb91768a0a_jobGroupTracker" : "JobGroupN", 
}
requestBody.SetAdditionalData(additionalData)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
users, err := graphClient.Users().Post(context.Background(), requestBody, nil)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

User user = new User();
user.setAccountEnabled(true);
user.setDisplayName("Adele Vance");
user.setMailNickname("AdeleV");
user.setUserPrincipalName("AdeleV@contoso.com");
PasswordProfile passwordProfile = new PasswordProfile();
passwordProfile.setForceChangePasswordNextSignIn(false);
passwordProfile.setPassword("xWwvJ]6NMw+bWH-d");
user.setPasswordProfile(passwordProfile);
HashMap<String, Object> additionalData = new HashMap<String, Object>();
additionalData.put("extension_b7d8e648520f41d3b9c0fdeb91768a0a_jobGroupTracker", "JobGroupN");
user.setAdditionalData(additionalData);
User result = graphClient.users().post(user);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const user = {
    accountEnabled: true,
    displayName: 'Adele Vance',
    mailNickname: 'AdeleV',
    userPrincipalName: 'AdeleV@contoso.com',
    passwordProfile: {
        forceChangePasswordNextSignIn: false,
        password: 'xWwvJ]6NMw+bWH-d'
    },
    extension_b7d8e648520f41d3b9c0fdeb91768a0a_jobGroupTracker: 'JobGroupN'
};

await client.api('/users')
	.post(user);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\User;
use Microsoft\Graph\Generated\Models\PasswordProfile;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new User();
$requestBody->setAccountEnabled(true);
$requestBody->setDisplayName('Adele Vance');
$requestBody->setMailNickname('AdeleV');
$requestBody->setUserPrincipalName('AdeleV@contoso.com');
$passwordProfile = new PasswordProfile();
$passwordProfile->setForceChangePasswordNextSignIn(false);
$passwordProfile->setPassword('xWwvJ]6NMw+bWH-d');
$requestBody->setPasswordProfile($passwordProfile);
$additionalData = [
	'extension_b7d8e648520f41d3b9c0fdeb91768a0a_jobGroupTracker' => 'JobGroupN',
];
$requestBody->setAdditionalData($additionalData);

$result = $graphServiceClient->users()->post($requestBody)->wait();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```powershell

Import-Module Microsoft.Graph.Users

$params = @{
	accountEnabled = $true
	displayName = "Adele Vance"
	mailNickname = "AdeleV"
	userPrincipalName = "AdeleV@contoso.com"
	passwordProfile = @{
		forceChangePasswordNextSignIn = $false
		password = "xWwvJ]6NMw+bWH-d"
	}
	extension_b7d8e648520f41d3b9c0fdeb91768a0a_jobGroupTracker = "JobGroupN"
}

New-MgUser -BodyParameter $params
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.user import User
from msgraph.generated.models.password_profile import PasswordProfile
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = User(
	account_enabled = True,
	display_name = "Adele Vance",
	mail_nickname = "AdeleV",
	user_principal_name = "AdeleV@contoso.com",
	password_profile = PasswordProfile(
		force_change_password_next_sign_in = False,
		password = "xWwvJ]6NMw+bWH-d",
	),
	additional_data = {
			"extension_b7d8e648520f41d3b9c0fdeb91768a0a_job_group_tracker" : "JobGroupN",
	}
)

result = await graph_client.users.post(request_body)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

The request returns a `201 Created` response code and a [user](https://learn.microsoft.com/en-us/graph/api/resources/user) object in the response body.

#### Retrieve a directory extension

The following example shows how the directory extensions and associated data are presented on a resource instance. The extension property is returned by default through the `beta` endpoint, but only on `$select` through the `v1.0` endpoint.

#### Request

- [HTTP](#tabpanel_5_http)
- [C#](#tabpanel_5_csharp)
- [Go](#tabpanel_5_go)
- [Java](#tabpanel_5_java)
- [JavaScript](#tabpanel_5_javascript)
- [PHP](#tabpanel_5_php)
- [PowerShell](#tabpanel_5_powershell)
- [Python](#tabpanel_5_python)

```msgraph
GET https://graph.microsoft.com/beta/users?$select=id,displayName,extension_b7d8e648520f41d3b9c0fdeb91768a0a_jobGroupTracker,extension_b7d8e648520f41d3b9c0fdeb91768a0a_permanent_pensionable
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Users.GetAsync((requestConfiguration) =>
{
	requestConfiguration.QueryParameters.Select = new string []{ "id","displayName","extension_b7d8e648520f41d3b9c0fdeb91768a0a_jobGroupTracker","extension_b7d8e648520f41d3b9c0fdeb91768a0a_permanent_pensionable" };
});
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```go


// Code snippets are only available for the latest major version. Current major version is $v0.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-beta-sdk-go"
	  graphusers "github.com/microsoftgraph/msgraph-beta-sdk-go/users"
	  //other-imports
)

requestParameters := &graphusers.UsersRequestBuilderGetQueryParameters{
	Select: [] string {"id","displayName","extension_b7d8e648520f41d3b9c0fdeb91768a0a_jobGroupTracker","extension_b7d8e648520f41d3b9c0fdeb91768a0a_permanent_pensionable"},
}
configuration := &graphusers.UsersRequestBuilderGetRequestConfiguration{
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
	requestConfiguration.queryParameters.select = new String []{"id", "displayName", "extension_b7d8e648520f41d3b9c0fdeb91768a0a_jobGroupTracker", "extension_b7d8e648520f41d3b9c0fdeb91768a0a_permanent_pensionable"};
});
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let users = await client.api('/users')
	.version('beta')
	.select('id,displayName,extension_b7d8e648520f41d3b9c0fdeb91768a0a_jobGroupTracker,extension_b7d8e648520f41d3b9c0fdeb91768a0a_permanent_pensionable')
	.get();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Users\UsersRequestBuilderGetRequestConfiguration;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestConfiguration = new UsersRequestBuilderGetRequestConfiguration();
$queryParameters = UsersRequestBuilderGetRequestConfiguration::createQueryParameters();
$queryParameters->select = ["id","displayName","extension_b7d8e648520f41d3b9c0fdeb91768a0a_jobGroupTracker","extension_b7d8e648520f41d3b9c0fdeb91768a0a_permanent_pensionable"];
$requestConfiguration->queryParameters = $queryParameters;


$result = $graphServiceClient->users()->get($requestConfiguration)->wait();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```powershell

Import-Module Microsoft.Graph.Beta.Users

Get-MgBetaUser -Property "id,displayName,extension_b7d8e648520f41d3b9c0fdeb91768a0a_jobGroupTracker,extension_b7d8e648520f41d3b9c0fdeb91768a0a_permanent_pensionable" 
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.users.users_request_builder import UsersRequestBuilder
from kiota_abstractions.base_request_configuration import RequestConfiguration
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
query_params = UsersRequestBuilder.UsersRequestBuilderGetQueryParameters(
		select = ["id","displayName","extension_b7d8e648520f41d3b9c0fdeb91768a0a_jobGroupTracker","extension_b7d8e648520f41d3b9c0fdeb91768a0a_permanent_pensionable"],
)

request_configuration = RequestConfiguration(
query_parameters = query_params,
)

result = await graph_client.users.get(request_configuration = request_configuration)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

#### Response

```http
HTTP/1.1 200 OK
Content-type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#users(id,displayName,extension_b7d8e648520f41d3b9c0fdeb91768a0a_jobGroupTracker,extension_b7d8e648520f41d3b9c0fdeb91768a0a_permanent_pensionable)",
    "value": [
        {
            "id": "63384f56-42d2-4aa7-b1d6-b10c78f143a2",
            "displayName": "Adele Vance",
            "extension_b7d8e648520f41d3b9c0fdeb91768a0a_jobGroupTracker": "E4",
            "extension_b7d8e648520f41d3b9c0fdeb91768a0a_permanent_pensionable": true
        }
    ]
}
```

#### Update or delete directory extensions

To update or delete the value of the directory extension for a resource instance, use the PATCH method. To delete the extension property and its associated value, set its value to `null`.

The following request updates the value of one directory extension and deletes another extension property.

- [HTTP](#tabpanel_6_http)
- [C#](#tabpanel_6_csharp)
- [Go](#tabpanel_6_go)
- [Java](#tabpanel_6_java)
- [JavaScript](#tabpanel_6_javascript)
- [PHP](#tabpanel_6_php)
- [PowerShell](#tabpanel_6_powershell)
- [Python](#tabpanel_6_python)

```http
PATCH https://graph.microsoft.com/v1.0/users/63384f56-42d2-4aa7-b1d6-b10c78f143a2

{
    "extension_b7d8e648520f41d3b9c0fdeb91768a0a_permanent_pensionable": null,
    "extension_b7d8e648520f41d3b9c0fdeb91768a0a_jobGroupTracker": "E4"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new User
{
	AdditionalData = new Dictionary<string, object>
	{
		{
			"extension_b7d8e648520f41d3b9c0fdeb91768a0a_permanent_pensionable" , null
		},
		{
			"extension_b7d8e648520f41d3b9c0fdeb91768a0a_jobGroupTracker" , "E4"
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
additionalData := map[string]interface{}{
	extension_b7d8e648520f41d3b9c0fdeb91768a0a_permanent_pensionable := null
requestBody.SetExtension_b7d8e648520f41d3b9c0fdeb91768a0a_permanent_pensionable(&extension_b7d8e648520f41d3b9c0fdeb91768a0a_permanent_pensionable) 
	"extension_b7d8e648520f41d3b9c0fdeb91768a0a_jobGroupTracker" : "E4", 
}
requestBody.SetAdditionalData(additionalData)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
users, err := graphClient.Users().ByUserId("user-id").Patch(context.Background(), requestBody, nil)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

User user = new User();
HashMap<String, Object> additionalData = new HashMap<String, Object>();
additionalData.put("extension_b7d8e648520f41d3b9c0fdeb91768a0a_permanent_pensionable", null);
additionalData.put("extension_b7d8e648520f41d3b9c0fdeb91768a0a_jobGroupTracker", "E4");
user.setAdditionalData(additionalData);
User result = graphClient.users().byUserId("{user-id}").patch(user);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const user = {
    extension_b7d8e648520f41d3b9c0fdeb91768a0a_permanent_pensionable: null,
    extension_b7d8e648520f41d3b9c0fdeb91768a0a_jobGroupTracker: 'E4'
};

await client.api('/users/63384f56-42d2-4aa7-b1d6-b10c78f143a2')
	.update(user);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\User;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new User();
$additionalData = [
	'extension_b7d8e648520f41d3b9c0fdeb91768a0a_permanent_pensionable' => null,
	'extension_b7d8e648520f41d3b9c0fdeb91768a0a_jobGroupTracker' => 'E4',
];
$requestBody->setAdditionalData($additionalData);

$result = $graphServiceClient->users()->byUserId('user-id')->patch($requestBody)->wait();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```powershell

Import-Module Microsoft.Graph.Users

$params = @{
	extension_b7d8e648520f41d3b9c0fdeb91768a0a_permanent_pensionable = $null
	extension_b7d8e648520f41d3b9c0fdeb91768a0a_jobGroupTracker = "E4"
}

Update-MgUser -UserId $userId -BodyParameter $params
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.user import User
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = User(
	additional_data = {
			"extension_b7d8e648520f41d3b9c0fdeb91768a0a_permanent_pensionable" : None,
			"extension_b7d8e648520f41d3b9c0fdeb91768a0a_job_group_tracker" : "E4",
	}
)

result = await graph_client.users.by_user_id('user-id').patch(request_body)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

The request returns a `204 No Content` response code.

### Considerations for using directory extensions

If you accidentally delete a directory extension definition, any data stored in the associated property becomes undiscoverable. To recover the data, create a new directory extension definition with the same name as the deleted definition, on the same owner app.

When you delete a definition object before updating the corresponding extension property to `null`, the property counts against the 100-limit for the object.

When you delete the definition before deleting data in the associated extension property, there's no way to know the existence of the extension property via Microsoft Graph - even though the undiscoverable property counts against the 100-limit.

Deleting an owner app in the home tenant makes the associated directory extensions and their data undiscoverable. When you restore an owner app, it restores the directory extension definitions *but doesn't* make the directory extension properties or their data immediately discoverable; because restoring an app doesn't automatically restore the associated service principal in the tenant. To make the directory extension properties and their data discoverable, either create a new service principal or restore the deleted service principal. No changes are made to other tenants where the app has been consented to.

## Schema extensions

[Microsoft Graph schema extensions](https://learn.microsoft.com/en-us/graph/api/resources/schemaextension) are conceptually similar to directory extensions. First, you define your schema extension. Then, use it to extend supported resource instances with strongly typed custom properties. In addition, you can control the [status](https://learn.microsoft.com/en-us/graph/api/resources/schemaextension#schema-extensions-lifecycle) of your schema extension and let it be discoverable by other apps.

For the list of resource types that support schema extensions, see [Comparison of extension types](#comparison-of-extension-types).

<iframe src="https://www.youtube-nocookie.com/embed/3MOAlUFNus0" allowfullscreen="true" data-linktype="external" frameborder="0"></iframe>

### Developer experience

When you create a schema extension definition, you must provide a unique name for its **id**. You have two naming options:

- If you already have a vanity `.com`, `.net`, `.gov`, `.edu`, or `.org` domain that's verified with your tenant, use the domain name along with the schema name to define a unique name, in this format *{domainName}*\_*{schemaName}*. For example, if your vanity domain is `contoso.com`, you can define an **id** of `contoso_mySchema`. This option is highly recommended.
- Alternatively, set the **id** to a schema name \(without a domain name prefix\). For example, `mySchema`. Microsoft Graph assigns a string ID for you based on the supplied name, in this format: `ext{8-random-alphanumeric-chars}_{schema-name}`. For example, `extkvbmkofy_mySchema`.

The **id** is the name of the complex type that stores your data on the extended resource instance.

After you register a schema extension, all applications in the same tenant as the associated owner application can use it when it's in the `InDevelopment` state. When it's in the `Available` state, all applications in any tenant can use it. Like directory extensions, authorized apps can read and write data on any extensions defined on the target object.

You manage the [schema extension definitions](https://learn.microsoft.com/en-us/graph/api/resources/schemaextension) and the data in the corresponding schema extension property by using separate sets of API operations. To manage the schema extension data on the extended resource instance, use the same REST request that you use to manage the resource instance.

- Use POST to store data in the schema extension property when you're creating a new user.
- Use PATCH to store data in the schema extension property or update or delete the stored data.

  - To delete data from a property, set its value to `null`.
  - To delete data from *all* properties, set every property to `null`. If all properties are `null`, the schema extension object is also deleted.
  - To update any property, specify only the changed properties in the request body. Omitted properties aren't updated and retain their previous value.

- Use GET to read the schema extension properties for all users or individual users in the tenant.

#### Define a schema extension

##### Request

- [HTTP](#tabpanel_7_http)
- [C#](#tabpanel_7_csharp)
- [Go](#tabpanel_7_go)
- [Java](#tabpanel_7_java)
- [JavaScript](#tabpanel_7_javascript)
- [PHP](#tabpanel_7_php)
- [PowerShell](#tabpanel_7_powershell)
- [Python](#tabpanel_7_python)

```msgraph
POST https://graph.microsoft.com/v1.0/schemaExtensions

{
    "id": "graphLearnCourses",
    "description": "Graph Learn training courses extensions",
    "targetTypes": [
        "user"
    ],
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
	Id = "graphLearnCourses",
	Description = "Graph Learn training courses extensions",
	TargetTypes = new List<string>
	{
		"user",
	},
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
id := "graphLearnCourses"
requestBody.SetId(&id) 
description := "Graph Learn training courses extensions"
requestBody.SetDescription(&description) 
targetTypes := []string {
	"user",
}
requestBody.SetTargetTypes(targetTypes)


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
schemaExtension.setId("graphLearnCourses");
schemaExtension.setDescription("Graph Learn training courses extensions");
LinkedList<String> targetTypes = new LinkedList<String>();
targetTypes.add("user");
schemaExtension.setTargetTypes(targetTypes);
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
    id: 'graphLearnCourses',
    description: 'Graph Learn training courses extensions',
    targetTypes: [
        'user'
    ],
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
$requestBody->setId('graphLearnCourses');
$requestBody->setDescription('Graph Learn training courses extensions');
$requestBody->setTargetTypes(['user', 	]);
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
	id = "graphLearnCourses"
	description = "Graph Learn training courses extensions"
	targetTypes = @(
	"user"
)
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
	id = "graphLearnCourses",
	description = "Graph Learn training courses extensions",
	target_types = [
		"user",
	],
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

##### Response

```http
{
    "@odata.context": "https://graph.microsoft.com/beta/$metadata#schemaExtensions/$entity",
    "id": "extkmpdyld2_graphLearnCourses",
    "description": "Graph Learn training courses extensions",
    "targetTypes": [
        "user"
    ],
    "status": "InDevelopment",
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

#### Add a schema extension to a resource instance

After defining the schema extension, you can add the extension property to an instance of a target object type. You can store data in the schema extension when creating a new instance of the target object or when updating an existing object. The following example shows how to store data in the schema extension property when creating a new user object.

- [HTTP](#tabpanel_8_http)
- [C#](#tabpanel_8_csharp)
- [Go](#tabpanel_8_go)
- [Java](#tabpanel_8_java)
- [JavaScript](#tabpanel_8_javascript)
- [PHP](#tabpanel_8_php)
- [PowerShell](#tabpanel_8_powershell)
- [Python](#tabpanel_8_python)

```http
POST https://graph.microsoft.com/beta/users

{
    "accountEnabled": true,
    "displayName": "Adele Vance",
    "mailNickname": "AdeleV",
    "userPrincipalName": "AdeleV@contoso.com",
    "passwordProfile": {
        "forceChangePasswordNextSignIn": false,
        "password": "xWwvJ]6NMw+bWH-d"
    },
    "extkmpdyld2_graphLearnCourses": {
        "courseId": 100,
        "courseName": "Explore Microsoft Graph",
        "courseType": "Online"
    }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.Models;
using Microsoft.Kiota.Abstractions.Serialization;

var requestBody = new User
{
	AccountEnabled = true,
	DisplayName = "Adele Vance",
	MailNickname = "AdeleV",
	UserPrincipalName = "AdeleV@contoso.com",
	PasswordProfile = new PasswordProfile
	{
		ForceChangePasswordNextSignIn = false,
		Password = "xWwvJ]6NMw+bWH-d",
	},
	AdditionalData = new Dictionary<string, object>
	{
		{
			"extkmpdyld2_graphLearnCourses" , new UntypedObject(new Dictionary<string, UntypedNode>
			{
				{
					"courseId", new UntypedString("100")
				},
				{
					"courseName", new UntypedString("Explore Microsoft Graph")
				},
				{
					"courseType", new UntypedString("Online")
				},
			})
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Users.PostAsync(requestBody);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```go


// Code snippets are only available for the latest major version. Current major version is $v0.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-beta-sdk-go"
	  graphmodels "github.com/microsoftgraph/msgraph-beta-sdk-go/models"
	  //other-imports
)

requestBody := graphmodels.NewUser()
accountEnabled := true
requestBody.SetAccountEnabled(&accountEnabled) 
displayName := "Adele Vance"
requestBody.SetDisplayName(&displayName) 
mailNickname := "AdeleV"
requestBody.SetMailNickname(&mailNickname) 
userPrincipalName := "AdeleV@contoso.com"
requestBody.SetUserPrincipalName(&userPrincipalName) 
passwordProfile := graphmodels.NewPasswordProfile()
forceChangePasswordNextSignIn := false
passwordProfile.SetForceChangePasswordNextSignIn(&forceChangePasswordNextSignIn) 
password := "xWwvJ]6NMw+bWH-d"
passwordProfile.SetPassword(&password) 
requestBody.SetPasswordProfile(passwordProfile)
additionalData := map[string]interface{}{
extkmpdyld2_graphLearnCourses := graph.New()
courseId := int32(100)
extkmpdyld2_graphLearnCourses.SetCourseId(&courseId) 
courseName := "Explore Microsoft Graph"
extkmpdyld2_graphLearnCourses.SetCourseName(&courseName) 
courseType := "Online"
extkmpdyld2_graphLearnCourses.SetCourseType(&courseType) 
	requestBody.SetExtkmpdyld2_graphLearnCourses(extkmpdyld2_graphLearnCourses)
}
requestBody.SetAdditionalData(additionalData)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
users, err := graphClient.Users().Post(context.Background(), requestBody, nil)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

User user = new User();
user.setAccountEnabled(true);
user.setDisplayName("Adele Vance");
user.setMailNickname("AdeleV");
user.setUserPrincipalName("AdeleV@contoso.com");
PasswordProfile passwordProfile = new PasswordProfile();
passwordProfile.setForceChangePasswordNextSignIn(false);
passwordProfile.setPassword("xWwvJ]6NMw+bWH-d");
user.setPasswordProfile(passwordProfile);
HashMap<String, Object> additionalData = new HashMap<String, Object>();
 extkmpdyld2GraphLearnCourses = new ();
extkmpdyld2GraphLearnCourses.setCourseId(100);
extkmpdyld2GraphLearnCourses.setCourseName("Explore Microsoft Graph");
extkmpdyld2GraphLearnCourses.setCourseType("Online");
additionalData.put("extkmpdyld2_graphLearnCourses", extkmpdyld2GraphLearnCourses);
user.setAdditionalData(additionalData);
User result = graphClient.users().post(user);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const user = {
    accountEnabled: true,
    displayName: 'Adele Vance',
    mailNickname: 'AdeleV',
    userPrincipalName: 'AdeleV@contoso.com',
    passwordProfile: {
        forceChangePasswordNextSignIn: false,
        password: 'xWwvJ]6NMw+bWH-d'
    },
    extkmpdyld2_graphLearnCourses: {
        courseId: 100,
        courseName: 'Explore Microsoft Graph',
        courseType: 'Online'
    }
};

await client.api('/users')
	.version('beta')
	.post(user);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Models\User;
use Microsoft\Graph\Beta\Generated\Models\PasswordProfile;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new User();
$requestBody->setAccountEnabled(true);
$requestBody->setDisplayName('Adele Vance');
$requestBody->setMailNickname('AdeleV');
$requestBody->setUserPrincipalName('AdeleV@contoso.com');
$passwordProfile = new PasswordProfile();
$passwordProfile->setForceChangePasswordNextSignIn(false);
$passwordProfile->setPassword('xWwvJ]6NMw+bWH-d');
$requestBody->setPasswordProfile($passwordProfile);
$additionalData = [
	'extkmpdyld2_graphLearnCourses' => [
		'courseId' => 100,
		'courseName' => 'Explore Microsoft Graph',
		'courseType' => 'Online',
	],
];
$requestBody->setAdditionalData($additionalData);

$result = $graphServiceClient->users()->post($requestBody)->wait();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```powershell

Import-Module Microsoft.Graph.Beta.Users

$params = @{
	accountEnabled = $true
	displayName = "Adele Vance"
	mailNickname = "AdeleV"
	userPrincipalName = "AdeleV@contoso.com"
	passwordProfile = @{
		forceChangePasswordNextSignIn = $false
		password = "xWwvJ]6NMw+bWH-d"
	}
	extkmpdyld2_graphLearnCourses = @{
		courseId = 
		courseName = "Explore Microsoft Graph"
		courseType = "Online"
	}
}

New-MgBetaUser -BodyParameter $params
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.models.user import User
from msgraph_beta.generated.models.password_profile import PasswordProfile
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = User(
	account_enabled = True,
	display_name = "Adele Vance",
	mail_nickname = "AdeleV",
	user_principal_name = "AdeleV@contoso.com",
	password_profile = PasswordProfile(
		force_change_password_next_sign_in = False,
		password = "xWwvJ]6NMw+bWH-d",
	),
	additional_data = {
			"extkmpdyld2_graph_learn_courses" : {
					"course_id" : 100,
					"course_name" : "Explore Microsoft Graph",
					"course_type" : "Online",
			},
	}
)

result = await graph_client.users.post(request_body)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

The request returns a `201 Created` response code and a [schemaExtension](https://learn.microsoft.com/en-us/graph/api/resources/schemaextension) object in the response body.

#### Update or delete a schema extension property

Use the PATCH operation to update a schema extension or delete an existing schema extension. To delete the extension property and its associated value from the resource instance, set its value to `null`.

The following example deletes the value of the **courseId** property and updates the **courseType** property. To delete the `extkmpdyld2_graphLearnCourses` extension property in its entirety, set its value to `null`.

- [HTTP](#tabpanel_9_http)
- [C#](#tabpanel_9_csharp)
- [Go](#tabpanel_9_go)
- [Java](#tabpanel_9_java)
- [JavaScript](#tabpanel_9_javascript)
- [PHP](#tabpanel_9_php)
- [PowerShell](#tabpanel_9_powershell)
- [Python](#tabpanel_9_python)

```http
PATCH https://graph.microsoft.com/beta/users/0668e673-908b-44ea-861d-0661297e1a3e

{
    "extkmpdyld2_graphLearnCourses": {
        "courseType": "Instructor-led",
        "courseId": null
    }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.Models;
using Microsoft.Kiota.Abstractions.Serialization;

var requestBody = new User
{
	AdditionalData = new Dictionary<string, object>
	{
		{
			"extkmpdyld2_graphLearnCourses" , new UntypedObject(new Dictionary<string, UntypedNode>
			{
				{
					"courseType", new UntypedString("Instructor-led")
				},
				{
					"courseId", new UntypedNull()
				},
			})
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Users["{user-id}"].PatchAsync(requestBody);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```go


// Code snippets are only available for the latest major version. Current major version is $v0.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-beta-sdk-go"
	  graphmodels "github.com/microsoftgraph/msgraph-beta-sdk-go/models"
	  //other-imports
)

requestBody := graphmodels.NewUser()
additionalData := map[string]interface{}{
extkmpdyld2_graphLearnCourses := graph.New()
courseType := "Instructor-led"
extkmpdyld2_graphLearnCourses.SetCourseType(&courseType) 
	courseId := null
extkmpdyld2_graphLearnCourses.SetCourseId(&courseId) 
	requestBody.SetExtkmpdyld2_graphLearnCourses(extkmpdyld2_graphLearnCourses)
}
requestBody.SetAdditionalData(additionalData)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
users, err := graphClient.Users().ByUserId("user-id").Patch(context.Background(), requestBody, nil)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

User user = new User();
HashMap<String, Object> additionalData = new HashMap<String, Object>();
 extkmpdyld2GraphLearnCourses = new ();
extkmpdyld2GraphLearnCourses.setCourseType("Instructor-led");
extkmpdyld2GraphLearnCourses.setCourseId(null);
additionalData.put("extkmpdyld2_graphLearnCourses", extkmpdyld2GraphLearnCourses);
user.setAdditionalData(additionalData);
User result = graphClient.users().byUserId("{user-id}").patch(user);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const user = {
    extkmpdyld2_graphLearnCourses: {
        courseType: 'Instructor-led',
        courseId: null
    }
};

await client.api('/users/0668e673-908b-44ea-861d-0661297e1a3e')
	.version('beta')
	.update(user);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Models\User;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new User();
$additionalData = [
	'extkmpdyld2_graphLearnCourses' => [
		'courseType' => 'Instructor-led',
		'courseId' => null,
	],
];
$requestBody->setAdditionalData($additionalData);

$result = $graphServiceClient->users()->byUserId('user-id')->patch($requestBody)->wait();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```powershell

Import-Module Microsoft.Graph.Beta.Users

$params = @{
	extkmpdyld2_graphLearnCourses = @{
		courseType = "Instructor-led"
		courseId = $null
	}
}

Update-MgBetaUser -UserId $userId -BodyParameter $params
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.models.user import User
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = User(
	additional_data = {
			"extkmpdyld2_graph_learn_courses" : {
					"course_type" : "Instructor-led",
					"course_id" : None,
			},
	}
)

result = await graph_client.users.by_user_id('user-id').patch(request_body)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

The request returns a `204 No Content` response object.

#### Retrieve the schema extension property

To read the schema extension properties on a resource instance, specify the extension name in a `$select` request.

##### Request

- [HTTP](#tabpanel_10_http)
- [C#](#tabpanel_10_csharp)
- [Go](#tabpanel_10_go)
- [Java](#tabpanel_10_java)
- [JavaScript](#tabpanel_10_javascript)
- [PHP](#tabpanel_10_php)
- [PowerShell](#tabpanel_10_powershell)
- [Python](#tabpanel_10_python)

```msgraph
GET https://graph.microsoft.com/beta/users/0668e673-908b-44ea-861d-0661297e1a3e?$select=id,displayName,extkmpdyld2_graphLearnCourses
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Users["{user-id}"].GetAsync((requestConfiguration) =>
{
	requestConfiguration.QueryParameters.Select = new string []{ "id","displayName","extkmpdyld2_graphLearnCourses" };
});
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```go


// Code snippets are only available for the latest major version. Current major version is $v0.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-beta-sdk-go"
	  graphusers "github.com/microsoftgraph/msgraph-beta-sdk-go/users"
	  //other-imports
)

requestParameters := &graphusers.UserItemRequestBuilderGetQueryParameters{
	Select: [] string {"id","displayName","extkmpdyld2_graphLearnCourses"},
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
	requestConfiguration.queryParameters.select = new String []{"id", "displayName", "extkmpdyld2_graphLearnCourses"};
});
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let user = await client.api('/users/0668e673-908b-44ea-861d-0661297e1a3e')
	.version('beta')
	.select('id,displayName,extkmpdyld2_graphLearnCourses')
	.get();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Users\Item\UserItemRequestBuilderGetRequestConfiguration;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestConfiguration = new UserItemRequestBuilderGetRequestConfiguration();
$queryParameters = UserItemRequestBuilderGetRequestConfiguration::createQueryParameters();
$queryParameters->select = ["id","displayName","extkmpdyld2_graphLearnCourses"];
$requestConfiguration->queryParameters = $queryParameters;


$result = $graphServiceClient->users()->byUserId('user-id')->get($requestConfiguration)->wait();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```powershell

Import-Module Microsoft.Graph.Beta.Users

Get-MgBetaUser -UserId $userId -Property "id,displayName,extkmpdyld2_graphLearnCourses" 
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.users.item.user_item_request_builder import UserItemRequestBuilder
from kiota_abstractions.base_request_configuration import RequestConfiguration
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
query_params = UserItemRequestBuilder.UserItemRequestBuilderGetQueryParameters(
		select = ["id","displayName","extkmpdyld2_graphLearnCourses"],
)

request_configuration = RequestConfiguration(
query_parameters = query_params,
)

result = await graph_client.users.by_user_id('user-id').get(request_configuration = request_configuration)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

##### Response

```http
HTTP/1.1 200 OK
Content-type: application/json

{
    "@odata.context": "https://graph.microsoft.com/beta/$metadata#users(id,displayName,extkmpdyld2_graphLearnCourses)/$entity",
    "id": "63384f56-42d2-4aa7-b1d6-b10c78f143a2",
    "displayName": "Adele Vance",
    "extkmpdyld2_graphLearnCourses": {
        "@odata.type": "#microsoft.graph.ComplexExtensionValue",
        "courseType": "Instructor-led",
        "courseName": "Explore Microsoft Graph",
        "courseId": null
    }
}
```

### Considerations for using schema extensions

A schema extension must have an owner app. You can't reassign ownership of the schema extension to another app.

If you delete a schema extension definition without setting the schema extension to `null`, you make the property and its associated user data undiscoverable.

If you delete an owner app in the home tenant, you don't delete the associated schema extension definition or the property and the data it stores. You can still read, delete, or update the schema extension property for users. However, you can't update the schema extension definition.

## Open extensions

[Microsoft Graph open extensions](https://learn.microsoft.com/en-us/graph/api/resources/opentypeextension) are [open types](https://www.odata.org/getting-started/advanced-tutorial/#openType) that offer a simple and flexible way to add untyped data directly to a resource instance. These extensions aren't strongly typed, discoverable, or filterable.

For the list of resource types that support Microsoft Graph open extensions, see [Comparison of extension types](#comparison-of-extension-types).

<iframe src="https://www.youtube-nocookie.com/embed/ibdlADb8IZc" allowfullscreen="true" data-linktype="external" frameborder="0"></iframe>

### Developer experience

You can access open extensions and their data through the **extensions** navigation property of the resource instance. With open extensions, you can group related properties for easier access and management.

You define and manage open extensions on resource instances. Each open extension is unique to its object, so you don't need to apply a consistent pattern across all objects. For example, in the same tenant:

- The user object for Adele can have an open extension named *socialSettings* that has three properties: **linkedInProfile**, **skypeId**, and **xboxGamertag**.
- The user object for Allan can have no open extension property.
- The user object for Alex can have an open extension named *socialSettings* with five properties: **theme**, **color**, **language**, **font**, and **fontSize**.

Open extension properties can have any valid JSON structure.

#### Create an open extension

The following example shows an open extension definition with three properties and how the custom properties and associated data appear on a resource instance.

- [HTTP](#tabpanel_11_http)
- [C#](#tabpanel_11_csharp)
- [Go](#tabpanel_11_go)
- [Java](#tabpanel_11_java)
- [JavaScript](#tabpanel_11_javascript)
- [PHP](#tabpanel_11_php)
- [PowerShell](#tabpanel_11_powershell)
- [Python](#tabpanel_11_python)

```http
POST https://graph.microsoft.com/v1.0/users/3fbd929d-8c56-4462-851e-0eb9a7b3a2a5/extensions

{
    "@odata.type": "#microsoft.graph.openTypeExtension",
    "extensionName": "com.contoso.socialSettings",
    "skypeId": "skypeId.AdeleV",
    "linkedInProfile": "www.linkedin.com/in/testlinkedinprofile",
    "xboxGamerTag": "AwesomeAdele",
    "id": "com.contoso.socialSettings"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new OpenTypeExtension
{
	OdataType = "#microsoft.graph.openTypeExtension",
	ExtensionName = "com.contoso.socialSettings",
	Id = "com.contoso.socialSettings",
	AdditionalData = new Dictionary<string, object>
	{
		{
			"skypeId" , "skypeId.AdeleV"
		},
		{
			"linkedInProfile" , "www.linkedin.com/in/testlinkedinprofile"
		},
		{
			"xboxGamerTag" , "AwesomeAdele"
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Users["{user-id}"].Extensions.PostAsync(requestBody);
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

requestBody := graphmodels.NewExtension()
extensionName := "com.contoso.socialSettings"
requestBody.SetExtensionName(&extensionName) 
id := "com.contoso.socialSettings"
requestBody.SetId(&id) 
additionalData := map[string]interface{}{
	"skypeId" : "skypeId.AdeleV", 
	"linkedInProfile" : "www.linkedin.com/in/testlinkedinprofile", 
	"xboxGamerTag" : "AwesomeAdele", 
}
requestBody.SetAdditionalData(additionalData)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
extensions, err := graphClient.Users().ByUserId("user-id").Extensions().Post(context.Background(), requestBody, nil)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

OpenTypeExtension extension = new OpenTypeExtension();
extension.setOdataType("#microsoft.graph.openTypeExtension");
extension.setExtensionName("com.contoso.socialSettings");
extension.setId("com.contoso.socialSettings");
HashMap<String, Object> additionalData = new HashMap<String, Object>();
additionalData.put("skypeId", "skypeId.AdeleV");
additionalData.put("linkedInProfile", "www.linkedin.com/in/testlinkedinprofile");
additionalData.put("xboxGamerTag", "AwesomeAdele");
extension.setAdditionalData(additionalData);
Extension result = graphClient.users().byUserId("{user-id}").extensions().post(extension);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const extension = {
    '@odata.type': '#microsoft.graph.openTypeExtension',
    extensionName: 'com.contoso.socialSettings',
    skypeId: 'skypeId.AdeleV',
    linkedInProfile: 'www.linkedin.com/in/testlinkedinprofile',
    xboxGamerTag: 'AwesomeAdele',
    id: 'com.contoso.socialSettings'
};

await client.api('/users/3fbd929d-8c56-4462-851e-0eb9a7b3a2a5/extensions')
	.post(extension);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\OpenTypeExtension;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new OpenTypeExtension();
$requestBody->setOdataType('#microsoft.graph.openTypeExtension');
$requestBody->setExtensionName('com.contoso.socialSettings');
$requestBody->setId('com.contoso.socialSettings');
$additionalData = [
	'skypeId' => 'skypeId.AdeleV',
	'linkedInProfile' => 'www.linkedin.com/in/testlinkedinprofile',
	'xboxGamerTag' => 'AwesomeAdele',
];
$requestBody->setAdditionalData($additionalData);

$result = $graphServiceClient->users()->byUserId('user-id')->extensions()->post($requestBody)->wait();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```powershell

Import-Module Microsoft.Graph.Users

$params = @{
	"@odata.type" = "#microsoft.graph.openTypeExtension"
	extensionName = "com.contoso.socialSettings"
	skypeId = "skypeId.AdeleV"
	linkedInProfile = "www.linkedin.com/in/testlinkedinprofile"
	xboxGamerTag = "AwesomeAdele"
	id = "com.contoso.socialSettings"
}

New-MgUserExtension -UserId $userId -BodyParameter $params
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.open_type_extension import OpenTypeExtension
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = OpenTypeExtension(
	odata_type = "#microsoft.graph.openTypeExtension",
	extension_name = "com.contoso.socialSettings",
	id = "com.contoso.socialSettings",
	additional_data = {
			"skype_id" : "skypeId.AdeleV",
			"linked_in_profile" : "www.linkedin.com/in/testlinkedinprofile",
			"xbox_gamer_tag" : "AwesomeAdele",
	}
)

result = await graph_client.users.by_user_id('user-id').extensions.post(request_body)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

The request returns a `201 Created` response code and an [openTypeExtension](https://learn.microsoft.com/en-us/graph/api/resources/opentypeextension) object in the response body.

#### Update an existing open extension

To update an open extension, you must specify all its properties in the request body. Otherwise, the unspecified properties are deleted from the open extension. You can explicitly set a property to `null` to retain it in the open extension.

The following request specifies only the **linkedInProfile** and **xboxGamerTag** properties. The value of the **xboxGamerTag** property is updated while the **linkedInProfile** property stays the same. This request also deletes the unspecified **skypeId** property.

- [HTTP](#tabpanel_12_http)
- [C#](#tabpanel_12_csharp)
- [Go](#tabpanel_12_go)
- [Java](#tabpanel_12_java)
- [JavaScript](#tabpanel_12_javascript)
- [PHP](#tabpanel_12_php)
- [PowerShell](#tabpanel_12_powershell)
- [Python](#tabpanel_12_python)

```http
PATCH https://graph.microsoft.com/v1.0/users/3fbd929d-8c56-4462-851e-0eb9a7b3a2a5/extensions/com.contoso.socialSettings

{
    "xboxGamerTag": "FierceAdele",
    "linkedInProfile": "www.linkedin.com/in/testlinkedinprofile"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new Extension
{
	AdditionalData = new Dictionary<string, object>
	{
		{
			"xboxGamerTag" , "FierceAdele"
		},
		{
			"linkedInProfile" , "www.linkedin.com/in/testlinkedinprofile"
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Users["{user-id}"].Extensions["{extension-id}"].PatchAsync(requestBody);
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

requestBody := graphmodels.NewExtension()
additionalData := map[string]interface{}{
	"xboxGamerTag" : "FierceAdele", 
	"linkedInProfile" : "www.linkedin.com/in/testlinkedinprofile", 
}
requestBody.SetAdditionalData(additionalData)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
extensions, err := graphClient.Users().ByUserId("user-id").Extensions().ByExtensionId("extension-id").Patch(context.Background(), requestBody, nil)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

Extension extension = new Extension();
HashMap<String, Object> additionalData = new HashMap<String, Object>();
additionalData.put("xboxGamerTag", "FierceAdele");
additionalData.put("linkedInProfile", "www.linkedin.com/in/testlinkedinprofile");
extension.setAdditionalData(additionalData);
Extension result = graphClient.users().byUserId("{user-id}").extensions().byExtensionId("{extension-id}").patch(extension);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const extension = {
    xboxGamerTag: 'FierceAdele',
    linkedInProfile: 'www.linkedin.com/in/testlinkedinprofile'
};

await client.api('/users/3fbd929d-8c56-4462-851e-0eb9a7b3a2a5/extensions/com.contoso.socialSettings')
	.update(extension);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\Extension;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new Extension();
$additionalData = [
	'xboxGamerTag' => 'FierceAdele',
	'linkedInProfile' => 'www.linkedin.com/in/testlinkedinprofile',
];
$requestBody->setAdditionalData($additionalData);

$result = $graphServiceClient->users()->byUserId('user-id')->extensions()->byExtensionId('extension-id')->patch($requestBody)->wait();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```powershell

Import-Module Microsoft.Graph.Users

$params = @{
	xboxGamerTag = "FierceAdele"
	linkedInProfile = "www.linkedin.com/in/testlinkedinprofile"
}

Update-MgUserExtension -UserId $userId -ExtensionId $extensionId -BodyParameter $params
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.extension import Extension
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = Extension(
	additional_data = {
			"xbox_gamer_tag" : "FierceAdele",
			"linked_in_profile" : "www.linkedin.com/in/testlinkedinprofile",
	}
)

result = await graph_client.users.by_user_id('user-id').extensions.by_extension_id('extension-id').patch(request_body)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

This request returns a `204 No Content` response code.

#### Retrieve the open extensions

- [HTTP](#tabpanel_13_http)
- [C#](#tabpanel_13_csharp)
- [Go](#tabpanel_13_go)
- [Java](#tabpanel_13_java)
- [JavaScript](#tabpanel_13_javascript)
- [PHP](#tabpanel_13_php)
- [PowerShell](#tabpanel_13_powershell)
- [Python](#tabpanel_13_python)

```msgraph
GET https://graph.microsoft.com/v1.0/users/3fbd929d-8c56-4462-851e-0eb9a7b3a2a5/extensions/com.contoso.socialSettings

{
    "@odata.context": "https://graph.microsoft.com/beta/$metadata#users('3fbd929d-8c56-4462-851e-0eb9a7b3a2a5')/extensions/$entity",
    "@odata.type": "#microsoft.graph.openTypeExtension",
    "xboxGamerTag": "FierceAdele",
    "linkedInProfile": "www.linkedin.com/in/testlinkedinprofile",
    "id": "com.contoso.socialSettings"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new OpenTypeExtension
{
	OdataType = "#microsoft.graph.openTypeExtension",
	Id = "com.contoso.socialSettings",
	AdditionalData = new Dictionary<string, object>
	{
		{
			"@odata.context" , "https://graph.microsoft.com/beta/$metadata#users('3fbd929d-8c56-4462-851e-0eb9a7b3a2a5')/extensions/$entity"
		},
		{
			"xboxGamerTag" , "FierceAdele"
		},
		{
			"linkedInProfile" , "www.linkedin.com/in/testlinkedinprofile"
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Users["{user-id}"].Extensions["{extension-id}"].GetAsync(requestBody);
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

requestBody := graphmodels.NewExtension()
id := "com.contoso.socialSettings"
requestBody.SetId(&id) 
additionalData := map[string]interface{}{
	"@odata.context" : "https://graph.microsoft.com/beta/$metadata#users('3fbd929d-8c56-4462-851e-0eb9a7b3a2a5')/extensions/$entity", 
	"xboxGamerTag" : "FierceAdele", 
	"linkedInProfile" : "www.linkedin.com/in/testlinkedinprofile", 
}
requestBody.SetAdditionalData(additionalData)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
extensions, err := graphClient.Users().ByUserId("user-id").Extensions().ByExtensionId("extension-id").Get(context.Background(), requestBody, nil)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

OpenTypeExtension extension = new OpenTypeExtension();
extension.setOdataType("#microsoft.graph.openTypeExtension");
extension.setId("com.contoso.socialSettings");
HashMap<String, Object> additionalData = new HashMap<String, Object>();
additionalData.put("@odata.context", "https://graph.microsoft.com/beta/$metadata#users('3fbd929d-8c56-4462-851e-0eb9a7b3a2a5')/extensions/$entity");
additionalData.put("xboxGamerTag", "FierceAdele");
additionalData.put("linkedInProfile", "www.linkedin.com/in/testlinkedinprofile");
extension.setAdditionalData(additionalData);
Extension result = graphClient.users().byUserId("{user-id}").extensions().byExtensionId("{extension-id}").get(extension);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let extension = await client.api('/users/3fbd929d-8c56-4462-851e-0eb9a7b3a2a5/extensions/com.contoso.socialSettings')
	.get();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\OpenTypeExtension;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new OpenTypeExtension();
$requestBody->setOdataType('#microsoft.graph.openTypeExtension');
$requestBody->setId('com.contoso.socialSettings');
$additionalData = [
	'@odata.context' => 'https://graph.microsoft.com/beta/$metadata#users(\'3fbd929d-8c56-4462-851e-0eb9a7b3a2a5\')/extensions/$entity',
	'xboxGamerTag' => 'FierceAdele',
	'linkedInProfile' => 'www.linkedin.com/in/testlinkedinprofile',
];
$requestBody->setAdditionalData($additionalData);

$result = $graphServiceClient->users()->byUserId('user-id')->extensions()->byExtensionId('extension-id')->get($requestBody)->wait();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```powershell

Import-Module Microsoft.Graph.Users

$params = @{
	"@odata.context" = "https://graph.microsoft.com/beta/$metadata#users('3fbd929d-8c56-4462-851e-0eb9a7b3a2a5')/extensions/$entity"
	"@odata.type" = "#microsoft.graph.openTypeExtension"
	xboxGamerTag = "FierceAdele"
	linkedInProfile = "www.linkedin.com/in/testlinkedinprofile"
	id = "com.contoso.socialSettings"
}

Get-MgUserExtension -UserId $userId -ExtensionId $extensionId -BodyParameter $params
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.open_type_extension import OpenTypeExtension
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = OpenTypeExtension(
	odata_type = "#microsoft.graph.openTypeExtension",
	id = "com.contoso.socialSettings",
	additional_data = {
			"@odata_context" : "https://graph.microsoft.com/beta/$metadata#users('3fbd929d-8c56-4462-851e-0eb9a7b3a2a5')/extensions/$entity",
			"xbox_gamer_tag" : "FierceAdele",
			"linked_in_profile" : "www.linkedin.com/in/testlinkedinprofile",
	}
)

result = await graph_client.users.by_user_id('user-id').extensions.by_extension_id('extension-id').get(request_body)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

### Considerations for using open extensions

Deleting a creator app doesn't affect the open extension or the data it stores.

## Comparison of extension types

The following table compares the extension types. Use this comparison to decide which option is most appropriate for your scenario.

| Capability | Extension attributes 1-15 | Directory extensions | Schema extensions | Open extensions |
| --- | --- | --- | --- | --- |
| Supported resource types | [user](https://learn.microsoft.com/en-us/graph/api/resources/user)  <br>[device](https://learn.microsoft.com/en-us/graph/api/resources/device) | [user](https://learn.microsoft.com/en-us/graph/api/resources/user)  <br>[group](https://learn.microsoft.com/en-us/graph/api/resources/group)  <br>[administrativeUnit](https://learn.microsoft.com/en-us/graph/api/resources/administrativeunit)  <br>[application](https://learn.microsoft.com/en-us/graph/api/resources/application)  <br>[device](https://learn.microsoft.com/en-us/graph/api/resources/device)  <br>[organization](https://learn.microsoft.com/en-us/graph/api/resources/organization) | [user](https://learn.microsoft.com/en-us/graph/api/resources/user)  <br>[group](https://learn.microsoft.com/en-us/graph/api/resources/group)  <br>[administrativeUnit](https://learn.microsoft.com/en-us/graph/api/resources/administrativeunit)  <br>[contact](https://learn.microsoft.com/en-us/graph/api/resources/contact)  <br>[device](https://learn.microsoft.com/en-us/graph/api/resources/device)  <br>[event](https://learn.microsoft.com/en-us/graph/api/resources/event) \(both user and group calendars\)  <br>[message](https://learn.microsoft.com/en-us/graph/api/resources/message)  <br>[organization](https://learn.microsoft.com/en-us/graph/api/resources/organization)  <br>[post](https://learn.microsoft.com/en-us/graph/api/resources/post) | [user](https://learn.microsoft.com/en-us/graph/api/resources/user)  <br>[group](https://learn.microsoft.com/en-us/graph/api/resources/group)  <br>[contact](https://learn.microsoft.com/en-us/graph/api/resources/contact)  <br>[device](https://learn.microsoft.com/en-us/graph/api/resources/device)  <br>[event](https://learn.microsoft.com/en-us/graph/api/resources/event)<sup>1</sup> \(both user and group calendars\)  <br>[message](https://learn.microsoft.com/en-us/graph/api/resources/message)  <br>[organization](https://learn.microsoft.com/en-us/graph/api/resources/organization)  <br>[post](https://learn.microsoft.com/en-us/graph/api/resources/post)  <br>[todoTask](https://learn.microsoft.com/en-us/graph/api/resources/todotask)  <br>[todoTaskList](https://learn.microsoft.com/en-us/graph/api/resources/todotasklist) |
| Strongly typed | No | Yes | Yes | No |
| Filterable | Yes | Yes | Yes | No |
| Can store a collection | No | Yes | No | Yes |
| Tied to an "owner" application | No | Yes | Yes | No |
| Scoping | Assign values to pre-defined properties of the target object instance | Define at application-level then assign to target object instance | Define for the tenant then assign to target object instance | Define and assign on the object instance |
| Discoverability | Select or filter on the target object instance | LIST, select, or filter on the application level to GET definitions; Select or filter on the target object to GET assignments | LIST or filter to GET tenant-wide definitions; Select or filter on the target object to GET assignments | LIST or select on the target object to GET definitions and assignments |
| Managed via | Microsoft Graph  <br>Exchange admin center | Microsoft Graph | Microsoft Graph | Microsoft Graph |
| Sync data from on-premises to extensions using [AD connect](https://learn.microsoft.com/en-us/entra/identity/hybrid/whatis-hybrid-identity?context=%2Fazure%2Factive-directory%2Fenterprise-users%2Fcontext%2Fugr-context) | Yes, for users | [Yes](https://learn.microsoft.com/en-us/entra/identity/hybrid/connect/how-to-connect-sync-feature-directory-extensions) | No | No |
| Create [dynamic membership rules](https://learn.microsoft.com/en-us/entra/identity/users/groups-dynamic-membership) using custom extension properties and data | [Yes](https://learn.microsoft.com/en-us/entra/identity/users/groups-dynamic-membership#extension-properties-and-custom-extension-properties) | [Yes](https://learn.microsoft.com/en-us/entra/identity/users/groups-dynamic-membership#extension-properties-and-custom-extension-properties) | No | No |
| Usable for customizing token claims | Yes | Yes \([1](https://learn.microsoft.com/en-us/entra/identity-platform/schema-extensions), [2](https://learn.microsoft.com/en-us/entra/identity-platform/optional-claims#configure-directory-extension-optional-claims)\) | No | No |
| Available in Azure AD B2C | Yes | [Yes](https://learn.microsoft.com/en-us/azure/active-directory-b2c/user-profile-attributes#extension-attributes) | Yes | Yes |
| Available in Microsoft Entra External ID | Yes | Yes | Yes | Yes |
| Limits | <li>15 predefined attributes per user or device resource instance</li> | <li>100 extension values per resource instance</li> | <li>Maximum of five definitions per owner app <br></li><br><br><li> 100 extension values per resource instance (directory objects only)</li> | <li>Two open extensions per creator app per resource instance<sup>2</sup> <br></li><br><br><li> Max. of 2 Kb per open extension<sup>2</sup></li><br><br><li> For Outlook resources, each open extension is stored in a <a href="https://learn.microsoft.com/en-us/office/client-developer/outlook/mapi/mapi-named-properties" data-linktype="absolute-path">MAPI named property</a><sup>3</sup></li> |

Note

<sup>1</sup> Due to an existing service limitation, delegates can't create open extension-appended events in shared mailbox calendars. Attempts to do so result in an `ErrorAccessDenied` response.

<sup>2</sup> These limits on open extensions apply to the following directory resources: **user**, **group**, **device**,  and **organization**.

<sup>3</sup> Each [open extension](https://learn.microsoft.com/en-us/graph/api/resources/opentypeextension) is stored in a [MAPI named property](https://learn.microsoft.com/en-us/office/client-developer/outlook/mapi/mapi-named-properties), which are a limited resource in a user's mailbox. This limit applies to the following Outlook resources: **message**, **event**, and **contact**

You can manage all extensions when you sign in with a work or school account. Additionally, you can manage open extensions for the following resources when signed-in with a personal Microsoft account: **event**, **post**, **group**, **message**, **contact**, and **user**.

## Permissions and privileges

To manage any extensions data on a resource instance, your app needs the same privileges it uses to read from or write to that resource instance. For example, in a delegated scenario, an app can update any user's extension data only if it's granted the *User.ReadWrite.All* permission and the signed-in user has a supported Microsoft Entra administrator role.

## Related content

- [Tutorial: Add custom data to users using open extensions](https://learn.microsoft.com/en-us/graph/extensibility-open-users)
- [Tutorial: Add custom data to groups using schema extensions](https://learn.microsoft.com/en-us/graph/extensibility-schema-groups)
