<!-- Source: https://learn.microsoft.com/en-us/graph/api/security-ediscoverycase-list-noncustodialdatasources?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-02-26 -->

# List ediscoveryNoncustodialDataSources

Namespace: microsoft.graph.security

Get a list of the [non-custodial data sources](https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoverynoncustodialdatasource?view=graph-rest-1.0) and their properties.

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

- **eDiscovery Manager**. Allows members to view and access eDiscovery cases they create, including searching and accessing case data. However, eDiscovery Managers can only access and manage the cases they create. **This is the least privileged option for managing their own cases**.
- **eDiscovery Administrator**. Provides all the permissions of eDiscovery Manager, plus the ability to view and access all eDiscovery cases in the organization.

Additional roles that provide read access to eDiscovery cases:

- **Compliance Administrator**. Includes Case Management and Compliance Search permissions.
- **Organization Management**. Includes Case Management and Compliance Search permissions.
- **Reviewer**. Provides read-only access to review sets within eDiscovery cases where the user is a member.

The eDiscovery Manager and eDiscovery Administrator roles are part of the Microsoft Purview role groups and provide access to eDiscovery features through [role-based access control \(RBAC\)](https://learn.microsoft.com/en-us/purview/edisc-permissions#rbac-roles-related-to-ediscovery).

For more information about eDiscovery permissions and roles, see [Assign permissions in eDiscovery](https://learn.microsoft.com/en-us/purview/edisc-permissions).

## HTTP request

```http
POST /security/cases/ediscoveryCases/{ediscoveryCaseId}/noncustodialDataSources
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and a collection of [microsoft.graph.security.ediscoveryNoncustodialDataSource](https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoverynoncustodialdatasource?view=graph-rest-1.0) objects in the response body.

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

```msgraph
GET https://graph.microsoft.com/v1.0/security/cases/ediscoveryCases/b0073e4e-4184-41c6-9eb7-8c8cc3e2288b/noncustodialdatasources?$expand=dataSource
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Security.Cases.EdiscoveryCases["{ediscoveryCase-id}"].NoncustodialDataSources.GetAsync((requestConfiguration) =>
{
	requestConfiguration.QueryParameters.Expand = new string []{ "dataSource" };
});
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphsecurity "github.com/microsoftgraph/msgraph-sdk-go/security"
	  //other-imports
)

requestParameters := &graphsecurity.CasesEdiscoveryCasesItemNoncustodialDataSourcesRequestBuilderGetQueryParameters{
	Expand: [] string {"dataSource"},
}
configuration := &graphsecurity.CasesEdiscoveryCasesItemNoncustodialDataSourcesRequestBuilderGetRequestConfiguration{
	QueryParameters: requestParameters,
}

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
noncustodialDataSources, err := graphClient.Security().Cases().EdiscoveryCases().ByEdiscoveryCaseId("ediscoveryCase-id").NoncustodialDataSources().Get(context.Background(), configuration)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.models.security.EdiscoveryNoncustodialDataSourceCollectionResponse result = graphClient.security().cases().ediscoveryCases().byEdiscoveryCaseId("{ediscoveryCase-id}").noncustodialDataSources().get(requestConfiguration -> {
	requestConfiguration.queryParameters.expand = new String []{"dataSource"};
});
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let noncustodialDataSources = await client.api('/security/cases/ediscoveryCases/b0073e4e-4184-41c6-9eb7-8c8cc3e2288b/noncustodialdatasources')
	.expand('dataSource')
	.get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Security\Cases\EdiscoveryCases\Item\NoncustodialDataSources\NoncustodialDataSourcesRequestBuilderGetRequestConfiguration;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestConfiguration = new NoncustodialDataSourcesRequestBuilderGetRequestConfiguration();
$queryParameters = NoncustodialDataSourcesRequestBuilderGetRequestConfiguration::createQueryParameters();
$queryParameters->expand = ["dataSource"];
$requestConfiguration->queryParameters = $queryParameters;


$result = $graphServiceClient->security()->cases()->ediscoveryCases()->byEdiscoveryCaseId('ediscoveryCase-id')->noncustodialDataSources()->get($requestConfiguration)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Security

Get-MgSecurityCaseEdiscoveryCaseNoncustodialDataSource -EdiscoveryCaseId $ediscoveryCaseId -ExpandProperty "dataSource" 
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.security.cases.ediscovery_cases.item.noncustodial_data_sources.noncustodial_data_sources_request_builder import NoncustodialDataSourcesRequestBuilder
from kiota_abstractions.base_request_configuration import RequestConfiguration
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
query_params = NoncustodialDataSourcesRequestBuilder.NoncustodialDataSourcesRequestBuilderGetQueryParameters(
		expand = ["dataSource"],
)

request_configuration = RequestConfiguration(
query_parameters = query_params,
)

result = await graph_client.security.cases.ediscovery_cases.by_ediscovery_case_id('ediscoveryCase-id').noncustodial_data_sources.get(request_configuration = request_configuration)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

Here's an example of the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#security/cases/ediscoveryCases('b0073e4e-4184-41c6-9eb7-8c8cc3e2288b')/noncustodialDataSources(dataSource())",
    "@odata.count": 3,
    "value": [
        {
            "status": "active",
            "holdStatus": "applied",
            "createdDateTime": "2022-05-23T02:09:11.1395287Z",
            "lastModifiedDateTime": "2022-05-23T02:09:11.1395287Z",
            "releasedDateTime": "0001-01-01T00:00:00Z",
            "id": "35393639323133394345384344303043",
            "displayName": "U.S. Sales",
            "dataSource@odata.context": "https://graph.microsoft.com/v1.0/$metadata#security/cases/ediscoveryCases('b0073e4e-4184-41c6-9eb7-8c8cc3e2288b')/noncustodialDataSources('35393639323133394345384344303043')/dataSource/$entity",
            "dataSource": {
                "@odata.type": "#microsoft.graph.security.siteSource",
                "@odata.id": "https://graph.microsoft.com/v1.0/sites/169718e3-a8df-449d-bef4-ee09fe1ddc5d",
                "displayName": "U.S. Sales",
                "createdDateTime": "2022-05-23T02:09:11.1395535Z",
                "holdStatus": "0",
                "id": "169718e3-a8df-449d-bef4-ee09fe1ddc5d",
                "createdBy": {
                    "application": null,
                    "user": {
                        "id": "c25c3914-f9f7-43ee-9cba-a25377e0cec6",
                        "displayName": null
                    }
                },
                "site": {
                    "webUrl": "https://m365x809305.sharepoint.com/sites/USSales",
                    "id": "169718e3-a8df-449d-bef4-ee09fe1ddc5d",
                    "createdDateTime": "2022-05-23T02:09:11.1395535Z"
                }
            }
        },
        {
            "status": "active",
            "holdStatus": "applied",
            "createdDateTime": "2022-05-23T02:09:11.1395287Z",
            "lastModifiedDateTime": "2022-05-23T02:09:11.1395287Z",
            "releasedDateTime": "0001-01-01T00:00:00Z",
            "id": "31453237353743363432414242344641",
            "displayName": "Sales and Marketing",
            "dataSource@odata.context": "https://graph.microsoft.com/v1.0/$metadata#security/cases/ediscoveryCases('b0073e4e-4184-41c6-9eb7-8c8cc3e2288b')/noncustodialDataSources('31453237353743363432414242344641')/dataSource/$entity",
            "dataSource": {
                "@odata.type": "#microsoft.graph.security.siteSource",
                "@odata.id": "https://graph.microsoft.com/v1.0/sites/74f6c798-fc32-4dbe-9e5b-8e11459b9f44",
                "displayName": "Sales and Marketing",
                "createdDateTime": "2022-05-23T02:09:11.1397925Z",
                "holdStatus": "0",
                "id": "74f6c798-fc32-4dbe-9e5b-8e11459b9f44",
                "createdBy": {
                    "application": null,
                    "user": {
                        "id": "c25c3914-f9f7-43ee-9cba-a25377e0cec6",
                        "displayName": null
                    }
                },
                "site": {
                    "webUrl": "https://m365x809305.sharepoint.com/sites/SalesAndMarketing",
                    "id": "74f6c798-fc32-4dbe-9e5b-8e11459b9f44",
                    "createdDateTime": "2022-05-23T02:09:11.1397925Z"
                }
            }
        },
        {
            "status": "active",
            "holdStatus": "applied",
            "createdDateTime": "2022-05-23T02:09:11.1395287Z",
            "lastModifiedDateTime": "2022-05-23T02:09:11.1395287Z",
            "releasedDateTime": "0001-01-01T00:00:00Z",
            "id": "46333131344239353834433430454335",
            "displayName": "Retail",
            "dataSource@odata.context": "https://graph.microsoft.com/v1.0/$metadata#security/cases/ediscoveryCases('b0073e4e-4184-41c6-9eb7-8c8cc3e2288b')/noncustodialDataSources('46333131344239353834433430454335')/dataSource/$entity",
            "dataSource": {
                "@odata.type": "#microsoft.graph.security.siteSource",
                "@odata.id": "https://graph.microsoft.com/v1.0/sites/dbe4b18e-2765-4989-8647-48139180c45f",
                "displayName": "Retail",
                "createdDateTime": "2022-05-23T02:09:11.1399861Z",
                "holdStatus": "0",
                "id": "dbe4b18e-2765-4989-8647-48139180c45f",
                "createdBy": {
                    "application": null,
                    "user": {
                        "id": "c25c3914-f9f7-43ee-9cba-a25377e0cec6",
                        "displayName": null
                    }
                },
                "site": {
                    "webUrl": "https://m365x809305.sharepoint.com/sites/Retail",
                    "id": "dbe4b18e-2765-4989-8647-48139180c45f",
                    "createdDateTime": "2022-05-23T02:09:11.1399861Z"
                }
            }
        }
    ]
}
```
