
# Template Zabbix : TemplateWordPressMonitoring

## 🇫🇷 Description du template
Ce template Zabbix permet la supervision complète d’un site **WordPress** via l’API du plugin *wp-zabbix*. Il est basé sur le modèle original disponible ici : https://github.com/enderkus/wp-zabbix.

Il est distribué sous **licence GPL v3** : vous pouvez le modifier et le republier tant que le modèle original est cité.

---
## 🇫🇷 Installation
Pour installer ce template dans Zabbix :
1. Ouvrez l’interface **Zabbix** et connectez-vous avec un compte administrateur.
2. Accédez à : **Configuration → Templates**.
3. Cliquez sur **Import**.
4. Sélectionnez le fichier `TemplateWordPressMonitoring.yaml`.
5. Laissez les options d’import par défaut (ou cochez *« Créer des éléments manquants »* si nécessaire).
6. Cliquez sur **Import**.
7. Associez le template à un hôte : **Configuration → Hosts → (Votre hôte) → Templates → Link Template**.

Les premières données de supervision apparaîtront après quelques minutes.

---
## 🇫🇷 Fonctionnement
Le template interroge l’endpoint `wp-json/wp-zabbix/v1/metrics` du site WordPress pour récupérer un ensemble de métriques, réparties par catégories :

### 🔧 Santé du site
- Version WordPress
- HTTPS activé
- Mode multisite

### ⚙️ Performance
- Charge système (1min, 5min, 15min)
- Mémoire utilisée & pic mémoire
- Temps de réponse API
- Taille de la base de données

### ⏱️ Cron WordPress
- Tâches totales
- Tâches bloquées
- Prochaine exécution
- Cron désactivé/activé

### 📦 Stockage
- Espace disque libre
- Taille du répertoire uploads
- Pourcentage d’utilisation du disque

### 🔐 Sécurité
- Tentatives de connexions échouées (1h / 24h / semaine)
- IP à l’origine des attaques
- Edition de fichiers désactivée
- XML-RPC activé/désactivé

### 🐘 PHP & Logs
- Fatal errors
- Warnings
- Présence du fichier debug.log + taille

### 🔄 Mises à jour WordPress
- Mises à jour du cœur disponibles
- Mises à jour plugins & thèmes
- Nombre total d’updates

### 📉 SSL
- Jours restants avant expiration
- Certificat expiré ou non
- Émetteur

Des **items dépendants** découpent les données JSON fournies par l’API via **JSONPath**.

De nombreux **triggers** sont inclus pour alerter en cas :
- d’erreurs PHP critiques,
- de jobs cron bloqués,
- de fortes consommations disque,
- d’attaques bruteforce,
- d’expiration SSL imminente,
- de performances dégradées.

Des **graphiques** sont également fournis : performance globale, stockage, sécurité, logs PHP, base de données, etc.

---
## 🇫🇷 Macros disponibles
- `{$WP.URL}` : URL du site WordPress
- `{$WEB.DOMAIN}` : Domaine principal
- `{$WP.API.KEY}` : Clé API du plugin wp-zabbix

---
## 🇫🇷 Licence
Ce template est distribué sous **GPL v3**. Vous êtes libre :
- de le modifier,
- de le redistribuer,
À condition de **citer ce modèle**.

---
# 🇬🇧 Template description
This Zabbix template enables complete monitoring of a **WordPress** website through the *wp-zabbix* plugin API. It is based on the original model from: https://github.com/enderkus/wp-zabbix.

It is released under the **GPL v3 license**. You may modify or redistribute it as long as the original model is credited.

---
## 🇬🇧 Installation
To install this template:
1. Open the **Zabbix interface** and log in with an administrator account.
2. Go to **Configuration → Templates**.
3. Click **Import**.
4. Choose the file `TemplateWordPressMonitoring.yaml`.
5. Keep import defaults (or enable *“Create missing items”* if needed).
6. Click **Import**.
7. Attach the template to a host: **Configuration → Hosts → (Your host) → Templates → Link Template**.

Data collection will begin within a few minutes.

---
## 🇬🇧 How it works
The template queries the WordPress API endpoint `wp-json/wp-zabbix/v1/metrics` to retrieve structured monitoring data.

### 🔧 Site health
- WordPress version
- HTTPS enabled
- Multisite status

### ⚙️ Performance
- Load average (1 / 5 / 15min)
- Memory usage & memory peak
- API response time
- Database size

### ⏱️ WordPress Cron
- Total jobs
- Stuck jobs
- Next scheduled run
- Cron enabled/disabled

### 📦 Storage
- Free disk space
- Upload directory size
- Disk usage percent

### 🔐 Security
- Failed logins (1h / 24h / week)
- Attacking IP addresses
- File editing disabled
- XML-RPC enabled

### 🐘 PHP & Logs
- Fatal errors
- Warnings
- Debug.log presence & size

### 🔄 Updates
- WordPress core updates
- Plugin updates
- Theme updates
- Total updates available

### 📉 SSL
- Days until expiration
- Certificate expired or not
- Issuer

Dependent items extract JSON data using **JSONPath**. Triggers are included for:
- PHP fatal errors
- Stuck cron jobs
- High disk usage
- Brute force attacks
- SSL expiration
- Slow performance

Graphs are also provided: global performance, storage, security, PHP errors, cron, and more.

---
## 🇬🇧 Macros
- `{$WP.URL}` : WordPress website URL
- `{$WEB.DOMAIN}` : Main domain
- `{$WP.API.KEY}` : wp-zabbix plugin API key

---
## 🇬🇧 License
This template is released under **GPL v3**. You may:
- modify it,
- redistribute it,
As long as the **original model is credited**.

