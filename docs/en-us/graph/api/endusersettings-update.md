<!-- Source: https://learn.microsoft.com/en-us/graph/api/endusersettings-update?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-08-05 -->

# Update endUserSettings

Namespace: microsoft.graph

Update the properties of an [endUserSettings](https://learn.microsoft.com/en-us/graph/api/resources/endusersettings?view=graph-rest-1.0) object that controls the end user experience for access package suggestions and resource discovery.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | EntitlementManagement.ReadWrite.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | EntitlementManagement.ReadWrite.All | Not available. |

Tip

For delegated access using work or school accounts, the signed-in user must be assigned an administrator role with supported role permissions through one of the following options:

- A [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) where the least privileged role is *Identity Governance Administrator*. **This is the least privileged option.**

In app-only scenarios, the calling app can be assigned one of the preceding supported roles instead of the `EntitlementManagement.ReadWrite.All` application permission. The *Identity Governance Administrator* role is less privileged than the `EntitlementManagement.ReadWrite.All` application permission.

For more information, see [Delegation and roles in entitlement management](https://learn.microsoft.com/en-us/entra/id-governance/entitlement-management-delegate) and [how to delegate access governance to access package managers in entitlement management](https://learn.microsoft.com/en-us/entra/id-governance/entitlement-management-delegate-managers).

## HTTP request

```http
PUT /identityGovernance/entitlementManagement/controlConfigurations/endUserSettings
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the [endUserSettings](https://learn.microsoft.com/en-us/graph/api/resources/endusersettings?view=graph-rest-1.0) object.

The following table shows the properties that are required when you update the [endUserSettings](https://learn.microsoft.com/en-us/graph/api/resources/endusersettings?view=graph-rest-1.0).

| Property | Type | Description |
| :--- | :--- | :--- |
| relatedPeopleInsightLevel | accessPackageSuggestionRelatedPeopleInsightLevel | The level of related people insights to show in access package suggestions. The possible values are: `disabled`, `count`, `countAndNames`, `unknownFutureValue`. |
| showApproverDetailsToMembers | Boolean | Indicates whether approver details are shown to members. When `true`, approver information is visible to members. |

## Response

If successful, this method returns a `200 OK` response code and an updated [endUserSettings](https://learn.microsoft.com/en-us/graph/api/resources/endusersettings?view=graph-rest-1.0) object in the response body.

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
PUT https://graph.microsoft.com/v1.0/identityGovernance/entitlementManagement/controlConfigurations/endUserSettings
Content-type: application/json

{
  "@odata.type": "#microsoft.graph.endUserSettings",
  "relatedPeopleInsightLevel": "countAndNames",
  "showApproverDetailsToMembers": true
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new EndUserSettings
{
	OdataType = "#microsoft.graph.endUserSettings",
	RelatedPeopleInsightLevel = AccessPackageSuggestionRelatedPeopleInsightLevel.CountAndNames,
	ShowApproverDetailsToMembers = true,
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.IdentityGovernance.EntitlementManagement.ControlConfigurations["{controlConfiguration-id}"].PutAsync(requestBody);
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

requestBody := graphmodels.NewControlConfiguration()
relatedPeopleInsightLevel := graphmodels.COUNTANDNAMES_ACCESSPACKAGESUGGESTIONRELATEDPEOPLEINSIGHTLEVEL 
requestBody.SetRelatedPeopleInsightLevel(&relatedPeopleInsightLevel) 
showApproverDetailsToMembers := true
requestBody.SetShowApproverDetailsToMembers(&showApproverDetailsToMembers) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
controlConfigurations, err := graphClient.IdentityGovernance().EntitlementManagement().ControlConfigurations().ByControlConfigurationId("controlConfiguration-id").Put(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

EndUserSettings controlConfiguration = new EndUserSettings();
controlConfiguration.setOdataType("#microsoft.graph.endUserSettings");
controlConfiguration.setRelatedPeopleInsightLevel(AccessPackageSuggestionRelatedPeopleInsightLevel.CountAndNames);
controlConfiguration.setShowApproverDetailsToMembers(true);
ControlConfiguration result = graphClient.identityGovernance().entitlementManagement().controlConfigurations().byControlConfigurationId("{controlConfiguration-id}").put(controlConfiguration);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const controlConfiguration = {
  '@odata.type': '#microsoft.graph.endUserSettings',
  relatedPeopleInsightLevel: 'countAndNames',
  showApproverDetailsToMembers: true
};

await client.api('/identityGovernance/entitlementManagement/controlConfigurations/endUserSettings')
	.put(controlConfiguration);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\EndUserSettings;
use Microsoft\Graph\Generated\Models\AccessPackageSuggestionRelatedPeopleInsightLevel;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new EndUserSettings();
$requestBody->setOdataType('#microsoft.graph.endUserSettings');
$requestBody->setRelatedPeopleInsightLevel(new AccessPackageSuggestionRelatedPeopleInsightLevel('countAndNames'));
$requestBody->setShowApproverDetailsToMembers(true);

$result = $graphServiceClient->identityGovernance()->entitlementManagement()->controlConfigurations()->byControlConfigurationId('controlConfiguration-id')->put($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Identity.Governance

$params = @{
	"@odata.type" = "#microsoft.graph.endUserSettings"
	relatedPeopleInsightLevel = "countAndNames"
	showApproverDetailsToMembers = $true
}

Set-MgEntitlementManagementControlConfiguration -ControlConfigurationId $controlConfigurationId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.end_user_settings import EndUserSettings
from msgraph.generated.models.access_package_suggestion_related_people_insight_level import AccessPackageSuggestionRelatedPeopleInsightLevel
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = EndUserSettings(
	odata_type = "#microsoft.graph.endUserSettings",
	related_people_insight_level = AccessPackageSuggestionRelatedPeopleInsightLevel.CountAndNames,
	show_approver_details_to_members = True,
)

result = await graph_client.identity_governance.entitlement_management.control_configurations.by_control_configuration_id('controlConfiguration-id').put(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-type: application/json

{
  "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#identityGovernance/entitlementManagement/controlConfigurations/endUserSettings",
  "relatedPeopleInsightLevel": "countAndNames",
  "showApproverDetailsToMembers": true
}
```
