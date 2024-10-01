# Commandes Azure CLI pour Lab 1

## 1. Création d'une machine virtuelle Windows :
```bash
az vm create --resource-group myResourceGroup --name <nom_vm> --image UbuntuLTS --admin-username azureuser --admin-password myPassword123
