#                  VSD Mixed-signal PD Research Program 
##                                Flash_ADC  
##                  VSD OPENSOURCE TOOLS INSTALLATION  
#### Vsdflow creation  
* sudo apt-get install git  
* git clone https://github.com/kunalg123/vsdflow.git  
#### Magic installation  
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
#### Netgen installation  
* $ git clone git://opencircuitdesign.com/netgen  
* $ cd netgen  
* $ ./configure  
* $  make  
* $  sudo make install
#### xcschem installation  
* $ git clone https://github.com/StefanSchippers/xschem.git xschem_git  
* $ sudo apt-get install flex  
* $ sudo apt-get install bison  
* $ sudo apt-get install libxpm-dev  

#### ngspice installation  
* $ sudo apt-get update  
* $ sudo apt-get install ngspice  
* $ ngspice -v  

#### Openpdks installation  
* $ git clone git://opencircuitdesign.com/open_pdks  
* $ cd open_pdks  
* $	./configure --enable-sky130-pdk  
* $  make  
* $  sudo make install

#### Align installation
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

#### Running Align tool with examples  
* $ python -m venv general  
* $ source general/bin/activate  
* mkdir work  
* cd work  
//Example 1//  
* $ schematic2layout.py ../examples/telescopic_ota -p ../pdks/FinFET14nm_Mock_PDK/
![Screenshot from 2023-02-08 15-49-18](https://user-images.githubusercontent.com/86735438/217503607-9e016f6d-b93c-403d-a58a-6c0fdca412d9.png)  
//Klayout opening//  
* $ XDG_SESSION_TYPE=x11  
* klayout  
![Screenshot from 2023-02-08 16-21-58](https://user-images.githubusercontent.com/86735438/217509630-9d701012-17e6-4076-886e-cfb4e2c5def8.png)

![Screenshot from 2023-02-08 16-24-09](https://user-images.githubusercontent.com/86735438/217510003-bbef36ae-3282-42b3-95e2-e801b049965a.png)

![Screenshot from 2023-02-08 16-25-52](https://user-images.githubusercontent.com/86735438/217510361-c27afb3e-ed98-4166-9869-97e15458fc08.png)

![Screenshot from 2023-02-08 16-26-39](https://user-images.githubusercontent.com/86735438/217510586-6eb96b5a-f8d6-45fb-a3cd-b073e41ba7ac.png)

### Verifying openpdk installation
![image](https://user-images.githubusercontent.com/86735438/218019339-4747011f-7260-4965-b390-0f79ce80ced8.png)
#### magic test
![image](https://user-images.githubusercontent.com/86735438/218021669-23945e4e-9878-4e21-bd13-fa0dd40c3580.png)
#### xschem test  
![image](https://user-images.githubusercontent.com/86735438/218042832-459f7237-9ffb-4544-a7b5-128601d14a87.png)
#### netgen test
![image](https://user-images.githubusercontent.com/86735438/218021867-2bf931d3-4af7-4cba-89dc-9c8193aee448.png)  
### LAB - INVERTER using xschem
#### INVERTER CREATION
![image](https://user-images.githubusercontent.com/86735438/218067487-44814305-cffc-4ba1-a46e-3e1ce8101e23.png)
#### SYSMBOL CREATION  
![image](https://user-images.githubusercontent.com/86735438/218069967-530139fd-f7f3-46b4-a330-15eee45617a1.png)


