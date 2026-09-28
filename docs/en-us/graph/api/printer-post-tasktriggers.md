<!-- Source: https://learn.microsoft.com/en-us/graph/api/printer-post-tasktriggers?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-23 -->

# Create printTaskTrigger

Namespace: microsoft.graph

Create a new [task trigger](https://learn.microsoft.com/en-us/graph/api/resources/printtasktrigger?view=graph-rest-1.0) on the specified [printer](https://learn.microsoft.com/en-us/graph/api/resources/printer?view=graph-rest-1.0). Currently, only **one** task trigger can be specified per printer, but this limit might be removed in the future.

> **Note:** The appId used to generate an access token for creating a task trigger should be the same appId that was used to create the corresponding task definition.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Printer.ReadWrite.All | Printer.FullControl.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Not supported. | Not supported. |

## HTTP request

```http
POST /print/printers/{printerId}/taskTriggers
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of a [printTaskTrigger](https://learn.microsoft.com/en-us/graph/api/resources/printtasktrigger?view=graph-rest-1.0) object. Supply a reference to a [printTaskDefinition](https://learn.microsoft.com/en-us/graph/api/resources/printtaskdefinition?view=graph-rest-1.0) by using the `@odata.bind` format, as shown in the following example.

## Response

If successful, this method returns a `201 Created` response code and a [printTaskTrigger](https://learn.microsoft.com/en-us/graph/api/resources/printtasktrigger?view=graph-rest-1.0) in the response body.

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
POST https://graph.microsoft.com/v1.0/print/printers/{printerId}/taskTriggers
Content-Type: application/json

{
  "event": "jobStarted",
  "definition@odata.bind": "https://graph.microsoft.com/v1.0/print/taskDefinitions/{taskDefinitionId}"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new PrintTaskTrigger
{
	Event = PrintEvent.JobStarted,
	AdditionalData = new Dictionary<string, object>
	{
		{
			"definition@odata.bind" , "https://graph.microsoft.com/v1.0/print/taskDefinitions/{taskDefinitionId}"
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Print.Printers["{printer-id}"].TaskTriggers.PostAsync(requestBody);
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

requestBody := graphmodels.NewPrintTaskTrigger()
event := graphmodels.JOBSTARTED_PRINTEVENT 
requestBody.SetEvent(&event) 
additionalData := map[string]interface{}{
	"definition@odata.bind" : "https://graph.microsoft.com/v1.0/print/taskDefinitions/{taskDefinitionId}", 
}
requestBody.SetAdditionalData(additionalData)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
taskTriggers, err := graphClient.Print().Printers().ByPrinterId("printer-id").TaskTriggers().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

PrintTaskTrigger printTaskTrigger = new PrintTaskTrigger();
printTaskTrigger.setEvent(PrintEvent.JobStarted);
HashMap<String, Object> additionalData = new HashMap<String, Object>();
additionalData.put("definition@odata.bind", "https://graph.microsoft.com/v1.0/print/taskDefinitions/{taskDefinitionId}");
printTaskTrigger.setAdditionalData(additionalData);
PrintTaskTrigger result = graphClient.print().printers().byPrinterId("{printer-id}").taskTriggers().post(printTaskTrigger);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const printTaskTrigger = {
  event: 'jobStarted',
  'definition@odata.bind': 'https://graph.microsoft.com/v1.0/print/taskDefinitions/{taskDefinitionId}'
};

await client.api('/print/printers/{printerId}/taskTriggers')
	.post(printTaskTrigger);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\PrintTaskTrigger;
use Microsoft\Graph\Generated\Models\PrintEvent;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new PrintTaskTrigger();
$requestBody->setEvent(new PrintEvent('jobStarted'));
$additionalData = [
	'definition@odata.bind' => 'https://graph.microsoft.com/v1.0/print/taskDefinitions/{taskDefinitionId}',
];
$requestBody->setAdditionalData($additionalData);

$result = $graphServiceClient->escapedPrint()->printers()->byPrinterId('printer-id')->taskTriggers()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Devices.CloudPrint

$params = @{
	event = "jobStarted"
	"definition@odata.bind" = "https://graph.microsoft.com/v1.0/print/taskDefinitions/{taskDefinitionId}"
}

New-MgPrintPrinterTaskTrigger -PrinterId $printerId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.print_task_trigger import PrintTaskTrigger
from msgraph.generated.models.print_event import PrintEvent
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = PrintTaskTrigger(
	event = PrintEvent.JobStarted,
	additional_data = {
			"definition@odata_bind" : "https://graph.microsoft.com/v1.0/print/taskDefinitions/{taskDefinitionId}",
	}
)

result = await graph_client.print.printers.by_printer_id('printer-id').task_triggers.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-Type: application/json

{
  "@odata.context": "https://graph.print.microsoft.com/v1.0/$metadata#Collection(Microsoft.Graph.PrintTaskTrigger)",
  "id": "b6a843ca-e60e-4e20-a222-a58d85eead6d",
  "event": "jobStarted"
}
```
