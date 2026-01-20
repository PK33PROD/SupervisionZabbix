# 📡 Freebox Basic Monitoring – Template Zabbix

Ce template Zabbix fournit un **ensemble complet de vérifications essentielles** pour surveiller l’état et la réactivité d’une Freebox. Il a été conçu pour offrir un **suivi simple, fiable et efficace**, sans dépendre d’API complexes ou d’intégrations avancées.

---

## 🎯 Objectifs du template

- Vérifier la disponibilité réseau de la Freebox  
- Mesurer la latence ICMP (ping)  
- Détecter la perte de connectivité  
- Surveiller l’interface d’administration HTTP  
- Alerter en cas de dégradation des performances ou d’indisponibilité  

---

## 🧩 Éléments surveillés

### 1. Ping (Disponibilité ICMP)
- **Clé :** `icmpping[{$FREEBOX.HOST},3,20,56,1000]`
- Vérifie si la Freebox répond au ping  
- **Retour :**  
  - `1` → En ligne  
  - `0` → Hors ligne  
- **Trigger :** Freebox-serveur ne répond plus au ping *(DISASTER)*

---

### 2. Temps de réponse ICMP
- **Clé :** `icmppingsec[{$FREEBOX.IP},3,20,56,1000,avg]`
- Mesure la latence moyenne en millisecondes  
- **Trigger :** Latence ICMP > 50 ms *(AVERAGE)*

---

### 3. Disponibilité de l’interface HTTP
- **Clé :** `net.tcp.service[http,{$FREEBOX.HOST},80]`
- Vérifie si l’interface Freebox OS répond  
- **Trigger :** Interface HTTP inaccessible *(HIGH)*

---

### 4. Temps de réponse HTTP
- **Clé :** `net.tcp.service.perf[http,{$FREEBOX.HOST},80]`
- Mesure le temps de réponse HTTP en millisecondes  
- **Trigger :** Temps de réponse HTTP > 2 s *(AVERAGE)*

---

## 🏷️ Macros disponibles

| Macro | Description | Valeur par défaut |
|-------|-------------|-------------------|
| `{$FREEBOX.HOST}` | Nom DNS de la Freebox | `mafreebox.freebox.fr` |
| `{$FREEBOX.IP}` | Adresse IP locale | `192.168.1.254` |
| `{$HTTP.INTERVAL}` | Intervalle HTTP | `60` |
| `{$PING.INTERVAL}` | Intervalle ICMP | `60` |

---

## 📊 Graphiques inclus

- **Temps de réponse HTTP**  
- **Temps de réponse ICMP**

---

## 🗂️ Value Maps

### Ping (icmp)
- `0` → Hors ligne  
- `1` → En ligne  

### HTTP Status
- `200` → OK  
- `404` → Non trouvé  
- `500` → Erreur serveur  

---

## 🚀 Installation

1. Importer le fichier YAML dans Zabbix  
2. Associer le template à un hôte  
3. Ajuster les macros si nécessaire  
4. Vérifier l’accessibilité de la Freebox  

## 📜 Licence et réutilisation
Ce template est distribué sous licence GPL v3.0.
Vous êtes libre de l’utiliser, le modifier et le redistribuer, y compris dans des projets publics ou commerciaux, tant que les conditions suivantes sont respectées :
- La licence GPL v3.0 doit être conservée dans toute redistribution.
- Toute publication publique (GitHub, blog, site web, dépôt open source, etc.) doit mentionner l’auteur original : Noah Maillet.
- Les versions modifiées doivent également être publiées sous licence GPL v3.0.
- Cette licence garantit que le template reste libre, améliorable et partageable par toute la communauté.