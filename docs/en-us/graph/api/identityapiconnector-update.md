<!-- Source: https://learn.microsoft.com/en-us/graph/api/identityapiconnector-update?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-11-08 -->

# Update identityApiConnector

Namespace: microsoft.graph

Update the properties of an [identityApiConnector](https://learn.microsoft.com/en-us/graph/api/resources/identityapiconnector?view=graph-rest-1.0) object.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ✅ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | APIConnectors.ReadWrite.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | APIConnectors.ReadWrite.All | Not available. |

Important

For delegated access using work or school accounts, the signed-in user must be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) or a custom role that grants the permissions required for this operation. *External ID User Flow Administrator* is the least privileged role supported for this operation.

## HTTP request

```http
PATCH /identity/apiConnectors/{identityApiConnectorId}
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the [identityApiConnector](https://learn.microsoft.com/en-us/graph/api/resources/identityapiconnector?view=graph-rest-1.0) object.

The following table shows the properties of the [identityApiConnector](https://learn.microsoft.com/en-us/graph/api/resources/identityapiconnector?view=graph-rest-1.0) that can be updated.

| Property | Type | Description |
| :--- | :--- | :--- |
| displayName | String | The name of the API connector. |
| targetUrl | String | The URL of the API endpoint to call. |
| authenticationConfiguration | [apiAuthenticationConfigurationBase](https://learn.microsoft.com/en-us/graph/api/resources/apiauthenticationconfigurationbase?view=graph-rest-1.0) | The object which describes the authentication configuration details for calling the API. Only [Basic authentication](https://learn.microsoft.com/en-us/graph/api/resources/basicauthentication?view=graph-rest-1.0) and [PKCS 12 client certificate](https://learn.microsoft.com/en-us/graph/api/resources/pkcs12certificate?view=graph-rest-1.0) are supported. |

## Response

If successful, this method returns a `204 No Content` response code.

## Examples

### Example 1: Changing display name, targetUrl, and username & password used for basic authentication

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
PATCH https://graph.microsoft.com/v1.0/identity/apiConnectors/{identityApiConnectorId}
Content-Type: application/json

{
  "displayName": "New Test API",
  "targetUrl": "https://otherapi.com/api/endpoint",
  "authenticationConfiguration": {
    "@odata.type": "microsoft.graph.basicAuthentication",
    "username":"<NEW_USERNAME>", 
    "password":"<NEW_PASSWORD>"
  }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new IdentityApiConnector
{
	DisplayName = "New Test API",
	TargetUrl = "https://otherapi.com/api/endpoint",
	AuthenticationConfiguration = new BasicAuthentication
	{
		OdataType = "microsoft.graph.basicAuthentication",
		Username = "<NEW_USERNAME>",
		Password = "<NEW_PASSWORD>",
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Identity.ApiConnectors["{identityApiConnector-id}"].PatchAsync(requestBody);
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

requestBody := graphmodels.NewIdentityApiConnector()
displayName := "New Test API"
requestBody.SetDisplayName(&displayName) 
targetUrl := "https://otherapi.com/api/endpoint"
requestBody.SetTargetUrl(&targetUrl) 
authenticationConfiguration := graphmodels.NewBasicAuthentication()
username := "<NEW_USERNAME>"
authenticationConfiguration.SetUsername(&username) 
password := "<NEW_PASSWORD>"
authenticationConfiguration.SetPassword(&password) 
requestBody.SetAuthenticationConfiguration(authenticationConfiguration)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
apiConnectors, err := graphClient.Identity().ApiConnectors().ByIdentityApiConnectorId("identityApiConnector-id").Patch(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

IdentityApiConnector identityApiConnector = new IdentityApiConnector();
identityApiConnector.setDisplayName("New Test API");
identityApiConnector.setTargetUrl("https://otherapi.com/api/endpoint");
BasicAuthentication authenticationConfiguration = new BasicAuthentication();
authenticationConfiguration.setOdataType("microsoft.graph.basicAuthentication");
authenticationConfiguration.setUsername("<NEW_USERNAME>");
authenticationConfiguration.setPassword("<NEW_PASSWORD>");
identityApiConnector.setAuthenticationConfiguration(authenticationConfiguration);
IdentityApiConnector result = graphClient.identity().apiConnectors().byIdentityApiConnectorId("{identityApiConnector-id}").patch(identityApiConnector);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const identityApiConnector = {
  displayName: 'New Test API',
  targetUrl: 'https://otherapi.com/api/endpoint',
  authenticationConfiguration: {
    '@odata.type': 'microsoft.graph.basicAuthentication',
    username: '<NEW_USERNAME>', 
    password: '<NEW_PASSWORD>'
  }
};

await client.api('/identity/apiConnectors/{identityApiConnectorId}')
	.update(identityApiConnector);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\IdentityApiConnector;
use Microsoft\Graph\Generated\Models\BasicAuthentication;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new IdentityApiConnector();
$requestBody->setDisplayName('New Test API');
$requestBody->setTargetUrl('https://otherapi.com/api/endpoint');
$authenticationConfiguration = new BasicAuthentication();
$authenticationConfiguration->setOdataType('microsoft.graph.basicAuthentication');
$authenticationConfiguration->setUsername('<NEW_USERNAME>');
$authenticationConfiguration->setPassword('<NEW_PASSWORD>');
$requestBody->setAuthenticationConfiguration($authenticationConfiguration);

$result = $graphServiceClient->identity()->apiConnectors()->byIdentityApiConnectorId('identityApiConnector-id')->patch($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Identity.SignIns

$params = @{
	displayName = "New Test API"
	targetUrl = "https://otherapi.com/api/endpoint"
	authenticationConfiguration = @{
		"@odata.type" = "microsoft.graph.basicAuthentication"
		username = "<NEW_USERNAME>"
		password = "<NEW_PASSWORD>"
	}
}

Update-MgIdentityApiConnector -IdentityApiConnectorId $identityApiConnectorId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.identity_api_connector import IdentityApiConnector
from msgraph.generated.models.basic_authentication import BasicAuthentication
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = IdentityApiConnector(
	display_name = "New Test API",
	target_url = "https://otherapi.com/api/endpoint",
	authentication_configuration = BasicAuthentication(
		odata_type = "microsoft.graph.basicAuthentication",
		username = "<NEW_USERNAME>",
		password = "<NEW_PASSWORD>",
	),
)

result = await graph_client.identity.api_connectors.by_identity_api_connector_id('identityApiConnector-id').patch(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

```http
HTTP/1.1 204 No Content
```

### Example 2: Changing API connector to use client certificate authentication

This will overwrite any previous authenticationConfiguration settings. To change from Basic authentication to certificate authentication, use this. To add additional certificates to list of certificates, use the [Upload client certificate](https://learn.microsoft.com/en-us/graph/api/identityapiconnector-uploadclientcertificate?view=graph-rest-1.0) method. When using this method, consequent "Get" or "List" operations of API connectors, `authenticationConfiguration` will be of type [microsoft.graph.clientCertificateAuthentication](https://learn.microsoft.com/en-us/graph/api/resources/clientcertificateauthentication?view=graph-rest-1.0).

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
PATCH https://graph.microsoft.com/v1.0/identity/apiConnectors/be1f769b-9b13-437e-b540-79a905c4932c
Content-Type: application/json

{
  "authenticationConfiguration": {
    "@odata.type": "#microsoft.graph.pkcs12Certificate",
    "pkcs12Value": "eyJhbGciOiJSU0EtT0FFUCIsImVuYyI6IkEyNTZHQ00ifQ...kDJ04sJShkkgjL9Bm49plA",
    "password": "secret"
  }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new IdentityApiConnector
{
	AuthenticationConfiguration = new Pkcs12Certificate
	{
		OdataType = "#microsoft.graph.pkcs12Certificate",
		Pkcs12Value = "eyJhbGciOiJSU0EtT0FFUCIsImVuYyI6IkEyNTZHQ00ifQ...kDJ04sJShkkgjL9Bm49plA",
		Password = "secret",
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Identity.ApiConnectors["{identityApiConnector-id}"].PatchAsync(requestBody);
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

requestBody := graphmodels.NewIdentityApiConnector()
authenticationConfiguration := graphmodels.NewPkcs12Certificate()
pkcs12Value := "eyJhbGciOiJSU0EtT0FFUCIsImVuYyI6IkEyNTZHQ00ifQ...kDJ04sJShkkgjL9Bm49plA"
authenticationConfiguration.SetPkcs12Value(&pkcs12Value) 
password := "secret"
authenticationConfiguration.SetPassword(&password) 
requestBody.SetAuthenticationConfiguration(authenticationConfiguration)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
apiConnectors, err := graphClient.Identity().ApiConnectors().ByIdentityApiConnectorId("identityApiConnector-id").Patch(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

IdentityApiConnector identityApiConnector = new IdentityApiConnector();
Pkcs12Certificate authenticationConfiguration = new Pkcs12Certificate();
authenticationConfiguration.setOdataType("#microsoft.graph.pkcs12Certificate");
authenticationConfiguration.setPkcs12Value("eyJhbGciOiJSU0EtT0FFUCIsImVuYyI6IkEyNTZHQ00ifQ...kDJ04sJShkkgjL9Bm49plA");
authenticationConfiguration.setPassword("secret");
identityApiConnector.setAuthenticationConfiguration(authenticationConfiguration);
IdentityApiConnector result = graphClient.identity().apiConnectors().byIdentityApiConnectorId("{identityApiConnector-id}").patch(identityApiConnector);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const identityApiConnector = {
  authenticationConfiguration: {
    '@odata.type': '#microsoft.graph.pkcs12Certificate',
    pkcs12Value: 'eyJhbGciOiJSU0EtT0FFUCIsImVuYyI6IkEyNTZHQ00ifQ...kDJ04sJShkkgjL9Bm49plA',
    password: 'secret'
  }
};

await client.api('/identity/apiConnectors/be1f769b-9b13-437e-b540-79a905c4932c')
	.update(identityApiConnector);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\IdentityApiConnector;
use Microsoft\Graph\Generated\Models\Pkcs12Certificate;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new IdentityApiConnector();
$authenticationConfiguration = new Pkcs12Certificate();
$authenticationConfiguration->setOdataType('#microsoft.graph.pkcs12Certificate');
$authenticationConfiguration->setPkcs12Value('eyJhbGciOiJSU0EtT0FFUCIsImVuYyI6IkEyNTZHQ00ifQ...kDJ04sJShkkgjL9Bm49plA');
$authenticationConfiguration->setPassword('secret');
$requestBody->setAuthenticationConfiguration($authenticationConfiguration);

$result = $graphServiceClient->identity()->apiConnectors()->byIdentityApiConnectorId('identityApiConnector-id')->patch($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Identity.SignIns

$params = @{
	authenticationConfiguration = @{
		"@odata.type" = "#microsoft.graph.pkcs12Certificate"
		pkcs12Value = "eyJhbGciOiJSU0EtT0FFUCIsImVuYyI6IkEyNTZHQ00ifQ...kDJ04sJShkkgjL9Bm49plA"
		password = "secret"
	}
}

Update-MgIdentityApiConnector -IdentityApiConnectorId $identityApiConnectorId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.identity_api_connector import IdentityApiConnector
from msgraph.generated.models.pkcs12_certificate import Pkcs12Certificate
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = IdentityApiConnector(
	authentication_configuration = Pkcs12Certificate(
		odata_type = "#microsoft.graph.pkcs12Certificate",
		pkcs12_value = "eyJhbGciOiJSU0EtT0FFUCIsImVuYyI6IkEyNTZHQ00ifQ...kDJ04sJShkkgjL9Bm49plA",
		password = "secret",
	),
)

result = await graph_client.identity.api_connectors.by_identity_api_connector_id('identityApiConnector-id').patch(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

```http
HTTP/1.1 204 No Content
```
