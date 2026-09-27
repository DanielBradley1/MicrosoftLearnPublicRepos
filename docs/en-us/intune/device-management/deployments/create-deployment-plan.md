<!-- Source: https://learn.microsoft.com/en-us/intune/device-management/deployments/create-deployment-plan -->
<!-- Sitemap-Last-Modified: 2026-09-21 -->

# Create a deployment plan in Microsoft Intune

Note

This feature is in public preview. For more information, see [Public preview in Microsoft Intune](https://learn.microsoft.com/en-us/intune/fundamentals/public-preview).

A deployment plan is a reusable template that defines a standardized rollout pattern for delivering a payload across devices in controlled stages, or rings. Plans define the rollout structure, including rings, group assignments, assignment filters, and deferral timing, but don't contain or deliver a payload. For more information, see [Deployment plans and deployments overview](https://learn.microsoft.com/en-us/intune/device-management/deployments/overview).

## Prerequisites

- **Permissions**: You need **Create** permission for the **Deployment plan** category. For more information, see [Permissions, scope tags, and approvals for deployments](https://learn.microsoft.com/en-us/intune/device-management/deployments/rbac-scope-tags).
- **Groups**: Have at least one Microsoft Entra security group or supported virtual group ready for each ring.
- **Platform and payload type**: Identify the platform and payload type that the plan supports. These selections determine which assignment filters are available.

## Create a deployment plan

1. Sign in to the \[Microsoft Intune admin center\].
2. Select **Devices** from the left navigation menu.
3. Under **Manage devices**, select **Deployments**.
4. On the **Deployment plans** page, select **Create plan**.
5. On the **Basics** page, enter a **Name** and **Description**, and then select **Next**.
6. On the **Deployment schedule** page, select a **Platform** from the list. The platform determines which assignment filters are available.

   Select **All platforms** for a plan that's generic to any platform and payload type.
7. Select **Add rings** to open **Manage rings**.
8. Enter a name for the first ring. You can't set **Wait time to next ring** for the first ring because you set the first ring's start date and time when you load the plan into a deployment.
9. Select **Add ring** for each additional ring, and configure **Wait time to next ring** in days and hours. The wait time is the interval between rings, and must be at least one hour.
10. After you add all rings, select **Save**.
11. Add groups to each ring. Each ring requires at least one group assignment. You can also configure supported assignment filters for group assignments.

    Important

    Adding the **All users** or **All devices** virtual group to a ring automatically makes it the final ring. Virtual groups and Microsoft Entra security groups can't be combined in the same ring. When you select a virtual group, confirm the change in the dialog to continue.
12. Optionally, add **Exclude groups**. Exclude groups apply to all rings in the plan.
13. Select **Next**.
14. Optionally, add scope tags, and then select **Next**.
15. On **Review + create**, review the plan and select **Save**.

## Modify a deployment plan

You can modify a plan after you create it. Changes to a plan don't affect deployments that were already created from that plan.

1. In the \[Microsoft Intune admin center\], go to **Devices** > **Manage devices** > **Deployments** > **Deployment plans**.
2. Select the plan.
3. Update the plan properties, and then select **Save**.

For information about handling deleted groups or rings that become empty, see [Deployments and deleted groups](https://learn.microsoft.com/en-us/intune/device-management/deployments/create-deployment#deployments-and-deleted-groups).

## Related articles

- [Deployment plans and deployments overview](https://learn.microsoft.com/en-us/intune/device-management/deployments/overview)
- [Create and manage a deployment in Microsoft Intune](https://learn.microsoft.com/en-us/intune/device-management/deployments/create-deployment)
- [Permissions, scope tags, and approvals for deployments](https://learn.microsoft.com/en-us/intune/device-management/deployments/rbac-scope-tags)
- [Known issues with deployments \(preview\)](https://learn.microsoft.com/en-us/intune/device-management/deployments/known-issues)
