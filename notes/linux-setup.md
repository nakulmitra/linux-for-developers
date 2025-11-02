# Setting Up Our Linux Environment

## Setup Guide - Ubuntu on Oracle VirtualBox

### Step 1 - Install Oracle VirtualBox

1. Go to: [https://www.virtualbox.org/wiki/Downloads](https://www.virtualbox.org/wiki/Downloads)
2. Download and install **VirtualBox** for your operating system (Windows/Mac/Linux).

### Step 2 - Download Ubuntu ISO

1. Visit: [https://ubuntu.com/download/desktop](https://ubuntu.com/download/desktop)
2. Download the **Ubuntu Desktop ISO**.

### Step 3 - Create a New Virtual Machine

1. Open **VirtualBox** -> Click **New**.
2. Give your VM a name (e.g., "Ubuntu-Dev").
3. Choose:

   * **Type:** Linux
   * **Version:** Ubuntu (64-bit)
4. Assign:

   * **Memory (RAM):** at least **4 GB**
   * **Processors:** 2+ cores if available
5. Create a **virtual hard disk** (VDI), at least **25 GB**.

### Step 4 - Attach Ubuntu ISO

1. Go to VM **Settings -> Storage -> Empty Disk -> Choose a Disk File**.
2. Select the downloaded Ubuntu ISO.

### Step 5 - Install Ubuntu

1. Start the VM -> Ubuntu installer will launch.
2. Choose "Install Ubuntu."
3. Follow the installation wizard (username, password, timezone, etc.).
4. Once installed, eject ISO and reboot.

### Step 6 - Install Guest Additions (Optional but Recommended)

1. Start Ubuntu inside VirtualBox.
2. From top menu: **Devices -> Insert Guest Additions CD Image**.
3. Run installation and restart VM.
   This allows copy-paste, better display resolution, and shared folders.

## Setup Guide - Windows Subsystem for Linux (WSL)

### Step 1 - Enable WSL

Open **PowerShell as Administrator** and run:

```bash
wsl --install
```

This installs WSL 2 (the latest version) with Ubuntu by default.

### Step 2 - Restart and Open Ubuntu

After installation, restart your system.
Search **Ubuntu** in the Start Menu and open it.

### Step 3 - Set Up Your Linux User

On first launch, you'll be asked to:

* Create a **username**
* Set a **password**

Now you have a working Ubuntu terminal inside Windows!

### Step 4 - (Optional) Update Your System

Run:

```bash
sudo apt update && sudo apt upgrade -y
```

### Step 5 - Verify WSL Version

```bash
wsl --status
```

Make sure **Version 2** is shown (WSL 2 has full Linux kernel support).

[< Previous Tutorial](https://github.com/nakulmitra/linux-for-developers/blob/master/notes/linxu-file-system-st.md)