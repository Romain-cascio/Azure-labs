# Lab 4: Managing Azure Storage Accounts and Blobs

1. **Création d'un Storage Account avec des options de réplication**

## Commande équivalente (Azure CLI)
```bash
az storage account create \
  --name lab4stockage \
  --resource-group <nom_du_groupe> \
  --location <region> \
  --sku Standard_LRS
```

2. **Téléverser et gérer des blobs**

## Commande équivalente (Azure CLI)
```bash
az storage container create \
  --account-name lab4stockage \
  --name mycontainer

az storage blob upload \
  --account-name lab4stockage \
  --container-name mycontainer \
  --file <chemin_fichier> \
  --name <nom_blob>
```

3. **Configurer une Shared Access Signature**

## Commande équivalente (Azure CLI)
```bash
az storage blob generate-sas \
  --account-name lab4stockage \
  --container-name mycontainer \
  --name <nom_blob> \
  --permissions r \
  --expiry 2024-01-01T00:00:00Z \
  --https-only
```

4. **Implémenter des politiques de gestion du cycle de vie**

## Commande équivalente (Azure CLI)
```bash
az storage account management-policy create \
  --account-name lab4stockage \
  --resource-group <nom_du_groupe> \
  --policy <policy.json>
```