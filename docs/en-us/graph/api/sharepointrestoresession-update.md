<!-- Source: https://learn.microsoft.com/en-us/graph/api/sharepointrestoresession-update?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-05-12 -->

# Update sharePointRestoreSession

Namespace: microsoft.graph

Update the properties of a [sharePointRestoreSession](https://learn.microsoft.com/en-us/graph/api/resources/sharepointrestoresession?view=graph-rest-1.0) object.

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
PATCH /solutions/backupRestore/sharePointRestoreSessions/{sharePointRestoreSessionId}
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
| siteRestoreArtifacts | [siteRestoreArtifact](https://learn.microsoft.com/en-us/graph/api/resources/siterestoreartifact?view=graph-rest-1.0) collection | A collection of [siteRestoreArtifact](https://learn.microsoft.com/en-us/graph/api/resources/siterestoreartifact?view=graph-rest-1.0) objects. Required. |
| granularSiteRestoreArtifacts | [granularSiteRestoreArtifact](https://learn.microsoft.com/en-us/graph/api/resources/granularsiterestoreartifact?view=graph-rest-1.0) collection | A collection of [granularSiteRestoreArtifact](https://learn.microsoft.com/en-us/graph/api/resources/granularsiterestoreartifact?view=graph-rest-1.0) objects. Required. |

To remove a **siteRestoreArtifact** from a site restore session, specify the `@removed` annotation in the request body for the respective restore point artifact together with the ID of the [siteRestoreArtifact](https://learn.microsoft.com/en-us/graph/api/resources/siterestoreartifact?view=graph-rest-1.0).

To remove a **granularSiteRestoreArtifact** from a granular restore session, specify the `@removed` annotation in the request body for the respective artifact ID of the [granularSiteRestoreArtifact](https://learn.microsoft.com/en-us/graph/api/resources/granularsiterestoreartifact?view=graph-rest-1.0).

## Response

If successful, this method returns a `200 OK` response code and an updated [sharePointRestoreSession](https://learn.microsoft.com/en-us/graph/api/resources/sharepointrestoresession?view=graph-rest-1.0) object in the response body.

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
PATCH https://graph.microsoft.com/v1.0/solutions/backupRestore/sharepointRestoreSessions/845457dc-4bb2-4815-bef3-8628ebd1952
Content-Type: application/json

{
  "siteRestoreArtifacts@delta": [
    {
      "restorePoint": { "id": "1b014d8c-71fe-4d00-a01a-31850bc5b32c" }, //Create a new site restore artifact and add it under the Restore Session.
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
      "id": "959ba739-70b5-43c4-8c90-b2c22014f18a"
    },
    {
      "@removed": {
        "reason": "changed"
      },
      "id": "959ba739-70b5-43c4-8c90-b2c22014f18b"
    },
    {
      "@removed": {
        "reason": "changed"
      },
      "id": "959ba739-70b5-43c4-8c90-b2c22014f18c"
    }
  ]
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;
using Microsoft.Kiota.Abstractions.Serialization;

var requestBody = new SharePointRestoreSession
{
	AdditionalData = new Dictionary<string, object>
	{
		{
			"siteRestoreArtifacts@delta" , new List<object>
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
						"id", new UntypedString("959ba739-70b5-43c4-8c90-b2c22014f18a")
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
						"id", new UntypedString("959ba739-70b5-43c4-8c90-b2c22014f18b")
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
						"id", new UntypedString("959ba739-70b5-43c4-8c90-b2c22014f18c")
					},
				}),
			}
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Solutions.BackupRestore.SharePointRestoreSessions["{sharePointRestoreSession-id}"].PatchAsync(requestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

SharePointRestoreSession sharePointRestoreSession = new SharePointRestoreSession();
HashMap<String, Object> additionalData = new HashMap<String, Object>();
LinkedList<Object> siteRestoreArtifactsDelta = new LinkedList<Object>();
 property = new ();
 restorePoint = new ();
restorePoint.setId("1b014d8c-71fe-4d00-a01a-31850bc5b32c");
property.setRestorePoint(restorePoint);
property.setDestinationType("new");
siteRestoreArtifactsDelta.add(property);
 property1 = new ();
 restorePoint1 = new ();
restorePoint1.setId("2b014d8c-71fe-4d00-a01a-31850bc5b32");
property1.setRestorePoint(restorePoint1);
property1.setDestinationType("new");
siteRestoreArtifactsDelta.add(property1);
 property2 = new ();
 restorePoint2 = new ();
restorePoint2.setId("3b014d8c-71fe-4d00-a01a-31850bc5b32c");
property2.setRestorePoint(restorePoint2);
property2.setDestinationType("new");
siteRestoreArtifactsDelta.add(property2);
 property3 = new ();
 restorePoint3 = new ();
restorePoint3.setId("4b014d8c-71fe-4d00-a01a-31850bc5b32c");
property3.setRestorePoint(restorePoint3);
property3.setDestinationType("new");
siteRestoreArtifactsDelta.add(property3);
 property4 = new ();
 removed = new ();
removed.setReason("changed");
property4.setRemoved(removed);
property4.setId("959ba739-70b5-43c4-8c90-b2c22014f18a");
siteRestoreArtifactsDelta.add(property4);
 property5 = new ();
 removed1 = new ();
removed1.setReason("changed");
property5.setRemoved(removed1);
property5.setId("959ba739-70b5-43c4-8c90-b2c22014f18b");
siteRestoreArtifactsDelta.add(property5);
 property6 = new ();
 removed2 = new ();
removed2.setReason("changed");
property6.setRemoved(removed2);
property6.setId("959ba739-70b5-43c4-8c90-b2c22014f18c");
siteRestoreArtifactsDelta.add(property6);
additionalData.put("siteRestoreArtifacts@delta", siteRestoreArtifactsDelta);
sharePointRestoreSession.setAdditionalData(additionalData);
SharePointRestoreSession result = graphClient.solutions().backupRestore().sharePointRestoreSessions().bySharePointRestoreSessionId("{sharePointRestoreSession-id}").patch(sharePointRestoreSession);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const sharePointRestoreSession = {
  'siteRestoreArtifacts@delta': [
    {
      restorePoint: { id: '1b014d8c-71fe-4d00-a01a-31850bc5b32c' }, //Create a new site restore artifact and add it under the Restore Session.
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
      id: '959ba739-70b5-43c4-8c90-b2c22014f18a'
    },
    {
      '@removed': {
        reason: 'changed'
      },
      id: '959ba739-70b5-43c4-8c90-b2c22014f18b'
    },
    {
      '@removed': {
        reason: 'changed'
      },
      id: '959ba739-70b5-43c4-8c90-b2c22014f18c'
    }
  ]
};

await client.api('/solutions/backupRestore/sharepointRestoreSessions/845457dc-4bb2-4815-bef3-8628ebd1952')
	.update(sharePointRestoreSession);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\SharePointRestoreSession;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new SharePointRestoreSession();
$additionalData = [
	'siteRestoreArtifacts@delta' => [
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
				'id' => '959ba739-70b5-43c4-8c90-b2c22014f18a',
			],
			[
				'@removed' => [
					'reason' => 'changed',
				],
				'id' => '959ba739-70b5-43c4-8c90-b2c22014f18b',
			],
			[
				'@removed' => [
					'reason' => 'changed',
				],
				'id' => '959ba739-70b5-43c4-8c90-b2c22014f18c',
			],
		],
];
$requestBody->setAdditionalData($additionalData);

$result = $graphServiceClient->solutions()->backupRestore()->sharePointRestoreSessions()->bySharePointRestoreSessionId('sharePointRestoreSession-id')->patch($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.BackupRestore

$params = @{
	"siteRestoreArtifacts@delta" = @(
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
			id = "959ba739-70b5-43c4-8c90-b2c22014f18a"
		}
		@{
			"@removed" = @{
				reason = "changed"
			}
			id = "959ba739-70b5-43c4-8c90-b2c22014f18b"
		}
		@{
			"@removed" = @{
				reason = "changed"
			}
			id = "959ba739-70b5-43c4-8c90-b2c22014f18c"
		}
	)
}

Update-MgSolutionBackupRestoreSharePointRestoreSession -SharePointRestoreSessionId $sharePointRestoreSessionId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.share_point_restore_session import SharePointRestoreSession
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = SharePointRestoreSession(
	additional_data = {
			"site_restore_artifacts@delta" : [
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
						"id" : "959ba739-70b5-43c4-8c90-b2c22014f18a",
				},
				{
						"@removed" : {
								"reason" : "changed",
						},
						"id" : "959ba739-70b5-43c4-8c90-b2c22014f18b",
				},
				{
						"@removed" : {
								"reason" : "changed",
						},
						"id" : "959ba739-70b5-43c4-8c90-b2c22014f18c",
				},
			],
	}
)

result = await graph_client.solutions.backup_restore.share_point_restore_sessions.by_share_point_restore_session_id('sharePointRestoreSession-id').patch(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

```http
HTTP/1.1 200 OK

{
  "siteRestoreArtifacts@delta": [
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
      "id": "99954f18-c8ec-4b62-85bf-cdf3b70b140e",
      "restorePoint": { "id": "7b014d8c-71fe-4d00-a01a-31850bc5b32c" },
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
PATCH https://graph.microsoft.com/v1.0/solutions/backupRestore/sharePointRestoreSessions/01b9d504-a6a4-464b-b2e1-0085d9fab651
Content-Type: application/json

{
  "granularSiteRestoreArtifacts@delta": [
    {
      "browseSessionId": "m_RtZ8BiiUXOK69cuN6gwubfm9_yeVlDg8s6hci01_cVOAE",
      "id": "f3846f8d-80a6-4480-ae20-5966ebdf2009,26380145-c085-4772-b5ef-94de6bc9447e,3be2f282-276a-4a1a-8db0-8bf0849df84d,8d1ba53f-986a-409f-bf90-3bf55dbd7526"
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

var requestBody = new SharePointRestoreSession
{
	AdditionalData = new Dictionary<string, object>
	{
		{
			"granularSiteRestoreArtifacts@delta" , new List<object>
			{
				new UntypedObject(new Dictionary<string, UntypedNode>
				{
					{
						"browseSessionId", new UntypedString("m_RtZ8BiiUXOK69cuN6gwubfm9_yeVlDg8s6hci01_cVOAE")
					},
					{
						"id", new UntypedString("f3846f8d-80a6-4480-ae20-5966ebdf2009,26380145-c085-4772-b5ef-94de6bc9447e,3be2f282-276a-4a1a-8db0-8bf0849df84d,8d1ba53f-986a-409f-bf90-3bf55dbd7526")
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
var result = await graphClient.Solutions.BackupRestore.SharePointRestoreSessions["{sharePointRestoreSession-id}"].PatchAsync(requestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

SharePointRestoreSession sharePointRestoreSession = new SharePointRestoreSession();
HashMap<String, Object> additionalData = new HashMap<String, Object>();
LinkedList<Object> granularSiteRestoreArtifactsDelta = new LinkedList<Object>();
 property = new ();
property.setBrowseSessionId("m_RtZ8BiiUXOK69cuN6gwubfm9_yeVlDg8s6hci01_cVOAE");
property.setId("f3846f8d-80a6-4480-ae20-5966ebdf2009,26380145-c085-4772-b5ef-94de6bc9447e,3be2f282-276a-4a1a-8db0-8bf0849df84d,8d1ba53f-986a-409f-bf90-3bf55dbd7526");
granularSiteRestoreArtifactsDelta.add(property);
 property1 = new ();
 removed = new ();
removed.setReason("changed");
property1.setRemoved(removed);
property1.setId("a535851e-9fc6-4eb1-90ab-2955fd9117b5,2a8b7eaf-092a-4561-a25a-998ad2e5142e,38eec3f1-b879-44a6-8ae6-05bd46ed4b3d,ce66019f-cdf9-4575-aa81-de3aabe844a2");
granularSiteRestoreArtifactsDelta.add(property1);
additionalData.put("granularSiteRestoreArtifacts@delta", granularSiteRestoreArtifactsDelta);
sharePointRestoreSession.setAdditionalData(additionalData);
SharePointRestoreSession result = graphClient.solutions().backupRestore().sharePointRestoreSessions().bySharePointRestoreSessionId("{sharePointRestoreSession-id}").patch(sharePointRestoreSession);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const sharePointRestoreSession = {
  'granularSiteRestoreArtifacts@delta': [
    {
      browseSessionId: 'm_RtZ8BiiUXOK69cuN6gwubfm9_yeVlDg8s6hci01_cVOAE',
      id: 'f3846f8d-80a6-4480-ae20-5966ebdf2009,26380145-c085-4772-b5ef-94de6bc9447e,3be2f282-276a-4a1a-8db0-8bf0849df84d,8d1ba53f-986a-409f-bf90-3bf55dbd7526'
    },
    {
      '@removed': {
        reason: 'changed'
      },
      id: 'a535851e-9fc6-4eb1-90ab-2955fd9117b5,2a8b7eaf-092a-4561-a25a-998ad2e5142e,38eec3f1-b879-44a6-8ae6-05bd46ed4b3d,ce66019f-cdf9-4575-aa81-de3aabe844a2'
    }
  ]
};

await client.api('/solutions/backupRestore/sharePointRestoreSessions/01b9d504-a6a4-464b-b2e1-0085d9fab651')
	.update(sharePointRestoreSession);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\SharePointRestoreSession;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new SharePointRestoreSession();
$additionalData = [
	'granularSiteRestoreArtifacts@delta' => [
			[
				'browseSessionId' => 'm_RtZ8BiiUXOK69cuN6gwubfm9_yeVlDg8s6hci01_cVOAE',
				'id' => 'f3846f8d-80a6-4480-ae20-5966ebdf2009,26380145-c085-4772-b5ef-94de6bc9447e,3be2f282-276a-4a1a-8db0-8bf0849df84d,8d1ba53f-986a-409f-bf90-3bf55dbd7526',
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

$result = $graphServiceClient->solutions()->backupRestore()->sharePointRestoreSessions()->bySharePointRestoreSessionId('sharePointRestoreSession-id')->patch($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.BackupRestore

$params = @{
	"granularSiteRestoreArtifacts@delta" = @(
		@{
			browseSessionId = "m_RtZ8BiiUXOK69cuN6gwubfm9_yeVlDg8s6hci01_cVOAE"
			id = "f3846f8d-80a6-4480-ae20-5966ebdf2009,26380145-c085-4772-b5ef-94de6bc9447e,3be2f282-276a-4a1a-8db0-8bf0849df84d,8d1ba53f-986a-409f-bf90-3bf55dbd7526"
		}
		@{
			"@removed" = @{
				reason = "changed"
			}
			id = "a535851e-9fc6-4eb1-90ab-2955fd9117b5,2a8b7eaf-092a-4561-a25a-998ad2e5142e,38eec3f1-b879-44a6-8ae6-05bd46ed4b3d,ce66019f-cdf9-4575-aa81-de3aabe844a2"
		}
	)
}

Update-MgSolutionBackupRestoreSharePointRestoreSession -SharePointRestoreSessionId $sharePointRestoreSessionId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.share_point_restore_session import SharePointRestoreSession
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = SharePointRestoreSession(
	additional_data = {
			"granular_site_restore_artifacts@delta" : [
				{
						"browse_session_id" : "m_RtZ8BiiUXOK69cuN6gwubfm9_yeVlDg8s6hci01_cVOAE",
						"id" : "f3846f8d-80a6-4480-ae20-5966ebdf2009,26380145-c085-4772-b5ef-94de6bc9447e,3be2f282-276a-4a1a-8db0-8bf0849df84d,8d1ba53f-986a-409f-bf90-3bf55dbd7526",
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

result = await graph_client.solutions.backup_restore.share_point_restore_sessions.by_share_point_restore_session_id('sharePointRestoreSession-id').patch(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "@context": "https://graph.microsoft.com/v1.0/$metadata#solutions/backupRestore/sharePointRestoreSessions/$entity",
  "id": "01b9d504-a6a4-464b-b2e1-0085d9fab651",
  "granularSiteRestoreArtifacts@delta": [
    {
      "siteId": null,
      "id": "f3846f8d-80a6-4480-ae20-5966ebdf2009,26380145-c085-4772-b5ef-94de6bc9447e,3be2f282-276a-4a1a-8db0-8bf0849df84d,8d1ba53f-986a-409f-bf90-3bf55dbd7526",
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
