<!-- Source: https://learn.microsoft.com/en-us/graph/api/directory-deleteditems-restore?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-03-14 -->

# Restore deleted item \(directory object\)

Namespace: microsoft.graph

Restore a recently deleted directory object from [deleted items](https://learn.microsoft.com/en-us/graph/api/resources/directory?view=graph-rest-1.0). The following types are supported:

- [administrativeUnit](https://learn.microsoft.com/en-us/graph/api/resources/administrativeunit?view=graph-rest-1.0)
- [application](https://learn.microsoft.com/en-us/graph/api/resources/application?view=graph-rest-1.0)
- [agentIdentityBlueprint](https://learn.microsoft.com/en-us/graph/api/resources/agentidentityblueprint?view=graph-rest-1.0)
- [agentIdentity](https://learn.microsoft.com/en-us/graph/api/resources/agentidentity?view=graph-rest-1.0)
- [agentIdentityBlueprintPrincipal](https://learn.microsoft.com/en-us/graph/api/resources/agentidentityblueprintprincipal?view=graph-rest-1.0)
- [agentUser](https://learn.microsoft.com/en-us/graph/api/resources/agentuser?view=graph-rest-1.0)
- [certificateBasedAuthPki](https://learn.microsoft.com/en-us/graph/api/resources/certificatebasedauthpki?view=graph-rest-1.0)
- [certificateAuthorityDetail](https://learn.microsoft.com/en-us/graph/api/resources/certificateauthoritydetail?view=graph-rest-1.0)
- [group](https://learn.microsoft.com/en-us/graph/api/resources/group?view=graph-rest-1.0)
- [servicePrincipal](https://learn.microsoft.com/en-us/graph/api/resources/serviceprincipal?view=graph-rest-1.0)
- [user](https://learn.microsoft.com/en-us/graph/api/resources/user?view=graph-rest-1.0)

If an item is accidentally deleted, you can fully restore the item. Additionally, restoring an application doesn't automatically restore the associated service principal automatically. You must call this API to explicitly restore the deleted service principal.

A recently deleted item remains available for up to 30 days. After 30 days, the item is permanently deleted.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

The following table shows the least privileged permission or permissions required to call this API on each supported resource type. Follow [best practices](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions) to request least privileged permissions. For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Supported resource | Delegated \(work or school account\) | Delegated \(personal Microsoft account\) | Application |
| :--- | :--- | :--- | :--- |
| [administrativeUnit](https://learn.microsoft.com/en-us/graph/api/resources/administrativeunit?view=graph-rest-1.0) | AdministrativeUnit.ReadWrite.All | Not supported. | AdministrativeUnit.ReadWrite.All |
| [application](https://learn.microsoft.com/en-us/graph/api/resources/application?view=graph-rest-1.0) | Application.ReadWrite.All | Not supported. | Application.ReadWrite.OwnedBy |
| [agentIdentity](https://learn.microsoft.com/en-us/graph/api/resources/agentidentity?view=graph-rest-1.0) | AgentIdentity.DeleteRestore.All | Not supported. | AgentIdentity.DeleteRestore.All |
| [agentIdentityBlueprint](https://learn.microsoft.com/en-us/graph/api/resources/agentidentityblueprint?view=graph-rest-1.0) | AgentIdentityBlueprint.DeleteRestore.All | Not supported. | AgentIdentityBlueprint.DeleteRestore.All |
| [agentIdentityBlueprintPrincipal](https://learn.microsoft.com/en-us/graph/api/resources/agentidentityblueprintprincipal?view=graph-rest-1.0) | AgentIdentityBlueprintPrincipal.DeleteRestore.All | Not supported. | AgentIdentityBlueprintPrincipal.DeleteRestore.All |
| [agentUser](https://learn.microsoft.com/en-us/graph/api/resources/agentuser?view=graph-rest-1.0) | AgentIdUser.ReadWrite.IdentityParentedBy | Not supported. | AgentIdUser.ReadWrite.IdentityParentedBy |
| [certificateBasedAuthPki](https://learn.microsoft.com/en-us/graph/api/resources/certificatebasedauthpki?view=graph-rest-1.0) | PublicKeyInfrastructure.Read.All | Not supported. | PublicKeyInfrastructure.Read.All |
| [certificateAuthorityDetail](https://learn.microsoft.com/en-us/graph/api/resources/certificateauthoritydetail?view=graph-rest-1.0) | PublicKeyInfrastructure.Read.All | Not supported. | PublicKeyInfrastructure.Read.All |
| [group](https://learn.microsoft.com/en-us/graph/api/resources/group?view=graph-rest-1.0) | Group.ReadWrite.All | Not supported. | Group.ReadWrite.All |
| [servicePrincipal](https://learn.microsoft.com/en-us/graph/api/resources/serviceprincipal?view=graph-rest-1.0) | Application.ReadWrite.All | Not supported. | Application.ReadWrite.OwnedBy |
| [user](https://learn.microsoft.com/en-us/graph/api/resources/user?view=graph-rest-1.0) | User.DeleteRestore.All | Not supported. | User.DeleteRestore.All |

Important

For delegated access using work or school accounts, the signed-in user must be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) or a custom role that grants the permissions required for this operation. This operation supports the following built-in roles, which provide only the least privilege necessary:

- Agent identities, agent identity blueprints, and agent identity blueprint principals: Agent ID Administrator
- Administrative units: Directory Readers \(read-only\), Global Readers \(read-only\), Privileged Role Administrator
- Applications: Hybrid Identity Administrator, Cloud Application Administrator, Application Administrator
- External user profiles: Global Reader \(read-only\), Skype for Business Administrator, Teams Administrator
- Groups: Groups Administrator \(except for role-assignable groups\), User Administrator \(except for role-assignable groups\), Privileged Role Administrator \(least privileged role for role-assignable groups\)
- Pending external user profiles: Global Reader \(read-only\), Skype for Business Administrator, Teams Administrator
- Service principals: Hybrid Identity Administrator, Cloud Application Administrator, Application Administrator
- Users: Authentication Administrator, Privileged Authentication Administrator, User Administrator. However, to restore users with privileged administrator roles:

  - In delegated scenarios, the app must be assigned the *Directory.AccessAsUser.All* delegated permission, and the calling user must also be assigned a higher privileged administrator role as indicated in [Who can perform sensitive actions?](https://learn.microsoft.com/en-us/graph/api/resources/users#who-can-perform-sensitive-actions).
  - In app-only scenarios and in addition to being granted the *User.ReadWrite.All* application permission, the app must be assigned a higher privileged administrator role as indicated in [Who can perform sensitive actions?](https://learn.microsoft.com/en-us/graph/api/resources/users#who-can-perform-sensitive-actions).

## HTTP request

```http
POST /directory/deletedItems/{id}/restore
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-type | application/json |

## Request body

In the request body, supply a JSON representation of the parameters.

The following table lists the parameters that are required when you call this action.

| Parameter | Type | Description |
| :--- | :--- | :--- |
| autoReconcileProxyConflict | Boolean | Optional parameter. Indicates whether Microsoft Entra ID should remove any conflicting proxy addresses while restoring a soft-deleted user whose one or more proxy addresses are currently used for an active user. Used only for restoring soft-deleted [user](https://learn.microsoft.com/en-us/graph/api/resources/user?view=graph-rest-1.0). The default value for this paramater is `false`. |
| newUserPrincipalName | String | The new **userPrincipalName** to add to the restored [user](https://learn.microsoft.com/en-us/graph/api/resources/user?view=graph-rest-1.0). Optional. |

## Response

If successful, this method returns a `200 OK` response code and a [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0) object in the response body.

## Examples

### Example 1: Restore a deleted directory object

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
POST https://graph.microsoft.com/v1.0/directory/deletedItems/46cc6179-19d0-473e-97ad-6ff84347bbbb/restore
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Directory.DeletedItems["{directoryObject-id}"].Restore.PostAsync();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  //other-imports
)


// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
restore, err := graphClient.Directory().DeletedItems().ByDirectoryObjectId("directoryObject-id").Restore().Post(context.Background(), nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

var result = graphClient.directory().deletedItems().byDirectoryObjectId("{directoryObject-id}").restore().post();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

await client.api('/directory/deletedItems/46cc6179-19d0-473e-97ad-6ff84347bbbb/restore')
	.post();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);


$result = $graphServiceClient->directory()->deletedItems()->byDirectoryObjectId('directoryObject-id')->restore()->post()->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Identity.DirectoryManagement

Restore-MgDirectoryDeletedItem -DirectoryObjectId $directoryObjectId
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python

result = await graph_client.directory.deleted_items.by_directory_object_id('directoryObject-id').restore.post()
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-type: application/json

{
  "@odata.context":"https://graph.microsoft.com/v1.0/$metadata#directoryObjects/$entity",
  "@odata.type":"#microsoft.graph.group",
  "id":"46cc6179-19d0-473e-97ad-6ff84347bbbb",
  "displayName":"SampleGroup",
  "groupTypes":["Unified"],
  "mail":"example@contoso.com",
  "mailEnabled":true,
  "mailNickname":"Example",
  "securityEnabled":false,
  "visibility":"Public"
}
```

### Example 2: Restore a deleted user and remove conflicting proxy addresses

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
POST https://graph.microsoft.com/v1.0/directory/deletedItems/78bf875b-9343-4edc-9130-0d3958113563/restore
Content-Type: application/json

{
  "autoReconcileProxyConflict": true
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.DirectoryNamespace.DeletedItems.Item.Restore;

var requestBody = new RestorePostRequestBody
{
	AdditionalData = new Dictionary<string, object>
	{
		{
			"autoReconcileProxyConflict" , true
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Directory.DeletedItems["{directoryObject-id}"].Restore.PostAsync(requestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphdirectory "github.com/microsoftgraph/msgraph-sdk-go/directory"
	  //other-imports
)

requestBody := graphdirectory.NewRestorePostRequestBody()
additionalData := map[string]interface{}{
	autoReconcileProxyConflict := true
requestBody.SetAutoReconcileProxyConflict(&autoReconcileProxyConflict) 
}
requestBody.SetAdditionalData(additionalData)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
restore, err := graphClient.Directory().DeletedItems().ByDirectoryObjectId("directoryObject-id").Restore().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.directory.deleteditems.item.restore.RestorePostRequestBody restorePostRequestBody = new com.microsoft.graph.directory.deleteditems.item.restore.RestorePostRequestBody();
HashMap<String, Object> additionalData = new HashMap<String, Object>();
additionalData.put("autoReconcileProxyConflict", true);
restorePostRequestBody.setAdditionalData(additionalData);
var result = graphClient.directory().deletedItems().byDirectoryObjectId("{directoryObject-id}").restore().post(restorePostRequestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const directoryObject = {
  autoReconcileProxyConflict: true
};

await client.api('/directory/deletedItems/78bf875b-9343-4edc-9130-0d3958113563/restore')
	.post(directoryObject);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Directory\DeletedItems\Item\Restore\RestorePostRequestBody;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new RestorePostRequestBody();
$additionalData = [
	'autoReconcileProxyConflict' => true,
];
$requestBody->setAdditionalData($additionalData);

$result = $graphServiceClient->directory()->deletedItems()->byDirectoryObjectId('directoryObject-id')->restore()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Identity.DirectoryManagement

$params = @{
	autoReconcileProxyConflict = $true
}

Restore-MgDirectoryDeletedItem -DirectoryObjectId $directoryObjectId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.directory.deleteditems.item.restore.restore_post_request_body import RestorePostRequestBody
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = RestorePostRequestBody(
	additional_data = {
			"auto_reconcile_proxy_conflict" : True,
	}
)

result = await graph_client.directory.deleted_items.by_directory_object_id('directoryObject-id').restore.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#users/$entity",
    "@odata.type": "#microsoft.graph.user",
    "id": "78bf875b-9343-4edc-9130-0d3958113563",
    "businessPhones": [],
    "displayName": "SampleUser",
    "givenName": "Sample",
    "jobTitle": "Product Marketing Manager",
    "mail": "sampleuser@contoso.com",
    "mobilePhone": "+1 425 555 0109",
    "officeLocation": "18/2111",
    "preferredLanguage": "en-US",
    "surname": "Vance",
    "userPrincipalName": "sampleuser@contoso.com"
}
```

### Example 3: Restore a deleted user and assign them a new userPrincipalName

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
POST https://graph.microsoft.com/v1.0/directory/deletedItems/78bf875b-9343-4edc-9130-0d3958113563/restore
Content-Type: application/json

{
  "newUserPrincipalName": "johndoe@contoso.com"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.DirectoryNamespace.DeletedItems.Item.Restore;

var requestBody = new RestorePostRequestBody
{
	AdditionalData = new Dictionary<string, object>
	{
		{
			"newUserPrincipalName" , "johndoe@contoso.com"
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Directory.DeletedItems["{directoryObject-id}"].Restore.PostAsync(requestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphdirectory "github.com/microsoftgraph/msgraph-sdk-go/directory"
	  //other-imports
)

requestBody := graphdirectory.NewRestorePostRequestBody()
additionalData := map[string]interface{}{
	"newUserPrincipalName" : "johndoe@contoso.com", 
}
requestBody.SetAdditionalData(additionalData)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
restore, err := graphClient.Directory().DeletedItems().ByDirectoryObjectId("directoryObject-id").Restore().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.directory.deleteditems.item.restore.RestorePostRequestBody restorePostRequestBody = new com.microsoft.graph.directory.deleteditems.item.restore.RestorePostRequestBody();
HashMap<String, Object> additionalData = new HashMap<String, Object>();
additionalData.put("newUserPrincipalName", "johndoe@contoso.com");
restorePostRequestBody.setAdditionalData(additionalData);
var result = graphClient.directory().deletedItems().byDirectoryObjectId("{directoryObject-id}").restore().post(restorePostRequestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const directoryObject = {
  newUserPrincipalName: 'johndoe@contoso.com'
};

await client.api('/directory/deletedItems/78bf875b-9343-4edc-9130-0d3958113563/restore')
	.post(directoryObject);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Directory\DeletedItems\Item\Restore\RestorePostRequestBody;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new RestorePostRequestBody();
$additionalData = [
	'newUserPrincipalName' => 'johndoe@contoso.com',
];
$requestBody->setAdditionalData($additionalData);

$result = $graphServiceClient->directory()->deletedItems()->byDirectoryObjectId('directoryObject-id')->restore()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Identity.DirectoryManagement

$params = @{
	newUserPrincipalName = "johndoe@contoso.com"
}

Restore-MgDirectoryDeletedItem -DirectoryObjectId $directoryObjectId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.directory.deleteditems.item.restore.restore_post_request_body import RestorePostRequestBody
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = RestorePostRequestBody(
	additional_data = {
			"new_user_principal_name" : "johndoe@contoso.com",
	}
)

result = await graph_client.directory.deleted_items.by_directory_object_id('directoryObject-id').restore.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#directoryObjects/$entity",
    "@odata.type": "#microsoft.graph.user",
    "id": "78bf875b-9343-4edc-9130-0d3958113563",
    "businessPhones": [],
    "displayName": "SampleUser",
    "givenName": "Sample",
    "mobilePhone": "+1 425 555 0109",
    "officeLocation": "18/2111",
    "preferredLanguage": "en-US",
    "surname": "Vance",
    "userPrincipalName": "johndoe@contoso.com"
}
```
