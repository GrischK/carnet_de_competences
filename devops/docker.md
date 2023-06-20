# Docker

> ❌ A travailler

> ✔️ Auto validation par l'étudiant

## 🎓 J'ai compris et je peux expliquer

- la création d'une image docker ✔️

  Une image Docker est un package autonome qui contient tout le nécessaire pour exécuter une application. Elle comprend le code, les bibliothèques, les dépendances et les configurations, le tout encapsulé dans un conteneur léger et portable.
C'est la capture à un instant de notre projet. Pour ce faire, il faut créer un fichier de configuration appelé Dockerfile, qui décrit les étapes pour construire l'image.

- l'exécution d'un container ✔️

  Un container est une instance de l'exécution d'une image Docker. On peut les surveiller par le biais du terminal ou du docker desktop.

- l'orchestration de containers avec docker-compose ✔️

  Pour orchestrer plusieurs containers en même temps, on utilise la commande 'docker-compose up'. Un fichier YAML docker-compose.yml décrit comment générer les containers.


## 💻 J'utilise

### Un exemple personnel commenté ✔️

```yaml
version: '3.8'

services:  # Définition des services

  database:  # Service "database"
    networks:  
      - my-network  # Le service est connecté au réseau "my-network"
    container_name: mysql  # Nom du conteneur
    image: mysql:5.7 
    command: --default-authentication-plugin=mysql_native_password  
    restart: always  
    environment:  # Variables d'environnement utilisées par le conteneur
      MYSQL_ROOT_PASSWORD: "root"  # Mot de passe root pour la base de données MySQL
    ports:  # Configuration des ports exposés par le conteneur
      - "3307:3306"  # Port 3306 du conteneur est mappé au port 3307 de l'hôte
    volumes:  # Configuration des volumes montés dans le conteneur
      - my-db:/var/lib/mysql  # Montage du volume "my-db" pour persister les données de la base de données
      - ./docker/database:/docker-entrypoint-initdb.d/  # Montage du répertoire local contenant les scripts d'initialisation

  backend:  # Service "backend"
    networks:  
      - my-network  # Le service est connecté au réseau "my-network"
    build:  # Configuration de la construction de l'image du conteneur
      context: ./  # Chemin du contexte de construction de l'image (dossier racine du projet)
    container_name: nestjs-app  # Nom du conteneur
    depends_on:  
      - database  # Le service dépend du service "database"
    restart: unless-stopped  
    ports:  # Configuration des ports exposés par le conteneur
      - "3000:3000"  # Port 3000 du conteneur est mappé au port 3000 de l'hôte
    tty: true  
    volumes:  # Configuration des volumes montés dans le conteneur
      - .:/app  # Montage du répertoire courant du projet dans le répertoire "/app" du conteneur

volumes:  # Définition des volumes
  my-db:  # Volume "my-db"

networks:  # Définition des réseaux
  my-network:  # Réseau "my-network"
    name: todolist  # Nom du réseau
    driver: bridge  
```

### Utilisation dans un projet ✔️

- [Projet Mapado](https://github.com/WildCodeSchool/2209-wns-adleman-mapado).
  Description : Projet de soutenance au Titre de Concepteur Développeur d'Applications

### Utilisation en production si applicable ❌ 

### Utilisation en environnement professionnel ✔️

Description : Utilisation de Docker sur différents projets professionnels, et dans certains POC (proof of concept)

## 🌐 J'utilise des ressources

### Titre

- [Site officiel Docker](https://docs.docker.com/get-started/02_our_app/).
  Documentation pour créer une image Docker
- [Article sur Docker](https://datascientest.com/docker-guide-complet).
  Guide complet sur Docker

## 🚧 Je franchis les obstacles

### Point de blocage ✔️

## 📽️ J'en fais la démonstration

- J'ai écrit un [tutoriel]() ❌ 
- J'ai fait une [présentation]() ❌ 
