<!-- Source: https://learn.microsoft.com/en-us/entra/identity/hybrid/connect/how-to-connect-uninstall -->
<!-- Sitemap-Last-Modified: 2025-04-09 -->

# Uninstall Microsoft Entra Connect

This document describes how to correctly uninstall Microsoft Entra Connect.

## Uninstall Microsoft Entra Connect from the server

The first thing you need to do is remove Microsoft Entra Connect from the server that it's running on. Use the following steps:

1. On the server running Microsoft Entra Connect, navigate to **Control Panel**.
2. Select **Uninstall a program** ![Uninstall a program](https://learn.microsoft.com/en-us/entra/identity/hybrid/connect/media/how-to-connect-uninstall/uninstall-1.png)  

3. Select **Microsoft Entra Connect**. ![Select Microsoft Entra Connect](https://learn.microsoft.com/en-us/entra/identity/hybrid/connect/media/how-to-connect-uninstall/uninstall-2.png)  

4. When prompted, select **Yes** to confirm.
5. This confirmation brings up the Microsoft Entra Connect screen. Select **Remove**. ![Remove](https://learn.microsoft.com/en-us/entra/identity/hybrid/connect/media/how-to-connect-uninstall/uninstall-3.png)  

6. Once this action completes, select **Exit**.
7. ![Exit](https://learn.microsoft.com/en-us/entra/identity/hybrid/connect/media/how-to-connect-uninstall/uninstall-4.png)  

8. Back in **Control Panel** select **Refresh** and all of the components should be removed.

## Next steps

- Learn more about [Integrating your on-premises identities with Microsoft Entra ID](https://learn.microsoft.com/en-us/entra/identity/hybrid/whatis-hybrid-identity).
- [Install Microsoft Entra Connect using an existing ADSync database](https://learn.microsoft.com/en-us/entra/identity/hybrid/connect/how-to-connect-install-existing-database)
- [Install Microsoft Entra Connect using SQL delegated administrator permissions](https://learn.microsoft.com/en-us/entra/identity/hybrid/connect/how-to-connect-install-sql-delegation)
