<!-- Source: https://learn.microsoft.com/en-us/graph/permissions-grant-via-msgraph -->
<!-- Sitemap-Last-Modified: 2025-07-23 -->

# Grant or revoke API permissions programmatically

Granting API permissions to a client app in Microsoft Entra ID records the permission grants as objects that you read, update, or delete like any other data. You can use Microsoft Graph to grant or revoke API permissions for an app. This method avoids [interactive admin consent](https://learn.microsoft.com/en-us/azure/active-directory/manage-apps/consent-and-permissions-overview) and is useful for automation or bulk management.

[Application permissions](https://learn.microsoft.com/en-us/graph/permissions-overview#application-permissions), also called *app roles* or *direct access permissions*, let an app call an API using its own identity. Follow these steps to grant or revoke app roles.

Caution

Be careful! Permissions granted programmatically aren't subject to review or confirmation and take effect immediately.

## Prerequisites

To complete these instructions, you need:

- A Microsoft Entra tenant.
- To run the requests in this article in a delegated context. Complete these steps:

  - Sign in to an API client like [Graph Explorer](https://aka.ms/ge) as a user with privileges to create applications in the tenant. The privileges to create permission grants can be limited or controlled in your tenant through admin-configured [app consent policies](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/manage-app-consent-policies).
  - In the app you're signed in to, consent to the *Application.Read.All* and *AppRoleAssignment.ReadWrite.All* delegated permissions for the signed-in user. You don't need to consent on behalf of your organization.

- Get the object ID of the client service principal to which you grant app roles. In this article, the client service principal is identified by ID `b0d9b9e3-0ecf-4bfd-8dab-9273dd055a94`. In the Microsoft Entra admin center, expand **Identity** > **Applications** > **Enterprise applications** > **App applications** to find the client service principal. Select it and on the **Overview** page, copy the Object ID value.

Caution

Only appropriate users should access apps granted the *AppRoleAssignment.ReadWrite.All* permission.

## Step 1: Get the app roles of the resource service principal

First, find the app roles exposed by the resource service principal. App roles are defined in the **appRoles** object of the service principal. This article uses the Microsoft Graph service principal in your tenant as the resource service principal.

### Request

The following request retrieves the app roles defined by the Microsoft Graph service principal in the tenant.

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [PowerShell](#tabpanel_1_powershell)
- [Python](#tabpanel_1_python)

```msgraph
GET https://graph.microsoft.com/v1.0/servicePrincipals?$filter=appId eq '00000003-0000-0000-c000-000000000000'&$select=id,displayName,appId,appRoles
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.ServicePrincipals.GetAsync((requestConfiguration) =>
{
	requestConfiguration.QueryParameters.Filter = "appId eq '00000003-0000-0000-c000-000000000000'";
	requestConfiguration.QueryParameters.Select = new string []{ "id","displayName","appId","appRoles" };
});
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphserviceprincipals "github.com/microsoftgraph/msgraph-sdk-go/serviceprincipals"
	  //other-imports
)


requestFilter := "appId eq '00000003-0000-0000-c000-000000000000'"

requestParameters := &graphserviceprincipals.ServicePrincipalsRequestBuilderGetQueryParameters{
	Filter: &requestFilter,
	Select: [] string {"id","displayName","appId","appRoles"},
}
configuration := &graphserviceprincipals.ServicePrincipalsRequestBuilderGetRequestConfiguration{
	QueryParameters: requestParameters,
}

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
servicePrincipals, err := graphClient.ServicePrincipals().Get(context.Background(), configuration)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

ServicePrincipalCollectionResponse result = graphClient.servicePrincipals().get(requestConfiguration -> {
	requestConfiguration.queryParameters.filter = "appId eq '00000003-0000-0000-c000-000000000000'";
	requestConfiguration.queryParameters.select = new String []{"id", "displayName", "appId", "appRoles"};
});
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let servicePrincipals = await client.api('/servicePrincipals')
	.filter('appId eq \'00000003-0000-0000-c000-000000000000\'')
	.select('id,displayName,appId,appRoles')
	.get();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\ServicePrincipals\ServicePrincipalsRequestBuilderGetRequestConfiguration;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestConfiguration = new ServicePrincipalsRequestBuilderGetRequestConfiguration();
$queryParameters = ServicePrincipalsRequestBuilderGetRequestConfiguration::createQueryParameters();
$queryParameters->filter = "appId eq '00000003-0000-0000-c000-000000000000'";
$queryParameters->select = ["id","displayName","appId","appRoles"];
$requestConfiguration->queryParameters = $queryParameters;


$result = $graphServiceClient->servicePrincipals()->get($requestConfiguration)->wait();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```powershell

Import-Module Microsoft.Graph.Applications

Get-MgServicePrincipal -Filter "appId eq '00000003-0000-0000-c000-000000000000'" -Property "id,displayName,appId,appRoles" 
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.service_principals.service_principals_request_builder import ServicePrincipalsRequestBuilder
from kiota_abstractions.base_request_configuration import RequestConfiguration
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
query_params = ServicePrincipalsRequestBuilder.ServicePrincipalsRequestBuilderGetQueryParameters(
		filter = "appId eq '00000003-0000-0000-c000-000000000000'",
		select = ["id","displayName","appId","appRoles"],
)

request_configuration = RequestConfiguration(
query_parameters = query_params,
)

result = await graph_client.service_principals.get(request_configuration = request_configuration)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-Type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#servicePrincipals(id,displayName,appId,appRoles)",
    "value": [
        {
            "id": "7ea9e944-71ce-443d-811c-71e8047b557a",
            "displayName": "Microsoft Graph",
            "appId": "00000003-0000-0000-c000-000000000000",
            "appRoles": [
                {
                    "allowedMemberTypes": [
                        "Application"
                    ],
                    "description": "Allows the app to read user profiles without a signed in user.",
                    "displayName": "Read all users' full profiles",
                    "id": "df021288-bdef-4463-88db-98f22de89214",
                    "isEnabled": true,
                    "origin": "Application",
                    "value": "User.Read.All"
                }
            ]
        }
    ]
}
```

## Step 2: Grant an app role to a client service principal

In this step, grant your app an app role that's exposed by Microsoft Graph, resulting in an **app role assignment**. From Step 1, the object ID of Microsoft Graph is `7ea9e944-71ce-443d-811c-71e8047b557a`, and the app role `User.Read.All` is identified by ID `df021288-bdef-4463-88db-98f22de89214`.

### Request

The following request grants your client app \(the principal of ID `b0d9b9e3-0ecf-4bfd-8dab-9273dd055a94`\) an app role of ID `df021288-bdef-4463-88db-98f22de89214` that's exposed by a resource service principal of ID `7ea9e944-71ce-443d-811c-71e8047b557a`.

Note

If you use the Python SDK, import the following libraries:

```
from msgraph.generated.models.app_role_assignment import AppRoleAssignment
from msgraph.generated.models.service_principal import ServicePrincipal
```

- [HTTP](#tabpanel_2_http)
- [C#](#tabpanel_2_csharp)
- [Go](#tabpanel_2_go)
- [Java](#tabpanel_2_java)
- [JavaScript](#tabpanel_2_javascript)
- [PHP](#tabpanel_2_php)
- [PowerShell](#tabpanel_2_powershell)
- [Python](#tabpanel_2_python)

```msgraph
POST https://graph.microsoft.com/v1.0/servicePrincipals/7ea9e944-71ce-443d-811c-71e8047b557a/appRoleAssignedTo
Content-Type: application/json

{
    "principalId": "b0d9b9e3-0ecf-4bfd-8dab-9273dd055a94",
    "resourceId": "7ea9e944-71ce-443d-811c-71e8047b557a",
    "appRoleId": "df021288-bdef-4463-88db-98f22de89214"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new AppRoleAssignment
{
	PrincipalId = Guid.Parse("b0d9b9e3-0ecf-4bfd-8dab-9273dd055a94"),
	ResourceId = Guid.Parse("7ea9e944-71ce-443d-811c-71e8047b557a"),
	AppRoleId = Guid.Parse("df021288-bdef-4463-88db-98f22de89214"),
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.ServicePrincipals["{servicePrincipal-id}"].AppRoleAssignedTo.PostAsync(requestBody);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

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
principalId := uuid.MustParse("b0d9b9e3-0ecf-4bfd-8dab-9273dd055a94")
requestBody.SetPrincipalId(&principalId) 
resourceId := uuid.MustParse("7ea9e944-71ce-443d-811c-71e8047b557a")
requestBody.SetResourceId(&resourceId) 
appRoleId := uuid.MustParse("df021288-bdef-4463-88db-98f22de89214")
requestBody.SetAppRoleId(&appRoleId) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
appRoleAssignedTo, err := graphClient.ServicePrincipals().ByServicePrincipalId("servicePrincipal-id").AppRoleAssignedTo().Post(context.Background(), requestBody, nil)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

AppRoleAssignment appRoleAssignment = new AppRoleAssignment();
appRoleAssignment.setPrincipalId(UUID.fromString("b0d9b9e3-0ecf-4bfd-8dab-9273dd055a94"));
appRoleAssignment.setResourceId(UUID.fromString("7ea9e944-71ce-443d-811c-71e8047b557a"));
appRoleAssignment.setAppRoleId(UUID.fromString("df021288-bdef-4463-88db-98f22de89214"));
AppRoleAssignment result = graphClient.servicePrincipals().byServicePrincipalId("{servicePrincipal-id}").appRoleAssignedTo().post(appRoleAssignment);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const appRoleAssignment = {
    principalId: 'b0d9b9e3-0ecf-4bfd-8dab-9273dd055a94',
    resourceId: '7ea9e944-71ce-443d-811c-71e8047b557a',
    appRoleId: 'df021288-bdef-4463-88db-98f22de89214'
};

await client.api('/servicePrincipals/7ea9e944-71ce-443d-811c-71e8047b557a/appRoleAssignedTo')
	.post(appRoleAssignment);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\AppRoleAssignment;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new AppRoleAssignment();
$requestBody->setPrincipalId('b0d9b9e3-0ecf-4bfd-8dab-9273dd055a94');
$requestBody->setResourceId('7ea9e944-71ce-443d-811c-71e8047b557a');
$requestBody->setAppRoleId('df021288-bdef-4463-88db-98f22de89214');

$result = $graphServiceClient->servicePrincipals()->byServicePrincipalId('servicePrincipal-id')->appRoleAssignedTo()->post($requestBody)->wait();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```powershell

Import-Module Microsoft.Graph.Applications

$params = @{
	principalId = "b0d9b9e3-0ecf-4bfd-8dab-9273dd055a94"
	resourceId = "7ea9e944-71ce-443d-811c-71e8047b557a"
	appRoleId = "df021288-bdef-4463-88db-98f22de89214"
}

New-MgServicePrincipalAppRoleAssignedTo -ServicePrincipalId $servicePrincipalId -BodyParameter $params
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.app_role_assignment import AppRoleAssignment
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = AppRoleAssignment(
	principal_id = UUID("b0d9b9e3-0ecf-4bfd-8dab-9273dd055a94"),
	resource_id = UUID("7ea9e944-71ce-443d-811c-71e8047b557a"),
	app_role_id = UUID("df021288-bdef-4463-88db-98f22de89214"),
)

result = await graph_client.service_principals.by_service_principal_id('servicePrincipal-id').app_role_assigned_to.post(request_body)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

### Response

```http
HTTP/1.1 201 Created
Content-type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#servicePrincipals('7ea9e944-71ce-443d-811c-71e8047b557a')/appRoleAssignedTo/$entity",
    "id": "47nZsM8O_UuNq5Jz3QValCxBBiqJea9Drc9CMK4Ru_M",
    "deletedDateTime": null,
    "appRoleId": "df021288-bdef-4463-88db-98f22de89214",
    "createdDateTime": "2022-05-18T15:37:21.8215423Z",
    "principalDisplayName": "My application",
    "principalId": "b0d9b9e3-0ecf-4bfd-8dab-9273dd055a94",
    "principalType": "ServicePrincipal",
    "resourceDisplayName": "Microsoft Graph",
    "resourceId": "7ea9e944-71ce-443d-811c-71e8047b557a"
}
```

### Confirm the app role assignment

Verify the principals with role assignments to the resource service principal by running the following request.

#### Request

- [HTTP](#tabpanel_3_http)
- [C#](#tabpanel_3_csharp)
- [Go](#tabpanel_3_go)
- [Java](#tabpanel_3_java)
- [JavaScript](#tabpanel_3_javascript)
- [PHP](#tabpanel_3_php)
- [PowerShell](#tabpanel_3_powershell)
- [Python](#tabpanel_3_python)

```msgraph
GET https://graph.microsoft.com/v1.0/servicePrincipals/7ea9e944-71ce-443d-811c-71e8047b557a/appRoleAssignedTo
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.ServicePrincipals["{servicePrincipal-id}"].AppRoleAssignedTo.GetAsync();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  //other-imports
)


// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
appRoleAssignedTo, err := graphClient.ServicePrincipals().ByServicePrincipalId("servicePrincipal-id").AppRoleAssignedTo().Get(context.Background(), nil)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

AppRoleAssignmentCollectionResponse result = graphClient.servicePrincipals().byServicePrincipalId("{servicePrincipal-id}").appRoleAssignedTo().get();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let appRoleAssignedTo = await client.api('/servicePrincipals/7ea9e944-71ce-443d-811c-71e8047b557a/appRoleAssignedTo')
	.get();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```php

<?php
use Microsoft\Graph\GraphServiceClient;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);


$result = $graphServiceClient->servicePrincipals()->byServicePrincipalId('servicePrincipal-id')->appRoleAssignedTo()->get()->wait();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```powershell

Import-Module Microsoft.Graph.Applications

Get-MgServicePrincipalAppRoleAssignedTo -ServicePrincipalId $servicePrincipalId
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python

result = await graph_client.service_principals.by_service_principal_id('servicePrincipal-id').app_role_assigned_to.get()
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

#### Response

The response object includes a collection of app role assignments to your resource service principal and includes the app role assignment you created in the preceding request.

```http
HTTP/1.1 201 Created
Content-type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#servicePrincipals('7ea9e944-71ce-443d-811c-71e8047b557a')/appRoleAssignedTo",
    "value": [
        {
            "id": "47nZsM8O_UuNq5Jz3QValCxBBiqJea9Drc9CMK4Ru_M",
            "deletedDateTime": null,
            "appRoleId": "df021288-bdef-4463-88db-98f22de89214",
            "createdDateTime": "2022-05-18T15:37:21.8997216Z",
            "principalDisplayName": "My application",
            "principalId": "b0d9b9e3-0ecf-4bfd-8dab-9273dd055a94",
            "principalType": "ServicePrincipal",
            "resourceDisplayName": "Microsoft Graph",
            "resourceId": "7ea9e944-71ce-443d-811c-71e8047b557a"
        }
    ]
}
```

## Step 3: Revoke an app role assignment from a client service principal

### Request

- [HTTP](#tabpanel_4_http)
- [C#](#tabpanel_4_csharp)
- [Go](#tabpanel_4_go)
- [Java](#tabpanel_4_java)
- [JavaScript](#tabpanel_4_javascript)
- [PHP](#tabpanel_4_php)
- [PowerShell](#tabpanel_4_powershell)
- [Python](#tabpanel_4_python)

```msgraph
DELETE https://graph.microsoft.com/v1.0/servicePrincipals/7ea9e944-71ce-443d-811c-71e8047b557a/appRoleAssignedTo/47nZsM8O_UuNq5Jz3QValCxBBiqJea9Drc9CMK4Ru_M
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
await graphClient.ServicePrincipals["{servicePrincipal-id}"].AppRoleAssignedTo["{appRoleAssignment-id}"].DeleteAsync();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  //other-imports
)


// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
graphClient.ServicePrincipals().ByServicePrincipalId("servicePrincipal-id").AppRoleAssignedTo().ByAppRoleAssignmentId("appRoleAssignment-id").Delete(context.Background(), nil)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

graphClient.servicePrincipals().byServicePrincipalId("{servicePrincipal-id}").appRoleAssignedTo().byAppRoleAssignmentId("{appRoleAssignment-id}").delete();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

await client.api('/servicePrincipals/7ea9e944-71ce-443d-811c-71e8047b557a/appRoleAssignedTo/47nZsM8O_UuNq5Jz3QValCxBBiqJea9Drc9CMK4Ru_M')
	.delete();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```php

<?php
use Microsoft\Graph\GraphServiceClient;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);


$graphServiceClient->servicePrincipals()->byServicePrincipalId('servicePrincipal-id')->appRoleAssignedTo()->byAppRoleAssignmentId('appRoleAssignment-id')->delete()->wait();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```powershell

Import-Module Microsoft.Graph.Applications

Remove-MgServicePrincipalAppRoleAssignedTo -ServicePrincipalId $servicePrincipalId -AppRoleAssignmentId $appRoleAssignmentId
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python

await graph_client.service_principals.by_service_principal_id('servicePrincipal-id').app_role_assigned_to.by_app_role_assignment_id('appRoleAssignment-id').delete()
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

### Response

```http
HTTP/1.1 204 No Content
```

## Related content

- [Grant app roles using Microsoft Graph PowerShell](https://learn.microsoft.com/en-us/powershell/microsoftgraph/tutorial-grant-app-only-api-permissions)
- Learn more about the [appRoleAssignment resource type](https://learn.microsoft.com/en-us/graph/api/resources/approleassignment).

[Delegated permissions](https://learn.microsoft.com/en-us/graph/permissions-overview#delegated-permissions), also called *app roles* or *OAuth2 permissions*, let an app call an API on behalf of a signed-in user. Follow these steps to grant or revoke delegated permissions.

Caution

Be careful! Permissions granted programmatically aren't subject to review or confirmation. They take effect immediately.

## Prerequisites

To complete these instructions, you need:

- A valid Microsoft Entra tenant.
- To run the requests in this article as a user. Complete these steps:

  - Sign in to an API client like [Graph Explorer](https://aka.ms/ge) as a user with the *Cloud Application Administrator* Microsoft Entra role. This role is the least privileged role for creating applications and granting consent to delegated permissions in the tenant. The privileges to create permission grants can be limited or controlled in your tenant through admin-configured [app consent policies](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/manage-app-consent-policies).
  - In the app you're signed in to, consent to the *Application.Read.All* and *DelegatedPermissionGrant.ReadWrite.All* delegated permissions for the signed-in user. You don't need to consent on behalf of your organization.
  - Get the object ID of the client service principal to which you grant delegated permissions on behalf of a user. In this article, the client service principal is identified by ID `b0d9b9e3-0ecf-4bfd-8dab-9273dd055a94`. In the Microsoft Entra admin center, expand **Identity** > **Applications** > **Enterprise applications** > **App applications** to find the client service principal. Select it and on the **Overview** page, copy the Object ID value.

Caution

Only appropriate users should access apps granted the *DelegatedPermissionGrant.ReadWrite.All* permission.

## Step 1: Get delegated permissions of the resource service principal

First, find the delegated permissions exposed by the resource service principal. Delegated permissions are defined in the **oauth2PermissionScopes** object of the service principal. This article uses the Microsoft Graph service principal in your tenant as the resource service principal.

### Request

This request retrieves the delegated permissions defined by the Microsoft Graph service principal in the tenant.

- [HTTP](#tabpanel_5_http)
- [C#](#tabpanel_5_csharp)
- [Go](#tabpanel_5_go)
- [Java](#tabpanel_5_java)
- [JavaScript](#tabpanel_5_javascript)
- [PHP](#tabpanel_5_php)
- [PowerShell](#tabpanel_5_powershell)
- [Python](#tabpanel_5_python)

```msgraph
GET https://graph.microsoft.com/v1.0/servicePrincipals?$filter=appId eq '00000003-0000-0000-c000-000000000000'&$select=id,displayName,appId,oauth2PermissionScopes
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.ServicePrincipals.GetAsync((requestConfiguration) =>
{
	requestConfiguration.QueryParameters.Filter = "appId eq '00000003-0000-0000-c000-000000000000'";
	requestConfiguration.QueryParameters.Select = new string []{ "id","displayName","appId","oauth2PermissionScopes" };
});
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphserviceprincipals "github.com/microsoftgraph/msgraph-sdk-go/serviceprincipals"
	  //other-imports
)


requestFilter := "appId eq '00000003-0000-0000-c000-000000000000'"

requestParameters := &graphserviceprincipals.ServicePrincipalsRequestBuilderGetQueryParameters{
	Filter: &requestFilter,
	Select: [] string {"id","displayName","appId","oauth2PermissionScopes"},
}
configuration := &graphserviceprincipals.ServicePrincipalsRequestBuilderGetRequestConfiguration{
	QueryParameters: requestParameters,
}

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
servicePrincipals, err := graphClient.ServicePrincipals().Get(context.Background(), configuration)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

ServicePrincipalCollectionResponse result = graphClient.servicePrincipals().get(requestConfiguration -> {
	requestConfiguration.queryParameters.filter = "appId eq '00000003-0000-0000-c000-000000000000'";
	requestConfiguration.queryParameters.select = new String []{"id", "displayName", "appId", "oauth2PermissionScopes"};
});
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let servicePrincipals = await client.api('/servicePrincipals')
	.filter('appId eq \'00000003-0000-0000-c000-000000000000\'')
	.select('id,displayName,appId,oauth2PermissionScopes')
	.get();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\ServicePrincipals\ServicePrincipalsRequestBuilderGetRequestConfiguration;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestConfiguration = new ServicePrincipalsRequestBuilderGetRequestConfiguration();
$queryParameters = ServicePrincipalsRequestBuilderGetRequestConfiguration::createQueryParameters();
$queryParameters->filter = "appId eq '00000003-0000-0000-c000-000000000000'";
$queryParameters->select = ["id","displayName","appId","oauth2PermissionScopes"];
$requestConfiguration->queryParameters = $queryParameters;


$result = $graphServiceClient->servicePrincipals()->get($requestConfiguration)->wait();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```powershell

Import-Module Microsoft.Graph.Applications

Get-MgServicePrincipal -Filter "appId eq '00000003-0000-0000-c000-000000000000'" -Property "id,displayName,appId,oauth2PermissionScopes" 
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.service_principals.service_principals_request_builder import ServicePrincipalsRequestBuilder
from kiota_abstractions.base_request_configuration import RequestConfiguration
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
query_params = ServicePrincipalsRequestBuilder.ServicePrincipalsRequestBuilderGetQueryParameters(
		filter = "appId eq '00000003-0000-0000-c000-000000000000'",
		select = ["id","displayName","appId","oauth2PermissionScopes"],
)

request_configuration = RequestConfiguration(
query_parameters = query_params,
)

result = await graph_client.service_principals.get(request_configuration = request_configuration)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-Type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#servicePrincipals(id,displayName,appId,oauth2PermissionScopes)",
    "value": [
        {
            "id": "7ea9e944-71ce-443d-811c-71e8047b557a",
            "displayName": "Microsoft Graph",
            "appId": "00000003-0000-0000-c000-000000000000",
            "oauth2PermissionScopes": [
                {
                    "adminConsentDescription": "Allows the app to read the full set of profile properties, reports, and managers of other users in your organization, on behalf of the signed-in user.",
                    "adminConsentDisplayName": "Read all users' full profiles",
                    "id": "a154be20-db9c-4678-8ab7-66f6cc099a59",
                    "isEnabled": true,
                    "type": "Admin",
                    "userConsentDescription": "Allows the app to read the full set of profile properties, reports, and managers of other users in your organization, on your behalf.",
                    "userConsentDisplayName": "Read all users' full profiles",
                    "value": "User.Read.All"
                },
                {
                    "adminConsentDescription": "Allows the app to list groups, and to read their properties and all group memberships on behalf of the signed-in user.  Also allows the app to read calendar, conversations, files, and other group content for all groups the signed-in user can access. ",
                    "adminConsentDisplayName": "Read all groups",
                    "id": "5f8c59db-677d-491f-a6b8-5f174b11ec1d",
                    "isEnabled": true,
                    "type": "Admin",
                    "userConsentDescription": "Allows the app to list groups, and to read their properties and all group memberships on your behalf.  Also allows the app to read calendar, conversations, files, and other group content for all groups you can access.  ",
                    "userConsentDisplayName": "Read all groups",
                    "value": "Group.Read.All"
                }                
            ]
        }
    ]
}
```

## Step 2: Grant delegated permission to the client service principal on behalf of a user

### Request

In this step, grant your app delegated permission that's exposed by Microsoft Graph on behalf of a user, resulting in a **delegated permission grant**.

- From Step 1, the object ID of Microsoft Graph in the tenant is `7ea9e944-71ce-443d-811c-71e8047b557a`
- The delegated permissions `User.Read.All` and `Group.Read.All` are identified by the globally unique IDs `a154be20-db9c-4678-8ab7-66f6cc099a59` and `5f8c59db-677d-491f-a6b8-5f174b11ec1d` respectively.
- The principal is a user identified by ID `3fbd929d-8c56-4462-851e-0eb9a7b3a2a5`.
- The client service principal is identified by ID `b0d9b9e3-0ecf-4bfd-8dab-9273dd055a94`. This is the object **id** of the service principal and *not* its **appId**.

- [HTTP](#tabpanel_6_http)
- [C#](#tabpanel_6_csharp)
- [Go](#tabpanel_6_go)
- [Java](#tabpanel_6_java)
- [JavaScript](#tabpanel_6_javascript)
- [PHP](#tabpanel_6_php)
- [PowerShell](#tabpanel_6_powershell)
- [Python](#tabpanel_6_python)

```msgraph
POST https://graph.microsoft.com/v1.0/oauth2PermissionGrants
Content-Type: application/json

{
    "clientId": "b0d9b9e3-0ecf-4bfd-8dab-9273dd055a94",
    "consentType": "Principal",
    "resourceId": "7ea9e944-71ce-443d-811c-71e8047b557a",
    "principalId": "3fbd929d-8c56-4462-851e-0eb9a7b3a2a5",
    "scope": "User.Read.All Group.Read.All"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new OAuth2PermissionGrant
{
	ClientId = "b0d9b9e3-0ecf-4bfd-8dab-9273dd055a94",
	ConsentType = "Principal",
	ResourceId = "7ea9e944-71ce-443d-811c-71e8047b557a",
	PrincipalId = "3fbd929d-8c56-4462-851e-0eb9a7b3a2a5",
	Scope = "User.Read.All Group.Read.All",
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Oauth2PermissionGrants.PostAsync(requestBody);
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

requestBody := graphmodels.NewOAuth2PermissionGrant()
clientId := "b0d9b9e3-0ecf-4bfd-8dab-9273dd055a94"
requestBody.SetClientId(&clientId) 
consentType := "Principal"
requestBody.SetConsentType(&consentType) 
resourceId := "7ea9e944-71ce-443d-811c-71e8047b557a"
requestBody.SetResourceId(&resourceId) 
principalId := "3fbd929d-8c56-4462-851e-0eb9a7b3a2a5"
requestBody.SetPrincipalId(&principalId) 
scope := "User.Read.All Group.Read.All"
requestBody.SetScope(&scope) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
oauth2PermissionGrants, err := graphClient.Oauth2PermissionGrants().Post(context.Background(), requestBody, nil)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

OAuth2PermissionGrant oAuth2PermissionGrant = new OAuth2PermissionGrant();
oAuth2PermissionGrant.setClientId("b0d9b9e3-0ecf-4bfd-8dab-9273dd055a94");
oAuth2PermissionGrant.setConsentType("Principal");
oAuth2PermissionGrant.setResourceId("7ea9e944-71ce-443d-811c-71e8047b557a");
oAuth2PermissionGrant.setPrincipalId("3fbd929d-8c56-4462-851e-0eb9a7b3a2a5");
oAuth2PermissionGrant.setScope("User.Read.All Group.Read.All");
OAuth2PermissionGrant result = graphClient.oauth2PermissionGrants().post(oAuth2PermissionGrant);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const oAuth2PermissionGrant = {
    clientId: 'b0d9b9e3-0ecf-4bfd-8dab-9273dd055a94',
    consentType: 'Principal',
    resourceId: '7ea9e944-71ce-443d-811c-71e8047b557a',
    principalId: '3fbd929d-8c56-4462-851e-0eb9a7b3a2a5',
    scope: 'User.Read.All Group.Read.All'
};

await client.api('/oauth2PermissionGrants')
	.post(oAuth2PermissionGrant);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\OAuth2PermissionGrant;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new OAuth2PermissionGrant();
$requestBody->setClientId('b0d9b9e3-0ecf-4bfd-8dab-9273dd055a94');
$requestBody->setConsentType('Principal');
$requestBody->setResourceId('7ea9e944-71ce-443d-811c-71e8047b557a');
$requestBody->setPrincipalId('3fbd929d-8c56-4462-851e-0eb9a7b3a2a5');
$requestBody->setScope('User.Read.All Group.Read.All');

$result = $graphServiceClient->oauth2PermissionGrants()->post($requestBody)->wait();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```powershell

Import-Module Microsoft.Graph.Identity.SignIns

$params = @{
	clientId = "b0d9b9e3-0ecf-4bfd-8dab-9273dd055a94"
	consentType = "Principal"
	resourceId = "7ea9e944-71ce-443d-811c-71e8047b557a"
	principalId = "3fbd929d-8c56-4462-851e-0eb9a7b3a2a5"
	scope = "User.Read.All Group.Read.All"
}

New-MgOauth2PermissionGrant -BodyParameter $params
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.o_auth2_permission_grant import OAuth2PermissionGrant
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = OAuth2PermissionGrant(
	client_id = "b0d9b9e3-0ecf-4bfd-8dab-9273dd055a94",
	consent_type = "Principal",
	resource_id = "7ea9e944-71ce-443d-811c-71e8047b557a",
	principal_id = "3fbd929d-8c56-4462-851e-0eb9a7b3a2a5",
	scope = "User.Read.All Group.Read.All",
)

result = await graph_client.oauth2_permission_grants.post(request_body)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

The preceding request grants consent on behalf of a single user, but you can also grant consent on behalf of all users in the tenant. The request body is similar to the previous request body except with the following changes:

- The **consentType** is `AllPrincipals`, indicating that you're consenting on behalf of all users in the tenant.
- The **principalId** property isn't supplied or can be `null`.

Here is an example request body for granting consent on behalf of all users:

```msgraph
POST https://graph.microsoft.com/v1.0/oauth2PermissionGrants
Content-Type: application/json

{
    "clientId": "b0d9b9e3-0ecf-4bfd-8dab-9273dd055a94",
    "consentType": "AllPrincipals",
    "resourceId": "7ea9e944-71ce-443d-811c-71e8047b557a",
    "scope": "User.Read.All Group.Read.All"
}
```

### Response

```http
HTTP/1.1 201 Created
Content-type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#oauth2PermissionGrants/$entity",
    "clientId": "b0d9b9e3-0ecf-4bfd-8dab-9273dd055a94",
    "consentType": "Principal",
    "id": "47nZsM8O_UuNq5Jz3QValETpqX7OcT1EgRxx6AR7VXqdkr0_VoxiRIUeDrmns6Kl",
    "principalId": "3fbd929d-8c56-4462-851e-0eb9a7b3a2a5",
    "resourceId": "7ea9e944-71ce-443d-811c-71e8047b557a",
    "scope": "User.Read.All Group.Read.All"
}
```

If you granted consent for all users in the tenant, the **consentType** in the response object would be `AllPrincipals`, and the **principalId** would be `null`.

### Confirm the permission grant

Verify the principals with delegated permissions to the resource service principal by running the following request.

#### Request

- [HTTP](#tabpanel_7_http)
- [C#](#tabpanel_7_csharp)
- [Go](#tabpanel_7_go)
- [Java](#tabpanel_7_java)
- [JavaScript](#tabpanel_7_javascript)
- [PHP](#tabpanel_7_php)
- [PowerShell](#tabpanel_7_powershell)
- [Python](#tabpanel_7_python)

```msgraph
GET https://graph.microsoft.com/v1.0/oauth2PermissionGrants?$filter=clientId eq 'b0d9b9e3-0ecf-4bfd-8dab-9273dd055a94' and principalId eq '3fbd929d-8c56-4462-851e-0eb9a7b3a2a5' and consentType eq 'Principal'
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Oauth2PermissionGrants.GetAsync((requestConfiguration) =>
{
	requestConfiguration.QueryParameters.Filter = "clientId eq 'b0d9b9e3-0ecf-4bfd-8dab-9273dd055a94' and principalId eq '3fbd929d-8c56-4462-851e-0eb9a7b3a2a5' and consentType eq 'Principal'";
});
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphoauth2permissiongrants "github.com/microsoftgraph/msgraph-sdk-go/oauth2permissiongrants"
	  //other-imports
)


requestFilter := "clientId eq 'b0d9b9e3-0ecf-4bfd-8dab-9273dd055a94' and principalId eq '3fbd929d-8c56-4462-851e-0eb9a7b3a2a5' and consentType eq 'Principal'"

requestParameters := &graphoauth2permissiongrants.Oauth2PermissionGrantsRequestBuilderGetQueryParameters{
	Filter: &requestFilter,
}
configuration := &graphoauth2permissiongrants.Oauth2PermissionGrantsRequestBuilderGetRequestConfiguration{
	QueryParameters: requestParameters,
}

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
oauth2PermissionGrants, err := graphClient.Oauth2PermissionGrants().Get(context.Background(), configuration)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

OAuth2PermissionGrantCollectionResponse result = graphClient.oauth2PermissionGrants().get(requestConfiguration -> {
	requestConfiguration.queryParameters.filter = "clientId eq 'b0d9b9e3-0ecf-4bfd-8dab-9273dd055a94' and principalId eq '3fbd929d-8c56-4462-851e-0eb9a7b3a2a5' and consentType eq 'Principal'";
});
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let oauth2PermissionGrants = await client.api('/oauth2PermissionGrants')
	.filter('clientId eq \'b0d9b9e3-0ecf-4bfd-8dab-9273dd055a94\' and principalId eq \'3fbd929d-8c56-4462-851e-0eb9a7b3a2a5\' and consentType eq \'Principal\'')
	.get();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Oauth2PermissionGrants\Oauth2PermissionGrantsRequestBuilderGetRequestConfiguration;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestConfiguration = new Oauth2PermissionGrantsRequestBuilderGetRequestConfiguration();
$queryParameters = Oauth2PermissionGrantsRequestBuilderGetRequestConfiguration::createQueryParameters();
$queryParameters->filter = "clientId eq 'b0d9b9e3-0ecf-4bfd-8dab-9273dd055a94' and principalId eq '3fbd929d-8c56-4462-851e-0eb9a7b3a2a5' and consentType eq 'Principal'";
$requestConfiguration->queryParameters = $queryParameters;


$result = $graphServiceClient->oauth2PermissionGrants()->get($requestConfiguration)->wait();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```powershell

Import-Module Microsoft.Graph.Identity.SignIns

Get-MgOauth2PermissionGrant -Filter "clientId eq 'b0d9b9e3-0ecf-4bfd-8dab-9273dd055a94' and principalId eq '3fbd929d-8c56-4462-851e-0eb9a7b3a2a5' and consentType eq 'Principal'" 
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.oauth2_permission_grants.oauth2_permission_grants_request_builder import Oauth2PermissionGrantsRequestBuilder
from kiota_abstractions.base_request_configuration import RequestConfiguration
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
query_params = Oauth2PermissionGrantsRequestBuilder.Oauth2PermissionGrantsRequestBuilderGetQueryParameters(
		filter = "clientId eq 'b0d9b9e3-0ecf-4bfd-8dab-9273dd055a94' and principalId eq '3fbd929d-8c56-4462-851e-0eb9a7b3a2a5' and consentType eq 'Principal'",
)

request_configuration = RequestConfiguration(
query_parameters = query_params,
)

result = await graph_client.oauth2_permission_grants.get(request_configuration = request_configuration)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

#### Response

```http
HTTP/1.1 201 Created
Content-type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#oauth2PermissionGrants",
    "value": [
        {
            "clientId": "b0d9b9e3-0ecf-4bfd-8dab-9273dd055a94",
            "consentType": "Principal",
            "id": "47nZsM8O_UuNq5Jz3QValETpqX7OcT1EgRxx6AR7VXqdkr0_VoxiRIUeDrmns6Kl",
            "principalId": "3fbd929d-8c56-4462-851e-0eb9a7b3a2a5",
            "resourceId": "7ea9e944-71ce-443d-811c-71e8047b557a",
            "scope": "User.Read.All Group.Read.All"
        }
    ]
}
```

### Update the permission grant

To add more permissions or remove some permissions for the client to the resource service principal for the user, update the **oauth2PermissionGrant** object as shown in the following request. The request returns a `204 No Content` response.

- [HTTP](#tabpanel_8_http)
- [C#](#tabpanel_8_csharp)
- [Go](#tabpanel_8_go)
- [Java](#tabpanel_8_java)
- [JavaScript](#tabpanel_8_javascript)
- [PHP](#tabpanel_8_php)
- [PowerShell](#tabpanel_8_powershell)
- [Python](#tabpanel_8_python)

```msgraph
PATCH https://graph.microsoft.com/v1.0/oauth2PermissionGrants/47nZsM8O_UuNq5Jz3QValETpqX7OcT1EgRxx6AR7VXqdkr0_VoxiRIUeDrmns6Kl
Content-type: application/json

{
    "scope": "openid profile offline_access DelegatedPermissionGrant.ReadWrite.All AccessReview.ReadWrite.All AgentIdentityBlueprint.ReadWrite.All"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new OAuth2PermissionGrant
{
	Scope = "openid profile offline_access DelegatedPermissionGrant.ReadWrite.All AccessReview.ReadWrite.All AgentIdentityBlueprint.ReadWrite.All",
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Oauth2PermissionGrants["{oAuth2PermissionGrant-id}"].PatchAsync(requestBody);
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

requestBody := graphmodels.NewOAuth2PermissionGrant()
scope := "openid profile offline_access DelegatedPermissionGrant.ReadWrite.All AccessReview.ReadWrite.All AgentIdentityBlueprint.ReadWrite.All"
requestBody.SetScope(&scope) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
oauth2PermissionGrants, err := graphClient.Oauth2PermissionGrants().ByOAuth2PermissionGrantId("oAuth2PermissionGrant-id").Patch(context.Background(), requestBody, nil)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

OAuth2PermissionGrant oAuth2PermissionGrant = new OAuth2PermissionGrant();
oAuth2PermissionGrant.setScope("openid profile offline_access DelegatedPermissionGrant.ReadWrite.All AccessReview.ReadWrite.All AgentIdentityBlueprint.ReadWrite.All");
OAuth2PermissionGrant result = graphClient.oauth2PermissionGrants().byOAuth2PermissionGrantId("{oAuth2PermissionGrant-id}").patch(oAuth2PermissionGrant);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const oAuth2PermissionGrant = {
    scope: 'openid profile offline_access DelegatedPermissionGrant.ReadWrite.All AccessReview.ReadWrite.All AgentIdentityBlueprint.ReadWrite.All'
};

await client.api('/oauth2PermissionGrants/47nZsM8O_UuNq5Jz3QValETpqX7OcT1EgRxx6AR7VXqdkr0_VoxiRIUeDrmns6Kl')
	.update(oAuth2PermissionGrant);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\OAuth2PermissionGrant;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new OAuth2PermissionGrant();
$requestBody->setScope('openid profile offline_access DelegatedPermissionGrant.ReadWrite.All AccessReview.ReadWrite.All AgentIdentityBlueprint.ReadWrite.All');

$result = $graphServiceClient->oauth2PermissionGrants()->byOAuth2PermissionGrantId('oAuth2PermissionGrant-id')->patch($requestBody)->wait();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```powershell

Import-Module Microsoft.Graph.Identity.SignIns

$params = @{
	scope = "openid profile offline_access DelegatedPermissionGrant.ReadWrite.All AccessReview.ReadWrite.All AgentIdentityBlueprint.ReadWrite.All"
}

Update-MgOauth2PermissionGrant -OAuth2PermissionGrantId $oAuth2PermissionGrantId -BodyParameter $params
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.o_auth2_permission_grant import OAuth2PermissionGrant
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = OAuth2PermissionGrant(
	scope = "openid profile offline_access DelegatedPermissionGrant.ReadWrite.All AccessReview.ReadWrite.All AgentIdentityBlueprint.ReadWrite.All",
)

result = await graph_client.oauth2_permission_grants.by_o_auth2_permission_grant_id('oAuth2PermissionGrant-id').patch(request_body)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

---

## Step 3: Revoke delegated permissions granted to a service principal on behalf of a user \[optional\]

If a service principal has been granted multiple delegated permission grants on behalf of a user, you can choose to revoke either specific grants or all grants. Use this method to remove and revoke consent for the delegated permissions that you assigned to the client service principal.

- To revoke one or more grants, run a PATCH request on the oauth2PermissionGrant object and specify only the delegated permissions to retain in the **scope** parameter.
- To revoke all grants, send a DELETE request to the oauth2PermissionGrant object.

### Request

This request revokes all permission grants except the `User.Read.All` permission grant. It removes the permissions and revokes the previously granted consent.

- [HTTP](#tabpanel_9_http)
- [C#](#tabpanel_9_csharp)
- [Go](#tabpanel_9_go)
- [Java](#tabpanel_9_java)
- [JavaScript](#tabpanel_9_javascript)
- [PHP](#tabpanel_9_php)
- [PowerShell](#tabpanel_9_powershell)
- [Python](#tabpanel_9_python)

```msgraph
PATCH https://graph.microsoft.com/v1.0/oauth2PermissionGrants/47nZsM8O_UuNq5Jz3QValETpqX7OcT1EgRxx6AR7VXqdkr0_VoxiRIUeDrmns6Kl
Content-Type: application/json

{
    "scope": "User.Read.All"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new OAuth2PermissionGrant
{
	Scope = "User.Read.All",
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Oauth2PermissionGrants["{oAuth2PermissionGrant-id}"].PatchAsync(requestBody);
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

requestBody := graphmodels.NewOAuth2PermissionGrant()
scope := "User.Read.All"
requestBody.SetScope(&scope) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
oauth2PermissionGrants, err := graphClient.Oauth2PermissionGrants().ByOAuth2PermissionGrantId("oAuth2PermissionGrant-id").Patch(context.Background(), requestBody, nil)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

OAuth2PermissionGrant oAuth2PermissionGrant = new OAuth2PermissionGrant();
oAuth2PermissionGrant.setScope("User.Read.All");
OAuth2PermissionGrant result = graphClient.oauth2PermissionGrants().byOAuth2PermissionGrantId("{oAuth2PermissionGrant-id}").patch(oAuth2PermissionGrant);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const oAuth2PermissionGrant = {
    scope: 'User.Read.All'
};

await client.api('/oauth2PermissionGrants/47nZsM8O_UuNq5Jz3QValETpqX7OcT1EgRxx6AR7VXqdkr0_VoxiRIUeDrmns6Kl')
	.update(oAuth2PermissionGrant);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\OAuth2PermissionGrant;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new OAuth2PermissionGrant();
$requestBody->setScope('User.Read.All');

$result = $graphServiceClient->oauth2PermissionGrants()->byOAuth2PermissionGrantId('oAuth2PermissionGrant-id')->patch($requestBody)->wait();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```powershell

Import-Module Microsoft.Graph.Identity.SignIns

$params = @{
	scope = "User.Read.All"
}

Update-MgOauth2PermissionGrant -OAuth2PermissionGrantId $oAuth2PermissionGrantId -BodyParameter $params
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.o_auth2_permission_grant import OAuth2PermissionGrant
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = OAuth2PermissionGrant(
	scope = "User.Read.All",
)

result = await graph_client.oauth2_permission_grants.by_o_auth2_permission_grant_id('oAuth2PermissionGrant-id').patch(request_body)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

### Response

```http
HTTP/1.1 204 No Content
```

### Request

This request revokes all permission grants for a service principal on behalf of a user.

- [HTTP](#tabpanel_10_http)
- [C#](#tabpanel_10_csharp)
- [Go](#tabpanel_10_go)
- [Java](#tabpanel_10_java)
- [JavaScript](#tabpanel_10_javascript)
- [PHP](#tabpanel_10_php)
- [PowerShell](#tabpanel_10_powershell)
- [Python](#tabpanel_10_python)

```msgraph
DELETE https://graph.microsoft.com/v1.0/oauth2PermissionGrants/47nZsM8O_UuNq5Jz3QValETpqX7OcT1EgRxx6AR7VXqdkr0_VoxiRIUeDrmns6Kl
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
await graphClient.Oauth2PermissionGrants["{oAuth2PermissionGrant-id}"].DeleteAsync();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  //other-imports
)


// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
graphClient.Oauth2PermissionGrants().ByOAuth2PermissionGrantId("oAuth2PermissionGrant-id").Delete(context.Background(), nil)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

graphClient.oauth2PermissionGrants().byOAuth2PermissionGrantId("{oAuth2PermissionGrant-id}").delete();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

await client.api('/oauth2PermissionGrants/47nZsM8O_UuNq5Jz3QValETpqX7OcT1EgRxx6AR7VXqdkr0_VoxiRIUeDrmns6Kl')
	.delete();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```php

<?php
use Microsoft\Graph\GraphServiceClient;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);


$graphServiceClient->oauth2PermissionGrants()->byOAuth2PermissionGrantId('oAuth2PermissionGrant-id')->delete()->wait();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```powershell

Import-Module Microsoft.Graph.Identity.SignIns

Remove-MgOauth2PermissionGrant -OAuth2PermissionGrantId $oAuth2PermissionGrantId
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python

await graph_client.oauth2_permission_grants.by_o_auth2_permission_grant_id('oAuth2PermissionGrant-id').delete()
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

### Response

```http
HTTP/1.1 204 No Content
```

## Related content

- [Grant delegated permissions roles using PowerShell](https://learn.microsoft.com/en-us/powershell/microsoftgraph/tutorial-grant-app-only-api-permissions)
- [OAuth2PermissionGrant resource type](https://learn.microsoft.com/en-us/graph/api/resources/oauth2permissiongrant)
