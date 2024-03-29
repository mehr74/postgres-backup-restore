# Postgres backup and restore playground

The repository contains two postgres database `postgres-1` and `postgres-2`.
The database `postgres-1` has a table `usage` with some data in it. 
The purpose of this gig is to perform a backup of the `postgres-1` database 
and restore it to `postgres-2` database.


Here are the steps to perform the backup and restore:
```bash
docker-compose up -d
docker exec -it postgres-backup-restore-postgres-2-1 /bin/bash
(container)$ pg_dump -h postgres-1 -p 5432 -t usage -U postgres > dumpfile
(container)$ psql postgres -U postgres < dumpfile
```

At the end, the `postgres-2` database should have the same data as 
`postgres-1` database for table `usage`.