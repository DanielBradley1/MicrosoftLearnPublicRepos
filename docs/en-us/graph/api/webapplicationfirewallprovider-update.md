<!-- Source: https://learn.microsoft.com/en-us/graph/api/webapplicationfirewallprovider-update?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-03-21 -->

# Update webApplicationFirewallProvider

Namespace: microsoft.graph

Update the properties of a [webApplicationFirewallProvider](https://learn.microsoft.com/en-us/graph/api/resources/webapplicationfirewallprovider?view=graph-rest-1.0) object.

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
PATCH /identity/riskPrevention/webApplicationFirewallProviders/{webApplicationFirewallProviderId}
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply *only* the values for properties to update. Existing properties that aren't included in the request body maintain their previous values or are recalculated based on changes to other property values.

The following table specifies the properties that can be updated.

You must specify the **@odata.type** property to specify the type of [webApplicationFirewallProvider](https://learn.microsoft.com/en-us/graph/api/resources/webapplicationfirewallprovider?view=graph-rest-1.0) object to update. For example, "@odata.type": "#microsoft.graph.akamaiWebApplicationFirewallProvider".

| Property | Type | Description |
| :--- | :--- | :--- |
| displayName | String | The friendly display name of the Web Application Firewall provider configuration. |
| accessToken | String | Akamai API access token used to authenticate to the Akamai account. Contact your Akamai Customer Success Manager for assistance with your accessToken. Supported for Akamai only. |
| clientSecret | String | Akamai API client secret used in conjunction with the client token and access token for authentication. Contact your Akamai Customer Success Manager for assistance with this information. Supported for Akamai only. |
| clientToken | String | Akamai API client token used for authentication to the Akamai account. Contact your Akamai Customer Success Manager for assistance with this information. Supported for Akamai only. |
| hostPrefix | String | Prefix used to identify the host or domain in Akamai configuration operations. This value may be required for certain API calls or configuration scenarios. Supported for Akamai only. |
| apiToken | String | Cloudflare API token or credential used by Microsoft services to authenticate to the Cloudflare account. Contact your Cloudflare Customer Success Manager for assistance with your apitoken. Supported for Cloudflare only. |
| zoneId | String | Default Cloudflare Zone ID associated with this provider configuration. This ID identifies the DNS zone in Cloudflare that is commonly used for verification and configuration operations for the provider. Supported for Cloudflare only. |

## Response

If successful, this method returns a `200 OK` response code and an updated [webApplicationFirewallProvider](https://learn.microsoft.com/en-us/graph/api/resources/webapplicationfirewallprovider?view=graph-rest-1.0) object in the response body.

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
PATCH https://graph.microsoft.com/v1.0/identity/riskPrevention/webApplicationFirewallProviders/{webApplicationFirewallProviderId}
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.cloudFlareWebApplicationFirewallProvider",
  "displayName": "String"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new CloudFlareWebApplicationFirewallProvider
{
	OdataType = "#microsoft.graph.cloudFlareWebApplicationFirewallProvider",
	DisplayName = "String",
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Identity.RiskPrevention.WebApplicationFirewallProviders["{webApplicationFirewallProvider-id}"].PatchAsync(requestBody);
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
displayName := "String"
requestBody.SetDisplayName(&displayName) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
webApplicationFirewallProviders, err := graphClient.Identity().RiskPrevention().WebApplicationFirewallProviders().ByWebApplicationFirewallProviderId("webApplicationFirewallProvider-id").Patch(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

CloudFlareWebApplicationFirewallProvider webApplicationFirewallProvider = new CloudFlareWebApplicationFirewallProvider();
webApplicationFirewallProvider.setOdataType("#microsoft.graph.cloudFlareWebApplicationFirewallProvider");
webApplicationFirewallProvider.setDisplayName("String");
WebApplicationFirewallProvider result = graphClient.identity().riskPrevention().webApplicationFirewallProviders().byWebApplicationFirewallProviderId("{webApplicationFirewallProvider-id}").patch(webApplicationFirewallProvider);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const webApplicationFirewallProvider = {
  '@odata.type': '#microsoft.graph.cloudFlareWebApplicationFirewallProvider',
  displayName: 'String'
};

await client.api('/identity/riskPrevention/webApplicationFirewallProviders/{webApplicationFirewallProviderId}')
	.update(webApplicationFirewallProvider);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\CloudFlareWebApplicationFirewallProvider;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new CloudFlareWebApplicationFirewallProvider();
$requestBody->setOdataType('#microsoft.graph.cloudFlareWebApplicationFirewallProvider');
$requestBody->setDisplayName('String');

$result = $graphServiceClient->identity()->riskPrevention()->webApplicationFirewallProviders()->byWebApplicationFirewallProviderId('webApplicationFirewallProvider-id')->patch($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Identity.SignIns

$params = @{
	"@odata.type" = "#microsoft.graph.cloudFlareWebApplicationFirewallProvider"
	displayName = "String"
}

Update-MgIdentityRiskPreventionWebApplicationFirewallProvider -WebApplicationFirewallProviderId $webApplicationFirewallProviderId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.cloud_flare_web_application_firewall_provider import CloudFlareWebApplicationFirewallProvider
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = CloudFlareWebApplicationFirewallProvider(
	odata_type = "#microsoft.graph.cloudFlareWebApplicationFirewallProvider",
	display_name = "String",
)

result = await graph_client.identity.risk_prevention.web_application_firewall_providers.by_web_application_firewall_provider_id('webApplicationFirewallProvider-id').patch(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.cloudFlareWebApplicationFirewallProvider",
  "id": "4d8ac75a-e882-18c6-8ad4-2ab20c742e52",
  "displayName": "String"
}
```
