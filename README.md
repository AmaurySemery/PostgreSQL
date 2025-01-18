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

Connexion et authentification
sudo nano /etc/postgresql/14/main/postgresql.conf

sudo nano /etc/postgresql/14/main/pg_hba.conf

cf authentifcation methods sur la doc

sudo -i -u postgres psql

Pour lister les utilisateurs
\du

\password

Voir la doc pour la création d'utilisateur

sudo -i -u postgres createuser --interactive
fuan
n
y
n

\du

Utiliser pgAdmin pour l'interface graphique en mode web

sudo curl https://www.pgadmin.org/static/packages_pgadmin_org.pub | sudo apt-key add

sudo sh -c 'echo "deb [signed-by=/usr/share/keyrings/packages-pgadmin-org.gpg] https://ftp.postgresql.org/pub/pgadmin/pgadmin4/apt/$(lsb_release -cs) pgadmin4 main" > /etc/apt/sources.list.d/pgadmin4.list && apt update'

sudo apt install pgadmin4
sudo apt install pgadmin4-web
sudo /usr/pgadmin4/bin/setup-web.sh

http://127.0.0.1/pgadmin4

Pour restauter une DB

sudo -i -u postgres createdb -T template0 fuandataformation
sudo -i -u postgres psql
\l
sudo -i -u postgres createdb -T template0 fuandataformation
sudo -i -u postgres pg_restore -d fuandataformation /cheminabsolu/fuandataformation.pgdump
