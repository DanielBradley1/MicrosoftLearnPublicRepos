<!-- Source: https://learn.microsoft.com/en-us/graph/api/insiderriskyuserapproval-update?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-03-21 -->

# Update insiderRiskyUserApproval

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Update the properties of an [insiderRiskyUserApproval](https://learn.microsoft.com/en-us/graph/api/resources/insiderriskyuserapproval?view=graph-rest-beta) object.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permission | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Not supported. | Not supported. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Not supported. | Not supported. |

Important

For delegated access using work or school accounts, the signed-in user must be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) or a custom role that grants the permissions required for this operation. *Lifecycle Workflows Administrator* is the least privileged role supported for this operation.

## HTTP request

```http
PUT /identityGovernance/entitlementManagement/controlConfigurations/insiderRiskyUserApproval
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply *only* the values for properties to update. Existing properties that aren't included in the request body maintain their previous values or are recalculated based on changes to other property values.

The following table specifies the properties that can be updated.

The following table shows the properties that can be updated for an [insiderRiskyUserApproval](https://learn.microsoft.com/en-us/graph/api/resources/insiderriskyuserapproval?view=graph-rest-beta).

| Property | Type | Description |
| :--- | :--- | :--- |
| isApprovalRequired | Boolean | Indicates whether approval is required for risky users. |
| minimumRiskLevel | purviewInsiderRiskManagementLevel | The minimum risk level for which approval is required. The possible values are: `none`, `minor`, `moderate`, `elevated`, `unknownFutureValue`. |

## Response

If successful, this method returns a `200 OK` response code and an updated [insiderRiskyUserApproval](https://learn.microsoft.com/en-us/graph/api/resources/insiderriskyuserapproval?view=graph-rest-beta) object in the response body.

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
PUT https://graph.microsoft.com/beta/identityGovernance/entitlementManagement/controlConfigurations/insiderRiskyUserApproval
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.insiderRiskyUserApproval",
  "id": "insiderRiskyUserApproval",
  "isApprovalRequired": true,
  "minimumRiskLevel": "elevated"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.Models;

var requestBody = new InsiderRiskyUserApproval
{
	OdataType = "#microsoft.graph.insiderRiskyUserApproval",
	Id = "insiderRiskyUserApproval",
	IsApprovalRequired = true,
	MinimumRiskLevel = PurviewInsiderRiskManagementLevel.Elevated,
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.IdentityGovernance.EntitlementManagement.ControlConfigurations["{controlConfiguration-id}"].PutAsync(requestBody);
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
	  graphmodels "github.com/microsoftgraph/msgraph-beta-sdk-go/models"
	  //other-imports
)

requestBody := graphmodels.NewControlConfiguration()
id := "insiderRiskyUserApproval"
requestBody.SetId(&id) 
isApprovalRequired := true
requestBody.SetIsApprovalRequired(&isApprovalRequired) 
minimumRiskLevel := graphmodels.ELEVATED_PURVIEWINSIDERRISKMANAGEMENTLEVEL 
requestBody.SetMinimumRiskLevel(&minimumRiskLevel) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
controlConfigurations, err := graphClient.IdentityGovernance().EntitlementManagement().ControlConfigurations().ByControlConfigurationId("controlConfiguration-id").Put(context.Background(), requestBody, nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

InsiderRiskyUserApproval controlConfiguration = new InsiderRiskyUserApproval();
controlConfiguration.setOdataType("#microsoft.graph.insiderRiskyUserApproval");
controlConfiguration.setId("insiderRiskyUserApproval");
controlConfiguration.setIsApprovalRequired(true);
controlConfiguration.setMinimumRiskLevel(PurviewInsiderRiskManagementLevel.Elevated);
ControlConfiguration result = graphClient.identityGovernance().entitlementManagement().controlConfigurations().byControlConfigurationId("{controlConfiguration-id}").put(controlConfiguration);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const controlConfiguration = {
  '@odata.type': '#microsoft.graph.insiderRiskyUserApproval',
  id: 'insiderRiskyUserApproval',
  isApprovalRequired: true,
  minimumRiskLevel: 'elevated'
};

await client.api('/identityGovernance/entitlementManagement/controlConfigurations/insiderRiskyUserApproval')
	.version('beta')
	.put(controlConfiguration);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Models\InsiderRiskyUserApproval;
use Microsoft\Graph\Beta\Generated\Models\PurviewInsiderRiskManagementLevel;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new InsiderRiskyUserApproval();
$requestBody->setOdataType('#microsoft.graph.insiderRiskyUserApproval');
$requestBody->setId('insiderRiskyUserApproval');
$requestBody->setIsApprovalRequired(true);
$requestBody->setMinimumRiskLevel(new PurviewInsiderRiskManagementLevel('elevated'));

$result = $graphServiceClient->identityGovernance()->entitlementManagement()->controlConfigurations()->byControlConfigurationId('controlConfiguration-id')->put($requestBody)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Beta.Identity.Governance

$params = @{
	"@odata.type" = "#microsoft.graph.insiderRiskyUserApproval"
	id = "insiderRiskyUserApproval"
	isApprovalRequired = $true
	minimumRiskLevel = "elevated"
}

Set-MgBetaEntitlementManagementControlConfiguration -ControlConfigurationId $controlConfigurationId -BodyParameter $params
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.models.insider_risky_user_approval import InsiderRiskyUserApproval
from msgraph_beta.generated.models.purview_insider_risk_management_level import PurviewInsiderRiskManagementLevel
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = InsiderRiskyUserApproval(
	odata_type = "#microsoft.graph.insiderRiskyUserApproval",
	id = "insiderRiskyUserApproval",
	is_approval_required = True,
	minimum_risk_level = PurviewInsiderRiskManagementLevel.Elevated,
)

result = await graph_client.identity_governance.entitlement_management.control_configurations.by_control_configuration_id('controlConfiguration-id').put(request_body)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "@odata.context": "https://graph.microsoft.com/beta/$metadata#identityGovernance/entitlementManagement/controlConfigurations/$entity",
  "@odata.type": "#microsoft.graph.insiderRiskyUserApproval",
  "id": "insiderRiskyUserApproval",
  "createdBy": "kayat@elmdev.com",
  "createdDateTime": "2025-11-04T11:00:00Z",
  "modifiedBy": "kayat@elmdev.com",
  "modifiedDateTime": "2025-11-09T09:40:00Z",
  "isApprovalRequired": true,
  "minimumRiskLevel": "elevated"
}
```
