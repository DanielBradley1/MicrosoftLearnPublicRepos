<!-- Source: https://learn.microsoft.com/en-us/graph/api/security-ediscoverysearch-purgedata?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-02-26 -->

# ediscoverySearch: purgeData

Namespace: microsoft.graph.security

Delete Exchange mailbox items or Microsoft Teams messages contained in an [eDiscovery search](https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoverysearch?view=graph-rest-1.0).

You can collect and purge the following categories of Teams content:

- **Teams 1:1 chats** - Chat messages, posts, and attachments shared in a Teams conversation between two people. Teams 1:1 chats are also called *conversations*.
- **Teams group chats** - Chat messages, posts, and attachments shared in a Teams conversation between three or more people. Also called *1:N* chats or *group conversations*.
- **Teams channels** - Chat messages, posts, replies, and attachments shared in a standard Teams channel.
- **Private channels** - Message posts, replies, and attachments shared in a private Teams channel.
- **Shared channels** - Message posts, replies, and attachments shared in a shared Teams channel.

> **Note:** This request purges a maximum of 100 items per location only. When **purgeType** is set to either `recoverable` or `permanentlyDelete` and **purgeAreas** is set to `teamsMessages`, the Teams messages are permanently deleted.

For more information about purging Teams messages, see:

- [eDiscovery solution series: Data spillage scenario - Search and purge](https://learn.microsoft.com/en-us/microsoft-365/compliance/data-spillage-scenariosearch-and-purge)
- [eDiscovery \(Premium\) workflow for content in Microsoft Teams](https://learn.microsoft.com/en-us/microsoft-365/compliance/teams-workflow-in-advanced-ediscovery)

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | eDiscovery.ReadWrite.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | eDiscovery.ReadWrite.All | Not available. |

Important

For delegated access using work or school accounts, the signed-in user must be assigned a supported [Microsoft Purview role](https://learn.microsoft.com/en-us/purview/edisc-permissions) through one of the following options:

- **Organization Management**. Allows members to perform bulk removal of data matching the criteria of a search. **This is the least privileged option for purging data**.

The Search And Purge role is required to permanently delete email messages that match search criteria. This role is only available to members of the Organization Management role group and should be used with extreme caution as deleted data cannot be recovered.

For more information about eDiscovery permissions and roles, see [Assign permissions in eDiscovery](https://learn.microsoft.com/en-us/purview/edisc-permissions).

## HTTP request

```http
POST /security/cases/ediscoveryCases/{ediscoveryCaseId}/searches/{ediscoverySearchId}/purgeData
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

In the request body, supply a JSON representation of the parameters.

The following table shows the parameters that you can use with this action.

| Parameter | Type | Description |
| :--- | :--- | :--- |
| purgeAreas | microsoft.graph.security.purgeAreas | Option to define the locations to be in scope of the purge action. The possible values are: `mailboxes`, `teamsMessages`, `unknownFutureValue`. |
| purgeType | microsoft.graph.security.purgeType | Options that control whether the action is soft delete or hard delete. The possible values are: `recoverable`, `unknownFutureValue`, `permanentlyDelete`. |

## Response

If successful, this action returns a `202 Accepted` response code.

If the purge data operation is started successfully, this action returns a `202 Accepted` response code. The response also contains a `Location` header, which contains the location of the [Purge data operation](https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoverypurgedataoperation?view=graph-rest-1.0) that was created to commit the purge. To check the status of the purge data operation, make a GET request to the location URL.

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
POST https://graph.microsoft.com/v1.0/security/cases/ediscoveryCases/b0073e4e-4184-41c6-9eb7-8c8cc3e2288b/searches/c61a5860-d634-4d14-aea7-d82b6f4eb7af/purgeData

{
  "purgeType": "recoverable",
  "purgeAreas": "teamsMessages"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Security.Cases.EdiscoveryCases.Item.Searches.Item.MicrosoftGraphSecurityPurgeData;
using Microsoft.Graph.Models.Security;

var requestBody = new PurgeDataPostRequestBody
{
	PurgeType = PurgeType.Recoverable,
	PurgeAreas = PurgeAreas.TeamsMessages,
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
await graphClient.Security.Cases.EdiscoveryCases["{ediscoveryCase-id}"].Searches["{ediscoverySearch-id}"].MicrosoftGraphSecurityPurgeData.PostAsync(requestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphsecurity "github.com/microsoftgraph/msgraph-sdk-go/security"
	  graphmodelssecurity "github.com/microsoftgraph/msgraph-sdk-go/models/security"
	  //other-imports
)

requestBody := graphsecurity.NewPurgeDataPostRequestBody()
purgeType := graphmodels.RECOVERABLE_PURGETYPE 
requestBody.SetPurgeType(&purgeType) 
purgeAreas := graphmodels.TEAMSMESSAGES_PURGEAREAS 
requestBody.SetPurgeAreas(&purgeAreas) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
graphClient.Security().Cases().EdiscoveryCases().ByEdiscoveryCaseId("ediscoveryCase-id").Searches().ByEdiscoverySearchId("ediscoverySearch-id").MicrosoftGraphSecurityPurgeData().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.security.cases.ediscoverycases.item.searches.item.microsoftgraphsecuritypurgedata.PurgeDataPostRequestBody purgeDataPostRequestBody = new com.microsoft.graph.security.cases.ediscoverycases.item.searches.item.microsoftgraphsecuritypurgedata.PurgeDataPostRequestBody();
purgeDataPostRequestBody.setPurgeType(com.microsoft.graph.models.security.PurgeType.Recoverable);
purgeDataPostRequestBody.setPurgeAreas(EnumSet.of(com.microsoft.graph.models.security.PurgeAreas.TeamsMessages));
graphClient.security().cases().ediscoveryCases().byEdiscoveryCaseId("{ediscoveryCase-id}").searches().byEdiscoverySearchId("{ediscoverySearch-id}").microsoftGraphSecurityPurgeData().post(purgeDataPostRequestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const purgeData = {
  purgeType: 'recoverable',
  purgeAreas: 'teamsMessages'
};

await client.api('/security/cases/ediscoveryCases/b0073e4e-4184-41c6-9eb7-8c8cc3e2288b/searches/c61a5860-d634-4d14-aea7-d82b6f4eb7af/purgeData')
	.post(purgeData);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Security\Cases\EdiscoveryCases\Item\Searches\Item\MicrosoftGraphSecurityPurgeData\PurgeDataPostRequestBody;
use Microsoft\Graph\Generated\Models\Security\PurgeType;
use Microsoft\Graph\Generated\Models\Security\PurgeAreas;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new PurgeDataPostRequestBody();
$requestBody->setPurgeType(new PurgeType('recoverable'));
$requestBody->setPurgeAreas(new PurgeAreas('teamsMessages'));

$graphServiceClient->security()->cases()->ediscoveryCases()->byEdiscoveryCaseId('ediscoveryCase-id')->searches()->byEdiscoverySearchId('ediscoverySearch-id')->microsoftGraphSecurityPurgeData()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Security

$params = @{
	purgeType = "recoverable"
	purgeAreas = "teamsMessages"
}

Clear-MgSecurityCaseEdiscoveryCaseSearchData -EdiscoveryCaseId $ediscoveryCaseId -EdiscoverySearchId $ediscoverySearchId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.security.cases.ediscoverycases.item.searches.item.microsoft_graph_security_purge_data.purge_data_post_request_body import PurgeDataPostRequestBody
from msgraph.generated.models.purge_type import PurgeType
from msgraph.generated.models.purge_areas import PurgeAreas
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = PurgeDataPostRequestBody(
	purge_type = PurgeType.Recoverable,
	purge_areas = PurgeAreas.TeamsMessages,
)

await graph_client.security.cases.ediscovery_cases.by_ediscovery_case_id('ediscoveryCase-id').searches.by_ediscovery_search_id('ediscoverySearch-id').microsoft_graph_security_purge_data.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

```http
HTTP/1.1 202 Accepted
```
