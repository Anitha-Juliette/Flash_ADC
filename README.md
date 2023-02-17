##                  VSD Mixed-signal PD Research Program - Flash_ADC  
### <div align="center"> WEEK0 AI's
###                  VSD OPENSOURCE TOOLS INSTALLATION  
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
   $ mkdir Lab1_and  
   $ cd Lab1_and  
   $ mkdir mag  
   $ mkdir netgen  
   $ mkdir xschem  
   $ cd xschem  
   $ cp /usr/local/share/pdk/sky130A/libs.tech/xschem/xschemrc .  
   $ cp /usr/local/share/pdk/sky130A/libs.tech/ngspice/spinit .spiceinit  
   $ cd ../mag  
   $ cp /usr/local/share/pdk/sky130A/libs.tech/magic/sky130A.magicrc .magicrc  
   $ cd ../netgen  
   $ cp /usr/local/share/pdk/sky130A/libs.tech/netgen//sky130A_setup.tcl .
![image](https://user-images.githubusercontent.com/86735438/218258897-31956dfc-05a7-49ba-9650-d00fd3d7217e.png)
#### magic test
![image](https://user-images.githubusercontent.com/86735438/218021669-23945e4e-9878-4e21-bd13-fa0dd40c3580.png)
#### xschem test  
![image](https://user-images.githubusercontent.com/86735438/218042832-459f7237-9ffb-4544-a7b5-128601d14a87.png)
#### netgen test
![image](https://user-images.githubusercontent.com/86735438/218021867-2bf931d3-4af7-4cba-89dc-9c8193aee448.png)  
### DESIGN 1 - INVERTER 
#### INVERTER CREATION using xschem  
###### An inverter Schematic is created by importing components from Open Pdk library. 
![image](https://user-images.githubusercontent.com/86735438/218141200-37a986a8-eb03-4f02-ad32-8d8814b8835b.png)
#### SYMBOL CREATION  
###### Inorder for the subcircuit to be used in higher level circuits, a symbol is     created for the sub circuit inverter.
![image](https://user-images.githubusercontent.com/86735438/218079115-b6c12b92-8e34-4b1a-afc5-b6c054249006.png)
#### TESTBENCH CREATION
###### A testbench is created to invoke the Inverter symbol, reference the libraries and set up the simulation environment- transient /dc analysis
![image](https://user-images.githubusercontent.com/86735438/218113858-cc41f642-78cd-4d3a-a07f-93c618ebd188.png)
#### inverter_tb.spice Netlist
###### A Spice Netlist for the inverter testbench is created.
![image](https://user-images.githubusercontent.com/86735438/219472680-cc08fef7-3ed3-4d51-8056-1848f1bb4f34.png)  
#### Invoking ngspice from xschem to run Netlist
###### Through ngspice, the netlist is invoked and pre-layout simulation is executed.
![image](https://user-images.githubusercontent.com/86735438/218296498-726f4ec4-4ed3-482d-829c-5e286e3d8805.png)
#### Simulation
![image](https://user-images.githubusercontent.com/86735438/219472386-9894635c-fa6c-486a-852c-83de01a2b6dd.png)
### CREATING INVERTER LAYOUT IN MAGIC(invoked from Netlist from ngspice) - EXPORTING NETLIST & POST LAYOUT SIMULATION
  ![image](https://user-images.githubusercontent.com/86735438/219448463-560e803a-d8e5-4e86-8401-ef9082ca39e4.png)
![image](https://user-images.githubusercontent.com/86735438/219465982-eafd6c2a-b2fd-48c0-a3b7-c64b6cd5ea40.png)
![image](https://user-images.githubusercontent.com/86735438/219462668-209208d7-8fe0-4500-82dc-d2966a05fee2.png)
![image](https://user-images.githubusercontent.com/86735438/219463391-24da5f0b-45ab-4e64-a5f9-8bdd51445e3c.png)
![image](https://user-images.githubusercontent.com/86735438/219463202-0d7349d2-d6aa-435d-9486-2f1220516c82.png)
![image](https://user-images.githubusercontent.com/86735438/219471010-d805927c-c9d3-4d33-8e84-189d0a09767b.png)
![image](https://user-images.githubusercontent.com/86735438/218332205-f5a7ba8c-d75a-410b-91b8-1e092f369336.png)  
## DESIGN 2 - PRELAYOUT SIMULATION  
    ***Netlist description for prelayout simulation***
    M1 3 a vdd vdd pmos W=2.125u L=0.25u
    M2 2 b vdd vdd pmos W=2.125u L=0.25u
    M3 4 d 2 2 pmos W=2.125u L=0.25u
    M4 4 c 3 3 pmos W=2.125u L=0.25u
    M5 out e 4 4 pmos W=2.125u L=0.25u
    M6 out f 4 4 pmos W=2.125u L=0.25u

    M7 out a 6 6 nmos W=2.125u L=0.25u
    M8 out c 6 6 nmos W=2.125u L=0.25u
    M9 out e 7 7 nmos W=2.125u L=0.25u
    M10 6 b 0 0 nmos W=2.125u L=0.25u
    M11 6 d 0 0 nmos W=2.125u L=0.25u
    M12 7 f 0 0 nmos W=2.125u L=0.25u

    cload out 0 10f

    Vdd vdd 0 2.5
    V1 a 0 0 pulse 0 2.5 0.1n 10p 10p 1n 2n
    V2 b 0 0 pulse 0 2.5 0.2n 10p 10p 1n 2n
    V3 c 0 0 pulse 0 2.5 0.3n 10p 10p 1n 2n
    V4 d 0 0 pulse 0 2.5 0.4n 10p 10p 1n 2n
    V5 e 0 0 pulse 0 2.5 0.5n 10p 10p 1n 2n
    V6 f 0 0 pulse 0 2.5 0.6n 10p 10p 1n 2n

    ***Simulation commands***
    .op
    .tran 10p 4n

    *** .include model file ***
    .include my_model_file.mod
    .end

![image](https://user-images.githubusercontent.com/86735438/218333162-8946d2a4-6636-4382-ad38-fd3bc625098d.png)
![image](https://user-images.githubusercontent.com/86735438/218333181-a09a474d-571f-45ea-9fc8-afa8a060bc2a.png)
  
** INVERTER USING ALIGN
  ![image](https://user-images.githubusercontent.com/86735438/219578385-481cd7de-9958-4b1a-8846-bbf74bc1e92a.png)
![image](https://user-images.githubusercontent.com/86735438/219578504-77c43f40-778d-42d6-a613-200218dc60b2.png)
![image](https://user-images.githubusercontent.com/86735438/219665164-9d1d5c4f-4628-44c7-96b2-031d12edcf69.png)
![image](https://user-images.githubusercontent.com/86735438/219665225-d17d7784-8d69-4b5a-9071-545f1da95950.png)
  ![image](https://user-images.githubusercontent.com/86735438/219665323-55499ea0-490e-475e-ac32-628fb0592897.png)
  ![image](https://user-images.githubusercontent.com/86735438/219681463-b567e966-f130-4c9a-9c7e-c6658e4fbfdb.png)
![image](https://user-images.githubusercontent.com/86735438/219681490-8c2cb897-ffe0-41f0-a6f7-ef89b93fcfd1.png)
  ![image](https://user-images.githubusercontent.com/86735438/219680963-be93df16-9c35-4aa6-888a-5e8d109dc01a.png)
  
  ###                  PRELAYOUT SIMULATION OF COMPLEX FUNCTION  
  ![image](https://user-images.githubusercontent.com/86735438/219808918-db63d678-aad1-4b63-b85b-e9e28d6a8cc3.png)

 ![image](https://user-images.githubusercontent.com/86735438/219808556-1a10b36c-5e17-4a51-8413-59c466b99a37.png)
  ###                  POSTLAYOUT SIMULATION OF COMPLEX FUNCTION 
  ![image](https://user-images.githubusercontent.com/86735438/219793613-62ca25c1-4927-4e72-9d2a-f790de890478.png)
  ![image](https://user-images.githubusercontent.com/86735438/219793747-8d532d13-1bae-46fc-b4ab-daf092bb0bfe.png)
![image](https://user-images.githubusercontent.com/86735438/219793830-b1eca535-3caa-4bb5-bd03-b7e62b308219.png)








  










