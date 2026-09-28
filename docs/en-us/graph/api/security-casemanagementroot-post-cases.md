<!-- Source: https://learn.microsoft.com/en-us/graph/api/security-casemanagementroot-post-cases?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-08-20 -->

# Create case management case

Namespace: microsoft.graph.security.caseManagement

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Create a [case](https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-case?view=graph-rest-beta) object in case management.

Important

You can't use this API to create [incidentCase](https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-incidentcase?view=graph-rest-beta) objects. Incident cases are created by the service; API requests can't create new incident cases.

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
POST /security/caseManagement/cases
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the [case](https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-case?view=graph-rest-beta) object. Include `@odata.type` to identify a supported derived type. The `microsoft.graph.security.caseManagement.incidentCase` derived type isn't supported for create requests.

When creating a [genericCase](https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-genericcase?view=graph-rest-beta) object, you can specify all its properties except `id`, `createdBy`, `createdDateTime`, `lastModifiedBy`, and `lastModifiedDateTime`, which are inherited from [caseManagementEntity](https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-casemanagemententity?view=graph-rest-beta). The API ignores these properties if you include them in the request body.

Before constructing **customFields**, call [List customFields](https://learn.microsoft.com/en-us/graph/api/security-casemanagement-casetypeconfiguration-list-customfields?view=graph-rest-beta) at `/security/caseManagement/caseTypeConfigurations/genericCase/customFields`. Use each definition's **displayName**, not its **id**, as the dynamic property name. The name must match exactly one definition. Each dynamic value must be an object that includes the mapped concrete `@odata.type` and the corresponding **value**, **values**, or **valueDateTime** property from the [custom field value mapping](https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-customfieldvalues?view=graph-rest-beta#custom-field-value-mapping); bare values aren't supported.

| Property | Type | Description |
| :--- | :--- | :--- |
| assignedTo | String | The user assigned to the generic case. Optional. |
| closingNotes | String | Notes recorded when the generic case is closed. Optional. |
| customFields | [microsoft.graph.security.caseManagement.customFieldValues](https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-customfieldvalues?view=graph-rest-beta) | Tenant-defined custom field values keyed by the exact **displayName** of each custom field definition. Optional. |
| description | String | The description of the generic case. Optional. |
| displayName | String | The display name of the resource. Required. |
| dueDateTime | DateTimeOffset | The target completion date and time for the generic case. Optional. |
| priority | String | The priority assigned to the generic case. Possible values are: `veryLow`, `low`, `medium`, `high`, and `critical`. Optional. |
| status | String | The tenant-defined lifecycle status of the generic case. Use a **displayName** value returned in the status tree by [List statuses](https://learn.microsoft.com/en-us/graph/api/security-casemanagement-casetypeconfiguration-list-statuses?view=graph-rest-beta) from `/security/caseManagement/caseTypeConfigurations/genericCase/statuses`. Required. |

## Response

If successful, this method returns a `201 Created` response code and a [microsoft.graph.security.caseManagement.case](https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-case?view=graph-rest-beta) object in the response body.

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
POST https://graph.microsoft.com/beta/security/caseManagement/cases
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.security.caseManagement.genericCase",
  "displayName": "Security Breach Investigation",
  "status": "active",
  "description": "Investigating potential credential compromise.",
  "assignedTo": "john.doe@contoso.com",
  "priority": "high",
  "customFields": {
    "Customer impact": {
      "@odata.type": "#microsoft.graph.security.caseManagement.customFieldStringValue",
      "value": "Executive mailbox affected"
    },
    "Affected users": {
      "@odata.type": "#microsoft.graph.security.caseManagement.customFieldNumberValue",
      "value": 12
    },
    "Review date": {
      "@odata.type": "#microsoft.graph.security.caseManagement.customFieldDateTimeValue",
      "valueDateTime": "2026-06-15T09:00:00Z"
    },
    "Affected services": {
      "@odata.type": "#microsoft.graph.security.caseManagement.customFieldOptionsValue",
      "values": [
        "Exchange Online",
        "Microsoft Teams"
      ]
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
	DisplayName = "Security Breach Investigation",
	Status = "active",
	Description = "Investigating potential credential compromise.",
	AssignedTo = "john.doe@contoso.com",
	Priority = "high",
	CustomFields = new CustomFieldValues
	{
		AdditionalData = new Dictionary<string, object>
		{
			{
				"Customer impact" , new CustomFieldStringValue
				{
					OdataType = "#microsoft.graph.security.caseManagement.customFieldStringValue",
					Value = "Executive mailbox affected",
				}
			},
			{
				"Affected users" , new CustomFieldNumberValue
				{
					OdataType = "#microsoft.graph.security.caseManagement.customFieldNumberValue",
					Value = 12,
				}
			},
			{
				"Review date" , new CustomFieldDateTimeValue
				{
					OdataType = "#microsoft.graph.security.caseManagement.customFieldDateTimeValue",
					ValueDateTime = DateTimeOffset.Parse("2026-06-15T09:00:00Z"),
				}
			},
			{
				"Affected services" , new CustomFieldOptionsValue
				{
					OdataType = "#microsoft.graph.security.caseManagement.customFieldOptionsValue",
					Values = new List<string>
					{
						"Exchange Online",
						"Microsoft Teams",
					},
				}
			},
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Security.CaseManagement.Cases.PostAsync(requestBody);
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
displayName := "Security Breach Investigation"
requestBody.SetDisplayName(&displayName) 
status := "active"
requestBody.SetStatus(&status) 
description := "Investigating potential credential compromise."
requestBody.SetDescription(&description) 
assignedTo := "john.doe@contoso.com"
requestBody.SetAssignedTo(&assignedTo) 
priority := "high"
requestBody.SetPriority(&priority) 
customFields := graphmodelssecuritycasemanagement.NewCustomFieldValues()
additionalData := map[string]interface{}{
customer impact := graphmodelssecuritycasemanagement.NewCustomFieldStringValue()
value := "Executive mailbox affected"
customer impact.SetValue(&value) 
	customFields.SetCustomer impact(customer impact)
affected users := graphmodelssecuritycasemanagement.NewCustomFieldNumberValue()
value := int32(12)
affected users.SetValue(&value) 
	customFields.SetAffected users(affected users)
review date := graphmodelssecuritycasemanagement.NewCustomFieldDateTimeValue()
valueDateTime , err := time.Parse(time.RFC3339, "2026-06-15T09:00:00Z")
review date.SetValueDateTime(&valueDateTime) 
	customFields.SetReview date(review date)
affected services := graphmodelssecuritycasemanagement.NewCustomFieldOptionsValue()
	values := []string {
		"Exchange Online",
		"Microsoft Teams",
	}
	affected services.SetValues(values)
	customFields.SetAffected services(affected services)
}
customFields.SetAdditionalData(additionalData)
requestBody.SetCustomFields(customFields)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
cases, err := graphClient.Security().CaseManagement().Cases().Post(context.Background(), requestBody, nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.beta.models.security.casemanagement.GenericCase caseEscaped = new com.microsoft.graph.beta.models.security.casemanagement.GenericCase();
caseEscaped.setOdataType("#microsoft.graph.security.caseManagement.genericCase");
caseEscaped.setDisplayName("Security Breach Investigation");
caseEscaped.setStatus("active");
caseEscaped.setDescription("Investigating potential credential compromise.");
caseEscaped.setAssignedTo("john.doe@contoso.com");
caseEscaped.setPriority("high");
com.microsoft.graph.beta.models.security.casemanagement.CustomFieldValues customFields = new com.microsoft.graph.beta.models.security.casemanagement.CustomFieldValues();
HashMap<String, Object> additionalData = new HashMap<String, Object>();
com.microsoft.graph.beta.models.security.casemanagement.CustomFieldStringValue customerImpact = new com.microsoft.graph.beta.models.security.casemanagement.CustomFieldStringValue();
customerImpact.setOdataType("#microsoft.graph.security.caseManagement.customFieldStringValue");
customerImpact.setValue("Executive mailbox affected");
additionalData.put("Customer impact", customerImpact);
com.microsoft.graph.beta.models.security.casemanagement.CustomFieldNumberValue affectedUsers = new com.microsoft.graph.beta.models.security.casemanagement.CustomFieldNumberValue();
affectedUsers.setOdataType("#microsoft.graph.security.caseManagement.customFieldNumberValue");
affectedUsers.setValue(12);
additionalData.put("Affected users", affectedUsers);
com.microsoft.graph.beta.models.security.casemanagement.CustomFieldDateTimeValue reviewDate = new com.microsoft.graph.beta.models.security.casemanagement.CustomFieldDateTimeValue();
reviewDate.setOdataType("#microsoft.graph.security.caseManagement.customFieldDateTimeValue");
OffsetDateTime valueDateTime = OffsetDateTime.parse("2026-06-15T09:00:00Z");
reviewDate.setValueDateTime(valueDateTime);
additionalData.put("Review date", reviewDate);
com.microsoft.graph.beta.models.security.casemanagement.CustomFieldOptionsValue affectedServices = new com.microsoft.graph.beta.models.security.casemanagement.CustomFieldOptionsValue();
affectedServices.setOdataType("#microsoft.graph.security.caseManagement.customFieldOptionsValue");
LinkedList<String> values = new LinkedList<String>();
values.add("Exchange Online");
values.add("Microsoft Teams");
affectedServices.setValues(values);
additionalData.put("Affected services", affectedServices);
customFields.setAdditionalData(additionalData);
caseEscaped.setCustomFields(customFields);
com.microsoft.graph.models.security.casemanagement.Case result = graphClient.security().caseManagement().cases().post(caseEscaped);
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
  displayName: 'Security Breach Investigation',
  status: 'active',
  description: 'Investigating potential credential compromise.',
  assignedTo: 'john.doe@contoso.com',
  priority: 'high',
  customFields: {
    'Customer impact': {
      '@odata.type': '#microsoft.graph.security.caseManagement.customFieldStringValue',
      value: 'Executive mailbox affected'
    },
    'Affected users': {
      '@odata.type': '#microsoft.graph.security.caseManagement.customFieldNumberValue',
      value: 12
    },
    'Review date': {
      '@odata.type': '#microsoft.graph.security.caseManagement.customFieldDateTimeValue',
      valueDateTime: '2026-06-15T09:00:00Z'
    },
    'Affected services': {
      '@odata.type': '#microsoft.graph.security.caseManagement.customFieldOptionsValue',
      values: [
        'Exchange Online',
        'Microsoft Teams'
      ]
    }
  }
};

await client.api('/security/caseManagement/cases')
	.version('beta')
	.post(_case);
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
use Microsoft\Graph\Beta\Generated\Models\Security\CaseManagement\CustomFieldNumberValue;
use Microsoft\Graph\Beta\Generated\Models\Security\CaseManagement\CustomFieldDateTimeValue;
use Microsoft\Graph\Beta\Generated\Models\Security\CaseManagement\CustomFieldOptionsValue;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new GenericCase();
$requestBody->setOdataType('#microsoft.graph.security.caseManagement.genericCase');
$requestBody->setDisplayName('Security Breach Investigation');
$requestBody->setStatus('active');
$requestBody->setDescription('Investigating potential credential compromise.');
$requestBody->setAssignedTo('john.doe@contoso.com');
$requestBody->setPriority('high');
$customFields = new CustomFieldValues();
$additionalData = [
	'Customer impact' => [
		'@odata.type' => '#microsoft.graph.security.caseManagement.customFieldStringValue',
		'value' => 'Executive mailbox affected',
	],
	'Affected users' => [
		'@odata.type' => '#microsoft.graph.security.caseManagement.customFieldNumberValue',
		'value' => 12,
	],
	'Review date' => [
		'@odata.type' => '#microsoft.graph.security.caseManagement.customFieldDateTimeValue',
		'valueDateTime' => new \DateTime('2026-06-15T09:00:00Z'),
	],
	'Affected services' => [
		'@odata.type' => '#microsoft.graph.security.caseManagement.customFieldOptionsValue',
		'values' => [
'Exchange Online', 'Microsoft Teams', ],
	],
];
$customFields->setAdditionalData($additionalData);
$requestBody->setCustomFields($customFields);

$result = $graphServiceClient->security()->caseManagement()->cases()->post($requestBody)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Beta.Security

$params = @{
	"@odata.type" = "#microsoft.graph.security.caseManagement.genericCase"
	displayName = "Security Breach Investigation"
	status = "active"
	description = "Investigating potential credential compromise."
	assignedTo = "john.doe@contoso.com"
	priority = "high"
	customFields = @{
		"Customer impact" = @{
			"@odata.type" = "#microsoft.graph.security.caseManagement.customFieldStringValue"
			value = "Executive mailbox affected"
		}
		"Affected users" = @{
			"@odata.type" = "#microsoft.graph.security.caseManagement.customFieldNumberValue"
			value = 
		}
		"Review date" = @{
			"@odata.type" = "#microsoft.graph.security.caseManagement.customFieldDateTimeValue"
			valueDateTime = "2026-06-15T09:00:00Z"
		}
		"Affected services" = @{
			"@odata.type" = "#microsoft.graph.security.caseManagement.customFieldOptionsValue"
			values = @(
			"Exchange Online"
		"Microsoft Teams"
	)
}
}
}

New-MgBetaSecurityCaseManagementCase -BodyParameter $params
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
from msgraph_beta.generated.models.security.case_management.custom_field_number_value import CustomFieldNumberValue
from msgraph_beta.generated.models.security.case_management.custom_field_date_time_value import CustomFieldDateTimeValue
from msgraph_beta.generated.models.security.case_management.custom_field_options_value import CustomFieldOptionsValue
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = GenericCase(
	odata_type = "#microsoft.graph.security.caseManagement.genericCase",
	display_name = "Security Breach Investigation",
	status = "active",
	description = "Investigating potential credential compromise.",
	assigned_to = "john.doe@contoso.com",
	priority = "high",
	custom_fields = CustomFieldValues(
		additional_data = {
				"customer impact" : {
						"@odata_type" : "#microsoft.graph.security.caseManagement.customFieldStringValue",
						"value" : "Executive mailbox affected",
				},
				"affected users" : {
						"@odata_type" : "#microsoft.graph.security.caseManagement.customFieldNumberValue",
						"value" : 12,
				},
				"review date" : {
						"@odata_type" : "#microsoft.graph.security.caseManagement.customFieldDateTimeValue",
						"value_date_time" : "2026-06-15T09:00:00Z",
				},
				"affected services" : {
						"@odata_type" : "#microsoft.graph.security.caseManagement.customFieldOptionsValue",
						"values" : [
							"Exchange Online",
							"Microsoft Teams",
						],
				},
		}
	),
)

result = await graph_client.security.case_management.cases.post(request_body)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

```http
HTTP/1.1 201 Created
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.security.caseManagement.genericCase",
  "id": "987757fb-6ef4-1061-17e7-9de0d088e1dd",
  "createdDateTime": "2026-06-01T10:00:00Z",
  "createdBy": "john.doe@contoso.com",
  "lastModifiedDateTime": "2026-06-01T10:00:00Z",
  "lastModifiedBy": "john.doe@contoso.com",
  "displayName": "Security Breach Investigation",
  "status": "active",
  "description": "Investigating potential credential compromise.",
  "assignedTo": "john.doe@contoso.com",
  "priority": "high",
  "customFields": {
    "Customer impact": {
      "@odata.type": "#microsoft.graph.security.caseManagement.customFieldStringValue",
      "value": "Executive mailbox affected"
    },
    "Affected users": {
      "@odata.type": "#microsoft.graph.security.caseManagement.customFieldNumberValue",
      "value": 12
    },
    "Review date": {
      "@odata.type": "#microsoft.graph.security.caseManagement.customFieldDateTimeValue",
      "valueDateTime": "2026-06-15T09:00:00Z"
    },
    "Affected services": {
      "@odata.type": "#microsoft.graph.security.caseManagement.customFieldOptionsValue",
      "values": [
        "Exchange Online",
        "Microsoft Teams"
      ]
    }
  }
}
```
