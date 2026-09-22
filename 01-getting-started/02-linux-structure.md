# Linux Structure 🐧

Linux can be understood as a set of layers. Each layer has a specific responsibility.

## Linux Architecture

```text
┌──────────────────────────────┐
│            User              │
└──────────────┬───────────────┘
               ↓
┌──────────────────────────────┐
│        Applications          │
│  VS Code, Python, Browser    │
└──────────────┬───────────────┘
               ↓
┌──────────────────────────────┐
│       Shell / Terminal       │
│            Bash              │
└──────────────┬───────────────┘
               ↓
┌──────────────────────────────┐
│        Linux Kernel          │
│ CPU • Memory • Processes     │
│ Filesystem • Devices • Net   │
└──────────────┬───────────────┘
               ↓
┌──────────────────────────────┐
│           Hardware           │
│ CPU • RAM • Disk • Network   │
│ Keyboard • Mouse • GPU       │
└──────────────────────────────┘
