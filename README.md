# 🤖 TP1 : Déploiement d'un Portfolio Next.js avec Ansible et Semaphore UI

📄 **[Télécharger le rapport complet du TP1 (PDF)](./TP1_partie1.pdf)**

Ce dépôt contient l'Infrastructure as Code (IaC) pour automatiser le déploiement de l'application Next.js sur une machine virtuelle Ubuntu 24.04.

## 🛠️ Architecture et Technologies
*   **Serveur cible** : Ubuntu 24.04 (IP : `192.168.159.20`)
*   **Application** : Next.js (port 3000) gérée par **PM2**.
*   **Reverse Proxy** : **Nginx** (port 80).
*   **Orchestration** : **Semaphore UI** (via Docker).

---

## 🚀 1. Préparation et Configuration d'Ansible

### Installation d'Ansible
![Installation d'Ansible](captures/01-install-ansible.png)

### Création de la structure du projet
![Création de la structure](captures/02-structure-projet.png)

### Configuration d'Ansible (`ansible.cfg`)
![Configuration d'Ansible](./captures/03-ansible-cfg.png)

### Configuration de l'inventaire (`hosts.ini`)
![Inventaire](captures/04-inventory-hosts.png)

### Variables globales (`all.yml`)
![Variables globales](captures/05-group-vars.png)

---

## ⚙️ 2. Exécution du Playbook

### Test en mode Dry-run
Vérification des changements sans appliquer les modifications réelles.
![Test Dry-run](captures/06-dry-run.png)
![Test Dry-run](captures/06-dry-run1.png)


### Première exécution réelle
Déploiement complet de l'infrastructure.
![Exécution réelle](captures/07-execution-reelle.png)

### Vérifications post-déploiement
Statut du processus PM2 :
![Statut PM2](captures/08-pm2-status.png)

Statut du serveur Nginx :
![Statut Nginx](captures/09-nginx-status.png)

### L'application déployée
L'application Next.js est accessible via le navigateur sur l'IP du serveur.
![Application Portfolio](captures/10-portfolio-app.png)

---

## 🖥️ 3. Industrialisation avec Semaphore UI

### Lancement de Semaphore UI
Lancement du conteneur Docker de Semaphore.
![Lancement Semaphore](captures/11-docker-semaphore.png)

### Page de connexion Semaphore UI
![Connexion Semaphore](captures/12-semaphore-login.png)

### Création du projet
![Création du projet](captures/13-semaphore-project.png)

### Dashboard Semaphore UI
![Dashboard Semaphore](captures/14-semaphore-dashboard.png)

---

## 🔑 4. Configuration des objets Semaphore

### Ajout de la clé SSH pour le serveur cible :
![Clé SSH Serveur](captures/15-semaphore-ssh-key.png)

### Ajout de la clé SSH pour GitHub :
![Clé Git](captures/16-semaphore-git-key.png)

### Ajout du dépôt Git (`portfolio-repo`) :
![Dépôt Git](captures/17-semaphore-repo.png)

Configuration de l'inventaire (`prod-server`) :
![Inventaire Semaphore](captures/18-semaphore-inventory.png)

Configuration du groupe de variables (`portfolio-vars`) :
![Variables Semaphore](captures/19-semaphore-vars.png)

Création du modèle de tâche (`Deploy Portfolio`) :
![Task Template](captures/20-semaphore-template.png)

lancement :
![Task Template](captures/20-semaphore-template1.png)


---
*Réalisé par [Arij Belaid](https://github.com/arijbelaid)*
