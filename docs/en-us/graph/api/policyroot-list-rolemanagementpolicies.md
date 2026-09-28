<!-- Source: https://learn.microsoft.com/en-us/graph/api/policyroot-list-rolemanagementpolicies?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-11-13 -->

# List roleManagementPolicies

Namespace: microsoft.graph

Get the details of the policies in PIM that can be applied to Microsoft Entra roles or group membership or ownership. To retrieve policies that apply to Azure RBAC, use the [Azure REST PIM API for role management policies](https://learn.microsoft.com/en-us/rest/api/authorization/role-management-policies/list-for-scope).

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

One of the following permissions is required to call this API. To learn more, including how to choose permissions, see [Permissions](https://learn.microsoft.com/en-us/graph/permissions-reference).

### For PIM for Microsoft Entra roles

| Permission type | Permissions \(from least to most privileged\) |
| :--- | :--- |
| Delegated \(work or school account\) | RoleManagementPolicy.Read.Directory, RoleManagement.Read.Directory, RoleManagement.Read.All, RoleManagementPolicy.ReadWrite.Directory, RoleManagement.ReadWrite.Directory |
| Delegated \(personal Microsoft account\) | Not supported. |
| Application | RoleManagementPolicy.Read.Directory, RoleManagement.Read.Directory, RoleManagement.Read.All, RoleManagementPolicy.ReadWrite.Directory, RoleManagement.ReadWrite.Directory |

Important

For delegated access using work or school accounts, the signed-in user must be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) or a custom role that grants the permissions required for this operation. This operation supports the following built-in roles, which provide only the least privilege necessary:

- For read operations: *Global Reader*, *Security Operator*, *Security Reader*, *Security Administrator*, or *Privileged Role Administrator*
- For write operations: *Privileged Role Administrator*

### For PIM for Groups

| Permission type | Permissions \(from least to most privileged\) |
| :--- | :--- |
| Delegated \(work or school account\) | RoleManagementPolicy.Read.AzureADGroup, RoleManagementPolicy.ReadWrite.AzureADGroup |
| Delegated \(personal Microsoft account\) | Not supported. |
| Application | RoleManagementPolicy.Read.AzureADGroup, RoleManagementPolicy.ReadWrite.AzureADGroup |

## HTTP request

To retrieve policies and their details for Microsoft Entra roles scoped to the tenant:

```http
GET /policies/roleManagementPolicies?$filter=scopeId eq '/' and scopeType eq 'DirectoryRole'
```

To retrieve details of all role management policies scoped to a group:

```http
GET /policies/roleManagementPolicies?$filter=scopeId eq '{groupId}' and scopeType eq 'Group'
```

## Query parameters

This method requires the `$filter` \(`eq`\) query parameter to scope the request to a **scopeId** and a **scopeType**.

- To retrieve policies in PIM for Microsoft Entra roles, the **scopeId** must be `/` and **scopeType** can be either `Directory` or `DirectoryRole`.
- To retrieve policies in PIM for Groups, the **scopeId** must be a group ID and **scopeType** must be `Group`.

You can also use the `$select` and `$expand` OData query parameters to help customize the response. This API also supports `$select` nested in `$expand` to return only specific properties of those rules. For general information, see [OData query parameters](https://learn.microsoft.com/en-us/graph/query-parameters).

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and a collection of [unifiedRoleManagementPolicy](https://learn.microsoft.com/en-us/graph/api/resources/unifiedrolemanagementpolicy?view=graph-rest-1.0) objects in the response body.

## Examples

### Example 1: Retrieve the role management policies that apply to PIM for Microsoft Entra roles

#### Request

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [PowerShell](#tabpanel_1_powershell)
- [Python](#tabpanel_1_python)

```msgraph
GET https://graph.microsoft.com/v1.0/policies/roleManagementPolicies?$filter=scopeId eq '/' and scopeType eq 'DirectoryRole'
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Policies.RoleManagementPolicies.GetAsync((requestConfiguration) =>
{
	requestConfiguration.QueryParameters.Filter = "scopeId eq '/' and scopeType eq 'DirectoryRole'";
});
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphpolicies "github.com/microsoftgraph/msgraph-sdk-go/policies"
	  //other-imports
)


requestFilter := "scopeId eq '/' and scopeType eq 'DirectoryRole'"

requestParameters := &graphpolicies.PoliciesRoleManagementPoliciesRequestBuilderGetQueryParameters{
	Filter: &requestFilter,
}
configuration := &graphpolicies.PoliciesRoleManagementPoliciesRequestBuilderGetRequestConfiguration{
	QueryParameters: requestParameters,
}

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
roleManagementPolicies, err := graphClient.Policies().RoleManagementPolicies().Get(context.Background(), configuration)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

UnifiedRoleManagementPolicyCollectionResponse result = graphClient.policies().roleManagementPolicies().get(requestConfiguration -> {
	requestConfiguration.queryParameters.filter = "scopeId eq '/' and scopeType eq 'DirectoryRole'";
});
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let roleManagementPolicies = await client.api('/policies/roleManagementPolicies')
	.filter('scopeId eq \'/\' and scopeType eq \'DirectoryRole\'')
	.get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Policies\RoleManagementPolicies\RoleManagementPoliciesRequestBuilderGetRequestConfiguration;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestConfiguration = new RoleManagementPoliciesRequestBuilderGetRequestConfiguration();
$queryParameters = RoleManagementPoliciesRequestBuilderGetRequestConfiguration::createQueryParameters();
$queryParameters->filter = "scopeId eq '/' and scopeType eq 'DirectoryRole'";
$requestConfiguration->queryParameters = $queryParameters;


$result = $graphServiceClient->policies()->roleManagementPolicies()->get($requestConfiguration)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Identity.SignIns

Get-MgPolicyRoleManagementPolicy -Filter "scopeId eq '/' and scopeType eq 'DirectoryRole'" 
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.policies.role_management_policies.role_management_policies_request_builder import RoleManagementPoliciesRequestBuilder
from kiota_abstractions.base_request_configuration import RequestConfiguration
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
query_params = RoleManagementPoliciesRequestBuilder.RoleManagementPoliciesRequestBuilderGetQueryParameters(
		filter = "scopeId eq '/' and scopeType eq 'DirectoryRole'",
)

request_configuration = RequestConfiguration(
query_parameters = query_params,
)

result = await graph_client.policies.role_management_policies.get(request_configuration = request_configuration)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#policies/roleManagementPolicies",
    "value": [
        {
            "id": "DirectoryRole_cab01047-8ad9-4792-8e42-569340767f1b_70c808b5-0d35-4863-a0ba-07888e99d448",
            "displayName": "DirectoryRole",
            "description": "DirectoryRole",
            "isOrganizationDefault": false,
            "scopeId": "/",
            "scopeType": "DirectoryRole",
            "lastModifiedDateTime": null,
            "lastModifiedBy": {
                "displayName": null,
                "id": null
            }
        },
        {
            "id": "DirectoryRole_cab01047-8ad9-4792-8e42-569340767f1b_23b16f1a-1f8d-4891-93b1-21244cdf6115",
            "displayName": "DirectoryRole",
            "description": "DirectoryRole",
            "isOrganizationDefault": false,
            "scopeId": "/",
            "scopeType": "DirectoryRole",
            "lastModifiedDateTime": null,
            "lastModifiedBy": {
                "displayName": null,
                "id": null
            }
        }
    ]
}
```

### Example 2: Retrieve the role management policies that apply to PIM for Microsoft Entra roles and expand the associated rules

#### Request

- [HTTP](#tabpanel_2_http)
- [C#](#tabpanel_2_csharp)
- [Go](#tabpanel_2_go)
- [Java](#tabpanel_2_java)
- [JavaScript](#tabpanel_2_javascript)
- [PHP](#tabpanel_2_php)
- [PowerShell](#tabpanel_2_powershell)
- [Python](#tabpanel_2_python)

```msgraph
GET https://graph.microsoft.com/v1.0/policies/roleManagementPolicies?$filter=scopeId eq '/' and scopeType eq 'Directory'&$expand=rules
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Policies.RoleManagementPolicies.GetAsync((requestConfiguration) =>
{
	requestConfiguration.QueryParameters.Filter = "scopeId eq '/' and scopeType eq 'Directory'";
	requestConfiguration.QueryParameters.Expand = new string []{ "rules" };
});
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphpolicies "github.com/microsoftgraph/msgraph-sdk-go/policies"
	  //other-imports
)


requestFilter := "scopeId eq '/' and scopeType eq 'Directory'"

requestParameters := &graphpolicies.PoliciesRoleManagementPoliciesRequestBuilderGetQueryParameters{
	Filter: &requestFilter,
	Expand: [] string {"rules"},
}
configuration := &graphpolicies.PoliciesRoleManagementPoliciesRequestBuilderGetRequestConfiguration{
	QueryParameters: requestParameters,
}

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
roleManagementPolicies, err := graphClient.Policies().RoleManagementPolicies().Get(context.Background(), configuration)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

UnifiedRoleManagementPolicyCollectionResponse result = graphClient.policies().roleManagementPolicies().get(requestConfiguration -> {
	requestConfiguration.queryParameters.filter = "scopeId eq '/' and scopeType eq 'Directory'";
	requestConfiguration.queryParameters.expand = new String []{"rules"};
});
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let roleManagementPolicies = await client.api('/policies/roleManagementPolicies')
	.filter('scopeId eq \'/\' and scopeType eq \'Directory\'')
	.expand('rules')
	.get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Policies\RoleManagementPolicies\RoleManagementPoliciesRequestBuilderGetRequestConfiguration;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestConfiguration = new RoleManagementPoliciesRequestBuilderGetRequestConfiguration();
$queryParameters = RoleManagementPoliciesRequestBuilderGetRequestConfiguration::createQueryParameters();
$queryParameters->filter = "scopeId eq '/' and scopeType eq 'Directory'";
$queryParameters->expand = ["rules"];
$requestConfiguration->queryParameters = $queryParameters;


$result = $graphServiceClient->policies()->roleManagementPolicies()->get($requestConfiguration)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Identity.SignIns

Get-MgPolicyRoleManagementPolicy -Filter "scopeId eq '/' and scopeType eq 'Directory'" -ExpandProperty "rules" 
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.policies.role_management_policies.role_management_policies_request_builder import RoleManagementPoliciesRequestBuilder
from kiota_abstractions.base_request_configuration import RequestConfiguration
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
query_params = RoleManagementPoliciesRequestBuilder.RoleManagementPoliciesRequestBuilderGetQueryParameters(
		filter = "scopeId eq '/' and scopeType eq 'Directory'",
		expand = ["rules"],
)

request_configuration = RequestConfiguration(
query_parameters = query_params,
)

result = await graph_client.policies.role_management_policies.get(request_configuration = request_configuration)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#policies/roleManagementPolicies(rules())",
    "value": [
        {
            "id": "Directory_cab01047-8ad9-4792-8e42-569340767f1b_70c808b5-0d35-4863-a0ba-07888e99d448",
            "displayName": "Directory",
            "description": "Directory",
            "isOrganizationDefault": false,
            "scopeId": "/",
            "scopeType": "Directory",
            "lastModifiedDateTime": "2022-04-20T16:12:29.553Z",
            "lastModifiedBy": {
                "displayName": "MOD Administrator",
                "id": null
            },
            "rules": [
                {
                    "@odata.type": "#microsoft.graph.unifiedRoleManagementPolicyExpirationRule",
                    "id": "Expiration_Admin_Eligibility",
                    "isExpirationRequired": false,
                    "maximumDuration": "P365D",
                    "target": {
                        "caller": "Admin",
                        "operations": [
                            "all"
                        ],
                        "level": "Eligibility",
                        "inheritableSettings": [],
                        "enforcedSettings": []
                    }
                },
                {
                    "@odata.type": "#microsoft.graph.unifiedRoleManagementPolicyNotificationRule",
                    "id": "Notification_Admin_Admin_Eligibility",
                    "notificationType": "Email",
                    "recipientType": "Admin",
                    "notificationLevel": "All",
                    "isDefaultRecipientsEnabled": true,
                    "notificationRecipients": [],
                    "target": {
                        "caller": "Admin",
                        "operations": [
                            "all"
                        ],
                        "level": "Eligibility",
                        "inheritableSettings": [],
                        "enforcedSettings": []
                    }
                },
                {
                    "@odata.type": "#microsoft.graph.unifiedRoleManagementPolicyNotificationRule",
                    "id": "Notification_Requestor_Admin_Eligibility",
                    "notificationType": "Email",
                    "recipientType": "Requestor",
                    "notificationLevel": "All",
                    "isDefaultRecipientsEnabled": true,
                    "notificationRecipients": [],
                    "target": {
                        "caller": "Admin",
                        "operations": [
                            "all"
                        ],
                        "level": "Eligibility",
                        "inheritableSettings": [],
                        "enforcedSettings": []
                    }
                },
                {
                    "@odata.type": "#microsoft.graph.unifiedRoleManagementPolicyNotificationRule",
                    "id": "Notification_Approver_Admin_Eligibility",
                    "notificationType": "Email",
                    "recipientType": "Approver",
                    "notificationLevel": "All",
                    "isDefaultRecipientsEnabled": true,
                    "notificationRecipients": [],
                    "target": {
                        "caller": "Admin",
                        "operations": [
                            "all"
                        ],
                        "level": "Eligibility",
                        "inheritableSettings": [],
                        "enforcedSettings": []
                    }
                },
                {
                    "@odata.type": "#microsoft.graph.unifiedRoleManagementPolicyEnablementRule",
                    "id": "Enablement_Admin_Eligibility",
                    "enabledRules": [],
                    "target": {
                        "caller": "Admin",
                        "operations": [
                            "all"
                        ],
                        "level": "Eligibility",
                        "inheritableSettings": [],
                        "enforcedSettings": []
                    }
                },
                {
                    "@odata.type": "#microsoft.graph.unifiedRoleManagementPolicyExpirationRule",
                    "id": "Expiration_Admin_Assignment",
                    "isExpirationRequired": false,
                    "maximumDuration": "P180D",
                    "target": {
                        "caller": "Admin",
                        "operations": [
                            "all"
                        ],
                        "level": "Assignment",
                        "inheritableSettings": [],
                        "enforcedSettings": []
                    }
                },
                {
                    "@odata.type": "#microsoft.graph.unifiedRoleManagementPolicyEnablementRule",
                    "id": "Enablement_Admin_Assignment",
                    "enabledRules": [
                        "Justification"
                    ],
                    "target": {
                        "caller": "Admin",
                        "operations": [
                            "all"
                        ],
                        "level": "Assignment",
                        "inheritableSettings": [],
                        "enforcedSettings": []
                    }
                },
                {
                    "@odata.type": "#microsoft.graph.unifiedRoleManagementPolicyNotificationRule",
                    "id": "Notification_Admin_Admin_Assignment",
                    "notificationType": "Email",
                    "recipientType": "Admin",
                    "notificationLevel": "All",
                    "isDefaultRecipientsEnabled": true,
                    "notificationRecipients": [],
                    "target": {
                        "caller": "Admin",
                        "operations": [
                            "all"
                        ],
                        "level": "Assignment",
                        "inheritableSettings": [],
                        "enforcedSettings": []
                    }
                },
                {
                    "@odata.type": "#microsoft.graph.unifiedRoleManagementPolicyNotificationRule",
                    "id": "Notification_Requestor_Admin_Assignment",
                    "notificationType": "Email",
                    "recipientType": "Requestor",
                    "notificationLevel": "All",
                    "isDefaultRecipientsEnabled": true,
                    "notificationRecipients": [],
                    "target": {
                        "caller": "Admin",
                        "operations": [
                            "all"
                        ],
                        "level": "Assignment",
                        "inheritableSettings": [],
                        "enforcedSettings": []
                    }
                },
                {
                    "@odata.type": "#microsoft.graph.unifiedRoleManagementPolicyNotificationRule",
                    "id": "Notification_Approver_Admin_Assignment",
                    "notificationType": "Email",
                    "recipientType": "Approver",
                    "notificationLevel": "All",
                    "isDefaultRecipientsEnabled": true,
                    "notificationRecipients": [],
                    "target": {
                        "caller": "Admin",
                        "operations": [
                            "all"
                        ],
                        "level": "Assignment",
                        "inheritableSettings": [],
                        "enforcedSettings": []
                    }
                },
                {
                    "@odata.type": "#microsoft.graph.unifiedRoleManagementPolicyExpirationRule",
                    "id": "Expiration_EndUser_Assignment",
                    "isExpirationRequired": true,
                    "maximumDuration": "PT8H",
                    "target": {
                        "caller": "EndUser",
                        "operations": [
                            "all"
                        ],
                        "level": "Assignment",
                        "inheritableSettings": [],
                        "enforcedSettings": []
                    }
                },
                {
                    "@odata.type": "#microsoft.graph.unifiedRoleManagementPolicyEnablementRule",
                    "id": "Enablement_EndUser_Assignment",
                    "enabledRules": [
                        "MultiFactorAuthentication",
                        "Justification"
                    ],
                    "target": {
                        "caller": "EndUser",
                        "operations": [
                            "all"
                        ],
                        "level": "Assignment",
                        "inheritableSettings": [],
                        "enforcedSettings": []
                    }
                },
                {
                    "@odata.type": "#microsoft.graph.unifiedRoleManagementPolicyApprovalRule",
                    "id": "Approval_EndUser_Assignment",
                    "target": {
                        "caller": "EndUser",
                        "operations": [
                            "all"
                        ],
                        "level": "Assignment",
                        "inheritableSettings": [],
                        "enforcedSettings": []
                    },
                    "setting": {
                        "isApprovalRequired": false,
                        "isApprovalRequiredForExtension": false,
                        "isRequestorJustificationRequired": true,
                        "approvalMode": "SingleStage",
                        "approvalStages": [
                            {
                                "approvalStageTimeOutInDays": 1,
                                "isApproverJustificationRequired": true,
                                "escalationTimeInMinutes": 0,
                                "isEscalationEnabled": false,
                                "primaryApprovers": [],
                                "escalationApprovers": []
                            }
                        ]
                    }
                },
                {
                    "@odata.type": "#microsoft.graph.unifiedRoleManagementPolicyAuthenticationContextRule",
                    "id": "AuthenticationContext_EndUser_Assignment",
                    "isEnabled": false,
                    "claimValue": null,
                    "target": {
                        "caller": "EndUser",
                        "operations": [
                            "all"
                        ],
                        "level": "Assignment",
                        "inheritableSettings": [],
                        "enforcedSettings": []
                    }
                },
                {
                    "@odata.type": "#microsoft.graph.unifiedRoleManagementPolicyNotificationRule",
                    "id": "Notification_Admin_EndUser_Assignment",
                    "notificationType": "Email",
                    "recipientType": "Admin",
                    "notificationLevel": "All",
                    "isDefaultRecipientsEnabled": true,
                    "notificationRecipients": [],
                    "target": {
                        "caller": "EndUser",
                        "operations": [
                            "all"
                        ],
                        "level": "Assignment",
                        "inheritableSettings": [],
                        "enforcedSettings": []
                    }
                },
                {
                    "@odata.type": "#microsoft.graph.unifiedRoleManagementPolicyNotificationRule",
                    "id": "Notification_Requestor_EndUser_Assignment",
                    "notificationType": "Email",
                    "recipientType": "Requestor",
                    "notificationLevel": "All",
                    "isDefaultRecipientsEnabled": true,
                    "notificationRecipients": [],
                    "target": {
                        "caller": "EndUser",
                        "operations": [
                            "all"
                        ],
                        "level": "Assignment",
                        "inheritableSettings": [],
                        "enforcedSettings": []
                    }
                },
                {
                    "@odata.type": "#microsoft.graph.unifiedRoleManagementPolicyNotificationRule",
                    "id": "Notification_Approver_EndUser_Assignment",
                    "notificationType": "Email",
                    "recipientType": "Approver",
                    "notificationLevel": "All",
                    "isDefaultRecipientsEnabled": true,
                    "notificationRecipients": [],
                    "target": {
                        "caller": "EndUser",
                        "operations": [
                            "all"
                        ],
                        "level": "Assignment",
                        "inheritableSettings": [],
                        "enforcedSettings": []
                    }
                }
            ]
        }
    ]
}
```

### Example 3: Retrieve policies and their details in PIM for Groups

#### Request

The following example retrieves policies that are scoped to the group and apply to PIM for Groups membership and ownership.

- [HTTP](#tabpanel_3_http)
- [C#](#tabpanel_3_csharp)
- [Go](#tabpanel_3_go)
- [Java](#tabpanel_3_java)
- [JavaScript](#tabpanel_3_javascript)
- [PHP](#tabpanel_3_php)
- [PowerShell](#tabpanel_3_powershell)
- [Python](#tabpanel_3_python)

```msgraph
GET https://graph.microsoft.com/v1.0/policies/roleManagementPolicies?$filter=scopeId eq '60bba733-f09d-49b7-8445-32369aa066b3' and scopeType eq 'Group'&$expand=rules($select=id)
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Policies.RoleManagementPolicies.GetAsync((requestConfiguration) =>
{
	requestConfiguration.QueryParameters.Filter = "scopeId eq '60bba733-f09d-49b7-8445-32369aa066b3' and scopeType eq 'Group'";
	requestConfiguration.QueryParameters.Expand = new string []{ "rules($select=id)" };
});
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphpolicies "github.com/microsoftgraph/msgraph-sdk-go/policies"
	  //other-imports
)


requestFilter := "scopeId eq '60bba733-f09d-49b7-8445-32369aa066b3' and scopeType eq 'Group'"

requestParameters := &graphpolicies.PoliciesRoleManagementPoliciesRequestBuilderGetQueryParameters{
	Filter: &requestFilter,
	Expand: [] string {"rules($select=id)"},
}
configuration := &graphpolicies.PoliciesRoleManagementPoliciesRequestBuilderGetRequestConfiguration{
	QueryParameters: requestParameters,
}

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
roleManagementPolicies, err := graphClient.Policies().RoleManagementPolicies().Get(context.Background(), configuration)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

UnifiedRoleManagementPolicyCollectionResponse result = graphClient.policies().roleManagementPolicies().get(requestConfiguration -> {
	requestConfiguration.queryParameters.filter = "scopeId eq '60bba733-f09d-49b7-8445-32369aa066b3' and scopeType eq 'Group'";
	requestConfiguration.queryParameters.expand = new String []{"rules($select=id)"};
});
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let roleManagementPolicies = await client.api('/policies/roleManagementPolicies')
	.filter('scopeId eq \'60bba733-f09d-49b7-8445-32369aa066b3\' and scopeType eq \'Group\'')
	.expand('rules($select=id)')
	.get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Policies\RoleManagementPolicies\RoleManagementPoliciesRequestBuilderGetRequestConfiguration;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestConfiguration = new RoleManagementPoliciesRequestBuilderGetRequestConfiguration();
$queryParameters = RoleManagementPoliciesRequestBuilderGetRequestConfiguration::createQueryParameters();
$queryParameters->filter = "scopeId eq '60bba733-f09d-49b7-8445-32369aa066b3' and scopeType eq 'Group'";
$queryParameters->expand = ["rules(\$select=id)"];
$requestConfiguration->queryParameters = $queryParameters;


$result = $graphServiceClient->policies()->roleManagementPolicies()->get($requestConfiguration)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Identity.SignIns

Get-MgPolicyRoleManagementPolicy -Filter "scopeId eq '60bba733-f09d-49b7-8445-32369aa066b3' and scopeType eq 'Group'" -ExpandProperty "rules(`$select=id)" 
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.policies.role_management_policies.role_management_policies_request_builder import RoleManagementPoliciesRequestBuilder
from kiota_abstractions.base_request_configuration import RequestConfiguration
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
query_params = RoleManagementPoliciesRequestBuilder.RoleManagementPoliciesRequestBuilderGetQueryParameters(
		filter = "scopeId eq '60bba733-f09d-49b7-8445-32369aa066b3' and scopeType eq 'Group'",
		expand = ["rules($select=id)"],
)

request_configuration = RequestConfiguration(
query_parameters = query_params,
)

result = await graph_client.policies.role_management_policies.get(request_configuration = request_configuration)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#policies/roleManagementPolicies(rules(id))",
    "value": [
        {
            "id": "Group_60bba733-f09d-49b7-8445-32369aa066b3_f21b26d9-9ff9-4af1-b1d4-bddf28591369",
            "displayName": "Group",
            "description": "Group",
            "isOrganizationDefault": false,
            "scopeId": "60bba733-f09d-49b7-8445-32369aa066b3",
            "scopeType": "Group",
            "lastModifiedDateTime": null,
            "lastModifiedBy": {
                "displayName": null,
                "id": null
            },
            "rules@odata.context": "https://graph.microsoft.com/v1.0/$metadata#policies/roleManagementPolicies('Group_60bba733-f09d-49b7-8445-32369aa066b3_f21b26d9-9ff9-4af1-b1d4-bddf28591369')/rules(id)",
            "rules": [
                {
                    "@odata.type": "#microsoft.graph.unifiedRoleManagementPolicyEnablementRule",
                    "id": "Enablement_Admin_Eligibility"
                },
                {
                    "@odata.type": "#microsoft.graph.unifiedRoleManagementPolicyExpirationRule",
                    "id": "Expiration_Admin_Eligibility"
                },
                {
                    "@odata.type": "#microsoft.graph.unifiedRoleManagementPolicyNotificationRule",
                    "id": "Notification_Requestor_Admin_Eligibility"
                },
                {
                    "@odata.type": "#microsoft.graph.unifiedRoleManagementPolicyNotificationRule",
                    "id": "Notification_Approver_Admin_Eligibility"
                },
                {
                    "@odata.type": "#microsoft.graph.unifiedRoleManagementPolicyNotificationRule",
                    "id": "Notification_Admin_Admin_Eligibility"
                },
                {
                    "@odata.type": "#microsoft.graph.unifiedRoleManagementPolicyEnablementRule",
                    "id": "Enablement_Admin_Assignment"
                },
                {
                    "@odata.type": "#microsoft.graph.unifiedRoleManagementPolicyExpirationRule",
                    "id": "Expiration_Admin_Assignment"
                },
                {
                    "@odata.type": "#microsoft.graph.unifiedRoleManagementPolicyNotificationRule",
                    "id": "Notification_Admin_Admin_Assignment"
                },
                {
                    "@odata.type": "#microsoft.graph.unifiedRoleManagementPolicyNotificationRule",
                    "id": "Notification_Requestor_Admin_Assignment"
                },
                {
                    "@odata.type": "#microsoft.graph.unifiedRoleManagementPolicyNotificationRule",
                    "id": "Notification_Approver_Admin_Assignment"
                },
                {
                    "@odata.type": "#microsoft.graph.unifiedRoleManagementPolicyApprovalRule",
                    "id": "Approval_EndUser_Assignment"
                },
                {
                    "@odata.type": "#microsoft.graph.unifiedRoleManagementPolicyAuthenticationContextRule",
                    "id": "AuthenticationContext_EndUser_Assignment"
                },
                {
                    "@odata.type": "#microsoft.graph.unifiedRoleManagementPolicyEnablementRule",
                    "id": "Enablement_EndUser_Assignment"
                },
                {
                    "@odata.type": "#microsoft.graph.unifiedRoleManagementPolicyExpirationRule",
                    "id": "Expiration_EndUser_Assignment"
                },
                {
                    "@odata.type": "#microsoft.graph.unifiedRoleManagementPolicyNotificationRule",
                    "id": "Notification_Admin_EndUser_Assignment"
                },
                {
                    "@odata.type": "#microsoft.graph.unifiedRoleManagementPolicyNotificationRule",
                    "id": "Notification_Requestor_EndUser_Assignment"
                },
                {
                    "@odata.type": "#microsoft.graph.unifiedRoleManagementPolicyNotificationRule",
                    "id": "Notification_Approver_EndUser_Assignment"
                }
            ]
        },
        {
            "id": "Group_60bba733-f09d-49b7-8445-32369aa066b3_8ea17f58-323f-4b16-a1a1-2a7b8d974316",
            "displayName": "Group",
            "description": "Group",
            "isOrganizationDefault": false,
            "scopeId": "60bba733-f09d-49b7-8445-32369aa066b3",
            "scopeType": "Group",
            "lastModifiedDateTime": null,
            "lastModifiedBy": {
                "displayName": null,
                "id": null
            },
            "rules@odata.context": "https://graph.microsoft.com/v1.0/$metadata#policies/roleManagementPolicies('Group_60bba733-f09d-49b7-8445-32369aa066b3_8ea17f58-323f-4b16-a1a1-2a7b8d974316')/rules(id)",
            "rules": [
                {
                    "@odata.type": "#microsoft.graph.unifiedRoleManagementPolicyExpirationRule",
                    "id": "Expiration_Admin_Eligibility"
                },
                {
                    "@odata.type": "#microsoft.graph.unifiedRoleManagementPolicyEnablementRule",
                    "id": "Enablement_Admin_Eligibility"
                },
                {
                    "@odata.type": "#microsoft.graph.unifiedRoleManagementPolicyNotificationRule",
                    "id": "Notification_Admin_Admin_Eligibility"
                },
                {
                    "@odata.type": "#microsoft.graph.unifiedRoleManagementPolicyNotificationRule",
                    "id": "Notification_Requestor_Admin_Eligibility"
                },
                {
                    "@odata.type": "#microsoft.graph.unifiedRoleManagementPolicyNotificationRule",
                    "id": "Notification_Approver_Admin_Eligibility"
                },
                {
                    "@odata.type": "#microsoft.graph.unifiedRoleManagementPolicyExpirationRule",
                    "id": "Expiration_Admin_Assignment"
                },
                {
                    "@odata.type": "#microsoft.graph.unifiedRoleManagementPolicyEnablementRule",
                    "id": "Enablement_Admin_Assignment"
                },
                {
                    "@odata.type": "#microsoft.graph.unifiedRoleManagementPolicyNotificationRule",
                    "id": "Notification_Admin_Admin_Assignment"
                },
                {
                    "@odata.type": "#microsoft.graph.unifiedRoleManagementPolicyNotificationRule",
                    "id": "Notification_Requestor_Admin_Assignment"
                },
                {
                    "@odata.type": "#microsoft.graph.unifiedRoleManagementPolicyNotificationRule",
                    "id": "Notification_Approver_Admin_Assignment"
                },
                {
                    "@odata.type": "#microsoft.graph.unifiedRoleManagementPolicyExpirationRule",
                    "id": "Expiration_EndUser_Assignment"
                },
                {
                    "@odata.type": "#microsoft.graph.unifiedRoleManagementPolicyEnablementRule",
                    "id": "Enablement_EndUser_Assignment"
                },
                {
                    "@odata.type": "#microsoft.graph.unifiedRoleManagementPolicyApprovalRule",
                    "id": "Approval_EndUser_Assignment"
                },
                {
                    "@odata.type": "#microsoft.graph.unifiedRoleManagementPolicyAuthenticationContextRule",
                    "id": "AuthenticationContext_EndUser_Assignment"
                },
                {
                    "@odata.type": "#microsoft.graph.unifiedRoleManagementPolicyNotificationRule",
                    "id": "Notification_Admin_EndUser_Assignment"
                },
                {
                    "@odata.type": "#microsoft.graph.unifiedRoleManagementPolicyNotificationRule",
                    "id": "Notification_Requestor_EndUser_Assignment"
                },
                {
                    "@odata.type": "#microsoft.graph.unifiedRoleManagementPolicyNotificationRule",
                    "id": "Notification_Approver_EndUser_Assignment"
                }
            ]
        }
    ]
}
```
