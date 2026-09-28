<!-- Source: https://learn.microsoft.com/en-us/graph/api/group-post-approleassignments?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-23 -->

# Grant an appRoleAssignment to a group

Namespace: microsoft.graph

Use this API to assign an app role to a security [group](https://learn.microsoft.com/en-us/graph/api/resources/group?view=graph-rest-1.0). All direct members of the group will be considered assigned. Security groups with dynamic memberships are supported. To grant an app role assignment to a group, you need three identifiers:

- **principalId**: The ID of the **group** to which you are assigning the app role.
- **resourceId**: The ID of the resource **servicePrincipal** that has defined the app role.
- **appRoleId**: The ID of the **appRole** \(defined on the resource service principal\) to assign to the group.

Additional licenses might be required to [use a group to manage access to applications](https://learn.microsoft.com/en-us/azure/active-directory/users-groups-roles/groups-saasapps).

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | AppRoleAssignment.ReadWrite.All and Group.Read.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | AppRoleAssignment.ReadWrite.All and Group.Read.All | Not available. |

Important

For delegated access using work or school accounts, the signed-in user must be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) or a custom role that grants the permissions required for this operation. This operation supports the following built-in roles, which provide only the least privilege necessary:

- Directory Synchronization Accounts - for Microsoft Entra Connect and Microsoft Entra Cloud Sync services
- Directory Writer
- Hybrid Identity Administrator
- Identity Governance Administrator
- Privileged Role Administrator - the least privileged role supported for Microsoft Graph and Azure AD Graph app roles
- User Administrator
- Application Administrator
- Cloud Application Administrator
- Agent ID Administrator - For agent users only

## HTTP request

```http
POST /groups/{groupId}/appRoleAssignments
```

Note

As a best practice, we recommend creating app role assignments through the `appRoleAssignedTo` relationship of the *resource* service principal, instead of the `appRoleAssignments` relationship of the assigned user, group, or service principal.

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of an [appRoleAssignment](https://learn.microsoft.com/en-us/graph/api/resources/approleassignment?view=graph-rest-1.0) object.

The following table lists the properties that are required when you create the [appRoleAssignment](https://learn.microsoft.com/en-us/graph/api/resources/approleassignment?view=graph-rest-1.0). Specify other writable properties as necessary for your **appRoleAssignment**.

| Property | Type | Description |
| --- | --- | --- |
| appRoleId | Guid | The identifier \(**id**\) for the [app role](https://learn.microsoft.com/en-us/graph/api/resources/approle?view=graph-rest-1.0) which is assigned to the principal. This app role must be exposed in the **appRoles** property on the resource application's service principal \(**resourceId**\). If the resource application has not declared any app roles, a default app role ID of `00000000-0000-0000-0000-000000000000` can be specified to signal that the principal is assigned to the resource app without any specific app roles. |
| principalId | Guid | The unique identifier \(**id**\) for the [group](https://learn.microsoft.com/en-us/graph/api/resources/group?view=graph-rest-1.0) being granted the app role. |
| resourceId | Guid | The unique identifier \(**id**\) for the resource [service principal](https://learn.microsoft.com/en-us/graph/api/resources/serviceprincipal?view=graph-rest-1.0) for which the assignment is made. |

## Response

If successful, this method returns a `201 Created` response code and an [appRoleAssignment](https://learn.microsoft.com/en-us/graph/api/resources/approleassignment?view=graph-rest-1.0) object in the response body.

## Examples

### Request

The following example shows a request. In this example, ID in the URL and value of **principalId** would both be the ID of the assigned group.

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [PowerShell](#tabpanel_1_powershell)
- [Python](#tabpanel_1_python)

```http
POST https://graph.microsoft.com/v1.0/groups/7679d9a4-2323-44cd-b5c2-673ec88d8b12/appRoleAssignments
Content-Type: application/json

{
  "principalId": "7679d9a4-2323-44cd-b5c2-673ec88d8b12",
  "resourceId": "076e8b57-bac8-49d7-9396-e3449b685055",
  "appRoleId": "00000000-0000-0000-0000-000000000000"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new AppRoleAssignment
{
	PrincipalId = Guid.Parse("7679d9a4-2323-44cd-b5c2-673ec88d8b12"),
	ResourceId = Guid.Parse("076e8b57-bac8-49d7-9396-e3449b685055"),
	AppRoleId = Guid.Parse("00000000-0000-0000-0000-000000000000"),
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Groups["{group-id}"].AppRoleAssignments.PostAsync(requestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  "github.com/google/uuid"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphmodels "github.com/microsoftgraph/msgraph-sdk-go/models"
	  //other-imports
)

requestBody := graphmodels.NewAppRoleAssignment()
principalId := uuid.MustParse("7679d9a4-2323-44cd-b5c2-673ec88d8b12")
requestBody.SetPrincipalId(&principalId) 
resourceId := uuid.MustParse("076e8b57-bac8-49d7-9396-e3449b685055")
requestBody.SetResourceId(&resourceId) 
appRoleId := uuid.MustParse("00000000-0000-0000-0000-000000000000")
requestBody.SetAppRoleId(&appRoleId) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
appRoleAssignments, err := graphClient.Groups().ByGroupId("group-id").AppRoleAssignments().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

AppRoleAssignment appRoleAssignment = new AppRoleAssignment();
appRoleAssignment.setPrincipalId(UUID.fromString("7679d9a4-2323-44cd-b5c2-673ec88d8b12"));
appRoleAssignment.setResourceId(UUID.fromString("076e8b57-bac8-49d7-9396-e3449b685055"));
appRoleAssignment.setAppRoleId(UUID.fromString("00000000-0000-0000-0000-000000000000"));
AppRoleAssignment result = graphClient.groups().byGroupId("{group-id}").appRoleAssignments().post(appRoleAssignment);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const appRoleAssignment = {
  principalId: '7679d9a4-2323-44cd-b5c2-673ec88d8b12',
  resourceId: '076e8b57-bac8-49d7-9396-e3449b685055',
  appRoleId: '00000000-0000-0000-0000-000000000000'
};

await client.api('/groups/7679d9a4-2323-44cd-b5c2-673ec88d8b12/appRoleAssignments')
	.post(appRoleAssignment);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\AppRoleAssignment;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new AppRoleAssignment();
$requestBody->setPrincipalId('7679d9a4-2323-44cd-b5c2-673ec88d8b12');
$requestBody->setResourceId('076e8b57-bac8-49d7-9396-e3449b685055');
$requestBody->setAppRoleId('00000000-0000-0000-0000-000000000000');

$result = $graphServiceClient->groups()->byGroupId('group-id')->appRoleAssignments()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Applications

$params = @{
	principalId = "7679d9a4-2323-44cd-b5c2-673ec88d8b12"
	resourceId = "076e8b57-bac8-49d7-9396-e3449b685055"
	appRoleId = "00000000-0000-0000-0000-000000000000"
}

New-MgGroupAppRoleAssignment -GroupId $groupId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.app_role_assignment import AppRoleAssignment
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = AppRoleAssignment(
	principal_id = UUID("7679d9a4-2323-44cd-b5c2-673ec88d8b12"),
	resource_id = UUID("076e8b57-bac8-49d7-9396-e3449b685055"),
	app_role_id = UUID("00000000-0000-0000-0000-000000000000"),
)

result = await graph_client.groups.by_group_id('group-id').app_role_assignments.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-type: application/json

{
  "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#groups('7679d9a4-2323-44cd-b5c2-673ec88d8b12')/appRoleAssignments/$entity",
  "id": "pNl5diMjzUS1wmc-yI2LEkGgWqFFrFdLhG2Ly2CysL4",
  "deletedDateTime": null,
  "appRoleId": "00000000-0000-0000-0000-000000000000",
  "createdDateTime": "2021-02-19T17:55:08.3369542Z",
  "principalDisplayName": "Young techmakers",
  "principalId": "7679d9a4-2323-44cd-b5c2-673ec88d8b12",
  "principalType": "Group",
  "resourceDisplayName": "Yammer",
  "resourceId": "076e8b57-bac8-49d7-9396-e3449b685055"
}
```
