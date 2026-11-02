# Lego-Dimensions-Pad-Scripts
Scripts to interact with your Lego Dimensions pad (USB ID `0e6f:0241`), for Python 3.

- `legousb-colorcycle.py` cycles the whole pad through a few colours, then turns it off.
- `legousbtag.py` lights a pad green when a tag is placed on it (red for the tag set in `uidDarthVader`) and turns it off when the tag is lifted. Press Ctrl+C to stop.
- `legopad-colorbank.txt` lists colour values to use in your own scripts.

## Setup

```
pip install -r requirements.txt
```

pyusb needs the libusb library: it's `libusb1` on Fedora, `libusb-1.0-0` on Debian/Ubuntu, and `brew install libusb` on macOS. On Windows, use [Zadig](https://zadig.akeo.ie/) to switch the pad to the WinUSB driver.

On Linux the scripts need root unless you add a udev rule, for example `/etc/udev/rules.d/50-lego-dimensions.rules`:

```
SUBSYSTEM=="usb", ATTRS{idVendor}=="0e6f", ATTRS{idProduct}=="0241", TAG+="uaccess"
```

Then run `sudo udevadm control --reload` and plug the pad back in.

## Usage

```
python3 legousb-colorcycle.py
python3 legousbtag.py
```
