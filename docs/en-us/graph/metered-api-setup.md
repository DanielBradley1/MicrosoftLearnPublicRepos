<!-- Source: https://learn.microsoft.com/en-us/graph/metered-api-setup -->
<!-- Sitemap-Last-Modified: 2024-11-07 -->

# Enable metered APIs and services in Microsoft Graph

Some APIs and services in Microsoft Graph are [metered and require payment for use](https://learn.microsoft.com/en-us/graph/metered-api-overview). For a current list of APIs that require payment, see [Metered APIs and services in Microsoft Graph](https://learn.microsoft.com/en-us/graph/metered-api-list).

To consume metered APIs and services in Microsoft Graph, the application registration for the Microsoft Entra application that consumes the APIs must be associated with an Azure subscription. This subscription will be billed for any metered charges. This association also allows you to use [Azure Cost Management + Billing](https://learn.microsoft.com/en-us/azure/cost-management-billing/) to understand and manage the costs of the application.

This article describes how to associate your application with an Azure subscription.

## Known limitations

The following limitations apply to metered APIs:

- Metered APIs and services in Microsoft Graph are currently available only in the Microsoft global environment and not in national cloud deployments, including Microsoft 365 GCC deployments accessed through the worldwide Microsoft Graph endpoint. For details about national clouds, see [National cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).
- The target application must be a confidential client application \(for example, web application, web API, or daemon/service\). Public client applications \(desktop and mobile applications\) aren't supported.
- Azure managed identities aren't supported to call metered APIs. For more information, see [Azure services that support managed identities](https://learn.microsoft.com/en-us/entra/identity/managed-identities-azure-resources/managed-identities-status).

## Prerequisites

Before you can access metered APIs and services in Microsoft Graph, you must complete the following steps:

- Create an application registration in Microsoft Entra ID for the application that will be making calls to the metered Microsoft 365 APIs and services.
- If you don't have an Azure subscription, [create one](https://azure.microsoft.com/pricing/purchase-options/) now in the tenant that includes the application registration.
- You must have contributor permissions to the active Azure subscription you want to use, as well as application owner permissions for the target application registration.

## Enable an application

To enable an application to use metered APIs and services in Microsoft Graph, it must be associated with an Azure subscription. To create this association, you must create an Azure resource of type **Microsoft.GraphServices/accounts**. The Azure resource connects a single Microsoft Entra application registration with the Azure subscription where the application's usage of metered APIs is billed.

Use the following steps to create and link a **Microsoft.GraphServices/accounts** Azure resource to your application:

> **Note:** You can complete the following steps by signing in to [https://portal.azure.com](https://portal.azure.com) and choosing **Cloud Shell**, or by using your local Azure command-line interface. If you're using [Cloud Shell](https://learn.microsoft.com/en-us/azure/cloud-shell/overview) for the first time, you might need to create a storage account. Select an Azure subscription, choose **Create**, and follow the instructions to create a storage account. To use a local Azure command-line interface, install the [Azure CLI](https://learn.microsoft.com/en-us/cli/azure/).

1. If you have multiple Azure subscriptions, for information about setting the active subscription, see [Use multiple Azure subscriptions](https://learn.microsoft.com/en-us/powershell/azure/manage-subscriptions-azureps); otherwise, go to the next step.
2. Use [az graph-services](https://learn.microsoft.com/en-us/cli/azure/service-page/graph%20services) in [Azure Cloudshell](https://shell.azure.com/) or your own [Azure CLI](https://learn.microsoft.com/en-us/cli/azure/) installation to create a new instance of the **Microsoft.GraphServices/accounts** resource type to associate your application registration with the active subscription.

Copy the following command into your preferred command-line interface \(PowerShell, Bash, or Windows command prompt\), replace the parameters listed in the table with your own values, and type <**Enter**>. If the command succeeds, the response includes a JSON representation of the newly created billing resource.

```powershell
az graph-services account create --resource-group myRG  --resource-name myGraphAppBilling --subscription mySubscriptionGUID --location global --app-id AppRegGUID
```

| Parameter | Description |
| :--- | :--- |
| myRG | The name of an existing Azure resource group to add the newly created resource to. |
| myGraphAppBilling | The name you want to give to this resource instance. |
| myAppGUID | The Application \(client\) ID of the application being enabled, provided as a string parameter; for example, 123e4567-e89b-12d3-a456-426655440000. |
| mySubscriptionGUID | The ID of the Azure subscription that will receive billing events, provided as a string parameter; for example, 123e4567-e89b-12d3-a456-426655440000. |

A successful JSON result will look something like this:

```json
{
  "extendedLocation": null,
  "id": "/subscriptions/<mySubscriptionGUID>/resourceGroups/<myRG>/providers/Microsoft.GraphServices/accounts/<myGraphAppBilling>",
  "identity": null,
  "kind": null,
  "location": "Global",
  "managedBy": null,
  "name": "<myGraphAppBilling>",
  "plan": null,
  "properties": {
    "appId": "<myAppGUID>",
    "billingPlanId": "123e4567-e89b-12d3-a456-426655440000",
    "provisioningState": "Succeeded"
  },
  "resourceGroup": "<myRG>",
  "sku": null,
  "systemData": {
    "createdAt": "2023-01-31T00:12:20.7893671Z",
    "createdByType": "User",
    "lastModifiedAt": "2023-01-31T00:12:20.7893671Z",
    "lastModifiedByType": "User"
  },
  "tags": null,
  "type": "microsoft.graphservices/accounts"
}
```

## Verify setup

Use the following steps to verify that an application is properly enabled to use metered APIs and services in Microsoft Graph.

> **Note:** You can complete the following steps by signing in to [https://portal.azure.com](https://portal.azure.com) and choosing **Cloud Shell**, or by using your local Azure command-line interface. If you're using [Cloud Shell](https://learn.microsoft.com/en-us/azure/cloud-shell/overview) for the first time, you might need to create a storage account. Select an Azure subscription, choose **Create**, and follow the instructions to create a storage account. To use a local Azure command-line interface, install the [Azure CLI](https://learn.microsoft.com/en-us/cli/azure/).

1. If you have multiple Azure subscriptions, for information about setting the active subscription, see [Use multiple Azure subscriptions](https://learn.microsoft.com/en-us/powershell/azure/manage-subscriptions-azureps); otherwise, go to the next step.
2. Use **az resource list** to list the resources associated with the active Azure subscription. Copy the following command into your command-line interface and type <**Enter**>. If the command succeeds, the response will include a JSON representation of the resources associated with the active Azure subscription.

```powershell
  az resource list --resource-type Microsoft.GraphServices/accounts
```

A successful JSON result will look something like this:

```json
[
  {
    "changedTime": "2023-04-25T18:12:30.586342+00:00",
    "createdTime": "2023-04-25T18:02:30.141407+00:00",
    "extendedLocation": null,
    "id": "/subscriptions/<mySubscriptionGUID>/resourceGroups/<myRG>/providers/Microsoft.GraphServices/accounts/<myGraphAppBilling>",
    "identity": null,
    "kind": null,
    "location": "global",
    "managedBy": null,
    "name": "<myGraphAppBilling>",
    "plan": null,
    "properties": null,
    "provisioningState": "Succeeded",
    "resourceGroup": "<myRG>",
    "sku": null,
    "tags": null,
    "type": "Microsoft.GraphServices/accounts"
  }
]
```

3. With the values returned in step 2, use **az resource show** to show the full details of the resource. Copy the following command into your command-line interface, replace the parameters listed in the table with your own values, and type <**Enter**>. If the command succeeds, the response will include a JSON representation of the requested resource.

~~~powershell
  az resource show --resource-group myRg --name myGraphAppBilling --resource-type Microsoft.GraphServices/accounts

| Parameter | Description |
  |:--------------------------|:----------------------------------------|
  | myRG | The name of the Azure resource group provided in the result of step 2. |
  | myGraphAppBilling | The name of the resource provided in the result of step 2. |

  A successful JSON result will look something like this:

```json
{
  "extendedLocation": null,
  "id": "/subscriptions/<mySubscriptionGUID>/resourceGroups/<myRG>/providers/Microsoft.GraphServices/accounts/<myGraphAppBilling>",
  "identity": null,
  "kind": null,
  "location": "Global",
  "managedBy": null,
  "name": "<myGraphAppBilling>",
  "plan": null,
  "properties": {
    "appId": "<myAppGUID>",
    "billingPlanId": "123e4567-e89b-12d3-a456-426655440000"
  },
  "resourceGroup": "<myRG>",
  "sku": null,
  "tags": null,
  "type": "microsoft.graphservices/accounts"
}
~~~

The **properties** property will include the application ID of the associated application registration.

## Consume metered APIs in your application

After you associate your application registration and subscription, your application can start using metered APIs and services in Microsoft Graph. Costs generated from those requests will be charged to the Azure subscription associated with the application.

> **Note:** Your application might need to request a new OAuth access token before requests to metered APIs will be allowed.

You can monitor cost and usage of metered APIs and services in Microsoft Graph through [Azure Cost Management + Billing](https://learn.microsoft.com/en-us/azure/cost-management-billing/). This provides access to costs within the subscription, which can be split based on application, calling tenant, or meter.

## Bills for metered API and service usage

After the subscription billing cycle runs, typically on the 5th day of the month, a subscription owner or users with role-based permissions can download an invoice. For details, see [View and download your Azure invoice](https://learn.microsoft.com/en-us/azure/cost-management-billing/understand/download-azure-invoice).

The invoice will include details that allow you to understand the amount of usage your application generates, and for multi-tenant applications, where that usage is happening. For details, see [Understand your Azure invoice](https://learn.microsoft.com/en-us/azure/cost-management-billing/understand/understand-invoice).

## Related content

- [Overview of metered APIs and services in Microsoft Graph](https://learn.microsoft.com/en-us/graph/metered-api-overview)
- [Metered APIs and services in Microsoft Graph](https://learn.microsoft.com/en-us/graph/metered-api-list)
- [Metered APIs frequently asked questions](https://learn.microsoft.com/en-us/graph/metered-api-faq)
