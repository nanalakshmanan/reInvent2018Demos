# DEV 403
Demos for builder sessions **DEV 403 - Automate Common Maintenance & Deployment Tasks Using AWS Systems Manager**

**Setup**

Run the following cloudformation templates located in Setup/CloudformationTemplates folder. For the builder sessions, run these cloudformation templates in **us-west-1**

1. **LinuxInstances.yml** - to Create 2 managed Linux Instances. 
***Note*** For cross region demos, run this additionally in **us-east-1**
2. **AWS-SystemsManager-AutomationAdministrationRole.yml** - for creating the administration role in the management account (*account from which you execute multi account automations*)
3. **AWS-SystemsManager-AutomationExecutionRole.yml** - for creating execution role in the target account (*account in which you want to perform the action*). You need to specify the account id of the management account. For mutli region management within the same account, specify the account id
4. **SendMailLambda.yml** - setting up lambda that can send emails using SES. The from email id has to be validated using SES in **us-east-1**

**Automation Documents**

1. **Nana-StartEC2Instance.yml** - Automation document written using AWS API actions. Demonstrates how to convert AWS CLI command into automation action, wait for a desired resource property value, conditional branching
2. **Nana-RunPatchBaseline.yml** - Automation document that wraps AWS-RunPatchBaseline. Used for installing or scanning for patch compliance across multiple regions and accounts
3. **Nana-BounceHostRunbook.json** - automaion document that emulates an operational runbook for restarting hosts. Used for manually executing an automation document one step at a time