# DAY 0
Yosys
I installed Yosys using the following commands: 

$ git clone https://github.com/YosysHQ/yosys.git
$ cd yosys-master 
$ sudo apt install make (If make is not installed please install it) 
$ sudo apt-get install build-essential clang bison flex \
    libreadline-dev gawk tcl-dev libffi-dev git \
    graphviz xdot pkg-config python3 libboost-system-dev \
    libboost-python-dev libboost-filesystem-dev zlib1g-dev
$ make config-gcc
$ make 
$ sudo make install
Below is the screenshot showing successfull launch
![Screenshot from 2023-08-01 16-03-00](https://github.com/NharikaVulchi/IIITB_ASIC_MT513/assets/83216569/fb581d7c-6b2c-46b2-bdbf-7c7918120f3d)

