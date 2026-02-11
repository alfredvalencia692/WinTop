# WINTOP - Windows Installation Guide

<div align="center">

![Windows](https://img.shields.io/badge/Windows-7%2B-blue.svg)
![Python](https://img.shields.io/badge/python-3.7+-green.svg)

**Complete installation guide for Windows users**

</div>

---

## 📋 Table of Contents

- [Prerequisites](#prerequisites)
- [Installation Methods](#installation-methods)
- [GPU-Specific Installation](#gpu-specific-installation)
- [Verification](#verification)
- [Troubleshooting](#troubleshooting)
- [Advanced Configuration](#advanced-configuration)

---

## 🔧 Prerequisites

### 1. Python Installation

WINTOP requires Python 3.7 or higher.

#### Check if Python is installed:
```cmd
python --version
```

#### If Python is not installed:

1. **Download Python**:
   - Visit: https://www.python.org/downloads/
   - Download the latest Python 3.x installer

2. **Install Python**:
   - ✅ **IMPORTANT**: Check "Add Python to PATH" during installation
   - Click "Install Now"
   - Wait for installation to complete

3. **Verify installation**:
   ```cmd
   python --version
   pip --version
   ```

### 2. Git Installation (Optional)

For cloning the repository directly.

#### Check if Git is installed:
```cmd
git --version
```

#### If Git is not installed:
- Download from: https://git-scm.com/download/win
- Run installer with default options

---

## 🚀 Installation Methods

### Method 1: Quick Install (Recommended)

#### Step 1: Clone the Repository

**Option A: Using Git**
```cmd
git clone https://github.com/alfredvalencia692/wintop.git
cd wintop
```

**Option B: Download ZIP**
1. Visit: https://github.com/alfredvalencia692/wintop
2. Click "Code" → "Download ZIP"
3. Extract ZIP file
4. Open Command Prompt in extracted folder

#### Step 2: Install Dependencies

**For NVIDIA GPU users:**
```cmd
pip install psutil gputil nvidia-ml-py3 wmi
```

**For AMD GPU users:**
```cmd
pip install psutil wmi
```

**For Intel GPU users:**
```cmd
pip install psutil wmi
```

**For Multiple GPUs:**
```cmd
pip install psutil gputil nvidia-ml-py3 wmi
```

**Minimal (no GPU monitoring):**
```cmd
pip install psutil
```

#### Step 3: Run WINTOP
```cmd
python wintop.py
```

---

### Method 2: Manual Installation

#### Step 1: Create Project Directory
```cmd
mkdir C:\wintop
cd C:\wintop
```

#### Step 2: Download wintop.py
1. Visit: https://github.com/alfredvalencia692/wintop
2. Download `wintop.py` file
3. Save to `C:\wintop`

#### Step 3: Install Dependencies
```cmd
pip install psutil gputil nvidia-ml-py3 wmi
```

#### Step 4: Run WINTOP
```cmd
cd C:\wintop
python wintop.py
```

---

### Method 3: Using requirements.txt

#### Step 1: Clone Repository
```cmd
git clone https://github.com/alfredvalencia692/wintop.git
cd wintop
```

#### Step 2: Install from requirements.txt
```cmd
pip install -r requirements.txt
```

#### Step 3: Run WINTOP
```cmd
python wintop.py
```

---

## 🎮 GPU-Specific Installation

### NVIDIA GPU

NVIDIA GPUs have the best support with full metrics.

#### Option 1: GPUtil (Recommended for beginners)
```cmd
pip install gputil
```

**Pros:**
- Easy to install
- Works immediately
- No additional setup

**Metrics Available:**
- GPU Load (%)
- Memory Usage
- Temperature
- Memory Percentage

#### Option 2: nvidia-ml-py3 (Advanced users)
```cmd
pip install nvidia-ml-py3
```

**Pros:**
- More detailed metrics
- Power consumption
- Fan speed
- Official NVIDIA library

**Metrics Available:**
- GPU Load (%)
- Memory Usage
- Temperature
- Power Draw (Watts)
- Fan Speed (%)

#### Recommended: Install Both
```cmd
pip install gputil nvidia-ml-py3
```

---

### AMD GPU

AMD GPU support on Windows uses WMI (Windows Management Instrumentation).

#### Basic Installation:
```cmd
pip install wmi
```

**Note**: Basic metrics only (GPU name, memory, driver version).

#### Enhanced Metrics:

For temperature and load monitoring, install **OpenHardwareMonitor**:

1. **Download OpenHardwareMonitor**:
   - Visit: https://openhardwaremonitor.org/
   - Download latest version
   - Extract ZIP file

2. **Run OpenHardwareMonitor**:
   - Run `OpenHardwareMonitor.exe`
   - Minimize to system tray
   - Keep it running in background

3. **Run WINTOP**:
   ```cmd
   python wintop.py
   ```
   WINTOP will automatically detect OpenHardwareMonitor and show enhanced metrics!

**Enhanced Metrics Available:**
- GPU Load (%)
- GPU Temperature
- GPU Memory Usage (%)

---

### Intel GPU

Intel integrated GPU support is limited on Windows.

#### Installation:
```cmd
pip install wmi
```

**Metrics Available:**
- GPU Name
- Total Memory
- Driver Version
- Temperature (with OpenHardwareMonitor)

#### Enhanced Metrics:

Follow the same OpenHardwareMonitor steps as AMD GPU above.

---

### Generic/Unknown GPU

Any other GPU will be detected via WMI with basic information.

#### Installation:
```cmd
pip install wmi
```

**Metrics Available:**
- GPU Name
- Driver Version
- Total Memory (if available)

---

## ✅ Verification

### Test Basic Installation
```cmd
python -c "import psutil; print('✓ psutil installed successfully')"
```

### Test GPU Libraries

**Test NVIDIA GPUtil:**
```cmd
python -c "import GPUtil; print('✓ GPUtil installed successfully')"
```

**Test NVIDIA ML:**
```cmd
python -c "import pynvml; print('✓ nvidia-ml-py3 installed successfully')"
```

**Test WMI:**
```cmd
python -c "import wmi; print('✓ wmi installed successfully')"
```

### Complete System Test
```cmd
python wintop.py
```

You should see the startup menu. Press `H` for HTOP mode or `T` for TOP mode.

---

## 🐛 Troubleshooting

### Issue 1: "python is not recognized"

**Problem**: Python not in PATH.

**Solution**:
1. Reinstall Python with "Add to PATH" checked
2. OR manually add to PATH:
   - Search "Environment Variables" in Windows
   - Edit "Path" variable
   - Add: `C:\Users\YourName\AppData\Local\Programs\Python\Python3X`

### Issue 2: "pip is not recognized"

**Problem**: pip not in PATH.

**Solution**:
```cmd
python -m pip install psutil
```

### Issue 3: "Permission denied"

**Problem**: Insufficient permissions.

**Solution**:
1. Run Command Prompt as Administrator
2. OR use `--user` flag:
   ```cmd
   pip install --user psutil gputil wmi
   ```

### Issue 4: GPU not detected

**Problem**: GPU not showing in WINTOP.

**Solution**:

**For NVIDIA:**
1. Install NVIDIA drivers from: https://www.nvidia.com/drivers
2. Install GPUtil: `pip install gputil`
3. Restart computer
4. Run WINTOP and press `G` to toggle GPU

**For AMD:**
1. Install AMD drivers from: https://www.amd.com/drivers
2. Install WMI: `pip install wmi`
3. (Optional) Install OpenHardwareMonitor
4. Run WINTOP

**For Intel:**
1. Install Intel drivers from: https://www.intel.com/content/www/us/en/download-center/home.html
2. Install WMI: `pip install wmi`
3. Run WINTOP

### Issue 5: "Module not found" errors

**Problem**: Dependencies not installed.

**Solution**:
```cmd
pip install psutil gputil nvidia-ml-py3 wmi
```

### Issue 6: Colors not displaying

**Problem**: Terminal doesn't support ANSI colors.

**Solution**:
- Use **Windows Terminal** (Recommended)
  - Download from Microsoft Store
  - Or: https://github.com/microsoft/terminal
- OR use **PowerShell**
- Avoid: Old cmd.exe

### Issue 7: OpenHardwareMonitor not detected

**Problem**: WINTOP not seeing OpenHardwareMonitor data.

**Solution**:
1. Ensure OpenHardwareMonitor is running
2. Run OpenHardwareMonitor as Administrator
3. Restart WINTOP
4. Check if sensors appear in OpenHardwareMonitor's window

### Issue 8: "Access Denied" when killing processes

**Problem**: Insufficient permissions.

**Solution**:
1. Right-click Command Prompt
2. Select "Run as Administrator"
3. Navigate to WINTOP directory
4. Run `python wintop.py`

---

## 🔧 Advanced Configuration

### Creating a Desktop Shortcut

#### Step 1: Create Batch File

Create `wintop.bat` in WINTOP directory:
```batch
@echo off
cd /d "C:\path\to\wintop"
python wintop.py
pause
```

#### Step 2: Create Shortcut
1. Right-click `wintop.bat`
2. Select "Create shortcut"
3. Move shortcut to Desktop
4. (Optional) Change icon

---

### Adding to Windows PATH

To run WINTOP from anywhere:

#### Step 1: Create Launcher Script

Create `wintop.bat`:
```batch
@echo off
python "C:\path\to\wintop\wintop.py" %*
```

#### Step 2: Add to PATH
1. Search "Environment Variables"
2. Edit "Path" variable
3. Add WINTOP directory
4. Click OK

#### Step 3: Test
```cmd
wintop
```

---

### Running on Startup (Optional)

To run WINTOP automatically at startup:

1. Press `Win + R`
2. Type: `shell:startup`
3. Create shortcut to `wintop.bat` in this folder

---

## 📊 Performance Recommendations

### For Best Performance:

1. **Use Windows Terminal**:
   - Better rendering
   - Full color support
   - Smoother updates

2. **Adjust Refresh Rate**:
   - Press `+` for faster updates (more CPU usage)
   - Press `-` for slower updates (less CPU usage)
   - Default: 2 seconds (recommended)

3. **GPU Monitoring**:
   - Press `G` to toggle GPU off if not needed
   - Saves ~0.5% CPU usage

4. **Filter Processes**:
   - Use `F` to filter by process name
   - Reduces rendering overhead

---

## 🎯 Quick Start Guide

### Complete Installation (5 minutes)

```cmd
# 1. Clone repository
git clone https://github.com/alfredvalencia692/wintop.git
cd wintop

# 2. Install dependencies (choose one based on your GPU)
# For NVIDIA:
pip install psutil gputil nvidia-ml-py3 wmi

# For AMD:
pip install psutil wmi

# For Intel:
pip install psutil wmi

# 3. Run WINTOP
python wintop.py

# 4. Press H for HTOP mode or T for TOP mode
```

**That's it!** 🎉

---

## 📞 Getting Help

If you encounter issues:

1. Check [Troubleshooting](#troubleshooting) section above
2. Visit: [GitHub Issues](https://github.com/alfredvalencia692/wintop/issues)
3. Include:
   - Windows version
   - Python version (`python --version`)
   - GPU type
   - Error message
   - Screenshot (if applicable)

---

## 📚 Additional Resources

- **Python for Windows**: https://www.python.org/downloads/windows/
- **pip Documentation**: https://pip.pypa.io/en/stable/
- **OpenHardwareMonitor**: https://openhardwaremonitor.org/
- **NVIDIA Drivers**: https://www.nvidia.com/drivers
- **AMD Drivers**: https://www.amd.com/drivers
- **Intel Drivers**: https://www.intel.com/content/www/us/en/download-center/home.html

---

<div align="center">

**Windows Installation Complete!** ✅

Ready to monitor your system like a pro! 🚀

[← Back to Main README](README.md)

</div>
