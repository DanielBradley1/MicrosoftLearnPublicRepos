<!-- Source: https://learn.microsoft.com/en-us/intune/device-security/security-baselines/ref-openclaw-settings -->
<!-- Sitemap-Last-Modified: 2026-06-02 -->

# Local AI Agent Baseline - OpenClaw security baseline settings reference for Microsoft Intune

This article is a reference for the settings that are available in the Local AI Agent Baseline - OpenClaw security baseline for Microsoft Intune.

This baseline limits the use of unauthorized local AI agents such as OpenClaw by configuring device settings that disrupt commonly used execution paths. Included firewall rules restrict outbound network communication from common local agent runtime environments like Node.js.

Important

These settings might not fully block all agent execution paths. This baseline includes controls that restrict runtime environments \(for example, Windows Subsystem for Linux and Node.js\) which can be leveraged by local agents. This baseline might also block other processes in addition to OpenClaw. Review and test each setting before deployment, and disable settings that have an unacceptable impact on legitimate workloads.

Tip

To identify devices that have local AI agents installed before deploying this baseline, use the [properties catalog](https://learn.microsoft.com/en-us/intune/device-configuration/collect-device-properties) to collect **Local AI Agent** inventory data.

## About this reference article

Each security baseline is a group of preconfigured Windows settings that help you apply and enforce granular security settings that the relevant security teams recommend. You can also customize each baseline you deploy to enforce only those settings and values you require. When you create a security baseline profile in Intune, you're creating a template that consists of multiple device configuration settings.

This article displays:

- A list of each setting with its configuration as found in the default instance of that baseline version.
- When available, a link to the underlying configuration service provider \(CSP\) documentation or other related content from the relevant product group that provides context and possibly additional details for a settings use.

When a new version of a baseline becomes available, it replaces the previous version. Profile instances that were created before the availability of a new version:

- Become read-only. You can continue to use those profiles but can't edit them to change their configuration.
- Can be updated to the current version. After you update a profile to the current baseline version, you can edit the profile to modify settings.

To learn more about using security baselines, see:

- [Use security baselines](https://learn.microsoft.com/en-us/intune/device-security/security-baselines/overview)
- [Change the baseline version for a profile](https://learn.microsoft.com/en-us/intune/device-security/security-baselines/configure-baselines#update-a-baseline-profile-to-the-latest-version)
- [Manage security baselines](https://learn.microsoft.com/en-us/intune/device-security/security-baselines/configure-baselines)

## Local AI Agent Baseline - OpenClaw \(Preview\), Version 1

### Windows Subsystem For Linux

- **Allow WSL1**  
  Baseline default: *Enabled*  
  [Learn more](https://learn.microsoft.com/en-us/windows/wsl/compare-versions)
- **Allow the Windows Subsystem For Linux**  
  Baseline default: *Enabled*  
  [Learn more](https://learn.microsoft.com/en-us/windows/wsl/about)

### Firewall

- **Firewall Rule Name**  
  Baseline default: *Configured*  
  [Learn more](https://learn.microsoft.com/en-us/windows/client-management/mdm/firewall-csp#mdmstorefirewallrulesfirewallrulename)

  This baseline includes two preconfigured firewall rules. Both rules block outbound TCP connections from Node.js executables to disrupt common execution paths used by OpenClaw.

  #### Rule: block nodejs in LOCALAPPDATA folder


  | Property | Default value |
  | --- | --- |
  | [Enabled](https://learn.microsoft.com/en-us/windows/client-management/mdm/firewall-csp#mdmstorefirewallrulesfirewallrulenameenabled) | *Enabled* |
  | [Name](https://learn.microsoft.com/en-us/windows/client-management/mdm/firewall-csp#mdmstorefirewallrulesfirewallrulenamename) | block nodejs in LOCALAPPDATA folder |
  | [Interface Types](https://learn.microsoft.com/en-us/windows/client-management/mdm/firewall-csp#mdmstorefirewallrulesfirewallrulenameinterfacetypes) | *All* |
  | [File Path](https://learn.microsoft.com/en-us/windows/client-management/mdm/firewall-csp#mdmstorefirewallrulesfirewallrulenameappfilepath) | `%LOCALAPPDATA%\\Programs\\node\\node.exe` |
  | [Network Types](https://learn.microsoft.com/en-us/windows/client-management/mdm/firewall-csp#mdmstorefirewallrulesfirewallrulenameprofiles) | *FW\_PROFILE\_TYPE\_ALL* |
  | [Direction](https://learn.microsoft.com/en-us/windows/client-management/mdm/firewall-csp#mdmstorefirewallrulesfirewallrulenamedirection) | *The rule applies to outbound traffic* |
  | [Action](https://learn.microsoft.com/en-us/windows/client-management/mdm/firewall-csp#mdmstorefirewallrulesfirewallrulenameactiontype) | *Block* |
  | [Protocol](https://learn.microsoft.com/en-us/windows/client-management/mdm/firewall-csp#mdmstorefirewallrulesfirewallrulenameprotocol) | *Configured* - 6 \(TCP\) |


  #### Rule: block nodejs in ProgramFiles folder


  | Property | Default value |
  | --- | --- |
  | [Enabled](https://learn.microsoft.com/en-us/windows/client-management/mdm/firewall-csp#mdmstorefirewallrulesfirewallrulenameenabled) | *Enabled* |
  | [Name](https://learn.microsoft.com/en-us/windows/client-management/mdm/firewall-csp#mdmstorefirewallrulesfirewallrulenamename) | block nodejs in ProgramFiles folder |
  | [Interface Types](https://learn.microsoft.com/en-us/windows/client-management/mdm/firewall-csp#mdmstorefirewallrulesfirewallrulenameinterfacetypes) | *All* |
  | [File Path](https://learn.microsoft.com/en-us/windows/client-management/mdm/firewall-csp#mdmstorefirewallrulesfirewallrulenameappfilepath) | `%ProgramFiles%\\nodejs\\node.exe` |
  | [Network Types](https://learn.microsoft.com/en-us/windows/client-management/mdm/firewall-csp#mdmstorefirewallrulesfirewallrulenameprofiles) | *FW\_PROFILE\_TYPE\_ALL* |
  | [Direction](https://learn.microsoft.com/en-us/windows/client-management/mdm/firewall-csp#mdmstorefirewallrulesfirewallrulenamedirection) | *The rule applies to outbound traffic* |
  | [Action](https://learn.microsoft.com/en-us/windows/client-management/mdm/firewall-csp#mdmstorefirewallrulesfirewallrulenameactiontype) | *Block* |
  | [Protocol](https://learn.microsoft.com/en-us/windows/client-management/mdm/firewall-csp#mdmstorefirewallrulesfirewallrulenameprotocol) | *Configured* - 6 \(TCP\) |


  For details about firewall rule properties, see [Firewall CSP - FirewallRules](https://learn.microsoft.com/en-us/windows/client-management/mdm/firewall-csp#mdmstorefirewallrules).
