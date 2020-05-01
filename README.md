# Texas Instruments for Deep Learning (TIDL) API Setup

The page demonstrates the installation of the TIDL API provided by Texas Instruments. 

**Note: The installation is ONLY for Host side**(Ubuntu 14.04). 

The API is built over the _Processor SDK for AM57x processors_. Hence, we need to install it first.

## Setting up the SDK
* Download SDK from official site. I used [v06.02.00.81](http://software-dl.ti.com/processor-sdk-linux/esd/AM57X/latest/exports/ti-processor-sdk-linux-am57xx-evm-06.02.00.81-Linux-x86-Install.bin)

* Change directory to the `.bin` location and execute
```
$ chmod a+x ti-processor-sdk-linux-am57xx-evm-06.02.00.81-Linux-x86-Install_1.bin 
```
You should see the SDK setup complete. Now enter the SDK install directory (mine was: `pradan@pradan-HP-15-Notebook-PC:~/ti-processor-sdk-linux-am57xx-evm-06.02.00.81`) 
and Run
```
$ ./linux-devkit.sh
```
* Now run 
```
$ ./setup.sh
```
With a long log, you shall see something like 
```
Multiple filesystems found.
        1:tisdk-rootfs-image-am57xx-evm.tar.xz
        2:tisdk-docker-rootfs-image-am57xx-evm.tar.xz
```
Select 1. Next, the system will ask `In which directory do you want to install the target filesystem?` Just hit enter to use the current directory or provide any alternate path. 

* When prompted about kernel location 
```
Select Linux kernel location:
 1: TFTP
 2: SD card
```
Hit 1. In the upcoming steps, you will be asked to choose between an SD card or other option. Always choose the other option (as we are setting it up for host-side and not the actual BeagleBone device).

* By now, the setup should be almost complete. To check, re-run the command `$ ./linux-devkit.sh` and should see 
```
Enter target directory for SDK (default: /usr/local/arago-2019.11): 
You are about to install the SDK to "/usr/local/arago-2019.11". Proceed[Y/n]?y
Extracting SDK...done
Setting it up...done
```
 
* Setup the environment variables 
```
$ source linux-devkit/environment-setup
```
The console will now be similar to:
```
[linux-devkit]:~/ti-processor-sdk-linux-am57xx-evm-06.02.00.81> $
```

## Setting up the TIDL API
**Note: Try doing the below steps within the same working directory (__ti-processor-sdk-linux-am57xx-evm-06.02.00.81__ in my case) and keep the `[linux-devkit]` environment sourced !** 
* Clone the repo 
```
 git clone https://bitbucket.itg.ti.com/scm/mctools/tidl-api.git
```

* Now, export some important paths. Here's an example
```
$ export PSDK_LINUX="/home/pradan/ti-processor-sdk-linux-am57xx-evm-06.02.00.81"
$ export TARGET_ROOTDIR="/home/pradan/ti-processor-sdk-linux-am57xx-evm-06.02.00.81/linux-devkit/sysroots/armv7at2hf-neon-linux-gnueabi"
$ export HOSR_ROOTDIR="/home/pradan/ti-processor-sdk-linux-am57xx-evm-06.02.00.81/linux-devkit/sysroots/x86_64-arago-linux"
$ make build-api
$ make build-examples
```

If you faced any problem in the `make` part, refer to this [e2e thread](https://e2e.ti.com/support/processors/f/791/t/892281).

* If not, then we're done!
 

