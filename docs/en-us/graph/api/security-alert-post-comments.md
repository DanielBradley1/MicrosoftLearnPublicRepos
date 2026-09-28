<!-- Source: https://learn.microsoft.com/en-us/graph/api/security-alert-post-comments?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-03-19 -->

# Create comment for alert

Namespace: microsoft.graph

Create a comment for an existing [alert](https://learn.microsoft.com/en-us/graph/api/resources/security-alert?view=graph-rest-1.0) based on the specified alert **id** property.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | SecurityAlert.ReadWrite.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | SecurityAlert.ReadWrite.All | Not available. |

Important

For delegated access using work or school accounts, the signed-in user must be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) or a custom role that grants the permissions required for this operation. This operation supports the following built-in roles, which provide only the least privilege necessary:

- Security Operator
- Security Administrator

## HTTP request

```http
POST /security/alerts_v2/{alertId}/comments
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, use `@odata.type` to specify the parameter type of [alertComment](https://learn.microsoft.com/en-us/graph/api/resources/security-alertcomment?view=graph-rest-1.0), and provide a JSON object for the parameter, `comment`. See an [example](#examples).

| Parameter | Type | Description |
| :--- | :--- | :--- |
| comment | String | The comment to be added. |

## Response

If successful, this method returns a `200 OK` response code and an updated list of all [alertComment](https://learn.microsoft.com/en-us/graph/api/resources/security-alertcomment?view=graph-rest-1.0) resources for the specified alert.

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
POST https://graph.microsoft.com/v1.0/security/alerts_v2/da637865765418431569_-773071023/comments
Content-Type: application/json

{
    "@odata.type": "microsoft.graph.security.alertComment",
    "comment": "Demo for docs"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models.Security;

var requestBody = new AlertComment
{
	OdataType = "microsoft.graph.security.alertComment",
	Comment = "Demo for docs",
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Security.Alerts_v2["{alert-id}"].Comments.PostAsCommentsPostResponseAsync(requestBody);
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

requestBody := graphmodelssecurity.NewAlertComment()
comment := "Demo for docs"
requestBody.SetComment(&comment) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
comments, err := graphClient.Security().Alerts_v2().ByAlertId("alert-id").Comments().PostAsCommentsPostResponse(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.models.security.AlertComment alertComment = new com.microsoft.graph.models.security.AlertComment();
alertComment.setOdataType("microsoft.graph.security.alertComment");
alertComment.setComment("Demo for docs");
var result = graphClient.security().alertsV2().byAlertId("{alert-id}").comments().post(alertComment);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const alertComment = {
    '@odata.type': 'microsoft.graph.security.alertComment',
    comment: 'Demo for docs'
};

await client.api('/security/alerts_v2/da637865765418431569_-773071023/comments')
	.post(alertComment);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\Security\AlertComment;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new AlertComment();
$requestBody->setOdataType('microsoft.graph.security.alertComment');
$requestBody->setComment('Demo for docs');

$result = $graphServiceClient->security()->alerts_v2()->byAlertId('alert-id')->comments()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Security

$params = @{
	"@odata.type" = "microsoft.graph.security.alertComment"
	comment = "Demo for docs"
}

Set-MgSecurityAlert -AlertId $alertId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.security.alert_comment import AlertComment
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = AlertComment(
	odata_type = "microsoft.graph.security.alertComment",
	comment = "Demo for docs",
)

result = await graph_client.security.alerts_v2.by_alert_id('alert-id').comments.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#security/alerts_v2('da637865765418431569_-773071023')/comments",
    "value": [
        {
            "comment": "test",
            "createdByDisplayName": "secAdmin@contoso.com",
            "createdDateTime": "2022-10-13T07:08:30.1606766Z"
        },
        {
            "comment": "Demo for docs",
            "createdByDisplayName": "secAdmin@contoso.com",
            "createdDateTime": "2022-10-13T07:08:40.3825324Z"
        }
    ]
}
```
