<!-- Source: https://learn.microsoft.com/en-us/graph/api/serviceprincipal-post-approleassignments?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-23 -->

# Grant an appRoleAssignment to a service principal

Namespace: microsoft.graph

Assign an app role to a client service principal.

App roles that are assigned to service principals are also known as [application permissions](https://learn.microsoft.com/en-us/azure/active-directory/develop/v2-permissions-and-consent#permission-types). Application permissions can be granted directly with app role assignments, or through a [consent experience](https://learn.microsoft.com/en-us/azure/active-directory/develop/application-consent-experience).

To grant an app role assignment to a client service principal, you need three identifiers:

- `principalId`: The `id` of the client service principal to which you are assigning the app role.
- `resourceId`: The `id` of the resource `servicePrincipal` \(the API\) which has defined the app role \(the application permission\).
- `appRoleId`: The `id` of the `appRole` \(defined on the resource service principal\) to assign to the client service principal.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | AppRoleAssignment.ReadWrite.All and Application.Read.All | AppRoleAssignment.ReadWrite.All and Directory.Read.All, Application.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | AppRoleAssignment.ReadWrite.All and Application.Read.All | AppRoleAssignment.ReadWrite.All and Directory.Read.All, Application.ReadWrite.All |

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

You can address the service principal using either its **id** or **appId**. **id** and **appId** are referred to as the **Object ID** and **Application \(Client\) ID**, respectively, in app registrations in the Microsoft Entra admin center.

```http
POST /servicePrincipals/{id}/appRoleAssignments
POST /servicePrincipals(appId='{appId}')/appRoleAssignments
```

Note

As a best practice, we recommend creating app role assignments through the [`appRoleAssignedTo` relationship of the *resource* service principal](https://learn.microsoft.com/en-us/graph/api/serviceprincipal-post-approleassignedto?view=graph-rest-1.0), instead of the `appRoleAssignments` relationship of the assigned user, group, or service principal.

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of an [appRoleAssignment](https://learn.microsoft.com/en-us/graph/api/resources/approleassignment?view=graph-rest-1.0) object.

## Response

If successful, this method returns a `201 Created` response code and an [appRoleAssignment](https://learn.microsoft.com/en-us/graph/api/resources/approleassignment?view=graph-rest-1.0) object in the response body.

## Examples

### Request

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
POST https://graph.microsoft.com/v1.0/servicePrincipals/9028d19c-26a9-4809-8e3f-20ff73e2d75e/appRoleAssignments
Content-Type: application/json

{
  "principalId": "9028d19c-26a9-4809-8e3f-20ff73e2d75e",
  "resourceId": "8fce32da-1246-437b-99cd-76d1d4677bd5",
  "appRoleId": "498476ce-e0fe-48b0-b801-37ba7e2685c6"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new AppRoleAssignment
{
	PrincipalId = Guid.Parse("9028d19c-26a9-4809-8e3f-20ff73e2d75e"),
	ResourceId = Guid.Parse("8fce32da-1246-437b-99cd-76d1d4677bd5"),
	AppRoleId = Guid.Parse("498476ce-e0fe-48b0-b801-37ba7e2685c6"),
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.ServicePrincipals["{servicePrincipal-id}"].AppRoleAssignments.PostAsync(requestBody);
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
principalId := uuid.MustParse("9028d19c-26a9-4809-8e3f-20ff73e2d75e")
requestBody.SetPrincipalId(&principalId) 
resourceId := uuid.MustParse("8fce32da-1246-437b-99cd-76d1d4677bd5")
requestBody.SetResourceId(&resourceId) 
appRoleId := uuid.MustParse("498476ce-e0fe-48b0-b801-37ba7e2685c6")
requestBody.SetAppRoleId(&appRoleId) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
appRoleAssignments, err := graphClient.ServicePrincipals().ByServicePrincipalId("servicePrincipal-id").AppRoleAssignments().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

AppRoleAssignment appRoleAssignment = new AppRoleAssignment();
appRoleAssignment.setPrincipalId(UUID.fromString("9028d19c-26a9-4809-8e3f-20ff73e2d75e"));
appRoleAssignment.setResourceId(UUID.fromString("8fce32da-1246-437b-99cd-76d1d4677bd5"));
appRoleAssignment.setAppRoleId(UUID.fromString("498476ce-e0fe-48b0-b801-37ba7e2685c6"));
AppRoleAssignment result = graphClient.servicePrincipals().byServicePrincipalId("{servicePrincipal-id}").appRoleAssignments().post(appRoleAssignment);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const appRoleAssignment = {
  principalId: '9028d19c-26a9-4809-8e3f-20ff73e2d75e',
  resourceId: '8fce32da-1246-437b-99cd-76d1d4677bd5',
  appRoleId: '498476ce-e0fe-48b0-b801-37ba7e2685c6'
};

await client.api('/servicePrincipals/9028d19c-26a9-4809-8e3f-20ff73e2d75e/appRoleAssignments')
	.post(appRoleAssignment);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\AppRoleAssignment;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new AppRoleAssignment();
$requestBody->setPrincipalId('9028d19c-26a9-4809-8e3f-20ff73e2d75e');
$requestBody->setResourceId('8fce32da-1246-437b-99cd-76d1d4677bd5');
$requestBody->setAppRoleId('498476ce-e0fe-48b0-b801-37ba7e2685c6');

$result = $graphServiceClient->servicePrincipals()->byServicePrincipalId('servicePrincipal-id')->appRoleAssignments()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Applications

$params = @{
	principalId = "9028d19c-26a9-4809-8e3f-20ff73e2d75e"
	resourceId = "8fce32da-1246-437b-99cd-76d1d4677bd5"
	appRoleId = "498476ce-e0fe-48b0-b801-37ba7e2685c6"
}

New-MgServicePrincipalAppRoleAssignment -ServicePrincipalId $servicePrincipalId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.app_role_assignment import AppRoleAssignment
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = AppRoleAssignment(
	principal_id = UUID("9028d19c-26a9-4809-8e3f-20ff73e2d75e"),
	resource_id = UUID("8fce32da-1246-437b-99cd-76d1d4677bd5"),
	app_role_id = UUID("498476ce-e0fe-48b0-b801-37ba7e2685c6"),
)

result = await graph_client.service_principals.by_service_principal_id('servicePrincipal-id').app_role_assignments.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

In this example, note that the value used as the service principal **id** in the request URL \(`9028d19c-26a9-4809-8e3f-20ff73e2d75e`\) is the same as the **principalId** property in the body. The **resourceId** value is the **id** of the resource service principal \(the API\).

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-type: application/json

{
  "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#appRoleAssignments/$entity",
  "id": "2jLOj0YSe0OZzXbR1Gd71fDqFUrPM1xIgUfvWBHJ9n0",
  "createdDateTime": "2021-02-15T16:39:38.2975029Z",
  "appRoleId": "498476ce-e0fe-48b0-b801-37ba7e2685c6",
  "principalDisplayName": "Fabrikam App",
  "principalId": "9028d19c-26a9-4809-8e3f-20ff73e2d75e",
  "principalType": "ServicePrincipal",
  "resourceDisplayName": "Microsoft Graph",
  "resourceId": "8fce32da-1246-437b-99cd-76d1d4677bd5"
}
```
