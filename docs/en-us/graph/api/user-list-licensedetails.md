<!-- Source: https://learn.microsoft.com/en-us/graph/api/user-list-licensedetails?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-23 -->

# List licenseDetails

Namespace: microsoft.graph

Retrieve a list of [licenseDetails](https://learn.microsoft.com/en-us/graph/api/resources/licensedetails?view=graph-rest-1.0) objects for enterprise users. This API returns details for licenses that are directly assigned and those transitively assigned through memberships in licensed groups.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | LicenseAssignment.Read.All | AgentIdUser.ReadWrite.All, AgentIdUser.ReadWrite.IdentityParentedBy, Directory.Read.All, Directory.ReadWrite.All, User.Read, User.Read.All, User.ReadWrite.All |
| Delegated \(personal Microsoft account\) | User.Read | Not available. |
| Application | Not supported. | Not supported. |

Important

In delegated scenarios with work or school accounts, the signed-in user must be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) or a custom role with the `microsoft.directory/users/licenseDetails/read` role permission. The following least privileged roles are supported for this operation:

- Guest Inviter
- Directory Readers
- Directory Writers
- License Administrator
- User Administrator

## HTTP request

```http
GET /me/licenseDetails
GET /users/{id}/licenseDetails
```

Note

Calling the `/me` endpoint requires a signed-in user and therefore a delegated permission. Application permissions aren't supported when using the `/me` endpoint.

## Optional query parameters

This method supports the `$select` query parameter. For general information, see [OData query parameters](https://learn.microsoft.com/en-us/graph/query-parameters).

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and a collection of [licenseDetails](https://learn.microsoft.com/en-us/graph/api/resources/licensedetails?view=graph-rest-1.0) objects in the response body.

## Example

### Request

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [PowerShell](#tabpanel_1_powershell)
- [Python](#tabpanel_1_python)

```msgraph
GET https://graph.microsoft.com/v1.0/me/licenseDetails
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Me.LicenseDetails.GetAsync();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  //other-imports
)


// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
licenseDetails, err := graphClient.Me().LicenseDetails().Get(context.Background(), nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

LicenseDetailsCollectionResponse result = graphClient.me().licenseDetails().get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let licenseDetails = await client.api('/me/licenseDetails')
	.get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);


$result = $graphServiceClient->me()->licenseDetails()->get()->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Users

# A UPN can also be used as -UserId.
Get-MgUserLicenseDetail -UserId $userId
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python

result = await graph_client.me.license_details.get()
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

Note: The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#users('48d31887-5fad-4d73-a9f5-3c356e68a038')/licenseDetails",
    "value": [
        {
            "id": "3RnS3Gi8m0u_C0ozp5a-NWAn38eBLPdOtXhbU5K1cd8",
            "skuId": "c7df2760-2c81-4ef7-b578-5b5392b571df",
            "skuPartNumber": "ENTERPRISEPREMIUM",
            "servicePlans": [
                {
                    "servicePlanId": "cd31b152-6326-4d1b-ae1b-997b625182e6",
                    "servicePlanName": "MIP_S_Exchange",
                    "provisioningStatus": "PendingProvisioning",
                    "appliesTo": "User"
                },
                {
                    "servicePlanId": "8e0c0a52-6a6c-4d40-8370-dd62790dcd70",
                    "servicePlanName": "THREAT_INTELLIGENCE",
                    "provisioningStatus": "Success",
                    "appliesTo": "User"
                },
                {
                    "servicePlanId": "9c0dab89-a30c-4117-86e7-97bda240acd2",
                    "servicePlanName": "POWERAPPS_O365_P3",
                    "provisioningStatus": "Success",
                    "appliesTo": "User"
                },
                {
                    "servicePlanId": "8c098270-9dd4-4350-9b30-ba4703f3b36b",
                    "servicePlanName": "ADALLOM_S_O365",
                    "provisioningStatus": "Success",
                    "appliesTo": "User"
                },
                {
                    "servicePlanId": "5dbe027f-2339-4123-9542-606e4d348a72",
                    "servicePlanName": "SHAREPOINTENTERPRISE",
                    "provisioningStatus": "Success",
                    "appliesTo": "User"
                }
            ]
        },
        {
            "id": "3RnS3Gi8m0u_C0ozp5a-Ne0iVHIF4g5Aqwo4mdijmMo",
            "skuId": "725422ed-e205-400e-ab0a-3899d8a398ca",
            "skuPartNumber": "SCHOOL_DATA_SYNC_P2",
            "servicePlans": [
                {
                    "servicePlanId": "113feb6c-3fe4-4440-bddc-54d774bf0318",
                    "servicePlanName": "EXCHANGE_S_FOUNDATION",
                    "provisioningStatus": "Success",
                    "appliesTo": "Company"
                },
                {
                    "servicePlanId": "500b6a2a-7a50-4f40-b5f9-160e5b8c2f48",
                    "servicePlanName": "SCHOOL_DATA_SYNC_P2",
                    "provisioningStatus": "Success",
                    "appliesTo": "User"
                }
            ]
        }
    ]
}
```
