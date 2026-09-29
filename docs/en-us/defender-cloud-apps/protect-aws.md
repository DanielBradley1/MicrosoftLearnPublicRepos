<!-- Source: https://learn.microsoft.com/en-us/defender-cloud-apps/protect-aws -->
<!-- Sitemap-Last-Modified: 2026-08-08 -->

# How Defender for Cloud Apps helps protect your Amazon Web Services \(AWS\) environment

Amazon Web Services \(AWS\) is an IaaS provider that lets your organization host and manage workloads in the cloud. While cloud infrastructure offers many benefits, it can also expose critical assets to threats. These assets include storage instances with sensitive data, compute resources that run key applications, ports, and virtual private networks.

Connect AWS to Defender for Cloud Apps to secure your assets and detect threats. The connector monitors admin and sign-in activity. It notifies you about brute force attacks, misuse of privileged accounts, unusual VM deletions, and publicly exposed storage buckets.

## Main threats

Connecting AWS to Defender for Cloud Apps helps you detect and respond to the following threats:

- Abuse of cloud resources
- Compromised accounts and insider threats
- Data leakage
- Resource misconfiguration and insufficient access control

## Protect your environment with Defender for Cloud Apps

Defender for Cloud Apps protects your AWS environment by helping you:

- [Detect cloud threats, compromised accounts, and malicious insiders](https://learn.microsoft.com/en-us/defender-cloud-apps/best-practices#detect-cloud-threats-compromised-accounts-malicious-insiders-and-ransomware)
- [Limit exposure of shared data and enforce collaboration policies](https://learn.microsoft.com/en-us/defender-cloud-apps/best-practices#limit-exposure-of-shared-data-and-enforce-collaboration-policies)
- [Use the audit trail of activities for forensic investigations](https://learn.microsoft.com/en-us/defender-cloud-apps/best-practices#use-the-audit-trail-of-activities-for-forensic-investigations)

## Control AWS with built-in policies and policy templates

You can use the following built-in policy templates to detect and notify you about potential threats:

Important

File policies retire on January 6, 2027. To maintain file-based data protection for this app, [migrate to Microsoft Purview DLP or auto-labeling policies](https://learn.microsoft.com/en-us/defender-cloud-apps/migrate-file-policies-to-purview).

| Type | Name |
| --- | --- |
| Activity policy template | Admin console sign-in failures  <br>EC2 instance configuration changes  <br>IAM policy changes  <br>Logon from a risky IP address  <br>Network access control list \(ACL\) changes  <br>Network gateway changes  <br>S3 Bucket Activity  <br>Security group configuration changes  <br>Virtual private network changes |
| Built-in anomaly detection policy | [Activity from anonymous IP addresses](https://learn.microsoft.com/en-us/defender-cloud-apps/anomaly-detection-policy#activity-from-anonymous-ip-addresses)  <br>[Activity from infrequent country](https://learn.microsoft.com/en-us/defender-cloud-apps/anomaly-detection-policy#activity-from-infrequent-country)  <br>[Activity from suspicious IP addresses](https://learn.microsoft.com/en-us/defender-cloud-apps/anomaly-detection-policy#activity-from-suspicious-ip-addresses)  <br>[Impossible travel](https://learn.microsoft.com/en-us/defender-cloud-apps/anomaly-detection-policy#impossible-travel)  <br>[Activity performed by terminated user](https://learn.microsoft.com/en-us/defender-cloud-apps/anomaly-detection-policy#activity-performed-by-terminated-user) \(requires Microsoft Entra ID as IdP\)  <br>[Multiple failed login attempts](https://learn.microsoft.com/en-us/defender-cloud-apps/anomaly-detection-policy#multiple-failed-login-attempts)  <br>[Unusual administrative activities](https://learn.microsoft.com/en-us/defender-cloud-apps/anomaly-detection-policy#unusual-activities-by-user) |
| File policy template | S3 bucket is publicly accessible |

For more information about creating policies, see [Create a policy](https://learn.microsoft.com/en-us/defender-cloud-apps/control-cloud-apps-with-policies#create-a-policy).

## Automate governance controls

You can also apply and automate AWS governance actions to fix detected threats:

| Type | Action |
| --- | --- |
| User governance | - Notify user on alert \(via Microsoft Entra ID\)  <br>- Require user to sign in again \(via Microsoft Entra ID\)  <br>- Suspend user \(via Microsoft Entra ID\) |
| Data governance | - Make an S3 bucket private  <br>- Remove a collaborator for an S3 bucket |

For more information about remediating threats from apps, see [Governing connected apps](https://learn.microsoft.com/en-us/defender-cloud-apps/governance-actions).

## Protect AWS in real time

Review our best practices for [blocking and protecting the download of sensitive data to unmanaged or risky devices](https://learn.microsoft.com/en-us/defender-cloud-apps/best-practices#block-and-protect-download-of-sensitive-data-to-unmanaged-or-risky-devices).

## Connect Amazon Web Services to Microsoft Defender for Cloud Apps

Defender for Cloud Apps provides connector APIs that integrate with supported cloud services to ingest activity data. Use these APIs to connect your existing Amazon Web Services \(AWS\) account to Defender for Cloud Apps. For information about how Defender for Cloud Apps protects AWS, see [Protect AWS](https://learn.microsoft.com/en-us/defender-cloud-apps/protect-aws).

You can connect AWS **Security auditing** to Defender for Cloud Apps connections to gain visibility into and control over AWS app use.

### Step 1: Configure Amazon Web Services auditing

To configure AWS auditing for Defender for Cloud Apps, perform the following steps:

1. Sign in to the [Amazon Web Services console](https://aws.amazon.com/console/)
2. Add a new user for Defender for Cloud Apps, and give the user **Programmatic access**.
3. Select **Create policy** and enter a name for your new policy.
4. Select the **JSON** tab and paste the following script:

   ```json
   {
     "Version" : "2012-10-17",
     "Statement" : [{
         "Action" : [
           "cloudtrail:DescribeTrails",
           "cloudtrail:LookupEvents",
           "cloudtrail:GetTrailStatus",
           "cloudwatch:Describe*",
           "cloudwatch:Get*",
           "cloudwatch:List*",
           "iam:List*",
           "iam:Get*",
           "s3:ListAllMyBuckets",
           "s3:PutBucketAcl",
           "s3:GetBucketAcl",
           "s3:GetBucketLocation"
         ],
         "Effect" : "Allow",
         "Resource" : "*"
       }
     ]
    }
   ```

5. Select **Download .csv** to save a copy of the new user's credentials. You'll need these credentials later.

   Note

   After connecting AWS, you'll receive events for seven days prior to connection. If you just enabled CloudTrail, you receive events from the time you enabled CloudTrail.

### Step 2: Connect Amazon Web Services auditing to Defender for Cloud Apps

To connect AWS auditing to Defender for Cloud Apps, complete the following steps:

1. In the Microsoft Defender Portal, select **Settings**. Then choose **Cloud Apps**. Under **Connected apps**, select **App Connectors**.
2. In the **App connectors** page, to provide the AWS connector credentials, do one of the following:

**For a new connector**

1. Select the **+Connect an app**, followed by **Amazon Web Services**.

   [![Screenshot that shows where to find the +Connect an app button in the Microsoft Defender portal.](https://learn.microsoft.com/en-us/defender-cloud-apps/media/connect-aws.png)](https://learn.microsoft.com/en-us/defender-cloud-apps/media/connect-aws.png#lightbox)
2. In the next window, provide a name for the connector, and then select **Next**.

   [![Screenshot that shows how to add the instance name for your new AWS connector.](https://learn.microsoft.com/en-us/defender-cloud-apps/media/connect-aws-name.png)](https://learn.microsoft.com/en-us/defender-cloud-apps/media/connect-aws-name.png#lightbox)
3. On the **Connect Amazon Web Services** page, select **Security auditing**, and then select **Next**.
4. On the **Security auditing page**, paste the **Access key** and **Secret key** from the .csv file into the relevant fields, and select **Next**.

   [![Screenshot that shows the AWS app security auditing page and where to enter the access key and secret key.](https://learn.microsoft.com/en-us/defender-cloud-apps/media/aws-connect-app-audit.png)](https://learn.microsoft.com/en-us/defender-cloud-apps/media/aws-connect-app-audit.png#lightbox)

**For an existing connector**

1. In the list of connectors, on the row in which the AWS connector appears, select **Edit settings**.
2. On the **Instance name** and **Connect Amazon Web Services** pages, select **Next**. On the **Security auditing page**, paste the **Access key** and **Secret key** from the .csv file into the relevant fields, and select **Next**.

   [![Screenshot that shows the AWS app security auditing page and where to enter the access key and secret key.](https://learn.microsoft.com/en-us/defender-cloud-apps/media/aws-connect-app-audit.png)](https://learn.microsoft.com/en-us/defender-cloud-apps/media/aws-connect-app-audit.png#lightbox)
3. In the Microsoft Defender Portal, select **Settings**. Then choose **Cloud Apps**. Under **Connected apps**, select **App Connectors**. Make sure the status of the connected App Connector is **Connected**.

## Next steps

- [Control cloud apps with policies](https://learn.microsoft.com/en-us/defender-cloud-apps/control-cloud-apps-with-policies)
