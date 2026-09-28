<!-- Source: https://learn.microsoft.com/en-us/graph/api/organization-update?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-23 -->

# Update organization

Namespace: microsoft.graph

Update the properties of the currently authenticated organization. In this case, `organization` is defined as a collection of exactly one record, and so its **ID** must be specified in the request. The **ID** is also known as the **tenantId** of the organization.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Organization.ReadWrite.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Organization.ReadWrite.All | Not available. |

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
PATCH /organization/{id}
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json |

## Request body

In the request body, supply the values for relevant fields that should be updated. Existing properties that are not included in the request body will maintain their previous values or be recalculated based on changes to other property values. For best performance, you shouldn't include existing values that haven't changed.

| Property | Type | Description |
| :--- | :--- | :--- |
| marketingNotificationEmails | String collection | **Notes**: not nullable. |
| privacyProfile | [privacyProfile](https://learn.microsoft.com/en-us/graph/api/resources/privacyprofile?view=graph-rest-1.0) | The privacy profile of an organization \(set statementUrl and contactEmail\). |
| securityComplianceNotificationMails | String collection |  |
| securityComplianceNotificationPhones | String collection |  |
| technicalNotificationMails | String collection | **Notes**: not nullable. |

## Response

If successful, this method returns a `204 No Content` response code.

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

```http
PATCH https://graph.microsoft.com/v1.0/organization/84841066-274d-4ec0-a5c1-276be684bdd3
Content-type: application/json

{
  "marketingNotificationEmails" : ["marketing@contoso.com"],
  "privacyProfile" :
    {
      "contactEmail":"alice@contoso.com",
      "statementUrl":"https://contoso.com/privacyStatement"
    },
  "securityComplianceNotificationMails" : ["security@contoso.com"],
  "securityComplianceNotificationPhones" : ["(123) 456-7890"],
  "technicalNotificationMails" : ["tech@contoso.com"]
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new Organization
{
	MarketingNotificationEmails = new List<string>
	{
		"marketing@contoso.com",
	},
	PrivacyProfile = new PrivacyProfile
	{
		ContactEmail = "alice@contoso.com",
		StatementUrl = "https://contoso.com/privacyStatement",
	},
	SecurityComplianceNotificationMails = new List<string>
	{
		"security@contoso.com",
	},
	SecurityComplianceNotificationPhones = new List<string>
	{
		"(123) 456-7890",
	},
	TechnicalNotificationMails = new List<string>
	{
		"tech@contoso.com",
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Organization["{organization-id}"].PatchAsync(requestBody);
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

requestBody := graphmodels.NewOrganization()
marketingNotificationEmails := []string {
	"marketing@contoso.com",
}
requestBody.SetMarketingNotificationEmails(marketingNotificationEmails)
privacyProfile := graphmodels.NewPrivacyProfile()
contactEmail := "alice@contoso.com"
privacyProfile.SetContactEmail(&contactEmail) 
statementUrl := "https://contoso.com/privacyStatement"
privacyProfile.SetStatementUrl(&statementUrl) 
requestBody.SetPrivacyProfile(privacyProfile)
securityComplianceNotificationMails := []string {
	"security@contoso.com",
}
requestBody.SetSecurityComplianceNotificationMails(securityComplianceNotificationMails)
securityComplianceNotificationPhones := []string {
	"(123) 456-7890",
}
requestBody.SetSecurityComplianceNotificationPhones(securityComplianceNotificationPhones)
technicalNotificationMails := []string {
	"tech@contoso.com",
}
requestBody.SetTechnicalNotificationMails(technicalNotificationMails)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
organization, err := graphClient.Organization().ByOrganizationId("organization-id").Patch(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

Organization organization = new Organization();
LinkedList<String> marketingNotificationEmails = new LinkedList<String>();
marketingNotificationEmails.add("marketing@contoso.com");
organization.setMarketingNotificationEmails(marketingNotificationEmails);
PrivacyProfile privacyProfile = new PrivacyProfile();
privacyProfile.setContactEmail("alice@contoso.com");
privacyProfile.setStatementUrl("https://contoso.com/privacyStatement");
organization.setPrivacyProfile(privacyProfile);
LinkedList<String> securityComplianceNotificationMails = new LinkedList<String>();
securityComplianceNotificationMails.add("security@contoso.com");
organization.setSecurityComplianceNotificationMails(securityComplianceNotificationMails);
LinkedList<String> securityComplianceNotificationPhones = new LinkedList<String>();
securityComplianceNotificationPhones.add("(123) 456-7890");
organization.setSecurityComplianceNotificationPhones(securityComplianceNotificationPhones);
LinkedList<String> technicalNotificationMails = new LinkedList<String>();
technicalNotificationMails.add("tech@contoso.com");
organization.setTechnicalNotificationMails(technicalNotificationMails);
Organization result = graphClient.organization().byOrganizationId("{organization-id}").patch(organization);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const organization = {
  marketingNotificationEmails: ['marketing@contoso.com'],
  privacyProfile: 
    {
      contactEmail: 'alice@contoso.com',
      statementUrl: 'https://contoso.com/privacyStatement'
    },
  securityComplianceNotificationMails: ['security@contoso.com'],
  securityComplianceNotificationPhones: ['(123) 456-7890'],
  technicalNotificationMails: ['tech@contoso.com']
};

await client.api('/organization/84841066-274d-4ec0-a5c1-276be684bdd3')
	.update(organization);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\Organization;
use Microsoft\Graph\Generated\Models\PrivacyProfile;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new Organization();
$requestBody->setMarketingNotificationEmails(['marketing@contoso.com', 	]);
$privacyProfile = new PrivacyProfile();
$privacyProfile->setContactEmail('alice@contoso.com');
$privacyProfile->setStatementUrl('https://contoso.com/privacyStatement');
$requestBody->setPrivacyProfile($privacyProfile);
$requestBody->setSecurityComplianceNotificationMails(['security@contoso.com', 	]);
$requestBody->setSecurityComplianceNotificationPhones(['(123) 456-7890', 	]);
$requestBody->setTechnicalNotificationMails(['tech@contoso.com', 	]);

$result = $graphServiceClient->organization()->byOrganizationId('organization-id')->patch($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Identity.DirectoryManagement

$params = @{
	marketingNotificationEmails = @(
	"marketing@contoso.com"
)
privacyProfile = @{
	contactEmail = "alice@contoso.com"
	statementUrl = "https://contoso.com/privacyStatement"
}
securityComplianceNotificationMails = @(
"security@contoso.com"
)
securityComplianceNotificationPhones = @(
"(123) 456-7890"
)
technicalNotificationMails = @(
"tech@contoso.com"
)
}

Update-MgOrganization -OrganizationId $organizationId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.organization import Organization
from msgraph.generated.models.privacy_profile import PrivacyProfile
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = Organization(
	marketing_notification_emails = [
		"marketing@contoso.com",
	],
	privacy_profile = PrivacyProfile(
		contact_email = "alice@contoso.com",
		statement_url = "https://contoso.com/privacyStatement",
	),
	security_compliance_notification_mails = [
		"security@contoso.com",
	],
	security_compliance_notification_phones = [
		"(123) 456-7890",
	],
	technical_notification_mails = [
		"tech@contoso.com",
	],
)

result = await graph_client.organization.by_organization_id('organization-id').patch(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

```http
HTTP/1.1 204 No Content
```
