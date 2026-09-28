<!-- Source: https://learn.microsoft.com/en-us/graph/api/riskpreventioncontainer-post-webapplicationfirewallproviders?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-03-21 -->

# Create webApplicationFirewallProvider

Namespace: microsoft.graph

Create a new [webApplicationFirewallProvider](https://learn.microsoft.com/en-us/graph/api/resources/webapplicationfirewallprovider?view=graph-rest-1.0) object. You can create one of the following subtypes that are derived from **webApplicationFirewallProvider**.

- [akamaiWebApplicationFirewallProvider](https://learn.microsoft.com/en-us/graph/api/resources/akamaiwebapplicationfirewallprovider?view=graph-rest-1.0)
- [cloudFlareWebApplicationFirewallProvider](https://learn.microsoft.com/en-us/graph/api/resources/cloudflarewebapplicationfirewallprovider?view=graph-rest-1.0)

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | RiskPreventionProviders.ReadWrite.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Not supported. | Not supported. |

Important

For delegated access using work or school accounts, the admin must be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) or a custom role that grants the permissions required for this operation. This operation supports the following built-in roles, which provide only the least privilege necessary:

- External ID User Flow Administrator
- Application Administrator
- Security Administrator

## HTTP request

```http
POST /identity/riskPrevention/webApplicationFirewallProviders
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the [webApplicationFirewallProvider](https://learn.microsoft.com/en-us/graph/api/resources/webapplicationfirewallprovider?view=graph-rest-1.0) object.

You can specify the following properties when creating a **webApplicationFirewallProvider**. You must specify the **@odata.type** property to specify the type of **webApplicationFirewallProvider** to create; for example, `@odata.type": "microsoft.graph.AkamaiWebApplicationFirewallProvider"`.

| Property | Type | Description |
| :--- | :--- | :--- |
| displayName | String | The display name of this WAF provider configuration. Supported for all providers. Required. Inherited from [webApplicationFirewallProvider](https://learn.microsoft.com/en-us/graph/api/resources/webapplicationfirewallprovider?view=graph-rest-1.0). |
| accessToken | String | Akamai API access token used to authenticate to the Akamai account. Contact your Akamai Customer Success Manager for assistance with your accessToken. Supported for Akamai only. Required. |
| clientSecret | String | Akamai API client secret used in conjunction with the client token and access token for authentication. Contact your Akamai Customer Success Manager for assistance with this information. Supported for Akamai only. Required. |
| clientToken | String | Akamai API client token used for authentication to the Akamai account. Contact your Akamai Customer Success Manager for assistance with this information. Supported for Akamai only. Required. |
| hostPrefix | String | Prefix used to identify the host or domain in Akamai configuration operations. This value may be required for certain API calls or configuration scenarios. Supported for Akamai only. Required. |
| apiToken | String | Cloudflare API token or credential used by Microsoft services to authenticate to the Cloudflare account. Contact your Cloudflare Customer Success Manager for assistance with your apitoken. Supported for Cloudflare only. Required. |
| zoneId | String | Default Cloudflare Zone ID associated with this provider configuration. This ID identifies the DNS zone in Cloudflare that is commonly used for verification and configuration operations for the provider. Supported for Cloudflare only. Required. |

## Response

If successful, this method returns a `201 Created` response code and a [webApplicationFirewallProvider](https://learn.microsoft.com/en-us/graph/api/resources/webapplicationfirewallprovider?view=graph-rest-1.0) object in the response body.

## Examples

### Example 1: Create a new AkamaiWebApplicationFirewallProvider object

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
POST https://graph.microsoft.com/v1.0/identity/riskPrevention/webApplicationFirewallProviders
Content-Type: application/json

{
    "@odata.type": "#microsoft.graph.akamaiWebApplicationFirewallProvider",
    "displayName": "Akamai Provider Example",
    "hostPrefix": "akab-exampleprefix",
    "clientSecret": "akamai_example_secret_123",
    "clientToken": "akamai_example_token_456",
    "accessToken": "akamai_example_token_789"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new AkamaiWebApplicationFirewallProvider
{
	OdataType = "#microsoft.graph.akamaiWebApplicationFirewallProvider",
	DisplayName = "Akamai Provider Example",
	HostPrefix = "akab-exampleprefix",
	ClientSecret = "akamai_example_secret_123",
	ClientToken = "akamai_example_token_456",
	AccessToken = "akamai_example_token_789",
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Identity.RiskPrevention.WebApplicationFirewallProviders.PostAsync(requestBody);
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

requestBody := graphmodels.NewWebApplicationFirewallProvider()
displayName := "Akamai Provider Example"
requestBody.SetDisplayName(&displayName) 
hostPrefix := "akab-exampleprefix"
requestBody.SetHostPrefix(&hostPrefix) 
clientSecret := "akamai_example_secret_123"
requestBody.SetClientSecret(&clientSecret) 
clientToken := "akamai_example_token_456"
requestBody.SetClientToken(&clientToken) 
accessToken := "akamai_example_token_789"
requestBody.SetAccessToken(&accessToken) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
webApplicationFirewallProviders, err := graphClient.Identity().RiskPrevention().WebApplicationFirewallProviders().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

AkamaiWebApplicationFirewallProvider webApplicationFirewallProvider = new AkamaiWebApplicationFirewallProvider();
webApplicationFirewallProvider.setOdataType("#microsoft.graph.akamaiWebApplicationFirewallProvider");
webApplicationFirewallProvider.setDisplayName("Akamai Provider Example");
webApplicationFirewallProvider.setHostPrefix("akab-exampleprefix");
webApplicationFirewallProvider.setClientSecret("akamai_example_secret_123");
webApplicationFirewallProvider.setClientToken("akamai_example_token_456");
webApplicationFirewallProvider.setAccessToken("akamai_example_token_789");
WebApplicationFirewallProvider result = graphClient.identity().riskPrevention().webApplicationFirewallProviders().post(webApplicationFirewallProvider);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const webApplicationFirewallProvider = {
    '@odata.type': '#microsoft.graph.akamaiWebApplicationFirewallProvider',
    displayName: 'Akamai Provider Example',
    hostPrefix: 'akab-exampleprefix',
    clientSecret: 'akamai_example_secret_123',
    clientToken: 'akamai_example_token_456',
    accessToken: 'akamai_example_token_789'
};

await client.api('/identity/riskPrevention/webApplicationFirewallProviders')
	.post(webApplicationFirewallProvider);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\AkamaiWebApplicationFirewallProvider;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new AkamaiWebApplicationFirewallProvider();
$requestBody->setOdataType('#microsoft.graph.akamaiWebApplicationFirewallProvider');
$requestBody->setDisplayName('Akamai Provider Example');
$requestBody->setHostPrefix('akab-exampleprefix');
$requestBody->setClientSecret('akamai_example_secret_123');
$requestBody->setClientToken('akamai_example_token_456');
$requestBody->setAccessToken('akamai_example_token_789');

$result = $graphServiceClient->identity()->riskPrevention()->webApplicationFirewallProviders()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Identity.SignIns

$params = @{
	"@odata.type" = "#microsoft.graph.akamaiWebApplicationFirewallProvider"
	displayName = "Akamai Provider Example"
	hostPrefix = "akab-exampleprefix"
	clientSecret = "akamai_example_secret_123"
	clientToken = "akamai_example_token_456"
	accessToken = "akamai_example_token_789"
}

New-MgIdentityRiskPreventionWebApplicationFirewallProvider -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.akamai_web_application_firewall_provider import AkamaiWebApplicationFirewallProvider
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = AkamaiWebApplicationFirewallProvider(
	odata_type = "#microsoft.graph.akamaiWebApplicationFirewallProvider",
	display_name = "Akamai Provider Example",
	host_prefix = "akab-exampleprefix",
	client_secret = "akamai_example_secret_123",
	client_token = "akamai_example_token_456",
	access_token = "akamai_example_token_789",
)

result = await graph_client.identity.risk_prevention.web_application_firewall_providers.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-Type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#identity/riskPrevention/webApplicationFirewallProviders/$entity",
    "@odata.type": "#microsoft.graph.akamaiWebApplicationFirewallProvider",
    "id": "00000000-0000-0000-0000-000000000002",
    "displayName": "Akamai Provider Example",
    "hostPrefix": "akab-exampleprefix"
}
```

### Example 2: Create a new cloudFlareWebApplicationFirewallProvider object

#### Request

The following example shows a request to create a new Cloudflare WAF object.

- [HTTP](#tabpanel_2_http)
- [C#](#tabpanel_2_csharp)
- [Go](#tabpanel_2_go)
- [Java](#tabpanel_2_java)
- [JavaScript](#tabpanel_2_javascript)
- [PHP](#tabpanel_2_php)
- [PowerShell](#tabpanel_2_powershell)
- [Python](#tabpanel_2_python)

```http
POST https://graph.microsoft.com/v1.0/identity/riskPrevention/webApplicationFirewallProviders
Content-Type: application/json

{
    "@odata.type": "#microsoft.graph.cloudFlareWebApplicationFirewallProvider",
    "displayName": "Cloudflare Provider Example",
    "zoneId": "11111111111111111111111111111111",
    "apiToken": "cf_example_token_123"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new CloudFlareWebApplicationFirewallProvider
{
	OdataType = "#microsoft.graph.cloudFlareWebApplicationFirewallProvider",
	DisplayName = "Cloudflare Provider Example",
	ZoneId = "11111111111111111111111111111111",
	ApiToken = "cf_example_token_123",
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Identity.RiskPrevention.WebApplicationFirewallProviders.PostAsync(requestBody);
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

requestBody := graphmodels.NewWebApplicationFirewallProvider()
displayName := "Cloudflare Provider Example"
requestBody.SetDisplayName(&displayName) 
zoneId := "11111111111111111111111111111111"
requestBody.SetZoneId(&zoneId) 
apiToken := "cf_example_token_123"
requestBody.SetApiToken(&apiToken) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
webApplicationFirewallProviders, err := graphClient.Identity().RiskPrevention().WebApplicationFirewallProviders().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

CloudFlareWebApplicationFirewallProvider webApplicationFirewallProvider = new CloudFlareWebApplicationFirewallProvider();
webApplicationFirewallProvider.setOdataType("#microsoft.graph.cloudFlareWebApplicationFirewallProvider");
webApplicationFirewallProvider.setDisplayName("Cloudflare Provider Example");
webApplicationFirewallProvider.setZoneId("11111111111111111111111111111111");
webApplicationFirewallProvider.setApiToken("cf_example_token_123");
WebApplicationFirewallProvider result = graphClient.identity().riskPrevention().webApplicationFirewallProviders().post(webApplicationFirewallProvider);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const webApplicationFirewallProvider = {
    '@odata.type': '#microsoft.graph.cloudFlareWebApplicationFirewallProvider',
    displayName: 'Cloudflare Provider Example',
    zoneId: '11111111111111111111111111111111',
    apiToken: 'cf_example_token_123'
};

await client.api('/identity/riskPrevention/webApplicationFirewallProviders')
	.post(webApplicationFirewallProvider);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\CloudFlareWebApplicationFirewallProvider;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new CloudFlareWebApplicationFirewallProvider();
$requestBody->setOdataType('#microsoft.graph.cloudFlareWebApplicationFirewallProvider');
$requestBody->setDisplayName('Cloudflare Provider Example');
$requestBody->setZoneId('11111111111111111111111111111111');
$requestBody->setApiToken('cf_example_token_123');

$result = $graphServiceClient->identity()->riskPrevention()->webApplicationFirewallProviders()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Identity.SignIns

$params = @{
	"@odata.type" = "#microsoft.graph.cloudFlareWebApplicationFirewallProvider"
	displayName = "Cloudflare Provider Example"
	zoneId = "11111111111111111111111111111111"
	apiToken = "cf_example_token_123"
}

New-MgIdentityRiskPreventionWebApplicationFirewallProvider -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.cloud_flare_web_application_firewall_provider import CloudFlareWebApplicationFirewallProvider
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = CloudFlareWebApplicationFirewallProvider(
	odata_type = "#microsoft.graph.cloudFlareWebApplicationFirewallProvider",
	display_name = "Cloudflare Provider Example",
	zone_id = "11111111111111111111111111111111",
	api_token = "cf_example_token_123",
)

result = await graph_client.identity.risk_prevention.web_application_firewall_providers.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response with Cloudflare WAF object.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-Type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#identity/riskPrevention/webApplicationFirewallProviders/$entity",
    "@odata.type": "#microsoft.graph.cloudFlareWebApplicationFirewallProvider",
    "id": "00000000-0000-0000-0000-000000000001",
    "displayName": "Cloudflare Provider Example",
    "zoneId": "11111111111111111111111111111111"
}
```
