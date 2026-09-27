<!-- Source: https://learn.microsoft.com/en-us/intune/solutions/education/tutorial-school-deployment/enroll-entra-join -->
<!-- Sitemap-Last-Modified: 2026-04-14 -->

# Automatic Intune enrollment via Microsoft Entra join

If you're setting up a Windows device individually, you can use the out-of-box experience to join it to your school's Microsoft Entra tenant, and automatically enroll it in Intune. With this process, no advance preparation is needed:

1. Follow the on-screen prompts for region selection, keyboard selection, and network connection.
2. Wait for updates. If any updates are available, they are installed at this time.  ![Windows 11 OOBE - updates page](https://learn.microsoft.com/en-us/intune/solutions/education/tutorial-school-deployment/media/enroll-entra-join/win11-oobe-updates.png)
3. When prompted, select **Set up for work or school** and authenticate using your school's Microsoft Entra account.  ![Windows 11 OOBE - authentication page](https://learn.microsoft.com/en-us/intune/solutions/education/tutorial-school-deployment/media/enroll-entra-join/win11-oobe-auth.png)
4. The device joins Microsoft Entra ID and automatically enroll in Intune. All settings defined in Intune are applied to the device.

Important

If you configured enrollment restrictions in Intune blocking personal Windows devices, this process will not complete. You will need to use a different enrollment method, or ensure that the devices are registered in Windows Autopilot.

![Windows 11 login screen](https://learn.microsoft.com/en-us/intune/solutions/education/tutorial-school-deployment/media/shared/win11-login-screen.png)

---

## Next steps

With the devices joined to Microsoft Entra tenant and managed by Intune, you can use Intune to maintain them and report on their status.

[Next: Manage devices >](https://learn.microsoft.com/en-us/intune/solutions/education/tutorial-school-deployment/manage-overview)
