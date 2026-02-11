# WINTOP - Linux Installation Guide

<div align="center">

![Linux](https://img.shields.io/badge/Linux-Any%20Distro-yellow.svg)
![Python](https://img.shields.io/badge/python-3.7+-green.svg)

**Complete installation guide for Linux users**

</div>

---

## 📋 Table of Contents

- [Prerequisites](#prerequisites)
- [Installation Methods](#installation-methods)
- [Distribution-Specific Instructions](#distribution-specific-instructions)
- [GPU-Specific Installation](#gpu-specific-installation)
- [Verification](#verification)
- [Troubleshooting](#troubleshooting)
- [Advanced Configuration](#advanced-configuration)

---

## 🔧 Prerequisites

### 1. Python Installation

WINTOP requires Python 3.7 or higher.

#### Check if Python is installed:
```bash
python3 --version
# or
python --version
```

#### If Python is not installed:

See [Distribution-Specific Instructions](#distribution-specific-instructions) below.

### 2. pip Installation

#### Check if pip is installed:
```bash
pip3 --version
# or
pip --version
```

#### If pip is not installed:

**Ubuntu/Debian:**
```bash
sudo apt update
sudo apt install python3-pip
```

**Fedora:**
```bash
sudo dnf install python3-pip
```

**Arch Linux:**
```bash
sudo pacman -S python-pip
```

### 3. Git Installation (Optional)

#### Check if Git is installed:
```bash
git --version
```

#### If Git is not installed:

**Ubuntu/Debian:**
```bash
sudo apt install git
```

**Fedora:**
```bash
sudo dnf install git
```

**Arch Linux:**
```bash
sudo pacman -S git
```

---

## 🚀 Installation Methods

### Method 1: Quick Install (Recommended)

#### Step 1: Clone the Repository

```bash
git clone https://github.com/alfredvalencia692/wintop.git
cd wintop
```

#### Step 2: Install Dependencies

**For NVIDIA GPU users:**
```bash
pip3 install psutil gputil nvidia-ml-py3
```

**For AMD GPU users:**
```bash
pip3 install psutil
# Note: AMD support on Linux is limited without proprietary tools
```

**For Intel GPU users:**
```bash
pip3 install psutil
# Note: Intel GPU monitoring is limited on Linux
```

**Minimal (no GPU monitoring):**
```bash
pip3 install psutil
```

#### Step 3: Run WINTOP
```bash
python3 wintop.py
```

---

### Method 2: User Installation (No sudo required)

If you don't have sudo access or prefer user-level installation:

```bash
# Clone repository
git clone https://github.com/alfredvalencia692/wintop.git
cd wintop

# Install dependencies for current user only
pip3 install --user psutil gputil nvidia-ml-py3

# Run WINTOP
python3 wintop.py
```

---

### Method 3: Virtual Environment (Recommended for developers)

Using virtual environments keeps dependencies isolated:

```bash
# Install venv if not already installed
sudo apt install python3-venv  # Ubuntu/Debian
# or
sudo dnf install python3-virtualenv  # Fedora
# or
sudo pacman -S python-virtualenv  # Arch

# Create virtual environment
python3 -m venv wintop-env

# Activate virtual environment
source wintop-env/bin/activate

# Clone repository
git clone https://github.com/alfredvalencia692/wintop.git
cd wintop

# Install dependencies
pip install psutil gputil nvidia-ml-py3

# Run WINTOP
python wintop.py

# Deactivate when done
deactivate
```

---

## 🐧 Distribution-Specific Instructions

### Ubuntu / Debian / Linux Mint

#### Install Python and dependencies:
```bash
# Update package list
sudo apt update

# Install Python 3 and pip
sudo apt install python3 python3-pip git

# Clone WINTOP
git clone https://github.com/alfredvalencia692/wintop.git
cd wintop

# Install WINTOP dependencies
pip3 install psutil gputil nvidia-ml-py3

# Run WINTOP
python3 wintop.py
```

---

### Fedora / RHEL / CentOS

#### Install Python and dependencies:
```bash
# Install Python 3 and pip
sudo dnf install python3 python3-pip git

# Clone WINTOP
git clone https://github.com/alfredvalencia692/wintop.git
cd wintop

# Install WINTOP dependencies
pip3 install psutil gputil nvidia-ml-py3

# Run WINTOP
python3 wintop.py
```

---

### Arch Linux / Manjaro

#### Install Python and dependencies:
```bash
# Install Python and pip
sudo pacman -S python python-pip git

# Clone WINTOP
git clone https://github.com/alfredvalencia692/wintop.git
cd wintop

# Install WINTOP dependencies
pip install psutil gputil nvidia-ml-py3

# Run WINTOP
python wintop.py
```

---

### openSUSE

#### Install Python and dependencies:
```bash
# Install Python 3 and pip
sudo zypper install python3 python3-pip git

# Clone WINTOP
git clone https://github.com/alfredvalencia692/wintop.git
cd wintop

# Install WINTOP dependencies
pip3 install psutil gputil nvidia-ml-py3

# Run WINTOP
python3 wintop.py
```

---

## 🎮 GPU-Specific Installation

### NVIDIA GPU

NVIDIA GPUs have excellent support on Linux with full metrics.

#### Prerequisites:
1. **Install NVIDIA drivers**:

**Ubuntu/Debian:**
```bash
sudo apt install nvidia-driver-XXX  # Replace XXX with version
# or use automatic detection
sudo ubuntu-drivers autoinstall
```

**Fedora:**
```bash
sudo dnf install akmod-nvidia
```

**Arch:**
```bash
sudo pacman -S nvidia nvidia-utils
```

2. **Verify NVIDIA driver**:
```bash
nvidia-smi
```

If this works, your NVIDIA driver is properly installed.

#### Install WINTOP GPU Support:

**Option 1: GPUtil (Simple)**
```bash
pip3 install gputil
```

**Option 2: nvidia-ml-py3 (Advanced)**
```bash
pip3 install nvidia-ml-py3
```

**Recommended: Both**
```bash
pip3 install gputil nvidia-ml-py3
```

**Metrics Available:**
- GPU Load (%)
- Memory Usage (MB/GB)
- Temperature (°C)
- Power Draw (Watts)
- Fan Speed (%)

---

### AMD GPU

AMD GPU support on Linux is limited without proprietary tools.

#### Basic Installation:
```bash
pip3 install psutil
```

#### Advanced Monitoring (ROCm):

For advanced AMD GPU monitoring, you need ROCm (AMD's GPU compute platform):

**Ubuntu:**
```bash
# Add ROCm repository
wget -q -O - https://repo.radeon.com/rocm/rocm.gpg.key | sudo apt-key add -
echo 'deb [arch=amd64] https://repo.radeon.com/rocm/apt/debian/ ubuntu main' | sudo tee /etc/apt/sources.list.d/rocm.list

# Install ROCm
sudo apt update
sudo apt install rocm-dkms

# Reboot required
sudo reboot
```

**Note**: ROCm support is complex. Basic WINTOP installation will show AMD GPU information but with limited metrics.

---

### Intel GPU

Intel integrated GPU support is minimal on Linux.

#### Basic Installation:
```bash
pip3 install psutil
```

**Metrics Available:**
- GPU detection via sysfs
- Basic GPU information
- Limited or no load/temperature data

---

## ✅ Verification

### Test Basic Installation
```bash
python3 -c "import psutil; print('✓ psutil installed successfully')"
```

### Test GPU Libraries

**Test NVIDIA GPUtil:**
```bash
python3 -c "import GPUtil; print('✓ GPUtil installed successfully')"
```

**Test NVIDIA ML:**
```bash
python3 -c "import pynvml; print('✓ nvidia-ml-py3 installed successfully')"
```

### Complete System Test
```bash
python3 wintop.py
```

Press `H` for HTOP mode or `T` for TOP mode.

---

## 🐛 Troubleshooting

### Issue 1: "python3: command not found"

**Problem**: Python not installed or not in PATH.

**Solution**:
```bash
# Ubuntu/Debian
sudo apt install python3

# Fedora
sudo dnf install python3

# Arch
sudo pacman -S python
```

### Issue 2: "pip3: command not found"

**Problem**: pip not installed.

**Solution**:
```bash
# Ubuntu/Debian
sudo apt install python3-pip

# Fedora
sudo dnf install python3-pip

# Arch
sudo pacman -S python-pip
```

### Issue 3: "Permission denied"

**Problem**: Insufficient permissions.

**Solution 1**: Install for user only
```bash
pip3 install --user psutil gputil nvidia-ml-py3
```

**Solution 2**: Use sudo (not recommended for pip)
```bash
sudo pip3 install psutil gputil nvidia-ml-py3
```

**Solution 3**: Use virtual environment (recommended)
```bash
python3 -m venv env
source env/bin/activate
pip install psutil gputil nvidia-ml-py3
```

### Issue 4: GPU not detected (NVIDIA)

**Problem**: NVIDIA GPU not showing in WINTOP.

**Solution**:

1. **Verify NVIDIA driver**:
```bash
nvidia-smi
```

2. **Install GPU libraries**:
```bash
pip3 install gputil nvidia-ml-py3
```

3. **Check for errors**:
```bash
python3 -c "import pynvml; pynvml.nvmlInit(); print('NVIDIA GPU detected')"
```

### Issue 5: "Module not found" errors

**Problem**: Dependencies not installed correctly.

**Solution**:
```bash
pip3 install --upgrade psutil gputil nvidia-ml-py3
```

### Issue 6: Colors not displaying

**Problem**: Terminal doesn't support ANSI colors.

**Solution**:
Most modern Linux terminals support colors by default. If not:
```bash
export TERM=xterm-256color
```

Add to `~/.bashrc` to make permanent:
```bash
echo 'export TERM=xterm-256color' >> ~/.bashrc
source ~/.bashrc
```

### Issue 7: "Access Denied" when killing processes

**Problem**: Insufficient permissions.

**Solution**:
```bash
sudo python3 wintop.py
```

Or run WINTOP normally and only use sudo when killing protected processes.

### Issue 8: Import error with nvidia-ml-py3

**Problem**: NVIDIA ML library not compatible with driver.

**Solution**:
```bash
# Uninstall and reinstall
pip3 uninstall nvidia-ml-py3
pip3 install nvidia-ml-py3

# Or use GPUtil only
pip3 install gputil
```

---

## 🔧 Advanced Configuration

### Creating an Alias

Add to `~/.bashrc` or `~/.zshrc`:

```bash
alias wintop='python3 ~/wintop/wintop.py'
```

Then reload:
```bash
source ~/.bashrc  # or source ~/.zshrc
```

Now you can run:
```bash
wintop
```

---

### Creating a Desktop Entry

Create `~/.local/share/applications/wintop.desktop`:

```ini
[Desktop Entry]
Name=WINTOP
Comment=System Monitor
Exec=gnome-terminal -- python3 /path/to/wintop/wintop.py
Icon=utilities-system-monitor
Terminal=true
Type=Application
Categories=System;Monitor;
```

Replace `/path/to/wintop/wintop.py` with actual path.

---

### Running as System Service (Advanced)

Create `/etc/systemd/system/wintop.service`:

```ini
[Unit]
Description=WINTOP System Monitor
After=network.target

[Service]
Type=simple
User=your-username
WorkingDirectory=/path/to/wintop
ExecStart=/usr/bin/python3 /path/to/wintop/wintop.py
Restart=on-failure

[Install]
WantedBy=multi-user.target
```

Enable and start:
```bash
sudo systemctl daemon-reload
sudo systemctl enable wintop
sudo systemctl start wintop
```

---

### Setting Up as Launcher

**For GNOME:**
1. Press `Super` key
2. Search "wintop"
3. Right-click → "Add to Favorites"

**For KDE:**
1. Right-click Desktop
2. "Add Widget" → "Application Launcher"
3. Configure to launch WINTOP

---

## 📊 Performance Recommendations

### For Best Performance:

1. **Use Modern Terminal**:
   - GNOME Terminal (recommended)
   - Konsole
   - Alacritty (fastest)
   - Terminator

2. **Adjust Refresh Rate**:
   - Press `+` for faster updates (more CPU)
   - Press `-` for slower updates (less CPU)
   - Default: 2 seconds

3. **GPU Monitoring**:
   - Press `G` to toggle if not needed
   - Saves ~0.5% CPU

4. **Minimal Installation**:
```bash
pip3 install psutil  # Only if GPU not needed
```

---

## 🎯 Quick Start Guide

### Complete Installation (5 minutes)

**Ubuntu/Debian:**
```bash
# Install prerequisites
sudo apt update
sudo apt install python3 python3-pip git -y

# Clone and setup
git clone https://github.com/alfredvalencia692/wintop.git
cd wintop
pip3 install psutil gputil nvidia-ml-py3

# Run
python3 wintop.py
```

**Arch Linux:**
```bash
# Install prerequisites
sudo pacman -S python python-pip git

# Clone and setup
git clone https://github.com/alfredvalencia692/wintop.git
cd wintop
pip install psutil gputil nvidia-ml-py3

# Run
python wintop.py
```

**Fedora:**
```bash
# Install prerequisites
sudo dnf install python3 python3-pip git -y

# Clone and setup
git clone https://github.com/alfredvalencia692/wintop.git
cd wintop
pip3 install psutil gputil nvidia-ml-py3

# Run
python3 wintop.py
```

---

## 🔐 Security Considerations

### Running with Elevated Privileges

Some features (killing protected processes) require root:

```bash
sudo python3 wintop.py
```

**Security Note**: Only run with sudo when necessary.

### Alternative: Using capabilities

Grant specific capabilities without full root:

```bash
sudo setcap cap_kill=ep $(which python3)
```

**Warning**: This allows Python to kill any process. Use with caution.

---

## 📞 Getting Help

If you encounter issues:

1. Check [Troubleshooting](#troubleshooting) section above
2. Visit: [GitHub Issues](https://github.com/alfredvalencia692/wintop/issues)
3. Include:
   - Linux distribution and version
   - Python version (`python3 --version`)
   - GPU type (if applicable)
   - Output of `nvidia-smi` (NVIDIA users)
   - Error message
   - Screenshot (if applicable)

---

## 📚 Additional Resources

- **Python Documentation**: https://docs.python.org/3/
- **pip Documentation**: https://pip.pypa.io/en/stable/
- **NVIDIA CUDA Toolkit**: https://developer.nvidia.com/cuda-toolkit
- **ROCm (AMD)**: https://rocmdocs.amd.com/
- **psutil Documentation**: https://psutil.readthedocs.io/

---

<div align="center">

**Linux Installation Complete!** ✅

Ready to monitor your system! 🐧

[← Back to Main README](README.md)

</div>
