---
title: Cold Wallet Deployment
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
This is the deployment guide for the cold wallet. We are using CLI which is a command-line interface tool used to generate configuration and install the Cold wallet onto an air-gapped machine. It supports MacOS in Docker mode and Linux in systemd mode. 

## Prerequisites

* For Docker mode, Docker and docker compose must be installed in the offline machine.
* For systemd mode, your machine must be running a Linux distribution that supports systemd.
* Make sure you have the necessary permissions to run commands as root or with sudo.

## Overview

The CLI generates configuration files based on user input and uses these configuration files to manage the Cold Wallet. It uses the Cobra library for command handling and the Bubble Tea library for user input.

### MacOS System - Docker Mode

In Docker mode, the CLI generates Docker Compose configuration files and manages the Cold Wallet using Docker Compose commands.

### Linux System - systemd Mode

In system mode, the CLI generates systemd unit files and manages the Cold Wallet using system commands. It must be run as root or with sudo in this mode.

The CLI also includes a backup service that runs periodic backups of the Cold Wallet data and configuration. This service is managed in the same way as the Cold Wallet (either through Docker Compose or systemd, depending on the mode).

<Support />
