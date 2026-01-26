# Podman Installation and Setup Guide

## Table of Contents
- [What is Podman?](#what-is-podman)
- [Windows Installation](#windows-installation)
- [Linux Installation](#linux-installation)
- [macOS Installation](#macos-installation)
- [Podman Desktop Setup](#podman-desktop-setup)
- [Verification](#verification)
- [Basic Commands](#basic-commands)

---

## What is Podman?

Podman is a daemonless container engine for developing, managing, and running OCI Containers on your Linux, Windows, or macOS system. Containers can either be run as root or in rootless mode.

**Key Features:**
- Daemonless architecture (no background service required)
- Drop-in replacement for Docker CLI
- Rootless containers for better security
- Pod support (similar to Kubernetes)
- Compatible with Docker images and containers

---

## Windows Installation

### Prerequisites
- Windows 10/11 (64-bit)
- Windows Subsystem for Linux (WSL2) - Required
- Administrator privileges

### Method 1: Using Podman Desktop (Recommended for Windows)

1. **Download Podman Desktop**
   - Visit [Podman Desktop Official Website](https://podman-desktop.io/)
   - Click on "Download for Windows"
   - Download the `.exe` installer

2. **Install Podman Desktop**
   - Run the downloaded installer
   - Follow the installation wizard
   - Podman Desktop will automatically install Podman CLI as well

3. **Initial Setup**
   - Launch Podman Desktop
   - The application will detect if WSL2 is installed
   - If WSL2 is not installed, Podman Desktop will guide you through the installation
   - Podman Desktop will create and initialize a Podman machine automatically

### Method 2: Using Windows Installer (CLI Only)

1. **Enable WSL2**
   ```powershell
   # Open PowerShell as Administrator
   wsl --install
   ```
   
2. **Restart your computer** after WSL installation

3. **Download Podman**
   - Visit [Podman Releases](https://github.com/containers/podman/releases)
   - Download the latest `.msi` installer for Windows

4. **Install Podman**
   - Run the `.msi` installer
   - Follow the installation wizard
   - Choose installation directory (default is recommended)

5. **Initialize Podman Machine**
   ```powershell
   # Open PowerShell or Command Prompt
   podman machine init
   podman machine start
   ```

### Method 3: Using Chocolatey

```powershell
# Install Chocolatey if not already installed
# Visit https://chocolatey.org/install for instructions

# Install Podman
choco install podman-desktop

# Or install CLI only
choco install podman-cli
```

### Windows-Specific Configuration

1. **Set up Podman Machine**
   ```powershell
   # Initialize a new machine (if not done automatically)
   podman machine init --cpus 2 --memory 2048 --disk-size 50

   # Start the machine
   podman machine start

   # Check machine status
   podman machine list
   ```

2. **Configure Resources** (Optional)
   ```powershell
   # Stop the machine first
   podman machine stop

   # Remove existing machine
   podman machine rm

   # Create new machine with custom resources
   podman machine init --cpus 4 --memory 4096 --disk-size 100

   # Start the machine
   podman machine start
   ```

3. **Set up Rootful Mode** (Optional)
   ```powershell
   podman machine set --rootful
   ```

---

## Linux Installation

### Ubuntu/Debian

```bash
# Update package index
sudo apt update

# Install Podman
sudo apt install -y podman

# For latest version, use official repository
sudo sh -c "echo 'deb http://download.opensuse.org/repositories/devel:/kubic:/libpod:/stable/xUbuntu_$(lsb_release -rs)/ /' > /etc/apt/sources.list.d/devel:kubic:libpod:stable.list"

wget -nv https://download.opensuse.org/repositories/devel:kubic:libpod:stable/xUbuntu_$(lsb_release -rs)/Release.key -O- | sudo apt-key add -

sudo apt update
sudo apt install -y podman
```

### Fedora

```bash
# Podman is pre-installed on Fedora 31+
# To update or install:
sudo dnf install -y podman
```

### CentOS/RHEL

```bash
# RHEL 8/CentOS 8
sudo dnf install -y podman

# RHEL 7/CentOS 7
sudo yum install -y podman
```

### Arch Linux

```bash
sudo pacman -S podman
```

### openSUSE

```bash
sudo zypper install podman
```

### Linux Post-Installation (Rootless Setup)

```bash
# Enable user namespaces (if required)
sudo sysctl -w kernel.unprivileged_userns_clone=1

# Configure subuid and subgid
sudo usermod --add-subuids 100000-165535 --add-subgids 100000-165535 $USER

# Enable podman socket (optional, for Docker compatibility)
systemctl --user enable --now podman.socket

# Set up Docker alias (optional)
echo "alias docker=podman" >> ~/.bashrc
source ~/.bashrc
```

---

## macOS Installation

### Method 1: Using Homebrew (Recommended)

```bash
# Install Homebrew if not already installed
# Visit https://brew.sh for instructions

# Install Podman
brew install podman

# Initialize Podman machine
podman machine init

# Start the machine
podman machine start
```

### Method 2: Using Podman Desktop

1. **Download Podman Desktop**
   - Visit [Podman Desktop Official Website](https://podman-desktop.io/)
   - Click on "Download for macOS"
   - Download the `.dmg` file

2. **Install Podman Desktop**
   - Open the downloaded `.dmg` file
   - Drag Podman Desktop to Applications folder
   - Launch Podman Desktop
   - Follow the setup wizard to install Podman CLI and initialize machine

### macOS-Specific Configuration

```bash
# Configure machine resources
podman machine stop
podman machine rm

# Create machine with custom settings
podman machine init --cpus 4 --memory 4096 --disk-size 100

# Start the machine
podman machine start

# Check machine info
podman machine info
```

---

## Podman Desktop Setup

Podman Desktop provides a graphical interface for managing containers, similar to Docker Desktop.

### Installation

**Windows:**
- Download from [podman-desktop.io](https://podman-desktop.io/)
- Run the `.exe` installer
- Launch Podman Desktop

**macOS:**
- Download from [podman-desktop.io](https://podman-desktop.io/)
- Install the `.dmg` file
- Open from Applications

**Linux:**
```bash
# Flatpak (recommended)
flatpak install flathub io.podman_desktop.PodmanDesktop

# Or download .AppImage from website
chmod +x Podman-Desktop-*.AppImage
./Podman-Desktop-*.AppImage
```

### Podman Desktop Features

1. **Dashboard**
   - Overview of running containers
   - Resource usage statistics
   - Quick actions

2. **Container Management**
   - Start, stop, restart containers
   - View logs
   - Access container shell
   - Port mapping configuration

3. **Image Management**
   - Pull images from registries
   - Build images from Dockerfile
   - Push images to registries
   - Search for images

4. **Pod Management**
   - Create and manage pods
   - Group containers together
   - Kubernetes-style pod definitions

5. **Volume Management**
   - Create and manage volumes
   - Inspect volume contents
   - Mount volumes to containers

6. **Settings**
   - Configure Podman machine
   - Registry authentication
   - Proxy settings
   - Resource limits

### Windows-Specific Podman Desktop Setup

1. **First Launch**
   - Open Podman Desktop
   - Click on "Get Started"
   - Podman Desktop will check for prerequisites

2. **WSL2 Setup** (if not installed)
   - Podman Desktop will prompt to install WSL2
   - Click "Install WSL2"
   - Follow the prompts and restart if required

3. **Podman Machine Creation**
   - Click "Create Podman Machine"
   - Configure resources:
     - CPUs: 2-4 (recommended)
     - Memory: 2048-4096 MB
     - Disk: 50-100 GB
   - Click "Create"
   - Wait for initialization (may take a few minutes)

4. **Start the Machine**
   - Click "Start" on the Podman Machine card
   - Wait for the machine to start (green status)

5. **Configure Docker Compatibility** (Optional)
   - Go to Settings → Preferences
   - Enable "Docker Compatibility Mode"
   - This creates a `docker` command alias to `podman`

6. **Test the Setup**
   - Go to Dashboard
   - Click "Images" → "Pull"
   - Search for "hello-world"
   - Pull and run the image

---

## Verification

### Verify Installation

```bash
# Check Podman version
podman --version

# Check system info
podman info

# Run a test container
podman run hello-world

# List running containers
podman ps

# List all containers
podman ps -a

# List images
podman images
```

### Windows Verification

```powershell
# Check machine status
podman machine list

# Check machine is running
podman machine ssh -- echo "Connection successful"

# Test container
podman run --rm hello-world
```

---

## Basic Commands

### Container Operations

```bash
# Run a container
podman run -d --name mynginx -p 8080:80 nginx

# List running containers
podman ps

# Stop a container
podman stop mynginx

# Start a container
podman start mynginx

# Remove a container
podman rm mynginx

# View container logs
podman logs mynginx

# Execute command in container
podman exec -it mynginx /bin/bash
```

### Image Operations

```bash
# Pull an image
podman pull nginx

# List images
podman images

# Remove an image
podman rmi nginx

# Build an image from Dockerfile
podman build -t myapp:latest .

# Tag an image
podman tag myapp:latest myregistry.com/myapp:v1

# Push an image
podman push myregistry.com/myapp:v1
```

### Volume Operations

```bash
# Create a volume
podman volume create myvolume

# List volumes
podman volume ls

# Inspect a volume
podman volume inspect myvolume

# Remove a volume
podman volume rm myvolume

# Use volume with container
podman run -v myvolume:/data nginx
```

### Pod Operations

```bash
# Create a pod
podman pod create --name mypod -p 8080:80

# Add container to pod
podman run -d --pod mypod nginx

# List pods
podman pod ps

# Stop a pod
podman pod stop mypod

# Remove a pod
podman pod rm mypod
```

### Docker Compatibility

```bash
# Create Docker alias (Linux/macOS)
alias docker=podman

# Windows (PowerShell - add to profile)
Set-Alias -Name docker -Value podman

# Enable Docker socket compatibility (Linux)
systemctl --user enable --now podman.socket
export DOCKER_HOST=unix:///run/user/$UID/podman/podman.sock
```

---

## Troubleshooting

### Windows Issues

**Machine won't start:**
```powershell
# Check WSL2 status
wsl --list --verbose

# Restart WSL
wsl --shutdown

# Recreate machine
podman machine stop
podman machine rm
podman machine init
podman machine start
```

**Permission issues:**
```powershell
# Run PowerShell as Administrator
podman machine set --rootful
```

### Linux Issues

**Rootless configuration:**
```bash
# Check user namespaces
cat /proc/sys/kernel/unprivileged_userns_clone

# Enable if disabled
echo 'kernel.unprivileged_userns_clone=1' | sudo tee /etc/sysctl.d/userns.conf
sudo sysctl -p /etc/sysctl.d/userns.conf
```

### General Issues

**Network connectivity:**
```bash
# Restart Podman (Linux)
systemctl --user restart podman

# Restart machine (Windows/macOS)
podman machine restart
```

---

## Additional Resources

- [Official Podman Documentation](https://docs.podman.io/)
- [Podman Desktop Documentation](https://podman-desktop.io/docs)
- [Podman GitHub Repository](https://github.com/containers/podman)
- [Podman Tutorial](https://docs.podman.io/en/latest/Tutorial.html)
- [Migration from Docker](https://docs.podman.io/en/latest/Tutorials/docker_to_podman.html)

---

## Quick Reference

| Task | Command |
|------|---------|
| Pull image | `podman pull <image>` |
| Run container | `podman run <image>` |
| List containers | `podman ps` |
| Stop container | `podman stop <container>` |
| Remove container | `podman rm <container>` |
| List images | `podman images` |
| Remove image | `podman rmi <image>` |
| View logs | `podman logs <container>` |
| Execute command | `podman exec -it <container> <command>` |
| Build image | `podman build -t <tag> .` |
| Create pod | `podman pod create --name <name>` |
| Machine status | `podman machine list` |
| Start machine | `podman machine start` |
| Stop machine | `podman machine stop` |

---

**Happy Containerizing! 🚀**
