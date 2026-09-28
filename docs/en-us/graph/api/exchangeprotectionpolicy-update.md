<!-- Source: https://learn.microsoft.com/en-us/graph/api/exchangeprotectionpolicy-update?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-05-28 -->

# Update exchangeProtectionPolicy

Namespace: microsoft.graph

Update an [Exchange protection policy](https://learn.microsoft.com/en-us/graph/api/resources/exchangeprotectionpolicy?view=graph-rest-1.0). This method adds a [mailboxprotectionunit](https://learn.microsoft.com/en-us/graph/api/resources/mailboxprotectionunit?view=graph-rest-1.0) to or removes it from the protection policy.

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
PATCH /solutions/backupRestore/exchangeProtectionPolicies/{exchangeProtectionPolicyId}
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

In the request body, provide a JSON representation of the following properties to update the **exchangeProtectionPolicy** object.

| Property | Type | Description |
| :--- | :--- | :--- |
| displayName | String | Display Name of the [exchangeProtectionPolicy](https://learn.microsoft.com/en-us/graph/api/resources/exchangeprotectionpolicy?view=graph-rest-1.0). Optional. |
| mailboxProtectionUnits@delta | Collection\([mailboxProtectionUnit](https://learn.microsoft.com/en-us/graph/api/resources/mailboxprotectionunit?view=graph-rest-1.0)\) | Collection of **mailboxProtectionUnit** objects to be added to or removed from the Exchange protection policy. Required. |

To remove a **mailboxProtectionUnit** from the policy, specify the `@removed` annotation in the request body for the protection unit together with the ID of the [mailboxProtectionUnit](https://learn.microsoft.com/en-us/graph/api/resources/mailboxprotectionunit?view=graph-rest-1.0).

## Response

If successful, this method returns a `200 OK` response code and an updated [exchangeProtectionPolicy](https://learn.microsoft.com/en-us/graph/api/resources/exchangeprotectionpolicy?view=graph-rest-1.0) object in the response body.

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
PATCH https://graph.microsoft.com/v1.0/solutions/backupRestore/exchangeProtectionPolicies/845457dc-4bb2-4815-bef3-8628ebd1952e
Authorization: Bearer <Access-Token>

{
  "displayName": "Exchange Policy - Inadvertent data loss",
  "mailboxProtectionUnits@delta": [
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
      "id": "99954f18-c8ec-4b62-85bf-cdf3b70b140e"
    },
    {
      "@removed": {
        "reason": "changed"
      },
      "id": "4267e382-71a9-4c07-bef7-bda97e09c0d2"
    }
  ]
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;
using Microsoft.Kiota.Abstractions.Serialization;

var requestBody = new ExchangeProtectionPolicy
{
	DisplayName = "Exchange Policy - Inadvertent data loss",
	AdditionalData = new Dictionary<string, object>
	{
		{
			"mailboxProtectionUnits@delta" , new List<object>
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
			}
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Solutions.BackupRestore.ExchangeProtectionPolicies["{exchangeProtectionPolicy-id}"].PatchAsync(requestBody, (requestConfiguration) =>
{
	requestConfiguration.Headers.Add("Authorization", "Bearer <Access-Token>");
});
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

ExchangeProtectionPolicy exchangeProtectionPolicy = new ExchangeProtectionPolicy();
exchangeProtectionPolicy.setDisplayName("Exchange Policy - Inadvertent data loss");
HashMap<String, Object> additionalData = new HashMap<String, Object>();
LinkedList<Object> mailboxProtectionUnitsDelta = new LinkedList<Object>();
 property = new ();
property.setDirectoryObjectId("1b014d8c-71fe-4d00-a01a-31850bc5b32c");
mailboxProtectionUnitsDelta.add(property);
 property1 = new ();
property1.setDirectoryObjectId("2b014d8c-71fe-4d00-a01a-31850bc5b32c");
mailboxProtectionUnitsDelta.add(property1);
 property2 = new ();
 removed = new ();
removed.setReason("changed");
property2.setRemoved(removed);
property2.setId("99954f18-c8ec-4b62-85bf-cdf3b70b140e");
mailboxProtectionUnitsDelta.add(property2);
 property3 = new ();
 removed1 = new ();
removed1.setReason("changed");
property3.setRemoved(removed1);
property3.setId("4267e382-71a9-4c07-bef7-bda97e09c0d2");
mailboxProtectionUnitsDelta.add(property3);
additionalData.put("mailboxProtectionUnits@delta", mailboxProtectionUnitsDelta);
exchangeProtectionPolicy.setAdditionalData(additionalData);
ExchangeProtectionPolicy result = graphClient.solutions().backupRestore().exchangeProtectionPolicies().byExchangeProtectionPolicyId("{exchangeProtectionPolicy-id}").patch(exchangeProtectionPolicy, requestConfiguration -> {
	requestConfiguration.headers.add("Authorization", "Bearer <Access-Token>");
});
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const exchangeProtectionPolicy = {
  displayName: 'Exchange Policy - Inadvertent data loss',
  'mailboxProtectionUnits@delta': [
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
      id: '99954f18-c8ec-4b62-85bf-cdf3b70b140e'
    },
    {
      '@removed': {
        reason: 'changed'
      },
      id: '4267e382-71a9-4c07-bef7-bda97e09c0d2'
    }
  ]
};

await client.api('/solutions/backupRestore/exchangeProtectionPolicies/845457dc-4bb2-4815-bef3-8628ebd1952e')
	.update(exchangeProtectionPolicy);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Solutions\BackupRestore\ExchangeProtectionPolicies\Item\ExchangeProtectionPolicyItemRequestBuilderPatchRequestConfiguration;
use Microsoft\Graph\Generated\Models\ExchangeProtectionPolicy;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new ExchangeProtectionPolicy();
$requestBody->setDisplayName('Exchange Policy - Inadvertent data loss');
$additionalData = [
	'mailboxProtectionUnits@delta' => [
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
				'id' => '99954f18-c8ec-4b62-85bf-cdf3b70b140e',
			],
			[
				'@removed' => [
					'reason' => 'changed',
				],
				'id' => '4267e382-71a9-4c07-bef7-bda97e09c0d2',
			],
		],
];
$requestBody->setAdditionalData($additionalData);
$requestConfiguration = new ExchangeProtectionPolicyItemRequestBuilderPatchRequestConfiguration();
$headers = [
		'Authorization' => 'Bearer <Access-Token>',
	];
$requestConfiguration->headers = $headers;


$result = $graphServiceClient->solutions()->backupRestore()->exchangeProtectionPolicies()->byExchangeProtectionPolicyId('exchangeProtectionPolicy-id')->patch($requestBody, $requestConfiguration)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.BackupRestore

$params = @{
	displayName = "Exchange Policy - Inadvertent data loss"
	"mailboxProtectionUnits@delta" = @(
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
			id = "99954f18-c8ec-4b62-85bf-cdf3b70b140e"
		}
		@{
			"@removed" = @{
				reason = "changed"
			}
			id = "4267e382-71a9-4c07-bef7-bda97e09c0d2"
		}
	)
}

Update-MgSolutionBackupRestoreExchangeProtectionPolicy -ExchangeProtectionPolicyId $exchangeProtectionPolicyId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.solutions.backup_restore.exchange_protection_policies.item.exchange_protection_policy_item_request_builder import ExchangeProtectionPolicyItemRequestBuilder
from kiota_abstractions.base_request_configuration import RequestConfiguration
from msgraph.generated.models.exchange_protection_policy import ExchangeProtectionPolicy
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = ExchangeProtectionPolicy(
	display_name = "Exchange Policy - Inadvertent data loss",
	additional_data = {
			"mailbox_protection_units@delta" : [
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
						"id" : "99954f18-c8ec-4b62-85bf-cdf3b70b140e",
				},
				{
						"@removed" : {
								"reason" : "changed",
						},
						"id" : "4267e382-71a9-4c07-bef7-bda97e09c0d2",
				},
			],
	}
)

request_configuration = RequestConfiguration()
request_configuration.headers.add("Authorization", "Bearer <Access-Token>")


result = await graph_client.solutions.backup_restore.exchange_protection_policies.by_exchange_protection_policy_id('exchangeProtectionPolicy-id').patch(request_body, request_configuration = request_configuration)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK

{
  "displayName": "Exchange Policy - Inadvertent data loss",
  "mailboxProtectionUnits@delta": [
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
      "id": "99954f18-c8ec-4b62-85bf-cdf3b70b140e",
      "directoryObjectId": "7b014d8c-71fe-4d00-a01a-31850bc5b32c",
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
    }
  ]
}
```
