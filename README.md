# Texas Instruments for Deep Learning (TIDL) API Setup

The page demonstrates the installation of the TIDL API provided by Texas Instruments. **Note: The installation is ONLY for Host side**(Ubuntu 14.04).  

The API is built over the _Processor SDK for AM57x processors_. Hence, we need to install it first.

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
 
