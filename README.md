# Wi-Fi firmware to get wifi running on Linux on MacBook Pro 16,1 (16 inch, 2019).

The firmware has been extracted from **macOS Big Sur**.

You will require a patched kernel with support for **Big Sur firmware** in order to get this working. For more details refer to this [t2linux wiki].

## Will they work for my MacBook Pro 16,1?

It has been observed that some 16,1 Macs use different firmware. So it is advised to check which will work for your model. To do so, boot into macOS, open a terminal window and run:-

`ioreg -l | grep RequestedFiles`

If the **Firmware** values are `bali-ID.trx`, `bali-X0.trx`, `bali-X2.trx`, `bali-X3.trx`, `bali.trx`, `borneo-ID.trx`, `borneo-X0.trx`, `borneo-X2.trx`, `borneo-X3.trx` or `borneo.trx` check out the **Regulatory** values too as in instructions given below. Else the firmware files for your model are not in this repo.

If the **Regulatory** values are `bali-ID.clmb`, `bali-X0.clmb`, `bali-X2.clmb`, `bali-X3.clmb` or `bali.clmb` check out the **NVRAM** values too as in instructions given below. Else the firmware files for your model are not in this repo.

If the **NVRAM** value in the output shows `P-bali-ID_M-HRPN_V-m__m-7.9.txt`, `P-bali-X0_M-HRPN_V-m__m-7.9.txt`, `P-bali-X2_M-HRPN_V-m__m-7.9.txt`, `P-bali-X3_M-HRPN_V-m__m-7.9.txt` or `P-bali_M-HRPN_V-m__m-7.9.txt` then the 3 firmware files in **7.9** folder can be used on Linux. Alternatively, you may download the firmware files from [here](https://github.com/AdityaGarg8/mbp-16.1-wifi-firmware/releases/tag/7.9). This is an example of the output shared by a discord user :-

```sh
    "RequestedFiles" = ({
        "Firmware"="C-4364__s-B3/bali.trx",
        "TxCap"="C-4364__s-B3/bali-X3.txcb
        "Regulatory"="C-4364__s-B3/bali-X3.clmb",
        "NVRAM"="C-4364__s-B3/P-bali-X3_M-HRPN_V-m__m-7.9.txt"
    })
```
If the **NVRAM** value in the output shows `P-bali-ID_M-HRPN_V-u__m-7.7.txt`, `P-bali-X0_M-HRPN_V-u__m-7.7.txt`, `P-bali-X2_M-HRPN_V-u__m-7.7.txt`, `P-bali-X3_M-HRPN_V-u__m-7.7.txt` or `P-bali_M-HRPN_V-u__m-7.7.txt` then the 3 firmware files in **7.7** folder can be used on Linux. Alternatively, you may download the firmware files from [here](https://github.com/AdityaGarg8/mbp-16.1-wifi-firmware/releases/tag/7.7). This is an example of the output I had on my Mac :-

```sh
    "RequestedFiles" = ({
        "Firmware"="C-4364__s-B3/bali.trx",
        "TxCap"="C-4364__s-B3/bali-X3.txcb
        "Regulatory"="C-4364__s-B3/bali-X3.clmb",
        "NVRAM"="C-4364__s-B3/P-bali-X3_M-HRPN_V-u__m-7.7.txt"
    })
```
If there is a different **NVRAM** value that the ones given above, firmware files for your model are not on this repo.

## Installation

If you have got the correct firmware files, open linux and copy the three firmware files to `/lib/firmware/brcm`.

Open terminal and run `sudo modprobe -r brcmfmac && sudo modprobe brcmfmac`.

In case you are experiencing unstable WPA2 Wi-Fi connection, follow [this guide](https://wiki.t2linux.org/guides/wifi/#fixing-unstable-wpa2-using-iwd).

Wi-Fi should start working.

[t2linux wiki]: https://wiki.t2linux.org/guides/wifi/
