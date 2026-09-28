<!-- Source: https://learn.microsoft.com/en-us/graph/api/industrydata-sourcesystemdefinition-post?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-04-05 -->

# Create sourceSystemDefinition

Namespace: microsoft.graph.industryData

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Create a new [sourceSystemDefinition](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-sourcesystemdefinition?view=graph-rest-beta) object.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | IndustryData-SourceSystem.ReadWrite.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | IndustryData-SourceSystem.ReadWrite.All | Not available. |

## HTTP request

```http
POST /external/industryData/sourceSystems
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the [microsoft.graph.industryData.sourceSystemDefinition](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-sourcesystemdefinition?view=graph-rest-beta) object.

You can specify the following properties when you create a **sourceSystemDefinition**.

| Property | Type | Description |
| :--- | :--- | :--- |
| displayName | String | The name of the source system. Maximum supported length is 100 characters. Required. |
| userMatchingSettings | [microsoft.graph.industryData.userMatchingSetting](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-usermatchingsetting?view=graph-rest-beta) collection | A collection of user matching settings by [roleGroup](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-rolegroup?view=graph-rest-beta). Optional. |
| vendor | String | The name of the vendor who supplies the source system. Maximum supported length is 100 characters. Optional. |

## Response

If successful, this method returns a `201 Created` response code and a [microsoft.graph.industryData.sourceSystemDefinition](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-sourcesystemdefinition?view=graph-rest-beta) object in the response body.

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
POST https://graph.microsoft.com/beta/external/industryData/sourceSystems
Content-Type: application/json
Content-length: 250

{
  "displayName": "Rostering source",
  "userMatchingSettings": [
    {
      "matchTarget": {
        "code": "userPrincipalName"
      },
      "priorityOrder": 0,
      "roleGroup@odata.bind": "https://graph.microsoft.com/beta/external/industryData/roleGroups/staff",
      "sourceIdentifier": {
        "code": "username"
      }
    },
    {
      "matchTarget": {
        "code": "userPrincipalName"
      },
      "priorityOrder": 1,
      "roleGroup@odata.bind": "https://graph.microsoft.com/beta/external/industryData/roleGroups('students')",
      "sourceIdentifier": {
        "code": "username"
      }
    }
  ]
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.Models.IndustryData;

var requestBody = new SourceSystemDefinition
{
	DisplayName = "Rostering source",
	UserMatchingSettings = new List<UserMatchingSetting>
	{
		new UserMatchingSetting
		{
			MatchTarget = new UserMatchTargetReferenceValue
			{
				Code = "userPrincipalName",
			},
			PriorityOrder = 0,
			SourceIdentifier = new IdentifierTypeReferenceValue
			{
				Code = "username",
			},
			AdditionalData = new Dictionary<string, object>
			{
				{
					"roleGroup@odata.bind" , "https://graph.microsoft.com/beta/external/industryData/roleGroups/staff"
				},
			},
		},
		new UserMatchingSetting
		{
			MatchTarget = new UserMatchTargetReferenceValue
			{
				Code = "userPrincipalName",
			},
			PriorityOrder = 1,
			SourceIdentifier = new IdentifierTypeReferenceValue
			{
				Code = "username",
			},
			AdditionalData = new Dictionary<string, object>
			{
				{
					"roleGroup@odata.bind" , "https://graph.microsoft.com/beta/external/industryData/roleGroups('students')"
				},
			},
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.External.IndustryData.SourceSystems.PostAsync(requestBody);
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
	  graphmodelsindustrydata "github.com/microsoftgraph/msgraph-beta-sdk-go/models/industrydata"
	  //other-imports
)

requestBody := graphmodelsindustrydata.NewSourceSystemDefinition()
displayName := "Rostering source"
requestBody.SetDisplayName(&displayName) 


userMatchingSetting := graphmodelsindustrydata.NewUserMatchingSetting()
matchTarget := graphmodelsindustrydata.NewUserMatchTargetReferenceValue()
code := "userPrincipalName"
matchTarget.SetCode(&code) 
userMatchingSetting.SetMatchTarget(matchTarget)
priorityOrder := int32(0)
userMatchingSetting.SetPriorityOrder(&priorityOrder) 
sourceIdentifier := graphmodelsindustrydata.NewIdentifierTypeReferenceValue()
code := "username"
sourceIdentifier.SetCode(&code) 
userMatchingSetting.SetSourceIdentifier(sourceIdentifier)
additionalData := map[string]interface{}{
	"roleGroup@odata.bind" : "https://graph.microsoft.com/beta/external/industryData/roleGroups/staff", 
}
userMatchingSetting.SetAdditionalData(additionalData)
userMatchingSetting1 := graphmodelsindustrydata.NewUserMatchingSetting()
matchTarget := graphmodelsindustrydata.NewUserMatchTargetReferenceValue()
code := "userPrincipalName"
matchTarget.SetCode(&code) 
userMatchingSetting1.SetMatchTarget(matchTarget)
priorityOrder := int32(1)
userMatchingSetting1.SetPriorityOrder(&priorityOrder) 
sourceIdentifier := graphmodelsindustrydata.NewIdentifierTypeReferenceValue()
code := "username"
sourceIdentifier.SetCode(&code) 
userMatchingSetting1.SetSourceIdentifier(sourceIdentifier)
additionalData := map[string]interface{}{
	"roleGroup@odata.bind" : "https://graph.microsoft.com/beta/external/industryData/roleGroups('students')", 
}
userMatchingSetting1.SetAdditionalData(additionalData)

userMatchingSettings := []graphmodelsindustrydata.UserMatchingSettingable {
	userMatchingSetting,
	userMatchingSetting1,
}
requestBody.SetUserMatchingSettings(userMatchingSettings)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
sourceSystems, err := graphClient.External().IndustryData().SourceSystems().Post(context.Background(), requestBody, nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.beta.models.industrydata.SourceSystemDefinition sourceSystemDefinition = new com.microsoft.graph.beta.models.industrydata.SourceSystemDefinition();
sourceSystemDefinition.setDisplayName("Rostering source");
LinkedList<com.microsoft.graph.beta.models.industrydata.UserMatchingSetting> userMatchingSettings = new LinkedList<com.microsoft.graph.beta.models.industrydata.UserMatchingSetting>();
com.microsoft.graph.beta.models.industrydata.UserMatchingSetting userMatchingSetting = new com.microsoft.graph.beta.models.industrydata.UserMatchingSetting();
com.microsoft.graph.beta.models.industrydata.UserMatchTargetReferenceValue matchTarget = new com.microsoft.graph.beta.models.industrydata.UserMatchTargetReferenceValue();
matchTarget.setCode("userPrincipalName");
userMatchingSetting.setMatchTarget(matchTarget);
userMatchingSetting.setPriorityOrder(0);
com.microsoft.graph.beta.models.industrydata.IdentifierTypeReferenceValue sourceIdentifier = new com.microsoft.graph.beta.models.industrydata.IdentifierTypeReferenceValue();
sourceIdentifier.setCode("username");
userMatchingSetting.setSourceIdentifier(sourceIdentifier);
HashMap<String, Object> additionalData = new HashMap<String, Object>();
additionalData.put("roleGroup@odata.bind", "https://graph.microsoft.com/beta/external/industryData/roleGroups/staff");
userMatchingSetting.setAdditionalData(additionalData);
userMatchingSettings.add(userMatchingSetting);
com.microsoft.graph.beta.models.industrydata.UserMatchingSetting userMatchingSetting1 = new com.microsoft.graph.beta.models.industrydata.UserMatchingSetting();
com.microsoft.graph.beta.models.industrydata.UserMatchTargetReferenceValue matchTarget1 = new com.microsoft.graph.beta.models.industrydata.UserMatchTargetReferenceValue();
matchTarget1.setCode("userPrincipalName");
userMatchingSetting1.setMatchTarget(matchTarget1);
userMatchingSetting1.setPriorityOrder(1);
com.microsoft.graph.beta.models.industrydata.IdentifierTypeReferenceValue sourceIdentifier1 = new com.microsoft.graph.beta.models.industrydata.IdentifierTypeReferenceValue();
sourceIdentifier1.setCode("username");
userMatchingSetting1.setSourceIdentifier(sourceIdentifier1);
HashMap<String, Object> additionalData1 = new HashMap<String, Object>();
additionalData1.put("roleGroup@odata.bind", "https://graph.microsoft.com/beta/external/industryData/roleGroups('students')");
userMatchingSetting1.setAdditionalData(additionalData1);
userMatchingSettings.add(userMatchingSetting1);
sourceSystemDefinition.setUserMatchingSettings(userMatchingSettings);
com.microsoft.graph.models.industrydata.SourceSystemDefinition result = graphClient.external().industryData().sourceSystems().post(sourceSystemDefinition);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const sourceSystemDefinition = {
  displayName: 'Rostering source',
  userMatchingSettings: [
    {
      matchTarget: {
        code: 'userPrincipalName'
      },
      priorityOrder: 0,
      'roleGroup@odata.bind': 'https://graph.microsoft.com/beta/external/industryData/roleGroups/staff',
      sourceIdentifier: {
        code: 'username'
      }
    },
    {
      matchTarget: {
        code: 'userPrincipalName'
      },
      priorityOrder: 1,
      'roleGroup@odata.bind': 'https://graph.microsoft.com/beta/external/industryData/roleGroups(\'students\')',
      sourceIdentifier: {
        code: 'username'
      }
    }
  ]
};

await client.api('/external/industryData/sourceSystems')
	.version('beta')
	.post(sourceSystemDefinition);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Models\IndustryData\SourceSystemDefinition;
use Microsoft\Graph\Beta\Generated\Models\IndustryData\UserMatchingSetting;
use Microsoft\Graph\Beta\Generated\Models\IndustryData\UserMatchTargetReferenceValue;
use Microsoft\Graph\Beta\Generated\Models\IndustryData\IdentifierTypeReferenceValue;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new SourceSystemDefinition();
$requestBody->setDisplayName('Rostering source');
$userMatchingSettingsUserMatchingSetting1 = new UserMatchingSetting();
$userMatchingSettingsUserMatchingSetting1MatchTarget = new UserMatchTargetReferenceValue();
$userMatchingSettingsUserMatchingSetting1MatchTarget->setCode('userPrincipalName');
$userMatchingSettingsUserMatchingSetting1->setMatchTarget($userMatchingSettingsUserMatchingSetting1MatchTarget);
$userMatchingSettingsUserMatchingSetting1->setPriorityOrder(0);
$userMatchingSettingsUserMatchingSetting1SourceIdentifier = new IdentifierTypeReferenceValue();
$userMatchingSettingsUserMatchingSetting1SourceIdentifier->setCode('username');
$userMatchingSettingsUserMatchingSetting1->setSourceIdentifier($userMatchingSettingsUserMatchingSetting1SourceIdentifier);
$additionalData = [
	'roleGroup@odata.bind' => 'https://graph.microsoft.com/beta/external/industryData/roleGroups/staff',
];
$userMatchingSettingsUserMatchingSetting1->setAdditionalData($additionalData);
$userMatchingSettingsArray []= $userMatchingSettingsUserMatchingSetting1;
$userMatchingSettingsUserMatchingSetting2 = new UserMatchingSetting();
$userMatchingSettingsUserMatchingSetting2MatchTarget = new UserMatchTargetReferenceValue();
$userMatchingSettingsUserMatchingSetting2MatchTarget->setCode('userPrincipalName');
$userMatchingSettingsUserMatchingSetting2->setMatchTarget($userMatchingSettingsUserMatchingSetting2MatchTarget);
$userMatchingSettingsUserMatchingSetting2->setPriorityOrder(1);
$userMatchingSettingsUserMatchingSetting2SourceIdentifier = new IdentifierTypeReferenceValue();
$userMatchingSettingsUserMatchingSetting2SourceIdentifier->setCode('username');
$userMatchingSettingsUserMatchingSetting2->setSourceIdentifier($userMatchingSettingsUserMatchingSetting2SourceIdentifier);
$additionalData = [
	'roleGroup@odata.bind' => 'https://graph.microsoft.com/beta/external/industryData/roleGroups(\'students\')',
];
$userMatchingSettingsUserMatchingSetting2->setAdditionalData($additionalData);
$userMatchingSettingsArray []= $userMatchingSettingsUserMatchingSetting2;
$requestBody->setUserMatchingSettings($userMatchingSettingsArray);


$result = $graphServiceClient->external()->industryData()->sourceSystems()->post($requestBody)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Beta.Search

$params = @{
	displayName = "Rostering source"
	userMatchingSettings = @(
		@{
			matchTarget = @{
				code = "userPrincipalName"
			}
			priorityOrder = 0
			"roleGroup@odata.bind" = "https://graph.microsoft.com/beta/external/industryData/roleGroups/staff"
			sourceIdentifier = @{
				code = "username"
			}
		}
		@{
			matchTarget = @{
				code = "userPrincipalName"
			}
			priorityOrder = 1
			"roleGroup@odata.bind" = "https://graph.microsoft.com/beta/external/industryData/roleGroups('students')"
			sourceIdentifier = @{
				code = "username"
			}
		}
	)
}

New-MgBetaExternalIndustryDataSourceSystem -BodyParameter $params
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.models.industry_data.source_system_definition import SourceSystemDefinition
from msgraph_beta.generated.models.industry_data.user_matching_setting import UserMatchingSetting
from msgraph_beta.generated.models.industry_data.user_match_target_reference_value import UserMatchTargetReferenceValue
from msgraph_beta.generated.models.industry_data.identifier_type_reference_value import IdentifierTypeReferenceValue
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = SourceSystemDefinition(
	display_name = "Rostering source",
	user_matching_settings = [
		UserMatchingSetting(
			match_target = UserMatchTargetReferenceValue(
				code = "userPrincipalName",
			),
			priority_order = 0,
			source_identifier = IdentifierTypeReferenceValue(
				code = "username",
			),
			additional_data = {
					"role_group@odata_bind" : "https://graph.microsoft.com/beta/external/industryData/roleGroups/staff",
			}
		),
		UserMatchingSetting(
			match_target = UserMatchTargetReferenceValue(
				code = "userPrincipalName",
			),
			priority_order = 1,
			source_identifier = IdentifierTypeReferenceValue(
				code = "username",
			),
			additional_data = {
					"role_group@odata_bind" : "https://graph.microsoft.com/beta/external/industryData/roleGroups('students')",
			}
		),
	],
)

result = await graph_client.external.industry_data.source_systems.post(request_body)
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
    "@odata.context": "https://graph.microsoft.com/beta/$metadata#external/industryData/sourceSystems/$entity",
    "id": "aa050107-5784-4a8e-1876-08daddab21bc",
    "displayName": "Rostering source",
    "vendor": null,
    "userMatchingSettings": [
        {
            "priorityOrder": 0,
            "sourceIdentifier": {
                "code": "username"
            },
            "matchTarget": {
                "code": "userPrincipalName"
            }
        },
        {
            "priorityOrder": 1,
            "sourceIdentifier": {
                "code": "username"
            },
            "matchTarget": {
                "code": "userPrincipalName"
            }
        }
    ]
}
```
