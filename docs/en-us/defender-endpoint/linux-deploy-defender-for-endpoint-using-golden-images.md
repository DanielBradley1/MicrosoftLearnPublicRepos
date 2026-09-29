<!-- Source: https://learn.microsoft.com/en-us/defender-endpoint/linux-deploy-defender-for-endpoint-using-golden-images -->
<!-- Sitemap-Last-Modified: 2025-09-16 -->

# Deploy Microsoft Defender for Endpoint on Linux using golden images

Golden images are preconfigured virtual machine templates used to rapidly and consistently deploy multiple identical systems across an organization. Microsoft Defender for Endpoint on Linux supports golden image deployment across cloud and on-premises environments, with improved handling of machine identifiers and hostnames, ensuring reliable telemetry and device correlation.

This guide walks you through:

- Deploying Microsoft Defender for Endpoint on a golden image.
- Preparing the image for cloning.
- Ensuring unique identifiers for each virtual machine instance.
- Specific steps for cloud and on-premises environments.

## Step 1: Deploy Microsoft Defender for Endpoint on a golden image

1. Prepare the base virtual machine

   - Install your preferred [supported Linux distribution](https://learn.microsoft.com/en-us/defender-endpoint/mde-linux-prerequisites#supported-linux-distributions) and apply all necessary system updates.

2. Deploy Microsoft Defender for Endpoint on a golden image

   There are several methods and tools that you can use to deploy Microsoft Defender for Endpoint on Linux \(applicable to AMD64 and ARM64 Linux servers\):

   - [Installer script based deployment](https://learn.microsoft.com/en-us/defender-endpoint/linux-installer-script)
   - [Ansible based deployment](https://learn.microsoft.com/en-us/defender-endpoint/linux-install-with-ansible)
   - [Chef based deployment](https://learn.microsoft.com/en-us/defender-endpoint/linux-deploy-defender-for-endpoint-with-chef)
   - [Puppet based deployment](https://learn.microsoft.com/en-us/defender-endpoint/linux-install-with-puppet)
   - [SaltStack based deployment](https://learn.microsoft.com/en-us/defender-endpoint/linux-install-with-saltack)
   - [Manual deployment](https://learn.microsoft.com/en-us/defender-endpoint/linux-install-manually)
   - [Direct onboarding with Defender for Cloud](https://learn.microsoft.com/en-us/azure/defender-for-cloud/onboard-machines-with-defender-for-endpoint)
   - [Guidance for Defender for Endpoint on Linux Server with SAP](https://learn.microsoft.com/en-us/defender-endpoint/mde-linux-deployment-on-sap)

3. Validate the deployment

   Check the health status of the product by running the following command. A return value of `true` denotes that the product is functioning as expected:

   ```bash
   mdatp health
   ```

Note

Once Defender is successfully deployed on the golden image, there's no requirement to install and onboard it individually on each cloned machine.

## Step 2: Prepare the golden image for cloning

When deploying Defender for Endpoint on virtual machines, the hardware UUID reported by the system \(system-uuid from dmidecode\) is used to uniquely identify each instance.

Before making a snapshot of the virtual machine, ensure that each virtual machine clone gets a unique hardware UUID, as described in the following sections.

### On-premises machines

For on-premises environments, configure your virtualization platform so that each clone receives a unique hardware UUID from the underlying hypervisor. Follow these guidelines:

**KVM/libvirt**

- Don't hard-code the `<uuid>` element in the virtual machine's domain XML; if it's omitted, libvirt generates a random one at definition time.
- Alternatively, explicitly create a new UUID using `uuidgen`.
- For streamlined cloning, use `virt-clone` or `virt-manager`, which automatically assign unique UUIDs.

**VMware**

- During cloning, VMware prompts whether to keep the existing UUID or to create a new one. Always select **Create**, or configure `uuid.action = "create"` in the virtual machine's *.vmx* file.
- In VMware Cloud Director, set `backend.cloneBiosUuidOnVmCopy = 0` to force the creation of new UUIDs.

**Hyper-V**

Hyper-V automatically generates a new hardware UUID when you create a virtual machine using Hyper-V Manager or PowerShell \([New-VM](https://learn.microsoft.com/en-us/powershell/module/hyper-v/new-vm)\).

### Cloud virtual machines

Cloud platforms \(for example, Azure, AWS, GCP\) automatically inject unique metadata and identifiers via their instance metadata services \(IMDS\). No manual steps are required. Microsoft Defender for Endpoint automatically detects and uses these values to generate unique machine IDs.

## Hostname Management

If the hostname of a Linux server is changed after successful deployment of Defender, then you must restart the `mdatp` service to ensure the new hostname is correctly recognized by product.

## Related content

Tip

Do you want to learn more? Engage with the Microsoft Security community in our Tech Community: [Microsoft Defender for Endpoint Tech Community](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/bd-p/MicrosoftDefenderATP).
