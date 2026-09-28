<!-- Source: https://learn.microsoft.com/en-us/entra/global-secure-access/quickstart-install-client -->
<!-- Sitemap-Last-Modified: 2026-03-13 -->

# Quickstart: Install the Windows client to acquire Microsoft traffic

## Overview

Microsoft Entra Internet Access isolates the traffic for Microsoft applications and resources, such as Exchange Online and SharePoint Online. Users can access these resources by connecting to the Global Secure Access client or through a remote network, such as in a branch office location.

This quickstart shows you the steps needed to install the client and start acquiring Microsoft traffic. For more information about Global Secure Access, see [What is Global Secure Access?](https://learn.microsoft.com/en-us/entra/global-secure-access/overview-what-is-global-secure-access)

## Prerequisites

Administrators who interact with **Global Secure Access** features must have the [Global Secure Access Administrator role](https://learn.microsoft.com/en-us/azure/active-directory/roles/permissions-reference). Some features might also require other roles.

To follow the [Zero Trust principle of least privilege](https://learn.microsoft.com/en-us/security/zero-trust/), consider using [Privileged Identity Management \(PIM\)](https://learn.microsoft.com/en-us/azure/active-directory/privileged-identity-management/pim-configure) to activate just-in-time privileged role assignments.

The product requires licensing. For details, see the licensing section of [What is Global Secure Access?](https://learn.microsoft.com/en-us/entra/global-secure-access/overview-what-is-global-secure-access). If needed, you can [purchase licenses or get trial licenses](https://aka.ms/azureadlicense).

## Install the client to acquire Microsoft traffic

[![Diagram of the basic Microsoft Entra Internet Access traffic flow.](https://learn.microsoft.com/en-us/entra/global-secure-access/media/quickstart-install-client/internet-access-basic-option.png)](https://learn.microsoft.com/en-us/entra/global-secure-access/media/quickstart-install-client/internet-access-basic-option.png#lightbox)

1. [Enable the Microsoft traffic forwarding profile](https://learn.microsoft.com/en-us/entra/global-secure-access/how-to-manage-microsoft-profile).
2. [Install and configure the Global Secure Access Client on end-user devices](https://learn.microsoft.com/en-us/entra/global-secure-access/how-to-install-windows-client).
3. [Enable universal tenant restrictions](https://learn.microsoft.com/en-us/entra/global-secure-access/how-to-universal-tenant-restrictions).
4. [Enable enhanced Global Secure Access signaling and Conditional Access](https://learn.microsoft.com/en-us/entra/global-secure-access/how-to-compliant-network).

After you complete these four steps, users with the Global Secure Access client installed on their Windows device can securely access Microsoft resources from anywhere. Conditional Access policy requires users to use the Global Secure Access client or a configured remote network, when they access Exchange Online and SharePoint Online.

## Next step

- [Quickstart: Create a remote network, apply Conditional Access, and review the logs](https://learn.microsoft.com/en-us/entra/global-secure-access/quickstart-remote-network)
