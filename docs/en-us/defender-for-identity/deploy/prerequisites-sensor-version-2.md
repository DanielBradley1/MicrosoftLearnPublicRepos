<!-- Source: https://learn.microsoft.com/en-us/defender-for-identity/deploy/prerequisites-sensor-version-2 -->
<!-- Sitemap-Last-Modified: 2026-08-31 -->

# Microsoft Defender for Identity sensor v2.x prerequisites

The Defender for Identity sensor v2.x has the following requirements. The v2.x sensor supports:

- Domain controllers running Windows Server 2016 or earlier
- AD FS, AD CS, and Microsoft Entra Connect servers that aren't domain controllers

Tip

For domain controllers running Windows Server 2019 or later, we recommend deploying the [sensor v3.x](https://learn.microsoft.com/en-us/defender-for-identity/deploy/deploy-sensor-v3) instead.

Tip

For servers running Windows Server 2019 or later, we recommend deploying the [Defender for Identity sensor v3.x](https://learn.microsoft.com/en-us/defender-for-identity/deploy/deploy-sensor-v3) instead.

## Licensing requirements

Deploying Defender for Identity requires one of the following Microsoft 365 licenses:

- Enterprise Mobility + Security E5 \(EMS E5/A5\)
- Microsoft 365 E5 \(Microsoft E5/A5/G5\)
- Microsoft 365 E5/A5/G5/F5[\*](#req) Security
- Microsoft 365 F5 Security + Compliance[\*](#req)
- A standalone Defender for Identity license

\* Both F5 licenses require Microsoft 365 F1/F3 or Office 365 F3 and Enterprise Mobility + Security E3.

Acquire licenses directly via the [Microsoft 365 portal](https://www.microsoft.com/cloud-platform/enterprise-mobility-security-pricing) or use the Cloud Solution Partner \(CSP\) licensing model.

For more information, see [Licensing and privacy FAQs](https://learn.microsoft.com/en-us/defender-for-identity/technical-faq#licensing-and-privacy).

## Roles and permissions

- To create your Defender for Identity workspace, you need a Microsoft Entra ID tenant.
- You must have a user with a [Security administrator](https://learn.microsoft.com/en-us/azure/active-directory/users-groups-roles/directory-assign-admin-roles#available-roles) role. For more information, see [Microsoft Defender for Identity role groups](https://learn.microsoft.com/en-us/defender-for-identity/role-groups).
- We recommend using at least one Directory Service account, with read access to all objects in the monitored domains. For more information, see [Configure a Directory Service account for Microsoft Defender for Identity](https://learn.microsoft.com/en-us/defender-for-identity/deploy/directory-service-accounts).

## Network requirements

The Defender for Identity sensor must be able to communicate with the Defender for Identity cloud service, using one of the following methods:

| Method | Description | Considerations | Learn more |
| --- | --- | --- | --- |
| Proxy | Customers who have a forward proxy deployed can take advantage of the proxy to provide connectivity to the MDI cloud service.  <br>  <br>If you choose this option, you'll need to configure your proxy later in the deployment process. Proxy configurations include allowing traffic to the sensor URL, and configuring Defender for Identity URLs to any explicit allow lists used by your proxy or firewall. | Allows access to the internet for a single URL  <br>  <br>SSL inspection isn't supported | [Configure endpoint proxy and internet connectivity settings](https://learn.microsoft.com/en-us/defender-for-identity/deploy/configure-proxy)  <br>  <br>[Run a silent installation with a proxy configuration](https://learn.microsoft.com/en-us/defender-for-identity/deploy/install-sensor#command-for-running-a-silent-installation-with-a-proxy-configuration) |
| ExpressRoute | ExpressRoute can be configured to forward MDI sensor traffic over customer's express route.  <br>  <br>To route network traffic destined to the Defender for Identity cloud servers use ExpressRoute Microsoft peering and add the Microsoft Defender for Identity \(12076:5220\) service BGP community to your route filter. | Requires ExpressRoute | [Service to BGP community value](https://learn.microsoft.com/en-us/azure/expressroute/expressroute-routing#service-to-bgp-community-value) |
| Firewall, using the Defender for Identity Azure IP addresses | Customers who don't have a proxy or ExpressRoute can configure their firewall with the IP addresses assigned to the MDI cloud service. This requires that the customer monitor the Azure IP address list for any changes in the IP addresses used by the MDI cloud service.  <br>  <br>If you chose this option, we recommend that you download the [Azure IP Ranges and Service Tags – Public Cloud](https://www.microsoft.com/download/details.aspx?id=56519) file and use the **AzureAdvancedThreatProtection** service tag to add the relevant IP addresses. | Customer must monitor Azure IP assignments | [Virtual network service tags](https://learn.microsoft.com/en-us/azure/virtual-network/service-tags-overview) |

## Server requirements

The following table summarizes the server requirements and recommendations for the Defender for Identity sensor.

| Prerequisite / Recommendation | Description |
| --- | --- |
| Specifications | The Defender for Identity sensor requires the following resources beyond those already used by the operating system and domain controller services:  <br>  <br>- two cores  <br>- 6 GB of RAM  <br>- 6 GB of disk space required, 10 GB recommended, including space for Defender for Identity binaries and logs  <br>  <br>Defender for Identity supports read-only domain controllers \(RODC\). |
| Performance | For optimal performance, set the **Power Option** of the machine running the Defender for Identity sensor to **High Performance**. |
| Network interface configuration | If you're using VMware virtual machines, make sure the virtual machine's NIC configuration has Large Send Offload \(LSO\) disabled. For more information, see [VMware virtual machine sensor issue](https://learn.microsoft.com/en-us/defender-for-identity/troubleshooting-known-issues#vmware-virtual-machine-sensor-issue) for more details. |
| Maintenance window | We recommend scheduling a maintenance window for your domain controllers, as a restart might be required if the installation runs and a restart is already pending, or if .NET Framework needs to be installed.  <br>  <br>If .NET Framework version 4.7 or later isn't already found on the system, .NET Framework version 4.7 is installed, and might require a restart. |
| AD FS federation servers | In AD FS environments, Defender for Identity sensors are supported only on the federation servers. They're not required on Web Application Proxy \(WAP\) servers. |
| Microsoft Entra Connect servers | For Microsoft Entra Connect servers, you need to install the sensors on both active and staging servers. |
| AD CS servers | Defender for Identity sensor for AD CS supports only AD CS servers with Certification Authority Role Service. You don't need to install sensors on any AD CS servers that are offline. |
| Time synchronization | The servers and domain controllers onto which the sensor is installed must have time synchronized to within five minutes of each other. |

### Minimum operating system requirements

Defender for Identity sensors can be installed on the following operating systems:

- **Windows Server 2016**
- **Windows Server 2019**. Requires [KB4487044](https://support.microsoft.com/topic/february-12-2019-kb4487044-os-build-17763-316-6502eb5d-dde8-6902-e149-27ef359ed616) or a newer cumulative update. Sensors installed on Server 2019 without this update will be automatically stopped if the `ntdsai.dll` file version found in the system directory is older `than 10.0.17763.316`
- **Windows Server 2022**
- **Windows Server 2025**

For all operating systems:

- Both servers with desktop experience and server cores are supported.
- Nano servers aren't supported.
- Installations are supported for domain controllers, AD FS, AD CS, and Entra Connect servers.

#### Legacy operating systems

Windows Server 2012 and Windows Server 2012 R2 reached extended end of support on October 10, 2023. Sensors running on these operating systems continue to report to Defender for Identity and even receive the sensor updates, but some functionality that relies on operating system capabilities might not be available. We recommend that you upgrade any servers using these operating systems.

### Required ports

To enable the Defender for Identity sensor to communicate with the cloud service, allow outbound HTTPS traffic to your workspace sensor API URL in the following format: `https://<your-workspace-name>sensorapi.atp.azure.com`. For example, if your workspace name is "Contoso", allow traffic to `https://contoso-corpsensorapi.atp.azure.com`.

| Protocol | Transport | Port | From | To | Notes |
| --- | --- | --- | --- | --- | --- |
| Internet ports |  |  |  |  |  |
| SSL \(\*.atp.azure.com\) | TCP | 443 | Defender for Identity sensor | Defender for Identity cloud service | Alternately, [configure access through a proxy](https://learn.microsoft.com/en-us/defender-for-identity/deploy/configure-proxy). |
| Internal ports |  |  |  |  |  |
| DNS | TCP and UDP | 53 | Defender for Identity sensor | DNS Servers |  |
| RADIUS | UDP | 1813 | RADIUS | Defender for Identity sensor |  |
| Localhost port |  |  |  |  | Required for the sensor service updater. By default, *localhost* to *localhost* traffic is allowed unless a custom firewall policy blocks it. |
| SSL | TCP | 444 | Sensor service | Sensor updater service |  |
| Network Name Resolution \(NNR\) ports |  |  |  |  | To resolve IP addresses to computer names, we recommend opening all ports listed. However, only one port is required. |
| NTLM over RPC | TCP | Port 135 | Defender for Identity sensor | All devices on network \(DCs, ADFS, ADCS, and Microsoft Entra Connect\) |  |
| NetBIOS | UDP | 137 | Defender for Identity sensor | All devices on network \(DCs, ADFS, ADCS, and Microsoft Entra Connect\) |  |
| RDP | TCP | 3389 | Defender for Identity sensor | All devices on network \(DCs, ADFS, ADCS, and Microsoft Entra Connect\) | Only the first packet of **Client hello** queries the DNS server using reverse DNS lookup of the IP address \(UDP 53\) |

If you're working with [multiple forests](https://learn.microsoft.com/en-us/defender-for-identity/deploy/multi-forest), make sure that the following ports are opened on any machine where a Defender for Identity sensor is installed:

| Protocol | Transport | Port | To/From | Direction |
| --- | --- | --- | --- | --- |
| Internet ports |  |  |  |  |
| SSL \(\*.atp.azure.com\) | TCP | 443 | Defender for Identity cloud service | Outbound |
| Internal ports |  |  |  |  |
| LDAP | TCP and UDP | 389 | Domain controllers | Outbound |
| Secure LDAP \(LDAPS\) | TCP | 636 | Domain controllers | Outbound |
| LDAP to Global Catalog | TCP | 3268 | Domain controllers | Outbound |
| LDAPS to Global Catalog | TCP | 3269 | Domain controllers | Outbound |

Tip

By default, Defender for Identity sensors query the directory using LDAP on ports 389 and 3268. To switch to LDAPS on ports 636 and 3269, open a support case. For more information, see [Microsoft Defender for Identity support](https://learn.microsoft.com/en-us/defender-for-identity/support).

### Memory requirements

The following table describes memory requirements on the server used for the Defender for Identity sensor, depending on the type of virtualization you're using:

| VM running on | Description |
| --- | --- |
| Hyper-V | Ensure that **Enable Dynamic Memory** isn't enabled for the VM. |
| VMware | Ensure that the amount of memory configured and the reserved memory are the same, or select the **Reserve all guest memory \(All locked\)** option in the VM settings. |
| Other virtualization host | Refer to the vendor supplied documentation on how to ensure that memory is fully allocated to the VM at all times. |

Important

When running as a virtual machine, all memory must be allocated to the virtual machine at all times.

## Configure Windows event auditing

Defender for Identity detections rely on specific Windows event log entries to enhance detections and provide extra information about the users performing specific actions, such as NTLM sign-ins and security group modifications.

[Configure Windows event auditing](https://learn.microsoft.com/en-us/defender-for-identity/deploy/configure-windows-event-collection) on your domain controller to support Defender for Identity detections in the Defender portal or using PowerShell.

## Test your prerequisites

We recommend running the [*Test-MdiReadiness.ps1*](https://github.com/microsoft/Microsoft-Defender-for-Identity/tree/main/Test-MdiReadiness) script to test and see if your environment has the necessary prerequisites.

The *Test-MdiReadiness.ps1* script is also available from Microsoft Defender XDR, on the **Identities > Tools** page \(Preview\).

## Next step

[Plan capacity for Microsoft Defender for Identity](https://learn.microsoft.com/en-us/defender-for-identity/deploy/capacity-planning)
