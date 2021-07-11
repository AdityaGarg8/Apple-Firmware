# Wifi firmware to get wifi running on Linux on MacBook Pro 16,1 (16 inch, 2019).

The firmware has been extracted from macOS Big Sur.

You will require a patched kernel in order to get this working. For more details refer to this [t2linux wiki].

## Will they work for my MacBook Pro 16,1?

It has been observed that some 16,1 Macs use different firmware. So it is advised to check which will work for your model. To do so, boot into macOS, open a terminal window and run:-

`ioreg -l | grep RequestedFiles`

If the Firmware and Regulatory values match the ones given in the examples given below, check out the NVRAM values too as in instructions given below. Else the firmware files for your model are not in this repo.

If the NVRAM value in the output shows `P-bali-ID_M-HRPN_V-m__m-7.9.txt`, `P-bali-X0_M-HRPN_V-m__m-7.9.txt`, `P-bali-X2_M-HRPN_V-m__m-7.9.txt` or `P-bali-X3_M-HRPN_V-m__m-7.9.txt` then the 3 firmware files in 7.9 folder can be used on Linux. This is an example of the output shared by a discord user :-

```sh
    "RequestedFiles" = ({
        "Firmware"="C-4364__s-B3/bali.trx",
        "TxCap"="C-4364__s-B3/bali-X3.txcb
        "Regulatory"="C-4364__s-B3/bali-X3.clmb",
        "NVRAM"="C-4364__s-B3/P-bali-X3_M-HRPN_V-m__m-7.9.txt"
    })
```
If the NVRAM value in the output shows `P-bali-ID_M-HRPN_V-u__m-7.7.txt`, `P-bali-X0_M-HRPN_V-u__m-7.7.txt`, `P-bali-X2_M-HRPN_V-u__m-7.7.txt` or `P-bali-X3_M-HRPN_V-u__m-7.7.txt` then the 3 firmware files in 7.7 folder can be used on Linux. This is an example of the output I had on my Mac :-

```sh
    "RequestedFiles" = ({
        "Firmware"="C-4364__s-B3/bali.trx",
        "TxCap"="C-4364__s-B3/bali-X3.txcb
        "Regulatory"="C-4364__s-B3/bali-X3.clmb",
        "NVRAM"="C-4364__s-B3/P-bali-X3_M-HRPN_V-u__m-7.7.txt"
    })
```
If there is a different NVRAM value that the ones given above, firmware files for your model are not on this repo.

## Installation

If you have got the correct firmware files, copy the three firmware files to `/lib/firmware/brcm/`.

Open terminal and run `sudo modprobe -r brcmfmac && sudo modprobe brcmfmac`.

Wifi should start working.

[t2linux wiki]: https://wiki.t2linux.org/guides/wifi/
