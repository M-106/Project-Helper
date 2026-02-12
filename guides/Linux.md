Linux

[<img align="right" width=150px src='../res/rackete_2.png'></img>](../README.md)

This is a helper documentation for Linux. Use it as reference.


> Note that we use assume you have an Ubuntu Linux-Distribution. And use the term `Linux` most of the time interchangeable with `Ubuntu` in this guide. 



> You might find some interesting additional information in [Remote ML Workflow & GPU Management Guide](./Remote_ML_Workflow_and_GPU_Management.md). Like setting up a visual GUI via console and VSCode to your Server.



Contents:
- [Installation](#installation)
- [Interesting Software](#interesting-software)
- [Commands](#commands)
- [Interesting Software](#interesting-software)
- [File-System-Structure Explained](#file-system-structure-explained)
<!--
- [PDF Editing (password protection, signing)](#pdf-editing)
-->


<br><br>

---
### Installation

> See [Ubuntus Official Guide](https://documentation.ubuntu.com/desktop/en/latest/how-to/create-a-bootable-usb-stick/) or stick with my short guide.

On Windows:
1. Grab a USB-Stick
2. Download [Ubuntu](https://ubuntu.com/download/desktop)
3. Download [Rufus](https://rufus.ie/en/#download)
4. Start Rufus
5. Set Rufus settings:
    - Choose your USB Stick as `Device`
    - Set `Boot Selection` to `Disk or ISO image`
    - Click on `SELECT` next to the `Boot Selection` and find your downloaded Ubuntu iso file
6. Start Rufus Boot-Stick creation
7. Put your USB into your laptop or pc and start the device -> during the start-up press `F12`, `F2`, `Entf` -> it depends on your device and most likely is written very shortly on screen during boot-up.
8. Follow the installation process

> You may want to go into your boot menu and select the boot to the usb stick.

<br><br>

---
### Install Programs

In Linux there are 3 most ways to install software. The `apt` installation management system has older but stable version, then there is the `Ubuntu Software Center` for standard software and programs are often packed in a compromised version (`TAR`/`TAR.GZ`/`ZIP`). It follows a usage description of how to install software in these different ways.

Check program versions and installation with:
```bash
program --version
```

If you have a program and do not know where this program comes from, check it with:
```bash
which programname
```
- `usr/bin` -> apt
- `usr/local/bin` or `opt/` -> from yourself (maybe from `tar.gz`)
- `snap/bin` -> snap
- `var/lib/flatpak` -> flatpak

Following is a good base installtion:
```bash
sudo apt install build-essential cmake meson ninja-build git
```


1. **Ubuntu Software Center**<br>
    The Ubuntu Software Center is a GUI application installed on the Ubuntu operting system nd therefore can't be used on other Linux-Distributions.<br>
    It is very simple to use and provide basic progrms (but also not more than that), like VSCode, Wallper Apps, Bitwarden and other programs.<br>
    Installation Process:
    1. Open "Ubuntu Software" and register/sign in (if not already done)
    2. Search for the wanted program
    3. Click on install and follow any isntructions if needed
    
    It is simple like that.
2. **`apt` - native ubuntu system package manager**<br>
   `apt` provides very stable software excplicitly for your Ubuntu system version and is used via the terminal (bash).

   Installing and removing:
   ```bash
   sudo apt install packetname
   sudo apt install packetname==1.2.3-1    # specific version
   sudo apt remove packetname
   sudo apt purge packetname    # also deletes configuration files
   ```

   Keep your system clean:
   ```bash
   sudo apt autoremove    # removes not needed dependencies
   sudo apt clean         # clear packet-cache
   ```

   Search and Information:
   ```bash
   apt search packetname
   apt show packetname
   apt policy packetname    # shows repository and versions
   ```

   Mark a packet for not updating:
   ```bash
   sudo apt hold packetname
   sudo apt unhold packetname    # unlock updates again
   ```
3. **Compromised Files (`tar.gz`, ...)**<br>
    Unpack `.tar.gz` (also available via GUI with a right-click)
    ```bash
    tar -xvf your_program.tar.gz

    tar -xvf your_program.tar.gz - C target/folder
    ```

    Unpack `.tar`:
    ```bash
    tar -xvf file.tar
    ```

    Unpack `.tgz` (`tar.gz`):
    ```bash
    tar -xvzf file.tgz
    ```

    Unpack `.tar.bz2`:
    ```bash
    tar -xvjf file.tar.bz2
    ```

    Unpack `.tar.xz`:
    ```bash
    tar -xvJf file.tar.xz
    ```

    Meaning of parameters:
    | Parameter | Meaning |
    | --- | --- |
    | x | extract |
    | v | verbose (show files) |
    | f | file |
    | z | gzip |
    | j | bzip2 |
    | J | xz |

    > Modern `tar` version auto detect the right parameters just use `tar -xf file.tar.gz`

    Unpack ZIP:
    ```bash
    # install program
    sudo apt install unzip

    unzip file.zip

    unzip file.zip -d target/dir 
    ```

    Move to another location:
    ```bash
    sudo mv your_program /opt/your_program
    ```

    Create Symlink to make it global startable:
    ```bash
    sudo ln -s /opt/your_program /usr/local/bin/your_program

    # now you can use it just with
    your_program
    ```

    Create Desktop-Icon:
    ```bash
    nano ~/.local/share/applications/your_program.desktop
    ```

    Add following Content:
    ```bash
    [Desktop Entry]
    Name=your_program
    Exec=/opt/your_program/your_program_binary
    Icon=/opt/your_program/icon.png
    Type=Application
    Categories=Developement;
    ```

    Uninstall = Delete Folder:
    ```bash
    sudo rm -r /opt/your_program
    sudo rm -r /usr/local/bin/your_program
    ```

    Download:
    ```bash
    wget https://example.com/file.tar.gz

    # rename the file during donwload
    wget -O your_program.tar.gz https://example.com/download?ide=123

    # continue download
    wget -c https://example.com/largefile.tar.gz
    ```

    Or downloading with curl:
    ```bash
    curl -LO https://example.com/file.tar.gz

    # -L = follow redirects
    # -O iriginal filename
    ```
4. **Git Projects** (from GitHub for example)<br>
    [See our Git Guide](./Git_Helper.md)
5. **Snap**<br>
    Snap is a package management tool, independent of the used Ubuntut version and runs the program in a own environment which comes with performance decreases.

    Installation and removement:
    ```bash
    sudo snap install code
    sudo snap remove code
    ```

    Which snaps are running?:
    ```bash
    snap list
    ```

    The files are located in:
    ```bash
    ~/snap
    ```

    Check permissions:
    ```bash
    sudo connections code
    ```

    Sometimes a filesystemaccess is missing:
    ```bash
    sudo snap connect code:removable-media
    ```

    Control updates:
    ```bash
    snap refresh --list
    sudo snap refresh
    ```
6. **Flatpak**<br>
    Flatpak is like a community version of snap.

    Setup:
    ```bash
    sudo apt install flatpak
    flatpak remote-add --if-not-exists flathub https://flathub.org/repo/flathub.flatpakrepo
    ```

    Search and install:
    ```bash
    flatpak search blender
    flatpak install flathub org.blender.Blender
    ```

    Check permissions:
    ```bash
    flatpak info --show-permissions org.blender.Blender
    ```

    Clean:
    ```bash
    flatpak uninstall --unused
    ```
7. **Source Build**<br>
    Somtimes you donwload just the source code but have to compile it for your system by yourself. Compiling is the process to convert a program from a more High-Level programming language like C++ to binary machine-code which can be run by your CPU/OS directly.

    Most of following variants have following steps:
    1. Setup (check dependencies, prepare/check compiler, ...)
    2. Compile to machine code / executable
    3. Copy it to `/usr/local/bin`, `/usr/local/lib` or `/usr/local/include` and make it global accessable -> often called "install"

    You can use autotools:
    ```bash
    ./configure --prefix=/usr/local
    make -j$(nproc)
    sudo make install
    ```

    Using CMake (often when compiling software from GitHub):
    ```bash
    cmake -B build -S . -DCMAKE_BUILD_TYPE=Release
    cmake --build build -j$(nproc)
    sudo cmake --install-build

    # Install CMake
    sudo apt install cmake
    ```

    Using Meson/Ninja:
    ```bash
    meson setup build
    ninja -C build
    sudo ninja -C build install

    # Maybe install meson/ninja
    sudo apt install meson ninja-build
    ```

    Find installed files later:
    ```bash
    sudo ldconfig
    which program
    ```


<br><br>

---
### Commands

<br>

> See also [ther terminal chapter](#terminal-guide) for general movement and understanding.

<br>

**Navigation commands:**
- `pwd` -> print working directory
- `ls` -> list files
- `ls -l` -> detailed list
- `ls -a` -> show hidden files
- `cd folder` -> change directory
- `cd ..` -> go up one level
- `cd ~` -> go to home directory
- `cd /` -> go to root

<br><br>

**File and Directory Management:**
- `mkdir foldername` -> create directory
- `rmdir foldername` -> remove empty directory
- `rm file` -> remove file
- `rm -r folder` -> remove folder recursively
- `cp source target` -> copy
- `mv source target` -> move or rename
- `touch file.txt` -> create empty file

<br><br>

**Viewing and Editing Files:**
- `cat file.txt` -> show entire file
- `less file.txt` -> scrollable viewer
- `head file.txt` -> first lines
- `tail file.txt` -> last lines
- `tail -f logfile` -> live log monitoring
- `nano file.txt` -> simple editor
- `vim file.txt` -> advanced editor

<br><br>

**Permissions and Ownership**

Permission structure example:<br>
`-rwxr-xr--`

Meaning:
| Symbol | Meaning |
| ------ | ------- |
| r      | read    |
| w      | write   |
| x      | execute |

User groups:
| Position | Meaning |
| -------- | ------- |
| 1–3      | Owner   |
| 4–6      | Group   |
| 7–9      | Others  |

Commands:
- `chmod +x file` -> make executable
- `chmod 755 file` -> set numeric permissions
- `chown user file` -> change owner
- `chown user:group file` -> change owner and group

<br><br>

**Process Management:**
- `ps` -> list processes
- `ps aux` -> detailed process list
- `top` -> live process viewer
- `htop` -> improved process viewer (install required)
- `kill PID` -> terminate process
- `kill -9 PID` -> force kill
- `jobs` -> background jobs
- `fg` -> bring job to foreground
- `bg` -> send job to background
- `Ctrl + C` -> stop current process
- `Ctrl + Z` -> suspend process

<br><br>

**Useful Shortcuts in Bash:**
- `Tab` -> auto-complete
- `Up Arrow` -> previous command
- `Ctrl + R` -> search command history
- `Ctrl + A` -> move to beginning of line
- `Ctrl + E` -> move to end of line
- `Ctrl + U` -> delete to beginning
- `Ctrl + K` -> delete to end
- `Ctrl + Shift + V` or `Shift + Insert` -> paste cached content
- `!!` -> repeat last command
- `history` -> show command history
- `clear` -> clear screen

<br><br>

**Environment and Variables:**
- `echo $HOME` -> print variable
- `env` -> list environment variables
- `export VAR=value` -> set variable
- `.bashrc` -> user bash configuration file
- `.profile` -> login shell configuration

<br><br>

**Redirection and Pipes:**
- `command > file` -> overwrite output
- `command >> file` -> append output
- `command < file` -> input from file
- `command 2> error.txt` -> redirect errors

Pipes:<br>
`command1 | command2` -> example: `ls -l | grep .txt`

<br><br>

> Important Things to Know:
> - Everything in Linux is treated as a file
> - Root user has full system control
> - Use `sudo` carefully
> - Logs are usually in `/var/log`
> - Hidden files start with `.`
> - Absolute path starts with `/`
> - Relative path does not start with /
>     - They start with `.`, `..` or the Folder/File name directly
> - The shell is not the same as the terminal (see [terminology chapter](#terminal-terminology))
> - TTY is a real console -> GNOME Terminal is a terminal emulator
> - You can run multiple TTY sessions simultaneously.

<br><br>

---
### Interesting Software

- Bitwarden <br>
    Via Ubuntu Software Center
- Git <br>
    ```bash
    sudo apt update
    sudo apt install git
    ```
- VSCode <br>
    Via Ubuntu Software Center
- Anaconda <br>
    Download Installer
    ```bash
    wget https://repo.anaconda.com/archive/Anaconda3-latest-Linux-x86_64.sh
    ```
    Run installer (follow isntructions):
    ```bash
    bash Anaconda3-latest-Linux-x86_64.sh
    ```
    Verification:
    ```bash
    conda --version
    ```
- Python <br>
    Install:
    ```bash
    sudo apt update
    sudo apt install python3 python3-pip
    ```
    Verifiy:
    ```bash
    python3 --version
    pip3 --version
    ```
- Julia <br>
    Installation:
    ```bash
    sudo apt update
    sudo apt install julia
    ```
    Verification:
    ```bash
    julia --version
    ```
    Alternative installation:
    ```bash
    wget https://julialang-s3.julialang.org/bin/linux/x64/1.10/julia-1.10.0-linux-x86_64.tar.gz
    tar -xvzf julia-1.10.0-linux-x86_64.tar.gz
    sudo mv julia-1.10.0 /opt/julia
    sudo ln -s /opt/julia/bin/julia /usr/local/bin/julia
    ```
- C++ (Compiler) <br>
    ```bash
    sudo apt update
    sudo apt install gcc g++
    ```
    Install a specific version:
    ```bash
    sudo apt install gcc-6 g++-6
    ```
    Switiching Versions:
    ```bash
    sudo update-alternatives --install /usr/bin/g++ g++ /usr/bin/g++-6 6
    sudo update-alternatives --install /usr/bin/g++ g++ /usr/bin/g++-9 9

    sudo update-alternatives --config g++
    ```
- Latex <br>
    Install LateX:
    ```bash
    sudo apt update
    sudo apt install texlive-full
    ```
    Install TexStudio:
    ```bash
    sudo apt install texstudio
    ```
- Calculator
    - GNOME Calculator
        ```bash
        sudo apt install gnome-calculator
        ```
    - Qalculate
        ```bash
        sudo apt update
        sudo apt install qalculate-gtk
        ```
        Start with:
        ```bash
        qalculate-gtk
        ```
- Typora
    ```bash
    wget -qO - https://typora.io/linux/public-key.asc | sudo apt-key add -
    sudo add-apt-repository 'deb https://typora.io/linux ./'
    sudo apt update
    sudo apt install typora
    ```



Open:
- Presentation
    - Powerpoint Online
    - LibreOffice Impress
        ```bash
        sudo apt install libreoffice-impress
        ```
    - Marp
        ```bash
        sudo snap install marp
        ```
        Or use the VSCode extension.
    - Or use Google Slides
- Normal Writing (Latex? Word Online)
- Notes (OneNote Online)
- Image Editing (Luminar Neo not available?)
    - [Raw Therapee](https://rawtherapee.com/)
        ```bash
        sudo apt update && sudo apt install rawtherapee
        ```
    - [Shotwell](https://shotwell-project.org/)
        ```bash
        sudo apt update && sudo apt install shotwell
        ```
- PDF Reading / Page-Adding / Signing / Password Protection
    - Okular
        ```bash
        sudo apt update
        sudo apt install okular
        ```
        - Read PDFs
        - Add annotation and sinatures
        - Basic editing
    - LibreOffice Draw
        ```bash
        sudo apt install libreoffice
        ```
        - Add/remove pages
        - Edit PDF content
    - PDF Arranger
        ```bash
        sudo apt install pdfarranger
        ```
        - Merge / split / reorder pages
    - `qpdf` (terminal tool -> for password protection)
        ```bash
        sudo apt install qpdf
        ```
        Encrypt PDF:
        ```bash
        qpdf --encrypt yourpassword yourpassword 256 -- input.pdf output.pdf
        ```



<br><br>

---
### File-System-Structure Explained

In short:
Personal work -> `/home` <br>
System configuration -> `/etc` <br>
Installed programs -> `/usr` <br>
Logs -> `/var/log` <br>
Manual third-party software -> `/opt` <br>
Temporary files -> `/tmp`

<br><br>

Main Top-Level Directories in more detail:

| **Directory** | **Purpose** | **What You Typically Find There** | **Should You Modify It?** |
| --- | --- | --- | --- |
| `/` | Root of the entire file system | Everything starts here | No (critical system area) |
| `/home` | User data | Personal folders (documents, downloads, code projects) | Yes (this is your space) |
| `/root` | Home directory of root user | Root user's personal files | No (unless you are root) |
| `/bin` | Essential user binaries | Basic commands like ls, cp, mv | No |
| `/sbin` | System binaries | System tools like reboot, mount | No |
| `/etc` | System configuration | Config files for system and services | Carefully |
| `/usr` | User programs and libraries | Installed applications, libraries | Usually no |
| `/var` | Variable data | Logs, cache, databases | Usually no |
| `/tmp` | Temporary files | Short-lived temp files | Yes (safe, temporary) |
| `/opt` | Optional third-party software | Manually installed software | Yes (carefully) |
| `/dev` | Device files | Hardware representations (disks, USB) | No |
| `/proc` | Process & kernel info (virtual) | CPU info, running processes | No |
| `/sys` | Kernel & hardware interface (virtual) | System internals | No |
| `/mnt` | Temporary mount points | Mounted drives (manual) | Yes |
| `/media` | Auto-mounted removable media | USB drives, external disks | Yes |
| `/lib` | Essential shared libraries | Required system libraries | No |
| `/boot` | Boot loader files | Kernel, GRUB | No |

<br><br>

Explanation of Important Directories

<br><br>

`/`<br>
This is the root directory. Every file and folder on Linux is located somewhere under this directory.

<br><br>

`/home`<br>
Each user has a folder here. Example:<br>
`/home/tobia`<br>
This is where you store projects, code, downloads, and personal files.<br>
If you are working on C++ projects or GitHub repositories, they usually belong here.

<br><br>

`/root`<br>
This is not the same as `/`. It is the home directory for the root administrator account.

<br><br>

`/bin`<br>
Contains essential command-line programs needed even in recovery mode.

<br><br>

`/etc`<br>
Contains configuration files for the whole system.<br>
Examples:<br>
`/etc/hosts`
`/etc/ssh/`
`/etc/fstab`

If you configure services or networking, this is often where changes are made.

<br><br>

`/usr`<br>
Contains most installed applications.

Subdirectories:
- `/usr/bin` - user programs
- `/usr/lib` - libraries
- `/usr/share` - shared data like icons and documentation

Most software installed via apt goes here automatically.

<br><br>

`/var`<br>
Contains files that change often.

Examples:
- `/var/log` - system logs
- `/var/cache` - cached package data
- `/var/lib` - databases (e.g., for services)

If you troubleshoot errors, logs in /var/log are important.

<br><br>

`/tmp`<br>
Temporary files stored here.<br>
Usually cleared on reboot.

<br><br>

`/opt`<br>
Used for optional or third-party software that is not managed by the system package manager.<br>
Example:<br>
`/opt/google/chrome`

If you manually install software, it often goes here.

<br><br>

`/dev`<br>
Represents hardware as files.<br>
Example:<br>
`/dev/sda` - disk <br>
`/dev/tty` - terminal

You usually don't modify anything here.

<br><br>

`/proc`<br>
Virtual file system providing system and process information.<br>
Example:<br>
`/proc/cpuinfo`<br>
`/proc/meminfo`

It does not store real files on disk.

<br><br>

`/sys`<br>
Similar to /proc but focused on hardware and kernel interaction.

<br><br>

`/mnt` and `/media`<br>
Used for mounting external drives.<br>
`/media` is usually automatic (USB).<br>
`/mnt` is often used manually.


<br><br>

---
### Terminal Guide

- [Terminal Terminology](#terminal-terminology)
- [Understanding TTY](#understanding-tty)
- [Movement in Terminal](#movement-in-terminal)

> Also see [terminal/shell commands (seperate chapter)](#commands).


#### Terminal Terminology


Component summary/overview:

| Component | What It Is | Purpose |
| --- | --- | --- |
| Terminal | Interface | Displays input/output |
| Shell | Program | Interprets commands |
| SSH | Protocol | Secure remote connection |

A **terminal** is a program (a GUI) that lets you interact with the system using text commands (it provides the interface to a shell). The interpreter of these text commands (inside of/at the backend in the terminal) is called a **shell**.<br>
In Ubuntu the default shell is called `bash`. The shell interprets the commands and communicates with the Linux Kernel.<br>
`TTY` originally referred to "teletype" but now refers to text-based console sessions.

<br><br>

**Types of terminals:**

| Type | Name | How to Access | Description |
| --- | --- | --- | --- |
| Virtual Console | tty1–tty6 | `Ctrl` + `Alt` + `F1–F6` | Text-only console running directly on the system. Needed for installing GPU drivers |
| Graphical Terminal Emulator | GNOME Terminal | Applications  -> Terminal | GUI program that emulates a terminal |
| Graphical Terminal Emulator | Konsole | Install KDE | KDE terminal emulator |
| Graphical Terminal Emulator | Xfce Terminal | Xfce desktop | Lightweight terminal emulator |
| Graphical Terminal Emulator | Tilix | `sudo apt install tilix` | Tiling terminal emulator |

Important distinction:
- TTY = virtual console provided by the Linux kernel.
- Terminal Emulator = GUI application that simulates a terminal.


> Some notes to emulators:<br>
> An emulator is a program (or device) that imitates the behavior of another system so that software written for the original system can run unchanged.<br>
> GNOME Terminal pretends to be a VT100/xterm.<br>
> In terminal emulation, it imitates:
> - Character grid display
> - Cursor movement rules
> - Escape sequences
> - Screen clearing
> - Color codes
> - Keyboard behavior
> 
> <br>Programs send special control codes like:
> - Move cursor up
> - Clear screen
> - Change text color
>
> <br>GNOME Terminal must:
> - Parse control sequences
> - Track cursor position
> - Maintain a virtual text grid
> - Render it properly
> - Simulate scrolling behavior
> That is active behavior reproduction -> it is not just a visual interface.

<br><br>

**Types of Shells:**

| Shell | Command | Default in Ubuntu | Description |
| --- | --- | --- | --- |
| Bourne Again Shell | `bash` | Yes | Default Ubuntu shell |
| Dash | `dash` | Used for system scripts | Lightweight POSIX shell |
| Z Shell | `zsh` | No | Advanced interactive shell |
| Fish | `fish` | No | User-friendly interactive shell |
| Korn Shell | `ksh` | No | Older Unix shell |

<br><br>

**Types of Remote Access Protocols:**

| Protocol | Command | Purpose |
| --- | --- | --- |
| SSH | `ssh` | Secure remote shell access |
| Telnet | `telnet` | Unencrypted remote shell (obsolete) |
| Mosh | `mosh` | Mobile-friendly remote shell |

> SSH is a secure network protocol that transports a remote terminal session.

<br><br>

How terminal and shell work together:

Example flow:
1. You open GNOME terminal
2. GNOME terminal starts `bash`
3. You type `ls`
4. bash interprets it
5. The Linux kernel executes it
6. Output appears in the terminal

Remote example:
1. You run `ssh user@server`
2. SSH connects to the remote machine
3. The remote machine starts its default shell (often `bash`)
4. You interact with that shell through your local terminal

<br><br>

#### Understanding TTY

TTY is a text-only terminal/interface to interact with the Linux kernel directly. It is the base interface between the user and the Ubuntu system -> even when having a GUI, the GUI runs on top of a TTY, because TTYs act as the foundational input/output layer.<br>
On top of a TTY, a display server such as XOrg Server or Wayland handles graphical output and input devices, while a display manager like GDM starts the graphical session and login screen, which then launches the desktop environment (most likely GNOME) that provides the windows, panels, and overall graphical user interface running on top of the display server and underlying TTY.


What Usually Happens at Boot:
1. Linux kernel starts
2. System services start
3. The display manager (gdm3) starts
4. It launches the GNOME graphical session.<br>
   That session usually runs on tty1 (modern Ubuntu).

Some concepts to udnerstand this:
| Component | What It Is | Example in Ubuntu |
| --- | --- | --- |
| TTY | Text console | tty1–tty6 |
| Display Manager | Starts graphical login | gdm3 |
| Display Server | Draws windows | Wayland or Xorg |
| Desktop Environment | Full GUI | GNOME |

Controls:
- `Ctrl` + `Alt` + `F1–F6` switches to TTY consoles.
- `Ctrl` + `Alt` + `F1` or `F2` usually returns to graphical session (if a GNOME graphicl session is running).
    - Starting the GUI manually from TTY:
        ```bash
        # check installation of gdm3
        systemctl status gdm3

        # start graphical session
        sudo systemctl start gdm3

        # or you might want to restart it when crashed
        sudo systemctl restart gdm3

        # if not installed, install and start it
        sudo apt update
        sudo apt install ubuntu-desktop

        # you might want to reboot
        sudo reboot
        ```
- Check your current TTY with: `tty`


<br><br>

#### Movement in Terminal

In the terminal you are always at a given path in your file system which is exactly left to your input `current-path> our-input-comes-here`. Of cause you see previous command inputs and can fill them by using the up and down-arrow-keys to get previous commands (sometimes helpful).<br>
Also important to note is that you can use `tab` to autocomplete some commands and paths (for example type a letter and then press `tab` and you will get a auto-completion of a file or folder in your current directory strting with that -> and you can repeat pressing `tab` to get another proposal for auto-completion if there is a file starting also with that).

Now just use `cd` command to move. You can move relative from your current position `./FOLDERNAME` or `FOLDERNAME`. Or use absolute paths `cd /home/username/FOLDER` or `cd ~/data` (`~` is an alias for the user home path).<br>
And to see which files and folders are available use `ls`.

> You can also use relative paths, which are relative from your current path. `.` is the current path and you can do something like: `ls .`. You can also move/get path down in the file-structure relative to your current position using `.YOUR_FOLDER/YOUR_OTHER_FOLDER`. And of course you can also move/get path up relative to your current position `..` -> for example `ls ..`, `../YOUR_FILE` or `../../../FOLDER/FILENAME`.


Paths to remeber:
| Directory        | Meaning                      |
| ---------------- | ---------------------------- |
| `/`              | Root of the file system      |
| `/home`          | User home directories        |
| `/home/username` | Your personal home directory |
| `/etc`           | Configuration files          |
| `/var`           | Logs and variable data       |
| `/usr`           | User programs and libraries  |
| `/bin`           | Essential system binaries    |






