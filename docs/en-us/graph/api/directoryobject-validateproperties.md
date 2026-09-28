<!-- Source: https://learn.microsoft.com/en-us/graph/api/directoryobject-validateproperties?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-23 -->

# directoryObject: validateProperties

Namespace: microsoft.graph

Validate that a Microsoft 365 group's display name or mail nickname complies with naming policies. Clients can use this API to determine whether a display name or mail nickname is valid before trying to [create](https://learn.microsoft.com/en-us/graph/api/group-post-groups?view=graph-rest-1.0) a Microsoft 365 group. To validate the properties of an existing group, use the [group: validateProperties](https://learn.microsoft.com/en-us/graph/api/group-validateproperties?view=graph-rest-1.0) function.

The following policy validations are performed for the display name and mail nickname properties:

1. Validate the prefix and suffix naming policy
2. Validate the custom banned words policy
3. Validate that the mail nickname is unique

Note

- The following characters are considered invalid characters and aren't part of the policy validations: `@ () \ \[] " ; : <> , SPACE`.
- Admins with the User Administrator and Global Administrator roles are exempted from the custom banned words and prefix and suffix naming policies, allowing them to create groups by using blocked words and with their own naming conventions.

This API only returns the first validation failure that is encountered. If the properties fail multiple validations, only the first validation failure is returned. However, you can validate both the mail nickname and the display name and receive a collection of validation errors if you're only validating the prefix and suffix naming policy. To learn more about configuring naming policies, see [Configure naming policy](https://learn.microsoft.com/en-us/azure/active-directory/users-groups-roles/groups-naming-policy#configure-naming-policy-in-powershell).

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Group.Read.All | Directory.Read.All, Directory.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Group.Read.All | Directory.Read.All, Directory.ReadWrite.All, Group.ReadWrite.All |

## HTTP request

```http
POST /directoryObjects/validateProperties
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json |

## Request body

In the request body, provide a JSON object with the following parameters.

| Parameter | Type | Description |
| :--- | :--- | :--- |
| entityType | String | Group is the only supported entity type. |
| displayName | String | The display name of the group to validate. Either **displayName** or **mailNickname** must be specified. |
| mailNickname | String | The mail nickname of the group to validate. Either **displayName** or **mailNickname** must be specified. |
| onBehalfOfUserId | Guid | The ID of the user to impersonate when calling the API. The validation results are for the **onBehalfOfUserId's** attributes and roles. |

## Response

If successful and there are no validation errors, the method returns `204 No Content` response code. It doesn't return anything in the response body.

When a Global Administrator or User Administrator initiates a request that violates custom banned words or prefix and suffix naming policies, the API returns a `204 No Content` response code, as these administrators are exempt from naming policies. For other users or administrators, requests violating these policies are invalid.

If the request is invalid, the method returns `400 Bad Request` response code. An error message with details about the invalid request is returned in the response body.

If there's a validation error, the method returns `422 Unprocessable Entity` response code. An error message and a collection of error details is returned in the response body.

## Examples

### Example 1: A successful validation request

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
POST https://graph.microsoft.com/v1.0/directoryObjects/validateProperties
Content-type: application/json

{
  "entityType": "Group",
  "displayName": "Myprefix_test_mysuffix",
  "mailNickname": "Myprefix_test_mysuffix",
  "onBehalfOfUserId": "onBehalfOfUserId-value"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.DirectoryObjects.ValidateProperties;

var requestBody = new ValidatePropertiesPostRequestBody
{
	EntityType = "Group",
	DisplayName = "Myprefix_test_mysuffix",
	MailNickname = "Myprefix_test_mysuffix",
	OnBehalfOfUserId = Guid.Parse("onBehalfOfUserId-value"),
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
await graphClient.DirectoryObjects.ValidateProperties.PostAsync(requestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  "github.com/google/uuid"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphdirectoryobjects "github.com/microsoftgraph/msgraph-sdk-go/directoryobjects"
	  //other-imports
)

requestBody := graphdirectoryobjects.NewValidatePropertiesPostRequestBody()
entityType := "Group"
requestBody.SetEntityType(&entityType) 
displayName := "Myprefix_test_mysuffix"
requestBody.SetDisplayName(&displayName) 
mailNickname := "Myprefix_test_mysuffix"
requestBody.SetMailNickname(&mailNickname) 
onBehalfOfUserId := uuid.MustParse("onBehalfOfUserId-value")
requestBody.SetOnBehalfOfUserId(&onBehalfOfUserId) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
graphClient.DirectoryObjects().ValidateProperties().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.directoryobjects.validateproperties.ValidatePropertiesPostRequestBody validatePropertiesPostRequestBody = new com.microsoft.graph.directoryobjects.validateproperties.ValidatePropertiesPostRequestBody();
validatePropertiesPostRequestBody.setEntityType("Group");
validatePropertiesPostRequestBody.setDisplayName("Myprefix_test_mysuffix");
validatePropertiesPostRequestBody.setMailNickname("Myprefix_test_mysuffix");
validatePropertiesPostRequestBody.setOnBehalfOfUserId(UUID.fromString("onBehalfOfUserId-value"));
graphClient.directoryObjects().validateProperties().post(validatePropertiesPostRequestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const validateProperties = {
  entityType: 'Group',
  displayName: 'Myprefix_test_mysuffix',
  mailNickname: 'Myprefix_test_mysuffix',
  onBehalfOfUserId: 'onBehalfOfUserId-value'
};

await client.api('/directoryObjects/validateProperties')
	.post(validateProperties);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\DirectoryObjects\ValidateProperties\ValidatePropertiesPostRequestBody;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new ValidatePropertiesPostRequestBody();
$requestBody->setEntityType('Group');
$requestBody->setDisplayName('Myprefix_test_mysuffix');
$requestBody->setMailNickname('Myprefix_test_mysuffix');
$requestBody->setOnBehalfOfUserId('onBehalfOfUserId-value');

$graphServiceClient->directoryObjects()->validateProperties()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.DirectoryObjects

$params = @{
	entityType = "Group"
	displayName = "Myprefix_test_mysuffix"
	mailNickname = "Myprefix_test_mysuffix"
	onBehalfOfUserId = "onBehalfOfUserId-value"
}

Test-MgDirectoryObjectProperty -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.directoryobjects.validate_properties.validate_properties_post_request_body import ValidatePropertiesPostRequestBody
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = ValidatePropertiesPostRequestBody(
	entity_type = "Group",
	display_name = "Myprefix_test_mysuffix",
	mail_nickname = "Myprefix_test_mysuffix",
	on_behalf_of_user_id = UUID("onBehalfOfUserId-value"),
)

await graph_client.directory_objects.validate_properties.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

```http
HTTP/1.1 204 No Content
```

### Example 2: An unsuccessful validation request

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
POST https://graph.microsoft.com/v1.0/directoryObjects/validateProperties
Content-type: application/json

{
  "entityType": "Group",
  "displayName": "test",
  "mailNickname": "test",
  "onBehalfOfUserId": "onBehalfOfUserId-value"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.DirectoryObjects.ValidateProperties;

var requestBody = new ValidatePropertiesPostRequestBody
{
	EntityType = "Group",
	DisplayName = "test",
	MailNickname = "test",
	OnBehalfOfUserId = Guid.Parse("onBehalfOfUserId-value"),
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
await graphClient.DirectoryObjects.ValidateProperties.PostAsync(requestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  "github.com/google/uuid"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphdirectoryobjects "github.com/microsoftgraph/msgraph-sdk-go/directoryobjects"
	  //other-imports
)

requestBody := graphdirectoryobjects.NewValidatePropertiesPostRequestBody()
entityType := "Group"
requestBody.SetEntityType(&entityType) 
displayName := "test"
requestBody.SetDisplayName(&displayName) 
mailNickname := "test"
requestBody.SetMailNickname(&mailNickname) 
onBehalfOfUserId := uuid.MustParse("onBehalfOfUserId-value")
requestBody.SetOnBehalfOfUserId(&onBehalfOfUserId) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
graphClient.DirectoryObjects().ValidateProperties().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.directoryobjects.validateproperties.ValidatePropertiesPostRequestBody validatePropertiesPostRequestBody = new com.microsoft.graph.directoryobjects.validateproperties.ValidatePropertiesPostRequestBody();
validatePropertiesPostRequestBody.setEntityType("Group");
validatePropertiesPostRequestBody.setDisplayName("test");
validatePropertiesPostRequestBody.setMailNickname("test");
validatePropertiesPostRequestBody.setOnBehalfOfUserId(UUID.fromString("onBehalfOfUserId-value"));
graphClient.directoryObjects().validateProperties().post(validatePropertiesPostRequestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const validateProperties = {
  entityType: 'Group',
  displayName: 'test',
  mailNickname: 'test',
  onBehalfOfUserId: 'onBehalfOfUserId-value'
};

await client.api('/directoryObjects/validateProperties')
	.post(validateProperties);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\DirectoryObjects\ValidateProperties\ValidatePropertiesPostRequestBody;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new ValidatePropertiesPostRequestBody();
$requestBody->setEntityType('Group');
$requestBody->setDisplayName('test');
$requestBody->setMailNickname('test');
$requestBody->setOnBehalfOfUserId('onBehalfOfUserId-value');

$graphServiceClient->directoryObjects()->validateProperties()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.DirectoryObjects

$params = @{
	entityType = "Group"
	displayName = "test"
	mailNickname = "test"
	onBehalfOfUserId = "onBehalfOfUserId-value"
}

Test-MgDirectoryObjectProperty -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.directoryobjects.validate_properties.validate_properties_post_request_body import ValidatePropertiesPostRequestBody
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = ValidatePropertiesPostRequestBody(
	entity_type = "Group",
	display_name = "test",
	mail_nickname = "test",
	on_behalf_of_user_id = UUID("onBehalfOfUserId-value"),
)

await graph_client.directory_objects.validate_properties.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

```http
HTTP/1.1 422 Unprocessable Entity
Content-Type: application/json

{
  "error": {
    "code": "Request_UnprocessableEntity",
    "message": "The values provided contain one or more validation errors.",
    "innerError": {
      "request-id": "request-id-value",
      "date": "date-value"
    },
    "details": [
      {
        "target": "displayName",
        "code": "MissingPrefixSuffix",
        "message": "Property mailNickname is missing a required prefix/suffix per your organization's Group naming requirements.",
        "prefix": "Myprefix_",
        "suffix": "_mysuffix"
      },
      {
        "target": "mailNickname",
        "code": "MissingPrefixSuffix",
        "message": "Property mailNickname is missing a required prefix/suffix per your organization's Group naming requirements.",
        "prefix": "Myprefix_",
        "suffix": "_mysuffix"
      }
    ]
  }
}
```
