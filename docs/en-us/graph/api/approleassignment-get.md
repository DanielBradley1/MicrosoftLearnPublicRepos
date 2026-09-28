<!-- Source: https://learn.microsoft.com/en-us/graph/api/approleassignment-get?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-11-13 -->

# Get appRoleAssignment

Namespace: microsoft.graph

Read the properties and relationships of an [appRoleAssignment](https://learn.microsoft.com/en-us/graph/api/resources/approleassignment?view=graph-rest-1.0) object.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

The following table shows the least privileged permission or permissions required to call this API on each supported resource type. Follow [best practices](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions) to request least privileged permissions. For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Supported resource | Delegated \(work or school account\) | Delegated \(personal Microsoft account\) | Application |
| :--- | :--- | :--- | :--- |
| [group](https://learn.microsoft.com/en-us/graph/api/resources/group?view=graph-rest-1.0) | Group.Read.All | Not supported. | Group.Read.All |
| [servicePrincipal](https://learn.microsoft.com/en-us/graph/api/resources/serviceprincipal?view=graph-rest-1.0) | Application.Read.All | Not supported. | Application.Read.All |
| [user](https://learn.microsoft.com/en-us/graph/api/resources/user?view=graph-rest-1.0) | User.Read | Not supported. | Directory.Read.All |

Important

For delegated access using work or school accounts, the signed-in user must be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) or a custom role that grants the permissions required for this operation. This operation supports the following built-in roles, which provide only the least privilege necessary:

- Guest Inviter - Read app role assignments for users only
- Directory Readers
- Directory Synchronization Accounts - for Microsoft Entra Connect and Microsoft Entra Cloud Sync services
- Directory Writer
- Hybrid Identity Administrator
- Identity Governance Administrator
- Privileged Role Administrator
- User Administrator
- Application Administrator
- Cloud Application Administrator
- Agent ID Administrator - For agent users only

### Other supported permissions

The following higher privileged permissions are supported by each resource:

- Groups:

  - Delegated and application permissions: Directory.Read.All, AppRoleAssignment.ReadWrite.All, Directory.ReadWrite.All

- Users:

  - Delegated permissions: User.ReadBasic.All, Directory.Read.All, AppRoleAssignment.ReadWrite.All
  - Application permissions: Directory.Read.All, AppRoleAssignment.ReadWrite.All

- Service principals:

  - Delegated permissions: Directory.Read.All, Application.ReadWrite.All, Directory.ReadWrite.All
  - Application permissions: Application.ReadWrite.OwnedBy, Application.ReadWrite.All, Directory.ReadWrite.All

## HTTP request

To get details of an appRole granted to a service principal:

```http
GET /servicePrincipals/{client-serviceprincipal-id}/appRoleAssignments/{appRoleAssignment-id}
GET /servicePrincipals(appId='{client-servicePrincipal-appId}')/appRoleAssignments/{appRoleAssignment-id}
```

To get details of an appRole granted to a user, group, or client service principal for the given resource service principal:

```http
GET /servicePrincipals(appId='{resource-servicePrincipal-appId}')/appRoleAssignedTo/{appRoleAssignment-id}
GET /servicePrincipals/{resource-serviceprincipal-id}/appRoleAssignedTo/{appRoleAssignment-id}
```

To get details of an appRole granted to a group:

```http
GET /groups/{group-id}/appRoleAssignments/{appRoleAssignment-id}
```

To get details of an appRole granted to a user:

```http
GET /users/{user-id}/appRoleAssignments/{appRoleAssignment-id}
GET /me/appRoleAssignments/{appRoleAssignment-id}
```

Note

Calling the `/me` endpoint requires a signed-in user and therefore a delegated permission. Application permissions aren't supported when using the `/me` endpoint.

## Optional query parameters

This method supports the `$select` OData query parameter to help customize the response. For general information, see [OData query parameters](https://learn.microsoft.com/en-us/graph/query-parameters).

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and an [appRoleAssignment](https://learn.microsoft.com/en-us/graph/api/resources/approleassignment?view=graph-rest-1.0) object in the response body.

## Examples

### Example 1: Get details of an app role granted to a user, group, or client service principal for the given resource service principal

#### Request

The following request queries the resource service principal to get details of an app role it has granted to a client that can be a user, group, or client service principal in the tenant.

```http
GET https://graph.microsoft.com/v1.0/servicePrincipals(appId='00000003-0000-0000-c000-000000000000')/appRoleAssignedTo/ep6PKgGvOkGVksMuwOXBpxV3dkHvwM1ElSjMUzZtaIA
```

#### Response

The following example shows the response. It shows a client service principal named **Postman** has been granted an app role with the ID **df021288-bdef-4463-88db-98f22de89214** which is the *User.Read.All* application permission, for the resource service principal named **Microsoft Graph**.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#servicePrincipals('00000003-0000-0000-c000-000000000000')/appRoleAssignedTo/$entity",
    "id": "ep6PKgGvOkGVksMuwOXBpxV3dkHvwM1ElSjMUzZtaIA",
    "deletedDateTime": null,
    "appRoleId": "df021288-bdef-4463-88db-98f22de89214",
    "createdDateTime": "2023-02-24T17:01:47.0988029Z",
    "principalDisplayName": "Postman",
    "principalId": "2a8f9e7a-af01-413a-9592-c32ec0e5c1a7",
    "principalType": "ServicePrincipal",
    "resourceDisplayName": "Microsoft Graph",
    "resourceId": "7408235b-7540-4850-82fe-a5f15ed019e2"
}
```

### Example 2: Get details of an app role granted to a service principal

#### Request

The following request queries the client service principal to get details of an app role granted to it. In this instance, the app role represents the application permission.

```http
GET https://graph.microsoft.com/v1.0/servicePrincipals(appId='ceb96a54-de95-49a0-b38c-c55263fcf421')/appRoleAssignments/ep6PKgGvOkGVksMuwOXBpxV3dkHvwM1ElSjMUzZtaIA
```

#### Response

The following example shows the response. It shows a client service principal named **Postman** has been granted an app role with the ID **df021288-bdef-4463-88db-98f22de89214** which is the *User.Read.All* application permission, for the resource service principal named **Microsoft Graph**.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#servicePrincipals('ceb96a54-de95-49a0-b38c-c55263fcf421')/appRoleAssignments/$entity",
    "id": "ep6PKgGvOkGVksMuwOXBpxV3dkHvwM1ElSjMUzZtaIA",
    "deletedDateTime": null,
    "appRoleId": "df021288-bdef-4463-88db-98f22de89214",
    "createdDateTime": "2023-02-24T17:01:47.0988029Z",
    "principalDisplayName": "Postman",
    "principalId": "2a8f9e7a-af01-413a-9592-c32ec0e5c1a7",
    "principalType": "ServicePrincipal",
    "resourceDisplayName": "Microsoft Graph",
    "resourceId": "7408235b-7540-4850-82fe-a5f15ed019e2"
}
```

### Example 3: Get details of an app role granted to the signed-in user

#### Request

The following request queries the signed-in user's appRoleAssignments.

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [PowerShell](#tabpanel_1_powershell)
- [Python](#tabpanel_1_python)

```msgraph
GET https://graph.microsoft.com/v1.0/me/appRoleAssignments/Lo6gEKI-4EyAy9X91LBepo6Aq0Rt6QxBjWRl76txk8I
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Me.AppRoleAssignments["{appRoleAssignment-id}"].GetAsync();
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
appRoleAssignments, err := graphClient.Me().AppRoleAssignments().ByAppRoleAssignmentId("appRoleAssignment-id").Get(context.Background(), nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

AppRoleAssignment result = graphClient.me().appRoleAssignments().byAppRoleAssignmentId("{appRoleAssignment-id}").get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let appRoleAssignment = await client.api('/me/appRoleAssignments/Lo6gEKI-4EyAy9X91LBepo6Aq0Rt6QxBjWRl76txk8I')
	.get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);


$result = $graphServiceClient->me()->appRoleAssignments()->byAppRoleAssignmentId('appRoleAssignment-id')->get()->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Applications

# A UPN can also be used as -UserId.
Get-MgUserAppRoleAssignment -UserId $userId -AppRoleAssignmentId $appRoleAssignmentId
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python

result = await graph_client.me.app_role_assignments.by_app_role_assignment_id('appRoleAssignment-id').get()
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response. It shows the signed-in user has the default app role for a resource service principal named *Postman*.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#users('10a08e2e-3ea2-4ce0-80cb-d5fdd4b05ea6')/appRoleAssignments/$entity",
    "id": "Lo6gEKI-4EyAy9X91LBepo6Aq0Rt6QxBjWRl76txk8I",
    "deletedDateTime": null,
    "appRoleId": "00000000-0000-0000-0000-000000000000",
    "createdDateTime": "2022-09-08T17:43:57.8423817Z",
    "principalDisplayName": "MOD Administrator",
    "principalId": "10a08e2e-3ea2-4ce0-80cb-d5fdd4b05ea6",
    "principalType": "User",
    "resourceDisplayName": "Postman",
    "resourceId": "2a8f9e7a-af01-413a-9592-c32ec0e5c1a7"
}
```
