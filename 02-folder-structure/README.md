# 📁 Linux Folder Structure

Understanding the Linux folder structure is one of the most important Linux fundamentals.

Unlike Windows, where files are commonly organized under different drive letters such as:

```text
C:\
D:\
E:\
```

Linux uses a **single hierarchical filesystem** that starts from:

```text
/
```

This `/` directory is called the **root directory** of the filesystem.

Everything in the Linux filesystem exists somewhere below `/`.

---

# Linux Filesystem Structure

A simplified Linux filesystem looks like this:

```text
/
├── bin
├── boot
├── dev
├── etc
├── home
├── lib
├── media
├── mnt
├── opt
├── proc
├── root
├── run
├── sbin
├── srv
├── sys
├── tmp
├── usr
└── var
```

Each directory has a specific purpose.

```text
/       → Root of the filesystem
/bin    → Essential user commands
/boot   → Boot-related files
/dev    → Device files
/etc    → System configuration
/home   → Regular users' home directories
/lib    → Essential libraries
/media  → Removable media
/mnt    → Temporary/manual mount points
/opt    → Optional software
/proc   → Process and kernel information
/root   → Root user's home directory
/run    → Runtime system information
/sbin   → System administration commands
/srv    → Service data
/sys    → Kernel and device information
/tmp    → Temporary files
/usr    → User-space programs and data
/var    → Variable data
```

> **Note:** The exact filesystem layout can vary between Linux distributions. Modern distributions may use **usr-merge**, where directories such as `/bin`, `/sbin`, and `/lib` are integrated with `/usr`.

---

# 1. Understanding the Root Directory `/`

The `/` directory is the starting point of the Linux filesystem.

It is similar to the top level of the filesystem hierarchy.

You can move to `/` using:

```bash
cd /
```

Check your current directory:

```bash
pwd
```

Output:

```text
/
```

List the contents:

```bash
ls
```

For a detailed listing:

```bash
ls -la /
```

---

# 2. Root Directory `/` vs Root User `/root`

These two are often confused.

They are completely different.

```text
/       → Root of the entire filesystem

/root   → Home directory of the root user
```

For example:

```bash
cd /
```

takes you to the filesystem root.

While:

```bash
sudo cd /root
```

does **not** work as expected because `cd` is normally a shell built-in. Instead, you can access `/root` with:

```bash
sudo ls /root
```

Or start a root shell when appropriate:

```bash
sudo -i
```

Then:

```bash
cd /root
```

---

# 3. Absolute Paths

An **absolute path** starts from `/`.

Example:

```text
/home/user/documents/file.txt
```

Another example:

```text
/etc/ssh/sshd_config
```

Another:

```text
/var/log/
```

Because the path starts with `/`, it specifies the location from the root of the filesystem.

Example:

```bash
cd /home
```

---

# 4. Relative Paths

A **relative path** starts from your current directory.

Suppose you are currently here:

```text
/home/user
```

And there is a directory:

```text
/home/user/projects
```

You can use:

```bash
cd projects
```

instead of:

```bash
cd /home/user/projects
```

---

# 5. Important Path Symbols

Linux provides several useful path shortcuts.

## `.` — Current Directory

```bash
.
```

Example:

```bash
ls .
```

---

## `..` — Parent Directory

```bash
..
```

Example:

```bash
cd ..
```

If you are here:

```text
/home/user/projects
```

then:

```bash
cd ..
```

moves you to:

```text
/home/user
```

---

## `~` — Current User's Home Directory

```bash
~
```

Example:

```bash
cd ~
```

---

## `$HOME` — Home Directory Environment Variable

```bash
echo $HOME
```

Example:

```text
/home/user
```

You can also:

```bash
cd $HOME
```

---

# 6. Essential Navigation Commands

## `pwd`

Displays your current working directory.

```bash
pwd
```

Example:

```text
/home/user
```

---

## `ls`

Lists files and directories.

```bash
ls
```

Detailed:

```bash
ls -l
```

Hidden files:

```bash
ls -a
```

Detailed + hidden:

```bash
ls -la
```

Human-readable sizes:

```bash
ls -lh
```

---

## `cd`

Changes the current directory.

```bash
cd /etc
```

Home:

```bash
cd ~
```

Parent:

```bash
cd ..
```

Previous directory:

```bash
cd -
```

---

# 7. Explanation of System Directories

## `/bin`

Traditionally contains essential user command binaries.

Examples include commands such as:

```text
ls
cp
mv
rm
cat
mkdir
pwd
```

Check:

```bash
ls /bin
```

On many modern Linux distributions using usr-merge:

```text
/bin → /usr/bin
```

Check:

```bash
ls -ld /bin
```

---

# 8. `/sbin`

Traditionally contains important system administration commands.

These commands are generally associated with tasks such as:

```text
Filesystem administration
Network administration
System recovery
System configuration
```

Check:

```bash
ls /sbin
```

On usr-merged systems:

```text
/sbin → /usr/sbin
```

Check:

```bash
ls -ld /sbin
```

---

# 9. `/boot`

Contains files required during the system boot process.

Typical contents can include:

```text
Linux kernel
initramfs
Bootloader-related files
```

Check:

```bash
ls -lah /boot
```

You may see files similar to:

```text
vmlinuz-...
initrd.img-...
```

> **Warning:** Do not randomly delete files from `/boot`. Important boot files are required to start Linux.

---

# 10. `/dev`

`/dev` contains device files.

Linux exposes many hardware and virtual devices through file-like interfaces.

Examples:

```text
/dev/sda
/dev/sdb
/dev/null
/dev/zero
/dev/random
/dev/tty
```

List devices:

```bash
ls /dev
```

Check `/dev/null`:

```bash
ls -l /dev/null
```

---

## `/dev/null`

`/dev/null` is a special device that discards data written to it.

Example:

```bash
echo "Hello Linux" > /dev/null
```

Nothing is displayed because the output is discarded.

It is commonly useful when you want to ignore command output.

---

# 11. `/etc`

`/etc` contains system-wide configuration files.

Examples:

```text
/etc/hostname
/etc/hosts
/etc/passwd
/etc/fstab
/etc/ssh/
/etc/systemd/
```

List the directory:

```bash
ls /etc
```

---

## `/etc/hostname`

Contains the system hostname.

```bash
cat /etc/hostname
```

---

## `/etc/hosts`

Contains local hostname-to-IP mappings.

```bash
cat /etc/hosts
```

---

## `/etc/passwd`

Contains information about user accounts.

```bash
cat /etc/passwd
```

It does **not** contain users' plaintext passwords.

---

## `/etc/fstab`

Contains persistent filesystem mount configuration.

```bash
cat /etc/fstab
```

This file can be used to configure filesystems that should be mounted automatically.

---

# 12. `/home`

`/home` contains the home directories of regular users.

Example:

```text
/home
├── ali
├── ahmed
├── khan
└── user
```

If your username is:

```text
khan
```

your home directory may be:

```text
/home/khan
```

Check:

```bash
ls /home
```

Go to your home directory:

```bash
cd ~
```

Check:

```bash
pwd
```

---

# 13. `/lib`

Traditionally contains essential shared libraries and related components required by programs.

Modern distributions using usr-merge may have:

```text
/lib → /usr/lib
```

Check:

```bash
ls -ld /lib
```

Do not manually delete files from `/lib`.

---

# 14. `/media`

`/media` is commonly used by desktop Linux systems for automatically mounted removable devices.

Examples:

```text
USB drives
External disks
CD/DVD media
```

You might see:

```text
/media/user/USB
```

Check:

```bash
ls /media
```

---

# 15. `/mnt`

`/mnt` is traditionally used for temporary or manually mounted filesystems.

For example:

```bash
sudo mount /dev/sdb1 /mnt
```

The mounted filesystem can then be accessed through:

```text
/mnt
```

Check:

```bash
ls /mnt
```

---

# 16. `/opt`

`/opt` is intended for optional or additional application software.

For example:

```text
/opt/my-application/
```

Check:

```bash
ls /opt
```

It can be useful for software that is installed outside the normal distribution-managed software layout.

---

# 17. `/proc`

`/proc` is a **virtual filesystem** that exposes information about processes and the Linux kernel.

It is not a normal directory containing ordinary files stored on your disk.

Examples:

```text
/proc/cpuinfo
/proc/meminfo
/proc/version
/proc/uptime
```

---

## CPU Information

```bash
cat /proc/cpuinfo
```

---

## Memory Information

```bash
cat /proc/meminfo
```

---

## Kernel Information

```bash
cat /proc/version
```

---

## System Uptime

```bash
cat /proc/uptime
```

---

## Process Information

Process IDs are represented by directories under `/proc`.

For example:

```text
/proc/1
/proc/100
/proc/500
```

Check your current shell's process ID:

```bash
echo $$
```

Then:

```bash
ls /proc/$$
```

---

# 18. `/root`

`/root` is the home directory of the root user.

Remember:

```text
/      → Filesystem root
/root  → Root user's home directory
```

Check:

```bash
sudo ls -la /root
```

Normal users may not have permission to access all files inside `/root`.

---

# 19. `/run`

`/run` contains runtime information created while the Linux system is running.

It can contain:

```text
Process information
PID files
Sockets
Runtime service information
Other runtime state
```

Check:

```bash
ls /run
```

`/run` is generally volatile and is recreated during system startup.

---

# 20. `/srv`

`/srv` is intended for data served by system services.

Examples:

```text
/srv/www
/srv/ftp
```

The exact usage depends on the service and system administrator.

Check:

```bash
ls /srv
```

---

# 21. `/sys`

`/sys` is a virtual filesystem that provides information and interfaces related to:

```text
Kernel
Devices
Drivers
Hardware
```

Check:

```bash
ls /sys
```

Important directories include:

```text
/sys/class
/sys/devices
/sys/block
/sys/bus
```

---

# 22. `/tmp`

`/tmp` is used for temporary files.

Create a temporary file:

```bash
touch /tmp/example.txt
```

Check:

```bash
ls /tmp
```

Remove it:

```bash
rm /tmp/example.txt
```

Applications commonly use `/tmp` for temporary data.

> Cleanup behavior for `/tmp` depends on the Linux distribution and system configuration. Do not assume every file is always deleted at reboot.

---

# 23. `/usr`

`/usr` contains a large part of the user-space software and data on a Linux system.

Important directories include:

```text
/usr/bin
/usr/sbin
/usr/lib
/usr/share
/usr/local
```

Check:

```bash
ls /usr
```

---

## `/usr/bin`

Contains many executable programs.

Example:

```bash
ls /usr/bin | head
```

---

## `/usr/sbin`

Contains many system administration programs.

```bash
ls /usr/sbin | head
```

---

## `/usr/lib`

Contains libraries and program-related files.

```bash
ls /usr/lib
```

---

## `/usr/share`

Contains architecture-independent shared data.

Examples:

```text
Documentation
Manual pages
Icons
Locale data
Application data
```

Check:

```bash
ls /usr/share
```

---

## `/usr/local`

Used for software and data installed locally by the administrator.

Common directories include:

```text
/usr/local/bin
/usr/local/sbin
/usr/local/lib
```

Check:

```bash
ls /usr/local
```

---

# 24. `/var`

`/var` contains **variable data**.

This means data that changes while the system operates.

Examples include:

```text
Logs
Caches
Spools
Application data
Package-management data
```

Check:

```bash
ls /var
```

Important directories include:

```text
/var/log
/var/cache
/var/lib
/var/tmp
```

---

# 25. `/var/log`

Contains system and application logs.

Check:

```bash
ls /var/log
```

On systems using traditional syslog files, you may see files such as:

```text
/var/log/syslog
/var/log/auth.log
```

For example:

```bash
sudo less /var/log/syslog
```

The exact log files depend on the Linux distribution and logging system.

---

# 26. `/var/cache`

Contains cached data.

APT-related cache information may be found under:

```text
/var/cache/apt/
```

Check:

```bash
ls /var/cache
```

---

# 27. `/var/lib`

Contains persistent application and system state.

Examples:

```text
/var/lib/dpkg
/var/lib/apt
```

These directories can contain important system data.

> Do not manually delete files from `/var/lib` unless you understand exactly what the application or system component uses them for.

---

# 28. `/var/tmp`

`/var/tmp` is used for temporary files that may need to persist longer than files in `/tmp`.

Example:

```bash
touch /var/tmp/example.txt
```

Check:

```bash
ls /var/tmp
```

Cleanup behavior depends on the Linux distribution and system configuration.

---

# 29. Important System Directories — Quick View

```text
/
├── /bin
│   └── Essential user commands
│
├── /boot
│   └── Boot files
│
├── /dev
│   └── Device files
│
├── /etc
│   └── System configuration
│
├── /home
│   └── User home directories
│
├── /lib
│   └── Essential libraries
│
├── /media
│   └── Removable media
│
├── /mnt
│   └── Manual/temporary mounts
│
├── /opt
│   └── Optional software
│
├── /proc
│   └── Process/kernel information
│
├── /root
│   └── Root user's home
│
├── /run
│   └── Runtime information
│
├── /sbin
│   └── System administration commands
│
├── /srv
│   └── Service data
│
├── /sys
│   └── Kernel/device information
│
├── /tmp
│   └── Temporary files
│
├── /usr
│   └── User-space programs/data
│
└── /var
    └── Variable data
```

---

# 30. User & Application-Specific Directories

Linux users and applications can store configuration and data inside the user's home directory.

For example:

```text
/home/user/
├── Documents/
├── Downloads/
├── Pictures/
├── Videos/
├── .bashrc
├── .config/
└── .local/
```

---

# 31. The `~` Home Shortcut

The `~` symbol represents the current user's home directory.

Check:

```bash
echo ~
```

Example:

```text
/home/user
```

Go there:

```bash
cd ~
```

---

# 32. The `$HOME` Environment Variable

Linux provides the `$HOME` environment variable.

Check it:

```bash
echo $HOME
```

Example:

```text
/home/user
```

You can use:

```bash
cd $HOME
```

This normally takes you to your home directory.

---

# 33. Hidden Files

Linux files beginning with `.` are hidden from normal `ls` output.

Examples:

```text
.bashrc
.profile
.config
.local
```

Normal:

```bash
ls
```

Hidden files:

```bash
ls -a
```

Detailed:

```bash
ls -la
```

---

# 34. `.bashrc`

For users who use Bash, `.bashrc` commonly contains shell configuration.

It may contain:

```text
Aliases
Functions
Shell settings
Prompt configuration
Environment-related configuration
```

View it:

```bash
cat ~/.bashrc
```

Edit it:

```bash
nano ~/.bashrc
```

After making changes:

```bash
source ~/.bashrc
```

---

# 35. `.config`

Many applications store user-specific configuration inside:

```text
~/.config
```

Check:

```bash
ls ~/.config
```

An application might have:

```text
~/.config/application-name/
```

This configuration normally applies to the current user rather than the entire system.

---

# 36. `.local`

User-specific application data is commonly stored inside:

```text
~/.local
```

Important directories can include:

```text
~/.local/bin
~/.local/share
~/.local/state
```

Check:

```bash
ls ~/.local
```

---

# 37. System-Wide vs User-Specific Configuration

A useful way to understand Linux configuration is:

```text
System-wide
     |
     v
/etc
```

while user-specific configuration may be:

```text
Current User
     |
     v
~/.config
```

For example:

```text
/etc/application/
```

may contain system-wide configuration.

While:

```text
~/.config/application/
```

may contain configuration for one user.

The exact locations depend on the application.

---

# 38. Symbolic Links

A **symbolic link**, commonly called a **symlink**, is a special file that points to another file or directory.

It is similar to a shortcut.

Conceptually:

```text
original.txt
     ↑
     |
shortcut.txt
```

Create one:

```bash
ln -s original.txt shortcut.txt
```

---

# 39. Creating a Symbolic Link to a Directory

Suppose you have:

```text
project/
```

Create a symbolic link:

```bash
ln -s project project-link
```

Now:

```text
project/
project-link → project/
```

You can access the directory through:

```bash
cd project-link
```

---

# 40. Checking Symbolic Links

Use:

```bash
ls -l
```

Example:

```text
project-link -> project
```

The `->` indicates that `project-link` points to `project`.

---

# 41. Removing a Symbolic Link

You can remove the link with:

```bash
rm project-link
```

This removes the symbolic link.

It does **not** remove the target directory:

```text
project/
```

---

# 42. Absolute Symbolic Links

Example:

```bash
ln -s /home/user/project project-link
```

The link contains an absolute target path.

Conceptually:

```text
project-link
     |
     └──> /home/user/project
```

---

# 43. Relative Symbolic Links

Example:

```bash
ln -s project project-link
```

The link points to:

```text
project
```

relative to its location.

Relative symlinks can be useful when related directories are moved together.

---

# 44. Broken Symbolic Links

A symbolic link is **broken** when its target no longer exists.

Example:

```text
project-link → project
```

If the target is deleted:

```bash
rm -rf project
```

the symlink remains but points to a missing target.

Check:

```bash
ls -l project-link
```

---

# 45. Finding Symbolic Links

Find symlinks:

```bash
find . -type l
```

Display more information:

```bash
find . -type l -ls
```

---

# 46. Symbolic Links vs Hard Links

Linux supports both symbolic and hard links.

Symbolic link:

```bash
ln -s original.txt symlink.txt
```

Hard link:

```bash
ln original.txt hardlink.txt
```

Conceptually:

```text
Symbolic Link

symlink.txt
     |
     v
original.txt


Hard Link

original.txt ─────┐
                   |
                   v
              Same inode
                   ^
                   |
hardlink.txt ──────┘
```

A symbolic link stores a path to another file.

A hard link refers to the same underlying inode.

For beginners, understand symbolic links first.

---

# 47. Temporary & Volatile Directories

Linux has several directories used for temporary or runtime information.

The most important are:

```text
/tmp
/run
/var/tmp
```

---

# 48. `/tmp` — Temporary Files

`/tmp` is commonly used for temporary data.

Example:

```bash
cd /tmp
```

Create a file:

```bash
touch practice.txt
```

Write data:

```bash
echo "Temporary data" > practice.txt
```

Read it:

```bash
cat practice.txt
```

Remove it:

```bash
rm practice.txt
```

---

# 49. `/run` — Runtime Data

`/run` stores information needed while the system is running.

Examples include:

```text
PID files
Sockets
Runtime service state
Temporary system state
```

Check:

```bash
ls /run
```

Unlike normal persistent directories, `/run` is generally recreated during boot.

---

# 50. `/var/tmp` — Longer-Lived Temporary Data

`/var/tmp` is another location for temporary files.

Example:

```bash
touch /var/tmp/test.txt
```

Compared with `/tmp`, `/var/tmp` is intended for te
