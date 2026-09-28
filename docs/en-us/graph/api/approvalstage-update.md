<!-- Source: https://learn.microsoft.com/en-us/graph/api/approvalstage-update?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-08-14 -->

# Update approvalStage

Namespace: microsoft.graph

Approve or deny an [approvalStage](https://learn.microsoft.com/en-us/graph/api/resources/approvalstage?view=graph-rest-1.0) object in an [approval](https://learn.microsoft.com/en-us/graph/api/resources/approval?view=graph-rest-1.0).

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

The following tables show the least privileged permission or permissions required to call this API on each supported resource type. Follow [best practices](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions) to request least privileged permissions. For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

### For entitlement management

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | EntitlementManagement.ReadWrite.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Not supported. | Not supported. |

### For PIM for Groups

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | PrivilegedAssignmentSchedule.ReadWrite.AzureADGroup | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Not supported. | Not supported. |

## HTTP request

To update an approval decision in entitlement management:

```http
PATCH /identityGovernance/entitlementManagement/accessPackageAssignmentApprovals/{accessPackageAssignmentRequestId}/stages/{approvalStageId}
```

To update an approval decision in PIM for Groups:

```http
PATCH /identityGovernance/privilegedAccess/group/assignmentApprovals/{privilegedaccessgroupassignmentschedulerequestId}/stages/{approvalStageId}
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

The following table shows the properties that are required for this method.

| Property | Type | Description |
| :--- | :--- | :--- |
| reviewResult | String | Decision of the approver. The possible values are: `Approve`, `Deny`. Required. |
| justification | String | Justification related to the approver's decision. |

## Response

If successful, this method returns a `204 No Content` response code in the response body. If the caller doesn't have the right permissions, the method returns a `403 Forbidden` response code, or if the approval ID isn't found, the method returns `404 Not found`. If the request has already been approved by another approver in the same approval stage, the method returns `409 Conflict` response code.

## Examples

### Request

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [PowerShell](#tabpanel_1_powershell)
- [Python](#tabpanel_1_python)

```http
PATCH https://graph.microsoft.com/v1.0/identityGovernance/entitlementManagement/accessPackageAssignmentApprovals/abd306ef-f7b2-4a10-9fd1-493454322489/stages/d4fa4045-4716-436d-aec5-57b0a713f095

{
 "reviewResult":"Approve",
 "justification":"OK"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new ApprovalStage
{
	ReviewResult = "Approve",
	Justification = "OK",
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.IdentityGovernance.EntitlementManagement.AccessPackageAssignmentApprovals["{approval-id}"].Stages["{approvalStage-id}"].PatchAsync(requestBody);
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

requestBody := graphmodels.NewApprovalStage()
reviewResult := "Approve"
requestBody.SetReviewResult(&reviewResult) 
justification := "OK"
requestBody.SetJustification(&justification) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
stages, err := graphClient.IdentityGovernance().EntitlementManagement().AccessPackageAssignmentApprovals().ByApprovalId("approval-id").Stages().ByApprovalStageId("approvalStage-id").Patch(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

ApprovalStage approvalStage = new ApprovalStage();
approvalStage.setReviewResult("Approve");
approvalStage.setJustification("OK");
ApprovalStage result = graphClient.identityGovernance().entitlementManagement().accessPackageAssignmentApprovals().byApprovalId("{approval-id}").stages().byApprovalStageId("{approvalStage-id}").patch(approvalStage);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const approvalStage = {
 reviewResult: 'Approve',
 justification: 'OK'
};

await client.api('/identityGovernance/entitlementManagement/accessPackageAssignmentApprovals/abd306ef-f7b2-4a10-9fd1-493454322489/stages/d4fa4045-4716-436d-aec5-57b0a713f095')
	.update(approvalStage);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\ApprovalStage;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new ApprovalStage();
$requestBody->setReviewResult('Approve');
$requestBody->setJustification('OK');

$result = $graphServiceClient->identityGovernance()->entitlementManagement()->accessPackageAssignmentApprovals()->byApprovalId('approval-id')->stages()->byApprovalStageId('approvalStage-id')->patch($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Identity.Governance

$params = @{
	reviewResult = "Approve"
	justification = "OK"
}

Update-MgEntitlementManagementAccessPackageAssignmentApprovalStage -ApprovalId $approvalId -ApprovalStageId $approvalStageId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.approval_stage import ApprovalStage
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = ApprovalStage(
	review_result = "Approve",
	justification = "OK",
)

result = await graph_client.identity_governance.entitlement_management.access_package_assignment_approvals.by_approval_id('approval-id').stages.by_approval_stage_id('approvalStage-id').patch(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

```http
HTTP/1.1 204 No Content
```
