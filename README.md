# Wi-Fi and Bluetooth firmware for Linux on T2 and Apple Silicon Macs.

The firmware has been extracted from **[macOS GitHub Runner Image](https://github.com/actions/runner-images)**.

## Ubuntu/Debian

Ubuntu and Debian users can add the apt repo for firmware by running:

```bash
curl -s --compressed "https://adityagarg8.github.io/t2-ubuntu-repo/KEY.gpg" | gpg --dearmor | sudo tee /etc/apt/trusted.gpg.d/t2-ubuntu-repo.gpg >/dev/null
echo "deb [signed-by=/etc/apt/trusted.gpg.d/t2-ubuntu-repo.gpg] https://github.com/AdityaGarg8/Apple-Firmware/releases/download/debian ./" | sudo tee -a /etc/apt/sources.list.d/t2.list
sudo apt update
```

Then install the **apple-firmware** package by running:

```bash
sudo apt install apple-firmware
```

For more details refer to this [t2linux wiki](https://wiki.t2linux.org/guides/wifi-bluetooth/).
