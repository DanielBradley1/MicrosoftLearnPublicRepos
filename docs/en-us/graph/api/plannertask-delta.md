<!-- Source: https://learn.microsoft.com/en-us/graph/api/plannertask-delta?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-07-29 -->

# plannerTask: delta

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Get newly created, updated, or deleted [tasks](https://learn.microsoft.com/en-us/graph/api/resources/plannertask?view=graph-rest-beta) in either a Planner [plan](https://learn.microsoft.com/en-us/graph/api/resources/plannerplan?view=graph-rest-beta) or assigned to the signed-in user without having to perform a full read of the entire resource collection. For details, see [Use delta query to track changes in Microsoft Graph data](https://learn.microsoft.com/en-us/graph/delta-query-overview).

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Tasks.Read | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Tasks.Read.All | Not available. |

## HTTP request

```http
GET /planner/tasks/delta
GET /me/planner/tasks/delta
```

## Query parameters

Tracking changes incurs a round of one or more **delta** function calls. If you use any query parameter \(other than `$deltaToken` and `$skipToken`\), you must specify it in the initial **delta** request. Microsoft Graph automatically encodes any specified parameters into the token portion of the `@odata.nextLink` or `@odata.deltaLink` URL provided in the response. You only need to specify any query parameters once upfront. In subsequent requests, copy and apply the `@odata.nextLink` or `@odata.deltaLink` URL from the previous response. That URL already includes the encoded parameters.

| Query parameter | Type | Description |
| :--- | :--- | :--- |
| $deltaToken | string | A [state token](https://learn.microsoft.com/en-us/graph/delta-query-overview) returned in the `@odata.deltaLink` URL of the previous **delta** function call for the same resource collection, indicating the completion of that round of change tracking. Save and apply the entire `@odata.deltaLink` URL, including this token in the first request of the next round of change tracking for that collection. |
| $skipToken | string | A [state token](https://learn.microsoft.com/en-us/graph/delta-query-overview) returned in the `@odata.nextLink` URL of the previous **delta** function call, indicating there are further changes to be tracked in the same resource collection. |

When you call this API with application-only permissions, you must scope the request to a single plan by using a `$filter` query parameter of the form `planId eq '{planId}'`, and you must include a `$select` query parameter that specifies exactly these three non-id properties: `percentComplete`, `assignments`, and `creationSource`. For example, `$select=percentComplete,assignments,creationSource`. Selecting a different number of non-id properties returns a `405 Method Not Allowed` response, and selecting three non-id properties other than these returns a `403 Forbidden` response. The **id** property is always returned and can be included in `$select` without counting toward this limit.

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json |

## Request body

Don't supply a request body for this method.

## Response

If successful, this function returns a `200 OK` response code and a [plannerTask](https://learn.microsoft.com/en-us/graph/api/resources/plannertask?view=graph-rest-beta) collection in the response body.

## Examples

### Example 1: Get delta on tasks in a plannerPlan

The following example shows a request for the delta on **plannerTask** objects in a **plannerPlan**.

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

```msgraph
GET https://graph.microsoft.com/beta/planner/tasks/delta
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Planner.Tasks.Delta.GetAsDeltaGetResponseAsync();
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
	  //other-imports
)


// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
delta, err := graphClient.Planner().Tasks().Delta().GetAsDeltaGetResponse(context.Background(), nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

var result = graphClient.planner().tasks().delta().get();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let delta = await client.api('/planner/tasks/delta')
	.version('beta')
	.get();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);


$result = $graphServiceClient->planner()->tasks()->delta()->get()->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Beta.Planner

Get-MgBetaPlannerTaskDelta
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python

result = await graph_client.planner.tasks.delta.get()
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "@odata.context":"https://graph.microsoft.com/beta/$metadata#plannerTask",
  "@odata.deltaLink": "https://graph.microsoft.com/beta/planner/plans('-W4K7hIak0WlAwgJCn1sEWQABgjH')/tasks?%24expand=details&%24deltatoken=0%257eaa6c4c81-656f-40e8-a2c5-60f4116fa9a4",
  "value": [
    {
      "@odata.etag": "W/\"JzEtVGFzayAgQEBAQEBAQEBAQEBAQEBASCc=\"",
      "createdBy": "b40c85a0-1a66-4fa3-932f-cc9249ce8c29",
      "createdByApp": "09abbdfd-ed23-44ee-a2d9-a627aa1c90f3",
      "createdByAsIdentitySet": {
        "user": {
          "@odata.type": "#microsoft.taskServices.identity",
          "displayName": null,
          "id": "b40c85a0-1a66-4fa3-932f-cc9249ce8c29"
        },
        "application": {
          "@odata.type": "#microsoft.taskServices.identity",
          "displayName": null,
          "id": "09abbdfd-ed23-44ee-a2d9-a627aa1c90f3"
        }
      },
      "userContentLastModifiedBy": "b40c85a0-1a66-4fa3-932f-cc9249ce8c29",
      "userContentLastModifiedByApp": null,
      "userContentLastModifiedByAsIdentitySet": {
        "user": {
          "@odata.type": "#microsoft.taskServices.identity",
          "displayName": null,
          "id": "b40c85a0-1a66-4fa3-932f-cc9249ce8c29"
        }
      },
      "planId": "-W4K7hIak0WlAwgJCn1sEWQABgjH",
      "bucketId": "iz1mmIxX7EK0Yj7DmRsMs2QAEDXH",
      "title": "Testing",
      "orderHint": "8585371316800245114P\\",
      "assigneePriority": "8585371316123370883",
      "focusDateTime": null,
      "percentComplete": 0,
      "startDateTime": null,
      "createdDateTime": "2022-09-29T18:14:25.6091874Z",
      "userContentLastModifiedDate": "2022-09-29T18:14:33.1404924Z",
      "dueDateTime": null,
      "recurrence": null,
      "hasDescription": false,
      "previewType": "automatic",
      "completedDateTime": null,
      "completedBy": null,
      "completedByApp": null,
      "completedByAsIdentitySet": null,
      "referenceCount": 0,
      "checklistItemCount": 0,
      "activeChecklistItemCount": 0,
      "appliedCategories": {},
      "assignments": {
        "b40c85a0-1a66-4fa3-932f-cc9249ce8c29": {
          "@odata.type": "#microsoft.taskServices.assignment",
          "assignedBy": "b40c85a0-1a66-4fa3-932f-cc9249ce8c29",
          "assignedByAppId": null,
          "assignedByAsIdentitySet": {
            "user": {
              "@odata.type": "#microsoft.taskServices.identity",
              "displayName": null,
              "id": "b40c85a0-1a66-4fa3-932f-cc9249ce8c29"
            }
          },
          "assignedDateTime": "2022-09-29T18:14:33.1404924Z",
          "orderHint": "8585371316723527019PX",
          "createdBy": "b40c85a0-1a66-4fa3-932f-cc9249ce8c29",
          "createdByAppId": null,
          "createdByAsIdentitySet": {
            "user": {
              "@odata.type": "#microsoft.taskServices.identity",
              "displayName": null,
              "id": "b40c85a0-1a66-4fa3-932f-cc9249ce8c29"
            }
          }
        }
      },
      "conversationThreadId": null,
      "priority": 5,
      "creationSource": {
        "publication": null,
        "externalSource": null
      },
      "id": "aSOQ0mveu06bTSkfnJQay2QAIn_l",
      "version": "1-Task  @@@@@@@@@@@@@@@H",
      "details": {
        "@odata.etag": "W/\"JzEtVGFza0RldGFpbHMgQEBAQEBAQEBAQEBAQEBARCc=\"",
        "description": "",
        "notes": null,
        "previewType": "automatic",
        "references": {},
        "checklist": {},
        "id": "aSOQ0mveu06bTSkfnJQay2QAIn_l",
        "version": "1-TaskDetails @@@@@@@@@@@@@@@D"
      }
    }
  ]
}
```

### Example 2: Get delta on tasks assigned to a user

The following example shows a request for the delta on **plannerTask** objects assigned to a user.

#### Request

The following example shows a request.

- [HTTP](#tabpanel_2_http)
- [C#](#tabpanel_2_csharp)
- [Go](#tabpanel_2_go)
- [Java](#tabpanel_2_java)
- [JavaScript](#tabpanel_2_javascript)
- [PHP](#tabpanel_2_php)
- [PowerShell](#tabpanel_2_powershell)
- [Python](#tabpanel_2_python)

```msgraph
GET https://graph.microsoft.com/beta/me/planner/tasks/delta
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Me.Planner.Tasks.Delta.GetAsDeltaGetResponseAsync();
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
	  //other-imports
)


// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
delta, err := graphClient.Me().Planner().Tasks().Delta().GetAsDeltaGetResponse(context.Background(), nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

var result = graphClient.me().planner().tasks().delta().get();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let delta = await client.api('/me/planner/tasks/delta')
	.version('beta')
	.get();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);


$result = $graphServiceClient->me()->planner()->tasks()->delta()->get()->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Beta.Planner

# A UPN can also be used as -UserId.
Get-MgBetaUserPlannerTaskDelta -UserId $userId
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python

result = await graph_client.me.planner.tasks.delta.get()
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "@odata.context":"https://graph.microsoft.com/beta/$metadata#plannerTask",
  "@odata.deltaLink": "https://graph.microsoft.com/beta/me/planner/tasks/delta?%24expand=details&%24deltatoken=0%257eaa6c4c81-656f-40e8-a2c5-60f4116fa9a4",
  "value": [
    {
      "@odata.etag": "W/\"JzEtVGFzayAgQEBAQEBAQEBAQEBAQEBASCc=\"",
      "createdBy": "b40c85a0-1a66-4fa3-932f-cc9249ce8c29",
      "createdByApp": "09abbdfd-ed23-44ee-a2d9-a627aa1c90f3",
      "createdByAsIdentitySet": {
        "user": {
          "@odata.type": "#microsoft.taskServices.identity",
          "displayName": null,
          "id": "b40c85a0-1a66-4fa3-932f-cc9249ce8c29"
        },
        "application": {
          "@odata.type": "#microsoft.taskServices.identity",
          "displayName": null,
          "id": "09abbdfd-ed23-44ee-a2d9-a627aa1c90f3"
        }
      },
      "userContentLastModifiedBy": "b40c85a0-1a66-4fa3-932f-cc9249ce8c29",
      "userContentLastModifiedByApp": null,
      "userContentLastModifiedByAsIdentitySet": {
        "user": {
          "@odata.type": "#microsoft.taskServices.identity",
          "displayName": null,
          "id": "b40c85a0-1a66-4fa3-932f-cc9249ce8c29"
        }
      },
      "planId": "-W4K7hIak0WlAwgJCn1sEWQABgjH",
      "bucketId": "iz1mmIxX7EK0Yj7DmRsMs2QAEDXH",
      "title": "Testing",
      "orderHint": "8585371316800245114P\\",
      "assigneePriority": "8585371316123370883",
      "focusDateTime": null,
      "percentComplete": 0,
      "startDateTime": null,
      "createdDateTime": "2022-09-29T18:14:25.6091874Z",
      "userContentLastModifiedDate": "2022-09-29T18:14:33.1404924Z",
      "dueDateTime": null,
      "recurrence": null,
      "hasDescription": false,
      "previewType": "automatic",
      "completedDateTime": null,
      "completedBy": null,
      "completedByApp": null,
      "completedByAsIdentitySet": null,
      "referenceCount": 0,
      "checklistItemCount": 0,
      "activeChecklistItemCount": 0,
      "appliedCategories": {},
      "assignments": {
        "b40c85a0-1a66-4fa3-932f-cc9249ce8c29": {
          "@odata.type": "#microsoft.taskServices.assignment",
          "assignedBy": "b40c85a0-1a66-4fa3-932f-cc9249ce8c29",
          "assignedByAppId": null,
          "assignedByAsIdentitySet": {
            "user": {
              "@odata.type": "#microsoft.taskServices.identity",
              "displayName": null,
              "id": "b40c85a0-1a66-4fa3-932f-cc9249ce8c29"
            }
          },
          "assignedDateTime": "2022-09-29T18:14:33.1404924Z",
          "orderHint": "8585371316723527019PX",
          "createdBy": "b40c85a0-1a66-4fa3-932f-cc9249ce8c29",
          "createdByAppId": null,
          "createdByAsIdentitySet": {
            "user": {
              "@odata.type": "#microsoft.taskServices.identity",
              "displayName": null,
              "id": "b40c85a0-1a66-4fa3-932f-cc9249ce8c29"
            }
          }
        }
      },
      "conversationThreadId": null,
      "priority": 5,
      "creationSource": {
        "publication": null,
        "externalSource": null
      },
      "id": "aSOQ0mveu06bTSkfnJQay2QAIn_l",
      "version": "1-Task  @@@@@@@@@@@@@@@H",
      "details": {
        "@odata.etag": "W/\"JzEtVGFza0RldGFpbHMgQEBAQEBAQEBAQEBAQEBARCc=\"",
        "description": "",
        "notes": null,
        "previewType": "automatic",
        "references": {},
        "checklist": {},
        "id": "aSOQ0mveu06bTSkfnJQay2QAIn_l",
        "version": "1-TaskDetails @@@@@@@@@@@@@@@D"
      }
    }
  ]
}
```

### Example 3: Get delta on tasks in a plannerPlan by using application-only permissions

The following example shows a request that uses application-only permissions. As described in the [Query parameters](#query-parameters) section, the request must be scoped to a single plan by using a `$filter` query parameter and must select exactly the `percentComplete`, `assignments`, and `creationSource` properties by using a `$select` query parameter.

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
GET https://graph.microsoft.com/beta/planner/tasks/delta?$filter=planId eq '-W4K7hIak0WlAwgJCn1sEWQABgjH'&$select=percentComplete,assignments,creationSource
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Planner.Tasks.Delta.GetAsDeltaGetResponseAsync((requestConfiguration) =>
{
	requestConfiguration.QueryParameters.Filter = "planId eq '-W4K7hIak0WlAwgJCn1sEWQABgjH'";
	requestConfiguration.QueryParameters.Select = new string []{ "percentComplete","assignments","creationSource" };
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
	  graphplanner "github.com/microsoftgraph/msgraph-beta-sdk-go/planner"
	  //other-imports
)


requestFilter := "planId eq '-W4K7hIak0WlAwgJCn1sEWQABgjH'"

requestParameters := &graphplanner.TasksDeltaRequestBuilderGetQueryParameters{
	Filter: &requestFilter,
	Select: [] string {"percentComplete","assignments","creationSource"},
}
configuration := &graphplanner.TasksDeltaRequestBuilderGetRequestConfiguration{
	QueryParameters: requestParameters,
}

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
delta, err := graphClient.Planner().Tasks().Delta().GetAsDeltaGetResponse(context.Background(), configuration)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

var result = graphClient.planner().tasks().delta().get(requestConfiguration -> {
	requestConfiguration.queryParameters.filter = "planId eq '-W4K7hIak0WlAwgJCn1sEWQABgjH'";
	requestConfiguration.queryParameters.select = new String []{"percentComplete", "assignments", "creationSource"};
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

let delta = await client.api('/planner/tasks/delta')
	.version('beta')
	.filter('planId eq \'-W4K7hIak0WlAwgJCn1sEWQABgjH\'')
	.select('percentComplete,assignments,creationSource')
	.get();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Planner\Tasks\Delta\DeltaRequestBuilderGetRequestConfiguration;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestConfiguration = new DeltaRequestBuilderGetRequestConfiguration();
$queryParameters = DeltaRequestBuilderGetRequestConfiguration::createQueryParameters();
$queryParameters->filter = "planId eq '-W4K7hIak0WlAwgJCn1sEWQABgjH'";
$queryParameters->select = ["percentComplete","assignments","creationSource"];
$requestConfiguration->queryParameters = $queryParameters;


$result = $graphServiceClient->planner()->tasks()->delta()->get($requestConfiguration)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Beta.Planner

Get-MgBetaPlannerTaskDelta -Filter "planId eq '-W4K7hIak0WlAwgJCn1sEWQABgjH'" -Property "percentComplete,assignments,creationSource" 
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.planner.tasks.delta.delta_request_builder import DeltaRequestBuilder
from kiota_abstractions.base_request_configuration import RequestConfiguration
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
query_params = DeltaRequestBuilder.DeltaRequestBuilderGetQueryParameters(
		filter = "planId eq '-W4K7hIak0WlAwgJCn1sEWQABgjH'",
		select = ["percentComplete","assignments","creationSource"],
)

request_configuration = RequestConfiguration(
query_parameters = query_params,
)

result = await graph_client.planner.tasks.delta.get(request_configuration = request_configuration)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "@odata.context": "https://graph.microsoft.com/beta/$metadata#plannerTask",
  "@odata.deltaLink": "https://graph.microsoft.com/beta/planner/plans('-W4K7hIak0WlAwgJCn1sEWQABgjH')/tasks?%24select=percentComplete,assignments,creationSource&%24deltatoken=0%257eaa6c4c81-656f-40e8-a2c5-60f4116fa9a4",
  "value": [
    {
      "@odata.etag": "W/\"JzEtVGFzayAgQEBAQEBAQEBAQEBAQEBASCc=\"",
      "percentComplete": 0,
      "assignments": {
        "b40c85a0-1a66-4fa3-932f-cc9249ce8c29": {
          "@odata.type": "#microsoft.taskServices.assignment",
          "assignedBy": "b40c85a0-1a66-4fa3-932f-cc9249ce8c29",
          "assignedDateTime": "2022-09-29T18:14:33.1404924Z",
          "orderHint": "8585371316723527019PX"
        }
      },
      "creationSource": {
        "publication": null,
        "externalSource": null
      },
      "id": "aSOQ0mveu06bTSkfnJQay2QAIn_l"
    }
  ]
}
```
