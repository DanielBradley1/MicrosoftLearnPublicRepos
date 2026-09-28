<!-- Source: https://learn.microsoft.com/en-us/graph/api/printdocument-createuploadsession?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-04-05 -->

# printDocument: createUploadSession

Namespace: microsoft.graph

Create an upload session that allows an app to iteratively upload ranges of a binary file linked to the print document.

As part of the response, this action returns an upload URL that can be used in subsequent sequential `PUT` queries. Request headers for each `PUT` operation can be used to specify the exact range of bytes to be uploaded. This allows transfer to be resumed, in case the network connection is dropped during upload.

> **Note**: Creating an upload session using application permissions will only succeed if there is a [printTask](https://learn.microsoft.com/en-us/graph/api/resources/printtask?view=graph-rest-1.0) in a `processing` state on the associated print job, started by a trigger that the requesting app created. For details about how to register a task trigger, see [Extending Universal Print to support pull printing](https://learn.microsoft.com/en-us/graph/universal-print-concept-overview#extending-universal-print-to-support-pull-printing).

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | PrintJob.Create | PrintJob.ReadWrite, PrintJob.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | PrintJob.ReadWrite.All | Not available. |

## HTTP request

To create an upload session using **printer**:

```http
POST /print/printers/{id}/jobs/{id}/documents/{id}/createUploadSession
```

To create an upload session using **printerShare** \(supported with delegated permissions only\):

```http
POST /print/shares/{id}/jobs/{id}/documents/{id}/createUploadSession
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, provide a JSON object with the following parameters.

| Parameter | Type | Description |
| :--- | :--- | :--- |
| properties | [printDocumentUploadProperties](https://learn.microsoft.com/en-us/graph/api/resources/printdocumentuploadproperties?view=graph-rest-1.0) | Represents properties of the binary file to be uploaded. |

The value of the **contentType** property in the request body should be supported by the printer/printerShare. You can get the supported content types by getting [printerCapabilities](https://learn.microsoft.com/en-us/graph/api/resources/printercapabilities?view=graph-rest-1.0) of the printer/printerShare.

For **OXPS to PDF** conversion, you need to pass `application/oxps` as contentType for printer/printerShare that supports `application/pdf`. Universal Print converts **OXPS to PDF**, when **all** the following conditions are met:

1. The printer/printer share supports `application/pdf` in **printerCapabilities**.
2. The printer/printer share doesn't support `application/oxps` in **printerCapabilities**.
3. The value for the **contentType** property in the request body is `application/oxps`.

## Response

If successful, this method returns a `200 OK` response code and a new [uploadSession](https://learn.microsoft.com/en-us/graph/api/resources/uploadsession?view=graph-rest-1.0) object in the response body.

> **Note**: The **uploadUrl** property returned as part of the **uploadSession** response object is an opaque URL for subsequent `PUT` queries to upload byte ranges of the file. It contains the appropriate auth token for subsequent `PUT` queries that expire by **expirationDateTime**. Don't change this URL.

## Examples

The following example shows how to create an upload session that you can use in subsequent file upload operations to the specified printDocument.

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
POST https://graph.microsoft.com/v1.0/print/printers/{printerId}/jobs/{printJobId}/documents/{printDocumentId}/createUploadSession
Content-Type: application/json

{
  "properties": {
    "documentName": "TestFile.pdf",
    "contentType": "application/pdf", 
    "size": 4533322
  }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Print.Printers.Item.Jobs.Item.Documents.Item.CreateUploadSession;
using Microsoft.Graph.Models;

var requestBody = new CreateUploadSessionPostRequestBody
{
	Properties = new PrintDocumentUploadProperties
	{
		DocumentName = "TestFile.pdf",
		ContentType = "application/pdf",
		Size = 4533322L,
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Print.Printers["{printer-id}"].Jobs["{printJob-id}"].Documents["{printDocument-id}"].CreateUploadSession.PostAsync(requestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphprint "github.com/microsoftgraph/msgraph-sdk-go/print"
	  graphmodels "github.com/microsoftgraph/msgraph-sdk-go/models"
	  //other-imports
)

requestBody := graphprint.NewCreateUploadSessionPostRequestBody()
properties := graphmodels.NewPrintDocumentUploadProperties()
documentName := "TestFile.pdf"
properties.SetDocumentName(&documentName) 
contentType := "application/pdf"
properties.SetContentType(&contentType) 
size := int64(4533322)
properties.SetSize(&size) 
requestBody.SetProperties(properties)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
createUploadSession, err := graphClient.Print().Printers().ByPrinterId("printer-id").Jobs().ByPrintJobId("printJob-id").Documents().ByPrintDocumentId("printDocument-id").CreateUploadSession().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.print.printers.item.jobs.item.documents.item.createuploadsession.CreateUploadSessionPostRequestBody createUploadSessionPostRequestBody = new com.microsoft.graph.print.printers.item.jobs.item.documents.item.createuploadsession.CreateUploadSessionPostRequestBody();
PrintDocumentUploadProperties properties = new PrintDocumentUploadProperties();
properties.setDocumentName("TestFile.pdf");
properties.setContentType("application/pdf");
properties.setSize(4533322L);
createUploadSessionPostRequestBody.setProperties(properties);
var result = graphClient.print().printers().byPrinterId("{printer-id}").jobs().byPrintJobId("{printJob-id}").documents().byPrintDocumentId("{printDocument-id}").createUploadSession().post(createUploadSessionPostRequestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const uploadSession = {
  properties: {
    documentName: 'TestFile.pdf',
    contentType: 'application/pdf', 
    size: 4533322
  }
};

await client.api('/print/printers/{printerId}/jobs/{printJobId}/documents/{printDocumentId}/createUploadSession')
	.post(uploadSession);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Print\Printers\Item\Jobs\Item\Documents\Item\CreateUploadSession\CreateUploadSessionPostRequestBody;
use Microsoft\Graph\Generated\Models\PrintDocumentUploadProperties;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new CreateUploadSessionPostRequestBody();
$properties = new PrintDocumentUploadProperties();
$properties->setDocumentName('TestFile.pdf');
$properties->setContentType('application/pdf');
$properties->setSize(4533322);
$requestBody->setProperties($properties);

$result = $graphServiceClient->escapedPrint()->printers()->byPrinterId('printer-id')->jobs()->byPrintJobId('printJob-id')->documents()->byPrintDocumentId('printDocument-id')->createUploadSession()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Devices.CloudPrint

$params = @{
	properties = @{
		documentName = "TestFile.pdf"
		contentType = "application/pdf"
		size = 4533322
	}
}

New-MgPrintPrinterJobDocumentUploadSession -PrinterId $printerId -PrintJobId $printJobId -PrintDocumentId $printDocumentId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.print.printers.item.jobs.item.documents.item.create_upload_session.create_upload_session_post_request_body import CreateUploadSessionPostRequestBody
from msgraph.generated.models.print_document_upload_properties import PrintDocumentUploadProperties
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = CreateUploadSessionPostRequestBody(
	properties = PrintDocumentUploadProperties(
		document_name = "TestFile.pdf",
		content_type = "application/pdf",
		size = 4533322,
	),
)

result = await graph_client.print.printers.by_printer_id('printer-id').jobs.by_print_job_id('printJob-id').documents.by_print_document_id('printDocument-id').create_upload_session.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

**Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#microsoft.graph.uploadSession",
    "uploadUrl": "https://print.print.microsoft.com/uploadSessions/5400be13-5a4e-4c20-be70-90c85bfe5d6e?tempauthtoken={token}",
    "expirationDateTime": "2020-10-25T02:19:38.1694207Z",
    "nextExpectedRanges": [
        "0-4533321"
    ]
}
```
