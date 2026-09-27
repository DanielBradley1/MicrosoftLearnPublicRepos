<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/core/clients/manage/cmg/plan-cloud-management-gateway -->
<!-- Sitemap-Last-Modified: 2023-11-16 -->

# Plan for the CMG in Configuration Manager

*Applies to: Configuration Manager \(current branch\)*

To simplify management of internet-based clients, first develop a plan for the cloud management gateway \(CMG\). Design how it fits in your environment and prepare for your implementation.

For more foundational knowledge of CMG scenarios and use cases, see [Overview of CMG](https://learn.microsoft.com/en-us/intune/configmgr/core/clients/manage/cmg/overview).

Note

Some sections that were previously in this article have moved:

- **Hierarchy design**: [CMG hierarchy design](https://learn.microsoft.com/en-us/intune/configmgr/core/clients/manage/cmg/plan-hierarchy-design)
- **Performance and scale**: [CMG performance and scale](https://learn.microsoft.com/en-us/intune/configmgr/core/clients/manage/cmg/perf-scale)

## Planning checklist

The overall CMG planning process is divided into the following parts:

- *Components and requirements*: This article summarizes the components that make up the CMG system. It also lists the system requirements.
- *Client authentication*: Determine which authentication method you'll use for clients from potentially untrusted networks.
- *Hierarchy design*: Plan where to place the CMG in your environment.
- *Supported configurations*: Understand which Configuration Manager features you can support on internet-based clients that connect to the CMG.
- *Performance and scale*: Decide how many service components you'll need to best support your number of clients.
- *Cost*: Understand the cost of the Azure-based components.

## CMG components

Deployment and operation of the CMG includes the following components:

- The **CMG cloud service** in Azure authenticates and forwards Configuration Manager client requests over the internet to the on-premises CMG connection point.
- The **CMG connection point** site system role enables a consistent and high-performance connection from the on-premises network to the CMG service in Azure. It also publishes settings to the CMG including connection information and security settings. The CMG connection point forwards client requests from the CMG to on-premises roles according to URL mappings. For example, the management point and software update point.
- The [**service connection point**](https://learn.microsoft.com/en-us/intune/configmgr/core/servers/deploy/configure/about-the-service-connection-point) site system role runs the cloud service manager component, which handles all CMG deployment tasks. Additionally, it monitors and reports service health and logging information from Microsoft Entra ID. Make sure your service connection point is in [online mode](https://learn.microsoft.com/en-us/intune/configmgr/core/servers/deploy/configure/about-the-service-connection-point#bkmk_modes).
- The **management point** and **software update point** site system roles service client requests per normal.
- The CMG uses a **certificate-based HTTPS** web service to help secure network communication with clients.
- **Internet-based clients** connect to the CMG to access on-premises Configuration Manager components. There are multiple options for client identity and authentication:

  - Microsoft Entra ID
  - PKI certificates
  - Configuration Manager site-issued tokens


  For more information, see [Plan for CMG client authentication](https://learn.microsoft.com/en-us/intune/configmgr/core/clients/manage/cmg/plan-client-authentication).

- The CMG creates an **Azure storage account**, which it uses for its standard operations. By default, the CMG is also content-enabled to provide deployment content to internet-based clients. This storage account doesn't support customizations, such as virtual network restrictions.

  Note

  The cloud-based distribution point \(CDP\) is deprecated. Starting in version 2107, you can't create new CDP instances. To provide content to internet-based devices, enable the CMG to distribute content.

## Azure Resource Manager

You create the CMG using an **Azure Resource Manager deployment**. [Azure Resource Manager](https://learn.microsoft.com/en-us/azure/azure-resource-manager/resource-group-overview) is a modern platform for managing all solution resources as a single entity, called a [resource group](https://learn.microsoft.com/en-us/azure/azure-resource-manager/resource-group-overview#resource-groups). When you deploy a CMG with Azure Resource Manager, the site uses Microsoft Entra ID to authenticate and create the necessary cloud resources.

Important

Starting in version 2203, the option to deploy a CMG as a **cloud service \(classic\)** is removed. All CMG deployments should use a [virtual machine scale set](#virtual-machine-scale-sets). For more information, see [Removed and deprecated features](https://learn.microsoft.com/en-us/intune/configmgr/core/plan-design/changes/deprecated/removed-and-deprecated-cmfeatures).

## Virtual machine scale sets

Note

This feature was first introduced in version 2010 as a [pre-release feature](https://learn.microsoft.com/en-us/intune/configmgr/core/servers/manage/pre-release-features). Starting in version 2107, it's no longer a pre-release feature.

Configuration Manager doesn't enable this optional feature by default. You must enable this feature before using it. For more information, see [Enable optional features from updates](https://learn.microsoft.com/en-us/intune/configmgr/core/servers/manage/optional-features).

Starting in version 2010, customers with a Cloud Solution Provider \(CSP\) subscription can deploy the CMG with a **virtual machine scale set** in Azure. This support is only if they don't currently have a CMG deployed using classic cloud services to another subscription.

Starting in version 2107, all customers can deploy a CMG with a virtual machine scale set. If you have an existing CMG deployed with the classic cloud service, **convert** the CMG to use a virtual machine scale set.

With a few exceptions, the configuration, operation, and functionality of the CMG remains the same.

- Other [Azure resource providers](https://learn.microsoft.com/en-us/intune/configmgr/core/clients/manage/cmg/configure-azure-ad#configure-azure-resource-providers) in your Azure subscription.
- Different deployment names, for example, **GraniteFalls.EastUS.CloudApp.Azure.Com** for a deployment in the **East US** Azure region. This name change can affect how you create and manage the [CMG server authentication certificate](https://learn.microsoft.com/en-us/intune/configmgr/core/clients/manage/cmg/server-auth-cert).
- The CMG connection point only communicates with the virtual machine scale set in Azure over HTTPS. It doesn't require TCP-TLS ports.

### Limitations for a CMG with a virtual machine scale set

#### Limitations with versions 2107 and later

Note

Starting in version 2111, CMG deployments with a virtual machine scale set support Azure US Government cloud environments.

- Users may experience a delay of up to three seconds for actions in Software Center.
- You can't approve/deny application requests through the CMG.
- Version 2107 doesn't support Azure US Government cloud environments.

#### Limitations with versions 2010 and 2103

- If you require more than one CMG instance, they all have to use the same deployment method.
- The supported number of concurrent client connections is 2,000 per VM instance. For more information, see [CMG performance and scale](https://learn.microsoft.com/en-us/intune/configmgr/core/clients/manage/cmg/perf-scale).
- It's only supported with a standalone primary site.
- It doesn't support Azure US Government cloud environments.
- Users may experience a delay of up to three seconds for actions in Software Center.
- Configuration Manager currently creates the Azure storage container based on the name of the resource group. Azure has different naming requirements for resource groups and storage containers. Make sure the name of the resource group for this service only has lowercase letters, numbers, and hyphens. If you have an existing resource group that doesn't work, rename it in the Azure portal, or create a new resource group.
- If you have more than one HTTPS management point, then you can't install the Configuration Manager client on devices over the internet. If you need to [Install off-premises clients using a CMG](https://learn.microsoft.com/en-us/intune/configmgr/core/clients/manage/cmg/configure-clients#install-off-premises-clients-using-a-cmg), then you can only have one HTTPS management point. You also need to enable the CMG for content.
- You can't approve/deny application requests through the CMG.

## Requirements

Tip

To clarify some Azure terminology:

- The Microsoft Entra ID *tenant* is the directory of user accounts and app registrations. One tenant can have multiple subscriptions.
- An Azure *subscription* separates billing, resources, and services. It's associated with a single tenant.

For more information, see [Subscriptions, licenses, accounts, and tenants for Microsoft's cloud offerings](https://learn.microsoft.com/en-us/microsoft-365/enterprise/subscriptions-licenses-accounts-and-tenants-for-microsoft-cloud-offerings).

- An **Azure subscription** to host the CMG. This subscription can be in one of the following environments:

  - Global Azure cloud
  - Azure US Government cloud


  Customers with a Cloud Service Provider \(CSP\) subscription need to use version 2010 or later with a **virtual machine scale set** deployment.

- Integrate the site with **Microsoft Entra ID** to deploy the service with Azure Resource Manager. For more information, see [Configure Microsoft Entra ID for CMG](https://learn.microsoft.com/en-us/intune/configmgr/core/clients/manage/cmg/configure-azure-ad).

  When you onboard the site to Microsoft Entra ID, you can optionally enable **Microsoft Entra user discovery**. It isn't required to create the CMG, but required if you plan to use Microsoft Entra authentication with hybrid identities. For more information, see [Install clients using Microsoft Entra ID](https://learn.microsoft.com/en-us/intune/configmgr/core/clients/deploy/deploy-clients-cmg-azure) and see [About Microsoft Entra user discovery](https://learn.microsoft.com/en-us/intune/configmgr/core/servers/deploy/configure/about-discovery-methods#azureaddisc).
- An **Azure administrator** needs to participate in the initial creation of certain components. This persona can be the same as the Configuration Manager administrator, or separate. If separate, they don't require permissions in Configuration Manager.

  - When you integrate the site with Microsoft Entra ID for deploying the CMG using Azure Resource Manager, you need a **Global Administrator**.
  - When you create the CMG, you need an account that is an **[Azure subscription Owner](https://learn.microsoft.com/en-us/azure/role-based-access-control/built-in-roles#privileged)** and a **[Microsoft Entra Global Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#global-administrator)**.


  Important


  The [Microsoft Entra Global Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/privileged-roles-permissions) role is a highly privileged role and should only be used when another role can't be used. This feature requires the Global Administrator role. For other features, Microsoft recommends using roles with the fewest permissions. To learn more, see [Fundamentals of role-based administration for Configuration Manager](https://learn.microsoft.com/en-us/intune/configmgr/core/understand/fundamentals-of-role-based-administration).

- Your user account needs to be a **Full administrator** or **Infrastructure administrator** in Configuration Manager.
- At least one on-premises Windows server to host the **CMG connection point**. You can colocate this role with other Configuration Manager site system roles.
- The **service connection point** must be in [online mode](https://learn.microsoft.com/en-us/intune/configmgr/core/servers/deploy/configure/about-the-service-connection-point#bkmk_modes).
- Configure the **management point** to allow traffic from the CMG. It also needs to require HTTPS, or configure the site for [Enhanced HTTP](https://learn.microsoft.com/en-us/intune/configmgr/core/plan-design/hierarchy/enhanced-http).
- A [**server authentication certificate**](https://learn.microsoft.com/en-us/intune/configmgr/core/clients/manage/cmg/server-auth-cert) for the CMG.
- CMG names need to be between 3-24 alphanumeric characters. The name must begin with a letter, end with a letter or digit, and not contain consecutive hyphens.
- **Other certificates** may be required, depending upon your client OS version and authentication model. For more information, see [Configure client authentication](https://learn.microsoft.com/en-us/intune/configmgr/core/clients/manage/cmg/configure-authentication).
- Clients must use **IPv4**.
- Make sure the following [client settings](https://learn.microsoft.com/en-us/intune/configmgr/core/clients/deploy/about-client-settings#cloud-services) in the **Cloud services** group are enabled for devices that will use the CMG:

  - **Enable clients to use a cloud management gateway**
  - **Allow access to cloud distribution point**


  Note


  If you enable the client setting to [Download delta content when available](https://learn.microsoft.com/en-us/intune/configmgr/core/clients/deploy/about-client-settings#allow-clients-to-download-delta-content-when-available), the content for third-party updates won't download to clients.

## Next steps

Next, determine how clients will authenticate with the CMG:

[Plan for CMG client authentication](https://learn.microsoft.com/en-us/intune/configmgr/core/clients/manage/cmg/plan-client-authentication)
