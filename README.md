# Azure AKS Version Monitor

[![Azure AKS Monitor](https://github.com/johndohoneyjr/AKS-Version-Monitor/actions/workflows/azure-aks-monitor.yml/badge.svg)](https://github.com/johndohoneyjr/AKS-Version-Monitor/actions/workflows/azure-aks-monitor.yml)

## Installation
```
Create a Service Principal -- with the scope appropriate for your organization
az ad sp create-for-rbac --name My-AKS-BOT --role Contributor  --sdk-auth --scopes /subscriptions/zzz-aaa-www-rrrr

The output is a JSON DOcument, paste the entirety of the JSON into the Action Secret: CLUSTER_SERVICE_PRINCIPAL 
```
Finally, you will need to set the following secrets in your repository secrets settings:

```
AKS_CLUSTER_NAME: The name of your AKS cluster.

RESOURCE_GROUP: The resource group that contains your AKS cluster.

LOCATION: The location of your AKS cluster.
```
This action will run every day at midnight (UTC) and retrieve information about your AKS cluster, including the current revision and patch level, as well as a list of available patches and revisions. The available patches and revisions will be printed to the log.

## Integrations

This could be interfaced with Slack by adding the step:
```
 - name: Send to Slack
        uses: rtCamp/action-slack-notify@v1
        with:
          slack_webhook: ${{ secrets.SLACK_WEBHOOK }}
          message: |
            Current revision: $aks_cluster_version
            Available patches: $available_patches
            Available revisions: $available_revisions
```
