## How to migrate from SQLite to MySQL

The default storage system of the internal data of Linkurious is SQLite. We can migrate the database to MySQL as follows.

1) Export the SQLite database to a file:

```sqlite3 ./linkurious-linux/data/server/database.sqlite .dump > export.sql```

2) Load the exported database back into MySQL:

```mysql -u myMysqlUser -p -h localhost linkurious < export.sql```