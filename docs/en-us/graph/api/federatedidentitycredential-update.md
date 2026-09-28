<!-- Source: https://learn.microsoft.com/en-us/graph/api/federatedidentitycredential-update?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-03-21 -->

# Update federatedIdentityCredential

Namespace: microsoft.graph

Update the properties of a [federatedIdentityCredential](https://learn.microsoft.com/en-us/graph/api/resources/federatedidentitycredential?view=graph-rest-1.0) object assigned to an [application](https://learn.microsoft.com/en-us/graph/api/resources/application?view=graph-rest-1.0).

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Application.ReadWrite.All | Not available. |
| Delegated \(personal Microsoft account\) | Application.ReadWrite.All | Not available. |
| Application | Application.ReadWrite.OwnedBy | Application.ReadWrite.All |

Important

For delegated access using work or school accounts, the signed-in user must be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) or a custom role that grants the permissions required for this operation. This operation supports the following built-in roles, which provide only the least privilege necessary:

- A non-admin member user with default user permissions - for applications they own
- Application Developer - for applications they own
- Cloud Application Administrator
- Application Administrator

## HTTP request

You can address the application using either its **id** or **appId**. **id** and **appId** are referred to as the **Object ID** and **Application \(Client\) ID**, respectively, in app registrations in the Microsoft Entra admin center.

You can also address the federated identity credential with either its **id** or **name**.

```http
PATCH /applications/{id}/federatedIdentityCredentials/{federatedIdentityCredentialId}

PATCH /applications/{id}/federatedIdentityCredentials/{federatedIdentityCredentialName}

PATCH /applications(appId='{appId}')/federatedIdentityCredentials/{federatedIdentityCredentialId}

PATCH /applications(appId='{appId}')/federatedIdentityCredentials/{federatedIdentityCredentialName}
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
| audiences | String collection | The audience that can appear in the issued token. For Microsoft Entra ID, set its value to `api://AzureADTokenExchange`. This field can only accept a single value and has a limit of 600 characters. |
| description | String | A user-provided description of what the federatedIdentityCredential is used for. It has a limit of 600 characters. |
| issuer | String | The URL of the incoming trusted issuer \(Secure Token Service\). Matches the issuer claim of an access token. For example, with the Customer Managed Keys scenario, Microsoft Entra ID is the issuer and a valid value would be `https://login.microsoftonline.com/{tenantid}/v2.0`. The combination of the values of **issuer** and **subject** must be unique on the app. It has a limit of 600 characters. |
| subject | String | <li>For Microsoft Entra issuer, the <code>objectId</code> of the servicePrincipal (can represent a managed identity) that can impersonate the app. The object associated with this GUID needs to exist in the tenant.</li><br><br><li>For all other issuers, a string with no additional validation<br><br>The combination of the values of <strong>issuer</strong> and <strong>subject</strong> must be unique on the app. It has a limit of 600 characters.</li> |

## Response

If successful, this method returns a `204 No Content` response code.

## Examples

### Request

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [PowerShell](#tabpanel_1_powershell)
- [Python](#tabpanel_1_python)

```http
PATCH https://graph.microsoft.com/v1.0/applications/bcd7c908-1c4d-4d48-93ee-ff38349a75c8/federatedIdentityCredentials/15be77d1-1940-43fe-8aae-94a78e078da0
Content-Type: application/json

{
    "name": "testing02",
    "issuer": "https://login.microsoftonline.com/3d1e2be9-a10a-4a0c-8380-7ce190f98ed9/v2.0",
    "subject": "a7d388c3-5e3f-4959-ac7d-786b3383006a",
    "description": "Updated description",
    "audiences": [
        "api://AzureADTokenExchange"
    ]
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new FederatedIdentityCredential
{
	Name = "testing02",
	Issuer = "https://login.microsoftonline.com/3d1e2be9-a10a-4a0c-8380-7ce190f98ed9/v2.0",
	Subject = "a7d388c3-5e3f-4959-ac7d-786b3383006a",
	Description = "Updated description",
	Audiences = new List<string>
	{
		"api://AzureADTokenExchange",
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Applications["{application-id}"].FederatedIdentityCredentials["{federatedIdentityCredential-id}"].PatchAsync(requestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphmodels "github.com/microsoftgraph/msgraph-sdk-go/models"
	  //other-imports
)

requestBody := graphmodels.NewFederatedIdentityCredential()
name := "testing02"
requestBody.SetName(&name) 
issuer := "https://login.microsoftonline.com/3d1e2be9-a10a-4a0c-8380-7ce190f98ed9/v2.0"
requestBody.SetIssuer(&issuer) 
subject := "a7d388c3-5e3f-4959-ac7d-786b3383006a"
requestBody.SetSubject(&subject) 
description := "Updated description"
requestBody.SetDescription(&description) 
audiences := []string {
	"api://AzureADTokenExchange",
}
requestBody.SetAudiences(audiences)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
federatedIdentityCredentials, err := graphClient.Applications().ByApplicationId("application-id").FederatedIdentityCredentials().ByFederatedIdentityCredentialId("federatedIdentityCredential-id").Patch(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

FederatedIdentityCredential federatedIdentityCredential = new FederatedIdentityCredential();
federatedIdentityCredential.setName("testing02");
federatedIdentityCredential.setIssuer("https://login.microsoftonline.com/3d1e2be9-a10a-4a0c-8380-7ce190f98ed9/v2.0");
federatedIdentityCredential.setSubject("a7d388c3-5e3f-4959-ac7d-786b3383006a");
federatedIdentityCredential.setDescription("Updated description");
LinkedList<String> audiences = new LinkedList<String>();
audiences.add("api://AzureADTokenExchange");
federatedIdentityCredential.setAudiences(audiences);
FederatedIdentityCredential result = graphClient.applications().byApplicationId("{application-id}").federatedIdentityCredentials().byFederatedIdentityCredentialId("{federatedIdentityCredential-id}").patch(federatedIdentityCredential);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const federatedIdentityCredential = {
    name: 'testing02',
    issuer: 'https://login.microsoftonline.com/3d1e2be9-a10a-4a0c-8380-7ce190f98ed9/v2.0',
    subject: 'a7d388c3-5e3f-4959-ac7d-786b3383006a',
    description: 'Updated description',
    audiences: [
        'api://AzureADTokenExchange'
    ]
};

await client.api('/applications/bcd7c908-1c4d-4d48-93ee-ff38349a75c8/federatedIdentityCredentials/15be77d1-1940-43fe-8aae-94a78e078da0')
	.update(federatedIdentityCredential);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\FederatedIdentityCredential;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new FederatedIdentityCredential();
$requestBody->setName('testing02');
$requestBody->setIssuer('https://login.microsoftonline.com/3d1e2be9-a10a-4a0c-8380-7ce190f98ed9/v2.0');
$requestBody->setSubject('a7d388c3-5e3f-4959-ac7d-786b3383006a');
$requestBody->setDescription('Updated description');
$requestBody->setAudiences(['api://AzureADTokenExchange', 	]);

$result = $graphServiceClient->applications()->byApplicationId('application-id')->federatedIdentityCredentials()->byFederatedIdentityCredentialId('federatedIdentityCredential-id')->patch($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Applications

$params = @{
	name = "testing02"
	issuer = "https://login.microsoftonline.com/3d1e2be9-a10a-4a0c-8380-7ce190f98ed9/v2.0"
	subject = "a7d388c3-5e3f-4959-ac7d-786b3383006a"
	description = "Updated description"
	audiences = @(
	"api://AzureADTokenExchange"
)
}

Update-MgApplicationFederatedIdentityCredential -ApplicationId $applicationId -FederatedIdentityCredentialId $federatedIdentityCredentialId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.federated_identity_credential import FederatedIdentityCredential
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = FederatedIdentityCredential(
	name = "testing02",
	issuer = "https://login.microsoftonline.com/3d1e2be9-a10a-4a0c-8380-7ce190f98ed9/v2.0",
	subject = "a7d388c3-5e3f-4959-ac7d-786b3383006a",
	description = "Updated description",
	audiences = [
		"api://AzureADTokenExchange",
	],
)

result = await graph_client.applications.by_application_id('application-id').federated_identity_credentials.by_federated_identity_credential_id('federatedIdentityCredential-id').patch(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

```http
HTTP/1.1 204 No Content
```
