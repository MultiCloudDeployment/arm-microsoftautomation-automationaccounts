[![Deploy to Azure](https://aka.ms/deploytoazurebutton)](https://portal.azure.com/#create/Microsoft.Template/uri/https%3A%2F%2Fraw.githubusercontent.com%2FMultiCloudDeployment%2Farm-microsoftautomation-automationaccounts%2F1.0.0.4%2Fazuredeploy.json)
# Create Azure Automation account

This template creates an Automation Account in Azure

Azure Automation delivers a cloud-based automation and configuration service that provides consistent management across your Azure and non-Azure environments. It consists of process automation, update management, and configuration features. Azure Automation provides complete control during deployment, operations, and decommissioning of workloads and resources.

## Parameters

Parameter name | Required | Description
-------------- | -------- | -----------
name           | Yes      | The resource name
location       | No       | Gets or sets the location of the resource.
tags           | No       | Gets or sets the tags attached to the resource.
SkuName        | No       | The account SKU.
DisableLocalAuth | No       | Indicates whether requests using non-AAD authentication are blocked
PublicNetworkAccess | No       | Indicates whether traffic on the non-ARM endpoint (Webhook/Agent) is allowed from the public internet
ResourceGroupName | No       | The name of the Reosurce Group

### name

![Parameter Setting](https://img.shields.io/badge/parameter-required-orange?style=flat-square)

The resource name

### location

![Parameter Setting](https://img.shields.io/badge/parameter-optional-green?style=flat-square)

Gets or sets the location of the resource.

- Default value: `[resourceGroup().location]`

### tags

![Parameter Setting](https://img.shields.io/badge/parameter-optional-green?style=flat-square)

Gets or sets the tags attached to the resource.

### SkuName

![Parameter Setting](https://img.shields.io/badge/parameter-optional-green?style=flat-square)

The account SKU.

- Default value: `Free`

- Allowed values: `Free`, `Basic`

### DisableLocalAuth

![Parameter Setting](https://img.shields.io/badge/parameter-optional-green?style=flat-square)

Indicates whether requests using non-AAD authentication are blocked

- Default value: `False`

### PublicNetworkAccess

![Parameter Setting](https://img.shields.io/badge/parameter-optional-green?style=flat-square)

Indicates whether traffic on the non-ARM endpoint (Webhook/Agent) is allowed from the public internet

- Default value: `True`

### ResourceGroupName

![Parameter Setting](https://img.shields.io/badge/parameter-optional-green?style=flat-square)

The name of the Reosurce Group

## Outputs

Name | Type | Description
---- | ---- | -----------
armTemplate | object | Fully populated template

## Snippets

### Parameter file

```json
{
    "$schema": "https://schema.management.azure.com/schemas/2015-01-01/deploymentParameters.json#",
    "contentVersion": "1.0.0.0",
    "metadata": {
        "template": "azuredeploy.json"
    },
    "parameters": {
        "name": {
            "value": ""
        },
        "location": {
            "value": "[resourceGroup().location]"
        },
        "tags": {
            "value": {}
        },
        "SkuName": {
            "value": "Free"
        },
        "DisableLocalAuth": {
            "value": false
        },
        "PublicNetworkAccess": {
            "value": true
        },
        "ResourceGroupName": {
            "value": ""
        }
    }
}
```

### Command line

#### PowerShell

```powershell
New-AzResourceGroupDeployment -Name <deployment-name> -ResourceGroupName <resource-group-name> -TemplateFile <path-to-template> -TemplateParameterFile <path-to-templateparameter>
```

#### Azure CLI

```text
az group deployment create --name <deployment-name> --resource-group <resource-group-name> --template-file <path-to-template> --parameters @<path-to-templateparameterfile>
```
