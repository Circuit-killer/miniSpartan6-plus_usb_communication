# miniSpartan6-plus_usb_communication
A project to communicate a FPGA board (miniSpartan6+) and a PC via USB in 12Mbit/s. One byte takes 12 bits (2 start bits, 8 data bit and 2 stop bits), so It may goes 1.0MByte/s.

# Programs
## ISE
This FPGA program waits signal from serial port. If it received some data, it returns same data.

```sh
# After you create bit file by ISE
cd ./ise/work
sudo xc3sprog -c ftdi mojo_top.bit
```
Original: https://github.com/roman3017/miniSpartan6-plus/tree/master/projects/mojo-uart

## Python
You can communicate with Spartan6 by the following command.

```sh
python ./python/serial_communication.py
```

## CPP
You can communicate with Spartan6 with using libftdi or ioctl.

```sh
cd ./cpp
make
sudo ./bin/serial_with_libftdi
```

```sh
cd ./cpp
make
sudo ./bin/serial_with_ioctl
```

I also wrote program with using libusb but it does not run correctry only that.
Libusb can't set baudrate so the program needs to run other program to set baudrate.

```sh
cd ./cpp
make
sudo ./bin/serial_with_ioctl # run to set baudrate
sudo ./bin/serial_with_libusb
```

# License
MIT

# References
https://www.scarabhardware.com/forums/topic/connecting-usb-ft2232-to-an-microblaze-uart/
https://www.scarabhardware.com/forums/topic/how-to-reach-close-to-480mbps-over-usb/
