# Deploy Phi-3 models as serverless APIs

Phi-3 models (Mini, Small and Medium) in the [Azure model catalog](https://learn.microsoft.com/azure/machine-learning/concept-model-catalog?WT.mc_id=aiml-137032-kinfeylo) can be deployed as a serverless API with pay-as-you-go billing. This kind of deployment provides a way to consume models as an API without hosting them on your subscription, while keeping the enterprise security and compliance that organizations need. This deployment option doesn't require quota from your subscription.

[REST API](https://learn.microsoft.com/azure/ai-studio/reference/reference-model-inference-chat-completions?WT.mc_id=aiml-137032-kinfeylo) MaaS models now support a common REST API for chat completions using the /chat/completions route.

## Prerequisites

1. An Azure subscription with a valid payment method. Free or trial Azure subscriptions won't work. If you don't have an Azure subscription, create a paid Azure account to begin.
1. An [Azure AI Foundry](https://ai.azure.com/?WT.mc_id=aiml-137032-kinfeylo) hub. The serverless API model deployment offering for Phi-3 is only available with hubs created in these regions:
    - **East US 2**
    - **Sweden Central**

    > [!NOTE]
    > For a list of regions that are available for each of the models supporting serverless API endpoint deployments, see Region availability for models in serverless API endpoints.

1. An [Azure AI Foundry](https://ai.azure.com/?WT.mc_id=aiml-137032-kinfeylo) project.
1. Azure role-based access controls (Azure RBAC) are used to grant access to operations in Azure AI Foundry. To perform the steps in this article, your user account must be assigned the Azure AI Developer role on the resource group.

## Create a new deployment

Perform the following tasks to create a deployment:

1. Sign in to [Azure AI Foundry](https://ai.azure.com/?WT.mc_id=aiml-137032-kinfeylo).
1. Select Model catalog from the left sidebar.
1. Search for and select the model you want to deploy, for example Phi-3-mini-4k-Instruct, to open its Details page.
1. Select Deploy.
1. Choose the option Serverless API to open a serverless API deployment window for the model.

Alternatively, you can initiate a deployment by starting from your project in AI Foundry.

1. From the left sidebar of your project, select Components > Deployments.
1. Select + Create deployment.
1. Search for and select Phi-3-mini-4k-Instruct to open the model's Details page.
1. Select Confirm, and choose the option Serverless API to open a serverless API deployment window for the model.
1. Select the project in which you want to deploy your model. To deploy the Phi-3 model, your project must belong to one of the regions listed in the [prerequisites section](https://learn.microsoft.com/azure/ai-studio/how-to/deploy-models-phi-3?WT.mc_id=aiml-137032-kinfeylo).
1. Select the Pricing and terms tab to learn about pricing for the selected model.
1. Give the deployment a name. This name becomes part of the deployment API URL. This URL must be unique in each Azure region.
1. Select Deploy. Wait until the deployment is ready and you're redirected to the Deployments page. This step requires that your account has the Azure AI Developer role permissions on the Resource Group, as listed in the prerequisites.
1. Select Open in playground to start interacting with the model.

Return to the Deployments page, select the deployment, and note the endpoint's Target URL and the Secret Key, which you can use to call the deployment and generate completions. For more information on using the APIs, see [Reference: Chat Completions](https://learn.microsoft.com/azure/ai-studio/reference/reference-model-inference-chat-completions?WT.mc_id=aiml-137032-kinfeylo).

You can always find the endpoint's details, URL, and access keys by navigating to your Project overview page. Then, from the left sidebar of your project, select Components > Deployments.

## Consume Phi-3 models as a service

Models deployed as serverless APIs can be consumed using the chat API, depending on the type of model you deployed.

1. From your Project overview page, go to the left sidebar and select Components > Deployments.
2. Find and select the deployment you created.
3. Copy the Target URL and the Key value.
4. Make an API request using the chat/completions API using <target_url>chat/completions. For more information on using the APIs, see the [Reference: Chat Completions](https://learn.microsoft.com/azure/ai-studio/reference/reference-model-inference-chat-completions?WT.mc_id=aiml-137032-kinfeylo)

## Cost and quotas

Cost and quota considerations for Phi-3 models deployed as serverless APIs

You can find the pricing information on the Pricing and terms tab of the deployment wizard when deploying the model.

Quota is managed per deployment. Each deployment has a rate limit of 200,000 tokens per minute and 1,000 API requests per minute. However, we currently limit one deployment per model per project. Contact Microsoft Azure Support if the current rate limits aren't sufficient for your scenarios.

## Additional Resources 

### Deploy models as serverless APIs

MaaS Models as a Service For details on [MaaS Deployment](https://learn.microsoft.com//azure/ai-studio/how-to/deploy-models-serverless?tabs=azure-ai-studio?WT.mc_id=aiml-137032-kinfeylo)

### How to deploy Phi-3 family of small language models with Azure Machine Learning studio or Azure AI Foundry

Maap Models as a Platform for details on [MaaP Deployment](https://learn.microsoft.com/azure/machine-learning/how-to-deploy-models-phi-3?view=azureml-api-2&tabs=phi-3-mini)