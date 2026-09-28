<!-- Source: https://learn.microsoft.com/en-us/graph/api/networkaccess-forwardingprofile-update?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-03-21 -->

# Update forwardingProfile

Namespace: microsoft.graph.networkaccess

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Update an existing forwarding profile.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | NetworkAccess.ReadWrite.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | NetworkAccess.ReadWrite.All | Not available. |

Important

For delegated access using work or school accounts, the signed-in user must be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) or a custom role that grants the permissions required for this operation. This operation supports the following built-in roles, which provide only the least privilege necessary:

- Global Secure Access Administrator
- Security Administrator

## HTTP request

To update a base forwarding profile:

```http
PATCH /networkAccess/forwardingProfiles/{forwardingProfileId}
```

To update a forwarding profile for a branch:

```http
PATCH /networkAccess/connectivity/branches/{branchSiteId}/forwardingProfiles
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply *only* the values for properties to update. Existing properties that aren't included in the request body maintain their previous values or are recalculated based on changes to other property values.

The following table specifies the properties that can be updated.

| Property | Type | Description |
| :--- | :--- | :--- |
| name | String | Name of profile. Required. |
| associations | [microsoft.graph.networkaccess.association](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-association?view=graph-rest-beta) collection | Specifies the users, groups, devices, and branch locations that are associated with this traffic forwarding profile. Optional. You must include the **@odata.type** property with a value of the specific association in the body. For example, `"@odata.type": "#microsoft.graph.associatedBranch"`. |

## Response

If successful, this method returns a `204 No Content` response code.

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
PATCH https://graph.microsoft.com/beta/networkAccess/forwardingProfiles/{forwardingProfileId}
Content-Type: application/json

{
    "associations": [
        {
            "@odata.type": "#microsoft.graph.networkaccess.associatedBranch",
            "branchId": "88e5a488-92c3-45d6-ba56-e5cfa63677e8"
        }
    ]
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.Models.Networkaccess;

var requestBody = new ForwardingProfile
{
	Associations = new List<Association>
	{
		new AssociatedBranch
		{
			OdataType = "#microsoft.graph.networkaccess.associatedBranch",
			BranchId = "88e5a488-92c3-45d6-ba56-e5cfa63677e8",
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.NetworkAccess.ForwardingProfiles["{forwardingProfile-id}"].PatchAsync(requestBody);
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
	  graphmodelsnetworkaccess "github.com/microsoftgraph/msgraph-beta-sdk-go/models/networkaccess"
	  //other-imports
)

requestBody := graphmodelsnetworkaccess.NewForwardingProfile()


association := graphmodelsnetworkaccess.NewAssociatedBranch()
branchId := "88e5a488-92c3-45d6-ba56-e5cfa63677e8"
association.SetBranchId(&branchId) 

associations := []graphmodelsnetworkaccess.Associationable {
	association,
}
requestBody.SetAssociations(associations)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
forwardingProfiles, err := graphClient.NetworkAccess().ForwardingProfiles().ByForwardingProfileId("forwardingProfile-id").Patch(context.Background(), requestBody, nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.beta.models.networkaccess.ForwardingProfile forwardingProfile = new com.microsoft.graph.beta.models.networkaccess.ForwardingProfile();
LinkedList<com.microsoft.graph.beta.models.networkaccess.Association> associations = new LinkedList<com.microsoft.graph.beta.models.networkaccess.Association>();
com.microsoft.graph.beta.models.networkaccess.AssociatedBranch association = new com.microsoft.graph.beta.models.networkaccess.AssociatedBranch();
association.setOdataType("#microsoft.graph.networkaccess.associatedBranch");
association.setBranchId("88e5a488-92c3-45d6-ba56-e5cfa63677e8");
associations.add(association);
forwardingProfile.setAssociations(associations);
com.microsoft.graph.models.networkaccess.ForwardingProfile result = graphClient.networkAccess().forwardingProfiles().byForwardingProfileId("{forwardingProfile-id}").patch(forwardingProfile);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const forwardingProfile = {
    associations: [
        {
            '@odata.type': '#microsoft.graph.networkaccess.associatedBranch',
            branchId: '88e5a488-92c3-45d6-ba56-e5cfa63677e8'
        }
    ]
};

await client.api('/networkAccess/forwardingProfiles/{forwardingProfileId}')
	.version('beta')
	.update(forwardingProfile);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Models\Networkaccess\ForwardingProfile;
use Microsoft\Graph\Beta\Generated\Models\Networkaccess\Association;
use Microsoft\Graph\Beta\Generated\Models\Networkaccess\AssociatedBranch;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new ForwardingProfile();
$associationsAssociation1 = new AssociatedBranch();
$associationsAssociation1->setOdataType('#microsoft.graph.networkaccess.associatedBranch');
$associationsAssociation1->setBranchId('88e5a488-92c3-45d6-ba56-e5cfa63677e8');
$associationsArray []= $associationsAssociation1;
$requestBody->setAssociations($associationsArray);


$result = $graphServiceClient->networkAccess()->forwardingProfiles()->byForwardingProfileId('forwardingProfile-id')->patch($requestBody)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Beta.NetworkAccess

$params = @{
	associations = @(
		@{
			"@odata.type" = "#microsoft.graph.networkaccess.associatedBranch"
			branchId = "88e5a488-92c3-45d6-ba56-e5cfa63677e8"
		}
	)
}

Update-MgBetaNetworkAccessForwardingProfile -ForwardingProfileId $forwardingProfileId -BodyParameter $params
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.models.networkaccess.forwarding_profile import ForwardingProfile
from msgraph_beta.generated.models.networkaccess.association import Association
from msgraph_beta.generated.models.networkaccess.associated_branch import AssociatedBranch
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = ForwardingProfile(
	associations = [
		AssociatedBranch(
			odata_type = "#microsoft.graph.networkaccess.associatedBranch",
			branch_id = "88e5a488-92c3-45d6-ba56-e5cfa63677e8",
		),
	],
)

result = await graph_client.network_access.forwarding_profiles.by_forwarding_profile_id('forwardingProfile-id').patch(request_body)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

```http
HTTP/1.1 204 No Content
```
