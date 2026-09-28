<!-- Source: https://learn.microsoft.com/en-us/graph/api/backuprestoreroot-post-sharepointprotectionpolicies?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-23 -->

# Create sharePointProtectionPolicy

Namespace: microsoft.graph

Create a protection policy for a M365 service SharePoint. Policy will be created in `inactive` state. User can also provide a list of protection units under the policy.

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
POST /solutions/backupRestore/sharePointProtectionPolicies/
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

You can specify the following properties when creating a **sharePointProtectionPolicy** object.

| Property | Type | Description |
| :--- | :--- | :--- |
| displayName | String | Name of the SharePoint Protection Policy. Optional. |
| siteProtectionUnits | Collection\([siteProtectionUnit](https://learn.microsoft.com/en-us/graph/api/resources/siteprotectionunit?view=graph-rest-1.0)\) | Collection of the siteProtectionUnits to be added to the sharePointProtectionPolicy object. Required. Refer to [site](https://learn.microsoft.com/en-us/graph/api/resources/site?view=graph-rest-1.0) for the format of siteId. |

## Response

If successful, this method returns a `201 Created` response code and a [sharePointProtectionPolicy](https://learn.microsoft.com/en-us/graph/api/resources/sharepointprotectionpolicy?view=graph-rest-1.0) object in the response body.

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
POST https://graph.microsoft.com/v1.0/solutions/backupRestore/sharePointProtectionPolicies

{
  "displayName": "SharePoint Protection Policy",
  "siteProtectionUnits": [
    {
      "siteId": "contoso.sharepoint.com,febad3c2-a7b2-454c-8910-272c7bcf78fc,ba7b70d0-8ba0-4cae-b19a-7cb8c739512f"
    },
    {
      "siteId": "contoso.sharepoint.com/sites/marketing,da60e844-ba1d-49bc-b4d4-d5e36bae9019,712a596e-90a1-49e3-9b48-bfa80bee8740"
    },
    {
      "siteId": "contoso.sharepoint.com/sites/hr,3bfc861e-9a17-4a27-9562-3d8b26c81bb5,0271110f-634f-4300-a841-3a8a2e851851"
    }
  ]
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new SharePointProtectionPolicy
{
	DisplayName = "SharePoint Protection Policy",
	SiteProtectionUnits = new List<SiteProtectionUnit>
	{
		new SiteProtectionUnit
		{
			SiteId = "contoso.sharepoint.com,febad3c2-a7b2-454c-8910-272c7bcf78fc,ba7b70d0-8ba0-4cae-b19a-7cb8c739512f",
		},
		new SiteProtectionUnit
		{
			SiteId = "contoso.sharepoint.com/sites/marketing,da60e844-ba1d-49bc-b4d4-d5e36bae9019,712a596e-90a1-49e3-9b48-bfa80bee8740",
		},
		new SiteProtectionUnit
		{
			SiteId = "contoso.sharepoint.com/sites/hr,3bfc861e-9a17-4a27-9562-3d8b26c81bb5,0271110f-634f-4300-a841-3a8a2e851851",
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Solutions.BackupRestore.SharePointProtectionPolicies.PostAsync(requestBody);
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

requestBody := graphmodels.NewSharePointProtectionPolicy()
displayName := "SharePoint Protection Policy"
requestBody.SetDisplayName(&displayName) 


siteProtectionUnit := graphmodels.NewSiteProtectionUnit()
siteId := "contoso.sharepoint.com,febad3c2-a7b2-454c-8910-272c7bcf78fc,ba7b70d0-8ba0-4cae-b19a-7cb8c739512f"
siteProtectionUnit.SetSiteId(&siteId) 
siteProtectionUnit1 := graphmodels.NewSiteProtectionUnit()
siteId := "contoso.sharepoint.com/sites/marketing,da60e844-ba1d-49bc-b4d4-d5e36bae9019,712a596e-90a1-49e3-9b48-bfa80bee8740"
siteProtectionUnit1.SetSiteId(&siteId) 
siteProtectionUnit2 := graphmodels.NewSiteProtectionUnit()
siteId := "contoso.sharepoint.com/sites/hr,3bfc861e-9a17-4a27-9562-3d8b26c81bb5,0271110f-634f-4300-a841-3a8a2e851851"
siteProtectionUnit2.SetSiteId(&siteId) 

siteProtectionUnits := []graphmodels.SiteProtectionUnitable {
	siteProtectionUnit,
	siteProtectionUnit1,
	siteProtectionUnit2,
}
requestBody.SetSiteProtectionUnits(siteProtectionUnits)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
sharePointProtectionPolicies, err := graphClient.Solutions().BackupRestore().SharePointProtectionPolicies().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

SharePointProtectionPolicy sharePointProtectionPolicy = new SharePointProtectionPolicy();
sharePointProtectionPolicy.setDisplayName("SharePoint Protection Policy");
LinkedList<SiteProtectionUnit> siteProtectionUnits = new LinkedList<SiteProtectionUnit>();
SiteProtectionUnit siteProtectionUnit = new SiteProtectionUnit();
siteProtectionUnit.setSiteId("contoso.sharepoint.com,febad3c2-a7b2-454c-8910-272c7bcf78fc,ba7b70d0-8ba0-4cae-b19a-7cb8c739512f");
siteProtectionUnits.add(siteProtectionUnit);
SiteProtectionUnit siteProtectionUnit1 = new SiteProtectionUnit();
siteProtectionUnit1.setSiteId("contoso.sharepoint.com/sites/marketing,da60e844-ba1d-49bc-b4d4-d5e36bae9019,712a596e-90a1-49e3-9b48-bfa80bee8740");
siteProtectionUnits.add(siteProtectionUnit1);
SiteProtectionUnit siteProtectionUnit2 = new SiteProtectionUnit();
siteProtectionUnit2.setSiteId("contoso.sharepoint.com/sites/hr,3bfc861e-9a17-4a27-9562-3d8b26c81bb5,0271110f-634f-4300-a841-3a8a2e851851");
siteProtectionUnits.add(siteProtectionUnit2);
sharePointProtectionPolicy.setSiteProtectionUnits(siteProtectionUnits);
SharePointProtectionPolicy result = graphClient.solutions().backupRestore().sharePointProtectionPolicies().post(sharePointProtectionPolicy);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const sharePointProtectionPolicy = {
  displayName: 'SharePoint Protection Policy',
  siteProtectionUnits: [
    {
      siteId: 'contoso.sharepoint.com,febad3c2-a7b2-454c-8910-272c7bcf78fc,ba7b70d0-8ba0-4cae-b19a-7cb8c739512f'
    },
    {
      siteId: 'contoso.sharepoint.com/sites/marketing,da60e844-ba1d-49bc-b4d4-d5e36bae9019,712a596e-90a1-49e3-9b48-bfa80bee8740'
    },
    {
      siteId: 'contoso.sharepoint.com/sites/hr,3bfc861e-9a17-4a27-9562-3d8b26c81bb5,0271110f-634f-4300-a841-3a8a2e851851'
    }
  ]
};

await client.api('/solutions/backupRestore/sharePointProtectionPolicies')
	.post(sharePointProtectionPolicy);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\SharePointProtectionPolicy;
use Microsoft\Graph\Generated\Models\SiteProtectionUnit;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new SharePointProtectionPolicy();
$requestBody->setDisplayName('SharePoint Protection Policy');
$siteProtectionUnitsSiteProtectionUnit1 = new SiteProtectionUnit();
$siteProtectionUnitsSiteProtectionUnit1->setSiteId('contoso.sharepoint.com,febad3c2-a7b2-454c-8910-272c7bcf78fc,ba7b70d0-8ba0-4cae-b19a-7cb8c739512f');
$siteProtectionUnitsArray []= $siteProtectionUnitsSiteProtectionUnit1;
$siteProtectionUnitsSiteProtectionUnit2 = new SiteProtectionUnit();
$siteProtectionUnitsSiteProtectionUnit2->setSiteId('contoso.sharepoint.com/sites/marketing,da60e844-ba1d-49bc-b4d4-d5e36bae9019,712a596e-90a1-49e3-9b48-bfa80bee8740');
$siteProtectionUnitsArray []= $siteProtectionUnitsSiteProtectionUnit2;
$siteProtectionUnitsSiteProtectionUnit3 = new SiteProtectionUnit();
$siteProtectionUnitsSiteProtectionUnit3->setSiteId('contoso.sharepoint.com/sites/hr,3bfc861e-9a17-4a27-9562-3d8b26c81bb5,0271110f-634f-4300-a841-3a8a2e851851');
$siteProtectionUnitsArray []= $siteProtectionUnitsSiteProtectionUnit3;
$requestBody->setSiteProtectionUnits($siteProtectionUnitsArray);


$result = $graphServiceClient->solutions()->backupRestore()->sharePointProtectionPolicies()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.BackupRestore

$params = @{
	displayName = "SharePoint Protection Policy"
	siteProtectionUnits = @(
		@{
			siteId = "contoso.sharepoint.com,febad3c2-a7b2-454c-8910-272c7bcf78fc,ba7b70d0-8ba0-4cae-b19a-7cb8c739512f"
		}
		@{
			siteId = "contoso.sharepoint.com/sites/marketing,da60e844-ba1d-49bc-b4d4-d5e36bae9019,712a596e-90a1-49e3-9b48-bfa80bee8740"
		}
		@{
			siteId = "contoso.sharepoint.com/sites/hr,3bfc861e-9a17-4a27-9562-3d8b26c81bb5,0271110f-634f-4300-a841-3a8a2e851851"
		}
	)
}

New-MgSolutionBackupRestoreSharePointProtectionPolicy -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.share_point_protection_policy import SharePointProtectionPolicy
from msgraph.generated.models.site_protection_unit import SiteProtectionUnit
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = SharePointProtectionPolicy(
	display_name = "SharePoint Protection Policy",
	site_protection_units = [
		SiteProtectionUnit(
			site_id = "contoso.sharepoint.com,febad3c2-a7b2-454c-8910-272c7bcf78fc,ba7b70d0-8ba0-4cae-b19a-7cb8c739512f",
		),
		SiteProtectionUnit(
			site_id = "contoso.sharepoint.com/sites/marketing,da60e844-ba1d-49bc-b4d4-d5e36bae9019,712a596e-90a1-49e3-9b48-bfa80bee8740",
		),
		SiteProtectionUnit(
			site_id = "contoso.sharepoint.com/sites/hr,3bfc861e-9a17-4a27-9562-3d8b26c81bb5,0271110f-634f-4300-a841-3a8a2e851851",
		),
	],
)

result = await graph_client.solutions.backup_restore.share_point_protection_policies.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-Location: https://graph.microsoft.com/v1.0/solutions/backupRestore/protectionPolicies/b218eb4a-ea72-42bd-8f0b-d0bbf794bec7

{
  "@odata.context": " /solutions/backupRestore/$metadata#sharePointProtectionPolicies/$entity",
  "id": "b218eb4a-ea72-42bd-8f0b-d0bbf794bec7",
  "displayName": "SharePoint Protection Policy",
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
      //Keep the per 10 minute copies for 14 days
      "interval": "R/PT10M",
      "period": "P2W"
    },
    {
      //Keep the per week copies for 1 year
      "interval": "R/P1W",
      "period": "P1Y"
    }
  ]
}
```
