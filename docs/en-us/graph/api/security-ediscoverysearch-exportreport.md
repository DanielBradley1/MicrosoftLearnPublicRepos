<!-- Source: https://learn.microsoft.com/en-us/graph/api/security-ediscoverysearch-exportreport?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-02-26 -->

# ediscoverySearch: exportReport

Namespace: microsoft.graph.security

Export an item report from an estimated [ediscoverySearch](https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoverysearch?view=graph-rest-1.0). For details, see [Manage a collection estimate](https://learn.microsoft.com/en-us/purview/ediscovery-create-draft-collection#manage-a-collection-estimate).

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
POST /security/cases/ediscoveryCases/{ediscoveryCaseId}/searches/{ediscoverySearchId}/exportReport
POST /security/cases/ediscoveryCases('{ediscoveryCaseId}')/searches('{ediscoverySearchId}')/exportReport
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the parameters.

The following table lists the parameters that you can use with this action.

| Parameter | Type | Description |
| :--- | :--- | :--- |
| additionalOptions | [microsoft.graph.security.additionalOptions](https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoverysearchexportoperation?view=graph-rest-1.0#additionaloptions-values) | The additional options for the export. Supports a subset of the values for **additionalOptions**. The possible values are: `none`, `teamsAndYammerConversations`, `cloudAttachments`, `allDocumentVersions`, `subfolderContents`, `listAttachments`, `unknownFutureValue`, `htmlTranscripts`, `advancedIndexing`, `allItemsInFolder`. Use the `Prefer: include-unknown-enum-members` request header to get the following values from this [evolvable enum](https://learn.microsoft.com/en-us/graph/best-practices-concept#handling-future-members-in-evolvable-enumerations): `htmlTranscripts`, `advancedIndexing`, `allItemsInFolder`. The `advancedIndexing` value is only available if **exportCriteria** includes `partiallyIndexed`. Required. |
| cloudAttachmentVersion | microsoft.graph.security.cloudAttachmentVersion | The versions of cloud attachments to include in messages. The possible values are: `latest`, `recent10`, `recent100`, `all`, `unknownFutureValue`. The default value is `latest`. |
| description | String | The description of the export report. |
| documentVersion | microsoft.graph.security.documentVersion | The versions of files in SharePoint to include. The possible values are: `latest`, `recent10`, `recent100`, `all`, `unknownFutureValue`. The default value is `latest`. |
| displayName | String | The display name of the export report. |
| exportCriteria | [microsoft.graph.security.exportCriteria](https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoverysearchexportoperation?view=graph-rest-1.0#exportcriteria-values) | Bitwise options that specify the portion of the estimate report to export. The possible values are: `searchHits`, `partiallyIndexed`, `unknownFutureValue`. Required. |
| exportLocation | [microsoft.graph.security.exportLocation](https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoverysearchexportoperation?view=graph-rest-1.0#exportlocation-values) | Bitwise options that specify the location scope for partially indexed items. You can choose to include partially indexed items only in responsive locations with search hits or in all targeted locations. The possible values are: `responsiveLocations`, `nonresponsiveLocations`, `unknownFutureValue`. The `nonresponsiveLocations` value is only available if **exportCriteria** includes `partiallyIndexed`. |

## Response

If the export has started successfully, this action returns a `202 Accepted` response code. The response also contains a `Location` header that includes the location of the [microsoft.graph.security.ediscoverySearchExportOperation](https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoverysearchexportoperation?view=graph-rest-1.0) that was created to handle the export. To check the status of the export operation, make a GET request to the location URL.

## Examples

### Example 1: Export a report of items with search hits only, excluding partially indexed items, without additional options

The following example shows how to export a report of items with search hits only, excluding partially indexed items, with no additional options selected.

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
POST https://graph.microsoft.com/v1.0/security/cases/ediscoveryCases/dbc06feb-a6a5-46a2-8e4e-534353b071e4/searches/6c2ab774-2d2a-46b9-a601-3130f518757b/exportReport
Content-Type: application/json

{
  "displayName": "Export 1",
  "exportCriteria": "searchHits",
  "additionalOptions": "none"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Security.Cases.EdiscoveryCases.Item.Searches.Item.MicrosoftGraphSecurityExportReport;
using Microsoft.Graph.Models.Security;

var requestBody = new ExportReportPostRequestBody
{
	DisplayName = "Export 1",
	ExportCriteria = ExportCriteria.SearchHits,
	AdditionalOptions = AdditionalOptions.None,
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
await graphClient.Security.Cases.EdiscoveryCases["{ediscoveryCase-id}"].Searches["{ediscoverySearch-id}"].MicrosoftGraphSecurityExportReport.PostAsync(requestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphsecurity "github.com/microsoftgraph/msgraph-sdk-go/security"
	  graphmodelssecurity "github.com/microsoftgraph/msgraph-sdk-go/models/security"
	  //other-imports
)

requestBody := graphsecurity.NewExportReportPostRequestBody()
displayName := "Export 1"
requestBody.SetDisplayName(&displayName) 
exportCriteria := graphmodels.SEARCHHITS_EXPORTCRITERIA 
requestBody.SetExportCriteria(&exportCriteria) 
additionalOptions := graphmodels.NONE_ADDITIONALOPTIONS 
requestBody.SetAdditionalOptions(&additionalOptions) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
graphClient.Security().Cases().EdiscoveryCases().ByEdiscoveryCaseId("ediscoveryCase-id").Searches().ByEdiscoverySearchId("ediscoverySearch-id").MicrosoftGraphSecurityExportReport().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.security.cases.ediscoverycases.item.searches.item.microsoftgraphsecurityexportreport.ExportReportPostRequestBody exportReportPostRequestBody = new com.microsoft.graph.security.cases.ediscoverycases.item.searches.item.microsoftgraphsecurityexportreport.ExportReportPostRequestBody();
exportReportPostRequestBody.setDisplayName("Export 1");
exportReportPostRequestBody.setExportCriteria(EnumSet.of(com.microsoft.graph.models.security.ExportCriteria.SearchHits));
exportReportPostRequestBody.setAdditionalOptions(EnumSet.of(com.microsoft.graph.models.security.AdditionalOptions.None));
graphClient.security().cases().ediscoveryCases().byEdiscoveryCaseId("{ediscoveryCase-id}").searches().byEdiscoverySearchId("{ediscoverySearch-id}").microsoftGraphSecurityExportReport().post(exportReportPostRequestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const exportReport = {
  displayName: 'Export 1',
  exportCriteria: 'searchHits',
  additionalOptions: 'none'
};

await client.api('/security/cases/ediscoveryCases/dbc06feb-a6a5-46a2-8e4e-534353b071e4/searches/6c2ab774-2d2a-46b9-a601-3130f518757b/exportReport')
	.post(exportReport);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Security\Cases\EdiscoveryCases\Item\Searches\Item\MicrosoftGraphSecurityExportReport\ExportReportPostRequestBody;
use Microsoft\Graph\Generated\Models\Security\ExportCriteria;
use Microsoft\Graph\Generated\Models\Security\AdditionalOptions;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new ExportReportPostRequestBody();
$requestBody->setDisplayName('Export 1');
$requestBody->setExportCriteria(new ExportCriteria('searchHits'));
$requestBody->setAdditionalOptions(new AdditionalOptions('none'));

$graphServiceClient->security()->cases()->ediscoveryCases()->byEdiscoveryCaseId('ediscoveryCase-id')->searches()->byEdiscoverySearchId('ediscoverySearch-id')->microsoftGraphSecurityExportReport()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Security

$params = @{
	displayName = "Export 1"
	exportCriteria = "searchHits"
	additionalOptions = "none"
}

Export-MgSecurityCaseEdiscoveryCaseSearchReport -EdiscoveryCaseId $ediscoveryCaseId -EdiscoverySearchId $ediscoverySearchId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.security.cases.ediscoverycases.item.searches.item.microsoft_graph_security_export_report.export_report_post_request_body import ExportReportPostRequestBody
from msgraph.generated.models.export_criteria import ExportCriteria
from msgraph.generated.models.additional_options import AdditionalOptions
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = ExportReportPostRequestBody(
	display_name = "Export 1",
	export_criteria = ExportCriteria.SearchHits,
	additional_options = AdditionalOptions.None,
)

await graph_client.security.cases.ediscovery_cases.by_ediscovery_case_id('ediscoveryCase-id').searches.by_ediscovery_search_id('ediscoverySearch-id').microsoft_graph_security_export_report.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

```http
HTTP/1.1 202 Accepted
Content-Length: 0
Location: https://graph.microsoft.com/v1.0/security/cases/ediscoverycases('dbc06feb-a6a5-46a2-8e4e-534353b071e4')/operations('f57fc79d-bea8-42ac-b0be-217302d5683c')
```

### Example 2: Export a report of items with search hits and partially indexed items in all targeted locations, without additional options

The following example shows how to export a report of items with search hits and partially indexed items in all targeted locations, with no additional options selected.

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
POST https://graph.microsoft.com/v1.0/security/cases/ediscoveryCases/dbc06feb-a6a5-46a2-8e4e-534353b071e4/searches/6c2ab774-2d2a-46b9-a601-3130f518757b/exportReport
Content-Type: application/json

{
  "displayName": "Export 2",
  "exportCriteria": "searchHits, partiallyIndexed",
  "exportLocation": "responsiveLocations, nonresponsiveLocations",
  "additionalOptions": "none"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Security.Cases.EdiscoveryCases.Item.Searches.Item.MicrosoftGraphSecurityExportReport;
using Microsoft.Graph.Models.Security;

var requestBody = new ExportReportPostRequestBody
{
	DisplayName = "Export 2",
	ExportCriteria = ExportCriteria.SearchHits | ExportCriteria.PartiallyIndexed,
	ExportLocation = ExportLocation.ResponsiveLocations | ExportLocation.NonresponsiveLocations,
	AdditionalOptions = AdditionalOptions.None,
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
await graphClient.Security.Cases.EdiscoveryCases["{ediscoveryCase-id}"].Searches["{ediscoverySearch-id}"].MicrosoftGraphSecurityExportReport.PostAsync(requestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphsecurity "github.com/microsoftgraph/msgraph-sdk-go/security"
	  graphmodelssecurity "github.com/microsoftgraph/msgraph-sdk-go/models/security"
	  //other-imports
)

requestBody := graphsecurity.NewExportReportPostRequestBody()
displayName := "Export 2"
requestBody.SetDisplayName(&displayName) 
exportCriteria := graphmodels.SEARCHHITS, PARTIALLYINDEXED_EXPORTCRITERIA 
requestBody.SetExportCriteria(&exportCriteria) 
exportLocation := graphmodels.RESPONSIVELOCATIONS, NONRESPONSIVELOCATIONS_EXPORTLOCATION 
requestBody.SetExportLocation(&exportLocation) 
additionalOptions := graphmodels.NONE_ADDITIONALOPTIONS 
requestBody.SetAdditionalOptions(&additionalOptions) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
graphClient.Security().Cases().EdiscoveryCases().ByEdiscoveryCaseId("ediscoveryCase-id").Searches().ByEdiscoverySearchId("ediscoverySearch-id").MicrosoftGraphSecurityExportReport().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.security.cases.ediscoverycases.item.searches.item.microsoftgraphsecurityexportreport.ExportReportPostRequestBody exportReportPostRequestBody = new com.microsoft.graph.security.cases.ediscoverycases.item.searches.item.microsoftgraphsecurityexportreport.ExportReportPostRequestBody();
exportReportPostRequestBody.setDisplayName("Export 2");
exportReportPostRequestBody.setExportCriteria(EnumSet.of(com.microsoft.graph.models.security.ExportCriteria.SearchHits, com.microsoft.graph.models.security.ExportCriteria.PartiallyIndexed));
exportReportPostRequestBody.setExportLocation(EnumSet.of(com.microsoft.graph.models.security.ExportLocation.ResponsiveLocations, com.microsoft.graph.models.security.ExportLocation.NonresponsiveLocations));
exportReportPostRequestBody.setAdditionalOptions(EnumSet.of(com.microsoft.graph.models.security.AdditionalOptions.None));
graphClient.security().cases().ediscoveryCases().byEdiscoveryCaseId("{ediscoveryCase-id}").searches().byEdiscoverySearchId("{ediscoverySearch-id}").microsoftGraphSecurityExportReport().post(exportReportPostRequestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const exportReport = {
  displayName: 'Export 2',
  exportCriteria: 'searchHits, partiallyIndexed',
  exportLocation: 'responsiveLocations, nonresponsiveLocations',
  additionalOptions: 'none'
};

await client.api('/security/cases/ediscoveryCases/dbc06feb-a6a5-46a2-8e4e-534353b071e4/searches/6c2ab774-2d2a-46b9-a601-3130f518757b/exportReport')
	.post(exportReport);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Security\Cases\EdiscoveryCases\Item\Searches\Item\MicrosoftGraphSecurityExportReport\ExportReportPostRequestBody;
use Microsoft\Graph\Generated\Models\Security\ExportCriteria;
use Microsoft\Graph\Generated\Models\Security\ExportLocation;
use Microsoft\Graph\Generated\Models\Security\AdditionalOptions;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new ExportReportPostRequestBody();
$requestBody->setDisplayName('Export 2');
$requestBody->setExportCriteria(new ExportCriteria('searchHits, partiallyIndexed'));
$requestBody->setExportLocation(new ExportLocation('responsiveLocations, nonresponsiveLocations'));
$requestBody->setAdditionalOptions(new AdditionalOptions('none'));

$graphServiceClient->security()->cases()->ediscoveryCases()->byEdiscoveryCaseId('ediscoveryCase-id')->searches()->byEdiscoverySearchId('ediscoverySearch-id')->microsoftGraphSecurityExportReport()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Security

$params = @{
	displayName = "Export 2"
	exportCriteria = "searchHits, partiallyIndexed"
	exportLocation = "responsiveLocations, nonresponsiveLocations"
	additionalOptions = "none"
}

Export-MgSecurityCaseEdiscoveryCaseSearchReport -EdiscoveryCaseId $ediscoveryCaseId -EdiscoverySearchId $ediscoverySearchId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.security.cases.ediscoverycases.item.searches.item.microsoft_graph_security_export_report.export_report_post_request_body import ExportReportPostRequestBody
from msgraph.generated.models.export_criteria import ExportCriteria
from msgraph.generated.models.export_location import ExportLocation
from msgraph.generated.models.additional_options import AdditionalOptions
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = ExportReportPostRequestBody(
	display_name = "Export 2",
	export_criteria = ExportCriteria.SearchHits | ExportCriteria.PartiallyIndexed,
	export_location = ExportLocation.ResponsiveLocations | ExportLocation.NonresponsiveLocations,
	additional_options = AdditionalOptions.None,
)

await graph_client.security.cases.ediscovery_cases.by_ediscovery_case_id('ediscoveryCase-id').searches.by_ediscovery_search_id('ediscoverySearch-id').microsoft_graph_security_export_report.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

```http
HTTP/1.1 202 Accepted
Content-Length: 0
Location: https://graph.microsoft.com/v1.0/security/cases/ediscoverycases('dbc06feb-a6a5-46a2-8e4e-534353b071e4')/operations('cbcb4807-e76e-4ef0-bd5b-e2177c13f07e')
```

### Example 3: Export a report of items with search hits and partially indexed items in locations with search hits, without additional options

The following example shows how to export a report of items with search hits and partially indexed items in locations with search hits, with no additional options selected.

#### Request

The following example shows a request.

- [HTTP](#tabpanel_3_http)
- [C#](#tabpanel_3_csharp)
- [Go](#tabpanel_3_go)
- [Java](#tabpanel_3_java)
- [JavaScript](#tabpanel_3_javascript)
- [PHP](#tabpanel_3_php)
- [PowerShell](#tabpanel_3_powershell)
- [Python](#tabpanel_3_python)

```http
POST https://graph.microsoft.com/v1.0/security/cases/ediscoveryCases/dbc06feb-a6a5-46a2-8e4e-534353b071e4/searches/6c2ab774-2d2a-46b9-a601-3130f518757b/exportReport
Content-Type: application/json

{
  "displayName": "Export 3",
  "exportCriteria": "searchHits, partiallyIndexed",
  "exportLocation": "responsiveLocations",
  "additionalOptions": "none"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Security.Cases.EdiscoveryCases.Item.Searches.Item.MicrosoftGraphSecurityExportReport;
using Microsoft.Graph.Models.Security;

var requestBody = new ExportReportPostRequestBody
{
	DisplayName = "Export 3",
	ExportCriteria = ExportCriteria.SearchHits | ExportCriteria.PartiallyIndexed,
	ExportLocation = ExportLocation.ResponsiveLocations,
	AdditionalOptions = AdditionalOptions.None,
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
await graphClient.Security.Cases.EdiscoveryCases["{ediscoveryCase-id}"].Searches["{ediscoverySearch-id}"].MicrosoftGraphSecurityExportReport.PostAsync(requestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphsecurity "github.com/microsoftgraph/msgraph-sdk-go/security"
	  graphmodelssecurity "github.com/microsoftgraph/msgraph-sdk-go/models/security"
	  //other-imports
)

requestBody := graphsecurity.NewExportReportPostRequestBody()
displayName := "Export 3"
requestBody.SetDisplayName(&displayName) 
exportCriteria := graphmodels.SEARCHHITS, PARTIALLYINDEXED_EXPORTCRITERIA 
requestBody.SetExportCriteria(&exportCriteria) 
exportLocation := graphmodels.RESPONSIVELOCATIONS_EXPORTLOCATION 
requestBody.SetExportLocation(&exportLocation) 
additionalOptions := graphmodels.NONE_ADDITIONALOPTIONS 
requestBody.SetAdditionalOptions(&additionalOptions) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
graphClient.Security().Cases().EdiscoveryCases().ByEdiscoveryCaseId("ediscoveryCase-id").Searches().ByEdiscoverySearchId("ediscoverySearch-id").MicrosoftGraphSecurityExportReport().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.security.cases.ediscoverycases.item.searches.item.microsoftgraphsecurityexportreport.ExportReportPostRequestBody exportReportPostRequestBody = new com.microsoft.graph.security.cases.ediscoverycases.item.searches.item.microsoftgraphsecurityexportreport.ExportReportPostRequestBody();
exportReportPostRequestBody.setDisplayName("Export 3");
exportReportPostRequestBody.setExportCriteria(EnumSet.of(com.microsoft.graph.models.security.ExportCriteria.SearchHits, com.microsoft.graph.models.security.ExportCriteria.PartiallyIndexed));
exportReportPostRequestBody.setExportLocation(EnumSet.of(com.microsoft.graph.models.security.ExportLocation.ResponsiveLocations));
exportReportPostRequestBody.setAdditionalOptions(EnumSet.of(com.microsoft.graph.models.security.AdditionalOptions.None));
graphClient.security().cases().ediscoveryCases().byEdiscoveryCaseId("{ediscoveryCase-id}").searches().byEdiscoverySearchId("{ediscoverySearch-id}").microsoftGraphSecurityExportReport().post(exportReportPostRequestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const exportReport = {
  displayName: 'Export 3',
  exportCriteria: 'searchHits, partiallyIndexed',
  exportLocation: 'responsiveLocations',
  additionalOptions: 'none'
};

await client.api('/security/cases/ediscoveryCases/dbc06feb-a6a5-46a2-8e4e-534353b071e4/searches/6c2ab774-2d2a-46b9-a601-3130f518757b/exportReport')
	.post(exportReport);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Security\Cases\EdiscoveryCases\Item\Searches\Item\MicrosoftGraphSecurityExportReport\ExportReportPostRequestBody;
use Microsoft\Graph\Generated\Models\Security\ExportCriteria;
use Microsoft\Graph\Generated\Models\Security\ExportLocation;
use Microsoft\Graph\Generated\Models\Security\AdditionalOptions;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new ExportReportPostRequestBody();
$requestBody->setDisplayName('Export 3');
$requestBody->setExportCriteria(new ExportCriteria('searchHits, partiallyIndexed'));
$requestBody->setExportLocation(new ExportLocation('responsiveLocations'));
$requestBody->setAdditionalOptions(new AdditionalOptions('none'));

$graphServiceClient->security()->cases()->ediscoveryCases()->byEdiscoveryCaseId('ediscoveryCase-id')->searches()->byEdiscoverySearchId('ediscoverySearch-id')->microsoftGraphSecurityExportReport()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Security

$params = @{
	displayName = "Export 3"
	exportCriteria = "searchHits, partiallyIndexed"
	exportLocation = "responsiveLocations"
	additionalOptions = "none"
}

Export-MgSecurityCaseEdiscoveryCaseSearchReport -EdiscoveryCaseId $ediscoveryCaseId -EdiscoverySearchId $ediscoverySearchId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.security.cases.ediscoverycases.item.searches.item.microsoft_graph_security_export_report.export_report_post_request_body import ExportReportPostRequestBody
from msgraph.generated.models.export_criteria import ExportCriteria
from msgraph.generated.models.export_location import ExportLocation
from msgraph.generated.models.additional_options import AdditionalOptions
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = ExportReportPostRequestBody(
	display_name = "Export 3",
	export_criteria = ExportCriteria.SearchHits | ExportCriteria.PartiallyIndexed,
	export_location = ExportLocation.ResponsiveLocations,
	additional_options = AdditionalOptions.None,
)

await graph_client.security.cases.ediscovery_cases.by_ediscovery_case_id('ediscoveryCase-id').searches.by_ediscovery_search_id('ediscoverySearch-id').microsoft_graph_security_export_report.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

```http
HTTP/1.1 202 Accepted
Content-Length: 0
Location: https://graph.microsoft.com/v1.0/security/cases/ediscoverycases('dbc06feb-a6a5-46a2-8e4e-534353b071e4')/operations('c56f66de-b780-4efc-aa0c-4ef3271ad6b4')
```

### Example 4: Export a report of partially indexed items in all targeted locations with all additional options selected

The following example shows how to export a report of partially indexed items in all targeted locations with all additional options selected.

#### Request

The following example shows a request.

- [HTTP](#tabpanel_4_http)
- [C#](#tabpanel_4_csharp)
- [Go](#tabpanel_4_go)
- [Java](#tabpanel_4_java)
- [JavaScript](#tabpanel_4_javascript)
- [PHP](#tabpanel_4_php)
- [PowerShell](#tabpanel_4_powershell)
- [Python](#tabpanel_4_python)

```http
POST https://graph.microsoft.com/v1.0/security/cases/ediscoveryCases/dbc06feb-a6a5-46a2-8e4e-534353b071e4/searches/6c2ab774-2d2a-46b9-a601-3130f518757b/exportReport
Content-Type: application/json

{
  "displayName": "Export 4",
  "exportCriteria": "partiallyIndexed",
  "exportLocation": "responsiveLocations, nonresponsiveLocations",
  "additionalOptions": "advancedIndexing, subfolderContents, allItemsInFolder, listAttachments, teamsAndYammerConversations, htmlTranscripts, cloudAttachments"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Security.Cases.EdiscoveryCases.Item.Searches.Item.MicrosoftGraphSecurityExportReport;
using Microsoft.Graph.Models.Security;

var requestBody = new ExportReportPostRequestBody
{
	DisplayName = "Export 4",
	ExportCriteria = ExportCriteria.PartiallyIndexed,
	ExportLocation = ExportLocation.ResponsiveLocations | ExportLocation.NonresponsiveLocations,
	AdditionalOptions = AdditionalOptions.AdvancedIndexing | AdditionalOptions.SubfolderContents | AdditionalOptions.AllItemsInFolder | AdditionalOptions.ListAttachments | AdditionalOptions.TeamsAndYammerConversations | AdditionalOptions.HtmlTranscripts | AdditionalOptions.CloudAttachments,
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
await graphClient.Security.Cases.EdiscoveryCases["{ediscoveryCase-id}"].Searches["{ediscoverySearch-id}"].MicrosoftGraphSecurityExportReport.PostAsync(requestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphsecurity "github.com/microsoftgraph/msgraph-sdk-go/security"
	  graphmodelssecurity "github.com/microsoftgraph/msgraph-sdk-go/models/security"
	  //other-imports
)

requestBody := graphsecurity.NewExportReportPostRequestBody()
displayName := "Export 4"
requestBody.SetDisplayName(&displayName) 
exportCriteria := graphmodels.PARTIALLYINDEXED_EXPORTCRITERIA 
requestBody.SetExportCriteria(&exportCriteria) 
exportLocation := graphmodels.RESPONSIVELOCATIONS, NONRESPONSIVELOCATIONS_EXPORTLOCATION 
requestBody.SetExportLocation(&exportLocation) 
additionalOptions := graphmodels.ADVANCEDINDEXING, SUBFOLDERCONTENTS, ALLITEMSINFOLDER, LISTATTACHMENTS, TEAMSANDYAMMERCONVERSATIONS, HTMLTRANSCRIPTS, CLOUDATTACHMENTS_ADDITIONALOPTIONS 
requestBody.SetAdditionalOptions(&additionalOptions) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
graphClient.Security().Cases().EdiscoveryCases().ByEdiscoveryCaseId("ediscoveryCase-id").Searches().ByEdiscoverySearchId("ediscoverySearch-id").MicrosoftGraphSecurityExportReport().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.security.cases.ediscoverycases.item.searches.item.microsoftgraphsecurityexportreport.ExportReportPostRequestBody exportReportPostRequestBody = new com.microsoft.graph.security.cases.ediscoverycases.item.searches.item.microsoftgraphsecurityexportreport.ExportReportPostRequestBody();
exportReportPostRequestBody.setDisplayName("Export 4");
exportReportPostRequestBody.setExportCriteria(EnumSet.of(com.microsoft.graph.models.security.ExportCriteria.PartiallyIndexed));
exportReportPostRequestBody.setExportLocation(EnumSet.of(com.microsoft.graph.models.security.ExportLocation.ResponsiveLocations, com.microsoft.graph.models.security.ExportLocation.NonresponsiveLocations));
exportReportPostRequestBody.setAdditionalOptions(EnumSet.of(com.microsoft.graph.models.security.AdditionalOptions.AdvancedIndexing, com.microsoft.graph.models.security.AdditionalOptions.SubfolderContents, com.microsoft.graph.models.security.AdditionalOptions.AllItemsInFolder, com.microsoft.graph.models.security.AdditionalOptions.ListAttachments, com.microsoft.graph.models.security.AdditionalOptions.TeamsAndYammerConversations, com.microsoft.graph.models.security.AdditionalOptions.HtmlTranscripts, com.microsoft.graph.models.security.AdditionalOptions.CloudAttachments));
graphClient.security().cases().ediscoveryCases().byEdiscoveryCaseId("{ediscoveryCase-id}").searches().byEdiscoverySearchId("{ediscoverySearch-id}").microsoftGraphSecurityExportReport().post(exportReportPostRequestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const exportReport = {
  displayName: 'Export 4',
  exportCriteria: 'partiallyIndexed',
  exportLocation: 'responsiveLocations, nonresponsiveLocations',
  additionalOptions: 'advancedIndexing, subfolderContents, allItemsInFolder, listAttachments, teamsAndYammerConversations, htmlTranscripts, cloudAttachments'
};

await client.api('/security/cases/ediscoveryCases/dbc06feb-a6a5-46a2-8e4e-534353b071e4/searches/6c2ab774-2d2a-46b9-a601-3130f518757b/exportReport')
	.post(exportReport);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Security\Cases\EdiscoveryCases\Item\Searches\Item\MicrosoftGraphSecurityExportReport\ExportReportPostRequestBody;
use Microsoft\Graph\Generated\Models\Security\ExportCriteria;
use Microsoft\Graph\Generated\Models\Security\ExportLocation;
use Microsoft\Graph\Generated\Models\Security\AdditionalOptions;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new ExportReportPostRequestBody();
$requestBody->setDisplayName('Export 4');
$requestBody->setExportCriteria(new ExportCriteria('partiallyIndexed'));
$requestBody->setExportLocation(new ExportLocation('responsiveLocations, nonresponsiveLocations'));
$requestBody->setAdditionalOptions(new AdditionalOptions('advancedIndexing, subfolderContents, allItemsInFolder, listAttachments, teamsAndYammerConversations, htmlTranscripts, cloudAttachments'));

$graphServiceClient->security()->cases()->ediscoveryCases()->byEdiscoveryCaseId('ediscoveryCase-id')->searches()->byEdiscoverySearchId('ediscoverySearch-id')->microsoftGraphSecurityExportReport()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Security

$params = @{
	displayName = "Export 4"
	exportCriteria = "partiallyIndexed"
	exportLocation = "responsiveLocations, nonresponsiveLocations"
	additionalOptions = "advancedIndexing, subfolderContents, allItemsInFolder, listAttachments, teamsAndYammerConversations, htmlTranscripts, cloudAttachments"
}

Export-MgSecurityCaseEdiscoveryCaseSearchReport -EdiscoveryCaseId $ediscoveryCaseId -EdiscoverySearchId $ediscoverySearchId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.security.cases.ediscoverycases.item.searches.item.microsoft_graph_security_export_report.export_report_post_request_body import ExportReportPostRequestBody
from msgraph.generated.models.export_criteria import ExportCriteria
from msgraph.generated.models.export_location import ExportLocation
from msgraph.generated.models.additional_options import AdditionalOptions
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = ExportReportPostRequestBody(
	display_name = "Export 4",
	export_criteria = ExportCriteria.PartiallyIndexed,
	export_location = ExportLocation.ResponsiveLocations | ExportLocation.NonresponsiveLocations,
	additional_options = AdditionalOptions.AdvancedIndexing | AdditionalOptions.SubfolderContents | AdditionalOptions.AllItemsInFolder | AdditionalOptions.ListAttachments | AdditionalOptions.TeamsAndYammerConversations | AdditionalOptions.HtmlTranscripts | AdditionalOptions.CloudAttachments,
)

await graph_client.security.cases.ediscovery_cases.by_ediscovery_case_id('ediscoveryCase-id').searches.by_ediscovery_search_id('ediscoverySearch-id').microsoft_graph_security_export_report.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

```http
HTTP/1.1 202 Accepted
Content-Length: 0
Location: https://graph.microsoft.com/v1.0/security/cases/ediscoverycases('dbc06feb-a6a5-46a2-8e4e-534353b071e4')/operations('572d44e2-5e77-4443-a2ed-cd036bdc0304')
```

### Example 5: Export a report of partially indexed items in locations with search hits and cloud attachments

The following example shows how to export a report of partially indexed items in locations with search hits and cloud attachments, including the number of document and cloud attachment versions.

#### Request

The following example shows a request.

- [HTTP](#tabpanel_5_http)
- [C#](#tabpanel_5_csharp)
- [Go](#tabpanel_5_go)
- [Java](#tabpanel_5_java)
- [JavaScript](#tabpanel_5_javascript)
- [PHP](#tabpanel_5_php)
- [PowerShell](#tabpanel_5_powershell)
- [Python](#tabpanel_5_python)

```http
POST https://graph.microsoft.com/v1.0/security/cases/ediscoveryCases/dbc06feb-a6a5-46a2-8e4e-534353b071e4/searches/6c2ab774-2d2a-46b9-a601-3130f518757b/exportReport
Content-Type: application/json

{
  "displayName": "Export 5",
  "exportCriteria": "partiallyIndexed",
  "exportLocation": "responsiveLocations",
  "additionalOptions": "cloudAttachments",
  "cloudAttachmentVersion": "all",
  "doucmentVersion": "recent100"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Security.Cases.EdiscoveryCases.Item.Searches.Item.MicrosoftGraphSecurityExportReport;
using Microsoft.Graph.Models.Security;

var requestBody = new ExportReportPostRequestBody
{
	DisplayName = "Export 5",
	ExportCriteria = ExportCriteria.PartiallyIndexed,
	ExportLocation = ExportLocation.ResponsiveLocations,
	AdditionalOptions = AdditionalOptions.CloudAttachments,
	CloudAttachmentVersion = CloudAttachmentVersion.All,
	AdditionalData = new Dictionary<string, object>
	{
		{
			"doucmentVersion" , "recent100"
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
await graphClient.Security.Cases.EdiscoveryCases["{ediscoveryCase-id}"].Searches["{ediscoverySearch-id}"].MicrosoftGraphSecurityExportReport.PostAsync(requestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphsecurity "github.com/microsoftgraph/msgraph-sdk-go/security"
	  graphmodelssecurity "github.com/microsoftgraph/msgraph-sdk-go/models/security"
	  //other-imports
)

requestBody := graphsecurity.NewExportReportPostRequestBody()
displayName := "Export 5"
requestBody.SetDisplayName(&displayName) 
exportCriteria := graphmodels.PARTIALLYINDEXED_EXPORTCRITERIA 
requestBody.SetExportCriteria(&exportCriteria) 
exportLocation := graphmodels.RESPONSIVELOCATIONS_EXPORTLOCATION 
requestBody.SetExportLocation(&exportLocation) 
additionalOptions := graphmodels.CLOUDATTACHMENTS_ADDITIONALOPTIONS 
requestBody.SetAdditionalOptions(&additionalOptions) 
cloudAttachmentVersion := graphmodels.ALL_CLOUDATTACHMENTVERSION 
requestBody.SetCloudAttachmentVersion(&cloudAttachmentVersion) 
additionalData := map[string]interface{}{
	"doucmentVersion" : "recent100", 
}
requestBody.SetAdditionalData(additionalData)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
graphClient.Security().Cases().EdiscoveryCases().ByEdiscoveryCaseId("ediscoveryCase-id").Searches().ByEdiscoverySearchId("ediscoverySearch-id").MicrosoftGraphSecurityExportReport().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.security.cases.ediscoverycases.item.searches.item.microsoftgraphsecurityexportreport.ExportReportPostRequestBody exportReportPostRequestBody = new com.microsoft.graph.security.cases.ediscoverycases.item.searches.item.microsoftgraphsecurityexportreport.ExportReportPostRequestBody();
exportReportPostRequestBody.setDisplayName("Export 5");
exportReportPostRequestBody.setExportCriteria(EnumSet.of(com.microsoft.graph.models.security.ExportCriteria.PartiallyIndexed));
exportReportPostRequestBody.setExportLocation(EnumSet.of(com.microsoft.graph.models.security.ExportLocation.ResponsiveLocations));
exportReportPostRequestBody.setAdditionalOptions(EnumSet.of(com.microsoft.graph.models.security.AdditionalOptions.CloudAttachments));
exportReportPostRequestBody.setCloudAttachmentVersion(com.microsoft.graph.models.security.CloudAttachmentVersion.All);
HashMap<String, Object> additionalData = new HashMap<String, Object>();
additionalData.put("doucmentVersion", "recent100");
exportReportPostRequestBody.setAdditionalData(additionalData);
graphClient.security().cases().ediscoveryCases().byEdiscoveryCaseId("{ediscoveryCase-id}").searches().byEdiscoverySearchId("{ediscoverySearch-id}").microsoftGraphSecurityExportReport().post(exportReportPostRequestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const exportReport = {
  displayName: 'Export 5',
  exportCriteria: 'partiallyIndexed',
  exportLocation: 'responsiveLocations',
  additionalOptions: 'cloudAttachments',
  cloudAttachmentVersion: 'all',
  doucmentVersion: 'recent100'
};

await client.api('/security/cases/ediscoveryCases/dbc06feb-a6a5-46a2-8e4e-534353b071e4/searches/6c2ab774-2d2a-46b9-a601-3130f518757b/exportReport')
	.post(exportReport);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Security\Cases\EdiscoveryCases\Item\Searches\Item\MicrosoftGraphSecurityExportReport\ExportReportPostRequestBody;
use Microsoft\Graph\Generated\Models\Security\ExportCriteria;
use Microsoft\Graph\Generated\Models\Security\ExportLocation;
use Microsoft\Graph\Generated\Models\Security\AdditionalOptions;
use Microsoft\Graph\Generated\Models\Security\CloudAttachmentVersion;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new ExportReportPostRequestBody();
$requestBody->setDisplayName('Export 5');
$requestBody->setExportCriteria(new ExportCriteria('partiallyIndexed'));
$requestBody->setExportLocation(new ExportLocation('responsiveLocations'));
$requestBody->setAdditionalOptions(new AdditionalOptions('cloudAttachments'));
$requestBody->setCloudAttachmentVersion(new CloudAttachmentVersion('all'));
$additionalData = [
	'doucmentVersion' => 'recent100',
];
$requestBody->setAdditionalData($additionalData);

$graphServiceClient->security()->cases()->ediscoveryCases()->byEdiscoveryCaseId('ediscoveryCase-id')->searches()->byEdiscoverySearchId('ediscoverySearch-id')->microsoftGraphSecurityExportReport()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Security

$params = @{
	displayName = "Export 5"
	exportCriteria = "partiallyIndexed"
	exportLocation = "responsiveLocations"
	additionalOptions = "cloudAttachments"
	cloudAttachmentVersion = "all"
	doucmentVersion = "recent100"
}

Export-MgSecurityCaseEdiscoveryCaseSearchReport -EdiscoveryCaseId $ediscoveryCaseId -EdiscoverySearchId $ediscoverySearchId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.security.cases.ediscoverycases.item.searches.item.microsoft_graph_security_export_report.export_report_post_request_body import ExportReportPostRequestBody
from msgraph.generated.models.export_criteria import ExportCriteria
from msgraph.generated.models.export_location import ExportLocation
from msgraph.generated.models.additional_options import AdditionalOptions
from msgraph.generated.models.cloud_attachment_version import CloudAttachmentVersion
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = ExportReportPostRequestBody(
	display_name = "Export 5",
	export_criteria = ExportCriteria.PartiallyIndexed,
	export_location = ExportLocation.ResponsiveLocations,
	additional_options = AdditionalOptions.CloudAttachments,
	cloud_attachment_version = CloudAttachmentVersion.All,
	additional_data = {
			"doucment_version" : "recent100",
	}
)

await graph_client.security.cases.ediscovery_cases.by_ediscovery_case_id('ediscoveryCase-id').searches.by_ediscovery_search_id('ediscoverySearch-id').microsoft_graph_security_export_report.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

```http
HTTP/1.1 202 Accepted
Content-Length: 0
Location: https://graph.microsoft.com/v1.0/security/cases/ediscoverycases('dbc06feb-a6a5-46a2-8e4e-534353b071e4')/operations('788159f9-f860-43f2-8fc5-0fc17df0e696')
```
