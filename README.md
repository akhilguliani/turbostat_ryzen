# Linux [turbostat](https://manpages.debian.org/testing/linux-cpupower/turbostat.8.en.html) utility for AMD Ryzen
This is a modified version of the linux turbostat utility to do measurements on Ryzen family of CPU's.

### Build Instruction:
```
$ git clone https://github.com/akhilguliani/turbostat_ryzen.git
$ make
```
### Dependencies
This utility also requires that the msr kernel module is loaded before use.
```
$ sudo modprobe msr
```
This program requires root access to run. 
To avoid root access set permission for current user to read the msr registers present in the device file system as follows.
```
$ sudo setcap cap_sys_rawio=ep ./turbostat
$ sudo chmod +r /dev/cpu/*/msr
```
### Running the tool
```
# To caputer state of whole system [Tested and used by me]
$ turbostat [Options] [--interval seconds] 

# To profile a specific application
$ turbostat [Options] application_cmd
```
Please refer [manpage](https://manpages.debian.org/testing/linux-cpupower/turbostat.8.en.html) for more information.

I made these modifiction to perform application profiling experiments for my work [Per-application power delivery published in Eurosys 2019](http://pages.cs.wisc.edu/~swift/papers/eurosys19-power.pdf).
If you found this utility useful for you own project, please help support this work by citing it.
```
inproceedings{10.1145/3302424.3303981,
author = {Guliani, Akhil and Swift, Michael M.},
title = {Per-Application Power Delivery},
year = {2019},
isbn = {9781450362818},
publisher = {Association for Computing Machinery},
address = {New York, NY, USA},
url = {https://doi.org/10.1145/3302424.3303981},
doi = {10.1145/3302424.3303981},
booktitle = {Proceedings of the Fourteenth EuroSys Conference 2019},
articleno = {5},
numpages = {16},
keywords = {Power Management, Proportional Shares, DVFS},
location = {Dresden, Germany},
series = {EuroSys ’19}
}
```
  
