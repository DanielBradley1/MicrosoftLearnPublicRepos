<!-- Source: https://learn.microsoft.com/en-us/graph/api/admintodo-update?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-04-05 -->

# Update adminTodo

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Update the properties of a [adminTodo](https://learn.microsoft.com/en-us/graph/api/resources/admintodo?view=graph-rest-beta) object.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

One of the following permissions is required to call this API. To learn more, including how to choose permissions, see [Permissions](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Permissions \(from least to most privileged\) |
| :--- | :--- |
| Delegated \(work or school account\) | OrgSettings-Todo.ReadWrite.All |
| Delegated \(personal Microsoft account\) | **Not supported.** |
| Application | **OrgSettings-Todo.ReadWrite.All** |

## HTTP request

```http
PATCH /admin/todo
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply *only* the values for properties to update. Existing properties that aren't included in the request body maintain their previous values or are recalculated based on changes to other property values.

The following table specifies the properties that can be updated.

| Property | Type | Description |
| :--- | :--- | :--- |
| settings | [todoSettings](https://learn.microsoft.com/en-us/graph/api/resources/todosettings?view=graph-rest-beta) | Company-wide settings for Microsoft Todo. Required. |

## Response

If successful, this method returns a `200 OK` response code and an updated [adminTodo](https://learn.microsoft.com/en-us/graph/api/resources/admintodo?view=graph-rest-beta) object in the response body.

## Examples

### Request

The following example shows a request.

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [Python](#tabpanel_1_python)

```http
PATCH https://graph.microsoft.com/beta/admin/todo
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.adminTodo",
  "settings": {
    "@odata.type": "microsoft.graph.todoSettings",
    "isPushNotificationEnabled": true,
    "isExternalJoinEnabled": false,
    "isExternalShareEnabled": true
  }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.Models;

var requestBody = new AdminTodo
{
	OdataType = "#microsoft.graph.adminTodo",
	Settings = new TodoSettings
	{
		OdataType = "microsoft.graph.todoSettings",
		IsPushNotificationEnabled = true,
		IsExternalJoinEnabled = false,
		IsExternalShareEnabled = true,
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Admin.Todo.PatchAsync(requestBody);
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

requestBody := graphmodels.NewAdminTodo()
settings := graphmodels.NewTodoSettings()
isPushNotificationEnabled := true
settings.SetIsPushNotificationEnabled(&isPushNotificationEnabled) 
isExternalJoinEnabled := false
settings.SetIsExternalJoinEnabled(&isExternalJoinEnabled) 
isExternalShareEnabled := true
settings.SetIsExternalShareEnabled(&isExternalShareEnabled) 
requestBody.SetSettings(settings)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
todo, err := graphClient.Admin().Todo().Patch(context.Background(), requestBody, nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

AdminTodo adminTodo = new AdminTodo();
adminTodo.setOdataType("#microsoft.graph.adminTodo");
TodoSettings settings = new TodoSettings();
settings.setOdataType("microsoft.graph.todoSettings");
settings.setIsPushNotificationEnabled(true);
settings.setIsExternalJoinEnabled(false);
settings.setIsExternalShareEnabled(true);
adminTodo.setSettings(settings);
AdminTodo result = graphClient.admin().todo().patch(adminTodo);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const adminTodo = {
  '@odata.type': '#microsoft.graph.adminTodo',
  settings: {
    '@odata.type': 'microsoft.graph.todoSettings',
    isPushNotificationEnabled: true,
    isExternalJoinEnabled: false,
    isExternalShareEnabled: true
  }
};

await client.api('/admin/todo')
	.version('beta')
	.update(adminTodo);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Models\AdminTodo;
use Microsoft\Graph\Beta\Generated\Models\TodoSettings;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new AdminTodo();
$requestBody->setOdataType('#microsoft.graph.adminTodo');
$settings = new TodoSettings();
$settings->setOdataType('microsoft.graph.todoSettings');
$settings->setIsPushNotificationEnabled(true);
$settings->setIsExternalJoinEnabled(false);
$settings->setIsExternalShareEnabled(true);
$requestBody->setSettings($settings);

$result = $graphServiceClient->admin()->todo()->patch($requestBody)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.models.admin_todo import AdminTodo
from msgraph_beta.generated.models.todo_settings import TodoSettings
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = AdminTodo(
	odata_type = "#microsoft.graph.adminTodo",
	settings = TodoSettings(
		odata_type = "microsoft.graph.todoSettings",
		is_push_notification_enabled = True,
		is_external_join_enabled = False,
		is_external_share_enabled = True,
	),
)

result = await graph_client.admin.todo.patch(request_body)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 204 No Content
Content-Type: text/plain
```
