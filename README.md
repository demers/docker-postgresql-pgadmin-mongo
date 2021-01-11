# Description du dépôt Git demers/docker-postgresql-pgadmin-mongo

Ce conteneur contient:

- PostGreSQL 13.1
- PGAdmin 4 (administration web de PG)
- MongoDB

Pour la construction de ce dépôt, nous nous sommes inspiré sur https://linuxhint.com/postgresql_docker/ pour Postgres et https://medium.com/faun/managing-mongodb-on-docker-with-docker-compose-26bf8a0bbae3 pour MongoDB.

# Comment le démarrer

## Préalables

Vous devez avoir sur votre système:

- Windows Pro et Education (si vous êtes sous Windows)
- (optionnel) Linux (meilleur choix que Windows pour Docker)
- Chocolatey (si vous êtes sous Windows 10)
- Docker 17+
- Docker compose 2+
- Au moins 1 Go d'espace disque
- Désactiver votre antivirus durant l'installation
- Désactiver votre parefeu durant l'installation

## Comment installer Docker et Docker-compose sous Windows

ATTENTION: Vous devez avoir Windows PRO ou Education.  Sinon, faites le passage à PRO
par exemple, voir cette méthode https://www.lifewire.com/upgrade-windows-10-home-to-pro-4178259

Vous devez vous assurer que l'option de virtualisation dans votre BIOS est bien
activée.

Il faut d'abord activer Hyper-V.  Voir https://docs.microsoft.com/en-us/virtualization/hyper-v-on-windows/quick-start/enable-hyper-v ou https://www.poweronplatforms.com/enable-disable-hyper-v-windows-10-8/

Il suffit d'exécuter la commande Powershell suivante:

```
Enable-WindowsOptionalFeature -Online -FeatureName Microsoft-Hyper-V -All
```

Il faut redémarrer l'ordinateur après.

On installe Docker en suivant les étapes de: https://runnable.com/docker/install-docker-on-windows-10

On installe Chocolatey par les étapes suivantes: https://chocolatey.org/install
(redémarrer votre console PS)

On installe Git par la commande suivante:

```
choco install git
```

On installe Docker-compose en suivant les étapes de: https://docs.docker.com/compose/install/#install-compose
(section Windows Server est le plus rapide)

On active la commande SSH en suivant les étapes décrites dans ce guide: https://www.howtogeek.com/336775/how-to-enable-and-use-windows-10s-built-in-ssh-commands/

## Comment installer ce projet Docker sur votre ordinateur

Vous devez ouvrir une console Bash (pour Linux) ou Powershell (pour Windows) et exécuter:


```
git clone https://github.com/demers/docker-postgresql-pgadmin.git

cd docker-postgresql-pgadmin

docker-composer up -d
```

Si vous êtes sous Linux, il se peut que vous aillez à modifier le fichier
docker-compose.yml pour décommenter la ligne suivante:

```
  # network_mode: "host"
```

Pour arrêter temporairement le conteneur (par exemple, à la fin de votre
travail), on tape:

```
docker-compose stop
```

On redémarre le conteneur arrêté (pour reprendre vos travaux) par:

```
docker-compose start
```

On détruit le conteneur par:

```
docker-compose down
```

# Accès

Après le démarrage, on peut accéder sur le Web à PGAdmin Web par la page

```
http://localhost:8080
```

Il faut utiliser le nom d'utilisateur est `admin@admin.admin` et le mot de passe est `secret`

# Logiciel console PSQL

Il est possible d'utiliser l'application console native `psql` qui est installé déjà dans le conteneur Postgres.

Voici comment y accéder à l'intérieur du conteneur:

```
docker exec -ti postgres  /usr/bin/psql postgres admin
```

Si vous êtes sous Linux, vous pouvez installer le paquetage
`postgresql-client-12` pour obtenir la commande `psql`.  On accède alors à la
base de données par la commande suivante:

```
psql -h localhost postgres admin
```

# MongoDB Compass

Il est possible d'accéder à la base de données Mongo par l'application native
MongoDB Compass qu'on peut télécharger ici: https://www.mongodb.com/try/download/compass

en utilisant l'accès suivant:

```
mongodb://mongo:mongo@127.0.0.1:27017/mongodb
```

Le nom d'utilisateur est `mongo` avec le mot de passe `mongo`.  La base de
donnée par défaut est `mongodb`


