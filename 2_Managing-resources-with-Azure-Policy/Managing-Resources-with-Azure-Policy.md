# Managing resources with Azure Policy

### Goals
This is the second post in a series to help you become more familiar with Azure Policy.  If you haven't seen the [first post](https://cloudskills.io/blog/azure-policy) please check it out to get a basic understanding of Azure Policy components.  

We will build upon that by learning more about the Effects within Azure Policy.  We will also discuss how to create better Parameters to minimize any confusion when assigning our policy definitions.  


### Effects in Azure Policy
Effects within Azure Policy is where you decide how Azure Policy will handle resources that meet the "if" condition of the policy definition.  There are 7 effects as of this writing that are available.  2 more are available in preview that are associated with Kubernetes that we will not cover.   

- Append
    - This allows you to append additional fields to a resource when it is created or updated.  
    - For example, you need to ensure a certain IP range is always allowed to a storage account.
- Audit
    - This helps you identify a non-compliant resource.  It does not stop a resource from being created or modified. This is what we configured in the [first post](https://cloudskills.io/blog/azure-policy) post.  
- AuditIfNotExists
    - This helps you identify if a resource does not have all of the properties defined as intended. 
    - For example, you need to ensure that a VM has the diagnostic an extension enabled
- Deny
    - This will prevent a resource from being created or updated.  We will be covering this later in this post.
- DeployIfNotExists
    - This will allow you to modify a resource if it is not configured as intended.Similar to AuditIfNotExists, except this allows you to apply a template to the resource to remediate the variance. 
- Disabled
    - This is used for testing a policy.  For example, if you want to create a policy to ensure the "if" statement is running properly but do not want the rest of the policy to apply. 
- Modify
    - This is used to manage the tags associated with a resource.  

We will provide examples for both the "Deny" and "Modify" effects in this post.  Before we dive into how to use the effects lets discuss parameters.

### How to make better parameters in Azure Policy
Ultimately our goal with any Azure Policy is to help us manage our environment with the minimal amount of manual work.  One way to help us do this is by using parameters in our policy definitions so that it can be adjusted for each assignment rather then having to create a new definition each time.   

The parameters in Azure Policy follow the same format as those for ARM templates.  You can create help messages, allowed values, and even specify a default value for your parameters. This example below shows one that has all of these defined.  This example only allows you to select a storage SKU that is geographically replicated to support a workload that must be available if there was regional outage.  

```json
"parameters": {
  "allowedStorageSKU": {
    "type": "string",
    "allowedValues": [
      "Standard_GRS",
      "Standard_RAGRS",
    ],
    "defaultValue": "Standard_GRS",
    "metadata": {
      "description": "Select the type of replication to use for the storage account."
    }
  }
}
```

One other item that is very helpful for Azure Policy is what is called the property "strongType".  When this property is defined in a parameter, it provides a list of an existing resources to select from when creating the policy assignment.  This can be very helpful if you need to set the Log Analytics Workspace to use or need to specify the Event Hub authorization rule.  

Rather then typing in the Event Hub namespace and authorization rule  

##### Insert image of the crappy smell way  

It's much easier to select from a drop down menu  

##### Insert image of awesomeness  

