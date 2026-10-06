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

### Add the onboarding package to the golden image

You can include the tenant-specific onboarding package in the golden image so that every machine created from the image onboards to Microsoft Defender for Endpoint automatically when the Defender service starts. Each clone onboards directly, without waiting for a separate deployment or extension to run. This approach is useful for short-lived or autoscaled virtual machines.

Important

Copy the onboarding file to the golden image **only while the `mdatp` service is stopped**. If the service is running when you add the onboarding file, the golden image virtual machine onboards immediately and creates device identity state. That state is then captured in the image and carried over to every clone, which might cause multiple machines to report as the same device in the Microsoft Defender portal.

#### Prerequisites

- Microsoft Defender for Endpoint is installed on the golden image virtual machine, as described in [Step 1](#step-1-deploy-microsoft-defender-for-endpoint-on-a-golden-image). Use a current, supported version of the package.
- You have access to the Microsoft Defender portal with permissions to download the onboarding package.

#### Download the onboarding package

1. In the [Microsoft Defender portal](https://security.microsoft.com), go to **Settings** > **Endpoints** > **Device management** > **Onboarding**.
2. Select **Linux Server** as the operating system.
3. For **Deployment method**, select **Your preferred Linux configuration management tool**.
4. Select **Download onboarding package**, and save `WindowsDefenderATPOnboardingPackage.zip`.
5. Extract the package. It contains the `mdatp_onboard.json` onboarding file.

   ```bash
   unzip WindowsDefenderATPOnboardingPackage.zip
   ```

#### Add the onboarding file to the image

Run the following steps on the golden image virtual machine:

1. Stop the Defender service.

   ```bash
   sudo systemctl stop mdatp
   ```

2. Confirm that the service is stopped before you continue.

   ```bash
   systemctl is-active mdatp
   ```


   The command must return `inactive`. Don't continue until the service is stopped.

3. Copy the onboarding file to `/etc/opt/microsoft/mdatp/`, set its ownership to `root:root`, and restrict read and write access to the root user.

   ```bash
   sudo cp mdatp_onboard.json /etc/opt/microsoft/mdatp/mdatp_onboard.json
   sudo chown root:root /etc/opt/microsoft/mdatp/mdatp_onboard.json
   sudo chmod 600 /etc/opt/microsoft/mdatp/mdatp_onboard.json
   ```

Note

The onboarding file is tenant-specific. Store golden images that contain the onboarding file securely, and rebuild the image if you need to onboard machines to a different tenant.

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

## Handle hostname changes on cloned machines

Defender for Endpoint reads the machine's hostname when the `mdatp` service starts and uses it to represent the device in the Microsoft Defender portal. If the hostname changes after the service starts, Defender for Endpoint continues to report the machine with the temporary or template hostname and its associated device ID until the service restarts. When the `mdatp` service restarts, Defender for Endpoint assigns the machine a new device ID and reports it with the current hostname.

On machines created from a golden image, the final hostname is often set during first boot by a provisioning service, such as `cloud-init`, a cloud platform agent, or a custom startup script. These services can run at the same time as the `mdatp` service. If `mdatp` starts first, it picks up the hostname from the golden image instead of the clone's final hostname.

Important

If the hostname is set by a service that can run at the same time as the `mdatp` service, make sure the hostname is stable before you start the `mdatp` service on the cloned machine.

### Start Defender only after the hostname is stable

1. **On the golden image**, after you stop the service, disable it so that it doesn't start automatically when a clone boots.

   ```bash
   sudo systemctl stop mdatp
   sudo systemctl disable mdatp
   ```

2. **On each cloned machine**, wait until the service that sets the hostname has finished and the hostname has its final value.
3. Enable and start the Defender service.

   ```bash
   sudo systemctl enable --now mdatp
   ```

You can run the last two steps from your existing provisioning or startup automation after the hostname is set. For example, if `cloud-init` sets the hostname:

```bash
#!/bin/bash
# Wait for cloud-init to finish provisioning, including setting the hostname.
cloud-init status --wait

# Optional: Confirm that the hostname is no longer the golden image hostname.
GOLDEN_IMAGE_HOSTNAME="<golden-image-hostname>"
until [ "$(hostname)" != "$GOLDEN_IMAGE_HOSTNAME" ]; do
  sleep 5
done

# Start Defender for Endpoint after the hostname is stable.
systemctl enable --now mdatp
```

Adjust the wait condition to match the service that sets the hostname in your environment.

### Verify the cloned machine

After the service starts on the cloned machine, verify onboarding and health:

```bash
mdatp health --field org_id
mdatp health --field healthy
mdatp health --field licensed
```

Confirm that `org_id` shows your organization ID and that `healthy` and `licensed` both return `true`. In the Microsoft Defender portal, confirm that the device appears with the clone's final hostname.

### If the hostname changes after Defender starts

If the hostname of a Linux server changes after Defender for Endpoint starts, restart the `mdatp` service so that the new hostname is used:

```bash
sudo systemctl restart mdatp
```

## Related content

Tip

Do you want to learn more? Engage with the Microsoft Security community in our Tech Community: [Microsoft Defender for Endpoint Tech Community](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/bd-p/MicrosoftDefenderATP).
