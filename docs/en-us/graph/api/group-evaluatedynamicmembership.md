<!-- Source: https://learn.microsoft.com/en-us/graph/api/group-evaluatedynamicmembership?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-23 -->

# group: evaluateDynamicMembership

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Evaluate whether a user or device is or would be a member of a dynamic [group](https://learn.microsoft.com/en-us/graph/api/resources/group?view=graph-rest-beta). The membership rule is returned along with other details that were used in the evaluation. You can complete this operation in the following ways:

- Evaluate whether a user or device is a member of a specified dynamic group.
- Evaluate whether a user or device would be a member of a dynamic group based on the ID of the user or device and a membership rule.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

The following table shows the least privileged permission or permissions required to call this API on each supported resource type. Follow [best practices](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions) to request least privileged permissions. For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

### Evaluate dynamic membership with member ID and group ID

| Supported resource | Delegated \(work or school account\) | Delegated \(personal Microsoft account\) | Application |
| :--- | :--- | :--- | :--- |
| [device](https://learn.microsoft.com/en-us/graph/api/resources/device?view=graph-rest-beta) | Group.Read.All and Device.Read.All | Not supported. | Not supported. |
| [user](https://learn.microsoft.com/en-us/graph/api/resources/user?view=graph-rest-beta) | Group.Read.All and User.Read.All | Not supported. | Not supported. |

### Evaluate dynamic membership with member ID and membership rule

| Supported resource | Delegated \(work or school account\) | Delegated \(personal Microsoft account\) | Application |
| :--- | :--- | :--- | :--- |
| [device](https://learn.microsoft.com/en-us/graph/api/resources/device?view=graph-rest-beta) | Device.Read.All | Not supported. | Not supported. |
| [user](https://learn.microsoft.com/en-us/graph/api/resources/user?view=graph-rest-beta) | User.Read.All | Not supported. | Not supported. |

## HTTP request

```http
POST /groups/{id}/evaluateDynamicMembership
POST /groups/evaluateDynamicMembership
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-type | application/json |

## Request body

In the request body, supply the required properties.

The following table lists the properties that are required when you evaluate group membership.

| Parameter | Type | Description |
| :--- | :--- | :--- |
| memberId | String collection | memberId is the object Id of the user or device to be evaluated. |
| membershipRule | String collection | The rule that is used for membership evaluation. If this property is not provided, the rule for the existing group is evaluated. If this property is provided, the user or device is evaluated for possible membership in a group with the same rule. For more information, see [Dynamic membership rules for groups in Microsoft Entra ID](https://learn.microsoft.com/en-us/azure/active-directory/users-groups-roles/groups-dynamic-membership). |

## Response

If successful, this method returns a `200 OK` response code and an [evaluateDynamicMembershipResult](https://learn.microsoft.com/en-us/graph/api/resources/evaluatedynamicmembershipresult?view=graph-rest-beta) object.

## Examples

### Example 1: Evaluate if a user or device is a member of an existing group

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
POST https://graph.microsoft.com/beta/groups/{id}/evaluateDynamicMembership
Content-type: application/json

{
  "memberId": "319b41e8-d9e4-42f8-bdc9-741113f48b33"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.Groups.Item.EvaluateDynamicMembership;

var requestBody = new EvaluateDynamicMembershipPostRequestBody
{
	MemberId = "319b41e8-d9e4-42f8-bdc9-741113f48b33",
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Groups["{group-id}"].EvaluateDynamicMembership.PostAsync(requestBody);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v0.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-beta-sdk-go"
	  graphgroups "github.com/microsoftgraph/msgraph-beta-sdk-go/groups"
	  //other-imports
)

requestBody := graphgroups.NewEvaluateDynamicMembershipPostRequestBody()
memberId := "319b41e8-d9e4-42f8-bdc9-741113f48b33"
requestBody.SetMemberId(&memberId) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
evaluateDynamicMembership, err := graphClient.Groups().ByGroupId("group-id").EvaluateDynamicMembership().Post(context.Background(), requestBody, nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.beta.groups.item.evaluatedynamicmembership.EvaluateDynamicMembershipPostRequestBody evaluateDynamicMembershipPostRequestBody = new com.microsoft.graph.beta.groups.item.evaluatedynamicmembership.EvaluateDynamicMembershipPostRequestBody();
evaluateDynamicMembershipPostRequestBody.setMemberId("319b41e8-d9e4-42f8-bdc9-741113f48b33");
var result = graphClient.groups().byGroupId("{group-id}").evaluateDynamicMembership().post(evaluateDynamicMembershipPostRequestBody);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const evaluateDynamicMembershipResult = {
  memberId: '319b41e8-d9e4-42f8-bdc9-741113f48b33'
};

await client.api('/groups/{id}/evaluateDynamicMembership')
	.version('beta')
	.post(evaluateDynamicMembershipResult);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Groups\Item\EvaluateDynamicMembership\EvaluateDynamicMembershipPostRequestBody;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new EvaluateDynamicMembershipPostRequestBody();
$requestBody->setMemberId('319b41e8-d9e4-42f8-bdc9-741113f48b33');

$result = $graphServiceClient->groups()->byGroupId('group-id')->evaluateDynamicMembership()->post($requestBody)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Beta.Groups

$params = @{
	memberId = "319b41e8-d9e4-42f8-bdc9-741113f48b33"
}

Test-MgBetaGroupDynamicMembership -GroupId $groupId -BodyParameter $params
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.groups.item.evaluate_dynamic_membership.evaluate_dynamic_membership_post_request_body import EvaluateDynamicMembershipPostRequestBody
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = EvaluateDynamicMembershipPostRequestBody(
	member_id = "319b41e8-d9e4-42f8-bdc9-741113f48b33",
)

result = await graph_client.groups.by_group_id('group-id').evaluate_dynamic_membership.post(request_body)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

```http
HTTP/1.1 200 OK
Content-type: application/json

{
  "membershipRule": "(user.displayName -startsWith \"EndTestUser\")",
  "membershipRuleEvaluationResult": true,
  "membershipRuleEvaluationDetails": {
    "expressionResult": true,
    "expression": "user.displayName -startsWith \"EndTestUser\"",
    "propertyToEvaluate": {
      "propertyName": "displayName",
      "propertyValue": "EndTestUser001"
    }
  }
}
```

### Example 2: Evaluate if a user or device would be a member of a group based on a membership rule

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
POST https://graph.microsoft.com/beta/groups/evaluateDynamicMembership
Content-type: application/json

{
  "memberId": "319b41e8-d9e4-42f8-bdc9-741113f48b33",
  "membershipRule": "(user.displayName -startsWith \"EndTestUser\")"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.Groups.EvaluateDynamicMembership;

var requestBody = new EvaluateDynamicMembershipPostRequestBody
{
	MemberId = "319b41e8-d9e4-42f8-bdc9-741113f48b33",
	MembershipRule = "(user.displayName -startsWith \"EndTestUser\")",
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Groups.EvaluateDynamicMembership.PostAsync(requestBody);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v0.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-beta-sdk-go"
	  graphgroups "github.com/microsoftgraph/msgraph-beta-sdk-go/groups"
	  //other-imports
)

requestBody := graphgroups.NewEvaluateDynamicMembershipPostRequestBody()
memberId := "319b41e8-d9e4-42f8-bdc9-741113f48b33"
requestBody.SetMemberId(&memberId) 
membershipRule := "(user.displayName -startsWith \"EndTestUser\")"
requestBody.SetMembershipRule(&membershipRule) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
evaluateDynamicMembership, err := graphClient.Groups().EvaluateDynamicMembership().Post(context.Background(), requestBody, nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.beta.groups.evaluatedynamicmembership.EvaluateDynamicMembershipPostRequestBody evaluateDynamicMembershipPostRequestBody = new com.microsoft.graph.beta.groups.evaluatedynamicmembership.EvaluateDynamicMembershipPostRequestBody();
evaluateDynamicMembershipPostRequestBody.setMemberId("319b41e8-d9e4-42f8-bdc9-741113f48b33");
evaluateDynamicMembershipPostRequestBody.setMembershipRule("(user.displayName -startsWith \"EndTestUser\")");
var result = graphClient.groups().evaluateDynamicMembership().post(evaluateDynamicMembershipPostRequestBody);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const evaluateDynamicMembershipResult = {
  memberId: '319b41e8-d9e4-42f8-bdc9-741113f48b33',
  membershipRule: '(user.displayName -startsWith \"EndTestUser\")'
};

await client.api('/groups/evaluateDynamicMembership')
	.version('beta')
	.post(evaluateDynamicMembershipResult);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Groups\EvaluateDynamicMembership\EvaluateDynamicMembershipPostRequestBody;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new EvaluateDynamicMembershipPostRequestBody();
$requestBody->setMemberId('319b41e8-d9e4-42f8-bdc9-741113f48b33');
$requestBody->setMembershipRule('(user.displayName -startsWith \"EndTestUser\")');

$result = $graphServiceClient->groups()->evaluateDynamicMembership()->post($requestBody)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Beta.Groups

$params = @{
	memberId = "319b41e8-d9e4-42f8-bdc9-741113f48b33"
	membershipRule = "(user.displayName -startsWith "EndTestUser")"
}

Test-MgBetaGroupDynamicMembershipRule -BodyParameter $params
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.groups.evaluate_dynamic_membership.evaluate_dynamic_membership_post_request_body import EvaluateDynamicMembershipPostRequestBody
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = EvaluateDynamicMembershipPostRequestBody(
	member_id = "319b41e8-d9e4-42f8-bdc9-741113f48b33",
	membership_rule = "(user.displayName -startsWith \"EndTestUser\")",
)

result = await graph_client.groups.evaluate_dynamic_membership.post(request_body)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

```http
HTTP/1.1 200 OK
Content-type: application/json

{
  "membershipRule": "(user.displayName -startsWith \"EndTestUser\")",
  "membershipRuleEvaluationResult": true,
  "membershipRuleEvaluationDetails": {
    "expressionResult": true,
    "expression": "user.displayName -startsWith \"EndTestUser\"",
    "propertyToEvaluate": {
      "propertyName": "displayName",
      "propertyValue": "EndTestUser001"
    }
  }
}
```
