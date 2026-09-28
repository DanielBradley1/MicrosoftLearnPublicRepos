<!-- Source: https://learn.microsoft.com/en-us/graph/api/unifiedrolemanagementalertconfiguration-update?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-23 -->

# Update unifiedRoleManagementAlertConfiguration

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Update the properties of an alert configuration. The alert configuration can be one of the following types that are derived from the [unifiedRoleManagementAlertConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/unifiedrolemanagementalertconfiguration?view=graph-rest-beta) object:

- [invalidLicenseAlertConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/invalidlicensealertconfiguration?view=graph-rest-beta)
- [noMfaOnRoleActivationAlertConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/nomfaonroleactivationalertconfiguration?view=graph-rest-beta)
- [redundantAssignmentAlertConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/redundantassignmentalertconfiguration?view=graph-rest-beta)
- [rolesAssignedOutsidePrivilegedIdentityManagementAlertConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/rolesassignedoutsideprivilegedidentitymanagementalertconfiguration?view=graph-rest-beta)
- [sequentialActivationRenewalsAlertConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/sequentialactivationrenewalsalertconfiguration?view=graph-rest-beta)
- [staleSignInAlertConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/stalesigninalertconfiguration?view=graph-rest-beta)
- [tooManyGlobalAdminsAssignedToTenantAlertConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/toomanyglobaladminsassignedtotenantalertconfiguration?view=graph-rest-beta)

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | RoleManagementAlert.ReadWrite.Directory | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | RoleManagementAlert.ReadWrite.Directory | Not available. |

Important

For delegated access using work or school accounts, the signed-in user must be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) or a custom role that grants the permissions required for this operation. *Privileged Role Administrator* is the least privileged role supported for this operation.

## HTTP request

```http
PATCH /identityGovernance/roleManagementAlerts/alertConfigurations/{unifiedRoleManagementAlertConfigurationId}
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply *only* the values for properties to update. Existing properties that aren't included in the request body maintain their previous values or are recalculated based on changes to other property values.

The following table specifies the properties that can be updated.

You must include the **@odata.type** property in the body of the request. The value for this property must be the same as the derived alert configuration type that you are updating. For example, if you are updating the **tooManyGlobalAdminsAssignedToTenantAlertConfiguration** alert configuration, the value for the **@odata.type** property must be **#microsoft.graph.tooManyGlobalAdminsAssignedToTenantAlertConfiguration**.

| Property | Type | Description |
| :--- | :--- | :--- |
| duration | Boolean | The number of days to look back on from current timestamp.  <br>  <br>Can be updated for the **redundantAssignmentAlertConfiguration** and the **staleSignInAlertConfiguration** alert configuration type. |
| globalAdminCountThreshold | Int32 | The threshold for the number of accounts assigned the Global Administrator role in the tenant. Triggers an alert if the number of global administrators in the tenant reaches or crosses this threshold value.  <br>  <br>Can be updated for the **tooManyGlobalAdminsAssignedToTenantAlertConfiguration** alert configuration type. |
| isEnabled | Boolean | True if the alert is enabled. Setting to false will disable scanning for the specific alert. Optional.  <br>  <br>Can be updated for all alert configuration types. |
| percentageOfGlobalAdminsOutOfRolesThreshold | Int32 | Threshold of the percentage of global administrators out of all the role assignments in the tenant. Triggers an alert if the percentage in the tenant reaches or crosses this threshold value.  <br>  <br>Can be updated for the **tooManyGlobalAdminsAssignedToTenantAlertConfiguration** alert configuration type. |
| sequentialActivationCounterThreshold | Int32 | The minimum number of activations within the timeIntervalBetweenActivations period to trigger an alert.  <br>  <br>Can be updated for the **sequentialactivationrenewalsalertconfiguration** alert configuration type. |
| timeIntervalBetweenActivations | Duration | Time interval between activations to trigger an alert.  <br>  <br>Can be updated for the **sequentialactivationrenewalsalertconfiguration** alert configuration type. |

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
PATCH https://graph.microsoft.com/beta/identityGovernance/roleManagementAlerts/alertConfigurations/DirectoryRole_67b47f38-0f0b-4e62-a3be-859140c2061f_TooManyGlobalAdminsAssignedToTenantAlert
Content-Type: application/json

{
  "@odata.type":"#microsoft.graph.tooManyGlobalAdminsAssignedToTenantAlertConfiguration",
  "isEnabled": "true",
  "globalAdminCountThreshold": 7,
  "percentageOfGlobalAdminsOutOfRolesThreshold": 70
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.Models;

var requestBody = new TooManyGlobalAdminsAssignedToTenantAlertConfiguration
{
	OdataType = "#microsoft.graph.tooManyGlobalAdminsAssignedToTenantAlertConfiguration",
	IsEnabled = true,
	GlobalAdminCountThreshold = 7,
	PercentageOfGlobalAdminsOutOfRolesThreshold = 70,
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.IdentityGovernance.RoleManagementAlerts.AlertConfigurations["{unifiedRoleManagementAlertConfiguration-id}"].PatchAsync(requestBody);
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

requestBody := graphmodels.NewUnifiedRoleManagementAlertConfiguration()
isEnabled := true
requestBody.SetIsEnabled(&isEnabled) 
globalAdminCountThreshold := int32(7)
requestBody.SetGlobalAdminCountThreshold(&globalAdminCountThreshold) 
percentageOfGlobalAdminsOutOfRolesThreshold := int32(70)
requestBody.SetPercentageOfGlobalAdminsOutOfRolesThreshold(&percentageOfGlobalAdminsOutOfRolesThreshold) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
alertConfigurations, err := graphClient.IdentityGovernance().RoleManagementAlerts().AlertConfigurations().ByUnifiedRoleManagementAlertConfigurationId("unifiedRoleManagementAlertConfiguration-id").Patch(context.Background(), requestBody, nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

TooManyGlobalAdminsAssignedToTenantAlertConfiguration unifiedRoleManagementAlertConfiguration = new TooManyGlobalAdminsAssignedToTenantAlertConfiguration();
unifiedRoleManagementAlertConfiguration.setOdataType("#microsoft.graph.tooManyGlobalAdminsAssignedToTenantAlertConfiguration");
unifiedRoleManagementAlertConfiguration.setIsEnabled(true);
unifiedRoleManagementAlertConfiguration.setGlobalAdminCountThreshold(7);
unifiedRoleManagementAlertConfiguration.setPercentageOfGlobalAdminsOutOfRolesThreshold(70);
UnifiedRoleManagementAlertConfiguration result = graphClient.identityGovernance().roleManagementAlerts().alertConfigurations().byUnifiedRoleManagementAlertConfigurationId("{unifiedRoleManagementAlertConfiguration-id}").patch(unifiedRoleManagementAlertConfiguration);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const unifiedRoleManagementAlertConfiguration = {
  '@odata.type':'#microsoft.graph.tooManyGlobalAdminsAssignedToTenantAlertConfiguration',
  isEnabled: 'true',
  globalAdminCountThreshold: 7,
  percentageOfGlobalAdminsOutOfRolesThreshold: 70
};

await client.api('/identityGovernance/roleManagementAlerts/alertConfigurations/DirectoryRole_67b47f38-0f0b-4e62-a3be-859140c2061f_TooManyGlobalAdminsAssignedToTenantAlert')
	.version('beta')
	.update(unifiedRoleManagementAlertConfiguration);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Models\TooManyGlobalAdminsAssignedToTenantAlertConfiguration;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new TooManyGlobalAdminsAssignedToTenantAlertConfiguration();
$requestBody->setOdataType('#microsoft.graph.tooManyGlobalAdminsAssignedToTenantAlertConfiguration');
$requestBody->setIsEnabled(true);
$requestBody->setGlobalAdminCountThreshold(7);
$requestBody->setPercentageOfGlobalAdminsOutOfRolesThreshold(70);

$result = $graphServiceClient->identityGovernance()->roleManagementAlerts()->alertConfigurations()->byUnifiedRoleManagementAlertConfigurationId('unifiedRoleManagementAlertConfiguration-id')->patch($requestBody)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Beta.Identity.Governance

$params = @{
	"@odata.type" = "#microsoft.graph.tooManyGlobalAdminsAssignedToTenantAlertConfiguration"
	isEnabled = "true"
	globalAdminCountThreshold = 
	percentageOfGlobalAdminsOutOfRolesThreshold = 
}

Update-MgBetaIdentityGovernanceRoleManagementAlertConfiguration -UnifiedRoleManagementAlertConfigurationId $unifiedRoleManagementAlertConfigurationId -BodyParameter $params
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.models.too_many_global_admins_assigned_to_tenant_alert_configuration import TooManyGlobalAdminsAssignedToTenantAlertConfiguration
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = TooManyGlobalAdminsAssignedToTenantAlertConfiguration(
	odata_type = "#microsoft.graph.tooManyGlobalAdminsAssignedToTenantAlertConfiguration",
	is_enabled = True,
	global_admin_count_threshold = 7,
	percentage_of_global_admins_out_of_roles_threshold = 70,
)

result = await graph_client.identity_governance.role_management_alerts.alert_configurations.by_unified_role_management_alert_configuration_id('unifiedRoleManagementAlertConfiguration-id').patch(request_body)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

```http
HTTP/1.1 204 No Content
```
