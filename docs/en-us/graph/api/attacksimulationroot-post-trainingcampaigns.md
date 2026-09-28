<!-- Source: https://learn.microsoft.com/en-us/graph/api/attacksimulationroot-post-trainingcampaigns?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-06-10 -->

# Create trainingCampaign

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Create a new [trainingCampaign](https://learn.microsoft.com/en-us/graph/api/resources/trainingcampaign?view=graph-rest-beta) object.

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
POST /security/attackSimulation/trainingCampaigns
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the [trainingCampaign](https://learn.microsoft.com/en-us/graph/api/resources/trainingcampaign?view=graph-rest-beta) object.

You can specify the following properties when creating a **trainingCampaign**.

| Property | Type | Description |
| :--- | :--- | :--- |
| createdBy | [emailIdentity](https://learn.microsoft.com/en-us/graph/api/resources/emailidentity?view=graph-rest-beta) | The identity of the user who created the training campaign. Optional. |
| createdDateTime | DateTimeOffset | The date and time when the training campaign was created. Optional. |
| description | String | The description of the training campaign. Optional. |
| displayName | String | The display name of the training campaign. Required. |
| endUserNotificationSetting | [endUserNotificationSetting](https://learn.microsoft.com/en-us/graph/api/resources/endusernotificationsetting?view=graph-rest-beta) | Details about the end user notification setting. Required. |
| excludedAccountTarget | [accountTargetContent](https://learn.microsoft.com/en-us/graph/api/resources/accounttargetcontent?view=graph-rest-beta) | The users who are excluded from the training campaign. Optional. |
| includedAccountTarget | [accountTargetContent](https://learn.microsoft.com/en-us/graph/api/resources/accounttargetcontent?view=graph-rest-beta) | The users who are targeted in the training campaign. Required. |
| lastModifiedDateTime | DateTimeOffset | The identity of the user who most recently modified the training campaign. Optional. |
| trainingSetting | [trainingSetting](https://learn.microsoft.com/en-us/graph/api/resources/trainingsetting?view=graph-rest-beta) | Details about the training settings for a training campaign. Required. |
| campaignSchedule | [campaignSchedule](https://learn.microsoft.com/en-us/graph/api/resources/campaignschedule?view=graph-rest-beta) | Details about the schedule and current status for a training campaign. Required. |

## Response

If successful, this method returns a `202 Accepted` response code and a tracking header named `location` in the response.

## Examples

### Request

The following example shows a request.

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [PowerShell](#tabpanel_1_powershell)
- [Python](#tabpanel_1_python)

```http
POST https://graph.microsoft.com/beta/security/attackSimulation/trainingCampaigns
Content-Type: application/json

{
    "displayName": "Graph Training Campaign",
    "description": "Graph Training Campaign Description",
    "createdBy": {
        "email": "john@contoso.com"
    },
    "lastModifiedBy": {
        "email": "john@contoso.com"
    },
    "includedAccountTarget": {
        "type": "addressBook",
        "accountTargetEmails": [
            "john@contoso.com"
        ]
    },
    "endUserNotificationSetting": {
        "notificationPreference": "microsoft",
        "settingType": "trainingSelected",
        "trainingReminder": {
            "deliveryFrequency": "weekly",
            "endUserNotification@odata.bind": "https://graph.microsoft.com/beta/security/attackSimulation/endUserNotifications('fe521249-9901-4584-a987-026a9980c58e')",
            "defaultLanguage": "en"
        },
        "trainingAssignment": {
            "endUserNotification@odata.bind": "https://graph.microsoft.com/beta/security/attackSimulation/endUserNotifications('36fb4dc1-7c37-4b96-9096-12e6d6014fae')",
            "defaultLanguage": "en"
        }
    },
    "trainingSetting": {
        "settingType": "microsoftCustom",
        "trainingAssignmentMappings": [
            {
                "assignedTo": [
                    "allUsers"
                ],
                "training@odata.bind": "https://graph.microsoft.com/beta/security/attackSimulation/trainings('40454905-dc26-4f36-b854-3042a5362cb3')"
            },
            {
                "assignedTo": [
                    "allUsers"
                ],
                "training@odata.bind": "https://graph.microsoft.com/beta/security/attackSimulation/trainings('ea70ae06-3859-4818-be9d-270ee81d80a4')"
            },
            {
                "assignedTo": [
                    "allUsers"
                ],
                "training@odata.bind": "https://graph.microsoft.com/beta/security/attackSimulation/trainings('d733d88c-1b5a-48e3-a588-9910e41ac21d')"
            }
        ]
    },
    "campaignSchedule": {
        "launchDateTime": "2024-02-15T07:59:44Z",
        "completionDateTime": "2024-02-18T07:59:44Z",
        "status": "Scheduled"
    }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.Models;
using Microsoft.Kiota.Abstractions.Serialization;

var requestBody = new TrainingCampaign
{
	DisplayName = "Graph Training Campaign",
	Description = "Graph Training Campaign Description",
	CreatedBy = new EmailIdentity
	{
		Email = "john@contoso.com",
	},
	LastModifiedBy = new EmailIdentity
	{
		Email = "john@contoso.com",
	},
	IncludedAccountTarget = new AccountTargetContent
	{
		Type = AccountTargetContentType.AddressBook,
		AdditionalData = new Dictionary<string, object>
		{
			{
				"accountTargetEmails" , new List<string>
				{
					"john@contoso.com",
				}
			},
		},
	},
	EndUserNotificationSetting = new EndUserNotificationSetting
	{
		NotificationPreference = EndUserNotificationPreference.Microsoft,
		SettingType = EndUserNotificationSettingType.TrainingSelected,
		AdditionalData = new Dictionary<string, object>
		{
			{
				"trainingReminder" , new UntypedObject(new Dictionary<string, UntypedNode>
				{
					{
						"deliveryFrequency", new UntypedString("weekly")
					},
					{
						"endUserNotification@odata.bind", new UntypedString("https://graph.microsoft.com/beta/security/attackSimulation/endUserNotifications('fe521249-9901-4584-a987-026a9980c58e')")
					},
					{
						"defaultLanguage", new UntypedString("en")
					},
				})
			},
			{
				"trainingAssignment" , new UntypedObject(new Dictionary<string, UntypedNode>
				{
					{
						"endUserNotification@odata.bind", new UntypedString("https://graph.microsoft.com/beta/security/attackSimulation/endUserNotifications('36fb4dc1-7c37-4b96-9096-12e6d6014fae')")
					},
					{
						"defaultLanguage", new UntypedString("en")
					},
				})
			},
		},
	},
	TrainingSetting = new TrainingSetting
	{
		SettingType = TrainingSettingType.MicrosoftCustom,
		AdditionalData = new Dictionary<string, object>
		{
			{
				"trainingAssignmentMappings" , new List<object>
				{
					new UntypedObject(new Dictionary<string, UntypedNode>
					{
						{
							"assignedTo", new UntypedArray(new List<UntypedNode>
							{
								new UntypedString("allUsers"),
							})
						},
						{
							"training@odata.bind", new UntypedString("https://graph.microsoft.com/beta/security/attackSimulation/trainings('40454905-dc26-4f36-b854-3042a5362cb3')")
						},
					}),
					new UntypedObject(new Dictionary<string, UntypedNode>
					{
						{
							"assignedTo", new UntypedArray(new List<UntypedNode>
							{
								new UntypedString("allUsers"),
							})
						},
						{
							"training@odata.bind", new UntypedString("https://graph.microsoft.com/beta/security/attackSimulation/trainings('ea70ae06-3859-4818-be9d-270ee81d80a4')")
						},
					}),
					new UntypedObject(new Dictionary<string, UntypedNode>
					{
						{
							"assignedTo", new UntypedArray(new List<UntypedNode>
							{
								new UntypedString("allUsers"),
							})
						},
						{
							"training@odata.bind", new UntypedString("https://graph.microsoft.com/beta/security/attackSimulation/trainings('d733d88c-1b5a-48e3-a588-9910e41ac21d')")
						},
					}),
				}
			},
		},
	},
	CampaignSchedule = new CampaignSchedule
	{
		LaunchDateTime = DateTimeOffset.Parse("2024-02-15T07:59:44Z"),
		CompletionDateTime = DateTimeOffset.Parse("2024-02-18T07:59:44Z"),
		Status = CampaignStatus.Scheduled,
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Security.AttackSimulation.TrainingCampaigns.PostAsync(requestBody);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

TrainingCampaign trainingCampaign = new TrainingCampaign();
trainingCampaign.setDisplayName("Graph Training Campaign");
trainingCampaign.setDescription("Graph Training Campaign Description");
EmailIdentity createdBy = new EmailIdentity();
createdBy.setEmail("john@contoso.com");
trainingCampaign.setCreatedBy(createdBy);
EmailIdentity lastModifiedBy = new EmailIdentity();
lastModifiedBy.setEmail("john@contoso.com");
trainingCampaign.setLastModifiedBy(lastModifiedBy);
AccountTargetContent includedAccountTarget = new AccountTargetContent();
includedAccountTarget.setType(AccountTargetContentType.AddressBook);
HashMap<String, Object> additionalData = new HashMap<String, Object>();
LinkedList<String> accountTargetEmails = new LinkedList<String>();
accountTargetEmails.add("john@contoso.com");
additionalData.put("accountTargetEmails", accountTargetEmails);
includedAccountTarget.setAdditionalData(additionalData);
trainingCampaign.setIncludedAccountTarget(includedAccountTarget);
EndUserNotificationSetting endUserNotificationSetting = new EndUserNotificationSetting();
endUserNotificationSetting.setNotificationPreference(EndUserNotificationPreference.Microsoft);
endUserNotificationSetting.setSettingType(EndUserNotificationSettingType.TrainingSelected);
HashMap<String, Object> additionalData1 = new HashMap<String, Object>();
 trainingReminder = new ();
trainingReminder.setDeliveryFrequency("weekly");
trainingReminder.setEndUserNotificationOdataBind("https://graph.microsoft.com/beta/security/attackSimulation/endUserNotifications('fe521249-9901-4584-a987-026a9980c58e')");
trainingReminder.setDefaultLanguage("en");
additionalData1.put("trainingReminder", trainingReminder);
 trainingAssignment = new ();
trainingAssignment.setEndUserNotificationOdataBind("https://graph.microsoft.com/beta/security/attackSimulation/endUserNotifications('36fb4dc1-7c37-4b96-9096-12e6d6014fae')");
trainingAssignment.setDefaultLanguage("en");
additionalData1.put("trainingAssignment", trainingAssignment);
endUserNotificationSetting.setAdditionalData(additionalData1);
trainingCampaign.setEndUserNotificationSetting(endUserNotificationSetting);
TrainingSetting trainingSetting = new TrainingSetting();
trainingSetting.setSettingType(TrainingSettingType.MicrosoftCustom);
HashMap<String, Object> additionalData2 = new HashMap<String, Object>();
LinkedList<Object> trainingAssignmentMappings = new LinkedList<Object>();
 property1 = new ();
LinkedList<String> assignedTo = new LinkedList<String>();
assignedTo.add("allUsers");
property1.setAssignedTo(assignedTo);
property1.setTrainingOdataBind("https://graph.microsoft.com/beta/security/attackSimulation/trainings('40454905-dc26-4f36-b854-3042a5362cb3')");
trainingAssignmentMappings.add(property1);
 property3 = new ();
LinkedList<String> assignedTo1 = new LinkedList<String>();
assignedTo1.add("allUsers");
property3.setAssignedTo(assignedTo1);
property3.setTrainingOdataBind("https://graph.microsoft.com/beta/security/attackSimulation/trainings('ea70ae06-3859-4818-be9d-270ee81d80a4')");
trainingAssignmentMappings.add(property3);
 property5 = new ();
LinkedList<String> assignedTo2 = new LinkedList<String>();
assignedTo2.add("allUsers");
property5.setAssignedTo(assignedTo2);
property5.setTrainingOdataBind("https://graph.microsoft.com/beta/security/attackSimulation/trainings('d733d88c-1b5a-48e3-a588-9910e41ac21d')");
trainingAssignmentMappings.add(property5);
additionalData2.put("trainingAssignmentMappings", trainingAssignmentMappings);
trainingSetting.setAdditionalData(additionalData2);
trainingCampaign.setTrainingSetting(trainingSetting);
CampaignSchedule campaignSchedule = new CampaignSchedule();
OffsetDateTime launchDateTime = OffsetDateTime.parse("2024-02-15T07:59:44Z");
campaignSchedule.setLaunchDateTime(launchDateTime);
OffsetDateTime completionDateTime = OffsetDateTime.parse("2024-02-18T07:59:44Z");
campaignSchedule.setCompletionDateTime(completionDateTime);
campaignSchedule.setStatus(CampaignStatus.Scheduled);
trainingCampaign.setCampaignSchedule(campaignSchedule);
TrainingCampaign result = graphClient.security().attackSimulation().trainingCampaigns().post(trainingCampaign);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const trainingCampaign = {
    displayName: 'Graph Training Campaign',
    description: 'Graph Training Campaign Description',
    createdBy: {
        email: 'john@contoso.com'
    },
    lastModifiedBy: {
        email: 'john@contoso.com'
    },
    includedAccountTarget: {
        type: 'addressBook',
        accountTargetEmails: [
            'john@contoso.com'
        ]
    },
    endUserNotificationSetting: {
        notificationPreference: 'microsoft',
        settingType: 'trainingSelected',
        trainingReminder: {
            deliveryFrequency: 'weekly',
            'endUserNotification@odata.bind': 'https://graph.microsoft.com/beta/security/attackSimulation/endUserNotifications(\'fe521249-9901-4584-a987-026a9980c58e\')',
            defaultLanguage: 'en'
        },
        trainingAssignment: {
            'endUserNotification@odata.bind': 'https://graph.microsoft.com/beta/security/attackSimulation/endUserNotifications(\'36fb4dc1-7c37-4b96-9096-12e6d6014fae\')',
            defaultLanguage: 'en'
        }
    },
    trainingSetting: {
        settingType: 'microsoftCustom',
        trainingAssignmentMappings: [
            {
                assignedTo: [
                    'allUsers'
                ],
                'training@odata.bind': 'https://graph.microsoft.com/beta/security/attackSimulation/trainings(\'40454905-dc26-4f36-b854-3042a5362cb3\')'
            },
            {
                assignedTo: [
                    'allUsers'
                ],
                'training@odata.bind': 'https://graph.microsoft.com/beta/security/attackSimulation/trainings(\'ea70ae06-3859-4818-be9d-270ee81d80a4\')'
            },
            {
                assignedTo: [
                    'allUsers'
                ],
                'training@odata.bind': 'https://graph.microsoft.com/beta/security/attackSimulation/trainings(\'d733d88c-1b5a-48e3-a588-9910e41ac21d\')'
            }
        ]
    },
    campaignSchedule: {
        launchDateTime: '2024-02-15T07:59:44Z',
        completionDateTime: '2024-02-18T07:59:44Z',
        status: 'Scheduled'
    }
};

await client.api('/security/attackSimulation/trainingCampaigns')
	.version('beta')
	.post(trainingCampaign);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Models\TrainingCampaign;
use Microsoft\Graph\Beta\Generated\Models\EmailIdentity;
use Microsoft\Graph\Beta\Generated\Models\AccountTargetContent;
use Microsoft\Graph\Beta\Generated\Models\AccountTargetContentType;
use Microsoft\Graph\Beta\Generated\Models\EndUserNotificationSetting;
use Microsoft\Graph\Beta\Generated\Models\EndUserNotificationPreference;
use Microsoft\Graph\Beta\Generated\Models\EndUserNotificationSettingType;
use Microsoft\Graph\Beta\Generated\Models\TrainingSetting;
use Microsoft\Graph\Beta\Generated\Models\TrainingSettingType;
use Microsoft\Graph\Beta\Generated\Models\CampaignSchedule;
use Microsoft\Graph\Beta\Generated\Models\CampaignStatus;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new TrainingCampaign();
$requestBody->setDisplayName('Graph Training Campaign');
$requestBody->setDescription('Graph Training Campaign Description');
$createdBy = new EmailIdentity();
$createdBy->setEmail('john@contoso.com');
$requestBody->setCreatedBy($createdBy);
$lastModifiedBy = new EmailIdentity();
$lastModifiedBy->setEmail('john@contoso.com');
$requestBody->setLastModifiedBy($lastModifiedBy);
$includedAccountTarget = new AccountTargetContent();
$includedAccountTarget->setType(new AccountTargetContentType('addressBook'));
$additionalData = [
	'accountTargetEmails' => [
'john@contoso.com', ],
];
$includedAccountTarget->setAdditionalData($additionalData);
$requestBody->setIncludedAccountTarget($includedAccountTarget);
$endUserNotificationSetting = new EndUserNotificationSetting();
$endUserNotificationSetting->setNotificationPreference(new EndUserNotificationPreference('microsoft'));
$endUserNotificationSetting->setSettingType(new EndUserNotificationSettingType('trainingSelected'));
$additionalData = [
	'trainingReminder' => [
		'deliveryFrequency' => 'weekly',
		'endUserNotification@odata.bind' => 'https://graph.microsoft.com/beta/security/attackSimulation/endUserNotifications(\'fe521249-9901-4584-a987-026a9980c58e\')',
		'defaultLanguage' => 'en',
	],
	'trainingAssignment' => [
		'endUserNotification@odata.bind' => 'https://graph.microsoft.com/beta/security/attackSimulation/endUserNotifications(\'36fb4dc1-7c37-4b96-9096-12e6d6014fae\')',
		'defaultLanguage' => 'en',
	],
];
$endUserNotificationSetting->setAdditionalData($additionalData);
$requestBody->setEndUserNotificationSetting($endUserNotificationSetting);
$trainingSetting = new TrainingSetting();
$trainingSetting->setSettingType(new TrainingSettingType('microsoftCustom'));
$additionalData = [
	'trainingAssignmentMappings' => [
			[
				'assignedTo' => [
'allUsers', ],
				'training@odata.bind' => 'https://graph.microsoft.com/beta/security/attackSimulation/trainings(\'40454905-dc26-4f36-b854-3042a5362cb3\')',
			],
			[
				'assignedTo' => [
'allUsers', ],
				'training@odata.bind' => 'https://graph.microsoft.com/beta/security/attackSimulation/trainings(\'ea70ae06-3859-4818-be9d-270ee81d80a4\')',
			],
			[
				'assignedTo' => [
'allUsers', ],
				'training@odata.bind' => 'https://graph.microsoft.com/beta/security/attackSimulation/trainings(\'d733d88c-1b5a-48e3-a588-9910e41ac21d\')',
			],
		],
];
$trainingSetting->setAdditionalData($additionalData);
$requestBody->setTrainingSetting($trainingSetting);
$campaignSchedule = new CampaignSchedule();
$campaignSchedule->setLaunchDateTime(new \DateTime('2024-02-15T07:59:44Z'));
$campaignSchedule->setCompletionDateTime(new \DateTime('2024-02-18T07:59:44Z'));
$campaignSchedule->setStatus(new CampaignStatus('scheduled'));
$requestBody->setCampaignSchedule($campaignSchedule);

$result = $graphServiceClient->security()->attackSimulation()->trainingCampaigns()->post($requestBody)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Beta.Security

$params = @{
	displayName = "Graph Training Campaign"
	description = "Graph Training Campaign Description"
	createdBy = @{
		email = "john@contoso.com"
	}
	lastModifiedBy = @{
		email = "john@contoso.com"
	}
	includedAccountTarget = @{
		type = "addressBook"
		accountTargetEmails = @(
		"john@contoso.com"
	)
}
endUserNotificationSetting = @{
	notificationPreference = "microsoft"
	settingType = "trainingSelected"
	trainingReminder = @{
		deliveryFrequency = "weekly"
		"endUserNotification@odata.bind" = "https://graph.microsoft.com/beta/security/attackSimulation/endUserNotifications('fe521249-9901-4584-a987-026a9980c58e')"
		defaultLanguage = "en"
	}
	trainingAssignment = @{
		"endUserNotification@odata.bind" = "https://graph.microsoft.com/beta/security/attackSimulation/endUserNotifications('36fb4dc1-7c37-4b96-9096-12e6d6014fae')"
		defaultLanguage = "en"
	}
}
trainingSetting = @{
	settingType = "microsoftCustom"
	trainingAssignmentMappings = @(
		@{
			assignedTo = @(
			"allUsers"
		)
		"training@odata.bind" = "https://graph.microsoft.com/beta/security/attackSimulation/trainings('40454905-dc26-4f36-b854-3042a5362cb3')"
	}
	@{
		assignedTo = @(
		"allUsers"
	)
	"training@odata.bind" = "https://graph.microsoft.com/beta/security/attackSimulation/trainings('ea70ae06-3859-4818-be9d-270ee81d80a4')"
}
@{
	assignedTo = @(
	"allUsers"
)
"training@odata.bind" = "https://graph.microsoft.com/beta/security/attackSimulation/trainings('d733d88c-1b5a-48e3-a588-9910e41ac21d')"
}
)
}
campaignSchedule = @{
launchDateTime = [System.DateTime]::Parse("2024-02-15T07:59:44Z")
completionDateTime = [System.DateTime]::Parse("2024-02-18T07:59:44Z")
status = "Scheduled"
}
}

New-MgBetaSecurityAttackSimulationTrainingCampaign -BodyParameter $params
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.models.training_campaign import TrainingCampaign
from msgraph_beta.generated.models.email_identity import EmailIdentity
from msgraph_beta.generated.models.account_target_content import AccountTargetContent
from msgraph_beta.generated.models.account_target_content_type import AccountTargetContentType
from msgraph_beta.generated.models.end_user_notification_setting import EndUserNotificationSetting
from msgraph_beta.generated.models.end_user_notification_preference import EndUserNotificationPreference
from msgraph_beta.generated.models.end_user_notification_setting_type import EndUserNotificationSettingType
from msgraph_beta.generated.models.training_setting import TrainingSetting
from msgraph_beta.generated.models.training_setting_type import TrainingSettingType
from msgraph_beta.generated.models.campaign_schedule import CampaignSchedule
from msgraph_beta.generated.models.campaign_status import CampaignStatus
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = TrainingCampaign(
	display_name = "Graph Training Campaign",
	description = "Graph Training Campaign Description",
	created_by = EmailIdentity(
		email = "john@contoso.com",
	),
	last_modified_by = EmailIdentity(
		email = "john@contoso.com",
	),
	included_account_target = AccountTargetContent(
		type = AccountTargetContentType.AddressBook,
		additional_data = {
				"account_target_emails" : [
					"john@contoso.com",
				],
		}
	),
	end_user_notification_setting = EndUserNotificationSetting(
		notification_preference = EndUserNotificationPreference.Microsoft,
		setting_type = EndUserNotificationSettingType.TrainingSelected,
		additional_data = {
				"training_reminder" : {
						"delivery_frequency" : "weekly",
						"end_user_notification@odata_bind" : "https://graph.microsoft.com/beta/security/attackSimulation/endUserNotifications('fe521249-9901-4584-a987-026a9980c58e')",
						"default_language" : "en",
				},
				"training_assignment" : {
						"end_user_notification@odata_bind" : "https://graph.microsoft.com/beta/security/attackSimulation/endUserNotifications('36fb4dc1-7c37-4b96-9096-12e6d6014fae')",
						"default_language" : "en",
				},
		}
	),
	training_setting = TrainingSetting(
		setting_type = TrainingSettingType.MicrosoftCustom,
		additional_data = {
				"training_assignment_mappings" : [
					{
							"assigned_to" : [
								"allUsers",
							],
							"training@odata_bind" : "https://graph.microsoft.com/beta/security/attackSimulation/trainings('40454905-dc26-4f36-b854-3042a5362cb3')",
					},
					{
							"assigned_to" : [
								"allUsers",
							],
							"training@odata_bind" : "https://graph.microsoft.com/beta/security/attackSimulation/trainings('ea70ae06-3859-4818-be9d-270ee81d80a4')",
					},
					{
							"assigned_to" : [
								"allUsers",
							],
							"training@odata_bind" : "https://graph.microsoft.com/beta/security/attackSimulation/trainings('d733d88c-1b5a-48e3-a588-9910e41ac21d')",
					},
				],
		}
	),
	campaign_schedule = CampaignSchedule(
		launch_date_time = "2024-02-15T07:59:44Z",
		completion_date_time = "2024-02-18T07:59:44Z",
		status = CampaignStatus.Scheduled,
	),
)

result = await graph_client.security.attack_simulation.training_campaigns.post(request_body)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

```http
HTTP/1.1 202 Accepted 
```
