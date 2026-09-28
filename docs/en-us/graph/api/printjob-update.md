<!-- Source: https://learn.microsoft.com/en-us/graph/api/printjob-update?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-23 -->

# Update printJob

Namespace: microsoft.graph

Update a [print job](https://learn.microsoft.com/en-us/graph/api/resources/printjob?view=graph-rest-1.0). Only the **configuration** property can be updated.

Updating a print job will only succeed if there is a [printTask](https://learn.microsoft.com/en-us/graph/api/resources/printtask?view=graph-rest-1.0) in a `processing` state on the associated print job, started by a trigger that the requesting app created. For details about how to register a task trigger, see [Extending Universal Print to support pull printing](https://learn.microsoft.com/en-us/graph/universal-print-concept-overview#extending-universal-print-to-support-pull-printing).

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Not supported. | Not supported. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | PrintJob.ReadWriteBasic.All | PrintJob.Manage.All, PrintJob.ReadWrite.All |

## HTTP request

```http
PATCH /print/printers/{printerId}/jobs/{printJobId}
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply the values of the relevant [printJob](https://learn.microsoft.com/en-us/graph/api/resources/printjob?view=graph-rest-1.0) fields. Existing properties that are not included in the request body will maintain their previous values.

Only the **configuration** property can be updated.

## Response

If successful, this method returns a `200 OK` response code with an updated [printJob](https://learn.microsoft.com/en-us/graph/api/resources/printjob?view=graph-rest-1.0) object in the response body.

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
PATCH https://graph.microsoft.com/v1.0/print/printers/{printerId}/jobs/{printJobId}
Content-Type: application/json

{
  "configuration": {
    "feedOrientation": "longEdgeFirst",
    "pageRanges": [
      {
        "start": 1,
        "end": 1
      }
    ],
    "quality": "medium",
    "dpi": 600,
    "orientation": "landscape",
    "copies": 1,
    "duplexMode": "oneSided",
    "colorMode": "blackAndWhite",
    "inputBin": "by-pass-tray",
    "outputBin": "output-tray",
    "mediaSize": "A4",
    "margin": {
      "top": 0,
      "bottom": 0,
      "left": 0,
      "right": 0
    },
    "mediaType": "stationery",
    "finishings": null,
    "pagesPerSheet": 1,
    "multipageLayout": "clockwiseFromBottomLeft",
    "collate": false,
    "scaling": "shrinkToFit",
    "fitPdfToPage": false
  }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new PrintJob
{
	Configuration = new PrintJobConfiguration
	{
		FeedOrientation = PrinterFeedOrientation.LongEdgeFirst,
		PageRanges = new List<IntegerRange>
		{
			new IntegerRange
			{
				Start = 1L,
				End = 1L,
			},
		},
		Quality = PrintQuality.Medium,
		Dpi = 600,
		Orientation = PrintOrientation.Landscape,
		Copies = 1,
		DuplexMode = PrintDuplexMode.OneSided,
		ColorMode = PrintColorMode.BlackAndWhite,
		InputBin = "by-pass-tray",
		OutputBin = "output-tray",
		MediaSize = "A4",
		Margin = new PrintMargin
		{
			Top = 0,
			Bottom = 0,
			Left = 0,
			Right = 0,
		},
		MediaType = "stationery",
		Finishings = null,
		PagesPerSheet = 1,
		MultipageLayout = PrintMultipageLayout.ClockwiseFromBottomLeft,
		Collate = false,
		Scaling = PrintScaling.ShrinkToFit,
		FitPdfToPage = false,
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Print.Printers["{printer-id}"].Jobs["{printJob-id}"].PatchAsync(requestBody);
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

requestBody := graphmodels.NewPrintJob()
configuration := graphmodels.NewPrintJobConfiguration()
feedOrientation := graphmodels.LONGEDGEFIRST_PRINTERFEEDORIENTATION 
configuration.SetFeedOrientation(&feedOrientation) 


integerRange := graphmodels.NewIntegerRange()
start := int64(1)
integerRange.SetStart(&start) 
end := int64(1)
integerRange.SetEnd(&end) 

pageRanges := []graphmodels.IntegerRangeable {
	integerRange,
}
configuration.SetPageRanges(pageRanges)
quality := graphmodels.MEDIUM_PRINTQUALITY 
configuration.SetQuality(&quality) 
dpi := int32(600)
configuration.SetDpi(&dpi) 
orientation := graphmodels.LANDSCAPE_PRINTORIENTATION 
configuration.SetOrientation(&orientation) 
copies := int32(1)
configuration.SetCopies(&copies) 
duplexMode := graphmodels.ONESIDED_PRINTDUPLEXMODE 
configuration.SetDuplexMode(&duplexMode) 
colorMode := graphmodels.BLACKANDWHITE_PRINTCOLORMODE 
configuration.SetColorMode(&colorMode) 
inputBin := "by-pass-tray"
configuration.SetInputBin(&inputBin) 
outputBin := "output-tray"
configuration.SetOutputBin(&outputBin) 
mediaSize := "A4"
configuration.SetMediaSize(&mediaSize) 
margin := graphmodels.NewPrintMargin()
top := int32(0)
margin.SetTop(&top) 
bottom := int32(0)
margin.SetBottom(&bottom) 
left := int32(0)
margin.SetLeft(&left) 
right := int32(0)
margin.SetRight(&right) 
configuration.SetMargin(margin)
mediaType := "stationery"
configuration.SetMediaType(&mediaType) 
finishings := null
configuration.SetFinishings(&finishings) 
pagesPerSheet := int32(1)
configuration.SetPagesPerSheet(&pagesPerSheet) 
multipageLayout := graphmodels.CLOCKWISEFROMBOTTOMLEFT_PRINTMULTIPAGELAYOUT 
configuration.SetMultipageLayout(&multipageLayout) 
collate := false
configuration.SetCollate(&collate) 
scaling := graphmodels.SHRINKTOFIT_PRINTSCALING 
configuration.SetScaling(&scaling) 
fitPdfToPage := false
configuration.SetFitPdfToPage(&fitPdfToPage) 
requestBody.SetConfiguration(configuration)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
jobs, err := graphClient.Print().Printers().ByPrinterId("printer-id").Jobs().ByPrintJobId("printJob-id").Patch(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

PrintJob printJob = new PrintJob();
PrintJobConfiguration configuration = new PrintJobConfiguration();
configuration.setFeedOrientation(PrinterFeedOrientation.LongEdgeFirst);
LinkedList<IntegerRange> pageRanges = new LinkedList<IntegerRange>();
IntegerRange integerRange = new IntegerRange();
integerRange.setStart(1L);
integerRange.setEnd(1L);
pageRanges.add(integerRange);
configuration.setPageRanges(pageRanges);
configuration.setQuality(PrintQuality.Medium);
configuration.setDpi(600);
configuration.setOrientation(PrintOrientation.Landscape);
configuration.setCopies(1);
configuration.setDuplexMode(PrintDuplexMode.OneSided);
configuration.setColorMode(PrintColorMode.BlackAndWhite);
configuration.setInputBin("by-pass-tray");
configuration.setOutputBin("output-tray");
configuration.setMediaSize("A4");
PrintMargin margin = new PrintMargin();
margin.setTop(0);
margin.setBottom(0);
margin.setLeft(0);
margin.setRight(0);
configuration.setMargin(margin);
configuration.setMediaType("stationery");
configuration.setFinishings(null);
configuration.setPagesPerSheet(1);
configuration.setMultipageLayout(PrintMultipageLayout.ClockwiseFromBottomLeft);
configuration.setCollate(false);
configuration.setScaling(PrintScaling.ShrinkToFit);
configuration.setFitPdfToPage(false);
printJob.setConfiguration(configuration);
PrintJob result = graphClient.print().printers().byPrinterId("{printer-id}").jobs().byPrintJobId("{printJob-id}").patch(printJob);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const printJob = {
  configuration: {
    feedOrientation: 'longEdgeFirst',
    pageRanges: [
      {
        start: 1,
        end: 1
      }
    ],
    quality: 'medium',
    dpi: 600,
    orientation: 'landscape',
    copies: 1,
    duplexMode: 'oneSided',
    colorMode: 'blackAndWhite',
    inputBin: 'by-pass-tray',
    outputBin: 'output-tray',
    mediaSize: 'A4',
    margin: {
      top: 0,
      bottom: 0,
      left: 0,
      right: 0
    },
    mediaType: 'stationery',
    finishings: null,
    pagesPerSheet: 1,
    multipageLayout: 'clockwiseFromBottomLeft',
    collate: false,
    scaling: 'shrinkToFit',
    fitPdfToPage: false
  }
};

await client.api('/print/printers/{printerId}/jobs/{printJobId}')
	.update(printJob);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\PrintJob;
use Microsoft\Graph\Generated\Models\PrintJobConfiguration;
use Microsoft\Graph\Generated\Models\PrinterFeedOrientation;
use Microsoft\Graph\Generated\Models\IntegerRange;
use Microsoft\Graph\Generated\Models\PrintQuality;
use Microsoft\Graph\Generated\Models\PrintOrientation;
use Microsoft\Graph\Generated\Models\PrintDuplexMode;
use Microsoft\Graph\Generated\Models\PrintColorMode;
use Microsoft\Graph\Generated\Models\PrintMargin;
use Microsoft\Graph\Generated\Models\PrintMultipageLayout;
use Microsoft\Graph\Generated\Models\PrintScaling;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new PrintJob();
$configuration = new PrintJobConfiguration();
$configuration->setFeedOrientation(new PrinterFeedOrientation('longEdgeFirst'));
$pageRangesIntegerRange1 = new IntegerRange();
$pageRangesIntegerRange1->setStart(1);
$pageRangesIntegerRange1->setEnd(1);
$pageRangesArray []= $pageRangesIntegerRange1;
$configuration->setPageRanges($pageRangesArray);

$configuration->setQuality(new PrintQuality('medium'));
$configuration->setDpi(600);
$configuration->setOrientation(new PrintOrientation('landscape'));
$configuration->setCopies(1);
$configuration->setDuplexMode(new PrintDuplexMode('oneSided'));
$configuration->setColorMode(new PrintColorMode('blackAndWhite'));
$configuration->setInputBin('by-pass-tray');
$configuration->setOutputBin('output-tray');
$configuration->setMediaSize('A4');
$configurationMargin = new PrintMargin();
$configurationMargin->setTop(0);
$configurationMargin->setBottom(0);
$configurationMargin->setLeft(0);
$configurationMargin->setRight(0);
$configuration->setMargin($configurationMargin);
$configuration->setMediaType('stationery');
$configuration->setFinishings(null);
$configuration->setPagesPerSheet(1);
$configuration->setMultipageLayout(new PrintMultipageLayout('clockwiseFromBottomLeft'));
$configuration->setCollate(false);
$configuration->setScaling(new PrintScaling('shrinkToFit'));
$configuration->setFitPdfToPage(false);
$requestBody->setConfiguration($configuration);

$result = $graphServiceClient->escapedPrint()->printers()->byPrinterId('printer-id')->jobs()->byPrintJobId('printJob-id')->patch($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Devices.CloudPrint

$params = @{
	configuration = @{
		feedOrientation = "longEdgeFirst"
		pageRanges = @(
			@{
				start = 1
				end = 1
			}
		)
		quality = "medium"
		dpi = 600
		orientation = "landscape"
		copies = 1
		duplexMode = "oneSided"
		colorMode = "blackAndWhite"
		inputBin = "by-pass-tray"
		outputBin = "output-tray"
		mediaSize = "A4"
		margin = @{
			top = 0
			bottom = 0
			left = 0
			right = 0
		}
		mediaType = "stationery"
		finishings = $null
		pagesPerSheet = 1
		multipageLayout = "clockwiseFromBottomLeft"
		collate = $false
		scaling = "shrinkToFit"
		fitPdfToPage = $false
	}
}

Update-MgPrintPrinterJob -PrinterId $printerId -PrintJobId $printJobId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.print_job import PrintJob
from msgraph.generated.models.print_job_configuration import PrintJobConfiguration
from msgraph.generated.models.printer_feed_orientation import PrinterFeedOrientation
from msgraph.generated.models.integer_range import IntegerRange
from msgraph.generated.models.print_quality import PrintQuality
from msgraph.generated.models.print_orientation import PrintOrientation
from msgraph.generated.models.print_duplex_mode import PrintDuplexMode
from msgraph.generated.models.print_color_mode import PrintColorMode
from msgraph.generated.models.print_margin import PrintMargin
from msgraph.generated.models.print_multipage_layout import PrintMultipageLayout
from msgraph.generated.models.print_scaling import PrintScaling
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = PrintJob(
	configuration = PrintJobConfiguration(
		feed_orientation = PrinterFeedOrientation.LongEdgeFirst,
		page_ranges = [
			IntegerRange(
				start = 1,
				end = 1,
			),
		],
		quality = PrintQuality.Medium,
		dpi = 600,
		orientation = PrintOrientation.Landscape,
		copies = 1,
		duplex_mode = PrintDuplexMode.OneSided,
		color_mode = PrintColorMode.BlackAndWhite,
		input_bin = "by-pass-tray",
		output_bin = "output-tray",
		media_size = "A4",
		margin = PrintMargin(
			top = 0,
			bottom = 0,
			left = 0,
			right = 0,
		),
		media_type = "stationery",
		finishings = None,
		pages_per_sheet = 1,
		multipage_layout = PrintMultipageLayout.ClockwiseFromBottomLeft,
		collate = False,
		scaling = PrintScaling.ShrinkToFit,
		fit_pdf_to_page = False,
	),
)

result = await graph_client.print.printers.by_printer_id('printer-id').jobs.by_print_job_id('printJob-id').patch(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

**Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#print/printers('d5ef6ec4-07ca-4212-baf9-d45be126bfbb')/jobs/$entity",
  "id": "44353",
  "createdDateTime": "2020-06-26T04:20:06.5715544Z",
  "createdBy": {
    "id": "",
    "displayName": "",
    "userPrincipalName": ""
  },
  "status": {
    "state": "paused",
    "description": "The job is not a candidate for processing yet."
  },
  "configuration": {
    "feedOrientation": "longEdgeFirst",
    "pageRanges": [
      {
        "start": 1,
        "end": 1
      }
    ],
    "quality": "medium",
    "dpi": 600,
    "orientation": "landscape",
    "copies": 1,
    "duplexMode": "oneSided",
    "colorMode": "blackAndWhite",
    "inputBin": "by-pass-tray",
    "outputBin": "output-tray",
    "mediaSize": "A4",
    "margin": {
      "top": 0,
      "bottom": 0,
      "left": 0,
      "right": 0
    },
    "mediaType": "stationery",
    "finishings": null,
    "pagesPerSheet": 1,
    "multipageLayout": "clockwiseFromBottomLeft",
    "collate": false,
    "scaling": "shrinkToFit",
    "fitPdfToPage": false
  }
}
```
