<!-- Source: https://learn.microsoft.com/en-us/graph/api/attacksimulationroot-post-simulation?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-12-04 -->

# Create simulation

Namespace: microsoft.graph

Create an attack simulation campaign for a tenant.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | AttackSimulation.ReadWrite.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | AttackSimulation.ReadWrite.All | Not available. |

## HTTP request

```http
POST /security/attackSimulation/simulations
```

## Request headers

| Header | Value |
| --- | --- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json |

## Request body

In the request body, supply a JSON representation of a [simulation](https://learn.microsoft.com/en-us/graph/api/resources/simulation?view=graph-rest-1.0) object.

The following table lists the properties that are required when you create the simulation.

| Property | Type | Description |
| :--- | :--- | :--- |
| attackTechnique | [simulationAttackTechnique](https://learn.microsoft.com/en-us/graph/api/resources/simulation?view=graph-rest-1.0#simulationattacktechnique-values) | The social engineering technique used in the attack simulation and training campaign. Supports `$filter` and `$orderby`. The possible values are: `unknown`, `credentialHarvesting`, `attachmentMalware`, `driveByUrl`, `linkInAttachment`, `linkToMalwareFile`, `unknownFutureValue`, `oAuthConsentGrant`. Use the `Prefer: include-unknown-enum-members` request header to get the following values from this [evolvable enum](https://learn.microsoft.com/en-us/graph/best-practices-concept#handling-future-members-in-evolvable-enumerations): `oAuthConsentGrant`. For more information about the types of social engineering attack techniques, see [simulations](https://learn.microsoft.com/en-us/microsoft-365/security/office-365-security/attack-simulation-training-get-started?view=o365-worldwide&preserve-view=true#simulations). |
| attackType | [simulationAttackType](https://learn.microsoft.com/en-us/graph/api/resources/simulation?view=graph-rest-1.0#simulationattacktype-values) | Attack type of the attack simulation and training campaign. Supports `$filter` and `$orderby`. The possible values are: `unknown`, `social`, `cloud`, `endpoint`, `unknownFutureValue`. |
| createdBy | [emailIdentity](https://learn.microsoft.com/en-us/graph/api/resources/emailidentity?view=graph-rest-1.0) | Identity of the user who created the attack simulation and training campaign. |
| displayName | String | Display name of the attack simulation and training campaign. Supports `$filter` and `$orderby`. |
| durationInDays | Int32 | Simulation duration in days. Optional. |
| endUserNotificationSetting | [endUserNotificationSetting](https://learn.microsoft.com/en-us/graph/api/resources/endusernotificationsetting?view=graph-rest-1.0) | The end user notification setting for the attack simulation and training campaign. |
| includedAccountTarget | [accountTargetContent](https://learn.microsoft.com/en-us/graph/api/resources/accounttargetcontent?view=graph-rest-1.0) | Users targeted in the simulation. |
| landingPage | [landingPage](https://learn.microsoft.com/en-us/graph/api/resources/landingpage?view=graph-rest-1.0) | The landing page associated with the attack simulation and training campaign. |
| lastModifiedBy | [emailIdentity](https://learn.microsoft.com/en-us/graph/api/resources/emailidentity?view=graph-rest-1.0) | Identity of the user who most recently modified the attack simulation and training campaign. |
| launchDateTime | DateTimeOffset | Date and time of the launch/start of the attack simulation and training campaign. Supports `$filter` and `$orderby`. The timestamp represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. |
| loginPage | [loginPage](https://learn.microsoft.com/en-us/graph/api/resources/loginpage?view=graph-rest-1.0) | The login page associated with the attack simulation and training campaign. |
| oAuthConsentAppDetail | [oAuthConsentAppDetail](https://learn.microsoft.com/en-us/graph/api/resources/oauthconsentappdetail?view=graph-rest-1.0) | Details required for the `oAuthConsentGrant` technique. |
| payload | [payload](https://learn.microsoft.com/en-us/graph/api/resources/payload?view=graph-rest-1.0) | The payload associated with the attack simulation and training campaign. |
| payloadDeliveryPlatform | payloadDeliveryPlatform | Method of delivery of the phishing payload used in the attack simulation and training campaign. The possible values are: `unknown`, `sms`, `email`, `teams`, `unknownFutureValue`. |
| status | [simulationStatus](https://learn.microsoft.com/en-us/graph/api/resources/simulation?view=graph-rest-1.0#simulationstatus-values) | Status of the attack simulation and training campaign. Supports `$filter` and `$orderby`. The possible values are: `unknown`, `draft`, `running`, `scheduled`, `succeeded`, `failed`, `cancelled`, `excluded`, `unknownFutureValue`. |
| trainingSetting | [trainingSetting](https://learn.microsoft.com/en-us/graph/api/resources/trainingsetting?view=graph-rest-1.0) | The training setting for the attack simulation and training campaign. |

## Response

If successful, this method returns a `202 Accepted` response code and a tracking header named `location` in the response.

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
POST https://graph.microsoft.com/v1.0/security/attackSimulation/simulations
Content-type: application/json

{
  "displayName": "Graph Simulation",
  "payload@odata.bind": "https://graph.microsoft.com/v1.0/security/attacksimulation/payloads/12345678-9abc-def0-123456789a",
  "loginPage@odata.bind": "https://graph.microsoft.com/v1.0/security/attacksimulation/loginPages/1w345678-9abc-def0-123456789a",
  "landingPage@odata.bind": "https://graph.microsoft.com/v1.0/security/attacksimulation/landingPages/1c345678-9abc-def0-123456789a",
  "createdBy": {
    "email": "john@contoso.com"
  },
  "durationInDays": "3",
  "attackTechnique": "credentialHarvesting",
  "status": "scheduled",
  "includedAccountTarget": {
    "@odata.type": "#microsoft.graph.addressBookAccountTargetContent",
    "type": "addressBook",
    "accountTargetEmails": [
      "john@contoso.com"
    ]
  },
  "trainingSetting": {
    "settingType": "noTraining"
  },
  "endUserNotificationSetting": {
    "notificationPreference": "microsoft",
    "settingType": "noTraining",
    "positiveReinforcement": {
      "deliveryPreference": "deliverAfterCampaignEnd",
      "endUserNotification@odata.bind": "https://graph.microsoft.com/v1.0/security/attacksimulation/endUserNotifications/1ewer3678-9abc-def0-123456789a",
      "defaultLanguage": "en"
    },
    "simulationNotification": {
      "targettedUserType": "compromised",
      "endUserNotification@odata.bind": "https://graph.microsoft.com/v1.0/security/attacksimulation/endUserNotifications/12wer3678-9abc-def0-123456789a",
      "defaultLanguage": "en"
    }
  }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;
using Microsoft.Kiota.Abstractions.Serialization;

var requestBody = new Simulation
{
	DisplayName = "Graph Simulation",
	CreatedBy = new EmailIdentity
	{
		Email = "john@contoso.com",
	},
	DurationInDays = 3,
	AttackTechnique = SimulationAttackTechnique.CredentialHarvesting,
	Status = SimulationStatus.Scheduled,
	IncludedAccountTarget = new AddressBookAccountTargetContent
	{
		OdataType = "#microsoft.graph.addressBookAccountTargetContent",
		Type = AccountTargetContentType.AddressBook,
		AccountTargetEmails = new List<string>
		{
			"john@contoso.com",
		},
	},
	TrainingSetting = new TrainingSetting
	{
		SettingType = TrainingSettingType.NoTraining,
	},
	EndUserNotificationSetting = new EndUserNotificationSetting
	{
		NotificationPreference = EndUserNotificationPreference.Microsoft,
		SettingType = EndUserNotificationSettingType.NoTraining,
		PositiveReinforcement = new PositiveReinforcementNotification
		{
			DeliveryPreference = NotificationDeliveryPreference.DeliverAfterCampaignEnd,
			DefaultLanguage = "en",
			AdditionalData = new Dictionary<string, object>
			{
				{
					"endUserNotification@odata.bind" , "https://graph.microsoft.com/v1.0/security/attacksimulation/endUserNotifications/1ewer3678-9abc-def0-123456789a"
				},
			},
		},
		AdditionalData = new Dictionary<string, object>
		{
			{
				"simulationNotification" , new UntypedObject(new Dictionary<string, UntypedNode>
				{
					{
						"targettedUserType", new UntypedString("compromised")
					},
					{
						"endUserNotification@odata.bind", new UntypedString("https://graph.microsoft.com/v1.0/security/attacksimulation/endUserNotifications/12wer3678-9abc-def0-123456789a")
					},
					{
						"defaultLanguage", new UntypedString("en")
					},
				})
			},
		},
	},
	AdditionalData = new Dictionary<string, object>
	{
		{
			"payload@odata.bind" , "https://graph.microsoft.com/v1.0/security/attacksimulation/payloads/12345678-9abc-def0-123456789a"
		},
		{
			"loginPage@odata.bind" , "https://graph.microsoft.com/v1.0/security/attacksimulation/loginPages/1w345678-9abc-def0-123456789a"
		},
		{
			"landingPage@odata.bind" , "https://graph.microsoft.com/v1.0/security/attacksimulation/landingPages/1c345678-9abc-def0-123456789a"
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Security.AttackSimulation.Simulations.PostAsync(requestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphmodels "github.com/microsoftgraph/msgraph-sdk-go/models"
	  //other-imports
)

requestBody := graphmodels.NewSimulation()
displayName := "Graph Simulation"
requestBody.SetDisplayName(&displayName) 
createdBy := graphmodels.NewEmailIdentity()
email := "john@contoso.com"
createdBy.SetEmail(&email) 
requestBody.SetCreatedBy(createdBy)
durationInDays := int32(3)
requestBody.SetDurationInDays(&durationInDays) 
attackTechnique := graphmodels.CREDENTIALHARVESTING_SIMULATIONATTACKTECHNIQUE 
requestBody.SetAttackTechnique(&attackTechnique) 
status := graphmodels.SCHEDULED_SIMULATIONSTATUS 
requestBody.SetStatus(&status) 
includedAccountTarget := graphmodels.NewAddressBookAccountTargetContent()
type := graphmodels.ADDRESSBOOK_ACCOUNTTARGETCONTENTTYPE 
includedAccountTarget.SetType(&type) 
accountTargetEmails := []string {
	"john@contoso.com",
}
includedAccountTarget.SetAccountTargetEmails(accountTargetEmails)
requestBody.SetIncludedAccountTarget(includedAccountTarget)
trainingSetting := graphmodels.NewTrainingSetting()
settingType := graphmodels.NOTRAINING_TRAININGSETTINGTYPE 
trainingSetting.SetSettingType(&settingType) 
requestBody.SetTrainingSetting(trainingSetting)
endUserNotificationSetting := graphmodels.NewEndUserNotificationSetting()
notificationPreference := graphmodels.MICROSOFT_ENDUSERNOTIFICATIONPREFERENCE 
endUserNotificationSetting.SetNotificationPreference(&notificationPreference) 
settingType := graphmodels.NOTRAINING_ENDUSERNOTIFICATIONSETTINGTYPE 
endUserNotificationSetting.SetSettingType(&settingType) 
positiveReinforcement := graphmodels.NewPositiveReinforcementNotification()
deliveryPreference := graphmodels.DELIVERAFTERCAMPAIGNEND_NOTIFICATIONDELIVERYPREFERENCE 
positiveReinforcement.SetDeliveryPreference(&deliveryPreference) 
defaultLanguage := "en"
positiveReinforcement.SetDefaultLanguage(&defaultLanguage) 
additionalData := map[string]interface{}{
	"endUserNotification@odata.bind" : "https://graph.microsoft.com/v1.0/security/attacksimulation/endUserNotifications/1ewer3678-9abc-def0-123456789a", 
}
positiveReinforcement.SetAdditionalData(additionalData)
endUserNotificationSetting.SetPositiveReinforcement(positiveReinforcement)
additionalData := map[string]interface{}{
simulationNotification := graph.New()
targettedUserType := "compromised"
simulationNotification.SetTargettedUserType(&targettedUserType) 
odataBind := "https://graph.microsoft.com/v1.0/security/attacksimulation/endUserNotifications/12wer3678-9abc-def0-123456789a"
simulationNotification.SetOdataBind(&odataBind) 
defaultLanguage := "en"
simulationNotification.SetDefaultLanguage(&defaultLanguage) 
	endUserNotificationSetting.SetSimulationNotification(simulationNotification)
}
endUserNotificationSetting.SetAdditionalData(additionalData)
requestBody.SetEndUserNotificationSetting(endUserNotificationSetting)
additionalData := map[string]interface{}{
	"payload@odata.bind" : "https://graph.microsoft.com/v1.0/security/attacksimulation/payloads/12345678-9abc-def0-123456789a", 
	"loginPage@odata.bind" : "https://graph.microsoft.com/v1.0/security/attacksimulation/loginPages/1w345678-9abc-def0-123456789a", 
	"landingPage@odata.bind" : "https://graph.microsoft.com/v1.0/security/attacksimulation/landingPages/1c345678-9abc-def0-123456789a", 
}
requestBody.SetAdditionalData(additionalData)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
simulations, err := graphClient.Security().AttackSimulation().Simulations().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

Simulation simulation = new Simulation();
simulation.setDisplayName("Graph Simulation");
EmailIdentity createdBy = new EmailIdentity();
createdBy.setEmail("john@contoso.com");
simulation.setCreatedBy(createdBy);
simulation.setDurationInDays(3);
simulation.setAttackTechnique(SimulationAttackTechnique.CredentialHarvesting);
simulation.setStatus(SimulationStatus.Scheduled);
AddressBookAccountTargetContent includedAccountTarget = new AddressBookAccountTargetContent();
includedAccountTarget.setOdataType("#microsoft.graph.addressBookAccountTargetContent");
includedAccountTarget.setType(AccountTargetContentType.AddressBook);
LinkedList<String> accountTargetEmails = new LinkedList<String>();
accountTargetEmails.add("john@contoso.com");
includedAccountTarget.setAccountTargetEmails(accountTargetEmails);
simulation.setIncludedAccountTarget(includedAccountTarget);
TrainingSetting trainingSetting = new TrainingSetting();
trainingSetting.setSettingType(TrainingSettingType.NoTraining);
simulation.setTrainingSetting(trainingSetting);
EndUserNotificationSetting endUserNotificationSetting = new EndUserNotificationSetting();
endUserNotificationSetting.setNotificationPreference(EndUserNotificationPreference.Microsoft);
endUserNotificationSetting.setSettingType(EndUserNotificationSettingType.NoTraining);
PositiveReinforcementNotification positiveReinforcement = new PositiveReinforcementNotification();
positiveReinforcement.setDeliveryPreference(NotificationDeliveryPreference.DeliverAfterCampaignEnd);
positiveReinforcement.setDefaultLanguage("en");
HashMap<String, Object> additionalData = new HashMap<String, Object>();
additionalData.put("endUserNotification@odata.bind", "https://graph.microsoft.com/v1.0/security/attacksimulation/endUserNotifications/1ewer3678-9abc-def0-123456789a");
positiveReinforcement.setAdditionalData(additionalData);
endUserNotificationSetting.setPositiveReinforcement(positiveReinforcement);
HashMap<String, Object> additionalData1 = new HashMap<String, Object>();
 simulationNotification = new ();
simulationNotification.setTargettedUserType("compromised");
simulationNotification.setEndUserNotificationOdataBind("https://graph.microsoft.com/v1.0/security/attacksimulation/endUserNotifications/12wer3678-9abc-def0-123456789a");
simulationNotification.setDefaultLanguage("en");
additionalData1.put("simulationNotification", simulationNotification);
endUserNotificationSetting.setAdditionalData(additionalData1);
simulation.setEndUserNotificationSetting(endUserNotificationSetting);
HashMap<String, Object> additionalData2 = new HashMap<String, Object>();
additionalData2.put("payload@odata.bind", "https://graph.microsoft.com/v1.0/security/attacksimulation/payloads/12345678-9abc-def0-123456789a");
additionalData2.put("loginPage@odata.bind", "https://graph.microsoft.com/v1.0/security/attacksimulation/loginPages/1w345678-9abc-def0-123456789a");
additionalData2.put("landingPage@odata.bind", "https://graph.microsoft.com/v1.0/security/attacksimulation/landingPages/1c345678-9abc-def0-123456789a");
simulation.setAdditionalData(additionalData2);
Simulation result = graphClient.security().attackSimulation().simulations().post(simulation);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const simulation = {
  displayName: 'Graph Simulation',
  'payload@odata.bind': 'https://graph.microsoft.com/v1.0/security/attacksimulation/payloads/12345678-9abc-def0-123456789a',
  'loginPage@odata.bind': 'https://graph.microsoft.com/v1.0/security/attacksimulation/loginPages/1w345678-9abc-def0-123456789a',
  'landingPage@odata.bind': 'https://graph.microsoft.com/v1.0/security/attacksimulation/landingPages/1c345678-9abc-def0-123456789a',
  createdBy: {
    email: 'john@contoso.com'
  },
  durationInDays: '3',
  attackTechnique: 'credentialHarvesting',
  status: 'scheduled',
  includedAccountTarget: {
    '@odata.type': '#microsoft.graph.addressBookAccountTargetContent',
    type: 'addressBook',
    accountTargetEmails: [
      'john@contoso.com'
    ]
  },
  trainingSetting: {
    settingType: 'noTraining'
  },
  endUserNotificationSetting: {
    notificationPreference: 'microsoft',
    settingType: 'noTraining',
    positiveReinforcement: {
      deliveryPreference: 'deliverAfterCampaignEnd',
      'endUserNotification@odata.bind': 'https://graph.microsoft.com/v1.0/security/attacksimulation/endUserNotifications/1ewer3678-9abc-def0-123456789a',
      defaultLanguage: 'en'
    },
    simulationNotification: {
      targettedUserType: 'compromised',
      'endUserNotification@odata.bind': 'https://graph.microsoft.com/v1.0/security/attacksimulation/endUserNotifications/12wer3678-9abc-def0-123456789a',
      defaultLanguage: 'en'
    }
  }
};

await client.api('/security/attackSimulation/simulations')
	.post(simulation);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\Simulation;
use Microsoft\Graph\Generated\Models\EmailIdentity;
use Microsoft\Graph\Generated\Models\SimulationAttackTechnique;
use Microsoft\Graph\Generated\Models\SimulationStatus;
use Microsoft\Graph\Generated\Models\AddressBookAccountTargetContent;
use Microsoft\Graph\Generated\Models\AccountTargetContentType;
use Microsoft\Graph\Generated\Models\TrainingSetting;
use Microsoft\Graph\Generated\Models\TrainingSettingType;
use Microsoft\Graph\Generated\Models\EndUserNotificationSetting;
use Microsoft\Graph\Generated\Models\EndUserNotificationPreference;
use Microsoft\Graph\Generated\Models\EndUserNotificationSettingType;
use Microsoft\Graph\Generated\Models\PositiveReinforcementNotification;
use Microsoft\Graph\Generated\Models\NotificationDeliveryPreference;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new Simulation();
$requestBody->setDisplayName('Graph Simulation');
$createdBy = new EmailIdentity();
$createdBy->setEmail('john@contoso.com');
$requestBody->setCreatedBy($createdBy);
$requestBody->setDurationInDays(3);
$requestBody->setAttackTechnique(new SimulationAttackTechnique('credentialHarvesting'));
$requestBody->setStatus(new SimulationStatus('scheduled'));
$includedAccountTarget = new AddressBookAccountTargetContent();
$includedAccountTarget->setOdataType('#microsoft.graph.addressBookAccountTargetContent');
$includedAccountTarget->setType(new AccountTargetContentType('addressBook'));
$includedAccountTarget->setAccountTargetEmails(['john@contoso.com', 	]);
$requestBody->setIncludedAccountTarget($includedAccountTarget);
$trainingSetting = new TrainingSetting();
$trainingSetting->setSettingType(new TrainingSettingType('noTraining'));
$requestBody->setTrainingSetting($trainingSetting);
$endUserNotificationSetting = new EndUserNotificationSetting();
$endUserNotificationSetting->setNotificationPreference(new EndUserNotificationPreference('microsoft'));
$endUserNotificationSetting->setSettingType(new EndUserNotificationSettingType('noTraining'));
$endUserNotificationSettingPositiveReinforcement = new PositiveReinforcementNotification();
$endUserNotificationSettingPositiveReinforcement->setDeliveryPreference(new NotificationDeliveryPreference('deliverAfterCampaignEnd'));
$endUserNotificationSettingPositiveReinforcement->setDefaultLanguage('en');
$additionalData = [
	'endUserNotification@odata.bind' => 'https://graph.microsoft.com/v1.0/security/attacksimulation/endUserNotifications/1ewer3678-9abc-def0-123456789a',
];
$endUserNotificationSettingPositiveReinforcement->setAdditionalData($additionalData);
$endUserNotificationSetting->setPositiveReinforcement($endUserNotificationSettingPositiveReinforcement);
$additionalData = [
	'simulationNotification' => [
		'targettedUserType' => 'compromised',
		'endUserNotification@odata.bind' => 'https://graph.microsoft.com/v1.0/security/attacksimulation/endUserNotifications/12wer3678-9abc-def0-123456789a',
		'defaultLanguage' => 'en',
	],
];
$endUserNotificationSetting->setAdditionalData($additionalData);
$requestBody->setEndUserNotificationSetting($endUserNotificationSetting);
$additionalData = [
	'payload@odata.bind' => 'https://graph.microsoft.com/v1.0/security/attacksimulation/payloads/12345678-9abc-def0-123456789a',
	'loginPage@odata.bind' => 'https://graph.microsoft.com/v1.0/security/attacksimulation/loginPages/1w345678-9abc-def0-123456789a',
	'landingPage@odata.bind' => 'https://graph.microsoft.com/v1.0/security/attacksimulation/landingPages/1c345678-9abc-def0-123456789a',
];
$requestBody->setAdditionalData($additionalData);

$result = $graphServiceClient->security()->attackSimulation()->simulations()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Security

$params = @{
	displayName = "Graph Simulation"
	"payload@odata.bind" = "https://graph.microsoft.com/v1.0/security/attacksimulation/payloads/12345678-9abc-def0-123456789a"
	"loginPage@odata.bind" = "https://graph.microsoft.com/v1.0/security/attacksimulation/loginPages/1w345678-9abc-def0-123456789a"
	"landingPage@odata.bind" = "https://graph.microsoft.com/v1.0/security/attacksimulation/landingPages/1c345678-9abc-def0-123456789a"
	createdBy = @{
		email = "john@contoso.com"
	}
	durationInDays = "3"
	attackTechnique = "credentialHarvesting"
	status = "scheduled"
	includedAccountTarget = @{
		"@odata.type" = "#microsoft.graph.addressBookAccountTargetContent"
		type = "addressBook"
		accountTargetEmails = @(
		"john@contoso.com"
	)
}
trainingSetting = @{
	settingType = "noTraining"
}
endUserNotificationSetting = @{
	notificationPreference = "microsoft"
	settingType = "noTraining"
	positiveReinforcement = @{
		deliveryPreference = "deliverAfterCampaignEnd"
		"endUserNotification@odata.bind" = "https://graph.microsoft.com/v1.0/security/attacksimulation/endUserNotifications/1ewer3678-9abc-def0-123456789a"
		defaultLanguage = "en"
	}
	simulationNotification = @{
		targettedUserType = "compromised"
		"endUserNotification@odata.bind" = "https://graph.microsoft.com/v1.0/security/attacksimulation/endUserNotifications/12wer3678-9abc-def0-123456789a"
		defaultLanguage = "en"
	}
}
}

New-MgSecurityAttackSimulation -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.simulation import Simulation
from msgraph.generated.models.email_identity import EmailIdentity
from msgraph.generated.models.simulation_attack_technique import SimulationAttackTechnique
from msgraph.generated.models.simulation_status import SimulationStatus
from msgraph.generated.models.address_book_account_target_content import AddressBookAccountTargetContent
from msgraph.generated.models.account_target_content_type import AccountTargetContentType
from msgraph.generated.models.training_setting import TrainingSetting
from msgraph.generated.models.training_setting_type import TrainingSettingType
from msgraph.generated.models.end_user_notification_setting import EndUserNotificationSetting
from msgraph.generated.models.end_user_notification_preference import EndUserNotificationPreference
from msgraph.generated.models.end_user_notification_setting_type import EndUserNotificationSettingType
from msgraph.generated.models.positive_reinforcement_notification import PositiveReinforcementNotification
from msgraph.generated.models.notification_delivery_preference import NotificationDeliveryPreference
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = Simulation(
	display_name = "Graph Simulation",
	created_by = EmailIdentity(
		email = "john@contoso.com",
	),
	duration_in_days = 3,
	attack_technique = SimulationAttackTechnique.CredentialHarvesting,
	status = SimulationStatus.Scheduled,
	included_account_target = AddressBookAccountTargetContent(
		odata_type = "#microsoft.graph.addressBookAccountTargetContent",
		type = AccountTargetContentType.AddressBook,
		account_target_emails = [
			"john@contoso.com",
		],
	),
	training_setting = TrainingSetting(
		setting_type = TrainingSettingType.NoTraining,
	),
	end_user_notification_setting = EndUserNotificationSetting(
		notification_preference = EndUserNotificationPreference.Microsoft,
		setting_type = EndUserNotificationSettingType.NoTraining,
		positive_reinforcement = PositiveReinforcementNotification(
			delivery_preference = NotificationDeliveryPreference.DeliverAfterCampaignEnd,
			default_language = "en",
			additional_data = {
					"end_user_notification@odata_bind" : "https://graph.microsoft.com/v1.0/security/attacksimulation/endUserNotifications/1ewer3678-9abc-def0-123456789a",
			}
		),
		additional_data = {
				"simulation_notification" : {
						"targetted_user_type" : "compromised",
						"end_user_notification@odata_bind" : "https://graph.microsoft.com/v1.0/security/attacksimulation/endUserNotifications/12wer3678-9abc-def0-123456789a",
						"default_language" : "en",
				},
		}
	),
	additional_data = {
			"payload@odata_bind" : "https://graph.microsoft.com/v1.0/security/attacksimulation/payloads/12345678-9abc-def0-123456789a",
			"login_page@odata_bind" : "https://graph.microsoft.com/v1.0/security/attacksimulation/loginPages/1w345678-9abc-def0-123456789a",
			"landing_page@odata_bind" : "https://graph.microsoft.com/v1.0/security/attacksimulation/landingPages/1c345678-9abc-def0-123456789a",
	}
)

result = await graph_client.security.attack_simulation.simulations.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

```http
HTTP/1.1 202 Accepted 
```
