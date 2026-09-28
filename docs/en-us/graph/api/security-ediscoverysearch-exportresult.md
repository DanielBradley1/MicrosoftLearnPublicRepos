<!-- Source: https://learn.microsoft.com/en-us/graph/api/security-ediscoverysearch-exportresult?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-02-26 -->

# ediscoverySearch: exportResult

Namespace: microsoft.graph.security

Export results from an estimated [ediscoverySearch](https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoverysearch?view=graph-rest-1.0). For details, see [Manage a collection estimate](https://learn.microsoft.com/en-us/purview/ediscovery-create-draft-collection#manage-a-collection-estimate).

Note

Usage of eDiscovery APIs for tenants with Standard Microsoft \(for example, E3\) licenses requires a subscription to Purview pay-as-you-go billing. For more information, see [Billing in eDiscovery](https://learn.microsoft.com/en-us/purview/edisc-billing).

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
POST /security/cases/ediscoveryCases/{ediscoveryCaseId}/searches/{ediscoverySearchId}/exportResult
POST /security/cases/ediscoveryCases('{ediscoveryCaseId}')/searches('{ediscoverySearchId}')/exportResult
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
| additionalOptions | [microsoft.graph.security.additionalOptions](https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoverysearchexportoperation?view=graph-rest-1.0#additionaloptions-values) | The additional options for the export. The possible values are: `none`, `teamsAndYammerConversations`, `cloudAttachments`, `allDocumentVersions`, `subfolderContents`, `listAttachments`, `unknownFutureValue`, `htmlTranscripts`, `advancedIndexing`, `allItemsInFolder`, `includeFolderAndPath`, `condensePaths`, `friendlyName`, `splitSource`, `includeReport`. Use the `Prefer: include-unknown-enum-members` request header to get the following values from this [evolvable enum](https://learn.microsoft.com/en-us/graph/best-practices-concept#handling-future-members-in-evolvable-enumerations): `htmlTranscripts`, `advancedIndexing`, `allItemsInFolder`, `includeFolderAndPath`, `condensePaths`, `friendlyName`, `splitSource`, `includeReport`. The `advancedIndexing` value is only available if **exportCriteria** includes `partiallyIndexed`. Required. |
| cloudAttachmentVersion | microsoft.graph.security.cloudAttachmentVersion | The versions of cloud attachments to include in messages. The possible values are: `latest`, `recent10`, `recent100`, `all`, `unknownFutureValue`. The default value is `latest`. |
| description | String | The description of the export result. |
| displayName | String | The display name of the export result. |
| documentVersion | microsoft.graph.security.documentVersion | The versions of files in SharePoint to include. The possible values are: `latest`, `recent10`, `recent100`, `all`, `unknownFutureValue`. The default value is `latest`. |
| exportCriteria | [microsoft.graph.security.exportCriteria](https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoverysearchexportoperation?view=graph-rest-1.0#exportcriteria-values) | The portion of the estimate results to be exported. The possible values are: `searchHits`, `partiallyIndexed`, `unknownFutureValue`. Required. |
| exportFormat | [microsoft.graph.security.exportFormat](https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoverysearchexportoperation?view=graph-rest-1.0#exportformat-values) | The desired format of the exported emails. The possible values are: `pst`, `msg`, `eml` \(deprecated\), `unknownFutureValue`. Required. The `eml` member is deprecated. It remains in v1.0 for backward compatibility. Going forward, use either `pst` or `msg`. |
| exportLocation | [microsoft.graph.security.exportLocation](https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoverysearchexportoperation?view=graph-rest-1.0#exportlocation-values) | Location scope for partially indexed items. You can choose to include partially indexed items only in responsive locations with search hits or in all targeted locations. The possible values are: `responsiveLocations`, `nonresponsiveLocations`, `unknownFutureValue`. The `nonresponsiveLocations` value is only available if **exportCriteria** includes `partiallyIndexed`. |

## Response

If the export starts successfully, this action returns a `202 Accepted` response code. The response also contains a `Location` header that includes the location of the [microsoft.graph.security.ediscoverySearchExportOperation](https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoverysearchexportoperation?view=graph-rest-1.0) that was created to handle the export. To check the status of the export operation, make a GET request to the location URL.

## Examples

### Example 1: Export results with search hits only, excluding partially indexed items, as .pst files for each mailbox, and thread contextual chat messages into HTML transcripts

The following example shows how to export results with search hits only, excluding partially indexed items, as .pst files for each mailbox, and thread contextual chat messages into HTML transcripts.

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
POST https://graph.microsoft.com/v1.0/security/cases/ediscoveryCases/dbc06feb-a6a5-46a2-8e4e-534353b071e4/searches/6c2ab774-2d2a-46b9-a601-3130f518757b/exportResult
Content-Type: application/json

{
  "displayName": "Export 1 - simple PST",
  "exportCriteria": "searchHits",
  "additionalOptions": "htmlTranscripts, splitSource, includeFolderAndPath, condensePaths, friendlyName",
  "exportFormat": "pst"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Security.Cases.EdiscoveryCases.Item.Searches.Item.MicrosoftGraphSecurityExportResult;
using Microsoft.Graph.Models.Security;

var requestBody = new ExportResultPostRequestBody
{
	DisplayName = "Export 1 - simple PST",
	ExportCriteria = ExportCriteria.SearchHits,
	AdditionalOptions = AdditionalOptions.HtmlTranscripts | AdditionalOptions.SplitSource | AdditionalOptions.IncludeFolderAndPath | AdditionalOptions.CondensePaths | AdditionalOptions.FriendlyName,
	ExportFormat = ExportFormat.Pst,
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
await graphClient.Security.Cases.EdiscoveryCases["{ediscoveryCase-id}"].Searches["{ediscoverySearch-id}"].MicrosoftGraphSecurityExportResult.PostAsync(requestBody);
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

requestBody := graphsecurity.NewExportResultPostRequestBody()
displayName := "Export 1 - simple PST"
requestBody.SetDisplayName(&displayName) 
exportCriteria := graphmodels.SEARCHHITS_EXPORTCRITERIA 
requestBody.SetExportCriteria(&exportCriteria) 
additionalOptions := graphmodels.HTMLTRANSCRIPTS, SPLITSOURCE, INCLUDEFOLDERANDPATH, CONDENSEPATHS, FRIENDLYNAME_ADDITIONALOPTIONS 
requestBody.SetAdditionalOptions(&additionalOptions) 
exportFormat := graphmodels.PST_EXPORTFORMAT 
requestBody.SetExportFormat(&exportFormat) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
graphClient.Security().Cases().EdiscoveryCases().ByEdiscoveryCaseId("ediscoveryCase-id").Searches().ByEdiscoverySearchId("ediscoverySearch-id").MicrosoftGraphSecurityExportResult().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.security.cases.ediscoverycases.item.searches.item.microsoftgraphsecurityexportresult.ExportResultPostRequestBody exportResultPostRequestBody = new com.microsoft.graph.security.cases.ediscoverycases.item.searches.item.microsoftgraphsecurityexportresult.ExportResultPostRequestBody();
exportResultPostRequestBody.setDisplayName("Export 1 - simple PST");
exportResultPostRequestBody.setExportCriteria(EnumSet.of(com.microsoft.graph.models.security.ExportCriteria.SearchHits));
exportResultPostRequestBody.setAdditionalOptions(EnumSet.of(com.microsoft.graph.models.security.AdditionalOptions.HtmlTranscripts, com.microsoft.graph.models.security.AdditionalOptions.SplitSource, com.microsoft.graph.models.security.AdditionalOptions.IncludeFolderAndPath, com.microsoft.graph.models.security.AdditionalOptions.CondensePaths, com.microsoft.graph.models.security.AdditionalOptions.FriendlyName));
exportResultPostRequestBody.setExportFormat(com.microsoft.graph.models.security.ExportFormat.Pst);
graphClient.security().cases().ediscoveryCases().byEdiscoveryCaseId("{ediscoveryCase-id}").searches().byEdiscoverySearchId("{ediscoverySearch-id}").microsoftGraphSecurityExportResult().post(exportResultPostRequestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const exportResult = {
  displayName: 'Export 1 - simple PST',
  exportCriteria: 'searchHits',
  additionalOptions: 'htmlTranscripts, splitSource, includeFolderAndPath, condensePaths, friendlyName',
  exportFormat: 'pst'
};

await client.api('/security/cases/ediscoveryCases/dbc06feb-a6a5-46a2-8e4e-534353b071e4/searches/6c2ab774-2d2a-46b9-a601-3130f518757b/exportResult')
	.post(exportResult);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Security\Cases\EdiscoveryCases\Item\Searches\Item\MicrosoftGraphSecurityExportResult\ExportResultPostRequestBody;
use Microsoft\Graph\Generated\Models\Security\ExportCriteria;
use Microsoft\Graph\Generated\Models\Security\AdditionalOptions;
use Microsoft\Graph\Generated\Models\Security\ExportFormat;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new ExportResultPostRequestBody();
$requestBody->setDisplayName('Export 1 - simple PST');
$requestBody->setExportCriteria(new ExportCriteria('searchHits'));
$requestBody->setAdditionalOptions(new AdditionalOptions('htmlTranscripts, splitSource, includeFolderAndPath, condensePaths, friendlyName'));
$requestBody->setExportFormat(new ExportFormat('pst'));

$graphServiceClient->security()->cases()->ediscoveryCases()->byEdiscoveryCaseId('ediscoveryCase-id')->searches()->byEdiscoverySearchId('ediscoverySearch-id')->microsoftGraphSecurityExportResult()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Security

$params = @{
	displayName = "Export 1 - simple PST"
	exportCriteria = "searchHits"
	additionalOptions = "htmlTranscripts, splitSource, includeFolderAndPath, condensePaths, friendlyName"
	exportFormat = "pst"
}

Export-MgSecurityCaseEdiscoveryCaseSearchResult -EdiscoveryCaseId $ediscoveryCaseId -EdiscoverySearchId $ediscoverySearchId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.security.cases.ediscoverycases.item.searches.item.microsoft_graph_security_export_result.export_result_post_request_body import ExportResultPostRequestBody
from msgraph.generated.models.export_criteria import ExportCriteria
from msgraph.generated.models.additional_options import AdditionalOptions
from msgraph.generated.models.export_format import ExportFormat
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = ExportResultPostRequestBody(
	display_name = "Export 1 - simple PST",
	export_criteria = ExportCriteria.SearchHits,
	additional_options = AdditionalOptions.HtmlTranscripts | AdditionalOptions.SplitSource | AdditionalOptions.IncludeFolderAndPath | AdditionalOptions.CondensePaths | AdditionalOptions.FriendlyName,
	export_format = ExportFormat.Pst,
)

await graph_client.security.cases.ediscovery_cases.by_ediscovery_case_id('ediscoveryCase-id').searches.by_ediscovery_search_id('ediscoverySearch-id').microsoft_graph_security_export_result.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

```http
HTTP/1.1 202 Accepted
Content-Length: 0
Location: https://graph.microsoft.com/v1.0/security/cases/ediscoverycases('dbc06feb-a6a5-46a2-8e4e-534353b071e4')/operations('01826ce3-43a3-4235-a121-81d05926efae')
```

### Example 2: Export results with search hits and partially indexed items from all locations, as .pst files for each mailbox

The following example shows how to export results with search hits and partially indexed items from all locations, as .pst files for each mailbox.

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
POST https://graph.microsoft.com/v1.0/security/cases/ediscoveryCases/dbc06feb-a6a5-46a2-8e4e-534353b071e4/searches/6c2ab774-2d2a-46b9-a601-3130f518757b/exportResult
Content-Type: application/json

{
  "displayName": "Export 2",
  "exportCriteria": "searchHits, partiallyIndexed",
  "exportLocation": "responsiveLocations, nonresponsiveLocations",
  "additionalOptions": "splitSource",
  "exportFormat": "pst"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Security.Cases.EdiscoveryCases.Item.Searches.Item.MicrosoftGraphSecurityExportResult;
using Microsoft.Graph.Models.Security;

var requestBody = new ExportResultPostRequestBody
{
	DisplayName = "Export 2",
	ExportCriteria = ExportCriteria.SearchHits | ExportCriteria.PartiallyIndexed,
	ExportLocation = ExportLocation.ResponsiveLocations | ExportLocation.NonresponsiveLocations,
	AdditionalOptions = AdditionalOptions.SplitSource,
	ExportFormat = ExportFormat.Pst,
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
await graphClient.Security.Cases.EdiscoveryCases["{ediscoveryCase-id}"].Searches["{ediscoverySearch-id}"].MicrosoftGraphSecurityExportResult.PostAsync(requestBody);
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

requestBody := graphsecurity.NewExportResultPostRequestBody()
displayName := "Export 2"
requestBody.SetDisplayName(&displayName) 
exportCriteria := graphmodels.SEARCHHITS, PARTIALLYINDEXED_EXPORTCRITERIA 
requestBody.SetExportCriteria(&exportCriteria) 
exportLocation := graphmodels.RESPONSIVELOCATIONS, NONRESPONSIVELOCATIONS_EXPORTLOCATION 
requestBody.SetExportLocation(&exportLocation) 
additionalOptions := graphmodels.SPLITSOURCE_ADDITIONALOPTIONS 
requestBody.SetAdditionalOptions(&additionalOptions) 
exportFormat := graphmodels.PST_EXPORTFORMAT 
requestBody.SetExportFormat(&exportFormat) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
graphClient.Security().Cases().EdiscoveryCases().ByEdiscoveryCaseId("ediscoveryCase-id").Searches().ByEdiscoverySearchId("ediscoverySearch-id").MicrosoftGraphSecurityExportResult().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.security.cases.ediscoverycases.item.searches.item.microsoftgraphsecurityexportresult.ExportResultPostRequestBody exportResultPostRequestBody = new com.microsoft.graph.security.cases.ediscoverycases.item.searches.item.microsoftgraphsecurityexportresult.ExportResultPostRequestBody();
exportResultPostRequestBody.setDisplayName("Export 2");
exportResultPostRequestBody.setExportCriteria(EnumSet.of(com.microsoft.graph.models.security.ExportCriteria.SearchHits, com.microsoft.graph.models.security.ExportCriteria.PartiallyIndexed));
exportResultPostRequestBody.setExportLocation(EnumSet.of(com.microsoft.graph.models.security.ExportLocation.ResponsiveLocations, com.microsoft.graph.models.security.ExportLocation.NonresponsiveLocations));
exportResultPostRequestBody.setAdditionalOptions(EnumSet.of(com.microsoft.graph.models.security.AdditionalOptions.SplitSource));
exportResultPostRequestBody.setExportFormat(com.microsoft.graph.models.security.ExportFormat.Pst);
graphClient.security().cases().ediscoveryCases().byEdiscoveryCaseId("{ediscoveryCase-id}").searches().byEdiscoverySearchId("{ediscoverySearch-id}").microsoftGraphSecurityExportResult().post(exportResultPostRequestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const exportResult = {
  displayName: 'Export 2',
  exportCriteria: 'searchHits, partiallyIndexed',
  exportLocation: 'responsiveLocations, nonresponsiveLocations',
  additionalOptions: 'splitSource',
  exportFormat: 'pst'
};

await client.api('/security/cases/ediscoveryCases/dbc06feb-a6a5-46a2-8e4e-534353b071e4/searches/6c2ab774-2d2a-46b9-a601-3130f518757b/exportResult')
	.post(exportResult);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Security\Cases\EdiscoveryCases\Item\Searches\Item\MicrosoftGraphSecurityExportResult\ExportResultPostRequestBody;
use Microsoft\Graph\Generated\Models\Security\ExportCriteria;
use Microsoft\Graph\Generated\Models\Security\ExportLocation;
use Microsoft\Graph\Generated\Models\Security\AdditionalOptions;
use Microsoft\Graph\Generated\Models\Security\ExportFormat;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new ExportResultPostRequestBody();
$requestBody->setDisplayName('Export 2');
$requestBody->setExportCriteria(new ExportCriteria('searchHits, partiallyIndexed'));
$requestBody->setExportLocation(new ExportLocation('responsiveLocations, nonresponsiveLocations'));
$requestBody->setAdditionalOptions(new AdditionalOptions('splitSource'));
$requestBody->setExportFormat(new ExportFormat('pst'));

$graphServiceClient->security()->cases()->ediscoveryCases()->byEdiscoveryCaseId('ediscoveryCase-id')->searches()->byEdiscoverySearchId('ediscoverySearch-id')->microsoftGraphSecurityExportResult()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Security

$params = @{
	displayName = "Export 2"
	exportCriteria = "searchHits, partiallyIndexed"
	exportLocation = "responsiveLocations, nonresponsiveLocations"
	additionalOptions = "splitSource"
	exportFormat = "pst"
}

Export-MgSecurityCaseEdiscoveryCaseSearchResult -EdiscoveryCaseId $ediscoveryCaseId -EdiscoverySearchId $ediscoverySearchId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.security.cases.ediscoverycases.item.searches.item.microsoft_graph_security_export_result.export_result_post_request_body import ExportResultPostRequestBody
from msgraph.generated.models.export_criteria import ExportCriteria
from msgraph.generated.models.export_location import ExportLocation
from msgraph.generated.models.additional_options import AdditionalOptions
from msgraph.generated.models.export_format import ExportFormat
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = ExportResultPostRequestBody(
	display_name = "Export 2",
	export_criteria = ExportCriteria.SearchHits | ExportCriteria.PartiallyIndexed,
	export_location = ExportLocation.ResponsiveLocations | ExportLocation.NonresponsiveLocations,
	additional_options = AdditionalOptions.SplitSource,
	export_format = ExportFormat.Pst,
)

await graph_client.security.cases.ediscovery_cases.by_ediscovery_case_id('ediscoveryCase-id').searches.by_ediscovery_search_id('ediscoverySearch-id').microsoft_graph_security_export_result.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

```http
HTTP/1.1 202 Accepted
Content-Length: 0
Location: https://graph.microsoft.com/v1.0/security/cases/ediscoverycases('dbc06feb-a6a5-46a2-8e4e-534353b071e4')/operations('c74d3039-5c79-4093-8e45-2abb94e32ba9')
```

### Example 3: Export results with search hits and partially indexed items from locations with search hits, with no additional options, as .msg files for each message

The following example shows how to export results with search hits and partially indexed items from locations with search hits, with no additional options selected, as .msg files for each message.

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
POST https://graph.microsoft.com/v1.0/security/cases/ediscoveryCases/dbc06feb-a6a5-46a2-8e4e-534353b071e4/searches/6c2ab774-2d2a-46b9-a601-3130f518757b/exportResult
Content-Type: application/json

{
  "displayName": "Export 3",
  "exportCriteria": "searchHits, partiallyIndexed",
  "exportLocation": "responsiveLocations",
  "additionalOptions": "none",
  "exportFormat": "msg"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Security.Cases.EdiscoveryCases.Item.Searches.Item.MicrosoftGraphSecurityExportResult;
using Microsoft.Graph.Models.Security;

var requestBody = new ExportResultPostRequestBody
{
	DisplayName = "Export 3",
	ExportCriteria = ExportCriteria.SearchHits | ExportCriteria.PartiallyIndexed,
	ExportLocation = ExportLocation.ResponsiveLocations,
	AdditionalOptions = AdditionalOptions.None,
	ExportFormat = ExportFormat.Msg,
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
await graphClient.Security.Cases.EdiscoveryCases["{ediscoveryCase-id}"].Searches["{ediscoverySearch-id}"].MicrosoftGraphSecurityExportResult.PostAsync(requestBody);
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

requestBody := graphsecurity.NewExportResultPostRequestBody()
displayName := "Export 3"
requestBody.SetDisplayName(&displayName) 
exportCriteria := graphmodels.SEARCHHITS, PARTIALLYINDEXED_EXPORTCRITERIA 
requestBody.SetExportCriteria(&exportCriteria) 
exportLocation := graphmodels.RESPONSIVELOCATIONS_EXPORTLOCATION 
requestBody.SetExportLocation(&exportLocation) 
additionalOptions := graphmodels.NONE_ADDITIONALOPTIONS 
requestBody.SetAdditionalOptions(&additionalOptions) 
exportFormat := graphmodels.MSG_EXPORTFORMAT 
requestBody.SetExportFormat(&exportFormat) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
graphClient.Security().Cases().EdiscoveryCases().ByEdiscoveryCaseId("ediscoveryCase-id").Searches().ByEdiscoverySearchId("ediscoverySearch-id").MicrosoftGraphSecurityExportResult().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.security.cases.ediscoverycases.item.searches.item.microsoftgraphsecurityexportresult.ExportResultPostRequestBody exportResultPostRequestBody = new com.microsoft.graph.security.cases.ediscoverycases.item.searches.item.microsoftgraphsecurityexportresult.ExportResultPostRequestBody();
exportResultPostRequestBody.setDisplayName("Export 3");
exportResultPostRequestBody.setExportCriteria(EnumSet.of(com.microsoft.graph.models.security.ExportCriteria.SearchHits, com.microsoft.graph.models.security.ExportCriteria.PartiallyIndexed));
exportResultPostRequestBody.setExportLocation(EnumSet.of(com.microsoft.graph.models.security.ExportLocation.ResponsiveLocations));
exportResultPostRequestBody.setAdditionalOptions(EnumSet.of(com.microsoft.graph.models.security.AdditionalOptions.None));
exportResultPostRequestBody.setExportFormat(com.microsoft.graph.models.security.ExportFormat.Msg);
graphClient.security().cases().ediscoveryCases().byEdiscoveryCaseId("{ediscoveryCase-id}").searches().byEdiscoverySearchId("{ediscoverySearch-id}").microsoftGraphSecurityExportResult().post(exportResultPostRequestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const exportResult = {
  displayName: 'Export 3',
  exportCriteria: 'searchHits, partiallyIndexed',
  exportLocation: 'responsiveLocations',
  additionalOptions: 'none',
  exportFormat: 'msg'
};

await client.api('/security/cases/ediscoveryCases/dbc06feb-a6a5-46a2-8e4e-534353b071e4/searches/6c2ab774-2d2a-46b9-a601-3130f518757b/exportResult')
	.post(exportResult);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Security\Cases\EdiscoveryCases\Item\Searches\Item\MicrosoftGraphSecurityExportResult\ExportResultPostRequestBody;
use Microsoft\Graph\Generated\Models\Security\ExportCriteria;
use Microsoft\Graph\Generated\Models\Security\ExportLocation;
use Microsoft\Graph\Generated\Models\Security\AdditionalOptions;
use Microsoft\Graph\Generated\Models\Security\ExportFormat;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new ExportResultPostRequestBody();
$requestBody->setDisplayName('Export 3');
$requestBody->setExportCriteria(new ExportCriteria('searchHits, partiallyIndexed'));
$requestBody->setExportLocation(new ExportLocation('responsiveLocations'));
$requestBody->setAdditionalOptions(new AdditionalOptions('none'));
$requestBody->setExportFormat(new ExportFormat('msg'));

$graphServiceClient->security()->cases()->ediscoveryCases()->byEdiscoveryCaseId('ediscoveryCase-id')->searches()->byEdiscoverySearchId('ediscoverySearch-id')->microsoftGraphSecurityExportResult()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Security

$params = @{
	displayName = "Export 3"
	exportCriteria = "searchHits, partiallyIndexed"
	exportLocation = "responsiveLocations"
	additionalOptions = "none"
	exportFormat = "msg"
}

Export-MgSecurityCaseEdiscoveryCaseSearchResult -EdiscoveryCaseId $ediscoveryCaseId -EdiscoverySearchId $ediscoverySearchId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.security.cases.ediscoverycases.item.searches.item.microsoft_graph_security_export_result.export_result_post_request_body import ExportResultPostRequestBody
from msgraph.generated.models.export_criteria import ExportCriteria
from msgraph.generated.models.export_location import ExportLocation
from msgraph.generated.models.additional_options import AdditionalOptions
from msgraph.generated.models.export_format import ExportFormat
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = ExportResultPostRequestBody(
	display_name = "Export 3",
	export_criteria = ExportCriteria.SearchHits | ExportCriteria.PartiallyIndexed,
	export_location = ExportLocation.ResponsiveLocations,
	additional_options = AdditionalOptions.None,
	export_format = ExportFormat.Msg,
)

await graph_client.security.cases.ediscovery_cases.by_ediscovery_case_id('ediscoveryCase-id').searches.by_ediscovery_search_id('ediscoverySearch-id').microsoft_graph_security_export_result.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

```http
HTTP/1.1 202 Accepted
Content-Length: 0
Location: https://graph.microsoft.com/v1.0/security/cases/ediscoverycases('dbc06feb-a6a5-46a2-8e4e-534353b071e4')/operations('4bf812e0-44ad-4856-a302-b4ea79725573')
```

### Example 4: Export results with partially indexed items from all targeted locations, with all additional options, as .eml files for each message

The following example shows how to export results with partially indexed items from all targeted locations, with all additional options selected, as .eml files for each message.

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
POST https://graph.microsoft.com/v1.0/security/cases/ediscoveryCases/dbc06feb-a6a5-46a2-8e4e-534353b071e4/searches/6c2ab774-2d2a-46b9-a601-3130f518757b/exportResult
Content-Type: application/json

{
  "displayName": "Export 4",
  "exportCriteria": "partiallyIndexed",
  "exportLocation": "responsiveLocations, nonresponsiveLocations",
  "additionalOptions": "advancedIndexing, subfolderContents, allItemsInFolder, listAttachments, teamsAndYammerConversations, htmlTranscripts, cloudAttachments, includeFolderAndPath, splitSource, condensePaths, friendlyName, includeReport",
  "exportFormat": "eml"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Security.Cases.EdiscoveryCases.Item.Searches.Item.MicrosoftGraphSecurityExportResult;
using Microsoft.Graph.Models.Security;

var requestBody = new ExportResultPostRequestBody
{
	DisplayName = "Export 4",
	ExportCriteria = ExportCriteria.PartiallyIndexed,
	ExportLocation = ExportLocation.ResponsiveLocations | ExportLocation.NonresponsiveLocations,
	AdditionalOptions = AdditionalOptions.AdvancedIndexing | AdditionalOptions.SubfolderContents | AdditionalOptions.AllItemsInFolder | AdditionalOptions.ListAttachments | AdditionalOptions.TeamsAndYammerConversations | AdditionalOptions.HtmlTranscripts | AdditionalOptions.CloudAttachments | AdditionalOptions.IncludeFolderAndPath | AdditionalOptions.SplitSource | AdditionalOptions.CondensePaths | AdditionalOptions.FriendlyName | AdditionalOptions.IncludeReport,
	ExportFormat = ExportFormat.Eml,
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
await graphClient.Security.Cases.EdiscoveryCases["{ediscoveryCase-id}"].Searches["{ediscoverySearch-id}"].MicrosoftGraphSecurityExportResult.PostAsync(requestBody);
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

requestBody := graphsecurity.NewExportResultPostRequestBody()
displayName := "Export 4"
requestBody.SetDisplayName(&displayName) 
exportCriteria := graphmodels.PARTIALLYINDEXED_EXPORTCRITERIA 
requestBody.SetExportCriteria(&exportCriteria) 
exportLocation := graphmodels.RESPONSIVELOCATIONS, NONRESPONSIVELOCATIONS_EXPORTLOCATION 
requestBody.SetExportLocation(&exportLocation) 
additionalOptions := graphmodels.ADVANCEDINDEXING, SUBFOLDERCONTENTS, ALLITEMSINFOLDER, LISTATTACHMENTS, TEAMSANDYAMMERCONVERSATIONS, HTMLTRANSCRIPTS, CLOUDATTACHMENTS, INCLUDEFOLDERANDPATH, SPLITSOURCE, CONDENSEPATHS, FRIENDLYNAME, INCLUDEREPORT_ADDITIONALOPTIONS 
requestBody.SetAdditionalOptions(&additionalOptions) 
exportFormat := graphmodels.EML_EXPORTFORMAT 
requestBody.SetExportFormat(&exportFormat) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
graphClient.Security().Cases().EdiscoveryCases().ByEdiscoveryCaseId("ediscoveryCase-id").Searches().ByEdiscoverySearchId("ediscoverySearch-id").MicrosoftGraphSecurityExportResult().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.security.cases.ediscoverycases.item.searches.item.microsoftgraphsecurityexportresult.ExportResultPostRequestBody exportResultPostRequestBody = new com.microsoft.graph.security.cases.ediscoverycases.item.searches.item.microsoftgraphsecurityexportresult.ExportResultPostRequestBody();
exportResultPostRequestBody.setDisplayName("Export 4");
exportResultPostRequestBody.setExportCriteria(EnumSet.of(com.microsoft.graph.models.security.ExportCriteria.PartiallyIndexed));
exportResultPostRequestBody.setExportLocation(EnumSet.of(com.microsoft.graph.models.security.ExportLocation.ResponsiveLocations, com.microsoft.graph.models.security.ExportLocation.NonresponsiveLocations));
exportResultPostRequestBody.setAdditionalOptions(EnumSet.of(com.microsoft.graph.models.security.AdditionalOptions.AdvancedIndexing, com.microsoft.graph.models.security.AdditionalOptions.SubfolderContents, com.microsoft.graph.models.security.AdditionalOptions.AllItemsInFolder, com.microsoft.graph.models.security.AdditionalOptions.ListAttachments, com.microsoft.graph.models.security.AdditionalOptions.TeamsAndYammerConversations, com.microsoft.graph.models.security.AdditionalOptions.HtmlTranscripts, com.microsoft.graph.models.security.AdditionalOptions.CloudAttachments, com.microsoft.graph.models.security.AdditionalOptions.IncludeFolderAndPath, com.microsoft.graph.models.security.AdditionalOptions.SplitSource, com.microsoft.graph.models.security.AdditionalOptions.CondensePaths, com.microsoft.graph.models.security.AdditionalOptions.FriendlyName, com.microsoft.graph.models.security.AdditionalOptions.IncludeReport));
exportResultPostRequestBody.setExportFormat(com.microsoft.graph.models.security.ExportFormat.Eml);
graphClient.security().cases().ediscoveryCases().byEdiscoveryCaseId("{ediscoveryCase-id}").searches().byEdiscoverySearchId("{ediscoverySearch-id}").microsoftGraphSecurityExportResult().post(exportResultPostRequestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const exportResult = {
  displayName: 'Export 4',
  exportCriteria: 'partiallyIndexed',
  exportLocation: 'responsiveLocations, nonresponsiveLocations',
  additionalOptions: 'advancedIndexing, subfolderContents, allItemsInFolder, listAttachments, teamsAndYammerConversations, htmlTranscripts, cloudAttachments, includeFolderAndPath, splitSource, condensePaths, friendlyName, includeReport',
  exportFormat: 'eml'
};

await client.api('/security/cases/ediscoveryCases/dbc06feb-a6a5-46a2-8e4e-534353b071e4/searches/6c2ab774-2d2a-46b9-a601-3130f518757b/exportResult')
	.post(exportResult);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Security\Cases\EdiscoveryCases\Item\Searches\Item\MicrosoftGraphSecurityExportResult\ExportResultPostRequestBody;
use Microsoft\Graph\Generated\Models\Security\ExportCriteria;
use Microsoft\Graph\Generated\Models\Security\ExportLocation;
use Microsoft\Graph\Generated\Models\Security\AdditionalOptions;
use Microsoft\Graph\Generated\Models\Security\ExportFormat;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new ExportResultPostRequestBody();
$requestBody->setDisplayName('Export 4');
$requestBody->setExportCriteria(new ExportCriteria('partiallyIndexed'));
$requestBody->setExportLocation(new ExportLocation('responsiveLocations, nonresponsiveLocations'));
$requestBody->setAdditionalOptions(new AdditionalOptions('advancedIndexing, subfolderContents, allItemsInFolder, listAttachments, teamsAndYammerConversations, htmlTranscripts, cloudAttachments, includeFolderAndPath, splitSource, condensePaths, friendlyName, includeReport'));
$requestBody->setExportFormat(new ExportFormat('eml'));

$graphServiceClient->security()->cases()->ediscoveryCases()->byEdiscoveryCaseId('ediscoveryCase-id')->searches()->byEdiscoverySearchId('ediscoverySearch-id')->microsoftGraphSecurityExportResult()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Security

$params = @{
	displayName = "Export 4"
	exportCriteria = "partiallyIndexed"
	exportLocation = "responsiveLocations, nonresponsiveLocations"
	additionalOptions = "advancedIndexing, subfolderContents, allItemsInFolder, listAttachments, teamsAndYammerConversations, htmlTranscripts, cloudAttachments, includeFolderAndPath, splitSource, condensePaths, friendlyName, includeReport"
	exportFormat = "eml"
}

Export-MgSecurityCaseEdiscoveryCaseSearchResult -EdiscoveryCaseId $ediscoveryCaseId -EdiscoverySearchId $ediscoverySearchId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.security.cases.ediscoverycases.item.searches.item.microsoft_graph_security_export_result.export_result_post_request_body import ExportResultPostRequestBody
from msgraph.generated.models.export_criteria import ExportCriteria
from msgraph.generated.models.export_location import ExportLocation
from msgraph.generated.models.additional_options import AdditionalOptions
from msgraph.generated.models.export_format import ExportFormat
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = ExportResultPostRequestBody(
	display_name = "Export 4",
	export_criteria = ExportCriteria.PartiallyIndexed,
	export_location = ExportLocation.ResponsiveLocations | ExportLocation.NonresponsiveLocations,
	additional_options = AdditionalOptions.AdvancedIndexing | AdditionalOptions.SubfolderContents | AdditionalOptions.AllItemsInFolder | AdditionalOptions.ListAttachments | AdditionalOptions.TeamsAndYammerConversations | AdditionalOptions.HtmlTranscripts | AdditionalOptions.CloudAttachments | AdditionalOptions.IncludeFolderAndPath | AdditionalOptions.SplitSource | AdditionalOptions.CondensePaths | AdditionalOptions.FriendlyName | AdditionalOptions.IncludeReport,
	export_format = ExportFormat.Eml,
)

await graph_client.security.cases.ediscovery_cases.by_ediscovery_case_id('ediscoveryCase-id').searches.by_ediscovery_search_id('ediscoverySearch-id').microsoft_graph_security_export_result.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

```http
HTTP/1.1 202 Accepted
Content-Length: 0
Location: https://graph.microsoft.com/v1.0/security/cases/ediscoverycases('dbc06feb-a6a5-46a2-8e4e-534353b071e4')/operations('05b5c707-ed0d-4f5c-bbfd-e4941137baf1')
```

### Example 5: Export results with partially indexed items from search hit locations and cloud attachments

The following example shows how to export results with partially indexed items from search hit locations and cloud attachments. It specifies how many versions of documents and cloud attachments to include, and exports each message as a .eml file.

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
POST https://graph.microsoft.com/v1.0/security/cases/ediscoveryCases/dbc06feb-a6a5-46a2-8e4e-534353b071e4/searches/6c2ab774-2d2a-46b9-a601-3130f518757b/exportResult
Content-Type: application/json

{
  "displayName": "Export 5",
  "exportCriteria": "partiallyIndexed",
  "exportLocation": "responsiveLocations",
  "additionalOptions": "splitSource, includeFolderAndPath, condensePaths, friendlyName",
  "exportFormat": "eml",
  "cloudAttachmentVersion": "all",
  "documentVersion": "recent100"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Security.Cases.EdiscoveryCases.Item.Searches.Item.MicrosoftGraphSecurityExportResult;
using Microsoft.Graph.Models.Security;

var requestBody = new ExportResultPostRequestBody
{
	DisplayName = "Export 5",
	ExportCriteria = ExportCriteria.PartiallyIndexed,
	ExportLocation = ExportLocation.ResponsiveLocations,
	AdditionalOptions = AdditionalOptions.SplitSource | AdditionalOptions.IncludeFolderAndPath | AdditionalOptions.CondensePaths | AdditionalOptions.FriendlyName,
	ExportFormat = ExportFormat.Eml,
	CloudAttachmentVersion = CloudAttachmentVersion.All,
	DocumentVersion = DocumentVersion.Recent100,
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
await graphClient.Security.Cases.EdiscoveryCases["{ediscoveryCase-id}"].Searches["{ediscoverySearch-id}"].MicrosoftGraphSecurityExportResult.PostAsync(requestBody);
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

requestBody := graphsecurity.NewExportResultPostRequestBody()
displayName := "Export 5"
requestBody.SetDisplayName(&displayName) 
exportCriteria := graphmodels.PARTIALLYINDEXED_EXPORTCRITERIA 
requestBody.SetExportCriteria(&exportCriteria) 
exportLocation := graphmodels.RESPONSIVELOCATIONS_EXPORTLOCATION 
requestBody.SetExportLocation(&exportLocation) 
additionalOptions := graphmodels.SPLITSOURCE, INCLUDEFOLDERANDPATH, CONDENSEPATHS, FRIENDLYNAME_ADDITIONALOPTIONS 
requestBody.SetAdditionalOptions(&additionalOptions) 
exportFormat := graphmodels.EML_EXPORTFORMAT 
requestBody.SetExportFormat(&exportFormat) 
cloudAttachmentVersion := graphmodels.ALL_CLOUDATTACHMENTVERSION 
requestBody.SetCloudAttachmentVersion(&cloudAttachmentVersion) 
documentVersion := graphmodels.RECENT100_DOCUMENTVERSION 
requestBody.SetDocumentVersion(&documentVersion) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
graphClient.Security().Cases().EdiscoveryCases().ByEdiscoveryCaseId("ediscoveryCase-id").Searches().ByEdiscoverySearchId("ediscoverySearch-id").MicrosoftGraphSecurityExportResult().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.security.cases.ediscoverycases.item.searches.item.microsoftgraphsecurityexportresult.ExportResultPostRequestBody exportResultPostRequestBody = new com.microsoft.graph.security.cases.ediscoverycases.item.searches.item.microsoftgraphsecurityexportresult.ExportResultPostRequestBody();
exportResultPostRequestBody.setDisplayName("Export 5");
exportResultPostRequestBody.setExportCriteria(EnumSet.of(com.microsoft.graph.models.security.ExportCriteria.PartiallyIndexed));
exportResultPostRequestBody.setExportLocation(EnumSet.of(com.microsoft.graph.models.security.ExportLocation.ResponsiveLocations));
exportResultPostRequestBody.setAdditionalOptions(EnumSet.of(com.microsoft.graph.models.security.AdditionalOptions.SplitSource, com.microsoft.graph.models.security.AdditionalOptions.IncludeFolderAndPath, com.microsoft.graph.models.security.AdditionalOptions.CondensePaths, com.microsoft.graph.models.security.AdditionalOptions.FriendlyName));
exportResultPostRequestBody.setExportFormat(com.microsoft.graph.models.security.ExportFormat.Eml);
exportResultPostRequestBody.setCloudAttachmentVersion(com.microsoft.graph.models.security.CloudAttachmentVersion.All);
exportResultPostRequestBody.setDocumentVersion(com.microsoft.graph.models.security.DocumentVersion.Recent100);
graphClient.security().cases().ediscoveryCases().byEdiscoveryCaseId("{ediscoveryCase-id}").searches().byEdiscoverySearchId("{ediscoverySearch-id}").microsoftGraphSecurityExportResult().post(exportResultPostRequestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const exportResult = {
  displayName: 'Export 5',
  exportCriteria: 'partiallyIndexed',
  exportLocation: 'responsiveLocations',
  additionalOptions: 'splitSource, includeFolderAndPath, condensePaths, friendlyName',
  exportFormat: 'eml',
  cloudAttachmentVersion: 'all',
  documentVersion: 'recent100'
};

await client.api('/security/cases/ediscoveryCases/dbc06feb-a6a5-46a2-8e4e-534353b071e4/searches/6c2ab774-2d2a-46b9-a601-3130f518757b/exportResult')
	.post(exportResult);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Security\Cases\EdiscoveryCases\Item\Searches\Item\MicrosoftGraphSecurityExportResult\ExportResultPostRequestBody;
use Microsoft\Graph\Generated\Models\Security\ExportCriteria;
use Microsoft\Graph\Generated\Models\Security\ExportLocation;
use Microsoft\Graph\Generated\Models\Security\AdditionalOptions;
use Microsoft\Graph\Generated\Models\Security\ExportFormat;
use Microsoft\Graph\Generated\Models\Security\CloudAttachmentVersion;
use Microsoft\Graph\Generated\Models\Security\DocumentVersion;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new ExportResultPostRequestBody();
$requestBody->setDisplayName('Export 5');
$requestBody->setExportCriteria(new ExportCriteria('partiallyIndexed'));
$requestBody->setExportLocation(new ExportLocation('responsiveLocations'));
$requestBody->setAdditionalOptions(new AdditionalOptions('splitSource, includeFolderAndPath, condensePaths, friendlyName'));
$requestBody->setExportFormat(new ExportFormat('eml'));
$requestBody->setCloudAttachmentVersion(new CloudAttachmentVersion('all'));
$requestBody->setDocumentVersion(new DocumentVersion('recent100'));

$graphServiceClient->security()->cases()->ediscoveryCases()->byEdiscoveryCaseId('ediscoveryCase-id')->searches()->byEdiscoverySearchId('ediscoverySearch-id')->microsoftGraphSecurityExportResult()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Security

$params = @{
	displayName = "Export 5"
	exportCriteria = "partiallyIndexed"
	exportLocation = "responsiveLocations"
	additionalOptions = "splitSource, includeFolderAndPath, condensePaths, friendlyName"
	exportFormat = "eml"
	cloudAttachmentVersion = "all"
	documentVersion = "recent100"
}

Export-MgSecurityCaseEdiscoveryCaseSearchResult -EdiscoveryCaseId $ediscoveryCaseId -EdiscoverySearchId $ediscoverySearchId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.security.cases.ediscoverycases.item.searches.item.microsoft_graph_security_export_result.export_result_post_request_body import ExportResultPostRequestBody
from msgraph.generated.models.export_criteria import ExportCriteria
from msgraph.generated.models.export_location import ExportLocation
from msgraph.generated.models.additional_options import AdditionalOptions
from msgraph.generated.models.export_format import ExportFormat
from msgraph.generated.models.cloud_attachment_version import CloudAttachmentVersion
from msgraph.generated.models.document_version import DocumentVersion
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = ExportResultPostRequestBody(
	display_name = "Export 5",
	export_criteria = ExportCriteria.PartiallyIndexed,
	export_location = ExportLocation.ResponsiveLocations,
	additional_options = AdditionalOptions.SplitSource | AdditionalOptions.IncludeFolderAndPath | AdditionalOptions.CondensePaths | AdditionalOptions.FriendlyName,
	export_format = ExportFormat.Eml,
	cloud_attachment_version = CloudAttachmentVersion.All,
	document_version = DocumentVersion.Recent100,
)

await graph_client.security.cases.ediscovery_cases.by_ediscovery_case_id('ediscoveryCase-id').searches.by_ediscovery_search_id('ediscoverySearch-id').microsoft_graph_security_export_result.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

```http
HTTP/1.1 202 Accepted
Content-Length: 0
Location: https://graph.microsoft.com/v1.0/security/cases/ediscoverycases('dbc06feb-a6a5-46a2-8e4e-534353b071e4')/operations('d488f23e-f3cb-4a1c-9b9f-88ac4342f534')
```
