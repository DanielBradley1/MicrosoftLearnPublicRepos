<!-- Source: https://learn.microsoft.com/en-us/graph/api/partners-billing-unbilledusage-export?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-12-03 -->

# unbilledUsage: export

Namespace: microsoft.graph.partners.billing

Note

This API is available for Cloud Solution Provider \(CSP\) partners only to access their billed and unbilled reconciliation data for a tenant. To learn more about the CSP program, see [Microsoft Cloud Solution Provider](https://learn.microsoft.com/en-us/partner-center/csp-overview).

Export unbilled Azure usage data for a specific billing period and currency.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

One of the following permissions is required to call this API. To learn more, including how to choose permissions, see [Permissions](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | PartnerBilling.Read.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | PartnerBilling.Read.All | Not available. |

## HTTP request

```http
POST /reports/partners/billing/usage/unbilled/export
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the parameters.

The following table shows the parameters that you can use with this action.

| Parameter | Type | Description |
| :--- | :--- | :--- |
| attributeSet | [microsoft.graph.partners.billing.attributeSet](https://learn.microsoft.com/en-us/graph/api/resources/partners-billing-attributeset?view=graph-rest-1.0) | Attributes that should be exported. The possible values are: `full`, `basic`, `unknownFutureValue`. The default value is `full`. Choose `full` for a complete response or `basic` for a subset of attributes. Optional. |
| billingPeriod | [microsoft.graph.partners.billing.billingPeriod](https://learn.microsoft.com/en-us/graph/api/resources/partners-billing-unbilledusage?view=graph-rest-1.0#billingperiod-values) | The billing period for the export data. The possible values are: `current`, `last`, `unknownFutureValue`. Choose `current` for the current billing period and `last` for the last billing period. Required. |
| currencyCode | String | The currency code for the partner billing. Required. |

## Response

If successful, this method returns a `202 Accepted` response code and a `Location` header that contains the URL to the long-running operation. You can check the status of the long-running operation by making a GET request to this URL that returns one of the following objects in the response body: [microsoft.graph.partners.billing.runningOperation](https://learn.microsoft.com/en-us/graph/api/resources/partners-billing-runningoperation?view=graph-rest-1.0), [microsoft.graph.partners.billing.exportSuccessOperation](https://learn.microsoft.com/en-us/graph/api/resources/partners-billing-exportsuccessoperation?view=graph-rest-1.0), or [microsoft.graph.partners.billing.failedOperation](https://learn.microsoft.com/en-us/graph/api/resources/partners-billing-failedoperation?view=graph-rest-1.0).

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
POST https://graph.microsoft.com/v1.0/reports/partners/billing/usage/unbilled/export
Content-Type: application/json

{
  "currencyCode": "USD",
  "attributeSet": "full",
  "billingPeriod": "current"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Reports.Partners.Billing.Usage.Unbilled.MicrosoftGraphPartnersBillingExport;
using Microsoft.Graph.Models.Partners.Billing;

var requestBody = new ExportPostRequestBody
{
	CurrencyCode = "USD",
	AttributeSet = AttributeSet.Full,
	BillingPeriod = BillingPeriod.Current,
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Reports.Partners.Billing.Usage.Unbilled.MicrosoftGraphPartnersBillingExport.PostAsync(requestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphreports "github.com/microsoftgraph/msgraph-sdk-go/reports"
	  graphmodelspartnersbilling "github.com/microsoftgraph/msgraph-sdk-go/models/partners/billing"
	  //other-imports
)

requestBody := graphreports.NewExportPostRequestBody()
currencyCode := "USD"
requestBody.SetCurrencyCode(&currencyCode) 
attributeSet := graphmodels.FULL_ATTRIBUTESET 
requestBody.SetAttributeSet(&attributeSet) 
billingPeriod := graphmodels.CURRENT_BILLINGPERIOD 
requestBody.SetBillingPeriod(&billingPeriod) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
microsoftGraphPartnersBillingExport, err := graphClient.Reports().Partners().Billing().Usage().Unbilled().MicrosoftGraphPartnersBillingExport().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.reports.partners.billing.usage.unbilled.microsoftgraphpartnersbillingexport.ExportPostRequestBody exportPostRequestBody = new com.microsoft.graph.reports.partners.billing.usage.unbilled.microsoftgraphpartnersbillingexport.ExportPostRequestBody();
exportPostRequestBody.setCurrencyCode("USD");
exportPostRequestBody.setAttributeSet(com.microsoft.graph.models.partners.billing.AttributeSet.Full);
exportPostRequestBody.setBillingPeriod(com.microsoft.graph.models.partners.billing.BillingPeriod.Current);
var result = graphClient.reports().partners().billing().usage().unbilled().microsoftGraphPartnersBillingExport().post(exportPostRequestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const operation = {
  currencyCode: 'USD',
  attributeSet: 'full',
  billingPeriod: 'current'
};

await client.api('/reports/partners/billing/usage/unbilled/export')
	.post(operation);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Reports\Partners\Billing\Usage\Unbilled\MicrosoftGraphPartnersBillingExport\ExportPostRequestBody;
use Microsoft\Graph\Generated\Models\Partners\Billing\AttributeSet;
use Microsoft\Graph\Generated\Models\Partners\Billing\BillingPeriod;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new ExportPostRequestBody();
$requestBody->setCurrencyCode('USD');
$requestBody->setAttributeSet(new AttributeSet('full'));
$requestBody->setBillingPeriod(new BillingPeriod('current'));

$result = $graphServiceClient->reports()->partners()->billing()->usage()->unbilled()->microsoftGraphPartnersBillingExport()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Reports

$params = @{
	currencyCode = "USD"
	attributeSet = "full"
	billingPeriod = "current"
}

Export-MgReportPartnerBillingUsageUnbilled -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.reports.partners.billing.usage.unbilled.microsoft_graph_partners_billing_export.export_post_request_body import ExportPostRequestBody
from msgraph.generated.models.attribute_set import AttributeSet
from msgraph.generated.models.billing_period import BillingPeriod
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = ExportPostRequestBody(
	currency_code = "USD",
	attribute_set = AttributeSet.Full,
	billing_period = BillingPeriod.Current,
)

result = await graph_client.reports.partners.billing.usage.unbilled.microsoft_graph_partners_billing_export.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

```http
HTTP/1.1 202 Accepted
Content-Type: application/json
Location: https://graph.microsoft.com/v1.0/reports/partners/billing/operations/9ab9cb54-d07f-4f52-9ea6-a09d7de52c14
```
