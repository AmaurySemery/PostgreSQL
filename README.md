sudo apt install postgresql postgresql-client
pgrep -u postgres -fa

Pour se connecter à la base
sudo -i -u postgres psql

Le ; permet de lancer la commande SQL

\e permet de choisir un éditeur pour modifier la précédente requête
\q pour quitter postgre
\? pour l'invite d'aide
\l pour lister mes bases de données

CREATE DATABASE test;

Pour se connecter à la base de données
\c test
Accéder à la liste des tables
\dt

Pour revenir à l'administrateur postgres
\c postgres

DROP DATABASE test;

sudo apt install postgresql-contrib

Pour contrôler le service (le démarrer, l'arrêter, le redémarrer, etc.)
pg_ctl

Script pour gérer le service
find /usr/lib/postgresql/ -name pg_ctl

Pour obtenir les chemins importants
pgrep -u postgres -fa
/var/lib/postgresql/14/main

Fichier de config
/etc/postgresql/14/main/postgresql.conf

sudo su
mm
ll
find /usr/lib/postgresql/ -name oid2name
sudo -i -u postgres /usr/lib/postgresql/14/bin/oid2name
exit

sudo -i -u postgres psql

Pour trouver répertoire où se trouvent les bases de données
SELECT current_setting('cluster_name'), current_setting('server_version');
ou
show cluster_name;
ou
SELECT name, setting FROM pg_settings WHERE name= 'cluster_name';

select oid, datname from pg_database;
