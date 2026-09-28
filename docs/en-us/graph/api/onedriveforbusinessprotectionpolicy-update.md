<!-- Source: https://learn.microsoft.com/en-us/graph/api/onedriveforbusinessprotectionpolicy-update?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-05-28 -->

# Update oneDriveForBusinessProtectionPolicy

Namespace: microsoft.graph

Update the protection policy for the OneDrive service in Microsoft 365. This method adds a [driveProtectionUnit](https://learn.microsoft.com/en-us/graph/api/resources/driveprotectionunit?view=graph-rest-1.0) to or removes it from a [oneDriveForBusinessProtectionPolicy](https://learn.microsoft.com/en-us/graph/api/resources/onedriveforbusinessprotectionpolicy?view=graph-rest-1.0) object.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | BackupRestore-Configuration.ReadWrite.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | BackupRestore-Configuration.ReadWrite.All | Not available. |

## HTTP request

```http
PATCH /solutions/backupRestore/oneDriveForBusinessProtectionPolicies/{oneDriveForBusinessProtectionPolicyId}
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the **oneDriveForBusinessProtectionPolicy** with the updated properties.

| Property | Type | Description |
| :--- | :--- | :--- |
| displayName | String | Display Name of the [oneDriveForBusinessProtectionPolicy](https://learn.microsoft.com/en-us/graph/api/resources/onedriveforbusinessprotectionpolicy?view=graph-rest-1.0). Optional |
| driveProtectionUnits@delta | Collection\([driveProtectionUnit](https://learn.microsoft.com/en-us/graph/api/resources/driveprotectionunit?view=graph-rest-1.0)\) | Collection of the driveProtectionUnit to be added/removed to the oneDriveForBusinessProtectionPolicy. Required |

To remove a **driveProtectionUnit** from the policy, specify the `@removed` annotation in the request body for the protection unit together with the ID of the [driveProtectionUnit](https://learn.microsoft.com/en-us/graph/api/resources/driveprotectionunit?view=graph-rest-1.0).

## Response

If successful, this method returns a `200 OK` response code and an updated [oneDriveForBusinessProtectionPolicy](https://learn.microsoft.com/en-us/graph/api/resources/onedriveforbusinessprotectionpolicy?view=graph-rest-1.0) in the response body.

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
PATCH https://graph.microsoft.com/v1.0/solutions/backupRestore/oneDriveForBusinessProtectionPolicies/845457dc-4bb2-4815-bef3-8628ebd1952e

{
  "displayName": "One Drive  Policy - Inadvertent data loss",
  "driveProtectionUnits@delta": [
    {
      "directoryObjectId": "1b014d8c-71fe-4d00-a01a-31850bc5b32c"
    },
    {
      "directoryObjectId": "2b014d8c-71fe-4d00-a01a-31850bc5b32c"
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

var requestBody = new OneDriveForBusinessProtectionPolicy
{
	DisplayName = "One Drive  Policy - Inadvertent data loss",
	AdditionalData = new Dictionary<string, object>
	{
		{
			"driveProtectionUnits@delta" , new List<object>
			{
				new UntypedObject(new Dictionary<string, UntypedNode>
				{
					{
						"directoryObjectId", new UntypedString("1b014d8c-71fe-4d00-a01a-31850bc5b32c")
					},
				}),
				new UntypedObject(new Dictionary<string, UntypedNode>
				{
					{
						"directoryObjectId", new UntypedString("2b014d8c-71fe-4d00-a01a-31850bc5b32c")
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
var result = await graphClient.Solutions.BackupRestore.OneDriveForBusinessProtectionPolicies["{oneDriveForBusinessProtectionPolicy-id}"].PatchAsync(requestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

OneDriveForBusinessProtectionPolicy oneDriveForBusinessProtectionPolicy = new OneDriveForBusinessProtectionPolicy();
oneDriveForBusinessProtectionPolicy.setDisplayName("One Drive  Policy - Inadvertent data loss");
HashMap<String, Object> additionalData = new HashMap<String, Object>();
LinkedList<Object> driveProtectionUnitsDelta = new LinkedList<Object>();
 property = new ();
property.setDirectoryObjectId("1b014d8c-71fe-4d00-a01a-31850bc5b32c");
driveProtectionUnitsDelta.add(property);
 property1 = new ();
property1.setDirectoryObjectId("2b014d8c-71fe-4d00-a01a-31850bc5b32c");
driveProtectionUnitsDelta.add(property1);
 property2 = new ();
 removed = new ();
removed.setReason("changed");
property2.setRemoved(removed);
property2.setId("4267e382-71a9-4c07-bef7-bda97e09c0d2");
driveProtectionUnitsDelta.add(property2);
 property3 = new ();
 removed1 = new ();
removed1.setReason("changed");
property3.setRemoved(removed1);
property3.setId("3667e382-71a9-4c07-bef7-bda97e09c0d2");
driveProtectionUnitsDelta.add(property3);
additionalData.put("driveProtectionUnits@delta", driveProtectionUnitsDelta);
oneDriveForBusinessProtectionPolicy.setAdditionalData(additionalData);
OneDriveForBusinessProtectionPolicy result = graphClient.solutions().backupRestore().oneDriveForBusinessProtectionPolicies().byOneDriveForBusinessProtectionPolicyId("{oneDriveForBusinessProtectionPolicy-id}").patch(oneDriveForBusinessProtectionPolicy);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const oneDriveForBusinessProtectionPolicy = {
  displayName: 'One Drive  Policy - Inadvertent data loss',
  'driveProtectionUnits@delta': [
    {
      directoryObjectId: '1b014d8c-71fe-4d00-a01a-31850bc5b32c'
    },
    {
      directoryObjectId: '2b014d8c-71fe-4d00-a01a-31850bc5b32c'
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

await client.api('/solutions/backupRestore/oneDriveForBusinessProtectionPolicies/845457dc-4bb2-4815-bef3-8628ebd1952e')
	.update(oneDriveForBusinessProtectionPolicy);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\OneDriveForBusinessProtectionPolicy;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new OneDriveForBusinessProtectionPolicy();
$requestBody->setDisplayName('One Drive  Policy - Inadvertent data loss');
$additionalData = [
	'driveProtectionUnits@delta' => [
			[
				'directoryObjectId' => '1b014d8c-71fe-4d00-a01a-31850bc5b32c',
			],
			[
				'directoryObjectId' => '2b014d8c-71fe-4d00-a01a-31850bc5b32c',
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

$result = $graphServiceClient->solutions()->backupRestore()->oneDriveForBusinessProtectionPolicies()->byOneDriveForBusinessProtectionPolicyId('oneDriveForBusinessProtectionPolicy-id')->patch($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.BackupRestore

$params = @{
	displayName = "One Drive  Policy - Inadvertent data loss"
	"driveProtectionUnits@delta" = @(
		@{
			directoryObjectId = "1b014d8c-71fe-4d00-a01a-31850bc5b32c"
		}
		@{
			directoryObjectId = "2b014d8c-71fe-4d00-a01a-31850bc5b32c"
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

Update-MgSolutionBackupRestoreOneDriveForBusinessProtectionPolicy -OneDriveForBusinessProtectionPolicyId $oneDriveForBusinessProtectionPolicyId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.one_drive_for_business_protection_policy import OneDriveForBusinessProtectionPolicy
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = OneDriveForBusinessProtectionPolicy(
	display_name = "One Drive  Policy - Inadvertent data loss",
	additional_data = {
			"drive_protection_units@delta" : [
				{
						"directory_object_id" : "1b014d8c-71fe-4d00-a01a-31850bc5b32c",
				},
				{
						"directory_object_id" : "2b014d8c-71fe-4d00-a01a-31850bc5b32c",
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

result = await graph_client.solutions.backup_restore.one_drive_for_business_protection_policies.by_one_drive_for_business_protection_policy_id('oneDriveForBusinessProtectionPolicy-id').patch(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK

{
  "displayName": "OneDrive Policy - Inadvertent data loss",
  "driveProtectionUnits@delta": [
    {
      "id": "89014d8c-71fe-4d00-a01a-31850bc5b32c",
      "policyId": "845457dc-4bb2-4815-bef3-8628ebd1952e",
      "directoryObjectId": "1b014d8c-71fe-4d00-a01a-31850bc5b32c",
      "status": "protectRequested",
      "createdBy": {
        "application": {
          "id": "1fec8e78-bce4-4aaf-ab1b-5451cc387264",
          "displayName": "Microsoft Enhanced Restore"
        },
        "user": {
          "email": "User1@contoso.com",
          "id": "845457dc-4bb2-4815-bef3-8628ebd1952e",
          "displayName": "User1"
        }
      },
      "createdDateTime": "2015-06-19T12:01:03.45Z",
      "lastModifiedBy": {
        "application": {
          "id": "1fec8e78-bce4-4aaf-ab1b-5451cc387264",
          "displayName": "Microsoft Enhanced Restore"
        },
        "user": {
          "email": "User1@contoso.com",
          "id": "845457dc-4bb2-4815-bef3-8628ebd1952e",
          "displayName": "User1"
        }
      },
      "lastModifiedDateTime": "2015-06-19T12:01:03.45Z"
    },
    {
      "id": "67014d8c-71fe-4d00-a01a-31850bc5b32c",
      "directoryObjectId": "2b014d8c-71fe-4d00-a01a-31850bc5b32c",
      "policyId": "845457dc-4bb2-4815-bef3-8628ebd1952e",
      "status": "protectRequested",
      "createdBy": {
        "application": {
          "id": "1fec8e78-bce4-4aaf-ab1b-5451cc387264",
          "displayName": "Microsoft Enhanced Restore"
        },
        "user": {
          "email": "User1@contoso.com",
          "id": "845457dc-4bb2-4815-bef3-8628ebd1952e",
          "displayName": "User1"
        }
      },
      "createdDateTime": "2015-06-19T12:01:03.45Z",
      "lastModifiedBy": {
        "application": {
          "id": "1fec8e78-bce4-4aaf-ab1b-5451cc387264",
          "displayName": "Microsoft Enhanced Restore"
        },
        "user": {
          "email": "User1@contoso.com",
          "id": "845457dc-4bb2-4815-bef3-8628ebd1952e",
          "displayName": "User1"
        }
      },
      "lastModifiedDateTime": "2015-06-19T12:01:03.45Z"
    },
    {
      //Error scenario
      "@contentId": "3467e382-71a9-4c07-bef7-bda97e09c0d2", // To add context and more traceability.
      "@Core.DataModificationException": {
        "info": {
          "code": "Invalid",
          "message": "The identifier to be removed from the Protection Policy does not exist"
        },
        "failedOperation": "remove",
        "responseCode": 409
      },
      "id": "4267e382-71a9-4c07-bef7-bda97e09c0d2"
    },
    {
      "id": "3667e382-71a9-4c07-bef7-bda97e09c0d2",
      "directoryObjectId": "5767e382-71a9-4c07-bef7-bda97e09c0d2",
      "policyId": "845457dc-4bb2-4815-bef3-8628ebd1952e",
      "status": "removeRequested",
      "createdBy": {
        "application": {
          "id": "1fec8e78-bce4-4aaf-ab1b-5451cc387264",
          "displayName": "Microsoft Enhanced Restore"
        },
        "user": {
          "email": "User1@contoso.com",
          "id": "845457dc-4bb2-4815-bef3-8628ebd1952e",
          "displayName": "User1"
        }
      },
      "createdDateTime": "2015-06-19T12:01:03.45Z",
      "lastModifiedBy": {
        "application": {
          "id": "1fec8e78-bce4-4aaf-ab1b-5451cc387264",
          "displayName": "Microsoft Enhanced Restore"
        },
        "user": {
          "email": "User1@contoso.com",
          "id": "845457dc-4bb2-4815-bef3-8628ebd1952e",
          "displayName": "User1"
        }
      },
      "lastModifiedDateTime": "2015-06-19T12:01:03.45Z"
    }
  ]
}
```
