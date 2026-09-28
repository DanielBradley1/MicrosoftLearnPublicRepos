<!-- Source: https://learn.microsoft.com/en-us/graph/api/industrydata-outboundprovisioningflowset-post-provisioningflows?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-16 -->

# Create provisioningFlow

Namespace: microsoft.graph.industryData

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Create a new [provisioningFlow](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-provisioningflow?view=graph-rest-beta) object.

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
POST /external/industryData/outboundProvisioningFlowSets/{id}/provisioningFlows
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the [provisioningFlow](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-provisioningflow?view=graph-rest-beta) object.

Any of the following provisioning flows are valid:

- [administrativeUnitProvisioningFlow](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-administrativeunitprovisioningflow?view=graph-rest-beta)
- [classGroupProvisioningFlow](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-classgroupprovisioningflow?view=graph-rest-beta)
- [securityGroupProvisioningFlow](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-securitygroupprovisioningflow?view=graph-rest-beta)
- [userProvisioningFlow](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-userprovisioningflow?view=graph-rest-beta)

Caution

The **markAllStudentsAsMinors** property of **additionalUserOptions** under **managementOptions** in **userProvisioningFlow** is deprecated and will stop returning data on October 15, 2025. Going forward, use the **studentAgeGroup** property.

## Response

If successful, this method returns a `201 Created` response code and a [provisioningFlow](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-provisioningflow?view=graph-rest-beta) object in the response body.

## Examples

### Example 1: Create an administrativeUnitProvisioningFlow

#### Request

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
POST https://graph.microsoft.com/beta/external/industryData/OutboundProvisioningFlowSets/9ab41255-5364-4c53-e15c-08dc4ab6ee03/provisioningFlows
Content-type: application/json

{
  "@odata.type": "#microsoft.graph.industryData.administrativeUnitProvisioningFlow",
  "creationOptions":
  {
    "createBasedOnOrg": true,
    "createBasedOnOrgPlusroleGroup": true
  }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.Models.IndustryData;

var requestBody = new AdministrativeUnitProvisioningFlow
{
	OdataType = "#microsoft.graph.industryData.administrativeUnitProvisioningFlow",
	CreationOptions = new AdminUnitCreationOptions
	{
		CreateBasedOnOrg = true,
		CreateBasedOnOrgPlusroleGroup = true,
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.External.IndustryData.OutboundProvisioningFlowSets["{outboundProvisioningFlowSet-id}"].ProvisioningFlows.PostAsync(requestBody);
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
creationOptions := graphmodelsindustrydata.NewAdminUnitCreationOptions()
createBasedOnOrg := true
creationOptions.SetCreateBasedOnOrg(&createBasedOnOrg) 
createBasedOnOrgPlusroleGroup := true
creationOptions.SetCreateBasedOnOrgPlusroleGroup(&createBasedOnOrgPlusroleGroup) 
requestBody.SetCreationOptions(creationOptions)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
provisioningFlows, err := graphClient.External().IndustryData().OutboundProvisioningFlowSets().ByOutboundProvisioningFlowSetId("outboundProvisioningFlowSet-id").ProvisioningFlows().Post(context.Background(), requestBody, nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.beta.models.industrydata.AdministrativeUnitProvisioningFlow provisioningFlow = new com.microsoft.graph.beta.models.industrydata.AdministrativeUnitProvisioningFlow();
provisioningFlow.setOdataType("#microsoft.graph.industryData.administrativeUnitProvisioningFlow");
com.microsoft.graph.beta.models.industrydata.AdminUnitCreationOptions creationOptions = new com.microsoft.graph.beta.models.industrydata.AdminUnitCreationOptions();
creationOptions.setCreateBasedOnOrg(true);
creationOptions.setCreateBasedOnOrgPlusroleGroup(true);
provisioningFlow.setCreationOptions(creationOptions);
com.microsoft.graph.models.industrydata.ProvisioningFlow result = graphClient.external().industryData().outboundProvisioningFlowSets().byOutboundProvisioningFlowSetId("{outboundProvisioningFlowSet-id}").provisioningFlows().post(provisioningFlow);
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
  '@odata.type': '#microsoft.graph.industryData.administrativeUnitProvisioningFlow',
  creationOptions: 
  {
    createBasedOnOrg: true,
    createBasedOnOrgPlusroleGroup: true
  }
};

await client.api('/external/industryData/OutboundProvisioningFlowSets/9ab41255-5364-4c53-e15c-08dc4ab6ee03/provisioningFlows')
	.version('beta')
	.post(provisioningFlow);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Models\IndustryData\AdministrativeUnitProvisioningFlow;
use Microsoft\Graph\Beta\Generated\Models\IndustryData\AdminUnitCreationOptions;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new AdministrativeUnitProvisioningFlow();
$requestBody->setOdataType('#microsoft.graph.industryData.administrativeUnitProvisioningFlow');
$creationOptions = new AdminUnitCreationOptions();
$creationOptions->setCreateBasedOnOrg(true);
$creationOptions->setCreateBasedOnOrgPlusroleGroup(true);
$requestBody->setCreationOptions($creationOptions);

$result = $graphServiceClient->external()->industryData()->outboundProvisioningFlowSets()->byOutboundProvisioningFlowSetId('outboundProvisioningFlowSet-id')->provisioningFlows()->post($requestBody)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Beta.Search

$params = @{
	"@odata.type" = "#microsoft.graph.industryData.administrativeUnitProvisioningFlow"
	creationOptions = @{
		createBasedOnOrg = $true
		createBasedOnOrgPlusroleGroup = $true
	}
}

New-MgBetaExternalIndustryDataOutboundProvisioningFlowSetProvisioningFlow -OutboundProvisioningFlowSetId $outboundProvisioningFlowSetId -BodyParameter $params
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.models.industry_data.administrative_unit_provisioning_flow import AdministrativeUnitProvisioningFlow
from msgraph_beta.generated.models.industry_data.admin_unit_creation_options import AdminUnitCreationOptions
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = AdministrativeUnitProvisioningFlow(
	odata_type = "#microsoft.graph.industryData.administrativeUnitProvisioningFlow",
	creation_options = AdminUnitCreationOptions(
		create_based_on_org = True,
		create_based_on_org_plusrole_group = True,
	),
)

result = await graph_client.external.industry_data.outbound_provisioning_flow_sets.by_outbound_provisioning_flow_set_id('outboundProvisioningFlowSet-id').provisioning_flows.post(request_body)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-type: application/json

{
    "@odata.context": "https://graph.microsoft.com/beta/$metadata#external/industryData/outboundProvisioningFlowSets('9ab41255-5364-4c53-e15c-08dc4ab6ee03')/provisioningFlows/$entity",
    "@odata.type": "#microsoft.graph.industryData.administrativeUnitProvisioningFlow",
    "id": "f66e97ad-0870-46e0-3ff3-08dc49dccdc9",
    "createdDateTime": "2024-03-22T21:28:02.7164229Z",
    "lastModifiedDateTime": "2024-03-22T21:28:02.7164229Z",
    "readinessStatus": "notReady",
    "creationOptions": {
        "createBasedOnOrg": true,
        "createBasedOnOrgPlusRoleGroup": true
    }
}
```

### Example 2: Create a classGroupProvisioningFlow

#### Request

The following example shows a request.

- [HTTP](#tabpanel_2_http)
- [C#](#tabpanel_2_csharp)
- [Go](#tabpanel_2_go)
- [Java](#tabpanel_2_java)
- [JavaScript](#tabpanel_2_javascript)
- [PHP](#tabpanel_2_php)
- [PowerShell](#tabpanel_2_powershell)
- [Python](#tabpanel_2_python)

```http
POST https://graph.microsoft.com/beta/external/industryData/OutboundProvisioningFlowSets/9ab41255-5364-4c53-e15c-08dc4ab6ee03/provisioningFlows
Content-type: application/json

{
    "@odata.type": "#microsoft.graph.industryData.classGroupProvisioningFlow",
    "configuration": {
        "@odata.type": "#microsoft.graph.industryData.classGroupConfiguration",
        "additionalAttributes": [
            "courseTitle",
            "courseCode",
            "courseSubject",
            "courseGradeLevel",
            "courseExternalId",
            "academicSessionTitle",
            "academicSessionExternalId"
        ],
        "additionalOptions": {
            "@odata.type": "#microsoft.graph.industryData.additionalClassGroupOptions",
            "createTeam": true,
            "writeDisplayNameOnCreateOnly": true
        },
        "enrollmentMappings": {
            "@odata.type": "#microsoft.graph.industryData.enrollmentMappings",
            "ownerEnrollmentMappings": [
                {
                    "@odata.type": "#microsoft.graph.industryData.sectionRoleReferenceValue",
                    "code": "teacher"
                },
                {
                    "@odata.type": "#microsoft.graph.industryData.sectionRoleReferenceValue",
                    "code": "proctor"
                },
                {
                    "@odata.type": "#microsoft.graph.industryData.sectionRoleReferenceValue",
                    "code": "teacherAssistant"
                },
                {
                    "@odata.type": "#microsoft.graph.industryData.sectionRoleReferenceValue",
                    "code": "paraProfessional"
                },
                {
                    "@odata.type": "#microsoft.graph.industryData.sectionRoleReferenceValue",
                    "code": "physicalTherapist"
                },
                {
                    "@odata.type": "#microsoft.graph.industryData.sectionRoleReferenceValue",
                    "code": "speechTherapist"
                },
                {
                    "@odata.type": "#microsoft.graph.industryData.sectionRoleReferenceValue",
                    "code": "visionTherapist"
                },
                {
                    "@odata.type": "#microsoft.graph.industryData.sectionRoleReferenceValue",
                    "code": "occupationalTherapist"
                },
                {
                    "@odata.type": "#microsoft.graph.industryData.sectionRoleReferenceValue",
                    "code": "staff"
                }
            ],
            "memberEnrollmentMappings": [
                {
                    "@odata.type": "#microsoft.graph.industryData.sectionRoleReferenceValue",
                    "code": "student"
                },
                {
                    "@odata.type": "#microsoft.graph.industryData.sectionRoleReferenceValue",
                    "code": "substitute"
                },
                {
                    "@odata.type": "#microsoft.graph.industryData.sectionRoleReferenceValue",
                    "code": "aide"
                },
                {
                    "@odata.type": "#microsoft.graph.industryData.sectionRoleReferenceValue",
                    "code": "proctor"
                },
                {
                    "@odata.type": "#microsoft.graph.industryData.sectionRoleReferenceValue",
                    "code": "teacherAssistant"
                },
                {
                    "@odata.type": "#microsoft.graph.industryData.sectionRoleReferenceValue",
                    "code": "paraProfessional"
                },
                {
                    "@odata.type": "#microsoft.graph.industryData.sectionRoleReferenceValue",
                    "code": "physicalTherapist"
                },
                {
                    "@odata.type": "#microsoft.graph.industryData.sectionRoleReferenceValue",
                    "code": "speechTherapist"
                },
                {
                    "@odata.type": "#microsoft.graph.industryData.sectionRoleReferenceValue",
                    "code": "visionTherapist"
                },
                {
                    "@odata.type": "#microsoft.graph.industryData.sectionRoleReferenceValue",
                    "code": "occupationalTherapist"
                },
                {
                    "@odata.type": "#microsoft.graph.industryData.sectionRoleReferenceValue",
                    "code": "staff"
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
			AdditionalClassGroupAttributes.CourseSubject,
			AdditionalClassGroupAttributes.CourseGradeLevel,
			AdditionalClassGroupAttributes.CourseExternalId,
			AdditionalClassGroupAttributes.AcademicSessionTitle,
			AdditionalClassGroupAttributes.AcademicSessionExternalId,
		},
		AdditionalOptions = new AdditionalClassGroupOptions
		{
			OdataType = "#microsoft.graph.industryData.additionalClassGroupOptions",
			CreateTeam = true,
			WriteDisplayNameOnCreateOnly = true,
		},
		EnrollmentMappings = new EnrollmentMappings
		{
			OdataType = "#microsoft.graph.industryData.enrollmentMappings",
			OwnerEnrollmentMappings = new List<SectionRoleReferenceValue>
			{
				new SectionRoleReferenceValue
				{
					OdataType = "#microsoft.graph.industryData.sectionRoleReferenceValue",
					Code = "teacher",
				},
				new SectionRoleReferenceValue
				{
					OdataType = "#microsoft.graph.industryData.sectionRoleReferenceValue",
					Code = "proctor",
				},
				new SectionRoleReferenceValue
				{
					OdataType = "#microsoft.graph.industryData.sectionRoleReferenceValue",
					Code = "teacherAssistant",
				},
				new SectionRoleReferenceValue
				{
					OdataType = "#microsoft.graph.industryData.sectionRoleReferenceValue",
					Code = "paraProfessional",
				},
				new SectionRoleReferenceValue
				{
					OdataType = "#microsoft.graph.industryData.sectionRoleReferenceValue",
					Code = "physicalTherapist",
				},
				new SectionRoleReferenceValue
				{
					OdataType = "#microsoft.graph.industryData.sectionRoleReferenceValue",
					Code = "speechTherapist",
				},
				new SectionRoleReferenceValue
				{
					OdataType = "#microsoft.graph.industryData.sectionRoleReferenceValue",
					Code = "visionTherapist",
				},
				new SectionRoleReferenceValue
				{
					OdataType = "#microsoft.graph.industryData.sectionRoleReferenceValue",
					Code = "occupationalTherapist",
				},
				new SectionRoleReferenceValue
				{
					OdataType = "#microsoft.graph.industryData.sectionRoleReferenceValue",
					Code = "staff",
				},
			},
			MemberEnrollmentMappings = new List<SectionRoleReferenceValue>
			{
				new SectionRoleReferenceValue
				{
					OdataType = "#microsoft.graph.industryData.sectionRoleReferenceValue",
					Code = "student",
				},
				new SectionRoleReferenceValue
				{
					OdataType = "#microsoft.graph.industryData.sectionRoleReferenceValue",
					Code = "substitute",
				},
				new SectionRoleReferenceValue
				{
					OdataType = "#microsoft.graph.industryData.sectionRoleReferenceValue",
					Code = "aide",
				},
				new SectionRoleReferenceValue
				{
					OdataType = "#microsoft.graph.industryData.sectionRoleReferenceValue",
					Code = "proctor",
				},
				new SectionRoleReferenceValue
				{
					OdataType = "#microsoft.graph.industryData.sectionRoleReferenceValue",
					Code = "teacherAssistant",
				},
				new SectionRoleReferenceValue
				{
					OdataType = "#microsoft.graph.industryData.sectionRoleReferenceValue",
					Code = "paraProfessional",
				},
				new SectionRoleReferenceValue
				{
					OdataType = "#microsoft.graph.industryData.sectionRoleReferenceValue",
					Code = "physicalTherapist",
				},
				new SectionRoleReferenceValue
				{
					OdataType = "#microsoft.graph.industryData.sectionRoleReferenceValue",
					Code = "speechTherapist",
				},
				new SectionRoleReferenceValue
				{
					OdataType = "#microsoft.graph.industryData.sectionRoleReferenceValue",
					Code = "visionTherapist",
				},
				new SectionRoleReferenceValue
				{
					OdataType = "#microsoft.graph.industryData.sectionRoleReferenceValue",
					Code = "occupationalTherapist",
				},
				new SectionRoleReferenceValue
				{
					OdataType = "#microsoft.graph.industryData.sectionRoleReferenceValue",
					Code = "staff",
				},
			},
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.External.IndustryData.OutboundProvisioningFlowSets["{outboundProvisioningFlowSet-id}"].ProvisioningFlows.PostAsync(requestBody);
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
	additionalClassGroupAttributes := graphmodels.COURSESUBJECT_ADDITIONALCLASSGROUPATTRIBUTES 
	configuration.SetAdditionalClassGroupAttributes(&additionalClassGroupAttributes) 
	additionalClassGroupAttributes := graphmodels.COURSEGRADELEVEL_ADDITIONALCLASSGROUPATTRIBUTES 
	configuration.SetAdditionalClassGroupAttributes(&additionalClassGroupAttributes) 
	additionalClassGroupAttributes := graphmodels.COURSEEXTERNALID_ADDITIONALCLASSGROUPATTRIBUTES 
	configuration.SetAdditionalClassGroupAttributes(&additionalClassGroupAttributes) 
	additionalClassGroupAttributes := graphmodels.ACADEMICSESSIONTITLE_ADDITIONALCLASSGROUPATTRIBUTES 
	configuration.SetAdditionalClassGroupAttributes(&additionalClassGroupAttributes) 
	additionalClassGroupAttributes := graphmodels.ACADEMICSESSIONEXTERNALID_ADDITIONALCLASSGROUPATTRIBUTES 
	configuration.SetAdditionalClassGroupAttributes(&additionalClassGroupAttributes)
}
configuration.SetAdditionalAttributes(additionalAttributes)
additionalOptions := graphmodelsindustrydata.NewAdditionalClassGroupOptions()
createTeam := true
additionalOptions.SetCreateTeam(&createTeam) 
writeDisplayNameOnCreateOnly := true
additionalOptions.SetWriteDisplayNameOnCreateOnly(&writeDisplayNameOnCreateOnly) 
configuration.SetAdditionalOptions(additionalOptions)
enrollmentMappings := graphmodelsindustrydata.NewEnrollmentMappings()


sectionRoleReferenceValue := graphmodelsindustrydata.NewSectionRoleReferenceValue()
code := "teacher"
sectionRoleReferenceValue.SetCode(&code) 
sectionRoleReferenceValue1 := graphmodelsindustrydata.NewSectionRoleReferenceValue()
code := "proctor"
sectionRoleReferenceValue1.SetCode(&code) 
sectionRoleReferenceValue2 := graphmodelsindustrydata.NewSectionRoleReferenceValue()
code := "teacherAssistant"
sectionRoleReferenceValue2.SetCode(&code) 
sectionRoleReferenceValue3 := graphmodelsindustrydata.NewSectionRoleReferenceValue()
code := "paraProfessional"
sectionRoleReferenceValue3.SetCode(&code) 
sectionRoleReferenceValue4 := graphmodelsindustrydata.NewSectionRoleReferenceValue()
code := "physicalTherapist"
sectionRoleReferenceValue4.SetCode(&code) 
sectionRoleReferenceValue5 := graphmodelsindustrydata.NewSectionRoleReferenceValue()
code := "speechTherapist"
sectionRoleReferenceValue5.SetCode(&code) 
sectionRoleReferenceValue6 := graphmodelsindustrydata.NewSectionRoleReferenceValue()
code := "visionTherapist"
sectionRoleReferenceValue6.SetCode(&code) 
sectionRoleReferenceValue7 := graphmodelsindustrydata.NewSectionRoleReferenceValue()
code := "occupationalTherapist"
sectionRoleReferenceValue7.SetCode(&code) 
sectionRoleReferenceValue8 := graphmodelsindustrydata.NewSectionRoleReferenceValue()
code := "staff"
sectionRoleReferenceValue8.SetCode(&code) 

ownerEnrollmentMappings := []graphmodelsindustrydata.SectionRoleReferenceValueable {
	sectionRoleReferenceValue,
	sectionRoleReferenceValue1,
	sectionRoleReferenceValue2,
	sectionRoleReferenceValue3,
	sectionRoleReferenceValue4,
	sectionRoleReferenceValue5,
	sectionRoleReferenceValue6,
	sectionRoleReferenceValue7,
	sectionRoleReferenceValue8,
}
enrollmentMappings.SetOwnerEnrollmentMappings(ownerEnrollmentMappings)


sectionRoleReferenceValue := graphmodelsindustrydata.NewSectionRoleReferenceValue()
code := "student"
sectionRoleReferenceValue.SetCode(&code) 
sectionRoleReferenceValue1 := graphmodelsindustrydata.NewSectionRoleReferenceValue()
code := "substitute"
sectionRoleReferenceValue1.SetCode(&code) 
sectionRoleReferenceValue2 := graphmodelsindustrydata.NewSectionRoleReferenceValue()
code := "aide"
sectionRoleReferenceValue2.SetCode(&code) 
sectionRoleReferenceValue3 := graphmodelsindustrydata.NewSectionRoleReferenceValue()
code := "proctor"
sectionRoleReferenceValue3.SetCode(&code) 
sectionRoleReferenceValue4 := graphmodelsindustrydata.NewSectionRoleReferenceValue()
code := "teacherAssistant"
sectionRoleReferenceValue4.SetCode(&code) 
sectionRoleReferenceValue5 := graphmodelsindustrydata.NewSectionRoleReferenceValue()
code := "paraProfessional"
sectionRoleReferenceValue5.SetCode(&code) 
sectionRoleReferenceValue6 := graphmodelsindustrydata.NewSectionRoleReferenceValue()
code := "physicalTherapist"
sectionRoleReferenceValue6.SetCode(&code) 
sectionRoleReferenceValue7 := graphmodelsindustrydata.NewSectionRoleReferenceValue()
code := "speechTherapist"
sectionRoleReferenceValue7.SetCode(&code) 
sectionRoleReferenceValue8 := graphmodelsindustrydata.NewSectionRoleReferenceValue()
code := "visionTherapist"
sectionRoleReferenceValue8.SetCode(&code) 
sectionRoleReferenceValue9 := graphmodelsindustrydata.NewSectionRoleReferenceValue()
code := "occupationalTherapist"
sectionRoleReferenceValue9.SetCode(&code) 
sectionRoleReferenceValue10 := graphmodelsindustrydata.NewSectionRoleReferenceValue()
code := "staff"
sectionRoleReferenceValue10.SetCode(&code) 

memberEnrollmentMappings := []graphmodelsindustrydata.SectionRoleReferenceValueable {
	sectionRoleReferenceValue,
	sectionRoleReferenceValue1,
	sectionRoleReferenceValue2,
	sectionRoleReferenceValue3,
	sectionRoleReferenceValue4,
	sectionRoleReferenceValue5,
	sectionRoleReferenceValue6,
	sectionRoleReferenceValue7,
	sectionRoleReferenceValue8,
	sectionRoleReferenceValue9,
	sectionRoleReferenceValue10,
}
enrollmentMappings.SetMemberEnrollmentMappings(memberEnrollmentMappings)
configuration.SetEnrollmentMappings(enrollmentMappings)
requestBody.SetConfiguration(configuration)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
provisioningFlows, err := graphClient.External().IndustryData().OutboundProvisioningFlowSets().ByOutboundProvisioningFlowSetId("outboundProvisioningFlowSet-id").ProvisioningFlows().Post(context.Background(), requestBody, nil)
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
additionalAttributes.add(com.microsoft.graph.beta.models.industrydata.AdditionalClassGroupAttributes.CourseSubject);
additionalAttributes.add(com.microsoft.graph.beta.models.industrydata.AdditionalClassGroupAttributes.CourseGradeLevel);
additionalAttributes.add(com.microsoft.graph.beta.models.industrydata.AdditionalClassGroupAttributes.CourseExternalId);
additionalAttributes.add(com.microsoft.graph.beta.models.industrydata.AdditionalClassGroupAttributes.AcademicSessionTitle);
additionalAttributes.add(com.microsoft.graph.beta.models.industrydata.AdditionalClassGroupAttributes.AcademicSessionExternalId);
configuration.setAdditionalAttributes(additionalAttributes);
com.microsoft.graph.beta.models.industrydata.AdditionalClassGroupOptions additionalOptions = new com.microsoft.graph.beta.models.industrydata.AdditionalClassGroupOptions();
additionalOptions.setOdataType("#microsoft.graph.industryData.additionalClassGroupOptions");
additionalOptions.setCreateTeam(true);
additionalOptions.setWriteDisplayNameOnCreateOnly(true);
configuration.setAdditionalOptions(additionalOptions);
com.microsoft.graph.beta.models.industrydata.EnrollmentMappings enrollmentMappings = new com.microsoft.graph.beta.models.industrydata.EnrollmentMappings();
enrollmentMappings.setOdataType("#microsoft.graph.industryData.enrollmentMappings");
LinkedList<com.microsoft.graph.beta.models.industrydata.SectionRoleReferenceValue> ownerEnrollmentMappings = new LinkedList<com.microsoft.graph.beta.models.industrydata.SectionRoleReferenceValue>();
com.microsoft.graph.beta.models.industrydata.SectionRoleReferenceValue sectionRoleReferenceValue = new com.microsoft.graph.beta.models.industrydata.SectionRoleReferenceValue();
sectionRoleReferenceValue.setOdataType("#microsoft.graph.industryData.sectionRoleReferenceValue");
sectionRoleReferenceValue.setCode("teacher");
ownerEnrollmentMappings.add(sectionRoleReferenceValue);
com.microsoft.graph.beta.models.industrydata.SectionRoleReferenceValue sectionRoleReferenceValue1 = new com.microsoft.graph.beta.models.industrydata.SectionRoleReferenceValue();
sectionRoleReferenceValue1.setOdataType("#microsoft.graph.industryData.sectionRoleReferenceValue");
sectionRoleReferenceValue1.setCode("proctor");
ownerEnrollmentMappings.add(sectionRoleReferenceValue1);
com.microsoft.graph.beta.models.industrydata.SectionRoleReferenceValue sectionRoleReferenceValue2 = new com.microsoft.graph.beta.models.industrydata.SectionRoleReferenceValue();
sectionRoleReferenceValue2.setOdataType("#microsoft.graph.industryData.sectionRoleReferenceValue");
sectionRoleReferenceValue2.setCode("teacherAssistant");
ownerEnrollmentMappings.add(sectionRoleReferenceValue2);
com.microsoft.graph.beta.models.industrydata.SectionRoleReferenceValue sectionRoleReferenceValue3 = new com.microsoft.graph.beta.models.industrydata.SectionRoleReferenceValue();
sectionRoleReferenceValue3.setOdataType("#microsoft.graph.industryData.sectionRoleReferenceValue");
sectionRoleReferenceValue3.setCode("paraProfessional");
ownerEnrollmentMappings.add(sectionRoleReferenceValue3);
com.microsoft.graph.beta.models.industrydata.SectionRoleReferenceValue sectionRoleReferenceValue4 = new com.microsoft.graph.beta.models.industrydata.SectionRoleReferenceValue();
sectionRoleReferenceValue4.setOdataType("#microsoft.graph.industryData.sectionRoleReferenceValue");
sectionRoleReferenceValue4.setCode("physicalTherapist");
ownerEnrollmentMappings.add(sectionRoleReferenceValue4);
com.microsoft.graph.beta.models.industrydata.SectionRoleReferenceValue sectionRoleReferenceValue5 = new com.microsoft.graph.beta.models.industrydata.SectionRoleReferenceValue();
sectionRoleReferenceValue5.setOdataType("#microsoft.graph.industryData.sectionRoleReferenceValue");
sectionRoleReferenceValue5.setCode("speechTherapist");
ownerEnrollmentMappings.add(sectionRoleReferenceValue5);
com.microsoft.graph.beta.models.industrydata.SectionRoleReferenceValue sectionRoleReferenceValue6 = new com.microsoft.graph.beta.models.industrydata.SectionRoleReferenceValue();
sectionRoleReferenceValue6.setOdataType("#microsoft.graph.industryData.sectionRoleReferenceValue");
sectionRoleReferenceValue6.setCode("visionTherapist");
ownerEnrollmentMappings.add(sectionRoleReferenceValue6);
com.microsoft.graph.beta.models.industrydata.SectionRoleReferenceValue sectionRoleReferenceValue7 = new com.microsoft.graph.beta.models.industrydata.SectionRoleReferenceValue();
sectionRoleReferenceValue7.setOdataType("#microsoft.graph.industryData.sectionRoleReferenceValue");
sectionRoleReferenceValue7.setCode("occupationalTherapist");
ownerEnrollmentMappings.add(sectionRoleReferenceValue7);
com.microsoft.graph.beta.models.industrydata.SectionRoleReferenceValue sectionRoleReferenceValue8 = new com.microsoft.graph.beta.models.industrydata.SectionRoleReferenceValue();
sectionRoleReferenceValue8.setOdataType("#microsoft.graph.industryData.sectionRoleReferenceValue");
sectionRoleReferenceValue8.setCode("staff");
ownerEnrollmentMappings.add(sectionRoleReferenceValue8);
enrollmentMappings.setOwnerEnrollmentMappings(ownerEnrollmentMappings);
LinkedList<com.microsoft.graph.beta.models.industrydata.SectionRoleReferenceValue> memberEnrollmentMappings = new LinkedList<com.microsoft.graph.beta.models.industrydata.SectionRoleReferenceValue>();
com.microsoft.graph.beta.models.industrydata.SectionRoleReferenceValue sectionRoleReferenceValue9 = new com.microsoft.graph.beta.models.industrydata.SectionRoleReferenceValue();
sectionRoleReferenceValue9.setOdataType("#microsoft.graph.industryData.sectionRoleReferenceValue");
sectionRoleReferenceValue9.setCode("student");
memberEnrollmentMappings.add(sectionRoleReferenceValue9);
com.microsoft.graph.beta.models.industrydata.SectionRoleReferenceValue sectionRoleReferenceValue10 = new com.microsoft.graph.beta.models.industrydata.SectionRoleReferenceValue();
sectionRoleReferenceValue10.setOdataType("#microsoft.graph.industryData.sectionRoleReferenceValue");
sectionRoleReferenceValue10.setCode("substitute");
memberEnrollmentMappings.add(sectionRoleReferenceValue10);
com.microsoft.graph.beta.models.industrydata.SectionRoleReferenceValue sectionRoleReferenceValue11 = new com.microsoft.graph.beta.models.industrydata.SectionRoleReferenceValue();
sectionRoleReferenceValue11.setOdataType("#microsoft.graph.industryData.sectionRoleReferenceValue");
sectionRoleReferenceValue11.setCode("aide");
memberEnrollmentMappings.add(sectionRoleReferenceValue11);
com.microsoft.graph.beta.models.industrydata.SectionRoleReferenceValue sectionRoleReferenceValue12 = new com.microsoft.graph.beta.models.industrydata.SectionRoleReferenceValue();
sectionRoleReferenceValue12.setOdataType("#microsoft.graph.industryData.sectionRoleReferenceValue");
sectionRoleReferenceValue12.setCode("proctor");
memberEnrollmentMappings.add(sectionRoleReferenceValue12);
com.microsoft.graph.beta.models.industrydata.SectionRoleReferenceValue sectionRoleReferenceValue13 = new com.microsoft.graph.beta.models.industrydata.SectionRoleReferenceValue();
sectionRoleReferenceValue13.setOdataType("#microsoft.graph.industryData.sectionRoleReferenceValue");
sectionRoleReferenceValue13.setCode("teacherAssistant");
memberEnrollmentMappings.add(sectionRoleReferenceValue13);
com.microsoft.graph.beta.models.industrydata.SectionRoleReferenceValue sectionRoleReferenceValue14 = new com.microsoft.graph.beta.models.industrydata.SectionRoleReferenceValue();
sectionRoleReferenceValue14.setOdataType("#microsoft.graph.industryData.sectionRoleReferenceValue");
sectionRoleReferenceValue14.setCode("paraProfessional");
memberEnrollmentMappings.add(sectionRoleReferenceValue14);
com.microsoft.graph.beta.models.industrydata.SectionRoleReferenceValue sectionRoleReferenceValue15 = new com.microsoft.graph.beta.models.industrydata.SectionRoleReferenceValue();
sectionRoleReferenceValue15.setOdataType("#microsoft.graph.industryData.sectionRoleReferenceValue");
sectionRoleReferenceValue15.setCode("physicalTherapist");
memberEnrollmentMappings.add(sectionRoleReferenceValue15);
com.microsoft.graph.beta.models.industrydata.SectionRoleReferenceValue sectionRoleReferenceValue16 = new com.microsoft.graph.beta.models.industrydata.SectionRoleReferenceValue();
sectionRoleReferenceValue16.setOdataType("#microsoft.graph.industryData.sectionRoleReferenceValue");
sectionRoleReferenceValue16.setCode("speechTherapist");
memberEnrollmentMappings.add(sectionRoleReferenceValue16);
com.microsoft.graph.beta.models.industrydata.SectionRoleReferenceValue sectionRoleReferenceValue17 = new com.microsoft.graph.beta.models.industrydata.SectionRoleReferenceValue();
sectionRoleReferenceValue17.setOdataType("#microsoft.graph.industryData.sectionRoleReferenceValue");
sectionRoleReferenceValue17.setCode("visionTherapist");
memberEnrollmentMappings.add(sectionRoleReferenceValue17);
com.microsoft.graph.beta.models.industrydata.SectionRoleReferenceValue sectionRoleReferenceValue18 = new com.microsoft.graph.beta.models.industrydata.SectionRoleReferenceValue();
sectionRoleReferenceValue18.setOdataType("#microsoft.graph.industryData.sectionRoleReferenceValue");
sectionRoleReferenceValue18.setCode("occupationalTherapist");
memberEnrollmentMappings.add(sectionRoleReferenceValue18);
com.microsoft.graph.beta.models.industrydata.SectionRoleReferenceValue sectionRoleReferenceValue19 = new com.microsoft.graph.beta.models.industrydata.SectionRoleReferenceValue();
sectionRoleReferenceValue19.setOdataType("#microsoft.graph.industryData.sectionRoleReferenceValue");
sectionRoleReferenceValue19.setCode("staff");
memberEnrollmentMappings.add(sectionRoleReferenceValue19);
enrollmentMappings.setMemberEnrollmentMappings(memberEnrollmentMappings);
configuration.setEnrollmentMappings(enrollmentMappings);
provisioningFlow.setConfiguration(configuration);
com.microsoft.graph.models.industrydata.ProvisioningFlow result = graphClient.external().industryData().outboundProvisioningFlowSets().byOutboundProvisioningFlowSetId("{outboundProvisioningFlowSet-id}").provisioningFlows().post(provisioningFlow);
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
            'courseCode',
            'courseSubject',
            'courseGradeLevel',
            'courseExternalId',
            'academicSessionTitle',
            'academicSessionExternalId'
        ],
        additionalOptions: {
            '@odata.type': '#microsoft.graph.industryData.additionalClassGroupOptions',
            createTeam: true,
            writeDisplayNameOnCreateOnly: true
        },
        enrollmentMappings: {
            '@odata.type': '#microsoft.graph.industryData.enrollmentMappings',
            ownerEnrollmentMappings: [
                {
                    '@odata.type': '#microsoft.graph.industryData.sectionRoleReferenceValue',
                    code: 'teacher'
                },
                {
                    '@odata.type': '#microsoft.graph.industryData.sectionRoleReferenceValue',
                    code: 'proctor'
                },
                {
                    '@odata.type': '#microsoft.graph.industryData.sectionRoleReferenceValue',
                    code: 'teacherAssistant'
                },
                {
                    '@odata.type': '#microsoft.graph.industryData.sectionRoleReferenceValue',
                    code: 'paraProfessional'
                },
                {
                    '@odata.type': '#microsoft.graph.industryData.sectionRoleReferenceValue',
                    code: 'physicalTherapist'
                },
                {
                    '@odata.type': '#microsoft.graph.industryData.sectionRoleReferenceValue',
                    code: 'speechTherapist'
                },
                {
                    '@odata.type': '#microsoft.graph.industryData.sectionRoleReferenceValue',
                    code: 'visionTherapist'
                },
                {
                    '@odata.type': '#microsoft.graph.industryData.sectionRoleReferenceValue',
                    code: 'occupationalTherapist'
                },
                {
                    '@odata.type': '#microsoft.graph.industryData.sectionRoleReferenceValue',
                    code: 'staff'
                }
            ],
            memberEnrollmentMappings: [
                {
                    '@odata.type': '#microsoft.graph.industryData.sectionRoleReferenceValue',
                    code: 'student'
                },
                {
                    '@odata.type': '#microsoft.graph.industryData.sectionRoleReferenceValue',
                    code: 'substitute'
                },
                {
                    '@odata.type': '#microsoft.graph.industryData.sectionRoleReferenceValue',
                    code: 'aide'
                },
                {
                    '@odata.type': '#microsoft.graph.industryData.sectionRoleReferenceValue',
                    code: 'proctor'
                },
                {
                    '@odata.type': '#microsoft.graph.industryData.sectionRoleReferenceValue',
                    code: 'teacherAssistant'
                },
                {
                    '@odata.type': '#microsoft.graph.industryData.sectionRoleReferenceValue',
                    code: 'paraProfessional'
                },
                {
                    '@odata.type': '#microsoft.graph.industryData.sectionRoleReferenceValue',
                    code: 'physicalTherapist'
                },
                {
                    '@odata.type': '#microsoft.graph.industryData.sectionRoleReferenceValue',
                    code: 'speechTherapist'
                },
                {
                    '@odata.type': '#microsoft.graph.industryData.sectionRoleReferenceValue',
                    code: 'visionTherapist'
                },
                {
                    '@odata.type': '#microsoft.graph.industryData.sectionRoleReferenceValue',
                    code: 'occupationalTherapist'
                },
                {
                    '@odata.type': '#microsoft.graph.industryData.sectionRoleReferenceValue',
                    code: 'staff'
                }
            ]
        }
    }
};

await client.api('/external/industryData/OutboundProvisioningFlowSets/9ab41255-5364-4c53-e15c-08dc4ab6ee03/provisioningFlows')
	.version('beta')
	.post(provisioningFlow);
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
$configuration->setAdditionalAttributes([new AdditionalClassGroupAttributes('courseTitle'),new AdditionalClassGroupAttributes('courseCode'),new AdditionalClassGroupAttributes('courseSubject'),new AdditionalClassGroupAttributes('courseGradeLevel'),new AdditionalClassGroupAttributes('courseExternalId'),new AdditionalClassGroupAttributes('academicSessionTitle'),new AdditionalClassGroupAttributes('academicSessionExternalId'),	]);
$configurationAdditionalOptions = new AdditionalClassGroupOptions();
$configurationAdditionalOptions->setOdataType('#microsoft.graph.industryData.additionalClassGroupOptions');
$configurationAdditionalOptions->setCreateTeam(true);
$configurationAdditionalOptions->setWriteDisplayNameOnCreateOnly(true);
$configuration->setAdditionalOptions($configurationAdditionalOptions);
$configurationEnrollmentMappings = new EnrollmentMappings();
$configurationEnrollmentMappings->setOdataType('#microsoft.graph.industryData.enrollmentMappings');
$ownerEnrollmentMappingsSectionRoleReferenceValue1 = new SectionRoleReferenceValue();
$ownerEnrollmentMappingsSectionRoleReferenceValue1->setOdataType('#microsoft.graph.industryData.sectionRoleReferenceValue');
$ownerEnrollmentMappingsSectionRoleReferenceValue1->setCode('teacher');
$ownerEnrollmentMappingsArray []= $ownerEnrollmentMappingsSectionRoleReferenceValue1;
$ownerEnrollmentMappingsSectionRoleReferenceValue2 = new SectionRoleReferenceValue();
$ownerEnrollmentMappingsSectionRoleReferenceValue2->setOdataType('#microsoft.graph.industryData.sectionRoleReferenceValue');
$ownerEnrollmentMappingsSectionRoleReferenceValue2->setCode('proctor');
$ownerEnrollmentMappingsArray []= $ownerEnrollmentMappingsSectionRoleReferenceValue2;
$ownerEnrollmentMappingsSectionRoleReferenceValue3 = new SectionRoleReferenceValue();
$ownerEnrollmentMappingsSectionRoleReferenceValue3->setOdataType('#microsoft.graph.industryData.sectionRoleReferenceValue');
$ownerEnrollmentMappingsSectionRoleReferenceValue3->setCode('teacherAssistant');
$ownerEnrollmentMappingsArray []= $ownerEnrollmentMappingsSectionRoleReferenceValue3;
$ownerEnrollmentMappingsSectionRoleReferenceValue4 = new SectionRoleReferenceValue();
$ownerEnrollmentMappingsSectionRoleReferenceValue4->setOdataType('#microsoft.graph.industryData.sectionRoleReferenceValue');
$ownerEnrollmentMappingsSectionRoleReferenceValue4->setCode('paraProfessional');
$ownerEnrollmentMappingsArray []= $ownerEnrollmentMappingsSectionRoleReferenceValue4;
$ownerEnrollmentMappingsSectionRoleReferenceValue5 = new SectionRoleReferenceValue();
$ownerEnrollmentMappingsSectionRoleReferenceValue5->setOdataType('#microsoft.graph.industryData.sectionRoleReferenceValue');
$ownerEnrollmentMappingsSectionRoleReferenceValue5->setCode('physicalTherapist');
$ownerEnrollmentMappingsArray []= $ownerEnrollmentMappingsSectionRoleReferenceValue5;
$ownerEnrollmentMappingsSectionRoleReferenceValue6 = new SectionRoleReferenceValue();
$ownerEnrollmentMappingsSectionRoleReferenceValue6->setOdataType('#microsoft.graph.industryData.sectionRoleReferenceValue');
$ownerEnrollmentMappingsSectionRoleReferenceValue6->setCode('speechTherapist');
$ownerEnrollmentMappingsArray []= $ownerEnrollmentMappingsSectionRoleReferenceValue6;
$ownerEnrollmentMappingsSectionRoleReferenceValue7 = new SectionRoleReferenceValue();
$ownerEnrollmentMappingsSectionRoleReferenceValue7->setOdataType('#microsoft.graph.industryData.sectionRoleReferenceValue');
$ownerEnrollmentMappingsSectionRoleReferenceValue7->setCode('visionTherapist');
$ownerEnrollmentMappingsArray []= $ownerEnrollmentMappingsSectionRoleReferenceValue7;
$ownerEnrollmentMappingsSectionRoleReferenceValue8 = new SectionRoleReferenceValue();
$ownerEnrollmentMappingsSectionRoleReferenceValue8->setOdataType('#microsoft.graph.industryData.sectionRoleReferenceValue');
$ownerEnrollmentMappingsSectionRoleReferenceValue8->setCode('occupationalTherapist');
$ownerEnrollmentMappingsArray []= $ownerEnrollmentMappingsSectionRoleReferenceValue8;
$ownerEnrollmentMappingsSectionRoleReferenceValue9 = new SectionRoleReferenceValue();
$ownerEnrollmentMappingsSectionRoleReferenceValue9->setOdataType('#microsoft.graph.industryData.sectionRoleReferenceValue');
$ownerEnrollmentMappingsSectionRoleReferenceValue9->setCode('staff');
$ownerEnrollmentMappingsArray []= $ownerEnrollmentMappingsSectionRoleReferenceValue9;
$configurationEnrollmentMappings->setOwnerEnrollmentMappings($ownerEnrollmentMappingsArray);

$memberEnrollmentMappingsSectionRoleReferenceValue1 = new SectionRoleReferenceValue();
$memberEnrollmentMappingsSectionRoleReferenceValue1->setOdataType('#microsoft.graph.industryData.sectionRoleReferenceValue');
$memberEnrollmentMappingsSectionRoleReferenceValue1->setCode('student');
$memberEnrollmentMappingsArray []= $memberEnrollmentMappingsSectionRoleReferenceValue1;
$memberEnrollmentMappingsSectionRoleReferenceValue2 = new SectionRoleReferenceValue();
$memberEnrollmentMappingsSectionRoleReferenceValue2->setOdataType('#microsoft.graph.industryData.sectionRoleReferenceValue');
$memberEnrollmentMappingsSectionRoleReferenceValue2->setCode('substitute');
$memberEnrollmentMappingsArray []= $memberEnrollmentMappingsSectionRoleReferenceValue2;
$memberEnrollmentMappingsSectionRoleReferenceValue3 = new SectionRoleReferenceValue();
$memberEnrollmentMappingsSectionRoleReferenceValue3->setOdataType('#microsoft.graph.industryData.sectionRoleReferenceValue');
$memberEnrollmentMappingsSectionRoleReferenceValue3->setCode('aide');
$memberEnrollmentMappingsArray []= $memberEnrollmentMappingsSectionRoleReferenceValue3;
$memberEnrollmentMappingsSectionRoleReferenceValue4 = new SectionRoleReferenceValue();
$memberEnrollmentMappingsSectionRoleReferenceValue4->setOdataType('#microsoft.graph.industryData.sectionRoleReferenceValue');
$memberEnrollmentMappingsSectionRoleReferenceValue4->setCode('proctor');
$memberEnrollmentMappingsArray []= $memberEnrollmentMappingsSectionRoleReferenceValue4;
$memberEnrollmentMappingsSectionRoleReferenceValue5 = new SectionRoleReferenceValue();
$memberEnrollmentMappingsSectionRoleReferenceValue5->setOdataType('#microsoft.graph.industryData.sectionRoleReferenceValue');
$memberEnrollmentMappingsSectionRoleReferenceValue5->setCode('teacherAssistant');
$memberEnrollmentMappingsArray []= $memberEnrollmentMappingsSectionRoleReferenceValue5;
$memberEnrollmentMappingsSectionRoleReferenceValue6 = new SectionRoleReferenceValue();
$memberEnrollmentMappingsSectionRoleReferenceValue6->setOdataType('#microsoft.graph.industryData.sectionRoleReferenceValue');
$memberEnrollmentMappingsSectionRoleReferenceValue6->setCode('paraProfessional');
$memberEnrollmentMappingsArray []= $memberEnrollmentMappingsSectionRoleReferenceValue6;
$memberEnrollmentMappingsSectionRoleReferenceValue7 = new SectionRoleReferenceValue();
$memberEnrollmentMappingsSectionRoleReferenceValue7->setOdataType('#microsoft.graph.industryData.sectionRoleReferenceValue');
$memberEnrollmentMappingsSectionRoleReferenceValue7->setCode('physicalTherapist');
$memberEnrollmentMappingsArray []= $memberEnrollmentMappingsSectionRoleReferenceValue7;
$memberEnrollmentMappingsSectionRoleReferenceValue8 = new SectionRoleReferenceValue();
$memberEnrollmentMappingsSectionRoleReferenceValue8->setOdataType('#microsoft.graph.industryData.sectionRoleReferenceValue');
$memberEnrollmentMappingsSectionRoleReferenceValue8->setCode('speechTherapist');
$memberEnrollmentMappingsArray []= $memberEnrollmentMappingsSectionRoleReferenceValue8;
$memberEnrollmentMappingsSectionRoleReferenceValue9 = new SectionRoleReferenceValue();
$memberEnrollmentMappingsSectionRoleReferenceValue9->setOdataType('#microsoft.graph.industryData.sectionRoleReferenceValue');
$memberEnrollmentMappingsSectionRoleReferenceValue9->setCode('visionTherapist');
$memberEnrollmentMappingsArray []= $memberEnrollmentMappingsSectionRoleReferenceValue9;
$memberEnrollmentMappingsSectionRoleReferenceValue10 = new SectionRoleReferenceValue();
$memberEnrollmentMappingsSectionRoleReferenceValue10->setOdataType('#microsoft.graph.industryData.sectionRoleReferenceValue');
$memberEnrollmentMappingsSectionRoleReferenceValue10->setCode('occupationalTherapist');
$memberEnrollmentMappingsArray []= $memberEnrollmentMappingsSectionRoleReferenceValue10;
$memberEnrollmentMappingsSectionRoleReferenceValue11 = new SectionRoleReferenceValue();
$memberEnrollmentMappingsSectionRoleReferenceValue11->setOdataType('#microsoft.graph.industryData.sectionRoleReferenceValue');
$memberEnrollmentMappingsSectionRoleReferenceValue11->setCode('staff');
$memberEnrollmentMappingsArray []= $memberEnrollmentMappingsSectionRoleReferenceValue11;
$configurationEnrollmentMappings->setMemberEnrollmentMappings($memberEnrollmentMappingsArray);

$configuration->setEnrollmentMappings($configurationEnrollmentMappings);
$requestBody->setConfiguration($configuration);

$result = $graphServiceClient->external()->industryData()->outboundProvisioningFlowSets()->byOutboundProvisioningFlowSetId('outboundProvisioningFlowSet-id')->provisioningFlows()->post($requestBody)->wait();
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
"courseSubject"
"courseGradeLevel"
"courseExternalId"
"academicSessionTitle"
"academicSessionExternalId"
)
additionalOptions = @{
"@odata.type" = "#microsoft.graph.industryData.additionalClassGroupOptions"
createTeam = $true
writeDisplayNameOnCreateOnly = $true
}
enrollmentMappings = @{
"@odata.type" = "#microsoft.graph.industryData.enrollmentMappings"
ownerEnrollmentMappings = @(
@{
"@odata.type" = "#microsoft.graph.industryData.sectionRoleReferenceValue"
code = "teacher"
}
@{
"@odata.type" = "#microsoft.graph.industryData.sectionRoleReferenceValue"
code = "proctor"
}
@{
"@odata.type" = "#microsoft.graph.industryData.sectionRoleReferenceValue"
code = "teacherAssistant"
}
@{
"@odata.type" = "#microsoft.graph.industryData.sectionRoleReferenceValue"
code = "paraProfessional"
}
@{
"@odata.type" = "#microsoft.graph.industryData.sectionRoleReferenceValue"
code = "physicalTherapist"
}
@{
"@odata.type" = "#microsoft.graph.industryData.sectionRoleReferenceValue"
code = "speechTherapist"
}
@{
"@odata.type" = "#microsoft.graph.industryData.sectionRoleReferenceValue"
code = "visionTherapist"
}
@{
"@odata.type" = "#microsoft.graph.industryData.sectionRoleReferenceValue"
code = "occupationalTherapist"
}
@{
"@odata.type" = "#microsoft.graph.industryData.sectionRoleReferenceValue"
code = "staff"
}
)
memberEnrollmentMappings = @(
@{
"@odata.type" = "#microsoft.graph.industryData.sectionRoleReferenceValue"
code = "student"
}
@{
"@odata.type" = "#microsoft.graph.industryData.sectionRoleReferenceValue"
code = "substitute"
}
@{
"@odata.type" = "#microsoft.graph.industryData.sectionRoleReferenceValue"
code = "aide"
}
@{
"@odata.type" = "#microsoft.graph.industryData.sectionRoleReferenceValue"
code = "proctor"
}
@{
"@odata.type" = "#microsoft.graph.industryData.sectionRoleReferenceValue"
code = "teacherAssistant"
}
@{
"@odata.type" = "#microsoft.graph.industryData.sectionRoleReferenceValue"
code = "paraProfessional"
}
@{
"@odata.type" = "#microsoft.graph.industryData.sectionRoleReferenceValue"
code = "physicalTherapist"
}
@{
"@odata.type" = "#microsoft.graph.industryData.sectionRoleReferenceValue"
code = "speechTherapist"
}
@{
"@odata.type" = "#microsoft.graph.industryData.sectionRoleReferenceValue"
code = "visionTherapist"
}
@{
"@odata.type" = "#microsoft.graph.industryData.sectionRoleReferenceValue"
code = "occupationalTherapist"
}
@{
"@odata.type" = "#microsoft.graph.industryData.sectionRoleReferenceValue"
code = "staff"
}
)
}
}
}

New-MgBetaExternalIndustryDataOutboundProvisioningFlowSetProvisioningFlow -OutboundProvisioningFlowSetId $outboundProvisioningFlowSetId -BodyParameter $params
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
			AdditionalClassGroupAttributes.CourseSubject,
			AdditionalClassGroupAttributes.CourseGradeLevel,
			AdditionalClassGroupAttributes.CourseExternalId,
			AdditionalClassGroupAttributes.AcademicSessionTitle,
			AdditionalClassGroupAttributes.AcademicSessionExternalId,
		],
		additional_options = AdditionalClassGroupOptions(
			odata_type = "#microsoft.graph.industryData.additionalClassGroupOptions",
			create_team = True,
			write_display_name_on_create_only = True,
		),
		enrollment_mappings = EnrollmentMappings(
			odata_type = "#microsoft.graph.industryData.enrollmentMappings",
			owner_enrollment_mappings = [
				SectionRoleReferenceValue(
					odata_type = "#microsoft.graph.industryData.sectionRoleReferenceValue",
					code = "teacher",
				),
				SectionRoleReferenceValue(
					odata_type = "#microsoft.graph.industryData.sectionRoleReferenceValue",
					code = "proctor",
				),
				SectionRoleReferenceValue(
					odata_type = "#microsoft.graph.industryData.sectionRoleReferenceValue",
					code = "teacherAssistant",
				),
				SectionRoleReferenceValue(
					odata_type = "#microsoft.graph.industryData.sectionRoleReferenceValue",
					code = "paraProfessional",
				),
				SectionRoleReferenceValue(
					odata_type = "#microsoft.graph.industryData.sectionRoleReferenceValue",
					code = "physicalTherapist",
				),
				SectionRoleReferenceValue(
					odata_type = "#microsoft.graph.industryData.sectionRoleReferenceValue",
					code = "speechTherapist",
				),
				SectionRoleReferenceValue(
					odata_type = "#microsoft.graph.industryData.sectionRoleReferenceValue",
					code = "visionTherapist",
				),
				SectionRoleReferenceValue(
					odata_type = "#microsoft.graph.industryData.sectionRoleReferenceValue",
					code = "occupationalTherapist",
				),
				SectionRoleReferenceValue(
					odata_type = "#microsoft.graph.industryData.sectionRoleReferenceValue",
					code = "staff",
				),
			],
			member_enrollment_mappings = [
				SectionRoleReferenceValue(
					odata_type = "#microsoft.graph.industryData.sectionRoleReferenceValue",
					code = "student",
				),
				SectionRoleReferenceValue(
					odata_type = "#microsoft.graph.industryData.sectionRoleReferenceValue",
					code = "substitute",
				),
				SectionRoleReferenceValue(
					odata_type = "#microsoft.graph.industryData.sectionRoleReferenceValue",
					code = "aide",
				),
				SectionRoleReferenceValue(
					odata_type = "#microsoft.graph.industryData.sectionRoleReferenceValue",
					code = "proctor",
				),
				SectionRoleReferenceValue(
					odata_type = "#microsoft.graph.industryData.sectionRoleReferenceValue",
					code = "teacherAssistant",
				),
				SectionRoleReferenceValue(
					odata_type = "#microsoft.graph.industryData.sectionRoleReferenceValue",
					code = "paraProfessional",
				),
				SectionRoleReferenceValue(
					odata_type = "#microsoft.graph.industryData.sectionRoleReferenceValue",
					code = "physicalTherapist",
				),
				SectionRoleReferenceValue(
					odata_type = "#microsoft.graph.industryData.sectionRoleReferenceValue",
					code = "speechTherapist",
				),
				SectionRoleReferenceValue(
					odata_type = "#microsoft.graph.industryData.sectionRoleReferenceValue",
					code = "visionTherapist",
				),
				SectionRoleReferenceValue(
					odata_type = "#microsoft.graph.industryData.sectionRoleReferenceValue",
					code = "occupationalTherapist",
				),
				SectionRoleReferenceValue(
					odata_type = "#microsoft.graph.industryData.sectionRoleReferenceValue",
					code = "staff",
				),
			],
		),
	),
)

result = await graph_client.external.industry_data.outbound_provisioning_flow_sets.by_outbound_provisioning_flow_set_id('outboundProvisioningFlowSet-id').provisioning_flows.post(request_body)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-type: application/json

{
    "@odata.context": "https://graph.microsoft.com/beta/$metadata#external/industryData/outboundProvisioningFlowSets('9ab41255-5364-4c53-e15c-08dc4ab6ee03')/provisioningFlows/$entity",
    "@odata.type": "#microsoft.graph.industryData.classGroupProvisioningFlow",
    "id": "417a82c8-7caa-4f82-3ac6-08dc4ac6fb7f",
    "createdDateTime": "2024-03-22T23:34:18.5035988Z",
    "lastModifiedDateTime": "2024-03-22T23:34:18.5035988Z",
    "readinessStatus": "notReady",
    "configuration": {
        "additionalAttributes": [
            "courseTitle",
            "courseCode",
            "courseSubject",
            "courseGradeLevel",
            "courseExternalId",
            "academicSessionTitle",
            "academicSessionExternalId"
        ],
        "additionalOptions": {
            "createTeam": true,
            "writeDisplayNameOnCreateOnly": true
        },
        "enrollmentMappings": {
            "ownerEnrollmentMappings": [
                {
                    "code": "teacher"
                },
                {
                    "code": "proctor"
                },
                {
                    "code": "teacherAssistant"
                },
                {
                    "code": "paraprofessional"
                },
                {
                    "code": "physicalTherapist"
                },
                {
                    "code": "speechTherapist"
                },
                {
                    "code": "visionTherapist"
                },
                {
                    "code": "occupationalTherapist"
                },
                {
                    "code": "staff"
                }
            ],
            "memberEnrollmentMappings": [
                {
                    "code": "student"
                },
                {
                    "code": "substitute"
                },
                {
                    "code": "aide"
                },
                {
                    "code": "proctor"
                },
                {
                    "code": "teacherAssistant"
                },
                {
                    "code": "paraprofessional"
                },
                {
                    "code": "physicalTherapist"
                },
                {
                    "code": "speechTherapist"
                },
                {
                    "code": "visionTherapist"
                },
                {
                    "code": "occupationalTherapist"
                },
                {
                    "code": "staff"
                }
            ]
        }
    }
}
```

### Example 3: Create a securityGroupProvisioningFlow

#### Request

The following example shows a request.

- [HTTP](#tabpanel_3_http)
- [C#](#tabpanel_3_csharp)
- [Go](#tabpanel_3_go)
- [Java](#tabpanel_3_java)
- [JavaScript](#tabpanel_3_javascript)
- [PHP](#tabpanel_3_php)
- [PowerShell](#tabpanel_3_powershell)
- [Python](#tabpanel_3_python)

```http
POST https://graph.microsoft.com/beta/external/industryData/OutboundProvisioningFlowSets/9ab41255-5364-4c53-e15c-08dc4ab6ee03/provisioningFlows
Content-type: application/json

{
  "@odata.type": "#microsoft.graph.industryData.securityGroupProvisioningFlow",
  "creationOptions":
  {
    "createBasedOnroleGroup": true,
    "createBasedOnOrgPlusroleGroup": false
  }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.Models.IndustryData;

var requestBody = new SecurityGroupProvisioningFlow
{
	OdataType = "#microsoft.graph.industryData.securityGroupProvisioningFlow",
	CreationOptions = new SecurityGroupCreationOptions
	{
		CreateBasedOnroleGroup = true,
		CreateBasedOnOrgPlusroleGroup = false,
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.External.IndustryData.OutboundProvisioningFlowSets["{outboundProvisioningFlowSet-id}"].ProvisioningFlows.PostAsync(requestBody);
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
creationOptions := graphmodelsindustrydata.NewSecurityGroupCreationOptions()
createBasedOnroleGroup := true
creationOptions.SetCreateBasedOnroleGroup(&createBasedOnroleGroup) 
createBasedOnOrgPlusroleGroup := false
creationOptions.SetCreateBasedOnOrgPlusroleGroup(&createBasedOnOrgPlusroleGroup) 
requestBody.SetCreationOptions(creationOptions)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
provisioningFlows, err := graphClient.External().IndustryData().OutboundProvisioningFlowSets().ByOutboundProvisioningFlowSetId("outboundProvisioningFlowSet-id").ProvisioningFlows().Post(context.Background(), requestBody, nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.beta.models.industrydata.SecurityGroupProvisioningFlow provisioningFlow = new com.microsoft.graph.beta.models.industrydata.SecurityGroupProvisioningFlow();
provisioningFlow.setOdataType("#microsoft.graph.industryData.securityGroupProvisioningFlow");
com.microsoft.graph.beta.models.industrydata.SecurityGroupCreationOptions creationOptions = new com.microsoft.graph.beta.models.industrydata.SecurityGroupCreationOptions();
creationOptions.setCreateBasedOnroleGroup(true);
creationOptions.setCreateBasedOnOrgPlusroleGroup(false);
provisioningFlow.setCreationOptions(creationOptions);
com.microsoft.graph.models.industrydata.ProvisioningFlow result = graphClient.external().industryData().outboundProvisioningFlowSets().byOutboundProvisioningFlowSetId("{outboundProvisioningFlowSet-id}").provisioningFlows().post(provisioningFlow);
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
  '@odata.type': '#microsoft.graph.industryData.securityGroupProvisioningFlow',
  creationOptions: 
  {
    createBasedOnroleGroup: true,
    createBasedOnOrgPlusroleGroup: false
  }
};

await client.api('/external/industryData/OutboundProvisioningFlowSets/9ab41255-5364-4c53-e15c-08dc4ab6ee03/provisioningFlows')
	.version('beta')
	.post(provisioningFlow);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Models\IndustryData\SecurityGroupProvisioningFlow;
use Microsoft\Graph\Beta\Generated\Models\IndustryData\SecurityGroupCreationOptions;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new SecurityGroupProvisioningFlow();
$requestBody->setOdataType('#microsoft.graph.industryData.securityGroupProvisioningFlow');
$creationOptions = new SecurityGroupCreationOptions();
$creationOptions->setCreateBasedOnroleGroup(true);
$creationOptions->setCreateBasedOnOrgPlusroleGroup(false);
$requestBody->setCreationOptions($creationOptions);

$result = $graphServiceClient->external()->industryData()->outboundProvisioningFlowSets()->byOutboundProvisioningFlowSetId('outboundProvisioningFlowSet-id')->provisioningFlows()->post($requestBody)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Beta.Search

$params = @{
	"@odata.type" = "#microsoft.graph.industryData.securityGroupProvisioningFlow"
	creationOptions = @{
		createBasedOnroleGroup = $true
		createBasedOnOrgPlusroleGroup = $false
	}
}

New-MgBetaExternalIndustryDataOutboundProvisioningFlowSetProvisioningFlow -OutboundProvisioningFlowSetId $outboundProvisioningFlowSetId -BodyParameter $params
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.models.industry_data.security_group_provisioning_flow import SecurityGroupProvisioningFlow
from msgraph_beta.generated.models.industry_data.security_group_creation_options import SecurityGroupCreationOptions
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = SecurityGroupProvisioningFlow(
	odata_type = "#microsoft.graph.industryData.securityGroupProvisioningFlow",
	creation_options = SecurityGroupCreationOptions(
		create_based_onrole_group = True,
		create_based_on_org_plusrole_group = False,
	),
)

result = await graph_client.external.industry_data.outbound_provisioning_flow_sets.by_outbound_provisioning_flow_set_id('outboundProvisioningFlowSet-id').provisioning_flows.post(request_body)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-type: application/json

{
    "@odata.context": "https://graph.microsoft.com/beta/$metadata#external/industryData/outboundProvisioningFlowSets('9ab41255-5364-4c53-e15c-08dc4ab6ee03')/provisioningFlows/$entity",
    "@odata.type": "#microsoft.graph.industryData.securityGroupProvisioningFlow",
    "id": "4598f62a-7bd9-40a1-d38a-08dc4ac68cf2",
    "createdDateTime": "2024-03-22T23:55:06.3141592Z",
    "lastModifiedDateTime": "2024-03-22T23:55:06.3141592Z",
    "readinessStatus": "notReady",
    "creationOptions": {
        "createBasedOnRoleGroup": true,
        "createBasedOnOrgPlusRoleGroup": false
    }
}
```

### Example 4: Create a userProvisioningFlow

#### Request

The following example shows a request.

- [HTTP](#tabpanel_4_http)
- [C#](#tabpanel_4_csharp)
- [Go](#tabpanel_4_go)
- [Java](#tabpanel_4_java)
- [JavaScript](#tabpanel_4_javascript)
- [PHP](#tabpanel_4_php)
- [PowerShell](#tabpanel_4_powershell)
- [Python](#tabpanel_4_python)

```http
POST https://graph.microsoft.com/beta/external/industryData/OutboundProvisioningFlowSets/9ab41255-5364-4c53-e15c-08dc4ab6ee03/provisioningFlows
Content-type: application/json

{
    "@odata.type": "#microsoft.graph.industryData.userProvisioningFlow",
    "createUnmatchedUsers": true,
    "managementOptions":
    {
        "additionalAttributes": ["userGradeLevel"],
        "additionalOptions":
        {
            "studentAgeGroup": "minor",
            "allowStudentContactAssociation"  : false
        }
    },
    "creationOptions":
    {
        "configurations": [
          {
            "roleGroup@odata.bind": "https://graph.microsoft.com/beta/external/industryData/roleGroups/staff",
            "defaultPasswordSettings":
            {
              "@odata.type": "#microsoft.graph.industryData.simplePasswordSettings",
              "password": "********"
            },
            "licenseSkus": [ "Sku1"]
          },
          {
            "roleGroup@odata.bind": "https://graph.microsoft.com/beta/external/industryData/roleGroups/students",
            "defaultPasswordSettings":
            {
              "@odata.type": "#microsoft.graph.industryData.simplePasswordSettings",
              "password": "********"
            },
            "licenseSkus": [ "Sku2"]
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
			AllowStudentContactAssociation = false,
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
					"Sku1",
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
					"Sku2",
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
var result = await graphClient.External.IndustryData.OutboundProvisioningFlowSets["{outboundProvisioningFlowSet-id}"].ProvisioningFlows.PostAsync(requestBody);
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
allowStudentContactAssociation := false
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
	"Sku1",
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
	"Sku2",
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
provisioningFlows, err := graphClient.External().IndustryData().OutboundProvisioningFlowSets().ByOutboundProvisioningFlowSetId("outboundProvisioningFlowSet-id").ProvisioningFlows().Post(context.Background(), requestBody, nil)
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
additionalOptions.setAllowStudentContactAssociation(false);
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
licenseSkus.add("Sku1");
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
licenseSkus1.add("Sku2");
userConfiguration1.setLicenseSkus(licenseSkus1);
HashMap<String, Object> additionalData1 = new HashMap<String, Object>();
additionalData1.put("roleGroup@odata.bind", "https://graph.microsoft.com/beta/external/industryData/roleGroups/students");
userConfiguration1.setAdditionalData(additionalData1);
configurations.add(userConfiguration1);
creationOptions.setConfigurations(configurations);
provisioningFlow.setCreationOptions(creationOptions);
com.microsoft.graph.models.industrydata.ProvisioningFlow result = graphClient.external().industryData().outboundProvisioningFlowSets().byOutboundProvisioningFlowSetId("{outboundProvisioningFlowSet-id}").provisioningFlows().post(provisioningFlow);
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
    managementOptions: 
    {
        additionalAttributes: ['userGradeLevel'],
        additionalOptions: 
        {
            studentAgeGroup: 'minor',
            allowStudentContactAssociation: false
        }
    },
    creationOptions: 
    {
        configurations: [
          {
            'roleGroup@odata.bind': 'https://graph.microsoft.com/beta/external/industryData/roleGroups/staff',
            defaultPasswordSettings: 
            {
              '@odata.type': '#microsoft.graph.industryData.simplePasswordSettings',
              password: '********'
            },
            licenseSkus: [ 'Sku1']
          },
          {
            'roleGroup@odata.bind': 'https://graph.microsoft.com/beta/external/industryData/roleGroups/students',
            defaultPasswordSettings: 
            {
              '@odata.type': '#microsoft.graph.industryData.simplePasswordSettings',
              password: '********'
            },
            licenseSkus: [ 'Sku2']
          }
        ]
    }
};

await client.api('/external/industryData/OutboundProvisioningFlowSets/9ab41255-5364-4c53-e15c-08dc4ab6ee03/provisioningFlows')
	.version('beta')
	.post(provisioningFlow);
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
$managementOptionsAdditionalOptions->setAllowStudentContactAssociation(false);
$managementOptions->setAdditionalOptions($managementOptionsAdditionalOptions);
$requestBody->setManagementOptions($managementOptions);
$creationOptions = new UserCreationOptions();
$configurationsUserConfiguration1 = new UserConfiguration();
$configurationsUserConfiguration1DefaultPasswordSettings = new SimplePasswordSettings();
$configurationsUserConfiguration1DefaultPasswordSettings->setOdataType('#microsoft.graph.industryData.simplePasswordSettings');
$configurationsUserConfiguration1DefaultPasswordSettings->setPassword('********');
$configurationsUserConfiguration1->setDefaultPasswordSettings($configurationsUserConfiguration1DefaultPasswordSettings);
$configurationsUserConfiguration1->setLicenseSkus(['Sku1', 	]);
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
$configurationsUserConfiguration2->setLicenseSkus(['Sku2', 	]);
$additionalData = [
	'roleGroup@odata.bind' => 'https://graph.microsoft.com/beta/external/industryData/roleGroups/students',
];
$configurationsUserConfiguration2->setAdditionalData($additionalData);
$configurationsArray []= $configurationsUserConfiguration2;
$creationOptions->setConfigurations($configurationsArray);

$requestBody->setCreationOptions($creationOptions);

$result = $graphServiceClient->external()->industryData()->outboundProvisioningFlowSets()->byOutboundProvisioningFlowSetId('outboundProvisioningFlowSet-id')->provisioningFlows()->post($requestBody)->wait();
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
		allowStudentContactAssociation = $false
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
			"Sku1"
		)
	}
	@{
		"roleGroup@odata.bind" = "https://graph.microsoft.com/beta/external/industryData/roleGroups/students"
		defaultPasswordSettings = @{
			"@odata.type" = "#microsoft.graph.industryData.simplePasswordSettings"
			password = "********"
		}
		licenseSkus = @(
		"Sku2"
	)
}
)
}
}

New-MgBetaExternalIndustryDataOutboundProvisioningFlowSetProvisioningFlow -OutboundProvisioningFlowSetId $outboundProvisioningFlowSetId -BodyParameter $params
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
			allow_student_contact_association = False,
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
					"Sku1",
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
					"Sku2",
				],
				additional_data = {
						"role_group@odata_bind" : "https://graph.microsoft.com/beta/external/industryData/roleGroups/students",
				}
			),
		],
	),
)

result = await graph_client.external.industry_data.outbound_provisioning_flow_sets.by_outbound_provisioning_flow_set_id('outboundProvisioningFlowSet-id').provisioning_flows.post(request_body)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-type: application/json

{
    "@odata.context": "https://graph.microsoft.com/beta/$metadata#external/industryData/outboundProvisioningFlowSets('9ab41255-5364-4c53-e15c-08dc4ab6ee03')/provisioningFlows/$entity",
    "@odata.type": "#microsoft.graph.industryData.userProvisioningFlow",
    "id": "dbd36d16-c574-4ed8-3ac7-08dc4ac6fb7f",
    "createdDateTime": "2024-03-23T00:24:32.3286035Z",
    "lastModifiedDateTime": "2024-03-23T00:24:32.3286035Z",
    "readinessStatus": "notReady",
    "createUnmatchedUsers": true,
    "managementOptions": {
        "additionalAttributes": [
            "userGradeLevel"
        ],
        "additionalOptions": {
            "markAllStudentsAsMinors": true,
            "allowStudentContactAssociation": false,
            "studentAgeGroup": "minor"
        }
    },
    "creationOptions": {
        "configurations": [
            {
                "licenseSkus": [
                    "Sku1"
                ],
                "defaultPasswordSettings": {
                    "@odata.type": "#microsoft.graph.industryData.simplePasswordSettings",
                    "password": "***************"
                }
            },
            {
                "licenseSkus": [
                    "Sku2"
                ],
                "defaultPasswordSettings": {
                    "@odata.type": "#microsoft.graph.industryData.simplePasswordSettings",
                    "password": "***************"
                }
            }
        ]
    }
}
```
