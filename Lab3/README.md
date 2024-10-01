# Lab 3: Deploying Azure App Service Web Apps

## Créer un plan App Service
1. Créez un App Service Plan dans le portail Azure :
    Name : AppServicePlan-Lab3
    Operating System : Linux ou Windows
    Region : Sélectionner la région préférée
    Pricing Tier : Free ou Standard selon les besoins

### Commande équivalente (Azure CLI)
az appservice plan create \
  --name myAppServicePlan \
  --resource-group <nom_du_groupe> \
  --sku S1 \
  --location France paris

## Déployer une application Web

# Créer une application web
az webapp create \
  --resource-group <nom_du_groupe> \
  --plan AppServicePlan-lab3 \
  --name Appservice-lab3 \
  --runtime "NODE|20-lts"

## Configurer un domaine personnalisé et SSL

### Commande équivalente (Azure CLI)
az webapp config hostname add \
  --resource-group <nom_du_groupe> \
  --webapp-name Appservice-lab3 \
  --hostname <nom_domaine_personnalisé>

az webapp config ssl upload \
  --certificate-file <certificat> \
  --certificate-password <mot_de_passe> \
  --name Appservice-lab3 \
  --resource-group <nom_du_groupe>

## Implémenter des slots de déploiement

### Commande équivalente (Azure CLI)
az webapp deployment slot create \
  --resource-group <nom_du_groupe> \
  --name Appservice-lab3 \
  --slot staging \
  --configuration-source Appservice-lab3

az webapp deployment slot swap \
  --resource-group <nom_du_groupe> \
  --name Appservice-lab3 \
  --slot staging