<!-- Source: https://learn.microsoft.com/en-us/graph/api/windowsupdates-updatepolicy-post-compliancechanges-contentapproval?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-01-29 -->

# Create contentApproval

Namespace: microsoft.graph.windowsUpdates

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Create a new [contentApproval](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-contentapproval?view=graph-rest-beta) object.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | WindowsUpdates.ReadWrite.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | WindowsUpdates.ReadWrite.All | Not available. |

Important

For delegated access using work or school accounts, the signed-in user must be an owner or member of the group or be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) or a custom role that grants the permissions required for this operation. *Intune Administrator*, or *Windows Update Deployment Administrator* are the least privileged roles supported for this operation.

## HTTP request

```http
POST /admin/windows/updates/updatePolicies/{updatePolicyId}/complianceChanges
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the [contentApproval](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-contentapproval?view=graph-rest-beta) object.

You can specify the following properties when you create a **contentApproval**.

| Property | Type | Description |
| :--- | :--- | :--- |
| content | [microsoft.graph.windowsUpdates.deployableContent](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-deployablecontent?view=graph-rest-beta) | Specifies what content to deploy. Deployable content should be provided as one of the following derived types: [microsoft.graph.windowsUpdates.catalogContent](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-catalogcontent?view=graph-rest-beta). |
| deploymentSettings | [microsoft.graph.windowsUpdates.deploymentSettings](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-deploymentsettings?view=graph-rest-beta) | Settings for governing how to deploy **content**. |

## Response

If successful, this method returns a `200 OK` response code and an updated [microsoft.graph.windowsUpdates.contentApproval](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-contentapproval?view=graph-rest-beta) object in the response body.

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
POST https://graph.microsoft.com/beta/admin/windows/updates/updatePolicies/a7aa99c1-34a2-850c-5223-7816fde70713/complianceChanges
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.windowsUpdates.contentApproval",
  "content": {
    "@odata.type": "#microsoft.graph.windowsUpdates.catalogContent",
    "catalogEntry": {
      "@odata.type": "#microsoft.graph.windowsUpdates.featureUpdateCatalogEntry", 
      "id": "6b7e60db-a8e4-426a-9aed-bd12b5c0b9d4"
    }
  },
  "deploymentSettings": {},
    "schedule": {
      "startDateTime": "String (timestamp)",
      "gradualRollout": {
        "@odata.type": "#microsoft.graph.windowsUpdates.dateDrivenRolloutSettings",
        "endDateTime": "String (timestamp)"
      }
   }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.Models.WindowsUpdates;
using Microsoft.Kiota.Abstractions.Serialization;

var requestBody = new ContentApproval
{
	OdataType = "#microsoft.graph.windowsUpdates.contentApproval",
	Content = new CatalogContent
	{
		OdataType = "#microsoft.graph.windowsUpdates.catalogContent",
		CatalogEntry = new FeatureUpdateCatalogEntry
		{
			OdataType = "#microsoft.graph.windowsUpdates.featureUpdateCatalogEntry",
			Id = "6b7e60db-a8e4-426a-9aed-bd12b5c0b9d4",
		},
	},
	DeploymentSettings = new DeploymentSettings
	{
	},
	AdditionalData = new Dictionary<string, object>
	{
		{
			"schedule" , new UntypedObject(new Dictionary<string, UntypedNode>
			{
				{
					"startDateTime", new UntypedString("String (timestamp)")
				},
				{
					"gradualRollout", new UntypedObject(new Dictionary<string, UntypedNode>
					{
						{
							"@odata.type", new UntypedString("#microsoft.graph.windowsUpdates.dateDrivenRolloutSettings")
						},
						{
							"endDateTime", new UntypedString("String (timestamp)")
						},
					})
				},
			})
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Admin.Windows.Updates.UpdatePolicies["{updatePolicy-id}"].ComplianceChanges.PostAsync(requestBody);
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
	  graphmodelswindowsupdates "github.com/microsoftgraph/msgraph-beta-sdk-go/models/windowsupdates"
	  //other-imports
)

requestBody := graphmodelswindowsupdates.NewComplianceChange()
content := graphmodelswindowsupdates.NewCatalogContent()
catalogEntry := graphmodelswindowsupdates.NewFeatureUpdateCatalogEntry()
id := "6b7e60db-a8e4-426a-9aed-bd12b5c0b9d4"
catalogEntry.SetId(&id) 
content.SetCatalogEntry(catalogEntry)
requestBody.SetContent(content)
deploymentSettings := graphmodelswindowsupdates.NewDeploymentSettings()
requestBody.SetDeploymentSettings(deploymentSettings)
additionalData := map[string]interface{}{
schedule := graph.New()
startDateTime := "String (timestamp)"
schedule.SetStartDateTime(&startDateTime) 
gradualRollout := graph.New()
endDateTime := "String (timestamp)"
gradualRollout.SetEndDateTime(&endDateTime) 
	schedule.SetGradualRollout(gradualRollout)
	requestBody.SetSchedule(schedule)
}
requestBody.SetAdditionalData(additionalData)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
complianceChanges, err := graphClient.Admin().Windows().Updates().UpdatePolicies().ByUpdatePolicyId("updatePolicy-id").ComplianceChanges().Post(context.Background(), requestBody, nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.beta.models.windowsupdates.ContentApproval complianceChange = new com.microsoft.graph.beta.models.windowsupdates.ContentApproval();
complianceChange.setOdataType("#microsoft.graph.windowsUpdates.contentApproval");
com.microsoft.graph.beta.models.windowsupdates.CatalogContent content = new com.microsoft.graph.beta.models.windowsupdates.CatalogContent();
content.setOdataType("#microsoft.graph.windowsUpdates.catalogContent");
com.microsoft.graph.beta.models.windowsupdates.FeatureUpdateCatalogEntry catalogEntry = new com.microsoft.graph.beta.models.windowsupdates.FeatureUpdateCatalogEntry();
catalogEntry.setOdataType("#microsoft.graph.windowsUpdates.featureUpdateCatalogEntry");
catalogEntry.setId("6b7e60db-a8e4-426a-9aed-bd12b5c0b9d4");
content.setCatalogEntry(catalogEntry);
complianceChange.setContent(content);
com.microsoft.graph.beta.models.windowsupdates.DeploymentSettings deploymentSettings = new com.microsoft.graph.beta.models.windowsupdates.DeploymentSettings();
complianceChange.setDeploymentSettings(deploymentSettings);
HashMap<String, Object> additionalData = new HashMap<String, Object>();
 schedule = new ();
schedule.setStartDateTime("String (timestamp)");
 gradualRollout = new ();
gradualRollout.setOdataType("#microsoft.graph.windowsUpdates.dateDrivenRolloutSettings");
gradualRollout.setEndDateTime("String (timestamp)");
schedule.setGradualRollout(gradualRollout);
additionalData.put("schedule", schedule);
complianceChange.setAdditionalData(additionalData);
com.microsoft.graph.models.windowsupdates.ComplianceChange result = graphClient.admin().windows().updates().updatePolicies().byUpdatePolicyId("{updatePolicy-id}").complianceChanges().post(complianceChange);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const complianceChange = {
  '@odata.type': '#microsoft.graph.windowsUpdates.contentApproval',
  content: {
    '@odata.type': '#microsoft.graph.windowsUpdates.catalogContent',
    catalogEntry: {
      '@odata.type': '#microsoft.graph.windowsUpdates.featureUpdateCatalogEntry', 
      id: '6b7e60db-a8e4-426a-9aed-bd12b5c0b9d4'
    }
  },
  deploymentSettings: {},
    schedule: {
      startDateTime: 'String (timestamp)',
      gradualRollout: {
        '@odata.type': '#microsoft.graph.windowsUpdates.dateDrivenRolloutSettings',
        endDateTime: 'String (timestamp)'
      }
   }
};

await client.api('/admin/windows/updates/updatePolicies/a7aa99c1-34a2-850c-5223-7816fde70713/complianceChanges')
	.version('beta')
	.post(complianceChange);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Models\WindowsUpdates\ContentApproval;
use Microsoft\Graph\Beta\Generated\Models\WindowsUpdates\CatalogContent;
use Microsoft\Graph\Beta\Generated\Models\WindowsUpdates\FeatureUpdateCatalogEntry;
use Microsoft\Graph\Beta\Generated\Models\WindowsUpdates\DeploymentSettings;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new ContentApproval();
$requestBody->setOdataType('#microsoft.graph.windowsUpdates.contentApproval');
$content = new CatalogContent();
$content->setOdataType('#microsoft.graph.windowsUpdates.catalogContent');
$contentCatalogEntry = new FeatureUpdateCatalogEntry();
$contentCatalogEntry->setOdataType('#microsoft.graph.windowsUpdates.featureUpdateCatalogEntry');
$contentCatalogEntry->setId('6b7e60db-a8e4-426a-9aed-bd12b5c0b9d4');
$content->setCatalogEntry($contentCatalogEntry);
$requestBody->setContent($content);
$deploymentSettings = new DeploymentSettings();
$requestBody->setDeploymentSettings($deploymentSettings);
$additionalData = [
	'schedule' => [
		'startDateTime' => 'String (timestamp)',
		'gradualRollout' => [
			'@odata.type' => '#microsoft.graph.windowsUpdates.dateDrivenRolloutSettings',
			'endDateTime' => 'String (timestamp)',
		],
	],
];
$requestBody->setAdditionalData($additionalData);

$result = $graphServiceClient->admin()->windows()->updates()->updatePolicies()->byUpdatePolicyId('updatePolicy-id')->complianceChanges()->post($requestBody)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Beta.WindowsUpdates

$params = @{
	"@odata.type" = "#microsoft.graph.windowsUpdates.contentApproval"
	content = @{
		"@odata.type" = "#microsoft.graph.windowsUpdates.catalogContent"
		catalogEntry = @{
			"@odata.type" = "#microsoft.graph.windowsUpdates.featureUpdateCatalogEntry"
			id = "6b7e60db-a8e4-426a-9aed-bd12b5c0b9d4"
		}
	}
	deploymentSettings = @{
	}
	schedule = @{
		startDateTime = "String (timestamp)"
		gradualRollout = @{
			"@odata.type" = "#microsoft.graph.windowsUpdates.dateDrivenRolloutSettings"
			endDateTime = "String (timestamp)"
		}
	}
}

New-MgBetaWindowsUpdatesPolicyComplianceChange -UpdatePolicyId $updatePolicyId -BodyParameter $params
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.models.windows_updates.content_approval import ContentApproval
from msgraph_beta.generated.models.windows_updates.catalog_content import CatalogContent
from msgraph_beta.generated.models.windows_updates.feature_update_catalog_entry import FeatureUpdateCatalogEntry
from msgraph_beta.generated.models.windows_updates.deployment_settings import DeploymentSettings
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = ContentApproval(
	odata_type = "#microsoft.graph.windowsUpdates.contentApproval",
	content = CatalogContent(
		odata_type = "#microsoft.graph.windowsUpdates.catalogContent",
		catalog_entry = FeatureUpdateCatalogEntry(
			odata_type = "#microsoft.graph.windowsUpdates.featureUpdateCatalogEntry",
			id = "6b7e60db-a8e4-426a-9aed-bd12b5c0b9d4",
		),
	),
	deployment_settings = DeploymentSettings(
	),
	additional_data = {
			"schedule" : {
					"start_date_time" : "String (timestamp)",
					"gradual_rollout" : {
							"@odata_type" : "#microsoft.graph.windowsUpdates.dateDrivenRolloutSettings",
							"end_date_time" : "String (timestamp)",
					},
			},
	}
)

result = await graph_client.admin.windows.updates.update_policies.by_update_policy_id('updatePolicy-id').compliance_changes.post(request_body)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-Type: application/json

{
    "@odata.type": "#microsoft.graph.windowsUpdates.contentApproval",
    "id": "6b73d038-68bc-4f0b-8b94-72a26f1e879d",
    "createdDateTime": "String (timestamp)",
    "isRevoked": false,
    "revokedDateTime": "String (timestamp)",
    "content": {
        "@odata.type": "#microsoft.graph.windowsUpdates.catalogContent"
    },
    "deploymentSettings": {
        "schedule": null,
        "monitoring": null,
        "contentApplicability": null,
        "userExperience": null,
        "expedite": null
    }
}
```
