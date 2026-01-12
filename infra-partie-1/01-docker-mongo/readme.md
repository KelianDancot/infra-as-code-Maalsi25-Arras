# 📦 TP – MongoDB en local avec Docker

## 🎯 Objectif
L’objectif de ce TP est de mettre en place une base de données **MongoDB en local** à l’aide de **Docker** et **Docker Compose**.  
Cette solution permet de déployer MongoDB rapidement, sans installation directe sur la machine hôte, tout en garantissant la **persistance des données**.

---

## 🧰 Outils utilisés
- Ubuntu  
- Docker  
- Docker Compose  
- MongoDB (image officielle Docker)

---

## 1️⃣ Installation de Docker

Avant de commencer, j’ai vérifié que Docker était bien installé sur ma machine :

```bash
docker --version
docker compose version
Docker étant déjà installé, j’ai pu continuer le TP.

---

## 2️⃣ Création du fichier Docker Compose
J’ai créé un dossier de travail, puis un fichier docker-compose.yml :
bash
Copier le code
mkdir mongo-docker
cd mongo-docker
nano docker-compose.yml
Ce fichier permet de configurer et lancer le conteneur MongoDB.

---

## 3️⃣ Configuration de MongoDB
Contenu du fichier docker-compose.yml :
yaml
Copier le code
version: "3.9"

services:
  mongo:
    image: mongo:7
    container_name: mongo
    restart: always
    ports:
      - "27017:27017"
    environment:
      MONGO_INITDB_ROOT_USERNAME: root
      MONGO_INITDB_ROOT_PASSWORD: example
    volumes:
      - ./db_data:/data/db
Explications
image : image officielle MongoDB
ports : accès à MongoDB via le port 27017
environment : identifiants administrateur
volumes : persistance des données

---

## 4️⃣ Lancement du conteneur MongoDB
Le conteneur est lancé avec la commande suivante :

bash
Copier le code
docker compose up -d
Vérification du conteneur :

bash
Copier le code
docker ps

---

## 5️⃣ Connexion au shell MongoDB
Connexion directe au conteneur MongoDB :

bash
Copier le code
docker exec -it mongo mongosh -u root -p example
📸 Connexion et insertion de données :
image.png
---

## 6️⃣ Création d’une base et insertion de données
=======
Dans le shell MongoDB :

js
Copier le code
use testdb
db.users.insertOne({ name: "Alice", age: 25 })
db.users.find()
Une base MongoDB existe uniquement après l’insertion d’au moins un document.

---

## 7️⃣ Connexion via chaîne MongoDB
=======
Connexion via une chaîne MongoDB :

text
Copier le code
mongodb://root:example@localhost:27017
Création d’une base dédiée au TP :

js
Copier le code
show dbs
use tp_mongo
db.test.insertOne({ message: "TP OK" })
db.test.find()
📸 Base tp_mongo fonctionnelle :
image2e.png
---

## 8️⃣ Bonnes pratiques
Utilisation de volumes Docker pour conserver les données
Possibilité de modifier les identifiants MongoDB
Docker permet une installation propre et rapide
Solution idéale pour les environnements de développement

✅ Conclusion
Ce TP m’a permis de comprendre comment déployer MongoDB en local à l’aide de Docker.
Docker Compose simplifie la configuration et le lancement des services, tout en garantissant un environnement stable et reproductible.

📚 Ressources
https://docs.docker.com/
https://www.mongodb.com/docs/

yaml
Copier le code

---

### ✅ À FAIRE AVANT DE PUSH SUR GIT
✔️ Vérifie que tes images sont bien nommées :
image.png
imag2e.png

yaml
Copier le code

✔️ Qu’elles sont à la racine du dépôt (ou adapte le chemin)

---

Si tu veux, je peux aussi :
- 🧑‍🏫 adapter le niveau **exact prof / BTS / BUT / Licence**
- 📄 faire un **README encore plus court**
- 🚀 t’aider à faire un **commit Git propre**

Dis-moi 😄