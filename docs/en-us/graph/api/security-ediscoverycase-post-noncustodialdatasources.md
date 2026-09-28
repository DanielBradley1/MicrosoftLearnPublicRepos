<!-- Source: https://learn.microsoft.com/en-us/graph/api/security-ediscoverycase-post-noncustodialdatasources?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-04-22 -->

# Create nonCustodialDataSources

Namespace: microsoft.graph.security

Create a new [ediscoveryNoncustodialDataSource](https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoverynoncustodialdatasource?view=graph-rest-1.0) object.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | eDiscovery.Read.All | eDiscovery.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | eDiscovery.Read.All | eDiscovery.ReadWrite.All |

Important

For delegated access using work or school accounts, the signed-in user must be assigned a supported [Microsoft Purview role](https://learn.microsoft.com/en-us/purview/edisc-permissions) through one of the following options:

- **eDiscovery Manager**. Allows members to manage custodians and data sources for eDiscovery cases they create. However, eDiscovery Managers can only manage custodians for the cases they create. **This is the least privileged option for managing custodians in their own cases**.
- **eDiscovery Administrator**. Provides all the permissions of eDiscovery Manager, plus the ability to manage custodians and data sources for all eDiscovery cases in the organization.

The Custodian role provides access to manage data sources \(mailboxes, SharePoint sites, and Teams\) associated with custodians in eDiscovery cases. This role is only available to members of the eDiscovery Manager role group.

For more information about eDiscovery permissions and roles, see [Assign permissions in eDiscovery](https://learn.microsoft.com/en-us/purview/edisc-permissions).

## HTTP request

```http
POST /security/cases/ediscoveryCases/{ediscoveryCaseId}/noncustodialDataSources
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the [ediscoveryNoncustodialDataSource](https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoverynoncustodialdatasource?view=graph-rest-1.0) object.

You can specify the following properties when you create an **ediscoveryNoncustodialDataSource**.

| Property | Type | Description |
| :--- | :--- | :--- |
| dataSource | [microsoft.graph.security.dataSource](https://learn.microsoft.com/en-us/graph/api/resources/security-datasource?view=graph-rest-1.0) | Required. Either a [microsoft.graph.security.userSource](https://learn.microsoft.com/en-us/graph/api/resources/security-usersource?view=graph-rest-1.0) or [microsoft.graph.security.siteSource](https://learn.microsoft.com/en-us/graph/api/resources/security-sitesource?view=graph-rest-1.0).<br><br>- For userSource, use `"dataSource" : { "@odata.type" : "microsoft.graph.security.userSource", "email" : "SMTP address"}`.<br>- For siteSource, use `"dataSource" : { "@odata.type" : "microsoft.graph.security.siteSource", "site@odata.bind" : "siteId" }`.<br>- Alternatively, use the webUrl directly: `"dataSource": {"@odata.type": "microsoft.graph.security.siteSource","site": {"webUrl": "https://contoso.sharepoint.com/sites/Design-topsecret"}}`.<br>- SharePoint site URLs must use the standard `.sharepoint.com` format. |

## Response

If successful, this method returns a `201 Created` response code and an [microsoft.graph.security.ediscoveryNoncustodialDataSource](https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoverynoncustodialdatasource?view=graph-rest-1.0) object in the response body.

## Examples

### Request

Here's an example of a request.

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [PowerShell](#tabpanel_1_powershell)
- [Python](#tabpanel_1_python)

```http
POST https://graph.microsoft.com/v1.0/security/cases/ediscoveryCases/b0073e4e-4184-41c6-9eb7-8c8cc3e2288b/noncustodialDataSources
Content-Type: application/json

{
    "dataSource": {
        "@odata.type": "microsoft.graph.security.siteSource",
        "site": {
            "webUrl": "https://m365x809305.sharepoint.com/sites/Design-topsecret"
        }
    }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models.Security;
using Microsoft.Graph.Models;

var requestBody = new EdiscoveryNoncustodialDataSource
{
	DataSource = new SiteSource
	{
		OdataType = "microsoft.graph.security.siteSource",
		Site = new Site
		{
			WebUrl = "https://m365x809305.sharepoint.com/sites/Design-topsecret",
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Security.Cases.EdiscoveryCases["{ediscoveryCase-id}"].NoncustodialDataSources.PostAsync(requestBody);
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

requestBody := graphmodelssecurity.NewEdiscoveryNoncustodialDataSource()
dataSource := graphmodelssecurity.NewSiteSource()
site := graphmodels.NewSite()
webUrl := "https://m365x809305.sharepoint.com/sites/Design-topsecret"
site.SetWebUrl(&webUrl) 
dataSource.SetSite(site)
requestBody.SetDataSource(dataSource)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
noncustodialDataSources, err := graphClient.Security().Cases().EdiscoveryCases().ByEdiscoveryCaseId("ediscoveryCase-id").NoncustodialDataSources().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.models.security.EdiscoveryNoncustodialDataSource ediscoveryNoncustodialDataSource = new com.microsoft.graph.models.security.EdiscoveryNoncustodialDataSource();
com.microsoft.graph.models.security.SiteSource dataSource = new com.microsoft.graph.models.security.SiteSource();
dataSource.setOdataType("microsoft.graph.security.siteSource");
Site site = new Site();
site.setWebUrl("https://m365x809305.sharepoint.com/sites/Design-topsecret");
dataSource.setSite(site);
ediscoveryNoncustodialDataSource.setDataSource(dataSource);
com.microsoft.graph.models.security.EdiscoveryNoncustodialDataSource result = graphClient.security().cases().ediscoveryCases().byEdiscoveryCaseId("{ediscoveryCase-id}").noncustodialDataSources().post(ediscoveryNoncustodialDataSource);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const ediscoveryNoncustodialDataSource = {
    dataSource: {
        '@odata.type': 'microsoft.graph.security.siteSource',
        site: {
            webUrl: 'https://m365x809305.sharepoint.com/sites/Design-topsecret'
        }
    }
};

await client.api('/security/cases/ediscoveryCases/b0073e4e-4184-41c6-9eb7-8c8cc3e2288b/noncustodialDataSources')
	.post(ediscoveryNoncustodialDataSource);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\Security\EdiscoveryNoncustodialDataSource;
use Microsoft\Graph\Generated\Models\Security\SiteSource;
use Microsoft\Graph\Generated\Models\Site;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new EdiscoveryNoncustodialDataSource();
$dataSource = new SiteSource();
$dataSource->setOdataType('microsoft.graph.security.siteSource');
$dataSourceSite = new Site();
$dataSourceSite->setWebUrl('https://m365x809305.sharepoint.com/sites/Design-topsecret');
$dataSource->setSite($dataSourceSite);
$requestBody->setDataSource($dataSource);

$result = $graphServiceClient->security()->cases()->ediscoveryCases()->byEdiscoveryCaseId('ediscoveryCase-id')->noncustodialDataSources()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Security

$params = @{
	dataSource = @{
		"@odata.type" = "microsoft.graph.security.siteSource"
		site = @{
			webUrl = "https://m365x809305.sharepoint.com/sites/Design-topsecret"
		}
	}
}

New-MgSecurityCaseEdiscoveryCaseNoncustodialDataSource -EdiscoveryCaseId $ediscoveryCaseId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.security.ediscovery_noncustodial_data_source import EdiscoveryNoncustodialDataSource
from msgraph.generated.models.security.site_source import SiteSource
from msgraph.generated.models.site import Site
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = EdiscoveryNoncustodialDataSource(
	data_source = SiteSource(
		odata_type = "microsoft.graph.security.siteSource",
		site = Site(
			web_url = "https://m365x809305.sharepoint.com/sites/Design-topsecret",
		),
	),
)

result = await graph_client.security.cases.ediscovery_cases.by_ediscovery_case_id('ediscoveryCase-id').noncustodial_data_sources.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

Here's an example of the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-Type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#security/cases/ediscoveryCases('b0073e4e-4184-41c6-9eb7-8c8cc3e2288b')/noncustodialDataSources/$entity",
    "status": "active",
    "holdStatus": "notApplied",
    "createdDateTime": "2022-05-23T03:15:08.5354451Z",
    "lastModifiedDateTime": "2022-05-23T03:15:08.5354451Z",
    "releasedDateTime": "0001-01-01T00:00:00Z",
    "id": "43373338343345303943344434423032",
    "displayName": "Design - top secret"
}
```
