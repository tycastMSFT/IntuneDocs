---
# required metadata

title: Get an Apple DEP certificate for IntunetitleSuffix: "Intune Azure preview"
description: "Intune Azure preview: Instructions for configuring and uploading an MDM push certificate, a prerequisite for managing Apple devices in Intune. "
keywords:
author: staciebarker
ms.author: stabar
manager: angrobe
ms.date: 02/03/17
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 7e5c79c5-2883-4841-9be6-74cba16ee447

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: dagerrit
ms.suite: ems
#ms.tgt_pltfrm:
ms.custom: intune-azure
---

# Get an Apple DEP certificate

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

Before you can enroll corporate-owned iOS devices with Apple's Device Enrollment Program (DEP), you need a DEP token from Apple. This token lets Intune sync information about DEP-participating devices that your corporation owns. It also permits Intune to perform enrollment profile uploads to Apple and to assign devices to those profiles.

To manage corporate-owned iOS devices with DEP, your organization must join Apple DEP and get devices through that program. Details of that process are available at: https://deploy.apple.com. Advantages of the program include hands-free setup of devices without using a USB cable to connect each device to a computer.

> [!NOTE]
> This note only applies to Intune customers who have been migrated from the Intune administration console to the Azure portal. If you deleted an Apple DEP token from the Intune administration console during the migration period, you may find that the DEP token has been restored to your Intune account. If this happens, just delete the DEP token from the Azure portal.

## Steps to get the Apple DEP certificate
In the Azure portal, choose **More Services** > **Monitoring + Management** > **Intune**. On the Intune blade, choose **Enroll devices** > **Apple DEP Token**, and then follow the numbered steps in the Azure portal, which are shown below.

**Step 1. Download an Intune public key certificate required to create an Apple DEP token.**<br>
Select **Download your public key** to download and save the encryption key (.pem) file locally. The .pem file is used to request a trust-relationship certificate from the Apple Device Enrollment Program portal.

**Step 2. Download an Apple DEP token from the appropriate Apple website.**<br>
Select [Create a DEP token via Apple Deployment Programs](https://deploy.apple.com) (https://deploy.apple.com), and sign in with your company Apple ID. You must use this Apple ID to renew your DEP token.

   a.  In the [Device Enrollment Program Portal](https://deploy.apple.com), go to **Device Enrollment Program** &gt; **Manage Servers**, and then choose **Add MDM Server**.

   b.  Enter the **MDM Server Name**, and then choose **Next**. The server name is for your reference to identify the mobile device management (MDM) server. It is not the name or URL of the Microsoft Intune server.

   c.  The **Add &lt;ServerName&gt;** dialog box opens. Choose **Choose File…** to upload the .pem file, and then choose **Next**.

   d.  The **Add &lt;ServerName&gt;** dialog box shows a **Your Server Token** link. Download the server token (.p7m) file to your computer, and then choose **Done**.

    This certificate (.p7m) file is used to establish a trust relationship between Intune and Apple’s Device Enrollment Program servers.

**Step 3. Enter the Apple ID used to create your Apple DEP token. This ID can be used to renew your Apple DEP token.**

**Step 4. Browse to your Apple DEP token to upload. Intune will automatically synchronize with your DEP account.**<br>
Go to the certificate (.pem) file, choose **Open**, and then choose **Upload**. With the push certificate, Intune can enroll and manage iOS devices by pushing policy to enrolled mobile devices.
