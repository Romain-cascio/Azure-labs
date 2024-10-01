# Lab 10: Configuring Azure Backup and Recovery Services

1. **Créer un Recovery Services Vault**

- Commande équivalente (Azure CLI)

```bash
az backup vault create \
  --resource-group myResourceGroup \
  --name myRecoveryVault \
  --location $LOCATION
```

2. **Configurer la sauvegarde pour les VMs et Azure Files**

- Commande équivalente (Azure CLI)

```bash
az backup protection enable-for-vm \
  --resource-group $RESOURCE_GROUP \
  --vault-name myRecoveryVault \
  --vm myVM1
```

```bash
az backup protection enable-for-azurefileshare \
  --resource-group $RESOURCE_GROUP \
  --vault-name myRecoveryVault \
  --storage-account $STORAGE_ACCOUNT_NAME \
  --azure-file-share $FILE_SHARE_NAME
```

3. **Effectuer une sauvegarde et une restauration**

- Commande équivalente (Azure CLI)

```bash
az backup protection backup-now \
  --resource-group $RESOURCE_GROUP \
  --vault-name $VAULT_NAME \
  --container-name $VM_NAME \
  --item-name $VM_NAME \
  --retain-until 30-12-2024 
```

4. **Implémenter des politiques de sauvegarde et de rétention**

- Commande équivalente (Azure CLI)

```bash
az backup policy create \
  --resource-group $RESOURCE_GROUP \
  --vault-name $VAULT_NAME \
  --name "MyBackupPolicy" \
  --policy '{"schedulePolicy": {"scheduleRunFrequency": "Daily", "scheduleRunTimes": ["2024-12-30T02:00:00Z"]}, "retentionPolicy": {"dailySchedule": {"retentionDuration": {"count": 30, "durationType": "Days"}}}}'

az backup protection update-for-vm \
  --resource-group $RESOURCE_GROUP \
  --vault-name $VAULT_NAME \
  --vm $VM_NAME \
  --policy-name "MyBackupPolicy"
```
