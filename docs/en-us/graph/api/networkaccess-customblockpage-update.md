<!-- Source: https://learn.microsoft.com/en-us/graph/api/networkaccess-customblockpage-update?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-03-24 -->

# Update customBlockPage

Namespace: microsoft.graph.networkaccess

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Update the properties of a customBlockPage object.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | NetworkAccess.ReadWrite.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | NetworkAccess.ReadWrite.All | Not available. |

Important

For delegated access using work or school accounts, the signed-in user must be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) or a custom role that grants the permissions required for this operation. This operation supports the following built-in roles, which provide only the least privilege necessary:

- Global Secure Access Administrator
- Security Administrator

## HTTP request

```http
PATCH /networkAccess/settings/customBlockPage
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
| state | microsoft.graph.networkaccess.status | The current status of the custom block page. The possible values are: `enabled`, `disabled`, `unknownFutureValue`. Required. |
| configuration | [microsoft.graph.networkaccess.blockPageConfigurationBase](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-blockpageconfigurationbase?view=graph-rest-beta) | The current configuration of the customized message. The body can be input in limited markdown language, supporting links via the format: `[link](https://example.com)`. Optional. |

## Response

If successful, this method returns a `204 No Content` response code.

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
PATCH https://graph.microsoft.com/beta/networkAccess/settings/customBlockPage
Content-Type: application/json

{
    "state": "enabled",
    "configuration": {
        "@odata.type": "#microsoft.graph.networkaccess.markdownBlockMessageConfiguration",
        "body": "Your admin at NaaSLitware has blocked your access. [Click here for NaaSLitware's Terms of Use](https://www.bing.com)."
    }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.Models.Networkaccess;

var requestBody = new CustomBlockPage
{
	State = Status.Enabled,
	Configuration = new MarkdownBlockMessageConfiguration
	{
		OdataType = "#microsoft.graph.networkaccess.markdownBlockMessageConfiguration",
		Body = "Your admin at NaaSLitware has blocked your access. [Click here for NaaSLitware's Terms of Use](https://www.bing.com).",
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.NetworkAccess.Settings.CustomBlockPage.PatchAsync(requestBody);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v0.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-beta-sdk-go"
	  graphmodelsnetworkaccess "github.com/microsoftgraph/msgraph-beta-sdk-go/models/networkaccess"
	  //other-imports
)

requestBody := graphmodelsnetworkaccess.NewCustomBlockPage()
state := graphmodels.ENABLED_STATUS 
requestBody.SetState(&state) 
configuration := graphmodelsnetworkaccess.NewMarkdownBlockMessageConfiguration()
body := "Your admin at NaaSLitware has blocked your access. [Click here for NaaSLitware's Terms of Use](https://www.bing.com)."
configuration.SetBody(&body) 
requestBody.SetConfiguration(configuration)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
customBlockPage, err := graphClient.NetworkAccess().Settings().CustomBlockPage().Patch(context.Background(), requestBody, nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.beta.models.networkaccess.CustomBlockPage customBlockPage = new com.microsoft.graph.beta.models.networkaccess.CustomBlockPage();
customBlockPage.setState(com.microsoft.graph.beta.models.networkaccess.Status.Enabled);
com.microsoft.graph.beta.models.networkaccess.MarkdownBlockMessageConfiguration configuration = new com.microsoft.graph.beta.models.networkaccess.MarkdownBlockMessageConfiguration();
configuration.setOdataType("#microsoft.graph.networkaccess.markdownBlockMessageConfiguration");
configuration.setBody("Your admin at NaaSLitware has blocked your access. [Click here for NaaSLitware's Terms of Use](https://www.bing.com).");
customBlockPage.setConfiguration(configuration);
com.microsoft.graph.models.networkaccess.CustomBlockPage result = graphClient.networkAccess().settings().customBlockPage().patch(customBlockPage);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const customBlockPage = {
    state: 'enabled',
    configuration: {
        '@odata.type': '#microsoft.graph.networkaccess.markdownBlockMessageConfiguration',
        body: 'Your admin at NaaSLitware has blocked your access. [Click here for NaaSLitware\'s Terms of Use](https://www.bing.com).'
    }
};

await client.api('/networkAccess/settings/customBlockPage')
	.version('beta')
	.update(customBlockPage);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Models\Networkaccess\CustomBlockPage;
use Microsoft\Graph\Beta\Generated\Models\Networkaccess\Status;
use Microsoft\Graph\Beta\Generated\Models\Networkaccess\MarkdownBlockMessageConfiguration;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new CustomBlockPage();
$requestBody->setState(new Status('enabled'));
$configuration = new MarkdownBlockMessageConfiguration();
$configuration->setOdataType('#microsoft.graph.networkaccess.markdownBlockMessageConfiguration');
$configuration->setBody('Your admin at NaaSLitware has blocked your access. [Click here for NaaSLitware\'s Terms of Use](https://www.bing.com).');
$requestBody->setConfiguration($configuration);

$result = $graphServiceClient->networkAccess()->settings()->customBlockPage()->patch($requestBody)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Beta.NetworkAccess

$params = @{
	state = "enabled"
	configuration = @{
		"@odata.type" = "#microsoft.graph.networkaccess.markdownBlockMessageConfiguration"
		body = "Your admin at NaaSLitware has blocked your access. [Click here for NaaSLitware's Terms of Use](https://www.bing.com)."
	}
}

Update-MgBetaNetworkAccessSettingCustomBlockPage -BodyParameter $params
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.models.networkaccess.custom_block_page import CustomBlockPage
from msgraph_beta.generated.models.status import Status
from msgraph_beta.generated.models.networkaccess.markdown_block_message_configuration import MarkdownBlockMessageConfiguration
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = CustomBlockPage(
	state = Status.Enabled,
	configuration = MarkdownBlockMessageConfiguration(
		odata_type = "#microsoft.graph.networkaccess.markdownBlockMessageConfiguration",
		body = "Your admin at NaaSLitware has blocked your access. [Click here for NaaSLitware's Terms of Use](https://www.bing.com).",
	),
)

result = await graph_client.network_access.settings.custom_block_page.patch(request_body)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

```http
HTTP/1.1 204 No Content
```
