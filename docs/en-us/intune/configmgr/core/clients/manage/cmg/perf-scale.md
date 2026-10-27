<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/core/clients/manage/cmg/perf-scale -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# CMG performance and scale

*Applies to: Configuration Manager \(current branch\)*

The supported scale and performance of the cloud management gateway \(CMG\) is based on the number of devices that you expect to simultaneously connect to the service. Use the information in this article to determine how many of the following components you need in your environment for the best performance at the appropriate scale:

- CMG cloud service
- Virtual machine instances for each CMG
- CMG connection point site system on your internal network

Note

Sizing guidance for management points and software update points doesn't change whether they service on-premises or internet-based clients. For more information, see [Size and scale numbers](https://learn.microsoft.com/en-us/intune/configmgr/core/plan-design/configs/size-and-scale-numbers).

## Size and scale for CMG

Unless otherwise noted, this guidance is the same for all deployment models and VM sizes.

- You can install multiple instances of the cloud management gateway \(CMG\) at primary sites, or the central administration site \(CAS\).

  Tip

  In a hierarchy, create the CMG at the CAS.
- One CMG supports up to 16 virtual machine \(VM\) instances in the Azure cloud service.
- Simultaneous client connections per each CMG VM instance depend upon the deployment model and VM size. When the CMG is under high load with more than the supported number of clients, it still handles requests but there may be delay.

  - **Virtual machine scale-set** *\(version 2107 and later\)*

    Use the table for your Configuration Manager version and installed updates.

    **Version 2609 and later, and version 2603 with the update rollup \(KB39169655\)**

    | CMG tier | VM size | vCPU | Memory | Simultaneous client connections per VM instance |
    | --- | --- | --- | --- | --- |
    | Small | Standard\_D2ads\_v6 | 2 | 8 GiB | 10 |
    | Medium | Standard\_D4ads\_v6 | 4 | 16 GiB | 6,000 |
    | Large | Standard\_D8ads\_v6 | 8 | 32 GiB | 10,000 |


    When you update to version 2609 or install the [version 2603 update rollup \(KB39169655\)](https://learn.microsoft.com/en-us/intune/configmgr/hotfix/2603/39169655), existing deployments are automatically migrated: Lab to Small, Standard to Medium, and Large to Large. The client connection limits for each tier remain the same.


    Important


    Before updating, check that the new VM sizes are available in your Azure region and that both the **standard Dadv6 Family vCPUs** and **Total Regional vCPUs** quotas have enough available quota, including headroom for temporary instances during upgrade or maintenance. For details, see [Check CMG capacity and vCPU quotas before upgrading](https://learn.microsoft.com/en-us/intune/configmgr/core/plan-design/changes/whats-new-version-2609#check-cmg-capacity-and-vcpu-quotas-before-upgrading). Upgrade the Configuration Manager console after installing the update so that it displays the new VM sizes correctly.


    **Version 2603 without KB39169655 and versions 2107 through 2509**


    | CMG tier | VM size | vCPU | Memory | Simultaneous client connections per VM instance |
    | --- | --- | --- | --- | --- |
    | Lab | Standard\_B2s | 2 | 4 GiB | 10 |
    | Standard | Standard\_A2\_v2 | 2 | 4 GiB | 6,000 |
    | Large | Standard\_A4\_v2 | 4 | 8 GiB | 10,000 |


    Important


    The **Small** tier \(previously **Lab \(B2s\)**\) is only intended for lab testing and small proof-of-concept environments, not production use with the CMG. The Configuration Manager technical preview branch only supports 10 clients, which is why this tier supports that number of clients.

  - **Virtual machine scale set** *\(version 2010 and 2103 for Cloud Service Provider \(CSP\) subscriptions\)*: 2,000
  - **Cloud service \(classic\)** *\(version 2111 and earlier\)*: 6,000

    Important

    Starting in version 2203, the option to deploy a CMG as a **cloud service \(classic\)** is removed. All CMG deployments should use a [virtual machine scale set](https://learn.microsoft.com/en-us/intune/configmgr/core/clients/manage/cmg/plan-cloud-management-gateway#virtual-machine-scale-sets). For more information, see [Removed and deprecated features](https://learn.microsoft.com/en-us/intune/configmgr/core/plan-design/changes/deprecated/removed-and-deprecated-cmfeatures).

## Size and scale for CMG connection point

This guidance is the same for all deployment models and VM sizes.

- You can install multiple instances of the CMG connection point at primary sites.
- One CMG connection point can support a CMG with up to four VM instances. If the CMG has more than four VM instances, add a second CMG connection point for load balancing. A CMG with 16 VM instances should be linked with four CMG connection points.

Note

When considering hardware requirements for the CMG connection point, see [Recommended hardware for remote site system servers](https://learn.microsoft.com/en-us/intune/configmgr/core/plan-design/configs/recommended-hardware#remote-site-system-servers).

## Improve performance

The following recommendations can help you improve CMG performance:

- The connection between the Configuration Manager client and the CMG isn't region-aware. Client communication is largely unaffected by latency and geographic separation. It's generally not necessary to deploy multiple CMG for the purposes of geo-proximity. Deploy the CMG at the top-level site in your hierarchy. To increase scale, add VM instances.
- For high availability of the service, create a CMG with at least two VM instances and two CMG connection points per site.
- Scale the CMG to support more clients by adding more VM instances. The Azure load balancer controls client connections to the service.
- Create more CMG connection points to distribute the load among them. The CMG distributes the traffic to its connecting CMG connection points in a round-robin fashion.

Note

The CMG connection point creates a TCP connection to the management point for each client. While Configuration Manager has no hard limit on the number of clients for a CMG connection point, Windows Server has a default maximum TCP dynamic port range of 16,384. If a Configuration Manager site manages more than 16,384 clients with a single CMG connection point, add another site system or increase the Windows Server limit. All clients maintain a channel for client notifications, which holds a port open on the CMG connection point. For more information on how to increase this limit, see [Microsoft Support article 929851](https://support.microsoft.com/help/929851).

## Content performance

As with any distribution point design, consider the following factors for a content-enabled CMG:

- Number of concurrent client connections
- The size of the content that clients download
- The length of time allowed to meet your business requirements

Depending upon your design, if clients have the option of more than one CMG for any given content, then they naturally randomize across those cloud sources. If you only distribute a certain piece of content to a single CMG, and a large number of clients try to download this content at the same time, it puts higher load on that single CMG. Adding another CMG includes a separate Azure storage service. For more information on how the client communicates with the CMG components and downloads content, see [Data flow](https://learn.microsoft.com/en-us/intune/configmgr/core/clients/manage/cmg/data-flow).

Note

The Azure storage service supports 500 requests per second for a single file. Performance testing of a single cloud-based content source supported distribution of a single 100-MB file to 50,000 clients in 24 hours.

## Next steps

Next, understand the costs associated with operating an Azure service for the CMG:

[Cost of CMG](https://learn.microsoft.com/en-us/intune/configmgr/core/clients/manage/cmg/cost)
