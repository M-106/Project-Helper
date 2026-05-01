# Windows

[<img align="right" width=150px src='../res/rackete_2.png'></img>](../README.md)

This is a helper documentation for Windows 11. Use it as reference.

<br>

Contents:
- [Installation](#installation)
- [Fast Boot](#fast-boot)
- [Versions](#versions)
- [Interesting Software](#interesting-software)
- [WSL](#wsl)
- [Filesystem](#filesystem)
- [CMD](#cmd)
- [Powershell](#powershell)
- [SSH (in Powershell)](#ssh-in-powershell)


<br>

> Interesting to know: press `Windows` and `.` for opening the emoji and more part where you also find useful ascii signs as arrows like this: →


<br><br>

---
### Installation


1. **Download Windows 11**
   Go to the official Microsoft website and download the Windows 11 Installation Assistant or Media Creation Tool.
2. **Create Installation Media (optional)**
   Use a USB drive (at least 8 GB) to create a bootable installer with the Media Creation Tool.
3. **Boot from USB**
    Insert the USB stick and restart your PC. Enter the BIOS/UEFI (usually with F2, F12, DEL, or ESC) and select the USB device as the boot option.
4. **Start Installation**
   When the Windows Setup screen appears, choose your language, time, and keyboard settings, then click *Install Now*.
5. **Enter Product Key**
   Enter your Windows 11 key or skip this step to activate later.
6. **Choose Installation Type**
   Select *Custom: Install Windows only* for a clean installation, or *Upgrade* if you are updating an existing system.
7. **Select Drive**
   Pick the drive/partition where Windows should be installed. You can format it if needed.
8. **Complete Setup**
   The system will copy files and restart several times. Afterward, follow the on-screen steps to set up your account, network, and preferences.

<br>

> **Note:** Make sure your PC meets Windows 11 requirements (TPM 2.0, Secure Boot, supported CPU) before installing.


<br><br>

---
### Fast Boot

The fast booting does hinder your computer from emptying your RAM but comes with faster boot ups, because your RAM storage gets stored into a file and then loaded back after your next boot up. To turn off this option:
1. Press the windows key and search for `control panel` (Systemsteuerung)
2. Click on Hardware and Sound
3. Click on  change energysaving configurations (Energiespareinstellungen ändern) - under Energy Options
4. Click on Choosing, what happens when pressing the power button (Auswählen, was beim Drücken des Netzschalters geschehen soll)
5. Activate admin rights by clicking on `Some options are currently not available` (Einige Einstellungen sind aktuell nicht verfügbar)
6. Now remove the check by fast boot (Schnellstart aktivieren)

<br><br>

---
### Versions

1. **Windows 1.0** (1985): First graphical shell for MS-DOS, introduced basic windows, mouse support, and tiled multitasking.
2. **Windows 2.0** (1987): Added overlapping windows and improved performance; supported early versions of Word and Excel.
3. **Windows 3.x** (1990–1994): First widely successful version; introduced Program Manager and better memory handling.
4. **Windows 95 & 98** (1995-1998): Defined the modern Start menu/Taskbar paradigm.
5. **Windows 2000 & ME** (2000): Final operating systems based on 9x (ME) and NT (2000) technologies.
6. **Windows XP** (2001): Unified consumer/business lines (NT architecture) with extreme longevity.
7. **Windows Vista** (2006): Introduced Windows Aero, known for high hardware requirements.
8. **Windows 7** (2009): Widely lauded for stability and performance, replacing Vista.
9. **Windows 8/8.1** (2012–2013): Introduced the tile-based Start screen, focusing on touch interfaces.
10. **Windows 10** (2015–2025): Long-term, widely used version with consistent updates.
11. **Windows 11** (2021–Present): Current standard with a centered Taskbar, 22H2/23H2/24H2 updates, and strong AI focus.

Nowadays it is always recommended to install the newest Windows for Security reasons, but you still can experience old Windows versions via a virtual environment (for example with [VirtualBox](https://www.virtualbox.org/)). You can get old os images (iso files) from [the Internet Archive](https://archive.org/) ([Example: Windows XP](https://archive.org/details/windows-xp-all-sp-msdn-iso-files-en-de-ru-tr-x86-x64)) and [WinWorldPC](https://winworldpc.com/home) for older versions. And with VirtualBox you don't need an iso-file at all which is great.


<br><br>

---
### Interesting Software

Here are some interesting Software, this can vary from your components and needs but here are some proposals. Most software can be downloaded on their official website and then the installe exe file just have to be ran by yourself. Some software is already preinstalled and other can be found in the Microsoft Store.

<br>

#### General

- **Settings** - Central place to configure system, devices, network, and updates
- **Control Panel/Systemsteuerung** - Legacy configuration interface for advanced system settings - e.g., programs, hardware, user accounts), overlaps with Settings but still required for some options
- **Clock** - Alarms, timers, world clock, and focus sessions
- **Calculator** - Calculation with different modes: scientific, informatics, ...
- **Editor** - Lightweight text editor for quick notes and code snippets
- **Microsoft Store** - Download and update apps, games, and system components
- **Explorer** - Browse and manage files and folders
- **Outlook** - Email, calendar, and contacts management
- **Snipping Tool** - Capture screenshots and screen recordings

> All are already installed.

<br>

#### System

- **MSI Center** - Main-/Motherboard Software → fan curves, updates, RGB, etc.
- **Nvidia App** - GPU Software → GPU driver updates, game optimization, and recording features (replacement for GeForce Experience)
- **MSI Afterburner** (+ RivaTurner) - GPU/CPU Stats → fan curves, updates, RGB, etc.
- **WizTree** - Show Data Usage
- **DiskGenius** - Format Disks, see "all" disks, other Disk Features
- **AOMEI Partition Assistent** - Alternative to DiskGenius but most features are not free
- **HWiNFO** - Detailed Information about your Hardware
- **WSL** - Run Linux environments directly in Windows → [see WSL chapter](#wsl)
- **VirtualBox** - Run virtual machines (alternative: VMware)

<br>

#### System Commandlines

- **CMD / Command Prompt** - Legacy command-line interface; simple but still useful for basic tasks
- **Powershell** - Modern, powerful shell with scripting and automation capabilities
- **Powershell ISE** - Integrated scripting environment (now deprecated; replaced by editors like VS Code)
- **Windows Terminal** - Modern terminal that combines CMD, PowerShell, and WSL in one interface

> all preinstalled


<br>

#### Security

- **Bitwarden** - Secure password and key management across devices
- **Gpg4win/Kleopatra** - File encryption, decryption, and key management (OpenPGP)
- **Microsoft Defender** - Built-in antivirus and threat protection in Windows

More?

<br>

#### Browser

- **Firefox** - Privacy-focused, open-source browser
- **Chrome** - Fast, widely supported, large extension ecosystem
- **Microsoft Edge** - Chromium-based, optimized for Windows with good efficiency

<br>

#### Office

- **Microsoft Word** - Text documents and formatting
- **Microsoft Powerpoint** - Create presentations and slides
- **Microsoft Excel** - Data analysis, tables, and calculations
- **Microsoft OneNote** - Digital notebooks and organization
- **Microsoft To Do** - Simple task and reminder management
- **LibreOffice** - Free and open-source alternative to Microsoft Office
- And there are some other ...

> Just search for `Word` in the Microsoft Store and click on the app then the Microsoft 365 site should be shown and with clicking on install every of the above apps should be installed at once. Else search for `Microsoft 365 download` and download all in that way.

<br>

#### PDF & Writting

- **PDF Annotator** - Annotate, highlight, and edit PDF documents
- **Adobe Acrobat** - Industry-standard tool for viewing, editing, and signing PDFs
- **PDF24** - Free all-in-one PDF tool (create, merge, compress, convert)
- **MiKTeX** - LaTeX distribution for compiling scientific and technical documents
- **TeXstudio** - Editor for writing and managing LaTeX documents
- **Zotero** - Manage sources, citations, and bibliographies for academic work
- **Typora** - Clean Markdown editor with live preview

<br>

#### AI / LLM

- **ChatGPT**
- **Codex**
- **Copilot**
- **Claude**

<br>

#### Dev

- **VSCode** - Lightweight, extensible code editor with strong plugin ecosystem
- **Git** (GitBash & GitGUI) - Track changes, manage versions, and collaborate on code
- **Anaconda Prompt** (and navigator) - Python distribution for data science and package management
    - Comes with **Jupyter Notebook** and **Spyder**
- **Python Manager** - Manage and launch multiple Python versions
- **Docker Desktop** - Run and manage containers for reproducible development environments
- **MSYS2** - Unix-like environment with package manager for building native Windows software → [also see C++ Guide via MSYS](https://github.com/M-106/CPP/blob/main/docs/Basics/Installation.md#installation_)
- **Visual Studio** - Full-featured IDE for C++, C#, .NET, and more


<br>

#### Streaming

- **Spotify** - Stream music, podcasts, and playlists online
- **Netflix** - Movies, series, and original productions on demand
- **Disney +** - Disney, Marvel, Star Wars, and Pixar content
- **Amazon Prime** - Movies, series, and Amazon Originals
- **ZDF Mediathek** - Free German TV content and replays (public broadcasting)
- **Crunchyroll** - Anime streaming platform


<br>

#### Gaming

- **Steam** - Largest PC gaming platform with store, library, and community features
- **Ubisoft Connect** - Ubisoft's platform for games, updates, and rewards
- **Epic Store** - Game launcher/store with frequent free game offers and with an Unreal Engine Manager
- **GOG Galaxy 2** - DRM-free game platform with optional multi-launcher integration
- **EA Store** - Electronic Arts platform for games and subscriptions (replaced Origin)
- **Xbox Store** - Access Xbox Game Pass, manage games, and social features on PC
- **Xbox Zubehör** - Configure and update Xbox controllers
- **Playstation Accessories** - Manage PlayStation controllers on PC


<br>

#### Social

- **Discord** - Voice, video, and text chat for communities and gaming
- **LinkedIn** - Career networking and job platform
- **Whatsapp** - Popular messaging and calling app
- **Wechat** - Messaging, social media, and payments (mainly in China)
- **Telegram** - Privacy-focused messaging with channels and bots
- **VooV Meeting** (Tencent Meeting) - Video meetings and collaboration
- **Zoom** - Online meetings, webinars, and screen sharing


<br>

#### Images

- **Luminar Neo** - Simple photo editing and enhancement with AI-features
- **PlayMemories Home** - Organize and view photos/videos (Sony ecosystem)
- **OBS Studio** - Screen recording and live streaming tool
- **Paint** - Simple built-in image editing tool



<br>

#### 3D

- **CloudCompare** - Process and analyze 3D point cloud data
- **Blender** - Free and open-source 3D modeling, animation, and rendering suite


<br>

#### Audio

- **Cakewalk Next by BandLab** - Modern DAW for music production, recording, and mixing
- **Audacity** - Free, open-source tool for recording and editing audio


<br><br>

---
### WSL


<br>

**What is WSL?**

**WSL (Windows Subsystem for Linux)** lets you run a real Linux environment directly inside Windows—no virtual machine needed.

You can use:
* Linux terminals (bash, zsh)
* Linux tools (grep, ssh, git, python, etc.)
* Full Linux filesystem integration

<br><br>

**Install WSL**

1. Open **PowerShell as Administrator**:
2. Now type
    ```powershell id="wsl-install"
    wsl --install
    ```

This will:
* Enable WSL
* Install a default Linux distro (usually Ubuntu)
* Install WSL2 (modern version)
* Prompt for restart

<br><br> 

Install a specific Linux distro

1. List available distros:
    ```powershell id="wsl-list"
    wsl --list --online
    ```
2. Install one:
    ```powershell id="wsl-install-ubuntu"
    wsl --install -d Ubuntu
    ```

<br><br> 

Install the same distribution multiple times / set a custom name for your WSL subsystem

1. Install your subsystem (for example we want 2 Ubuntu systems) → in Powershell:
    ```powershell
    wsl --install -d Ubuntu
    ```
2. Export it:
    ```powershell
    wsl --export Ubuntu ubuntu1.tar
    ```
3. Import a second copy with a new name:
    ```powershell
    wsl --import Ubuntu-Dev D:\WSL\Ubuntu-Dev ubuntu1.tar
    ```
4. Test if you can see your distro
    ```powershell
    wsl -l -v
    ```
5. Remove backup file
    ```powershell
    Remove-Item ubuntu1.tar
    # or
    del ubuntu1.tar
    ```
6. You have now a custom name  (and in this case 2 different Ubuntu subsystems):
    ```powershell
    wsl -d Ubuntu
    wsl -d Ubuntu-Dev
    ```

<br><br> 

Install into a specific location

1. Install your subsystem (for example we want 2 Ubuntu systems) → in Powershell:
    ```powershell
    wsl --install -d Ubuntu
    ```
2. Export it:
    ```powershell
    wsl --export Ubuntu ubuntu1.tar
    ```
3. Import a second copy with a new name:
    ```powershell
    wsl --import Ubuntu-Dev D:\WSL\Ubuntu-Dev ubuntu1.tar
    ```
4. Test if you can see your distro
    ```powershell
    wsl -l -v
    ```
5. Remove backup file
    ```powershell
    Remove-Item ubuntu1.tar
    # or
    del ubuntu1.tar
    ```

> The `D:\WSL\Ubuntu-Dev` would be the storage place

WSL creates a folder like:
```text
D:\WSL\Ubuntu-Dev\
 ├── ext4.vhdx
 └── <some metadata files>
```

The virtual hard disk contains then the whole linux subsystem.

<br><br>

**Check WSL Installation**

Check WSL version:
```powershell id="wsl-version"
wsl --status
```

Check installed distros:
```powershell id="wsl-list-installed"
wsl -l -v
```

<br><br>

**Using WSL**

1. Start Linux
    Just type in the Powershell:
    ```powershell id="wsl-start"
    wsl
    ```
    Or open:
    * Start Menu → Ubuntu (or other distro)
2. Run Linux commands
    Inside WSL:
    ```bash id="linux-commands"
    ls
    pwd
    cd /home
    sudo apt update
    ```
3. Run Linux commands from Windows
    ```powershell id="wsl-run-command"
    wsl ls -la
    ```
4. Run Windows apps from Linux
    Inside WSL:
    ```bash id="wsl-win-app"
    notepad.exe
    explorer.exe .
    ```

<br><br>

**Stop / deactivate WSL**

- List running systems:
    ```powershell
    wsl -l -v
    # or:
    wsl -l -v | findstr Running
    ```
- Stop all running WSL instances:
    ```powershell id="wsl-shutdown"
    wsl --shutdown
    ```
- Stop specific running WSL instance:
    ```powershell id="wsl-shutdown"
    wsl -t name
    # example:
    wsl -t Ubuntu
    ```
- Uninstall a distro:
    ```powershell id="wsl-uninstall"
    wsl --unregister Ubuntu
    ```
- Disable WSL completely (Windows features)
    Run in PowerShell (Admin):
    ```powershell id="wsl-disable"
    dism.exe /online /disable-feature /featurename:Microsoft-Windows-Subsystem-Linux
    ```
    Also disable:
    * Virtual Machine Platform
    Then restart.


<br><br>

**Can you have multiple subsystems?**

▷ Yes

You can install multiple distros:
```powershell id="wsl-multi"
wsl --install -d Ubuntu
wsl --install -d Debian
wsl --install -d Kali-Linux
```

<br>

Check them:
```powershell
wsl -l -v
```

<br>
Switch default:
```powershell id="wsl-default"
wsl --set-default Ubuntu
```

<br>
Run specific distro:
```powershell id="wsl-run-distro"
wsl -d Debian
```

<br><br> 

**Move a WSL subsystem into another path**

1. Find the name of your subsystem → in Powershell:
    ```powershell
    wsl -l -v
    ```
2. Export it:
    ```powershell
    wsl --export YOUR_WSL_NAME your_wsl_name_1.tar
    ```
3. Remove the old WSL Subsystem
    ```powershell
    wsl --unregister YOUR_WSL_NAME
    ```
4. Import a second copy and set the path as you want:
    ```powershell
    wsl --import YOUR_WSL_NAME D:\WSL\Ubuntu-Dev your_wsl_name_1.tar
    ```
5. Test if you can see your distro
    ```powershell
    wsl -l -v
    ```
6. Remove backup file
    ```powershell
    Remove-Item your_wsl_name_1.tar
    # or
    del your_wsl_name_1.tar
    ```

<br><br>

**File system access**

From Windows to Linux subsystem

- Windows drive access
    Windows files are here in WSL:
    ```bash id="wsl-c-drive"
    /mnt/c/
    ```
    Examples:
    ```bash
    cd /mnt/c/Users/YourName/Documents
    ```
    Meaning:
    * `C:\Users\Name` → `/mnt/c/Users/Name`
    You can use copy commands or other commands.
- External commands from powershell
    ```powershell
    wsl cp -r C:\Users\You\Desktop\Project /home/user/
    ```
- Powershell method to access Windows
    ```powershell
    Copy-Item -Recurse C:\Project \\wsl$\Ubuntu\home\user\Project
    ```



<br><br>

From Linux subsystem to Windows

- FIle Explorer
    From Windows Explorer:
    ```
    \\wsl$\Ubuntu\
    ```
    Or:
    * Open Explorer
    * Type:
    ```
    \\wsl$
    ```
    You'll see:
    * Linux filesystem (Ubuntu, Debian, etc.)
- Powershell method to access Linux
    ```powershell
    Copy-Item -Recurse \\wsl$\Ubuntu\home\user\Project C:\Project
    ```
- Copy in WSL subsystem to Windows
    ```powershell
    cp -r /home/user/project /mnt/c/Users/You/Desktop/
    ```


<br>

> Your WSL Subsystem probably have to get started if you can't find/access the subsystem. 

<br><br>

**Where Linux files are stored (physically)**

WSL stores Linux files inside a virtual hard disk file (`.vhdx`) and the standard storage path is:
```
C:\Users\<you>\AppData\Local\Packages\
```

But you can install it everywhere you want to. That said the previous decribed method to access files from the linux subsystem is done by a virtual disk view from windows.

> Hint: Don't manually edit these files from Windows → they can corrupt WSL.

During the access as described previously following happen:
1. WSL2 runs a lightweight Linux VM in the background
2. Linux filesystem is exposed via a network-like share
    ```powershell
    \\wsl$\Ubuntu\
    ```
3. Windows accesses files through that interface

* So it is NOT raw disk access
* It is a virtual filesystem bridge

<br><br>

**Useful WSL commands cheat sheet**

| Command                      | Meaning             |
| ---------------------------- | ------------------- |
| `wsl`                        | start default Linux |
| `wsl -l -v`                  | list distros        |
| `wsl --shutdown`             | stop all WSL        |
| `wsl --set-default <distro>` | set default         |
| `wsl -d Ubuntu`              | run specific distro |
| `wsl --update`               | update WSL          |

<br><br>

**How WSL actually works**

* Windows runs a lightweight Linux kernel (WSL2)
* Linux behaves like a real machine
* Filesystems are bridged:
  * Windows ↔ `/mnt/c`
  * Linux ↔ `\\wsl$`

<br><br>

**Best way to use WSL**

Common developer setup:
* Code in Windows (VS Code)
* Run backend in WSL (Linux)
* Use Git, Python, Node inside WSL
* Access files via `/mnt/c` or `\\wsl$`

<br><br>

---
### Filesystem


<br>

**What is a filesystem?**

A **filesystem** is how your computer organizes files and folders on a drive (HDD/SSD).
It works like a tree:
* Root (top level)
* Folders (directories)
* Files (data inside folders)

Example structure:

```
C:\
 ├── Windows\
 ├── Program Files\
 ├── Users\
 └── ProgramData\
```

<br><br>


**Main Windows folders (important ones)**

> Notice that you might install programs on a custom disk/path for storage limitation reasons.

- `C:\Windows`
    * Core operating system files
    * DO NOT delete or modify manually
    * Contains drivers, system libraries, OS components
- `C:\Program Files`
    * Installed 64-bit applications
    * Example: Chrome, Steam, VS Code
- `C:\Program Files (x86)`
    * Installed 32-bit applications
    * Older or legacy software
- `C:\Users`
    * Personal user accounts
    - Inside:
        ```
        C:\Users\YourName\
        ├── Desktop
        ├── Documents
        ├── Downloads
        ├── Pictures
        └── AppData
        ```
- `C:\Users\<name>\AppData` (hidden)
    * Application settings and caches
    * Very important but usually hidden
    - Inside:
        * `Local` → device-specific data
        * `Roaming` → syncable settings (cloud profiles)
        * `LocalLow` → low-security apps (browsers, games)
- `C:\ProgramData`
    * Shared application data for all users
    * Not tied to one account
    - Example:
        * antivirus configs
        * shared game data
- `C:\Windows\System32`
    * Critical system executables
    * Commands like `cmd`, `powershell`, drivers
    * Deleting here = breaking your OS
- `C:\`
    * Root drive (top level of system disk, like `/` in Linux)
    * Everything starts here


<br><br>

**Path examples**

Absolute path (full location)
```
C:\Users\Tobia\Documents\file.txt
```

Relative path (from current folder)
```
Documents\file.txt
```

<br><br>

**Special folders (PowerShell shortcuts)**

* `$env:USERPROFILE` → your user folder
  → `C:\Users\YourName`
* `$env:APPDATA` → roaming AppData
* `$env:LOCALAPPDATA` → local AppData
* `$env:PROGRAMFILES` → Program Files

<br><br>

**Linux comparison**

| Windows         | Linux              |
| --------------- | ------------------ |
| `C:\`           | `/`                |
| `Users`         | `/home`            |
| `Program Files` | `/usr/bin`, `/opt` |
| `System32`      | `/bin`, `/sbin`    |
| `AppData`       | hidden `~/.config` |


<br><br>

**Mental model**

Think of your filesystem like:

* 🏠 Drive = house
* 🚪 Root (`C:\`) = front door
* 🏢 Folders = rooms
* 📦 Files = objects inside rooms




<br><br>

---
### CMD

Here’s a solid Windows **Command Prompt (CMD)** equivalent cheat sheet, covering the most common and practical commands similar to your Linux list.

<br>

**Navigation commands:**
* `cd` → show current directory
* `cd folder` → change directory
* `cd ..` → go up one level
* `cd \` → go to root of current drive
* `cd /d D:\folder` → switch drive and directory
* `F:` → switch drive (change `F` with your drive name)
* `dir` → list files and folders
* `dir /a` → show hidden files
* `dir /w` → wide list format
* `cls` → clear screen

<br><br>

**File and Directory Management:**
* `mkdir foldername` → create directory
* `rmdir foldername` → remove empty directory
* `rmdir /s folder` → remove folder and contents
* `rmdir /s /q folder` → force delete folder (quiet)
* `del file.txt` → delete file
* `del /f file.txt` → force delete
* `copy source target` → copy file
* `xcopy source target /E /I` → copy folders (including subfolders)
* `robocopy source target /E` → advanced copy (recommended)
* `move source target` → move or rename
* `ren oldname newname` → rename file

<br><br>

**Viewing and Editing Files:**
* `type file.txt` → display file contents
* `more file.txt` → paginated view
* `notepad file.txt` → open in Notepad
* `echo text > file.txt` → create/write file
* `echo text >> file.txt` → append to file

<br><br>

**System & Info Commands:**
* `whoami` → current user
* `hostname` → computer name
* `systeminfo` → system details
* `tasklist` → running processes
* `taskkill /IM program.exe /F` → force kill process

<br><br>

**Disk & File System:**
* `chkdsk` → check disk
* `diskpart` → disk management tool
* `format D:` → format drive (careful!)

<br><br>

**Network Commands:**
* `ipconfig` → IP info
* `ipconfig /all` → detailed info
* `ping google.com` → test connectivity
* `tracert google.com` → trace route
* `netstat` → network connections

<br><br>

**Permissions & Ownership:**
* `attrib` → view/change file attributes
* `attrib +h file` → hide file
* `attrib -h file` → unhide file

<br><br>

**Search:**
* `dir /s filename` → search for file
* `find "text" file.txt` → search text
* `findstr "text" file.txt` → advanced search

<br><br>

**Misc / Useful:**
* `exit` → close CMD
* `help` → list commands
* `command /?` → help for specific command
* `start file_or_program` → open file/app
* `pause` → wait for key press (useful in scripts)

<br><br>

> **Bonus: PowerShell equivalents (modern Windows)**<br>
> If you ever switch to PowerShell (recommended), many Linux-like commands work:
> * `ls`, `cd`, `cp`, `mv`, `rm`, `cat` all exist as aliases




<br><br>

---
### Powershell



<br>

**Navigation commands:**
* `Get-Location` → print working directory
* `Set-Location folder` → change directory
* `Set-Location ..` → go up one level
* `Set-Location ~` → go to home directory
* `Set-Location \` → go to root
* `Get-ChildItem` → list files (`ls`, `dir` alias)
* `Get-ChildItem -Force` → include hidden files
* `Clear-Host` → clear screen

<br><br>

**File and Directory Management:**
* `New-Item -ItemType Directory foldername` → create directory
* `Remove-Item foldername` → remove empty directory
* `Remove-Item folder -Recurse` → remove folder recursively
* `Remove-Item folder -Recurse -Force` → force remove
* `Remove-Item file.txt` → delete file
* `Copy-Item source target` → copy
* `Move-Item source target` → move or rename
* `Rename-Item oldname newname` → rename
* `New-Item file.txt` → create empty file

<br><br>

**Viewing and Editing Files:**
* `Get-Content file.txt` → show entire file (`cat` alias)
* `Get-Content file.txt -Tail 10` → last lines
* `Get-Content file.txt -Wait` → live log monitoring (like `tail -f`)
* `Get-Content file.txt -Head 10` → first lines
* `Out-Host -Paging` → paginated output (like `less`)
* `notepad file.txt` → open in Notepad
* `"text" | Out-File file.txt` → write to file
* `"text" | Add-Content file.txt` → append to file

<br><br>

**System & Info Commands:**
* `whoami` → current user
* `$env:COMPUTERNAME` → computer name
* `Get-ComputerInfo` → system details
* `Get-Process` → running processes
* `Stop-Process -Name program` → stop process

<br><br>

**Disk & File System:**
* `Get-PSDrive` → list drives
* `Get-Volume` → disk info
* `Format-Volume` → format drive (careful!)

<br><br>

**Network Commands:**
* `Get-NetIPAddress` → IP info
* `Test-Connection google.com` → ping
* `Test-NetConnection google.com` → detailed network test
* `Get-NetTCPConnection` → active connections

<br><br>

**Permissions & Attributes:**
* `Get-Acl file` → view permissions
* `Set-Acl file` → change permissions
* `Get-Item file | Format-List *` → detailed file info

<br><br>

**Search:**
* `Get-ChildItem -Recurse -Filter filename` → search files
* `Select-String "text" file.txt` → search text (like `grep`)

<br><br>

**Pipelines & Objects (PowerShell strength):**
* `Get-Process | Where-Object {$_.CPU -gt 100}` → filter
* `Get-Service | Sort-Object Status` → sort
* `Get-ChildItem | Select-Object Name, Length` → select fields

<br><br>

**Misc / Useful:**
* `exit` → close PowerShell
* `Get-Help` → help system
* `Get-Help command` → help for command
* `Start-Process file_or_program` → open file/app
* `Pause` → wait for key press

<br><br>

**Aliases (Linux-like shortcuts):**

PowerShell includes many familiar aliases:

* `ls` → `Get-ChildItem`
* `cd` → `Set-Location`
* `cp` → `Copy-Item`
* `mv` → `Move-Item`
* `rm` → `Remove-Item`
* `cat` → `Get-Content`



<br><br>

---
### SSH (in Powershell)


PowerShell actually has built-in SSH support (via **OpenSSH**, which is included in modern Windows 10/11).

<br>

**Basic connection:**
* `ssh user@host` → connect to remote server
* `ssh user@192.168.1.10` → connect via IP
* `ssh -p 2222 user@host` → connect on custom port
* `ssh -i path\to\key user@host` → use specific private key

<br><br>

**Remote command execution:**
* `ssh user@host "ls"` → run single command remotely
* `ssh user@host "systemctl status nginx"` → check service
* `ssh user@host "df -h"` → disk usage

<br><br>

**File transfer (SCP):**
* `scp file.txt user@host:/path/` → copy file to server
* `scp user@host:/path/file.txt .` → copy from server
* `scp -r folder user@host:/path/` → copy folder recursively

<br><br>

**SFTP (interactive file transfer):**
* `sftp user@host` → start SFTP session
  Inside SFTP:
* `ls` → list remote files
* `cd folder` → change directory
* `get file.txt` → download file
* `put file.txt` → upload file
* `exit` → quit

<br><br>

**SSH Key management:**
* `ssh-keygen` → generate key pair
* `ssh-keygen -t ed25519` → modern recommended key type
* `ssh-keygen -t rsa -b 4096` → older but widely compatible

Default output:
* Private key: `~\.ssh\id_rsa` or `id_ed25519`
* Public key: `.pub` file

<br><br>

**Copy public key to server:**
* `type $env:USERPROFILE\.ssh\id_rsa.pub | ssh user@host "mkdir -p ~/.ssh && cat >> ~/.ssh/authorized_keys"`

(or simpler if available)

* `ssh-copy-id user@host` *(not always installed on Windows)*

<br><br>

**SSH agent (key caching):**
* `Start-Service ssh-agent` → start agent
* `ssh-add ~\.ssh\id_rsa` → add key to agent
* `ssh-add -l` → list loaded keys

<br><br>

**Config file (very useful):**

Location:

* `~\.ssh\config`

Example:

```text
Host myserver
    HostName 192.168.1.10
    User ubuntu
    Port 22
    IdentityFile ~/.ssh/id_rsa
```

Then you can simply run:

* `ssh myserver`

<br><br>

**PowerShell tips with SSH:**

* `ssh` works natively in PowerShell (no extra setup needed on modern Windows)
* You can pipeline commands:
  * `ssh user@host "ps aux | grep nginx"`
* Use PowerShell aliases + SSH together:
  * `ls` locally = PowerShell
  * `ssh user@host ls` = remote Linux-style listing

<br><br>

**Common troubleshooting:**
* `ssh -v user@host` → verbose debug mode
* `ssh -vvv user@host` → deep debug
* `Test-NetConnection host -Port 22` → check SSH port reachable









