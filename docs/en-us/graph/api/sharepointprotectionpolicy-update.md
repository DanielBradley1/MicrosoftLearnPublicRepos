<!-- Source: https://learn.microsoft.com/en-us/graph/api/sharepointprotectionpolicy-update?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-05-28 -->

# Update sharePointProtectionPolicy

Namespace: microsoft.graph

Update a [SharePoint protection policy](https://learn.microsoft.com/en-us/graph/api/resources/sharepointprotectionpolicy?view=graph-rest-1.0). This method adds a [siteprotectionunit](https://learn.microsoft.com/en-us/graph/api/resources/siteprotectionunit?view=graph-rest-1.0) to or removes it from the protection policy.

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
PATCH /solutions/backupRestore/sharePointProtectionPolicies/{sharePointProtectionPolicyId}
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, provide a JSON representation of following properties to update **sharePointProtectionPolicy** object.

| Property | Type | Description |
| :--- | :--- | :--- |
| displayName | String | Display Name of the [sharePointProtectionPolicy](https://learn.microsoft.com/en-us/graph/api/resources/sharepointprotectionpolicy?view=graph-rest-1.0). Optional |
| siteProtectionUnits@delta | Collection\([siteProtectionUnit](https://learn.microsoft.com/en-us/graph/api/resources/siteprotectionunit?view=graph-rest-1.0)\) | Collection of siteProtectionUnit objects to be added to or removed from the [sharePointProtectionPolicy](https://learn.microsoft.com/en-us/graph/api/resources/sharepointprotectionpolicy?view=graph-rest-1.0). Required. |

To remove a **siteProtectionUnit** from the policy, specify the `@removed` annotation in the request body for the protection unit together with the ID of the [siteProtectionUnit](https://learn.microsoft.com/en-us/graph/api/resources/siteprotectionunit?view=graph-rest-1.0).

## Response

If successful, this method returns a `200 OK` response code and an updated [sharePointProtectionPolicy](https://learn.microsoft.com/en-us/graph/api/resources/sharepointprotectionpolicy?view=graph-rest-1.0) in the response body.

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
PATCH https://graph.microsoft.com/v1.0/solutions/backupRestore/sharePointProtectionPolicies/845457dc-4bb2-4815-bef3-8628ebd1952e
Content-Type: application/json

{
  "displayName": "SharePoint Policy - Inadvertent data loss",
  "siteProtectionUnits@delta": [
    {
      "siteId": "contoso.sharepoint.com,bf6fb551-d508-4946-a439-b2a6154fc1d9,65a04b8b-1f44-442b-a1fc-9e5852fb946c" //Create a new siteProtectionUnit.
    },
    {
      "siteId": "contoso.sharepoint.com,d9ecf079-9b13-4376-ac5d-f242dda55626,746dbcc1-fa2b-4120-b657-2670bae5bb6f"
    },
    {
      "siteId": "contoso.sharepoint.com,fd1a778f-263e-4c43-acdf-d5c2519d80eb,c06016db-dfec-4f79-83a1-09c6dbfd7022"
    },
    {
      "siteId": "contoso.sharepoint.com,bf6fb551-d508-4946-a439-b2a6154fc1d9,65a04b8b-1f44-442b-a1fc-9e5852fb946c"
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

var requestBody = new SharePointProtectionPolicy
{
	DisplayName = "SharePoint Policy - Inadvertent data loss",
	AdditionalData = new Dictionary<string, object>
	{
		{
			"siteProtectionUnits@delta" , new List<object>
			{
				new UntypedObject(new Dictionary<string, UntypedNode>
				{
					{
						"siteId", new UntypedString("contoso.sharepoint.com,bf6fb551-d508-4946-a439-b2a6154fc1d9,65a04b8b-1f44-442b-a1fc-9e5852fb946c")
					},
				}),
				new UntypedObject(new Dictionary<string, UntypedNode>
				{
					{
						"siteId", new UntypedString("contoso.sharepoint.com,d9ecf079-9b13-4376-ac5d-f242dda55626,746dbcc1-fa2b-4120-b657-2670bae5bb6f")
					},
				}),
				new UntypedObject(new Dictionary<string, UntypedNode>
				{
					{
						"siteId", new UntypedString("contoso.sharepoint.com,fd1a778f-263e-4c43-acdf-d5c2519d80eb,c06016db-dfec-4f79-83a1-09c6dbfd7022")
					},
				}),
				new UntypedObject(new Dictionary<string, UntypedNode>
				{
					{
						"siteId", new UntypedString("contoso.sharepoint.com,bf6fb551-d508-4946-a439-b2a6154fc1d9,65a04b8b-1f44-442b-a1fc-9e5852fb946c")
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
var result = await graphClient.Solutions.BackupRestore.SharePointProtectionPolicies["{sharePointProtectionPolicy-id}"].PatchAsync(requestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

SharePointProtectionPolicy sharePointProtectionPolicy = new SharePointProtectionPolicy();
sharePointProtectionPolicy.setDisplayName("SharePoint Policy - Inadvertent data loss");
HashMap<String, Object> additionalData = new HashMap<String, Object>();
LinkedList<Object> siteProtectionUnitsDelta = new LinkedList<Object>();
 property = new ();
property.setSiteId("contoso.sharepoint.com,bf6fb551-d508-4946-a439-b2a6154fc1d9,65a04b8b-1f44-442b-a1fc-9e5852fb946c");
siteProtectionUnitsDelta.add(property);
 property1 = new ();
property1.setSiteId("contoso.sharepoint.com,d9ecf079-9b13-4376-ac5d-f242dda55626,746dbcc1-fa2b-4120-b657-2670bae5bb6f");
siteProtectionUnitsDelta.add(property1);
 property2 = new ();
property2.setSiteId("contoso.sharepoint.com,fd1a778f-263e-4c43-acdf-d5c2519d80eb,c06016db-dfec-4f79-83a1-09c6dbfd7022");
siteProtectionUnitsDelta.add(property2);
 property3 = new ();
property3.setSiteId("contoso.sharepoint.com,bf6fb551-d508-4946-a439-b2a6154fc1d9,65a04b8b-1f44-442b-a1fc-9e5852fb946c");
siteProtectionUnitsDelta.add(property3);
 property4 = new ();
 removed = new ();
removed.setReason("changed");
property4.setRemoved(removed);
property4.setId("99954f18-c8ec-4b62-85bf-cdf3b70b140e");
siteProtectionUnitsDelta.add(property4);
 property5 = new ();
 removed1 = new ();
removed1.setReason("changed");
property5.setRemoved(removed1);
property5.setId("4267e382-71a9-4c07-bef7-bda97e09c0d2");
siteProtectionUnitsDelta.add(property5);
 property6 = new ();
 removed2 = new ();
removed2.setReason("changed");
property6.setRemoved(removed2);
property6.setId("3667e382-71a9-4c07-bef7-bda97e09c0d2");
siteProtectionUnitsDelta.add(property6);
additionalData.put("siteProtectionUnits@delta", siteProtectionUnitsDelta);
sharePointProtectionPolicy.setAdditionalData(additionalData);
SharePointProtectionPolicy result = graphClient.solutions().backupRestore().sharePointProtectionPolicies().bySharePointProtectionPolicyId("{sharePointProtectionPolicy-id}").patch(sharePointProtectionPolicy);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const sharePointProtectionPolicy = {
  displayName: 'SharePoint Policy - Inadvertent data loss',
  'siteProtectionUnits@delta': [
    {
      siteId: 'contoso.sharepoint.com,bf6fb551-d508-4946-a439-b2a6154fc1d9,65a04b8b-1f44-442b-a1fc-9e5852fb946c' //Create a new siteProtectionUnit.
    },
    {
      siteId: 'contoso.sharepoint.com,d9ecf079-9b13-4376-ac5d-f242dda55626,746dbcc1-fa2b-4120-b657-2670bae5bb6f'
    },
    {
      siteId: 'contoso.sharepoint.com,fd1a778f-263e-4c43-acdf-d5c2519d80eb,c06016db-dfec-4f79-83a1-09c6dbfd7022'
    },
    {
      siteId: 'contoso.sharepoint.com,bf6fb551-d508-4946-a439-b2a6154fc1d9,65a04b8b-1f44-442b-a1fc-9e5852fb946c'
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

await client.api('/solutions/backupRestore/sharePointProtectionPolicies/845457dc-4bb2-4815-bef3-8628ebd1952e')
	.update(sharePointProtectionPolicy);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\SharePointProtectionPolicy;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new SharePointProtectionPolicy();
$requestBody->setDisplayName('SharePoint Policy - Inadvertent data loss');
$additionalData = [
	'siteProtectionUnits@delta' => [
			[
				'siteId' => 'contoso.sharepoint.com,bf6fb551-d508-4946-a439-b2a6154fc1d9,65a04b8b-1f44-442b-a1fc-9e5852fb946c',
			],
			[
				'siteId' => 'contoso.sharepoint.com,d9ecf079-9b13-4376-ac5d-f242dda55626,746dbcc1-fa2b-4120-b657-2670bae5bb6f',
			],
			[
				'siteId' => 'contoso.sharepoint.com,fd1a778f-263e-4c43-acdf-d5c2519d80eb,c06016db-dfec-4f79-83a1-09c6dbfd7022',
			],
			[
				'siteId' => 'contoso.sharepoint.com,bf6fb551-d508-4946-a439-b2a6154fc1d9,65a04b8b-1f44-442b-a1fc-9e5852fb946c',
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

$result = $graphServiceClient->solutions()->backupRestore()->sharePointProtectionPolicies()->bySharePointProtectionPolicyId('sharePointProtectionPolicy-id')->patch($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.BackupRestore

$params = @{
	displayName = "SharePoint Policy - Inadvertent data loss"
	"siteProtectionUnits@delta" = @(
		@{
			siteId = "contoso.sharepoint.com,bf6fb551-d508-4946-a439-b2a6154fc1d9,65a04b8b-1f44-442b-a1fc-9e5852fb946c"
		}
		@{
			siteId = "contoso.sharepoint.com,d9ecf079-9b13-4376-ac5d-f242dda55626,746dbcc1-fa2b-4120-b657-2670bae5bb6f"
		}
		@{
			siteId = "contoso.sharepoint.com,fd1a778f-263e-4c43-acdf-d5c2519d80eb,c06016db-dfec-4f79-83a1-09c6dbfd7022"
		}
		@{
			siteId = "contoso.sharepoint.com,bf6fb551-d508-4946-a439-b2a6154fc1d9,65a04b8b-1f44-442b-a1fc-9e5852fb946c"
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

Update-MgSolutionBackupRestoreSharePointProtectionPolicy -SharePointProtectionPolicyId $sharePointProtectionPolicyId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.share_point_protection_policy import SharePointProtectionPolicy
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = SharePointProtectionPolicy(
	display_name = "SharePoint Policy - Inadvertent data loss",
	additional_data = {
			"site_protection_units@delta" : [
				{
						"site_id" : "contoso.sharepoint.com,bf6fb551-d508-4946-a439-b2a6154fc1d9,65a04b8b-1f44-442b-a1fc-9e5852fb946c",
				},
				{
						"site_id" : "contoso.sharepoint.com,d9ecf079-9b13-4376-ac5d-f242dda55626,746dbcc1-fa2b-4120-b657-2670bae5bb6f",
				},
				{
						"site_id" : "contoso.sharepoint.com,fd1a778f-263e-4c43-acdf-d5c2519d80eb,c06016db-dfec-4f79-83a1-09c6dbfd7022",
				},
				{
						"site_id" : "contoso.sharepoint.com,bf6fb551-d508-4946-a439-b2a6154fc1d9,65a04b8b-1f44-442b-a1fc-9e5852fb946c",
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

result = await graph_client.solutions.backup_restore.share_point_protection_policies.by_share_point_protection_policy_id('sharePointProtectionPolicy-id').patch(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

```http
HTTP/1.1 200 OK

{
  "displayName": "SharePoint Policy - Inadvertent data loss",
  "siteProtectionUnits@delta": [
    {
      "id": "89014d8c-71fe-4d00-a01a-31850bc5b32c",
      "siteId": "contoso.sharepoint.com,d9ecf079-9b13-4376-ac5d-f242dda55626,746dbcc1-fa2b-4120-b657-2670bae5bb6f",
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
      "lastModifiedDateTime": "2015-06-19T12:01:03.45Z",
      "error": null
    },
    {
      "id": "67014d8c-71fe-4d00-a01a-31850bc5b32c",
      "siteId": "contoso.sharepoint.com,fd1a778f-263e-4c43-acdf-d5c2519d80eb,c06016db-dfec-4f79-83a1-09c6dbfd7022",
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
      "lastModifiedDateTime": "2015-06-19T12:01:03.45Z",
      "error": null
    },
    {
      "id": "56014d8c-71fe-4d00-a01a-31850bc5b32c",
      "siteId": "contoso.sharepoint.com,bf6fb551-d508-4946-a439-b2a6154fc1d9,65a04b8b-1f44-442b-a1fc-98356ccfas5y",
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
      "lastModifiedDateTime": "2015-06-19T12:01:03.45Z",
      "error": null
    },
    {
      "id": "32014d8c-71fe-4d00-a01a-31850bc5b32c",
      "siteId": "contoso.sharepoint.com,bf6fb551-d508-4946-a439-b2a6154fc1d9,65a04b8b-1f44-442b-a1fc-9e5852fb8970",
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
      "lastModifiedDateTime": "2015-06-19T12:01:03.45Z",
      "error": null
    },
    {
      "policyId": "845457dc-4bb2-4815-bef3-8628ebd1952e",
      "id": "99954f18-c8ec-4b62-85bf-cdf3b70b140e",
      "siteId": "contoso.sharepoint.com,bf6fb551-d508-4946-a439-b2a6154fc1d9,65a04b8b-1f44-442b-a1fc-9e5852fbrtys",
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
      "lastModifiedDateTime": "2015-06-19T12:01:03.45Z",
      "error": null
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
      "policyId": "845457dc-4bb2-4815-bef3-8628ebd1952e",
      "siteId": "contoso.sharepoint.com,bf6fb551-d508-4946-a439-b2a6154fc1d9,65a04b8b-1f44-442b-a1fc-9e5852fb123c",
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
      "lastModifiedDateTime": "2015-06-19T12:01:03.45Z",
      "error": null
    }
  ]
}
```
