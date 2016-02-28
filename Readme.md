# Create a new SSRS Server with 3 machines

This template creates three new Azure VMs, each with a public IP address, it configures one VM to be an SSRS Server, one with SQL Server mixed auth for the SSRS Catalog with the SQL Agent Started, and one one with SQL Server mixed auth for datasources, all VMs have public facing RDP and diagnostics enabled , the diagnostics is stored in a consolidated diagnostics storage account different than the vm disk

Click the button below to deploy

<a href="https://portal.azure.com/#create/Microsoft.Template/uri/https%3A%2F%2Fraw.githubusercontent.com%2Fjtarquino%2FRsArm%2Fmaster%2FRSARM%2FTemplates%2FAzureDeploy.json" target="_blank">
    <img src="http://azuredeploy.net/deploybutton.png"/>
</a>

***Warning: For CTP Versions of SQL the SKU should be set to Evaluation*** 

***
It contains a modified version of xSQLServerRSConfig that supports machines that are non domain join and uses SQL authentication for connection SSRS with the database 
based on the DSC package http://www.powershellgallery.com/packages/xSQLServer/1.4.0.0.

It contains the DSC scripts from https://sqlvmgroup.blob.core.windows.net/singlevm/PrepareSqlServer.ps1.zip used by the Azure marketplace to create SQL Machines

Avaialble images based on SQL Images availables running the command

        Get-AzureRmVMImageOffer -Location "westus" -Publisher "MicrosoftSQLServer"