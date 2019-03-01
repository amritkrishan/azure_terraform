#Azure CLI to all subscriptions in the account
az account show --query "{subscriptionId:id, tenantId:tenantId}"

#Azure CLI to set the subscription id
az account set --subscription="${SUBSCRIPTION_ID}"

#Azure CLI to create a Service Principal for Terraform
az ad sp create-for-rbac --role="Contributor" --scopes="/subscriptions/${SUBSCRIPTION_ID}"

#Also you can use the shell script to export the variables,

#!/bin/sh
echo "Setting environment variables for Terraform"
export ARM_SUBSCRIPTION_ID=your_subscription_id
export ARM_CLIENT_ID=your_appId
export ARM_CLIENT_SECRET=your_password
export ARM_TENANT_ID=your_tenant_id

# Not needed for public, required for usgovernment, german, china
export ARM_ENVIRONMENT=public