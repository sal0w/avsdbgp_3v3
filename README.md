# A glance at avsdbgp_3x3 IP

**avsdbgp_3x3** is a Bandgap Reference circuit, which is used to generate a constant voltage reference in analog domain which is independent of temperatarure and supply voltage variations.

The objective was to achieve some specifications using only **open-source tools** with the Flow/FreePDKs provided by **VLSI Computer Architecture Research Group** [(**VLSIARCH**)](https://vlsiarch.ecen.okstate.edu/) at **Oklahoma State University** [(**OSU**)](https://go.okstate.edu/).  

To get an basic idea about this **IP**, the working principle, basic implementation, applications and significance, kindly go thru [**this**](/Prelayout/Files/BGR.pdf)

## Symbol and Pin descriptions

<p align="center">
  <img width="800" height="600" src="/Images/Circuit_and_Specs/symbol.jpg">
</p>


## Parameters


## Typical performance characteristics

#### 1. 

<p align="center">
  <img width="800" height="500" src="/Images/Circuit_and_Specs/tv.jpg">
</p>


#### 2. 

<p align="center">
  <img width="800" height="500" src="/Images/Circuit_and_Specs/vv.jpg">
 </p>

#### 3. 

<p align="center">
  <img width="800" height="500" src="/Images/Circuit_and_Specs/tc.jpg">
</p>


#### 4. 

<p align="center">
  <img width="800" height="500" src="/Images/Circuit_and_Specs/vc.jpg">
</p>


#### 5. 

<p align="center">
  <img width="800" height="500" src="/Images/Circuit_and_Specs/su.jpg">
 </p>
   
   
 ##  Future work and limitations
 
 # IP usage
 
 ## Tools needed to view and simulate this IP
 
  <img align="left" width="45" height="45" src=/Prelayout/Logo/logo.jpg>

### 1. Ngspice

[Ngspice](http://ngspice.sourceforge.net/devel.html) is the open source spice simulator for electric and electronic circuits. Ngspice is an open project, there is no closed group of developers.

#### Installing Ngspice in Ubuntu 20.04

 Open the terminal and type the following to install Ngspice
```
$  sudo apt-get install ngspice
```

<img align="left" width="45" height="45" src=/Postlayout/Logo/logo.JPG>

 ### 2. Magic
 
 [Magic](http://opencircuitdesign.com/magic/) is a VLSI layout tool.
 
#### Installing Magic in Ubuntu 20.04

Open the terminal and type the following to install Magic
```
$  wget http://opencircuitdesign.com/magic/archive/magic-8.3.32.tgz
$  tar xvfz magic-8.3.32.tgz
$  cd magic-8.3.28
$  ./configure
$  sudo make
$  sudo make install
```
### Steps to clone this git repository in Unix based systems for simulating waveforms.

Open the terminal and type the following

```
$  sudo apt install -y git
$  git clone https://github.com/ankursah5/avsd_bgr

```
##  Pre-Layout simulations

- To run and view the waveforms, type the following commands after cloning in above step.

 ```
$  cd avsd_bgr/Prelayout/Cir/
$  ngspice
```
- This opens ngspice shell.
- **To plot Vref vs Temperature (-40 to 140C) at Rload = 100Mohms**, Type the following in Ngspice shell and press enter.

```
ngspice 1 -> source 1bgr_tv.cir
```

 <p align="center">
  <img width="800" height="500" src="/Images/Pre_layout/tv.jpg">
</p>

- **To Plot Vref vs Vdd (2V to 4V) at Rload=100Mohms**, Type the following in Ngspice shell and press enter.

```
ngspice 1 -> source 2bgr_vv.cir
```

<p align="center">
  <img width="800" height="500" src="/Images/Pre_layout/vv.jpg">
</p>

- **To plot Temperature Co-efficient of Vref vs Temperature (-40 to 125C) at Rload=100Mohms**,  Type the following in Ngspice shell and press enter.

```
ngspice 1 -> source 3bgr_tc.cir
```

<p align="center">
  <img width="800" height="500" src="/Images/Pre_layout/tc.jpg">
</p>


- **To plot Voltage Co-efficient of Vref vs VDD(2.1V to 3.6V) at Rload=100Mohms**, Type the following in Ngspice shell and press enter.

```
ngspice 1 -> source 4bgr_vc.cir
```

<p align="center">
  <img width="800" height="500" src="/Images/Pre_layout/vc.jpg">
</p>

- **To plot Start-up Votage variation with time using ramp signal**, Type the following in Ngspice shell and press enter.

```
ngspice 1 -> source 5bgr_su.cir
```

<p align="center">
  <img width="800" height="500" src="/Images/Pre_layout/su.jpg">
</p>


##  Post-Layout simulations

- To view the **layout**, type the following comand,

```
ngspice 1 -> exit
```

- This exits the ngspice shell. 
- In the terminal, type the following commands.

```
$  cd ..
$  cd ..
$  cd Postlayout/Mags
$  magic -T osu018.tech bgr1.mag
```

<p align="center">
  <img width="1000" height="500" src="/Postlayout/Mags/layout_img.JPG">
</p>

 - **To run and view the post- layout waveforms**, type the following commands after above steps in terminal.

 ```
$  cd ..
$  cd spice
$  ngspice
```
- This opens ngspice shell.
- **To plot Vref vs Temperature (-40 to 140C) at Rload = 100Mohms**, Type the following in Ngspice shell and press enter.

```
ngspice 1 -> source 1pl_tv.spice
```

 <p align="center">
  <img width="800" height="500" src="/Images/Post_layout/1pl_tv.JPG">
</p>

- **To Plot Vref vs Vdd (2V to 4V) at Rload=100Mohms**, Type the following in Ngspice shell and press enter.

```
ngspice 1 -> source 2pl_vv.spice
```

<p align="center">
  <img width="800" height="500" src="/Images/Post_layout/2pl_vv.JPG"">
</p>

- **To plot Temperature Co-efficient of Vref vs Temperature (-40 to 125C) at Rload=100Mohms**,  Type the following in Ngspice shell and press enter.

```
ngspice 1 -> source 3pl_tc.spice
```

<p align="center">
  <img width="800" height="500" src="/Images/Post_layout/3pl_tc.JPG"">
</p>


- **To plot Voltage Co-efficient of Vref vs VDD(2.1V to 3.6V) at Rload=100Mohms**, Type the following in Ngspice shell and press enter.

```
ngspice 1 -> source 4pl_vc.spice
```

<p align="center">
  <img width="800" height="500" src="/Images/Post_layout/4pl_vc.JPG"">
</p>

- **To plot Start-up Votage variation with time using ramp signal**, Type the following in Ngspice shell and press enter.

```
ngspice 1 -> source 5pl_su.spice
```

<p align="center">
  <img width="800" height="500" src="/Images/Post_layout/5pl_su.JPG"">
</p>
 


Contact Information
===================================
- ANKUR SAH, 
 M.tech Embedded Systems, NIT Jamshedpur
  ankursah5@gmail.com
- KUNAL GHOSH, 
 Director, VSD Corp. Pvt. Ltd. 
  kunalpghosh@gmail.com
- PHILIPP GÜHRING, 
Software Architect at LibreSilicon Association
  pg@futureware.at
 - Dr. GAURAV TRIVEDI, 
 Co-Principal Investigator, EICT Academy, IIT Guwahati
 trivedi@iitg.ac.in
