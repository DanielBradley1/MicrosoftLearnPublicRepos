<!-- Source: https://learn.microsoft.com/en-us/defender-endpoint/network-isolation-exclusions -->
<!-- Sitemap-Last-Modified: 2026-07-17 -->

# Network isolation exclusions

Isolation exclusions let you exclude specific processes, IP addresses, or services from network isolation by applying the selective isolation response action to devices.

Network isolation in Microsoft Defender for Endpoint restricts a compromised device's communication to prevent threat spread. However, certain critical services, such as management tools or security solutions, might need to remain operational.

Isolation exclusions allow designated processes or endpoints to bypass the restrictions of network isolation, ensuring essential functions \(for example, remote remediation or monitoring\) continue while limiting broader network exposure.

## Prerequisites

Before you use isolation exclusions, make sure the following prerequisites are met:

- Isolation exclusion must be enabled.
- Enabling isolation exclusion requires Security Admin or Manage Security settings permissions or above.

### Supported operating systems

Isolation exclusion is supported on the following operating systems:

- Isolation exclusion is available on Windows 11, Windows 10 version 1703 or later, Windows Server 2016 and later, Windows Server 2012 R2, macOS, and Azure Stack HCI OS, version 23H2 and later.

Warning

**Any exclusion weakens device isolation and increases security risks. To minimize risk, configure exclusions only when strictly necessary**.

Regularly review and update exclusions to align with security policies.

## Isolation modes

There are two modes of isolation: **full isolation** and **selective isolation**.

- **Full isolation**: In full isolation mode, the device is completely isolated from the network, and no exceptions are allowed. All traffic is blocked, except for essential communications with the Defender agent. Exclusions aren't applied in full isolation mode.

  Full isolation mode is the most secure option, suitable for scenarios where a high level of containment is necessary. For more information about full isolation mode, see [Isolate devices from the network](https://learn.microsoft.com/en-us/defender-endpoint/respond-machine-alerts#isolate-devices-from-the-network).
- **Selective isolation**: Selective isolation mode allows administrators to apply exclusions to ensure that critical tools and network communications can still function, while maintaining the device's isolated state.

## How to use isolation exclusion

There are two steps to using isolation exclusion: defining isolation exclusion rules, and applying isolation exclusion on a device.

[![Screenshot showing how to enable isolation exclusions.](https://learn.microsoft.com/en-us/defender-endpoint/media/network-isolation-exclusions/enable-exclusions.png)](https://learn.microsoft.com/en-us/defender-endpoint/media/network-isolation-exclusions/enable-exclusions.png#lightbox)

Note

Once the isolation exclusions feature has been enabled, the previously embedded exclusions for Microsoft Teams, Outlook, and Skype no longer apply, and the exclusions list starts empty on all platforms. If Microsoft Teams, Outlook, and Skype still require access during isolation, you must manually define new exclusion rules for them.

Skype has been deprecated and is no longer included in any default exclusions.

### Step 1: Define global exclusions in the settings

To define global isolation exclusion rules, perform the following steps:

1. In the [Microsoft Defender portal](https://security.microsoft.com), navigate to **Settings** > **Endpoints** > **Advanced features** > **Isolation Exclusion Rules**.
2. Select the relevant OS tab \(Windows rules or Mac rules\).
3. Select **+ Add exclusion rule**

   [![Screenshot showing how to add a new isolation exclusion rule.](https://learn.microsoft.com/en-us/defender-endpoint/media/network-isolation-exclusions/add-new-exclusion-rule.png)](https://learn.microsoft.com/en-us/defender-endpoint/media/network-isolation-exclusions/add-new-exclusion-rule.png#lightbox)
4. The **Add new exclusion rule** dialog appears:

   [![Screenshot showing the fields required for defining an isolation exclusion rule.](https://learn.microsoft.com/en-us/defender-endpoint/media/network-isolation-exclusions/exclusion-rule-definition.png)](https://learn.microsoft.com/en-us/defender-endpoint/media/network-isolation-exclusions/exclusion-rule-definition.png#lightbox)

   Fill in the isolation exclusion parameters. Red asterisks denote required parameters. The parameters and their valid values are:

   - **Rule name**: Provide a name for the rule.
   - **Rule description**: Describe the purpose of the rule.
   - **Process path** \(Windows only\): The file path of an executable is its location on the endpoint. You can define one executable to be used in each rule.

     Examples:

     - `C:\Windows\System\Notepad.exe`
     - `%WINDIR%\Notepad.exe`


     Notes:


     - The executable must exist when isolation is applied, otherwise the exclusion rule is ignored.
     - The exclusion doesn't apply to any child processes created by the specified process.

   - **Service name** \(Windows only\): Windows service short names can be used in cases where you want to exclude a service \(not an application\) that is sending or receiving traffic. Service short names can be retrieved by running the **Get-Service** command from PowerShell. You can define one service to be used in each rule.

     Example: termservice
   - **Package family name** \(Windows only\): The Package Family Name \(PFN\) is a unique identifier assigned to Windows app packages. The PFN format follows this structure: `<Name>_<PublisherId>`.

     Package family names can be retrieved by running the **Get-AppxPackage** command from PowerShell. For example, to get the new Microsoft Teams PFN, run `Get-AppxPackage MSTeams`, and look for the value of the **PackageFamilyName** property.

     Supported on:

     - Windows 11, version 22H2 or later \(version 23H2 requires KB5050092\)
     - Windows 10, version 22H2 or later \(requires KB5050081\)
     - Windows Server 2025 or later
     - Windows Server, version 23H2 or later
     - Azure Stack HCI OS, version 23H2 or later

   - **Direction**: The connection direction \(Inbound/Outbound\). Examples:

     - **Outbound connection**: If the device initiates a connection, for instance, an HTTPS connection to a remote backend server, define only an outbound rule. Example: The device sends a request to 1.1.1.1 \(outbound\). In this case, no inbound rule is needed, as the response from the server is automatically accepted as part of the connection.
     - **Inbound connection**: If the device is listening to incoming connections, define an **inbound rule**.

   - **Remote IP**: The IP \(or IPs\) with which communication is allowed while the device is isolated from the network.

     Supported IP formats:

     - IPv4/IPv6, with optional CIDR notation
     - A comma-separated list of valid IPs


     Up to 20 IP addresses can be defined per rule.


     Valid input examples:


     - Single IP address: `1.1.1.1`
     - IPV6 address: `2001:db8:85a3::8a2e:370:7334`
     - IP address with CIDR notation \(IPv4 or IPv6\): `1.1.1.1/24`. This example defines a range of IP addresses. In this case, it includes all IPs from 1.1.1.0 to 1.1.1.255. The /24 represents the subnet mask, which specifies that the first 24 bits of the address are fixed, and the remaining 8 bits define the address range.

5. Save and apply changes.

The global isolation exclusion rules you define in the portal apply whenever selective isolation is enabled for a device.

### Step 2: Apply selective isolation to a specific device

1. Navigate to the device page in the portal.
2. Select **Isolate device** and choose **Selective isolation**.
3. Check **Use isolation exclusions to allow specific communication while the device is isolated** and enter a comment.

   [![Screenshot showing how to apply an exclusion rule to a device.](https://learn.microsoft.com/en-us/defender-endpoint/media/network-isolation-exclusions/apply-exclusion-rule.png)](https://learn.microsoft.com/en-us/defender-endpoint/media/network-isolation-exclusions/apply-exclusion-rule.png#lightbox)
4. Select **Confirm**.

Exclusions that were applied to a specific device can be reviewed in the Action center history.

[![Screenshot showing exclusions in the Action center history.](https://learn.microsoft.com/en-us/defender-endpoint/media/network-isolation-exclusions/review-exclusions.png)](https://learn.microsoft.com/en-us/defender-endpoint/media/network-isolation-exclusions/review-exclusions.png#lightbox)

#### Apply selective isolation via API

Alternatively, you can apply selective isolation via API. To do so, set the **IsolationType** parameter to *Selective*. For more information, see [Isolate machine API](https://learn.microsoft.com/en-us/defender-endpoint/api/isolate-machine).

## Exclusion logic

Isolation exclusions are evaluated according to the following logic:

- All rules that match are applied.
- Within a single rule, conditions use AND logic \(all must match\).
- Undefined conditions in a rule are treated as "any" \(that is, unrestricted for that parameter\).

For example, if the following rules are defined:

```text
Rule 1:

   Process path = c:\example.exe
   Remote IP = 1.1.1.1
   Direction = Outbound

Rule 2:

   Process path = c:\example_2.exe
   Direction = Outbound

Rule 3:

   Remote IP = 18.18.18.18
   Direction = Inbound
```

- *example.exe* can only initiate network connections to remote IP 1.1.1.1.
- *example\_2.exe* can initiate network connections to every IP address.
- The device can receive inbound connection from IP address 18.18.18.18.

## Considerations and limitations

Changes to exclusion rules only impact new isolation requests. Devices that were already isolated remain with the exclusions that were defined when they were applied. To apply updated exclusion rules to isolated devices, release those devices from isolation and then reisolate them.

Keeping existing exclusions unchanged for already-isolated devices ensures that isolation rules remain consistent throughout the duration of an active isolation session.

## Related content

- [Take response actions on a device](https://learn.microsoft.com/en-us/defender-endpoint/respond-machine-alerts)
- [Investigate files](https://learn.microsoft.com/en-us/defender-endpoint/investigate-files)
- [Manual response actions in Microsoft Defender for Endpoint Plan 1](https://learn.microsoft.com/en-us/defender-endpoint/defender-endpoint-plan-1#manual-response-actions)
