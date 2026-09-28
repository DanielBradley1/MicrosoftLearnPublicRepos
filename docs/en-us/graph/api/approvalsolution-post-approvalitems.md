<!-- Source: https://learn.microsoft.com/en-us/graph/api/approvalsolution-post-approvalitems?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-09-10 -->

# Create approvalItem

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Create a new [approvalItem](https://learn.microsoft.com/en-us/graph/api/resources/approvalitem?view=graph-rest-beta) object.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | ApprovalSolution.ReadWrite | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Not supported. | Not supported. |

## HTTP request

```http
POST /solutions/approval/approvalItems
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the [approvalItem](https://learn.microsoft.com/en-us/graph/api/resources/approvalitem?view=graph-rest-beta) object.

You can specify the following properties when creating an **approvalItem**.

| Property | Type | Description |
| :--- | :--- | :--- |
| displayName | String | The displayName of the approval request. Required. |
| description | String | The description of the approval request. Optional. |
| allowEmailNotification | Boolean | Indicates whether email notification is enabled. Optional. |
| approvalType | approvalItemType | The workflow type of the approval item. The possible values are: `basic`, `basicAwaitAll`, `custom`, `customAwaitAll`. Required. |
| responsePrompts | String collection | Approval response prompts. Only provide a value for this property when creating a custom approval item. For custom approval items, supply two response prompt strings. The default response prompts are "Approve" and "Reject". Optional. |
| approvers | [approvalIdentitySet](https://learn.microsoft.com/en-us/graph/api/resources/approvalidentityset?view=graph-rest-beta) collection | The identity of the principals to whom the approval item was initially assigned. Required. |
| owner | [approvalIdentitySet](https://learn.microsoft.com/en-us/graph/api/resources/approvalidentityset?view=graph-rest-beta) | The identity set of the principal who owns the approval item. Only provide a value for this property when creating an approval item on behalf of the principal. If the owner field isn't provided, the user information from the user context is used. Optional. |

## Response

If successful, this method returns a `202 Accepted` response code with the operation location in the header.

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
POST https://graph.microsoft.com/beta/solutions/approval/approvalItems
Content-Type: application/json

{
  "approvers":[
    {
      "user": {
        "id": "39d1a7fb-5f54-4c89-b513-241683718c9b",
        "displayName": "Jana Pihlak"
      }
    },
    {
      "group": {
        "id": "f2926053-5479-4bce-ad4c-8394ce51d6c5"
      }
    }
  ],
  "displayName":"Title of approval",
  "description":"Details of approval",
  "approvalType": "basic",
  "allowEmailNotification": true
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.Models;

var requestBody = new ApprovalItem
{
	Approvers = new List<ApprovalIdentitySet>
	{
		new ApprovalIdentitySet
		{
			User = new Identity
			{
				Id = "39d1a7fb-5f54-4c89-b513-241683718c9b",
				DisplayName = "Jana Pihlak",
			},
		},
		new ApprovalIdentitySet
		{
			Group = new Identity
			{
				Id = "f2926053-5479-4bce-ad4c-8394ce51d6c5",
			},
		},
	},
	DisplayName = "Title of approval",
	Description = "Details of approval",
	ApprovalType = ApprovalItemType.Basic,
	AllowEmailNotification = true,
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Solutions.Approval.ApprovalItems.PostAsync(requestBody);
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
	  graphmodels "github.com/microsoftgraph/msgraph-beta-sdk-go/models"
	  //other-imports
)

requestBody := graphmodels.NewApprovalItem()


approvalIdentitySet := graphmodels.NewApprovalIdentitySet()
user := graphmodels.NewIdentity()
id := "39d1a7fb-5f54-4c89-b513-241683718c9b"
user.SetId(&id) 
displayName := "Jana Pihlak"
user.SetDisplayName(&displayName) 
approvalIdentitySet.SetUser(user)
approvalIdentitySet1 := graphmodels.NewApprovalIdentitySet()
group := graphmodels.NewIdentity()
id := "f2926053-5479-4bce-ad4c-8394ce51d6c5"
group.SetId(&id) 
approvalIdentitySet1.SetGroup(group)

approvers := []graphmodels.ApprovalIdentitySetable {
	approvalIdentitySet,
	approvalIdentitySet1,
}
requestBody.SetApprovers(approvers)
displayName := "Title of approval"
requestBody.SetDisplayName(&displayName) 
description := "Details of approval"
requestBody.SetDescription(&description) 
approvalType := graphmodels.BASIC_APPROVALITEMTYPE 
requestBody.SetApprovalType(&approvalType) 
allowEmailNotification := true
requestBody.SetAllowEmailNotification(&allowEmailNotification) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
approvalItems, err := graphClient.Solutions().Approval().ApprovalItems().Post(context.Background(), requestBody, nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

ApprovalItem approvalItem = new ApprovalItem();
LinkedList<ApprovalIdentitySet> approvers = new LinkedList<ApprovalIdentitySet>();
ApprovalIdentitySet approvalIdentitySet = new ApprovalIdentitySet();
Identity user = new Identity();
user.setId("39d1a7fb-5f54-4c89-b513-241683718c9b");
user.setDisplayName("Jana Pihlak");
approvalIdentitySet.setUser(user);
approvers.add(approvalIdentitySet);
ApprovalIdentitySet approvalIdentitySet1 = new ApprovalIdentitySet();
Identity group = new Identity();
group.setId("f2926053-5479-4bce-ad4c-8394ce51d6c5");
approvalIdentitySet1.setGroup(group);
approvers.add(approvalIdentitySet1);
approvalItem.setApprovers(approvers);
approvalItem.setDisplayName("Title of approval");
approvalItem.setDescription("Details of approval");
approvalItem.setApprovalType(ApprovalItemType.Basic);
approvalItem.setAllowEmailNotification(true);
ApprovalItem result = graphClient.solutions().approval().approvalItems().post(approvalItem);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const approvalItem = {
  approvers: [
    {
      user: {
        id: '39d1a7fb-5f54-4c89-b513-241683718c9b',
        displayName: 'Jana Pihlak'
      }
    },
    {
      group: {
        id: 'f2926053-5479-4bce-ad4c-8394ce51d6c5'
      }
    }
  ],
  displayName: 'Title of approval',
  description: 'Details of approval',
  approvalType: 'basic',
  allowEmailNotification: true
};

await client.api('/solutions/approval/approvalItems')
	.version('beta')
	.post(approvalItem);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Models\ApprovalItem;
use Microsoft\Graph\Beta\Generated\Models\ApprovalIdentitySet;
use Microsoft\Graph\Beta\Generated\Models\Identity;
use Microsoft\Graph\Beta\Generated\Models\ApprovalItemType;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new ApprovalItem();
$approversApprovalIdentitySet1 = new ApprovalIdentitySet();
$approversApprovalIdentitySet1User = new Identity();
$approversApprovalIdentitySet1User->setId('39d1a7fb-5f54-4c89-b513-241683718c9b');
$approversApprovalIdentitySet1User->setDisplayName('Jana Pihlak');
$approversApprovalIdentitySet1->setUser($approversApprovalIdentitySet1User);
$approversArray []= $approversApprovalIdentitySet1;
$approversApprovalIdentitySet2 = new ApprovalIdentitySet();
$approversApprovalIdentitySet2Group = new Identity();
$approversApprovalIdentitySet2Group->setId('f2926053-5479-4bce-ad4c-8394ce51d6c5');
$approversApprovalIdentitySet2->setGroup($approversApprovalIdentitySet2Group);
$approversArray []= $approversApprovalIdentitySet2;
$requestBody->setApprovers($approversArray);

$requestBody->setDisplayName('Title of approval');
$requestBody->setDescription('Details of approval');
$requestBody->setApprovalType(new ApprovalItemType('basic'));
$requestBody->setAllowEmailNotification(true);

$result = $graphServiceClient->solutions()->approval()->approvalItems()->post($requestBody)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.models.approval_item import ApprovalItem
from msgraph_beta.generated.models.approval_identity_set import ApprovalIdentitySet
from msgraph_beta.generated.models.identity import Identity
from msgraph_beta.generated.models.approval_item_type import ApprovalItemType
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = ApprovalItem(
	approvers = [
		ApprovalIdentitySet(
			user = Identity(
				id = "39d1a7fb-5f54-4c89-b513-241683718c9b",
				display_name = "Jana Pihlak",
			),
		),
		ApprovalIdentitySet(
			group = Identity(
				id = "f2926053-5479-4bce-ad4c-8394ce51d6c5",
			),
		),
	],
	display_name = "Title of approval",
	description = "Details of approval",
	approval_type = ApprovalItemType.Basic,
	allow_email_notification = True,
)

result = await graph_client.solutions.approval.approval_items.post(request_body)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 202 Accepted
Location: https://graph.microsoft.com/beta/solutions/approval/operations/1a837203-b794-4cea-8def-47a7d1f89335
```
