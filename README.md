# WINTOP - Cross-Platform System Monitor

<div align="center">

![Version](https://img.shields.io/badge/version-2.5-blue.svg)
![Platform](https://img.shields.io/badge/platform-Windows%20%7C%20Linux-lightgrey.svg)
![Python](https://img.shields.io/badge/python-3.7+-green.svg)
![License](https://img.shields.io/badge/license-MIT-orange.svg)

**A powerful, interactive system monitoring tool inspired by Linux's `htop` and `top` commands**

[Features](#features) • [Installation](#installation) • [Usage](#usage) • [Screenshots](#screenshots) • [Contributing](#contributing)

</div>

---

## 🌟 Overview

WINTOP is a feature-rich, cross-platform system monitoring tool that brings the power of Linux's beloved `htop` to Windows while maintaining full Linux compatibility. Monitor your system's CPU, memory, disk, network, and GPU usage in real-time with an elegant, colorful interface.

Created by **Frank Gacxs**  
Repository: [https://github.com/alfredvalencia692/wintop](https://github.com/alfredvalencia692/wintop)

---

## ✨ Features

### 🖥️ Core Monitoring

- **CPU Monitoring**: Per-core usage with colorful progress bars and frequency display
- **Memory & Swap**: Real-time memory usage tracking with visual indicators
- **Disk Usage**: Storage space monitoring with I/O statistics
- **Network I/O**: Network traffic monitoring (sent/received bytes)
- **GPU Monitoring**: Multi-vendor GPU support (NVIDIA, AMD, Intel)
- **Process Management**: View, filter, sort, and manage running processes

### 🎮 GPU Support

- ✅ **NVIDIA**: Full metrics (load, memory, temperature, power, fan speed)
- ✅ **AMD**: Basic to advanced metrics (via WMI on Windows)
- ✅ **Intel**: Basic metrics (integrated graphics support)
- ✅ **Multi-GPU**: Detect and monitor multiple GPUs simultaneously

### 🎛️ Process Controls

- **Sort Options**: Sort by CPU, Memory, PID, or Name
- **Kill Process**: Terminate processes by PID with confirmation
- **Start Process**: Launch new applications directly from WINTOP
- **Filter**: Filter processes by name for focused monitoring
- **Pagination**: Navigate through large process lists easily

### 🎨 Display Modes

- **TOP Mode**: Simple, clean interface (like traditional `top`)
- **HTOP Mode**: Colorful, detailed interface with visual progress bars
- **Color Coding**: Resource usage color-coded (green → yellow → red)
- **Live Updates**: Configurable refresh rate (1-10 seconds)

### 🔧 Advanced Features

- Real-time updates with adjustable refresh rate
- Multi-page process view with navigation
- Process filtering by name
- Vendor-specific GPU color coding
- Temperature monitoring with alerts
- Cross-platform compatibility (Windows & Linux)
- Minimal resource usage (<1% CPU overhead)

---

## 📋 Requirements

### System Requirements

- **Operating System**: Windows 7+ or Linux (any modern distribution)
- **Python**: Version 3.7 or higher
- **RAM**: 50MB minimum
- **Disk Space**: 10MB

### Python Dependencies

- **psutil** (required) - System and process monitoring
- **gputil** (optional) - NVIDIA GPU monitoring
- **nvidia-ml-py3** (optional) - Advanced NVIDIA GPU metrics
- **wmi** (Windows only) - AMD, Intel, and generic GPU support

---

## 🚀 Installation

### Quick Install

Choose your platform:

- **Windows**: See [Windows Installation Guide](INSTALL_WINDOWS.md)
- **Linux**: See [Linux Installation Guide](INSTALL_LINUX.md)

### Basic Installation (All Platforms)

```bash
# Clone the repository
git clone https://github.com/alfredvalencia692/wintop.git
cd wintop

# Install required dependencies
pip install psutil

# Run WINTOP
python wintop.py
```

### Full Installation (with GPU support)

**Windows:**

```bash
pip install psutil gputil nvidia-ml-py3 wmi
```

**Linux:**

```bash
pip install psutil gputil nvidia-ml-py3
```

For detailed installation instructions, please refer to:

- [Windows Installation Guide](INSTALL_WINDOWS.md)

**OPTIONAL:**

- If you want to install on linux or you can just use the HTOP pkg
 ```bash
 Ubuntu/Debian:
 sudo apt install htop
 ```
 ```bash
 Fedora:
 sudo dnf install htop
 ```
 ```bash
 CentOS/RHEL(8+):
 sudo dnf install htop
 ```
 ```bash
 Older CentOS:
 sudo yum install epel-release
 sudo yum install htop
 ```
 ```bash
 Arch Linux/Manjaro:
 sudo pacman -S htop
 ```
 ```bash
 openSUSE:
 sudo zypper install htop
 ```

 then after installation just type

 ```bash
 htop
 ```

- Or else going to Wintop:
- [Linux Installation Guide](INSTALL_LINUX.md)

---

## 🎯 Usage

### Starting WINTOP

```bash
python wintop.py
```

You'll be greeted with a menu to choose your display style:

- **[T]** - TOP style (simple, clean)
- **[H]** - HTOP style (colorful, detailed)
- **[Q]** - Quit

### Keyboard Controls

#### Navigation

- `N` - Next page
- `P` - Previous page

#### Sorting

- `C` - Sort by CPU usage
- `M` - Sort by Memory usage

#### Actions

- `K` - Kill process (requires PID)
- `S` - Start new process
- `F` - Filter processes by name

#### Display

- `T` - Switch to TOP style
- `H` - Switch to HTOP style
- `G` - Toggle GPU monitoring on/off

#### Other

- `+` or `=` - Increase refresh rate (faster updates)
- `-` - Decrease refresh rate (slower updates)
- `Q` - Quit WINTOP

### Examples

#### Kill a Process

1. Press `K`
2. Enter the PID of the process (e.g., `1234`)
3. Confirm or type `cancel` to abort

#### Start a Process

1. Press `S`
2. Enter command (e.g., `notepad`, `calc`, `chrome`)
3. Process launches in a new window

#### Filter Processes

1. Press `F`
2. Enter process name (e.g., `python`, `chrome`)
3. View only matching processes
4. Press `F` again and type `clear` to remove filter

#### Adjust Refresh Rate

- Press `+` to refresh faster (minimum 1 second)
- Press `-` to refresh slower (maximum 10 seconds)

---

## 📸 Screenshots

### MAIN

```
╔════════════════════════════════════════════════════════════════════╗
║  WINTOP - Windows System Monitor v2.5 (Multi-GPU)                  ║
║  Github - https://github.com/alfredvalencia692/wintop              ║
╚════════════════════════════════════════════════════════════════════╝

  [T] - Display in TOP style (simple, clean)
  [H] - Display in HTOP style (colorful, detailed)
  [Q] - Quit

──────────────────────────────────────────────────────────────────────
GPU Support Status:
  NVIDIA: ✗ (Full metrics)
  AMD:    ⚠
  Intel:  ⚠

  For better GPU monitoring:
    NVIDIA: pip install gputil (or nvidia-ml-py3)
    AMD/Intel: Install OpenHardwareMonitor for advanced metrics
    Download: https://openhardwaremonitor.org/
──────────────────────────────────────────────────────────────────────

  Select your option:
```

### HTOP Mode (Colorful)

```
╔══════════════════════════════════════════════════════════╗
║ WINTOP - Windows System Process Monitor (Multi-GPU)     ║
╚══════════════════════════════════════════════════════════╝

CPU (8 cores @ 3600MHz)
   1 [████████████░░░░░░░░░░] 48.5%      5 [██████░░░░░░░░░░░░░░░] 24.2%
   2 [███████░░░░░░░░░░░░░░░] 28.3%      6 [████░░░░░░░░░░░░░░░░░] 16.7%
   3 [██████████░░░░░░░░░░░░] 40.1%      7 [███░░░░░░░░░░░░░░░░░░] 12.5%
   4 [█████████████░░░░░░░░░] 52.8%      8 [█████░░░░░░░░░░░░░░░░] 20.4%

Mem [████████████████░░░░░░░░░░░░░░] 12.5GB/32.0GB (39.1%)
Dsk [██████████░░░░░░░░░░░░░░░░░░░░] 450.2GB/1.0TB (45.0%)

GPU0 [NVIDIA] [████████████░░░░░░░░░░░] 45.2% 68°C NVIDIA RTX 4090
              [████████░░░░░░░░░░░░░░░] 8192MB/24576MB (33.3%)

Tasks: 245 (5 run, 230 sleep)   Uptime: 2:15:30   Sort: CPU   Page: 1/10
```

### TOP Mode (Simple)

```
wintop - 14:30:45 up 2:15:30, 245 processes
Tasks: 5 running, 230 sleeping, 0 stopped, 0 zombie
CPU(s): 45.2% total @ 3600MHz
MiB Mem : 32.0GB total, 12.5GB used, 19.5GB free
Disk C:: 450.2GB/1.0TB (45.0%)
GPU 0 [NVIDIA] (NVIDIA RTX 4090): 45.2% load, 8192MB/24576MB, 68°C

PID      USER         CPU%     MEM%     MEMORY     THR   S     TIME       COMMAND
1234     frank        85.2     12.5     4.0GB      8     RUN   01:23:45   python.exe
5678     frank        45.1     5.2      1.6GB      12    RUN   00:45:23   chrome.exe
```

---

## 🎨 Color Coding

### Resource Usage

- **🟢 Green**: < 50% (Normal usage)
- **🟡 Yellow**: 50-80% (Moderate usage)
- **🔴 Red**: > 80% (Heavy usage)

### GPU Temperature

- **🟢 Green**: < 65°C (Cool)
- **🟡 Yellow**: 65-80°C (Warm)
- **🔴 Red**: > 80°C (Hot - needs attention)

### GPU Vendors

- **🟢 NVIDIA**: Green
- **🔴 AMD**: Red
- **🔵 Intel**: Blue
- **⚪ Generic**: Gray

### Process Status

- **🟢 Running**: Green
- **⚪ Sleeping/Idle**: Gray

---

## 🔧 Configuration

WINTOP uses in-memory settings that can be adjusted during runtime:

| Setting | Default | Range | Description |
|---------|---------|-------|-------------|
| Refresh Rate | 2 seconds | 1-10s | Update frequency |
| Process Limit | 25 | N/A | Processes per page |
| Sort By | CPU | CPU/MEM/PID/NAME | Sort order |
| Show GPU | True | True/False | GPU monitoring |
| Style | HTOP | TOP/HTOP | Display mode |

---

## 🐛 Troubleshooting

### Common Issues

#### GPU Not Detected

**Problem**: GPU not showing up even with drivers installed.

**Solution**:

1. Install appropriate GPU library:
   - NVIDIA: `pip install gputil`
   - AMD/Intel: `pip install wmi` (Windows)
2. Restart WINTOP
3. Press `G` to toggle GPU monitoring

#### Permission Denied When Killing Process

**Problem**: Cannot kill certain processes.

**Solution**:

- Windows: Run Command Prompt as Administrator
- Linux: Use `sudo python wintop.py`

#### Import Error: No module named 'wmi'

**Problem**: WMI not installed (Windows only).

**Solution**:

```bash
pip install wmi
```

#### Colors Not Displaying

**Problem**: Terminal doesn't support colors.

**Solution**:

- Windows: Use Windows Terminal or PowerShell
- Linux: Most modern terminals support colors by default

#### AMD GPU Shows Limited Metrics

**Problem**: AMD GPU shows "N/A" for load/temperature.

**Solution (Windows)**:

1. Download OpenHardwareMonitor: <https://openhardwaremonitor.org/>
2. Run it in the background before starting WINTOP
3. WINTOP will automatically detect and use enhanced metrics

---

## 🤝 Contributing

Contributions are welcome! Here's how you can help:

1. **Fork the repository**
2. **Create a feature branch**: `git checkout -b feature/amazing-feature`
3. **Commit your changes**: `git commit -m 'Add amazing feature'`
4. **Push to the branch**: `git push origin feature/amazing-feature`
5. **Open a Pull Request**

### Development Setup

```bash
# Clone your fork
git clone https://github.com/YOUR_USERNAME/wintop.git
cd wintop

# Install development dependencies
pip install -r requirements.txt

# Run tests (if available)
python -m pytest
```

### Reporting Bugs

Please use the [GitHub Issues](https://github.com/alfredvalencia692/wintop/issues) page to report bugs. Include:

- Operating System and version
- Python version
- GPU type (if GPU-related)
- Steps to reproduce
- Error messages or screenshots

---

## 📝 Changelog

### Version 2.5 (Current)

- ✨ Added multi-vendor GPU monitoring (NVIDIA, AMD, Intel)
- ✨ Added process filtering by name
- ✨ Added CPU frequency display
- ✨ Improved cross-platform compatibility
- ✨ Enhanced color coding system
- 🐛 Fixed Windows WMI GPU detection
- 🐛 Fixed pagination bugs
- 🐛 Fixed memory calculation accuracy

### Version 1.0

- 🎉 Initial release
- Basic CPU, Memory, Disk monitoring
- Process management (kill/start)
- TOP and HTOP display modes

---

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

```
MIT License

Copyright (c) 2024 Frank Gacxs

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
```

---

## 👨‍💻 Author

**Frank Gacxs**

- GitHub: [@alfredvalencia692](https://github.com/alfredvalencia692)
- Repository: [https://github.com/alfredvalencia692/wintop](https://github.com/alfredvalencia692/wintop)

---

## 🙏 Acknowledgments

- Inspired by Linux's `htop` and `top` utilities
- Built with [psutil](https://github.com/giampaolo/psutil) - Cross-platform system monitoring
- GPU monitoring powered by [GPUtil](https://github.com/anderskm/gputil) and NVIDIA ML
- Windows integration via WMI (Windows Management Instrumentation)

---

## 📞 Support

If you like this project, please consider:

- ⭐ Starring the repository
- 🐛 Reporting bugs and issues
- 💡 Suggesting new features
- 🤝 Contributing code improvements

For questions and support, please open an issue on [GitHub Issues](https://github.com/alfredvalencia692/wintop/issues).

---

<div align="center">

**Made with ❤️ by Frank Gacxs**

[⬆ Back to Top](#wintop---cross-platform-system-monitor)

</div>
