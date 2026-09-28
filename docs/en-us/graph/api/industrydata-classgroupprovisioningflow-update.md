<!-- Source: https://learn.microsoft.com/en-us/graph/api/industrydata-classgroupprovisioningflow-update?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-06-22 -->

# Update classGroupProvisioningFlow

Namespace: microsoft.graph.industryData

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Update the properties of a [classGroupProvisioningFlow](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-classgroupprovisioningflow?view=graph-rest-beta) object.

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
| configuration | [microsoft.graph.industryData.classGroupConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-classgroupconfiguration?view=graph-rest-beta) | The different attribute choices for the class groups to be provisioned. Required. |

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
PATCH https://graph.microsoft.com/beta/external/industryData/OutboundProvisioningFlowSets/9ab41255-5364-4c53-e15c-08dc4ab6ee03/provisioningFlows/417a82c8-7caa-4f82-3ac6-08dc4ac6fb7f
Content-Type: application/json

{
    "@odata.type": "#microsoft.graph.industryData.classGroupProvisioningFlow",
    "configuration": {
        "@odata.type": "#microsoft.graph.industryData.classGroupConfiguration",
        "additionalAttributes": [
            "courseTitle",
            "courseCode"
        ],
        "additionalOptions": {
            "@odata.type": "#microsoft.graph.industryData.additionalClassGroupOptions",
            "createTeam": false,
            "writeDisplayNameOnCreateOnly": false
        },
        "enrollmentMappings": {
            "@odata.type": "#microsoft.graph.industryData.enrollmentMappings",
            "memberEnrollmentMappings": [
                {
                    "@odata.type": "#microsoft.graph.industryData.sectionRoleReferenceValue",
                    "code": "substitute"
                }
            ],
            "ownerEnrollmentMappings": [
                {
                    "@odata.type": "#microsoft.graph.industryData.sectionRoleReferenceValue",
                    "code": "teacher"
                }
            ]
        }
    }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.Models.IndustryData;

var requestBody = new ClassGroupProvisioningFlow
{
	OdataType = "#microsoft.graph.industryData.classGroupProvisioningFlow",
	Configuration = new ClassGroupConfiguration
	{
		OdataType = "#microsoft.graph.industryData.classGroupConfiguration",
		AdditionalAttributes = new List<AdditionalClassGroupAttributes?>
		{
			AdditionalClassGroupAttributes.CourseTitle,
			AdditionalClassGroupAttributes.CourseCode,
		},
		AdditionalOptions = new AdditionalClassGroupOptions
		{
			OdataType = "#microsoft.graph.industryData.additionalClassGroupOptions",
			CreateTeam = false,
			WriteDisplayNameOnCreateOnly = false,
		},
		EnrollmentMappings = new EnrollmentMappings
		{
			OdataType = "#microsoft.graph.industryData.enrollmentMappings",
			MemberEnrollmentMappings = new List<SectionRoleReferenceValue>
			{
				new SectionRoleReferenceValue
				{
					OdataType = "#microsoft.graph.industryData.sectionRoleReferenceValue",
					Code = "substitute",
				},
			},
			OwnerEnrollmentMappings = new List<SectionRoleReferenceValue>
			{
				new SectionRoleReferenceValue
				{
					OdataType = "#microsoft.graph.industryData.sectionRoleReferenceValue",
					Code = "teacher",
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
configuration := graphmodelsindustrydata.NewClassGroupConfiguration()
additionalAttributes := []graphmodelsindustrydata.AdditionalClassGroupAttributesable {
	additionalClassGroupAttributes := graphmodels.COURSETITLE_ADDITIONALCLASSGROUPATTRIBUTES 
	configuration.SetAdditionalClassGroupAttributes(&additionalClassGroupAttributes) 
	additionalClassGroupAttributes := graphmodels.COURSECODE_ADDITIONALCLASSGROUPATTRIBUTES 
	configuration.SetAdditionalClassGroupAttributes(&additionalClassGroupAttributes)
}
configuration.SetAdditionalAttributes(additionalAttributes)
additionalOptions := graphmodelsindustrydata.NewAdditionalClassGroupOptions()
createTeam := false
additionalOptions.SetCreateTeam(&createTeam) 
writeDisplayNameOnCreateOnly := false
additionalOptions.SetWriteDisplayNameOnCreateOnly(&writeDisplayNameOnCreateOnly) 
configuration.SetAdditionalOptions(additionalOptions)
enrollmentMappings := graphmodelsindustrydata.NewEnrollmentMappings()


sectionRoleReferenceValue := graphmodelsindustrydata.NewSectionRoleReferenceValue()
code := "substitute"
sectionRoleReferenceValue.SetCode(&code) 

memberEnrollmentMappings := []graphmodelsindustrydata.SectionRoleReferenceValueable {
	sectionRoleReferenceValue,
}
enrollmentMappings.SetMemberEnrollmentMappings(memberEnrollmentMappings)


sectionRoleReferenceValue := graphmodelsindustrydata.NewSectionRoleReferenceValue()
code := "teacher"
sectionRoleReferenceValue.SetCode(&code) 

ownerEnrollmentMappings := []graphmodelsindustrydata.SectionRoleReferenceValueable {
	sectionRoleReferenceValue,
}
enrollmentMappings.SetOwnerEnrollmentMappings(ownerEnrollmentMappings)
configuration.SetEnrollmentMappings(enrollmentMappings)
requestBody.SetConfiguration(configuration)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
provisioningFlows, err := graphClient.External().IndustryData().OutboundProvisioningFlowSets().ByOutboundProvisioningFlowSetId("outboundProvisioningFlowSet-id").ProvisioningFlows().ByProvisioningFlowId("provisioningFlow-id").Patch(context.Background(), requestBody, nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.beta.models.industrydata.ClassGroupProvisioningFlow provisioningFlow = new com.microsoft.graph.beta.models.industrydata.ClassGroupProvisioningFlow();
provisioningFlow.setOdataType("#microsoft.graph.industryData.classGroupProvisioningFlow");
com.microsoft.graph.beta.models.industrydata.ClassGroupConfiguration configuration = new com.microsoft.graph.beta.models.industrydata.ClassGroupConfiguration();
configuration.setOdataType("#microsoft.graph.industryData.classGroupConfiguration");
LinkedList<com.microsoft.graph.beta.models.industrydata.com.microsoft.graph.beta.models.industrydata.AdditionalClassGroupAttributes> additionalAttributes = new LinkedList<com.microsoft.graph.beta.models.industrydata.com.microsoft.graph.beta.models.industrydata.AdditionalClassGroupAttributes>();
additionalAttributes.add(com.microsoft.graph.beta.models.industrydata.AdditionalClassGroupAttributes.CourseTitle);
additionalAttributes.add(com.microsoft.graph.beta.models.industrydata.AdditionalClassGroupAttributes.CourseCode);
configuration.setAdditionalAttributes(additionalAttributes);
com.microsoft.graph.beta.models.industrydata.AdditionalClassGroupOptions additionalOptions = new com.microsoft.graph.beta.models.industrydata.AdditionalClassGroupOptions();
additionalOptions.setOdataType("#microsoft.graph.industryData.additionalClassGroupOptions");
additionalOptions.setCreateTeam(false);
additionalOptions.setWriteDisplayNameOnCreateOnly(false);
configuration.setAdditionalOptions(additionalOptions);
com.microsoft.graph.beta.models.industrydata.EnrollmentMappings enrollmentMappings = new com.microsoft.graph.beta.models.industrydata.EnrollmentMappings();
enrollmentMappings.setOdataType("#microsoft.graph.industryData.enrollmentMappings");
LinkedList<com.microsoft.graph.beta.models.industrydata.SectionRoleReferenceValue> memberEnrollmentMappings = new LinkedList<com.microsoft.graph.beta.models.industrydata.SectionRoleReferenceValue>();
com.microsoft.graph.beta.models.industrydata.SectionRoleReferenceValue sectionRoleReferenceValue = new com.microsoft.graph.beta.models.industrydata.SectionRoleReferenceValue();
sectionRoleReferenceValue.setOdataType("#microsoft.graph.industryData.sectionRoleReferenceValue");
sectionRoleReferenceValue.setCode("substitute");
memberEnrollmentMappings.add(sectionRoleReferenceValue);
enrollmentMappings.setMemberEnrollmentMappings(memberEnrollmentMappings);
LinkedList<com.microsoft.graph.beta.models.industrydata.SectionRoleReferenceValue> ownerEnrollmentMappings = new LinkedList<com.microsoft.graph.beta.models.industrydata.SectionRoleReferenceValue>();
com.microsoft.graph.beta.models.industrydata.SectionRoleReferenceValue sectionRoleReferenceValue1 = new com.microsoft.graph.beta.models.industrydata.SectionRoleReferenceValue();
sectionRoleReferenceValue1.setOdataType("#microsoft.graph.industryData.sectionRoleReferenceValue");
sectionRoleReferenceValue1.setCode("teacher");
ownerEnrollmentMappings.add(sectionRoleReferenceValue1);
enrollmentMappings.setOwnerEnrollmentMappings(ownerEnrollmentMappings);
configuration.setEnrollmentMappings(enrollmentMappings);
provisioningFlow.setConfiguration(configuration);
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
    '@odata.type': '#microsoft.graph.industryData.classGroupProvisioningFlow',
    configuration: {
        '@odata.type': '#microsoft.graph.industryData.classGroupConfiguration',
        additionalAttributes: [
            'courseTitle',
            'courseCode'
        ],
        additionalOptions: {
            '@odata.type': '#microsoft.graph.industryData.additionalClassGroupOptions',
            createTeam: false,
            writeDisplayNameOnCreateOnly: false
        },
        enrollmentMappings: {
            '@odata.type': '#microsoft.graph.industryData.enrollmentMappings',
            memberEnrollmentMappings: [
                {
                    '@odata.type': '#microsoft.graph.industryData.sectionRoleReferenceValue',
                    code: 'substitute'
                }
            ],
            ownerEnrollmentMappings: [
                {
                    '@odata.type': '#microsoft.graph.industryData.sectionRoleReferenceValue',
                    code: 'teacher'
                }
            ]
        }
    }
};

await client.api('/external/industryData/OutboundProvisioningFlowSets/9ab41255-5364-4c53-e15c-08dc4ab6ee03/provisioningFlows/417a82c8-7caa-4f82-3ac6-08dc4ac6fb7f')
	.version('beta')
	.update(provisioningFlow);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Models\IndustryData\ClassGroupProvisioningFlow;
use Microsoft\Graph\Beta\Generated\Models\IndustryData\ClassGroupConfiguration;
use Microsoft\Graph\Beta\Generated\Models\IndustryData\AdditionalClassGroupAttributes;
use Microsoft\Graph\Beta\Generated\Models\IndustryData\AdditionalClassGroupOptions;
use Microsoft\Graph\Beta\Generated\Models\IndustryData\EnrollmentMappings;
use Microsoft\Graph\Beta\Generated\Models\IndustryData\SectionRoleReferenceValue;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new ClassGroupProvisioningFlow();
$requestBody->setOdataType('#microsoft.graph.industryData.classGroupProvisioningFlow');
$configuration = new ClassGroupConfiguration();
$configuration->setOdataType('#microsoft.graph.industryData.classGroupConfiguration');
$configuration->setAdditionalAttributes([new AdditionalClassGroupAttributes('courseTitle'),new AdditionalClassGroupAttributes('courseCode'),	]);
$configurationAdditionalOptions = new AdditionalClassGroupOptions();
$configurationAdditionalOptions->setOdataType('#microsoft.graph.industryData.additionalClassGroupOptions');
$configurationAdditionalOptions->setCreateTeam(false);
$configurationAdditionalOptions->setWriteDisplayNameOnCreateOnly(false);
$configuration->setAdditionalOptions($configurationAdditionalOptions);
$configurationEnrollmentMappings = new EnrollmentMappings();
$configurationEnrollmentMappings->setOdataType('#microsoft.graph.industryData.enrollmentMappings');
$memberEnrollmentMappingsSectionRoleReferenceValue1 = new SectionRoleReferenceValue();
$memberEnrollmentMappingsSectionRoleReferenceValue1->setOdataType('#microsoft.graph.industryData.sectionRoleReferenceValue');
$memberEnrollmentMappingsSectionRoleReferenceValue1->setCode('substitute');
$memberEnrollmentMappingsArray []= $memberEnrollmentMappingsSectionRoleReferenceValue1;
$configurationEnrollmentMappings->setMemberEnrollmentMappings($memberEnrollmentMappingsArray);

$ownerEnrollmentMappingsSectionRoleReferenceValue1 = new SectionRoleReferenceValue();
$ownerEnrollmentMappingsSectionRoleReferenceValue1->setOdataType('#microsoft.graph.industryData.sectionRoleReferenceValue');
$ownerEnrollmentMappingsSectionRoleReferenceValue1->setCode('teacher');
$ownerEnrollmentMappingsArray []= $ownerEnrollmentMappingsSectionRoleReferenceValue1;
$configurationEnrollmentMappings->setOwnerEnrollmentMappings($ownerEnrollmentMappingsArray);

$configuration->setEnrollmentMappings($configurationEnrollmentMappings);
$requestBody->setConfiguration($configuration);

$result = $graphServiceClient->external()->industryData()->outboundProvisioningFlowSets()->byOutboundProvisioningFlowSetId('outboundProvisioningFlowSet-id')->provisioningFlows()->byProvisioningFlowId('provisioningFlow-id')->patch($requestBody)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Beta.Search

$params = @{
	"@odata.type" = "#microsoft.graph.industryData.classGroupProvisioningFlow"
	configuration = @{
		"@odata.type" = "#microsoft.graph.industryData.classGroupConfiguration"
		additionalAttributes = @(
		"courseTitle"
	"courseCode"
)
additionalOptions = @{
	"@odata.type" = "#microsoft.graph.industryData.additionalClassGroupOptions"
	createTeam = $false
	writeDisplayNameOnCreateOnly = $false
}
enrollmentMappings = @{
	"@odata.type" = "#microsoft.graph.industryData.enrollmentMappings"
	memberEnrollmentMappings = @(
		@{
			"@odata.type" = "#microsoft.graph.industryData.sectionRoleReferenceValue"
			code = "substitute"
		}
	)
	ownerEnrollmentMappings = @(
		@{
			"@odata.type" = "#microsoft.graph.industryData.sectionRoleReferenceValue"
			code = "teacher"
		}
	)
}
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
from msgraph_beta.generated.models.industry_data.class_group_provisioning_flow import ClassGroupProvisioningFlow
from msgraph_beta.generated.models.industry_data.class_group_configuration import ClassGroupConfiguration
from msgraph_beta.generated.models.industry_data.additional_class_group_attributes import AdditionalClassGroupAttributes
from msgraph_beta.generated.models.additional_class_group_attributes import AdditionalClassGroupAttributes
from msgraph_beta.generated.models.industry_data.additional_class_group_options import AdditionalClassGroupOptions
from msgraph_beta.generated.models.industry_data.enrollment_mappings import EnrollmentMappings
from msgraph_beta.generated.models.industry_data.section_role_reference_value import SectionRoleReferenceValue
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = ClassGroupProvisioningFlow(
	odata_type = "#microsoft.graph.industryData.classGroupProvisioningFlow",
	configuration = ClassGroupConfiguration(
		odata_type = "#microsoft.graph.industryData.classGroupConfiguration",
		additional_attributes = [
			AdditionalClassGroupAttributes.CourseTitle,
			AdditionalClassGroupAttributes.CourseCode,
		],
		additional_options = AdditionalClassGroupOptions(
			odata_type = "#microsoft.graph.industryData.additionalClassGroupOptions",
			create_team = False,
			write_display_name_on_create_only = False,
		),
		enrollment_mappings = EnrollmentMappings(
			odata_type = "#microsoft.graph.industryData.enrollmentMappings",
			member_enrollment_mappings = [
				SectionRoleReferenceValue(
					odata_type = "#microsoft.graph.industryData.sectionRoleReferenceValue",
					code = "substitute",
				),
			],
			owner_enrollment_mappings = [
				SectionRoleReferenceValue(
					odata_type = "#microsoft.graph.industryData.sectionRoleReferenceValue",
					code = "teacher",
				),
			],
		),
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
