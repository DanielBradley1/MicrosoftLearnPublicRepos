<!-- Source: https://learn.microsoft.com/en-us/graph/api/security-autoauditingconfiguration-update?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-05-12 -->

# Update autoAuditingConfiguration

Namespace: microsoft.graph.security

Update the properties of an [autoAuditingConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/security-autoauditingconfiguration?view=graph-rest-1.0) object.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permission | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | SecurityIdentitiesAutoConfig.ReadWrite.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | SecurityIdentitiesAutoConfig.ReadWrite.All | Not available. |

Important

For delegated access using work or school accounts, the signed-in user must be assigned the *Security Administrator* [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) or a custom role with supported permissions created through the Microsoft Defender XDR Unified Role-Based Access Control \(RBAC\).

## HTTP request

```http
PATCH /security/identities/settings/autoAuditingConfiguration
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

| Property | Type | Description |
| :--- | :--- | :--- |
| isAutomatic | Boolean | Required. |

## Response

If successful, this method returns a `200 OK` response code.

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
PATCH https://graph.microsoft.com/v1.0/security/identities/settings/autoAuditingConfiguration
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.security.autoAuditingConfiguration",
  "isAutomatic": true
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models.Security;

var requestBody = new AutoAuditingConfiguration
{
	OdataType = "#microsoft.graph.security.autoAuditingConfiguration",
	IsAutomatic = true,
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Security.Identities.Settings.AutoAuditingConfiguration.PatchAsync(requestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphmodelssecurity "github.com/microsoftgraph/msgraph-sdk-go/models/security"
	  //other-imports
)

requestBody := graphmodelssecurity.NewAutoAuditingConfiguration()
isAutomatic := true
requestBody.SetIsAutomatic(&isAutomatic) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
autoAuditingConfiguration, err := graphClient.Security().Identities().Settings().AutoAuditingConfiguration().Patch(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.models.security.AutoAuditingConfiguration autoAuditingConfiguration = new com.microsoft.graph.models.security.AutoAuditingConfiguration();
autoAuditingConfiguration.setOdataType("#microsoft.graph.security.autoAuditingConfiguration");
autoAuditingConfiguration.setIsAutomatic(true);
com.microsoft.graph.models.security.AutoAuditingConfiguration result = graphClient.security().identities().settings().autoAuditingConfiguration().patch(autoAuditingConfiguration);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const autoAuditingConfiguration = {
  '@odata.type': '#microsoft.graph.security.autoAuditingConfiguration',
  isAutomatic: true
};

await client.api('/security/identities/settings/autoAuditingConfiguration')
	.update(autoAuditingConfiguration);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\Security\AutoAuditingConfiguration;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new AutoAuditingConfiguration();
$requestBody->setOdataType('#microsoft.graph.security.autoAuditingConfiguration');
$requestBody->setIsAutomatic(true);

$result = $graphServiceClient->security()->identities()->settings()->autoAuditingConfiguration()->patch($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Security

$params = @{
	"@odata.type" = "#microsoft.graph.security.autoAuditingConfiguration"
	isAutomatic = $true
}

Update-MgSecurityIdentitySettingAutoAuditingConfiguration -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.security.auto_auditing_configuration import AutoAuditingConfiguration
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = AutoAuditingConfiguration(
	odata_type = "#microsoft.graph.security.autoAuditingConfiguration",
	is_automatic = True,
)

result = await graph_client.security.identities.settings.auto_auditing_configuration.patch(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
```
