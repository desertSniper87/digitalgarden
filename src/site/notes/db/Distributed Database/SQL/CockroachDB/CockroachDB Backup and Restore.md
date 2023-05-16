---
{"dg-publish":true,"permalink":"/db/distributed-database/sql/cockroach-db/cockroach-db-backup-and-restore/","dgPassFrontmatter":true}
---

## Links

1. [`BACKUP`](https://www.cockroachlabs.com/docs/v22.1/backup) statement to efficiently back up cluster's schemas and data to NFS
2. [`RESTORE`](https://www.cockroachlabs.com/docs/v22.1/restore) statement to efficiently restore schema and data as necessary. 


## Backup a cluster (To S3)

**Full Backup**
```sql
BACKUP INTO 's3://{BUCKET NAME}?AWS_ACCESS_KEY_ID={KEY ID}&AWS_SECRET_ACCESS_KEY={SECRET ACCESS KEY}' AS OF SYSTEM TIME '-10s';
```
## Backup database/s

**Requires an enterprise license**

```sql
BACKUP DATABASE bank, employees INTO 's3://{BUCKET NAME}?AWS_ACCESS_KEY_ID={KEY ID}&AWS_SECRET_ACCESS_KEY={SECRET ACCESS KEY}' AS OF SYSTEM TIME '-10s';
```

## Perform Core backup and restore

### Backup

```bash
cockroach dump <database_name> <flags> > backup.sql
```

### Restore

```bash
cockroach sql --database=[database name] < backup.sql
```



## Scheduling automated backups


### Fully automated backups

```sql
CREATE SCHEDULE core_schedule_label
  FOR BACKUP INTO 's3://{BUCKET NAME}/{PATH}?AWS_ACCESS_KEY_ID={KEY ID}&AWS_SECRET_ACCESS_KEY={SECRET ACCESS KEY}'
    RECURRING '@daily'
    FULL BACKUP ALWAYS
    WITH SCHEDULE OPTIONS first_run = 'now';
```


## Incremental Backups

If cluster grows too large for nightly [full backups](https://www.cockroachlabs.com/docs/v22.1/take-full-and-incremental-backups#full-backups),

1. less frequent full backups (e.g., weekly) 
2. Nightly incremental backups. 

Incremental backups are storage efficient and faster than full backups for larger clusters.

```sql
BACKUP INTO LATEST IN '{collectionURI}';
```

This will add the incremental backup to the default `/incrementals` directory at the root of the backup collection's directory.


### Incremental Backups from existing full backups

### Backup collections

1. A _backup collection_ defines a set of backups and their metadata
2. The collection can contain multiple full backups and their subsequent [incremental backups](https://www.cockroachlabs.com/docs/v22.1/take-full-and-incremental-backups#incremental-backups).


#### View Backups at collection URI

```sql
SHOW BACKUPS IN 's3://{bucket name}/{path}?AWS_ACCESS_KEY_ID={placeholder}&AWS_SECRET_ACCESS_KEY={placeholder}';
```

#### Restore from Collection URI

```sql
RESTORE FROM LATEST IN '{collectionURI}';
```


## Reference

1. [Backup and Restore Overview | CockroachDB Docs](https://www.cockroachlabs.com/docs/stable/backup-and-restore-overview.html)
2. [Take Full and Incremental Backups | CockroachDB Docs](https://www.cockroachlabs.com/docs/v22.1/take-full-and-incremental-backups)
	1. [incremental backup](https://www.cockroachlabs.com/docs/v22.1/take-full-and-incremental-backups#incremental-backups)
	2. [collections](https://www.cockroachlabs.com/docs/v22.1/take-full-and-incremental-backups#backup-collections)
3. [Use Cloud Storage for Bulk Operations](https://www.cockroachlabs.com/docs/v22.1/use-cloud-storage-for-bulk-operations).
4. [CREATE SCHEDULE FOR BACKUP | CockroachDB Docs](https://www.cockroachlabs.com/docs/stable/create-schedule-for-backup.html)[]()
5. [Protect Your Data Using CockRoach Backups - Justuno](https://www.justuno.com/blog/protect-your-data-using-cockroach-backups/)