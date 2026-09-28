<!-- Source: https://learn.microsoft.com/en-us/graph/api/security-retentionevent-post?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-04-05 -->

# Create retentionEvent

Namespace: microsoft.graph.security

Create a new [retentionEvent](https://learn.microsoft.com/en-us/graph/api/resources/security-retentionevent?view=graph-rest-1.0) object.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | RecordsManagement.ReadWrite.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | RecordsManagement.ReadWrite.All | Not available. |

## HTTP request

```http
POST /security/triggers/retentionEvents
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the [retentionEvent](https://learn.microsoft.com/en-us/graph/api/resources/security-retentionevent?view=graph-rest-1.0) object.

Specify the following properties when creating a **retentionEvent**.

| Property | Type | Description |
| :--- | :--- | :--- |
| description | String | Optional information about the event. |
| displayName | String | Name of the event. |
| eventQuery | [microsoft.graph.security.eventQuery](https://learn.microsoft.com/en-us/graph/api/resources/security-eventquery?view=graph-rest-1.0) collection | Represents the workload \(SharePoint Online, OneDrive for Business, Exchange Online\) and identification information associated with a retention event. |
| eventTriggerDateTime | DateTimeOffset | Optional time when the event should be triggered. |
| retentionEventType | String | Name of the event type associated with the event. |

## Response

If successful, this method returns a `201 Created` response code and a [microsoft.graph.security.retentionEvent](https://learn.microsoft.com/en-us/graph/api/resources/security-retentionevent?view=graph-rest-1.0) object in the response body.

## Examples

### Request

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [PowerShell](#tabpanel_1_powershell)
- [Python](#tabpanel_1_python)

```http
POST https://graph.microsoft.com/v1.0/security/triggers/retentionEvents
Content-Type: application/json
Content-length: 616

{
  "@odata.type": "#microsoft.graph.security.retentionEvent",
  "displayName": "String",
  "description": "String",
  "eventQuery": [
    {
      "@odata.type": "microsoft.graph.security.eventQuery"
    }
  ],
  "eventTriggerDateTime": "String (timestamp)",
  "retentionEventType@odata.bind": "https://graph.microsoft.com/v1.0/security/triggerTypes/retentionEventType/9eecef97-fb3c-4c68-825b-4dd74530863a"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models.Security;
using Microsoft.Kiota.Abstractions.Serialization;

var requestBody = new RetentionEvent
{
	OdataType = "#microsoft.graph.security.retentionEvent",
	DisplayName = "String",
	Description = "String",
	EventTriggerDateTime = DateTimeOffset.Parse("String (timestamp)"),
	AdditionalData = new Dictionary<string, object>
	{
		{
			"eventQuery" , new List<object>
			{
				new UntypedObject(new Dictionary<string, UntypedNode>
				{
					{
						"@odata.type", new UntypedString("microsoft.graph.security.eventQuery")
					},
				}),
			}
		},
		{
			"retentionEventType@odata.bind" , "https://graph.microsoft.com/v1.0/security/triggerTypes/retentionEventType/9eecef97-fb3c-4c68-825b-4dd74530863a"
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Security.Triggers.RetentionEvents.PostAsync(requestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.models.security.RetentionEvent retentionEvent = new com.microsoft.graph.models.security.RetentionEvent();
retentionEvent.setOdataType("#microsoft.graph.security.retentionEvent");
retentionEvent.setDisplayName("String");
retentionEvent.setDescription("String");
OffsetDateTime eventTriggerDateTime = OffsetDateTime.parse("String (timestamp)");
retentionEvent.setEventTriggerDateTime(eventTriggerDateTime);
HashMap<String, Object> additionalData = new HashMap<String, Object>();
LinkedList<Object> eventQuery = new LinkedList<Object>();
 property = new ();
property.setOdataType("microsoft.graph.security.eventQuery");
eventQuery.add(property);
additionalData.put("eventQuery", eventQuery);
additionalData.put("retentionEventType@odata.bind", "https://graph.microsoft.com/v1.0/security/triggerTypes/retentionEventType/9eecef97-fb3c-4c68-825b-4dd74530863a");
retentionEvent.setAdditionalData(additionalData);
com.microsoft.graph.models.security.RetentionEvent result = graphClient.security().triggers().retentionEvents().post(retentionEvent);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const retentionEvent = {
  '@odata.type': '#microsoft.graph.security.retentionEvent',
  displayName: 'String',
  description: 'String',
  eventQuery: [
    {
      '@odata.type': 'microsoft.graph.security.eventQuery'
    }
  ],
  eventTriggerDateTime: 'String (timestamp)',
  'retentionEventType@odata.bind': 'https://graph.microsoft.com/v1.0/security/triggerTypes/retentionEventType/9eecef97-fb3c-4c68-825b-4dd74530863a'
};

await client.api('/security/triggers/retentionEvents')
	.post(retentionEvent);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\Security\RetentionEvent;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new RetentionEvent();
$requestBody->setOdataType('#microsoft.graph.security.retentionEvent');
$requestBody->setDisplayName('String');
$requestBody->setDescription('String');
$requestBody->setEventTriggerDateTime(new \DateTime('String (timestamp)'));
$additionalData = [
	'eventQuery' => [
			[
				'@odata.type' => 'microsoft.graph.security.eventQuery',
			],
		],
	'retentionEventType@odata.bind' => 'https://graph.microsoft.com/v1.0/security/triggerTypes/retentionEventType/9eecef97-fb3c-4c68-825b-4dd74530863a',
];
$requestBody->setAdditionalData($additionalData);

$result = $graphServiceClient->security()->triggers()->retentionEvents()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Security

$params = @{
	"@odata.type" = "#microsoft.graph.security.retentionEvent"
	displayName = "String"
	description = "String"
	eventQuery = @(
		@{
			"@odata.type" = "microsoft.graph.security.eventQuery"
		}
	)
	eventTriggerDateTime = [System.DateTime]::Parse("String (timestamp)")
	"retentionEventType@odata.bind" = "https://graph.microsoft.com/v1.0/security/triggerTypes/retentionEventType/9eecef97-fb3c-4c68-825b-4dd74530863a"
}

New-MgSecurityTriggerRetentionEvent -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.security.retention_event import RetentionEvent
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = RetentionEvent(
	odata_type = "#microsoft.graph.security.retentionEvent",
	display_name = "String",
	description = "String",
	event_trigger_date_time = "String (timestamp)",
	additional_data = {
			"event_query" : [
				{
						"@odata_type" : "microsoft.graph.security.eventQuery",
				},
			],
			"retention_event_type@odata_bind" : "https://graph.microsoft.com/v1.0/security/triggerTypes/retentionEventType/9eecef97-fb3c-4c68-825b-4dd74530863a",
	}
)

result = await graph_client.security.triggers.retention_events.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.security.retentionEvent",
  "id": "fcdbfb58-d0c6-85dd-d011-4e0ff9a6805d",
  "displayName": "String",
  "description": "String",
  "eventQuery": [
    {
      "@odata.type": "microsoft.graph.security.eventQuery"
    }
  ],
  "eventTriggerDateTime": "String (timestamp)",
  "createdBy": {
    "@odata.type": "microsoft.graph.identitySet"
  },
  "createdDateTime": "String (timestamp)",
  "lastModifiedBy": {
    "@odata.type": "microsoft.graph.identitySet"
  },
  "lastModifiedDateTime": "String (timestamp)",
  "eventPropagationResults": [
    {
      "@odata.type": "microsoft.graph.security.eventPropagationResult"
    }
  ],
  "eventStatus": {
    "@odata.type": "microsoft.graph.security.retentionEventStatus"
  },
  "lastStatusUpdateDateTime": "String (timestamp)"
}
```
