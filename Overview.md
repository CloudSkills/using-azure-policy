## Azure Policy Series
1. Intro to Azure Policies and Auditing examples
2. Leveraging Azure Policy to only allow for specific resource types
3. Handling tagging within Azure Policy
4. Updating resources using Azure Policy


### Post: Intro to Azure Policies and Auditing examples
What is Azure Policy?
- What can it do
- Where can you apply it
- Why do I want to use it

Goals
- You will be able to review an Azure Policy and setup a new policy to audit your resources

Prerequisites
- You will need a valid Azure Subscription

Step 1 - Review the Azure Policy in the Portal
- Overview and Compliance

Step 2 - Understanding components of Azure policy
- Definitions
- Assignments
    - Touch on initiative but mention you will cover this later

Step 3 - Reviewing the existing policies
- Go the Subscription --> Policies
- Review what is in place (Example will be empty)

Step 4 - Creating our first Audit policy
- Describe the goal

Step 5 - Create the policy definition
- Filter by category
- Duplicate the policy 
- Update the Effect from "Deny" to "Audit"
- Save

Step 6 - Create the assignment
- Basics
- Parameters

Step 7 - Reviewing your Policy
- View resources that are in compliance and those that are not

Next post 

Step 2 - Configuring a 

Auditing Example
- Check for resources that are not tagged
- Check for resources that do not have diagnostics enabled


### Post: Leveraging Azure Policy to only allow for specific resource groups