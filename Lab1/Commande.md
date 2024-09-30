# Commandes Azure CLI pour Lab 1

## 1. Création d'une machine virtuelle Windows :
```bash
az vm create --resource-group myResourceGroup --name myWinVM --image Win2019Datacenter --admin-username azureuser --admin-password myPassword123
