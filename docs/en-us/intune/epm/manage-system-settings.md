<!-- Source: https://learn.microsoft.com/en-us/intune/epm/manage-system-settings -->
<!-- Sitemap-Last-Modified: 2026-10-02 -->

# Manage system settings with Endpoint Privilege Management

With Microsoft Intune **Endpoint Privilege Management \(EPM\)** your organization's users can run as a standard user \(without administrator rights\) and complete tasks that require elevated privileges. For more information, see [EPM Overview](https://learn.microsoft.com/en-us/intune/epm/overview).

Applies to:

- Windows

An *elevation system settings policy* lets Endpoint Privilege Management \(EPM\) grant standard users access to specific Windows system settings that normally require administrator rights. This policy type supports *network settings*, which let a standard user change IPv4, IPv6, and DNS server values for the network adapters on their device.

Some everyday tasks, like changing an IP address or DNS server, require administrator rights. A standard user who tries to change these values in Windows is blocked by a User Account Control \(UAC\) prompt. With an elevation system settings policy, you let standard users make these specific changes through EPM, without granting broad administrator rights and without a separate app deployment.

A common scenario is a user who travels between sites. To connect a device at a new location, the user might need to set a static IP address or DNS server before the device is online. An elevation system settings policy lets the user make that change, even when the device is offline.

For elevation system settings policies to take effect, devices must also have an *elevation settings policy* targeted that enables EPM. For more information, see [Manage elevation settings](https://learn.microsoft.com/en-us/intune/epm/manage-elevation-settings).

## About elevation system settings policy

An *elevation system settings policy* identifies a category of Windows system settings and the elevation behavior that applies when a standard user changes those settings. Each policy contains one or more *rules*. Each rule defines:

- **System setting** - The category of settings the rule applies to. **Network settings** covers IPv4, IPv6, and DNS server configuration for the device's network adapters.
- **Elevation type** - How EPM responds when the user changes a setting. **User confirmed** requires the user to act on a confirmation prompt before the change is applied.
- **Validation** - Optional requirements the user must satisfy when *User confirmed* is selected. You can require a business justification, Windows authentication, or both. A business justification is visible in reporting.

When a device receives an elevation system settings policy, users access the supported settings from a single entry point in the Windows Company Portal. EPM shows only the settings categories that the device has a policy for. For example, if a device has a policy for network settings, the user sees only the network settings experience.

## Create an elevation system settings policy

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431) and go to **Endpoint security** > **Endpoint Privilege Management** > select the **Policies** tab > and then select **Create Policy**.

   Set the *Platform* to **Windows**, *Profile* to **Elevation system settings policy**, and then select **Create**.
2. On **Basics**, enter the following properties:

   - **Name**: Enter a descriptive name for the profile. Name profiles so you can easily identify them later.
   - **Description**: Enter a description for the profile. This setting is optional but recommended.

3. On **Configuration settings**, add a rule that defines the system settings users can change:

   1. Select **Add**, and then select **Edit instance** to open the **Rule properties** pane.
   2. Configure the rule:

      - **Rule name**: Enter a descriptive name for the rule. This field is required.
      - **Description**: Enter an optional description for the rule.
      - **System setting**: Select **Network settings**. This option lets users change IPv4, IPv6, and DNS server values for the device's network adapters.
      - **Elevation type**: Select **User confirmed**. The user must act on a confirmation prompt before a change is applied.
      - **Validation**: Optionally require the user to provide more confirmation when they make a change. Options include:

        - **Business justification**: Require the user to enter a justification for the change. The justification is saved and can be reviewed in reporting.
        - **Windows authentication**: Require the user to authenticate with their organization credentials before the change is applied.


        Note


        You can select multiple validation options. If you don't select any, the user only needs to confirm their intent to apply the change.

   3. Select **Save** to save the rule, and then select **Next**.

4. On the **Scope tags** page, select any desired scope tags to apply, then select **Next**.
5. For **Assignments**, select the groups that receive the policy. For more information on assigning profiles, see [Assign user and device profiles](https://learn.microsoft.com/en-us/intune/device-configuration/assign-device-profile). Select **Next**.
6. For **Review + create**, review your settings and then select **Create**. When you select *Create*, your changes are saved, and the profile is assigned. The policy is also shown in the policy list with a *Policy type* of **Elevation system settings policy**.

After the device's next policy sync, the user can change the configured system settings from the Windows Company Portal.

## End-user experience in the Company Portal

Changing these settings is an end-user task that takes place in the Windows Company Portal, not something you complete in the Intune admin center. The steps in this section describe what your users see and do on their own devices. Share these steps with your users so they know what to expect and how to change the settings you allow.

After a user's device has an assigned elevation system settings policy and completes its next policy sync, the user changes the configured settings:

1. In the Windows Company Portal, the user goes to **Help & support**, and then in the **System settings** tile, selects **Edit settings**.

   The **System settings** tile is the single entry point for all system settings that EPM manages on the device. EPM shows only the settings categories that the device has a policy for.
2. The **Endpoint Privilege Management - Network Settings** window opens and lists the network adapters available on the device. The user selects an adapter, like **Ethernet**.
3. The adapter details show the current IPv4, IPv6, and DNS server values, along with hardware properties for the adapter. The user selects **Edit** next to the section they want to change.
4. In the edit dialog, the user selects how the setting is assigned:

   - **Automatic \(DHCP\)**: The adapter obtains the values automatically.
   - **Manual**: The user enters the values. For IPv4, the fields are:

     - **IP Address**
     - **Subnet Mask**
     - **Gateway**
     - **Preferred DNS**
     - **Alternate DNS**


     For IPv6, the fields are:


     - **IPv6 Address**
     - **Prefix Length**
     - **Gateway**
     - **Preferred DNS**
     - **Alternate DNS**

5. The user selects **Save**. Depending on the policy's validation options, the user might need to provide a business justification, authenticate, or both before the change is applied.

## Next steps

[Reports for Endpoint Privilege Management](https://learn.microsoft.com/en-us/intune/epm/monitor-reports)
