
# Template Zabbix : StaticWebsite-PK33PROD-SansScenarioWeb

## 🇫🇷 Description du template
Ce template Zabbix permet la supervision complète d’un site web statique (HTML/CSS) en utilisant uniquement des éléments réseau natifs de Zabbix. Il fonctionne sous Zabbix **7.4.6**.

⚠️ **Aucun scénario web n’est inclus** : Zabbix 7.4.6 ne permet pas l’export des scénarios web (HTTP tests), ce modèle est donc conçu exclusivement à partir d’items simples (SIMPLE CHECK).

---

## 🇫🇷 Installation
Voici les étapes pour installer ce template dans votre instance Zabbix :

1. **Ouvrez l’interface Zabbix** et connectez-vous avec un compte disposant des droits d’administration.
2. Accédez à : **Configuration → Templates**.
3. Cliquez sur **Import**.
4. Sélectionnez le fichier `StaticWebsite-PK33PROD-SansScenarioWeb.yaml`.
5. Laissez les options par défaut (ou cochez *« Créer des éléments manquants »* si nécessaire).
6. Cliquez sur **Import** pour finaliser.
7. Associez ensuite le template à un hôte : **Configuration → Hosts → (Votre hôte) → Templates → Link Template**.

Le template est maintenant actif et les premiers résultats apparaîtront après quelques minutes.

---

## 🇫🇷 Fonctionnement
Le template effectue les contrôles suivants :
- Vérification de la disponibilité du port **HTTPS (443)**
- Mesure du temps de réponse (ms) via `net.tcp.service.perf`
- Déclenchement d’alertes si :
  - Le port HTTPS devient injoignable
  - Le temps de réponse dépasse **1.5s** (Alerte AVERAGE)
  - Le temps de réponse dépasse **3s** (Alerte HIGH)
- Mise à disposition de plusieurs graphiques : santé HTTPS, performance globale, etc.

### Macros disponibles
- `{$WEB.DOMAIN}` : Nom de domaine
- `{$WEB.URL}` : URL complète (HTTPS obligatoire)
- `{$DOMAIN.SLA}` : Valeur personnalisée pour vos SLA

### Licence
Ce template est distribué sous licence **GPL v3**. Vous êtes libre :
- de le modifier,
- de le redistribuer,
à condition de **citer ce modèle original**.

---

# 🇬🇧 Template description
This Zabbix template provides monitoring for a static HTML/CSS website using only native Zabbix network checks. It is fully compatible with **Zabbix 7.4.6**.

⚠️ **No web scenario is included**: Zabbix 7.4.6 does not allow exporting web scenarios (HTTP tests), therefore this template relies exclusively on SIMPLE CHECK items.

---

## 🇬🇧 Installation
To install this template in your Zabbix instance:

1. Open the **Zabbix interface** and log in with an admin‑level account.
2. Go to **Configuration → Templates**.
3. Click **Import**.
4. Select the file `StaticWebsite-PK33PROD-SansScenarioWeb.yaml`.
5. Keep default import options (or enable *“Create missing items”* if needed).
6. Click **Import** to complete.
7. Attach the template to a host: **Configuration → Hosts → (Your host) → Templates → Link Template**.

The template will start collecting data within a few minutes.

---

## 🇬🇧 How it works
The template performs the following checks:
- Availability of the **HTTPS (443)** port
- Response time measurement (ms) using `net.tcp.service.perf`
- Triggering alerts when:
  - HTTPS port becomes unreachable
  - Response time exceeds **1.5s** (AVERAGE severity)
  - Response time exceeds **3s** (HIGH severity)
- Several graphs are included: HTTPS health, global performance, etc.

### Available macros
- `{$WEB.DOMAIN}`: Domain name
- `{$WEB.URL}`: Full URL (HTTPS required)
- `{$DOMAIN.SLA}`: Custom SLA tag

### License
This template is distributed under the **GPL v3 license**. You are free to:
- modify it,
- redistribute it,
as long as the **original model is credited**.

