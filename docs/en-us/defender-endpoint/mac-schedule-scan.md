<!-- Source: https://learn.microsoft.com/en-us/defender-endpoint/mac-schedule-scan -->
<!-- Sitemap-Last-Modified: 2026-09-19 -->

# Schedule scans with Microsoft Defender for Endpoint on macOS

Scheduled antivirus scans help ensure that macOS devices are scanned regularly without relying on users to start scans. Security administrators can configure hourly or daily quick scans and weekly quick or full scans, and use multiple schedules on the same device. Use this guidance to deploy scan schedules through a mobile device management \(MDM\) profile or configure them locally with the `mdatp` command-line tool.

## Prerequisites

- Review the shared [prerequisites for Defender for Endpoint on macOS](https://learn.microsoft.com/en-us/defender-endpoint/microsoft-defender-endpoint-mac-prerequisites).
- Install Defender for Endpoint platform update version `101.23122.0005` or later.

## Understand scheduled scan options

In addition to starting scans on demand, schedule scans to run at regular intervals or specific times. For example, schedule a quick scan at the beginning of each workday and a full scan once a week.

Defender for Endpoint supports hourly, daily, and weekly schedules. Hourly and daily schedules run quick scans. Weekly schedules can run quick or full scans. You can configure all three schedule types simultaneously. See the [daily and weekly scan example](#example-1-schedule-a-daily-quick-scan-and-weekly-full-scan-using-a-plist) and the [hourly, daily, and weekly scan example](#example-2-schedule-an-hourly-quick-scan-a-daily-quick-scan-and-weekly-full-scan-using-a-plist).

## Schedule scans with a configuration profile

Use the `features` and `scheduledScan` dictionaries in a Defender for Endpoint configuration profile to create scheduled scans.

The Microsoft Intune and Jamf Pro examples use Apple property list XML. Save Intune profiles with the `.xml` extension and Jamf Pro property lists with the `.plist` extension. For more information about the XML format, see the [Apple Information Property List file reference](https://developer.apple.com/library/archive/documentation/General/Reference/InfoPlistKeyReference/Articles/AboutInformationPropertyListFiles.html).

Use the following settings to define the scan schedules:

Tip

Schedules are based on the local time zone of the device.

| Setting | Description | Values | Default |
| --- | --- | --- | --- |
| `features.scheduledScan` | Turns the scheduled scan feature on or off. | `enabled`, `disabled` | `disabled` when no daily or weekly configuration is present |
| `dailyConfiguration.interval` | Runs an interval-based quick scan every specified number of hours. | `0` through `24`. `0` disables interval-based scans. | `0` |
| `dailyConfiguration.timeOfDay` | Runs a daily quick scan at the specified number of minutes after midnight. | `0` through `1440` | `0` |
| `weeklyConfiguration.dayOfWeek` | Specifies when a weekly scan runs. | `0`: Never  <br>`1`: Sunday  <br>`2`: Monday  <br>`3`: Tuesday  <br>`4`: Wednesday  <br>`5`: Thursday  <br>`6`: Friday  <br>`7`: Saturday  <br>`8`: Every day | `0` |
| `weeklyConfiguration.timeOfDay` | Runs a weekly scan at the specified number of minutes after midnight. | `0` through `1440` | Profile schema: `0`  <br>`mdatp` command-line interface: `120` |
| `weeklyConfiguration.scanType` | Specifies the weekly scan type. | `quick`, `full` | `quick` |
| `ignoreExclusions` | Specifies whether the scheduled scan ignores configured exclusions. | `true`, `false` | `false` |
| `lowPriorityScheduledScan` | Runs scheduled scans with reduced CPU priority. The scan might take longer to complete. | `true`, `false` | `false` |
| `checkForDefinitionsUpdate` | Checks for security intelligence updates before starting a scheduled scan. | `true`, `false` | `false` |
| `randomizeScanStartTime` | Randomizes daily and weekly scan start times by up to the specified number of hours. | `0` through `23` | `0` |
| `runScanWhenIdle` | Delays a weekly full scan until the device is idle. | `true`, `false` | `false` |

The daily `interval` and `timeOfDay` settings create independent quick scan schedules. If you configure both settings, more than one quick scan might run each day.

### Example 1: Schedule a daily quick scan and weekly full scan

The following profiles demonstrate a daily quick scan and a weekly full scan on Wednesday. Both profiles ignore exclusions and use low-priority scheduling.

Use the [scheduled scan settings table](#schedule-scans-by-deploying-a-plist-in-microsoft-defender-for-endpoint-on-macos) to replace the example times with the values required by your organization.

Open a text editor and use the [Intune profile](#for-intune) or [Jamf Pro property list](#for-jamf-and-other-third-party-mdms) as a guide.

#### For Microsoft Intune

The following sample defines a complete Intune configuration profile that enables a daily quick scan and a weekly full scan.

```XML
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
<plist version="1.0">
<dict>
    <key>PayloadUUID</key>
    <string>C4E6A782-0C8D-44AB-A025-EB893987A295</string>
    <key>PayloadType</key>
    <string>Configuration</string>
    <key>PayloadOrganization</key>
    <string>Microsoft</string>
    <key>PayloadIdentifier</key>
    <string>C4E6A782-0C8D-44AB-A025-EB893987A295</string>
    <key>PayloadDisplayName</key>
    <string>Microsoft Defender for Endpoint settings</string>
    <key>PayloadDescription</key>
    <string>Microsoft Defender for Endpoint configuration settings</string>
    <key>PayloadVersion</key>
    <integer>1</integer>
    <key>PayloadEnabled</key>
    <true/>
    <key>PayloadRemovalDisallowed</key>
    <true/>
    <key>PayloadScope</key>
    <string>System</string>
    <key>PayloadContent</key>
    <array>
        <dict>
            <key>PayloadUUID</key>
            <string>99DBC2BC-3B3A-46A2-A413-C8F9BB9A7295</string>
            <key>PayloadType</key>
            <string>com.microsoft.wdav</string>
            <key>PayloadOrganization</key>
            <string>Microsoft</string>
            <key>PayloadIdentifier</key>
            <string>99DBC2BC-3B3A-46A2-A413-C8F9BB9A7295</string>
            <key>PayloadDisplayName</key>
            <string>Microsoft Defender for Endpoint configuration settings</string>
            <key>PayloadDescription</key>
            <string/>
            <key>PayloadVersion</key>
            <integer>1</integer>
            <key>PayloadEnabled</key>
            <true/>
            <key>features</key>
            <dict>
                <key>scheduledScan</key>
                <string>enabled</string>
            </dict>
            <key>scheduledScan</key>
            <dict>
                <key>ignoreExclusions</key>
                <true/>
                <key>lowPriorityScheduledScan</key>
                <true/>
                <key>dailyConfiguration</key>
                <dict>
                    <key>timeOfDay</key>
                    <integer>880</integer>
                </dict>
                <key>weeklyConfiguration</key>
                <dict>
                    <key>dayOfWeek</key>
                    <integer>4</integer>
                    <key>timeOfDay</key>
                    <integer>885</integer>
                    <key>scanType</key>
                    <string>full</string>
                </dict>
            </dict>
        </dict>
    </array>
</dict>
</plist>
```

Save the file as `com.microsoft.wdav.xml`.

#### For Jamf Pro and compatible MDM solutions

The following property list configures a daily quick scan and weekly full scan for Jamf Pro and other MDM solutions that accept property lists. Save the content as `com.microsoft.wdav.plist`.

```XML
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
<plist version="1.0">
<dict>
    <key>features</key>
    <dict>
        <key>scheduledScan</key>
        <string>enabled</string>
    </dict>
    <key>scheduledScan</key>
    <dict>
        <key>ignoreExclusions</key>
        <true/>
        <key>lowPriorityScheduledScan</key>
        <true/>
        <key>dailyConfiguration</key>
        <dict>
            <key>timeOfDay</key>
            <integer>885</integer>
        </dict>
        <key>weeklyConfiguration</key>
        <dict>
            <key>dayOfWeek</key>
            <integer>4</integer>
            <key>timeOfDay</key>
            <integer>880</integer>
            <key>scanType</key>
            <string>full</string>
        </dict>
    </dict>
</dict>
</plist>
```

Save the file as `com.microsoft.wdav.plist`.

After you deploy the profile, verify that the scheduled scan is configured as a managed preference by running the following command:

```bash
mdatp health --details scheduled_scan
```

In the results, verify that the scheduled scan reports `managed`.

### Example 2: Schedule interval-based and daily quick scans and a weekly full scan

The following profiles demonstrate an interval-based quick scan, a daily quick scan, and a weekly full scan on Wednesday.

Open a text editor and use the [Intune profile](#for-intune-1) or [Jamf Pro property list](#for-jamf-and-other-third-party-mdms-1) as a guide.

#### For Microsoft Intune

The following sample packages the scheduled scan settings into a complete Intune configuration profile.

```XML
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
<plist version="1.0">
<dict>
     <key>PayloadUUID</key>
     <string>C4E6A782-0C8D-44AB-A025-EB893987A295</string>
     <key>PayloadType</key>
     <string>Configuration</string>
     <key>PayloadOrganization</key>
     <string>Microsoft</string>
     <key>PayloadIdentifier</key>
     <string>C4E6A782-0C8D-44AB-A025-EB893987A295</string>
     <key>PayloadDisplayName</key>
     <string>Microsoft Defender for Endpoint settings</string>
     <key>PayloadDescription</key>
     <string>Microsoft Defender for Endpoint configuration settings</string>
     <key>PayloadVersion</key>
     <integer>1</integer>
     <key>PayloadEnabled</key>
     <true/>
     <key>PayloadRemovalDisallowed</key>
     <true/>
     <key>PayloadScope</key>
     <string>System</string>
     <key>PayloadContent</key>
     <array>
       <dict>
           <key>PayloadUUID</key>
           <string>99DBC2BC-3B3A-46A2-A413-C8F9BB9A7295</string>
           <key>PayloadType</key>
           <string>com.microsoft.wdav</string>
           <key>PayloadOrganization</key>
           <string>Microsoft</string>
           <key>PayloadIdentifier</key>
           <string>99DBC2BC-3B3A-46A2-A413-C8F9BB9A7295</string>
           <key>PayloadDisplayName</key>
           <string>Microsoft Defender for Endpoint configuration settings</string>
           <key>PayloadDescription</key>
           <string/>
           <key>PayloadVersion</key>
           <integer>1</integer>
           <key>PayloadEnabled</key>
           <true/>
    <key>features</key>
    <dict>
        <key>scheduledScan</key>
        <string>enabled</string>
    </dict>
<key>scheduledScan</key>
<dict>
    <key>ignoreExclusions</key>
    <true/>
    <key>lowPriorityScheduledScan</key>
    <true/>
    <key>dailyConfiguration</key>
    <dict>
        <key>timeOfDay</key>
        <integer>885</integer>
        <key>interval</key>
        <integer>1</integer>
    </dict>
    <key>weeklyConfiguration</key>
    <dict>
        <key>dayOfWeek</key>
        <integer>4</integer>
        <key>timeOfDay</key>
        <integer>880</integer>
        <key>scanType</key>
        <string>full</string>
        </dict>
        </dict>
    </dict>
</array>
</dict>
</plist>
```

Save the file as `com.microsoft.wdav.xml`.

#### For Jamf Pro and compatible MDM solutions

The following property list configures interval-based, daily, and weekly scans for Jamf Pro and other MDM solutions that accept property lists. Save the content as `com.microsoft.wdav.plist`.

```XML
<?xml version="1.0" encoding="UTF-8"?><!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
    <plist version="1.0">
    <dict>
        <key>features</key>
        <dict>
            <key>scheduledScan</key>
            <string>enabled</string>
        </dict>
    <key>scheduledScan</key>
    <dict>
        <key>ignoreExclusions</key>
        <true/>
        <key>lowPriorityScheduledScan</key>
        <true/>
        <key>dailyConfiguration</key>
        <dict>
            <key>timeOfDay</key>
            <integer>885</integer>
            <key>interval</key>
            <integer>1</integer>
        </dict>
        <key>weeklyConfiguration</key>
        <dict>
            <key>dayOfWeek</key>
            <integer>4</integer>
            <key>timeOfDay</key>
            <integer>880</integer>
            <key>scanType</key>
            <string>full</string>
            </dict>
            </dict>
        </dict>
    </plist>
```

Save the file as `com.microsoft.wdav.plist`.

### Deploy the configuration profile

#### Deploy with Microsoft Intune

> Microsoft Intune is the recommended tool for configuring and distributing Defender for Endpoint features to devices. However, Intune is a separate product that isn't part of Defender for Endpoint, and it isn't included in all subscriptions. To use Intune, you need a subscription that includes it, or you can buy it separately as a standalone subscription or add-on. If you don't have Intune, you can use any of the other methods in this article. For more information, see [Microsoft Intune licensing](https://learn.microsoft.com/en-us/intune/intune-service/fundamentals/licenses).

To create and deploy the custom configuration profile in Intune, see [Set policies in Microsoft Intune](https://learn.microsoft.com/en-us/defender-endpoint/mac-install-with-intune#9b-set-policies-using-microsoft-intune). Use `com.microsoft.wdav` as the configuration profile name, select **Device channel**, and upload the `.xml` file.

#### Deploy with Jamf Pro

> Jamf Pro is a separate third-party product that isn't part of Defender for Endpoint and isn't included with Defender for Endpoint subscriptions. To use Jamf Pro, your organization needs a separate Jamf Pro subscription. For product and subscription information, see [Jamf Pro](https://www.jamf.com/products/jamf-pro/). If your organization doesn't use Jamf Pro, use another configuration method in this article, if available.

For the maintained Defender for Endpoint workflow, see [Deploy Microsoft Defender for Endpoint on macOS with Jamf Pro](https://learn.microsoft.com/en-us/defender-endpoint/mac-jamfpro-policies).

Follow the Jamf instructions to [deploy a custom computer configuration profile](https://learn.jamf.com/r/technical-articles/Deploying_Custom_Computer_Configuration_Profiles_Using_the_Application_and_Custom_Settings_Payload). Use either property list from [Example 1](#example-1-schedule-a-daily-quick-scan-and-weekly-full-scan-using-a-plist) or [Example 2](#example-2-schedule-an-hourly-quick-scan-a-daily-quick-scan-and-weekly-full-scan-using-a-plist), and set **Preference Domain** to `com.microsoft.wdav`.

For an MDM solution that supports property-list payloads, follow the provider's instructions and the profile deployment guidance in [Deploy Microsoft Defender for Endpoint on macOS with another MDM solution](https://learn.microsoft.com/en-us/defender-endpoint/mac-install-with-other-mdm).

After Jamf Pro deploys the profile, verify the scheduled scan configuration by running the following command:

```bash
mdatp health --details scheduled_scan
```

In the results, verify that the scheduled scan reports `managed`.

## Configure scheduled scans with the mdatp CLI

Use the Microsoft Defender for Endpoint command-line tool \(`mdatp`\) to configure scheduled scans locally from Terminal. Command-line configuration is most useful for testing or individual devices. Use an MDM profile for managed deployments.

Enable the scheduled scan feature:

```bash
sudo mdatp config scheduled-scan settings feature --value enabled
```

Configure interval-based quick scans:

```bash
sudo mdatp config scheduled-scan quick-scan hourly-interval --value <arg>
```

![Screenshot of mdatp hourly interval command help showing values from 0 through 24 hours.](https://learn.microsoft.com/en-us/defender-endpoint/media/schedule-scans-mac/schedule-scan-pic2.png)

Configure a daily quick scan:

```bash
sudo mdatp config scheduled-scan quick-scan time-of-day --value <arg>
```

![Screenshot of mdatp daily scan command help showing minutes after midnight from 0 through 1440.](https://learn.microsoft.com/en-us/defender-endpoint/media/schedule-scans-mac/schedule-scan-pic1.png)

Configure a weekly scan:

```bash
sudo mdatp config scheduled-scan weekly-scan --day-of-week <arg> --time-of-day <arg> --scan-type <arg>
```

![Screenshot of mdatp weekly scan command help showing day, time, and scan type options.](https://learn.microsoft.com/en-us/defender-endpoint/media/schedule-scans-mac/schedule-scan-pic3.png)

You can also configure security intelligence updates and low-priority execution:

- To check for security intelligence updates before scheduled scans:

  ```bash
  sudo mdatp config scheduled-scan settings check-for-definitions --value true
  ```

- To use low priority threads for scheduled scanning:

  ```bash
  sudo mdatp config scheduled-scan settings low-priority --value true
  ```

### Verify that scheduled scans ran

To list completed scheduled scans and their results, run `mdatp scan list`:

![Screenshot of the mdatp scan list command entered in Terminal.](https://learn.microsoft.com/en-us/defender-endpoint/media/schedule-scans-mac/schedule-scan-pic5.png)

![Screenshot of a completed quick scan showing a succeeded state, duration, files scanned, and threats detected.](https://learn.microsoft.com/en-us/defender-endpoint/media/schedule-scans-mac/schedule-scan-pic4.png)

Important

If the device is asleep at the scheduled time, the scan runs after the device resumes. If the device is turned off, the scan runs at the next scheduled time.
