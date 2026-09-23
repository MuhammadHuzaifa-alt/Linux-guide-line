# 🐧 Setup Linux Environment on Windows and macOS

This guide explains how to set up a Linux environment on:

- 🪟 Windows
- 🍎 macOS

The goal is to create a Linux environment for learning Linux commands, shell scripting, development, Docker, DevOps, and system administration.

---

# 📚 Table of Contents

- [1. Linux Setup on Windows](#1-linux-setup-on-windows)
  - [1.1 Windows Subsystem for Linux (WSL)](#11-windows-subsystem-for-linux-wsl)
  - [1.2 Install Ubuntu with WSL](#12-install-ubuntu-with-wsl)
  - [1.3 Verify WSL](#13-verify-wsl)
  - [1.4 Update Ubuntu](#14-update-ubuntu)
  - [1.5 Install Development Tools](#15-install-development-tools)
  - [1.6 Access Windows Files from Linux](#16-access-windows-files-from-linux)
  - [1.7 Access Linux Files from Windows](#17-access-linux-files-from-windows)
  - [1.8 Useful WSL Commands](#18-useful-wsl-commands)
  - [1.9 Virtual Machine Alternative](#19-virtual-machine-alternative)
- [2. Linux Setup on macOS](#2-linux-setup-on-macos)
  - [2.1 Virtual Machine](#21-virtual-machine)
  - [2.2 Install Ubuntu](#22-install-ubuntu)
  - [2.3 Multipass](#23-multipass)
  - [2.4 Docker Linux Environment](#24-docker-linux-environment)
- [3. Verify Linux Environment](#3-verify-linux-environment)
- [4. Recommended Tools](#4-recommended-tools)
- [5. Basic Linux Commands](#5-basic-linux-commands)
- [6. Troubleshooting](#6-troubleshooting)
- [7. Useful References](#7-useful-references)

---

# 1. Linux Setup on Windows

Windows does not use the Linux kernel as its normal operating-system kernel.

However, Windows provides several ways to work with Linux:

```text
Windows
│
├── WSL 2 ⭐ Recommended
│
├── Virtual Machine
│   ├── VirtualBox
│   └── VMware
│
└── Docker
