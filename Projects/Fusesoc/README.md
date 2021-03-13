FuseSoC
-----



### Objectives and considerations

* See how easy is to run FuseSoC cores with a few commands from shell without opening Quartus


### Resources of information

* Fusesoc general info https://github.com/olofk/fusesoc

* Blinky core https://github.com/somhi/blinky

* SERV core https://github.com/olofk/serv

* Corescore core https://github.com/olofk/corescore

  

### Install FuseSoC

Follow more detailed instructions at https://github.com/olofk/fusesoc

```sh
#install (if pip does not work try with pip3)
pip install fusesoc
#add fusesoc workspace library folder where you prefer
#I recommend ~/bin/fusesoc so later it's easy for adding Zephyr OS support
mkdir fusesoc
cd fusesoc

#Install the FuseSoc base library into the workspace
fusesoc library add fusesoc-cores https://github.com/fusesoc/fusesoc-cores
#Get a list of cores found in the workspace
fusesoc core list

#When working with FuseSoC always open a terminal window in the workspace folder
```



See basic core examples in the sections below. 

Here are general commands to work with cores:

```sh
#if some time has passed since install, update the core libraries 
fusesoc library update

#export your path to the synthesis tool so FuseSoC can find it, eg:
export PATH="/...path..to.../intelFPGA_lite/17.1/quartus/bin:$PATH"

#Build core on one of the supported FPGA targets  (cyc1000, deca, sockit, verilator_tb, ...)  [replace cyc1000 with your target, and corename with the name of the core]
fusesoc run --target=cyc1000 corename

#If the core you are looking for is not there, or if you want to modify the project, e.g. to add support for an additional board, add library in your workspace
fusesoc library add corename https://github.com/xxxxx/yyyyyyyy
#[replace corename with the name of the core and his repository]

#Check available core targets already ported [replace corename]
fusesoc core show corename

```



### Blinky core

Blinks a led in the board target.

Follow more detailed instructions at https://github.com/somhi/blinky

```sh
#export your path to the synthesis tool so FuseSoC can find it, eg:
export PATH="/...path..to.../intelFPGA_lite/17.1/quartus/bin:$PATH"

#Build one of the supported targets  (cyc1000, deca, sockit, ...)
fusesoc run --target=cyc1000 fusesoc:utils:blinky

#If the core is not there, or if you want to modify the project run first
fusesoc library add blinky https://github.com/fusesoc/blinky

```



### SERV core

Outputs a Hello World message at the serial port using Zephyr OS running on the SERV bit-serial RISC-V core.

Follow more detailed instructions at https://github.com/olofk/serv

```sh
#add library
fusesoc library add serv https://github.com/olofk/serv

#export your path to the synthesis tool so FuseSoC can find it, eg:
export PATH="/...path..to.../intelFPGA_lite/17.1/quartus/bin:$PATH"

#Build one of the supported targets  (cyc1000, deca, sockit, ...)
fusesoc run --target=cyc1000 servant

#run a serial terminal in another window before fusesoc loads the bitstream. 
#This command works on the CYC1000 (might need to adjust for the correct UART port)
picocom -b 115200 /dev/ttyUSB0

```

DECA development kit:

```sh
#FPGA Pin W18 (Pin 3 P8 connector) is used for UART output with 57600 baud rate. Key 0 is reset and Led 0 q output.
fusesoc run --target=deca servant
picocom -b 57600 /dev/ttyUSB0
```

SoCKit development kit:

```sh
#FPGA Pin F14 (HSTC GPIO addon connector J2, pin 2) is used for UART output with 57600 baud rate.
fusesoc run --target=sockit servant
picocom -b 57600 /dev/ttyUSB0
```

Test with Verilator:

```sh
SERV='/....path..to...../fusesoc/fusesoc_libraries/serv'
fusesoc run --target=verilator_tb servant --uart_baudrate=57600 --firmware=$SERV/sw/zephyr_hello.hex
```



### Corescore core

Fed your board with multiple SERV cores into the FPGA just for the sake of showing how many of them your board is capable to run with.

Follow more detailed instructions at https://github.com/olofk/corescore

```sh
#Add CoreScore as a library in your workspace
fusesoc library add corescore https://github.com/olofk/corescore
#Check available corescore targets
fusesoc core show corescore

#export your path to the synthesis tool so FuseSoC can find it, eg:
export PATH="/...path..to.../intelFPGA_lite/17.1/quartus/bin:$PATH"

#Build one of the supported targets  (cyc1000, deca, sockit, ...)
fusesoc run --target=cyc1000 corescore

#Run the corecount utility (might need to adjust for the correct UART port)
python3 fusesoc_libraries/corescore/sw/corecount.py /dev/ttyUSB0
```

```sh
#If not installed you would need this libraries to run the corecount utility
pip3 install pyserial
pip3 install u_msgpack_python
```



## Modify a core to add a new board

```sh
#Check in the Github repo if there is already a port pending in the Pull request section
#Add Core as a library in your workspace
fusesoc library add CORENAME https://github.com/XXXXX
#Go to the library folder  
cd /....path..to...../fusesoc/fusesoc_libraries/libraryname
#edit the .core file
gedit CORENAME.core
#look for an existing target similar to the one you want to port and copy sections and add verilog files as needed in the proper folders descrived in the .core file
```





## Zephyr OS support for the SERV core

For more info look at:

* https://github.com/olofk/serv
* https://www.zephyrproject.org/

Set up a command-line Zephyr development environment:

* https://docs.zephyrproject.org/latest/getting_started/index.html