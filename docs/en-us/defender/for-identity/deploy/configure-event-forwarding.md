<!-- Source: https://learn.microsoft.com/en-us/defender-for-identity/deploy/configure-event-forwarding -->
<!-- Sitemap-Last-Modified: 2026-07-02 -->

# Configure Windows event forwarding to your Defender for Identity standalone sensor

This article describes an example of how to configure Windows event forwarding to your Microsoft Defender for Identity standalone sensor. Event forwarding is one method for enhancing your detection abilities with extra Windows events that aren't available from the domain controller network. For more information, see [Configure Windows event auditing](https://learn.microsoft.com/en-us/defender-for-identity/deploy/configure-windows-event-collection).

Important

Defender for Identity standalone sensors don't support the collection of Event Tracing for Windows \(ETW\) log entries that provide the data for multiple detections. For full coverage of your environment, we recommend deploying the Defender for Identity sensor.

## Prerequisites

Before you start:

- Make sure that the domain controller is properly configured to capture the required events. For more information, see [Configure Windows event auditing](https://learn.microsoft.com/en-us/defender-for-identity/deploy/configure-windows-event-collection).
- [Configure port mirroring](https://learn.microsoft.com/en-us/defender-for-identity/deploy/configure-port-mirroring)

## Step 1: Add the network service account to the domain

This procedure describes how to add the Network Service account to the **Event Log Readers** group in the domain. For this scenario, assume that the Defender for Identity standalone sensor is a member of the domain.

1. In Active Directory's Users and Computers, go to the **Built-in** folder and double-click **Event Log Readers**.
2. Select **Members**.
3. If **Network Service** isn't listed, select **Add**, and then enter **Network Service** in the **Enter the object names to select** field.
4. Select **Check Names** and select **OK** twice.

After adding the **Network Service** to the **Event Log Readers** group, reboot the domain controllers for the change to take effect.

For more information, see [Active Directory accounts](https://learn.microsoft.com/en-us/windows-server/identity/ad-ds/manage/understand-default-user-accounts).

## Step 2: Create a policy that sets the Configure target setting

This procedure describes how to create a policy on the domain controllers to set the **Configure target Subscription Manager** setting, which is the Group Policy setting that tells domain controllers where to forward events.

Tip

You can create a group policy for these settings and apply the group policy to each domain controller monitored by the Defender for Identity standalone sensor. The following steps modify the local policy of the domain controller.

1. On each domain controller, run:

   ```cmd
   winrm quickconfig
   ```

2. From a command prompt, enter

   ```cmd
   gpedit.msc
   ```

3. Expand **Computer Configuration > Administrative Templates > Windows Components > Event Forwarding**. For example:

   ![Screenshot of Local Group Policy Editor expanded to Computer Configuration, Administrative Templates, Windows Components, Event Forwarding.](https://learn.microsoft.com/en-us/defender-for-identity/media/wef-1-local-group-policy-editor.png)

4. Double-click **Configure target Subscription Manager** and then:

   1. Select **Enabled**.
   2. Under **Options**, select **Show**.
   3. Under **SubscriptionManagers**, enter the following value and select **OK**:

      **Server=http://`<fqdnMicrosoftDefenderForIdentitySensor>`:5985/wsman/SubscriptionManager/WEC,Refresh=10**

      For example, using **Server=http://atpsensor.contoso.com:5985/wsman/SubscriptionManager/WEC,Refresh=10**:

      ![Screenshot of the Configure target Subscription Manager dialog with Enabled selected and the server URL entered in the SubscriptionManagers field.](https://learn.microsoft.com/en-us/defender-for-identity/media/wef-2-config-target-sub-manager.png)

5. Select **OK**.
6. From an elevated command prompt, enter:

   ```cmd
   gpupdate /force
   ```

## Step 3: Create and select a subscription on your sensor

This procedure describes how to create a subscription for use with Defender for Identity and then select the subscription from your standalone sensor.

1. Open an elevated command prompt and enter

   ```cmd
   wecutil qc
   ```

2. Open **Event Viewer**.
3. Right-click **Subscriptions** and select **Create Subscription**.

   1. Enter a name and description for the subscription.
   2. For **Destination Log**, confirm that **Forwarded Events** is selected. For Defender for Identity to read the events, the destination log must be **Forwarded Events**.
   3. Select **Source computer initiated** > **Select Computers Groups** > **Add Domain Computer**.

      1. Enter the name of the domain controller in the **Enter the object name to select** field.
      2. Select **Check Names** > **OK** > **OK**.
      3. Select **OK**. For example:

         [![Screenshot of the Event Viewer dialog.](https://learn.microsoft.com/en-us/defender-for-identity/media/wef-3-event-viewer.png)](https://learn.microsoft.com/en-us/defender-for-identity/media/wef-3-event-viewer.png#lightbox)

   4. Select **Select Events** > **By log** > **Security**.
   5. In the **Includes/Excludes Event ID** field type the event number and select **OK**. For example, enter **4776**:

      ![Screenshot of the Query filter dialog with the Security log selected and event ID 4776 entered in the Includes/Excludes Event ID field.](https://learn.microsoft.com/en-us/defender-for-identity/media/wef-4-query-filter.png)

   6. Return to the elevated command prompt where you ran `wecutil qc`. Run the following commands, replacing *SubscriptionName* with the name you created for the subscription.

      ```cmd
      wecutil ss "SubscriptionName" /cm:"Custom"
      wecutil ss "SubscriptionName" /HeartbeatInterval:5000
      ```

   7. Return to the **Event Viewer** console. Right-click the created subscription and select **Runtime Status** to see if there are any issues with the status.
   8. After a few minutes, verify that the forwarded events appear in the Forwarded Events log on the Defender for Identity standalone sensor.

For more information, see: [Configure the computers to forward and collect events](https://learn.microsoft.com/en-us/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc748890\(v=ws.11\)).

## Related content

For more information, see:

- [Configure port mirroring](https://learn.microsoft.com/en-us/defender-for-identity/deploy/configure-port-mirroring)
- [Listen for SIEM events on your Defender for Identity standalone sensor](https://learn.microsoft.com/en-us/defender-for-identity/deploy/configure-event-collection)
