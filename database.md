# Sql
| Base SQL       | Port par défaut | Connexion de base                           |
|----------------|----------------|--------------------------------------------|
| PostgreSQL     | 5432           | `psql -h host -p 5432 -U user -d nomdb`   |
| MySQL / MariaDB| 3306           | `mysql -h host -P 3306 -u user -p`        |
| SQLite         | N/A            | `sqlite3 nomdb.sqlite`                     |
| SQL Server     | 1433           | `sqlcmd -S server,1433 -U user -P password`|

| Action                   | PostgreSQL                  | MySQL / MariaDB           | SQLite                  | SQL Server                       |
|--------------------------|----------------------------|---------------------------|------------------------|---------------------------------|
| Lister les bases         | `\l`                       | `SHOW DATABASES;`         | `.databases`           | `SELECT name FROM sys.databases;`|
| Sélectionner la base     | `\c nomdb`                 | `USE nomdb;`              | N/A                     | `USE nomdb;`                     |
| Lister les tables        | `\dt`                       | `SHOW TABLES;`            | `.tables`              | `SELECT name FROM sys.tables;`  |
| Lire les données         | `SELECT * FROM nomtable;`   | `SELECT * FROM nomtable;` | `SELECT * FROM nomtable;` | `SELECT * FROM nomtable;`       |
