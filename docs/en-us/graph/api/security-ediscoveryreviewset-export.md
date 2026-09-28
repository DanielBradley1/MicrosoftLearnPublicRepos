<!-- Source: https://learn.microsoft.com/en-us/graph/api/security-ediscoveryreviewset-export?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-01-29 -->

# ediscoveryReviewSet: export

Namespace: microsoft.graph.security

Initiate an export from a [ediscoveryReviewSet](https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoveryreviewset?view=graph-rest-1.0). For details, see [Export documents from a review set in eDiscovery \(Premium\)](https://learn.microsoft.com/en-us/microsoft-365/compliance/export-documents-from-review-set).

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
POST /security/cases/ediscoveryCases/{ediscoveryCaseId}/reviewSets/{ediscoveryReviewSetId}/export
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
| description | String | Description of the export. |
| exportOptions | [microsoft.graph.security.exportOptions](https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoveryexportoperation?view=graph-rest-1.0#exportoptions-values) | Bitwise options that control the format of the export. The possible values are: `originalFiles`, `text`, `pdfReplacement`, `tags`, `unknownFutureValue`, `splitSource`, `includeFolderAndPath`, `friendlyName`, `condensePaths`. Use the `Prefer: include-unknown-enum-members` request header to get the following values from this [evolvable enum](https://learn.microsoft.com/en-us/graph/best-practices-concept#handling-future-members-in-evolvable-enumerations): `splitSource`, `includeFolderAndPath`, `friendlyName`, `condensePaths`. The summary and load files are always included. If `originalFiles` isn't selected, only the `tags` member is considered. |
| exportStructure | [microsoft.graph.security.exportFileStructure](https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoveryexportoperation?view=graph-rest-1.0#exportfilestructure-values) | Bitwise options that control file structure and packaging of the export. The possible values are: `none`, `directory` \(deprecated\), `pst`, `unknownFutureValue`, `msg`. Use the `Prefer: include-unknown-enum-members` request header to get the following members from this [evolvable enum](https://learn.microsoft.com/en-us/graph/best-practices-concept#handling-future-members-in-evolvable-enumerations): `msg`. The `directory` member is deprecated. It remains in v1.0 for backward compatibility. Going forward, use either `pst` or `msg`. |
| outputName | String | Name of the export. Required. |

## Response

If the export has started successfully, this action returns a `202 Accepted` response code. The response contains also a `Location` header, which contains the location of the [Export operation](https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoveryexportoperation?view=graph-rest-1.0) that was created to handle the export.

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
POST https://graph.microsoft.com/v1.0/security/cases/ediscoveryCases/58399dff-cebe-478f-b1af-d3227f1fd645/reviewSets/273f11a1-17aa-419c-981d-ff10d33e420f/export
Content-Type: application/json

{
    "outputName": "Export via API",
    "description": "Export for the Contoso investigation",
    "exportOptions": "originalFiles,tags",
    "exportStructure": "directory"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Security.Cases.EdiscoveryCases.Item.ReviewSets.Item.MicrosoftGraphSecurityExport;
using Microsoft.Graph.Models.Security;

var requestBody = new ExportPostRequestBody
{
	OutputName = "Export via API",
	Description = "Export for the Contoso investigation",
	ExportOptions = ExportOptions.OriginalFiles | ExportOptions.Tags,
	ExportStructure = ExportFileStructure.Directory,
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
await graphClient.Security.Cases.EdiscoveryCases["{ediscoveryCase-id}"].ReviewSets["{ediscoveryReviewSet-id}"].MicrosoftGraphSecurityExport.PostAsync(requestBody);
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

requestBody := graphsecurity.NewExportPostRequestBody()
outputName := "Export via API"
requestBody.SetOutputName(&outputName) 
description := "Export for the Contoso investigation"
requestBody.SetDescription(&description) 
exportOptions := graphmodels.ORIGINALFILES,TAGS_EXPORTOPTIONS 
requestBody.SetExportOptions(&exportOptions) 
exportStructure := graphmodels.DIRECTORY_EXPORTFILESTRUCTURE 
requestBody.SetExportStructure(&exportStructure) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
graphClient.Security().Cases().EdiscoveryCases().ByEdiscoveryCaseId("ediscoveryCase-id").ReviewSets().ByEdiscoveryReviewSetId("ediscoveryReviewSet-id").MicrosoftGraphSecurityExport().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.security.cases.ediscoverycases.item.reviewsets.item.microsoftgraphsecurityexport.ExportPostRequestBody exportPostRequestBody = new com.microsoft.graph.security.cases.ediscoverycases.item.reviewsets.item.microsoftgraphsecurityexport.ExportPostRequestBody();
exportPostRequestBody.setOutputName("Export via API");
exportPostRequestBody.setDescription("Export for the Contoso investigation");
exportPostRequestBody.setExportOptions(EnumSet.of(com.microsoft.graph.models.security.ExportOptions.OriginalFiles, com.microsoft.graph.models.security.ExportOptions.Tags));
exportPostRequestBody.setExportStructure(com.microsoft.graph.models.security.ExportFileStructure.Directory);
graphClient.security().cases().ediscoveryCases().byEdiscoveryCaseId("{ediscoveryCase-id}").reviewSets().byEdiscoveryReviewSetId("{ediscoveryReviewSet-id}").microsoftGraphSecurityExport().post(exportPostRequestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const _export = {
    outputName: 'Export via API',
    description: 'Export for the Contoso investigation',
    exportOptions: 'originalFiles,tags',
    exportStructure: 'directory'
};

await client.api('/security/cases/ediscoveryCases/58399dff-cebe-478f-b1af-d3227f1fd645/reviewSets/273f11a1-17aa-419c-981d-ff10d33e420f/export')
	.post(_export);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Security\Cases\EdiscoveryCases\Item\ReviewSets\Item\MicrosoftGraphSecurityExport\ExportPostRequestBody;
use Microsoft\Graph\Generated\Models\Security\ExportOptions;
use Microsoft\Graph\Generated\Models\Security\ExportFileStructure;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new ExportPostRequestBody();
$requestBody->setOutputName('Export via API');
$requestBody->setDescription('Export for the Contoso investigation');
$requestBody->setExportOptions(new ExportOptions('originalFiles,tags'));
$requestBody->setExportStructure(new ExportFileStructure('directory'));

$graphServiceClient->security()->cases()->ediscoveryCases()->byEdiscoveryCaseId('ediscoveryCase-id')->reviewSets()->byEdiscoveryReviewSetId('ediscoveryReviewSet-id')->microsoftGraphSecurityExport()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Security

$params = @{
	outputName = "Export via API"
	description = "Export for the Contoso investigation"
	exportOptions = "originalFiles,tags"
	exportStructure = "directory"
}

Export-MgSecurityCaseEdiscoveryCaseReviewSet -EdiscoveryCaseId $ediscoveryCaseId -EdiscoveryReviewSetId $ediscoveryReviewSetId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.security.cases.ediscoverycases.item.reviewsets.item.microsoft_graph_security_export.export_post_request_body import ExportPostRequestBody
from msgraph.generated.models.export_options import ExportOptions
from msgraph.generated.models.export_file_structure import ExportFileStructure
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = ExportPostRequestBody(
	output_name = "Export via API",
	description = "Export for the Contoso investigation",
	export_options = ExportOptions.OriginalFiles | ExportOptions.Tags,
	export_structure = ExportFileStructure.Directory,
)

await graph_client.security.cases.ediscovery_cases.by_ediscovery_case_id('ediscoveryCase-id').review_sets.by_ediscovery_review_set_id('ediscoveryReviewSet-id').microsoft_graph_security_export.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

```http
HTTP/1.1 202 Accepted
cache-control: no-cache,
client-request-id: 3ec98906-7187-927e-5203-2ed4533175c6,
location: https://graph.microsoft.com/v1.0/compliance/ediscovery/cases('5b840b94-f821-4c4a-8cad-3a90062bf51a')/operations('2ad2da7c7dbb404abfbbb28b7b6babd6'),
request-id: 9e6b9230-113c-49de-8f7d-ecb90d35b0de
```
