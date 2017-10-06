# IaaS IIS and SQL on Windows Server 2016 using Managed Disks and Availability Set

<a href="https://portal.azure.com/#create/Microsoft.Template/uri/https%3A%2F%2Fraw.githubusercontent.com%2Ffixx220%2FARMTemplates%2Fmaster%2FIISandSQL-ManDisksandAS%2Fazuredeploy.json" target="_blank">
    <img src="http://azuredeploy.net/deploybutton.png" />
</a>
<a href="https://portal.azure.us/#create/Microsoft.Template/uri/https%3A%2F%2Fraw.githubusercontent.com%2Ffixx220%2FARMTemplates%2Fmaster%2FIISandSQL-ManDisksandAS%2Fazuredeploy.json" target="_blank">
    <img src="http://azuredeploy.net/AzureGov.png" />
</a>
<a href="http://armviz.io/#/?load=https%3A%2F%2Fraw.githubusercontent.com%2Ffixx220%2FARMTemplates%2Fmaster%2FIISandSQL-ManDisksandAS%2Fazuredeploy.json" target="_blank">
    <img src="http://armviz.io/visualizebutton.png"/>
</a>

This template creates one to four Windows Server 2016 VM(s) with IIS configured using DSC. It also installs one SQL Server 2016 SP1 standard edition VM, a VNET with two subnets, NSG, Load Balancer, NATing and probing rules.  VMs are created with managed disks and web servers are members of a managed Availability Set.

<b>Context:</b><br>
This template is a carbon copy of another one on my account with the only difference being that it uses managed disks and a managed Availability Set. 

<b>You can find the original here:</b>
<a href="https://github.com/fixx220/ARMTemplates/tree/master/IIS-4VM-SQL-1VM">
https://github.com/fixx220/ARMTemplates/tree/master/IIS-4VM-SQL-1VM
</a><br>

## Resources
The following resources are created by this template:
- 1 to 4 Windows Server 2016 VMs with the IIS role installed
- 1 Windows Server 2016 VM with SQL Server 2016 SP1 installed.
- SQL Server has a 50GB data disk attached.
- All created VM disks are managed by Azure.
- 1 Virtual Network with 2 Subnets (Frontend and Backend) with NSG rules.
- 1 Managed Availability Set for IIS servers.
- 1 Load balancer with NATing rules.


<img src="https://raw.githubusercontent.com/fixx220/ARMTemplates/master/IISandSQL-ManDisksandAS/images/resources.png" />


## Architecture Diagram
<img src="https://raw.githubusercontent.com/fixx220/ARMTemplates/master/IISandSQL-ManDisksandAS/images/architecture.png" />

## PowerShell Deployment

Here is some example code for deploying this template using PowerShell.  Remeber to log into your Azure account first using <b>"Login-AzureRMAccount"</b>
<br>

```PowerShell
# Deployment Variables
$DeploymentNumber = "001" # Increment this number for subscequent deployments
$RGName = "ResourceGroupName"
$RGLocation = "southcentralus" # Change this as required
$TemplatePath = "Enter the path to your ARM template"

# Create new Resource Group for Template Deployment
New-AzureRmResourceGroup -Name $RGName -Location $RGLocation

# Deploy IISandSQL-ManDisksandAS ARM Template
New-AzureRmResourceGroupDeployment -Name CustomerPrefix$DeploymentNumber `
    -ResourceGroupName $RGName `
    -TemplateFile $TemplatePath `
    -dnsLabelPrefix "DNSLabelHere (Lowercase)" `
    -adminUsername "AdministratorUsername" `
    -adminPassword ("AdministratorPassword" | ConvertTo-SecureString -AsPlainText -Force) `
    -webServerVMSize "Standard_A1" ` # Change as required, allowed values are listed in the template under parameter of the same name
    -numberOfWebServers 2 ` # Change as required, allowed values are listed in the template under parameter of the same name
    -sqlServerVMSize "Standard_DS1" # Change as required, allowed values are listed in the template under parameter of the same name
    ```