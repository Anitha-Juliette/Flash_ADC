## VSD OPENSOURCE TOOLS INSTALLATION  
### Vsdflow creation  
* sudo apt-get install git  
* git clone https://github.com/kunalg123/vsdflow.git
### Magic installation  
* $ sudo apt-get install m4 // Install M4 preprocessor  
* $ sudo apt-get install tcsh // Install tcsh shell  
* $ sudo apt-get install csh // Install csh shell  
* $ sudo apt-get install libx11-dev // Install xlib
//If you wish to have the Tcl/Tk wrapper around magic (recommended) you will need to install the Tcl/Tk libraries. Version 8.5 or higher is highly recommended.Tcl/Tk//  
* $ sudo apt-get install tcl-dev tk-dev  
// Cairo graphics interface ("magic -d XR")//  
* $ sudo apt-get install libcairo2-dev
// The OpenGL interface//  
* $ sudo apt-get install mesa-common-dev libglu1-mesa-dev  
// ncurses library //  
* $ sudo apt-get install libncurses-dev  
* $ cd magic  
* $ ./configure  
* $ make  
* $  sudo make install
### Netgen installation  
* $ git clone git://opencircuitdesign.com/netgen  
* $ cd netgen  
* $ ./configure  
* $  make  
* $  sudo make install
### xcschem installation  
* $ git clone https://github.com/StefanSchippers/xschem.git xschem_git  
* $ sudo apt-get install flex  
* $ sudo apt-get install bison  
* $ sudo apt-get install libxpm-dev  

### ngspice installation  
* $ sudo apt-get update  
* $ sudo apt-get install ngspice  
* $ ngspice -v  

### Openpdks installation  
* $ git clone git://opencircuitdesign.com/open_pdks  
* $ cd open_pdks  
* $	./configure --enable-sky130-pdk  
* $  make  
* $  sudo make install

### Align installation
* $ sudo apt-get install libboost-all-dev
* $ sudo apt-get update  
* $ sudo apt-get install lp-solve  
* $ export CC=/usr/bin/gcc  
* $ export CXX=/usr/bin/g++  
* $ git clone https://github.com/ALIGN-analoglayout/ALIGN-public  
* cd ALIGN-public  
* //Create a Python virtualenv//  
* $ python -m venv general  
* $ source general/bin/activate  
* $ python -m pip install pip --upgrade  
* // Install ALIGN as a USER //  
* $ pip install -v .  
* // Install ALIGN as a DEVELOPER //  
* $ pip install -e .  
* $ pip install setuptools wheel pybind11 scikit-build cmake ninja  
* $ python3 -m pip install --upgrade pip setuptools wheel  
* $ pip install -v -e .[test] --no-build-isolation  
* $ pip install -v --no-build-isolation -e . --no-deps --install-option=' DBUILD_TESTING=ON'  
* $ git clone https://github.com/ALIGN-analoglayout/ALIGN-pdk-sky130  
* $ move SKY130_PDK folder to /home/ani/ALIGN-public/pdks 

### Running Align tool with examples  
* $ python -m venv general  
* $ source general/bin/activate  
* mkdir work  
* cd work  
//Example 1//  
* $ schematic2layout.py ../examples/telescopic_ota -p ../pdks/FinFET14nm_Mock_PDK/
//Klayout opening//  
* $ XDG_SESSION_TYPE=x11  
* klayout  

