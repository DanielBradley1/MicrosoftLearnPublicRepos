<!-- Source: https://learn.microsoft.com/en-us/graph/api/rolemanagementalert-list-alertdefinitions?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-11-13 -->

# List alertDefinitions

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Get a list of the [unifiedRoleManagementAlertDefinition](https://learn.microsoft.com/en-us/graph/api/resources/unifiedrolemanagementalertdefinition?view=graph-rest-beta) objects and their properties.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | RoleManagementAlert.Read.Directory | RoleManagementAlert.ReadWrite.Directory |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | RoleManagementAlert.Read.Directory | RoleManagementAlert.ReadWrite.Directory |

Important

For delegated access using work or school accounts, the signed-in user must be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) or a custom role that grants the permissions required for this operation. This operation supports the following built-in roles, which provide only the least privilege necessary:

- Privileged Role Administrator
- Global Reader
- Security Administrator
- Security Reader

## HTTP request

```http
GET /identityGovernance/roleManagementAlerts/alertDefinitions?$filter=scopeId eq 'scopeId' and scopeType eq 'scopeType'
```

## Optional query parameters

This method supports the `$select`, `$filter`, and `$expand` OData query parameters to help customize the response. For general information, see [OData query parameters](https://learn.microsoft.com/en-us/graph/query-parameters).

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and a collection of [unifiedRoleManagementAlertDefinition](https://learn.microsoft.com/en-us/graph/api/resources/unifiedrolemanagementalertdefinition?view=graph-rest-beta) object in the response body.

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

```msgraph
GET https://graph.microsoft.com/beta/identityGovernance/roleManagementAlerts/alertDefinitions?$filter=scopeId eq '/' and scopeType eq 'DirectoryRole'
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.IdentityGovernance.RoleManagementAlerts.AlertDefinitions.GetAsync((requestConfiguration) =>
{
	requestConfiguration.QueryParameters.Filter = "scopeId eq '/' and scopeType eq 'DirectoryRole'";
});
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
	  graphidentitygovernance "github.com/microsoftgraph/msgraph-beta-sdk-go/identitygovernance"
	  //other-imports
)


requestFilter := "scopeId eq '/' and scopeType eq 'DirectoryRole'"

requestParameters := &graphidentitygovernance.RoleManagementAlertsAlertDefinitionsRequestBuilderGetQueryParameters{
	Filter: &requestFilter,
}
configuration := &graphidentitygovernance.RoleManagementAlertsAlertDefinitionsRequestBuilderGetRequestConfiguration{
	QueryParameters: requestParameters,
}

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
alertDefinitions, err := graphClient.IdentityGovernance().RoleManagementAlerts().AlertDefinitions().Get(context.Background(), configuration)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

UnifiedRoleManagementAlertDefinitionCollectionResponse result = graphClient.identityGovernance().roleManagementAlerts().alertDefinitions().get(requestConfiguration -> {
	requestConfiguration.queryParameters.filter = "scopeId eq '/' and scopeType eq 'DirectoryRole'";
});
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let alertDefinitions = await client.api('/identityGovernance/roleManagementAlerts/alertDefinitions')
	.version('beta')
	.filter('scopeId eq \'/\' and scopeType eq \'DirectoryRole\'')
	.get();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\IdentityGovernance\RoleManagementAlerts\AlertDefinitions\AlertDefinitionsRequestBuilderGetRequestConfiguration;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestConfiguration = new AlertDefinitionsRequestBuilderGetRequestConfiguration();
$queryParameters = AlertDefinitionsRequestBuilderGetRequestConfiguration::createQueryParameters();
$queryParameters->filter = "scopeId eq '/' and scopeType eq 'DirectoryRole'";
$requestConfiguration->queryParameters = $queryParameters;


$result = $graphServiceClient->identityGovernance()->roleManagementAlerts()->alertDefinitions()->get($requestConfiguration)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Beta.Identity.Governance

Get-MgBetaIdentityGovernanceRoleManagementAlertDefinition -Filter "scopeId eq '/' and scopeType eq 'DirectoryRole'" 
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.identity_governance.role_management_alerts.alert_definitions.alert_definitions_request_builder import AlertDefinitionsRequestBuilder
from kiota_abstractions.base_request_configuration import RequestConfiguration
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
query_params = AlertDefinitionsRequestBuilder.AlertDefinitionsRequestBuilderGetQueryParameters(
		filter = "scopeId eq '/' and scopeType eq 'DirectoryRole'",
)

request_configuration = RequestConfiguration(
query_parameters = query_params,
)

result = await graph_client.identity_governance.role_management_alerts.alert_definitions.get(request_configuration = request_configuration)
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
    "@odata.context": "https://graph.microsoft.com/beta/$metadata#identityGovernance/roleManagementAlerts/alertDefinitions",
    "value": [
        {
            "id": "DirectoryRole_19356be4-7e93-4ed6-a7c6-0ae28454d125_InvalidLicenseAlert",
            "displayName": "The organization doesn't have Azure AD Premium P2",
            "scopeType": "DirectoryRole",
            "scopeId": "/",
            "description": "Azure AD Privileged Identity Management requires a license, but the tenant either doesn't have an Azure AD Premium P2 license, or a trial license has expired.  If you do not obtain a license, Azure AD Privileged Identity Management and its configuration will be removed from the tenant.",
            "severityLevel": "high",
            "securityImpact": "Administrators in the tenant will not be able to use Azure AD Privileged Identity Management for role activation, access reviews or other management tasks unless a license is present.",
            "mitigationSteps": "Purchase a license plan which includes Azure AD Premium P2 for all users who will be interacting with Azure AD PIM or with Azure AD Identity Protection.  More information on pricing and purchase options is at https://azure.microsoft.com/en-us/pricing/details/active-directory/",
            "howToPrevent": "To dismiss this alert, ensure there is a license on the tenant for Azure AD Premium P2.",
            "isRemediatable": false,
            "isConfigurable": false
        },
        {
            "id": "DirectoryRole_19356be4-7e93-4ed6-a7c6-0ae28454d125_NoMfaOnRoleActivationAlert",
            "displayName": "Roles don't require multi-factor authentication for activation",
            "scopeType": "DirectoryRole",
            "scopeId": "/",
            "description": "Roles are configured for activation without requiring multifactor authentication. This is highly discouraged.",
            "severityLevel": "medium",
            "securityImpact": "Without multi-factor authentication, compromised users can activate privileged roles.",
            "mitigationSteps": "Review the list of roles and require multi-factor authentication for every role.",
            "howToPrevent": "Every privileged role should be configured to require MFA for activation.",
            "isRemediatable": true,
            "isConfigurable": false
        },
        {
            "id": "DirectoryRole_19356be4-7e93-4ed6-a7c6-0ae28454d125_RedundantAssignmentAlert",
            "displayName": "Eligible administrators aren't activating their privileged role",
            "scopeType": "DirectoryRole",
            "scopeId": "/",
            "description": "{0} user(s) haven't activated their privileged roles in the past {1} days",
            "severityLevel": "low",
            "securityImpact": "Users that have been assigned privileged roles they don't need increases the chance of an attack. It is also easier for attackers to remain unnoticed in accounts that are not actively being used.",
            "mitigationSteps": "Review the users in the list and remove them from privileged roles they do not need.",
            "howToPrevent": "·Assign privileged roles to users that have a business justification.·Schedule regular access reviews to verify that users still need their access.",
            "isRemediatable": true,
            "isConfigurable": true
        },
        {
            "id": "DirectoryRole_19356be4-7e93-4ed6-a7c6-0ae28454d125_RolesAssignedOutsidePimAlert",
            "displayName": "Roles are being assigned outside of Privileged Identity Management",
            "scopeType": "DirectoryRole",
            "scopeId": "/",
            "description": "{0} privileged assignment(s) were made outisde of Azure AD PIM",
            "severityLevel": "high",
            "securityImpact": "Privileged role assignments made outside of Privileged Identity Management are not properly monitored and may indicate an active attack.",
            "mitigationSteps": "Review the users in the list and remove them from privileged roles assigned outside of Privileged Identity Management.",
            "howToPrevent": "Investigate where users are being assigned privileged roles outside of Privileged Identity Management and prohibit future assignments from there.",
            "isRemediatable": true,
            "isConfigurable": false
        },
        {
            "id": "DirectoryRole_19356be4-7e93-4ed6-a7c6-0ae28454d125_SequentialActivationRenewalsAlert",
            "displayName": "Roles are being activated too frequently",
            "scopeType": "DirectoryRole",
            "scopeId": "/",
            "description": "{0} multiple activations for a privileged role were made by the same user",
            "severityLevel": "medium",
            "securityImpact": "Multiple activations to the same privileged role by the same user is a sign of an attack.",
            "mitigationSteps": "Review the users in the list and ensure that the activation duration for their privileged role is set long enough for them to perform their tasks.",
            "howToPrevent": "·Ensure that the activation duration for privileged roles is set long enough for users to perform their tasks.·Require multi-factor authentication for privileged roles that have accounts shared by multiple administrators.",
            "isRemediatable": false,
            "isConfigurable": true
        },
        {
            "id": "DirectoryRole_19356be4-7e93-4ed6-a7c6-0ae28454d125_StaleSignInAlert",
            "displayName": "Potential stale accounts in a privileged role",
            "scopeType": "DirectoryRole",
            "scopeId": "/",
            "description": "{0} account(s) in privileged roles that have not signed in to Azure AD in the past {1} day(s)",
            "severityLevel": "medium",
            "securityImpact": "Accounts in a privileged role have not signed in recently. These accounts might be service or shared accounts that aren't being maintained and are vulnerable to attackers.",
            "mitigationSteps": "Review the accounts in the list. If they no longer need access, remove them from their privileged roles.",
            "howToPrevent": "Regularly review accounts with privileged roles using <a href=\"https://docs.microsoft.com/en-us/azure/active-directory/governance/access-reviews-overview\" target=\"_blank\" >access reviews</a> and remove role assignments which are no longer needed.",
            "isRemediatable": true,
            "isConfigurable": true
        },
        {
            "id": "DirectoryRole_19356be4-7e93-4ed6-a7c6-0ae28454d125_TooManyGlobalAdminsAssignedToTenantAlert",
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
        }
    ]
}
```
