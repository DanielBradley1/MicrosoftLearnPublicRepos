<!-- Source: https://learn.microsoft.com/en-us/graph/api/security-securitycopilot-session-post-prompts?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-08-26 -->

# Create prompt

Namespace: microsoft.graph.security.securityCopilot

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Create a new [prompt](https://learn.microsoft.com/en-us/graph/api/resources/security-securitycopilot-prompt?view=graph-rest-beta) in a Security Copilot session.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | SecurityCopilotWorkspaces.ReadWrite.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | SecurityCopilotWorkspaces.ReadWrite.All | Not available. |

Important

For delegated access using work or school accounts, the signed-in user must be assigned a supported [Microsoft Security Copilot role](https://learn.microsoft.com/en-us/copilot/security/authentication). *Security Copilot Contributor* is the least privileged role supported for this operation.

## HTTP request

```http
POST /security/securityCopilot/workspaces/{workspaceId}/sessions/{sessionId}/prompts
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the [microsoft.graph.security.securityCopilot.prompt](https://learn.microsoft.com/en-us/graph/api/resources/security-securitycopilot-prompt?view=graph-rest-beta) object.

You can specify the following properties when creating a **prompt**.

| Property | Type | Description |
| :--- | :--- | :--- |
| type | microsoft.graph.security.securityCopilot.promptType | The type of input prompts. The possible values are: `unknown`, `context`, `prompt`, `skill`, `feedback`, `unknownFutureValue`. **Only `prompt` is currently supported.** |
| content | String | Input text when used with type `prompt` for evaluation. Required for AI evaluation. |

## Response

If successful, this method returns a `201 Created` response code and a [microsoft.graph.security.securityCopilot.prompt](https://learn.microsoft.com/en-us/graph/api/resources/security-securitycopilot-prompt?view=graph-rest-beta) object in the response body.

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
POST https://graph.microsoft.com/beta/security/securityCopilot/workspaces/default/sessions/ecdfb9b3-58f5-457f-a18c-4a477890b252/prompts
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.security.securityCopilot.prompt",
  "type": "prompt",
  "content": "who am I",
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.Models.Security.SecurityCopilot;

var requestBody = new Prompt
{
	OdataType = "#microsoft.graph.security.securityCopilot.prompt",
	Type = PromptType.Prompt,
	Content = "who am I",
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Security.SecurityCopilot.Workspaces["{workspace-id}"].Sessions["{session-id}"].Prompts.PostAsync(requestBody);
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
	  graphmodelssecuritysecuritycopilot "github.com/microsoftgraph/msgraph-beta-sdk-go/models/security/securitycopilot"
	  //other-imports
)

requestBody := graphmodelssecuritysecuritycopilot.NewPrompt()
type := graphmodels.PROMPT_PROMPTTYPE 
requestBody.SetType(&type) 
content := "who am I"
requestBody.SetContent(&content) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
prompts, err := graphClient.Security().SecurityCopilot().Workspaces().ByWorkspaceId("workspace-id").Sessions().BySessionId("session-id").Prompts().Post(context.Background(), requestBody, nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.beta.models.security.securitycopilot.Prompt prompt = new com.microsoft.graph.beta.models.security.securitycopilot.Prompt();
prompt.setOdataType("#microsoft.graph.security.securityCopilot.prompt");
prompt.setType(com.microsoft.graph.beta.models.security.securitycopilot.PromptType.Prompt);
prompt.setContent("who am I");
com.microsoft.graph.models.security.securitycopilot.Prompt result = graphClient.security().securityCopilot().workspaces().byWorkspaceId("{workspace-id}").sessions().bySessionId("{session-id}").prompts().post(prompt);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const prompt = {
  '@odata.type': '#microsoft.graph.security.securityCopilot.prompt',
  type: 'prompt',
  content: 'who am I',
};

await client.api('/security/securityCopilot/workspaces/default/sessions/ecdfb9b3-58f5-457f-a18c-4a477890b252/prompts')
	.version('beta')
	.post(prompt);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Models\Security\SecurityCopilot\Prompt;
use Microsoft\Graph\Beta\Generated\Models\Security\SecurityCopilot\PromptType;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new Prompt();
$requestBody->setOdataType('#microsoft.graph.security.securityCopilot.prompt');
$requestBody->setType(new PromptType('prompt'));
$requestBody->setContent('who am I');

$result = $graphServiceClient->security()->securityCopilot()->workspaces()->byWorkspaceId('workspace-id')->sessions()->bySessionId('session-id')->prompts()->post($requestBody)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Beta.Security

$params = @{
	"@odata.type" = "#microsoft.graph.security.securityCopilot.prompt"
	type = "prompt"
	content = "who am I"
}

New-MgBetaSecurityCopilotWorkspaceSessionPrompt -WorkspaceId $workspaceId -SessionId $sessionId -BodyParameter $params
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.models.security.security_copilot.prompt import Prompt
from msgraph_beta.generated.models.prompt_type import PromptType
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = Prompt(
	odata_type = "#microsoft.graph.security.securityCopilot.prompt",
	type = PromptType.Prompt,
	content = "who am I",
)

result = await graph_client.security.security_copilot.workspaces.by_workspace_id('workspace-id').sessions.by_session_id('session-id').prompts.post(request_body)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-Type: application/json

{
    "@odata.context": "https://graph.microsoft.com/beta/$metadata#security/securityCopilot/workspaces('default')/sessions('ecdfb9b3-58f5-457f-a18c-4a477890b252')/prompts/$entity",
    "id": "76a9b8c6-6656-4ef4-a4c7-7ed07fb93e01",
    "type": "prompt",
    "createdDateTime": "2025-10-22T20:12:13.759634Z",
    "lastModifiedDateTime": "2025-10-22T20:12:13.759634Z",
    "skillName": null,
    "content": "who am I",
    "inputs": {
        "keyValuePairs": []
    },
    "skillInputDescriptors": []
}
```
