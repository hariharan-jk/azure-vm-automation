# azure-vm-automation

**Project: Automating Virtual Machine Management with Azure Logic Apps**

**Overview**
This project focuses on automating the start and stop operations of an Azure Virtual Machine (VM) using Azure Logic Apps. By setting up a scheduled workflow, the VM can be automatically started at a specified time and stopped when not in use. This automation helps in optimizing resource usage, reducing manual effort, and lowering costs.

**Tools & Services Used:**
- Azure Logic Apps – To create the automation workflow.
- Azure Virtual Machines – The resource to be managed.
- Azure Resource Group – To organize resources.
- Managed Identity – For secure authentication.
- Azure Portal – To configure and monitor resources.
- Azure Role-Based Access Control (RBAC) – To assign necessary permissions.

**Implementation Steps**
Step 1: Create a Resource Group
A resource group named LogicApp-RG was created to keep all related resources together.

Step 2: Create an Azure Virtual Machine
A new Virtual Machine (VM) was created inside LogicApp-RG.
A simple Windows/Linux VM was configured with a basic setup.

Step 3: Create an Azure Logic App
A new Logic App was created in Consumption Plan mode.
System-assigned Managed Identity was enabled for authentication.

Step 4: Define the Logic App Workflow
Recurrence Trigger: Set to run every 1 minute (for testing; later modified as needed).
Start Virtual Machine Action: Selected the VM, assigned permissions, and configured the action.
Stop Virtual Machine Action: Added to turn off the VM at a scheduled time.

Step 5: Assign Permissions
Managed Identity of the Logic App was granted the Virtual Machine Contributor role to allow starting and stopping the VM.

Step 6: Run and Monitor the Workflow
Tested the Logic App to ensure it successfully started and stopped the VM as per schedule.
Checked the Logic App Run History for success or failure messages.

**Challenges & Solutions**
Unauthorized Error While Starting the VM
Issue: The Logic App failed due to missing permissions.
Solution: Assigned Virtual Machine Contributor role to the Logic App’s managed identity in Access Control (IAM).

Subscription & Resource Group Not Visible in Logic Apps Designer
Issue: The dropdown for selecting the Resource Group and VM was empty.
Solution: Re-verified Azure subscription access and ensured the Logic App was in the same tenant as the VM.

Incorrect Tenant ID in Authentication
Issue: The workflow failed due to an InvalidAuthenticationTokenTenant error.
Solution: Used the correct Managed Identity authentication instead of OAuth.

**Key Learnings**
Understanding Azure Logic Apps: Learned how to use Logic Apps for automating Azure services.
Managed Identity Usage: Implemented secure authentication without storing credentials.
Role-Based Access Control (RBAC): Assigned permissions to allow automation workflows to control VM operations.
Troubleshooting Authentication Issues: Resolved errors related to tenant mismatches and missing subscriptions.
Optimizing Cost & Efficiency: Reduced manual intervention by scheduling VM start/stop actions.

