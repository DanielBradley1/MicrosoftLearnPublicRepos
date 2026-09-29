<!-- Source: https://learn.microsoft.com/en-us/defender-endpoint/configure-mssp-notifications -->
<!-- Sitemap-Last-Modified: 2026-01-15 -->

# Configure alert notifications that are sent to MSSPs

Note

This step can be done by either the MSSP customer or MSSP. MSSPs must be granted the appropriate permissions to configure this on behalf of the MSSP customer.

After access the portal is granted, alert notification rules can be created so that emails are sent to MSSPs when alerts associated with the tenant are created and set conditions are met.

For more information, see [Create rules for alert notifications](https://learn.microsoft.com/en-us/defender-xdr/configure-email-notifications#create-rules-for-alert-notifications).

These check boxes must be checked:

- **Include organization name** - The customer name will be added to email notifications
- **Include tenant-specific portal link** - Alert link URL will have tenant specific parameter \(tid=target\_tenant\_id\) that allows direct access to target tenant portal

## Related topics

- [Grant MSSP access to the portal](https://learn.microsoft.com/en-us/defender-endpoint/grant-mssp-access)
- [Access the MSSP customer portal](https://learn.microsoft.com/en-us/defender-endpoint/access-mssp-portal)
- [Fetch alerts from customer tenant](https://learn.microsoft.com/en-us/defender-endpoint/api/fetch-alerts-mssp)
