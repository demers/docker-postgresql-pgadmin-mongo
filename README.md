# Description du dépôt Git demers/docker-postgresql-pgadmin

Ce conteneur contient:

- PostGreSQL 13.1
- PGAdmin 4 (administration web de PG)
- MongoDB

Pour la construction de ce dépôt, nous nous sommes inspiré sur https://linuxhint.com/postgresql_docker/ pour Postgres et https://medium.com/faun/managing-mongodb-on-docker-with-docker-compose-26bf8a0bbae3 pour MongoDB.

# Comment le démarrer

```
git clone https://github.com/demers/docker-postgresql-pgadmin.git

cd docker-postgresql-pgadmin

docker-composer up -d
```

# Accès

Après le démarrage, on peut accéder sur le Web à PGAdmin Web par la page

```
http://localhost:8080
```

Il faut utiliser le nom d'utilisateur est `admin@admin.admin` et le mot de passe est `secret`

# PGAdmin

Il est aussi possible d'utiliser l'application native PGAdmin https://www.pgadmin.org/

en utilisant le nom d'utilisateur d'administration `admin` et le mot de passe `secret`

# MongoDB Compass

Il est possible d'accéder à la base de données Mongo par l'application native
MongoDB Compass https://www.mongodb.com/try/download/compass

en utilisant l'accès suivant:

```
mongodb://mongo:mongo@127.0.0.1:27017/mongodb
```

Le nom d'utilisateur est `mongo` avec le mot de passe `mongo`.  La base de
donnée par défaut est `mongodb`


