<!-- Source: https://learn.microsoft.com/en-us/graph/api/admindynamics-update?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-04-05 -->

# Update adminDynamics

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Update the properties of a [adminDynamics](https://learn.microsoft.com/en-us/graph/api/resources/admindynamics?view=graph-rest-beta) object.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | OrgSettings-DynamicsVoice.ReadWrite.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | OrgSettings-DynamicsVoice.ReadWrite.All | Not available. |

## HTTP request

```http
PATCH /admin/dynamics
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
| customerVoice | [customerVoiceSettings](https://learn.microsoft.com/en-us/graph/api/resources/customervoicesettings?view=graph-rest-beta) | Company-wide settings for Dynamics customer voice. Required. |

## Response

If successful, this method returns a `200 OK` response code and an updated [adminDynamics](https://learn.microsoft.com/en-us/graph/api/resources/admindynamics?view=graph-rest-beta) object in the response body.

## Examples

### Request

The following example shows a request.

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [Python](#tabpanel_1_python)

```http
PATCH https://graph.microsoft.com/beta/admin/dynamics
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.adminDynamics",
  "customerVoice": {
    "@odata.type": "microsoft.graph.customerVoiceSettings",
    "isRestrictedSurveyAccessEnabled": "false",
    "isRecordIdentityByDefaultEnabled": "false",
    "isInOrgFormsPhishingScanEnabled": "false"
  }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.Models;

var requestBody = new AdminDynamics
{
	OdataType = "#microsoft.graph.adminDynamics",
	CustomerVoice = new CustomerVoiceSettings
	{
		OdataType = "microsoft.graph.customerVoiceSettings",
		IsRestrictedSurveyAccessEnabled = false,
		IsRecordIdentityByDefaultEnabled = false,
		IsInOrgFormsPhishingScanEnabled = false,
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Admin.Dynamics.PatchAsync(requestBody);
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

requestBody := graphmodels.NewAdminDynamics()
customerVoice := graphmodels.NewCustomerVoiceSettings()
isRestrictedSurveyAccessEnabled := false
customerVoice.SetIsRestrictedSurveyAccessEnabled(&isRestrictedSurveyAccessEnabled) 
isRecordIdentityByDefaultEnabled := false
customerVoice.SetIsRecordIdentityByDefaultEnabled(&isRecordIdentityByDefaultEnabled) 
isInOrgFormsPhishingScanEnabled := false
customerVoice.SetIsInOrgFormsPhishingScanEnabled(&isInOrgFormsPhishingScanEnabled) 
requestBody.SetCustomerVoice(customerVoice)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
dynamics, err := graphClient.Admin().Dynamics().Patch(context.Background(), requestBody, nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

AdminDynamics adminDynamics = new AdminDynamics();
adminDynamics.setOdataType("#microsoft.graph.adminDynamics");
CustomerVoiceSettings customerVoice = new CustomerVoiceSettings();
customerVoice.setOdataType("microsoft.graph.customerVoiceSettings");
customerVoice.setIsRestrictedSurveyAccessEnabled(false);
customerVoice.setIsRecordIdentityByDefaultEnabled(false);
customerVoice.setIsInOrgFormsPhishingScanEnabled(false);
adminDynamics.setCustomerVoice(customerVoice);
AdminDynamics result = graphClient.admin().dynamics().patch(adminDynamics);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const adminDynamics = {
  '@odata.type': '#microsoft.graph.adminDynamics',
  customerVoice: {
    '@odata.type': 'microsoft.graph.customerVoiceSettings',
    isRestrictedSurveyAccessEnabled: 'false',
    isRecordIdentityByDefaultEnabled: 'false',
    isInOrgFormsPhishingScanEnabled: 'false'
  }
};

await client.api('/admin/dynamics')
	.version('beta')
	.update(adminDynamics);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Models\AdminDynamics;
use Microsoft\Graph\Beta\Generated\Models\CustomerVoiceSettings;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new AdminDynamics();
$requestBody->setOdataType('#microsoft.graph.adminDynamics');
$customerVoice = new CustomerVoiceSettings();
$customerVoice->setOdataType('microsoft.graph.customerVoiceSettings');
$customerVoice->setIsRestrictedSurveyAccessEnabled(false);
$customerVoice->setIsRecordIdentityByDefaultEnabled(false);
$customerVoice->setIsInOrgFormsPhishingScanEnabled(false);
$requestBody->setCustomerVoice($customerVoice);

$result = $graphServiceClient->admin()->dynamics()->patch($requestBody)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.models.admin_dynamics import AdminDynamics
from msgraph_beta.generated.models.customer_voice_settings import CustomerVoiceSettings
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = AdminDynamics(
	odata_type = "#microsoft.graph.adminDynamics",
	customer_voice = CustomerVoiceSettings(
		odata_type = "microsoft.graph.customerVoiceSettings",
		is_restricted_survey_access_enabled = False,
		is_record_identity_by_default_enabled = False,
		is_in_org_forms_phishing_scan_enabled = False,
	),
)

result = await graph_client.admin.dynamics.patch(request_body)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 204 No Content
Content-Type: text/plain
```
