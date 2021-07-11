# Wifi firmware to get wifi running on Linux on MacBook Pro 16,1 (16 inch, 2019).

The firmware has been extracted from macOS Big Sur.

You will require a patched kernel in order to get this working. For more details refer to this [t2linux wiki].

## Installation

Copy the three firmware files to `/lib/firmware/brcm/`.

Open terminal and run `sudo modprobe -r brcmfmac && sudo modprobe brcmfmac`.

Wifi should start working.

[t2linux wiki]: https://wiki.t2linux.org/guides/wifi/
