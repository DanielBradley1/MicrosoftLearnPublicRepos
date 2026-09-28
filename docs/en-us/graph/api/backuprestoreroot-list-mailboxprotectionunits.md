<!-- Source: https://learn.microsoft.com/en-us/graph/api/backuprestoreroot-list-mailboxprotectionunits?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-23 -->

# List mailboxProtectionUnits

Namespace: microsoft.graph

Get a list of [mailboxProtectionUnit](https://learn.microsoft.com/en-us/graph/api/resources/mailboxprotectionunit?view=graph-rest-1.0) objects.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | BackupRestore-Configuration.Read.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | BackupRestore-Configuration.Read.All | Not available. |

## HTTP request

```http
GET /solutions/backupRestore/protectionUnits/microsoft.graph.mailboxProtectionUnit
GET /solutions/backupRestore/exchangeProtectionPolicies/{exchangeProtectionPolicyId}/mailboxProtectionUnits/
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and a [mailboxProtectionUnit](https://learn.microsoft.com/en-us/graph/api/resources/mailboxprotectionunit?view=graph-rest-1.0) in the response body.

For a list of possible error responses, see [Backup Storage API error responses](https://learn.microsoft.com/en-us/graph/backup-storage-error-codes).

Note

The `displayName` and `email` properties are only available for the `Delegated` permission type.

## Examples

### Example 1: List all mailboxProtectionUnits in a tenant

#### Request

The following example shows a request.

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [PowerShell](#tabpanel_1_powershell)
- [Python](#tabpanel_1_python)

```msgraph
GET https://graph.microsoft.com/v1.0/solutions/backupRestore/protectionUnits/microsoft.graph.mailboxProtectionUnit
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Solutions.BackupRestore.ProtectionUnits.GraphMailboxProtectionUnit.GetAsync();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  //other-imports
)


// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
graphMailboxProtectionUnit, err := graphClient.Solutions().BackupRestore().ProtectionUnits().GraphMailboxProtectionUnit().Get(context.Background(), nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

MailboxProtectionUnitCollectionResponse result = graphClient.solutions().backupRestore().protectionUnits().graphMailboxProtectionUnit().get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let mailboxProtectionUnit = await client.api('/solutions/backupRestore/protectionUnits/microsoft.graph.mailboxProtectionUnit')
	.get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);


$result = $graphServiceClient->solutions()->backupRestore()->protectionUnits()->graphMailboxProtectionUnit()->get()->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.BackupRestore

Get-MgSolutionBackupRestoreProtectionUnitAsMailboxProtectionUnit
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python

result = await graph_client.solutions.backup_restore.protection_units.graph_mailbox_protection_unit.get()
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

```http
HTTP/1.1 200 OK

{
  "@odata.nextLink": "https://graph.microsoft.com/v1.0/solutions/backupRestore/protectionUnits/microsoft.graph.mailboxProtectionUnit?$skiptoken=M2UyZDAwMDAwMDMxMzkzYTMyNjQ2MTM0NjMzMjM5NjYzNjY0MzczMDM0MzE2NTYzNjEzNzMwNjIzNjMzMzg2MjM0MzM2NDM0MzUzNDMzMzc0MDc0Njg3MjY1NjE2NDJlNzYzMjAxZThmYjY4M2Y3ODAxMDAwMDg4NjA5ODdhNzgwMTAwMDB8MTYxNjk2NDUwOTgzMg%3d%3d",
  "value": [
    {
      "@odata.type": "#microsoft.graph.mailboxProtectionUnit",
      "id": "2b014d8c-71fe-4d00-a01a-31850bc5b32c",
      "policyId": "9fec8e78-bce4-4aaf-ab1b-5451cc387264",
      "directoryObjectId": "384974e2-72cd-48de-a6e8-6985d7c5db90",
      "displayName": "Emily Braun", // Newly Added
      "email": "emilyb@contoso.com", // Newly Added
      "status": "unprotectRequested",
      "protectionSources": "none",
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
      "error": null,
      "offboardRequestedDateTime": "0001-01-01T00:00:00.0000000Z"
    },
    {
      "@odata.type": "#microsoft.graph.mailboxProtectionUnit",
      "id": "8f014d8c-71fe-4d00-a01a-31850bc5b32c",
      "policyId": "9fec8e78-bce4-4aaf-ab1b-5451cc387264",
      "directoryObjectId": "781d9337-d8f0-456e-92cd-00a3abdd2093",
      "displayName": "Alex Wilber", // Newly Added
      "email": "alexw@contoso.com", // Newly Added
      "status": "unprotected",
      "protectionSources": "none",
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
      "error": null,
      "offboardRequestedDateTime": "0001-01-01T00:00:00.0000000Z"
    },
    {
      "@odata.type": "#microsoft.graph.mailboxProtectionUnit",
      "id": "9b014d8c-71fe-4d00-a01a-31850bc5b32c",
      "policyId": "9fec8e78-bce4-4aaf-ab1b-5451cc387264",
      "directoryObjectId": "2d1d9337-d8f0-456e-92cd-00a3abdd2093",
      "displayName": "Shaun Wong", // Newly Added
      "email": "shaunw@contoso.com", // Newly Added
      "status": "protectRequested",
      "protectionSources": "manual",
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
      "error": null,
      "offboardRequestedDateTime": "0001-01-01T00:00:00.0000000Z"
    },
    {
      "@odata.type": "#microsoft.graph.mailboxProtectionUnit",
      "id": "9b014d8c-71fe-4d00-a01a-31850bc5b32c",
      "policyId": "9fec8e78-bce4-4aaf-ab1b-5451cc387264",
      "directoryObjectId": "2e1d9337-d8f0-456e-92cd-00a3abdd2093",
      "displayName": "Janet Green", // Newly Added
      "email": "janetg@contoso.com", // Newly Added
      "status": "protected",
      "protectionSources": "dynamicRule",
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
      "error": null,
      "offboardRequestedDateTime": "0001-01-01T00:00:00.0000000Z"
    },
    {
      "@odata.type": "#microsoft.graph.mailboxProtectionUnit",
      "id": "9b014d8c-71fe-4d00-a01a-31850bc5b32c",
      "directoryObjectId": "2w1d9337-d8f0-456e-92cd-00a3abdd2093",
      "displayName": "Eddie Brock ", // Newly Added
      "email": "eddyb@contoso.com", // Newly Added
      "status": "unprotected",
      "protectionSources": "none",
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
      "error": null,
      "offboardRequestedDateTime": "0001-01-01T00:00:00.0000000Z"
    }
  ]
}
```

### Example 2: List all mailboxProtecionUnits under an exchangeProtectionPolicy

#### Request

The following example shows a request.

```http
GET https://graph.microsoft.com/v1.0/solutions/solutions/backupRestore/exchangeProtectionPolicies/845457dc-4bb2-4815-bef3-8628ebd1952e/mailboxProtectionUnits
```

#### Response

The following example shows the response.

```http
HTTP/1.1 200 OK

{
  "@odata.nextLink": "https://graph.microsoft.com/v1.0/solutions/backupRestore/exchangeProtectionPolicies/845457dc-4bb2-4815-bef3-8628ebd1952e/mailboxProtectionUnits?$skiptoken=M2UyZDAwMDAwMDMxMzkzYTMyNjQ2MTM0NjMzMjM5NjYzNjY0MzczMDM0MzE2NTYzNjEzNzMwNjIzNjMzMzg2MjM0MzM2NDM0MzUzNDMzMzc0MDc0Njg3MjY1NjE2NDJlNzYzMjAxZThmYjY4M2Y3ODAxMDAwMDg4NjA5ODdhNzgwMTAwMDB8MTYxNjk2NDUwOTgzMg%3d%3d",
  "value": [
    {
      "@odata.type": "#microsoft.graph.mailboxProtectionUnit",
      "id": "2b014d8c-71fe-4d00-a01a-31850bc5b32c",
      "policyId": "9fec8e78-bce4-4aaf-ab1b-5451cc387264",
      "directoryObjectId": "384974e2-72cd-48de-a6e8-6985d7c5db90",
      "displayName": "Emily Braun", // Newly Added
      "email": "emilyb@contoso.com", // Newly Added
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
      "error": null,
      "offboardRequestedDateTime": "0001-01-01T00:00:00.0000000Z"
    },
    {
      "@odata.type": "#microsoft.graph.mailboxProtectionUnit",
      "id": "57014d8c-71fe-4d00-a01a-31850bc5b32c",
      "policyId": "9fec8e78-bce4-4aaf-ab1b-5451cc387264",
      "directoryObjectId": "184d9337-d8f0-456e-92cd-00a3abdd2093",
      "displayName": "Alex Wilber", // Newly Added
      "email": "alexw@contoso.com", // Newly Added
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
      "error": null,
      "offboardRequestedDateTime": "0001-01-01T00:00:00.0000000Z"
    },
    {
      "@odata.type": "#microsoft.graph.mailboxProtectionUnit",
      "id": "17014d8c-71fe-4d00-a01a-31850bc5b32c",
      "policyId": "9fec8e78-bce4-4aaf-ab1b-5451cc387264",
      "directoryObjectId": "344d9337-d8f0-456e-92cd-00a3abdd2093",
      "displayName": "Shaun Wong", // Newly Added
      "email": "shaunw@contoso.com", // Newly Added
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
      "error": null,
      "offboardRequestedDateTime": "0001-01-01T00:00:00.0000000Z"
    },
    {
      "@odata.type": "#microsoft.graph.mailboxProtectionUnit",
      "id": "8f014d8c-71fe-4d00-a01a-31850bc5b32c",
      "policyId": "9fec8e78-bce4-4aaf-ab1b-5451cc387264",
      "directoryObjectId": "781d9337-d8f0-456e-92cd-00a3abdd2093",
      "displayName": "Janet Green", // Newly Added
      "email": "janetg@contoso.com", // Newly Added
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
      "error": null,
      "offboardRequestedDateTime": "0001-01-01T00:00:00.0000000Z"
    },
    {
      "@odata.type": "#microsoft.graph.mailboxProtectionUnit",
      "id": "9b014d8c-71fe-4d00-a01a-31850bc5b32c",
      "policyId": "9fec8e78-bce4-4aaf-ab1b-5451cc387264",
      "directoryObjectId": "2d1d9337-d8f0-456e-92cd-00a3abdd2093",
      "displayName": "Eddie Brock ", // Newly Added
      "email": "eddyb@contoso.com", // Newly Added
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
      "error": null,
      "offboardRequestedDateTime": "0001-01-01T00:00:00.0000000Z"
    }
  ]
}
```
