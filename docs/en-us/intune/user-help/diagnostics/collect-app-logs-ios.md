<!-- Source: https://learn.microsoft.com/en-us/intune/user-help/diagnostics/collect-app-logs-ios -->
<!-- Sitemap-Last-Modified: 2026-04-08 -->

# Retrieve iOS app logs from device

Whenever you experience a problem in Company Portal, the details of that problem are recorded and stored on your device in a *diagnostic log*. This article describes how to upload those logs from your device to your computer. This process is useful for when you need to troubleshoot, because you can save the logs in a file and email it to your IT support person.

## Retrieve logs via Console app

To retrieve logs via the native Console app, you need your iOS device, a Mac running macOS 10.12 or later, and a cable to connect both devices.

1. Connect your iOS device to your Mac with the cable.
2. On your Mac, press **command + Space** and search for Console. Open Console.
3. On your iOS device, you'll be prompted to trust the computer. Select **Trust**.
4. In Console, select your iOS device from the **Devices** list > **Start**. Console begins to gather your logs.
5. From the Console menu, select **Action** > **Include Info Messages** and **Include Debug Messages**.
6. Select **Clear** and remove any search queries you may have in Console.
7. Open Company Portal on your iOS device and try to reproduce the problem by repeating the steps or actions you took leading up to the problem.
8. From the Console menu, select **Edit** > **Select All**, and then select **Edit** > **Copy**.
9. Paste the log contents in TextEdit.
10. From the TextEdit menu, select **Format** > **Make Plain Text**.
11. Save the file as a .log file. Example: Contosologs.log

## Next steps

After you save your file, you can send it to your IT support person as an email attachment. For contact information, check for helpdesk information on the [Company Portal website](https://go.microsoft.com/fwlink/?linkid=2010980) or app.
