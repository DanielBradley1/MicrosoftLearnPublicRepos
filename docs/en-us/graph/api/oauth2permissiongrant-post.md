<!-- Source: https://learn.microsoft.com/en-us/graph/api/oauth2permissiongrant-post?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-23 -->

# Create oAuth2PermissionGrant \(a delegated permission grant\)

Namespace: microsoft.graph

Create a delegated permission grant represented by an [oAuth2PermissionGrant](https://learn.microsoft.com/en-us/graph/api/resources/oauth2permissiongrant?view=graph-rest-1.0) object.

A delegated permission grant authorizes a client service principal \(representing a client application\) to access a resource service principal \(representing an API\), on behalf of a signed-in user, for the level of access limited by the delegated permissions which were granted.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | DelegatedPermissionGrant.ReadWrite.All | Directory.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | DelegatedPermissionGrant.ReadWrite.All | Directory.ReadWrite.All |

Important

For delegated access using work or school accounts, the signed-in user must be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) or a custom role that grants the permissions required for this operation. This operation supports the following built-in roles, which provide only the least privilege necessary:

- Application Administrator
- Application Developer
- Cloud Application Administrator
- Directory Writers
- Privileged Role Administrator
- User Administrator

## HTTP request

```http
POST /oauth2PermissionGrants
```

## Request headers

| Name | Type | Description |
| :--- | :--- | :--- |
| Authorization | string | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

In the request body, supply a JSON representation of an [oAuth2PermissionGrant](https://learn.microsoft.com/en-us/graph/api/resources/oauth2permissiongrant?view=graph-rest-1.0) object.

## Response

If successful, this method returns a 200-series response code and a new [oAuth2PermissionGrant](https://learn.microsoft.com/en-us/graph/api/resources/oauth2permissiongrant?view=graph-rest-1.0) object in the response body. The following table lists the properties that are required when you create the [oAuth2PermissionGrant](https://learn.microsoft.com/en-us/graph/api/resources/oauth2permissiongrant?view=graph-rest-1.0).

| Property | Type | Description |
| :--- | :--- | :--- |
| clientId | String | The object **id** \(*not* **appId**\) of the client [service principal](https://learn.microsoft.com/en-us/graph/api/resources/serviceprincipal?view=graph-rest-1.0) for the application which is authorized to act on behalf of a signed-in user when accessing an API. Required. |
| consentType | String | Indicates whether authorization is granted for the client application to impersonate all users or only a specific user. *AllPrincipals* indicates authorization to impersonate all users. *Principal* indicates authorization to impersonate a specific user. Consent on behalf of all users can be granted by an administrator. Non-admin users may be authorized to consent on behalf of themselves in some cases, for some delegated permissions. Required. |
| principalId | String | The **id** of the [user](https://learn.microsoft.com/en-us/graph/api/resources/user?view=graph-rest-1.0) on behalf of whom the client is authorized to access the resource, when **consentType** is *Principal*. If **consentType** is *AllPrincipals* this value is null. Required when **consentType** is *Principal*. |
| resourceId | String | The **id** of the resource [service principal](https://learn.microsoft.com/en-us/graph/api/resources/serviceprincipal?view=graph-rest-1.0) to which access is authorized. This identifies the API which the client is authorized to attempt to call on behalf of a signed-in user. |
| scope | String | A space-separated list of the claim values for delegated permissions which should be included in access tokens for the resource application \(the API\). For example, `openid User.Read GroupMember.Read.All`. Each claim value should match the **value** field of one of the delegated permissions defined by the API, listed in the **oauth2PermissionScopes** property of the resource [service principal](https://learn.microsoft.com/en-us/graph/api/resources/serviceprincipal?view=graph-rest-1.0). Must not exceed 3850 characters in length. |

## Example

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
POST https://graph.microsoft.com/v1.0/oauth2PermissionGrants
Content-Type: application/json

{
    "clientId": "ef969797-201d-4f6b-960c-e9ed5f31dab5",
    "consentType": "AllPrincipals",
    "resourceId": "943603e4-e787-4fe9-93d1-e30f749aae39",
    "scope": "DelegatedPermissionGrant.ReadWrite.All"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new OAuth2PermissionGrant
{
	ClientId = "ef969797-201d-4f6b-960c-e9ed5f31dab5",
	ConsentType = "AllPrincipals",
	ResourceId = "943603e4-e787-4fe9-93d1-e30f749aae39",
	Scope = "DelegatedPermissionGrant.ReadWrite.All",
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Oauth2PermissionGrants.PostAsync(requestBody);
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

requestBody := graphmodels.NewOAuth2PermissionGrant()
clientId := "ef969797-201d-4f6b-960c-e9ed5f31dab5"
requestBody.SetClientId(&clientId) 
consentType := "AllPrincipals"
requestBody.SetConsentType(&consentType) 
resourceId := "943603e4-e787-4fe9-93d1-e30f749aae39"
requestBody.SetResourceId(&resourceId) 
scope := "DelegatedPermissionGrant.ReadWrite.All"
requestBody.SetScope(&scope) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
oauth2PermissionGrants, err := graphClient.Oauth2PermissionGrants().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

OAuth2PermissionGrant oAuth2PermissionGrant = new OAuth2PermissionGrant();
oAuth2PermissionGrant.setClientId("ef969797-201d-4f6b-960c-e9ed5f31dab5");
oAuth2PermissionGrant.setConsentType("AllPrincipals");
oAuth2PermissionGrant.setResourceId("943603e4-e787-4fe9-93d1-e30f749aae39");
oAuth2PermissionGrant.setScope("DelegatedPermissionGrant.ReadWrite.All");
OAuth2PermissionGrant result = graphClient.oauth2PermissionGrants().post(oAuth2PermissionGrant);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const oAuth2PermissionGrant = {
    clientId: 'ef969797-201d-4f6b-960c-e9ed5f31dab5',
    consentType: 'AllPrincipals',
    resourceId: '943603e4-e787-4fe9-93d1-e30f749aae39',
    scope: 'DelegatedPermissionGrant.ReadWrite.All'
};

await client.api('/oauth2PermissionGrants')
	.post(oAuth2PermissionGrant);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\OAuth2PermissionGrant;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new OAuth2PermissionGrant();
$requestBody->setClientId('ef969797-201d-4f6b-960c-e9ed5f31dab5');
$requestBody->setConsentType('AllPrincipals');
$requestBody->setResourceId('943603e4-e787-4fe9-93d1-e30f749aae39');
$requestBody->setScope('DelegatedPermissionGrant.ReadWrite.All');

$result = $graphServiceClient->oauth2PermissionGrants()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Identity.SignIns

$params = @{
	clientId = "ef969797-201d-4f6b-960c-e9ed5f31dab5"
	consentType = "AllPrincipals"
	resourceId = "943603e4-e787-4fe9-93d1-e30f749aae39"
	scope = "DelegatedPermissionGrant.ReadWrite.All"
}

New-MgOauth2PermissionGrant -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.o_auth2_permission_grant import OAuth2PermissionGrant
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = OAuth2PermissionGrant(
	client_id = "ef969797-201d-4f6b-960c-e9ed5f31dab5",
	consent_type = "AllPrincipals",
	resource_id = "943603e4-e787-4fe9-93d1-e30f749aae39",
	scope = "DelegatedPermissionGrant.ReadWrite.All",
)

result = await graph_client.oauth2_permission_grants.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

```http
HTTP/1.1 201 Created
Content-Type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#oauth2PermissionGrants/$entity",
    "clientId": "ef969797-201d-4f6b-960c-e9ed5f31dab5",
    "consentType": "AllPrincipals",
    "id": "l5eW7x0ga0-WDOntXzHateQDNpSH5-lPk9HjD3Sarjk",
    "principalId": null,
    "resourceId": "943603e4-e787-4fe9-93d1-e30f749aae39",
    "scope": "DelegatedPermissionGrant.ReadWrite.All"
}
```
