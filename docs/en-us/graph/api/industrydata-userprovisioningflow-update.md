<!-- Source: https://learn.microsoft.com/en-us/graph/api/industrydata-userprovisioningflow-update?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-23 -->

# Update userProvisioningFlow

Namespace: microsoft.graph.industryData

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Update the properties of a [userProvisioningFlow](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-userprovisioningflow?view=graph-rest-beta) object.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permission | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | IndustryData-OutboundFlow.ReadWrite.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | IndustryData-OutboundFlow.ReadWrite.All | Not available. |

## HTTP request

```http
PATCH /external/industryData/OutboundProvisioningFlowSets/{id}/provisioningFlows/{id}
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
| createUnmatchedUsers | Boolean | A Boolean choice indicating whether unmatched users should be created or ignored. Optional. |
| creationOptions | [microsoft.graph.industryData.userCreationOptions](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-usercreationoptions?view=graph-rest-beta) | The different management choices for the new users to be provisioned. Optional. |
| managementOptions | [microsoft.graph.industryData.userManagementOptions](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-usermanagementoptions?view=graph-rest-beta) | The different attribute choices for all the users to be considered. Required |

Caution

The **markAllStudentsAsMinors** property of **additionalOptions** under **managementOptions** is deprecated and will stop returning data on October 15, 2025. Going forward, use the **studentAgeGroup** property.

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
PATCH https://graph.microsoft.com/beta/external/industryData/OutboundProvisioningFlowSets/9ab41255-5364-4c53-e15c-08dc4ab6ee03/provisioningFlows/dbd36d16-c574-4ed8-3ac7-08dc4ac6fb7f
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.industryData.userProvisioningFlow",
  "createUnmatchedUsers": true,
  "managementOptions": {
    "additionalAttributes": [
      "userGradeLevel"
    ],
    "additionalOptions": {
      "studentAgeGroup": "minor",
      "allowStudentContactAssociation": true
    }
  },
  "creationOptions": {
    "configurations": [
      {
        "roleGroup@odata.bind": "https://graph.microsoft.com/beta/external/industryData/roleGroups/staff",
        "defaultPasswordSettings": {
          "@odata.type": "#microsoft.graph.industryData.simplePasswordSettings",
          "password": "********"
        },
        "licenseSkus": [
          "SkuUpdated"
        ]
      },
      {
        "roleGroup@odata.bind": "https://graph.microsoft.com/beta/external/industryData/roleGroups/students",
        "defaultPasswordSettings": {
          "@odata.type": "#microsoft.graph.industryData.simplePasswordSettings",
          "password": "********"
        },
        "licenseSkus": [
          "SkuUpdated2"
        ]
      }
    ]
  }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.Models.IndustryData;

var requestBody = new UserProvisioningFlow
{
	OdataType = "#microsoft.graph.industryData.userProvisioningFlow",
	CreateUnmatchedUsers = true,
	ManagementOptions = new UserManagementOptions
	{
		AdditionalAttributes = new List<AdditionalUserAttributes?>
		{
			AdditionalUserAttributes.UserGradeLevel,
		},
		AdditionalOptions = new AdditionalUserOptions
		{
			StudentAgeGroup = StudentAgeGroup.Minor,
			AllowStudentContactAssociation = true,
		},
	},
	CreationOptions = new UserCreationOptions
	{
		Configurations = new List<UserConfiguration>
		{
			new UserConfiguration
			{
				DefaultPasswordSettings = new SimplePasswordSettings
				{
					OdataType = "#microsoft.graph.industryData.simplePasswordSettings",
					Password = "********",
				},
				LicenseSkus = new List<string>
				{
					"SkuUpdated",
				},
				AdditionalData = new Dictionary<string, object>
				{
					{
						"roleGroup@odata.bind" , "https://graph.microsoft.com/beta/external/industryData/roleGroups/staff"
					},
				},
			},
			new UserConfiguration
			{
				DefaultPasswordSettings = new SimplePasswordSettings
				{
					OdataType = "#microsoft.graph.industryData.simplePasswordSettings",
					Password = "********",
				},
				LicenseSkus = new List<string>
				{
					"SkuUpdated2",
				},
				AdditionalData = new Dictionary<string, object>
				{
					{
						"roleGroup@odata.bind" , "https://graph.microsoft.com/beta/external/industryData/roleGroups/students"
					},
				},
			},
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.External.IndustryData.OutboundProvisioningFlowSets["{outboundProvisioningFlowSet-id}"].ProvisioningFlows["{provisioningFlow-id}"].PatchAsync(requestBody);
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

requestBody := graphmodelsindustrydata.NewProvisioningFlow()
createUnmatchedUsers := true
requestBody.SetCreateUnmatchedUsers(&createUnmatchedUsers) 
managementOptions := graphmodelsindustrydata.NewUserManagementOptions()
additionalAttributes := []graphmodelsindustrydata.AdditionalUserAttributesable {
	additionalUserAttributes := graphmodels.USERGRADELEVEL_ADDITIONALUSERATTRIBUTES 
	managementOptions.SetAdditionalUserAttributes(&additionalUserAttributes)
}
managementOptions.SetAdditionalAttributes(additionalAttributes)
additionalOptions := graphmodelsindustrydata.NewAdditionalUserOptions()
studentAgeGroup := graphmodels.MINOR_STUDENTAGEGROUP 
additionalOptions.SetStudentAgeGroup(&studentAgeGroup) 
allowStudentContactAssociation := true
additionalOptions.SetAllowStudentContactAssociation(&allowStudentContactAssociation) 
managementOptions.SetAdditionalOptions(additionalOptions)
requestBody.SetManagementOptions(managementOptions)
creationOptions := graphmodelsindustrydata.NewUserCreationOptions()


userConfiguration := graphmodelsindustrydata.NewUserConfiguration()
defaultPasswordSettings := graphmodelsindustrydata.NewSimplePasswordSettings()
password := "********"
defaultPasswordSettings.SetPassword(&password) 
userConfiguration.SetDefaultPasswordSettings(defaultPasswordSettings)
licenseSkus := []string {
	"SkuUpdated",
}
userConfiguration.SetLicenseSkus(licenseSkus)
additionalData := map[string]interface{}{
	"roleGroup@odata.bind" : "https://graph.microsoft.com/beta/external/industryData/roleGroups/staff", 
}
userConfiguration.SetAdditionalData(additionalData)
userConfiguration1 := graphmodelsindustrydata.NewUserConfiguration()
defaultPasswordSettings := graphmodelsindustrydata.NewSimplePasswordSettings()
password := "********"
defaultPasswordSettings.SetPassword(&password) 
userConfiguration1.SetDefaultPasswordSettings(defaultPasswordSettings)
licenseSkus := []string {
	"SkuUpdated2",
}
userConfiguration1.SetLicenseSkus(licenseSkus)
additionalData := map[string]interface{}{
	"roleGroup@odata.bind" : "https://graph.microsoft.com/beta/external/industryData/roleGroups/students", 
}
userConfiguration1.SetAdditionalData(additionalData)

configurations := []graphmodelsindustrydata.UserConfigurationable {
	userConfiguration,
	userConfiguration1,
}
creationOptions.SetConfigurations(configurations)
requestBody.SetCreationOptions(creationOptions)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
provisioningFlows, err := graphClient.External().IndustryData().OutboundProvisioningFlowSets().ByOutboundProvisioningFlowSetId("outboundProvisioningFlowSet-id").ProvisioningFlows().ByProvisioningFlowId("provisioningFlow-id").Patch(context.Background(), requestBody, nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.beta.models.industrydata.UserProvisioningFlow provisioningFlow = new com.microsoft.graph.beta.models.industrydata.UserProvisioningFlow();
provisioningFlow.setOdataType("#microsoft.graph.industryData.userProvisioningFlow");
provisioningFlow.setCreateUnmatchedUsers(true);
com.microsoft.graph.beta.models.industrydata.UserManagementOptions managementOptions = new com.microsoft.graph.beta.models.industrydata.UserManagementOptions();
LinkedList<com.microsoft.graph.beta.models.industrydata.com.microsoft.graph.beta.models.industrydata.AdditionalUserAttributes> additionalAttributes = new LinkedList<com.microsoft.graph.beta.models.industrydata.com.microsoft.graph.beta.models.industrydata.AdditionalUserAttributes>();
additionalAttributes.add(com.microsoft.graph.beta.models.industrydata.AdditionalUserAttributes.UserGradeLevel);
managementOptions.setAdditionalAttributes(additionalAttributes);
com.microsoft.graph.beta.models.industrydata.AdditionalUserOptions additionalOptions = new com.microsoft.graph.beta.models.industrydata.AdditionalUserOptions();
additionalOptions.setStudentAgeGroup(com.microsoft.graph.beta.models.industrydata.StudentAgeGroup.Minor);
additionalOptions.setAllowStudentContactAssociation(true);
managementOptions.setAdditionalOptions(additionalOptions);
provisioningFlow.setManagementOptions(managementOptions);
com.microsoft.graph.beta.models.industrydata.UserCreationOptions creationOptions = new com.microsoft.graph.beta.models.industrydata.UserCreationOptions();
LinkedList<com.microsoft.graph.beta.models.industrydata.UserConfiguration> configurations = new LinkedList<com.microsoft.graph.beta.models.industrydata.UserConfiguration>();
com.microsoft.graph.beta.models.industrydata.UserConfiguration userConfiguration = new com.microsoft.graph.beta.models.industrydata.UserConfiguration();
com.microsoft.graph.beta.models.industrydata.SimplePasswordSettings defaultPasswordSettings = new com.microsoft.graph.beta.models.industrydata.SimplePasswordSettings();
defaultPasswordSettings.setOdataType("#microsoft.graph.industryData.simplePasswordSettings");
defaultPasswordSettings.setPassword("********");
userConfiguration.setDefaultPasswordSettings(defaultPasswordSettings);
LinkedList<String> licenseSkus = new LinkedList<String>();
licenseSkus.add("SkuUpdated");
userConfiguration.setLicenseSkus(licenseSkus);
HashMap<String, Object> additionalData = new HashMap<String, Object>();
additionalData.put("roleGroup@odata.bind", "https://graph.microsoft.com/beta/external/industryData/roleGroups/staff");
userConfiguration.setAdditionalData(additionalData);
configurations.add(userConfiguration);
com.microsoft.graph.beta.models.industrydata.UserConfiguration userConfiguration1 = new com.microsoft.graph.beta.models.industrydata.UserConfiguration();
com.microsoft.graph.beta.models.industrydata.SimplePasswordSettings defaultPasswordSettings1 = new com.microsoft.graph.beta.models.industrydata.SimplePasswordSettings();
defaultPasswordSettings1.setOdataType("#microsoft.graph.industryData.simplePasswordSettings");
defaultPasswordSettings1.setPassword("********");
userConfiguration1.setDefaultPasswordSettings(defaultPasswordSettings1);
LinkedList<String> licenseSkus1 = new LinkedList<String>();
licenseSkus1.add("SkuUpdated2");
userConfiguration1.setLicenseSkus(licenseSkus1);
HashMap<String, Object> additionalData1 = new HashMap<String, Object>();
additionalData1.put("roleGroup@odata.bind", "https://graph.microsoft.com/beta/external/industryData/roleGroups/students");
userConfiguration1.setAdditionalData(additionalData1);
configurations.add(userConfiguration1);
creationOptions.setConfigurations(configurations);
provisioningFlow.setCreationOptions(creationOptions);
com.microsoft.graph.models.industrydata.ProvisioningFlow result = graphClient.external().industryData().outboundProvisioningFlowSets().byOutboundProvisioningFlowSetId("{outboundProvisioningFlowSet-id}").provisioningFlows().byProvisioningFlowId("{provisioningFlow-id}").patch(provisioningFlow);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const provisioningFlow = {
  '@odata.type': '#microsoft.graph.industryData.userProvisioningFlow',
  createUnmatchedUsers: true,
  managementOptions: {
    additionalAttributes: [
      'userGradeLevel'
    ],
    additionalOptions: {
      studentAgeGroup: 'minor',
      allowStudentContactAssociation: true
    }
  },
  creationOptions: {
    configurations: [
      {
        'roleGroup@odata.bind': 'https://graph.microsoft.com/beta/external/industryData/roleGroups/staff',
        defaultPasswordSettings: {
          '@odata.type': '#microsoft.graph.industryData.simplePasswordSettings',
          password: '********'
        },
        licenseSkus: [
          'SkuUpdated'
        ]
      },
      {
        'roleGroup@odata.bind': 'https://graph.microsoft.com/beta/external/industryData/roleGroups/students',
        defaultPasswordSettings: {
          '@odata.type': '#microsoft.graph.industryData.simplePasswordSettings',
          password: '********'
        },
        licenseSkus: [
          'SkuUpdated2'
        ]
      }
    ]
  }
};

await client.api('/external/industryData/OutboundProvisioningFlowSets/9ab41255-5364-4c53-e15c-08dc4ab6ee03/provisioningFlows/dbd36d16-c574-4ed8-3ac7-08dc4ac6fb7f')
	.version('beta')
	.update(provisioningFlow);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Models\IndustryData\UserProvisioningFlow;
use Microsoft\Graph\Beta\Generated\Models\IndustryData\UserManagementOptions;
use Microsoft\Graph\Beta\Generated\Models\IndustryData\AdditionalUserAttributes;
use Microsoft\Graph\Beta\Generated\Models\IndustryData\AdditionalUserOptions;
use Microsoft\Graph\Beta\Generated\Models\IndustryData\StudentAgeGroup;
use Microsoft\Graph\Beta\Generated\Models\IndustryData\UserCreationOptions;
use Microsoft\Graph\Beta\Generated\Models\IndustryData\UserConfiguration;
use Microsoft\Graph\Beta\Generated\Models\IndustryData\SimplePasswordSettings;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new UserProvisioningFlow();
$requestBody->setOdataType('#microsoft.graph.industryData.userProvisioningFlow');
$requestBody->setCreateUnmatchedUsers(true);
$managementOptions = new UserManagementOptions();
$managementOptions->setAdditionalAttributes([new AdditionalUserAttributes('userGradeLevel'),	]);
$managementOptionsAdditionalOptions = new AdditionalUserOptions();
$managementOptionsAdditionalOptions->setStudentAgeGroup(new StudentAgeGroup('minor'));
$managementOptionsAdditionalOptions->setAllowStudentContactAssociation(true);
$managementOptions->setAdditionalOptions($managementOptionsAdditionalOptions);
$requestBody->setManagementOptions($managementOptions);
$creationOptions = new UserCreationOptions();
$configurationsUserConfiguration1 = new UserConfiguration();
$configurationsUserConfiguration1DefaultPasswordSettings = new SimplePasswordSettings();
$configurationsUserConfiguration1DefaultPasswordSettings->setOdataType('#microsoft.graph.industryData.simplePasswordSettings');
$configurationsUserConfiguration1DefaultPasswordSettings->setPassword('********');
$configurationsUserConfiguration1->setDefaultPasswordSettings($configurationsUserConfiguration1DefaultPasswordSettings);
$configurationsUserConfiguration1->setLicenseSkus(['SkuUpdated', 	]);
$additionalData = [
	'roleGroup@odata.bind' => 'https://graph.microsoft.com/beta/external/industryData/roleGroups/staff',
];
$configurationsUserConfiguration1->setAdditionalData($additionalData);
$configurationsArray []= $configurationsUserConfiguration1;
$configurationsUserConfiguration2 = new UserConfiguration();
$configurationsUserConfiguration2DefaultPasswordSettings = new SimplePasswordSettings();
$configurationsUserConfiguration2DefaultPasswordSettings->setOdataType('#microsoft.graph.industryData.simplePasswordSettings');
$configurationsUserConfiguration2DefaultPasswordSettings->setPassword('********');
$configurationsUserConfiguration2->setDefaultPasswordSettings($configurationsUserConfiguration2DefaultPasswordSettings);
$configurationsUserConfiguration2->setLicenseSkus(['SkuUpdated2', 	]);
$additionalData = [
	'roleGroup@odata.bind' => 'https://graph.microsoft.com/beta/external/industryData/roleGroups/students',
];
$configurationsUserConfiguration2->setAdditionalData($additionalData);
$configurationsArray []= $configurationsUserConfiguration2;
$creationOptions->setConfigurations($configurationsArray);

$requestBody->setCreationOptions($creationOptions);

$result = $graphServiceClient->external()->industryData()->outboundProvisioningFlowSets()->byOutboundProvisioningFlowSetId('outboundProvisioningFlowSet-id')->provisioningFlows()->byProvisioningFlowId('provisioningFlow-id')->patch($requestBody)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Beta.Search

$params = @{
	"@odata.type" = "#microsoft.graph.industryData.userProvisioningFlow"
	createUnmatchedUsers = $true
	managementOptions = @{
		additionalAttributes = @(
		"userGradeLevel"
	)
	additionalOptions = @{
		studentAgeGroup = "minor"
		allowStudentContactAssociation = $true
	}
}
creationOptions = @{
	configurations = @(
		@{
			"roleGroup@odata.bind" = "https://graph.microsoft.com/beta/external/industryData/roleGroups/staff"
			defaultPasswordSettings = @{
				"@odata.type" = "#microsoft.graph.industryData.simplePasswordSettings"
				password = "********"
			}
			licenseSkus = @(
			"SkuUpdated"
		)
	}
	@{
		"roleGroup@odata.bind" = "https://graph.microsoft.com/beta/external/industryData/roleGroups/students"
		defaultPasswordSettings = @{
			"@odata.type" = "#microsoft.graph.industryData.simplePasswordSettings"
			password = "********"
		}
		licenseSkus = @(
		"SkuUpdated2"
	)
}
)
}
}

Update-MgBetaExternalIndustryDataOutboundProvisioningFlowSetProvisioningFlow -OutboundProvisioningFlowSetId $outboundProvisioningFlowSetId -ProvisioningFlowId $provisioningFlowId -BodyParameter $params
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.models.industry_data.user_provisioning_flow import UserProvisioningFlow
from msgraph_beta.generated.models.industry_data.user_management_options import UserManagementOptions
from msgraph_beta.generated.models.industry_data.additional_user_attributes import AdditionalUserAttributes
from msgraph_beta.generated.models.additional_user_attributes import AdditionalUserAttributes
from msgraph_beta.generated.models.industry_data.additional_user_options import AdditionalUserOptions
from msgraph_beta.generated.models.student_age_group import StudentAgeGroup
from msgraph_beta.generated.models.industry_data.user_creation_options import UserCreationOptions
from msgraph_beta.generated.models.industry_data.user_configuration import UserConfiguration
from msgraph_beta.generated.models.industry_data.simple_password_settings import SimplePasswordSettings
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = UserProvisioningFlow(
	odata_type = "#microsoft.graph.industryData.userProvisioningFlow",
	create_unmatched_users = True,
	management_options = UserManagementOptions(
		additional_attributes = [
			AdditionalUserAttributes.UserGradeLevel,
		],
		additional_options = AdditionalUserOptions(
			student_age_group = StudentAgeGroup.Minor,
			allow_student_contact_association = True,
		),
	),
	creation_options = UserCreationOptions(
		configurations = [
			UserConfiguration(
				default_password_settings = SimplePasswordSettings(
					odata_type = "#microsoft.graph.industryData.simplePasswordSettings",
					password = "********",
				),
				license_skus = [
					"SkuUpdated",
				],
				additional_data = {
						"role_group@odata_bind" : "https://graph.microsoft.com/beta/external/industryData/roleGroups/staff",
				}
			),
			UserConfiguration(
				default_password_settings = SimplePasswordSettings(
					odata_type = "#microsoft.graph.industryData.simplePasswordSettings",
					password = "********",
				),
				license_skus = [
					"SkuUpdated2",
				],
				additional_data = {
						"role_group@odata_bind" : "https://graph.microsoft.com/beta/external/industryData/roleGroups/students",
				}
			),
		],
	),
)

result = await graph_client.external.industry_data.outbound_provisioning_flow_sets.by_outbound_provisioning_flow_set_id('outboundProvisioningFlowSet-id').provisioning_flows.by_provisioning_flow_id('provisioningFlow-id').patch(request_body)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

```http
HTTP/1.1 204 No Content
```
