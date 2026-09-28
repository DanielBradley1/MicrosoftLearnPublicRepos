<!-- Source: https://learn.microsoft.com/en-us/graph/api/privilegedaccessgroup-list-assignmentscheduleinstances?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-11-13 -->

# List assignmentScheduleInstances

Namespace: microsoft.graph

Get a list of the [privilegedAccessGroupAssignmentScheduleInstance](https://learn.microsoft.com/en-us/graph/api/resources/privilegedaccessgroupassignmentscheduleinstance?view=graph-rest-1.0) objects and their properties.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | PrivilegedAssignmentSchedule.Read.AzureADGroup | PrivilegedAssignmentSchedule.ReadWrite.AzureADGroup |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | PrivilegedAssignmentSchedule.Read.AzureADGroup | PrivilegedAssignmentSchedule.ReadWrite.AzureADGroup |

Important

For delegated access using work or school accounts, the signed-in user must be an owner or member of the group or be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) or a custom role that grants the permissions required for this operation. This operation supports the following built-in roles, which provide only the least privilege necessary:

- For role-assignable groups: *Global Reader* or *Privileged Role Administrator*
- For non-role-assignable groups: *Global Reader*, *Directory Writer*, *Groups Administrator*, *Identity Governance Administrator*, or *User Administrator*

The role assignments for the calling user should be scoped at the directory level.

Other roles with permissions to manage groups \(such as Exchange Administrators for non-role-assignable Microsoft 365 groups\) and administrators with assignments scoped at administrative unit level can manage groups through groups API and override changes made in Microsoft Entra PIM through PIM for Groups APIs.

## HTTP request

```http
GET /identityGovernance/privilegedAccess/group/assignmentScheduleInstances?$filter=groupId eq '{groupId}'
GET /identityGovernance/privilegedAccess/group/assignmentScheduleInstances?$filter=principalId eq '{principalId}'
```

## Query parameters

This method requires the `$filter` \(`eq`\) query parameter to scope the request to a **principalId** or a **groupId**.

This method supports the `$select`, `$filter`, and `$expand` OData query parameters to help customize the response. For general information, see [OData query parameters](https://learn.microsoft.com/en-us/graph/query-parameters).

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and a collection of [privilegedAccessGroupAssignmentScheduleInstance](https://learn.microsoft.com/en-us/graph/api/resources/privilegedaccessgroupassignmentscheduleinstance?view=graph-rest-1.0) objects in the response body.

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
GET https://graph.microsoft.com/v1.0/identityGovernance/privilegedAccess/group/assignmentScheduleInstances?$filter=groupId eq '2b5ed229-4072-478d-9504-a047ebd4b07d' 
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.IdentityGovernance.PrivilegedAccess.Group.AssignmentScheduleInstances.GetAsync((requestConfiguration) =>
{
	requestConfiguration.QueryParameters.Filter = "groupId eq '2b5ed229-4072-478d-9504-a047ebd4b07d'";
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


requestFilter := "groupId eq '2b5ed229-4072-478d-9504-a047ebd4b07d'"

requestParameters := &graphidentitygovernance.PrivilegedAccessGroupAssignmentScheduleInstancesRequestBuilderGetQueryParameters{
	Filter: &requestFilter,
}
configuration := &graphidentitygovernance.PrivilegedAccessGroupAssignmentScheduleInstancesRequestBuilderGetRequestConfiguration{
	QueryParameters: requestParameters,
}

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
assignmentScheduleInstances, err := graphClient.IdentityGovernance().PrivilegedAccess().Group().AssignmentScheduleInstances().Get(context.Background(), configuration)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

PrivilegedAccessGroupAssignmentScheduleInstanceCollectionResponse result = graphClient.identityGovernance().privilegedAccess().group().assignmentScheduleInstances().get(requestConfiguration -> {
	requestConfiguration.queryParameters.filter = "groupId eq '2b5ed229-4072-478d-9504-a047ebd4b07d'";
});
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let assignmentScheduleInstances = await client.api('/identityGovernance/privilegedAccess/group/assignmentScheduleInstances')
	.filter('groupId eq \'2b5ed229-4072-478d-9504-a047ebd4b07d\'')
	.get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\IdentityGovernance\PrivilegedAccess\Group\AssignmentScheduleInstances\AssignmentScheduleInstancesRequestBuilderGetRequestConfiguration;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestConfiguration = new AssignmentScheduleInstancesRequestBuilderGetRequestConfiguration();
$queryParameters = AssignmentScheduleInstancesRequestBuilderGetRequestConfiguration::createQueryParameters();
$queryParameters->filter = "groupId eq '2b5ed229-4072-478d-9504-a047ebd4b07d'";
$requestConfiguration->queryParameters = $queryParameters;


$result = $graphServiceClient->identityGovernance()->privilegedAccess()->group()->assignmentScheduleInstances()->get($requestConfiguration)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Identity.Governance

Get-MgIdentityGovernancePrivilegedAccessGroupAssignmentScheduleInstance -Filter "groupId eq '2b5ed229-4072-478d-9504-a047ebd4b07d'" 
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.identity_governance.privileged_access.group.assignment_schedule_instances.assignment_schedule_instances_request_builder import AssignmentScheduleInstancesRequestBuilder
from kiota_abstractions.base_request_configuration import RequestConfiguration
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
query_params = AssignmentScheduleInstancesRequestBuilder.AssignmentScheduleInstancesRequestBuilderGetQueryParameters(
		filter = "groupId eq '2b5ed229-4072-478d-9504-a047ebd4b07d'",
)

request_configuration = RequestConfiguration(
query_parameters = query_params,
)

result = await graph_client.identity_governance.privileged_access.group.assignment_schedule_instances.get(request_configuration = request_configuration)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#identityGovernance/privilegedAccess/group/assignmentScheduleInstances",
    "value": [
        {
            "id": "2b5ed229-4072-478d-9504-a047ebd4b07d_member_365163ce-df68-40b8-a782-1824c9eb7bcc",
            "principalId": "6be4b305-b75e-4efc-bfcc-31bd3b53a5f8",
            "startDateTime": "2023-09-29T15:48:00.273Z",
            "endDateTime": "2024-03-27T15:47:19.653Z",
            "assignmentType": "Assigned",
            "accessId": "member",
            "groupId": "2b5ed229-4072-478d-9504-a047ebd4b07d",
            "memberType": "Direct",
            "assignmentScheduleId": "2b5ed229-4072-478d-9504-a047ebd4b07d_member_f13739ce-d5f9-4a5a-845a-22fbccf0e14f"
        },
        {
            "id": "2b5ed229-4072-478d-9504-a047ebd4b07d_member_dce168aa-2909-4f10-8cc9-c98e82d8b507",
            "principalId": "56f2d212-e49c-42e3-8298-0188e5bef094",
            "startDateTime": null,
            "endDateTime": null,
            "assignmentType": "Assigned",
            "accessId": "member",
            "groupId": "2b5ed229-4072-478d-9504-a047ebd4b07d",
            "memberType": "Direct",
            "assignmentScheduleId": "2b5ed229-4072-478d-9504-a047ebd4b07d_member_dce168aa-2909-4f10-8cc9-c98e82d8b507"
        }
    ]
}
```
