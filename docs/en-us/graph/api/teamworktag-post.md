<!-- Source: https://learn.microsoft.com/en-us/graph/api/teamworktag-post?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-23 -->

# Create teamworkTag

Namespace: microsoft.graph

Create a standard [tag](https://learn.microsoft.com/en-us/graph/api/resources/teamworktag?view=graph-rest-1.0) for members in a team.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | TeamworkTag.ReadWrite | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | TeamworkTag.ReadWrite.All | Not available. |

## HTTP request

```http
POST /teams/{team-id}/tags
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the [teamworkTag](https://learn.microsoft.com/en-us/graph/api/resources/teamworktag?view=graph-rest-1.0) object.

The following table shows the properties that are required when you create a [teamworkTag](https://learn.microsoft.com/en-us/graph/api/resources/teamworktag?view=graph-rest-1.0).

| Property | Type | Description |
| :--- | :--- | :--- |
| displayName | String | The name of the tag. The value can't be more than 40 characters. |
| members | [teamworkTagMember](https://learn.microsoft.com/en-us/graph/api/resources/teamworktagmember?view=graph-rest-1.0) collection | The unique identifier for the members of the team to add to the tag. The members count shouldn't be more than 25. |

## Response

If successful, this method returns a `201 Created` response code and a [teamworkTag](https://learn.microsoft.com/en-us/graph/api/resources/teamworktag?view=graph-rest-1.0) object in the response body.

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

```http
POST https://graph.microsoft.com/v1.0/teams/53c53217-fe77-4383-bc5a-ed4937a1aecd/tags
Content-Type: application/json

{
  "displayName": "Finance",
  "members": [
    {
      "userId": "92f6952f-61ca-4a94-8910-508a240bc167"
    },
    {
      "userId": "085d800c-b86b-4bfc-a857-9371ad1caf29"
    }
  ]
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new TeamworkTag
{
	DisplayName = "Finance",
	Members = new List<TeamworkTagMember>
	{
		new TeamworkTagMember
		{
			UserId = "92f6952f-61ca-4a94-8910-508a240bc167",
		},
		new TeamworkTagMember
		{
			UserId = "085d800c-b86b-4bfc-a857-9371ad1caf29",
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Teams["{team-id}"].Tags.PostAsync(requestBody);
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

requestBody := graphmodels.NewTeamworkTag()
displayName := "Finance"
requestBody.SetDisplayName(&displayName) 


teamworkTagMember := graphmodels.NewTeamworkTagMember()
userId := "92f6952f-61ca-4a94-8910-508a240bc167"
teamworkTagMember.SetUserId(&userId) 
teamworkTagMember1 := graphmodels.NewTeamworkTagMember()
userId := "085d800c-b86b-4bfc-a857-9371ad1caf29"
teamworkTagMember1.SetUserId(&userId) 

members := []graphmodels.TeamworkTagMemberable {
	teamworkTagMember,
	teamworkTagMember1,
}
requestBody.SetMembers(members)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
tags, err := graphClient.Teams().ByTeamId("team-id").Tags().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

TeamworkTag teamworkTag = new TeamworkTag();
teamworkTag.setDisplayName("Finance");
LinkedList<TeamworkTagMember> members = new LinkedList<TeamworkTagMember>();
TeamworkTagMember teamworkTagMember = new TeamworkTagMember();
teamworkTagMember.setUserId("92f6952f-61ca-4a94-8910-508a240bc167");
members.add(teamworkTagMember);
TeamworkTagMember teamworkTagMember1 = new TeamworkTagMember();
teamworkTagMember1.setUserId("085d800c-b86b-4bfc-a857-9371ad1caf29");
members.add(teamworkTagMember1);
teamworkTag.setMembers(members);
TeamworkTag result = graphClient.teams().byTeamId("{team-id}").tags().post(teamworkTag);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const teamworkTag = {
  displayName: 'Finance',
  members: [
    {
      userId: '92f6952f-61ca-4a94-8910-508a240bc167'
    },
    {
      userId: '085d800c-b86b-4bfc-a857-9371ad1caf29'
    }
  ]
};

await client.api('/teams/53c53217-fe77-4383-bc5a-ed4937a1aecd/tags')
	.post(teamworkTag);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\TeamworkTag;
use Microsoft\Graph\Generated\Models\TeamworkTagMember;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new TeamworkTag();
$requestBody->setDisplayName('Finance');
$membersTeamworkTagMember1 = new TeamworkTagMember();
$membersTeamworkTagMember1->setUserId('92f6952f-61ca-4a94-8910-508a240bc167');
$membersArray []= $membersTeamworkTagMember1;
$membersTeamworkTagMember2 = new TeamworkTagMember();
$membersTeamworkTagMember2->setUserId('085d800c-b86b-4bfc-a857-9371ad1caf29');
$membersArray []= $membersTeamworkTagMember2;
$requestBody->setMembers($membersArray);


$result = $graphServiceClient->teams()->byTeamId('team-id')->tags()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Teams

$params = @{
	displayName = "Finance"
	members = @(
		@{
			userId = "92f6952f-61ca-4a94-8910-508a240bc167"
		}
		@{
			userId = "085d800c-b86b-4bfc-a857-9371ad1caf29"
		}
	)
}

New-MgTeamTag -TeamId $teamId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.teamwork_tag import TeamworkTag
from msgraph.generated.models.teamwork_tag_member import TeamworkTagMember
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = TeamworkTag(
	display_name = "Finance",
	members = [
		TeamworkTagMember(
			user_id = "92f6952f-61ca-4a94-8910-508a240bc167",
		),
		TeamworkTagMember(
			user_id = "085d800c-b86b-4bfc-a857-9371ad1caf29",
		),
	],
)

result = await graph_client.teams.by_team_id('team-id').tags.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

```http
HTTP/1.1 201 Created
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.teamworkTag",
  "id": "MjQzMmI1N2ItMGFiZC00M2RiLWFhN2ItMTZlYWRkMTE1ZDM0IyM3ZDg4M2Q4Yi1hMTc5LTRkZDctOTNiMy1hOGQzZGUxYTIxMmUjI3RhY29VSjN2RGk==",
  "teamId": "53c53217-fe77-4383-bc5a-ed4937a1aecd",
  "displayName": "Finance",
  "memberCount": 2,
  "tagType": "standard"
}
```
