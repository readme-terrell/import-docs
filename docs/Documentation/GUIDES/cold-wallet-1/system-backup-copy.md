---
title: System Backup (DRAFT)
excerpt: ''
deprecated: false
hidden: true
metadata:
  title: ''
  description: ''
  robots: index
next:
  description: ''
---
This guide walks you through the process of backing up and restoring the Cold Wallet database using the Cold Wallet CLI.

## Prerequisites

Before you begin, ensure you have installed and can run the [Cold Wallet CLI Deployment ](https://wallet.docs.blockdaemon.com/docs/cold-wallet-cli-deployment).

## Backup & Restore

1. Run the Cold Wallet CLI installer with the command for your OS. <br/>

* **Linux** <br/>

```go
./coldwallet-cli-linux
```

* **macOS** <br/>

```go
./coldwallet-cli-darwin
```

2. Once launched, the CLI will display a list of commands for managing databases, keys, and presignatures:

```go
This CLI is used to manage the Blockdaemon cold wallet. It can generate
        configuration, run the cold wallet, and manage the cold wallet.

Usage:
  walletcli [command]

Available Commands:
  completion   Generate the autocompletion script for the specified shell
  config       Manage wallets' configurations.
  database     Manage MPC nodes' databases.
  help         Help about any command
  key          Manage MPC nodes' keys.
  presignature Presignatures are essential in MPC protocol. Each node must get hold of sufficient presignatures for the wallet to work.

Flags:
  -h, --help   help for walletcli

Use "walletcli [command] --help" for more information about a command.
```

### How to Backup

1. To back up the Cold Wallet database, run the following command.

```go
./coldwallet-cli-darwin database
```

2. This command will display database management options, such as `backup` or `restore` a database.

```go
/Manage MPC nodes' databases.

Usage:
  walletcli database [command]

Available Commands:
  backup      Backup the database of the node
  restore     Restore the database of the node

Flags:
  -h, --help   help for database

Use "walletcli database [command] --help" for more information about a command.
```

3. Select the node you want to back up. For example, to back up `node0`, run:

```go
./coldwallet-cli-darwin database backup --node-index 0
```

4. The backup file for `node0` will be saved in the `backup/backup` folder.

### How to Restore

> ❗️ Note
>
> Ensure that the container running the MPC node is stopped before restoring.

1. Run the `restore` command with the backup file name:

```go
./coldwallet-cli-darwin database restore --node-index 0 --backup-file <the backup file name>
```

2. Confirm the node is stopped by typing `YES`.
3. Once the restoration process is complete, the backup file will be removed.

<Support />
