<!-- Source: https://learn.microsoft.com/en-us/entra/identity/domain-services/change-sku -->
<!-- Sitemap-Last-Modified: 2025-01-21 -->

# Change the SKU for an existing Microsoft Entra Domain Services managed domain

In Microsoft Entra Domain Services, the available performance and features are based on the SKU type. These feature differences include the backup frequency or maximum number of one-way outbound forest trusts.

You select a SKU when you create the managed domain, and you can switch SKUs up or down as your business needs change after the managed domain has been deployed. Changes in business requirements could include the need for more frequent backups or to create additional forest trusts. For more information on the limits and pricing of the different SKUs, see [Domain Services SKU concepts](https://learn.microsoft.com/en-us/entra/identity/domain-services/administration-concepts#azure-ad-ds-skus) and [Domain Services pricing](https://azure.microsoft.com/pricing/details/active-directory-ds/) pages.

This article shows you how to change the SKU for an existing Domain Services managed domain using the [Microsoft Entra admin center](https://entra.microsoft.com).

## Before you begin

To complete this article, you need the following resources and privileges:

- An active Azure subscription.

  - If you don't have an Azure subscription, [create an account](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn).

- A Microsoft Entra tenant associated with your subscription, either synchronized with an on-premises directory or a cloud-only directory.

  - If needed, [create a Microsoft Entra tenant](https://learn.microsoft.com/en-us/azure/active-directory/fundamentals/sign-up-organization) or [associate an Azure subscription with your account](https://learn.microsoft.com/en-us/azure/active-directory/fundamentals/how-subscriptions-associated-directory).

- A Microsoft Entra Domain Services managed domain enabled and configured in your Microsoft Entra tenant.

  - If needed, complete the tutorial to [create and configure a managed domain](https://learn.microsoft.com/en-us/entra/identity/domain-services/tutorial-create-instance).

## SKU change limitations

You can change SKUs up or down after the managed domain has been deployed. However, the *Premium* and *Enterprise* SKUs define a limit on the number of trusts you can create. You can't change to a SKU with a lower maximum limit than you currently have configured.

For example, if you have created seven trusts on the *Premium* SKU, you can't change down to the *Enterprise* SKU. The *Enterprise* SKU supports a maximum of five trusts.

For more information on these limits, see [Domain Services SKU features and limits](https://learn.microsoft.com/en-us/entra/identity/domain-services/administration-concepts#azure-ad-ds-skus).

## Select a new SKU

To change the SKU for a managed domain using the [Microsoft Entra admin center](https://entra.microsoft.com), complete the following steps:

1. In the [Microsoft Entra admin center](https://entra.microsoft.com), search for and select **Microsoft Entra Domain Services**. Choose your managed domain from the list, such as *aaddscontoso.com*.
2. In the menu on the left-hand side of the Domain Services page, select **Settings > SKU**.

   ![Select the SKU menu option for your Domain Services managed domain in the Microsoft Entra admin center](https://learn.microsoft.com/en-us/entra/identity/domain-services/media/change-sku/overview-change-sku.png)

3. From the drop-down menu, select the SKU you wish for your managed domain. If you have a resource forest, you can't select *Standard* SKU as forest trusts are only available on the *Enterprise* SKU or higher.

   Choose the SKU you want from the drop-down menu, then select **Save**.

   ![Choose the required SKU from the drop-down menu in the Microsoft Entra admin center](https://learn.microsoft.com/en-us/entra/identity/domain-services/media/change-sku/change-sku-selection.png)

It can take a minute or two to change the SKU type.

## Next steps

If you have a resource forest and want to create additional trusts after the SKU change, see [Create an outbound forest trust to an on-premises domain in Domain Services](https://learn.microsoft.com/en-us/entra/identity/domain-services/tutorial-create-forest-trust).
