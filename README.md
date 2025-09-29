# 🧰 EDA Tools Installation — E0 217 ESDCS
---

## Scope of this repo
This includes **only the installation** of the required tools.  
**How to use** these tools is already explained clearly in the **Tutorial PDF shared on Microsoft Teams**. Please follow that PDF for the same.

- **Git Repo Link**: [Link to this git repository](https://github.com/E0217-ESDCS/ESDCS_EDA_TOOLS) 
---

## Version Specs
- **Ubuntu**: 22.04.5 LTS (Jammy Jellyfish)  
- **macOS**: 15.6 (Sequoia)
- **Windows**: 11 

> ✅ These versions are tested and known to work reliably with the tools in this course.

---

## Platforms

### 🔹 Windows (3 Options)
1. **If you are already using Ubuntu on Windows**
2. **Preinstalled Ubuntu Image**
3. **WSL (Windows Subsystem for Linux)**
   
Please feel free to choose any one of the options given above that works best for you.

➡️ See the following steps for the installation process.

---

### 🔹 Linux (Ubuntu 22.04.5)
Just run:
```bash
sudo apt install -y iverilog gtkwave yosys opensta
```
➡️ That’s all you need on Linux Ubuntu 22.04.5 and earlier. (Latest version of Ubuntu i.e. 24.04 does not support opensta yet)

---

### 🔹 macOS (15.6 Sequoia)
We will use Docker to create a Linux environment for **iverilog, yosys, opensta**. We will use **Surfer** natively on macOS as waveform viewer.  

➡️ See the following steps for the installation process.

---

<div align="center">

&nbsp;  
&nbsp;  
&nbsp;  
&nbsp;  

</div>


# <img src="https://upload.wikimedia.org/wikipedia/commons/thumb/5/5f/Windows_logo_-_2012.svg/88px-Windows_logo_-_2012.svg.png" alt="Windows Logo" width="25"/> EDA Tools Installation — Windows 11


## Installation Options on Windows

**Please feel free to choose any one** of the options given above that works best for you.

### 1️⃣ Option 1: If you are already using Ubuntu on Windows

If you are using **Ubuntu on VirtualBox or as WSL** for other courses for example TCP/IP, and **Ubuntu version is 22.04.5 or earlier,** then you can use the same Ubuntu environment for EDA tools for this course also. 

You can check the Ubuntu version with the following command:

```bash
lsb_release -a
```

So if the version is 22.04.5 or earlier, just open the terminal and run the following command 

```bash
sudo apt install -y iverilog gtkwave yosys opensta
```

If you are  using later versions of Ubuntu (for example, 24.04) then it won't work for these tools. Please choose any one of the following options. 

### 2️⃣ Option 2: Preinstalled Ubuntu Image (If RAM >= 8GB && Disk Space > 25 GB you can go with this option. Otherwise, go to option 3)

#### Step 1: Download and Install VirtualBox
Download from: [VirtualBox Download](https://www.virtualbox.org/wiki/Downloads)

#### Step 2: Download .ova file (Open Virtualization Archive format)

Download the `.ova` file for preinstalled apps from 

Google Drive Link: [![Google Drive](https://img.shields.io/badge/Google%20Drive-34A853?logo=googledrive&logoColor=white)](https://drive.google.com/file/d/1TcOnpjCnTXO8srmuOn0vr1XODIpAz0az/view?usp=sharing)

For OpenRoad, download the .ova file from Annexure B. (This is optional. You won't need this for course assignments and project. We shall tell more about it in the Lab session)

#### Step 3: Import Appliance in VirtualBox
1. Open **VirtualBox**  
2. Go to **File → Import Appliance**  
3. In **Source**, select the downloaded `.ova` file  
4. In **Settings**, select the path where you want to keep the Ubuntu files  
   - If OS drive has less space than **25 GB**, prefer another drive  
   - Preferably choose a **faster drive** for better performance  
   - You can also adjust **RAM, CPU cores, and other resources** here if needed  
5. Click **Finish** → Import will take some time

#### Step 4: Start and Use Ubuntu VM
- Start the imported VM from VirtualBox  
- Credentials:  
  - **Username**: `esdcs`  
  - **Password**: `esdcs#123`
    
It has preinstalled tools (iverilog, gtkwave, opensta, yosys).




#### Step 5: Setting up Shared Folder

Enable the shared folder  
 `Devices > Shared Folders`  
 Choose a Windows folder that you want to share with Ubuntu. Check Auto-mount and Make Permanent options.
 Then open a terminal and enter the following command
 
 ```bash
sudo adduser $USER vboxsf
```
    
---

### 3️⃣ Option 3: WSL (Windows Subsystem for Linux)

#### Step 1: Enable WSL and Install Ubuntu 22.04.5
Open CMD or PowerShell as Administrator and run:
```powershell
wsl --install -d Ubuntu-22.04
```
After running the above command, if you get error like `WslRegisterDistribution failed with error: 0x80370114 Error: 0x80370114 The operation could not be started because a required feature is not installed.` Then run the following commands.

```powershell
dism.exe /online /enable-feature /featurename:Microsoft-Windows-Subsystem-Linux /all /norestart
dism.exe /online /enable-feature /featurename:VirtualMachinePlatform /all /norestart
dism.exe /online /enable-feature /featurename:Microsoft-Hyper-V-All /all /norestart
bcdedit /set hypervisorlaunchtype Auto
```
Then reboot. Then again, try the first command.

#### Step 2: Open Ubuntu (WSL shell)
From the **Start Menu**, search and open **Ubuntu 22.04 LTS**, or run the following command in CMD:

```powershell
wsl
```

#### Step 3: Install EDA Tools
Inside Ubuntu shell:
```bash
sudo apt update
sudo apt upgrade
sudo apt install -y iverilog yosys opensta gtkwave 
```

#### Step 4: Verify installation
```bash
iverilog -V
yosys -V
sta -help
gtkwave -h
lsb_release -a
```


#### Notes

- To see the list of installed WSL distributions:
 ```powershell
wsl --list --verbose
```
- To start specific distro if multiple WSL are installed:
 ```powershell
wsl -d <DistributionName>
```
- To set specific distro default:
 ```powershell
wsl --set-default <DistributionName>
```
- To remove a WSL distribution:  
 ```powershell
wsl --unregister <DistributionName>
```
- Access Windows files inside WSL at `/mnt/c/...`. 

---

<div align="center">

&nbsp;  
&nbsp;  
&nbsp;  
&nbsp;  

</div>


# <img src="https://upload.wikimedia.org/wikipedia/commons/1/1b/Apple_logo_grey.svg" alt="Apple Logo" width="25"/> EDA Tools Installation — macOS 15.6 Sequoia

Here, we will install: **iverilog** (Verilog simulator), **yosys** (Logic synthesis tool), **opensta** (Static timing analysis), **Surfer** (Waveform viewer - used instead of GTKWave)  

---

## Installation Options on Windows

**Please feel free to choose any one** of the options given above that works best for you.

### 1️⃣ Option 1: Docker on macOS

📺 **Video Walkthrough:** [EDA Tools Installation on macOS](https://youtu.be/K2mgFNE60vA)  
[![Watch on YouTube](https://img.shields.io/badge/Watch%20Now-red?logo=youtube&logoColor=white)](https://youtu.be/K2mgFNE60vA)

---

### Step 1: Install Homebrew
[Homebrew](https://brew.sh) is the package manager for macOS.  
Install it by running this in your terminal: (You can skip this step if Homebrew is already installed)

```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

---

### Step 2: Install Surfer (Waveform Viewer)
Instead of GTKWave, we will use **Surfer**. To install it, enter the following brew command:

```bash
brew install surfer
```
---

### Step 3: Install Docker Desktop
We will use the other 3 tools (iverilog, yosys, opensta) in a Linux environment using Docker.

Download and install Docker Desktop for Mac (For **Intel Macs** → use Intel version, for **Apple Silicon Macs** → use Apple version ):  
👉 [Docker Desktop Download Link](https://docs.docker.com/desktop/setup/install/mac-install/)

After installation:  
1. Launch **Docker Desktop** from Applications.  
2. Log in with your **Docker Hub** account [Simply login with Google works].  

---

### Step 4: Prepare Workspace Directory
The workspace directory will be shared between macOS and Docker Ubuntu 22.04.5. Which means the contents at this path present in macOS will be accessible in Ubuntu and vice versa. 
Create such a directory to store Docker-related files (Please change the path according to your needs):

> ⚠️ Please replace `/Users/shubhamlanjewar/code/esdcs_docker` with **`your_path`**

```bash
mkdir -p /Users/shubhamlanjewar/code/esdcs_docker
```

---

### Step 5: Download and load Docker Image

This Docker image contains:  
- **Ubuntu** (22.04.5 LTS), **Preinstalled tools** (iverilog, yosys, opensta, lsb_release, git, curl, vim, sudo, bash)

**For Apple Silicon:**

To pull the Docker image, run:
```bash
docker pull shubhamlanjewar97/esdcs-ubuntu-img:latest
```
If this command `docker pull` does not show any error then you can go to Step 6 now. Otherwise,

**OR**

If the `docker pull` command doesn't work (possibly due to the pull limit reached), then download the Docker image tar file with the following link.

`esdcs-ubuntu-img.tar` [esdcs-ubuntu-img.tar](https://drive.google.com/file/d/1KC3WvvtfOk1EqfyCcwYt11UYfv6uCh1o/view?usp=sharing)  

Then, to load the Docker image, go to the location where the `.tar` file is present and run: (you won't need this if you used the `docker pull` command)

```bash
docker load -i esdcs-ubuntu-img.tar
```

**For Intel processor:**(Not tested yet. Let us know if you face any issues.)

Download the Docker image tar file with the following link.

`esdcs-ubuntu-img-intel.tar` [esdcs-ubuntu-img-intel.tar](https://drive.google.com/file/d/1sWtr6MWsvSRsL9LkmINIU2ok0UTsdrWC/view?usp=sharing)  

Then, to load the Docker image, go to the location where the `.tar` file is present and run:

```bash
docker load -i esdcs-ubuntu-img-intel.tar
```


---

### Step 6: Create and Run the Docker Container (First Time Only)
Run the container for the very first time:

> ⚠️ Please replace `/Users/shubhamlanjewar/code/esdcs_docker` with **`your_path`**

**For Apple Silicon:**

If you used the `docker pull` command in step 5, use the following command.
```bash
docker run -it --name esdcs-ubuntu   -v /Users/shubhamlanjewar/code/esdcs_docker:/macos_local   shubhamlanjewar97/esdcs-ubuntu-img:latest
```
Otherwise, if you used the  `docker load` command in step 5, use the following command instead.
```bash
docker run -it --name esdcs-ubuntu   -v /Users/shubhamlanjewar/code/esdcs_docker:/macos_local   esdcs-ubuntu-img
```

**For Intel processor:**

```bash
docker run -it --name esdcs-ubuntu-intel   -v /Users/shubhamlanjewar/code/esdcs_docker:/macos_local   esdcs-ubuntu-img-intel
```

This will take you to the Linux environment with user "esdcs". This Linux environment is running inside Docker.

✅ You will now be inside a Linux environment with **iverilog**, **yosys**, and **opensta** already installed.


### Note:
**iverilog, yosys, and opensta** are in the docker environment, however **surfer** is installed in the macOS environment. Make sure you are on the correct terminal to use the respective tools.


Since we already know that our workspace directory is shared between macOS (`/Users/shubhamlanjewar/code/esdcs_docker` here) and docker Ubuntu 22.04.5 (`/macos_local` here), once the `.vcd` file is generated in Ubuntu 22.04.5 environment, we can copy to `/macos_local` in Ubuntu and then go to macOS terminal (e.g. `/Users/shubhamlanjewar/code/esdcs_docker`) and use surfer to view waveforms using the following command:

```bash
surfer test.vcd
```


    
---



### 2️⃣ Option 2: Ubuntu 22.04 on UTM (Apple Silicon)


This guide explains how to run a **preinstalled Ubuntu 22.04 ARM64 VM** using **UTM on macOS Apple Silicon**.  
It is recommanded to have at least **8 GB RAM** and **25 GB free disk space** for this option. But you can try even with **20 GB free disk space**. Less than **15 GB free disk space** is not recommanded at all. In case of lower RAM or disk space, use Option 1 (Docker).

---

### Step 1: Install UTM  

Download and install UTM from : [UTM](https://mac.getutm.app)

This is a virtualization app for macOS on Apple Silicon. [Similar to VirtualBox but more optimized for macOS on Apple Silicon] 

---

### Step 2: Download Preinstalled Ubuntu UTM Image  
Download the prebuilt `.utm` image file from Google Drive:  

[![Google Drive](https://img.shields.io/badge/Google%20Drive-34A853?logo=googledrive&logoColor=white)](https://drive.google.com/file/d/1EQed3EkUCjg7oRKZQ4u0xFhEkjU5hruw/view?usp=sharing)

Extract this file with **Archieve Utility**

---

### Step 3: Open the UTM Image  
1. Open **UTM**.  
2. Go to **File → Open**. 
3. And select the extracted `.utm` file.  (Its better to copy this file at some other location than downloads since it will have all the data of VM)

---

### Step 4: Start and Use Ubuntu VM  
When you start the VM it may say "Dispaly output is not active" for around 30 seconds. You may have to wait for it to get started.
- Default credentials for VM:  
  - **Username**: `esdcs`  
  - **Password**: `esdcs#123`

After login you can use the preinstalled tools immediately.

---

### Step 5: Change scale
1. If text/icons looking too small, you can change the scale from 100% to 200% in Settings > Display > Scale. 


### Step 6: Setup Shared Folder and Retina Mode
1. Select the VM and click on setings (top right corner of UTM window)
2. Go to **Display** and check **Retina Mode** if it is unckecked.
3. Go to **Sharing** and make sure **Directory Share Mode** is set as **SPICE WebDAV** and select the path(path in macOS) of the folder which you want to share between VM and macOS.
4. Also make sure **Shared Clipboard** is ckecked in **Sharing**
5. This shared folder will be visible in **File Exploer > Other Locations** something like "SPICE client folder" (This may take about a minute for it to mount properly).
6. There is a way to make this shared folder mount autoamtically at each boot and more reliable so that it won't take some time to access it. (You can search on google about how to do it. We may update it here later.)
---

<div align="center">

&nbsp;  
&nbsp;  

</div>

# 📚 Annexures

### 🔹 Annexure A: Required Folders
Apart from installing these tools, you will need the following folder to follow the further steps of the Tutorial PDF.
- `NANGATE_OPEN_STDCELL` - are available on Microsoft Teams at **General > Files > Simulation Models > NANGATE_OPEN_STDCELL**

- Verilog files for example circuits (discussed in previous lab session and some more) are available on Microsoft Teams at **General > Files > Verilog Files**


---

### 🔹 Annexure B: .ova file for OpenRoad
Download the following .ova file for OpenRoad.


Ubuntu 22.04 with OpenRoad: [![Google Drive](https://img.shields.io/badge/Google%20Drive-34A853?logo=googledrive&logoColor=white)](https://drive.google.com/file/d/10v-Vd8ko0wSxDf4Dp-N8UwcSCcY0qUrN/view?usp=sharing)


---

### 🔹 Annexure C: Useful Docker Commands(Mandatory)

List Docker containers(this also shows the status of containers also e.g., exited, etc):
[For Intel processors, use `esdcs-ubuntu-img-intel` instead of `esdcs-ubuntu-img`.

```bash
docker ps -a
```

Start the container (next time onwards):
```bash
docker start -ai esdcs-ubuntu
```

Stop the container:
```bash
docker stop esdcs-ubuntu
```

Remove a container:
> ⚠️ Please use with caution! It will remove all data in the Docker container.
```bash
docker rm <container_name>
# Example:
docker rm esdcs-ubuntu
```
---

## Quick Links
- **Git Repo Link**: [EDA Tools Installation](https://github.com/E0217-ESDCS/ESDCS_EDA_TOOLS)
- **Tutorial PDF**: Available on Microsoft Teams
---

