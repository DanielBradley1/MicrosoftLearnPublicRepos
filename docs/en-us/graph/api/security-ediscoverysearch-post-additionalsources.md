<!-- Source: https://learn.microsoft.com/en-us/graph/api/security-ediscoverysearch-post-additionalsources?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-02-26 -->

# Add additional sources

Namespace: microsoft.graph.security

Create a new [additional source](https://learn.microsoft.com/en-us/graph/api/resources/security-datasource?view=graph-rest-1.0) associated with an [eDiscovery search](https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoverysearch?view=graph-rest-1.0).

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | eDiscovery.ReadWrite.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | eDiscovery.ReadWrite.All | Not available. |

Important

For delegated access using work or school accounts, the signed-in user must be assigned a supported [Microsoft Purview role](https://learn.microsoft.com/en-us/purview/edisc-permissions) through one of the following options:

- **eDiscovery Manager**. Allows members to create and manage eDiscovery cases they create, including creating custodians, holds, searches, and other case management tasks. However, eDiscovery Managers can only create and manage the cases they create. **This is the least privileged option for managing their own cases**.
- **eDiscovery Administrator**. Provides all the permissions of eDiscovery Manager, plus the ability to access and manage all eDiscovery cases in the organization, configure eDiscovery settings, and manage any case after adding themselves as a member.

Additional roles that provide write access to eDiscovery features:

- **Compliance Administrator**. Includes Case Management, Compliance Search, and Hold permissions.
- **Organization Management**. Includes Case Management, Compliance Search, Hold, and Search And Purge permissions.

The eDiscovery Manager and eDiscovery Administrator roles are part of the Microsoft Purview role groups and provide access to eDiscovery features through [role-based access control \(RBAC\)](https://learn.microsoft.com/en-us/purview/edisc-permissions#rbac-roles-related-to-ediscovery).

For more information about eDiscovery permissions and roles, see [Assign permissions in eDiscovery](https://learn.microsoft.com/en-us/purview/edisc-permissions).

## HTTP request

```http
POST /security/cases/ediscoveryCases/{ediscoveryCaseId}/searches/{ediscoverySearchId}/additionalSources
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the [dataSource](https://learn.microsoft.com/en-us/graph/api/resources/security-datasource?view=graph-rest-1.0) object.

You can specify the following properties when you create a **dataSource**.

> **Note:** Either **email** or **site** is required, but not both.

| Property | Type | Description |
| :--- | :--- | :--- |
| email | string | SMTP address of the mailbox. To get the email address of a group, use [List groups](https://learn.microsoft.com/en-us/graph/api/group-list?view=graph-rest-1.0) or [Get group](https://learn.microsoft.com/en-us/graph/api/group-get?view=graph-rest-1.0). You can query by the name of the group using `$filter`; for example, `https://graph.microsoft.com/v1.0/groups?$filter=displayName eq 'secret group'&$select=mail,id,displayName`. |
| site | string | URL of the site; for example, `https://contoso.sharepoint.com/sites/HumanResources`. |

## Response

If successful, this method returns a `201 Created` and a [microsoft.graph.security.dataSource](https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoverysearch?view=graph-rest-1.0) object in the response body.

## Examples

### Example 1: Create an additional eDiscovery source from a site source

#### Request

The following example shows a request that creates an eDiscovery source from a site source.

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [PowerShell](#tabpanel_1_powershell)
- [Python](#tabpanel_1_python)

```http
POST https://graph.microsoft.com/v1.0/security/cases/ediscoveryCases/{ediscoveryCaseId}/searches/{ediscoverySearchId}/additionalSources

{
    "@odata.type": "microsoft.graph.security.siteSource",
    "site": {
        "webUrl": "https://contoso.sharepoint.com/sites/SecretSite"
    }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models.Security;
using Microsoft.Graph.Models;

var requestBody = new SiteSource
{
	OdataType = "microsoft.graph.security.siteSource",
	Site = new Site
	{
		WebUrl = "https://contoso.sharepoint.com/sites/SecretSite",
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Security.Cases.EdiscoveryCases["{ediscoveryCase-id}"].Searches["{ediscoverySearch-id}"].AdditionalSources.PostAsync(requestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphmodelssecurity "github.com/microsoftgraph/msgraph-sdk-go/models/security"
	  graphmodels "github.com/microsoftgraph/msgraph-sdk-go/models"
	  //other-imports
)

requestBody := graphmodelssecurity.NewDataSource()
site := graphmodels.NewSite()
webUrl := "https://contoso.sharepoint.com/sites/SecretSite"
site.SetWebUrl(&webUrl) 
requestBody.SetSite(site)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
additionalSources, err := graphClient.Security().Cases().EdiscoveryCases().ByEdiscoveryCaseId("ediscoveryCase-id").Searches().ByEdiscoverySearchId("ediscoverySearch-id").AdditionalSources().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.models.security.SiteSource dataSource = new com.microsoft.graph.models.security.SiteSource();
dataSource.setOdataType("microsoft.graph.security.siteSource");
Site site = new Site();
site.setWebUrl("https://contoso.sharepoint.com/sites/SecretSite");
dataSource.setSite(site);
com.microsoft.graph.models.security.DataSource result = graphClient.security().cases().ediscoveryCases().byEdiscoveryCaseId("{ediscoveryCase-id}").searches().byEdiscoverySearchId("{ediscoverySearch-id}").additionalSources().post(dataSource);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const dataSource = {
    '@odata.type': 'microsoft.graph.security.siteSource',
    site: {
        webUrl: 'https://contoso.sharepoint.com/sites/SecretSite'
    }
};

await client.api('/security/cases/ediscoveryCases/{ediscoveryCaseId}/searches/{ediscoverySearchId}/additionalSources')
	.post(dataSource);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\Security\SiteSource;
use Microsoft\Graph\Generated\Models\Site;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new SiteSource();
$requestBody->setOdataType('microsoft.graph.security.siteSource');
$site = new Site();
$site->setWebUrl('https://contoso.sharepoint.com/sites/SecretSite');
$requestBody->setSite($site);

$result = $graphServiceClient->security()->cases()->ediscoveryCases()->byEdiscoveryCaseId('ediscoveryCase-id')->searches()->byEdiscoverySearchId('ediscoverySearch-id')->additionalSources()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Security

$params = @{
	"@odata.type" = "microsoft.graph.security.siteSource"
	site = @{
		webUrl = "https://contoso.sharepoint.com/sites/SecretSite"
	}
}

New-MgSecurityCaseEdiscoveryCaseSearchAdditionalSource -EdiscoveryCaseId $ediscoveryCaseId -EdiscoverySearchId $ediscoverySearchId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.security.site_source import SiteSource
from msgraph.generated.models.site import Site
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = SiteSource(
	odata_type = "microsoft.graph.security.siteSource",
	site = Site(
		web_url = "https://contoso.sharepoint.com/sites/SecretSite",
	),
)

result = await graph_client.security.cases.ediscovery_cases.by_ediscovery_case_id('ediscoveryCase-id').searches.by_ediscovery_search_id('ediscoverySearch-id').additional_sources.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#security/cases/ediscoveryCases('b0073e4e-4184-41c6-9eb7-8c8cc3e2288b')/searches('c61a5860-d634-4d14-aea7-d82b6f4eb7af')/additionalSources/$entity",
    "@odata.type": "#microsoft.graph.security.siteSource",
    "@odata.id": "https://graph.microsoft.com/v1.0/sites/46303732-3434-4630-3832-363333363441",
    "displayName": "Design - top secret",
    "createdDateTime": "2022-07-15T22:45:36.1096267Z",
    "holdStatus": "0",
    "id": "46303732-3434-4630-3832-363333363441",
    "createdBy": {
        "application": null,
        "user": {
            "id": null,
            "displayName": null
        }
    }
}
```

### Example 2: Create an additional eDiscovery source from a user source

#### Request

The following example shows a request that creates an eDiscovery source from a user source.

```
POST https://graph.microsoft.com/v1.0/security/cases/ediscoveryCases/17011798-ca63-4282-9cb3-0086f1042bfc/searches/2f5cc5a6-9728-4ba0-acfa-edce25e91244/additionalSources

{
    "@odata.type": "microsoft.graph.security.userSource",
    "email": "admin@edbig.onmicrosoft.com"
}
```

#### Response

The following example shows the response.

```http
HTTP/1.1 201 Created

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#security/cases/ediscoveryCases('17011798-ca63-4282-9cb3-0086f1042bfc')/searches('2f5cc5a6-9728-4ba0-acfa-edce25e91244')/additionalSources/$entity",
    "@odata.type": "#microsoft.graph.security.userSource",
    "displayName": "eDisco Big",
    "createdDateTime": "2024-11-19T20:11:11.5950513Z",
    "holdStatus": "0",
    "id": "5933247d-7011-494d-b9a6-65a3870d88fa",
    "email": "admin@edbig.onmicrosoft.com",
    "includedSources": "mailbox,site",
    "siteWebUrl": "https://edbig-my.sharepoint.com/personal/admin_edbig_onmicrosoft_com",
    "createdBy": {
        "application": null,
        "user": {
            "id": null,
            "displayName": null
        }
    }
}
```
