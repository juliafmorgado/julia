---
title: "How to Update Veeam Backup for AWS to Version 8"
author: 'Julia Furst Morgado'
date: 2024-07-11T06:46:05.964Z
draft: true
image: https://blog-imgs-23.s3.amazonaws.com/update-vbaws8challenge.png
tags:
categories: 
    - Veeam
slug: /how-to-update-veeam-backup-aws-to-version-8
---

## How and Why to Update Veeam Backup for AWS to Version 8

With the recent launch of Veeam Backup for AWS (VB for AWS) version 8 on July 2nd, it's time to update your setup to take advantage of the latest features and improvements. 

Version 8 introduces several enhancements, including tighter integration with Veeam Backup & Replication (VBR). By connecting VB for AWS with VBR, you can leverage VBR-specific features such as backup copies and central management for your cloud backup appliances. This integration simplifies management and provides additional capabilities that enhance your data protection strategy.

This guide will walk you through the process, ensuring a smooth transition.

**For more details:**
- **Complete list of new features and enhancements:** [What's New in v8](https://www.veeam.com/whats-new-v8)
- **System requirements, known issues, installation, and upgrade:** [Release Notes](https://www.veeam.com/release-notes-v8)
- **User Guide:** [Online Help](https://helpcenter.veeam.com/docs/backup/vba/introduction.html)
- **All user guides, manuals, and other documentation:** [Veeam Help Center](https://www.veeam.com/documentation-guides-datasheets.html)

### Key Points Before You Begin

1. **VBR Integration:** To benefit from the latest features, you need to connect VB for AWS with your existing VBR installation. There is no need for a dedicated VBR instance.
2. **Standalone Version:** The standalone version of VB for AWS is still available and supported. However, to access new features and updates, integration with VBR is required.
3. **Version Compatibility:** While you are required to deploy VBR to upgrade to version 8, version 7 is still supported and can be used if it meets your protection requirements.
4. **License Requirements:** [Veeam B&R Community Edition (CE)](https://www.veeam.com/products/free/backup-recovery.html) supports managing cloud backup appliances, but it is limited to 10 instances. If you use a VUL key for licensing VB for AWS, you can use the same key for VBR.

### What’s New in Version 8

Veeam Backup for AWS delivers AWS-native backup and disaster recovery that’s easy, cost-effective, and secure. Quickly recover from any cloud data loss scenario - whether due to outages, accidental deletion, malware, and more - in minutes. Here are the main features that you will get with the Version 8 of VB for AWS:

- **Amazon Redshift Cluster protection**
- **Amazon FSx protection**
- **Immutability extension improvements:** Save up to 30% on costs compared to the previous version for backups stored in S3 using immutability. Veeam Backup for AWS will now use a default generation period of up to 25 days for immutability, compared to a fixed 10-day period in previous versions.
- **Imageless deployment:** Deploy backup appliances directly from the Veeam Backup & Replication server to reduce complexity and enhance the efficiency of managing your infrastructure. This method ensures a consistent environment, significantly reducing the likelihood of configuration errors and improving the reliability of your deployments.

### Steps to Upgrade to Version 8

1. **Install Veeam Backup & Replication (VBR):**
   - If you haven't already, install VBR. You can download the latest version from the [Veeam website](https://www.veeam.com/backup-replication.html).
   - Follow the installation instructions provided in the Veeam Backup & Replication User Guide.

2. **Connect VB for AWS to VBR:**
   - Open the Veeam Backup & Replication console.
   - Navigate to the “Inventory” section and select “Backup Infrastructure”.
   - Click “Add Server” and choose “AWS”.
   - Follow the prompts to connect your VB for AWS appliance to VBR.

3. **Deploy AWS Plug-in for VBR:**
   - In the Veeam Backup & Replication console, go to “Backup Infrastructure” and select “Managed Servers”.
   - Right-click on your AWS server and select “Install Backup Agent”.
   - Follow the prompts to deploy the AWS plug-in.

4. **Update VB for AWS to Version 8:**
   - Once connected to VBR, the update process will begin automatically.
   - You can monitor the progress in the “Jobs” section of the VBR console.

5. **Verify the Update:**
   - After the update completes, verify that VB for AWS is functioning correctly.
   - Check the “Jobs” and “Backup & Replication” sections in VBR to ensure all your backup jobs are running smoothly.

#### Benefits of the Update

- **Centralized Management:** Manage your cloud backup appliances from a single VBR console.
- **Enhanced Features:** Access new features and improvements introduced in version 8.
- **Future-proof:** Stay updated with the latest developments and security updates from Veeam.

#### Conclusion

Updating Veeam Backup for AWS to version 8 ensures that you are leveraging the latest capabilities and improvements from Veeam. By integrating with Veeam Backup & Replication, you not only gain access to advanced features but also simplify the management of your backup infrastructure. Follow the steps outlined in this guide for a seamless upgrade experience. 

For detailed installation instructions and additional information, refer to the Veeam Backup & Replication User Guide and the Veeam Backup for AWS documentation.


















***

If you liked this article, follow me on [Twitter](https://twitter.com/juliafmorgado) (where I share my tech journey daily), connect with me on [LinkedIn](https://www.linkedin.com/in/juliafmorgado/), check out my [IG](https://www.instagram.com/juliafmorgado/), and make sure to subscribe to my [Youtube](https://www.youtube.com/c/JuliaFMorgado) channel for more amazing content!!
