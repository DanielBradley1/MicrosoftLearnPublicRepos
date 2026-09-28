<!-- Source: https://learn.microsoft.com/en-us/graph/api/ediscovery-reviewset-export?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-01-29 -->

# reviewSet: export

Namespace: microsoft.graph.ediscovery

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Caution

The eDiscovery APIs in the microsoft.graph.eDiscovery subnamespace are deprecated. Use the new [eDiscovery APIs under microsoft.graph.security subnamespace](https://learn.microsoft.com/en-us/graph/api/resources/security-api-overview#ediscovery).

Initiate an export from a **reviewSet**. For details, see [Export documents from a review set in Advanced eDiscovery](https://learn.microsoft.com/en-us/microsoft-365/compliance/export-documents-from-review-set).

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | eDiscovery.Read.All | eDiscovery.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | eDiscovery.Read.All | eDiscovery.ReadWrite.All |

## HTTP request

```http
POST /compliance/ediscovery/cases/{caseId}/reviewsets/{reviewsetId}/export
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the parameters.

The following table shows the parameters that can be used with this action.

| Parameter | Type | Description |
| :--- | :--- | :--- |
| outputName | String | Name of the export. Required. |
| description | String | Description of the export |
| azureBlobContainer | String | When exporting to your own Azure storage account, this is the container URL. |
| azureBlobToken | String | When exporting to your own Azure storage account, SAS token for the container URL. |
| exportOptions | [microsoft.graph.ediscovery.exportOptions](https://learn.microsoft.com/en-us/graph/api/resources/ediscovery-caseexportoperation?view=graph-rest-beta#exportoptions-values) | Specifies options that control the format of the export. The possible values are: `originalFiles`, `text`, `pdfReplacement`, `fileInfo`, `tags`. |
| exportStructure | [microsoft.graph.ediscovery.exportFileStructure](https://learn.microsoft.com/en-us/graph/api/resources/ediscovery-caseexportoperation?view=graph-rest-beta#exportfilestructure-values) | Options that control file structure and packaging of the export. The possible values are: `none`, `directory`, `pst`. |

## Response

If the export is started successfully, this action returns a `202 Accepted` response code. The response contains a `Location` header, which contains the location of the [caseExportOperation](https://learn.microsoft.com/en-us/graph/api/resources/ediscovery-caseexportoperation?view=graph-rest-beta) that was created to handle the export. Check the status of the export operation by making a GET request to the location, when successfully completed, the [status](https://learn.microsoft.com/en-us/graph/api/resources/ediscovery-caseoperation?view=graph-rest-beta#caseoperationstatus-values) changes to `succeeded`.

## Examples

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
POST https://graph.microsoft.com/beta/compliance/ediscovery/cases/99e865fc-e29f-479a-ba83-9e58eb017103/reviewsets/e44ac2cb-f8b4-4fd8-aa1c-1391b46ba9cc/export
Content-Type: application/json

{
  "outputName": "2020-12-06 Contoso investigation export",
  "description": "Export for the Contoso investigation",
  "exportOptions": "originalFiles,fileInfo,tags",
  "exportStructure": "directory"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.Compliance.Ediscovery.Cases.Item.ReviewSets.Item.MicrosoftGraphEdiscoveryExport;
using Microsoft.Graph.Beta.Models.Ediscovery;

var requestBody = new ExportPostRequestBody
{
	OutputName = "2020-12-06 Contoso investigation export",
	Description = "Export for the Contoso investigation",
	ExportOptions = ExportOptions.OriginalFiles | ExportOptions.FileInfo | ExportOptions.Tags,
	ExportStructure = ExportFileStructure.Directory,
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
await graphClient.Compliance.Ediscovery.Cases["{case-id}"].ReviewSets["{reviewSet-id}"].MicrosoftGraphEdiscoveryExport.PostAsync(requestBody);
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
	  graphcompliance "github.com/microsoftgraph/msgraph-beta-sdk-go/compliance"
	  graphmodelsediscovery "github.com/microsoftgraph/msgraph-beta-sdk-go/models/ediscovery"
	  //other-imports
)

requestBody := graphcompliance.NewExportPostRequestBody()
outputName := "2020-12-06 Contoso investigation export"
requestBody.SetOutputName(&outputName) 
description := "Export for the Contoso investigation"
requestBody.SetDescription(&description) 
exportOptions := graphmodels.ORIGINALFILES,FILEINFO,TAGS_EXPORTOPTIONS 
requestBody.SetExportOptions(&exportOptions) 
exportStructure := graphmodels.DIRECTORY_EXPORTFILESTRUCTURE 
requestBody.SetExportStructure(&exportStructure) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
graphClient.Compliance().Ediscovery().Cases().ByCaseId("case-id").ReviewSets().ByReviewSetId("reviewSet-id").MicrosoftGraphEdiscoveryExport().Post(context.Background(), requestBody, nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.beta.compliance.ediscovery.cases.item.reviewsets.item.microsoftgraphediscoveryexport.ExportPostRequestBody exportPostRequestBody = new com.microsoft.graph.beta.compliance.ediscovery.cases.item.reviewsets.item.microsoftgraphediscoveryexport.ExportPostRequestBody();
exportPostRequestBody.setOutputName("2020-12-06 Contoso investigation export");
exportPostRequestBody.setDescription("Export for the Contoso investigation");
exportPostRequestBody.setExportOptions(EnumSet.of(com.microsoft.graph.beta.models.ediscovery.ExportOptions.OriginalFiles, com.microsoft.graph.beta.models.ediscovery.ExportOptions.FileInfo, com.microsoft.graph.beta.models.ediscovery.ExportOptions.Tags));
exportPostRequestBody.setExportStructure(com.microsoft.graph.beta.models.ediscovery.ExportFileStructure.Directory);
graphClient.compliance().ediscovery().cases().byCaseId("{case-id}").reviewSets().byReviewSetId("{reviewSet-id}").microsoftGraphEdiscoveryExport().post(exportPostRequestBody);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const _export = {
  outputName: '2020-12-06 Contoso investigation export',
  description: 'Export for the Contoso investigation',
  exportOptions: 'originalFiles,fileInfo,tags',
  exportStructure: 'directory'
};

await client.api('/compliance/ediscovery/cases/99e865fc-e29f-479a-ba83-9e58eb017103/reviewsets/e44ac2cb-f8b4-4fd8-aa1c-1391b46ba9cc/export')
	.version('beta')
	.post(_export);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Compliance\Ediscovery\Cases\Item\ReviewSets\Item\MicrosoftGraphEdiscoveryExport\ExportPostRequestBody;
use Microsoft\Graph\Beta\Generated\Models\Ediscovery\ExportOptions;
use Microsoft\Graph\Beta\Generated\Models\Ediscovery\ExportFileStructure;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new ExportPostRequestBody();
$requestBody->setOutputName('2020-12-06 Contoso investigation export');
$requestBody->setDescription('Export for the Contoso investigation');
$requestBody->setExportOptions(new ExportOptions('originalFiles,fileInfo,tags'));
$requestBody->setExportStructure(new ExportFileStructure('directory'));

$graphServiceClient->compliance()->ediscovery()->cases()->byCaseId('case-id')->reviewSets()->byReviewSetId('reviewSet-id')->microsoftGraphEdiscoveryExport()->post($requestBody)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Beta.Compliance

$params = @{
	outputName = "2020-12-06 Contoso investigation export"
	description = "Export for the Contoso investigation"
	exportOptions = "originalFiles,fileInfo,tags"
	exportStructure = "directory"
}

Export-MgBetaComplianceEdiscoveryCaseReviewSet -CaseId $caseId -ReviewSetId $reviewSetId -BodyParameter $params
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.compliance.ediscovery.cases.item.reviewsets.item.microsoft_graph_ediscovery_export.export_post_request_body import ExportPostRequestBody
from msgraph_beta.generated.models.export_options import ExportOptions
from msgraph_beta.generated.models.export_file_structure import ExportFileStructure
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = ExportPostRequestBody(
	output_name = "2020-12-06 Contoso investigation export",
	description = "Export for the Contoso investigation",
	export_options = ExportOptions.OriginalFiles | ExportOptions.FileInfo | ExportOptions.Tags,
	export_structure = ExportFileStructure.Directory,
)

await graph_client.compliance.ediscovery.cases.by_case_id('case-id').review_sets.by_review_set_id('reviewSet-id').microsoft_graph_ediscovery_export.post(request_body)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

```http
HTTP/1.1 202 Accepted
cache-control: no-cache,
client-request-id: 3ec98906-7187-927e-5203-2ed4533175c6,
location: https://graph.microsoft.com/beta/compliance/ediscovery/cases('5b840b94-f821-4c4a-8cad-3a90062bf51a')/operations('2ad2da7c7dbb404abfbbb28b7b6babd6'),
request-id: 9e6b9230-113c-49de-8f7d-ecb90d35b0de
```
