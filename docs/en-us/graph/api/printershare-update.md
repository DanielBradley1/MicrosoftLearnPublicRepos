<!-- Source: https://learn.microsoft.com/en-us/graph/api/printershare-update?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-06-07 -->

# Update printerShare

Namespace: microsoft.graph

Update the properties of a printer share. This method can be used to swap [printers](https://learn.microsoft.com/en-us/graph/api/resources/printer?view=graph-rest-1.0).

For example, if a physical printer device breaks, an administrator can register a new [printer](https://learn.microsoft.com/en-us/graph/api/resources/printer?view=graph-rest-1.0) device and update this [printerShare](https://learn.microsoft.com/en-us/graph/api/resources/printershare?view=graph-rest-1.0) to point to the new printer without requiring users to take any action.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | PrinterShare.ReadWrite.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Not supported. | Not supported. |

## HTTP request

```http
PATCH /print/shares/{printerShareId}
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply the values for relevant [printerShare](https://learn.microsoft.com/en-us/graph/api/resources/printershare?view=graph-rest-1.0) fields that should be updated. Existing properties that aren't included in the request body maintains their previous values or be recalculated based on changes to other property values. For best performance, don't include existing values that haven't changed.

Following properties can be updated:

| Property | Type | Description |
| :--- | :--- | :--- |
| printer | microsoft.graph.printer | The printer that this printer share is related to. Use the `printer@odata.bind` syntax as shown in the following example to update which printer this printer share is associated with. |
| displayName | String | The name of the printer share that print clients should display. |
| allowAllUsers | Boolean | If true, all users and groups are granted access to this printer share. This supersedes the allowlists defined by the allowedUsers and allowedGroups navigation properties. |

Note

If you're updating the **printer** property, other properties can't be updated in the same request.

## Response

If successful, this method returns a `200 OK` response code and an updated [printerShare](https://learn.microsoft.com/en-us/graph/api/resources/printershare?view=graph-rest-1.0) object in the response body.

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
PATCH https://graph.microsoft.com/v1.0/print/shares/{printerShareId}
Content-Type: application/json

{
  "displayName": "PrinterShare Name",
  "printer@odata.bind": "https://graph.microsoft.com/v1.0/print/printers/{printerId}",
  "allowAllUsers": false
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new PrinterShare
{
	DisplayName = "PrinterShare Name",
	AllowAllUsers = false,
	AdditionalData = new Dictionary<string, object>
	{
		{
			"printer@odata.bind" , "https://graph.microsoft.com/v1.0/print/printers/{printerId}"
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Print.Shares["{printerShare-id}"].PatchAsync(requestBody);
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

requestBody := graphmodels.NewPrinterShare()
displayName := "PrinterShare Name"
requestBody.SetDisplayName(&displayName) 
allowAllUsers := false
requestBody.SetAllowAllUsers(&allowAllUsers) 
additionalData := map[string]interface{}{
	"printer@odata.bind" : "https://graph.microsoft.com/v1.0/print/printers/{printerId}", 
}
requestBody.SetAdditionalData(additionalData)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
shares, err := graphClient.Print().Shares().ByPrinterShareId("printerShare-id").Patch(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

PrinterShare printerShare = new PrinterShare();
printerShare.setDisplayName("PrinterShare Name");
printerShare.setAllowAllUsers(false);
HashMap<String, Object> additionalData = new HashMap<String, Object>();
additionalData.put("printer@odata.bind", "https://graph.microsoft.com/v1.0/print/printers/{printerId}");
printerShare.setAdditionalData(additionalData);
PrinterShare result = graphClient.print().shares().byPrinterShareId("{printerShare-id}").patch(printerShare);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const printerShare = {
  displayName: 'PrinterShare Name',
  'printer@odata.bind': 'https://graph.microsoft.com/v1.0/print/printers/{printerId}',
  allowAllUsers: false
};

await client.api('/print/shares/{printerShareId}')
	.update(printerShare);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\PrinterShare;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new PrinterShare();
$requestBody->setDisplayName('PrinterShare Name');
$requestBody->setAllowAllUsers(false);
$additionalData = [
	'printer@odata.bind' => 'https://graph.microsoft.com/v1.0/print/printers/{printerId}',
];
$requestBody->setAdditionalData($additionalData);

$result = $graphServiceClient->escapedPrint()->shares()->byPrinterShareId('printerShare-id')->patch($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Devices.CloudPrint

$params = @{
	displayName = "PrinterShare Name"
	"printer@odata.bind" = "https://graph.microsoft.com/v1.0/print/printers/{printerId}"
	allowAllUsers = $false
}

Update-MgPrintShare -PrinterShareId $printerShareId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.printer_share import PrinterShare
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = PrinterShare(
	display_name = "PrinterShare Name",
	allow_all_users = False,
	additional_data = {
			"printer@odata_bind" : "https://graph.microsoft.com/v1.0/print/printers/{printerId}",
	}
)

result = await graph_client.print.shares.by_printer_share_id('printerShare-id').patch(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

**Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#print/shares/$entity",
  "id": "d837c17b-3296-4384-a053-828d56e10f50",
  "displayName": "PrinterShare Name",
  "createdDateTime": "2020-02-04T00:00:00.0000000Z",
  "isAcceptingJobs": true,
  "allowAllUsers": false,
  "status": {
    "state": "stopped",
    "details": ["disconnected"],
    "description": ""
  }
}
```
