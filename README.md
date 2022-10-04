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

They have address for each pin. We can know that inforormation from the below.



## What is userspace and kernel space? What are privilages?

Userspace:

Kernel space:

GPIO:

Call from userspace is made to the kernel space before reaching the GPIO pin hardware.
Flow 1 Diagram
![alt text](https://github.com/vikaspac/pi_gpio/blob/main/Docs/1_flow.png?raw=true)

We cannot access the same GPIO pin address directly from the usermode.
Flow 2 Diagram
![alt text](https://github.com/vikaspac/pi_gpio/blob/main/Docs/2_flow_map_error.png?raw=true)

Thats why driver helps in the process which does the following things.
Flow 3 diagram
![alt text](https://github.com/vikaspac/pi_gpio/blob/main/Docs/3_driver_flow.png?raw=true)

## How to communicate from userspace to kernel space?

![alt text](https://github.com/vikaspac/pi_gpio/blob/main/Docs/4_how_talk.png?raw=true)



## How to work the code
1. git clone https://github.com/vikaspac/pi_gpio.git
2. cd pi_gpio.git

## History
NA

## Credits
source_URL: https://www.youtube.com/watch?v=lWzFFusYg6g&list=PLc7W4b0WHTAWxMsEuSUiccXPJtoPs_g9u&index=1
code      : https://github.com/lowlevellearning/lll-gpio-driver

## License
TODO: Write license

## Notes for Author
To create a new repository on the command line


git init
git add README.md
git commit -m "first commit"
git branch -M main
git remote add origin https://github.com/vikaspac/pi_gpio.git
git push -u origin main

…or push an existing repository from the command line

git remote add origin https://github.com/vikaspac/pi_gpio.git
git branch -M main
git push -u origin main



]]></content>
  <tabTrigger>readme</tabTrigger>
</snippet>










