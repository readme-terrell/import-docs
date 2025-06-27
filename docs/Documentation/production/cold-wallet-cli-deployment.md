---
title: Cold Wallet CLI Deployment (draft)
excerpt: ''
deprecated: false
hidden: true
metadata:
  title: Cold Wallet CLI Deployment
  description: ''
  image: >-
    https://files.readme.io/fc827c59cd8dc52a4c413de2836fe5bf05442f73452fe54247aaf1acf0ec9bea-metadata.png
  robots: index
next:
  description: ''
---
This guide provides instructions for setting up and running the Cold Wallet CLI. This process is compatible with both macOS and Linux.

## Prerequisites

Before you begin, make sure you have the following:

* Docker (Version 25 or higher)
* Golang
* Public key which you can get from [Emergency Recovery System (ERS)](https://wallet.docs.blockdaemon.com/docs/back-up-and-emergency-recovery)

## Step 1. Install Docker

Docker is required to run the Cold Wallet. If Docker isn’t installed on your system, follow these steps:

1. Download and install Docker by following the instructions for your operating system: [Get Docker](https://docs.docker.com/get-docker/).
2. Verify the installation by running the following command:

```go
docker version
```

> 🚧 Note:
>
> Make sure the output shows Docker version 25 or higher.

## Step 2. Install the Cold Wallet CLI

1. Open your terminal.
2. Go to your desired installation directory (e.g., your home directory), then create a folder for the Cold Wallet:

```shell
cd ~/
mkdir -p coldwallet
```

3. Contact your sales associate or technical representative to get the Cold Wallet installer or a one-time presigned URL.
4. Install the Cold Wallet: <br /><br />
   * **If you received an installer**: Right-click the `coldwallet.tar` file and select **Copy**. Then, extract it to the Cold Wallet directory by pasting the file path: <br /><br />
   ```shell
   tar -xf <paste path> -C coldwallet
   ```
   * **If you received a presigned URL:** Download and extract the `coldwallet.tar` file into the Cold Wallet directory: <br /><br />
   ```shell
   curl -o coldwallet.tar "<presigned URL>"
   ```
5. Change to the Cold Wallet directory:

```go
cd coldwallet
```

## Step 3. Run the Cold Wallet CLI

The Cold Wallet CLI configures the environment and sets up Docker containers.

1. Set the environment to use Docker mode.

```go
export APP_MODE=docker
```

2. Run the Cold Wallet CLI installer with the command for your OS. <br />\
   **Linux** <br /><br />
   ```go
   ./coldwallet-cli-linux
   ```
   **macOS** <br /><br />
   ```go
   ./coldwallet-cli-darwin
   ```
3. You’ll see a list of commands for managing Cold Wallet.

```go
This CLI is used to manage the Blockdaemon cold wallet. It can generate
        configuration, run the cold wallet, and manage the cold wallet.

Usage:
  walletcli [command]

Available Commands:
  completion   Generate the autocompletion script for the specified shell
  config       Manage wallets' configurations
  database     Manage MPC nodes' databases
  help         Help about any command
  key          Manage MPC nodes' keys
  presignature Presignatures are essential in MPC protocol. Each node must get hold of sufficient presignatures for the wallet to work

Flags:
  -h, --help   help for walletcli

Use "walletcli [command] --help" for more information about a command.
```

Below is an overview of the commands and their subcommands.

<Table align={["left","left"]}>
  <thead>
    <tr>
      <th>
        Commands
      </th>

      <th>
        Sub Commands
      </th>
    </tr>
  </thead>

  <tbody>
    <tr>
      <td>
        `completion`
      </td>

      <td>
        Autocompletion for shells:
        `bash` - Generate the autocompletion script for bash
        `fish` - Generate the autocompletion script for fish
        `powershell` - Generate the autocompletion script for powershell
        `zsh` - Generate the autocompletion script for zsh
      </td>
    </tr>

    <tr>
      <td>
        `config`
      </td>

      <td>
        `gen`: Generate configuration and installation files for the cold wallet
      </td>
    </tr>

    <tr>
      <td>
        `database`
      </td>

      <td>
        `backup`: Backup the database
        `restore`: Restore a database backup
      </td>
    </tr>

    <tr>
      <td>
        `key`
      </td>

      <td>
        `recover`: Convert the passed backup file, RSA private key, and derivation path to private key and chain code
        `reshare`: Reshare key shares. You must execute this command against two nodes simultaneously. This command will also backup the databases and generate the presignatures.
      </td>
    </tr>

    <tr>
      <td>
        `presignature`
      </td>

      <td>
        `gen`: Generate presignatures for MPC protocols. You must execute this command against two nodes simultaneously.
      </td>
    </tr>
  </tbody>
</Table>

### Step 3.1. Configuring the Cold Wallet CLI

> ❗️ Note:
>
> The following steps use macOS as the example environment.

1. Generate the Cold Wallet configuration using the `config` command as shown below.

```go
./coldwallet-cli-darwin config
```

2. To generate the full configuration, run:

```go
./coldwallet-cli-darwin config gen
```

3. During installation, you’ll be prompted to fill in the following information:

<Image align="center" width="600px" src="https://files.readme.io/fd3ae5259ab79d89a91c58ce95f1be58a77287cbfd68a355015983182839e84e-image.png" />

* **Company Name**: Enter your company name (optional)
* **Installation Absolute Path**: The path where the Cold Wallet will be installed. This will include the `docker-compose.yml` file
* **Configuration Absolute Path**: The location of your configuration files
* **Backup Directory**: The location where the database will be periodically backed up
* **ERS Public Key**: Input the public key for the wallet's Emergency Recovery Secret (ERS).

> 📘 Info:
>
> The public key encrypts the key shares for recovery purposes. Only the private key owner can decrypt this. Learn more how it works and how to get one [here](https://wallet.docs.blockdaemon.com/docs/back-up-and-emergency-recovery).

4. When completed, you’ll see a success message.

```go
Configuration files generated successfully.
```

This command generates application assets, such as:

* **`frontend/dist`**: Manages where to host the wallet, which runs locally on an air-gapped machine by default
* **`docker-compose.yml`**: Manages the web app, port, policy nodes, and the backup container
* **`node config files`**: There are two nodes (`node0` & `node1`) that have settings for communication with each other and the web app, including the ERS public key for recovery
* **`webapp`**: Hosts the web interface and routes communication through the nodes

## Step 4. Using the Cold Wallet

### Step 4.1. Start the Cold Wallet Backend

1. In the terminal, navigate to the `app` folder.

```go
cd app
```

2. Start the MPC node.

```go
docker compose run --use-aliases --service-ports mpcnode0
```

3. Enter the storage encryption key. As it is a non-encoded encryption key, you can enter plain text.

> ❗️ Ensure that only you have access to the key and keep it secure from others.

4. re-enter the storage encryption key
5. Once running, the node will show:

```go
mpc node 0 listening to gRPC socket: :8900
```

> 📘 Info:
>
> Repeat these steps for `mpcnode1` using a new terminal window.

### Step 4.2. Start the Cold Wallet Frontend

1. In the terminal, navigate to the `app` folder.

```go
cd app
```

2. Run the web application:

```go
docker compose run --use-aliases --service-ports webapp
```

3. Once it’s running, you’ll see:

```go
web app listening to HTTP socket: :8902
```

4. Open your browser and go to `localhost:8902` to access the Cold Wallet UI.

![](https://files.readme.io/c7fa014df3564f57999899782f8fe28971f117e35ebbc89f73a39bef6c698937-image.png)

<Support />