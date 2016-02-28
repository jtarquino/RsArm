# Create a new SSRS Server with a SQL catalog (2 Machines) 

This template creates two new Azure VMs, each with a public IP address, it configures one VM to be an SSRS Server, one with SQL Server mixed auth for the SSRS Catalog with the SQL Agent Started. All VMs have public facing RDP and diagnostics enabled , the diagnostics is stored in a consolidated diagnostics storage account different than the vm disk

Click the button below to deploy

<a href="https://portal.azure.com/#create/Microsoft.Template/uri/https%3A%2F%2Fraw.githubusercontent.com%2Fjtarquino%2FRsArm%2Fmaster%2FRSARM%2FTemplates%2FSSRS-Catalog%2FAzureDeploy.json" target="_blank">
    <img src="http://azuredeploy.net/deploybutton.png"/>
</a>
<a href="http://armviz.io/#/?load=https%3A%2F%2Fraw.githubusercontent.com%2Fjtarquino%2FRsArm%2Fmaster%2FRSARM%2FTemplates%2FSSRS-Catalog%2FAzureDeploy.json" target="_blank">
  <img src="http://armviz.io/visualizebutton.png"/>
</a>

 
By Default it will create the SQL machines using the image ***SQL2014SP1-WS2012R2*** and the ***Enterprise*** sku, the full list of available images and their SKUs can be obtained running

    Get-AzureRmVMImageOffer -Location "westus" -Publisher "MicrosoftSQLServer" | Select Offer
    Get-AzureRmVMImageSku -Location "westus"-Publisher "MicrosoftSQLServer" -Offer "SQL2014SP1-WS2012R2" | Select Skus

For example
* **sqlImageVersion:** SQL2014SP1-WS2012R2 **sku:** Enterprise 
* **sqlImageVersion:** SQL2016CTP3.3-WS2012R2 **sku:** Evaluation


***For CTP Versions of SQL the only SKU available is Evaluation*** 

***
It contains a modified version of xSQLServerRSConfig that supports machines that are non domain join and uses SQL authentication for connection SSRS with the database 
based on the DSC package http://www.powershellgallery.com/packages/xSQLServer/1.4.0.0.

It contains the DSC scripts from https://sqlvmgroup.blob.core.windows.net/singlevm/PrepareSqlServer.ps1.zip used by the Azure marketplace to create SQL Machines


        