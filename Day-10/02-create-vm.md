# Create VM using Azure CLI
### Start by loging in to azure
---
az login
---

### Start with creating a Resource Group

```
az group create --name learn-azure-cli --location eastus
az group list --output table

```

### Set the Resource Group as default (Optional)

```
az configure --defaults group=learn-azure-cli

```

### Create VM with Vnet

```
az vm create \
  --resource-group learn-azure-cli \
  --name azure-cli \
  --vnet-name default \
  --subnet default \
  --image Ubuntu2204 \
  --admin-username azureuser \
  --generate-ssh-keys \
  --output json \
  --verbose

```
### Connect Using SSH
---
## Step 1: Get the Public IP Address
az vm show --resource-group learn-azure-cli --name azure-cli --show-details --query [publicIps] --output tsv
## Step 2: Connect Using SSH
ssh azureuser@13.92.81.20
## Step 3: Troubleshooting
chmod 600 ~/.ssh/id_rsa

---

### Delete the Resource Group to delete all the resources

```
az group delete --name learn-azure-cli
```

