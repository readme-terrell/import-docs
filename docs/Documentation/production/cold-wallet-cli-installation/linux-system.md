---
title: Linux System
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
<Image align="center" src="https://files.readme.io/206c8a6-Asset_60300x_3.png" />

This article will walk you through installing the cold wallet onto a Linux-based machine.

## Prerequisites

* Ensure that your machine can run a Linux distribution that supports systemd.
* Ensure you have the permissions to run commands as root or with sudo.

## Step 1: Download the Installer

Download the installer by following the steps below:

1. Open your terminal.
2. Go to your home path by using the command below:

```
cd ~/
```

3. Create the cold wallet directory by using the command below:

```
mkdir -p coldwallet
```

4. Download the file with curl using the following command:

```
curl --output bundle.tar &lt;presigned url&gt;
```

> 📘 Note:
>
> Change the `&lt;presigned URL&gt;` with the URL that you got from your sales associate or technical representative.

## Step 2: Unpack the Assets

To unpack the assets, follow the steps below:

1. Unpack by using the following command:

```
tar -xf bundle.tar -C coldwallet
```

2. Navigate to the cold wallet directory where you have unpacked all the required assets.
3. Export the env var `APP_MODE` to select a systemd type of installation by using the following command:

```
export APP_MODE=systemd
```

## Step 3: Initiate the Cold Wallet

To initiate the cold wallet, follow the steps below:

1. Navigate to the cold wallet directory.
2. Initiate the cold wallet app installation by using the following command:

```
./coldwallet-cli init
```

3. Run the cold wallet using the following command:

```
./coldwallet-cli start
```

### Command Usage

The following is the list of all the systemd Cold wallet commands that you can use:

| Command   | Description                                                                |
| :-------- | :------------------------------------------------------------------------- |
| `init`    | Run the config generation TUI to create the config and installation files. |
| `start`   | Starts the cold wallet.                                                    |
| `stop`    | Stops the cold wallet.                                                     |
| `enable`  | Enables the cold wallet to start on the boot.                              |
| `disable` | Disables the cold wallet from starting on boot.                            |
| `status`  | Shows the status of the cold wallet services.                              |

<Support />

<br />