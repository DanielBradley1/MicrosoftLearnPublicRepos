<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/education/guide/1-windows/win10win11upgrade -->
<!-- Sitemap-Last-Modified: 2025-08-22 -->

# Windows 10 upgrade to Windows 11 considerations

![Diagram that shows Windows 10 end of support is October 12, 2025.](https://learn.microsoft.com/en-us/microsoft-365/education/guide/images/reference/windows-10-end-support.png)

## Microsoft Education Solution: Equity, Accessibility, Security

Microsoft is committed to empowering students and educators to achieve more. We support our mission with best-in-class Windows 11 Pro Education and offering the best classroom applications, enabling improved student outcomes.

- **Inclusively Designed**

  - *Secure and Future-proof Intel*- Solutions that are secure, future-proof, and trustworthy are essential to unlocking digital transformation.
  - *Inclusively Designed*- Accessible and inclusive tools provide the support students need to reach their full potential.

- **Accelerate Learning**

  - *Accelerate Learning*-Real-time data insights can accelerate learning and support career and workforce development.

- **Foster Well-Being**

  - *Foster Well-Being*-Products that support social and emotional well-being affect student motivation, engagement, and learning.

## Why schools should upgrade to a Windows 11 device

- Schools are prime targets to cybersecurity threats.
- The technology can counteract human error.
- Superior security solutions help keep our schools safe.
- Enhanced AI capabilities are available with Microsoft Copilot.

## Steps to Windows 10 Upgrades

### Assess

- Where are you on your Windows 11 journey
- Benefits and end of support pathway
- Windows 11 Readiness Assessment

### Plan

- Windows 11 Acceleration Plan
- Consider Windows 11 Proof-of-Concept \(POC\)
- SLF-Shape the Future \(K-12\)
- Consider Copilot+PC devices

### Deploy

- Deployment Rings
- Windows 11 can be managed alongside Windows 10
- Success Case Studies
- Windows 11 Onboarding Kit

## Paths to Windows 11 Upgrades

- Upgrade eligible devices from Windows 10 to Windows 11
- Refresh existing devices to new Windows 11 PCs
- Extended support for Windows 10 & Refresh Planning \(Windows 10 end of support - End of Support\)

### Upgrade eligible devices from Windows 10 to Windows 11

<details>
<summary>Click here for instructions to upgrade eligible devices from Windows 10 to Windows 11.</summary>

Upgrading to Windows 11 gives you the latest features and security improvements, but it’s important to prepare properly. This step-by-step guide helps you check if your PC is ready, back up your data, choose an upgrade method, troubleshoot common issues, and perform post-upgrade optimizations. Follow the steps in the following order:

#### 1. Check Windows 11 System Requirements

Before attempting the upgrade, make sure your PC meets the minimum hardware requirements for Windows 11:

- **Processor \(CPU\):** 1 GHz or faster, **2 or more cores**, and on the list of supported 64-bit CPUs. \(Most Intel 8th Gen/AMD Ryzen 2000 series or newer processors are supported.\)
- **Memory \(RAM\):** **4 GB** or more.
- **Storage:** **64 GB** or larger storage device. Ensure you have additional free space for the upgrade process \(around 20 GB or more free is recommended\).
- **System Firmware:** UEFI firmware with **Secure Boot** capability. \(You may need to enable UEFI mode and Secure Boot in your BIOS settings if currently using Legacy/CSM mode.\)
- **TPM:** **Trusted Platform Module \(TPM\) 2.0** enabled. This security chip is required – most PCs from the last five years have TPM 2.0, but it might be turned off in firmware settings.
- **Graphics & Display:** A graphics card compatible with DirectX 12 or later \(WDDM 2.0 driver\) and a display larger than 9″ with at least 720p resolution \(1280×720\).
- **Internet and Accounts:** For Windows 11 Home edition, internet connectivity and a Microsoft account are required during the initial setup. \(Windows 11 Pro allows local account setup, but network is still needed for updates.\)
- **Operating System:** Your PC should be running Windows 10 version 2004 or later to directly upgrade via Windows Update. If you have an older version, install the latest Windows 10 updates first.

#### 2. Verify Compatibility with the PC Health Check App

Run Microsoft’s **PC Health Check** tool to confirm your PC is officially compatible with Windows 11:

1. **Download and install PC Health Check:** Get the tool from Microsoft’s site \(**aka.ms/GetPCHealthCheckApp**\).
2. **Run the compatibility check:** Open **PC Health Check**, and under the *Windows 11* section select **"Check now"**.
3. **Review the result:** If your PC **meets the requirements**, you see a message that “This PC can run Windows 11.” If **not**, the tool lists which criteria aren't met.
4. **Address any issues:** You may need to enable TPM or Secure Boot in your BIOS if they're turned off.

#### 3. Back Up Important Data

Upgrading from Windows 10 to 11 is designed to **keep all your files and applications in place**, but it’s always wise to back up your important data before any major OS upgrade:

- **Back up user files:** Save copies of your critical files \(documents, photos, etc.\) to an external drive or a cloud service \(OneDrive, Google Drive, or an external USB drive\).
- **Ensure you know your app logins:** Have a record of any essential software product keys or account credentials in case you need to reauthenticate after upgrading.
- **Consider an image backup \(optional\):** Advanced users can create a full system image using Windows Backup & Restore or third-party software.

#### 4. Methods to Upgrade from Windows 10 to Windows 11

##### Option 1: Windows Update \(Recommended\)

1. **Open Windows Update:** Go to **Start > Settings > Update & Security > Windows Update**.
2. **Check for updates:** Select **“Check for updates.”**
3. **Look for Windows 11 upgrade:** If eligible, a banner appears offering **“Upgrade to Windows 11.”** Select **Download and install**.
4. **Restart when prompted:** The upgrade installs and your PC will reboot several times.

##### **Option 2: Windows 11 Installation Assistant**

1. **Download the tool:** Get the **Windows 11 Installation Assistant** from Microsoft’s website.
2. **Run as administrator:** Launch the tool and follow the on-screen instructions.
3. **Download and install Windows 11:** The assistant downloads the update, and prompt you to restart.

##### **Option 3: ISO File / USB Installation \(Advanced\)**

1. **Download the Windows 11 ISO** from Microsoft.
2. **Create installation media:** Use the Windows Media Creation Tool to make a bootable USB.
3. **Launch the upgrade from Windows 10:** Open the mounted ISO and run **`Setup.exe`**.
4. **Follow the Setup wizard:** Choose **Keep personal files and apps** if you want to retain your data.
5. **Complete installation:** Windows 11 will install and reboot several times.

#### 5. Troubleshooting Common Upgrade Issues

##### **Issue: TPM 2.0 Not Detected**

- Restart your PC and enter BIOS/UEFI \(press **F2, F10, Del, or Esc** at boot\).
- Look for **TPM** or **PTT** \(Intel\) / **fTPM** \(AMD\) and enable it.
- Save changes and restart.

##### **Issue: Secure Boot Disabled**

- In BIOS/UEFI, ensure the system is in **UEFI mode** \(not Legacy/CSM\).
- Enable **Secure Boot** under Boot options.
- Save and restart.

##### **Issue: Not Enough Storage Space**

- Free up space by deleting temporary files and unused applications.
- Empty Recycle Bin and use **Disk Cleanup** to remove system junk.

##### **Issue: Windows 11 Upgrade Not Showing in Windows Update**

- Ensure your Windows 10 is fully updated.
- Check Microsoft's Windows 11 release status page.
- Use the **Installation Assistant** or ISO method.

#### 6. Post-Upgrade Setup and Optimization

- **Install Updates and Drivers:** Run **Windows Update** after the upgrade to get the latest patches.
- **Verify Settings and Account:** Ensure your **Microsoft account is signed in** and Windows is activated.
- **Customize Windows 11:** Adjust the Start menu, taskbar, and personalization settings.
- **Remove Old Windows Files:** Run **Disk Cleanup** and select **Previous Windows Installation\(s\)** to free up space.
- **Know the Rollback Option:** You have **10 days** to revert to Windows 10 via **Settings > System > Recovery** if needed.
</details>

### Refresh existing devices to new Windows 11 PCs

- [Purchase Windows 11 Machines](https://www.microsoft.com/windows/get-windows-11)

### Extended support for Windows 10 & Refresh Planning \(Windows 10 - End of Support\)

There are two options for ESUs for your Windows 10 estate: the traditional license using a 5-by-5 activation key or activation as part of your Windows 365 or Azure Virtual Desktop subscription.

**Traditional ESU activation:**

- With the 5-by-5 activation method, you download an activation key and apply it to individual Windows 10 devices that you've selected for your ESU program. Manage it via scripting or the Volume Activation Management Tool \(VAMT\), among other methods. You can use on-premises management tools such as Windows Server Update Services \(WSUS\) to download and apply the updates to your Windows 10 devices.
- The 5-by-5 activation subscription will establish the Year One list price of ESU for Windows 10. This is the base license and will cost $1 USD per device for Year 1. It's now available through Volume Licensing.

For those organizations using a Microsoft cloud-based update management solution \(that is, Microsoft Intune or Windows Autopatch\), there's a special offer. You can manage and monitor the complete update process in Microsoft Intune or utilize Windows Autopatch to fully automate the update process for you. With Windows Autopatch, there's no required action on your part. Check the monthly update reports to understand the status of your environment.

**ESU through Windows 365 and Azure Virtual Desktop:**

Windows 10 Cloud PCs in Windows 365 and virtual machines in Azure Virtual Desktop are automatically entitled to ESUs at no additional charge. Additionally, Windows 10 devices accessing Windows 11 Cloud PCs through Windows 365 will automatically be activated to receive security updates without any additional steps.

[Computers and Laptops for Schools](https://www.microsoft.com/education/devices/overview)
