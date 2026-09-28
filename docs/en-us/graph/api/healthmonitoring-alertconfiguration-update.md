<!-- Source: https://learn.microsoft.com/en-us/graph/api/healthmonitoring-alertconfiguration-update?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-11-08 -->

# Update alertConfiguration

Namespace: microsoft.graph.healthMonitoring

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Update the properties of a Microsoft Entra health monitoring [alertConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/healthmonitoring-alertconfiguration?view=graph-rest-beta) object. You can use alertConfiguration settings to specify the distribution groups where alert notifications are to be sent.

This API doesn't currently support group validation.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | HealthMonitoringAlertConfig.ReadWrite.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Not supported. | Not supported. |

Important

For delegated access using work or school accounts, the admin must be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json). This operation supports the following built-in roles, which provide only the least privilege necessary:

- Security Administrator
- Helpdesk Administrator

## HTTP request

```http
PATCH /reports/healthMonitoring/alertConfigurations/{alertConfigurationId}
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
| emailNotificationConfigurations | [microsoft.graph.healthMonitoring.emailNotificationConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/healthmonitoring-emailnotificationconfiguration?view=graph-rest-beta) collection | Email notification settings for the particular alert type. Currently, only one email notification configuration is supported for an alert configuration, meaning just one group will receive notifications for an alert type. |

## Response

If successful, this method returns a `200 OK` response code and an updated [microsoft.graph.healthMonitoring.alertConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/healthmonitoring-alertconfiguration?view=graph-rest-beta) object in the response body.

## Examples

### Request

The following example shows a request. It currently supports only 1 group to receive email notification for an alert type.

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [PowerShell](#tabpanel_1_powershell)
- [Python](#tabpanel_1_python)

```http
PATCH https://graph.microsoft.com/beta/reports/healthMonitoring/alertConfigurations/{alertConfigurationId}
Content-Type: application/json

{
  "emailNotificationConfigurations": [
    {
      "groupId":"c5140914-9507-4180-b60c-04d5ec5eddcb",
      "isEnabled": true
    }
  ]
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.Models.HealthMonitoring;

var requestBody = new AlertConfiguration
{
	EmailNotificationConfigurations = new List<EmailNotificationConfiguration>
	{
		new EmailNotificationConfiguration
		{
			GroupId = "c5140914-9507-4180-b60c-04d5ec5eddcb",
			IsEnabled = true,
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Reports.HealthMonitoring.AlertConfigurations["{alertConfiguration-id}"].PatchAsync(requestBody);
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
	  graphmodelshealthmonitoring "github.com/microsoftgraph/msgraph-beta-sdk-go/models/healthmonitoring"
	  //other-imports
)

requestBody := graphmodelshealthmonitoring.NewAlertConfiguration()


emailNotificationConfiguration := graphmodelshealthmonitoring.NewEmailNotificationConfiguration()
groupId := "c5140914-9507-4180-b60c-04d5ec5eddcb"
emailNotificationConfiguration.SetGroupId(&groupId) 
isEnabled := true
emailNotificationConfiguration.SetIsEnabled(&isEnabled) 

emailNotificationConfigurations := []graphmodelshealthmonitoring.EmailNotificationConfigurationable {
	emailNotificationConfiguration,
}
requestBody.SetEmailNotificationConfigurations(emailNotificationConfigurations)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
alertConfigurations, err := graphClient.Reports().HealthMonitoring().AlertConfigurations().ByAlertConfigurationId("alertConfiguration-id").Patch(context.Background(), requestBody, nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.beta.models.healthmonitoring.AlertConfiguration alertConfiguration = new com.microsoft.graph.beta.models.healthmonitoring.AlertConfiguration();
LinkedList<com.microsoft.graph.beta.models.healthmonitoring.EmailNotificationConfiguration> emailNotificationConfigurations = new LinkedList<com.microsoft.graph.beta.models.healthmonitoring.EmailNotificationConfiguration>();
com.microsoft.graph.beta.models.healthmonitoring.EmailNotificationConfiguration emailNotificationConfiguration = new com.microsoft.graph.beta.models.healthmonitoring.EmailNotificationConfiguration();
emailNotificationConfiguration.setGroupId("c5140914-9507-4180-b60c-04d5ec5eddcb");
emailNotificationConfiguration.setIsEnabled(true);
emailNotificationConfigurations.add(emailNotificationConfiguration);
alertConfiguration.setEmailNotificationConfigurations(emailNotificationConfigurations);
com.microsoft.graph.models.healthmonitoring.AlertConfiguration result = graphClient.reports().healthMonitoring().alertConfigurations().byAlertConfigurationId("{alertConfiguration-id}").patch(alertConfiguration);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const alertConfiguration = {
  emailNotificationConfigurations: [
    {
      groupId: 'c5140914-9507-4180-b60c-04d5ec5eddcb',
      isEnabled: true
    }
  ]
};

await client.api('/reports/healthMonitoring/alertConfigurations/{alertConfigurationId}')
	.version('beta')
	.update(alertConfiguration);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Models\HealthMonitoring\AlertConfiguration;
use Microsoft\Graph\Beta\Generated\Models\HealthMonitoring\EmailNotificationConfiguration;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new AlertConfiguration();
$emailNotificationConfigurationsEmailNotificationConfiguration1 = new EmailNotificationConfiguration();
$emailNotificationConfigurationsEmailNotificationConfiguration1->setGroupId('c5140914-9507-4180-b60c-04d5ec5eddcb');
$emailNotificationConfigurationsEmailNotificationConfiguration1->setIsEnabled(true);
$emailNotificationConfigurationsArray []= $emailNotificationConfigurationsEmailNotificationConfiguration1;
$requestBody->setEmailNotificationConfigurations($emailNotificationConfigurationsArray);


$result = $graphServiceClient->reports()->healthMonitoring()->alertConfigurations()->byAlertConfigurationId('alertConfiguration-id')->patch($requestBody)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Beta.Reports

$params = @{
	emailNotificationConfigurations = @(
		@{
			groupId = "c5140914-9507-4180-b60c-04d5ec5eddcb"
			isEnabled = $true
		}
	)
}

Update-MgBetaReportHealthMonitoringAlertConfiguration -AlertConfigurationId $alertConfigurationId -BodyParameter $params
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.models.health_monitoring.alert_configuration import AlertConfiguration
from msgraph_beta.generated.models.health_monitoring.email_notification_configuration import EmailNotificationConfiguration
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = AlertConfiguration(
	email_notification_configurations = [
		EmailNotificationConfiguration(
			group_id = "c5140914-9507-4180-b60c-04d5ec5eddcb",
			is_enabled = True,
		),
	],
)

result = await graph_client.reports.health_monitoring.alert_configurations.by_alert_configuration_id('alertConfiguration-id').patch(request_body)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "@odata.context": "https://graph.microsoft.com/beta/$metadata#reports/healthMonitoring/alertConfigurations/$entity",
  "id": "mfaSignInFailure",
  "emailNotificationConfigurations": [
    {
      "groupId": "c5140914-9507-4180-b60c-04d5ec5eddcb",
      "isEnabled": true
    }
  ]
}
```
