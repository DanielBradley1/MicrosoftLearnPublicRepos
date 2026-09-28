<!-- Source: https://learn.microsoft.com/en-us/graph/api/security-identitycontainer-list-identityaccounts?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-03-21 -->

# List identityAccounts objects

Namespace: microsoft.graph.security

Get a list of the [identityAccounts](https://learn.microsoft.com/en-us/graph/api/resources/security-identityaccounts?view=graph-rest-1.0) objects and their properties.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

One of the following permissions is required to call this API. Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | SecurityIdentitiesAccount.Read.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | SecurityIdentitiesAccount.Read.All | Not available. |

Important

For delegated access using work or school accounts, the signed-in user must be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) or a custom role that grants the permissions required for this operation. *Security Administrator* is the least privileged role supported for this operation.

## HTTP request

```http
GET /security/identities/identityAccounts
```

## Optional query parameters

This method supports the `$filter` and `$select` OData query parameters to help customize the response. For more information, see [OData query parameters](https://learn.microsoft.com/en-us/graph/query-parameters).

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and a collection of [identityAccounts](https://learn.microsoft.com/en-us/graph/api/resources/security-identityaccounts?view=graph-rest-1.0) objects in the response body.

## Examples

### Example 1: Retrieve details of identity accounts

#### Request

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
GET https://graph.microsoft.com/v1.0/security/identities/identityAccounts
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Security.Identities.IdentityAccounts.GetAsync();
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
identityAccounts, err := graphClient.Security().Identities().IdentityAccounts().Get(context.Background(), nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.models.security.IdentityAccountsCollectionResponse result = graphClient.security().identities().identityAccounts().get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let identityAccounts = await client.api('/security/identities/identityAccounts')
	.get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);


$result = $graphServiceClient->security()->identities()->identityAccounts()->get()->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Security

Get-MgSecurityIdentityAccount
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python

result = await graph_client.security.identities.identity_accounts.get()
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "value": [
    {
      "id": "00104216-0539-4838-88b1-55baafdc296b",
      "displayName": "accoundJon",
      "domain": "domain1.test.local",
      "onPremisesSecurityIdentifier": "S-1-5-21-989687458-3461180213-172365591-281652",
      "cloudSecurityIdentifier": "S-1-12-4-2492432728-1225839317-3974870967-847981844",
      "isEnabled": true,
      "accounts": [
        {
          "provider": "ActiveDirectory",
          "identifier": "256db173-930a-4991-9061-0d51a9a93ba5",
          "actions": []
        },
        {
          "provider": "EntraID",
          "identifier": "69dfa3ea-1295-4e2c-b469-59564581143d",
          "actions": []
        },
        {
          "provider": "Okta",
          "identifier": "878a6911-f3da-41eb-a895-1d46fa054d3e",
          "actions": []
        }
      ]
    },
    {
      "id": "00054217-0539-4838-88b1-55baafdc296b",
      "displayName": "account",
      "domain": "domain1.test.local",
      "onPremisesSecurityIdentifier": "S-1-5-21-989687458-3461180213-172365591-391652",
      "cloudSecurityIdentifier": "S-1-12-4-2492432728-1225839317-3974870967-847981844",
      "isEnabled": true,
      "accounts": [
        {
          "provider": "Okta",
          "identifier": "878a6911-f3da-41eb-a895-1d46fa054d3e",
          "actions": []
        }
      ]
    }
  ]
}
```

### Example 2: Retrieve details of identity accounts that match a security identifier

#### Request

The following example shows a request.

- [HTTP](#tabpanel_2_http)
- [C#](#tabpanel_2_csharp)
- [Go](#tabpanel_2_go)
- [Java](#tabpanel_2_java)
- [JavaScript](#tabpanel_2_javascript)
- [PHP](#tabpanel_2_php)
- [PowerShell](#tabpanel_2_powershell)
- [Python](#tabpanel_2_python)

```http
GET https://graph.microsoft.com/v1.0/security/identities/identityAccounts?$filter=onPremisesSecurityIdentifier eq 'S-1-5-21-989687458-3461180213-172365591-281652'
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Security.Identities.IdentityAccounts.GetAsync((requestConfiguration) =>
{
	requestConfiguration.QueryParameters.Filter = "onPremisesSecurityIdentifier eq 'S-1-5-21-989687458-3461180213-172365591-281652'";
});
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphsecurity "github.com/microsoftgraph/msgraph-sdk-go/security"
	  //other-imports
)


requestFilter := "onPremisesSecurityIdentifier eq 'S-1-5-21-989687458-3461180213-172365591-281652'"

requestParameters := &graphsecurity.IdentitiesIdentityAccountsRequestBuilderGetQueryParameters{
	Filter: &requestFilter,
}
configuration := &graphsecurity.IdentitiesIdentityAccountsRequestBuilderGetRequestConfiguration{
	QueryParameters: requestParameters,
}

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
identityAccounts, err := graphClient.Security().Identities().IdentityAccounts().Get(context.Background(), configuration)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.models.security.IdentityAccountsCollectionResponse result = graphClient.security().identities().identityAccounts().get(requestConfiguration -> {
	requestConfiguration.queryParameters.filter = "onPremisesSecurityIdentifier eq 'S-1-5-21-989687458-3461180213-172365591-281652'";
});
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let identityAccounts = await client.api('/security/identities/identityAccounts')
	.filter('onPremisesSecurityIdentifier eq \'S-1-5-21-989687458-3461180213-172365591-281652\'')
	.get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Security\Identities\IdentityAccounts\IdentityAccountsRequestBuilderGetRequestConfiguration;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestConfiguration = new IdentityAccountsRequestBuilderGetRequestConfiguration();
$queryParameters = IdentityAccountsRequestBuilderGetRequestConfiguration::createQueryParameters();
$queryParameters->filter = "onPremisesSecurityIdentifier eq 'S-1-5-21-989687458-3461180213-172365591-281652'";
$requestConfiguration->queryParameters = $queryParameters;


$result = $graphServiceClient->security()->identities()->identityAccounts()->get($requestConfiguration)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Security

Get-MgSecurityIdentityAccount -Filter "onPremisesSecurityIdentifier eq 'S-1-5-21-989687458-3461180213-172365591-281652'" 
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.security.identities.identity_accounts.identity_accounts_request_builder import IdentityAccountsRequestBuilder
from kiota_abstractions.base_request_configuration import RequestConfiguration
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
query_params = IdentityAccountsRequestBuilder.IdentityAccountsRequestBuilderGetQueryParameters(
		filter = "onPremisesSecurityIdentifier eq 'S-1-5-21-989687458-3461180213-172365591-281652'",
)

request_configuration = RequestConfiguration(
query_parameters = query_params,
)

result = await graph_client.security.identities.identity_accounts.get(request_configuration = request_configuration)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "value": [
    {
      "id": "00104216-0539-4838-88b1-55baafdc296b",
      "displayName": "accoundJon",
      "domain": "domain1.test.local",
      "onPremisesSecurityIdentifier": "S-1-5-21-989687458-3461180213-172365591-281652",
      "cloudSecurityIdentifier": "S-1-12-4-2492432728-1225839317-3974870967-847981844",
      "isEnabled": true,
      "accounts": [
        {
          "provider": "ActiveDirectory",
          "identifier": "256db173-930a-4991-9061-0d51a9a93ba5",
          "actions": []
        },
        {
          "provider": "EntraID",
          "identifier": "69dfa3ea-1295-4e2c-b469-59564581143d",
          "actions": []
        },
        {
          "provider": "Okta",
          "identifier": "878a6911-f3da-41eb-a895-1d46fa054d3e",
          "actions": []
        }
      ]
    }
  ]
}
```
