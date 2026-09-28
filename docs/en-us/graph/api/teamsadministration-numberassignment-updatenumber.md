<!-- Source: https://learn.microsoft.com/en-us/graph/api/teamsadministration-numberassignment-updatenumber?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-04-15 -->

# numberAssignment: updateNumber

Namespace: microsoft.graph.teamsAdministration

This method is used to update an existing number with optional attributes. Currently supported attributes are `locationId`, `networkSiteId`, and `reverseNumberLookupOptions`.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | TeamsTelephoneNumber.ReadWrite.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | TeamsTelephoneNumber.ReadWrite.All | Not available. |

## HTTP request

```http
POST /admin/teams/telephoneNumberManagement/numberAssignments/updateNumber
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the parameters.

The following table lists the parameters that are required when you call this action.

| Parameter | Type | Description |
| :--- | :--- | :--- |
| telephoneNumber | String | Mandatory. The telephone number intended to be assigned. |
| locationId | String | Indicates the emergency address identifier set on the phone number. Passing an empty string clears the locationId, while passing `null` or not including the field preserves the existing value. |
| networkSiteId | String | Indicates the updated networkSiteId. Use an empty string to clear the existing networkSiteId, or use `null`/omit the field to preserve the existing value. |
| reverseNumberLookupOptions | String collection | This parameter is used to control the behavior of reverse number lookup \(RNL\) for a phone number. When RNL contains `skipInternalVoip`, an internal call to this phone number doesn't attempt to pass through internal VoIP via reverse number lookup in Microsoft Teams. Instead, the call establishes through external Public Switched Telephone Network \(PSTN\) connectivity directly. |

## Response

If successful, this method returns a `200 OK` response code.

## Examples

### Example 1: Update location ID

#### Request

The following example shows a request to update `locationId` of a telephone number.

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [Python](#tabpanel_1_python)

```http
POST https://graph.microsoft.com/v1.0/admin/teams/telephoneNumberManagement/numberAssignments/updateNumber
Content-Type: application/json

{
  "telephoneNumber": "+12061234567",
  "locationId": "93cb8a70-b4af-41df-9928-d07607e21776",
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Admin.Teams.TelephoneNumberManagement.NumberAssignments.MicrosoftGraphTeamsAdministrationUpdateNumber;

var requestBody = new UpdateNumberPostRequestBody
{
	TelephoneNumber = "+12061234567",
	LocationId = "93cb8a70-b4af-41df-9928-d07607e21776",
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
await graphClient.Admin.Teams.TelephoneNumberManagement.NumberAssignments.MicrosoftGraphTeamsAdministrationUpdateNumber.PostAsync(requestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphadmin "github.com/microsoftgraph/msgraph-sdk-go/admin"
	  //other-imports
)

requestBody := graphadmin.NewUpdateNumberPostRequestBody()
telephoneNumber := "+12061234567"
requestBody.SetTelephoneNumber(&telephoneNumber) 
locationId := "93cb8a70-b4af-41df-9928-d07607e21776"
requestBody.SetLocationId(&locationId) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
graphClient.Admin().Teams().TelephoneNumberManagement().NumberAssignments().MicrosoftGraphTeamsAdministrationUpdateNumber().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.admin.teams.telephonenumbermanagement.numberassignments.microsoftgraphteamsadministrationupdatenumber.UpdateNumberPostRequestBody updateNumberPostRequestBody = new com.microsoft.graph.admin.teams.telephonenumbermanagement.numberassignments.microsoftgraphteamsadministrationupdatenumber.UpdateNumberPostRequestBody();
updateNumberPostRequestBody.setTelephoneNumber("+12061234567");
updateNumberPostRequestBody.setLocationId("93cb8a70-b4af-41df-9928-d07607e21776");
graphClient.admin().teams().telephoneNumberManagement().numberAssignments().microsoftGraphTeamsAdministrationUpdateNumber().post(updateNumberPostRequestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const updateNumber = {
  telephoneNumber: '+12061234567',
  locationId: '93cb8a70-b4af-41df-9928-d07607e21776',
};

await client.api('/admin/teams/telephoneNumberManagement/numberAssignments/updateNumber')
	.post(updateNumber);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Admin\Teams\TelephoneNumberManagement\NumberAssignments\MicrosoftGraphTeamsAdministrationUpdateNumber\UpdateNumberPostRequestBody;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new UpdateNumberPostRequestBody();
$requestBody->setTelephoneNumber('+12061234567');
$requestBody->setLocationId('93cb8a70-b4af-41df-9928-d07607e21776');

$graphServiceClient->admin()->teams()->telephoneNumberManagement()->numberAssignments()->microsoftGraphTeamsAdministrationUpdateNumber()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.admin.teams.telephonenumbermanagement.numberassignments.microsoft_graph_teams_administration_update_number.update_number_post_request_body import UpdateNumberPostRequestBody
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = UpdateNumberPostRequestBody(
	telephone_number = "+12061234567",
	location_id = "93cb8a70-b4af-41df-9928-d07607e21776",
)

await graph_client.admin.teams.telephone_number_management.number_assignments.microsoft_graph_teams_administration_update_number.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
```

### Example 2: Update network site ID

#### Request

The following example shows a request to update `networkSiteId` of a telephone number.

- [HTTP](#tabpanel_2_http)
- [C#](#tabpanel_2_csharp)
- [Go](#tabpanel_2_go)
- [Java](#tabpanel_2_java)
- [JavaScript](#tabpanel_2_javascript)
- [PHP](#tabpanel_2_php)
- [Python](#tabpanel_2_python)

```http
POST https://graph.microsoft.com/v1.0/admin/teams/telephoneNumberManagement/numberAssignments/updateNumber
Content-Type: application/json

{
  "telephoneNumber": "+12061234567",
  "networkSiteId": "fff21455-0f84-4a6b-babd-0a9b46971a62",
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Admin.Teams.TelephoneNumberManagement.NumberAssignments.MicrosoftGraphTeamsAdministrationUpdateNumber;

var requestBody = new UpdateNumberPostRequestBody
{
	TelephoneNumber = "+12061234567",
	NetworkSiteId = "fff21455-0f84-4a6b-babd-0a9b46971a62",
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
await graphClient.Admin.Teams.TelephoneNumberManagement.NumberAssignments.MicrosoftGraphTeamsAdministrationUpdateNumber.PostAsync(requestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphadmin "github.com/microsoftgraph/msgraph-sdk-go/admin"
	  //other-imports
)

requestBody := graphadmin.NewUpdateNumberPostRequestBody()
telephoneNumber := "+12061234567"
requestBody.SetTelephoneNumber(&telephoneNumber) 
networkSiteId := "fff21455-0f84-4a6b-babd-0a9b46971a62"
requestBody.SetNetworkSiteId(&networkSiteId) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
graphClient.Admin().Teams().TelephoneNumberManagement().NumberAssignments().MicrosoftGraphTeamsAdministrationUpdateNumber().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.admin.teams.telephonenumbermanagement.numberassignments.microsoftgraphteamsadministrationupdatenumber.UpdateNumberPostRequestBody updateNumberPostRequestBody = new com.microsoft.graph.admin.teams.telephonenumbermanagement.numberassignments.microsoftgraphteamsadministrationupdatenumber.UpdateNumberPostRequestBody();
updateNumberPostRequestBody.setTelephoneNumber("+12061234567");
updateNumberPostRequestBody.setNetworkSiteId("fff21455-0f84-4a6b-babd-0a9b46971a62");
graphClient.admin().teams().telephoneNumberManagement().numberAssignments().microsoftGraphTeamsAdministrationUpdateNumber().post(updateNumberPostRequestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const updateNumber = {
  telephoneNumber: '+12061234567',
  networkSiteId: 'fff21455-0f84-4a6b-babd-0a9b46971a62',
};

await client.api('/admin/teams/telephoneNumberManagement/numberAssignments/updateNumber')
	.post(updateNumber);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Admin\Teams\TelephoneNumberManagement\NumberAssignments\MicrosoftGraphTeamsAdministrationUpdateNumber\UpdateNumberPostRequestBody;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new UpdateNumberPostRequestBody();
$requestBody->setTelephoneNumber('+12061234567');
$requestBody->setNetworkSiteId('fff21455-0f84-4a6b-babd-0a9b46971a62');

$graphServiceClient->admin()->teams()->telephoneNumberManagement()->numberAssignments()->microsoftGraphTeamsAdministrationUpdateNumber()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.admin.teams.telephonenumbermanagement.numberassignments.microsoft_graph_teams_administration_update_number.update_number_post_request_body import UpdateNumberPostRequestBody
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = UpdateNumberPostRequestBody(
	telephone_number = "+12061234567",
	network_site_id = "fff21455-0f84-4a6b-babd-0a9b46971a62",
)

await graph_client.admin.teams.telephone_number_management.number_assignments.microsoft_graph_teams_administration_update_number.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
```

### Example 3: Update reverse number lookup options

#### Request

The following example shows a request to update `reverseNumberLookupOptions` for telephone number associated with resource account.

- [HTTP](#tabpanel_3_http)
- [C#](#tabpanel_3_csharp)
- [Go](#tabpanel_3_go)
- [Java](#tabpanel_3_java)
- [JavaScript](#tabpanel_3_javascript)
- [PHP](#tabpanel_3_php)
- [Python](#tabpanel_3_python)

```http
POST https://graph.microsoft.com/v1.0/admin/teams/telephoneNumberManagement/numberAssignments/updateNumber
Content-Type: application/json

{
  "telephoneNumber": "+12061234567",
  "reverseNumberLookupOptions": ["skipInternalVoip"],
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Admin.Teams.TelephoneNumberManagement.NumberAssignments.MicrosoftGraphTeamsAdministrationUpdateNumber;

var requestBody = new UpdateNumberPostRequestBody
{
	TelephoneNumber = "+12061234567",
	ReverseNumberLookupOptions = new List<string>
	{
		"skipInternalVoip",
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
await graphClient.Admin.Teams.TelephoneNumberManagement.NumberAssignments.MicrosoftGraphTeamsAdministrationUpdateNumber.PostAsync(requestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphadmin "github.com/microsoftgraph/msgraph-sdk-go/admin"
	  //other-imports
)

requestBody := graphadmin.NewUpdateNumberPostRequestBody()
telephoneNumber := "+12061234567"
requestBody.SetTelephoneNumber(&telephoneNumber) 
reverseNumberLookupOptions := []string {
	"skipInternalVoip",
}
requestBody.SetReverseNumberLookupOptions(reverseNumberLookupOptions)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
graphClient.Admin().Teams().TelephoneNumberManagement().NumberAssignments().MicrosoftGraphTeamsAdministrationUpdateNumber().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.admin.teams.telephonenumbermanagement.numberassignments.microsoftgraphteamsadministrationupdatenumber.UpdateNumberPostRequestBody updateNumberPostRequestBody = new com.microsoft.graph.admin.teams.telephonenumbermanagement.numberassignments.microsoftgraphteamsadministrationupdatenumber.UpdateNumberPostRequestBody();
updateNumberPostRequestBody.setTelephoneNumber("+12061234567");
LinkedList<String> reverseNumberLookupOptions = new LinkedList<String>();
reverseNumberLookupOptions.add("skipInternalVoip");
updateNumberPostRequestBody.setReverseNumberLookupOptions(reverseNumberLookupOptions);
graphClient.admin().teams().telephoneNumberManagement().numberAssignments().microsoftGraphTeamsAdministrationUpdateNumber().post(updateNumberPostRequestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const updateNumber = {
  telephoneNumber: '+12061234567',
  reverseNumberLookupOptions: ['skipInternalVoip'],
};

await client.api('/admin/teams/telephoneNumberManagement/numberAssignments/updateNumber')
	.post(updateNumber);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Admin\Teams\TelephoneNumberManagement\NumberAssignments\MicrosoftGraphTeamsAdministrationUpdateNumber\UpdateNumberPostRequestBody;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new UpdateNumberPostRequestBody();
$requestBody->setTelephoneNumber('+12061234567');
$requestBody->setReverseNumberLookupOptions(['skipInternalVoip', 	]);

$graphServiceClient->admin()->teams()->telephoneNumberManagement()->numberAssignments()->microsoftGraphTeamsAdministrationUpdateNumber()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.admin.teams.telephonenumbermanagement.numberassignments.microsoft_graph_teams_administration_update_number.update_number_post_request_body import UpdateNumberPostRequestBody
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = UpdateNumberPostRequestBody(
	telephone_number = "+12061234567",
	reverse_number_lookup_options = [
		"skipInternalVoip",
	],
)

await graph_client.admin.teams.telephone_number_management.number_assignments.microsoft_graph_teams_administration_update_number.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
```

### Example 4: Clear location ID

#### Request

The following example shows a request to update `locationId` of a telephone number.

- [HTTP](#tabpanel_4_http)
- [C#](#tabpanel_4_csharp)
- [Go](#tabpanel_4_go)
- [Java](#tabpanel_4_java)
- [JavaScript](#tabpanel_4_javascript)
- [PHP](#tabpanel_4_php)
- [Python](#tabpanel_4_python)

```http
POST https://graph.microsoft.com/v1.0/admin/teams/telephoneNumberManagement/numberAssignments/updateNumber
Content-Type: application/json

{
  "telephoneNumber": "+12061234567",
  "locationId": "",
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Admin.Teams.TelephoneNumberManagement.NumberAssignments.MicrosoftGraphTeamsAdministrationUpdateNumber;

var requestBody = new UpdateNumberPostRequestBody
{
	TelephoneNumber = "+12061234567",
	LocationId = "",
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
await graphClient.Admin.Teams.TelephoneNumberManagement.NumberAssignments.MicrosoftGraphTeamsAdministrationUpdateNumber.PostAsync(requestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphadmin "github.com/microsoftgraph/msgraph-sdk-go/admin"
	  //other-imports
)

requestBody := graphadmin.NewUpdateNumberPostRequestBody()
telephoneNumber := "+12061234567"
requestBody.SetTelephoneNumber(&telephoneNumber) 
locationId := ""
requestBody.SetLocationId(&locationId) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
graphClient.Admin().Teams().TelephoneNumberManagement().NumberAssignments().MicrosoftGraphTeamsAdministrationUpdateNumber().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.admin.teams.telephonenumbermanagement.numberassignments.microsoftgraphteamsadministrationupdatenumber.UpdateNumberPostRequestBody updateNumberPostRequestBody = new com.microsoft.graph.admin.teams.telephonenumbermanagement.numberassignments.microsoftgraphteamsadministrationupdatenumber.UpdateNumberPostRequestBody();
updateNumberPostRequestBody.setTelephoneNumber("+12061234567");
updateNumberPostRequestBody.setLocationId("");
graphClient.admin().teams().telephoneNumberManagement().numberAssignments().microsoftGraphTeamsAdministrationUpdateNumber().post(updateNumberPostRequestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const updateNumber = {
  telephoneNumber: '+12061234567',
  locationId: '',
};

await client.api('/admin/teams/telephoneNumberManagement/numberAssignments/updateNumber')
	.post(updateNumber);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Admin\Teams\TelephoneNumberManagement\NumberAssignments\MicrosoftGraphTeamsAdministrationUpdateNumber\UpdateNumberPostRequestBody;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new UpdateNumberPostRequestBody();
$requestBody->setTelephoneNumber('+12061234567');
$requestBody->setLocationId('');

$graphServiceClient->admin()->teams()->telephoneNumberManagement()->numberAssignments()->microsoftGraphTeamsAdministrationUpdateNumber()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.admin.teams.telephonenumbermanagement.numberassignments.microsoft_graph_teams_administration_update_number.update_number_post_request_body import UpdateNumberPostRequestBody
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = UpdateNumberPostRequestBody(
	telephone_number = "+12061234567",
	location_id = "",
)

await graph_client.admin.teams.telephone_number_management.number_assignments.microsoft_graph_teams_administration_update_number.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
```
