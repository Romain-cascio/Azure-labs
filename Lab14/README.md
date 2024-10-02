# Lab 14: Configuring Azure DNS and Custom Domains

1. **Créer une zone DNS Azure**

![1.png](1.png)

- Commande équivalente (Azure CLI)

```bash
az network dns zone create \
  --resource-group $RESOURCE_GROUP \
  --name $DNS_ZONE
```

2. **Gérer les enregistrements DNS pour un domaine personnalisé**

![2.png](2.png)

- Commande équivalente (Azure CLI)

Créer un enregistrement A (pour mapper un sous-domaine www à une adresse IP) :
```bash
az network dns record-set a add-record \
  --resource-group $RESOURCE_GROUP \
  --zone-name $DNS_ZONE \
  --record-set-name "www" \
  --ipv4-address "123.123.123.123"
```

Créer un enregistrement CNAME (pour mapper un sous-domaine à un autre domaine) :
```bash
az network dns record-set cname set-record \
  --resource-group $RESOURCE_GROUP \
  --zone-name $DNS_ZONE \
  --record-set-name "www" \
  --cname "myapp.azurewebsites.net"
```

3. **Configurer la vérification de domaine et le mappage pour les services Azure**

- Commande équivalente (Azure CLI)

Associer un domaine personnalisé à un App Service :
```bash
az webapp config hostname add \
  --resource-group $RESOURCE_GROUP \
  --webapp-name "myAppService" \
  --hostname "www.mydomain.com"
```
Créer un enregistrement TXT pour la vérification :
```bash
  az network dns record-set txt add-record \
  --resource-group $RESOURCE_GROUP \
  --zone-name $DNS_ZONE \
  --record-set-name "@" \
  --value "verification-code-from-azure"
```

4. **Mettre en œuvre des alias DNS (CNAME) et des ensembles d'enregistrements**

- Commande équivalente (Azure CLI)

Créer un enregistrement CNAME :
```bash
az network dns record-set cname set-record \
  --resource-group $RESOURCE_GROUP \
  --zone-name $DNS_ZONE \
  --record-set-name "app" \
  --cname "myapp.azurewebsites.net"

```
