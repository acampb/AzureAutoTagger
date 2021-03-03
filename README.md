# AzureAutoTagger

[![Deploy to Azure](https://aka.ms/deploytoazurebutton)](https://portal.azure.com/#create/Microsoft.Template/uri/https%3A%2F%2Fraw.githubusercontent.com%2Facampb%2FAzureAutoTagger%2Fmain%2Fazuredeploy.json)


Azure AutoTagger is a lightweight, low-cost serverless solution that can easily be deployed to an Azure subscription. Once deployed Azure AutoTagger monitors for `ResourceWriteSucess` events within the subscription and triggers an Azure Function to automatically apply a `LastModifiedTimestamp` and `LastModifiedBy` tag.

![autotagger](/images/autotagger.png)

* [**https://cloudlumberjack.com/posts/azureautotagger/**](https://cloudlumberjack.com/posts/azureautotagger/){:target="_blank"}: More details in a blog post describing the solution.

* [**https://github.com/acampb/AzureAutoTagger**](https://github.com/acampb/AzureAutoTagger){:target="_blank"}: Contains the ARM template code to deploy the infrastructure and role assignments to the subscription

* [**https://github.com/acampb/AzureAutoTaggerFunction**](https://github.com/acampb/AzureAutoTaggerFunction){:target="_blank"}: Contains the Azure Function PowerShell code

![tagging](/images/tagging-spedup.gif)

## Deployment

> Important: You must have **Owner** permissions on the subscription you intend to deploy this to. The template will create a managed identity and assign it to the `Reader` and `Tag Contributor` roles.

Use the **Deploy to Azure** button to easily deploy this solution in a subscription

[![Deploy to Azure](https://aka.ms/deploytoazurebutton)](https://portal.azure.com/#create/Microsoft.Template/uri/https%3A%2F%2Fraw.githubusercontent.com%2Facampb%2FAzureAutoTagger%2Fmain%2Fazuredeploy.json)

-- OR --

1. Clone the GitHub repo locally

```shell
git clone https://github.com/acampb/AzureAutoTagger.git
```

2. Initiate an ARM Template deployment with Azure PowerShell or Azure CLI

Azure PowerShell:

```powershell
New-AzDeployment -Location "East US" -TemplateFile ".\azuredeploy.json" -resourceGroupName "rg-autotagger" -Verbose
```

Azure CLI:

```python
az deployment create --location "West US" --template-file ".\azuredeploy.json" --parameters resourceGroupName=rg-autotagger
```
