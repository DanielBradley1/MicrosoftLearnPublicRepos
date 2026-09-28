<!-- Source: https://learn.microsoft.com/en-us/graph/api/unifiedrolemanagementpolicyassignment-get?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-11-13 -->

# Get unifiedRoleManagementPolicyAssignment

Namespace: microsoft.graph

Get the details of a policy assignment in PIM that's assigned to Microsoft Entra roles or group membership or ownership.

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

To retrieve the details of a policy assignment made in PIM for Microsoft Entra roles or PIM for Groups membership and ownership:

```http
GET /policies/roleManagementPolicyAssignments/{unifiedRoleManagementPolicyAssignmentId}
```

## Optional query parameters

This method supports the `$select` and `$expand` OData query parameters to help customize the response. You can also specify the wildcard value `*` to expand all supported relationships, that is, `?$expand=*`. For general information, see [OData query parameters](https://learn.microsoft.com/en-us/graph/query-parameters).

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and an [unifiedRoleManagementPolicyAssignment](https://learn.microsoft.com/en-us/graph/api/resources/unifiedrolemanagementpolicyassignment?view=graph-rest-1.0) object in the response body.

## Examples

### Example 1: Retrieve the details of a policy assignment for PIM for Microsoft Entra roles

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
GET https://graph.microsoft.com/v1.0/policies/roleManagementPolicyAssignments/Directory_cab01047-8ad9-4792-8e42-569340767f1b_70c808b5-0d35-4863-a0ba-07888e99d448_62e90394-69f5-4237-9190-012177145e10
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Policies.RoleManagementPolicyAssignments["{unifiedRoleManagementPolicyAssignment-id}"].GetAsync();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  //other-imports
)


// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
roleManagementPolicyAssignments, err := graphClient.Policies().RoleManagementPolicyAssignments().ByUnifiedRoleManagementPolicyAssignmentId("unifiedRoleManagementPolicyAssignment-id").Get(context.Background(), nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

UnifiedRoleManagementPolicyAssignment result = graphClient.policies().roleManagementPolicyAssignments().byUnifiedRoleManagementPolicyAssignmentId("{unifiedRoleManagementPolicyAssignment-id}").get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let unifiedRoleManagementPolicyAssignment = await client.api('/policies/roleManagementPolicyAssignments/Directory_cab01047-8ad9-4792-8e42-569340767f1b_70c808b5-0d35-4863-a0ba-07888e99d448_62e90394-69f5-4237-9190-012177145e10')
	.get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);


$result = $graphServiceClient->policies()->roleManagementPolicyAssignments()->byUnifiedRoleManagementPolicyAssignmentId('unifiedRoleManagementPolicyAssignment-id')->get()->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Identity.SignIns

Get-MgPolicyRoleManagementPolicyAssignment -UnifiedRoleManagementPolicyAssignmentId $unifiedRoleManagementPolicyAssignmentId
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python

result = await graph_client.policies.role_management_policy_assignments.by_unified_role_management_policy_assignment_id('unifiedRoleManagementPolicyAssignment-id').get()
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#policies/roleManagementPolicyAssignments/$entity",
    "id": "Directory_cab01047-8ad9-4792-8e42-569340767f1b_70c808b5-0d35-4863-a0ba-07888e99d448_62e90394-69f5-4237-9190-012177145e10",
    "policyId": "Directory_cab01047-8ad9-4792-8e42-569340767f1b_70c808b5-0d35-4863-a0ba-07888e99d448",
    "scopeId": "/",
    "scopeType": "Directory",
    "roleDefinitionId": "62e90394-69f5-4237-9190-012177145e10"
}
```

### Example 2: Retrieve the details of a policy assignment for PIM for Microsoft Entra roles and expand the policy and its associated rules

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
GET https://graph.microsoft.com/v1.0/policies/roleManagementPolicyAssignments/Directory_cab01047-8ad9-4792-8e42-569340767f1b_70c808b5-0d35-4863-a0ba-07888e99d448_62e90394-69f5-4237-9190-012177145e10?$expand=policy($expand=rules)
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Policies.RoleManagementPolicyAssignments["{unifiedRoleManagementPolicyAssignment-id}"].GetAsync((requestConfiguration) =>
{
	requestConfiguration.QueryParameters.Expand = new string []{ "policy($expand=rules)" };
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

requestParameters := &graphpolicies.RoleManagementPolicyAssignmentsItemRequestBuilderGetQueryParameters{
	Expand: [] string {"policy($expand=rules)"},
}
configuration := &graphpolicies.RoleManagementPolicyAssignmentsItemRequestBuilderGetRequestConfiguration{
	QueryParameters: requestParameters,
}

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
roleManagementPolicyAssignments, err := graphClient.Policies().RoleManagementPolicyAssignments().ByUnifiedRoleManagementPolicyAssignmentId("unifiedRoleManagementPolicyAssignment-id").Get(context.Background(), configuration)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

UnifiedRoleManagementPolicyAssignment result = graphClient.policies().roleManagementPolicyAssignments().byUnifiedRoleManagementPolicyAssignmentId("{unifiedRoleManagementPolicyAssignment-id}").get(requestConfiguration -> {
	requestConfiguration.queryParameters.expand = new String []{"policy($expand=rules)"};
});
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let unifiedRoleManagementPolicyAssignment = await client.api('/policies/roleManagementPolicyAssignments/Directory_cab01047-8ad9-4792-8e42-569340767f1b_70c808b5-0d35-4863-a0ba-07888e99d448_62e90394-69f5-4237-9190-012177145e10')
	.expand('policy($expand=rules)')
	.get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Policies\RoleManagementPolicyAssignments\Item\UnifiedRoleManagementPolicyAssignmentItemRequestBuilderGetRequestConfiguration;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestConfiguration = new UnifiedRoleManagementPolicyAssignmentItemRequestBuilderGetRequestConfiguration();
$queryParameters = UnifiedRoleManagementPolicyAssignmentItemRequestBuilderGetRequestConfiguration::createQueryParameters();
$queryParameters->expand = ["policy(\$expand=rules)"];
$requestConfiguration->queryParameters = $queryParameters;


$result = $graphServiceClient->policies()->roleManagementPolicyAssignments()->byUnifiedRoleManagementPolicyAssignmentId('unifiedRoleManagementPolicyAssignment-id')->get($requestConfiguration)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Identity.SignIns

Get-MgPolicyRoleManagementPolicyAssignment -UnifiedRoleManagementPolicyAssignmentId $unifiedRoleManagementPolicyAssignmentId -ExpandProperty "policy(`$expand=rules)" 
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.policies.role_management_policy_assignments.item.unified_role_management_policy_assignment_item_request_builder import UnifiedRoleManagementPolicyAssignmentItemRequestBuilder
from kiota_abstractions.base_request_configuration import RequestConfiguration
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
query_params = UnifiedRoleManagementPolicyAssignmentItemRequestBuilder.UnifiedRoleManagementPolicyAssignmentItemRequestBuilderGetQueryParameters(
		expand = ["policy($expand=rules)"],
)

request_configuration = RequestConfiguration(
query_parameters = query_params,
)

result = await graph_client.policies.role_management_policy_assignments.by_unified_role_management_policy_assignment_id('unifiedRoleManagementPolicyAssignment-id').get(request_configuration = request_configuration)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#policies/roleManagementPolicyAssignments(policy(rules()))/$entity",
    "id": "Directory_cab01047-8ad9-4792-8e42-569340767f1b_70c808b5-0d35-4863-a0ba-07888e99d448_62e90394-69f5-4237-9190-012177145e10",
    "policyId": "Directory_cab01047-8ad9-4792-8e42-569340767f1b_70c808b5-0d35-4863-a0ba-07888e99d448",
    "scopeId": "/",
    "scopeType": "Directory",
    "roleDefinitionId": "62e90394-69f5-4237-9190-012177145e10",
    "policy": {
        "id": "Directory_cab01047-8ad9-4792-8e42-569340767f1b_70c808b5-0d35-4863-a0ba-07888e99d448",
        "displayName": "Directory",
        "description": "Directory",
        "isOrganizationDefault": false,
        "scopeId": "/",
        "scopeType": "Directory",
        "lastModifiedDateTime": null,
        "lastModifiedBy": {
            "displayName": null,
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
}
```

### Example 3: Retrieve the details of a policy assignment for PIM for Groups

#### Request

The following example shows a request.

- [HTTP](#tabpanel_3_http)
- [C#](#tabpanel_3_csharp)
- [Go](#tabpanel_3_go)
- [Java](#tabpanel_3_java)
- [JavaScript](#tabpanel_3_javascript)
- [PHP](#tabpanel_3_php)
- [PowerShell](#tabpanel_3_powershell)
- [Python](#tabpanel_3_python)

```msgraph
GET https://graph.microsoft.com/v1.0/policies/roleManagementPolicyAssignments/Group_60bba733-f09d-49b7-8445-32369aa066b3_f21b26d9-9ff9-4af1-b1d4-bddf28591369_member
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Policies.RoleManagementPolicyAssignments["{unifiedRoleManagementPolicyAssignment-id}"].GetAsync();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  //other-imports
)


// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
roleManagementPolicyAssignments, err := graphClient.Policies().RoleManagementPolicyAssignments().ByUnifiedRoleManagementPolicyAssignmentId("unifiedRoleManagementPolicyAssignment-id").Get(context.Background(), nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

UnifiedRoleManagementPolicyAssignment result = graphClient.policies().roleManagementPolicyAssignments().byUnifiedRoleManagementPolicyAssignmentId("{unifiedRoleManagementPolicyAssignment-id}").get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let unifiedRoleManagementPolicyAssignment = await client.api('/policies/roleManagementPolicyAssignments/Group_60bba733-f09d-49b7-8445-32369aa066b3_f21b26d9-9ff9-4af1-b1d4-bddf28591369_member')
	.get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);


$result = $graphServiceClient->policies()->roleManagementPolicyAssignments()->byUnifiedRoleManagementPolicyAssignmentId('unifiedRoleManagementPolicyAssignment-id')->get()->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Identity.SignIns

Get-MgPolicyRoleManagementPolicyAssignment -UnifiedRoleManagementPolicyAssignmentId $unifiedRoleManagementPolicyAssignmentId
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python

result = await graph_client.policies.role_management_policy_assignments.by_unified_role_management_policy_assignment_id('unifiedRoleManagementPolicyAssignment-id').get()
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#policies/roleManagementPolicyAssignments/$entity",
    "id": "Group_60bba733-f09d-49b7-8445-32369aa066b3_f21b26d9-9ff9-4af1-b1d4-bddf28591369_member",
    "policyId": "Group_60bba733-f09d-49b7-8445-32369aa066b3_f21b26d9-9ff9-4af1-b1d4-bddf28591369",
    "scopeId": "60bba733-f09d-49b7-8445-32369aa066b3",
    "scopeType": "Group",
    "roleDefinitionId": "member"
}
```
