<!-- Source: https://learn.microsoft.com/en-us/graph/api/exchangerestoresession-update?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-23 -->

# Update exchangeRestoreSession

Namespace: microsoft.graph

Update the properties of an [exchangeRestoreSession](https://learn.microsoft.com/en-us/graph/api/resources/exchangerestoresession?view=graph-rest-1.0).

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | BackupRestore-Restore.ReadWrite.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | BackupRestore-Restore.ReadWrite.All | Not available. |

## HTTP request

```http
PATCH /solutions/backupRestore/exchangeRestoreSessions/{exchangeRestoreSessionId}
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply *only* the values for properties to update. Existing properties that aren't included in the request body maintain their previous values or are recalculated based on changes to other property values.

The following table specifies the properties that can be updated.

| Property | Type | Description |
| :--- | :--- | :--- |
| mailboxRestoreArtifacts | [mailboxRestoreArtifact](https://learn.microsoft.com/en-us/graph/api/resources/mailboxrestoreartifact?view=graph-rest-1.0) collection | A collection of [mailboxRestoreArtifact](https://learn.microsoft.com/en-us/graph/api/resources/mailboxrestoreartifact?view=graph-rest-1.0) objects. Required. |

To remove an **exchangeRestoreSession**, specify the @removed annotation in the request body for the restore point artifact with the ID of the [mailboxRestoreArtifact](https://learn.microsoft.com/en-us/graph/api/resources/mailboxrestoreartifact?view=graph-rest-1.0).

## Response

If successful, this method returns a `200 OK` response code and an updated [exchangeRestoreSession](https://learn.microsoft.com/en-us/graph/api/resources/exchangerestoresession?view=graph-rest-1.0) object in the response body.

For a list of possible error responses, see [Backup Storage API error responses](https://learn.microsoft.com/en-us/graph/backup-storage-error-codes).

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
PATCH https://graph.microsoft.com/v1.0/solutions/backupRestore/exchangeRestoreSessions/2b814d8c-71fd-4d00-a01a-31850bc5b32c
Content-Type: application/json

{
  "mailboxRestoreArtifacts@delta": [
    {
      "restorePoint": { "id": "1b014d8c-71fe-4d00-a01a-31850bc5b32c" }, //Create a new mailbox restore artifact and add it under the Restore Session.
      "destinationType": "inPlace"
    },
    {
      "restorePoint": { "id": "2b014d8c-71fe-4d00-a01a-31850bc5b32" },
      "destinationType": "inPlace"
    },
    {
      "restorePoint": { "id": "3b014d8c-71fe-4d00-a01a-31850bc5b32c" },
      "destinationType": "inPlace"
    },
    {
      "restorePoint": { "id": "4b014d8c-71fe-4d00-a01a-31850bc5b32c" },
      "destinationType": "inPlace"
    },
    {
      "@removed": {
        "reason": "changed"
      },
      "id": "99954f18-c8ec-4b62-85bf-cdf3b70b140e"
    },
    {
      "@removed": {
        "reason": "changed"
      },
      "id": "4267e382-71a9-4c07-bef7-bda97e09c0d2"
    },
    {
      "@removed": {
        "reason": "changed"
      },
      "id": "3667e382-71a9-4c07-bef7-bda97e09c0d2"
    }
  ]
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;
using Microsoft.Kiota.Abstractions.Serialization;

var requestBody = new ExchangeRestoreSession
{
	AdditionalData = new Dictionary<string, object>
	{
		{
			"mailboxRestoreArtifacts@delta" , new List<object>
			{
				new UntypedObject(new Dictionary<string, UntypedNode>
				{
					{
						"restorePoint", new UntypedObject(new Dictionary<string, UntypedNode>
						{
							{
								"id", new UntypedString("1b014d8c-71fe-4d00-a01a-31850bc5b32c")
							},
						})
					},
					{
						"destinationType", new UntypedString("inPlace")
					},
				}),
				new UntypedObject(new Dictionary<string, UntypedNode>
				{
					{
						"restorePoint", new UntypedObject(new Dictionary<string, UntypedNode>
						{
							{
								"id", new UntypedString("2b014d8c-71fe-4d00-a01a-31850bc5b32")
							},
						})
					},
					{
						"destinationType", new UntypedString("inPlace")
					},
				}),
				new UntypedObject(new Dictionary<string, UntypedNode>
				{
					{
						"restorePoint", new UntypedObject(new Dictionary<string, UntypedNode>
						{
							{
								"id", new UntypedString("3b014d8c-71fe-4d00-a01a-31850bc5b32c")
							},
						})
					},
					{
						"destinationType", new UntypedString("inPlace")
					},
				}),
				new UntypedObject(new Dictionary<string, UntypedNode>
				{
					{
						"restorePoint", new UntypedObject(new Dictionary<string, UntypedNode>
						{
							{
								"id", new UntypedString("4b014d8c-71fe-4d00-a01a-31850bc5b32c")
							},
						})
					},
					{
						"destinationType", new UntypedString("inPlace")
					},
				}),
				new UntypedObject(new Dictionary<string, UntypedNode>
				{
					{
						"@removed", new UntypedObject(new Dictionary<string, UntypedNode>
						{
							{
								"reason", new UntypedString("changed")
							},
						})
					},
					{
						"id", new UntypedString("99954f18-c8ec-4b62-85bf-cdf3b70b140e")
					},
				}),
				new UntypedObject(new Dictionary<string, UntypedNode>
				{
					{
						"@removed", new UntypedObject(new Dictionary<string, UntypedNode>
						{
							{
								"reason", new UntypedString("changed")
							},
						})
					},
					{
						"id", new UntypedString("4267e382-71a9-4c07-bef7-bda97e09c0d2")
					},
				}),
				new UntypedObject(new Dictionary<string, UntypedNode>
				{
					{
						"@removed", new UntypedObject(new Dictionary<string, UntypedNode>
						{
							{
								"reason", new UntypedString("changed")
							},
						})
					},
					{
						"id", new UntypedString("3667e382-71a9-4c07-bef7-bda97e09c0d2")
					},
				}),
			}
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Solutions.BackupRestore.ExchangeRestoreSessions["{exchangeRestoreSession-id}"].PatchAsync(requestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

ExchangeRestoreSession exchangeRestoreSession = new ExchangeRestoreSession();
HashMap<String, Object> additionalData = new HashMap<String, Object>();
LinkedList<Object> mailboxRestoreArtifactsDelta = new LinkedList<Object>();
 property = new ();
 restorePoint = new ();
restorePoint.setId("1b014d8c-71fe-4d00-a01a-31850bc5b32c");
property.setRestorePoint(restorePoint);
property.setDestinationType("inPlace");
mailboxRestoreArtifactsDelta.add(property);
 property1 = new ();
 restorePoint1 = new ();
restorePoint1.setId("2b014d8c-71fe-4d00-a01a-31850bc5b32");
property1.setRestorePoint(restorePoint1);
property1.setDestinationType("inPlace");
mailboxRestoreArtifactsDelta.add(property1);
 property2 = new ();
 restorePoint2 = new ();
restorePoint2.setId("3b014d8c-71fe-4d00-a01a-31850bc5b32c");
property2.setRestorePoint(restorePoint2);
property2.setDestinationType("inPlace");
mailboxRestoreArtifactsDelta.add(property2);
 property3 = new ();
 restorePoint3 = new ();
restorePoint3.setId("4b014d8c-71fe-4d00-a01a-31850bc5b32c");
property3.setRestorePoint(restorePoint3);
property3.setDestinationType("inPlace");
mailboxRestoreArtifactsDelta.add(property3);
 property4 = new ();
 removed = new ();
removed.setReason("changed");
property4.setRemoved(removed);
property4.setId("99954f18-c8ec-4b62-85bf-cdf3b70b140e");
mailboxRestoreArtifactsDelta.add(property4);
 property5 = new ();
 removed1 = new ();
removed1.setReason("changed");
property5.setRemoved(removed1);
property5.setId("4267e382-71a9-4c07-bef7-bda97e09c0d2");
mailboxRestoreArtifactsDelta.add(property5);
 property6 = new ();
 removed2 = new ();
removed2.setReason("changed");
property6.setRemoved(removed2);
property6.setId("3667e382-71a9-4c07-bef7-bda97e09c0d2");
mailboxRestoreArtifactsDelta.add(property6);
additionalData.put("mailboxRestoreArtifacts@delta", mailboxRestoreArtifactsDelta);
exchangeRestoreSession.setAdditionalData(additionalData);
ExchangeRestoreSession result = graphClient.solutions().backupRestore().exchangeRestoreSessions().byExchangeRestoreSessionId("{exchangeRestoreSession-id}").patch(exchangeRestoreSession);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const exchangeRestoreSession = {
  'mailboxRestoreArtifacts@delta': [
    {
      restorePoint: { id: '1b014d8c-71fe-4d00-a01a-31850bc5b32c' }, //Create a new mailbox restore artifact and add it under the Restore Session.
      destinationType: 'inPlace'
    },
    {
      restorePoint: { id: '2b014d8c-71fe-4d00-a01a-31850bc5b32' },
      destinationType: 'inPlace'
    },
    {
      restorePoint: { id: '3b014d8c-71fe-4d00-a01a-31850bc5b32c' },
      destinationType: 'inPlace'
    },
    {
      restorePoint: { id: '4b014d8c-71fe-4d00-a01a-31850bc5b32c' },
      destinationType: 'inPlace'
    },
    {
      '@removed': {
        reason: 'changed'
      },
      id: '99954f18-c8ec-4b62-85bf-cdf3b70b140e'
    },
    {
      '@removed': {
        reason: 'changed'
      },
      id: '4267e382-71a9-4c07-bef7-bda97e09c0d2'
    },
    {
      '@removed': {
        reason: 'changed'
      },
      id: '3667e382-71a9-4c07-bef7-bda97e09c0d2'
    }
  ]
};

await client.api('/solutions/backupRestore/exchangeRestoreSessions/2b814d8c-71fd-4d00-a01a-31850bc5b32c')
	.update(exchangeRestoreSession);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\ExchangeRestoreSession;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new ExchangeRestoreSession();
$additionalData = [
	'mailboxRestoreArtifacts@delta' => [
			[
				'restorePoint' => [
					'id' => '1b014d8c-71fe-4d00-a01a-31850bc5b32c',
				],
				'destinationType' => 'inPlace',
			],
			[
				'restorePoint' => [
					'id' => '2b014d8c-71fe-4d00-a01a-31850bc5b32',
				],
				'destinationType' => 'inPlace',
			],
			[
				'restorePoint' => [
					'id' => '3b014d8c-71fe-4d00-a01a-31850bc5b32c',
				],
				'destinationType' => 'inPlace',
			],
			[
				'restorePoint' => [
					'id' => '4b014d8c-71fe-4d00-a01a-31850bc5b32c',
				],
				'destinationType' => 'inPlace',
			],
			[
				'@removed' => [
					'reason' => 'changed',
				],
				'id' => '99954f18-c8ec-4b62-85bf-cdf3b70b140e',
			],
			[
				'@removed' => [
					'reason' => 'changed',
				],
				'id' => '4267e382-71a9-4c07-bef7-bda97e09c0d2',
			],
			[
				'@removed' => [
					'reason' => 'changed',
				],
				'id' => '3667e382-71a9-4c07-bef7-bda97e09c0d2',
			],
		],
];
$requestBody->setAdditionalData($additionalData);

$result = $graphServiceClient->solutions()->backupRestore()->exchangeRestoreSessions()->byExchangeRestoreSessionId('exchangeRestoreSession-id')->patch($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.BackupRestore

$params = @{
	"mailboxRestoreArtifacts@delta" = @(
		@{
			restorePoint = @{
				id = "1b014d8c-71fe-4d00-a01a-31850bc5b32c"
			}
			destinationType = "inPlace"
		}
		@{
			restorePoint = @{
				id = "2b014d8c-71fe-4d00-a01a-31850bc5b32"
			}
			destinationType = "inPlace"
		}
		@{
			restorePoint = @{
				id = "3b014d8c-71fe-4d00-a01a-31850bc5b32c"
			}
			destinationType = "inPlace"
		}
		@{
			restorePoint = @{
				id = "4b014d8c-71fe-4d00-a01a-31850bc5b32c"
			}
			destinationType = "inPlace"
		}
		@{
			"@removed" = @{
				reason = "changed"
			}
			id = "99954f18-c8ec-4b62-85bf-cdf3b70b140e"
		}
		@{
			"@removed" = @{
				reason = "changed"
			}
			id = "4267e382-71a9-4c07-bef7-bda97e09c0d2"
		}
		@{
			"@removed" = @{
				reason = "changed"
			}
			id = "3667e382-71a9-4c07-bef7-bda97e09c0d2"
		}
	)
}

Update-MgSolutionBackupRestoreExchangeRestoreSession -ExchangeRestoreSessionId $exchangeRestoreSessionId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.exchange_restore_session import ExchangeRestoreSession
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = ExchangeRestoreSession(
	additional_data = {
			"mailbox_restore_artifacts@delta" : [
				{
						"restore_point" : {
								"id" : "1b014d8c-71fe-4d00-a01a-31850bc5b32c",
						},
						"destination_type" : "inPlace",
				},
				{
						"restore_point" : {
								"id" : "2b014d8c-71fe-4d00-a01a-31850bc5b32",
						},
						"destination_type" : "inPlace",
				},
				{
						"restore_point" : {
								"id" : "3b014d8c-71fe-4d00-a01a-31850bc5b32c",
						},
						"destination_type" : "inPlace",
				},
				{
						"restore_point" : {
								"id" : "4b014d8c-71fe-4d00-a01a-31850bc5b32c",
						},
						"destination_type" : "inPlace",
				},
				{
						"@removed" : {
								"reason" : "changed",
						},
						"id" : "99954f18-c8ec-4b62-85bf-cdf3b70b140e",
				},
				{
						"@removed" : {
								"reason" : "changed",
						},
						"id" : "4267e382-71a9-4c07-bef7-bda97e09c0d2",
				},
				{
						"@removed" : {
								"reason" : "changed",
						},
						"id" : "3667e382-71a9-4c07-bef7-bda97e09c0d2",
				},
			],
	}
)

result = await graph_client.solutions.backup_restore.exchange_restore_sessions.by_exchange_restore_session_id('exchangeRestoreSession-id').patch(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "mailboxRestoreArtifacts@delta": [
    {
      "id": "89014d8c-71fe-4d00-a01a-31850bc5b32c",
      "restorePoint": { "id": "1b014d8c-71fe-4d00-a01a-31850bc5b32c" },
      "destinationType": "inPlace",
      "status": "added",
      "createdDateTime": "2015-06-19T12:01:03.45Z"
    },
    {
      "id": "67014d8c-71fe-4d00-a01a-31850bc5b32c",
      "restorePoint": { "id": "2b014d8c-71fe-4d00-a01a-31850bc5b32c" },
      "destinationType": "inPlace",
      "status": "added",
      "createdDateTime": "2015-06-19T12:01:03.45Z"
    },
    {
      "id": "56014d8c-71fe-4d00-a01a-31850bc5b32c",
      "restorePoint": { "id": "3b014d8c-71fe-4d00-a01a-31850bc5b32c" },
      "destinationType": "inPlace",
      "status": "added",
      "createdDateTime": "2015-06-19T12:01:03.45Z"
    },
    {
      "id": "32014d8c-71fe-4d00-a01a-31850bc5b32c",
      "restorePoint": { "id": "4b014d8c-71fe-4d00-a01a-31850bc5b32c" },
      "destinationType": "inPlace",
      "status": "added",
      "createdDateTime": "2015-06-19T12:01:03.45Z"
    },
    {
      //Error scenario
      "@contentId": "3467e382-71a9-4c07-bef7-bda97e09c0d2", // To add context and more traceability.
      "@Core.DataModificationException": {
        "info": {
          "code": "Invalid",
          "message": "The identifier to be removed from the Restore Session does not exist"
        },
        "failedOperation": "remove",
        "responseCode": 409
      },
      "id": "4267e382-71a9-4c07-bef7-bda97e09c0d2"
    }
  ]
}
```
