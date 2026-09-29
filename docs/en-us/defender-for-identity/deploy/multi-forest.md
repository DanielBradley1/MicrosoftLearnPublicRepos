<!-- Source: https://learn.microsoft.com/en-us/defender-for-identity/deploy/multi-forest -->
<!-- Sitemap-Last-Modified: 2024-11-27 -->

# Microsoft Defender for Identity multi-forest considerations

Microsoft Defender for Identity supports organizations with multiple Active Directory forests, giving you the ability to easily monitor activity and profile users across forests.

Enterprise organizations typically have several Active Directory forests - often used for different purposes, including legacy infrastructure from corporate mergers and acquisitions, geographical distribution, and security boundaries \(red forests\).

Securing your multiple Active Directory forests with Defender for Identity provides the following advantages:

- **View and investigate** activities performed by users across multiple forests from a single location
- **Gain improved detection** and reduce false positives with advanced Active Directory integration and account resolution
- **Gain greater control and easier deployment**, with an improved set of health issues and reporting for cross-org coverage when your domain controllers are all monitored from a single Defender for Identity server

Note

Each Defender for Identity sensor can only report to a single Defender for Identity workspace.

## Detection activity across multiple forests

To detect cross-forest activities, Defender for Identity sensors query domain controllers in remote forests to create profiles for all entities involved, including users and computers from remote forests.

- Defender for Identity sensors can be installed on domain controllers in all forests, even forests with no trust.
- [Add additional credentials](https://learn.microsoft.com/en-us/defender-for-identity/deploy/create-directory-service-account-gmsa#configure-a-directory-service-account-in-microsoft-defender-portal) on the **Directory services accounts** page to support any untrusted forests in your environment.

  - Only one credential is required to support all forests with a two-way trust.
  - Additional credentials are required for each forest with non-Kerberos trust or no trust.
  - There's a default limit of 30 credentials per Defender for Identity workspace. [Contact support](https://learn.microsoft.com/en-us/defender-for-identity/support) if you need to add more than 30 credentials.

For more information, see [Microsoft Defender for Identity Directory Service account recommendations](https://learn.microsoft.com/en-us/defender-for-identity/deploy/directory-service-accounts).

## Network traffic impact for multi-forest support

When Defender for Identity maps your forests, it uses the following process:

1. After the Defender for Identity sensor starts running, the sensor queries the remote Active Directory forests and retrieves a list of users and machine data for profile creation.
2. Every 5 minutes, each Defender for Identity sensor queries one domain controller from each domain, from each forest, to map all the forests in the network.

   The Defender for Identity sensors map the forests using the `trustedDomain` Active Directory object, by signing in and checking the trust type.

You may see ad-hoc traffic when the Defender for Identity sensor detects cross forest activity. When this occurs, the Defender for Identity sensors will send an LDAP query to the relevant domain controllers to retrieve entity information.

## Related content

- [Deploy Microsoft Defender for Identity with Microsoft Defender](https://learn.microsoft.com/en-us/defender-for-identity/deploy/deploy-defender-identity)
- [Microsoft Defender for Identity prerequisites](https://learn.microsoft.com/en-us/defender-for-identity/deploy/prerequisites-sensor-version-2)
- [Directory Service Accounts for Microsoft Defender for Identity](https://learn.microsoft.com/en-us/defender-for-identity/deploy/directory-service-accounts)
