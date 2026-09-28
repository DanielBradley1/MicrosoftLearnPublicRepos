<!-- Source: https://learn.microsoft.com/en-us/graph/api/distributionlist-deletemembers?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-08-19 -->

# distributionList: deleteMembers

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Remove members from a [distributionList](https://learn.microsoft.com/en-us/graph/api/resources/distributionlist?view=graph-rest-beta).

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Contacts.ReadWrite | Not available. |
| Delegated \(personal Microsoft account\) | Contacts.ReadWrite | Not available. |
| Application | Contacts.ReadWrite | Not available. |

## HTTP request

```http
POST /me/distributionLists/{distributionList-id}/deleteMembers
POST /users/{id | userPrincipalName}/distributionLists/{distributionList-id}/deleteMembers
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
| members | [member](https://learn.microsoft.com/en-us/graph/api/resources/member?view=graph-rest-beta) collection | The members to remove from the distribution list. Each member must include **type** and either **key**, **memberId**, or both. The **displayName** property is ignored. Required. |

## Response

If successful, this action returns a `200 OK` response code and a [distributionList](https://learn.microsoft.com/en-us/graph/api/resources/distributionlist?view=graph-rest-beta) object in the response body.

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
POST https://graph.microsoft.com/beta/me/distributionLists/AAMkAGI2THVSAAA=/deleteMembers
Content-Type: application/json

{
  "members": [
    {
      "key": "MeganB@contoso.com",
      "type": "mailbox"
    }
  ]
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.Me.DistributionLists.Item.DeleteMembers;
using Microsoft.Graph.Beta.Models;

var requestBody = new DeleteMembersPostRequestBody
{
	Members = new List<Member>
	{
		new Member
		{
			Key = "MeganB@contoso.com",
			Type = RecipientType.Mailbox,
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Me.DistributionLists["{distributionList-id}"].DeleteMembers.PostAsync(requestBody);
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
	  graphusers "github.com/microsoftgraph/msgraph-beta-sdk-go/users"
	  graphmodels "github.com/microsoftgraph/msgraph-beta-sdk-go/models"
	  //other-imports
)

requestBody := graphusers.NewItemDeleteMembersPostRequestBody()


member := graphmodels.NewMember()
key := "MeganB@contoso.com"
member.SetKey(&key) 
type := graphmodels.MAILBOX_RECIPIENTTYPE 
member.SetType(&type) 

members := []graphmodels.Memberable {
	member,
}
requestBody.SetMembers(members)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
deleteMembers, err := graphClient.Me().DistributionLists().ByDistributionListId("distributionList-id").DeleteMembers().Post(context.Background(), requestBody, nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.beta.users.item.distributionlists.item.deletemembers.DeleteMembersPostRequestBody deleteMembersPostRequestBody = new com.microsoft.graph.beta.users.item.distributionlists.item.deletemembers.DeleteMembersPostRequestBody();
LinkedList<Member> members = new LinkedList<Member>();
Member member = new Member();
member.setKey("MeganB@contoso.com");
member.setType(RecipientType.Mailbox);
members.add(member);
deleteMembersPostRequestBody.setMembers(members);
var result = graphClient.me().distributionLists().byDistributionListId("{distributionList-id}").deleteMembers().post(deleteMembersPostRequestBody);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const distributionList = {
  members: [
    {
      key: 'MeganB@contoso.com',
      type: 'mailbox'
    }
  ]
};

await client.api('/me/distributionLists/AAMkAGI2THVSAAA=/deleteMembers')
	.version('beta')
	.post(distributionList);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Users\Item\DistributionLists\Item\DeleteMembers\DeleteMembersPostRequestBody;
use Microsoft\Graph\Beta\Generated\Models\Member;
use Microsoft\Graph\Beta\Generated\Models\RecipientType;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new DeleteMembersPostRequestBody();
$membersMember1 = new Member();
$membersMember1->setKey('MeganB@contoso.com');
$membersMember1->setType(new RecipientType('mailbox'));
$membersArray []= $membersMember1;
$requestBody->setMembers($membersArray);


$result = $graphServiceClient->me()->distributionLists()->byDistributionListId('distributionList-id')->deleteMembers()->post($requestBody)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.users.item.distributionlists.item.delete_members.delete_members_post_request_body import DeleteMembersPostRequestBody
from msgraph_beta.generated.models.member import Member
from msgraph_beta.generated.models.recipient_type import RecipientType
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = DeleteMembersPostRequestBody(
	members = [
		Member(
			key = "MeganB@contoso.com",
			type = RecipientType.Mailbox,
		),
	],
)

result = await graph_client.me.distribution_lists.by_distribution_list_id('distributionList-id').delete_members.post(request_body)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "@odata.context": "https://graph.microsoft.com/beta/$metadata#users('user-id')/distributionLists/$entity",
  "id": "AAMkAGI2THVSAAA=",
  "displayName": "Project Team",
  "lastModifiedDateTime": "2024-03-17T11:15:00Z"
}
```
