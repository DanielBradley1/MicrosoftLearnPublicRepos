<!-- Source: https://learn.microsoft.com/en-us/graph/api/security-retentionlabel-update?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-05-21 -->

# Update retentionLabel

Namespace: microsoft.graph.security

Update the properties of a [retentionLabel](https://learn.microsoft.com/en-us/graph/api/resources/security-retentionlabel?view=graph-rest-1.0) object.

To update a [disposition review stage](https://learn.microsoft.com/en-us/graph/api/resources/security-dispositionreviewstage?view=graph-rest-1.0), include the **actionAfterRetentionPeriod** property in the request body with one of the possible values specified.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | RecordsManagement.ReadWrite.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Not supported. | Not supported. |

## HTTP request

```http
PATCH /security/labels/retentionLabels/{retentionLabelId}
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply *only* the values for properties to update. Existing properties that aren't included in the request body maintain their previous values or are recalculated based on changes to other property values.

The following table specifies the properties that can be updated.

| Property | Type | Description |
| :--- | :--- | :--- |
| descriptionForAdmins | String | This is an optional property that provides the label information for the admin. |
| descriptionForUsers | String | This is an optional property that provides the label information for the user. |
| dispositionReviewStages | [microsoft.graph.security.dispositionReviewStage](https://learn.microsoft.com/en-us/graph/api/resources/security-dispositionreviewstage?view=graph-rest-1.0) collection | Review stages during which reviewers are notified to determine whether a document must be deleted or retained. |
| retentionDuration | [microsoft.graph.security.retentionDuration](https://learn.microsoft.com/en-us/graph/api/resources/security-retentionduration?view=graph-rest-1.0) | Specifies the number of days to retain the content. |
| defaultRecordBehavior | microsoft.graph.security.defaultRecordBehavior | Specifies the locked or unlocked state of a record label when it is created. The possible values are: `startLocked`, `startUnlocked`, `unknownFutureValue`. |
| labelToBeApplied | String | Specifies the replacement label to be applied automatically after the retention period of the current label ends. |

## Response

If successful, this method returns a `204 No Content` response code.

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
PATCH https://graph.microsoft.com/v1.0/security/labels/retentionLabels/9563a605-e827-4324-a5a9-09efddff1e50
Content-Type: application/json
Content-length: 555

{
  "@odata.type": "#microsoft.graph.security.retentionLabel",
  "retentionDuration": {
    "@odata.type": "microsoft.graph.security.retentionDurationInDays",
    "days": 2555
  },
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models.Security;

var requestBody = new RetentionLabel
{
	OdataType = "#microsoft.graph.security.retentionLabel",
	RetentionDuration = new RetentionDurationInDays
	{
		OdataType = "microsoft.graph.security.retentionDurationInDays",
		Days = 2555,
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Security.Labels.RetentionLabels["{retentionLabel-id}"].PatchAsync(requestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphmodelssecurity "github.com/microsoftgraph/msgraph-sdk-go/models/security"
	  //other-imports
)

requestBody := graphmodelssecurity.NewRetentionLabel()
retentionDuration := graphmodelssecurity.NewRetentionDurationInDays()
days := int32(2555)
retentionDuration.SetDays(&days) 
requestBody.SetRetentionDuration(retentionDuration)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
retentionLabels, err := graphClient.Security().Labels().RetentionLabels().ByRetentionLabelId("retentionLabel-id").Patch(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.models.security.RetentionLabel retentionLabel = new com.microsoft.graph.models.security.RetentionLabel();
retentionLabel.setOdataType("#microsoft.graph.security.retentionLabel");
com.microsoft.graph.models.security.RetentionDurationInDays retentionDuration = new com.microsoft.graph.models.security.RetentionDurationInDays();
retentionDuration.setOdataType("microsoft.graph.security.retentionDurationInDays");
retentionDuration.setDays(2555);
retentionLabel.setRetentionDuration(retentionDuration);
com.microsoft.graph.models.security.RetentionLabel result = graphClient.security().labels().retentionLabels().byRetentionLabelId("{retentionLabel-id}").patch(retentionLabel);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const retentionLabel = {
  '@odata.type': '#microsoft.graph.security.retentionLabel',
  retentionDuration: {
    '@odata.type': 'microsoft.graph.security.retentionDurationInDays',
    days: 2555
  },
};

await client.api('/security/labels/retentionLabels/9563a605-e827-4324-a5a9-09efddff1e50')
	.update(retentionLabel);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\Security\RetentionLabel;
use Microsoft\Graph\Generated\Models\Security\RetentionDurationInDays;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new RetentionLabel();
$requestBody->setOdataType('#microsoft.graph.security.retentionLabel');
$retentionDuration = new RetentionDurationInDays();
$retentionDuration->setOdataType('microsoft.graph.security.retentionDurationInDays');
$retentionDuration->setDays(2555);
$requestBody->setRetentionDuration($retentionDuration);

$result = $graphServiceClient->security()->labels()->retentionLabels()->byRetentionLabelId('retentionLabel-id')->patch($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Security

$params = @{
	"@odata.type" = "#microsoft.graph.security.retentionLabel"
	retentionDuration = @{
		"@odata.type" = "microsoft.graph.security.retentionDurationInDays"
		days = 
	}
}

Update-MgSecurityLabelRetentionLabel -RetentionLabelId $retentionLabelId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.security.retention_label import RetentionLabel
from msgraph.generated.models.security.retention_duration_in_days import RetentionDurationInDays
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = RetentionLabel(
	odata_type = "#microsoft.graph.security.retentionLabel",
	retention_duration = RetentionDurationInDays(
		odata_type = "microsoft.graph.security.retentionDurationInDays",
		days = 2555,
	),
)

result = await graph_client.security.labels.retention_labels.by_retention_label_id('retentionLabel-id').patch(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

```http
HTTP/1.1 204 No Content
```
