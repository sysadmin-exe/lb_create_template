#Template creates Internal load balancer with 2 backend pools that contains 3 VMs each

The below PowerShell script will deploy the ARM template

$projectName = "Tester"
$location = "westeurope"
$adminUserName = "sysadmin-exe"
$adminPassword = Read-Host -Prompt "Enter the virtual machine administrator password" -AsSecureString

$resourceGroupName = "${projectName}rg"
$templateUri = "https://raw.githubusercontent.com/sysadmin-exe/lb_create_template/master/azuredeploy.json"

New-AzResourceGroup -Name $resourceGroupName -Location $location
New-AzResourceGroupDeployment -ResourceGroupName $resourceGroupName -TemplateUri $templateUri -projectName $projectName -location $location -adminUsername $adminUsername -adminPassword $adminPassword

Write-Host "Press [ENTER] to continue."