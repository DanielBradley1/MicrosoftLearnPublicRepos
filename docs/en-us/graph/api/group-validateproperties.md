<!-- Source: https://learn.microsoft.com/en-us/graph/api/group-validateproperties?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-08-08 -->

# group: validateProperties

Namespace: microsoft.graph

Validate that a Microsoft 365 [group's](https://learn.microsoft.com/en-us/graph/api/resources/group?view=graph-rest-1.0) display name or mail nickname complies with naming policies. Clients can use this API to determine whether a display name or mail nickname is valid before trying to [update](https://learn.microsoft.com/en-us/graph/api/group-update?view=graph-rest-1.0) a Microsoft 365 group. To validate the properties before creating a group, use the [directoryobject:validateProperties](https://learn.microsoft.com/en-us/graph/api/directoryobject-validateproperties?view=graph-rest-1.0) function.

The following policy validations are performed for the display name and mail nickname properties:

1. Validate the prefix and suffix naming policy
2. Validate the custom banned words policy

This API only returns the first validation failure that is encountered. If the properties fail multiple validations, only the first validation failure is returned. However, you can validate both the mail nickname and the display name and receive a collection of validation errors if you are only validating the prefix and suffix naming policy. To learn more about configuring naming policies, see [Configure naming policy](https://learn.microsoft.com/en-us/azure/active-directory/users-groups-roles/groups-naming-policy#configure-naming-policy-in-powershell).

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Group.Read.All | Group.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Group.Read.All | Group.ReadWrite.All |

## HTTP request

```http
POST /groups/{id}/validateProperties
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
| displayName | String | The display name of the group to validate. The property is not individually required. However, at least one property \(**displayName** or **mailNickname**\) is required. |
| mailNickname | String | The mail nickname of the group to validate. The property is not individually required. However, at least one property \(**displayName** or **mailNickname**\) is required. |
| onBehalfOfUserId | Guid | The ID of the user to impersonate when calling the API. The validation results are for the **onBehalfOfUserId's** attributes and roles. |

## Response

If successful and there are no validation errors, the method returns `204 No Content` response code. It doesn't return anything in the response body.

If the request is invalid, the method returns `400 Bad Request` response code. An error message with details about the invalid request is returned in the response body.

If there is a validation error. The method returns `422 Unprocessable Entity` response code. An error message and a collection of error details is returned in the response body.

## Examples

### Example 1: Successful validation request

This is an example of a successful validation request.

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
POST https://graph.microsoft.com/v1.0/groups/{id}/validateProperties
Content-type: application/json

{
  "displayName": "Myprefix_test_mysuffix",
  "mailNickname": "Myprefix_test_mysuffix",
  "onBehalfOfUserId": "onBehalfOfUserId-value"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Groups.Item.ValidateProperties;

var requestBody = new ValidatePropertiesPostRequestBody
{
	DisplayName = "Myprefix_test_mysuffix",
	MailNickname = "Myprefix_test_mysuffix",
	OnBehalfOfUserId = Guid.Parse("onBehalfOfUserId-value"),
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
await graphClient.Groups["{group-id}"].ValidateProperties.PostAsync(requestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  "github.com/google/uuid"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphgroups "github.com/microsoftgraph/msgraph-sdk-go/groups"
	  //other-imports
)

requestBody := graphgroups.NewValidatePropertiesPostRequestBody()
displayName := "Myprefix_test_mysuffix"
requestBody.SetDisplayName(&displayName) 
mailNickname := "Myprefix_test_mysuffix"
requestBody.SetMailNickname(&mailNickname) 
onBehalfOfUserId := uuid.MustParse("onBehalfOfUserId-value")
requestBody.SetOnBehalfOfUserId(&onBehalfOfUserId) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
graphClient.Groups().ByGroupId("group-id").ValidateProperties().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.groups.item.validateproperties.ValidatePropertiesPostRequestBody validatePropertiesPostRequestBody = new com.microsoft.graph.groups.item.validateproperties.ValidatePropertiesPostRequestBody();
validatePropertiesPostRequestBody.setDisplayName("Myprefix_test_mysuffix");
validatePropertiesPostRequestBody.setMailNickname("Myprefix_test_mysuffix");
validatePropertiesPostRequestBody.setOnBehalfOfUserId(UUID.fromString("onBehalfOfUserId-value"));
graphClient.groups().byGroupId("{group-id}").validateProperties().post(validatePropertiesPostRequestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const validateProperties = {
  displayName: 'Myprefix_test_mysuffix',
  mailNickname: 'Myprefix_test_mysuffix',
  onBehalfOfUserId: 'onBehalfOfUserId-value'
};

await client.api('/groups/{id}/validateProperties')
	.post(validateProperties);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Groups\Item\ValidateProperties\ValidatePropertiesPostRequestBody;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new ValidatePropertiesPostRequestBody();
$requestBody->setDisplayName('Myprefix_test_mysuffix');
$requestBody->setMailNickname('Myprefix_test_mysuffix');
$requestBody->setOnBehalfOfUserId('onBehalfOfUserId-value');

$graphServiceClient->groups()->byGroupId('group-id')->validateProperties()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Groups

$params = @{
	displayName = "Myprefix_test_mysuffix"
	mailNickname = "Myprefix_test_mysuffix"
	onBehalfOfUserId = "onBehalfOfUserId-value"
}

Test-MgGroupProperty -GroupId $groupId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.groups.item.validate_properties.validate_properties_post_request_body import ValidatePropertiesPostRequestBody
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = ValidatePropertiesPostRequestBody(
	display_name = "Myprefix_test_mysuffix",
	mail_nickname = "Myprefix_test_mysuffix",
	on_behalf_of_user_id = UUID("onBehalfOfUserId-value"),
)

await graph_client.groups.by_group_id('group-id').validate_properties.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

```http
HTTP/1.1 204 No Content
```

### Example 2: Request with validation errors

This is an example of a request with validation errors.

#### Request

```http
POST https://graph.microsoft.com/v1.0/groups/{id}/validateProperties
Content-type: application/json

{
  "displayName": "MyPrefix_test_mysuffix",
  "mailNickname": "MyPrefix_test_mysuffix"
}
```

#### Response

```http
HTTP/1.1 422
Content-type: application/json

{
  "error": {
    "code": "Request_UnprocessableEntity",
    "message": "The values provided contain one or more validation errors.",
    "innerError": {
      "request-id": "id-value",
      "date": "date-value"
    },
    "details": [
      {
        "target": "mailNickname",
        "code": "PropertyConflict",
        "message": "Another object with the same value for property mailNickname already exists."
      }
    ]
  }
}
```
