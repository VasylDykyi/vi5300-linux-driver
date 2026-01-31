# VI5300 dToF Linux kernel driver

Linux kernel driver for the VI5300 Chinese dToF (direct Time-of-Flight) distance sensor.

This driver was originally provided as a vendor driver for Linux 4.x and has been
ported to the Raspberry Pi kernel `rpi-6.15.y`.

The driver is provided as a patch against the Raspberry Pi Linux kernel tree.

---

## Features

- I2C interface
- In-tree kernel driver style
- Device Tree support
- Tested on Raspberry Pi platforms

---

## Tested environment

- Hardware: Raspberry Pi (BCM2711 / BCM2712)
- Kernel: `linux:rpi-6.15.y`
- Interface: I2C
- Architecture: ARM64

---

## Repository contents

```text
vi5300-linux-driver/
 ├─ vi5300-dtof-driver-linux-rpi-6.15.patch
 ├─ README.md
 └─ LICENSE
```

---

## How to apply the patch

Clone the Raspberry Pi Linux kernel tree:
```bash
git clone https://github.com/raspberrypi/linux.git
cd linux
git checkout rpi-6.15.y
```

Apply the driver patch:
```bash
git apply /path/to/vi5300-dtof-driver-linux-rpi-6.15.patch
```

---

## Kernel configuration

Enable the driver using menuconfig:
```bash
make menuconfig
```

Navigate to the appropriate menu and enable the VI5300 driver
(either built-in or as a module).

Then build the kernel:
```bash
make -j$(nproc)
```

---

## Device Tree example

Example Device Tree node for the VI5300 sensor:

```dts
&i2c1 {
    vi5300@XX {
        compatible = "vendor,vi5300";
        reg = <0xXX>;
    };
};
```
Replace XX with the actual I2C address of the sensor.

---

## Notes

- This driver is not upstream in the mainline Linux kernel.

- Vendor documentation for the VI5300 sensor is limited.

- The driver is provided as-is, without guarantees.

---

## License

This project is licensed under the GNU General Public License v2.0 (GPL-2.0),
in accordance with the Linux kernel licensing model.

---

## Author

Ported to Raspberry Pi kernel rpi-6.15.y by Vasyl Dykyi.
