<!-- Source: https://learn.microsoft.com/en-us/graph/api/security-auditcoreroot-post-auditlogqueries?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-09-18 -->

# Create auditLogQuery

Namespace: microsoft.graph.security

Create a new [auditLogQuery](https://learn.microsoft.com/en-us/graph/api/resources/security-auditlogquery?view=graph-rest-1.0) object.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Auditing data can be accessed through Microsoft Purview Audit Search API via the following permissions, which are classified at a Microsoft 365 service level. To learn more, including how to choose permissions, see [Permissions](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | AuditLogsQuery-Entra.Read.All | AuditLogsQuery-CRM.Read.All, AuditLogsQuery-Endpoint.Read.All, AuditLogsQuery-Exchange.Read.All, AuditLogsQuery-OneDrive.Read.All, AuditLogsQuery-SharePoint.Read.All, AuditLogsQuery.Read.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | AuditLogsQuery-Entra.Read.All | AuditLogsQuery-CRM.Read.All, AuditLogsQuery-Endpoint.Read.All, AuditLogsQuery-Exchange.Read.All, AuditLogsQuery-OneDrive.Read.All, AuditLogsQuery-SharePoint.Read.All, AuditLogsQuery.Read.All |

## HTTP request

```http
POST /security/auditLog/queries
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the [auditLogQuery](https://learn.microsoft.com/en-us/graph/api/resources/security-auditlogquery?view=graph-rest-1.0) object.

You can specify the following properties when creating a **auditLogQuery**.

| Property | Type | Description |
| :--- | :--- | :--- |
| displayName | String | Display name for the saved audit log query. Optional. |
| filterStartDateTime | DateTimeOffset | Start date of the date range in the query. Optional. |
| filterEndDateTime | DateTimeOffset | End date of the date range in the query. Optional. |
| recordTypeFilters | Collection\(string\) of microsoft.graph.security.auditLogRecordType | The operation type or types indicated by the record. The possible values are: `exchangeAdmin`, `exchangeItem`, `exchangeItemGroup`, `sharePoint`, `syntheticProbe`, `sharePointFileOperation`, `oneDrive`, `azureActiveDirectory`, `azureActiveDirectoryAccountLogon`, `dataCenterSecurityCmdlet`, `complianceDLPSharePoint`, `sway`, `complianceDLPExchange`, `sharePointSharingOperation`, `azureActiveDirectoryStsLogon`, `skypeForBusinessPSTNUsage`, `skypeForBusinessUsersBlocked`, `securityComplianceCenterEOPCmdlet`, `exchangeAggregatedOperation`, `powerBIAudit`, `crm`, `yammer`, `skypeForBusinessCmdlets`, `discovery`, `microsoftTeams`, `threatIntelligence`, `mailSubmission`, `microsoftFlow`, `aeD`, `microsoftStream`, `complianceDLPSharePointClassification`, `threatFinder`, `project`, `sharePointListOperation`, `sharePointCommentOperation`, `dataGovernance`, `kaizala`, `securityComplianceAlerts`, `threatIntelligenceUrl`, `securityComplianceInsights`, `mipLabel`, `workplaceAnalytics`, `powerAppsApp`, `powerAppsPlan`, `threatIntelligenceAtpContent`, `labelContentExplorer`, `teamsHealthcare`, `exchangeItemAggregated`, `hygieneEvent`, `dataInsightsRestApiAudit`, `informationBarrierPolicyApplication`, `sharePointListItemOperation`, `sharePointContentTypeOperation`, `sharePointFieldOperation`, `microsoftTeamsAdmin`, `hrSignal`, `microsoftTeamsDevice`, `microsoftTeamsAnalytics`, `informationWorkerProtection`, `campaign`, `dlpEndpoint`, `airInvestigation`, `quarantine`, `microsoftForms`, `applicationAudit`, `complianceSupervisionExchange`, `customerKeyServiceEncryption`, `officeNative`, `mipAutoLabelSharePointItem`, `mipAutoLabelSharePointPolicyLocation`, `microsoftTeamsShifts`, `secureScore`, `mipAutoLabelExchangeItem`, `cortanaBriefing`, `search`, `wdatpAlerts`, `powerPlatformAdminDlp`, `powerPlatformAdminEnvironment`, `mdatpAudit`, `sensitivityLabelPolicyMatch`, `sensitivityLabelAction`, `sensitivityLabeledFileAction`, `attackSim`, `airManualInvestigation`, `securityComplianceRBAC`, `userTraining`, `airAdminActionInvestigation`, `mstic`, `physicalBadgingSignal`, `teamsEasyApprovals`, `aipDiscover`, `aipSensitivityLabelAction`, `aipProtectionAction`, `aipFileDeleted`, `aipHeartBeat`, `mcasAlerts`, `onPremisesFileShareScannerDlp`, `onPremisesSharePointScannerDlp`, `exchangeSearch`, `sharePointSearch`, `privacyDataMinimization`, `labelAnalyticsAggregate`, `myAnalyticsSettings`, `securityComplianceUserChange`, `complianceDLPExchangeClassification`, `complianceDLPEndpoint`, `mipExactDataMatch`, `msdeResponseActions`, `msdeGeneralSettings`, `msdeIndicatorsSettings`, `ms365DCustomDetection`, `msdeRolesSettings`, `mapgAlerts`, `mapgPolicy`, `mapgRemediation`, `privacyRemediationAction`, `privacyDigestEmail`, `mipAutoLabelSimulationProgress`, `mipAutoLabelSimulationCompletion`, `mipAutoLabelProgressFeedback`, `dlpSensitiveInformationType`, `mipAutoLabelSimulationStatistics`, `largeContentMetadata`, `microsoft365Group`, `cdpMlInferencingResult`, `filteringMailMetadata`, `cdpClassificationMailItem`, `cdpClassificationDocument`, `officeScriptsRunAction`, `filteringPostMailDeliveryAction`, `cdpUnifiedFeedback`, `tenantAllowBlockList`, `consumptionResource`, `healthcareSignal`, `dlpImportResult`, `cdpCompliancePolicyExecution`, `multiStageDisposition`, `privacyDataMatch`, `filteringDocMetadata`, `filteringEmailFeatures`, `powerBIDlp`, `filteringUrlInfo`, `filteringAttachmentInfo`, `coreReportingSettings`, `complianceConnector`, `powerPlatformLockboxResourceAccessRequest`, `powerPlatformLockboxResourceCommand`, `cdpPredictiveCodingLabel`, `cdpCompliancePolicyUserFeedback`, `webpageActivityEndpoint`, `omePortal`, `cmImprovementActionChange`, `filteringUrlClick`, `mipLabelAnalyticsAuditRecord`, `filteringEntityEvent`, `filteringRuleHits`, `filteringMailSubmission`, `labelExplorer`, `microsoftManagedServicePlatform`, `powerPlatformServiceActivity`, `scorePlatformGenericAuditRecord`, `filteringTimeTravelDocMetadata`, `alert`, `alertStatus`, `alertIncident`, `incidentStatus`, `case`, `caseInvestigation`, `recordsManagement`, `privacyRemediation`, `dataShareOperation`, `cdpDlpSensitive`, `ehrConnector`, `filteringMailGradingResult`, `publicFolder`, `privacyTenantAuditHistoryRecord`, `aipScannerDiscoverEvent`, `eduDataLakeDownloadOperation`, `m365ComplianceConnector`, `microsoftGraphDataConnectOperation`, `microsoftPurview`, `filteringEmailContentFeatures`, `powerPagesSite`, `powerAppsResource`, `plannerPlan`, `plannerCopyPlan`, `plannerTask`, `plannerRoster`, `plannerPlanList`, `plannerTaskList`, `plannerTenantSettings`, `projectForTheWebProject`, `projectForTheWebTask`, `projectForTheWebRoadmap`, `projectForTheWebRoadmapItem`, `projectForTheWebProjectSettings`, `projectForTheWebRoadmapSettings`, `quarantineMetadata`, `microsoftTodoAudit`, `timeTravelFilteringDocMetadata`, `teamsQuarantineMetadata`, `sharePointAppPermissionOperation`, `microsoftTeamsSensitivityLabelAction`, `filteringTeamsMetadata`, `filteringTeamsUrlInfo`, `filteringTeamsPostDeliveryAction`, `mdcAssessments`, `mdcRegulatoryComplianceStandards`, `mdcRegulatoryComplianceControls`, `mdcRegulatoryComplianceAssessments`, `mdcSecurityConnectors`, `mdaDataSecuritySignal`, `vivaGoals`, `filteringRuntimeInfo`, `attackSimAdmin`, `microsoftGraphDataConnectConsent`, `filteringAtpDetonationInfo`, `privacyPortal`, `managedTenants`, `unifiedSimulationMatchedItem`, `unifiedSimulationSummary`, `updateQuarantineMetadata`, `ms365DSuppressionRule`, `purviewDataMapOperation`, `filteringUrlPostClickAction`, `irmUserDefinedDetectionSignal`, `teamsUpdates`, `plannerRosterSensitivityLabel`, `ms365DIncident`, `filteringDelistingMetadata`, `complianceDLPSharePointClassificationExtended`, `microsoftDefenderForIdentityAudit`, `supervisoryReviewDayXInsight`, `defenderExpertsforXDRAdmin`, `cdpEdgeBlockedMessage`, `hostedRpa`, `cdpContentExplorerAggregateRecord`, `cdpHygieneAttachmentInfo`, `cdpHygieneSummary`, `cdpPostMailDeliveryAction`, `cdpEmailFeatures`, `cdpHygieneUrlInfo`, `cdpUrlClick`, `cdpPackageManagerHygieneEvent`, `filteringDocScan`, `timeTravelFilteringDocScan`, `mapgOnboard`, `unknownFutureValue`. Optional. |
| keywordFilter | String | Free text field to search non-indexed properties of the audit log. Optional. |
| serviceFilter | String | Refers to the workload property in the audit record. This is the Microsoft service where the activity occurred. Optional. |
| operationFilters | String collection | The name of the user or admin activity. For a description of the most common operations/activities, see [Search the audit log in the Office 365 Protection Center](https://go.microsoft.com/fwlink/p/?LinkId=708432). Optional. |
| userPrincipalNameFilters | String collection | The UPN \(user principal name\) of the user who performed the action \(specified in the operation property\) that resulted in the record being logged; for example, *my\_name@my\_domain\_name*. Optional. |
| ipAddressFilters | String collection | The IP address of the device that was used when the activity was logged. Optional. |
| objectIdFilters | String collection | For SharePoint and OneDrive for Business activity, the full path name of the file or folder accessed by the user. For Exchange admin audit logging, the name of the object that was modified by the cmdlet. Optional. |
| administrativeUnitIdFilters | String collection | Administrative units tagged to an audit log record. Optional. |
| status | microsoft.graph.security.auditLogQueryStatus | Current status of the query. The possible values are: `notStarted`, `running`, `succeeded`, `failed`, `cancelled`, `unknownFutureValue`. Optional. |

## Response

If successful, this method returns a `201 Created` response code and a [auditLogQuery](https://learn.microsoft.com/en-us/graph/api/resources/security-auditlogquery?view=graph-rest-1.0) object in the response body.

Note

This method is subject to tenant-level daily submission and concurrent-query limits. A tenant receives a baseline allocation, and tenants with more eligible licenses can receive a higher allocation. For details and retry guidance, see [Microsoft Graph service-specific throttling limits](https://learn.microsoft.com/en-us/graph/throttling-limits#security-audit-log-query-service-limits).

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
POST https://graph.microsoft.com/v1.0/security/auditLog/queries
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.security.auditLogQuery",
  "displayName": "String",
  "filterStartDateTime": "String (timestamp)",
  "filterEndDateTime": "String (timestamp)",
  "recordTypeFilters": [
    "String"
  ],
  "keywordFilter": "String",
  "serviceFilter": "String",
  "operationFilters": [
    "String"
  ],
  "userPrincipalNameFilters": [
    "String"
  ],
  "ipAddressFilters": [
    "String"
  ],
  "objectIdFilters": [
    "String"
  ],
  "administrativeUnitIdFilters": [
    "String"
  ],
  "status": "String"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models.Security;

var requestBody = new AuditLogQuery
{
	OdataType = "#microsoft.graph.security.auditLogQuery",
	DisplayName = "String",
	FilterStartDateTime = DateTimeOffset.Parse("String (timestamp)"),
	FilterEndDateTime = DateTimeOffset.Parse("String (timestamp)"),
	RecordTypeFilters = new List<AuditLogRecordType?>
	{
		AuditLogRecordType.ExchangeAdmin,
	},
	KeywordFilter = "String",
	OperationFilters = new List<string>
	{
		"String",
	},
	UserPrincipalNameFilters = new List<string>
	{
		"String",
	},
	IpAddressFilters = new List<string>
	{
		"String",
	},
	ObjectIdFilters = new List<string>
	{
		"String",
	},
	AdministrativeUnitIdFilters = new List<string>
	{
		"String",
	},
	Status = AuditLogQueryStatus.NotStarted,
	AdditionalData = new Dictionary<string, object>
	{
		{
			"serviceFilter" , "String"
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Security.AuditLog.Queries.PostAsync(requestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  "time"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphmodelssecurity "github.com/microsoftgraph/msgraph-sdk-go/models/security"
	  //other-imports
)

requestBody := graphmodelssecurity.NewAuditLogQuery()
displayName := "String"
requestBody.SetDisplayName(&displayName) 
filterStartDateTime , err := time.Parse(time.RFC3339, "String (timestamp)")
requestBody.SetFilterStartDateTime(&filterStartDateTime) 
filterEndDateTime , err := time.Parse(time.RFC3339, "String (timestamp)")
requestBody.SetFilterEndDateTime(&filterEndDateTime) 
recordTypeFilters := []graphmodelssecurity.AuditLogRecordTypeable {
	auditLogRecordType := graphmodels.STRING_AUDITLOGRECORDTYPE 
	requestBody.SetAuditLogRecordType(&auditLogRecordType)
}
requestBody.SetRecordTypeFilters(recordTypeFilters)
keywordFilter := "String"
requestBody.SetKeywordFilter(&keywordFilter) 
operationFilters := []string {
	"String",
}
requestBody.SetOperationFilters(operationFilters)
userPrincipalNameFilters := []string {
	"String",
}
requestBody.SetUserPrincipalNameFilters(userPrincipalNameFilters)
ipAddressFilters := []string {
	"String",
}
requestBody.SetIpAddressFilters(ipAddressFilters)
objectIdFilters := []string {
	"String",
}
requestBody.SetObjectIdFilters(objectIdFilters)
administrativeUnitIdFilters := []string {
	"String",
}
requestBody.SetAdministrativeUnitIdFilters(administrativeUnitIdFilters)
status := graphmodels.STRING_AUDITLOGQUERYSTATUS 
requestBody.SetStatus(&status) 
additionalData := map[string]interface{}{
	"serviceFilter" : "String", 
}
requestBody.SetAdditionalData(additionalData)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
queries, err := graphClient.Security().AuditLog().Queries().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.models.security.AuditLogQuery auditLogQuery = new com.microsoft.graph.models.security.AuditLogQuery();
auditLogQuery.setOdataType("#microsoft.graph.security.auditLogQuery");
auditLogQuery.setDisplayName("String");
OffsetDateTime filterStartDateTime = OffsetDateTime.parse("String (timestamp)");
auditLogQuery.setFilterStartDateTime(filterStartDateTime);
OffsetDateTime filterEndDateTime = OffsetDateTime.parse("String (timestamp)");
auditLogQuery.setFilterEndDateTime(filterEndDateTime);
LinkedList<com.microsoft.graph.models.security.com.microsoft.graph.models.security.AuditLogRecordType> recordTypeFilters = new LinkedList<com.microsoft.graph.models.security.com.microsoft.graph.models.security.AuditLogRecordType>();
recordTypeFilters.add(com.microsoft.graph.models.security.AuditLogRecordType.ExchangeAdmin);
auditLogQuery.setRecordTypeFilters(recordTypeFilters);
auditLogQuery.setKeywordFilter("String");
LinkedList<String> operationFilters = new LinkedList<String>();
operationFilters.add("String");
auditLogQuery.setOperationFilters(operationFilters);
LinkedList<String> userPrincipalNameFilters = new LinkedList<String>();
userPrincipalNameFilters.add("String");
auditLogQuery.setUserPrincipalNameFilters(userPrincipalNameFilters);
LinkedList<String> ipAddressFilters = new LinkedList<String>();
ipAddressFilters.add("String");
auditLogQuery.setIpAddressFilters(ipAddressFilters);
LinkedList<String> objectIdFilters = new LinkedList<String>();
objectIdFilters.add("String");
auditLogQuery.setObjectIdFilters(objectIdFilters);
LinkedList<String> administrativeUnitIdFilters = new LinkedList<String>();
administrativeUnitIdFilters.add("String");
auditLogQuery.setAdministrativeUnitIdFilters(administrativeUnitIdFilters);
auditLogQuery.setStatus(com.microsoft.graph.models.security.AuditLogQueryStatus.NotStarted);
HashMap<String, Object> additionalData = new HashMap<String, Object>();
additionalData.put("serviceFilter", "String");
auditLogQuery.setAdditionalData(additionalData);
com.microsoft.graph.models.security.AuditLogQuery result = graphClient.security().auditLog().queries().post(auditLogQuery);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const auditLogQuery = {
  '@odata.type': '#microsoft.graph.security.auditLogQuery',
  displayName: 'String',
  filterStartDateTime: 'String (timestamp)',
  filterEndDateTime: 'String (timestamp)',
  recordTypeFilters: [
    'String'
  ],
  keywordFilter: 'String',
  serviceFilter: 'String',
  operationFilters: [
    'String'
  ],
  userPrincipalNameFilters: [
    'String'
  ],
  ipAddressFilters: [
    'String'
  ],
  objectIdFilters: [
    'String'
  ],
  administrativeUnitIdFilters: [
    'String'
  ],
  status: 'String'
};

await client.api('/security/auditLog/queries')
	.post(auditLogQuery);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\Security\AuditLogQuery;
use Microsoft\Graph\Generated\Models\Security\AuditLogRecordType;
use Microsoft\Graph\Generated\Models\Security\AuditLogQueryStatus;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new AuditLogQuery();
$requestBody->setOdataType('#microsoft.graph.security.auditLogQuery');
$requestBody->setDisplayName('String');
$requestBody->setFilterStartDateTime(new \DateTime('String (timestamp)'));
$requestBody->setFilterEndDateTime(new \DateTime('String (timestamp)'));
$requestBody->setRecordTypeFilters([new AuditLogRecordType('string'),	]);
$requestBody->setKeywordFilter('String');
$requestBody->setOperationFilters(['String', 	]);
$requestBody->setUserPrincipalNameFilters(['String', 	]);
$requestBody->setIpAddressFilters(['String', 	]);
$requestBody->setObjectIdFilters(['String', 	]);
$requestBody->setAdministrativeUnitIdFilters(['String', 	]);
$requestBody->setStatus(new AuditLogQueryStatus('string'));
$additionalData = [
	'serviceFilter' => 'String',
];
$requestBody->setAdditionalData($additionalData);

$result = $graphServiceClient->security()->auditLog()->queries()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Security

$params = @{
	"@odata.type" = "#microsoft.graph.security.auditLogQuery"
	displayName = "String"
	filterStartDateTime = [System.DateTime]::Parse("String (timestamp)")
	filterEndDateTime = [System.DateTime]::Parse("String (timestamp)")
	recordTypeFilters = @(
	"String"
)
keywordFilter = "String"
serviceFilter = "String"
operationFilters = @(
"String"
)
userPrincipalNameFilters = @(
"String"
)
ipAddressFilters = @(
"String"
)
objectIdFilters = @(
"String"
)
administrativeUnitIdFilters = @(
"String"
)
status = "String"
}

New-MgSecurityAuditLogQuery -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.security.audit_log_query import AuditLogQuery
from msgraph.generated.models.security.audit_log_record_type import AuditLogRecordType
from msgraph.generated.models.audit_log_record_type import AuditLogRecordType
from msgraph.generated.models.audit_log_query_status import AuditLogQueryStatus
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = AuditLogQuery(
	odata_type = "#microsoft.graph.security.auditLogQuery",
	display_name = "String",
	filter_start_date_time = "String (timestamp)",
	filter_end_date_time = "String (timestamp)",
	record_type_filters = [
		AuditLogRecordType.ExchangeAdmin,
	],
	keyword_filter = "String",
	operation_filters = [
		"String",
	],
	user_principal_name_filters = [
		"String",
	],
	ip_address_filters = [
		"String",
	],
	object_id_filters = [
		"String",
	],
	administrative_unit_id_filters = [
		"String",
	],
	status = AuditLogQueryStatus.NotStarted,
	additional_data = {
			"service_filter" : "String",
	}
)

result = await graph_client.security.audit_log.queries.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

---

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.security.auditLogQuery",
  "id": "168ec429-084b-a489-90d8-504a87846305",
  "displayName": "String",
  "filterStartDateTime": "String (timestamp)",
  "filterEndDateTime": "String (timestamp)",
  "recordTypeFilters": [
    "String"
  ],
  "keywordFilter": "String",
  "serviceFilter": "String",
  "operationFilters": [
    "String"
  ],
  "userPrincipalNameFilters": [
    "String"
  ],
  "ipAddressFilters": [
    "String"
  ],
  "objectIdFilters": [
    "String"
  ],
  "administrativeUnitIdFilters": [
    "String"
  ],
  "status": "String"
}
```
