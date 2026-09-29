<!-- Source: https://learn.microsoft.com/en-us/defender-xdr/mto-endpoint-security-policy -->
<!-- Sitemap-Last-Modified: 2026-09-10 -->

# Endpoint security policies in multitenant management

Microsoft Defender for Endpoint security policies help you manage security settings across your devices. In the multitenant management portal, go to **Endpoints > Configuration management > Endpoint security policies** to manage these settings across multiple tenants.

For more information, see [Manage endpoint security policies in Microsoft Defender for Endpoint](https://learn.microsoft.com/en-us/defender-endpoint/endpoint-security-policies-configure).

## Prerequisites

Before you use endpoint security policies in multitenant management, ensure the following prerequisites are met:

- You must have Microsoft Defender for Endpoint to use endpoint security policies in multitenant management.
- Security administrators must have permissions in each tenant to access the endpoint security policies page in multitenant management.
- The **Endpoint security policies** page is available only for [users with the security administrator role in Microsoft Defender XDR](https://learn.microsoft.com/en-us/defender-endpoint/assign-portal-access). Other user roles, like Security Reader, don't provide access to the **Endpoint security policies** page.

  When a user has permissions to view policies in the Microsoft Defender portal, the data shown depends on their Intune permissions. Intune role-based access control, if applied, controls which policies appear in the list.

  We recommend that you assign the [Intune built-in role "Endpoint Security Manager"](https://learn.microsoft.com/en-us/intune/intune-service/fundamentals/role-based-access-control#built-in-roles) to security administrators. This role helps align permissions between Intune and Microsoft Defender XDR.

## Create a new or edit an existing security policy

You create endpoint security policies the same way in the multitenant portal as in the single tenant portal. For steps, see [Create an endpoint security policy](https://learn.microsoft.com/en-us/defender-endpoint/endpoint-security-policies-configure#create-an-endpoint-security-policy).

Differences include:

- Before you start, select the tenant for which you want to create the policy. Each policy is created for a specific tenant, and you can only create policies for one tenant at a time.

  For example:

  [![Screenshot of the policy creation page in endpoints security policy page in multitenant management.](https://learn.microsoft.com/en-us/defender-xdr/media/mto-endpoint-security-policy/mto-create-policy-small.png)](https://learn.microsoft.com/en-us/defender-xdr/media/mto-endpoint-security-policy/mto-create-policy.png#lightbox)
- To edit scope tags, go to the [Microsoft Intune admin center](https://intune.microsoft.com/). The Intune admin center doesn't yet support multitenant management, so you must edit scope tags in the single tenant portal.

Use the **Search** and **Filter** options to find a specific policy in the **Endpoint security policies** page. You can filter policies by tenant name, policy category, policy type, and targets.

Edit or delete a security policy by selecting the policy in the Endpoint security policies page, then selecting **Edit** or **Delete**. For example:

[![Screenshot of the editing pane for endpoint security policies page in multitenant management in Microsoft Defender XDR.](https://learn.microsoft.com/en-us/defender-xdr/media/mto-endpoint-security-policy/mto-edit-policy-small.png)](https://learn.microsoft.com/en-us/defender-xdr/media/mto-endpoint-security-policy/mto-edit-policy.png#lightbox)

## Verify endpoint security policy status

To verify that a policy was created, select it from the list and click the policy name. The policy page opens in a new tab. You can also open it through **Edit > Open policy page**.

The policy page shows the policy status, which devices it applies to, and the assigned groups.

[![Screenshot of the policy page in multitenant management in Microsoft Defender XDR.](https://learn.microsoft.com/en-us/defender-xdr/media/mto-endpoint-security-policy/mto-policy-page-small.png)](https://learn.microsoft.com/en-us/defender-xdr/media/mto-endpoint-security-policy/mto-policy-page.png#lightbox)

You can also view the policy in the Microsoft Intune admin center. To view the policy in Intune, select the More actions ellipsis \(…\) in the policy page, then select **View in Intune**.

## View distributed policies

Policies distributed across tenants appear in a tree view. The original policy is the parent, and its copies are listed beneath it. For example:

[![Screenshot of the endpoint security policies page in multitenant management highlighting distributed policies](https://learn.microsoft.com/en-us/defender-xdr/media/mto-endpoint-security-policy/mto-distributed.png)](https://learn.microsoft.com/en-us/defender-xdr/media/mto-endpoint-security-policy/mto-distributed.png#lightbox)

The **Last Distribution Status** column shows the overall status of the distributed copies. The **Tenants** and **Distribution profiles** columns show which tenants received the policy. For more information, see [Content distribution in multitenant management](https://learn.microsoft.com/en-us/defender-xdr/mto-distribution-profiles).

Tip

Do you want to learn more? Engage with the Microsoft Security community in our Tech Community: [Microsoft Defender XDR Tech Community](https://techcommunity.microsoft.com/t5/microsoft-365-defender/bd-p/MicrosoftThreatProtection).

## Related content

- [Microsoft Defender multitenant management](https://learn.microsoft.com/en-us/defender-xdr/mto-overview)
- [Set up Microsoft Defender multitenant management](https://learn.microsoft.com/en-us/defender-xdr/mto-requirements)
