<!-- Source: https://learn.microsoft.com/en-us/graph/how-to-pim-alerts -->
<!-- Sitemap-Last-Modified: 2025-09-29 -->

# Manage security alerts for Microsoft Entra roles by using PIM APIs

Privileged Identity Management \(PIM\) for Microsoft Entra roles generates alerts when it detects suspicious or unsafe settings for Microsoft Entra roles in your tenant. This article describes scenarios for managing PIM alerts by using Microsoft Graph.

For more information about API resources for managing PIM security alerts, see [Security alerts for Microsoft Entra roles](https://learn.microsoft.com/en-us/graph/api/resources/privilegedidentitymanagementv3-overview?view=graph-rest-beta&preserve-view=true#security-alerts-for-azure-ad-roles).

Note

PIM security alerts are currently on the `/beta` endpoint only and are available only for Microsoft Entra roles.

## Prerequisites

- Understand [PIM for Microsoft Entra roles APIs](https://learn.microsoft.com/en-us/graph/api/resources/privilegedidentitymanagementv3-overview).
- In this article, you call the APIs in a [delegated scenario](https://learn.microsoft.com/en-us/graph/auth-v2-user).

  - Sign in to an API client such as [Graph Explorer](https://aka.ms/ge) with administrative privileges to manage PIM rules. The *Privileged Role Administrator* role is the least privileged role sufficient to manage PIM rules.
  - Grant yourself the *RoleManagementAlert.ReadWrite.Directory* delegated permission.

## List all PIM alerts

### Request

Only alerts that relate to Microsoft Entra built-in roles and are scoped to the tenant \(`/`\) are supported. You can retrieve these alerts by using the following request. If you don't specify the correct **scope** and **scopeType**, the request returns a `400 Bad Request` error.

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [PowerShell](#tabpanel_1_powershell)
- [Python](#tabpanel_1_python)

```msgraph
GET https://graph.microsoft.com/beta/identityGovernance/roleManagementAlerts/alerts?$filter=scopeId eq '/' and scopeType eq 'DirectoryRole'
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.IdentityGovernance.RoleManagementAlerts.Alerts.GetAsync((requestConfiguration) =>
{
	requestConfiguration.QueryParameters.Filter = "scopeId eq '/' and scopeType eq 'DirectoryRole'";
});
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```go


// Code snippets are only available for the latest major version. Current major version is $v0.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-beta-sdk-go"
	  graphidentitygovernance "github.com/microsoftgraph/msgraph-beta-sdk-go/identitygovernance"
	  //other-imports
)


requestFilter := "scopeId eq '/' and scopeType eq 'DirectoryRole'"

requestParameters := &graphidentitygovernance.RoleManagementAlertsAlertsRequestBuilderGetQueryParameters{
	Filter: &requestFilter,
}
configuration := &graphidentitygovernance.RoleManagementAlertsAlertsRequestBuilderGetRequestConfiguration{
	QueryParameters: requestParameters,
}

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
alerts, err := graphClient.IdentityGovernance().RoleManagementAlerts().Alerts().Get(context.Background(), configuration)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

UnifiedRoleManagementAlertCollectionResponse result = graphClient.identityGovernance().roleManagementAlerts().alerts().get(requestConfiguration -> {
	requestConfiguration.queryParameters.filter = "scopeId eq '/' and scopeType eq 'DirectoryRole'";
});
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let alerts = await client.api('/identityGovernance/roleManagementAlerts/alerts')
	.version('beta')
	.filter('scopeId eq \'/\' and scopeType eq \'DirectoryRole\'')
	.get();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\IdentityGovernance\RoleManagementAlerts\Alerts\AlertsRequestBuilderGetRequestConfiguration;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestConfiguration = new AlertsRequestBuilderGetRequestConfiguration();
$queryParameters = AlertsRequestBuilderGetRequestConfiguration::createQueryParameters();
$queryParameters->filter = "scopeId eq '/' and scopeType eq 'DirectoryRole'";
$requestConfiguration->queryParameters = $queryParameters;


$result = $graphServiceClient->identityGovernance()->roleManagementAlerts()->alerts()->get($requestConfiguration)->wait();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```powershell

Import-Module Microsoft.Graph.Beta.Identity.Governance

Get-MgBetaIdentityGovernanceRoleManagementAlert -Filter "scopeId eq '/' and scopeType eq 'DirectoryRole'" 
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.identity_governance.role_management_alerts.alerts.alerts_request_builder import AlertsRequestBuilder
from kiota_abstractions.base_request_configuration import RequestConfiguration
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
query_params = AlertsRequestBuilder.AlertsRequestBuilderGetQueryParameters(
		filter = "scopeId eq '/' and scopeType eq 'DirectoryRole'",
)

request_configuration = RequestConfiguration(
query_parameters = query_params,
)

result = await graph_client.identity_governance.role_management_alerts.alerts.get(request_configuration = request_configuration)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
    "@odata.context": "https://graph.microsoft.com/beta/$metadata#identityGovernance/roleManagementAlerts/alerts",
    "@microsoft.graph.tips": "Use $select to choose only the properties your app needs, as this can lead to performance improvements. For example: GET identityGovernance/roleManagementAlerts/alerts?$select=alertDefinitionId,incidentCount",
    "value": [
        {
            "id": "DirectoryRole_3b0e753b-22fa-4c16-9bf2-470b80be80d6_InvalidLicenseAlert",
            "alertDefinitionId": "DirectoryRole_3b0e753b-22fa-4c16-9bf2-470b80be80d6_InvalidLicenseAlert",
            "scopeId": "/",
            "scopeType": "DirectoryRole",
            "incidentCount": 0,
            "isActive": false,
            "lastModifiedDateTime": "0001-01-01T08:00:00Z",
            "lastScannedDateTime": "2023-09-20T17:05:57.457Z"
        },
        {
            "id": "DirectoryRole_3b0e753b-22fa-4c16-9bf2-470b80be80d6_NoMfaOnRoleActivationAlert",
            "alertDefinitionId": "DirectoryRole_3b0e753b-22fa-4c16-9bf2-470b80be80d6_NoMfaOnRoleActivationAlert",
            "scopeId": "/",
            "scopeType": "DirectoryRole",
            "incidentCount": 0,
            "isActive": false,
            "lastModifiedDateTime": "0001-01-01T08:00:00Z",
            "lastScannedDateTime": "2023-09-20T17:06:01.25Z"
        },
        {
            "id": "DirectoryRole_3b0e753b-22fa-4c16-9bf2-470b80be80d6_RedundantAssignmentAlert",
            "alertDefinitionId": "DirectoryRole_3b0e753b-22fa-4c16-9bf2-470b80be80d6_RedundantAssignmentAlert",
            "scopeId": "/",
            "scopeType": "DirectoryRole",
            "incidentCount": 0,
            "isActive": false,
            "lastModifiedDateTime": "0001-01-01T08:00:00Z",
            "lastScannedDateTime": "2023-09-20T17:06:00.603Z"
        },
        {
            "id": "DirectoryRole_3b0e753b-22fa-4c16-9bf2-470b80be80d6_RolesAssignedOutsidePimAlert",
            "alertDefinitionId": "DirectoryRole_3b0e753b-22fa-4c16-9bf2-470b80be80d6_RolesAssignedOutsidePimAlert",
            "scopeId": "/",
            "scopeType": "DirectoryRole",
            "incidentCount": 0,
            "isActive": false,
            "lastModifiedDateTime": "0001-01-01T08:00:00Z",
            "lastScannedDateTime": "2023-09-20T17:05:57.78Z"
        },
        {
            "id": "DirectoryRole_3b0e753b-22fa-4c16-9bf2-470b80be80d6_SequentialActivationRenewalsAlert",
            "alertDefinitionId": "DirectoryRole_3b0e753b-22fa-4c16-9bf2-470b80be80d6_SequentialActivationRenewalsAlert",
            "scopeId": "/",
            "scopeType": "DirectoryRole",
            "incidentCount": 0,
            "isActive": false,
            "lastModifiedDateTime": "0001-01-01T08:00:00Z",
            "lastScannedDateTime": "2023-09-20T17:05:57.857Z"
        },
        {
            "id": "DirectoryRole_3b0e753b-22fa-4c16-9bf2-470b80be80d6_StaleSignInAlert",
            "alertDefinitionId": "DirectoryRole_3b0e753b-22fa-4c16-9bf2-470b80be80d6_StaleSignInAlert",
            "scopeId": "/",
            "scopeType": "DirectoryRole",
            "incidentCount": 0,
            "isActive": false,
            "lastModifiedDateTime": "0001-01-01T08:00:00Z",
            "lastScannedDateTime": "2023-09-20T17:06:03.117Z"
        },
        {
            "id": "DirectoryRole_3b0e753b-22fa-4c16-9bf2-470b80be80d6_TooManyGlobalAdminsAssignedToTenantAlert",
            "alertDefinitionId": "DirectoryRole_3b0e753b-22fa-4c16-9bf2-470b80be80d6_TooManyGlobalAdminsAssignedToTenantAlert",
            "scopeId": "/",
            "scopeType": "DirectoryRole",
            "incidentCount": 7,
            "isActive": true,
            "lastModifiedDateTime": "2023-09-20T17:06:01.363Z",
            "lastScannedDateTime": "2023-09-20T17:06:01.363Z"
        }
    ]
}
```

## Get a PIM alert

### Request

- [HTTP](#tabpanel_2_http)
- [C#](#tabpanel_2_csharp)
- [Go](#tabpanel_2_go)
- [Java](#tabpanel_2_java)
- [JavaScript](#tabpanel_2_javascript)
- [PHP](#tabpanel_2_php)
- [PowerShell](#tabpanel_2_powershell)
- [Python](#tabpanel_2_python)

```msgraph
GET https://graph.microsoft.com/beta/identityGovernance/roleManagementAlerts/alerts/DirectoryRole_3b0e753b-22fa-4c16-9bf2-470b80be80d6_TooManyGlobalAdminsAssignedToTenantAlert
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.IdentityGovernance.RoleManagementAlerts.Alerts["{unifiedRoleManagementAlert-id}"].GetAsync();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```go


// Code snippets are only available for the latest major version. Current major version is $v0.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-beta-sdk-go"
	  //other-imports
)


// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
alerts, err := graphClient.IdentityGovernance().RoleManagementAlerts().Alerts().ByUnifiedRoleManagementAlertId("unifiedRoleManagementAlert-id").Get(context.Background(), nil)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

UnifiedRoleManagementAlert result = graphClient.identityGovernance().roleManagementAlerts().alerts().byUnifiedRoleManagementAlertId("{unifiedRoleManagementAlert-id}").get();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let unifiedRoleManagementAlert = await client.api('/identityGovernance/roleManagementAlerts/alerts/DirectoryRole_3b0e753b-22fa-4c16-9bf2-470b80be80d6_TooManyGlobalAdminsAssignedToTenantAlert')
	.version('beta')
	.get();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);


$result = $graphServiceClient->identityGovernance()->roleManagementAlerts()->alerts()->byUnifiedRoleManagementAlertId('unifiedRoleManagementAlert-id')->get()->wait();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```powershell

Import-Module Microsoft.Graph.Beta.Identity.Governance

Get-MgBetaIdentityGovernanceRoleManagementAlert -UnifiedRoleManagementAlertId $unifiedRoleManagementAlertId
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python

result = await graph_client.identity_governance.role_management_alerts.alerts.by_unified_role_management_alert_id('unifiedRoleManagementAlert-id').get()
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
    "@odata.context": "https://graph.microsoft.com/beta/$metadata#identityGovernance/roleManagementAlerts/alerts/$entity",
    "@microsoft.graph.tips": "Use $select to choose only the properties your app needs, as this can lead to performance improvements. For example: GET identityGovernance/roleManagementAlerts/alerts('<key>')?$select=alertDefinitionId,incidentCount",
    "id": "DirectoryRole_3b0e753b-22fa-4c16-9bf2-470b80be80d6_TooManyGlobalAdminsAssignedToTenantAlert",
    "alertDefinitionId": "DirectoryRole_3b0e753b-22fa-4c16-9bf2-470b80be80d6_TooManyGlobalAdminsAssignedToTenantAlert",
    "scopeId": "/",
    "scopeType": "DirectoryRole",
    "incidentCount": 7,
    "isActive": true,
    "lastModifiedDateTime": "2023-09-20T17:06:01.363Z",
    "lastScannedDateTime": "2023-09-20T17:06:01.363Z"
}
```

## Get a security alert and expand the relationships to read the definition, configuration, and incidents

### Request

You can read a security alert and its definition, configuration, and related incidents in the tenant in a single query. Either expand all relationships by using the wildcard character \(\*\), or expand the relationships individually by using `$expand=alertDefinition,alertConfiguration,alertIncidents`. This request helps you avoid retrieving the alert definition, configuration, and incidents separately, and then correlating them to the alert.

- [HTTP](#tabpanel_3_http)
- [C#](#tabpanel_3_csharp)
- [Go](#tabpanel_3_go)
- [Java](#tabpanel_3_java)
- [JavaScript](#tabpanel_3_javascript)
- [PHP](#tabpanel_3_php)
- [PowerShell](#tabpanel_3_powershell)
- [Python](#tabpanel_3_python)

```msgraph
GET https://graph.microsoft.com/beta/identityGovernance/roleManagementAlerts/alerts/DirectoryRole_3b0e753b-22fa-4c16-9bf2-470b80be80d6_TooManyGlobalAdminsAssignedToTenantAlert?$expand=*
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.IdentityGovernance.RoleManagementAlerts.Alerts["{unifiedRoleManagementAlert-id}"].GetAsync((requestConfiguration) =>
{
	requestConfiguration.QueryParameters.Expand = new string []{ "*" };
});
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```go


// Code snippets are only available for the latest major version. Current major version is $v0.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-beta-sdk-go"
	  graphidentitygovernance "github.com/microsoftgraph/msgraph-beta-sdk-go/identitygovernance"
	  //other-imports
)

requestParameters := &graphidentitygovernance.RoleManagementAlertsAlertsItemRequestBuilderGetQueryParameters{
	Expand: [] string {"*"},
}
configuration := &graphidentitygovernance.RoleManagementAlertsAlertsItemRequestBuilderGetRequestConfiguration{
	QueryParameters: requestParameters,
}

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
alerts, err := graphClient.IdentityGovernance().RoleManagementAlerts().Alerts().ByUnifiedRoleManagementAlertId("unifiedRoleManagementAlert-id").Get(context.Background(), configuration)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

UnifiedRoleManagementAlert result = graphClient.identityGovernance().roleManagementAlerts().alerts().byUnifiedRoleManagementAlertId("{unifiedRoleManagementAlert-id}").get(requestConfiguration -> {
	requestConfiguration.queryParameters.expand = new String []{"*"};
});
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\IdentityGovernance\RoleManagementAlerts\Alerts\Item\UnifiedRoleManagementAlertItemRequestBuilderGetRequestConfiguration;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestConfiguration = new UnifiedRoleManagementAlertItemRequestBuilderGetRequestConfiguration();
$queryParameters = UnifiedRoleManagementAlertItemRequestBuilderGetRequestConfiguration::createQueryParameters();
$queryParameters->expand = ["*"];
$requestConfiguration->queryParameters = $queryParameters;


$result = $graphServiceClient->identityGovernance()->roleManagementAlerts()->alerts()->byUnifiedRoleManagementAlertId('unifiedRoleManagementAlert-id')->get($requestConfiguration)->wait();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```powershell

Import-Module Microsoft.Graph.Beta.Identity.Governance

Get-MgBetaIdentityGovernanceRoleManagementAlert -UnifiedRoleManagementAlertId $unifiedRoleManagementAlertId -ExpandProperty "*" 
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.identity_governance.role_management_alerts.alerts.item.unified_role_management_alert_item_request_builder import UnifiedRoleManagementAlertItemRequestBuilder
from kiota_abstractions.base_request_configuration import RequestConfiguration
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
query_params = UnifiedRoleManagementAlertItemRequestBuilder.UnifiedRoleManagementAlertItemRequestBuilderGetQueryParameters(
		expand = ["*"],
)

request_configuration = RequestConfiguration(
query_parameters = query_params,
)

result = await graph_client.identity_governance.role_management_alerts.alerts.by_unified_role_management_alert_id('unifiedRoleManagementAlert-id').get(request_configuration = request_configuration)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
    "@odata.context": "https://graph.microsoft.com/beta/$metadata#identityGovernance/roleManagementAlerts/alerts(alertConfiguration(),alertDefinition(),alertIncidents())/$entity",
    "@microsoft.graph.tips": "Use $select to choose only the properties your app needs, as this can lead to performance improvements. For example: GET identityGovernance/roleManagementAlerts/alerts('<key>')?$select=alertDefinitionId,incidentCount",
    "id": "DirectoryRole_3b0e753b-22fa-4c16-9bf2-470b80be80d6_TooManyGlobalAdminsAssignedToTenantAlert",
    "alertDefinitionId": "DirectoryRole_3b0e753b-22fa-4c16-9bf2-470b80be80d6_TooManyGlobalAdminsAssignedToTenantAlert",
    "scopeId": "/",
    "scopeType": "DirectoryRole",
    "incidentCount": 7,
    "isActive": true,
    "lastModifiedDateTime": "2023-09-20T17:06:01.363Z",
    "lastScannedDateTime": "2023-09-20T17:06:01.363Z",
    "alertConfiguration": {
        "@odata.type": "#microsoft.graph.tooManyGlobalAdminsAssignedToTenantAlertConfiguration",
        "id": "DirectoryRole_3b0e753b-22fa-4c16-9bf2-470b80be80d6_TooManyGlobalAdminsAssignedToTenantAlert",
        "alertDefinitionId": "DirectoryRole_3b0e753b-22fa-4c16-9bf2-470b80be80d6_TooManyGlobalAdminsAssignedToTenantAlert",
        "scopeType": "DirectoryRole",
        "scopeId": "/",
        "isEnabled": true,
        "globalAdminCountThreshold": 3,
        "percentageOfGlobalAdminsOutOfRolesThreshold": 10
    },
    "alertDefinition": {
        "id": "DirectoryRole_3b0e753b-22fa-4c16-9bf2-470b80be80d6_TooManyGlobalAdminsAssignedToTenantAlert",
        "displayName": "There are too many global administrators",
        "scopeType": "DirectoryRole",
        "scopeId": "/",
        "description": "The percentage of global administrators is high, relative to other privileged roles. It is recommended to use least privileged roles, with just enough privileges to perform the required tasks.",
        "severityLevel": "low",
        "securityImpact": "Global administrator is the highest privileged role. If a Global Administrator is compromised, the attacker gains access to all of their permissions, which puts your whole system at risk.",
        "mitigationSteps": "·Review the users in the list and remove any that do not absolutely need the Global Administrator role.·Assign lower privileged roles to these users instead.",
        "howToPrevent": "Assign users the least privileged role they need.",
        "isRemediatable": true,
        "isConfigurable": true
    },
    "alertIncidents@odata.context": "https://graph.microsoft.com/beta/$metadata#identityGovernance/roleManagementAlerts/alerts('DirectoryRole_3b0e753b-22fa-4c16-9bf2-470b80be80d6_TooManyGlobalAdminsAssignedToTenantAlert')/alertIncidents",
    "alertIncidents": [
        {
            "@odata.type": "#microsoft.graph.tooManyGlobalAdminsAssignedToTenantAlertIncident",
            "id": "60caa50f-7863-4f48-bf97-2a8fb990b681",
            "assigneeId": "60caa50f-7863-4f48-bf97-2a8fb990b681",
            "assigneeDisplayName": "MOD Administrator",
            "assigneeUserPrincipalName": "admin@contoso.com"
        },
        {
            "@odata.type": "#microsoft.graph.tooManyGlobalAdminsAssignedToTenantAlertIncident",
            "id": "6dd82b18-d45f-4346-bf87-e9700db41849",
            "assigneeId": "6dd82b18-d45f-4346-bf87-e9700db41849",
            "assigneeDisplayName": "Nestor Wilke",
            "assigneeUserPrincipalName": "NestorW@Contoso.com"
        },
        {
            "@odata.type": "#microsoft.graph.tooManyGlobalAdminsAssignedToTenantAlertIncident",
            "id": "87404028-0c5b-4d0a-9d9d-3150e4b5ce74",
            "assigneeId": "87404028-0c5b-4d0a-9d9d-3150e4b5ce74",
            "assigneeDisplayName": "Isaiah Langer",
            "assigneeUserPrincipalName": "IsaiahL@Contoso.com"
        },
        {
            "@odata.type": "#microsoft.graph.tooManyGlobalAdminsAssignedToTenantAlertIncident",
            "id": "143ebd3d-e522-485c-aa52-94675ee83e6c",
            "assigneeId": "143ebd3d-e522-485c-aa52-94675ee83e6c",
            "assigneeDisplayName": "Lidia Holloway",
            "assigneeUserPrincipalName": "LidiaH@Contoso.com"
        },
        {
            "@odata.type": "#microsoft.graph.tooManyGlobalAdminsAssignedToTenantAlertIncident",
            "id": "2832ca72-700e-4f20-a3c7-97028803a95b",
            "assigneeId": "2832ca72-700e-4f20-a3c7-97028803a95b",
            "assigneeDisplayName": "Microsoft Service Account",
            "assigneeUserPrincipalName": "ms-serviceaccount@Contoso.com"
        },
        {
            "@odata.type": "#microsoft.graph.tooManyGlobalAdminsAssignedToTenantAlertIncident",
            "id": "31336492-bf1b-48bb-a072-e554e4f992fc",
            "assigneeId": "31336492-bf1b-48bb-a072-e554e4f992fc",
            "assigneeDisplayName": "Megan Bowen",
            "assigneeUserPrincipalName": "MeganB@Contoso.com"
        },
        {
            "@odata.type": "#microsoft.graph.tooManyGlobalAdminsAssignedToTenantAlertIncident",
            "id": "308110a6-4f71-49c2-bbef-c6dbda50b392",
            "assigneeId": "308110a6-4f71-49c2-bbef-c6dbda50b392",
            "assigneeDisplayName": "Allan Deyoung",
            "assigneeUserPrincipalName": "AllanD@Contoso.com"
        }
    ]
}
```

## Get details of the incidents that triggered an alert

### Request

- [HTTP](#tabpanel_4_http)
- [C#](#tabpanel_4_csharp)
- [Go](#tabpanel_4_go)
- [Java](#tabpanel_4_java)
- [JavaScript](#tabpanel_4_javascript)
- [PHP](#tabpanel_4_php)
- [PowerShell](#tabpanel_4_powershell)
- [Python](#tabpanel_4_python)

```msgraph
GET https://graph.microsoft.com/beta/identityGovernance/roleManagementAlerts/alerts/DirectoryRole_3b0e753b-22fa-4c16-9bf2-470b80be80d6_TooManyGlobalAdminsAssignedToTenantAlert/alertIncidents
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.IdentityGovernance.RoleManagementAlerts.Alerts["{unifiedRoleManagementAlert-id}"].AlertIncidents.GetAsync();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```go


// Code snippets are only available for the latest major version. Current major version is $v0.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-beta-sdk-go"
	  //other-imports
)


// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
alertIncidents, err := graphClient.IdentityGovernance().RoleManagementAlerts().Alerts().ByUnifiedRoleManagementAlertId("unifiedRoleManagementAlert-id").AlertIncidents().Get(context.Background(), nil)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

UnifiedRoleManagementAlertIncidentCollectionResponse result = graphClient.identityGovernance().roleManagementAlerts().alerts().byUnifiedRoleManagementAlertId("{unifiedRoleManagementAlert-id}").alertIncidents().get();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let alertIncidents = await client.api('/identityGovernance/roleManagementAlerts/alerts/DirectoryRole_3b0e753b-22fa-4c16-9bf2-470b80be80d6_TooManyGlobalAdminsAssignedToTenantAlert/alertIncidents')
	.version('beta')
	.get();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);


$result = $graphServiceClient->identityGovernance()->roleManagementAlerts()->alerts()->byUnifiedRoleManagementAlertId('unifiedRoleManagementAlert-id')->alertIncidents()->get()->wait();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```powershell

Import-Module Microsoft.Graph.Beta.Identity.Governance

Get-MgBetaIdentityGovernanceRoleManagementAlertIncident -UnifiedRoleManagementAlertId $unifiedRoleManagementAlertId
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python

result = await graph_client.identity_governance.role_management_alerts.alerts.by_unified_role_management_alert_id('unifiedRoleManagementAlert-id').alert_incidents.get()
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
    "@odata.context": "https://graph.microsoft.com/beta/$metadata#identityGovernance/roleManagementAlerts/alerts('DirectoryRole_3b0e753b-22fa-4c16-9bf2-470b80be80d6_TooManyGlobalAdminsAssignedToTenantAlert')/alertIncidents",
    "@microsoft.graph.tips": "Use $select to choose only the properties your app needs, as this can lead to performance improvements. For example: GET identityGovernance/roleManagementAlerts/alerts('<key>')/alertIncidents?$select=id",
    "value": [
        {
            "@odata.type": "#microsoft.graph.tooManyGlobalAdminsAssignedToTenantAlertIncident",
            "id": "143ebd3d-e522-485c-aa52-94675ee83e6c",
            "assigneeId": "143ebd3d-e522-485c-aa52-94675ee83e6c",
            "assigneeDisplayName": "Lidia Holloway",
            "assigneeUserPrincipalName": "LidiaH@contoso.com"
        },
        {
            "@odata.type": "#microsoft.graph.tooManyGlobalAdminsAssignedToTenantAlertIncident",
            "id": "2832ca72-700e-4f20-a3c7-97028803a95b",
            "assigneeId": "2832ca72-700e-4f20-a3c7-97028803a95b",
            "assigneeDisplayName": "Microsoft Service Account",
            "assigneeUserPrincipalName": "ms-serviceaccount@contoso.com"
        },
        {
            "@odata.type": "#microsoft.graph.tooManyGlobalAdminsAssignedToTenantAlertIncident",
            "id": "308110a6-4f71-49c2-bbef-c6dbda50b392",
            "assigneeId": "308110a6-4f71-49c2-bbef-c6dbda50b392",
            "assigneeDisplayName": "Allan Deyoung",
            "assigneeUserPrincipalName": "AllanD@contoso.com"
        },
        {
            "@odata.type": "#microsoft.graph.tooManyGlobalAdminsAssignedToTenantAlertIncident",
            "id": "31336492-bf1b-48bb-a072-e554e4f992fc",
            "assigneeId": "31336492-bf1b-48bb-a072-e554e4f992fc",
            "assigneeDisplayName": "Megan Bowen",
            "assigneeUserPrincipalName": "MeganB@contoso.com"
        },
        {
            "@odata.type": "#microsoft.graph.tooManyGlobalAdminsAssignedToTenantAlertIncident",
            "id": "60caa50f-7863-4f48-bf97-2a8fb990b681",
            "assigneeId": "60caa50f-7863-4f48-bf97-2a8fb990b681",
            "assigneeDisplayName": "MOD Administrator",
            "assigneeUserPrincipalName": "admin@contoso.com"
        },
        {
            "@odata.type": "#microsoft.graph.tooManyGlobalAdminsAssignedToTenantAlertIncident",
            "id": "6dd82b18-d45f-4346-bf87-e9700db41849",
            "assigneeId": "6dd82b18-d45f-4346-bf87-e9700db41849",
            "assigneeDisplayName": "Nestor Wilke",
            "assigneeUserPrincipalName": "NestorW@contoso.com"
        },
        {
            "@odata.type": "#microsoft.graph.tooManyGlobalAdminsAssignedToTenantAlertIncident",
            "id": "87404028-0c5b-4d0a-9d9d-3150e4b5ce74",
            "assigneeId": "87404028-0c5b-4d0a-9d9d-3150e4b5ce74",
            "assigneeDisplayName": "Isaiah Langer",
            "assigneeUserPrincipalName": "IsaiahL@contoso.com"
        }
    ]
}
```

## Dismiss an alert

You dismiss an alert by setting the **isActive** property to `false`. When you dismiss an alert, PIM no longer scans the alert in your tenant for incidents. Existing incidents can still be queried, but no new incidents are generated. You can re-enable the alert by setting the `isActive` property to `true` or by [refreshing the alert type](#refresh-alerts).

The request returns a `204 No Content` response.

- [HTTP](#tabpanel_5_http)
- [C#](#tabpanel_5_csharp)
- [Go](#tabpanel_5_go)
- [Java](#tabpanel_5_java)
- [JavaScript](#tabpanel_5_javascript)
- [PHP](#tabpanel_5_php)
- [PowerShell](#tabpanel_5_powershell)
- [Python](#tabpanel_5_python)

```http
PATCH https://graph.microsoft.com/beta/identityGovernance/roleManagementAlerts/alerts/DirectoryRole_3b0e753b-22fa-4c16-9bf2-470b80be80d6_RolesAssignedOutsidePimAlert
Content-Type: application/json

{
    "isActive": false
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.Models;

var requestBody = new UnifiedRoleManagementAlert
{
	IsActive = false,
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.IdentityGovernance.RoleManagementAlerts.Alerts["{unifiedRoleManagementAlert-id}"].PatchAsync(requestBody);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```go


// Code snippets are only available for the latest major version. Current major version is $v0.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-beta-sdk-go"
	  graphmodels "github.com/microsoftgraph/msgraph-beta-sdk-go/models"
	  //other-imports
)

requestBody := graphmodels.NewUnifiedRoleManagementAlert()
isActive := false
requestBody.SetIsActive(&isActive) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
alerts, err := graphClient.IdentityGovernance().RoleManagementAlerts().Alerts().ByUnifiedRoleManagementAlertId("unifiedRoleManagementAlert-id").Patch(context.Background(), requestBody, nil)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

UnifiedRoleManagementAlert unifiedRoleManagementAlert = new UnifiedRoleManagementAlert();
unifiedRoleManagementAlert.setIsActive(false);
UnifiedRoleManagementAlert result = graphClient.identityGovernance().roleManagementAlerts().alerts().byUnifiedRoleManagementAlertId("{unifiedRoleManagementAlert-id}").patch(unifiedRoleManagementAlert);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const unifiedRoleManagementAlert = {
    isActive: false
};

await client.api('/identityGovernance/roleManagementAlerts/alerts/DirectoryRole_3b0e753b-22fa-4c16-9bf2-470b80be80d6_RolesAssignedOutsidePimAlert')
	.version('beta')
	.update(unifiedRoleManagementAlert);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Models\UnifiedRoleManagementAlert;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new UnifiedRoleManagementAlert();
$requestBody->setIsActive(false);

$result = $graphServiceClient->identityGovernance()->roleManagementAlerts()->alerts()->byUnifiedRoleManagementAlertId('unifiedRoleManagementAlert-id')->patch($requestBody)->wait();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.models.unified_role_management_alert import UnifiedRoleManagementAlert
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = UnifiedRoleManagementAlert(
	is_active = False,
)

result = await graph_client.identity_governance.role_management_alerts.alerts.by_unified_role_management_alert_id('unifiedRoleManagementAlert-id').patch(request_body)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

## Refresh alerts

In PIM, you can refresh a single alert type or all alerts in the tenant. When you refresh either type, PIM scans the tenant for incidents that match the alerts. This request is a long-running operation and returns a **Location** header that you can use to poll the status of the operation - whether the refresh succeeded or failed. In a successful refresh, PIM includes alerts that you previously dismissed, reactivates dismissed alerts \(updates **isActive** to `true`\), and scans and generates new incidents for the alerts.

### Refresh a single alert type

#### Request

- [HTTP](#tabpanel_6_http)
- [C#](#tabpanel_6_csharp)
- [Go](#tabpanel_6_go)
- [Java](#tabpanel_6_java)
- [JavaScript](#tabpanel_6_javascript)
- [PHP](#tabpanel_6_php)
- [PowerShell](#tabpanel_6_powershell)
- [Python](#tabpanel_6_python)

```http
POST https://graph.microsoft.com/beta/identityGovernance/roleManagementAlerts/alerts/DirectoryRole_3b0e753b-22fa-4c16-9bf2-470b80be80d6_RolesAssignedOutsidePimAlert/refresh
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
await graphClient.IdentityGovernance.RoleManagementAlerts.Alerts["{unifiedRoleManagementAlert-id}"].Refresh.PostAsync();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```go


// Code snippets are only available for the latest major version. Current major version is $v0.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-beta-sdk-go"
	  //other-imports
)


// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
graphClient.IdentityGovernance().RoleManagementAlerts().Alerts().ByUnifiedRoleManagementAlertId("unifiedRoleManagementAlert-id").Refresh().Post(context.Background(), nil)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

graphClient.identityGovernance().roleManagementAlerts().alerts().byUnifiedRoleManagementAlertId("{unifiedRoleManagementAlert-id}").refresh().post();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

await client.api('/identityGovernance/roleManagementAlerts/alerts/DirectoryRole_3b0e753b-22fa-4c16-9bf2-470b80be80d6_RolesAssignedOutsidePimAlert/refresh')
	.version('beta')
	.post();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);


$graphServiceClient->identityGovernance()->roleManagementAlerts()->alerts()->byUnifiedRoleManagementAlertId('unifiedRoleManagementAlert-id')->refresh()->post()->wait();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```powershell

Import-Module Microsoft.Graph.Beta.Identity.Governance

Update-MgBetaIdentityGovernanceRoleManagementAlert -UnifiedRoleManagementAlertId $unifiedRoleManagementAlertId
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python

await graph_client.identity_governance.role_management_alerts.alerts.by_unified_role_management_alert_id('unifiedRoleManagementAlert-id').refresh.post()
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

### Response

```http
HTTP/1.1 202 Accepted
Location: https://graph.microsoft.com/beta/identityGovernance/roleManagementAlerts/operations/refresh:DirectoryRole_3b0e753b-22fa-4c16-9bf2-470b80be80d6_RolesAssignedOutsidePimAlert
```

### Refresh all alert types in the tenant

#### Request

Only the tenant scope \(`/`\) and `DirectoryRole` scope type are supported.

- [HTTP](#tabpanel_7_http)
- [C#](#tabpanel_7_csharp)
- [Go](#tabpanel_7_go)
- [Java](#tabpanel_7_java)
- [JavaScript](#tabpanel_7_javascript)
- [PHP](#tabpanel_7_php)
- [PowerShell](#tabpanel_7_powershell)
- [Python](#tabpanel_7_python)

```http
POST https://graph.microsoft.com/beta/identityGovernance/roleManagementAlerts/alerts/refresh
Content-Type: application/json

{
    "scopeId" : "/",
    "scopeType" : "DirectoryRole"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.IdentityGovernance.RoleManagementAlerts.Alerts.Refresh;

var requestBody = new RefreshPostRequestBody
{
	ScopeId = "/",
	ScopeType = "DirectoryRole",
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
await graphClient.IdentityGovernance.RoleManagementAlerts.Alerts.Refresh.PostAsync(requestBody);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```go


// Code snippets are only available for the latest major version. Current major version is $v0.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-beta-sdk-go"
	  graphidentitygovernance "github.com/microsoftgraph/msgraph-beta-sdk-go/identitygovernance"
	  //other-imports
)

requestBody := graphidentitygovernance.NewRefreshPostRequestBody()
scopeId := "/"
requestBody.SetScopeId(&scopeId) 
scopeType := "DirectoryRole"
requestBody.SetScopeType(&scopeType) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
graphClient.IdentityGovernance().RoleManagementAlerts().Alerts().Refresh().Post(context.Background(), requestBody, nil)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.beta.identitygovernance.rolemanagementalerts.alerts.refresh.RefreshPostRequestBody refreshPostRequestBody = new com.microsoft.graph.beta.identitygovernance.rolemanagementalerts.alerts.refresh.RefreshPostRequestBody();
refreshPostRequestBody.setScopeId("/");
refreshPostRequestBody.setScopeType("DirectoryRole");
graphClient.identityGovernance().roleManagementAlerts().alerts().refresh().post(refreshPostRequestBody);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const refresh = {
    scopeId: '/',
    scopeType: 'DirectoryRole'
};

await client.api('/identityGovernance/roleManagementAlerts/alerts/refresh')
	.version('beta')
	.post(refresh);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\IdentityGovernance\RoleManagementAlerts\Alerts\Refresh\RefreshPostRequestBody;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new RefreshPostRequestBody();
$requestBody->setScopeId('/');
$requestBody->setScopeType('DirectoryRole');

$graphServiceClient->identityGovernance()->roleManagementAlerts()->alerts()->refresh()->post($requestBody)->wait();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.identitygovernance.rolemanagementalerts.alerts.refresh.refresh_post_request_body import RefreshPostRequestBody
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = RefreshPostRequestBody(
	scope_id = "/",
	scope_type = "DirectoryRole",
)

await graph_client.identity_governance.role_management_alerts.alerts.refresh.post(request_body)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

#### Response

```http
HTTP/1.1 202 Accepted
Location: https://graph.microsoft.com/beta/identityGovernance/roleManagementAlerts/operations/refresh:DirectoryRole_3b0e753b-22fa-4c16-9bf2-470b80be80d6_RolesAssignedOutsidePimAlert
```

## Update an alert configuration

Updating an alert configuration means changing the tenant-specific settings that control how PIM scans the tenant for incidents that match the alert type. For example, you can change whether to scan the alert in the tenant or you can change the threshold that when crossed triggers a known incident.

- [HTTP](#tabpanel_8_http)
- [C#](#tabpanel_8_csharp)
- [Go](#tabpanel_8_go)
- [Java](#tabpanel_8_java)
- [JavaScript](#tabpanel_8_javascript)
- [PHP](#tabpanel_8_php)
- [PowerShell](#tabpanel_8_powershell)
- [Python](#tabpanel_8_python)

```http
PATCH https://graph.microsoft.com/beta/identityGovernance/roleManagementAlerts/alertConfigurations/DirectoryRole_3b0e753b-22fa-4c16-9bf2-470b80be80d6_TooManyGlobalAdminsAssignedToTenantAlert
Content-Type: application/json

{
    "@odata.type": "#microsoft.graph.tooManyGlobalAdminsAssignedToTenantAlertConfiguration",
    "isEnabled": true,
    "globalAdminCountThreshold": 4,
    "percentageOfGlobalAdminsOutOfRolesThreshold": 10
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
	GlobalAdminCountThreshold = 4,
	PercentageOfGlobalAdminsOutOfRolesThreshold = 10,
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.IdentityGovernance.RoleManagementAlerts.AlertConfigurations["{unifiedRoleManagementAlertConfiguration-id}"].PatchAsync(requestBody);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

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
globalAdminCountThreshold := int32(4)
requestBody.SetGlobalAdminCountThreshold(&globalAdminCountThreshold) 
percentageOfGlobalAdminsOutOfRolesThreshold := int32(10)
requestBody.SetPercentageOfGlobalAdminsOutOfRolesThreshold(&percentageOfGlobalAdminsOutOfRolesThreshold) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
alertConfigurations, err := graphClient.IdentityGovernance().RoleManagementAlerts().AlertConfigurations().ByUnifiedRoleManagementAlertConfigurationId("unifiedRoleManagementAlertConfiguration-id").Patch(context.Background(), requestBody, nil)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

TooManyGlobalAdminsAssignedToTenantAlertConfiguration unifiedRoleManagementAlertConfiguration = new TooManyGlobalAdminsAssignedToTenantAlertConfiguration();
unifiedRoleManagementAlertConfiguration.setOdataType("#microsoft.graph.tooManyGlobalAdminsAssignedToTenantAlertConfiguration");
unifiedRoleManagementAlertConfiguration.setIsEnabled(true);
unifiedRoleManagementAlertConfiguration.setGlobalAdminCountThreshold(4);
unifiedRoleManagementAlertConfiguration.setPercentageOfGlobalAdminsOutOfRolesThreshold(10);
UnifiedRoleManagementAlertConfiguration result = graphClient.identityGovernance().roleManagementAlerts().alertConfigurations().byUnifiedRoleManagementAlertConfigurationId("{unifiedRoleManagementAlertConfiguration-id}").patch(unifiedRoleManagementAlertConfiguration);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const unifiedRoleManagementAlertConfiguration = {
    '@odata.type': '#microsoft.graph.tooManyGlobalAdminsAssignedToTenantAlertConfiguration',
    isEnabled: true,
    globalAdminCountThreshold: 4,
    percentageOfGlobalAdminsOutOfRolesThreshold: 10
};

await client.api('/identityGovernance/roleManagementAlerts/alertConfigurations/DirectoryRole_3b0e753b-22fa-4c16-9bf2-470b80be80d6_TooManyGlobalAdminsAssignedToTenantAlert')
	.version('beta')
	.update(unifiedRoleManagementAlertConfiguration);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Models\TooManyGlobalAdminsAssignedToTenantAlertConfiguration;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new TooManyGlobalAdminsAssignedToTenantAlertConfiguration();
$requestBody->setOdataType('#microsoft.graph.tooManyGlobalAdminsAssignedToTenantAlertConfiguration');
$requestBody->setIsEnabled(true);
$requestBody->setGlobalAdminCountThreshold(4);
$requestBody->setPercentageOfGlobalAdminsOutOfRolesThreshold(10);

$result = $graphServiceClient->identityGovernance()->roleManagementAlerts()->alertConfigurations()->byUnifiedRoleManagementAlertConfigurationId('unifiedRoleManagementAlertConfiguration-id')->patch($requestBody)->wait();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```powershell

Import-Module Microsoft.Graph.Beta.Identity.Governance

$params = @{
	"@odata.type" = "#microsoft.graph.tooManyGlobalAdminsAssignedToTenantAlertConfiguration"
	isEnabled = $true
	globalAdminCountThreshold = 
	percentageOfGlobalAdminsOutOfRolesThreshold = 
}

Update-MgBetaIdentityGovernanceRoleManagementAlertConfiguration -UnifiedRoleManagementAlertConfigurationId $unifiedRoleManagementAlertConfigurationId -BodyParameter $params
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.models.too_many_global_admins_assigned_to_tenant_alert_configuration import TooManyGlobalAdminsAssignedToTenantAlertConfiguration
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = TooManyGlobalAdminsAssignedToTenantAlertConfiguration(
	odata_type = "#microsoft.graph.tooManyGlobalAdminsAssignedToTenantAlertConfiguration",
	is_enabled = True,
	global_admin_count_threshold = 4,
	percentage_of_global_admins_out_of_roles_threshold = 10,
)

result = await graph_client.identity_governance.role_management_alerts.alert_configurations.by_unified_role_management_alert_configuration_id('unifiedRoleManagementAlertConfiguration-id').patch(request_body)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

The request returns a `204 No Content` response.

## Remediate an alert incident

Remediating an alert incident means requesting Microsoft Entra ID to apply the mitigation steps that are defined in the alert definition. For example, if the alert definition recommends that you remove a user from a role, remediating the incident means that Microsoft Entra ID removes the user from the role.

### Request

- [HTTP](#tabpanel_9_http)
- [C#](#tabpanel_9_csharp)
- [Go](#tabpanel_9_go)
- [Java](#tabpanel_9_java)
- [JavaScript](#tabpanel_9_javascript)
- [PHP](#tabpanel_9_php)
- [PowerShell](#tabpanel_9_powershell)
- [Python](#tabpanel_9_python)

```http
POST https://graph.microsoft.com/beta/identityGovernance/roleManagementAlerts/alerts/DirectoryRole_3b0e753b-22fa-4c16-9bf2-470b80be80d6_RolesAssignedOutsidePimAlert/alertIncidents/9e864769-63e3-4635-8069-551bcd46183d/remediate
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
await graphClient.IdentityGovernance.RoleManagementAlerts.Alerts["{unifiedRoleManagementAlert-id}"].AlertIncidents["{unifiedRoleManagementAlertIncident-id}"].Remediate.PostAsync();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```go


// Code snippets are only available for the latest major version. Current major version is $v0.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-beta-sdk-go"
	  //other-imports
)


// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
graphClient.IdentityGovernance().RoleManagementAlerts().Alerts().ByUnifiedRoleManagementAlertId("unifiedRoleManagementAlert-id").AlertIncidents().ByUnifiedRoleManagementAlertIncidentId("unifiedRoleManagementAlertIncident-id").Remediate().Post(context.Background(), nil)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

graphClient.identityGovernance().roleManagementAlerts().alerts().byUnifiedRoleManagementAlertId("{unifiedRoleManagementAlert-id}").alertIncidents().byUnifiedRoleManagementAlertIncidentId("{unifiedRoleManagementAlertIncident-id}").remediate().post();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

await client.api('/identityGovernance/roleManagementAlerts/alerts/DirectoryRole_3b0e753b-22fa-4c16-9bf2-470b80be80d6_RolesAssignedOutsidePimAlert/alertIncidents/9e864769-63e3-4635-8069-551bcd46183d/remediate')
	.version('beta')
	.post();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);


$graphServiceClient->identityGovernance()->roleManagementAlerts()->alerts()->byUnifiedRoleManagementAlertId('unifiedRoleManagementAlert-id')->alertIncidents()->byUnifiedRoleManagementAlertIncidentId('unifiedRoleManagementAlertIncident-id')->remediate()->post()->wait();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```powershell

Import-Module Microsoft.Graph.Beta.Identity.Governance

Invoke-MgBetaRemediateIdentityGovernanceRoleManagementAlertIncident -UnifiedRoleManagementAlertId $unifiedRoleManagementAlertId -UnifiedRoleManagementAlertIncidentId $unifiedRoleManagementAlertIncidentId
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python

await graph_client.identity_governance.role_management_alerts.alerts.by_unified_role_management_alert_id('unifiedRoleManagementAlert-id').alert_incidents.by_unified_role_management_alert_incident_id('unifiedRoleManagementAlertIncident-id').remediate.post()
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

### Response

```http
HTTP/1.1 200 OK
```

## Related content

- [Tutorial: Assign Microsoft Entra roles through PIM](https://learn.microsoft.com/en-us/graph/tutorial-assign-azureadroles).
