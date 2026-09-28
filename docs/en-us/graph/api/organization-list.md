<!-- Source: https://learn.microsoft.com/en-us/graph/api/organization-list?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-23 -->

# List organizations

Namespace: microsoft.graph

Retrieve a list of organization objects. There's only one organization object in the collection.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

One of the following permissions is required to call this API. To learn more, including how to choose permissions, see [Permissions](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Permissions \(from least to most privileged\) |
| :--- | :--- |
| Delegated \(work or school account\) | User.Read, Organization.Read.All, Directory.Read.All, Organization.ReadWrite.All, Directory.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. |
| Application | Organization.Read.All, Directory.Read.All, Organization.ReadWrite.All, Directory.ReadWrite.All |

Important

Applications granted the *User.Read* permission are able to read only the **id**, **displayName**, and **verifiedDomains** properties of the organization. All other properties return with `null` values. To read all properties, use at least *Organization.Read.All*.

For delegated access using work or school accounts, the signed-in user must be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) or a custom role that grants the permissions required for this operation. This operation supports the following built-in roles, which provide only the least privilege necessary:

- AdHoc License Administrator
- Application Administrator
- Authentication Administrator
- Azure Information Protection Administrator
- Azure Information Protection Administrator
- Billing Administrator
- Cloud Application Administrator
- Compliance Data Administrator
- Customer LockBox Access Approver
- Customer LockBox Access Approver
- Desktop Analytics Administrator
- Directory Readers
- Directory Reviewer
- Directory Synchronization Accounts - for Microsoft Entra Connect and Microsoft Entra Cloud Sync services
- Directory Writers
- Dynamics 365 Administrator
- Dynamics 365 Administrator
- Global Reader
- Guest User
- Helpdesk Administrator
- Hybrid Identity Administrator
- Insights Administrator
- Kaizala Administrator
- License Administrator
- Mailbox Administrator
- Microsoft Managed Desktop Administrator
- Microsoft Store for Business User
- Modern Commerce Administrator
- Power BI Administrator
- Power BI Administrator
- Privileged Authentication Administrator
- Privileged Role Administrator
- Restricted Guest User
- Security Administrator
- Security Operator
- Security Reader
- Service Support Administrator
- Teams Administrator
- Teams Communications Administrator
- Teams Communications Support Engineer
- Teams Communications Support Specialist
- User
- User Administrator
- Volume Licensing Business Center User
- Volume Licensing Service Center User

## HTTP request

```http
GET /organization
```

## Optional query parameters

This method supports the `$select` [OData query parameter](https://learn.microsoft.com/en-us/graph/query-parameters) to help customize the response.

## Request headers

| Name | Type | Description |
| :--- | :--- | :--- |
| Authorization | string | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and collection of [organization](https://learn.microsoft.com/en-us/graph/api/resources/organization?view=graph-rest-1.0) objects in the response body. Only one object is returned in the collection.

## Example

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

```msgraph
GET https://graph.microsoft.com/v1.0/organization
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Organization.GetAsync();
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
organization, err := graphClient.Organization().Get(context.Background(), nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

OrganizationCollectionResponse result = graphClient.organization().get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let organization = await client.api('/organization')
	.get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);


$result = $graphServiceClient->organization()->get()->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Identity.DirectoryManagement

Get-MgOrganization
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python

result = await graph_client.organization.get()
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#organization",
    "value": [
        {
            "id": "84841066-274d-4ec0-a5c1-276be684bdd3",
            "deletedDateTime": null,
            "businessPhones": [
                "425-555-0100"
            ],
            "city": null,
            "country": null,
            "countryLetterCode": "NL",
            "createdDateTime": "2021-08-02T10:30:06Z",
            "defaultUsageLocation": "String",
            "displayName": "Contoso",
            "isMultipleDataLocationsForServicesEnabled": null,
            "marketingNotificationEmails": [],
            "onPremisesLastSyncDateTime": null,
            "onPremisesSyncEnabled": null,
            "partnerTenantType": "ResellerPartnerDelegatedAdmin",
            "postalCode": null,
            "preferredLanguage": "en",
            "securityComplianceNotificationMails": [],
            "securityComplianceNotificationPhones": [],
            "state": null,
            "street": null,
            "technicalNotificationMails": [
                "admin@contoso.com"
            ],
            "tenantType": "AAD",
            "directorySizeQuota": {
                "used": 698,
                "total": 50000
            },
            "assignedPlans": [
                {
                    "assignedDateTime": "2022-04-03T02:46:42Z",
                    "capabilityStatus": "Deleted",
                    "service": "Adallom",
                    "servicePlanId": "932ad362-64a8-4783-9106-97849a1a30b9"
                },
                {
                    "assignedDateTime": "2022-04-03T02:46:42Z",
                    "capabilityStatus": "Deleted",
                    "service": "MultiFactorService",
                    "servicePlanId": "8a256a2b-b617-496d-b51b-e76466e88db0"
                },
                {
                    "assignedDateTime": "2021-08-02T10:36:57Z",
                    "capabilityStatus": "Enabled",
                    "service": "exchange",
                    "servicePlanId": "113feb6c-3fe4-4440-bddc-54d774bf0318"
                },
                {
                    "assignedDateTime": "2021-08-02T10:36:02Z",
                    "capabilityStatus": "Deleted",
                    "service": "SCO",
                    "servicePlanId": "882e1d05-acd1-4ccb-8708-6ee03664b117"
                }
            ],
            "privacyProfile": {
                "contactEmail": "",
                "statementUrl": ""
            },
            "provisionedPlans": [
                {
                    "capabilityStatus": "Deleted",
                    "provisioningStatus": "Success",
                    "service": "Adallom"
                },
                {
                    "capabilityStatus": "Enabled",
                    "provisioningStatus": "Success",
                    "service": "exchange"
                }
            ],
            "verifiedDomains": [
                {
                    "capabilities": "Email, OfficeCommunicationsOnline",
                    "isDefault": true,
                    "isInitial": true,
                    "name": "contoso.com",
                    "type": "Managed"
                }
            ]
        }
    ]
}
```
