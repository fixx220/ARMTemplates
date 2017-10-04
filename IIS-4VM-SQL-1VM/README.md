# IIS VMs and SQL VM

<a href="https://portal.azure.com/#create/Microsoft.Template/uri/https%3A%2F%2Fraw.githubusercontent.com%2Ffixx220%2FARMTemplates%2Fmaster%2FIIS-4VM-SQL-1VM%2Fazuredeploy.json" target="_blank">
    <img src="http://azuredeploy.net/deploybutton.png" />
</a>
<a href="https://portal.azure.us/#create/Microsoft.Template/uri/https%3A%2F%2Fraw.githubusercontent.com%2Ffixx220%2FARMTemplates%2Fmaster%2FIIS-4VM-SQL-1VM%2Fazuredeploy.json" target="_blank">
    <img src="http://azuredeploy.net/AzureGov.png" />
</a>
<a href="http://armviz.io/#/?load=https%3A%2F%2Fraw.githubusercontent.com%2Ffixx220%2FARMTemplates%2Fmaster%2FIIS-4VM-SQL-1VM%2Fazuredeploy.json" target="_blank">
    <img src="http://armviz.io/visualizebutton.png"/>
</a>

This template creates one to four Windows Server 2016 VM(s) with IIS configured using DSC. It also installs one SQL Server 2014 standard edition VM, a VNET with two subnets, NSG, load balancer, NATing and probing rules.

<b>Context:</b><br>
I'm creating this template as a learning tool and modifying one of the quickstart templates created by GitHub User:  alibaloch

<b>You can find the original here:</b>
<a href="https://github.com/Azure/azure-quickstart-templates/tree/master/iis-2vm-sql-1vm">
https://github.com/Azure/azure-quickstart-templates/tree/master/iis-2vm-sql-1vm
</a><br>
I chose this template as a base because it's well put together, both the template itself and the GitHub integrations, images etc.

## Resources
The following resources are created by this template:
- 1 to 4 Windows Server 2016 VMs running the IIS role.
- 1 SQL Server 2014 running on premium or standard storage.
- 1 virtual network with 2 subnets (Frotend and Backend) with NSG rules.
- 1 storage account for the VHD files.
- 1 Availability Set for IIS servers.
- 1 Load balancer with NATing rules.


<img src="https://raw.githubusercontent.com/fixx220/ARMTemplates/master/IIS-4VM-SQL-1VM/images/resources.png" />


## Architecture Diagram
<img src="https://raw.githubusercontent.com/fixx220/ARMTemplates/master/IIS-4VM-SQL-1VM/images/architecture.png" />