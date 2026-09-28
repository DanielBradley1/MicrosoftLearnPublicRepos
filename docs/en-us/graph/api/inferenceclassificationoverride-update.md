<!-- Source: https://learn.microsoft.com/en-us/graph/api/inferenceclassificationoverride-update?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-23 -->

# Update inferenceclassificationoverride

Namespace: microsoft.graph

Change the **classifyAs** field of an override as specified.

You cannot use PATCH to change any other fields in an [inferenceClassificationOverride](https://learn.microsoft.com/en-us/graph/api/resources/inferenceclassificationoverride?view=graph-rest-1.0) instance.

If an override exists for a sender and the sender changes his/her display name, you can use [POST](https://learn.microsoft.com/en-us/graph/api/inferenceclassification-post-overrides?view=graph-rest-1.0) to force an update to the name field in the existing override.

If an override exists for a sender and the sender changes his/her SMTP address, [deleting](https://learn.microsoft.com/en-us/graph/api/inferenceclassificationoverride-delete?view=graph-rest-1.0) the existing override and [creating](https://learn.microsoft.com/en-us/graph/api/inferenceclassification-post-overrides?view=graph-rest-1.0) a new one with the new SMTP address is the only way to "update" the override for this sender.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Mail.ReadWrite | Not available. |
| Delegated \(personal Microsoft account\) | Mail.ReadWrite | Not available. |
| Application | Mail.ReadWrite | Not available. |

## HTTP request

```http
PATCH /me/inferenceClassification/overrides/{id}
PATCH /users/{id}/inferenceClassification/overrides/{id}
```

## Request headers

| Name | Type | Description |
| :--- | :--- | :--- |
| Authorization | string | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | string | Nature of the data in the body of an entity. Required. |

## Request body

In the request body, supply the new value for **classifyAs**. For best performance you shouldn't include existing values that are not changing.

| Property | Type | Description |
| :--- | :--- | :--- |
| classifyAs | string | Specifies how incoming messages from a specific sender should always be classified as. The possible values are: `focused`, `other`. |

## Response

If successful, this method returns a `200 OK` response code and updated [inferenceClassificationOverride](https://learn.microsoft.com/en-us/graph/api/resources/inferenceclassificationoverride?view=graph-rest-1.0) object in the response body.

## Example

### Request

The following example changes the override for the SMTP address randiw@contoso.com from `other` to `focused`.

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [PowerShell](#tabpanel_1_powershell)
- [Python](#tabpanel_1_python)

```http
PATCH https://graph.microsoft.com/v1.0/me/inferenceClassification/overrides/{id}
Content-type: application/json

{
  "classifyAs": "focused"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new InferenceClassificationOverride
{
	ClassifyAs = InferenceClassificationType.Focused,
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Me.InferenceClassification.Overrides["{inferenceClassificationOverride-id}"].PatchAsync(requestBody);
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

requestBody := graphmodels.NewInferenceClassificationOverride()
classifyAs := graphmodels.FOCUSED_INFERENCECLASSIFICATIONTYPE 
requestBody.SetClassifyAs(&classifyAs) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
overrides, err := graphClient.Me().InferenceClassification().Overrides().ByInferenceClassificationOverrideId("inferenceClassificationOverride-id").Patch(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

InferenceClassificationOverride inferenceClassificationOverride = new InferenceClassificationOverride();
inferenceClassificationOverride.setClassifyAs(InferenceClassificationType.Focused);
InferenceClassificationOverride result = graphClient.me().inferenceClassification().overrides().byInferenceClassificationOverrideId("{inferenceClassificationOverride-id}").patch(inferenceClassificationOverride);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const inferenceClassificationOverride = {
  classifyAs: 'focused'
};

await client.api('/me/inferenceClassification/overrides/{id}')
	.update(inferenceClassificationOverride);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\InferenceClassificationOverride;
use Microsoft\Graph\Generated\Models\InferenceClassificationType;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new InferenceClassificationOverride();
$requestBody->setClassifyAs(new InferenceClassificationType('focused'));

$result = $graphServiceClient->me()->inferenceClassification()->overrides()->byInferenceClassificationOverrideId('inferenceClassificationOverride-id')->patch($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Mail

$params = @{
	classifyAs = "focused"
}

# A UPN can also be used as -UserId.
Update-MgUserInferenceClassificationOverride -UserId $userId -InferenceClassificationOverrideId $inferenceClassificationOverrideId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.inference_classification_override import InferenceClassificationOverride
from msgraph.generated.models.inference_classification_type import InferenceClassificationType
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = InferenceClassificationOverride(
	classify_as = InferenceClassificationType.Focused,
)

result = await graph_client.me.inference_classification.overrides.by_inference_classification_override_id('inferenceClassificationOverride-id').patch(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-type: application/json

{
  "classifyAs": "focused",
  "senderEmailAddress": {
    "name": "Randi Welch",
    "address": "randiw@contoso.com"
  },
  "id": "98f5bdef-576a-404d-a2ea-07a3cf34af4r"
}
```
