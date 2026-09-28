<!-- Source: https://learn.microsoft.com/en-us/graph/api/security-rulesroot-post-detectionrules?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-07-01 -->

# Create detectionRule

Namespace: microsoft.graph.security

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Create a new [detectionRule](https://learn.microsoft.com/en-us/graph/api/resources/security-detectionrule?view=graph-rest-beta) object.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | CustomDetection.ReadWrite.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | CustomDetection.ReadWrite.All | Not available. |

Important

For delegated access using work or school accounts, the signed-in user must be assigned a role that grants the permissions required for this operation. Custom detection rules use the Microsoft Defender XDR Unified role-based access control \(RBAC\) model. The following roles are supported:

- **Detection tuning \(Manage\)** - A [Microsoft Defender XDR Unified RBAC](https://learn.microsoft.com/en-us/defender-xdr/custom-permissions-details) permission that grants manage access to detections in the Microsoft Defender portal, including custom detections, alert tuning, and threat indicators of compromise.
- **Security Administrator** - A [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json#security-administrator) that grants manage permissions across Microsoft Defender portals and services.
- **Security Operator** - A [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json#security-operator). Sufficient for managing custom detection rules only when role-based access control is turned off in Microsoft Defender for Endpoint. If RBAC is configured, the **Manage Security Settings** permission for Defender for Endpoint is also required.

Additional workload-specific permissions might be required to manage rules that target data from specific Defender workloads \(for example, Defender for Endpoint, Defender for Office 365\). For more information, see [Required permissions for managing custom detections](https://learn.microsoft.com/en-us/defender-xdr/custom-detection-rules#required-permissions-for-managing-custom-detections).

## HTTP request

```http
POST /security/rules/detectionRules
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the [microsoft.graph.security.detectionRule](https://learn.microsoft.com/en-us/graph/api/resources/security-detectionrule?view=graph-rest-beta) object.

You can specify the following properties and relationships when creating a **detectionRule**.

| Property | Type | Description |
| :--- | :--- | :--- |
| description | String | A user-supplied description of the detection rule. Optional. |
| detectionAction | [microsoft.graph.security.detectionAction](https://learn.microsoft.com/en-us/graph/api/resources/security-detectionaction?view=graph-rest-beta) | The actions taken when a detection is made by this rule, including the alert that is created and any automated response actions. Optional. |
| displayName | String | The display name of the rule. Required. |
| id | String | The client-provided unique identifier of the rule. Required. |
| isEnabled | Boolean | **Deprecated.** Use **status** instead. The `isEnabled` property will be removed from this resource on 2026-10-01. Optional. |
| queryCondition | [microsoft.graph.security.queryCondition](https://learn.microsoft.com/en-us/graph/api/resources/security-querycondition?view=graph-rest-beta) | The advanced hunting query that defines the detection logic of this rule. Required. |
| schedule | [microsoft.graph.security.ruleSchedule](https://learn.microsoft.com/en-us/graph/api/resources/security-ruleschedule?view=graph-rest-beta) | The triggering schedule of this rule. Required. |
| status | [microsoft.graph.security.detectionRuleStatus](https://learn.microsoft.com/en-us/graph/api/resources/enums-security?view=graph-rest-beta#detectionrulestatus-values) | The current run status of the rule. The possible values are: `enabled`, `disabled`, `autoDisabled`, `unknownFutureValue`. Required. |

## Response

If successful, this method returns a `201 Created` response code and a [microsoft.graph.security.detectionRule](https://learn.microsoft.com/en-us/graph/api/resources/security-detectionrule?view=graph-rest-beta) object in the response body.

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
POST https://graph.microsoft.com/beta/security/rules/detectionRules
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.security.detectionRule",
  "id": "office-encoded-powershell",
  "displayName": "Suspicious encoded PowerShell from Office",
  "description": "Detects encoded PowerShell processes launched by Office applications, a common phishing payload pattern.",
  "status": "enabled",
  "queryCondition": {
    "queryText": "DeviceProcessEvents | where InitiatingProcessFileName in~ ('winword.exe','excel.exe','outlook.exe') | where FileName == 'powershell.exe' | where ProcessCommandLine has '-enc'"
  },
  "schedule": {
    "frequency": "PT1H"
  },
  "detectionAction": {
    "alertTemplate": {
      "title": "Suspicious encoded PowerShell from Office",
      "description": "An Office app launched an encoded PowerShell command, which may indicate phishing-driven code execution.",
      "severity": "high",
      "recommendedActions": "Investigate the parent Office document, isolate the device, and review the user's recent email activity.",
      "entityMappings": {
        "accounts": [
          {
            "nameColumn": "AccountName",
            "ntDomainColumn": "AccountDomain",
            "sidColumn": "AccountSid"
          }
        ],
        "hosts": [
          {
            "deviceIdColumn": "DeviceId",
            "nameColumn": "DeviceName"
          }
        ],
        "files": [
          {
            "nameColumn": "FileName",
            "sha1Column": "SHA1",
            "sha256Column": "SHA256"
          }
        ]
      },
      "tactics": [
        {
          "tactic": "Execution",
          "techniques": [
            {
              "technique": "T1059.001"
            }
          ]
        }
      ]
    }
  }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.Models.Security;

var requestBody = new DetectionRule
{
	OdataType = "#microsoft.graph.security.detectionRule",
	Id = "office-encoded-powershell",
	DisplayName = "Suspicious encoded PowerShell from Office",
	Description = "Detects encoded PowerShell processes launched by Office applications, a common phishing payload pattern.",
	Status = DetectionRuleStatus.Enabled,
	QueryCondition = new QueryCondition
	{
		QueryText = "DeviceProcessEvents | where InitiatingProcessFileName in~ ('winword.exe','excel.exe','outlook.exe') | where FileName == 'powershell.exe' | where ProcessCommandLine has '-enc'",
	},
	Schedule = new RuleSchedule
	{
		Frequency = TimeSpan.Parse("PT1H"),
	},
	DetectionAction = new DetectionAction
	{
		AlertTemplate = new AlertTemplate
		{
			Title = "Suspicious encoded PowerShell from Office",
			Description = "An Office app launched an encoded PowerShell command, which may indicate phishing-driven code execution.",
			Severity = AlertSeverity.High,
			RecommendedActions = "Investigate the parent Office document, isolate the device, and review the user's recent email activity.",
			EntityMappings = new EntityMappingConfiguration
			{
				Accounts = new List<AccountEntityMapping>
				{
					new AccountEntityMapping
					{
						NameColumn = "AccountName",
						NtDomainColumn = "AccountDomain",
						SidColumn = "AccountSid",
					},
				},
				Hosts = new List<HostEntityMapping>
				{
					new HostEntityMapping
					{
						DeviceIdColumn = "DeviceId",
						NameColumn = "DeviceName",
					},
				},
				Files = new List<FileEntityMapping>
				{
					new FileEntityMapping
					{
						NameColumn = "FileName",
						Sha1Column = "SHA1",
						Sha256Column = "SHA256",
					},
				},
			},
			Tactics = new List<MitreTactic>
			{
				new MitreTactic
				{
					Tactic = "Execution",
					Techniques = new List<MitreTechnique>
					{
						new MitreTechnique
						{
							Technique = "T1059.001",
						},
					},
				},
			},
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Security.Rules.DetectionRules.PostAsync(requestBody);
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

requestBody := graphmodelssecurity.NewDetectionRule()
id := "office-encoded-powershell"
requestBody.SetId(&id) 
displayName := "Suspicious encoded PowerShell from Office"
requestBody.SetDisplayName(&displayName) 
description := "Detects encoded PowerShell processes launched by Office applications, a common phishing payload pattern."
requestBody.SetDescription(&description) 
status := graphmodels.ENABLED_DETECTIONRULESTATUS 
requestBody.SetStatus(&status) 
queryCondition := graphmodelssecurity.NewQueryCondition()
queryText := "DeviceProcessEvents | where InitiatingProcessFileName in~ ('winword.exe','excel.exe','outlook.exe') | where FileName == 'powershell.exe' | where ProcessCommandLine has '-enc'"
queryCondition.SetQueryText(&queryText) 
requestBody.SetQueryCondition(queryCondition)
schedule := graphmodelssecurity.NewRuleSchedule()
frequency , err := abstractions.ParseISODuration("PT1H")
schedule.SetFrequency(&frequency) 
requestBody.SetSchedule(schedule)
detectionAction := graphmodelssecurity.NewDetectionAction()
alertTemplate := graphmodelssecurity.NewAlertTemplate()
title := "Suspicious encoded PowerShell from Office"
alertTemplate.SetTitle(&title) 
description := "An Office app launched an encoded PowerShell command, which may indicate phishing-driven code execution."
alertTemplate.SetDescription(&description) 
severity := graphmodels.HIGH_ALERTSEVERITY 
alertTemplate.SetSeverity(&severity) 
recommendedActions := "Investigate the parent Office document, isolate the device, and review the user's recent email activity."
alertTemplate.SetRecommendedActions(&recommendedActions) 
entityMappings := graphmodelssecurity.NewEntityMappingConfiguration()


accountEntityMapping := graphmodelssecurity.NewAccountEntityMapping()
nameColumn := "AccountName"
accountEntityMapping.SetNameColumn(&nameColumn) 
ntDomainColumn := "AccountDomain"
accountEntityMapping.SetNtDomainColumn(&ntDomainColumn) 
sidColumn := "AccountSid"
accountEntityMapping.SetSidColumn(&sidColumn) 

accounts := []graphmodelssecurity.AccountEntityMappingable {
	accountEntityMapping,
}
entityMappings.SetAccounts(accounts)


hostEntityMapping := graphmodelssecurity.NewHostEntityMapping()
deviceIdColumn := "DeviceId"
hostEntityMapping.SetDeviceIdColumn(&deviceIdColumn) 
nameColumn := "DeviceName"
hostEntityMapping.SetNameColumn(&nameColumn) 

hosts := []graphmodelssecurity.HostEntityMappingable {
	hostEntityMapping,
}
entityMappings.SetHosts(hosts)


fileEntityMapping := graphmodelssecurity.NewFileEntityMapping()
nameColumn := "FileName"
fileEntityMapping.SetNameColumn(&nameColumn) 
sha1Column := "SHA1"
fileEntityMapping.SetSha1Column(&sha1Column) 
sha256Column := "SHA256"
fileEntityMapping.SetSha256Column(&sha256Column) 

files := []graphmodelssecurity.FileEntityMappingable {
	fileEntityMapping,
}
entityMappings.SetFiles(files)
alertTemplate.SetEntityMappings(entityMappings)


mitreTactic := graphmodelssecurity.NewMitreTactic()
tactic := "Execution"
mitreTactic.SetTactic(&tactic) 


mitreTechnique := graphmodelssecurity.NewMitreTechnique()
technique := "T1059.001"
mitreTechnique.SetTechnique(&technique) 

techniques := []graphmodelssecurity.MitreTechniqueable {
	mitreTechnique,
}
mitreTactic.SetTechniques(techniques)

tactics := []graphmodelssecurity.MitreTacticable {
	mitreTactic,
}
alertTemplate.SetTactics(tactics)
detectionAction.SetAlertTemplate(alertTemplate)
requestBody.SetDetectionAction(detectionAction)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
detectionRules, err := graphClient.Security().Rules().DetectionRules().Post(context.Background(), requestBody, nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.beta.models.security.DetectionRule detectionRule = new com.microsoft.graph.beta.models.security.DetectionRule();
detectionRule.setOdataType("#microsoft.graph.security.detectionRule");
detectionRule.setId("office-encoded-powershell");
detectionRule.setDisplayName("Suspicious encoded PowerShell from Office");
detectionRule.setDescription("Detects encoded PowerShell processes launched by Office applications, a common phishing payload pattern.");
detectionRule.setStatus(com.microsoft.graph.beta.models.security.DetectionRuleStatus.Enabled);
com.microsoft.graph.beta.models.security.QueryCondition queryCondition = new com.microsoft.graph.beta.models.security.QueryCondition();
queryCondition.setQueryText("DeviceProcessEvents | where InitiatingProcessFileName in~ ('winword.exe','excel.exe','outlook.exe') | where FileName == 'powershell.exe' | where ProcessCommandLine has '-enc'");
detectionRule.setQueryCondition(queryCondition);
com.microsoft.graph.beta.models.security.RuleSchedule schedule = new com.microsoft.graph.beta.models.security.RuleSchedule();
PeriodAndDuration frequency = PeriodAndDuration.ofDuration(Duration.parse("PT1H"));
schedule.setFrequency(frequency);
detectionRule.setSchedule(schedule);
com.microsoft.graph.beta.models.security.DetectionAction detectionAction = new com.microsoft.graph.beta.models.security.DetectionAction();
com.microsoft.graph.beta.models.security.AlertTemplate alertTemplate = new com.microsoft.graph.beta.models.security.AlertTemplate();
alertTemplate.setTitle("Suspicious encoded PowerShell from Office");
alertTemplate.setDescription("An Office app launched an encoded PowerShell command, which may indicate phishing-driven code execution.");
alertTemplate.setSeverity(com.microsoft.graph.beta.models.security.AlertSeverity.High);
alertTemplate.setRecommendedActions("Investigate the parent Office document, isolate the device, and review the user's recent email activity.");
com.microsoft.graph.beta.models.security.EntityMappingConfiguration entityMappings = new com.microsoft.graph.beta.models.security.EntityMappingConfiguration();
LinkedList<com.microsoft.graph.beta.models.security.AccountEntityMapping> accounts = new LinkedList<com.microsoft.graph.beta.models.security.AccountEntityMapping>();
com.microsoft.graph.beta.models.security.AccountEntityMapping accountEntityMapping = new com.microsoft.graph.beta.models.security.AccountEntityMapping();
accountEntityMapping.setNameColumn("AccountName");
accountEntityMapping.setNtDomainColumn("AccountDomain");
accountEntityMapping.setSidColumn("AccountSid");
accounts.add(accountEntityMapping);
entityMappings.setAccounts(accounts);
LinkedList<com.microsoft.graph.beta.models.security.HostEntityMapping> hosts = new LinkedList<com.microsoft.graph.beta.models.security.HostEntityMapping>();
com.microsoft.graph.beta.models.security.HostEntityMapping hostEntityMapping = new com.microsoft.graph.beta.models.security.HostEntityMapping();
hostEntityMapping.setDeviceIdColumn("DeviceId");
hostEntityMapping.setNameColumn("DeviceName");
hosts.add(hostEntityMapping);
entityMappings.setHosts(hosts);
LinkedList<com.microsoft.graph.beta.models.security.FileEntityMapping> files = new LinkedList<com.microsoft.graph.beta.models.security.FileEntityMapping>();
com.microsoft.graph.beta.models.security.FileEntityMapping fileEntityMapping = new com.microsoft.graph.beta.models.security.FileEntityMapping();
fileEntityMapping.setNameColumn("FileName");
fileEntityMapping.setSha1Column("SHA1");
fileEntityMapping.setSha256Column("SHA256");
files.add(fileEntityMapping);
entityMappings.setFiles(files);
alertTemplate.setEntityMappings(entityMappings);
LinkedList<com.microsoft.graph.beta.models.security.MitreTactic> tactics = new LinkedList<com.microsoft.graph.beta.models.security.MitreTactic>();
com.microsoft.graph.beta.models.security.MitreTactic mitreTactic = new com.microsoft.graph.beta.models.security.MitreTactic();
mitreTactic.setTactic("Execution");
LinkedList<com.microsoft.graph.beta.models.security.MitreTechnique> techniques = new LinkedList<com.microsoft.graph.beta.models.security.MitreTechnique>();
com.microsoft.graph.beta.models.security.MitreTechnique mitreTechnique = new com.microsoft.graph.beta.models.security.MitreTechnique();
mitreTechnique.setTechnique("T1059.001");
techniques.add(mitreTechnique);
mitreTactic.setTechniques(techniques);
tactics.add(mitreTactic);
alertTemplate.setTactics(tactics);
detectionAction.setAlertTemplate(alertTemplate);
detectionRule.setDetectionAction(detectionAction);
com.microsoft.graph.models.security.DetectionRule result = graphClient.security().rules().detectionRules().post(detectionRule);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const detectionRule = {
  '@odata.type': '#microsoft.graph.security.detectionRule',
  id: 'office-encoded-powershell',
  displayName: 'Suspicious encoded PowerShell from Office',
  description: 'Detects encoded PowerShell processes launched by Office applications, a common phishing payload pattern.',
  status: 'enabled',
  queryCondition: {
    queryText: 'DeviceProcessEvents | where InitiatingProcessFileName in~ (\'winword.exe\',\'excel.exe\',\'outlook.exe\') | where FileName == \'powershell.exe\' | where ProcessCommandLine has \'-enc\''
  },
  schedule: {
    frequency: 'PT1H'
  },
  detectionAction: {
    alertTemplate: {
      title: 'Suspicious encoded PowerShell from Office',
      description: 'An Office app launched an encoded PowerShell command, which may indicate phishing-driven code execution.',
      severity: 'high',
      recommendedActions: 'Investigate the parent Office document, isolate the device, and review the user\'s recent email activity.',
      entityMappings: {
        accounts: [
          {
            nameColumn: 'AccountName',
            ntDomainColumn: 'AccountDomain',
            sidColumn: 'AccountSid'
          }
        ],
        hosts: [
          {
            deviceIdColumn: 'DeviceId',
            nameColumn: 'DeviceName'
          }
        ],
        files: [
          {
            nameColumn: 'FileName',
            sha1Column: 'SHA1',
            sha256Column: 'SHA256'
          }
        ]
      },
      tactics: [
        {
          tactic: 'Execution',
          techniques: [
            {
              technique: 'T1059.001'
            }
          ]
        }
      ]
    }
  }
};

await client.api('/security/rules/detectionRules')
	.version('beta')
	.post(detectionRule);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Models\Security\DetectionRule;
use Microsoft\Graph\Beta\Generated\Models\Security\DetectionRuleStatus;
use Microsoft\Graph\Beta\Generated\Models\Security\QueryCondition;
use Microsoft\Graph\Beta\Generated\Models\Security\RuleSchedule;
use Microsoft\Graph\Beta\Generated\Models\Security\DetectionAction;
use Microsoft\Graph\Beta\Generated\Models\Security\AlertTemplate;
use Microsoft\Graph\Beta\Generated\Models\Security\AlertSeverity;
use Microsoft\Graph\Beta\Generated\Models\Security\EntityMappingConfiguration;
use Microsoft\Graph\Beta\Generated\Models\Security\AccountEntityMapping;
use Microsoft\Graph\Beta\Generated\Models\Security\HostEntityMapping;
use Microsoft\Graph\Beta\Generated\Models\Security\FileEntityMapping;
use Microsoft\Graph\Beta\Generated\Models\Security\MitreTactic;
use Microsoft\Graph\Beta\Generated\Models\Security\MitreTechnique;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new DetectionRule();
$requestBody->setOdataType('#microsoft.graph.security.detectionRule');
$requestBody->setId('office-encoded-powershell');
$requestBody->setDisplayName('Suspicious encoded PowerShell from Office');
$requestBody->setDescription('Detects encoded PowerShell processes launched by Office applications, a common phishing payload pattern.');
$requestBody->setStatus(new DetectionRuleStatus('enabled'));
$queryCondition = new QueryCondition();
$queryCondition->setQueryText('DeviceProcessEvents | where InitiatingProcessFileName in~ (\'winword.exe\',\'excel.exe\',\'outlook.exe\') | where FileName == \'powershell.exe\' | where ProcessCommandLine has \'-enc\'');
$requestBody->setQueryCondition($queryCondition);
$schedule = new RuleSchedule();
$schedule->setFrequency(new \DateInterval('PT1H'));
$requestBody->setSchedule($schedule);
$detectionAction = new DetectionAction();
$detectionActionAlertTemplate = new AlertTemplate();
$detectionActionAlertTemplate->setTitle('Suspicious encoded PowerShell from Office');
$detectionActionAlertTemplate->setDescription('An Office app launched an encoded PowerShell command, which may indicate phishing-driven code execution.');
$detectionActionAlertTemplate->setSeverity(new AlertSeverity('high'));
$detectionActionAlertTemplate->setRecommendedActions('Investigate the parent Office document, isolate the device, and review the user\'s recent email activity.');
$detectionActionAlertTemplateEntityMappings = new EntityMappingConfiguration();
$accountsAccountEntityMapping1 = new AccountEntityMapping();
$accountsAccountEntityMapping1->setNameColumn('AccountName');
$accountsAccountEntityMapping1->setNtDomainColumn('AccountDomain');
$accountsAccountEntityMapping1->setSidColumn('AccountSid');
$accountsArray []= $accountsAccountEntityMapping1;
$detectionActionAlertTemplateEntityMappings->setAccounts($accountsArray);

$hostsHostEntityMapping1 = new HostEntityMapping();
$hostsHostEntityMapping1->setDeviceIdColumn('DeviceId');
$hostsHostEntityMapping1->setNameColumn('DeviceName');
$hostsArray []= $hostsHostEntityMapping1;
$detectionActionAlertTemplateEntityMappings->setHosts($hostsArray);

$filesFileEntityMapping1 = new FileEntityMapping();
$filesFileEntityMapping1->setNameColumn('FileName');
$filesFileEntityMapping1->setSha1Column('SHA1');
$filesFileEntityMapping1->setSha256Column('SHA256');
$filesArray []= $filesFileEntityMapping1;
$detectionActionAlertTemplateEntityMappings->setFiles($filesArray);

$detectionActionAlertTemplate->setEntityMappings($detectionActionAlertTemplateEntityMappings);
$tacticsMitreTactic1 = new MitreTactic();
$tacticsMitreTactic1->setTactic('Execution');
$techniquesMitreTechnique1 = new MitreTechnique();
$techniquesMitreTechnique1->setTechnique('T1059.001');
$techniquesArray []= $techniquesMitreTechnique1;
$tacticsMitreTactic1->setTechniques($techniquesArray);

$tacticsArray []= $tacticsMitreTactic1;
$detectionActionAlertTemplate->setTactics($tacticsArray);

$detectionAction->setAlertTemplate($detectionActionAlertTemplate);
$requestBody->setDetectionAction($detectionAction);

$result = $graphServiceClient->security()->rules()->detectionRules()->post($requestBody)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Beta.Security

$params = @{
	"@odata.type" = "#microsoft.graph.security.detectionRule"
	id = "office-encoded-powershell"
	displayName = "Suspicious encoded PowerShell from Office"
	description = "Detects encoded PowerShell processes launched by Office applications, a common phishing payload pattern."
	status = "enabled"
	queryCondition = @{
		queryText = "DeviceProcessEvents | where InitiatingProcessFileName in~ ('winword.exe','excel.exe','outlook.exe') | where FileName == 'powershell.exe' | where ProcessCommandLine has '-enc'"
	}
	schedule = @{
		frequency = "PT1H"
	}
	detectionAction = @{
		alertTemplate = @{
			title = "Suspicious encoded PowerShell from Office"
			description = "An Office app launched an encoded PowerShell command, which may indicate phishing-driven code execution."
			severity = "high"
			recommendedActions = "Investigate the parent Office document, isolate the device, and review the user's recent email activity."
			entityMappings = @{
				accounts = @(
					@{
						nameColumn = "AccountName"
						ntDomainColumn = "AccountDomain"
						sidColumn = "AccountSid"
					}
				)
				hosts = @(
					@{
						deviceIdColumn = "DeviceId"
						nameColumn = "DeviceName"
					}
				)
				files = @(
					@{
						nameColumn = "FileName"
						sha1Column = "SHA1"
						sha256Column = "SHA256"
					}
				)
			}
			tactics = @(
				@{
					tactic = "Execution"
					techniques = @(
						@{
							technique = "T1059.001"
						}
					)
				}
			)
		}
	}
}

New-MgBetaSecurityRuleDetectionRule -BodyParameter $params
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.models.security.detection_rule import DetectionRule
from msgraph_beta.generated.models.detection_rule_status import DetectionRuleStatus
from msgraph_beta.generated.models.security.query_condition import QueryCondition
from msgraph_beta.generated.models.security.rule_schedule import RuleSchedule
from msgraph_beta.generated.models.security.detection_action import DetectionAction
from msgraph_beta.generated.models.security.alert_template import AlertTemplate
from msgraph_beta.generated.models.alert_severity import AlertSeverity
from msgraph_beta.generated.models.security.entity_mapping_configuration import EntityMappingConfiguration
from msgraph_beta.generated.models.security.account_entity_mapping import AccountEntityMapping
from msgraph_beta.generated.models.security.host_entity_mapping import HostEntityMapping
from msgraph_beta.generated.models.security.file_entity_mapping import FileEntityMapping
from msgraph_beta.generated.models.security.mitre_tactic import MitreTactic
from msgraph_beta.generated.models.security.mitre_technique import MitreTechnique
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = DetectionRule(
	odata_type = "#microsoft.graph.security.detectionRule",
	id = "office-encoded-powershell",
	display_name = "Suspicious encoded PowerShell from Office",
	description = "Detects encoded PowerShell processes launched by Office applications, a common phishing payload pattern.",
	status = DetectionRuleStatus.Enabled,
	query_condition = QueryCondition(
		query_text = "DeviceProcessEvents | where InitiatingProcessFileName in~ ('winword.exe','excel.exe','outlook.exe') | where FileName == 'powershell.exe' | where ProcessCommandLine has '-enc'",
	),
	schedule = RuleSchedule(
		frequency = "PT1H",
	),
	detection_action = DetectionAction(
		alert_template = AlertTemplate(
			title = "Suspicious encoded PowerShell from Office",
			description = "An Office app launched an encoded PowerShell command, which may indicate phishing-driven code execution.",
			severity = AlertSeverity.High,
			recommended_actions = "Investigate the parent Office document, isolate the device, and review the user's recent email activity.",
			entity_mappings = EntityMappingConfiguration(
				accounts = [
					AccountEntityMapping(
						name_column = "AccountName",
						nt_domain_column = "AccountDomain",
						sid_column = "AccountSid",
					),
				],
				hosts = [
					HostEntityMapping(
						device_id_column = "DeviceId",
						name_column = "DeviceName",
					),
				],
				files = [
					FileEntityMapping(
						name_column = "FileName",
						sha1_column = "SHA1",
						sha256_column = "SHA256",
					),
				],
			),
			tactics = [
				MitreTactic(
					tactic = "Execution",
					techniques = [
						MitreTechnique(
							technique = "T1059.001",
						),
					],
				),
			],
		),
	),
)

result = await graph_client.security.rules.detection_rules.post(request_body)
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
Location: https://graph.microsoft.com/beta/security/rules/detectionRules/office-encoded-powershell

{
  "@odata.type": "#microsoft.graph.security.detectionRule",
  "id": "office-encoded-powershell",
  "displayName": "Suspicious encoded PowerShell from Office",
  "description": "Detects encoded PowerShell processes launched by Office applications, a common phishing payload pattern.",
  "status": "enabled",
  "createdBy": "alice@contoso.com",
  "createdDateTime": "2026-05-25T10:15:00Z",
  "lastModifiedBy": "alice@contoso.com",
  "lastModifiedDateTime": "2026-05-25T10:15:00Z",
  "queryCondition": {
    "queryText": "DeviceProcessEvents | where InitiatingProcessFileName in~ ('winword.exe','excel.exe','outlook.exe') | where FileName == 'powershell.exe' | where ProcessCommandLine has '-enc'"
  },
  "schedule": {
    "frequency": "PT1H"
  },
  "detectionAction": {
    "alertTemplate": {
      "title": "Suspicious encoded PowerShell from Office",
      "description": "An Office app launched an encoded PowerShell command, which may indicate phishing-driven code execution.",
      "severity": "high",
      "recommendedActions": "Investigate the parent Office document, isolate the device, and review the user's recent email activity.",
      "entityMappings": {
        "accounts": [
          {
            "nameColumn": "AccountName",
            "sidColumn": "AccountSid"
          }
        ]
      },
      "tactics": [
        {
          "tactic": "Execution",
          "techniques": [
            {
              "technique": "T1059.001"
            }
          ]
        }
      ]
    },
    "automatedActions": {
      "isolateDevices": [
        {
          "deviceIdColumn": "DeviceId",
          "isolationType": "full"
        }
      ],
      "initiateInvestigations": [
        {
          "deviceIdColumn": "DeviceId"
        }
      ]
    }
  }
}
```
