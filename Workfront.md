
# Integration of Adobe Workfront Fusion with AEM Forms Submission

**Last updated:** July 14, 2025

* **Applies to:** Adobe Experience Manager Forms as a Cloud Service
* **Topics:** Workfront Fusion Integration, AEM Forms, Adaptive Forms, Integration
* **Audience:** Admin, Developer, Business User

## Overview

This enhanced documentation provides comprehensive guidance for implementing Adobe Experience Manager Forms integration with Workfront Fusion, combining insights from both the original documentation and video analysis to deliver actionable, step-by-step instructions.

## Prerequisites

Before you begin, ensure you have:

**Last updated:** Mon Jul 14 2025 00:29:37 GMT+0000 (Coordinated Universal Time)
*   **Licenses:** Valid licenses for both Adobe Experience Manager Forms and Adobe Workfront Fusion are required.
*   **AEM User Access:** An AEM user with administrator privileges and access to the Developer Console to retrieve service credentials is necessary.
*   **Workfront Fusion Account:** A Workfront Fusion account with appropriate permissions to create and manage Scenarios.
*   **Technical Account Membership:** The Technical Account used for integration *must* be a member of the `forms-users` group within Workfront Fusion.
*   **Network Connectivity:** Stable network connectivity between the AEM Forms instance, Workfront Fusion, and Adobe's IMS service.
*   **SSL Certificates:** Valid SSL certificates for secure communication between AEM Forms and Workfront Fusion.
*   **Adobe Developer Console Access:** Access to the Adobe Developer Console ([https://developer.com/console](https://developer.com/console)) to retrieve service credentials.
*   **Understanding of JSON:** Familiarity with JSON data formats and webhook configurations.
*   **Adobe Experience League Account:** An Adobe Experience League account ([https://experienceleague.com](https://experienceleague.com)) for accessing documentation and support.
*   **Adobe Support Access:** Access to Adobe Support ([https://helpx.com](https://helpx.com)) for troubleshooting.
*   **Adobe Documentation Access:** Access to Adobe Documentation ([https://docs.com](https://docs.com)) for reference materials.
*   **AEM Forms as a Cloud Service Early Adopter Program:** This feature is currently available under the early adopter program. To request access, email `aem-forms-ea@adobe.com` from your official email address.

## Implementation Steps

```markdown

# Integration of Adobe Workfront Fusion with AEM Forms Submission
**Last updated:** Mon Jul 14 2025 00:29:37 GMT+0000 (Coordinated Universal Time)


This document details how to integrate Adobe Workfront Fusion with AEM Forms to automate form submission processing. This integration allows seamless transfer of form submissions data to Workfront Fusion workflows, enabling automation of tasks like project initiation, task assignment, notifications, and status updates.


## Prerequisites

Before proceeding, ensure 
*   **Licenses:** Valid licenses for both Adobe Experience Manager Forms and Adobe Workfront Fusion are required.
*   **AEM User Access:** An AEM user with administrator privileges and access to the Developer Console to retrieve service credentials is necessary.
*   **Workfront Fusion Account:** A Workfront Fusion account with appropriate permissions to create and manage Scenarios.
*   **Technical Account Membership:** The Technical Account used for integration *must* be a member of the `forms-users` group within Workfront Fusion.
*   **Network Connectivity:** Stable network connectivity between the AEM Forms instance, Workfront Fusion, and Adobe's IMS service.
*   **SSL Certificates:** Valid SSL certificates for secure communication between AEM Forms and Workfront Fusion.
*   **Adobe Developer Console Access:** Access to the Adobe Developer Console ([https://developer.com/console](https://developer.com/console)) to retrieve service credentials.
*   **Understanding of JSON:** Familiarity with JSON data formats and webhook configurations.
*   **Adobe Experience League Account:** An Adobe Experience League account ([https://experienceleague.com](https://experienceleague.com)) for accessing documentation and support.
*   **Adobe Support Access:** Access to Adobe Support ([https://helpx.com](https://helpx.com)) for troubleshooting.
*   **Adobe Documentation Access:** Access to Adobe Documentation ([https://docs.com](https://docs.com)) for reference materials.
*   **AEM Forms as a Cloud Service Early Adopter Program:** This feature is currently available under the early adopter program. To request access, email `aem-forms-ea@adobe.com` from your official email address.


## Configuration Example

```json
{
  "ok": true,
  "integration": {
    "imsEndpoint": "ims-na1-stg1.adobelogin.com",
    "metascopes": "ent_aem_cloud_api",
    "technicalAccount": {
      "clientId": "cm-p107005-e259039-cmstg-integration-0",
      "clientSecret": "s8e-lYOwlQPlvfC12oeDDr7XYRLNS3lta4HC"
    },
    "email": "40932833-4069-47f3-9d8f-accbef0ffd86@techacct.adobe.com",
    "id": "12191A6367AEF24A0A494232@techacct.adobe.com",
    "org": "864A59455E3C1E970A49400C@AdobeOrg",
    "privateKey": "-----BEGIN RSA PRIVATE KEY-----\r\n<PRIVATE_KEY_PLACEHOLDER>\r\n-----END RSA PRIVATE KEY-----\r\n",
    "publicKey": "-----BEGIN CERTIFICATE-----\r\nMIIDKjCCAhKgAwIBAgIJPmvyJ9VAmeq8MA0GCSqGSIb3DQEBCwUAMDExLzAtBgNV\r\nBAMTJmNtLXAxMDcwMDUtZTI1OTAzOS1jbXN0Zy1pbnRlZ3JhdGlvbi0wMB4XDTI1\r\nMDIxNDA3MzUzN1oXDTI2MDIxNDA3MzUzN1owMTEvMC0GA1UEAxMmY20tcDEwNzAw\r\nNS1lMjU5MDM5LWNtc3RnLWludGVncmF0aW9uLTAwggEiMA0GCSqGSIb3DQEBAQUA\r\nAQIBDwAwggEKAoIBAQD35+ergX6tUymoef1zuE2bL70u9Y+K0/SjTThxH9RhVGSa\r\nHe/a6RURIbtIASvPKH1k7dKX/+klx9+Km4BtePORKsOqvzpiGsa6WBa+cgR6le9D\r\nvfg4cs8eMOCiqohCQ3YgKnTRRWplLUBYrmKoz6oY5KOvLP+fXNzUC/Ji5E2Dy5TG\r\n1wvceS0q1XBmW9Gy1PYrHf7n4K2dOPLc7aNvL8kPtKcG5ViyG78PQUhnioADCUjT\r\na4RF9Ia8Mzosv15Aki7sDmDaTTPr5zsbPfSHfUMbg0lofW64+VRTWv9B4EBjUs64\r\nABOZPEFZeUqtODtiPrOviMdrd9O1aA9j+Nj3gk9tAgMBAAGjRTBDMAwGA1UdEwQF\r\nMAMBAf8wCwYDVR0PBAQDAgL0MCYGA1UdEQQfMB2GG2h0dHA6Ly9leGFtcGxlLm9y\r\nZy93ZWJpZCNtZTANBgkqhkiG9w0BAQsFAAOCAQEAPuggX4xlFUpIAe7QGA2d87Rb\r\nspraD4tGBun9EiQAx+PyXXWyp6HH5zV+ikWDlB1AF4EgQrPi/iMxGJUBtRCxscKp\r\n8JZRuywjNe5BXey7gNukI/kZXNrlZGGa5HjkWkHIxV58vegFvfSq0Vc5ClYHTBHO\r\nEcNXvngLM/eprt3pOXHY8bagwke+BOqsvKY4YwbASmwKXe06Y3GXqOxXLBkZyc1a\r\nbAsc6NzefvZganhbk5U5QtNP8yVo06wBFvWbyhM8UhHuhlTG34YzsEyrXN5u9NHR\r\nNymHNNxSoH3X+jwPLOaq0kqQFUN1WtdVogjuP7x/dB7GZNxdI6gSzXI6QVAZ/g==\r\n-----END CERTIFICATE-----\r\n",
    "certificateExpirationDate": "2026-02-14T07:35:37.000Z"
  },
  "statusCode": 200
}
```


## Steps

1.  **Create a Workfront Scenario**
    *   **Objective:** To create a Workfront scenario to automate form submission processing.
    *   **Actions:**
        *   Sign into your [Workfront Fusion account](https://).
        *   Click `Scenarios` in the left panel.
        *   Click `Create a new scenario` in the upper-right corner of the page.
        *   Select `New scenario` in the upper-left corner and type a proper name for the scenario.
        *   Click the question mark icon and ensure you add the first module as `AEM Forms`.
        *   Select the `Watch for Form Events` dialog box.

2.  **Add a Webhook**
    *   **Objective:** To add a webhook to the Workfront scenario.
    *   **Actions:**
        *   Click `Add` in the `Watch for Form Events` dialog box. A dialog box to add a webhook appears.
        *   Specify a webhook name.  *Note: This webhook name will appear in the AEM instance.*
        *   Click `Add` to add a new connection. The `Create a Connection` dialog box appears.

3.  **Add a Connection to a Webhook**
    *   **Objective:** To configure the connection details for the webhook.
    *   **Actions:**
        *   Specify a `Connection Name` in the `Create a Connection` dialog box.
        *   Select `Environment` and `Type` from the drop-down list.
        *   Enter the `Instance URL`.
        *   Retrieve the service credentials from the Developer console.
        *   Replace `ims-na1.adobelogin.com` in the `IMS endpoint` with the value of `imsEndpoint` from the service credentials in the Developer console.
        *   Retain the `[https://`](https://`) in the `IMS endpoint` textbox while adding the `imsEndpoint` URL.
        *   Specify             *   `Client ID` with the value of `clientId` from the service credentials.
            *   `Client Secret` with the value of `clientSecret` from the service credentials.
            *   `Technical Account ID` with the value of `id` from the service credentials.
            *   `Org ID` with the value of `org` from the service credentials.
            *   `Meta Scopes` with the value of `metascopes` from the service credentials.
            *   `Private Keys` with the value of `privateKey` from the service credentials.
        *   For `Private Key`, remove `\r\n` from its value.
        *   You can also retrieve a private key or certificate from a file by selecting the `Extract` button.
        *   Click `Continue`.
        *   Select the created connection from the drop-down list in the `Add a webhook` dialog box.
        *   Click `Save`.
        *   Click `OK` and save the changes for the scenario.
        *   To activate the scenario, click the ON/OFF toggle button in the scenario editor.

4.  **Configure Submit Action of an Adaptive Form for Workfront Fusion**
    *   **Objective:** To configure the submit action of an Adaptive Form to invoke the created Workfront Fusion scenario.
    *   **Actions (New Adaptive Form):**
        *   Log in to your AEM instance.
        *   Go to `Forms > Forms and Documents > Create > Adaptive Form`. The `Create Form` wizard appears.
        *   Select an Adaptive Form template from the `Source` tab.
        *   Select a theme from the `Style` tab.
        *   Select `Invoke a WorkFront Fusion Scenario` from the `Submission` tab.
        *   Select the created webhook from the `Options` tab in the `Properties` window.
        *   Click `Create`.
        *   Specify the name for your new Adaptive Form and click `Create`.
    *   **Actions (Existing Adaptive Form):**
        *   Log in to your AEM instance.
        *   Go to `Forms > Forms and Documents`.
        *   Select an Adaptive Form and open the form in an edit mode.
        *   Open the Content browser, and select the `Guide Container` component of your Adaptive Form.
        *   Click the Guide Container properties icon. The Adaptive Form Container dialog box opens.
        *   Open the `Submission` tab.
        *   Select the `Submit action` as `Invoke a WorkFront Fusion Scenario`.
        *   Select `Workfront Fusion scenario` from the drop-down list.
        *   Click `Done`.


## Next Steps

*   Review the [video tutorial](https://video.tv.adobe.com/v/3427145/adaptive-forms-adobe-workfront-af-workfront-workfront-aem-forms/?quality=12&learn=on) for a visual demonstration.
*   Consult the provided support and resources for further assistance:
    *   [Send email](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/forms/integrate/services/submit-adaptive-form-to-sharepoint-document-library)
    *   [Submit to SharePoint Document Library](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/forms/integrate/services/submit-adaptive-form-to-sharepoint-document-library)
    *   [Submit to SharePoint List](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/forms/integrate/services/submit-adaptive-form-to-sharepoint-list)
    *   [Submit using Form Data Model](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/forms/integrate/services/submit-adaptive-form-using-form-data-model)
    *   [Submit to Azure Blob Storage](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/forms/integrate/services/submit-adaptive-form-to-azure-blob-storage)
    *   [Submit to REST endpoint](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/forms/integrate/services/submit-adaptive-form-to-rest-endpoint)
    *   [Submit to OneDrive](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/forms/integrate/services/submit-adaptive-form-to-onedrive)
    *   [Invoke an AEM Workflow](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/forms/integrate/services/invoke-aem-workflow)
    *   [Submit to Power Automate](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/forms/integrate/services/submit-adaptive-form-to-power-automate)
    *   [Submit to Workfront Fusion](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/forms/integrate/services/submit-adaptive-form-to-workfront-fusion)
    *   [Connect Adaptive Form to Salesforce application](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/forms/integrate/services/connect-adaptive-form-to-salesforce-application)
    *   [Connect an Adaptive Form to Microsoft® Dynamics](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/forms/integrate/services/connect-adaptive-form-to-microsoft-dynamics)
    *   [Connect an Adaptive Form to Adobe Marketo Engage](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/forms/integrate/services/connect-adaptive-form-to-adobe-marketo-engage)
    *   [Create custom submit action](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/forms/integrate/services/create-custom-submit-action)
```

## Related Links

* **Original Documentation:** https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/forms/integrate/services/submit-adaptive-form-to-workfront-fusion
* **Adobe Experience League:** https://experienceleague.adobe.com
* **Adobe Developer Console:** https://developer.adobe.com/console
* **Adobe Support:** https://helpx.adobe.com

## Additional Resources

* **Adobe Documentation:** https://docs.adobe.com
* **Community Forums:** https://experienceleaguecommunities.adobe.com
* **Training Resources:** https://learning.adobe.com

---
