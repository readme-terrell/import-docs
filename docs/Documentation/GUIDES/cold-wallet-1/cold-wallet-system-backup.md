---
title: System Backup
excerpt: ''
deprecated: false
hidden: false
metadata:
  title: ''
  description: ''
  robots: index
next:
  description: ''
---
## Overview

System backups are set to occur every hour by default. You can customize this schedule by changing the cron environment variable found in the `docker-compose.yaml` file under `backup/environment/cron`. The backup archives are stored in the `/backup` folder.

The backup process protects the cold wallet's configuration and the database's state. However, it does not include the application software binaries. If a restore is required in a new environment, a new cold wallet installation should be completed before performing the restore from the backup.

> 📘 Note:
>
> After resharing the key materials, the previous database backup files can no longer be used with the new batch of database backup files, i.e. the database backup files have to be always restored in sync with each other (from the same batch).

## Ad-Hoc Backup

To perform an ad-hoc backup, follow the steps below:

1. Open a terminal, and use the following command to stop all the services to ensure memory is flushed to disk:

```
docker compose stop
```

2. Initiate the ad-hoc backup of the state to the `/backup` folder:

```
docker compose run backup backup.sh
```

3. Start the services back up again by using the following command:

```
docker compose start
```

## Ad-Hoc Restore

> ❗️ Important:
>
> Please be sure to encrypt the zip file (.tgz) when saving this to external media.

> 📘 Note:
>
> If restoring to a new environment, a **new** cold wallet installation should be completed first.

To perform an ad-hoc restore, follow the steps below:

1. Open a terminal, and use the following command to stop all the services:

```
docker compose stop
```

2. Initiate the ad-hoc restore and specify the desired file name from the `/backup/` folder:

```
docker compose run backup restore.sh backup_<timestamp>.tgz
```

3. Start the services back up again by using the following command:

```
docker compose start
```

<Support />
