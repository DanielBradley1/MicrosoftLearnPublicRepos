<!-- Source: https://learn.microsoft.com/en-us/graph/api/activitiescontainer-post-contentactivities?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-23 -->

# Create contentActivity

Namespace: microsoft.graph

Create a [content activity](https://learn.microsoft.com/en-us/graph/api/resources/contentactivity?view=graph-rest-1.0) for the signed-in user.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | ContentActivity.Write | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | ContentActivity.Write | Not available. |

## HTTP request

```http
POST /me/dataSecurityAndGovernance/activities/contentActivities
```

Note

Calling the `/me` endpoint requires a signed-in user and therefore a delegated permission. Application permissions aren't supported when using the `/me` endpoint.

```http
POST /users/{userId}/dataSecurityAndGovernance/activities/contentActivities
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the [contentActivity](https://learn.microsoft.com/en-us/graph/api/resources/contentactivity?view=graph-rest-1.0) object.

## Response

If successful, this method returns a `201 Created` response code and a [contentActivity](https://learn.microsoft.com/en-us/graph/api/resources/contentactivity?view=graph-rest-1.0) object in the response body.

## Examples

### Request

The following example shows a request.

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [Python](#tabpanel_1_python)

```http
POST https://graph.microsoft.com/v1.0/me/dataSecurityAndGovernance/activities/contentActivities
Content-Type: application/json

{
    "contentToProcess": {
       "contentEntries": [
          {
             "@odata.type": "microsoft.graph.processConversationMetadata",
             "identifier": "07785517-9081-4fe7-a9dc-85bcdf5e9075",
             "name":"PC Purview API Explorer message",
             "correlationId": "d63eafd2-e3a9-4c1a-b726-a2e9b9d9580d",
             "sequenceNumber": 0, 
             "isTruncated": false,
             "createdDateTime": "2025-05-27T17:23:20",
             "modifiedDateTime": "2025-05-27T17:23:20"
          }
       ],
       "activityMetadata": { 
          "activity": "uploadText"
       },
       "deviceMetadata": {
          "operatingSystemSpecifications": {
             "operatingSystemPlatform": "Windows 11",
             "operatingSystemVersion": "10.0.26100.0" 
          },
          "ipAddress": "127.0.0.1"
       },
       "protectedAppMetadata": {
          "name": "PC Purview API Explorer",
          "version": "0.2",
          "applicationLocation":{
             "@odata.type": "microsoft.graph.policyLocationApplication",
             "value": "83ef208a-0396-4893-9d4f-d36efbffc8bd"
          }
       },
       "integratedAppMetadata": {
          "name": "PC Purview API Explorer",
          "version": "0.2" 
       }
    }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;
using Microsoft.Kiota.Abstractions.Serialization;

var requestBody = new ContentActivity
{
	AdditionalData = new Dictionary<string, object>
	{
		{
			"contentToProcess" , new UntypedObject(new Dictionary<string, UntypedNode>
			{
				{
					"contentEntries", new UntypedArray(new List<UntypedNode>
					{
						new UntypedObject(new Dictionary<string, UntypedNode>
						{
							{
								"@odata.type", new UntypedString("microsoft.graph.processConversationMetadata")
							},
							{
								"identifier", new UntypedString("07785517-9081-4fe7-a9dc-85bcdf5e9075")
							},
							{
								"name", new UntypedString("PC Purview API Explorer message")
							},
							{
								"correlationId", new UntypedString("d63eafd2-e3a9-4c1a-b726-a2e9b9d9580d")
							},
							{
								"sequenceNumber", new UntypedString("0")
							},
							{
								"isTruncated", new UntypedBoolean(false)
							},
							{
								"createdDateTime", new UntypedString("2025-05-27T17:23:20")
							},
							{
								"modifiedDateTime", new UntypedString("2025-05-27T17:23:20")
							},
						}),
					})
				},
				{
					"activityMetadata", new UntypedObject(new Dictionary<string, UntypedNode>
					{
						{
							"activity", new UntypedString("uploadText")
						},
					})
				},
				{
					"deviceMetadata", new UntypedObject(new Dictionary<string, UntypedNode>
					{
						{
							"operatingSystemSpecifications", new UntypedObject(new Dictionary<string, UntypedNode>
							{
								{
									"operatingSystemPlatform", new UntypedString("Windows 11")
								},
								{
									"operatingSystemVersion", new UntypedString("10.0.26100.0")
								},
							})
						},
						{
							"ipAddress", new UntypedString("127.0.0.1")
						},
					})
				},
				{
					"protectedAppMetadata", new UntypedObject(new Dictionary<string, UntypedNode>
					{
						{
							"name", new UntypedString("PC Purview API Explorer")
						},
						{
							"version", new UntypedString("0.2")
						},
						{
							"applicationLocation", new UntypedObject(new Dictionary<string, UntypedNode>
							{
								{
									"@odata.type", new UntypedString("microsoft.graph.policyLocationApplication")
								},
								{
									"value", new UntypedString("83ef208a-0396-4893-9d4f-d36efbffc8bd")
								},
							})
						},
					})
				},
				{
					"integratedAppMetadata", new UntypedObject(new Dictionary<string, UntypedNode>
					{
						{
							"name", new UntypedString("PC Purview API Explorer")
						},
						{
							"version", new UntypedString("0.2")
						},
					})
				},
			})
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Me.DataSecurityAndGovernance.Activities.ContentActivities.PostAsync(requestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

ContentActivity contentActivity = new ContentActivity();
HashMap<String, Object> additionalData = new HashMap<String, Object>();
 contentToProcess = new ();
LinkedList<Object> contentEntries = new LinkedList<Object>();
 property = new ();
property.setOdataType("microsoft.graph.processConversationMetadata");
property.setIdentifier("07785517-9081-4fe7-a9dc-85bcdf5e9075");
property.setName("PC Purview API Explorer message");
property.setCorrelationId("d63eafd2-e3a9-4c1a-b726-a2e9b9d9580d");
property.setSequenceNumber(0);
property.setIsTruncated(false);
property.setCreatedDateTime("2025-05-27T17:23:20");
property.setModifiedDateTime("2025-05-27T17:23:20");
contentEntries.add(property);
contentToProcess.setContentEntries(contentEntries);
 activityMetadata = new ();
activityMetadata.setActivity("uploadText");
contentToProcess.setActivityMetadata(activityMetadata);
 deviceMetadata = new ();
 operatingSystemSpecifications = new ();
operatingSystemSpecifications.setOperatingSystemPlatform("Windows 11");
operatingSystemSpecifications.setOperatingSystemVersion("10.0.26100.0");
deviceMetadata.setOperatingSystemSpecifications(operatingSystemSpecifications);
deviceMetadata.setIpAddress("127.0.0.1");
contentToProcess.setDeviceMetadata(deviceMetadata);
 protectedAppMetadata = new ();
protectedAppMetadata.setName("PC Purview API Explorer");
protectedAppMetadata.setVersion("0.2");
 applicationLocation = new ();
applicationLocation.setOdataType("microsoft.graph.policyLocationApplication");
applicationLocation.setValue("83ef208a-0396-4893-9d4f-d36efbffc8bd");
protectedAppMetadata.setApplicationLocation(applicationLocation);
contentToProcess.setProtectedAppMetadata(protectedAppMetadata);
 integratedAppMetadata = new ();
integratedAppMetadata.setName("PC Purview API Explorer");
integratedAppMetadata.setVersion("0.2");
contentToProcess.setIntegratedAppMetadata(integratedAppMetadata);
additionalData.put("contentToProcess", contentToProcess);
contentActivity.setAdditionalData(additionalData);
ContentActivity result = graphClient.me().dataSecurityAndGovernance().activities().contentActivities().post(contentActivity);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const contentActivity = {
    contentToProcess: {
       contentEntries: [
          {
             '@odata.type': 'microsoft.graph.processConversationMetadata',
             identifier: '07785517-9081-4fe7-a9dc-85bcdf5e9075',
             name: 'PC Purview API Explorer message',
             correlationId: 'd63eafd2-e3a9-4c1a-b726-a2e9b9d9580d',
             sequenceNumber: 0, 
             isTruncated: false,
             createdDateTime: '2025-05-27T17:23:20',
             modifiedDateTime: '2025-05-27T17:23:20'
          }
       ],
       activityMetadata: { 
          activity: 'uploadText'
       },
       deviceMetadata: {
          operatingSystemSpecifications: {
             operatingSystemPlatform: 'Windows 11',
             operatingSystemVersion: '10.0.26100.0' 
          },
          ipAddress: '127.0.0.1'
       },
       protectedAppMetadata: {
          name: 'PC Purview API Explorer',
          version: '0.2',
          applicationLocation: {
             '@odata.type': 'microsoft.graph.policyLocationApplication',
             value: '83ef208a-0396-4893-9d4f-d36efbffc8bd'
          }
       },
       integratedAppMetadata: {
          name: 'PC Purview API Explorer',
          version: '0.2' 
       }
    }
};

await client.api('/me/dataSecurityAndGovernance/activities/contentActivities')
	.post(contentActivity);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\ContentActivity;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new ContentActivity();
$additionalData = [
	'contentToProcess' => [
		'contentEntries' => [
				[
					'@odata.type' => 'microsoft.graph.processConversationMetadata',
					'identifier' => '07785517-9081-4fe7-a9dc-85bcdf5e9075',
					'name' => 'PC Purview API Explorer message',
					'correlationId' => 'd63eafd2-e3a9-4c1a-b726-a2e9b9d9580d',
					'sequenceNumber' => 0,
					'isTruncated' => false,
					'createdDateTime' => '2025-05-27T17:23:20',
					'modifiedDateTime' => '2025-05-27T17:23:20',
				],
			],
		'activityMetadata' => [
			'activity' => 'uploadText',
		],
		'deviceMetadata' => [
			'operatingSystemSpecifications' => [
				'operatingSystemPlatform' => 'Windows 11',
				'operatingSystemVersion' => '10.0.26100.0',
			],
			'ipAddress' => '127.0.0.1',
		],
		'protectedAppMetadata' => [
			'name' => 'PC Purview API Explorer',
			'version' => '0.2',
			'applicationLocation' => [
				'@odata.type' => 'microsoft.graph.policyLocationApplication',
				'value' => '83ef208a-0396-4893-9d4f-d36efbffc8bd',
			],
		],
		'integratedAppMetadata' => [
			'name' => 'PC Purview API Explorer',
			'version' => '0.2',
		],
	],
];
$requestBody->setAdditionalData($additionalData);

$result = $graphServiceClient->me()->dataSecurityAndGovernance()->activities()->contentActivities()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.content_activity import ContentActivity
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = ContentActivity(
	additional_data = {
			"content_to_process" : {
					"content_entries" : [
						{
								"@odata_type" : "microsoft.graph.processConversationMetadata",
								"identifier" : "07785517-9081-4fe7-a9dc-85bcdf5e9075",
								"name" : "PC Purview API Explorer message",
								"correlation_id" : "d63eafd2-e3a9-4c1a-b726-a2e9b9d9580d",
								"sequence_number" : 0,
								"is_truncated" : False,
								"created_date_time" : "2025-05-27T17:23:20",
								"modified_date_time" : "2025-05-27T17:23:20",
						},
					],
					"activity_metadata" : {
							"activity" : "uploadText",
					},
					"device_metadata" : {
							"operating_system_specifications" : {
									"operating_system_platform" : "Windows 11",
									"operating_system_version" : "10.0.26100.0",
							},
							"ip_address" : "127.0.0.1",
					},
					"protected_app_metadata" : {
							"name" : "PC Purview API Explorer",
							"version" : "0.2",
							"application_location" : {
									"@odata_type" : "microsoft.graph.policyLocationApplication",
									"value" : "83ef208a-0396-4893-9d4f-d36efbffc8bd",
							},
					},
					"integrated_app_metadata" : {
							"name" : "PC Purview API Explorer",
							"version" : "0.2",
					},
			},
	}
)

result = await graph_client.me.data_security_and_governance.activities.content_activities.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-Type: application/json

{
  "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#users('7c497f10-cba8-4a8d-9449-db4b76d1ef80')/dataSecurityAndGovernance/activities/contentActivities/$entity",
  "id": "4c3d1219-b1af-442f-85b5-06b7ef1cf8c8",
  "userId": "7c497f10-cba8-4a8d-9449-db4b76d1ef80",
  "scopeIdentifier": null,
  "contentMetadata": {
    "protectedAppMetadata": null,
    "contentEntries": [
      {
        "identifier": "d6ab5054-e111-45c3-9fba-9f2a59c9bbf8",
        "content": null,
        "name": "CA Purview API Explorer message",
        "correlationId": "edfb7f88-b963-4ef2-8b30-5cb90f80e01e",
        "sequenceNumber": 0,
        "length": null,
        "isTruncated": false,
        "createdDateTime": "2025-05-28T20:20:37Z",
        "modifiedDateTime": "2025-05-28T20:20:37Z"
      }
    ],
    "activityMetadata": {
      "activity": "downloadText"
    },
    "deviceMetadata": {
      "deviceType": null,
      "operatingSystemSpecifications": {
        "operatingSystemPlatform": "Windows 11",
        "operatingSystemVersion": "10.0.26100.0"
      }
    },
    "integratedAppMetadata": {
      "name": "CA Purview API Explorer",
      "version": "0.1"
    }
  }
}
```
