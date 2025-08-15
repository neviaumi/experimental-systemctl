# Experimental Systemctl Service

This project demonstrates how to create and manage a simple systemd service that continuously runs a bash script. The script prints "hello systemctl" to the console every 2 seconds.

## Prerequisites

*   A Linux system (like a Raspberry Pi) with `systemd` installed.
*   `bash` shell.
*   `sudo` privileges for installing and managing services.
*   `realpath` command (usually installed by default on most modern Linux systems).

## Getting Started & Usage

This section outlines the core workflow for setting up, managing, and removing your systemd service.

### 1. Install the Service

Run the installation script to set up the systemd service. This script handles generating the service file, enabling, starting, and reloading systemd.

```bash
# Make sure you are in the root directory of your project (e.g., ~/apps/experimental-systemctl)
bash ./scripts/systemctl-install.sh
```
(Note: The installation script uses `sudo` internally for system-level operations.)

### 2. Check Service Status
After installation, verify that the service is running correctly:
```shell
sudo systemctl status demo-systemctl.service
```
You should see output indicating the service is "active (running)". You can also check the logs for "hello systemctl" messages using `sudo journalctl -u demo-systemctl.service`.

### 3. Uninstall the Service
When you no longer need the service, you can completely remove it using the uninstallation script:
```shell
bash ./scripts/systemctl-uninstall.sh
```
This will stop the service, disable it from starting on boot, remove its configuration file, and reload systemd.
