<!-- Source: https://learn.microsoft.com/en-us/entra/global-secure-access/how-to-list-remote-networks -->
<!-- Sitemap-Last-Modified: 2026-03-25 -->

# How to list remote networks for Global Secure Access

## Overview

Reviewing your remote networks is an important part of managing your Global Secure Access deployment. As your organization grows, you add more remote networks. You use the Microsoft Entra admin center or the Microsoft Graph API.

## Prerequisites

- A **Global Secure Access Administrator** role in Microsoft Entra ID.
- The product requires licensing. For details, see the licensing section of [What is Global Secure Access](https://learn.microsoft.com/en-us/entra/global-secure-access/overview-what-is-global-secure-access). If needed, you can [purchase licenses or get trial licenses](https://aka.ms/azureadlicense).

## List all remote networks using the Microsoft Entra admin center

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com).
2. Browse to **Global Secure Access** > **Connect** > **Remote networks**. All remote networks are listed.
3. To view the details, select a remote network.

## List all remote networks using the Microsoft Graph API

1. Sign in to [Graph Explorer](https://aka.ms/ge).
2. Select `GET` as the HTTP method from the dropdown.
3. Set the API version to beta.
4. Enter the following query.

   ```
      GET https://graph.microsoft.com/beta/networkaccess/connectivity/branches
   ```

5. Select the **Run query** button to list the remote networks.

## Next steps

- [Create remote networks](https://learn.microsoft.com/en-us/entra/global-secure-access/how-to-manage-remote-networks)
