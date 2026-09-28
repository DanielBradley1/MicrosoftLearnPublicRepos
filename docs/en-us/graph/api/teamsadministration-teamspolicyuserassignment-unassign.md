<!-- Source: https://learn.microsoft.com/en-us/graph/api/teamsadministration-teamspolicyuserassignment-unassign?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-03-21 -->

# teamsPolicyUserAssignment: unassign

Namespace: microsoft.graph.teamsAdministration

Unassign a Teams [policy](https://learn.microsoft.com/en-us/graph/api/resources/teamsadministration-teamspolicyuserassignment?view=graph-rest-1.0) from a user using the user ID and policy type.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | TeamsPolicyUserAssign.ReadWrite.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | TeamsPolicyUserAssign.ReadWrite.All | Not available. |

## HTTP request

```http
POST /admin/teams/policy/userAssignments/unassign
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
| value | [microsoft.graph.teamsAdministration.teamsPolicyUserAssignment](https://learn.microsoft.com/en-us/graph/api/resources/teamsadministration-teamspolicyuserassignment?view=graph-rest-1.0) collection | A collection of **teamsPolicyUserAssignment** objects that specify the user ID and policy type to unassign. |

## Response

If successful, this action returns a `204 No Content` response code.

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
POST https://graph.microsoft.com/v1.0/admin/teams/policy/userAssignments/unassign
Content-Type: application/json

{
  "value": [
    {
      "@odata.type": "#microsoft.graph.teamsAdministration.teamsPolicyUserAssignment",
      "userId": "5c802b19-3600-83f1-1767-7b9edc7f38ab",
      "policyType": "TeamsMeetingPolicy"
    }
  ]
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Admin.Teams.Policy.UserAssignments.MicrosoftGraphTeamsAdministrationUnassign;
using Microsoft.Graph.Models.TeamsAdministration;

var requestBody = new UnassignPostRequestBody
{
	Value = new List<TeamsPolicyUserAssignment>
	{
		new TeamsPolicyUserAssignment
		{
			OdataType = "#microsoft.graph.teamsAdministration.teamsPolicyUserAssignment",
			UserId = "5c802b19-3600-83f1-1767-7b9edc7f38ab",
			PolicyType = "TeamsMeetingPolicy",
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
await graphClient.Admin.Teams.Policy.UserAssignments.MicrosoftGraphTeamsAdministrationUnassign.PostAsync(requestBody);
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

requestBody := graphadmin.NewUnassignPostRequestBody()


teamsPolicyUserAssignment := graphmodelsteamsadministration.NewTeamsPolicyUserAssignment()
userId := "5c802b19-3600-83f1-1767-7b9edc7f38ab"
teamsPolicyUserAssignment.SetUserId(&userId) 
policyType := "TeamsMeetingPolicy"
teamsPolicyUserAssignment.SetPolicyType(&policyType) 

value := []graphmodelsteamsadministration.TeamsPolicyUserAssignmentable {
	teamsPolicyUserAssignment,
}
requestBody.SetValue(value)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
graphClient.Admin().Teams().Policy().UserAssignments().MicrosoftGraphTeamsAdministrationUnassign().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.admin.teams.policy.userassignments.microsoftgraphteamsadministrationunassign.UnassignPostRequestBody unassignPostRequestBody = new com.microsoft.graph.admin.teams.policy.userassignments.microsoftgraphteamsadministrationunassign.UnassignPostRequestBody();
LinkedList<com.microsoft.graph.models.teamsadministration.TeamsPolicyUserAssignment> value = new LinkedList<com.microsoft.graph.models.teamsadministration.TeamsPolicyUserAssignment>();
com.microsoft.graph.models.teamsadministration.TeamsPolicyUserAssignment teamsPolicyUserAssignment = new com.microsoft.graph.models.teamsadministration.TeamsPolicyUserAssignment();
teamsPolicyUserAssignment.setOdataType("#microsoft.graph.teamsAdministration.teamsPolicyUserAssignment");
teamsPolicyUserAssignment.setUserId("5c802b19-3600-83f1-1767-7b9edc7f38ab");
teamsPolicyUserAssignment.setPolicyType("TeamsMeetingPolicy");
value.add(teamsPolicyUserAssignment);
unassignPostRequestBody.setValue(value);
graphClient.admin().teams().policy().userAssignments().microsoftGraphTeamsAdministrationUnassign().post(unassignPostRequestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const unassign = {
  value: [
    {
      '@odata.type': '#microsoft.graph.teamsAdministration.teamsPolicyUserAssignment',
      userId: '5c802b19-3600-83f1-1767-7b9edc7f38ab',
      policyType: 'TeamsMeetingPolicy'
    }
  ]
};

await client.api('/admin/teams/policy/userAssignments/unassign')
	.post(unassign);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Admin\Teams\Policy\UserAssignments\MicrosoftGraphTeamsAdministrationUnassign\UnassignPostRequestBody;
use Microsoft\Graph\Generated\Models\TeamsAdministration\TeamsPolicyUserAssignment;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new UnassignPostRequestBody();
$valueTeamsPolicyUserAssignment1 = new TeamsPolicyUserAssignment();
$valueTeamsPolicyUserAssignment1->setOdataType('#microsoft.graph.teamsAdministration.teamsPolicyUserAssignment');
$valueTeamsPolicyUserAssignment1->setUserId('5c802b19-3600-83f1-1767-7b9edc7f38ab');
$valueTeamsPolicyUserAssignment1->setPolicyType('TeamsMeetingPolicy');
$valueArray []= $valueTeamsPolicyUserAssignment1;
$requestBody->setValue($valueArray);


$graphServiceClient->admin()->teams()->policy()->userAssignments()->microsoftGraphTeamsAdministrationUnassign()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.admin.teams.policy.userassignments.microsoft_graph_teams_administration_unassign.unassign_post_request_body import UnassignPostRequestBody
from msgraph.generated.models.teams_administration.teams_policy_user_assignment import TeamsPolicyUserAssignment
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = UnassignPostRequestBody(
	value = [
		TeamsPolicyUserAssignment(
			odata_type = "#microsoft.graph.teamsAdministration.teamsPolicyUserAssignment",
			user_id = "5c802b19-3600-83f1-1767-7b9edc7f38ab",
			policy_type = "TeamsMeetingPolicy",
		),
	],
)

await graph_client.admin.teams.policy.user_assignments.microsoft_graph_teams_administration_unassign.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

```http
HTTP/1.1 204 No Content
```
