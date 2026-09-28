<!-- Source: https://learn.microsoft.com/en-us/graph/api/ownerlessgrouppolicy-upsert?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-05-19 -->

# Create or update ownerlessGroupPolicy

Namespace: microsoft.graph

Create or update the [ownerlessGroupPolicy](https://learn.microsoft.com/en-us/graph/api/resources/ownerlessgrouppolicy?view=graph-rest-1.0) for the tenant. If the policy doesn't exist, it creates a new one; if the policy exists, it updates the existing policy.

To disable the policy, set **isEnabled** to `false`. Setting **isEnabled** to `false` clears the values of all other policy parameters.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Group.ReadWrite.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Not supported. | Not supported. |

Important

In delegated scenarios, the calling user must be assigned the *Groups Administrator* or *Exchange Administrator* [Microsoft Entra roles](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json).

## HTTP request

```http
PATCH /policies/ownerlessGroupPolicy
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the [ownerlessGroupPolicy](https://learn.microsoft.com/en-us/graph/api/resources/ownerlessgrouppolicy?view=graph-rest-1.0) object. For create operations and for update operations that enable the policy or change its configuration, all required properties must be provided because the API performs a full replacement of the policy configuration. To disable the policy, you can send only **isEnabled** set to `false`; when you do so, the service clears the values of all other policy parameters. Unlike the admin portal, the API doesn't apply default values for most properties, except for **targetOwners**, which defaults to allowing all members to become owners.

| Property | Type | Description |
| :--- | :--- | :--- |
| emailInfo | [emailDetails](https://learn.microsoft.com/en-us/graph/api/resources/emaildetails?view=graph-rest-1.0) | The email notification details for the ownerless group policy. Required when creating the policy or when enabling or updating the policy configuration. |
| enabledGroupIds | String collection | The collection of IDs for Microsoft 365 groups for which the policy is enabled. If empty, the policy is enabled for all groups in the tenant. Required when creating the policy or when enabling or updating the policy configuration. |
| isEnabled | Boolean | Indicates whether the ownerless group policy is enabled. Required. Setting this property to `false` clears the values of all other policy parameters; to disable the policy, you can send only this property with the value `false`. |
| maxMembersToNotify | Int64 | The maximum number of members to notify. Value range is 0-90. Required when creating the policy or when enabling or updating the policy configuration. |
| notificationDurationInWeeks | Int64 | The number of weeks for the notification duration. Value range is 1-7. Required when creating the policy or when enabling or updating the policy configuration. |
| policyWebUrl | String | The URL to the policy documentation. Optional. |
| targetOwners | [targetOwners](https://learn.microsoft.com/en-us/graph/api/resources/targetowners?view=graph-rest-1.0) | Specifies which members are eligible to become owners. If not specified, all members are eligible. Optional. |

## Response

If successful, this method returns a `200 OK` response code and an updated [ownerlessGroupPolicy](https://learn.microsoft.com/en-us/graph/api/resources/ownerlessgrouppolicy?view=graph-rest-1.0) object in the response body when the policy already exists, or a `201 Created` response code and a new [ownerlessGroupPolicy](https://learn.microsoft.com/en-us/graph/api/resources/ownerlessgrouppolicy?view=graph-rest-1.0) object in the response body when the policy is created.

### Errors

| Condition | Status code | Error code |
| :--- | :--- | :--- |
| **notificationDurationInWeeks** is not in range 1-7 | 400 Bad Request | `badRequest` |
| **maxMembersToNotify** is not in range 0-90 | 400 Bad Request | `badRequest` |

## Examples

### Example 1: Create or update the ownerless group policy

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

```http
PATCH https://graph.microsoft.com/v1.0/policies/ownerlessGroupPolicy
Content-Type: application/json

{
  "isEnabled": true,
  "notificationDurationInWeeks": 3,
  "maxMembersToNotify": 40,
  "policyWebUrl": "https://contoso.com/policies/ownerless-groups",
  "targetOwners": {
    "notifyMembers": "allowSelected",
    "securityGroups": [
      "security-group1@contoso.com",
      "security-group2@contoso.com"
    ]
  },
  "enabledGroupIds": [
    "b14e5eb2-a0a1-4c8f-b83e-940526219200",
    "454dde77-ac2b-421b-a6ab-165be910e0fc"
  ],
  "emailInfo": {
    "senderEmailAddress": "admin@contoso.com",
    "subject": "Need your help with $Group.Name group",
    "body": "Hi $User.DisplayName, \n\nYou'\''re receiving this email because you'\''ve been an active member of the $Group.Name group. This group currently does not have an owner. \n\nPer your organization'\''s policy, the group requires an owner.\n\nThank you"
  }
}
```

```
Snippet not available
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```
Snippet not available
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```
Snippet not available
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const ownerlessGroupPolicy = {
  isEnabled: true,
  notificationDurationInWeeks: 3,
  maxMembersToNotify: 40,
  policyWebUrl: 'https://contoso.com/policies/ownerless-groups',
  targetOwners: {
    notifyMembers: 'allowSelected',
    securityGroups: [
      'security-group1@contoso.com',
      'security-group2@contoso.com'
    ]
  },
  enabledGroupIds: [
    'b14e5eb2-a0a1-4c8f-b83e-940526219200',
    '454dde77-ac2b-421b-a6ab-165be910e0fc'
  ],
  emailInfo: {
    senderEmailAddress: 'admin@contoso.com',
    subject: 'Need your help with $Group.Name group',
    body: 'Hi $User.DisplayName, \n\nYou\'\\'\'re receiving this email because you\'\\'\'ve been an active member of the $Group.Name group. This group currently does not have an owner. \n\nPer your organization\'\\'\'s policy, the group requires an owner.\n\nThank you'
  }
};

await client.api('/policies/ownerlessGroupPolicy')
	.update(ownerlessGroupPolicy);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```
Snippet not available
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```
Snippet not available
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```
Snippet not available
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.ownerlessGroupPolicy",
  "isEnabled": true,
  "notificationDurationInWeeks": 3,
  "maxMembersToNotify": 40,
  "enabledGroupIds": [
    "b14e5eb2-a0a1-4c8f-b83e-940526219200",
    "454dde77-ac2b-421b-a6ab-165be910e0fc"
  ],
  "emailInfo": {
    "@odata.type": "microsoft.graph.emailDetails",
    "senderEmailAddress": "admin@contoso.com",
    "subject": "Need your help with $Group.Name group",
    "body": "Hi $User.DisplayName, \n\nYou'\''re receiving this email because you'\''ve been an active member of the $Group.Name group. This group currently does not have an owner. \n\nPer your organization'\''s policy, the group requires an owner.\n\nThank you"
  },
  "policyWebUrl": "https://contoso.com/policies/ownerless-groups",
  "targetOwners": {
    "@odata.type": "microsoft.graph.targetOwners",
    "notifyMembers": "allowSelected",
    "securityGroups": [
      "security-group1@contoso.com",
      "security-group2@contoso.com"
    ]
  }
}
```

### Example 2: Disable the ownerless group policy

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

```http
PATCH https://graph.microsoft.com/v1.0/policies/ownerlessGroupPolicy
Content-Type: application/json

{
  "isEnabled": false
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new OwnerlessGroupPolicy
{
	IsEnabled = false,
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Policies.OwnerlessGroupPolicy.PatchAsync(requestBody);
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

requestBody := graphmodels.NewOwnerlessGroupPolicy()
isEnabled := false
requestBody.SetIsEnabled(&isEnabled) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
ownerlessGroupPolicy, err := graphClient.Policies().OwnerlessGroupPolicy().Patch(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

OwnerlessGroupPolicy ownerlessGroupPolicy = new OwnerlessGroupPolicy();
ownerlessGroupPolicy.setIsEnabled(false);
OwnerlessGroupPolicy result = graphClient.policies().ownerlessGroupPolicy().patch(ownerlessGroupPolicy);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const ownerlessGroupPolicy = {
  isEnabled: false
};

await client.api('/policies/ownerlessGroupPolicy')
	.update(ownerlessGroupPolicy);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\OwnerlessGroupPolicy;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new OwnerlessGroupPolicy();
$requestBody->setIsEnabled(false);

$result = $graphServiceClient->policies()->ownerlessGroupPolicy()->patch($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Identity.SignIns

$params = @{
	isEnabled = $false
}

Update-MgPolicyOwnerlessGroupPolicy -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.ownerless_group_policy import OwnerlessGroupPolicy
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = OwnerlessGroupPolicy(
	is_enabled = False,
)

result = await graph_client.policies.ownerless_group_policy.patch(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.ownerlessGroupPolicy",
  "isEnabled": false,
  "notificationDurationInWeeks": 0,
  "maxMembersToNotify": 0,
  "enabledGroupIds": [],
  "emailInfo": {
    "@odata.type": "microsoft.graph.emailDetails",
    "senderEmailAddress": "",
    "subject": "",
    "body": ""
  },
  "policyWebUrl": "",
  "targetOwners": {
    "@odata.type": "microsoft.graph.targetOwners",
    "notifyMembers": "all",
    "securityGroups": []
  }
}
```
