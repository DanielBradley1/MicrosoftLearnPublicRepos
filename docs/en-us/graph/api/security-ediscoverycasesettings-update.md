<!-- Source: https://learn.microsoft.com/en-us/graph/api/security-ediscoverycasesettings-update?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-01-29 -->

# Update ediscoveryCaseSettings

Namespace: microsoft.graph.security

Update the properties of an [ediscoveryCaseSettings](https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoverycasesettings?view=graph-rest-1.0) object.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | eDiscovery.ReadWrite.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | eDiscovery.ReadWrite.All | Not available. |

Important

For delegated access using work or school accounts, the signed-in user must be assigned a supported [Microsoft Purview role](https://learn.microsoft.com/en-us/purview/edisc-permissions) through one of the following options:

- **eDiscovery Manager**. Allows members to create and manage eDiscovery cases they create, including creating custodians, holds, searches, and other case management tasks. However, eDiscovery Managers can only create and manage the cases they create. **This is the least privileged option for managing their own cases**.
- **eDiscovery Administrator**. Provides all the permissions of eDiscovery Manager, plus the ability to access and manage all eDiscovery cases in the organization, configure eDiscovery settings, and manage any case after adding themselves as a member.

Additional roles that provide write access to eDiscovery features:

- **Compliance Administrator**. Includes Case Management, Compliance Search, and Hold permissions.
- **Organization Management**. Includes Case Management, Compliance Search, Hold, and Search And Purge permissions.

The eDiscovery Manager and eDiscovery Administrator roles are part of the Microsoft Purview role groups and provide access to eDiscovery features through [role-based access control \(RBAC\)](https://learn.microsoft.com/en-us/purview/edisc-permissions#rbac-roles-related-to-ediscovery).

For more information about eDiscovery permissions and roles, see [Assign permissions in eDiscovery](https://learn.microsoft.com/en-us/purview/edisc-permissions).

## HTTP request

```http
PATCH /security/cases/ediscoveryCases/{ediscoveryCaseId}/settings
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

| Property | Type | Description |
| :--- | :--- | :--- |
| caseType | [microsoft.graph.security.caseType](https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoverycasesettings?view=graph-rest-1.0#casetype-values) | The type of the eDiscovery case. The possible values are: `standard`, `premium`, `unknownFutureValue`. |
| ocr | [microsoft.graph.security.ocrSettings](https://learn.microsoft.com/en-us/graph/api/resources/security-ocrsettings?view=graph-rest-1.0) | The OCR \(Optical Character Recognition\) settings for the eDiscovery case. Optional. |
| redundancyDetection | [microsoft.graph.security.redundancyDetectionSettings](https://learn.microsoft.com/en-us/graph/api/resources/security-redundancydetectionsettings?view=graph-rest-1.0) | Redundancy \(email threading and near duplicate detection\) settings for an eDiscovery case. Optional. |
| reviewSetSettings | [microsoft.graph.security.reviewSetSettings](https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoverycasesettings?view=graph-rest-1.0#reviewsetsettings-values) | The settings of the review set for the case. The possible values are: `none`, `disableGrouping`, `unknownFutureValue`. |
| topicModeling | [microsoft.graph.security.topicModelingSettings](https://learn.microsoft.com/en-us/graph/api/resources/security-topicmodelingsettings?view=graph-rest-1.0) | Topic modeling \(Themes\) settings for an eDiscovery case. Optional. |

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
PATCH https://graph.microsoft.com/v1.0/security/cases/ediscoveryCases/b0073e4e-4184-41c6-9eb7-8c8cc3e2288b/settings
Content-Type: application/json

{
    "@odata.type": "https://graph.microsoft.com/v1.0/$metadata#security/cases/ediscoveryCases('b0073e4e-4184-41c6-9eb7-8c8cc3e2288b')/settings/$entity",
    "redundancyDetection": {
        "isEnabled": true,
        "similarityThreshold": 65,
        "minWords": 10,
        "maxWords": 500000
    },
    "topicModeling": {
        "isEnabled": false,
        "ignoreNumbers": true,
        "topicCount": 100,
        "dynamicallyAdjustTopicCount": true
    },
    "ocr": {
        "isEnabled": false,
        "maxImageSize": 24576,
        "timeout": "PT1M"
    },
    "caseType": "standard",
    "reviewSetSettings": "disableGrouping"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models.Security;

var requestBody = new EdiscoveryCaseSettings
{
	OdataType = "https://graph.microsoft.com/v1.0/$metadata#security/cases/ediscoveryCases('b0073e4e-4184-41c6-9eb7-8c8cc3e2288b')/settings/$entity",
	RedundancyDetection = new RedundancyDetectionSettings
	{
		IsEnabled = true,
		SimilarityThreshold = 65,
		MinWords = 10,
		MaxWords = 500000,
	},
	TopicModeling = new TopicModelingSettings
	{
		IsEnabled = false,
		IgnoreNumbers = true,
		TopicCount = 100,
		DynamicallyAdjustTopicCount = true,
	},
	Ocr = new OcrSettings
	{
		IsEnabled = false,
		MaxImageSize = 24576,
		Timeout = TimeSpan.Parse("PT1M"),
	},
	CaseType = CaseType.Standard,
	ReviewSetSettings = ReviewSetSettings.DisableGrouping,
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Security.Cases.EdiscoveryCases["{ediscoveryCase-id}"].Settings.PatchAsync(requestBody);
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

requestBody := graphmodelssecurity.NewEdiscoveryCaseSettings()
redundancyDetection := graphmodelssecurity.NewRedundancyDetectionSettings()
isEnabled := true
redundancyDetection.SetIsEnabled(&isEnabled) 
similarityThreshold := int32(65)
redundancyDetection.SetSimilarityThreshold(&similarityThreshold) 
minWords := int32(10)
redundancyDetection.SetMinWords(&minWords) 
maxWords := int32(500000)
redundancyDetection.SetMaxWords(&maxWords) 
requestBody.SetRedundancyDetection(redundancyDetection)
topicModeling := graphmodelssecurity.NewTopicModelingSettings()
isEnabled := false
topicModeling.SetIsEnabled(&isEnabled) 
ignoreNumbers := true
topicModeling.SetIgnoreNumbers(&ignoreNumbers) 
topicCount := int32(100)
topicModeling.SetTopicCount(&topicCount) 
dynamicallyAdjustTopicCount := true
topicModeling.SetDynamicallyAdjustTopicCount(&dynamicallyAdjustTopicCount) 
requestBody.SetTopicModeling(topicModeling)
ocr := graphmodelssecurity.NewOcrSettings()
isEnabled := false
ocr.SetIsEnabled(&isEnabled) 
maxImageSize := int32(24576)
ocr.SetMaxImageSize(&maxImageSize) 
timeout , err := abstractions.ParseISODuration("PT1M")
ocr.SetTimeout(&timeout) 
requestBody.SetOcr(ocr)
caseType := graphmodels.STANDARD_CASETYPE 
requestBody.SetCaseType(&caseType) 
reviewSetSettings := graphmodels.DISABLEGROUPING_REVIEWSETSETTINGS 
requestBody.SetReviewSetSettings(&reviewSetSettings) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
settings, err := graphClient.Security().Cases().EdiscoveryCases().ByEdiscoveryCaseId("ediscoveryCase-id").Settings().Patch(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.models.security.EdiscoveryCaseSettings ediscoveryCaseSettings = new com.microsoft.graph.models.security.EdiscoveryCaseSettings();
ediscoveryCaseSettings.setOdataType("https://graph.microsoft.com/v1.0/$metadata#security/cases/ediscoveryCases('b0073e4e-4184-41c6-9eb7-8c8cc3e2288b')/settings/$entity");
com.microsoft.graph.models.security.RedundancyDetectionSettings redundancyDetection = new com.microsoft.graph.models.security.RedundancyDetectionSettings();
redundancyDetection.setIsEnabled(true);
redundancyDetection.setSimilarityThreshold(65);
redundancyDetection.setMinWords(10);
redundancyDetection.setMaxWords(500000);
ediscoveryCaseSettings.setRedundancyDetection(redundancyDetection);
com.microsoft.graph.models.security.TopicModelingSettings topicModeling = new com.microsoft.graph.models.security.TopicModelingSettings();
topicModeling.setIsEnabled(false);
topicModeling.setIgnoreNumbers(true);
topicModeling.setTopicCount(100);
topicModeling.setDynamicallyAdjustTopicCount(true);
ediscoveryCaseSettings.setTopicModeling(topicModeling);
com.microsoft.graph.models.security.OcrSettings ocr = new com.microsoft.graph.models.security.OcrSettings();
ocr.setIsEnabled(false);
ocr.setMaxImageSize(24576);
PeriodAndDuration timeout = PeriodAndDuration.ofDuration(Duration.parse("PT1M"));
ocr.setTimeout(timeout);
ediscoveryCaseSettings.setOcr(ocr);
ediscoveryCaseSettings.setCaseType(com.microsoft.graph.models.security.CaseType.Standard);
ediscoveryCaseSettings.setReviewSetSettings(EnumSet.of(com.microsoft.graph.models.security.ReviewSetSettings.DisableGrouping));
com.microsoft.graph.models.security.EdiscoveryCaseSettings result = graphClient.security().cases().ediscoveryCases().byEdiscoveryCaseId("{ediscoveryCase-id}").settings().patch(ediscoveryCaseSettings);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const ediscoveryCaseSettings = {
    '@odata.type': 'https://graph.microsoft.com/v1.0/$metadata#security/cases/ediscoveryCases(\'b0073e4e-4184-41c6-9eb7-8c8cc3e2288b\')/settings/$entity',
    redundancyDetection: {
        isEnabled: true,
        similarityThreshold: 65,
        minWords: 10,
        maxWords: 500000
    },
    topicModeling: {
        isEnabled: false,
        ignoreNumbers: true,
        topicCount: 100,
        dynamicallyAdjustTopicCount: true
    },
    ocr: {
        isEnabled: false,
        maxImageSize: 24576,
        timeout: 'PT1M'
    },
    caseType: 'standard',
    reviewSetSettings: 'disableGrouping'
};

await client.api('/security/cases/ediscoveryCases/b0073e4e-4184-41c6-9eb7-8c8cc3e2288b/settings')
	.update(ediscoveryCaseSettings);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\Security\EdiscoveryCaseSettings;
use Microsoft\Graph\Generated\Models\Security\RedundancyDetectionSettings;
use Microsoft\Graph\Generated\Models\Security\TopicModelingSettings;
use Microsoft\Graph\Generated\Models\Security\OcrSettings;
use Microsoft\Graph\Generated\Models\Security\CaseType;
use Microsoft\Graph\Generated\Models\Security\ReviewSetSettings;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new EdiscoveryCaseSettings();
$requestBody->setOdataType('https://graph.microsoft.com/v1.0/$metadata#security/cases/ediscoveryCases(\'b0073e4e-4184-41c6-9eb7-8c8cc3e2288b\')/settings/$entity');
$redundancyDetection = new RedundancyDetectionSettings();
$redundancyDetection->setIsEnabled(true);
$redundancyDetection->setSimilarityThreshold(65);
$redundancyDetection->setMinWords(10);
$redundancyDetection->setMaxWords(500000);
$requestBody->setRedundancyDetection($redundancyDetection);
$topicModeling = new TopicModelingSettings();
$topicModeling->setIsEnabled(false);
$topicModeling->setIgnoreNumbers(true);
$topicModeling->setTopicCount(100);
$topicModeling->setDynamicallyAdjustTopicCount(true);
$requestBody->setTopicModeling($topicModeling);
$ocr = new OcrSettings();
$ocr->setIsEnabled(false);
$ocr->setMaxImageSize(24576);
$ocr->setTimeout(new \DateInterval('PT1M'));
$requestBody->setOcr($ocr);
$requestBody->setCaseType(new CaseType('standard'));
$requestBody->setReviewSetSettings(new ReviewSetSettings('disableGrouping'));

$result = $graphServiceClient->security()->cases()->ediscoveryCases()->byEdiscoveryCaseId('ediscoveryCase-id')->settings()->patch($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Security

$params = @{
	"@odata.type" = "https://graph.microsoft.com/v1.0/$metadata#security/cases/ediscoveryCases('b0073e4e-4184-41c6-9eb7-8c8cc3e2288b')/settings/$entity"
	redundancyDetection = @{
		isEnabled = $true
		similarityThreshold = 65
		minWords = 10
		maxWords = 500000
	}
	topicModeling = @{
		isEnabled = $false
		ignoreNumbers = $true
		topicCount = 100
		dynamicallyAdjustTopicCount = $true
	}
	ocr = @{
		isEnabled = $false
		maxImageSize = 24576
		timeout = "PT1M"
	}
	caseType = "standard"
	reviewSetSettings = "disableGrouping"
}

Update-MgSecurityCaseEdiscoveryCaseSetting -EdiscoveryCaseId $ediscoveryCaseId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.security.ediscovery_case_settings import EdiscoveryCaseSettings
from msgraph.generated.models.security.redundancy_detection_settings import RedundancyDetectionSettings
from msgraph.generated.models.security.topic_modeling_settings import TopicModelingSettings
from msgraph.generated.models.security.ocr_settings import OcrSettings
from msgraph.generated.models.case_type import CaseType
from msgraph.generated.models.review_set_settings import ReviewSetSettings
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = EdiscoveryCaseSettings(
	odata_type = "https://graph.microsoft.com/v1.0/$metadata#security/cases/ediscoveryCases('b0073e4e-4184-41c6-9eb7-8c8cc3e2288b')/settings/$entity",
	redundancy_detection = RedundancyDetectionSettings(
		is_enabled = True,
		similarity_threshold = 65,
		min_words = 10,
		max_words = 500000,
	),
	topic_modeling = TopicModelingSettings(
		is_enabled = False,
		ignore_numbers = True,
		topic_count = 100,
		dynamically_adjust_topic_count = True,
	),
	ocr = OcrSettings(
		is_enabled = False,
		max_image_size = 24576,
		timeout = "PT1M",
	),
	case_type = CaseType.Standard,
	review_set_settings = ReviewSetSettings.DisableGrouping,
)

result = await graph_client.security.cases.ediscovery_cases.by_ediscovery_case_id('ediscoveryCase-id').settings.patch(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

```http
HTTP/1.1 204 No Content
```
