<!-- Source: https://learn.microsoft.com/en-us/graph/api/onedriveforbusinessrestoresession-update?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-09-11 -->

# Update oneDriveForBusinessRestoreSession

Namespace: microsoft.graph

Update the properties of a [oneDriveForBusinessRestoreSession](https://learn.microsoft.com/en-us/graph/api/resources/onedriveforbusinessrestoresession?view=graph-rest-1.0) object.

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
PATCH /solutions/backupRestore/oneDriveForBusinessRestoreSessions/{oneDriveForBusinessRestoreSessionId}
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
| driveRestoreArtifacts | [driveRestoreArtifact](https://learn.microsoft.com/en-us/graph/api/resources/driverestoreartifact?view=graph-rest-1.0) collection | Collection of [driveRestoreArtifact](https://learn.microsoft.com/en-us/graph/api/resources/driverestoreartifact?view=graph-rest-1.0). Required |
| granularDriveRestoreArtifacts | [granularDriveRestoreArtifact](https://learn.microsoft.com/en-us/graph/api/resources/granulardriverestoreartifact?view=graph-rest-1.0) collection | A collection of [granularDriveRestoreArtifact](https://learn.microsoft.com/en-us/graph/api/resources/granulardriverestoreartifact?view=graph-rest-1.0) objects. Required. |

To remove a **driveRestoreArtifact** from a standard restore session, specify the `@removed` annotation in the request body together with the ID of the [driveRestoreArtifact](https://learn.microsoft.com/en-us/graph/api/resources/driverestoreartifact?view=graph-rest-1.0) object.

To remove a **granularDriveRestoreArtifact** from a granular restore session, specify the `@removed` annotation in the request body for the respective artifact ID of the [granularDriveRestoreArtifact](https://learn.microsoft.com/en-us/graph/api/resources/granulardriverestoreartifact?view=graph-rest-1.0).

## Response

If successful, this method returns a `200 OK` response code and an updated [oneDriveForBusinessRestoreSession](https://learn.microsoft.com/en-us/graph/api/resources/driverestoreartifact?view=graph-rest-1.0) object in the response body.

For a list of possible error responses, see [Backup Storage API error responses](https://learn.microsoft.com/en-us/graph/backup-storage-error-codes).

## Examples

### Example 1: Update a standard restore session

#### Request

The following example shows a request.

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [PowerShell](#tabpanel_1_powershell)
- [Python](#tabpanel_1_python)

```http
PATCH https://graph.microsoft.com/v1.0/solutions/backupRestore/oneDriveForBusinessRestoreSessions/1b014d8c-71fe-4d00-8ab2-31850bc5b32c

{
  "driveRestoreArtifacts@delta": [
    {
      "restorePoint": { "id": "1b014d8c-71fe-4d00-a01a-31850bc5b32c" }, //Create a new drive restore artifact and add it under the Restore Session.
      "destinationType": "new"
    },
    {
      "restorePoint": { "id": "2b014d8c-71fe-4d00-a01a-31850bc5b32" },
      "destinationType": "new"
    },
    {
      "restorePoint": { "id": "3b014d8c-71fe-4d00-a01a-31850bc5b32c" },
      "destinationType": "new"
    },
    {
      "restorePoint": { "id": "4b014d8c-71fe-4d00-a01a-31850bc5b32c" },
      "destinationType": "new"
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

var requestBody = new OneDriveForBusinessRestoreSession
{
	AdditionalData = new Dictionary<string, object>
	{
		{
			"driveRestoreArtifacts@delta" , new List<object>
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
						"destinationType", new UntypedString("new")
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
						"destinationType", new UntypedString("new")
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
						"destinationType", new UntypedString("new")
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
						"destinationType", new UntypedString("new")
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
var result = await graphClient.Solutions.BackupRestore.OneDriveForBusinessRestoreSessions["{oneDriveForBusinessRestoreSession-id}"].PatchAsync(requestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

OneDriveForBusinessRestoreSession oneDriveForBusinessRestoreSession = new OneDriveForBusinessRestoreSession();
HashMap<String, Object> additionalData = new HashMap<String, Object>();
LinkedList<Object> driveRestoreArtifactsDelta = new LinkedList<Object>();
 property = new ();
 restorePoint = new ();
restorePoint.setId("1b014d8c-71fe-4d00-a01a-31850bc5b32c");
property.setRestorePoint(restorePoint);
property.setDestinationType("new");
driveRestoreArtifactsDelta.add(property);
 property1 = new ();
 restorePoint1 = new ();
restorePoint1.setId("2b014d8c-71fe-4d00-a01a-31850bc5b32");
property1.setRestorePoint(restorePoint1);
property1.setDestinationType("new");
driveRestoreArtifactsDelta.add(property1);
 property2 = new ();
 restorePoint2 = new ();
restorePoint2.setId("3b014d8c-71fe-4d00-a01a-31850bc5b32c");
property2.setRestorePoint(restorePoint2);
property2.setDestinationType("new");
driveRestoreArtifactsDelta.add(property2);
 property3 = new ();
 restorePoint3 = new ();
restorePoint3.setId("4b014d8c-71fe-4d00-a01a-31850bc5b32c");
property3.setRestorePoint(restorePoint3);
property3.setDestinationType("new");
driveRestoreArtifactsDelta.add(property3);
 property4 = new ();
 removed = new ();
removed.setReason("changed");
property4.setRemoved(removed);
property4.setId("99954f18-c8ec-4b62-85bf-cdf3b70b140e");
driveRestoreArtifactsDelta.add(property4);
 property5 = new ();
 removed1 = new ();
removed1.setReason("changed");
property5.setRemoved(removed1);
property5.setId("4267e382-71a9-4c07-bef7-bda97e09c0d2");
driveRestoreArtifactsDelta.add(property5);
 property6 = new ();
 removed2 = new ();
removed2.setReason("changed");
property6.setRemoved(removed2);
property6.setId("3667e382-71a9-4c07-bef7-bda97e09c0d2");
driveRestoreArtifactsDelta.add(property6);
additionalData.put("driveRestoreArtifacts@delta", driveRestoreArtifactsDelta);
oneDriveForBusinessRestoreSession.setAdditionalData(additionalData);
OneDriveForBusinessRestoreSession result = graphClient.solutions().backupRestore().oneDriveForBusinessRestoreSessions().byOneDriveForBusinessRestoreSessionId("{oneDriveForBusinessRestoreSession-id}").patch(oneDriveForBusinessRestoreSession);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const oneDriveForBusinessRestoreSession = {
  'driveRestoreArtifacts@delta': [
    {
      restorePoint: { id: '1b014d8c-71fe-4d00-a01a-31850bc5b32c' }, //Create a new drive restore artifact and add it under the Restore Session.
      destinationType: 'new'
    },
    {
      restorePoint: { id: '2b014d8c-71fe-4d00-a01a-31850bc5b32' },
      destinationType: 'new'
    },
    {
      restorePoint: { id: '3b014d8c-71fe-4d00-a01a-31850bc5b32c' },
      destinationType: 'new'
    },
    {
      restorePoint: { id: '4b014d8c-71fe-4d00-a01a-31850bc5b32c' },
      destinationType: 'new'
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

await client.api('/solutions/backupRestore/oneDriveForBusinessRestoreSessions/1b014d8c-71fe-4d00-8ab2-31850bc5b32c')
	.update(oneDriveForBusinessRestoreSession);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\OneDriveForBusinessRestoreSession;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new OneDriveForBusinessRestoreSession();
$additionalData = [
	'driveRestoreArtifacts@delta' => [
			[
				'restorePoint' => [
					'id' => '1b014d8c-71fe-4d00-a01a-31850bc5b32c',
				],
				'destinationType' => 'new',
			],
			[
				'restorePoint' => [
					'id' => '2b014d8c-71fe-4d00-a01a-31850bc5b32',
				],
				'destinationType' => 'new',
			],
			[
				'restorePoint' => [
					'id' => '3b014d8c-71fe-4d00-a01a-31850bc5b32c',
				],
				'destinationType' => 'new',
			],
			[
				'restorePoint' => [
					'id' => '4b014d8c-71fe-4d00-a01a-31850bc5b32c',
				],
				'destinationType' => 'new',
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

$result = $graphServiceClient->solutions()->backupRestore()->oneDriveForBusinessRestoreSessions()->byOneDriveForBusinessRestoreSessionId('oneDriveForBusinessRestoreSession-id')->patch($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.BackupRestore

$params = @{
	"driveRestoreArtifacts@delta" = @(
		@{
			restorePoint = @{
				id = "1b014d8c-71fe-4d00-a01a-31850bc5b32c"
			}
			destinationType = "new"
		}
		@{
			restorePoint = @{
				id = "2b014d8c-71fe-4d00-a01a-31850bc5b32"
			}
			destinationType = "new"
		}
		@{
			restorePoint = @{
				id = "3b014d8c-71fe-4d00-a01a-31850bc5b32c"
			}
			destinationType = "new"
		}
		@{
			restorePoint = @{
				id = "4b014d8c-71fe-4d00-a01a-31850bc5b32c"
			}
			destinationType = "new"
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

Update-MgSolutionBackupRestoreOneDriveForBusinessRestoreSession -OneDriveForBusinessRestoreSessionId $oneDriveForBusinessRestoreSessionId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.one_drive_for_business_restore_session import OneDriveForBusinessRestoreSession
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = OneDriveForBusinessRestoreSession(
	additional_data = {
			"drive_restore_artifacts@delta" : [
				{
						"restore_point" : {
								"id" : "1b014d8c-71fe-4d00-a01a-31850bc5b32c",
						},
						"destination_type" : "new",
				},
				{
						"restore_point" : {
								"id" : "2b014d8c-71fe-4d00-a01a-31850bc5b32",
						},
						"destination_type" : "new",
				},
				{
						"restore_point" : {
								"id" : "3b014d8c-71fe-4d00-a01a-31850bc5b32c",
						},
						"destination_type" : "new",
				},
				{
						"restore_point" : {
								"id" : "4b014d8c-71fe-4d00-a01a-31850bc5b32c",
						},
						"destination_type" : "new",
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

result = await graph_client.solutions.backup_restore.one_drive_for_business_restore_sessions.by_one_drive_for_business_restore_session_id('oneDriveForBusinessRestoreSession-id').patch(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK

{
  "driveRestoreArtifacts@delta": [
    {
      "id": "89014d8c-71fe-4d00-a01a-31850bc5b32c",
      "restorePoint": { "id": "1b014d8c-71fe-4d00-a01a-31850bc5b32c" },
      "destinationType": "new",
      "status": "added",
      "createdDateTime": "2015-06-19T12:01:03.45Z"
    },
    {
      "id": "67014d8c-71fe-4d00-a01a-31850bc5b32c",
      "restorePoint": { "id": "2b014d8c-71fe-4d00-a01a-31850bc5b32c" },
      "destinationType": "new",
      "status": "added",
      "createdDateTime": "2015-06-19T12:01:03.45Z"
    },
    {
      "id": "56014d8c-71fe-4d00-a01a-31850bc5b32c",
      "restorePoint": { "id": "3b014d8c-71fe-4d00-a01a-31850bc5b32c" },
      "destinationType": "new",
      "status": "added",
      "createdDateTime": "2015-06-19T12:01:03.45Z"
    },
    {
      "id": "32014d8c-71fe-4d00-a01a-31850bc5b32c",
      "restorePoint": { "id": "4b014d8c-71fe-4d00-a01a-31850bc5b32c" },
      "destinationType": "new",
      "status": "added",
      "createdDateTime": "2015-06-19T12:01:03.45Z"
    },
    {
      //Error scenario
      "@contentId": "3467e382-71a9-4c07-bef7-bda97e09c0d2", // To add context and more traceability.
      "@Core.DataModificationException": {
        "info": {
          "code": "Invalid",
          "message": "The identifier to be removed from the restore session does not exist"
        },
        "failedOperation": "remove",
        "responseCode": 409
      },
      "id": "4267e382-71a9-4c07-bef7-bda97e09c0d2"
    }
  ]
}
```

### Example 2: Update a granular restore session

#### Request

The following example shows a request.

- [HTTP](#tabpanel_2_http)
- [C#](#tabpanel_2_csharp)
- [Java](#tabpanel_2_java)
- [JavaScript](#tabpanel_2_javascript)
- [PHP](#tabpanel_2_php)
- [PowerShell](#tabpanel_2_powershell)
- [Python](#tabpanel_2_python)

```http
PATCH https://graph.microsoft.com/v1.0/solutions/backupRestore/oneDriveForBusinessRestoreSessions/43e0638e-3ad7-4c7e-8749-72175d046e30
Content-Type: application/json

{
  "granularDriveRestoreArtifacts@delta": [
    {
      "browseSessionId": "m_RtZ8BiiUXOK69cuN6gwubfm9_yeVlDg8s6hci01_cVOAE",
      "itemKey": "a535851e-9fc6-4eb1-90ab-2955fd9117b5,2a8b7eaf-092a-4561-a25a-998ad2e5142e,38eec3f1-b879-44a6-8ae6-05bd46ed4b3d,ce66019f-cdf9-4575-aa81-de3aabe844a2"
    },
    {
      "@removed": {
        "reason": "changed"
      },
      "id": "a535851e-9fc6-4eb1-90ab-2955fd9117b5,2a8b7eaf-092a-4561-a25a-998ad2e5142e,38eec3f1-b879-44a6-8ae6-05bd46ed4b3d,ce66019f-cdf9-4575-aa81-de3aabe844a2"
    }
  ]
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;
using Microsoft.Kiota.Abstractions.Serialization;

var requestBody = new OneDriveForBusinessRestoreSession
{
	AdditionalData = new Dictionary<string, object>
	{
		{
			"granularDriveRestoreArtifacts@delta" , new List<object>
			{
				new UntypedObject(new Dictionary<string, UntypedNode>
				{
					{
						"browseSessionId", new UntypedString("m_RtZ8BiiUXOK69cuN6gwubfm9_yeVlDg8s6hci01_cVOAE")
					},
					{
						"itemKey", new UntypedString("a535851e-9fc6-4eb1-90ab-2955fd9117b5,2a8b7eaf-092a-4561-a25a-998ad2e5142e,38eec3f1-b879-44a6-8ae6-05bd46ed4b3d,ce66019f-cdf9-4575-aa81-de3aabe844a2")
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
						"id", new UntypedString("a535851e-9fc6-4eb1-90ab-2955fd9117b5,2a8b7eaf-092a-4561-a25a-998ad2e5142e,38eec3f1-b879-44a6-8ae6-05bd46ed4b3d,ce66019f-cdf9-4575-aa81-de3aabe844a2")
					},
				}),
			}
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Solutions.BackupRestore.OneDriveForBusinessRestoreSessions["{oneDriveForBusinessRestoreSession-id}"].PatchAsync(requestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

OneDriveForBusinessRestoreSession oneDriveForBusinessRestoreSession = new OneDriveForBusinessRestoreSession();
HashMap<String, Object> additionalData = new HashMap<String, Object>();
LinkedList<Object> granularDriveRestoreArtifactsDelta = new LinkedList<Object>();
 property = new ();
property.setBrowseSessionId("m_RtZ8BiiUXOK69cuN6gwubfm9_yeVlDg8s6hci01_cVOAE");
property.setItemKey("a535851e-9fc6-4eb1-90ab-2955fd9117b5,2a8b7eaf-092a-4561-a25a-998ad2e5142e,38eec3f1-b879-44a6-8ae6-05bd46ed4b3d,ce66019f-cdf9-4575-aa81-de3aabe844a2");
granularDriveRestoreArtifactsDelta.add(property);
 property1 = new ();
 removed = new ();
removed.setReason("changed");
property1.setRemoved(removed);
property1.setId("a535851e-9fc6-4eb1-90ab-2955fd9117b5,2a8b7eaf-092a-4561-a25a-998ad2e5142e,38eec3f1-b879-44a6-8ae6-05bd46ed4b3d,ce66019f-cdf9-4575-aa81-de3aabe844a2");
granularDriveRestoreArtifactsDelta.add(property1);
additionalData.put("granularDriveRestoreArtifacts@delta", granularDriveRestoreArtifactsDelta);
oneDriveForBusinessRestoreSession.setAdditionalData(additionalData);
OneDriveForBusinessRestoreSession result = graphClient.solutions().backupRestore().oneDriveForBusinessRestoreSessions().byOneDriveForBusinessRestoreSessionId("{oneDriveForBusinessRestoreSession-id}").patch(oneDriveForBusinessRestoreSession);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const oneDriveForBusinessRestoreSession = {
  'granularDriveRestoreArtifacts@delta': [
    {
      browseSessionId: 'm_RtZ8BiiUXOK69cuN6gwubfm9_yeVlDg8s6hci01_cVOAE',
      itemKey: 'a535851e-9fc6-4eb1-90ab-2955fd9117b5,2a8b7eaf-092a-4561-a25a-998ad2e5142e,38eec3f1-b879-44a6-8ae6-05bd46ed4b3d,ce66019f-cdf9-4575-aa81-de3aabe844a2'
    },
    {
      '@removed': {
        reason: 'changed'
      },
      id: 'a535851e-9fc6-4eb1-90ab-2955fd9117b5,2a8b7eaf-092a-4561-a25a-998ad2e5142e,38eec3f1-b879-44a6-8ae6-05bd46ed4b3d,ce66019f-cdf9-4575-aa81-de3aabe844a2'
    }
  ]
};

await client.api('/solutions/backupRestore/oneDriveForBusinessRestoreSessions/43e0638e-3ad7-4c7e-8749-72175d046e30')
	.update(oneDriveForBusinessRestoreSession);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\OneDriveForBusinessRestoreSession;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new OneDriveForBusinessRestoreSession();
$additionalData = [
	'granularDriveRestoreArtifacts@delta' => [
			[
				'browseSessionId' => 'm_RtZ8BiiUXOK69cuN6gwubfm9_yeVlDg8s6hci01_cVOAE',
				'itemKey' => 'a535851e-9fc6-4eb1-90ab-2955fd9117b5,2a8b7eaf-092a-4561-a25a-998ad2e5142e,38eec3f1-b879-44a6-8ae6-05bd46ed4b3d,ce66019f-cdf9-4575-aa81-de3aabe844a2',
			],
			[
				'@removed' => [
					'reason' => 'changed',
				],
				'id' => 'a535851e-9fc6-4eb1-90ab-2955fd9117b5,2a8b7eaf-092a-4561-a25a-998ad2e5142e,38eec3f1-b879-44a6-8ae6-05bd46ed4b3d,ce66019f-cdf9-4575-aa81-de3aabe844a2',
			],
		],
];
$requestBody->setAdditionalData($additionalData);

$result = $graphServiceClient->solutions()->backupRestore()->oneDriveForBusinessRestoreSessions()->byOneDriveForBusinessRestoreSessionId('oneDriveForBusinessRestoreSession-id')->patch($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.BackupRestore

$params = @{
	"granularDriveRestoreArtifacts@delta" = @(
		@{
			browseSessionId = "m_RtZ8BiiUXOK69cuN6gwubfm9_yeVlDg8s6hci01_cVOAE"
			itemKey = "a535851e-9fc6-4eb1-90ab-2955fd9117b5,2a8b7eaf-092a-4561-a25a-998ad2e5142e,38eec3f1-b879-44a6-8ae6-05bd46ed4b3d,ce66019f-cdf9-4575-aa81-de3aabe844a2"
		}
		@{
			"@removed" = @{
				reason = "changed"
			}
			id = "a535851e-9fc6-4eb1-90ab-2955fd9117b5,2a8b7eaf-092a-4561-a25a-998ad2e5142e,38eec3f1-b879-44a6-8ae6-05bd46ed4b3d,ce66019f-cdf9-4575-aa81-de3aabe844a2"
		}
	)
}

Update-MgSolutionBackupRestoreOneDriveForBusinessRestoreSession -OneDriveForBusinessRestoreSessionId $oneDriveForBusinessRestoreSessionId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.one_drive_for_business_restore_session import OneDriveForBusinessRestoreSession
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = OneDriveForBusinessRestoreSession(
	additional_data = {
			"granular_drive_restore_artifacts@delta" : [
				{
						"browse_session_id" : "m_RtZ8BiiUXOK69cuN6gwubfm9_yeVlDg8s6hci01_cVOAE",
						"item_key" : "a535851e-9fc6-4eb1-90ab-2955fd9117b5,2a8b7eaf-092a-4561-a25a-998ad2e5142e,38eec3f1-b879-44a6-8ae6-05bd46ed4b3d,ce66019f-cdf9-4575-aa81-de3aabe844a2",
				},
				{
						"@removed" : {
								"reason" : "changed",
						},
						"id" : "a535851e-9fc6-4eb1-90ab-2955fd9117b5,2a8b7eaf-092a-4561-a25a-998ad2e5142e,38eec3f1-b879-44a6-8ae6-05bd46ed4b3d,ce66019f-cdf9-4575-aa81-de3aabe844a2",
				},
			],
	}
)

result = await graph_client.solutions.backup_restore.one_drive_for_business_restore_sessions.by_one_drive_for_business_restore_session_id('oneDriveForBusinessRestoreSession-id').patch(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "@context": "#$delta",
  "id": "43e0638e-3ad7-4c7e-8749-72175d046e30",
  "granularDriveRestoreArtifacts@delta": [
    {
      "directoryObjectId": null,
      "id": "a535851e-9fc6-4eb1-90ab-2955fd9117b5,2a8b7eaf-092a-4561-a25a-998ad2e5142e,38eec3f1-b879-44a6-8ae6-05bd46ed4b3d,ce66019f-cdf9-4575-aa81-de3aabe844a2",
      "browseSessionId": "m_RtZ8BiiUXOK69cuN6gwubfm9_yeVlDg8s6hci01_cVOAE",
      "restoredItemKey": "",
      "webUrl": "",
      "restoredItemPath": null,
      "restoredItemWebUrl": "",
      "status": "added",
      "restorePointDateTime": "0001-01-01T00:00:00Z",
      "startDateTime": "0001-01-01T00:00:00Z",
      "completionDateTime": "0001-01-01T00:00:00Z"
    },
    {
      "id": "a535851e-9fc6-4eb1-90ab-2955fd9117b5,2a8b7eaf-092a-4561-a25a-998ad2e5142e,38eec3f1-b879-44a6-8ae6-05bd46ed4b3d,ce66019f-cdf9-4575-aa81-de3aabe844a2",
      "@removed": {
        "reason": "changed"
      }
    }
  ]
}
```
