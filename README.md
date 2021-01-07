# Description du dépôt Git demers/docker-postgresql-pgadmin

Ce conteneur contient:

- PostGreSQL 13.1
- PGAdmin 4 (administration web de PG)

Pour la construction de ce dépôt, nous nous sommes inspiré sur https://linuxhint.com/postgresql_docker/

# Comment le démarrer

```
git clone https://github.com/demers/docker-postgresql-pgadmin.git

cd docker-postgresql-pgadmin

docker-composer up -d
```

# Accès

Après le démarrage, on peut accéder sur le Web par la page

```
http://localhost:8080
```

Il faut utiliser le nom d'utilisateur est `admin@admin.admin` et le mot de passe est `secret`

# PGAdmin

Il est aussi possible d'utiliser l'application native PGAdmin https://www.pgadmin.org/

en utilisant le nom d'utilisateur d'administration `admin` et le mot de passe `secret`


