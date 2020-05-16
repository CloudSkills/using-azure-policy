### Step 3 - Creating a policy that will dynamically assign tags

Now we have a policy to audit our resources to ensure they are tagged properly and another policy to ensure no additional resources are created without the required tags.  We can create a policy to dynamically assign a tag to resources.  Our goal is to create a policy that will assign a value to the MaintWindow tag that is based on the value of the "Env" and "App" associated with each resource. 

We are going to focus on making 
