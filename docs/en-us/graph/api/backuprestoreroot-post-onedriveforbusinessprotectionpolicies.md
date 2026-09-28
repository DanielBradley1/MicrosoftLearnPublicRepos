<!-- Source: https://learn.microsoft.com/en-us/graph/api/backuprestoreroot-post-onedriveforbusinessprotectionpolicies?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-09-11 -->

# Create oneDriveForBusinessProtectionPolicy

Namespace: microsoft.graph

Create a protection policy for the OneDrive service in Microsoft 365. When the policy is created, its state is set to `inactive`. Users can also provide a list of protection units under the policy.

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
POST /solutions/backupRestore/oneDriveForBusinessProtectionPolicies
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

You can specify the following properties when creating a **oneDriveForBusinessProtectionPolicy**.

| Property | Type | Description |
| :--- | :--- | :--- |
| displayName | String | Name of the SharePoint Protection Policy. Required |
| driveProtectionUnits | Collection\([driveProtectionUnit](https://learn.microsoft.com/en-us/graph/api/resources/driveprotectionunit?view=graph-rest-1.0)\) | Collection of the driveProtectionUnit to be added to the oneDriveForBusinessProtectionPolicy. Required. |

## Response

If successful, this method returns a `201 Created` response code and a [oneDriveForBusinessProtectionPolicy](https://learn.microsoft.com/en-us/graph/api/resources/onedriveforbusinessprotectionpolicy?view=graph-rest-1.0) object in the response body.

For a list of possible error responses, see [Backup Storage API error responses](https://learn.microsoft.com/en-us/graph/backup-storage-error-codes).

## Examples

### Request

The following example shows a request.

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [PowerShell](#tabpanel_1_powershell)
- [Python](#tabpanel_1_python)

```http
POST https://graph.microsoft.com/v1.0/solutions/backupRestore/oneDriveForBusinessProtectionPolicies

{
  "displayName": "OneDrive For Business Protection Policy",
  "driveProtectionUnits": [
    {
      "directoryObjectId": "cdd3a849-dcaf-4a85-af82-7e39fc14019"
    },
    {
      "directoryObjectId": "9bc069da-b746-41a4-89ab-26125c6373c7"
    },
    {
      "directoryObjectId": "b218eb4a-ea72-42bd-8f0b-d0bbf794bec7"
    }
  ]
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new OneDriveForBusinessProtectionPolicy
{
	DisplayName = "OneDrive For Business Protection Policy",
	DriveProtectionUnits = new List<DriveProtectionUnit>
	{
		new DriveProtectionUnit
		{
			DirectoryObjectId = "cdd3a849-dcaf-4a85-af82-7e39fc14019",
		},
		new DriveProtectionUnit
		{
			DirectoryObjectId = "9bc069da-b746-41a4-89ab-26125c6373c7",
		},
		new DriveProtectionUnit
		{
			DirectoryObjectId = "b218eb4a-ea72-42bd-8f0b-d0bbf794bec7",
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Solutions.BackupRestore.OneDriveForBusinessProtectionPolicies.PostAsync(requestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphmodels "github.com/microsoftgraph/msgraph-sdk-go/models"
	  //other-imports
)

requestBody := graphmodels.NewOneDriveForBusinessProtectionPolicy()
displayName := "OneDrive For Business Protection Policy"
requestBody.SetDisplayName(&displayName) 


driveProtectionUnit := graphmodels.NewDriveProtectionUnit()
directoryObjectId := "cdd3a849-dcaf-4a85-af82-7e39fc14019"
driveProtectionUnit.SetDirectoryObjectId(&directoryObjectId) 
driveProtectionUnit1 := graphmodels.NewDriveProtectionUnit()
directoryObjectId := "9bc069da-b746-41a4-89ab-26125c6373c7"
driveProtectionUnit1.SetDirectoryObjectId(&directoryObjectId) 
driveProtectionUnit2 := graphmodels.NewDriveProtectionUnit()
directoryObjectId := "b218eb4a-ea72-42bd-8f0b-d0bbf794bec7"
driveProtectionUnit2.SetDirectoryObjectId(&directoryObjectId) 

driveProtectionUnits := []graphmodels.DriveProtectionUnitable {
	driveProtectionUnit,
	driveProtectionUnit1,
	driveProtectionUnit2,
}
requestBody.SetDriveProtectionUnits(driveProtectionUnits)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
oneDriveForBusinessProtectionPolicies, err := graphClient.Solutions().BackupRestore().OneDriveForBusinessProtectionPolicies().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

OneDriveForBusinessProtectionPolicy oneDriveForBusinessProtectionPolicy = new OneDriveForBusinessProtectionPolicy();
oneDriveForBusinessProtectionPolicy.setDisplayName("OneDrive For Business Protection Policy");
LinkedList<DriveProtectionUnit> driveProtectionUnits = new LinkedList<DriveProtectionUnit>();
DriveProtectionUnit driveProtectionUnit = new DriveProtectionUnit();
driveProtectionUnit.setDirectoryObjectId("cdd3a849-dcaf-4a85-af82-7e39fc14019");
driveProtectionUnits.add(driveProtectionUnit);
DriveProtectionUnit driveProtectionUnit1 = new DriveProtectionUnit();
driveProtectionUnit1.setDirectoryObjectId("9bc069da-b746-41a4-89ab-26125c6373c7");
driveProtectionUnits.add(driveProtectionUnit1);
DriveProtectionUnit driveProtectionUnit2 = new DriveProtectionUnit();
driveProtectionUnit2.setDirectoryObjectId("b218eb4a-ea72-42bd-8f0b-d0bbf794bec7");
driveProtectionUnits.add(driveProtectionUnit2);
oneDriveForBusinessProtectionPolicy.setDriveProtectionUnits(driveProtectionUnits);
OneDriveForBusinessProtectionPolicy result = graphClient.solutions().backupRestore().oneDriveForBusinessProtectionPolicies().post(oneDriveForBusinessProtectionPolicy);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const oneDriveForBusinessProtectionPolicy = {
  displayName: 'OneDrive For Business Protection Policy',
  driveProtectionUnits: [
    {
      directoryObjectId: 'cdd3a849-dcaf-4a85-af82-7e39fc14019'
    },
    {
      directoryObjectId: '9bc069da-b746-41a4-89ab-26125c6373c7'
    },
    {
      directoryObjectId: 'b218eb4a-ea72-42bd-8f0b-d0bbf794bec7'
    }
  ]
};

await client.api('/solutions/backupRestore/oneDriveForBusinessProtectionPolicies')
	.post(oneDriveForBusinessProtectionPolicy);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\OneDriveForBusinessProtectionPolicy;
use Microsoft\Graph\Generated\Models\DriveProtectionUnit;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new OneDriveForBusinessProtectionPolicy();
$requestBody->setDisplayName('OneDrive For Business Protection Policy');
$driveProtectionUnitsDriveProtectionUnit1 = new DriveProtectionUnit();
$driveProtectionUnitsDriveProtectionUnit1->setDirectoryObjectId('cdd3a849-dcaf-4a85-af82-7e39fc14019');
$driveProtectionUnitsArray []= $driveProtectionUnitsDriveProtectionUnit1;
$driveProtectionUnitsDriveProtectionUnit2 = new DriveProtectionUnit();
$driveProtectionUnitsDriveProtectionUnit2->setDirectoryObjectId('9bc069da-b746-41a4-89ab-26125c6373c7');
$driveProtectionUnitsArray []= $driveProtectionUnitsDriveProtectionUnit2;
$driveProtectionUnitsDriveProtectionUnit3 = new DriveProtectionUnit();
$driveProtectionUnitsDriveProtectionUnit3->setDirectoryObjectId('b218eb4a-ea72-42bd-8f0b-d0bbf794bec7');
$driveProtectionUnitsArray []= $driveProtectionUnitsDriveProtectionUnit3;
$requestBody->setDriveProtectionUnits($driveProtectionUnitsArray);


$result = $graphServiceClient->solutions()->backupRestore()->oneDriveForBusinessProtectionPolicies()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.BackupRestore

$params = @{
	displayName = "OneDrive For Business Protection Policy"
	driveProtectionUnits = @(
		@{
			directoryObjectId = "cdd3a849-dcaf-4a85-af82-7e39fc14019"
		}
		@{
			directoryObjectId = "9bc069da-b746-41a4-89ab-26125c6373c7"
		}
		@{
			directoryObjectId = "b218eb4a-ea72-42bd-8f0b-d0bbf794bec7"
		}
	)
}

New-MgSolutionBackupRestoreOneDriveForBusinessProtectionPolicy -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.one_drive_for_business_protection_policy import OneDriveForBusinessProtectionPolicy
from msgraph.generated.models.drive_protection_unit import DriveProtectionUnit
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = OneDriveForBusinessProtectionPolicy(
	display_name = "OneDrive For Business Protection Policy",
	drive_protection_units = [
		DriveProtectionUnit(
			directory_object_id = "cdd3a849-dcaf-4a85-af82-7e39fc14019",
		),
		DriveProtectionUnit(
			directory_object_id = "9bc069da-b746-41a4-89ab-26125c6373c7",
		),
		DriveProtectionUnit(
			directory_object_id = "b218eb4a-ea72-42bd-8f0b-d0bbf794bec7",
		),
	],
)

result = await graph_client.solutions.backup_restore.one_drive_for_business_protection_policies.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-Location: https://graph.microsoft.com/v1.0/solutions/backupRestore/ProtectionPolicies/b218eb4a-ea72-42bd-8f0b-d0bbf794bec7

{
  "@odata.context": "/solutions/backupRestore/$metadata#oneDriveForBusinessProtectionPolicies/$entity",
  "id": "b218eb4a-ea72-42bd-8f0b-d0bbf794bec7",
  "displayName": "OneDrive Protection Policy",
  "status": "inactive",
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
      "email": "User2@constoso.com",
      "id": "845457dc-4bb2-4815-bef3-8628ebd1952e",
      "displayName": "User2"
    }
  },
  "lastModifiedDateTime": "2015-06-19T12:01:03.45Z",
  "retentionSettings": [
    {
      "interval": "R/PT10M",
      "period": "P2W"
    },
    {
      "interval": "R/P1W",
      "period": "P1Y"
    }
  ]
}
```
