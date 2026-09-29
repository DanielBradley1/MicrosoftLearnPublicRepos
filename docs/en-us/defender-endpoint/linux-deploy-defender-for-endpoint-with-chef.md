<!-- Source: https://learn.microsoft.com/en-us/defender-endpoint/linux-deploy-defender-for-endpoint-with-chef -->
<!-- Sitemap-Last-Modified: 2026-05-21 -->

# Deploy Defender for Endpoint on Linux with Chef

Important

This article contains information about third-party tools. This is provided to help complete integration scenarios, however, Microsoft does not provide troubleshooting support for third-party tools.  
Contact the third-party vendor for support.

## Introduction

You can deploy [Defender for Endpoint on Linux](https://learn.microsoft.com/en-us/defender-endpoint/microsoft-defender-endpoint-linux) by using various tools and methods. This article describes how to deploy Defender for Endpoint on Linux at scale with Chef using two methods:

- Install using installer script
- Manually configure the repositories for more granular control over the deployment

To use another method, refer to the [See also](#see-also) section.

Important

If you want to run multiple security solutions side by side, see [Considerations for performance, configuration, and support](https://learn.microsoft.com/en-us/defender-endpoint/mde-side-by-side).

You might have already configured mutual security exclusions for devices onboarded to Microsoft Defender for Endpoint. If you still need to set mutual exclusions to avoid conflicts, see [Add Microsoft Defender for Endpoint to the exclusion list for your existing solution](https://learn.microsoft.com/en-us/defender-endpoint/switch-to-mde-phase-2#step-2-add-microsoft-defender-for-endpoint-to-the-exclusion-list-for-your-existing-solution).

## Prerequisites

Before you get started, see [Prerequisites for Defender for Endpoint on Linux](https://learn.microsoft.com/en-us/defender-endpoint/mde-linux-prerequisites) for a description of prerequisites and system requirements.

## Download the onboarding package

Warning

Repackaging the Defender for Endpoint installation package is not a supported scenario. Doing so can negatively impact the integrity of the product and lead to adverse results, including but not limited to triggering tampering alerts and updates failing to apply.

1. Sign in to the [Microsoft Defender portal](https://security.microsoft.com/) then navigate to **System** > **Settings** > **Endpoints** > **Device management** > **Onboarding**.
2. In the first drop-down menu, select **Linux Server** as the operating system. In the second drop-down menu, select **Your preferred Linux configuration management tool** as the deployment method.
3. Select **Download onboarding package** and save the file as `WindowsDefenderATPOnboardingPackage.zip`.
4. Extract the contents of the archive using the following command:

   ```
   unzip WindowsDefenderATPOnboardingPackage.zip
   ```


   The expected output is:


   ```
   Archive:  WindowsDefenderATPOnboardingPackage.zip
   inflating: mdatp_onboard.json
   ```

## Create a directory structure

Before you begin, ensure the Chef components are already installed and a Chef repository \(chef generate repo <reponame>\) exists to store the cookbook that's used to deploy to Defender for Endpoint on Chef-managed Linux servers.

The following command creates a new folder structure for the new cookbook called **mdatp**. You can also use an existing cookbook if you already have one you'd like to use to add the Defender for Endpoint deployment into.

```bash
chef generate cookbook mdatp
```

After the cookbook is created, create a files folder inside the cookbook folder that you created:

```bash
mkdir mdatp/files
```

Copy `mdatp_onboard.json` to the `/tmp` folder.

On the Chef Workstation, navigate to the **mdatp/recipes** folder, which is automatically created when the cookbook is generated. Use your preferred text editor \(like vi or nano\) to add the following instructions to the end of the **default.rb** file, and then save and close the file: `include_recipe '::install_mdatp'`.

## Create a cookbook

A cookbook can be created through any of the following methods:

- [Using an installer script](https://learn.microsoft.com/en-us/defender-endpoint/linux-deploy-defender-for-endpoint-with-chef#create-a-cookbook-using-installer-script)
- [Manually configuring repositories](https://learn.microsoft.com/en-us/defender-endpoint/linux-deploy-defender-for-endpoint-with-chef#create-a-cookbook-by-manually-configuring-repositories)

### Create a cookbook using installer script

1. Download the installer bash script. Pull the [installer bash script](https://github.com/microsoft/mdatp-xplat/blob/master/linux/installation/mde_installer.sh) from Microsoft GitHub Repository or use the following command to download it:

   ```bash
   wget https://raw.githubusercontent.com/microsoft/mdatp-xplat/refs/heads/master/linux/installation/mde_installer.sh /tmp
   ```

2. Create a new recipe file named **install\_mdatp.rb** in the recipes folder `~/cookbooks/mdatp/recipes/install_mdatp.rb` and add the following text to the file. You can also download the file directly from [GitHub](https://github.com/microsoft/mdatp-xplat/blob/master/linux/installation/third_party_installation_playbooks/chef.install_mdatp_simplified.rb).

   ```bash
   mdatp = "/etc/opt/microsoft/mdatp"

   #Download the onboarding json from tenant, keep the same at specific location
   onboarding_json = "/tmp/mdatp_onboard.json"

   #Download the installer script from: https://github.com/microsoft/mdatp-xplat/blob/master/linux/installation/mde_installer.sh
   #Place the same at specific location, edit this if needed
   mde_installer= "/tmp/mde_installer.sh"


   ## Invoke the mde-installer script 
   bash 'Installing mdatp using mde-installer' do
       code <<-EOS
       chmod +x #{mde_installer}
       #{mde_installer} --install --onboard #{onboarding_json}
       EOS
   end
   ```

Note

The installer script also supports other parameters such as channel, realtime protection, version, etc. To select from the list of available options, check help through the following command: `./mde_installer.sh --help`

### Create a cookbook by manually configuring repositories

Create a new recipe file named **install\_mdatp.rb** in the recipes folder `~/cookbooks/mdatp/recipes/install_mdatp.rb` and add the following text to the file. You can also download the file directly from [Github](https://github.com/microsoft/mdatp-xplat/blob/master/linux/installation/third_party_installation_playbooks/chef.install_mdatp_manual.rb).

```powershell
#Add Microsoft Defender
case node['platform_family']
when 'debian'
 apt_repository 'MDATPRepo' do
   arch               'amd64'
   cache_rebuild      true
   cookbook           false
   deb_src            false
   key                'BC528686B50D79E339D3721CEB3E94ADBE1229CF'
   keyserver          "keyserver.ubuntu.com"
   distribution       'jammy'
   repo_name          'microsoft-prod'
   components         ['main']
   uri                "https://packages.microsoft.com/ubuntu/22.04/prod"
 end
apt_package "mdatp"
when 'rhel'
 yum_repository 'microsoft-prod' do
   baseurl            "https://packages.microsoft.com/rhel/7/prod/"
   description        "Microsoft Defender for Endpoint"
   enabled            true
   gpgcheck           true
   gpgkey             "https://packages.microsoft.com/keys/microsoft.asc"
 end
 if node['platform_version'] <= 8 then
    yum_package "mdatp"
 else
    dnf_package "mdatp"
 end
end

#Create MDATP Directory
mdatp = "/etc/opt/microsoft/mdatp"
onboarding_json = "/tmp/mdatp_onboard.json"

directory "#{mdatp}" do
  owner 'root'
  group 'root'
  mode 0755
  recursive true
end

#Onboarding using tenant json 
file "#{mdatp}/mdatp_onboard.json" do
  content lazy { ::File.open(onboarding_json).read }
  owner 'root'
  group 'root'
  mode '0644'
  action :create_if_missing
end
```

Note

You can modify the os distribution, distribution version number, channel \(prod/insider-fast, insiders-slow\) and repo name to match the version you're deploying to and the channel you'd like to deploy to. Run `chef-client --local-mode --runlist  'recipe[mdatp]'` to test the cookbook on the Chef workstation.

## Troubleshoot installation issues

To troubleshoot issues:

1. For information on how to find the log that's generated automatically when an installation error occurs, see [Log installation issues](https://learn.microsoft.com/en-us/defender-endpoint/linux-resources#log-installation-issues).
2. For information about common installation issues, see [Installation issues](https://learn.microsoft.com/en-us/defender-endpoint/linux-support-install).
3. If the health of the device is `false`, see [Defender for Endpoint agent health issues](https://learn.microsoft.com/en-us/defender-endpoint/health-status).
4. For product performance issues, see [Troubleshoot performance issues](https://learn.microsoft.com/en-us/defender-endpoint/linux-support-perf).
5. For proxy and connectivity issues, see [Troubleshoot cloud connectivity issues](https://learn.microsoft.com/en-us/defender-endpoint/linux-support-connectivity). To get support from Microsoft, open a support ticket, and provide the log files created by using the [client analyzer](https://learn.microsoft.com/en-us/defender-endpoint/overview-client-analyzer).

## How to configure policies for Microsoft Defender on Linux

You can configure antivirus or EDR settings on your endpoints using any of the following methods:

- See [Set preferences for Microsoft Defender for Endpoint on Linux](https://learn.microsoft.com/en-us/defender-endpoint/linux-preferences).
- See [security settings management](https://learn.microsoft.com/en-us/intune/intune-service/protect/mde-security-integration) to configure settings in the Microsoft Defender portal.

## Uninstall MDATP cookbook

To uninstall Defender, save the following as a cookbook `~/cookbooks/mdatp/recipes/uninstall_mdatp.rb`.

```powershell
#Uninstall the Defender package
case node['platform_family']
when 'debian'
 apt_package "mdatp" do
   action :remove
 end
when 'rhel'
 if node['platform_version'] <= 8
then
    yum_package "mdatp" do
      action :remove
    end
 else
    dnf_package "mdatp" do
      action :remove
    end
 end
end
```

To include this step as part of the recipe, add `include_recipe ':: uninstall_mdatp` to your `default.rb` file within the recipe folder. Ensure that you have removed the `include_recipe '::install_mdatp'` from the `default.rb` file.

## See also

- [Prerequisites for Microsoft Defender for Endpoint on Linux](https://learn.microsoft.com/en-us/defender-endpoint/mde-linux-prerequisites)
- [Use installer script based deployment to deploy Defender for Endpoint on Linux](https://learn.microsoft.com/en-us/defender-endpoint/linux-installer-script)
- [Deploy Defender for Endpoint on Linux with Ansible](https://learn.microsoft.com/en-us/defender-endpoint/linux-install-with-ansible)
- [Deploy Defender for Endpoint on Linux with Puppet](https://learn.microsoft.com/en-us/defender-endpoint/linux-install-with-puppet)
- [Deploy Defender for Endpoint on Linux with Saltstack](https://learn.microsoft.com/en-us/defender-endpoint/linux-install-with-saltack)
- [Deploy Defender for Endpoint on Linux manually](https://learn.microsoft.com/en-us/defender-endpoint/linux-install-manually)
- [Connect your non-Azure machines to Microsoft Defender for Cloud with Defender for Endpoint](https://learn.microsoft.com/en-us/azure/defender-for-cloud/onboard-machines-with-defender-for-endpoint) \(direct onboarding using Defender for Cloud\)
- [Deployment guidance for Defender for Endpoint on Linux for SAP](https://learn.microsoft.com/en-us/defender-endpoint/mde-linux-deployment-on-sap)
