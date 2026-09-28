<!-- Source: https://learn.microsoft.com/en-us/graph/api/teamsadministration-numberassignment-assignnumber?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-04-15 -->

# numberAssignment: assignNumber

Namespace: microsoft.graph.teamsAdministration

Creates an asynchronous order to assign a telephone number to a user account.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | TeamsTelephoneNumber.ReadWrite.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | TeamsTelephoneNumber.ReadWrite.All | Not available. |

## HTTP request

```http
POST /admin/teams/telephoneNumberManagement/numberAssignments/assignNumber
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the parameters.

The following table lists the parameters that are required when you call this action.

| Parameter | Type | Description |
| :--- | :--- | :--- |
| telephoneNumber | String | The telephone number intended to be assigned. \(Mandatory parameter\). |
| assignmentTargetId | String | The ID associated with User account. \(Mandatory parameter\). |
| numberType | microsoft.graph.teamsAdministration.numberType | Number type can be direct routing, calling plan, or operator connect. \(Mandatory parameter\) |
| assignmentCategory | microsoft.graph.teamsAdministration.assignmentCategory | Indicates the type of number assignment. Example: primary or private. Default is primary. |
| locationId | String | The ID associated with an emergency address. |

## Response

If successful, the method returns a `202 Accepted` response code with the URL in the response Location to retrieve the action result.

## Examples

### Request

The following example shows a request.

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [Python](#tabpanel_1_python)

```http
POST https://graph.microsoft.com/v1.0/admin/teams/telephoneNumberManagement/numberAssignments/assignNumber
Content-Type: application/json

{
  "telephoneNumber": "12061234567",
  "assignmentTargetId": "94ec379d-30a2-4cdb-a377-75e42f7a61e5",
  "numberType": "directRouting",
  "assignmentCategory": "primary"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Admin.Teams.TelephoneNumberManagement.NumberAssignments.MicrosoftGraphTeamsAdministrationAssignNumber;
using Microsoft.Graph.Models.TeamsAdministration;

var requestBody = new AssignNumberPostRequestBody
{
	TelephoneNumber = "12061234567",
	AssignmentTargetId = "94ec379d-30a2-4cdb-a377-75e42f7a61e5",
	NumberType = NumberType.DirectRouting,
	AssignmentCategory = AssignmentCategory.Primary,
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
await graphClient.Admin.Teams.TelephoneNumberManagement.NumberAssignments.MicrosoftGraphTeamsAdministrationAssignNumber.PostAsync(requestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphadmin "github.com/microsoftgraph/msgraph-sdk-go/admin"
	  graphmodelsteamsadministration "github.com/microsoftgraph/msgraph-sdk-go/models/teamsadministration"
	  //other-imports
)

requestBody := graphadmin.NewAssignNumberPostRequestBody()
telephoneNumber := "12061234567"
requestBody.SetTelephoneNumber(&telephoneNumber) 
assignmentTargetId := "94ec379d-30a2-4cdb-a377-75e42f7a61e5"
requestBody.SetAssignmentTargetId(&assignmentTargetId) 
numberType := graphmodels.DIRECTROUTING_NUMBERTYPE 
requestBody.SetNumberType(&numberType) 
assignmentCategory := graphmodels.PRIMARY_ASSIGNMENTCATEGORY 
requestBody.SetAssignmentCategory(&assignmentCategory) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
graphClient.Admin().Teams().TelephoneNumberManagement().NumberAssignments().MicrosoftGraphTeamsAdministrationAssignNumber().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.admin.teams.telephonenumbermanagement.numberassignments.microsoftgraphteamsadministrationassignnumber.AssignNumberPostRequestBody assignNumberPostRequestBody = new com.microsoft.graph.admin.teams.telephonenumbermanagement.numberassignments.microsoftgraphteamsadministrationassignnumber.AssignNumberPostRequestBody();
assignNumberPostRequestBody.setTelephoneNumber("12061234567");
assignNumberPostRequestBody.setAssignmentTargetId("94ec379d-30a2-4cdb-a377-75e42f7a61e5");
assignNumberPostRequestBody.setNumberType(com.microsoft.graph.models.teamsadministration.NumberType.DirectRouting);
assignNumberPostRequestBody.setAssignmentCategory(com.microsoft.graph.models.teamsadministration.AssignmentCategory.Primary);
graphClient.admin().teams().telephoneNumberManagement().numberAssignments().microsoftGraphTeamsAdministrationAssignNumber().post(assignNumberPostRequestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const assignNumber = {
  telephoneNumber: '12061234567',
  assignmentTargetId: '94ec379d-30a2-4cdb-a377-75e42f7a61e5',
  numberType: 'directRouting',
  assignmentCategory: 'primary'
};

await client.api('/admin/teams/telephoneNumberManagement/numberAssignments/assignNumber')
	.post(assignNumber);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Admin\Teams\TelephoneNumberManagement\NumberAssignments\MicrosoftGraphTeamsAdministrationAssignNumber\AssignNumberPostRequestBody;
use Microsoft\Graph\Generated\Models\TeamsAdministration\NumberType;
use Microsoft\Graph\Generated\Models\TeamsAdministration\AssignmentCategory;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new AssignNumberPostRequestBody();
$requestBody->setTelephoneNumber('12061234567');
$requestBody->setAssignmentTargetId('94ec379d-30a2-4cdb-a377-75e42f7a61e5');
$requestBody->setNumberType(new NumberType('directRouting'));
$requestBody->setAssignmentCategory(new AssignmentCategory('primary'));

$graphServiceClient->admin()->teams()->telephoneNumberManagement()->numberAssignments()->microsoftGraphTeamsAdministrationAssignNumber()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.admin.teams.telephonenumbermanagement.numberassignments.microsoft_graph_teams_administration_assign_number.assign_number_post_request_body import AssignNumberPostRequestBody
from msgraph.generated.models.number_type import NumberType
from msgraph.generated.models.assignment_category import AssignmentCategory
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = AssignNumberPostRequestBody(
	telephone_number = "12061234567",
	assignment_target_id = "94ec379d-30a2-4cdb-a377-75e42f7a61e5",
	number_type = NumberType.DirectRouting,
	assignment_category = AssignmentCategory.Primary,
)

await graph_client.admin.teams.telephone_number_management.number_assignments.microsoft_graph_teams_administration_assign_number.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 202 Accepted
Location: https://graph.microsoft.com/v1.0/admin/teams/telephoneNumberManagement/operations('QXNzaWdubWVudHw2Y2E4Yjc0Ni00YzgxLTRhY2EtOTUyNi1jZmNjNGRiYWYyMmI')
```
