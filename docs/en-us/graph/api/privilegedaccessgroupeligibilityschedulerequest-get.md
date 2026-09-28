<!-- Source: https://learn.microsoft.com/en-us/graph/api/privilegedaccessgroupeligibilityschedulerequest-get?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-23 -->

# Get privilegedAccessGroupEligibilityScheduleRequest

Namespace: microsoft.graph

Read the properties and relationships of a [privilegedAccessGroupEligibilityScheduleRequest](https://learn.microsoft.com/en-us/graph/api/resources/privilegedaccessgroupeligibilityschedulerequest?view=graph-rest-1.0) object.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | PrivilegedEligibilitySchedule.Read.AzureADGroup | PrivilegedEligibilitySchedule.ReadWrite.AzureADGroup |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | PrivilegedEligibilitySchedule.Read.AzureADGroup | PrivilegedEligibilitySchedule.ReadWrite.AzureADGroup |

Important

For delegated access using work or school accounts, the signed-in user must be an owner or member of the group or be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) or a custom role that grants the permissions required for this operation. This operation supports the following built-in roles, which provide only the least privilege necessary:

- For role-assignable groups: *Global Reader* or *Privileged Role Administrator*
- For non-role-assignable groups: *Global Reader*, *Directory Writer*, *Groups Administrator*, *Identity Governance Administrator*, or *User Administrator*

The role assignments for the calling user should be scoped at the directory level.

Other roles with permissions to manage groups \(such as Exchange Administrators for non-role-assignable Microsoft 365 groups\) and administrators with assignments scoped at administrative unit level can manage groups through groups API and override changes made in Microsoft Entra PIM through PIM for Groups APIs.

## HTTP request

```http
GET /identityGovernance/privilegedAccess/group/eligibilityScheduleRequests/{privilegedAccessGroupEligibilityScheduleRequestId}
```

## Optional query parameters

This method supports the `$select` and `$expand` OData query parameters to help customize the response. For general information, see [OData query parameters](https://learn.microsoft.com/en-us/graph/query-parameters).

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and a [privilegedAccessGroupEligibilityScheduleRequest](https://learn.microsoft.com/en-us/graph/api/resources/privilegedaccessgroupeligibilityschedulerequest?view=graph-rest-1.0) object in the response body.

## Examples

### Example 1: Get all eligibility schedule requests

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
GET https://graph.microsoft.com/v1.0/identityGovernance/privilegedAccess/group/eligibilityScheduleRequests/534b3d4d-3ba0-8429-3568-5e9cce6c2cbd
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.IdentityGovernance.PrivilegedAccess.Group.EligibilityScheduleRequests["{privilegedAccessGroupEligibilityScheduleRequest-id}"].GetAsync();
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
eligibilityScheduleRequests, err := graphClient.IdentityGovernance().PrivilegedAccess().Group().EligibilityScheduleRequests().ByPrivilegedAccessGroupEligibilityScheduleRequestId("privilegedAccessGroupEligibilityScheduleRequest-id").Get(context.Background(), nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

PrivilegedAccessGroupEligibilityScheduleRequest result = graphClient.identityGovernance().privilegedAccess().group().eligibilityScheduleRequests().byPrivilegedAccessGroupEligibilityScheduleRequestId("{privilegedAccessGroupEligibilityScheduleRequest-id}").get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let privilegedAccessGroupEligibilityScheduleRequest = await client.api('/identityGovernance/privilegedAccess/group/eligibilityScheduleRequests/534b3d4d-3ba0-8429-3568-5e9cce6c2cbd')
	.get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);


$result = $graphServiceClient->identityGovernance()->privilegedAccess()->group()->eligibilityScheduleRequests()->byPrivilegedAccessGroupEligibilityScheduleRequestId('privilegedAccessGroupEligibilityScheduleRequest-id')->get()->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Identity.Governance

Get-MgIdentityGovernancePrivilegedAccessGroupEligibilityScheduleRequest -PrivilegedAccessGroupEligibilityScheduleRequestId $privilegedAccessGroupEligibilityScheduleRequestId
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python

result = await graph_client.identity_governance.privileged_access.group.eligibility_schedule_requests.by_privileged_access_group_eligibility_schedule_request_id('privilegedAccessGroupEligibilityScheduleRequest-id').get()
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#identityGovernance/privilegedAccess/group/eligibilityScheduleRequests/$entity",
    "id": "534b3d4d-3ba0-8429-3568-5e9cce6c2cbd",
    "status": "Revoked",
    "completedDateTime": null,
    "createdDateTime": "2022-04-12T09:12:18.187Z",
    "approvalId": null,
    "customData": null,
    "createdBy": {
        "user": {
            "displayName": null,
            "id": "3fbd929d-8c56-4462-851e-0eb9a7b3a2a5"
        }
    },
    "action": "adminRemove",
    "isValidationOnly": false,
    "justification": null,
    "scheduleInfo": null,
    "ticketInfo": {
        "ticketNumber": null,
        "ticketSystem": null
    },
    "principalId": "3cce9d87-3986-4f19-8335-7ed075408ca2",
    "accessId": "member",
    "groupId": "2b5ed229-4072-478d-9504-a047ebd4b07d",
    "targetScheduleId": null
}
```

### Example 2: Get specific properties of all eligibility schedule requests

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
GET https://graph.microsoft.com/v1.0/identityGovernance/privilegedAccess/group/eligibilityScheduleRequests/534b3d4d-3ba0-8429-3568-5e9cce6c2cbd?$select=principalId,action,groupId
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.IdentityGovernance.PrivilegedAccess.Group.EligibilityScheduleRequests["{privilegedAccessGroupEligibilityScheduleRequest-id}"].GetAsync((requestConfiguration) =>
{
	requestConfiguration.QueryParameters.Select = new string []{ "principalId","action","groupId" };
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

requestParameters := &graphidentitygovernance.PrivilegedAccessGroupEligibilityScheduleRequestsItemRequestBuilderGetQueryParameters{
	Select: [] string {"principalId","action","groupId"},
}
configuration := &graphidentitygovernance.PrivilegedAccessGroupEligibilityScheduleRequestsItemRequestBuilderGetRequestConfiguration{
	QueryParameters: requestParameters,
}

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
eligibilityScheduleRequests, err := graphClient.IdentityGovernance().PrivilegedAccess().Group().EligibilityScheduleRequests().ByPrivilegedAccessGroupEligibilityScheduleRequestId("privilegedAccessGroupEligibilityScheduleRequest-id").Get(context.Background(), configuration)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

PrivilegedAccessGroupEligibilityScheduleRequest result = graphClient.identityGovernance().privilegedAccess().group().eligibilityScheduleRequests().byPrivilegedAccessGroupEligibilityScheduleRequestId("{privilegedAccessGroupEligibilityScheduleRequest-id}").get(requestConfiguration -> {
	requestConfiguration.queryParameters.select = new String []{"principalId", "action", "groupId"};
});
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let privilegedAccessGroupEligibilityScheduleRequest = await client.api('/identityGovernance/privilegedAccess/group/eligibilityScheduleRequests/534b3d4d-3ba0-8429-3568-5e9cce6c2cbd')
	.select('principalId,action,groupId')
	.get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\IdentityGovernance\PrivilegedAccess\Group\EligibilityScheduleRequests\Item\PrivilegedAccessGroupEligibilityScheduleRequestItemRequestBuilderGetRequestConfiguration;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestConfiguration = new PrivilegedAccessGroupEligibilityScheduleRequestItemRequestBuilderGetRequestConfiguration();
$queryParameters = PrivilegedAccessGroupEligibilityScheduleRequestItemRequestBuilderGetRequestConfiguration::createQueryParameters();
$queryParameters->select = ["principalId","action","groupId"];
$requestConfiguration->queryParameters = $queryParameters;


$result = $graphServiceClient->identityGovernance()->privilegedAccess()->group()->eligibilityScheduleRequests()->byPrivilegedAccessGroupEligibilityScheduleRequestId('privilegedAccessGroupEligibilityScheduleRequest-id')->get($requestConfiguration)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Identity.Governance

Get-MgIdentityGovernancePrivilegedAccessGroupEligibilityScheduleRequest -PrivilegedAccessGroupEligibilityScheduleRequestId $privilegedAccessGroupEligibilityScheduleRequestId -Property "principalId,action,groupId" 
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.identity_governance.privileged_access.group.eligibility_schedule_requests.item.privileged_access_group_eligibility_schedule_request_item_request_builder import PrivilegedAccessGroupEligibilityScheduleRequestItemRequestBuilder
from kiota_abstractions.base_request_configuration import RequestConfiguration
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
query_params = PrivilegedAccessGroupEligibilityScheduleRequestItemRequestBuilder.PrivilegedAccessGroupEligibilityScheduleRequestItemRequestBuilderGetQueryParameters(
		select = ["principalId","action","groupId"],
)

request_configuration = RequestConfiguration(
query_parameters = query_params,
)

result = await graph_client.identity_governance.privileged_access.group.eligibility_schedule_requests.by_privileged_access_group_eligibility_schedule_request_id('privilegedAccessGroupEligibilityScheduleRequest-id').get(request_configuration = request_configuration)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#identityGovernance/privilegedAccess/group/eligibilityScheduleRequests/$entity",
    "principalId": "3cce9d87-3986-4f19-8335-7ed075408ca2",
    "action": "adminRemove",
    "groupId": "2b5ed229-4072-478d-9504-a047ebd4b07d"
}
```
