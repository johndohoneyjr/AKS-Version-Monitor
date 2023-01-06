# Azure AKS Version Monitor

[![Azure AKS Monitor](https://github.com/johndohoneyjr/AKS-Version-Monitor/actions/workflows/azure-aks-monitor.yml/badge.svg)](https://github.com/johndohoneyjr/AKS-Version-Monitor/actions/workflows/azure-aks-monitor.yml)

## Installation
```
SERVICE_PRINCIPAL_ID: The ID of the service principal used to authenticate with Azure.

SERVICE_PRINCIPAL_SECRET: The secret of the service principal used to authenticate with Azure.

TENANT_ID: The ID of the tenant associated with your Azure subscription.

SUBSCRIPTION_ID: The ID of the Azure subscription that contains your AKS cluster.
```
Finally, you will need to set the following environment variables in your repository settings:

```
AKS_CLUSTER_NAME: The name of your AKS cluster.

RESOURCE_GROUP: The resource group that contains your AKS cluster.

LOCATION: The location of your AKS cluster.
```
This action will run every day at midnight (UTC) and retrieve information about your AKS cluster, including the current revision and patch level, as well as a list of available patches and revisions. The available patches and revisions will be printed to the log.
