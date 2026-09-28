<!-- Source: https://learn.microsoft.com/en-us/graph/api/identitygovernance-lifecycleworkflowscontainer-list-taskdefinitions?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-23 -->

# List taskDefinitions

Namespace: microsoft.graph.identityGovernance

Get a list of built-in tasks in Lifecycle Workflows. A task is represented by the [taskDefinition](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-taskdefinition?view=graph-rest-1.0) object.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | LifecycleWorkflows.Read.All | LifecycleWorkflows.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | LifecycleWorkflows.Read.All | LifecycleWorkflows.ReadWrite.All |

Important

For delegated access using work or school accounts, the signed-in user must be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) or a custom role that grants the permissions required for this operation. *Global Reader* and *Lifecycle Workflows Administrator* are the least privileged roles supported for this operation.

## HTTP request

```http
GET /identityGovernance/lifecycleWorkflows/taskDefinitions
```

## Optional query parameters

This method supports the `$select`, `$orderby`, and `$filter` OData query parameters to help customize the response. For general information, see [OData query parameters](https://learn.microsoft.com/en-us/graph/query-parameters).

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and a collection of [microsoft.graph.identityGovernance.taskDefinition](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-taskdefinition?view=graph-rest-1.0) objects in the response body.

## Examples

### Example 1: Retrieve all built-in task definitions

#### Request

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
GET https://graph.microsoft.com/v1.0/identityGovernance/lifecycleWorkflows/taskDefinitions
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.IdentityGovernance.LifecycleWorkflows.TaskDefinitions.GetAsync();
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
taskDefinitions, err := graphClient.IdentityGovernance().LifecycleWorkflows().TaskDefinitions().Get(context.Background(), nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.models.identitygovernance.TaskDefinitionCollectionResponse result = graphClient.identityGovernance().lifecycleWorkflows().taskDefinitions().get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let taskDefinitions = await client.api('/identityGovernance/lifecycleWorkflows/taskDefinitions')
	.get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);


$result = $graphServiceClient->identityGovernance()->lifecycleWorkflows()->taskDefinitions()->get()->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Identity.Governance

Get-MgIdentityGovernanceLifecycleWorkflowTaskDefinition
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python

result = await graph_client.identity_governance.lifecycle_workflows.task_definitions.get()
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#identityGovernance/lifecycleWorkflows/taskDefinitions",
    "@odata.count": 25,
    "@microsoft.graph.tips": "Use $select to choose only the properties your app needs, as this can lead to performance improvements. For example: GET identityGovernance/lifecycleWorkflows/taskDefinitions?$select=category,continueOnError",
    "value": [
        {
            "category": "joiner,leaver,mover",
            "description": "Add user to selected groups",
            "displayName": "Add user to groups",
            "id": "22085229-5809-45e8-97fd-270d28d66910",
            "version": 1,
            "parameters": [
                {
                    "name": "groupID",
                    "values": [],
                    "valueType": "string"
                }
            ]
        },
        {
            "category": "joiner,leaver",
            "description": "Disable user account in the directory",
            "displayName": "Disable user account",
            "id": "1dfdfcc7-52fa-4c2e-bf3a-e3919cc12950",
            "version": 1,
            "parameters": [
                {
                    "name": "disableOnPremisesAccount",
                    "values": [
                        "true",
                        "false"
                    ],
                    "valueType": "enum"
                }
            ]
        },
        {
            "category": "joiner,leaver",
            "description": "Enable user account in the directory",
            "displayName": "Enable user account",
            "id": "6fc52c9d-398b-4305-9763-15f42c1676fc",
            "version": 1,
            "parameters": [
                {
                    "name": "enableOnPremisesAccount",
                    "values": [
                        "true",
                        "false"
                    ],
                    "valueType": "enum"
                }
            ]
        },
        {
            "category": "joiner,leaver,mover",
            "description": "Remove user from membership of selected Azure AD groups",
            "displayName": "Remove user from selected groups",
            "id": "1953a66c-751c-45e5-8bfe-01462c70da3c",
            "version": 1,
            "parameters": [
                {
                    "name": "groupID",
                    "values": [],
                    "valueType": "string"
                }
            ]
        },
        {
            "category": "joiner",
            "description": "Generate Temporary Access Pass and send via email to user's manager",
            "displayName": "Generate TAP and send email",
            "id": "1b555e50-7f65-41d5-b514-5894a026d10d",
            "version": 1,
            "parameters": [
                {
                    "name": "tapLifetimeMinutes",
                    "values": [],
                    "valueType": "string"
                },
                {
                    "name": "tapIsUsableOnce",
                    "values": [
                        "true",
                        "false"
                    ],
                    "valueType": "enum"
                },
                {
                    "name": "cc",
                    "values": [],
                    "valueType": "string"
                },
                {
                    "name": "customSubject",
                    "values": [],
                    "valueType": "string"
                },
                {
                    "name": "customBody",
                    "values": [],
                    "valueType": "string"
                },
                {
                    "name": "locale",
                    "values": [],
                    "valueType": "string"
                },
                {
                    "name": "to",
                    "values": [
                        "User",
                        "Manager",
                        "Sponsors",
                        "{UserId}",
                        "User/otherMails",
                        "User/customSecurityAttributes/{attributeSet}/{attributeName}",
                        "User/{directoryExtensionAttribute}",
                        "User/onPremisesExtensionAttributes/{extensionAttribute[1-15]}"
                    ],
                    "valueType": "string"
                }
            ]
        },
        {
            "category": "joiner",
            "description": "Send welcome email to new hire",
            "displayName": "Send welcome email",
            "id": "70b29d51-b59a-4773-9280-8841dfd3f2ea",
            "version": 1,
            "parameters": [
                {
                    "name": "cc",
                    "values": [],
                    "valueType": "string"
                },
                {
                    "name": "customSubject",
                    "values": [],
                    "valueType": "string"
                },
                {
                    "name": "customBody",
                    "values": [],
                    "valueType": "string"
                },
                {
                    "name": "locale",
                    "values": [],
                    "valueType": "string"
                },
                {
                    "name": "to",
                    "values": [
                        "User",
                        "Manager",
                        "Sponsors",
                        "{UserId}"
                    ],
                    "valueType": "string"
                }
            ]
        },
        {
            "category": "joiner,leaver,mover",
            "description": "Add user to selected Teams",
            "displayName": "Add user to Teams",
            "id": "e440ed8d-25a1-4618-84ce-091ed5be5594",
            "version": 1,
            "parameters": [
                {
                    "name": "teamID",
                    "values": [],
                    "valueType": "string"
                }
            ]
        },
        {
            "category": "leaver",
            "description": "Delete user account in Azure AD",
            "displayName": "Delete user account",
            "id": "8d18588d-9ad3-4c0f-99d0-ec215f0e3dff",
            "version": 1,
            "parameters": [
                {
                    "name": "deleteOnPremisesAccount",
                    "values": [
                        "true",
                        "false"
                    ],
                    "valueType": "enum"
                }
            ]
        },
        {
            "category": "joiner,leaver,mover",
            "description": "Remove user from membership of selected Teams",
            "displayName": "Remove user from selected Teams",
            "id": "06aa7acb-01af-4824-8899-b14e5ed788d6",
            "version": 1,
            "parameters": [
                {
                    "name": "teamID",
                    "values": [],
                    "valueType": "string"
                }
            ]
        },
        {
            "category": "leaver",
            "description": "Remove user from all Azure AD groups memberships",
            "displayName": "Remove user from all groups",
            "id": "b3a31406-2a15-4c9a-b25b-a658fa5f07fc",
            "version": 1,
            "parameters": []
        },
        {
            "category": "leaver",
            "description": "Remove user from all Teams memberships",
            "displayName": "Remove user from all Teams",
            "id": "81f7b200-2816-4b3b-8c5d-dc556f07b024",
            "version": 1,
            "parameters": []
        },
        {
            "category": "leaver",
            "description": "Remove all licenses assigned to the user",
            "displayName": "Remove all licenses for user",
            "id": "8fa97d28-3e52-4985-b3a9-a1126f9b8b4e",
            "version": 1,
            "parameters": []
        },
        {
            "category": "joiner,leaver,mover",
            "description": "Run a Custom Task Extension to callout to an external system.",
            "displayName": "Run a Custom Task Extension",
            "id": "4262b724-8dba-4fad-afc3-43fcbb497a0e",
            "version": 1,
            "parameters": [
                {
                    "name": "customTaskExtensionID",
                    "values": [],
                    "valueType": "string"
                }
            ]
        },
        {
            "category": "leaver",
            "description": "Send offboarding email to user’s manager before the last day of work",
            "displayName": "Send email before user’s last day",
            "id": "52853a3e-f4e5-4eb8-bb24-1ac09a1da935",
            "version": 1,
            "parameters": [
                {
                    "name": "cc",
                    "values": [],
                    "valueType": "string"
                },
                {
                    "name": "customSubject",
                    "values": [],
                    "valueType": "string"
                },
                {
                    "name": "customBody",
                    "values": [],
                    "valueType": "string"
                },
                {
                    "name": "locale",
                    "values": [],
                    "valueType": "string"
                },
                {
                    "name": "to",
                    "values": [
                        "User",
                        "Manager",
                        "Sponsors",
                        "{UserId}"
                    ],
                    "valueType": "string"
                }
            ]
        },
        {
            "category": "leaver",
            "description": "Send offboarding email to user’s manager on the last day of work",
            "displayName": "Send email on user’s last day",
            "id": "9c0a1eaf-5bda-4392-9d9e-6e155bb57411",
            "version": 1,
            "parameters": [
                {
                    "name": "cc",
                    "values": [],
                    "valueType": "string"
                },
                {
                    "name": "customSubject",
                    "values": [],
                    "valueType": "string"
                },
                {
                    "name": "customBody",
                    "values": [],
                    "valueType": "string"
                },
                {
                    "name": "locale",
                    "values": [],
                    "valueType": "string"
                },
                {
                    "name": "to",
                    "values": [
                        "User",
                        "Manager",
                        "Sponsors",
                        "{UserId}"
                    ],
                    "valueType": "string"
                }
            ]
        },
        {
            "category": "leaver",
            "description": "Send offboarding email to user’s manager after the last day of work",
            "displayName": "Send email after user’s last day",
            "id": "6f22ddd4-b3a5-47a4-a846-0d7c201a49ce",
            "version": 1,
            "parameters": [
                {
                    "name": "cc",
                    "values": [],
                    "valueType": "string"
                },
                {
                    "name": "customSubject",
                    "values": [],
                    "valueType": "string"
                },
                {
                    "name": "customBody",
                    "values": [],
                    "valueType": "string"
                },
                {
                    "name": "locale",
                    "values": [],
                    "valueType": "string"
                },
                {
                    "name": "to",
                    "values": [
                        "User",
                        "Manager",
                        "Sponsors",
                        "{UserId}"
                    ],
                    "valueType": "string"
                }
            ]
        },
        {
            "category": "joiner",
            "description": "Send onboarding reminder email to user’s manager",
            "displayName": "Send onboarding reminder email",
            "id": "3C860712-2D37-42A4-928F-5C93935D26A1",
            "version": 1,
            "parameters": [
                {
                    "name": "cc",
                    "values": [],
                    "valueType": "string"
                },
                {
                    "name": "customSubject",
                    "values": [],
                    "valueType": "string"
                },
                {
                    "name": "customBody",
                    "values": [],
                    "valueType": "string"
                },
                {
                    "name": "locale",
                    "values": [],
                    "valueType": "string"
                },
                {
                    "name": "to",
                    "values": [
                        "User",
                        "Manager",
                        "Sponsors",
                        "{UserId}"
                    ],
                    "valueType": "string"
                }
            ]
        },
        {
            "category": "joiner,mover",
            "description": "Request user assignment to selected access package",
            "displayName": "Request user access package assignment",
            "id": "c1ec1e76-f374-4375-aaa6-0bb6bd4c60be",
            "version": 1,
            "parameters": [
                {
                    "name": "assignmentPolicyId",
                    "values": [],
                    "valueType": "string"
                },
                {
                    "name": "accessPackageId",
                    "values": [],
                    "valueType": "string"
                }
            ]
        },
        {
            "category": "leaver,mover",
            "description": "Remove user assignment of selected access package",
            "displayName": "Remove access package assignment for user",
            "id": "4a0b64f2-c7ec-46ba-b117-18f262946c50",
            "version": 1,
            "parameters": [
                {
                    "name": "accessPackageId",
                    "values": [],
                    "valueType": "string"
                }
            ]
        },
        {
            "category": "leaver",
            "description": "Remove all access packages assigned to the user",
            "displayName": "Remove all access package assignments for user",
            "id": "42ae2956-193d-4f39-be06-691b8ac4fa1d",
            "version": 1,
            "parameters": []
        },
        {
            "category": "leaver,mover",
            "description": "Cancel all pending access packages assignment requests for the user",
            "displayName": "Cancel pending access package assignment requests for user",
            "id": "498770d9-bab7-4e4c-b73d-5ded82a1d0b3",
            "version": 1,
            "parameters": []
        },
        {
            "category": "mover",
            "description": "Send email to notify user’s manager of user move",
            "displayName": "Send email to notify manager of user move",
            "id": "aab41899-9972-422a-9d97-f626014578b7",
            "version": 1,
            "parameters": [
                {
                    "name": "cc",
                    "values": [],
                    "valueType": "string"
                },
                {
                    "name": "customSubject",
                    "values": [],
                    "valueType": "string"
                },
                {
                    "name": "customBody",
                    "values": [],
                    "valueType": "string"
                },
                {
                    "name": "locale",
                    "values": [],
                    "valueType": "string"
                },
                {
                    "name": "to",
                    "values": [
                        "User",
                        "Manager",
                        "Sponsors",
                        "{UserId}"
                    ],
                    "valueType": "string"
                }
            ]
        },
        {
            "category": "joiner,mover",
            "description": "Assign selected licenses to the user",
            "displayName": "Assign licenses to user",
            "id": "683c87a4-2ad4-420b-97d4-220d90afcd24",
            "version": 1,
            "parameters": [
                {
                    "name": "licenses",
                    "values": [],
                    "valueType": "string"
                }
            ]
        },
        {
            "category": "leaver,mover",
            "description": "Remove selected licenses assigned to the user",
            "displayName": "Remove licenses from user",
            "id": "5fc402a8-daaf-4b7b-9203-da868b05fc5f",
            "version": 1,
            "parameters": [
                {
                    "name": "licenses",
                    "values": [],
                    "valueType": "string"
                }
            ]
        },
        {
            "category": "leaver,mover",
            "description": "Revoke all refresh tokens for user",
            "displayName": "Revoke all refresh tokens for user",
            "id": "509589a4-0466-4471-829e-49c5e502bdee",
            "version": 1,
            "parameters": []
        }
    ]
}
```

### Example 2: Retrieve all built-in tasks supported for "joiner" workflows

#### Request

The following example shows a request. Because the **category** is a flagged enumeration that can be one of `joiner`, `joiner,leaver`, or `leaver`, the `has` operator checks tasks where the category includes "joiner".

- [HTTP](#tabpanel_2_http)
- [C#](#tabpanel_2_csharp)
- [Go](#tabpanel_2_go)
- [Java](#tabpanel_2_java)
- [JavaScript](#tabpanel_2_javascript)
- [PHP](#tabpanel_2_php)
- [PowerShell](#tabpanel_2_powershell)
- [Python](#tabpanel_2_python)

```http
GET https://graph.microsoft.com/v1.0/identityGovernance/lifecycleWorkflows/taskDefinitions?$filter=category has 'joiner'
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.IdentityGovernance.LifecycleWorkflows.TaskDefinitions.GetAsync((requestConfiguration) =>
{
	requestConfiguration.QueryParameters.Filter = "category has 'joiner'";
});
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphidentitygovernance "github.com/microsoftgraph/msgraph-sdk-go/identitygovernance"
	  //other-imports
)


requestFilter := "category has 'joiner'"

requestParameters := &graphidentitygovernance.LifecycleWorkflowsTaskDefinitionsRequestBuilderGetQueryParameters{
	Filter: &requestFilter,
}
configuration := &graphidentitygovernance.LifecycleWorkflowsTaskDefinitionsRequestBuilderGetRequestConfiguration{
	QueryParameters: requestParameters,
}

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
taskDefinitions, err := graphClient.IdentityGovernance().LifecycleWorkflows().TaskDefinitions().Get(context.Background(), configuration)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.models.identitygovernance.TaskDefinitionCollectionResponse result = graphClient.identityGovernance().lifecycleWorkflows().taskDefinitions().get(requestConfiguration -> {
	requestConfiguration.queryParameters.filter = "category has 'joiner'";
});
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let taskDefinitions = await client.api('/identityGovernance/lifecycleWorkflows/taskDefinitions')
	.filter('category has \'joiner\'')
	.get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\IdentityGovernance\LifecycleWorkflows\TaskDefinitions\TaskDefinitionsRequestBuilderGetRequestConfiguration;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestConfiguration = new TaskDefinitionsRequestBuilderGetRequestConfiguration();
$queryParameters = TaskDefinitionsRequestBuilderGetRequestConfiguration::createQueryParameters();
$queryParameters->filter = "category has 'joiner'";
$requestConfiguration->queryParameters = $queryParameters;


$result = $graphServiceClient->identityGovernance()->lifecycleWorkflows()->taskDefinitions()->get($requestConfiguration)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Identity.Governance

Get-MgIdentityGovernanceLifecycleWorkflowTaskDefinition -Filter "category has 'joiner'" 
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.identity_governance.lifecycle_workflows.task_definitions.task_definitions_request_builder import TaskDefinitionsRequestBuilder
from kiota_abstractions.base_request_configuration import RequestConfiguration
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
query_params = TaskDefinitionsRequestBuilder.TaskDefinitionsRequestBuilderGetQueryParameters(
		filter = "category has 'joiner'",
)

request_configuration = RequestConfiguration(
query_parameters = query_params,
)

result = await graph_client.identity_governance.lifecycle_workflows.task_definitions.get(request_configuration = request_configuration)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#identityGovernance/lifecycleWorkflows/taskDefinitions",
    "value": [
        {
            "category": "joiner,leaver",
            "description": "Add user to selected groups",
            "displayName": "Add User To Groups",
            "id": "22085229-5809-45e8-97fd-270d28d66910",
            "version": 1,
            "parameters": [
                {
                    "name": "groupID",
                    "values": [],
                    "valueType": "string"
                }
            ]
        },
        {
            "category": "joiner,leaver",
            "description": "Disable user account in the directory",
            "displayName": "Disable User Account",
            "id": "1dfdfcc7-52fa-4c2e-bf3a-e3919cc12950",
            "version": 1,
            "parameters": []
        },
        {
            "category": "joiner,leaver",
            "description": "Enable user account in the directory",
            "displayName": "Enable User Account",
            "id": "6fc52c9d-398b-4305-9763-15f42c1676fc",
            "version": 1,
            "parameters": []
        },
        {
            "category": "joiner,leaver",
            "description": "Remove user from membership of selected Azure AD groups",
            "displayName": "Remove user from selected groups",
            "id": "1953a66c-751c-45e5-8bfe-01462c70da3c",
            "version": 1,
            "parameters": [
                {
                    "name": "groupID",
                    "values": [],
                    "valueType": "string"
                }
            ]
        },
        {
            "category": "joiner",
            "description": "Generate Temporary Access Pass and send via email to user's manager",
            "displayName": "Generate TAP And Send Email",
            "id": "1b555e50-7f65-41d5-b514-5894a026d10d",
            "version": 1,
            "parameters": [
                {
                    "name": "tapLifetimeMinutes",
                    "values": [],
                    "valueType": "string"
                },
                {
                    "name": "tapIsUsableOnce",
                    "values": [
                        "true",
                        "false"
                    ],
                    "valueType": "enum"
                }
            ]
        },
        {
            "category": "joiner",
            "description": "Send welcome email to new hire",
            "displayName": "Send Welcome Email",
            "id": "70b29d51-b59a-4773-9280-8841dfd3f2ea",
            "version": 1,
            "parameters": []
        },
        {
            "category": "joiner,leaver",
            "description": "Add user to selected teams",
            "displayName": "Add User To Teams",
            "id": "e440ed8d-25a1-4618-84ce-091ed5be5594",
            "version": 1,
            "parameters": [
                {
                    "name": "teamID",
                    "values": [],
                    "valueType": "string"
                }
            ]
        },
        {
            "category": "joiner,leaver",
            "description": "Remove user from membership of selected Teams",
            "displayName": "Remove user from selected Teams",
            "id": "06aa7acb-01af-4824-8899-b14e5ed788d6",
            "version": 1,
            "parameters": [
                {
                    "name": "teamID",
                    "values": [],
                    "valueType": "string"
                }
            ]
        },
        {
            "category": "joiner,leaver",
            "description": "Run a Custom Task Extension to callout to an external system.",
            "displayName": "Run a Custom Task Extension",
            "id": "4262b724-8dba-4fad-afc3-43fcbb497a0e",
            "version": 1,
            "parameters": [
                {
                    "name": "customTaskExtensionID",
                    "values": [],
                    "valueType": "string"
                }
            ]
        }
    ]
}
```
