# Lab 12: Using Azure Resource Manager (ARM) Templates

1. **Créer un Template ARM pour déployer une application multi-tier**
    *creation d'un template.json*

2. **Créer un groupe de ressources**

- Commande équivalente (Azure CLI)

```bash
az group create --name myResourceGroup --location EastUS
```

3. **Déployer le template ARM**

```bash
az deployment group create \
  --resource-group myResourceGroup \
  --template-file template.json \
  --parameters adminPassword='Password123'

```