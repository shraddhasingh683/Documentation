AEM Forms as a Cloud Service provides an OOTB connector to connect and submit an Adaptive Form to Adobe Workfront Fusion. Submitting a form to Adobe Workfront Fusion can offer several advantages:

It enabled seamless transfer of form submissions data to Workfront Fusion workflows.
It helps automate various tasks triggered by form submissions. This can include initiating projects, assigning tasks to specific team members, sending notifications, and updating project statuses—all without manual intervention.
All form submissions captured within Workfront Fusion, provide a single source of truth for project-related information

## Prerequisites

Before proceeding, ensure 
*   **Licenses:** A valid Workfront and Workfront Fusion license is required.
*   **AEM Access:** An AEM user account with the necessary permissions to access the Developer Console and retrieve service credentials.
*   **Technical Account Membership:** The Technical Account used for the integration *must* be a member of the `forms-users` group within Workfront. Failure to do so will prevent webhook creation.
*   **Network Connectivity:** Stable network connectivity 
*   **Administrative Privileges:** Administrative access to both AEM Forms and Workfront Fusion.
*   **Understanding of Concepts:** A solid understanding of AEM Forms and Workfront Fusion concepts, including Adaptive Forms, scenarios, webhooks, and data models.
*   **SSL Certificates:** Valid SSL certificates for secure communication between AEM Forms and Workfront Fusion.
*   **API Keys & Authentication:** API keys and authentication credentials (Client ID, Client Secret, Technical Account ID, Org ID, Meta Scopes, Private Key) obtained from the Adobe Developer Console.  These are essential for establishing a secure connection.



Integrate AEM Forms with Adobe Workfront Fusion
1. Create a Workfront Scenario
To create a Workfront scenario, perform the following steps:

Create a scenario
Add a web hook to a scenario
Add a connection to a web hook
Create a scenario
To create a scenario:

1.Sign into your Workfront Fusion account.

2.Click Scenarios Share icon in the left panel.

3.Click Create a new scenario in the upper-right corner of the page. A page to create new scenario appears on-screen.

4.Select New scenario in the upper-left corner on the page and type a proper name for the scenario.

5.Click the question mark and make sure you add first module as AEM Forms.

6.Select the Watch for Form Events dialog box and a window to add a webhook appears.


Add a connection to a webhook:

Specify a Connection Name in the Create a Connection dialog box.

Select Environment and Type from the drop-down list.

Enter the Instance URL.

Specify the following values in the Create a Connection dialog box:

Specify Client ID with value of clientId from the service credentials in the Developer console.

Specify Client Secret with value of clientSecret from the service credentials in the Developer console.

Specify Technical Account ID with value of id from the service credentials in the Developer console.

Specify Org ID with value of org from the service credentials in the Developer console.

Meta Scopes with value of metascopes from the service credentials in the Developer console.

Private Keys with value of privateKey from the service credentials in the Developer console.

2. Configure submit action of an Adaptive Form for Workfront Fusion
You can configure the submit action for Workfront Fusion for:

New Adaptive Forms
Existing Adaptive forms
Configure submit action of new Adaptive Form for Workfront Fusion
To configure submit action of new Adaptive Form for Workfront Fusion:

Log in to your AEM instance.

Go to Forms > Forms and Documents > Create > Adaptive Form. The Create Form wizard appears.

Select an Adaptive Form template from the Source tab.

Select a theme from the Style tab.

