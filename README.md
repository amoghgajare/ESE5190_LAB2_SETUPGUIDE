# ESE5190_LAB2_SETUPGUIDE_Amogh_Gajare
Setup Guide for Running C Codes on QTPY2040 Board
```
Amogh Gajare
LinkedIn: https://www.linkedin.com/in/amoghgajare/
Tested on: HP 14-ck2018TU Laptop, Windows 10 21H2, with WSL2
```
## WSL Setup

Open Windows Command Prompt as an administrator and enter the following command
```
wsl --install
```
Now, restart your computer and after restarting, you will be asked to enter a username and set a password. After doing that, you'll see the following message

![](https://github.com/amoghgajare/ESE5190_LAB2_SETUPGUIDE/blob/main/welcome%20to%20ubuntu.PNG)

## Installation of the SDK on RP2040
On the Ubuntu WSL terminal enter the following commands

```
$ cd ~/
$ mkdir pico
$ cd pico
```

Now we clone the SDK repositories into the above created directory, type the below commands to do so

```
$ git clone -b master https://github.com/raspberrypi/pico-sdk.git 
$ cd pico-sdk 
$ git submodule update --init 
$ cd .. 
$ git clone -b master https://github.com/raspberrypi/pico-examples.git
```

To build projects we will require CMake, the GNU Embedded Toolchain for Arm. You can install it using apt from the command line.

```
$ sudo apt update 
$ sudo apt install cmake gcc-arm-none-eabi libnewlib-arm-none-eabi build-essential libstdc++-arm-none-eabi-newlib
```

To update your copy of the SDK, go into the pico-sdk directory, and enter the following commands

```
$ cd pico-sdk 
$ git pull 
$ git submodule update
```

## Running the Code on RP2040

Run the following commands
```
$ cd ~/
$ cd pico/pico-examples
$ mkdir build 
$ cd build
$ export PICO_SDK_PATH=~/pico/pico-sdk
$ cmake ..
```

To compile and run the code, enter the following commands

```
$ cd ~/
$ cd pico/pico-examples/build/hello_world
$ make -j4
```

Once this completes, we navigate into the hello_world folder and retrieve "hello_usb.uf2" file.

```
$ cd ~/
$ cd pico/pico-examples/build/hello_world/usb
$ cp hello_usb.uf2 "Destination folder address"
```

after the above step you'll find the code on the address you've given on windows machine


Connect your RP2040 board, while pressing the boot button press reset, RPI-RP2 drive will appear, once the drive appears, drag-drop the "hello_usb.uf2" file on that drive. the drive will disappear and your code will start running on the board

I've used the Serial Monitor in Arduino IDE to view the output
![](https://github.com/amoghgajare/ESE5190_LAB2_SETUPGUIDE/blob/main/serial%20monitor.PNG)







