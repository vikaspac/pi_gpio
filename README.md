<snippet>
  <content><![CDATA[
# ${1:Writing GPIO drive on Raspberry pi}

This is a personal code on how to write a GPIO driver for Raspberry pi.
I tried my best to make u understand properly.

## What is Linux Driver
The software that handles or manages a hardware controller is known as a device driver. The Linux kernel device drivers are, essentially, a shared library of privileged, memory resident, low level hardware handling routines. It is Linux's device drivers that handle the peculiarities of the devices they are managing.

## What are the types of Linux device drivers?
There are various types of drivers present in GNU/Linux such as Character, Block, Network and USB drivers. In this column, we will explore only character drivers. Character drivers are the most common drivers.

## How do I create a Linux driver?
To build a driver, these are the steps to follow:

    1) Program the driver source files, giving special attention to the kernel interface.
    2) Integrate the driver into the kernel, including in the kernel source calls to the driver functions.
    3) Configure and compile the new kernel.
    4) Test the driver, writing a user program.

## How to access a GPIO pin?
Below is the image of the raspberry pi pinouts.

GPIO pinout for Raspberry pi 4 Model (Used in this tutorial)

![alt text](https://github.com/vikaspac/pi_gpio/blob/main/Docs/GPIO_rpi4.png?raw=true)



GPIO pinout for Raspberry pi 3B+ model

![alt text](https://github.com/vikaspac/pi_gpio/blob/main/Docs/GPIO_rpi3.png?raw=true)



They have address for each pin. We can know that information from the below.

**Install Kernel headers for raspberry pi**

	```sh
	pi@raspberrypi:~/vikas/workspace $ sudo apt install raspberrypi-kernel-headers
	.....
	pi@raspberrypi:~/vikas/workspace $ uname -r
	5.15.61-v8+
	pi@raspberrypi:~/vikas/workspace $ ls /lib/modules/$(uname -r)/build
	arch   certs   Documentation  fs       init  Kconfig  lib       mm              net      scripts   sound  usr
	block  crypto  drivers        include  ipc   kernel   Makefile  Module.symvers  samples  security  tools  virt
	pi@raspberrypi:~/vikas/workspace $
	```


## What is userspace and kernel space? What are privilages?

**Userspace:**


**Kernel space:**


**GPIO:*
*

Call from userspace is made to the kernel space before reaching the GPIO pin hardware.

![alt text](https://github.com/vikaspac/pi_gpio/blob/main/Docs/1_flow.png?raw=true)


We cannot access the same GPIO pin address directly from the usermode.

![alt text](https://github.com/vikaspac/pi_gpio/blob/main/Docs/2_flow_map_error.png?raw=true)


Thats why driver helps in the process which does the following things.

![alt text](https://github.com/vikaspac/pi_gpio/blob/main/Docs/3_driver_flow.png?raw=true)



## How to communicate from userspace to kernel space?

![alt text](https://github.com/vikaspac/pi_gpio/blob/main/Docs/4_how_talk.png?raw=true)



## How to work the code
	1. git clone https://github.com/vikaspac/pi_gpio.git
	2. cd pi_gpio.git


**Chapter01**
	```sh
	This is about creating the generic driver. This does below things:

	1)	Know about the Makefile
			#vim Makefile
	2)	Create a gpio_driver.c add the necessary code.
			#vim gpio_driver.c
	3)	Compile the code. Then this generates the kernel module *.ko
			#make
	4)	Insert the kernel module into the driver. you'll see __init func executed.
			#sudo insmod gpio_driver.ko
	5)	Check the logs in the kernel logs. Also check in the modules list.
			#dmesg
			#lsmod
	6)	Remove the kernel module from the driver. You'll see__exit func executed.
			#sudo rmmod gpio_driver.ko
	7)	To clean the complete project
			#make clean
	```




## History
NA


## Credits
	1) source_URL: https://www.youtube.com/watch?v=lWzFFusYg6g&list=PLc7W4b0WHTAWxMsEuSUiccXPJtoPs_g9u&index=1
	2) code      : https://github.com/lowlevellearning/lll-gpio-driver


## License
TODO: Write license


## Notes for Author
To create a new repository on the command line
	```sh
	1) git init
	2) git add README.md
	3) git commit -m "first commit"
	4) git branch -M main
	5) git remote add origin https://github.com/vikaspac/pi_gpio.git
	6) git push -u origin main

	…or push an existing repository from the command line

	1) git remote add origin https://github.com/vikaspac/pi_gpio.git
	2) git branch -M main
	3) git push -u origin main
	```


]]></content>
  <tabTrigger>readme</tabTrigger>
</snippet>



