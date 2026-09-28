<!-- Source: https://learn.microsoft.com/en-us/graph/api/security-casemanagement-case-update?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-08-20 -->

# Update case management case

Namespace: microsoft.graph.security.caseManagement

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Update the properties of a [microsoft.graph.security.caseManagement.case](https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-case?view=graph-rest-beta) object.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | CaseManagement.ReadWrite.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | CaseManagement.ReadWrite.All | Not available. |

Important

For delegated access using work or school accounts, the signed-in user must be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) or a custom role that grants the permissions required for this operation. This API supports the following built-in roles:

- Global Reader
- Security Reader
- Security Operator
- Security Administrator

## HTTP request

```http
PATCH /security/caseManagement/cases/{caseId}
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply *only* the values for properties to update. Existing properties that aren't included in the request body maintain their previous values or are recalculated based on changes to other property values.

The following table specifies the properties that can be updated.

Supply a JSON representation of the resource. For polymorphic resources, include `@odata.type` to identify the concrete case type. The properties that can be updated depend on the case type.

To update **customFields**, call [List customFields](https://learn.microsoft.com/en-us/graph/api/security-casemanagement-casetypeconfiguration-list-customfields?view=graph-rest-beta) at `/security/caseManagement/caseTypeConfigurations/{caseTypeConfigurationId}/customFields`, where `{caseTypeConfigurationId}` matches the case type. Use each definition's **displayName**, not its **id**, as the dynamic property name. The name must match exactly one definition. Each dynamic value must be an object that includes the mapped concrete `@odata.type` and the corresponding **value**, **values**, or **valueDateTime** property from the [custom field value mapping](https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-customfieldvalues?view=graph-rest-beta#custom-field-value-mapping); bare values aren't supported.

For [genericCase](https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-genericcase?view=graph-rest-beta) objects, all properties can be updated except `id`, `createdBy`, `createdDateTime`, `lastModifiedBy`, and `lastModifiedDateTime`, which are inherited from [caseManagementEntity](https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-casemanagemententity?view=graph-rest-beta). The API ignores these properties if you include them in the request body.

The following properties can be updated for all case types.

| Property | Type | Description |
| :--- | :--- | :--- |
| displayName | String | The display name of the case. |
| status | String | The tenant-defined lifecycle status of the case. Use a **displayName** value returned in the status tree by [List statuses](https://learn.microsoft.com/en-us/graph/api/security-casemanagement-casetypeconfiguration-list-statuses?view=graph-rest-beta) from `/security/caseManagement/caseTypeConfigurations/genericCase/statuses` or `/security/caseManagement/caseTypeConfigurations/incidentCase/statuses`, depending on the case type. |

For [genericCase](https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-genericcase?view=graph-rest-beta) objects, you can also update the following properties.

| Property | Type | Description |
| :--- | :--- | :--- |
| assignedTo | String | The user assigned to the generic case. |
| closingNotes | String | Notes recorded when the generic case is closed. |
| customFields | [microsoft.graph.security.caseManagement.customFieldValues](https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-customfieldvalues?view=graph-rest-beta) | Tenant-defined custom field values keyed by the exact **displayName** of each custom field definition. |
| description | String | The description of the generic case. |
| dueDateTime | DateTimeOffset | The target completion date and time for the generic case. |
| priority | String | The priority assigned to the generic case. Possible values are: `veryLow`, `low`, `medium`, `high`, and `critical`. |

For [incidentCase](https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-incidentcase?view=graph-rest-beta) objects, the following properties are synchronized with the underlying incident. A PATCH request that includes any of these properties returns `202 Accepted` with no response body. The changes might take a few minutes to synchronize and appear on the case.

| Property | Type | Description |
| :--- | :--- | :--- |
| assignedTo | String | The user assigned to the incident case. |
| classification | [microsoft.graph.security.caseManagement.incidentClassification](https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-incidentcase?view=graph-rest-beta#incidentclassification-values) | The classification assigned to the incident. |
| determination | [microsoft.graph.security.caseManagement.incidentDetermination](https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-incidentcase?view=graph-rest-beta#incidentdetermination-values) | The determination assigned to the incident. |
| displayName | String | The display name of the incident case. |
| severity | [microsoft.graph.security.caseManagement.incidentSeverity](https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-incidentcase?view=graph-rest-beta#incidentseverity-values) | The severity assigned to the incident. |
| status | String | The tenant-defined lifecycle status of the incident case. Use a **displayName** value returned in the status tree by [List statuses](https://learn.microsoft.com/en-us/graph/api/security-casemanagement-casetypeconfiguration-list-statuses?view=graph-rest-beta) from `/security/caseManagement/caseTypeConfigurations/incidentCase/statuses`. |

The following incident case properties aren't synchronized with the underlying incident. A PATCH request that updates only these properties returns `200 OK` with the updated [incidentCase](https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-incidentcase?view=graph-rest-beta) object in the response body.

| Property | Type | Description |
| :--- | :--- | :--- |
| customFields | [microsoft.graph.security.caseManagement.customFieldValues](https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-customfieldvalues?view=graph-rest-beta) | Tenant-defined custom field values keyed by the exact **displayName** of each custom field definition. |
| dueDateTime | DateTimeOffset | The target completion date and time for the incident case. |

If a PATCH request includes properties from both groups, the method returns `202 Accepted` with no response body.

## Response

If successful, this method returns one of the following response codes:

- For [incidentCase](https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-incidentcase?view=graph-rest-beta) objects, a request that includes any property synchronized with the underlying incident returns `202 Accepted` with no response body. The changes might take a few minutes to synchronize and appear on the case.
- For [incidentCase](https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-incidentcase?view=graph-rest-beta) objects, a request that updates only properties that aren't synchronized returns `200 OK` and an updated [microsoft.graph.security.caseManagement.incidentCase](https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-incidentcase?view=graph-rest-beta) object in the response body.
- For other case types, this method returns a `200 OK` response code and an updated [microsoft.graph.security.caseManagement.case](https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-case?view=graph-rest-beta) object in the response body.

## Examples

### Example 1: Update a generic case

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
PATCH https://graph.microsoft.com/beta/security/caseManagement/cases/{caseId}
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.security.caseManagement.genericCase",
  "displayName": "Case MS-001",
  "status": "Open",
  "description": "Investigating potential credential compromise.",
  "assignedTo": "john.doe@contoso.com",
  "priority": "high",
  "dueDateTime": "2026-06-29T17:54:43Z",
  "closingNotes": "Follow up with the account owner.",
  "customFields": {
    "Customer impact": {
      "@odata.type": "#microsoft.graph.security.caseManagement.customFieldStringValue",
      "value": "Multiple executive mailboxes affected"
    }
  }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.Models.Security.CaseManagement;

var requestBody = new GenericCase
{
	OdataType = "#microsoft.graph.security.caseManagement.genericCase",
	DisplayName = "Case MS-001",
	Status = "Open",
	Description = "Investigating potential credential compromise.",
	AssignedTo = "john.doe@contoso.com",
	Priority = "high",
	DueDateTime = DateTimeOffset.Parse("2026-06-29T17:54:43Z"),
	ClosingNotes = "Follow up with the account owner.",
	CustomFields = new CustomFieldValues
	{
		AdditionalData = new Dictionary<string, object>
		{
			{
				"Customer impact" , new CustomFieldStringValue
				{
					OdataType = "#microsoft.graph.security.caseManagement.customFieldStringValue",
					Value = "Multiple executive mailboxes affected",
				}
			},
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Security.CaseManagement.Cases["{case-id}"].PatchAsync(requestBody);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v0.*

// Dependencies
import (
	  "context"
	  "time"
	  msgraphsdk "github.com/microsoftgraph/msgraph-beta-sdk-go"
	  graphmodelssecuritycasemanagement "github.com/microsoftgraph/msgraph-beta-sdk-go/models/security/casemanagement"
	  //other-imports
)

requestBody := graphmodelssecuritycasemanagement.NewCase()
displayName := "Case MS-001"
requestBody.SetDisplayName(&displayName) 
status := "Open"
requestBody.SetStatus(&status) 
description := "Investigating potential credential compromise."
requestBody.SetDescription(&description) 
assignedTo := "john.doe@contoso.com"
requestBody.SetAssignedTo(&assignedTo) 
priority := "high"
requestBody.SetPriority(&priority) 
dueDateTime , err := time.Parse(time.RFC3339, "2026-06-29T17:54:43Z")
requestBody.SetDueDateTime(&dueDateTime) 
closingNotes := "Follow up with the account owner."
requestBody.SetClosingNotes(&closingNotes) 
customFields := graphmodelssecuritycasemanagement.NewCustomFieldValues()
additionalData := map[string]interface{}{
customer impact := graphmodelssecuritycasemanagement.NewCustomFieldStringValue()
value := "Multiple executive mailboxes affected"
customer impact.SetValue(&value) 
	customFields.SetCustomer impact(customer impact)
}
customFields.SetAdditionalData(additionalData)
requestBody.SetCustomFields(customFields)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
cases, err := graphClient.Security().CaseManagement().Cases().ByCaseId("case-id").Patch(context.Background(), requestBody, nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.beta.models.security.casemanagement.GenericCase caseEscaped = new com.microsoft.graph.beta.models.security.casemanagement.GenericCase();
caseEscaped.setOdataType("#microsoft.graph.security.caseManagement.genericCase");
caseEscaped.setDisplayName("Case MS-001");
caseEscaped.setStatus("Open");
caseEscaped.setDescription("Investigating potential credential compromise.");
caseEscaped.setAssignedTo("john.doe@contoso.com");
caseEscaped.setPriority("high");
OffsetDateTime dueDateTime = OffsetDateTime.parse("2026-06-29T17:54:43Z");
caseEscaped.setDueDateTime(dueDateTime);
caseEscaped.setClosingNotes("Follow up with the account owner.");
com.microsoft.graph.beta.models.security.casemanagement.CustomFieldValues customFields = new com.microsoft.graph.beta.models.security.casemanagement.CustomFieldValues();
HashMap<String, Object> additionalData = new HashMap<String, Object>();
com.microsoft.graph.beta.models.security.casemanagement.CustomFieldStringValue customerImpact = new com.microsoft.graph.beta.models.security.casemanagement.CustomFieldStringValue();
customerImpact.setOdataType("#microsoft.graph.security.caseManagement.customFieldStringValue");
customerImpact.setValue("Multiple executive mailboxes affected");
additionalData.put("Customer impact", customerImpact);
customFields.setAdditionalData(additionalData);
caseEscaped.setCustomFields(customFields);
com.microsoft.graph.models.security.casemanagement.Case result = graphClient.security().caseManagement().cases().byCaseId("{case-id}").patch(caseEscaped);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const _case = {
  '@odata.type': '#microsoft.graph.security.caseManagement.genericCase',
  displayName: 'Case MS-001',
  status: 'Open',
  description: 'Investigating potential credential compromise.',
  assignedTo: 'john.doe@contoso.com',
  priority: 'high',
  dueDateTime: '2026-06-29T17:54:43Z',
  closingNotes: 'Follow up with the account owner.',
  customFields: {
    'Customer impact': {
      '@odata.type': '#microsoft.graph.security.caseManagement.customFieldStringValue',
      value: 'Multiple executive mailboxes affected'
    }
  }
};

await client.api('/security/caseManagement/cases/{caseId}')
	.version('beta')
	.update(_case);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Models\Security\CaseManagement\GenericCase;
use Microsoft\Graph\Beta\Generated\Models\Security\CaseManagement\CustomFieldValues;
use Microsoft\Graph\Beta\Generated\Models\Security\CaseManagement\CustomFieldStringValue;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new GenericCase();
$requestBody->setOdataType('#microsoft.graph.security.caseManagement.genericCase');
$requestBody->setDisplayName('Case MS-001');
$requestBody->setStatus('Open');
$requestBody->setDescription('Investigating potential credential compromise.');
$requestBody->setAssignedTo('john.doe@contoso.com');
$requestBody->setPriority('high');
$requestBody->setDueDateTime(new \DateTime('2026-06-29T17:54:43Z'));
$requestBody->setClosingNotes('Follow up with the account owner.');
$customFields = new CustomFieldValues();
$additionalData = [
	'Customer impact' => [
		'@odata.type' => '#microsoft.graph.security.caseManagement.customFieldStringValue',
		'value' => 'Multiple executive mailboxes affected',
	],
];
$customFields->setAdditionalData($additionalData);
$requestBody->setCustomFields($customFields);

$result = $graphServiceClient->security()->caseManagement()->cases()->byCaseId('case-id')->patch($requestBody)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Beta.Security

$params = @{
	"@odata.type" = "#microsoft.graph.security.caseManagement.genericCase"
	displayName = "Case MS-001"
	status = "Open"
	description = "Investigating potential credential compromise."
	assignedTo = "john.doe@contoso.com"
	priority = "high"
	dueDateTime = "2026-06-29T17:54:43Z"
	closingNotes = "Follow up with the account owner."
	customFields = @{
		"Customer impact" = @{
			"@odata.type" = "#microsoft.graph.security.caseManagement.customFieldStringValue"
			value = "Multiple executive mailboxes affected"
		}
	}
}

Update-MgBetaSecurityCaseManagementCase -CaseId $caseId -BodyParameter $params
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.models.security.case_management.generic_case import GenericCase
from msgraph_beta.generated.models.security.case_management.custom_field_values import CustomFieldValues
from msgraph_beta.generated.models.security.case_management.custom_field_string_value import CustomFieldStringValue
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = GenericCase(
	odata_type = "#microsoft.graph.security.caseManagement.genericCase",
	display_name = "Case MS-001",
	status = "Open",
	description = "Investigating potential credential compromise.",
	assigned_to = "john.doe@contoso.com",
	priority = "high",
	due_date_time = "2026-06-29T17:54:43Z",
	closing_notes = "Follow up with the account owner.",
	custom_fields = CustomFieldValues(
		additional_data = {
				"customer impact" : {
						"@odata_type" : "#microsoft.graph.security.caseManagement.customFieldStringValue",
						"value" : "Multiple executive mailboxes affected",
				},
		}
	),
)

result = await graph_client.security.case_management.cases.by_case_id('case-id').patch(request_body)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.security.caseManagement.genericCase",
  "id": "987757fb-6ef4-1061-17e7-9de0d088e1dd",
  "createdDateTime": "2026-05-20T11:12:28Z",
  "createdBy": "user@contoso.com",
  "lastModifiedDateTime": "2026-05-20T11:18:45Z",
  "lastModifiedBy": "user@contoso.com",
  "displayName": "Case MS-001",
  "status": "Open",
  "description": "Investigating potential credential compromise.",
  "assignedTo": "john.doe@contoso.com",
  "priority": "high",
  "dueDateTime": "2026-06-29T17:54:43Z",
  "closingNotes": "Follow up with the account owner.",
  "customFields": {
    "Customer impact": {
      "@odata.type": "#microsoft.graph.security.caseManagement.customFieldStringValue",
      "value": "Multiple executive mailboxes affected"
    }
  }
}
```

### Example 2: Update synchronized incident case properties

#### Request

The following example updates properties that are synchronized with the underlying incident.

- [HTTP](#tabpanel_2_http)
- [C#](#tabpanel_2_csharp)
- [Go](#tabpanel_2_go)
- [Java](#tabpanel_2_java)
- [JavaScript](#tabpanel_2_javascript)
- [PHP](#tabpanel_2_php)
- [PowerShell](#tabpanel_2_powershell)
- [Python](#tabpanel_2_python)

```http
PATCH https://graph.microsoft.com/beta/security/caseManagement/cases/{caseId}
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.security.caseManagement.incidentCase",
  "displayName": "Incident Case MS-002",
  "status": "InProgress",
  "classification": "truePositive",
  "determination": "phishing",
  "severity": "high"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.Models.Security.CaseManagement;

var requestBody = new IncidentCase
{
	OdataType = "#microsoft.graph.security.caseManagement.incidentCase",
	DisplayName = "Incident Case MS-002",
	Status = "InProgress",
	Classification = IncidentClassification.TruePositive,
	Determination = IncidentDetermination.Phishing,
	Severity = IncidentSeverity.High,
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Security.CaseManagement.Cases["{case-id}"].PatchAsync(requestBody);
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
	  graphmodelssecuritycasemanagement "github.com/microsoftgraph/msgraph-beta-sdk-go/models/security/casemanagement"
	  //other-imports
)

requestBody := graphmodelssecuritycasemanagement.NewCase()
displayName := "Incident Case MS-002"
requestBody.SetDisplayName(&displayName) 
status := "InProgress"
requestBody.SetStatus(&status) 
classification := graphmodels.TRUEPOSITIVE_INCIDENTCLASSIFICATION 
requestBody.SetClassification(&classification) 
determination := graphmodels.PHISHING_INCIDENTDETERMINATION 
requestBody.SetDetermination(&determination) 
severity := graphmodels.HIGH_INCIDENTSEVERITY 
requestBody.SetSeverity(&severity) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
cases, err := graphClient.Security().CaseManagement().Cases().ByCaseId("case-id").Patch(context.Background(), requestBody, nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.beta.models.security.casemanagement.IncidentCase caseEscaped = new com.microsoft.graph.beta.models.security.casemanagement.IncidentCase();
caseEscaped.setOdataType("#microsoft.graph.security.caseManagement.incidentCase");
caseEscaped.setDisplayName("Incident Case MS-002");
caseEscaped.setStatus("InProgress");
caseEscaped.setClassification(com.microsoft.graph.beta.models.security.casemanagement.IncidentClassification.TruePositive);
caseEscaped.setDetermination(com.microsoft.graph.beta.models.security.casemanagement.IncidentDetermination.Phishing);
caseEscaped.setSeverity(com.microsoft.graph.beta.models.security.casemanagement.IncidentSeverity.High);
com.microsoft.graph.models.security.casemanagement.Case result = graphClient.security().caseManagement().cases().byCaseId("{case-id}").patch(caseEscaped);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const _case = {
  '@odata.type': '#microsoft.graph.security.caseManagement.incidentCase',
  displayName: 'Incident Case MS-002',
  status: 'InProgress',
  classification: 'truePositive',
  determination: 'phishing',
  severity: 'high'
};

await client.api('/security/caseManagement/cases/{caseId}')
	.version('beta')
	.update(_case);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Models\Security\CaseManagement\IncidentCase;
use Microsoft\Graph\Beta\Generated\Models\Security\CaseManagement\IncidentClassification;
use Microsoft\Graph\Beta\Generated\Models\Security\CaseManagement\IncidentDetermination;
use Microsoft\Graph\Beta\Generated\Models\Security\CaseManagement\IncidentSeverity;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new IncidentCase();
$requestBody->setOdataType('#microsoft.graph.security.caseManagement.incidentCase');
$requestBody->setDisplayName('Incident Case MS-002');
$requestBody->setStatus('InProgress');
$requestBody->setClassification(new IncidentClassification('truePositive'));
$requestBody->setDetermination(new IncidentDetermination('phishing'));
$requestBody->setSeverity(new IncidentSeverity('high'));

$result = $graphServiceClient->security()->caseManagement()->cases()->byCaseId('case-id')->patch($requestBody)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Beta.Security

$params = @{
	"@odata.type" = "#microsoft.graph.security.caseManagement.incidentCase"
	displayName = "Incident Case MS-002"
	status = "InProgress"
	classification = "truePositive"
	determination = "phishing"
	severity = "high"
}

Update-MgBetaSecurityCaseManagementCase -CaseId $caseId -BodyParameter $params
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.models.security.case_management.incident_case import IncidentCase
from msgraph_beta.generated.models.incident_classification import IncidentClassification
from msgraph_beta.generated.models.incident_determination import IncidentDetermination
from msgraph_beta.generated.models.incident_severity import IncidentSeverity
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = IncidentCase(
	odata_type = "#microsoft.graph.security.caseManagement.incidentCase",
	display_name = "Incident Case MS-002",
	status = "InProgress",
	classification = IncidentClassification.TruePositive,
	determination = IncidentDetermination.Phishing,
	severity = IncidentSeverity.High,
)

result = await graph_client.security.case_management.cases.by_case_id('case-id').patch(request_body)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

```http
HTTP/1.1 202 Accepted
```
