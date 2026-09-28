<!-- Source: https://learn.microsoft.com/en-us/graph/api/programcontrol-create?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-23 -->

# Create programControl \(deprecated\)

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Caution

This version of the access review API is deprecated and will stop returning data on May 19, 2023. Please use [access reviews API](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewsv2-overview?view=graph-rest-beta&preserve-view=true).

In the Microsoft Entra [access reviews](https://learn.microsoft.com/en-us/graph/api/resources/accessreviews-root?view=graph-rest-beta) feature, create a new [programControl](https://learn.microsoft.com/en-us/graph/api/resources/programcontrol?view=graph-rest-beta) object. This links an access review to a program.

Prior to making this request, the caller must have previously

- [created a program](https://learn.microsoft.com/en-us/graph/api/program-create?view=graph-rest-beta) or [retrieved a program](https://learn.microsoft.com/en-us/graph/api/program-list?view=graph-rest-beta), to have the value of `programId` to include in the request,
- [created an access review](https://learn.microsoft.com/en-us/graph/api/accessreview-create?view=graph-rest-beta) or [retrieved an access review](https://learn.microsoft.com/en-us/graph/api/accessreview-get?view=graph-rest-beta), to have the value of `controlId` to include in the request, and
- [retrieved the list of program control types](https://learn.microsoft.com/en-us/graph/api/programcontroltype-list?view=graph-rest-beta), to have the value of `controlTypeId` to include in the request.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | ProgramControl.ReadWrite.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | ProgramControl.ReadWrite.All | Not available. |

The signed in user must also be in a directory role that permits them to create a **programControl**.

## HTTP request

```http
POST /programControls
```

## Request headers

| Name | Type | Description |
| :--- | :--- | :--- |
| Authorization | string | Bearer {token}. Required. |

## Request body

In the request body, supply a JSON representation of a [programControl](https://learn.microsoft.com/en-us/graph/api/resources/programcontrol?view=graph-rest-beta) object.

The following table shows the properties that are required when you create a program control.

| Property | Type | Description |
| :--- | :--- | :--- |
| `programId` | `String` | The programId of the program this control is going to become a part of. |
| `controlId` | `String` | The controlId of the control, in particular the identifier of an access review. |
| `controlTypeId` | `String` | The programControlType identifies the type of program control - for example, a control linking to guest access reviews. |

## Response

If successful, this method returns a `201, Created` response code and a [programControl](https://learn.microsoft.com/en-us/graph/api/resources/programcontrol?view=graph-rest-beta) object in the response body.

## Example

### Request

In the request body, supply a JSON representation of the [programControl](https://learn.microsoft.com/en-us/graph/api/resources/programcontrol?view=graph-rest-beta) object.

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [PowerShell](#tabpanel_1_powershell)
- [Python](#tabpanel_1_python)

```http
POST https://graph.microsoft.com/beta/programControls
Content-type: application/json

{
    "controlId": "7e59d237-2fb0-4e5d-b7bb-d4f9f9129213",
    "controlTypeId": "6e4f3d20-c5c3-407f-9695-8460952bcc68",
    "programId": "7e59d237-2fb0-4e5d-b7bb-d4f9f9129213"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.Models;

var requestBody = new ProgramControl
{
	ControlId = "7e59d237-2fb0-4e5d-b7bb-d4f9f9129213",
	ControlTypeId = "6e4f3d20-c5c3-407f-9695-8460952bcc68",
	ProgramId = "7e59d237-2fb0-4e5d-b7bb-d4f9f9129213",
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.ProgramControls.PostAsync(requestBody);
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
	  graphmodels "github.com/microsoftgraph/msgraph-beta-sdk-go/models"
	  //other-imports
)

requestBody := graphmodels.NewProgramControl()
controlId := "7e59d237-2fb0-4e5d-b7bb-d4f9f9129213"
requestBody.SetControlId(&controlId) 
controlTypeId := "6e4f3d20-c5c3-407f-9695-8460952bcc68"
requestBody.SetControlTypeId(&controlTypeId) 
programId := "7e59d237-2fb0-4e5d-b7bb-d4f9f9129213"
requestBody.SetProgramId(&programId) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
programControls, err := graphClient.ProgramControls().Post(context.Background(), requestBody, nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

ProgramControl programControl = new ProgramControl();
programControl.setControlId("7e59d237-2fb0-4e5d-b7bb-d4f9f9129213");
programControl.setControlTypeId("6e4f3d20-c5c3-407f-9695-8460952bcc68");
programControl.setProgramId("7e59d237-2fb0-4e5d-b7bb-d4f9f9129213");
ProgramControl result = graphClient.programControls().post(programControl);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const programControl = {
    controlId: '7e59d237-2fb0-4e5d-b7bb-d4f9f9129213',
    controlTypeId: '6e4f3d20-c5c3-407f-9695-8460952bcc68',
    programId: '7e59d237-2fb0-4e5d-b7bb-d4f9f9129213'
};

await client.api('/programControls')
	.version('beta')
	.post(programControl);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Models\ProgramControl;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new ProgramControl();
$requestBody->setControlId('7e59d237-2fb0-4e5d-b7bb-d4f9f9129213');
$requestBody->setControlTypeId('6e4f3d20-c5c3-407f-9695-8460952bcc68');
$requestBody->setProgramId('7e59d237-2fb0-4e5d-b7bb-d4f9f9129213');

$result = $graphServiceClient->programControls()->post($requestBody)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Beta.Identity.Governance

$params = @{
	controlId = "7e59d237-2fb0-4e5d-b7bb-d4f9f9129213"
	controlTypeId = "6e4f3d20-c5c3-407f-9695-8460952bcc68"
	programId = "7e59d237-2fb0-4e5d-b7bb-d4f9f9129213"
}

New-MgBetaProgramControl -BodyParameter $params
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.models.program_control import ProgramControl
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = ProgramControl(
	control_id = "7e59d237-2fb0-4e5d-b7bb-d4f9f9129213",
	control_type_id = "6e4f3d20-c5c3-407f-9695-8460952bcc68",
	program_id = "7e59d237-2fb0-4e5d-b7bb-d4f9f9129213",
)

result = await graph_client.program_controls.post(request_body)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-type: application/json

{
  "id": "63b2302c-7e62-43b7-aefb-063ba5bdb853",
  "controlId": "7e59d237-2fb0-4e5d-b7bb-d4f9f9129213",
  "programId": "7e59d237-2fb0-4e5d-b7bb-d4f9f9129213",
  "controlTypeId": "6e4f3d20-c5c3-407f-9695-8460952bcc68",
  "displayName": "test",
  "status": "Active",
  "createdDateTime": "2018-05-18T20:26:05.2976279Z"
}
```

## Related content

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List programControlTypes](https://learn.microsoft.com/en-us/graph/api/programcontroltype-list?view=graph-rest-beta) | [programControlType](https://learn.microsoft.com/en-us/graph/api/resources/programcontroltype?view=graph-rest-beta) collection | List program control types. |
