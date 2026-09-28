<!-- Source: https://learn.microsoft.com/en-us/graph/api/sharepointgroup-post-members?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-05-06 -->

# Create sharePointGroupMember

Namespace: microsoft.graph

Create a new [sharePointGroupMember](https://learn.microsoft.com/en-us/graph/api/resources/sharepointgroupmember?view=graph-rest-1.0) object within a [sharePointGroup](https://learn.microsoft.com/en-us/graph/api/resources/sharepointgroup?view=graph-rest-1.0). A **sharePointGroup** can have up to 5,000 users. For more information on service limits, see [SharePoint online limits](https://learn.microsoft.com/en-us/office365/servicedescriptions/sharepoint-online-service-description/sharepoint-online-limits#sharepoint-groups). Users and Microsoft 365 groups are supported as viable identities for **sharePointGroupMember**. The newly created **sharePointGroupMember** immediately inherits [driveItem](https://learn.microsoft.com/en-us/graph/api/resources/driveitem?view=graph-rest-1.0) permissions that have been granted to the **sharePointGroup**. It may take several minutes for substrate-related functionality, such as search and Copilot, to reflect the addition of the new **sharePointGroupMember**.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Not supported. | Not supported. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | FileStorageContainer.Selected | Not available. |

Note

In addition to Microsoft Graph permissions, applications calling this API must at least have the `AddPermissions` container type-level permission on the container type of the corresponding containers. For more information, see [container types](https://learn.microsoft.com/en-us/sharepoint/dev/embedded/concepts/app-concepts/containertypes). To learn more about container type-level permissions, see [SharePoint Embedded authorization](https://learn.microsoft.com/en-us/sharepoint/dev/embedded/concepts/app-concepts/auth#authorization).

## HTTP request

```http
POST /storage/fileStorage/containers/{fileStorageContainerId}/sharePointGroups/{sharePointGroupId}/members
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the [sharePointGroupMember](https://learn.microsoft.com/en-us/graph/api/resources/sharepointgroupmember?view=graph-rest-1.0) object.

You can specify the following property when you create a **sharePointGroupMember**.

| Property | Type | Description |
| :--- | :--- | :--- |
| identity | [sharePointIdentitySet](https://learn.microsoft.com/en-us/graph/api/resources/sharepointidentityset?view=graph-rest-1.0) | The identity of the **sharePointGroupMember**. Required. |

## Response

If successful, this method returns a `201 Created` response code and a [sharePointGroupMember](https://learn.microsoft.com/en-us/graph/api/resources/sharepointgroupmember?view=graph-rest-1.0) object in the response body.

## Examples

### Request

The following example shows a request that creates a **sharePointGroupMember** using their user principal name.

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [Python](#tabpanel_1_python)

```http
POST https://graph.microsoft.com/v1.0/storage/fileStorage/containers/b!ISJs1WRro0y0EWgkUYcktDa0mE8zSlFEqFzqRn70Zwp1CEtDEBZgQICPkRbil_5Z/sharePointGroups/ZGYwZTEzYTgtOTExOS00MjdmLWEzNjktOTdjOWM3YjNlYjcyXzE0/members
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.sharePointGroupMember",
  "identity": {
    "user": {
      "userPrincipalName": "john.smith@contoso.com"
    }
  }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new SharePointGroupMember
{
	OdataType = "#microsoft.graph.sharePointGroupMember",
	Identity = new SharePointIdentitySet
	{
		User = new Identity
		{
			AdditionalData = new Dictionary<string, object>
			{
				{
					"userPrincipalName" , "john.smith@contoso.com"
				},
			},
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Storage.FileStorage.Containers["{fileStorageContainer-id}"].SharePointGroups["{sharePointGroup-id}"].Members.PostAsync(requestBody);
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

requestBody := graphmodels.NewSharePointGroupMember()
identity := graphmodels.NewSharePointIdentitySet()
user := graphmodels.NewIdentity()
additionalData := map[string]interface{}{
	"userPrincipalName" : "john.smith@contoso.com", 
}
user.SetAdditionalData(additionalData)
identity.SetUser(user)
requestBody.SetIdentity(identity)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
members, err := graphClient.Storage().FileStorage().Containers().ByFileStorageContainerId("fileStorageContainer-id").SharePointGroups().BySharePointGroupId("sharePointGroup-id").Members().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

SharePointGroupMember sharePointGroupMember = new SharePointGroupMember();
sharePointGroupMember.setOdataType("#microsoft.graph.sharePointGroupMember");
SharePointIdentitySet identity = new SharePointIdentitySet();
Identity user = new Identity();
HashMap<String, Object> additionalData = new HashMap<String, Object>();
additionalData.put("userPrincipalName", "john.smith@contoso.com");
user.setAdditionalData(additionalData);
identity.setUser(user);
sharePointGroupMember.setIdentity(identity);
SharePointGroupMember result = graphClient.storage().fileStorage().containers().byFileStorageContainerId("{fileStorageContainer-id}").sharePointGroups().bySharePointGroupId("{sharePointGroup-id}").members().post(sharePointGroupMember);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const sharePointGroupMember = {
  '@odata.type': '#microsoft.graph.sharePointGroupMember',
  identity: {
    user: {
      userPrincipalName: 'john.smith@contoso.com'
    }
  }
};

await client.api('/storage/fileStorage/containers/b!ISJs1WRro0y0EWgkUYcktDa0mE8zSlFEqFzqRn70Zwp1CEtDEBZgQICPkRbil_5Z/sharePointGroups/ZGYwZTEzYTgtOTExOS00MjdmLWEzNjktOTdjOWM3YjNlYjcyXzE0/members')
	.post(sharePointGroupMember);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\SharePointGroupMember;
use Microsoft\Graph\Generated\Models\SharePointIdentitySet;
use Microsoft\Graph\Generated\Models\Identity;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new SharePointGroupMember();
$requestBody->setOdataType('#microsoft.graph.sharePointGroupMember');
$identity = new SharePointIdentitySet();
$identityUser = new Identity();
$additionalData = [
	'userPrincipalName' => 'john.smith@contoso.com',
];
$identityUser->setAdditionalData($additionalData);
$identity->setUser($identityUser);
$requestBody->setIdentity($identity);

$result = $graphServiceClient->storage()->fileStorage()->containers()->byFileStorageContainerId('fileStorageContainer-id')->sharePointGroups()->bySharePointGroupId('sharePointGroup-id')->members()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.share_point_group_member import SharePointGroupMember
from msgraph.generated.models.share_point_identity_set import SharePointIdentitySet
from msgraph.generated.models.identity import Identity
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = SharePointGroupMember(
	odata_type = "#microsoft.graph.sharePointGroupMember",
	identity = SharePointIdentitySet(
		user = Identity(
			additional_data = {
					"user_principal_name" : "john.smith@contoso.com",
			}
		),
	),
)

result = await graph_client.storage.file_storage.containers.by_file_storage_container_id('fileStorageContainer-id').share_point_groups.by_share_point_group_id('sharePointGroup-id').members.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

---

### Response

The following example shows the response with a JSON object that represents the created member.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.sharePointGroupMember",
  "id": "aTowIy5mfG1lbWJlcnNoaXB8YWRtaW5AYTgzMGVkYWQ5MDUwODQ5c3Bncm91cHRlc3QyLm9ubWljcm9zb2Z0LmNvbQ",
  "identity": {
    "@odata.type": "microsoft.graph.sharePointIdentitySet",
    "user": {
      "displayName": "John Smith",
      "email": "john.smith@contoso.onmicrosoft.com"
    }
  }
}
```
