# IaaS IIS and SQL on Windows Server 2016

<a href="https://portal.azure.com/#create/Microsoft.Template/uri/https%3A%2F%2Fraw.githubusercontent.com%2Ffixx220%2FARMTemplates%2Fmaster%2FIISandSQL-ManDisksAndAS%2Fazuredeploy.json" target="_blank">
    <img src="http://azuredeploy.net/deploybutton.png" />
</a>
<a href="https://portal.azure.us/#create/Microsoft.Template/uri/https%3A%2F%2Fraw.githubusercontent.com%2Ffixx220%2FARMTemplates%2Fmaster%2FIISandSQL-ManDisksAndAS%2Fazuredeploy.json" target="_blank">
    <img src="http://azuredeploy.net/AzureGov.png" />
</a>
<a href="http://armviz.io/#/?load=https%3A%2F%2Fraw.githubusercontent.com%2Ffixx220%2FARMTemplates%2Fmaster%2FIISandSQL-ManDisksAndAS%2Fazuredeploy.json" target="_blank">
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