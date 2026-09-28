<!-- Source: https://learn.microsoft.com/en-us/graph/api/security-alert-post-manualalert?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-06-12 -->

# Create manualAlert

Namespace: microsoft.graph.security

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Create a manual security alert in Microsoft 365 Defender with specified entities and metadata. When the alert is created, the backend automatically creates a new incident to contain the alert, or links the alert to an existing incident if **linkToIncident** is specified.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | SecurityAlert.Create.All | SecurityAlert.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | SecurityAlert.Create.All | SecurityAlert.ReadWrite.All |

Important

For delegated access using work or school accounts, the signed-in user must be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) or a custom role that grants the permissions required for this operation. This operation supports the following built-in roles, which provide only the least privilege necessary:

- Security Operator
- Security Administrator

## HTTP request

```http
POST /security/alerts_v2
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the [manualAlert](https://learn.microsoft.com/en-us/graph/api/resources/security-manualalert?view=graph-rest-beta) object.

You must include the `@odata.type` property with the value `#microsoft.graph.security.manualAlert` in the request body.

The following table lists the properties that are required when you create a manual alert.

| Property | Type | Description |
| :--- | :--- | :--- |
| @odata.type | String | Must be `#microsoft.graph.security.manualAlert`. Required. |
| category | String | MITRE ATT&CK category \(for example, `InitialAccess`, `Execution`\). Required. |
| description | String | Detailed description of the alert. Maximum 5000 characters. Required. |
| entityDefinitions | [microsoft.graph.security.entityDefinitionInput](https://learn.microsoft.com/en-us/graph/api/resources/security-entitydefinitioninput?view=graph-rest-beta) collection | Collection of entity definitions associated with the alert. Must contain 1 to 100 items. Required. |
| isExcludedFromCorrelation | Boolean | When `true`, excludes the alert from automatic correlation. Default is `false`. Optional. |
| linkToIncident | Int64 | Numeric ID of an existing incident to link to \(corresponds to the **incidentId** in the response\). If not provided, a new incident is created. Optional. |
| mitreTechniques | String collection | List of MITRE ATT&CK technique IDs \(for example, `T1566`, `T1078`\). Optional. |
| recommendedActions | String | Recommended remediation actions. Optional. |
| sentinelWorkspace | String | Sentinel workspace identifier for workspace routing. Optional. |
| severity | microsoft.graph.security.alertSeverity | Severity level. The possible values are: `unknown`, `informational`, `low`, `medium`, `high`, `unknownFutureValue`. Required. |
| title | String | Title of the alert. Required. |

For the supported **entityIdentifier** values per entity type, see [entityDefinitionInput](https://learn.microsoft.com/en-us/graph/api/resources/security-entitydefinitioninput?view=graph-rest-beta#supported-entity-identifiers).

## Response

If successful, this method returns a `201 Created` response code and an [alert](https://learn.microsoft.com/en-us/graph/api/resources/security-alert?view=graph-rest-beta) object in the response body. The response includes the **incidentId** of the automatically created or linked incident.

## Examples

### Example 1: Create a manual alert with a new incident

#### Request

The following example shows a request to create a manual alert. Because **linkToIncident** isn't specified, a new incident is automatically created.

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [PowerShell](#tabpanel_1_powershell)
- [Python](#tabpanel_1_python)

```http
POST https://graph.microsoft.com/beta/security/alerts_v2
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.security.manualAlert",
  "title": "Suspicious login from TOR exit node",
  "description": "User account showed login activity from known TOR exit node. Manual investigation revealed potential account compromise.",
  "category": "InitialAccess",
  "severity": "high",
  "recommendedActions": "Reset user credentials, enable MFA, review recent user activity",
  "mitreTechniques": ["T1078"],
  "entityDefinitions": [
    {
      "entityType": "user",
      "entityIdentifier": "userPrincipalName",
      "identifierValue": "john.doe@contoso.com",
      "role": "impacted"
    },
    {
      "entityType": "ip",
      "entityIdentifier": "address",
      "identifierValue": "185.220.101.50",
      "role": "related"
    }
  ]
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.Models.Security;

var requestBody = new ManualAlert
{
	OdataType = "#microsoft.graph.security.manualAlert",
	Title = "Suspicious login from TOR exit node",
	Description = "User account showed login activity from known TOR exit node. Manual investigation revealed potential account compromise.",
	Category = "InitialAccess",
	Severity = AlertSeverity.High,
	RecommendedActions = "Reset user credentials, enable MFA, review recent user activity",
	MitreTechniques = new List<string>
	{
		"T1078",
	},
	EntityDefinitions = new List<EntityDefinitionInput>
	{
		new EntityDefinitionInput
		{
			EntityType = ManualAlertEntityType.User,
			EntityIdentifier = "userPrincipalName",
			IdentifierValue = "john.doe@contoso.com",
			Role = EntityDefinitionInputRole.Impacted,
		},
		new EntityDefinitionInput
		{
			EntityType = ManualAlertEntityType.Ip,
			EntityIdentifier = "address",
			IdentifierValue = "185.220.101.50",
			Role = EntityDefinitionInputRole.Related,
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Security.Alerts_v2.PostAsync(requestBody);
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
	  graphmodelssecurity "github.com/microsoftgraph/msgraph-beta-sdk-go/models/security"
	  //other-imports
)

requestBody := graphmodelssecurity.NewAlert()
title := "Suspicious login from TOR exit node"
requestBody.SetTitle(&title) 
description := "User account showed login activity from known TOR exit node. Manual investigation revealed potential account compromise."
requestBody.SetDescription(&description) 
category := "InitialAccess"
requestBody.SetCategory(&category) 
severity := graphmodels.HIGH_ALERTSEVERITY 
requestBody.SetSeverity(&severity) 
recommendedActions := "Reset user credentials, enable MFA, review recent user activity"
requestBody.SetRecommendedActions(&recommendedActions) 
mitreTechniques := []string {
	"T1078",
}
requestBody.SetMitreTechniques(mitreTechniques)


entityDefinitionInput := graphmodelssecurity.NewEntityDefinitionInput()
entityType := graphmodels.USER_MANUALALERTENTITYTYPE 
entityDefinitionInput.SetEntityType(&entityType) 
entityIdentifier := "userPrincipalName"
entityDefinitionInput.SetEntityIdentifier(&entityIdentifier) 
identifierValue := "john.doe@contoso.com"
entityDefinitionInput.SetIdentifierValue(&identifierValue) 
role := graphmodels.IMPACTED_ENTITYDEFINITIONINPUTROLE 
entityDefinitionInput.SetRole(&role) 
entityDefinitionInput1 := graphmodelssecurity.NewEntityDefinitionInput()
entityType := graphmodels.IP_MANUALALERTENTITYTYPE 
entityDefinitionInput1.SetEntityType(&entityType) 
entityIdentifier := "address"
entityDefinitionInput1.SetEntityIdentifier(&entityIdentifier) 
identifierValue := "185.220.101.50"
entityDefinitionInput1.SetIdentifierValue(&identifierValue) 
role := graphmodels.RELATED_ENTITYDEFINITIONINPUTROLE 
entityDefinitionInput1.SetRole(&role) 

entityDefinitions := []graphmodelssecurity.EntityDefinitionInputable {
	entityDefinitionInput,
	entityDefinitionInput1,
}
requestBody.SetEntityDefinitions(entityDefinitions)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
alerts_v2, err := graphClient.Security().Alerts_v2().Post(context.Background(), requestBody, nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.beta.models.security.ManualAlert alert = new com.microsoft.graph.beta.models.security.ManualAlert();
alert.setOdataType("#microsoft.graph.security.manualAlert");
alert.setTitle("Suspicious login from TOR exit node");
alert.setDescription("User account showed login activity from known TOR exit node. Manual investigation revealed potential account compromise.");
alert.setCategory("InitialAccess");
alert.setSeverity(com.microsoft.graph.beta.models.security.AlertSeverity.High);
alert.setRecommendedActions("Reset user credentials, enable MFA, review recent user activity");
LinkedList<String> mitreTechniques = new LinkedList<String>();
mitreTechniques.add("T1078");
alert.setMitreTechniques(mitreTechniques);
LinkedList<com.microsoft.graph.beta.models.security.EntityDefinitionInput> entityDefinitions = new LinkedList<com.microsoft.graph.beta.models.security.EntityDefinitionInput>();
com.microsoft.graph.beta.models.security.EntityDefinitionInput entityDefinitionInput = new com.microsoft.graph.beta.models.security.EntityDefinitionInput();
entityDefinitionInput.setEntityType(com.microsoft.graph.beta.models.security.ManualAlertEntityType.User);
entityDefinitionInput.setEntityIdentifier("userPrincipalName");
entityDefinitionInput.setIdentifierValue("john.doe@contoso.com");
entityDefinitionInput.setRole(com.microsoft.graph.beta.models.security.EntityDefinitionInputRole.Impacted);
entityDefinitions.add(entityDefinitionInput);
com.microsoft.graph.beta.models.security.EntityDefinitionInput entityDefinitionInput1 = new com.microsoft.graph.beta.models.security.EntityDefinitionInput();
entityDefinitionInput1.setEntityType(com.microsoft.graph.beta.models.security.ManualAlertEntityType.Ip);
entityDefinitionInput1.setEntityIdentifier("address");
entityDefinitionInput1.setIdentifierValue("185.220.101.50");
entityDefinitionInput1.setRole(com.microsoft.graph.beta.models.security.EntityDefinitionInputRole.Related);
entityDefinitions.add(entityDefinitionInput1);
alert.setEntityDefinitions(entityDefinitions);
com.microsoft.graph.models.security.Alert result = graphClient.security().alertsV2().post(alert);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const alert = {
  '@odata.type': '#microsoft.graph.security.manualAlert',
  title: 'Suspicious login from TOR exit node',
  description: 'User account showed login activity from known TOR exit node. Manual investigation revealed potential account compromise.',
  category: 'InitialAccess',
  severity: 'high',
  recommendedActions: 'Reset user credentials, enable MFA, review recent user activity',
  mitreTechniques: ['T1078'],
  entityDefinitions: [
    {
      entityType: 'user',
      entityIdentifier: 'userPrincipalName',
      identifierValue: 'john.doe@contoso.com',
      role: 'impacted'
    },
    {
      entityType: 'ip',
      entityIdentifier: 'address',
      identifierValue: '185.220.101.50',
      role: 'related'
    }
  ]
};

await client.api('/security/alerts_v2')
	.version('beta')
	.post(alert);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Models\Security\ManualAlert;
use Microsoft\Graph\Beta\Generated\Models\Security\AlertSeverity;
use Microsoft\Graph\Beta\Generated\Models\Security\EntityDefinitionInput;
use Microsoft\Graph\Beta\Generated\Models\Security\ManualAlertEntityType;
use Microsoft\Graph\Beta\Generated\Models\Security\EntityDefinitionInputRole;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new ManualAlert();
$requestBody->setOdataType('#microsoft.graph.security.manualAlert');
$requestBody->setTitle('Suspicious login from TOR exit node');
$requestBody->setDescription('User account showed login activity from known TOR exit node. Manual investigation revealed potential account compromise.');
$requestBody->setCategory('InitialAccess');
$requestBody->setSeverity(new AlertSeverity('high'));
$requestBody->setRecommendedActions('Reset user credentials, enable MFA, review recent user activity');
$requestBody->setMitreTechniques(['T1078', 	]);
$entityDefinitionsEntityDefinitionInput1 = new EntityDefinitionInput();
$entityDefinitionsEntityDefinitionInput1->setEntityType(new ManualAlertEntityType('user'));
$entityDefinitionsEntityDefinitionInput1->setEntityIdentifier('userPrincipalName');
$entityDefinitionsEntityDefinitionInput1->setIdentifierValue('john.doe@contoso.com');
$entityDefinitionsEntityDefinitionInput1->setRole(new EntityDefinitionInputRole('impacted'));
$entityDefinitionsArray []= $entityDefinitionsEntityDefinitionInput1;
$entityDefinitionsEntityDefinitionInput2 = new EntityDefinitionInput();
$entityDefinitionsEntityDefinitionInput2->setEntityType(new ManualAlertEntityType('ip'));
$entityDefinitionsEntityDefinitionInput2->setEntityIdentifier('address');
$entityDefinitionsEntityDefinitionInput2->setIdentifierValue('185.220.101.50');
$entityDefinitionsEntityDefinitionInput2->setRole(new EntityDefinitionInputRole('related'));
$entityDefinitionsArray []= $entityDefinitionsEntityDefinitionInput2;
$requestBody->setEntityDefinitions($entityDefinitionsArray);


$result = $graphServiceClient->security()->alerts_v2()->post($requestBody)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Beta.Security

$params = @{
	"@odata.type" = "#microsoft.graph.security.manualAlert"
	title = "Suspicious login from TOR exit node"
	description = "User account showed login activity from known TOR exit node. Manual investigation revealed potential account compromise."
	category = "InitialAccess"
	severity = "high"
	recommendedActions = "Reset user credentials, enable MFA, review recent user activity"
	mitreTechniques = @(
	"T1078"
)
entityDefinitions = @(
	@{
		entityType = "user"
		entityIdentifier = "userPrincipalName"
		identifierValue = "john.doe@contoso.com"
		role = "impacted"
	}
	@{
		entityType = "ip"
		entityIdentifier = "address"
		identifierValue = "185.220.101.50"
		role = "related"
	}
)
}

New-MgBetaSecurityAlertV2 -BodyParameter $params
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.models.security.manual_alert import ManualAlert
from msgraph_beta.generated.models.alert_severity import AlertSeverity
from msgraph_beta.generated.models.security.entity_definition_input import EntityDefinitionInput
from msgraph_beta.generated.models.manual_alert_entity_type import ManualAlertEntityType
from msgraph_beta.generated.models.entity_definition_input_role import EntityDefinitionInputRole
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = ManualAlert(
	odata_type = "#microsoft.graph.security.manualAlert",
	title = "Suspicious login from TOR exit node",
	description = "User account showed login activity from known TOR exit node. Manual investigation revealed potential account compromise.",
	category = "InitialAccess",
	severity = AlertSeverity.High,
	recommended_actions = "Reset user credentials, enable MFA, review recent user activity",
	mitre_techniques = [
		"T1078",
	],
	entity_definitions = [
		EntityDefinitionInput(
			entity_type = ManualAlertEntityType.User,
			entity_identifier = "userPrincipalName",
			identifier_value = "john.doe@contoso.com",
			role = EntityDefinitionInputRole.Impacted,
		),
		EntityDefinitionInput(
			entity_type = ManualAlertEntityType.Ip,
			entity_identifier = "address",
			identifier_value = "185.220.101.50",
			role = EntityDefinitionInputRole.Related,
		),
	],
)

result = await graph_client.security.alerts_v2.post(request_body)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.security.alert",
  "id": "da637551227677560813_-961444813",
  "providerAlertId": "manual_da637551227677560813",
  "incidentId": "28282",
  "title": "Suspicious login from TOR exit node",
  "description": "User account showed login activity from known TOR exit node. Manual investigation revealed potential account compromise.",
  "severity": "high",
  "status": "new",
  "classification": "unknown",
  "determination": "unknown",
  "category": "InitialAccess",
  "detectionSource": "manual",
  "serviceSource": "microsoft365Defender",
  "tenantId": "b3cdbae4-eb1d-4b7c-a9e1-8c9f6d8e4f3a",
  "createdDateTime": "2026-05-19T15:30:00Z",
  "lastUpdateDateTime": "2026-05-19T15:30:00Z",
  "recommendedActions": "Reset user credentials, enable MFA, review recent user activity",
  "mitreTechniques": ["T1078"],
  "alertWebUrl": "https://security.microsoft.com/alerts/da637551227677560813_-961444813"
}
```

### Example 2: Create a manual alert linked to an existing incident

#### Request

The following example shows a request to create a manual alert that links to an existing incident.

- [HTTP](#tabpanel_2_http)
- [C#](#tabpanel_2_csharp)
- [Go](#tabpanel_2_go)
- [Java](#tabpanel_2_java)
- [JavaScript](#tabpanel_2_javascript)
- [PHP](#tabpanel_2_php)
- [PowerShell](#tabpanel_2_powershell)
- [Python](#tabpanel_2_python)

```http
POST https://graph.microsoft.com/beta/security/alerts_v2
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.security.manualAlert",
  "title": "Malicious file detected on device",
  "description": "Sandbox analysis revealed malicious behavior in downloaded file.",
  "category": "Execution",
  "severity": "high",
  "recommendedActions": "Isolate device, remove file, scan for additional IOCs",
  "linkToIncident": 28282,
  "entityDefinitions": [
    {
      "entityType": "file",
      "entityIdentifier": "sha256",
      "identifierValue": "e3b0c44298fc1c149afbf4c8996fb92427ae41e4649b934ca495991b7852b855",
      "role": "related"
    },
    {
      "entityType": "device",
      "entityIdentifier": "deviceName",
      "identifierValue": "DESKTOP-VICTIM01",
      "role": "impacted"
    }
  ]
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.Models.Security;

var requestBody = new ManualAlert
{
	OdataType = "#microsoft.graph.security.manualAlert",
	Title = "Malicious file detected on device",
	Description = "Sandbox analysis revealed malicious behavior in downloaded file.",
	Category = "Execution",
	Severity = AlertSeverity.High,
	RecommendedActions = "Isolate device, remove file, scan for additional IOCs",
	LinkToIncident = 28282L,
	EntityDefinitions = new List<EntityDefinitionInput>
	{
		new EntityDefinitionInput
		{
			EntityType = ManualAlertEntityType.File,
			EntityIdentifier = "sha256",
			IdentifierValue = "e3b0c44298fc1c149afbf4c8996fb92427ae41e4649b934ca495991b7852b855",
			Role = EntityDefinitionInputRole.Related,
		},
		new EntityDefinitionInput
		{
			EntityType = ManualAlertEntityType.Device,
			EntityIdentifier = "deviceName",
			IdentifierValue = "DESKTOP-VICTIM01",
			Role = EntityDefinitionInputRole.Impacted,
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Security.Alerts_v2.PostAsync(requestBody);
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
	  graphmodelssecurity "github.com/microsoftgraph/msgraph-beta-sdk-go/models/security"
	  //other-imports
)

requestBody := graphmodelssecurity.NewAlert()
title := "Malicious file detected on device"
requestBody.SetTitle(&title) 
description := "Sandbox analysis revealed malicious behavior in downloaded file."
requestBody.SetDescription(&description) 
category := "Execution"
requestBody.SetCategory(&category) 
severity := graphmodels.HIGH_ALERTSEVERITY 
requestBody.SetSeverity(&severity) 
recommendedActions := "Isolate device, remove file, scan for additional IOCs"
requestBody.SetRecommendedActions(&recommendedActions) 
linkToIncident := int64(28282)
requestBody.SetLinkToIncident(&linkToIncident) 


entityDefinitionInput := graphmodelssecurity.NewEntityDefinitionInput()
entityType := graphmodels.FILE_MANUALALERTENTITYTYPE 
entityDefinitionInput.SetEntityType(&entityType) 
entityIdentifier := "sha256"
entityDefinitionInput.SetEntityIdentifier(&entityIdentifier) 
identifierValue := "e3b0c44298fc1c149afbf4c8996fb92427ae41e4649b934ca495991b7852b855"
entityDefinitionInput.SetIdentifierValue(&identifierValue) 
role := graphmodels.RELATED_ENTITYDEFINITIONINPUTROLE 
entityDefinitionInput.SetRole(&role) 
entityDefinitionInput1 := graphmodelssecurity.NewEntityDefinitionInput()
entityType := graphmodels.DEVICE_MANUALALERTENTITYTYPE 
entityDefinitionInput1.SetEntityType(&entityType) 
entityIdentifier := "deviceName"
entityDefinitionInput1.SetEntityIdentifier(&entityIdentifier) 
identifierValue := "DESKTOP-VICTIM01"
entityDefinitionInput1.SetIdentifierValue(&identifierValue) 
role := graphmodels.IMPACTED_ENTITYDEFINITIONINPUTROLE 
entityDefinitionInput1.SetRole(&role) 

entityDefinitions := []graphmodelssecurity.EntityDefinitionInputable {
	entityDefinitionInput,
	entityDefinitionInput1,
}
requestBody.SetEntityDefinitions(entityDefinitions)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
alerts_v2, err := graphClient.Security().Alerts_v2().Post(context.Background(), requestBody, nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.beta.models.security.ManualAlert alert = new com.microsoft.graph.beta.models.security.ManualAlert();
alert.setOdataType("#microsoft.graph.security.manualAlert");
alert.setTitle("Malicious file detected on device");
alert.setDescription("Sandbox analysis revealed malicious behavior in downloaded file.");
alert.setCategory("Execution");
alert.setSeverity(com.microsoft.graph.beta.models.security.AlertSeverity.High);
alert.setRecommendedActions("Isolate device, remove file, scan for additional IOCs");
alert.setLinkToIncident(28282L);
LinkedList<com.microsoft.graph.beta.models.security.EntityDefinitionInput> entityDefinitions = new LinkedList<com.microsoft.graph.beta.models.security.EntityDefinitionInput>();
com.microsoft.graph.beta.models.security.EntityDefinitionInput entityDefinitionInput = new com.microsoft.graph.beta.models.security.EntityDefinitionInput();
entityDefinitionInput.setEntityType(com.microsoft.graph.beta.models.security.ManualAlertEntityType.File);
entityDefinitionInput.setEntityIdentifier("sha256");
entityDefinitionInput.setIdentifierValue("e3b0c44298fc1c149afbf4c8996fb92427ae41e4649b934ca495991b7852b855");
entityDefinitionInput.setRole(com.microsoft.graph.beta.models.security.EntityDefinitionInputRole.Related);
entityDefinitions.add(entityDefinitionInput);
com.microsoft.graph.beta.models.security.EntityDefinitionInput entityDefinitionInput1 = new com.microsoft.graph.beta.models.security.EntityDefinitionInput();
entityDefinitionInput1.setEntityType(com.microsoft.graph.beta.models.security.ManualAlertEntityType.Device);
entityDefinitionInput1.setEntityIdentifier("deviceName");
entityDefinitionInput1.setIdentifierValue("DESKTOP-VICTIM01");
entityDefinitionInput1.setRole(com.microsoft.graph.beta.models.security.EntityDefinitionInputRole.Impacted);
entityDefinitions.add(entityDefinitionInput1);
alert.setEntityDefinitions(entityDefinitions);
com.microsoft.graph.models.security.Alert result = graphClient.security().alertsV2().post(alert);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const alert = {
  '@odata.type': '#microsoft.graph.security.manualAlert',
  title: 'Malicious file detected on device',
  description: 'Sandbox analysis revealed malicious behavior in downloaded file.',
  category: 'Execution',
  severity: 'high',
  recommendedActions: 'Isolate device, remove file, scan for additional IOCs',
  linkToIncident: 28282,
  entityDefinitions: [
    {
      entityType: 'file',
      entityIdentifier: 'sha256',
      identifierValue: 'e3b0c44298fc1c149afbf4c8996fb92427ae41e4649b934ca495991b7852b855',
      role: 'related'
    },
    {
      entityType: 'device',
      entityIdentifier: 'deviceName',
      identifierValue: 'DESKTOP-VICTIM01',
      role: 'impacted'
    }
  ]
};

await client.api('/security/alerts_v2')
	.version('beta')
	.post(alert);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Models\Security\ManualAlert;
use Microsoft\Graph\Beta\Generated\Models\Security\AlertSeverity;
use Microsoft\Graph\Beta\Generated\Models\Security\EntityDefinitionInput;
use Microsoft\Graph\Beta\Generated\Models\Security\ManualAlertEntityType;
use Microsoft\Graph\Beta\Generated\Models\Security\EntityDefinitionInputRole;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new ManualAlert();
$requestBody->setOdataType('#microsoft.graph.security.manualAlert');
$requestBody->setTitle('Malicious file detected on device');
$requestBody->setDescription('Sandbox analysis revealed malicious behavior in downloaded file.');
$requestBody->setCategory('Execution');
$requestBody->setSeverity(new AlertSeverity('high'));
$requestBody->setRecommendedActions('Isolate device, remove file, scan for additional IOCs');
$requestBody->setLinkToIncident(28282);
$entityDefinitionsEntityDefinitionInput1 = new EntityDefinitionInput();
$entityDefinitionsEntityDefinitionInput1->setEntityType(new ManualAlertEntityType('file'));
$entityDefinitionsEntityDefinitionInput1->setEntityIdentifier('sha256');
$entityDefinitionsEntityDefinitionInput1->setIdentifierValue('e3b0c44298fc1c149afbf4c8996fb92427ae41e4649b934ca495991b7852b855');
$entityDefinitionsEntityDefinitionInput1->setRole(new EntityDefinitionInputRole('related'));
$entityDefinitionsArray []= $entityDefinitionsEntityDefinitionInput1;
$entityDefinitionsEntityDefinitionInput2 = new EntityDefinitionInput();
$entityDefinitionsEntityDefinitionInput2->setEntityType(new ManualAlertEntityType('device'));
$entityDefinitionsEntityDefinitionInput2->setEntityIdentifier('deviceName');
$entityDefinitionsEntityDefinitionInput2->setIdentifierValue('DESKTOP-VICTIM01');
$entityDefinitionsEntityDefinitionInput2->setRole(new EntityDefinitionInputRole('impacted'));
$entityDefinitionsArray []= $entityDefinitionsEntityDefinitionInput2;
$requestBody->setEntityDefinitions($entityDefinitionsArray);


$result = $graphServiceClient->security()->alerts_v2()->post($requestBody)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Beta.Security

$params = @{
	"@odata.type" = "#microsoft.graph.security.manualAlert"
	title = "Malicious file detected on device"
	description = "Sandbox analysis revealed malicious behavior in downloaded file."
	category = "Execution"
	severity = "high"
	recommendedActions = "Isolate device, remove file, scan for additional IOCs"
	linkToIncident = 
	entityDefinitions = @(
		@{
			entityType = "file"
			entityIdentifier = "sha256"
			identifierValue = "e3b0c44298fc1c149afbf4c8996fb92427ae41e4649b934ca495991b7852b855"
			role = "related"
		}
		@{
			entityType = "device"
			entityIdentifier = "deviceName"
			identifierValue = "DESKTOP-VICTIM01"
			role = "impacted"
		}
	)
}

New-MgBetaSecurityAlertV2 -BodyParameter $params
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.models.security.manual_alert import ManualAlert
from msgraph_beta.generated.models.alert_severity import AlertSeverity
from msgraph_beta.generated.models.security.entity_definition_input import EntityDefinitionInput
from msgraph_beta.generated.models.manual_alert_entity_type import ManualAlertEntityType
from msgraph_beta.generated.models.entity_definition_input_role import EntityDefinitionInputRole
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = ManualAlert(
	odata_type = "#microsoft.graph.security.manualAlert",
	title = "Malicious file detected on device",
	description = "Sandbox analysis revealed malicious behavior in downloaded file.",
	category = "Execution",
	severity = AlertSeverity.High,
	recommended_actions = "Isolate device, remove file, scan for additional IOCs",
	link_to_incident = 28282,
	entity_definitions = [
		EntityDefinitionInput(
			entity_type = ManualAlertEntityType.File,
			entity_identifier = "sha256",
			identifier_value = "e3b0c44298fc1c149afbf4c8996fb92427ae41e4649b934ca495991b7852b855",
			role = EntityDefinitionInputRole.Related,
		),
		EntityDefinitionInput(
			entity_type = ManualAlertEntityType.Device,
			entity_identifier = "deviceName",
			identifier_value = "DESKTOP-VICTIM01",
			role = EntityDefinitionInputRole.Impacted,
		),
	],
)

result = await graph_client.security.alerts_v2.post(request_body)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.security.alert",
  "id": "da637551227677560814_-961444814",
  "providerAlertId": "manual_da637551227677560814",
  "incidentId": "28282",
  "title": "Malicious file detected on device",
  "description": "Sandbox analysis revealed malicious behavior in downloaded file.",
  "severity": "high",
  "status": "new",
  "classification": "unknown",
  "determination": "unknown",
  "category": "Execution",
  "detectionSource": "manual",
  "serviceSource": "microsoft365Defender",
  "tenantId": "b3cdbae4-eb1d-4b7c-a9e1-8c9f6d8e4f3a",
  "createdDateTime": "2026-05-19T15:35:00Z",
  "lastUpdateDateTime": "2026-05-19T15:35:00Z",
  "recommendedActions": "Isolate device, remove file, scan for additional IOCs",
  "alertWebUrl": "https://security.microsoft.com/alerts/da637551227677560814_-961444814"
}
```
