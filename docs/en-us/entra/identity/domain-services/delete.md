<!-- Source: https://learn.microsoft.com/en-us/entra/identity/domain-services/delete -->
<!-- Sitemap-Last-Modified: 2025-01-21 -->

# Delete a Microsoft Entra Domain Services managed domain

If you no longer need a Microsoft Entra Domain Services managed domain, you can delete it. There's no way to turn off or temporarily disable a Domain Services managed domain. Deleting the managed domain doesn't delete or have any other impact on the Microsoft Entra tenant.

This article shows you how to use the Microsoft Entra admin center to delete a managed domain.

Warning

**Deletion is permanent and can't be reversed.** When you delete a managed domain, the following steps occur:

- Domain controllers for the managed domain are deprovisioned and removed from the virtual network.
- Data on the managed domain is deleted permanently. This data includes custom OUs, GPOs, custom DNS records, service principals, GMSAs, and so on. that you created.
- Machines joined to the managed domain lose their trust relationship with the domain and need to be unjoined from the domain.
- You can't sign in to these machines using corporate AD credentials. Instead, you must use the local administrator credentials for the machine.

## Delete the managed domain

To delete a managed domain, complete the following steps:

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as a [Global Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#global-administrator).
2. Search for and select **Microsoft Entra Domain Services**.
3. Select the name of your managed domain, such as *aaddscontoso.com*.
4. On the **Overview** page, select **Delete**. To confirm the deletion, type the domain name of the managed domain again, then select **Delete**.

It can take 15-20 minutes or more to delete the managed domain.

## Next steps

Consider [sharing feedback](https://feedback.azure.com/d365community/forum/22920db1-ad25-ec11-b6e6-000d3a4f0789?c=5d63b5b7-ae25-ec11-b6e6-000d3a4f0789) for the features that you would like to see in Domain Services.

If you want to get started with Domain Services again, see [Create and configure a Microsoft Entra Domain Services managed domain](https://learn.microsoft.com/en-us/entra/identity/domain-services/tutorial-create-instance).
