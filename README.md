# INSTALLATION DE L'APPLICATION WEB

Connectez-vous en SSH à votre serveur web via la commande suivante (remplacez **adresse-ip-publique** par l’adresse IP publique de votre serveur) :

```
ssh -i "nuumfactory-ec2-key-pair.pem" ec2-user@adresse-ip-publique
```

## Configuration des paramètres de connexion à la base de données

Créez le repertoire inc dans /var/www/ et placez-vous dedans :

```
cd /var/www
mkdir inc
cd inc
```

Dans le répertoire /var/www/inc/, créez le fichier **dbinfo.inc** et insérez-y le contenu suivant en remplaçant **db_instance_enpoint** par l’endpoint de votre base de données (ne pas inclure le port) et XX par votre digit :

```
<?php
define('DB_SERVER', 'db_instance_endpoint');
define('DB_USERNAME', 'dbadmin');
define('DB_PASSWORD', 'dbadminpassword');
define('DB_DATABASE', 'nuumfactorydbXX');
?>
```

Sauvegardez et fermez le fichier dbinfo.inc.

Ce fichier sera utilisé par l’application web pour récupérer les informations de connexion à votre base de données avant de s’y connecter.

## Configuration de l'application

Placez-vous dans le répertoire /var/www/html, créez le fichier **lab.php** et insérez-y le contenu du fichier du même nom que vous avez reçu par mail.

## Test de l'application

- Accédez à l’application depuis votre navigateur favori via l’adresse suivante (en remplaçant **lb-dns-name** par le DNS Name de votre load-balancer) : http://lb-dns-name/lab.php

- Renseignez un nom quelconque dans le champ **NAME**, une adresse mail quelconque dans le champ **ADDRESS** et cliquez sur **Add Data**

- Un tableau apparaît avec les informations que vous venez de soumettre

**Félicitations ! Votre application web est opérationnelle :)**