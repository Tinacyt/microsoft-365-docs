---
title: Enable SIEM integration in Microsoft Defender for Endpoint
description: Enable SIEM integration to receive detections in your security information and event management (SIEM) solution.
keywords: enable siem connector, siem, connector, security information and events
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: mde
---

# Enable SIEM integration in Microsoft Defender for Endpoint

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Applies to:**
- [Microsoft Defender for Endpoint](https://go.microsoft.com/fwlink/?linkid=2154037)


>Want to experience Microsoft Defender for Endpoint? [Sign up for a free trial.](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-enablesiem-abovefoldlink) 

Enable security information and event management (SIEM) integration so you can pull detections from Microsoft Defender Security Center. Pull detections using your SIEM solution or by connecting directly to the detections REST API.

>[!NOTE]
>- [Microsoft Defender for Endpoint Alert](alerts.md) is composed from one or more detections.
>- [Microsoft Defender for Endpoint Detection](api-portal-mapping.md) is composed from the suspicious event occurred on the Device and its related Alert details.
>- The Microsoft Defender for Endpoint Alert API is the latest API for alert consumption and contain a detailed list of related evidence for each alert. For more information, see [Alert methods and properties](alerts.md) and [List alerts](get-alerts.md).

## Prerequisites

- The user who activates the setting must have permissions to create an app in Azure Active Directory (AAD). This is someone with the following roles: 

  - Security Administrator and either Global Administrator
  - Cloud Application Administrator
  - Application Administrator
  - Owner of the service principal

- During the initial activation, a pop-up screen is displayed for credentials to be entered. Make sure that you allow pop-ups for this site.

## Enabling SIEM integration 
1. In the navigation pane, select **Settings** > **SIEM**.

    ![Image of SIEM integration from Settings menu1](images/enable_siem.png)

    >[!TIP]
    >If you encounter an error when trying to enable the SIEM connector application, check the pop-up blocker settings of your browser. It might be blocking the new window being opened when you enable the capability. 

2. Select **Enable SIEM integration**. This activates the **SIEM connector access details** section with pre-populated values and an application is created under your Azure Active Directory (Azure AD) tenant.

    > [!WARNING]
    >The client secret is only displayed once. Make sure you keep a copy of it in a safe place.<br>
     

    ![Image of SIEM integration from Settings menu2](images/siem_details.png)

3. Choose the SIEM type you use in your organization.

   > [!NOTE]
   > If you select HP ArcSight, you'll need to save these two configuration files:<br>
   > - WDATP-connector.jsonparser.properties
   > - WDATP-connector.properties <br>

   If you want to connect directly to the detections REST API through programmatic access, choose **Generic API**.

4. Copy the individual values or select **Save details to file** to download a file that contains all the values.

5. Select **Generate tokens** to get an access and refresh token.
  
   > [!NOTE]
   > You'll need to generate a new Refresh token every 90 days. 

6. Follow the instructions for [creating an Azure AD app registration for Microsoft Defender for Endpoint](https://docs.microsoft.com/microsoft-365/security/defender-endpoint/exposed-apis-create-app-webapp) and assign the correct permissions to it to read alerts.

You can now proceed with configuring your SIEM solution or connecting to the detections REST API through programmatic access. You'll need to use the tokens when configuring your SIEM solution to allow it to receive detections from Microsoft Defender Security Center.

## Integrate Microsoft Defender for Endpoint with IBM QRadar 
You can configure IBM QRadar to collect detections from Microsoft Defender for Endpoint. For more information, see [IBM Knowledge Center](https://www.ibm.com/support/knowledgecenter/SS42VS_DSM/c_dsm_guide_MS_Win_Defender_ATP_overview.html?cp=SS42VS_7.3.1).

## See also
- [Configure HP ArcSight to pull Microsoft Defender for Endpoint detections](configure-arcsight.md)
- [Microsoft Defender for Endpoint Detection fields](api-portal-mapping.md)
- [Pull Microsoft Defender for Endpoint detections using REST API](pull-alerts-using-rest-api.md)
- [Troubleshoot SIEM tool integration issues](troubleshoot-siem.md)