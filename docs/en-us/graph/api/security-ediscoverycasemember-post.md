<!-- Source: https://learn.microsoft.com/en-us/graph/api/security-ediscoverycasemember-post?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-03-21 -->

# Add ediscoveryCaseMember

Namespace: microsoft.graph.security

Add an [ediscoveryCaseMember](https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoverycasemember?view=graph-rest-1.0) to an [ediscoveryCase](https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoverycase?view=graph-rest-1.0). The [ediscoveryCaseMember](https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoverycasemember?view=graph-rest-1.0) can be one of two types: a user or a role group.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | eDiscovery.Read.All | eDiscovery.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | eDiscovery.Read.All | eDiscovery.ReadWrite.All |

Important

For delegated access using work or school accounts, the signed-in user must be assigned a supported [Microsoft Purview role](https://learn.microsoft.com/en-us/purview/edisc-permissions) through one of the following options:

- **eDiscovery Manager**. Allows members to create and manage eDiscovery cases they create, including creating custodians, holds, searches, and other case management tasks. However, eDiscovery Managers can only create and manage the cases they create. **This is the least privileged option for managing their own cases**.
- **eDiscovery Administrator**. Provides all the permissions of eDiscovery Manager, plus the ability to access and manage all eDiscovery cases in the organization, configure eDiscovery settings, and manage any case after adding themselves as a member.

Additional roles that provide write access to eDiscovery features:

- **Compliance Administrator**. Includes Case Management, Compliance Search, and Hold permissions.
- **Organization Management**. Includes Case Management, Compliance Search, Hold, and Search And Purge permissions.

The eDiscovery Manager and eDiscovery Administrator roles are part of the Microsoft Purview role groups and provide access to eDiscovery features through [role-based access control \(RBAC\)](https://learn.microsoft.com/en-us/purview/edisc-permissions#rbac-roles-related-to-ediscovery).

For more information about eDiscovery permissions and roles, see [Assign permissions in eDiscovery](https://learn.microsoft.com/en-us/purview/edisc-permissions).

## HTTP request

```http
POST /security/cases/ediscoveryCases/{ediscoveryCaseId}/caseMembers
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
| recipientType | microsoft.graph.security.recipientType | Specifies the recipient type of the eDiscovery case member. The possible values are: `user`, `roleGroup`, `unknownFutureValue`. Required. |
| id | String | The ID of the eDiscovery case member. If not specified, then either **displayName** \(for role group\) or **smtpAddress** \(for user\) must be provided. |
| displayName | String | The display name of the eDiscovery case member. Allowed only for case members of type **roleGroup**. If not specified, then **ID** must be provided. |
| smtpAddress | String | The smtp address of the eDiscovery case member. Allowed only for case members of type **user**. If not specified, then **ID** must be provided. |

## Response

If successful, this method returns a `200 OK` response code and the added [microsoft.graph.security.ediscoveryCaseMember](https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoverycasemember?view=graph-rest-1.0) object in the response body.

## Examples

### Example 1: Add a case member of type **user** using **smtpAddress**

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

```http
POST https://graph.microsoft.com/v1.0/security/cases/ediscoveryCases/b0073e4e-4184-41c6-9eb7-8c8cc3e2288b/caseMembers
Content-Type: application/json

{
    "recipientType": "user",
    "smtpAddress": "johnadams@microsoft.com"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models.Security;

var requestBody = new EdiscoveryCaseMember
{
	RecipientType = RecipientType.User,
	SmtpAddress = "johnadams@microsoft.com",
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Security.Cases.EdiscoveryCases["{ediscoveryCase-id}"].CaseMembers.PostAsync(requestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphmodelssecurity "github.com/microsoftgraph/msgraph-sdk-go/models/security"
	  //other-imports
)

requestBody := graphmodelssecurity.NewEdiscoveryCaseMember()
recipientType := graphmodels.USER_RECIPIENTTYPE 
requestBody.SetRecipientType(&recipientType) 
smtpAddress := "johnadams@microsoft.com"
requestBody.SetSmtpAddress(&smtpAddress) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
caseMembers, err := graphClient.Security().Cases().EdiscoveryCases().ByEdiscoveryCaseId("ediscoveryCase-id").CaseMembers().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.models.security.EdiscoveryCaseMember ediscoveryCaseMember = new com.microsoft.graph.models.security.EdiscoveryCaseMember();
ediscoveryCaseMember.setRecipientType(EnumSet.of(com.microsoft.graph.models.security.RecipientType.User));
ediscoveryCaseMember.setSmtpAddress("johnadams@microsoft.com");
com.microsoft.graph.models.security.EdiscoveryCaseMember result = graphClient.security().cases().ediscoveryCases().byEdiscoveryCaseId("{ediscoveryCase-id}").caseMembers().post(ediscoveryCaseMember);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const ediscoveryCaseMember = {
    recipientType: 'user',
    smtpAddress: 'johnadams@microsoft.com'
};

await client.api('/security/cases/ediscoveryCases/b0073e4e-4184-41c6-9eb7-8c8cc3e2288b/caseMembers')
	.post(ediscoveryCaseMember);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\Security\EdiscoveryCaseMember;
use Microsoft\Graph\Generated\Models\Security\RecipientType;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new EdiscoveryCaseMember();
$requestBody->setRecipientType(new RecipientType('user'));
$requestBody->setSmtpAddress('johnadams@microsoft.com');

$result = $graphServiceClient->security()->cases()->ediscoveryCases()->byEdiscoveryCaseId('ediscoveryCase-id')->caseMembers()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Security

$params = @{
	recipientType = "user"
	smtpAddress = "johnadams@microsoft.com"
}

New-MgSecurityCaseEdiscoveryCaseMember -EdiscoveryCaseId $ediscoveryCaseId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.security.ediscovery_case_member import EdiscoveryCaseMember
from msgraph.generated.models.recipient_type import RecipientType
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = EdiscoveryCaseMember(
	recipient_type = RecipientType.User,
	smtp_address = "johnadams@microsoft.com",
)

result = await graph_client.security.cases.ediscovery_cases.by_ediscovery_case_id('ediscoveryCase-id').case_members.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{  
    "@odata.type": "microsoft.graph.security.ediscoveryCaseMember",
    "recipientType": "user",
    "id": "c4af6f9d-37f6-43f9-9e17-601544234146",
    "displayName": "John Adams",
    "smtpAddress": "johnadams@microsoft.com"
}
```

### Example 2: Add a case member of type **roleGroup** using **displayName**

#### Request

The following example shows a request.

- [HTTP](#tabpanel_2_http)
- [C#](#tabpanel_2_csharp)
- [Go](#tabpanel_2_go)
- [Java](#tabpanel_2_java)
- [JavaScript](#tabpanel_2_javascript)
- [PHP](#tabpanel_2_php)
- [PowerShell](#tabpanel_2_powershell)
- [Python](#tabpanel_2_python)

```http
POST https://graph.microsoft.com/v1.0/security/cases/ediscoveryCases/b0073e4e-4184-41c6-9eb7-8c8cc3e2288b/caseMembers
Content-Type: application/json

{
    "recipientType": "roleGroup",
    "displayName": "Security Administrator"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models.Security;

var requestBody = new EdiscoveryCaseMember
{
	RecipientType = RecipientType.RoleGroup,
	DisplayName = "Security Administrator",
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Security.Cases.EdiscoveryCases["{ediscoveryCase-id}"].CaseMembers.PostAsync(requestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphmodelssecurity "github.com/microsoftgraph/msgraph-sdk-go/models/security"
	  //other-imports
)

requestBody := graphmodelssecurity.NewEdiscoveryCaseMember()
recipientType := graphmodels.ROLEGROUP_RECIPIENTTYPE 
requestBody.SetRecipientType(&recipientType) 
displayName := "Security Administrator"
requestBody.SetDisplayName(&displayName) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
caseMembers, err := graphClient.Security().Cases().EdiscoveryCases().ByEdiscoveryCaseId("ediscoveryCase-id").CaseMembers().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.models.security.EdiscoveryCaseMember ediscoveryCaseMember = new com.microsoft.graph.models.security.EdiscoveryCaseMember();
ediscoveryCaseMember.setRecipientType(EnumSet.of(com.microsoft.graph.models.security.RecipientType.RoleGroup));
ediscoveryCaseMember.setDisplayName("Security Administrator");
com.microsoft.graph.models.security.EdiscoveryCaseMember result = graphClient.security().cases().ediscoveryCases().byEdiscoveryCaseId("{ediscoveryCase-id}").caseMembers().post(ediscoveryCaseMember);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const ediscoveryCaseMember = {
    recipientType: 'roleGroup',
    displayName: 'Security Administrator'
};

await client.api('/security/cases/ediscoveryCases/b0073e4e-4184-41c6-9eb7-8c8cc3e2288b/caseMembers')
	.post(ediscoveryCaseMember);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\Security\EdiscoveryCaseMember;
use Microsoft\Graph\Generated\Models\Security\RecipientType;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new EdiscoveryCaseMember();
$requestBody->setRecipientType(new RecipientType('roleGroup'));
$requestBody->setDisplayName('Security Administrator');

$result = $graphServiceClient->security()->cases()->ediscoveryCases()->byEdiscoveryCaseId('ediscoveryCase-id')->caseMembers()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Security

$params = @{
	recipientType = "roleGroup"
	displayName = "Security Administrator"
}

New-MgSecurityCaseEdiscoveryCaseMember -EdiscoveryCaseId $ediscoveryCaseId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.security.ediscovery_case_member import EdiscoveryCaseMember
from msgraph.generated.models.recipient_type import RecipientType
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = EdiscoveryCaseMember(
	recipient_type = RecipientType.RoleGroup,
	display_name = "Security Administrator",
)

result = await graph_client.security.cases.ediscovery_cases.by_ediscovery_case_id('ediscoveryCase-id').case_members.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
    "@odata.type": "microsoft.graph.security.ediscoveryCaseMember",
    "recipientType": "roleGroup",
    "id": "b9fb4f22-5f90-47a0-b309-44fe96a959fd",
    "displayName": "Security Administrator",
    "smtpAddress": ""
}
```

### Example 3: Add a case member of type **user** using **ID**

#### Request

The following example shows a request.

- [HTTP](#tabpanel_3_http)
- [C#](#tabpanel_3_csharp)
- [Go](#tabpanel_3_go)
- [Java](#tabpanel_3_java)
- [JavaScript](#tabpanel_3_javascript)
- [PHP](#tabpanel_3_php)
- [PowerShell](#tabpanel_3_powershell)
- [Python](#tabpanel_3_python)

```http
POST https://graph.microsoft.com/v1.0/security/cases/ediscoveryCases/b0073e4e-4184-41c6-9eb7-8c8cc3e2288b/caseMembers
Content-Type: application/json

{
    "recipientType": "user",
    "id": "c4af6f9d-37f6-43f9-9e17-601544234146"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models.Security;

var requestBody = new EdiscoveryCaseMember
{
	RecipientType = RecipientType.User,
	Id = "c4af6f9d-37f6-43f9-9e17-601544234146",
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Security.Cases.EdiscoveryCases["{ediscoveryCase-id}"].CaseMembers.PostAsync(requestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphmodelssecurity "github.com/microsoftgraph/msgraph-sdk-go/models/security"
	  //other-imports
)

requestBody := graphmodelssecurity.NewEdiscoveryCaseMember()
recipientType := graphmodels.USER_RECIPIENTTYPE 
requestBody.SetRecipientType(&recipientType) 
id := "c4af6f9d-37f6-43f9-9e17-601544234146"
requestBody.SetId(&id) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
caseMembers, err := graphClient.Security().Cases().EdiscoveryCases().ByEdiscoveryCaseId("ediscoveryCase-id").CaseMembers().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.models.security.EdiscoveryCaseMember ediscoveryCaseMember = new com.microsoft.graph.models.security.EdiscoveryCaseMember();
ediscoveryCaseMember.setRecipientType(EnumSet.of(com.microsoft.graph.models.security.RecipientType.User));
ediscoveryCaseMember.setId("c4af6f9d-37f6-43f9-9e17-601544234146");
com.microsoft.graph.models.security.EdiscoveryCaseMember result = graphClient.security().cases().ediscoveryCases().byEdiscoveryCaseId("{ediscoveryCase-id}").caseMembers().post(ediscoveryCaseMember);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const ediscoveryCaseMember = {
    recipientType: 'user',
    id: 'c4af6f9d-37f6-43f9-9e17-601544234146'
};

await client.api('/security/cases/ediscoveryCases/b0073e4e-4184-41c6-9eb7-8c8cc3e2288b/caseMembers')
	.post(ediscoveryCaseMember);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\Security\EdiscoveryCaseMember;
use Microsoft\Graph\Generated\Models\Security\RecipientType;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new EdiscoveryCaseMember();
$requestBody->setRecipientType(new RecipientType('user'));
$requestBody->setId('c4af6f9d-37f6-43f9-9e17-601544234146');

$result = $graphServiceClient->security()->cases()->ediscoveryCases()->byEdiscoveryCaseId('ediscoveryCase-id')->caseMembers()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Security

$params = @{
	recipientType = "user"
	id = "c4af6f9d-37f6-43f9-9e17-601544234146"
}

New-MgSecurityCaseEdiscoveryCaseMember -EdiscoveryCaseId $ediscoveryCaseId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.security.ediscovery_case_member import EdiscoveryCaseMember
from msgraph.generated.models.recipient_type import RecipientType
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = EdiscoveryCaseMember(
	recipient_type = RecipientType.User,
	id = "c4af6f9d-37f6-43f9-9e17-601544234146",
)

result = await graph_client.security.cases.ediscovery_cases.by_ediscovery_case_id('ediscoveryCase-id').case_members.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
    "@odata.type": "microsoft.graph.security.ediscoveryCaseMember",
    "recipientType": "user",
    "id": "c4af6f9d-37f6-43f9-9e17-601544234146",
    "displayName": "John Adams",
    "smtpAddress": "johnadams@microsoft.com"
}
```

### Example 4: Add a case member of type **roleGroup** using **ID**

#### Request

The following example shows a request.

- [HTTP](#tabpanel_4_http)
- [C#](#tabpanel_4_csharp)
- [Go](#tabpanel_4_go)
- [Java](#tabpanel_4_java)
- [JavaScript](#tabpanel_4_javascript)
- [PHP](#tabpanel_4_php)
- [PowerShell](#tabpanel_4_powershell)
- [Python](#tabpanel_4_python)

```http
POST https://graph.microsoft.com/v1.0/security/cases/ediscoveryCases/b0073e4e-4184-41c6-9eb7-8c8cc3e2288b/caseMembers
Content-Type: application/json

{
    "recipientType": "roleGroup",
    "id": "b9fb4f22-5f90-47a0-b309-44fe96a959fd"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models.Security;

var requestBody = new EdiscoveryCaseMember
{
	RecipientType = RecipientType.RoleGroup,
	Id = "b9fb4f22-5f90-47a0-b309-44fe96a959fd",
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Security.Cases.EdiscoveryCases["{ediscoveryCase-id}"].CaseMembers.PostAsync(requestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphmodelssecurity "github.com/microsoftgraph/msgraph-sdk-go/models/security"
	  //other-imports
)

requestBody := graphmodelssecurity.NewEdiscoveryCaseMember()
recipientType := graphmodels.ROLEGROUP_RECIPIENTTYPE 
requestBody.SetRecipientType(&recipientType) 
id := "b9fb4f22-5f90-47a0-b309-44fe96a959fd"
requestBody.SetId(&id) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
caseMembers, err := graphClient.Security().Cases().EdiscoveryCases().ByEdiscoveryCaseId("ediscoveryCase-id").CaseMembers().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.models.security.EdiscoveryCaseMember ediscoveryCaseMember = new com.microsoft.graph.models.security.EdiscoveryCaseMember();
ediscoveryCaseMember.setRecipientType(EnumSet.of(com.microsoft.graph.models.security.RecipientType.RoleGroup));
ediscoveryCaseMember.setId("b9fb4f22-5f90-47a0-b309-44fe96a959fd");
com.microsoft.graph.models.security.EdiscoveryCaseMember result = graphClient.security().cases().ediscoveryCases().byEdiscoveryCaseId("{ediscoveryCase-id}").caseMembers().post(ediscoveryCaseMember);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const ediscoveryCaseMember = {
    recipientType: 'roleGroup',
    id: 'b9fb4f22-5f90-47a0-b309-44fe96a959fd'
};

await client.api('/security/cases/ediscoveryCases/b0073e4e-4184-41c6-9eb7-8c8cc3e2288b/caseMembers')
	.post(ediscoveryCaseMember);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\Security\EdiscoveryCaseMember;
use Microsoft\Graph\Generated\Models\Security\RecipientType;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new EdiscoveryCaseMember();
$requestBody->setRecipientType(new RecipientType('roleGroup'));
$requestBody->setId('b9fb4f22-5f90-47a0-b309-44fe96a959fd');

$result = $graphServiceClient->security()->cases()->ediscoveryCases()->byEdiscoveryCaseId('ediscoveryCase-id')->caseMembers()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Security

$params = @{
	recipientType = "roleGroup"
	id = "b9fb4f22-5f90-47a0-b309-44fe96a959fd"
}

New-MgSecurityCaseEdiscoveryCaseMember -EdiscoveryCaseId $ediscoveryCaseId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.security.ediscovery_case_member import EdiscoveryCaseMember
from msgraph.generated.models.recipient_type import RecipientType
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = EdiscoveryCaseMember(
	recipient_type = RecipientType.RoleGroup,
	id = "b9fb4f22-5f90-47a0-b309-44fe96a959fd",
)

result = await graph_client.security.cases.ediscovery_cases.by_ediscovery_case_id('ediscoveryCase-id').case_members.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
    "@odata.type": "microsoft.graph.security.ediscoveryCaseMember",
    "recipientType": "roleGroup",
    "id": "b9fb4f22-5f90-47a0-b309-44fe96a959fd",
    "displayName": "Security Administrator",
    "smtpAddress": ""
}
```
