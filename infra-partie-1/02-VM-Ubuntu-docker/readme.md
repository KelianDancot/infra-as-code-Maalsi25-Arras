# 🖥️ ATELIER 2 – Mise en place d’une VM et d’un conteneur Docker

## 🎯 Objectif
L’objectif de cet atelier est de mettre en pratique les notions de virtualisation et de conteneurisation.  
Il s’agit de créer une **machine virtuelle (VM)** avec VirtualBox, puis d’y déployer un **conteneur Docker** exécutant une application web.

---

## 🧰 Outils utilisés
- VirtualBox  
- Ubuntu Server  
- Docker  
- Image Docker Nginx  

---

## 1️⃣ Installation de VirtualBox

J’ai téléchargé VirtualBox depuis le site officiel :  
https://www.virtualbox.org/

L’installation a été réalisée en suivant les instructions par défaut adaptées à mon système.

---

## 2️⃣ Création de la machine virtuelle

Dans VirtualBox, j’ai créé une nouvelle machine virtuelle avec les paramètres suivants :

- **Nom** : UbuntuDev  
- **Type** : Linux  
- **Version** : Ubuntu (64-bit)  
- **Mémoire RAM** : 2 Go  
- **Processeur** : 1 CPU  

---

## 3️⃣ Configuration du disque dur virtuel

Lors de la création de la VM, j’ai configuré le disque dur virtuel :

- **Type de disque** : VDI (VirtualBox Disk Image)  
- **Allocation** : Dynamiquement alloué  
- **Taille** : 20 Go  

Ce choix permet d’économiser de l’espace disque sur la machine hôte.

---

## 4️⃣ Installation du système d’exploitation

J’ai téléchargé l’image ISO **Ubuntu Server** depuis le site officiel d’Ubuntu.  
Au démarrage de la VM, j’ai sélectionné cette image ISO et suivi les étapes d’installation :

- Choix de la langue  
- Configuration du clavier  
- Création d’un utilisateur  
- Installation standard du système  

Une fois l’installation terminée, la VM démarre correctement sur Ubuntu Server.

---

## 5️⃣ Configuration réseau de la VM

La carte réseau de la VM est configurée en mode **NAT**, ce qui permet à la machine virtuelle d’accéder à Internet via la machine hôte.

Ce mode est suffisant pour installer des paquets et utiliser Docker.

---

## 6️⃣ Installation de Docker dans la VM

Sur la machine virtuelle Ubuntu, j’ai installé Docker avec les commandes suivantes :

```bash
sudo apt update
sudo apt install -y docker.io docker-compose-plugin
sudo systemctl enable docker
sudo systemctl start docker

docker --version

---

## 7️⃣ Déploiement d’un conteneur Nginx

Pour tester Docker, j’ai lancé un conteneur Nginx :

docker run -d -p 80:80 --name nginx-test nginx

---

8️⃣ Vérification du fonctionnement

Depuis un navigateur web, j’ai accédé à l’adresse IP de la machine virtuelle :

http://IP_DE_LA_VM