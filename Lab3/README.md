# Lab 3: Deploying Azure App Service Web Apps

1. **Création d’un App Service Plan**

### Commande équivalente (Azure CLI)
```bash
az appservice plan create \
  --name myAppServicePlan \
  --resource-group <nom_du_groupe> \
  --sku S1 \
  --location France paris
```

2. **Déployer une application web**

### Commande équivalente (Azure CLI)
```bash
az webapp create \
  --resource-group <nom_du_groupe> \
  --plan AppServicePlan-lab3 \
  --name Appservice-lab3 \
  --runtime "NODE|20-lts"
```

3. **Configurer un domaine personnalisé et SSL**

### Commande équivalente (Azure CLI)
```bash
az webapp config hostname add \
  --resource-group <nom_du_groupe> \
  --webapp-name Appservice-lab3 \
  --hostname <nom_domaine_personnalisé>
```

```bash
az webapp config ssl upload \
  --certificate-file <certificat> \
  --certificate-password <mot_de_passe> \
  --name Appservice-lab3 \
  --resource-group <nom_du_groupe>
```

4. **Implémenter des slots de déploiement**

### Commande équivalente (Azure CLI)
```bash
az webapp deployment slot create \
  --resource-group <nom_du_groupe> \
  --name Appservice-lab3 \
  --slot staging \
  --configuration-source Appservice-lab3
```

```bash
az webapp deployment slot swap \
  --resource-group <nom_du_groupe> \
  --name Appservice-lab3 \
  --slot staging
```