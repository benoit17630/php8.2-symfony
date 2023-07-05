# Containeur docker pour symfony et php 8.2

## 1. <a name= 'sommaire'></a>Sommaire

- [1. Sommaire](#sommaire)
- [2. Prérequis](#Prérequis)
- [3. Installation](#installation)
- [4. Utilisation](#utilisation)
- [5. Base de donnée](#base-de-donnée)
- [6. Maildev](#maildev)




## 2. <a name= 'Prérequis'></a>Prérequis
    Il faut avoir installé docker et docker-compose sur votre machine.
    Pour installer docker et docker-compose sur votre machine, vous pouvez suivre ce lien: https://docs.docker.com/compose/install/
    Pour vérifier que docker et docker-compose sont bien installés sur votre machine, vous pouvez taper les commandes suivantes:
    docker -v
    docker-compose -v
    Vous devez avoir les versions de docker et docker-compose installées sur votre machine.
    
## 3. <a name= 'Installation'></a>Installation
    Pour installer le conteneur docker, vous pouvez taper la commande suivante:
    docker-compose up -d
    Pour vérifier que le conteneur est bien installé, vous pouvez taper la commande suivante:
    docker ps
    Vous devez voir le conteneur docker installé sur votre machine.

## 4. <a name= 'Utilisation'></a>Utilisation
    Pour entrer dans le conteneur, vous pouvez taper la commande suivante:
    docker exec -it www bash
    Vous devez être dans le conteneur.
    Pour créer un projet symfony, vous pouvez taper la commande suivante:
    symfony new project --webapp
    Vous devez avoir un dossier project.
    Pour arrêter le conteneur, vous pouvez taper la commande suivante:
    docker-compose down
    Pour voir la page d'accueil de symfony, vous pouvez taper l'url suivante:
    http://localhost:8000
    

## 5. <a name = 'Base de donnée'></a>Base de donnée
    Pour voir la base de donnée, vous pouvez taper l'url suivante:
    http://localhost:8081

    Une fois dans le projet sur votre editeur de code , vous pouvez modifier le fichier .env :
    DATABASE_URL="mysql://app:!ChangeMe!@database:3306/app?serverVersion=8&charset=utf8mb4"
    Pour créer la base de donnée, vous pouvez taper la commande suivante:
    php bin/console doctrine:database:create
    ou
    symfony console doctrine:database:create

## 6. <a name = 'Maildev'></a>Maildev
    Pour voir les mails envoyés, vous pouvez taper l'url suivante:
    http://localhost:1080
    dans le fichier .env, vous pouvez modifier les lignes suivantes:
    MAILER_DSN=smtp://maildev:25



