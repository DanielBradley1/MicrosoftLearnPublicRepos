<!-- Source: https://learn.microsoft.com/en-us/defender-endpoint/linux-updates -->
<!-- Sitemap-Last-Modified: 2026-01-14 -->

# Deploy updates for Microsoft Defender for Endpoint on Linux

Microsoft regularly publishes software updates to improve performance, security, and to deliver new features.

Warning

Each version of Defender for Endpoint on Linux is set to expire automatically after 9 months. While expired versions continue to receive security intelligence updates, install the latest version to get all available fixes and enhancements. To check the expiration date, run the following command:

```bash
mdatp health --field product_expiration
```

Expired clients report a health issue and warning message when you run the following command:

```bash
mdatp health
```

Indicators of an expired client include the message, "**ATTENTION: No license found. Contact your administrator for help**." with the following attributes:

```bash
ATTENTION: No license found. Contact your administrator for help.
healthy                                     : false
health_issues                               : ["missing license"]
licensed                                    : false
```

Defender for Endpoint capabilities that are generally available are equivalent, regardless of which update channel is used for deployment \(Beta \(Insider\), Preview \(External\), Current \(Production\)\).

To update Defender for Endpoint on Linux manually, run one of the following commands:

## RHEL and variants \(CentOS and Oracle Linux\)

```bash
sudo yum update mdatp
```

## SLES and variants

```bash
sudo zypper update mdatp
```

## Ubuntu and Debian systems

```bash
sudo apt-get install --only-upgrade mdatp
```

Important

When Defender for Cloud is provisioning the Microsoft Defender for Endpoint agent to Linux servers, it keeps the client updated automatically.

To schedule an update of Microsoft Defender for Endpoint on Linux, see [Schedule an update for Microsoft Defender for Endpoint on Linux](https://learn.microsoft.com/en-us/defender-endpoint/linux-update-mde-linux).
