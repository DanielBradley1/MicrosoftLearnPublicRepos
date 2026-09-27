<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/sum/get-started/prepare-for-software-updates-management -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# Prepare for software updates management

*Applies to: Configuration Manager \(current branch\)*

Before the compliance assessment data of the software update displays in the Configuration Manager console and before you can deploy software updates to client computers, you must complete the steps in the following sections.

## Step 1: Install a software update point

The software update point is required on the central administration site, or stand-alone primary site, and on primary sites to enable the software updates compliance assessment and to deploy software updates to clients. The software update point is optional on secondary sites. For details, see [Install a software update point](https://learn.microsoft.com/en-us/intune/configmgr/sum/get-started/install-a-software-update-point)

## Step 2: Synchronize Software Updates

Software updates synchronization is the process of retrieving the software updates metadata that meets the criteria that you configure. Software updates are not displayed in the Configuration Manager console until you synchronize software updates. For details, see [Synchronize software updates](https://learn.microsoft.com/en-us/intune/configmgr/sum/get-started/synchronize-software-updates).

## Step 3: Configure classifications and products to synchronize

Perform this configuration on the central administration site or stand-alone primary site. After you synchronize software updates the first time, Configuration Manager retrieves an updated list of classifications and products. Now, you can select from the new options in the Software Update Point Component properties. After you configure the new classifications and products, repeat step 2 to start software updates synchronization to retrieve software updates metadata for the new criteria. For details, see [Configure classifications and products to synchronize](https://learn.microsoft.com/en-us/intune/configmgr/sum/get-started/configure-classifications-and-products).

## Step 4: Manage settings for software updates

After you synchronize software updates, verify Configuration Manager client settings, group policy configurations, and software updates settings before you deploy software updates. For details, see [Manage settings for software updates](https://learn.microsoft.com/en-us/intune/configmgr/sum/get-started/manage-settings-for-software-updates).
