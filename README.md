# 🐧 Buildroot for Raspberry Pi 3

This repository provides a fully automated setup using **GitHub Actions** to build a custom **Buildroot Linux image** for the **Raspberry Pi 3**.

---

## 📦 Features

- ✅ SSH Access (Dropbear)
- ✅ Python 3 + pip + libgpiod
- ✅ Qt6 GUI + Weston + Wayland + Xterm
- ✅ Network Support (Connman + wpa_supplicant + dbus)
- ✅ Nano and Vim Editors
- ✅ libgpiod tools for GPIO control

---

## 🚀 Getting Started

### 📁 Structure

```
rpi3-buildroot-github/
├── .github/workflows/buildroot.yml
├── .config
├── README.md
```

### 🛠️ How to Build (automatically)

Every push to this repo will **trigger a build** on GitHub Actions.  
After completion, you'll find the built image (`sdcard.img`) in the **Actions artifacts**.

---

## 💾 Flashing the Image

1. Download the built image (`sdcard.img`) from GitHub Actions artifacts.
2. Use [Raspberry Pi Imager](https://www.raspberrypi.com/software/) or `dd` to flash it:

   ```bash
   sudo dd if=sdcard.img of=/dev/sdX bs=4M status=progress conv=fsync
   ```

---

## 🔐 Default Access

- **Username**: `root`
- **Password**: *(empty, press Enter)*
- SSH enabled by default on port 22.

---

## 📡 Network

- **Ethernet (eth0)** gets IP via DHCP.
- **WiFi** supported via `connmanctl`.

---

## 🎛️ GUI

- **Weston** Wayland compositor starts at boot.
- Use `xterm` or launch Qt6 apps from GUI.

---

## 🧪 Test Python + GPIO

You can test GPIOs via Python or CLI:

```bash
# Python GPIO example
import gpiod
chip = gpiod.Chip("gpiochip0")
line = chip.get_line(17)
line.request(consumer="test", type=gpiod.LINE_REQ_DIR_OUT)
line.set_value(1)
```

Or via CLI:

```bash
gpioset gpiochip0 17=1
```

---

## 📜 License

MIT — use this freely!

---

## ✨ Maintained by

**Mohamed ElSayed**  
GitHub: [@MohamedElSayed215](https://github.com/MohamedElSayed215)
