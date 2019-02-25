# Crontab

!!! important
    * Try to use /etc/cron.d/ files instead of crontab -e 
    * Stagger backup over time


## Frequency
```bash
* * * * * 		  Each minute
45 4 * * *  		  Each day at 4:45
59 23 31 12 * *   	  One minute before the end of year
```

## Backup folder
> Optimal backup of folders in tgz archive without swap during backup
```bash
* * * * * root nocache -n 2 tar -czf <destination_path>/<file_name>_`date +\%Y\%m\%d`.tgz <path_to_compress> ; echo 1 > /proc/sys/vm/drop_caches ; echo "end" > /dev/null
```

## Backup database inside Docker container
> Optimal backup of folders in tgz archive without swap during backup
```bash
* * * * * root docker exec <container_name> <database_backup_command> | gzip > <destination_path>/<file_name>_`date +\%Y\%m\%d`.sql.gz
```
Examples:
* MySQL database
```bash
* * * * * root docker exec atlassian-mysql /usr/bin/mysqldump --single-transaction --skip-lock-tables --max_allowed_packet=64M -ubackup -hlocalhost bitbucketdb | gzip > /u1/backup/atlassian-mysql/bitbucketdb_dump_`date +\%Y\%m\%d`.sql.gz
```

* Postgres database
```bash
* * * * *  root docker exec --user postgres atlassian-postgres pg_dump bamboo | gzip > /u1/backup/atlassian-postgres/bitbucketdb_dump_`date +\%Y\%m\%d`.sql.gz
```

## Automatic Cleanup of old backups
```bash
* * * * * root find <root_folder> -mtime +6 -exec rm -f {} \; > /dev/null
```
