<!-- Source: https://learn.microsoft.com/en-us/defender-for-identity/deploy/configure-sensor-settings -->
<!-- Sitemap-Last-Modified: 2026-07-02 -->

# Configure Microsoft Defender for Identity sensor settings

In this article, you'll learn how to correctly configure Microsoft Defender for Identity sensor settings to start seeing data. You'll need to do additional configuration and integration to take advantage of Defender for Identity's full capabilities.

## View and configure sensor settings

After the Defender for Identity sensor is installed, do the following to view and configure Defender for Identity sensor settings:

1. In [Microsoft Defender XDR](https://security.microsoft.com), go to **Settings** > **Identities** > **Sensors**. For example:

![Screenshot that shows the sensor page in the Microsoft Defender portal.](https://learn.microsoft.com/en-us/defender-for-identity/media/download-sensor/sensor-page.png)

The **Sensors** page displays all of your Defender for Identity sensors, listing the following details per sensor:

- Sensor name
- Sensor domain membership
- Sensor version number
- Whether updates should be [delayed \(delayed sensor updates\)](https://learn.microsoft.com/en-us/defender-for-identity/sensor-settings#delayed-update-for-sensor-v2x)
- Sensor service status

- Sensor status
- Sensor health status
- The number of health issues
- When the sensor was created

For more information, see [Sensor details](https://learn.microsoft.com/en-us/defender-for-identity/sensor-settings#sensor-details).

1. Select **Filters** to select the filters you want visible. For example:

   [![Screenshot of the Sensors page filter options for narrowing the sensor list.](https://learn.microsoft.com/en-us/defender-for-identity/media/sensor-filters.png)](https://learn.microsoft.com/en-us/defender-for-identity/media/sensor-filters.png#lightbox)

2. Use the displayed filters to determine which sensors to display. For example:

   [![Screenshot of a filtered list of sensors.](https://learn.microsoft.com/en-us/defender-for-identity/media/filtered-sensor.png)](https://learn.microsoft.com/en-us/defender-for-identity/media/filtered-sensor.png#lightbox)
3. Select a sensor to show a details pane with more information about the sensor and its health status. For example:

   [![Screenshot of a sensor details pane showing health status and configuration.](https://learn.microsoft.com/en-us/defender-for-identity/media/sensor-details.png)](https://learn.microsoft.com/en-us/defender-for-identity/media/sensor-details.png#lightbox)

4. Scroll down and select **Manage sensor** to show a pane where you can configure sensor details. For example:

   [![Screenshot of the Sensors page with the Manage sensor option selected to open sensor configuration settings.](https://learn.microsoft.com/en-us/defender-for-identity/media/manage-sensor.png)](https://learn.microsoft.com/en-us/defender-for-identity/media/manage-sensor.png#lightbox)
5. Configure the following sensor details:
   | Name | Description |
   | --- | --- |
   | **Description** | Optional. Enter a description for the Defender for Identity sensor. |
   | **Domain Controllers \(FQDN\)** | Required for the Defender for Identity [standalone sensors](https://learn.microsoft.com/en-us/defender-for-identity/deploy/prerequisites-standalone) and [sensors installed on AD FS / AD CS servers](https://learn.microsoft.com/en-us/defender-for-identity/deploy/active-directory-federation-services), and can't be modified for the Defender for Identity sensor.  <br>  <br>Enter the complete FQDN of your domain controller and select the plus sign to add it to the list. For example, **DC1.domain1.test.local**.  <br>  <br>For any servers you define in the **Domain Controllers** list:  <br>  <br>- All domain controllers whose traffic is being monitored via port mirroring by the Defender for Identity standalone sensor must be listed in the **Domain Controllers** list. If a domain controller isn't listed in the **Domain Controllers** list, detection of suspicious activities might not function as expected.  <br>  <br>- At least one domain controller in the list should be a global catalog. This enables Defender for Identity to resolve computer and user objects in other domains in the forest. |
   | **Capture Network adapters** | Required.  <br>  <br>- For Defender for Identity sensors, all network adapters that are used for communication with other computers in your organization.  <br>  <br>- For Defender for Identity standalone sensor on a dedicated server, select the network adapters that are configured as the destination mirror port. These network adapters receive the mirrored domain controller traffic. |
6. On the **Sensors** page, select **Export** to export a list of your sensors to a **.csv** file. For example:

   [![Screenshot of the Sensors page with the Export option for downloading the sensor list as a CSV file.](https://learn.microsoft.com/en-us/defender-for-identity/media/export-sensors.png)](https://learn.microsoft.com/en-us/defender-for-identity/media/export-sensors.png#lightbox)

## Validate installations

Use the following procedures to validate your Defender for Identity sensor installation.

Note

If you're installing on an AD FS or AD CS server, you use a different set of validations. For more information, see [Validate successful deployment on AD FS / AD CS servers](https://learn.microsoft.com/en-us/defender-for-identity/deploy/active-directory-federation-services#validate-successful-deployment).

### Validate successful deployment

To validate that the Defender for Identity sensor has been successfully deployed:

1. Check that the **Azure Advanced Threat Protection sensor** service is running on your sensor machine. After you save the Defender for Identity sensor settings, it might take a few seconds for the service to start.
2. If the service doesn't start, review the **Microsoft.Tri.sensor-Errors.log** file, located by default at `%programfiles%\Azure Advanced Threat Protection sensor\<sensor version>\Logs`, where `<sensor version>` is the version you deployed.

### Verify security alert functionality

The following procedure describes how to verify that security alerts are triggered as expected.

When using the examples in this validation procedure, make sure to replace `contosodc.contoso.azure` and `contoso.azure` with the fully qualified domain name \(FQDN\) of your Defender for Identity sensor and your domain name, respectively.

1. On a member-joined device, open a command prompt and enter `nslookup`
2. Enter `server` and the FQDN or IP address of the domain controller where the Defender for Identity sensor is installed. For example: `server contosodc.contoso.azure`
3. Enter `ls -d contoso.azure`
4. Repeat the `server` and `ls -d` commands for each sensor you want to test.
5. Access the device details page for the computer you ran the connectivity test from, such as from the **Devices** page, by searching for device name, or from elsewhere in the Defender portal.
6. On the device details tab, select the **Timeline** tab to view the following activity:

   - **Events**: DNS queries performed to a specified domain name
   - **Action type** MdiDnsQuery

If the domain controller or AD FS / AD CS that you're testing is the first sensor you've deployed, wait at least 15 minutes before verifying any logical activity for that domain controller, allowing the database backend to complete the initial microservice deployments.

### Verify latest available sensor version

The Defender for Identity version is updated frequently. Check for the latest version in the Microsoft Defender **Settings** > **Identities** > **About** page.

## Related content

Now that you've configured the Defender for Identity sensor settings, you can configure additional settings. See the following articles for more information:

- [Set entity tags: sensitive, honeytoken, and Exchange server](https://learn.microsoft.com/en-us/defender-for-identity/entity-tags)
- [Configure detection exclusions](https://learn.microsoft.com/en-us/defender-for-identity/exclusions)
- [Configure notifications: health issues, alerts, and Syslog](https://learn.microsoft.com/en-us/defender-for-identity/notifications)

## Next step

[Configure audit policies for Windows event logs](https://learn.microsoft.com/en-us/defender-for-identity/deploy/configure-windows-event-collection)
