# linux-gpio-nct610xd
NCT61XD GPIO Linux Driver for chip NCT6102D  NCT6104D and NCT6106D
The NCT6102D / NCT6104D / NCT6106D is a member of Nuvoton‟s Super I/O product line. The NCT6102D / NCT6104D / NCT6106D monitors several critical parameters in PC hardware, including power supply voltages, fan speeds, and temperatures. In terms of temperature monitoring, the NCT6102D / NCT6104D / NCT6106D adopts the Current Mode (dual current source) and thermistor sensor approach.
this driver is sepcific for GPIO function on chip NCT6102D  NCT6104D and NCT6106D.

## Preconditions (Compile) ##
you should have the following packages installed:
* linux-headers-$(uname -r)
* build-essential
* make
* git (you can also download the repo as zip)

`apt-get install -y linux-headers-$(uname -r) build-essential make git`

`git clone <this repo url>`

## Compilation ##
run `make` in the driver folder on the target machine
(otherwise your driver gets compiled for a different kernel version)

You can also provide the custom kernel directory (to compile for different
kernel than installed on host. E.g.:

```sh
make KDIR=../linux-4.9.0
```

## Usage ##

### Load the driver: ###
`insmod gpio-nct610xd.ko`

### Unload the driver: ###
unexport all the used GPIO Pins first, then run
`rmmod gpio-nct610xd.ko`

### Export a GPIO Pin: ###
`echo 40 > /sys/class/gpio/export` will export/reserve/setup the gpio 4 pin 0

### Unexport a GPIO Pin: ###
`echo 40 > /sys/class/gpio/unexport` will unexport/free the gpio 4 pin 0

### Set GPIO Pin as output: ###
`echo out > /sys/class/gpio/gpio40/direction`

### Set GPIO Pin output value: ###
`echo 1 > /sys/class/gpio/gpio40/value`

### Read GPIO Pin value: ###
`cat /sys/class/gpio/gpio40/value`


### Show GPIO states using kernel debug information: ###
`cat /sys/kernel/debug/gpio`
this has to be enabled in your kernel

## Additional information ##

see the Kernel documentation for more details:

* https://www.kernel.org/doc/Documentation/gpio/sysfs.txt
* https://www.kernel.org/doc/Documentation/gpio/gpio-legacy.txt

and so on...
