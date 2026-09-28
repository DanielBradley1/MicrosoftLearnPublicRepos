<!-- Source: https://learn.microsoft.com/en-us/entra/identity/authentication/kerberos-faq -->
<!-- Sitemap-Last-Modified: 2026-08-24 -->

# Microsoft Entra Kerberos FAQ

This article addresses frequently asked questions about how Microsoft Entra Kerberos works.

## What is Cloud Kerberos Trust?

A deployment model that lets Windows Hello for Business use Entra ID as the trust anchor for Kerberos, removing the need for Active Directory Federated Server \(ADFS\) or issuing user certs. Devices get a Cloud TGT from Entra ID and \(when needed\) exchange a partial TGT with on‑prem DCs for on‑prem access.

## What is the difference between a Cloud ticket granting ticket \(TGT\) and a partial \(referral\) TGT?

Cloud TGT: Issued by Entra ID for the KERBEROS.MICROSOFTONLINE.COM realm; used to request service tickets for cloud-integrated resources \(e.g., Azure Files, Azure SQL\).  
Partial TGT \(referral\): Minimal ticket from Entra ID that the client exchanges with an on‑prem DC to obtain a full AD TGT for on‑prem resources.

## Which devices are supported for Cloud Kerberos Trust?

Windows 10, version 2004 and later, and Windows 11 devices that are Azure AD joined or hybrid Azure AD joined.

## Is macOS supported?

Yes, via Platform single sign-on with a Kerberos single sign-on profile. macOS can obtain tgt\_cloud \(Entra\) and tgt\_ad \(on‑prem\) tickets when configured with the Kerberos extension.

## What policies must I enable on Windows clients?

Turn on Windows Hello for Business and enable Use cloud trust for on‑premises authentication. This is typically deployed via Intune Settings Catalog or Group Policy Object.

## Which user sign-in methods are supported for Cloud Kerberos Trust?

Key-based sign-in methods only: Windows Hello for Business \(PIN or FIDO2\) or passwordless phone sign-in. Password sign-in isn't supported.

## How do clients retrieve Cloud TGTs at logon?

Configure the device policy CloudKerberosTicketRetrievalEnabled = 1 \(Microsoft Intune Configuration Service Providers or Group Policy Object\). Without it, clients won’t fetch Cloud TGTs automatically.

## How do I check if the device is properly joined and has single sign-on state?

Run `dsregcmd /status` and confirm AzureAdJoined = YES \(or Hybrid\), AzureAdPrt = YES, and CloudTgt = YES.

## How do I verify service tickets for a resource?

Use `klist get cifs/<storage>.file.core.windows.net` \(Azure Files example\) and then klist to view retrieved tickets.

## Why does `klist cloud\_debug` show Cloud Kerberos enabled by policy: 0?

The client policy isn't applied. Set CloudKerberosTicketRetrievalEnabled = 1 via Intune or Group Policy Object and reboot to apply.

## Why is Cloud TGT missing even after enabling policy?

Ensure the user signed in with a key-based method \(WHfB/FIDO2\) and the device is Entra or hybrid joined. If hybrid access is needed, verify the Trusted Domain Object exists and DC connectivity.

## Why is Partial TGT \(referral\) missing in hybrid scenarios?

Validate that the AzureADKerberos object \(trusted domain object\) is created and healthy; confirm line-of-sight to DCs during the first interactive sign-in.

## How can I inspect Entra Kerberos traffic for deep diagnostics?

Use the Kerberos.NET Fiddler extension to decrypt Key Distribution Center proxy HTTPS traffic to Entra ID and investigate Authentication Server/Ticket Granting Service flows and error codes.

## Can I enforce Conditional Access and MFA for legacy apps via Entra Kerberos?

Yes, authentication goes through Entra ID first, so you can apply Conditional Access, then rely on Kerberos tickets for app access.

## Can Cloud Kerberos Trust coexist with WHfB certificate trust?

No. If certificate trust policies are present, they take precedence over cloud trust. Choose one trust model per device

## Do I need an AzureADKerberos computer object in AD for cloud-only identities?

No, AzureADKerberos computer object in AD is only required for hybrid scenarios.

## How does Entra Kerberos handle password changes?

For key-based sign-ins, password changes don't impact Kerberos tickets. The user continues to authenticate with WHfB/FIDO2 without interruption.

## How do I find cloud security identifier \(SID\) for a cloud only user?

```msgraph
GET https://graph.microsoft.com/v1.0/users/{userid}?$select=securityIdentifier
ConsistencyLevel: eventual
```

## How do I find on-premises SID for a Hybrid user?

```msgraph
GET https://graph.microsoft.com/v1.0/users/{userid}?$select=onPremisesSecurityIdentifier
ConsistencyLevel: eventual
```

## How do I find cloud group SIDs for a cloud only user?

```msgraph
GET https://graph.microsoft.com/v1.0/groups?$filter=securityEnabled eq true&$select=id,displayName,securityIdentifier
ConsistencyLevel: eventual
```

## How do I find on-premises group SIDs for a Hybrid user?

```msgraph
GET https://graph.microsoft.com/v1.0/groups?$filter=securityEnabled eq true&$select=id,displayName,onPremisesSecurityIdentifier
ConsistencyLevel: eventual
```

## Related content

If your question isn't answered here, see the following related articles:

- [Overview of Microsoft Entra Kerberos](https://learn.microsoft.com/en-us/entra/identity/authentication/kerberos)
