1. **Installer les outils Azure Functions Core Tools**

 Installer Node.js :
```bash
brew install node
```

Installer Azure Functions Core Tools :
```bash
brew tap azure/functions
brew install azure-functions-core-tools@4
```

2. **Créer un projet Azure Function localement**

Initialiser un nouveau projet Azure Functions avec Python comme langage de programmation :
```bash
func init MyFunctionProj --python
```

Naviguer dans le répertoire du projet :
```bash
cd MyFunctionProj
```

Créer une nouvelle fonction HTTP déclenchée :
```bash
func new --name HelloWorldFunction --template "HTTP trigger" --authlevel "anonymous"
```

3. **Tester et déployer la fonction**

Démarrer la fonction localement :
```bash
func start
```


```bash
```
```bash
```
```bash
```
```bash
```
