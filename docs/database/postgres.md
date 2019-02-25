# PostgreSQL

## Connect to PSQL client
```bash
psql postgres
psql -U <user> -h <hostname> postgres
```

## Users operations
### List Users
```bash
postgres=# \du
```

### Add User
```bash
# TODO
```

### Set password for user
```bash
postgres=# \password user
postgres=# [Enter password]
postgres=# \q
```

### Delete User
```bash
postgres=# DROP ROLE [USER_NAME];
```

## Database operations

### List Databases
```bash
postgres=# \list
postgres=# \l
```

### List tables in current database
```bash
postgres=# \dt
```

### Delete database
```bash
postgres=# DROP DATABASE [IF EXISTS] <databasename>;
```
!!! warning
    If the following message occurs:
    ```bash
    ERROR:  database "databasename" is being accessed by other users
    DETAIL:  There are N other sessions using the database.
    ```
    
    Execute the following command to drop database connections
    ```bash
    SELECT pg_terminate_backend(pg_stat_activity.pid)
    FROM pg_stat_activity
    WHERE pg_stat_activity.datname = '<databasename>'
      AND pid <> pg_backend_pid();
    ```

## Configuration file

### Get config file path
```bash
postgres=# show hba_file;
```
