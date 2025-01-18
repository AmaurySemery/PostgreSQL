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
