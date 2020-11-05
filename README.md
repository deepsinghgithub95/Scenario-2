# Scenario-2

<#Macro Life, a healthcare company has recently setup the entire Network and Infrastructure on Azure. The infrastructure has different components such as Virtual N/W, Subnets, NIC, IPs, NSG etc. The IT team currently has developed PowerShell scripts to deploy each component where all the properties of each resource is set using PowerShell commands. The business has realized that the PowerShell scripts are growing over period of time and difficult to handover when new admin is on-boarded in the IT. The IT team has now decided to move to ARM based deployment of all resources to Azure. All the passwords are stored in an Azure Service known as key Vault. The deployments needs to be automated using Azure DevOps using IaC (Infrastructure as Code).#>

1- What are different artifacts you need to create - name of the artifacts and its purpose.
A - There are two possible solutions for this. solution 1 - In the build pipeline, we can use the key vault artifact to fetch the secret and update the parameter file and publish everything to artifact
solution  
2 - use the key vault artifact in the release pipeline which is more easier and secure way to handle secrets.   

2 - List the tools you will to create and store the ARM templates.   
A - To create ARM templates, we can use VS code and store the templates in local repos, Azure Git repos or Github repos. For this scenario, I have used Github repos.

3 - Explain the process and steps to create automated deployment pipeline.   
A - i) sync the Azure DevOps repository to VS code where we will commit the changes or add new templates   
ii) In the build pipeline, set the deploy trigger to "Enable continuous integration"   
iii) Set the target resource group and subscription in the ARM template deployment task   
iv) Create appropriate stages as per the environments and setup appropriate triggers (eg: dev, uat, prod) in the release pipeline   
v) In this way, whenever there is a code commit to master branch, pipeline will be triggered automatically

4 - Create a sample ARM template you will use to deploy a Windows VM of any size  
A- Added to repos.

5 - Explain how will you access the password stored in Key Vault and use it as Admin Password in the VM ARM template.  
A- three solutions   
1- using the keyvault task in pipeline
2- use custom powershell script to get the secret name from output
3- Provide the keyvault resource id (endpoint) in the template
