<!-- Source: https://learn.microsoft.com/en-us/graph/api/permission-grant?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-04-05 -->

# permission: grant

Namespace: microsoft.graph

Grant users access to a link represented by a [permission](https://learn.microsoft.com/en-us/graph/api/resources/permission?view=graph-rest-1.0).

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Files.ReadWrite | Files.ReadWrite.All, Sites.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Files.ReadWrite.All | Sites.ReadWrite.All |

## HTTP request

```http
POST /shares/{encoded-sharing-url}/permission/grant
```

### Path parameters

| Parameter Name | Value | Description |
| :--- | :--- | :--- |
| **encoded-sharing-url** | `string` | Required. A properly encoded sharing URL. |

### Encoding sharing URLs

To encode a sharing URL, use the following logic:

1. First, use base64 encode the URL.
2. Convert the base64 encoded result to [unpadded base64url format](https://en.wikipedia.org/wiki/Base64) by removing `=` characters from the end of the value, replacing `/` with `_` and `+` with `-`.\)
3. Append `u!` to be beginning of the string.

As an example, to encode a URL in C#:

```csharp
string sharingUrl = "https://onedrive.live.com/redir?resid=1231244193912!12&authKey=1201919!12921!1";
string base64Value = System.Convert.ToBase64String(System.Text.Encoding.UTF8.GetBytes(sharingUrl));
string encodedUrl = "u!" + base64Value.TrimEnd('=').Replace('/','_').Replace('+','-');
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

In the request body, provide a JSON object with the following parameters.

```json
{
  "recipients": [
    { "@odata.type": "microsoft.graph.driveRecipient" }
  ],
  "roles": [ "read | write"]
}
```

| Parameter | Type | Description |
| :--- | :--- | :--- |
| recipients | [driveRecipient](https://learn.microsoft.com/en-us/graph/api/resources/driverecipient?view=graph-rest-1.0) collection | A collection of recipients who receive access. |
| roles | String collection | If the link is an "existing access" link, specifies roles to be granted to the users. Otherwise must match the role of the link. |

For a list of available roles, see [roles property values](https://learn.microsoft.com/en-us/graph/api/resources/permission?view=graph-rest-1.0#roles-property-values).

## Response

If successful, this method returns a `200 OK` response code and a [permission](https://learn.microsoft.com/en-us/graph/api/resources/permission?view=graph-rest-1.0) collection in the response body.

A [permission](https://learn.microsoft.com/en-us/graph/api/resources/permission?view=graph-rest-1.0) representing the updated link will always be returned in the result set on success. The updated link can be identified by the presence of a 'link' facet containing the 'scope' property. In some cases it may be possible that the updated link has a different URL than the original link, in which case the new URL should be used.

Read the [Error Responses](https://learn.microsoft.com/en-us/graph/errors) topic for more info about how errors are returned.

## Example

This example grants the users john@contoso.com and ryan@external.com access to a sharing link without modifying other existing permissions on the link.

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
POST https://graph.microsoft.com/v1.0/shares/{encoded-sharing-url}/permission/grant
Content-type: application/json

{
  "recipients": [
    {
      "email": "john@contoso.com"
    },
    {
      "email": "ryan@external.com"
    }
  ],
  "roles": ["read"]
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Shares.Item.Permission.Grant;
using Microsoft.Graph.Models;

var requestBody = new GrantPostRequestBody
{
	Recipients = new List<DriveRecipient>
	{
		new DriveRecipient
		{
			Email = "john@contoso.com",
		},
		new DriveRecipient
		{
			Email = "ryan@external.com",
		},
	},
	Roles = new List<string>
	{
		"read",
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Shares["{sharedDriveItem-id}"].Permission.Grant.PostAsGrantPostResponseAsync(requestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphshares "github.com/microsoftgraph/msgraph-sdk-go/shares"
	  graphmodels "github.com/microsoftgraph/msgraph-sdk-go/models"
	  //other-imports
)

requestBody := graphshares.NewGrantPostRequestBody()


driveRecipient := graphmodels.NewDriveRecipient()
email := "john@contoso.com"
driveRecipient.SetEmail(&email) 
driveRecipient1 := graphmodels.NewDriveRecipient()
email := "ryan@external.com"
driveRecipient1.SetEmail(&email) 

recipients := []graphmodels.DriveRecipientable {
	driveRecipient,
	driveRecipient1,
}
requestBody.SetRecipients(recipients)
roles := []string {
	"read",
}
requestBody.SetRoles(roles)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
grant, err := graphClient.Shares().BySharedDriveItemId("sharedDriveItem-id").Permission().Grant().PostAsGrantPostResponse(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.shares.item.permission.grant.GrantPostRequestBody grantPostRequestBody = new com.microsoft.graph.shares.item.permission.grant.GrantPostRequestBody();
LinkedList<DriveRecipient> recipients = new LinkedList<DriveRecipient>();
DriveRecipient driveRecipient = new DriveRecipient();
driveRecipient.setEmail("john@contoso.com");
recipients.add(driveRecipient);
DriveRecipient driveRecipient1 = new DriveRecipient();
driveRecipient1.setEmail("ryan@external.com");
recipients.add(driveRecipient1);
grantPostRequestBody.setRecipients(recipients);
LinkedList<String> roles = new LinkedList<String>();
roles.add("read");
grantPostRequestBody.setRoles(roles);
var result = graphClient.shares().bySharedDriveItemId("{sharedDriveItem-id}").permission().grant().post(grantPostRequestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const permission = {
  recipients: [
    {
      email: 'john@contoso.com'
    },
    {
      email: 'ryan@external.com'
    }
  ],
  roles: ['read']
};

await client.api('/shares/{encoded-sharing-url}/permission/grant')
	.post(permission);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Shares\Item\Permission\Grant\GrantPostRequestBody;
use Microsoft\Graph\Generated\Models\DriveRecipient;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new GrantPostRequestBody();
$recipientsDriveRecipient1 = new DriveRecipient();
$recipientsDriveRecipient1->setEmail('john@contoso.com');
$recipientsArray []= $recipientsDriveRecipient1;
$recipientsDriveRecipient2 = new DriveRecipient();
$recipientsDriveRecipient2->setEmail('ryan@external.com');
$recipientsArray []= $recipientsDriveRecipient2;
$requestBody->setRecipients($recipientsArray);

$requestBody->setRoles(['read', ]);

$result = $graphServiceClient->shares()->bySharedDriveItemId('sharedDriveItem-id')->permission()->grant()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Files

$params = @{
	recipients = @(
		@{
			email = "john@contoso.com"
		}
		@{
			email = "ryan@external.com"
		}
	)
	roles = @(
	"read"
)
}

Grant-MgSharePermission -SharedDriveItemId $sharedDriveItemId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.shares.item.permission.grant.grant_post_request_body import GrantPostRequestBody
from msgraph.generated.models.drive_recipient import DriveRecipient
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = GrantPostRequestBody(
	recipients = [
		DriveRecipient(
			email = "john@contoso.com",
		),
		DriveRecipient(
			email = "ryan@external.com",
		),
	],
	roles = [
		"read",
	],
)

result = await graph_client.shares.by_shared_drive_item_id('sharedDriveItem-id').permission.grant.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

```http
HTTP/1.1 200 OK
Content-type: application/json

{
  "value": [
    {
      "hasPassword": false,
      "id": "5fab944a-47ec-48d0-a9b5-5178a926d00f",
      "link": {
        "preventsDownload": false,
        "scope": "users",
        "type": "view",
        "webUrl": "https://contoso.sharepoint.com/:t:/g/design/EZexPoDjW4dMtKFUfAl6BK4BvIUuss52hLYzihBfx-PD6Q"
      },
      "roles": [
        "read"
      ]
    }
  ]
}
```

> **Note:** The response object shown here might be shortened for readability.

If the link is an [existing access](https://learn.microsoft.com/en-us/graph/api/resources/permission?view=graph-rest-1.0) link, additional permissions will be returned representing the following:

- User-type permissions representing recipients who were successfully granted access. These can be identified by presence of the **grantedTo** property.
- Link-type permissions representing invitations that need to be sent to unrecognized external users for them to gain access. These can be identified by the presence of an [invitation](https://learn.microsoft.com/en-us/graph/api/resources/sharinginvitation?view=graph-rest-1.0) facet. These entries will contain a [link](https://learn.microsoft.com/en-us/graph/api/resources/sharinglink?view=graph-rest-1.0) with the invitation URL, and the grantedToIdentities collection will indicate the users to whom the link should be sent.

```http
HTTP/1.1 200 OK
Content-type: application/json

{
  "value": [
    {
      "hasPassword": false,
      "id": "00000000-0000-0000-0000-000000000000",
      "link": {
        "preventsDownload": false,
        "scope": "existingAccess",
        "type": "view",
        "webUrl": "https://contoso.sharepoint.com/teams/design/shareddocs/Document.docx"
      },
      "roles": [
        "read"
      ]
    },
    {
      "grantedTo": {
        "user": {
          "displayName": "John Smith",
          "email": "john@contoso.com",
          "id": "47aecee2-d061-4730-8ecb-4c61360441ae"
        }
      },
      "id": "aTowIy5mfG1lbWJlcnNoaXB8bGltaXRlZDJAa2xhbW9kYi5vbm1pY3Jvc29mdC5jb20",
      "roles": [
        "read"
      ]
    },
    {
      "grantedToIdentities": [
        {
          "user": {
            "email": "ryan@external.com"
          }
        }
      ],
      "invitation": {
        "signInRequired": true
      },
      "roles": [
        "read"
      ],
      "link": {
        "type": "view",
        "webUrl": "https://contoso.sharepoint.com/:t:/g/teams/design/EZexPoDjW4dMtKFUfAl6BK4Bw_F7gFH63O310A7lDtK0mQ"
      }
    }
  ]
}
```

> **Note:** The response object shown here might be shortened for readability.
