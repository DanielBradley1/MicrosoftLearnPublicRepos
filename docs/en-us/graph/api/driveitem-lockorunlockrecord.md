<!-- Source: https://learn.microsoft.com/en-us/graph/api/driveitem-lockorunlockrecord?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-03-21 -->

# driveItem: lockOrUnlockRecord

Namespace: microsoft.graph

Lock or unlock a retention label on a [driveItem](https://learn.microsoft.com/en-us/graph/api/resources/driveitem?view=graph-rest-1.0) that classifies content as records.

For information about retention labels from an administrator's perspective, see [Use retention labels to manage the lifecycle of documents stored in SharePoint](https://learn.microsoft.com/en-us/microsoft-365/compliance/auto-apply-retention-labels-scenario).

For more information about how you can lock and unlock retention labels, see [Use record versioning to update records stored in SharePoint or OneDrive](https://learn.microsoft.com/en-us/microsoft-365/compliance/record-versioning).

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Files.ReadWrite.All | Sites.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Files.ReadWrite.All | Sites.ReadWrite.All |

## HTTP request

```http
PATCH /drives/{drive-id}/items/{item-id}/retentionLabel
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, provide a JSON object with the following parameter.

| Property | Type | Description |
| :--- | :--- | :--- |
| retentionSettings | [retentionLabelSettings](https://learn.microsoft.com/en-us/graph/api/resources/retentionlabelsettings?view=graph-rest-1.0) | The retention settings enforced on the item. |

## Response

If successful, this method returns a `200 OK` response code and an updated [itemRetentionLabel](https://learn.microsoft.com/en-us/graph/api/resources/itemretentionlabel?view=graph-rest-1.0) object in the response body.

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
PATCH https://graph.microsoft.com/v1.0/drives/b!t18F8ybsHUq1z3LTz8xvZqP8zaSWjkFNhsME-Fepo75dTf9vQKfeRblBZjoSQrd7/items/01NKDM7HMOJTVYMDOSXFDK2QJDXCDI3WUK/retentionLabel
Content-Type: application/json

{
  "retentionSettings": {
    "isRecordLocked": true
  }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new ItemRetentionLabel
{
	RetentionSettings = new RetentionLabelSettings
	{
		IsRecordLocked = true,
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Drives["{drive-id}"].Items["{driveItem-id}"].RetentionLabel.PatchAsync(requestBody);
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

requestBody := graphmodels.NewItemRetentionLabel()
retentionSettings := graphmodels.NewRetentionLabelSettings()
isRecordLocked := true
retentionSettings.SetIsRecordLocked(&isRecordLocked) 
requestBody.SetRetentionSettings(retentionSettings)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
retentionLabel, err := graphClient.Drives().ByDriveId("drive-id").Items().ByDriveItemId("driveItem-id").RetentionLabel().Patch(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

ItemRetentionLabel itemRetentionLabel = new ItemRetentionLabel();
RetentionLabelSettings retentionSettings = new RetentionLabelSettings();
retentionSettings.setIsRecordLocked(true);
itemRetentionLabel.setRetentionSettings(retentionSettings);
ItemRetentionLabel result = graphClient.drives().byDriveId("{drive-id}").items().byDriveItemId("{driveItem-id}").retentionLabel().patch(itemRetentionLabel);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const itemRetentionLabel = {
  retentionSettings: {
    isRecordLocked: true
  }
};

await client.api('/drives/b!t18F8ybsHUq1z3LTz8xvZqP8zaSWjkFNhsME-Fepo75dTf9vQKfeRblBZjoSQrd7/items/01NKDM7HMOJTVYMDOSXFDK2QJDXCDI3WUK/retentionLabel')
	.update(itemRetentionLabel);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\ItemRetentionLabel;
use Microsoft\Graph\Generated\Models\RetentionLabelSettings;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new ItemRetentionLabel();
$retentionSettings = new RetentionLabelSettings();
$retentionSettings->setIsRecordLocked(true);
$requestBody->setRetentionSettings($retentionSettings);

$result = $graphServiceClient->drives()->byDriveId('drive-id')->items()->byDriveItemId('driveItem-id')->retentionLabel()->patch($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Files

$params = @{
	retentionSettings = @{
		isRecordLocked = $true
	}
}

Update-MgDriveItemRetentionLabel -DriveId $driveId -DriveItemId $driveItemId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.item_retention_label import ItemRetentionLabel
from msgraph.generated.models.retention_label_settings import RetentionLabelSettings
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = ItemRetentionLabel(
	retention_settings = RetentionLabelSettings(
		is_record_locked = True,
	),
)

result = await graph_client.drives.by_drive_id('drive-id').items.by_drive_item_id('driveItem-id').retention_label.patch(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "name": "Retention label for Contracts",
  "retentionSettings": {
    "behaviorDuringRetentionPeriod": "retain",
    "isDeleteAllowed": false,
    "isRecordLocked": true,
    "isMetadataUpdateAllowed": false,
    "isContentUpdateAllowed": false,
    "isLabelUpdateAllowed": false
  },
  "isLabelAppliedExplicitly": false,
  "labelAppliedDateTime": "2022-12-22T10:18:23.6580555+00:00",
  "labelAppliedBy": {
    "user": {
      "id": "56d171c8-a92e-4359-9c4a-38b88ac7eabd",
      "displayName": "Contoso Admin"
    }
  }
}
```
