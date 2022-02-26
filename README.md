# LDO_VoltageRegulator_IITH_Hackathon

This repository presents the design of Low Dropout Voltage Regulator using Synopsis Custom Compiler Platform in 28nm CMOS Technology.

# Table of Contents
 * [Abstract](#Abstract)
 * [Refrence Circuit Details](#Circuit-Details)
 * [Reference Circuit Diagram](#Circuit-Diagram)
 * [Reference Circuit Waveforms](#Circuit-Waveforms)
 * [Tools Used](#Tools-Used)
 * [LDO Voltage Regulator](#LDO-Voltage-Regulator)
 * [Schematic](#Schematic)
 - [Simulations](#Simulations)
   * [DC Analysis](#DC-Analysis)
   * [Transient Analysis](#Transient-Analysis)
   * [AC Analysis](#AC-Analysis)   
 * [Author](#Author)
 * [Acknowledgements](#Acknowledgements)
 * [References](#References)


# Abstract:
The paper constitutes the design and analysis of a Low Dropout Voltage Regulator.  A low-dropout (LDO) transformer is the main component utilized in the bulk of portable electronic applications since it's used as a power management unit in those applications. In this paper, an LDO regulator for the power management microcircuit in 28m CMOS technology using Synopsys Custom Design Platform is presented. The error amplifier of the proposed LDO employed seven transistors for the current mirror. Meanwhile, the PMOS transistor is employed as a pass element transistor to control the voltage variation. The resistors are used as a feedback network circuit while the capacitor is employed to minimise the variation of output voltage.


# ReferenceCircuit Details:
The proposed LDO regulator circuit was constructed in Synopsys Custom Design Platform. Figure 1 shows the schematic of the proposed LDO regulator. In the schematic diagram, the error amplifier is constructed by three PMOS transistors and five NMOS transistors. The transistors M0 to M7 are used to form the current mirror circuit. The function of the current mirror structure will ensure each line of wire able to get the same current level in this design. All the transistors are using 28nm technology size. Based on the proposed design, a PMOS transistor M8 is used as a pass element transistor to control the voltage from the input to the output differential voltage. The main reason is the PMOS transistor is voltage-driven and does not require much current, thus greatly reducing the current consumed by the device itself. In addition, the voltage drop across the PMOS transistor is similar to the product of the output current and the on-resistance. The resistors R1 and R2 are used as a voltage divider network or feedback circuit. The feedback circuit structure can generate a feedback voltage into an error amplifier. The capacitor (Cload) is used as a stabilizer to stabilize the output voltage and the load resistor (Rload) is 10 kΩ.


# Reference Circuit Details:
![paper_1](https://user-images.githubusercontent.com/65547096/155827445-7f1c7868-ee12-4118-ab25-0541da5826d0.PNG)



# Reference Circuit Waveforms:
![paper_2](https://user-images.githubusercontent.com/65547096/155827697-90b5a6ef-4c39-493f-8dca-d9a3874631cc.PNG)
![paper_3](https://user-images.githubusercontent.com/65547096/155827706-c4275310-3e32-415c-93db-02599021b259.PNG)
![paper_4](https://user-images.githubusercontent.com/65547096/155827708-8b7ede25-4763-4508-b105-3e33d5170235.PNG)


# Tools Used:

<b>• Synopsys Custom Compiler:</b></br>
&emsp;The Synopsys Custom Compiler™ design environment is a modern solution for full-custom analog, custom digital, and mixed-signal IC design. As the heart of the Synopsys Custom Design Platform, Custom Compiler provides design entry, simulation management and analysis, and custom layout editing features. This tool was used to design the circuit on a transistor level.

<b>• Synopsys Primewave:</b></br>
&emsp;PrimeWave™ Design Environment is a comprehensive and flexible environment for simulation setup and analysis of analog, RF, mixed-signal design, custom-digital and memory designs within the Synopsys Custom Design Platform. This tool helped in various types of simulations of the above designed circuit.

<b>• Synopsys 28nm PDK:</b></br>
&emsp;The Synopsys 28nm Process Design Kit(PDK) was used in creation and simulation of the above designed circuit.


# Schematics:

![Schematic_2](https://user-images.githubusercontent.com/65547096/155853206-30500b8b-e55f-4aed-bddc-eba83a82749e.PNG)


# Simulations:


## DC Analysis

### Schematic

![VinVsVoutCkt](https://user-images.githubusercontent.com/65547096/155853007-932cb88b-dd7d-4aa5-8419-59b0c439aace.PNG)

### Parameters set for Voltage Source for Input Vin

![dc_para_1](https://user-images.githubusercontent.com/65547096/155854389-40f3b2a8-d302-4e3c-a713-b73ebe98a04b.PNG)

### Parameters set for Voltage Source for Input Vref

![dc_para_2](https://user-images.githubusercontent.com/65547096/155854400-f2a380f2-6bd7-41d5-b288-cd084d4f3471.PNG)

### DC Analysis Settings

![dc_analysis_parameters](https://user-images.githubusercontent.com/65547096/155854514-e257b45e-fa58-4928-ac2a-5c215af5bfa1.PNG)

### NetList

```
*  Generated for: PrimeSim
*  Design library name: sm_LDO_Voltage_Regulator
*  Design cell name: sm_LDO_VR_28nm
*  Design view name: schematic
.lib 'saed32nm.lib' TT
.param vs=1.8
*Custom Compiler Version S-2021.09
*Sat Feb 26 17:45:45 2022

.global gnd!
********************************************************************************
* Library          : sm_LDO_Voltage_Regulator
* Cell             : sm_LDO_VR_28nm
* View             : schematic
* View Search List : hspice hspiceD schematic spice veriloga
* View Stop List   : hspice hspiceD
********************************************************************************
xm3 vout net33 vin vin p105 w=0.1u l=0.03u nf=1 m=1
xm2 net33 net21 vin vin p105 w=0.1u l=0.03u nf=1 m=1
xm1 net21 net50 vin vin p105 w=0.1u l=0.03u nf=1 m=1
xm0 net50 net50 vin vin p105 w=0.1u l=0.03u nf=1 m=1
xm8 net33 vin gnd! gnd! n105 w=0.1u l=0.03u nf=1 m=1
xm7 vin vin gnd! gnd! n105 w=0.1u l=0.03u nf=1 m=1
xm6 net58 vin gnd! gnd! n105 w=0.1u l=0.03u nf=1 m=1
xm5 net21 net45 net58 net58 n105 w=0.1u l=0.03u nf=1 m=1
xm4 net50 vref net58 net58 n105 w=0.1u l=0.03u nf=1 m=1
v19 vref gnd! dc=0.5
v18 vin gnd! dc='vs'
c12 vout gnd! c=50p
r15 vout gnd! r=10k
r14 net45 gnd! r=100k
r13 vout net45 r=60k








.dcOP
.dc vs '0' '2' '0.5' name=dc

.option primesim_remove_probe_prefix = 0
.probe v(*) i(*) level=1
.probe dc v(vout)

.temp 25



.option primesim_output=wdf


.option parhier = LOCAL






.end
```

### Output Vs Input Voltage 

![VinVsVoutWaveform](https://user-images.githubusercontent.com/65547096/155853093-e612dd5f-217e-4308-93c6-f22bf9399198.PNG)

## Transient Analysis

### Schematic

![Schematic_2](https://user-images.githubusercontent.com/65547096/155853206-30500b8b-e55f-4aed-bddc-eba83a82749e.PNG)

### Parameters set for Voltage Source for Input Vin

![dc_para_1](https://user-images.githubusercontent.com/65547096/155854389-40f3b2a8-d302-4e3c-a713-b73ebe98a04b.PNG)

### Parameters set for Voltage Source for Input Vref

![dc_para_2](https://user-images.githubusercontent.com/65547096/155854400-f2a380f2-6bd7-41d5-b288-cd084d4f3471.PNG)

### Transient Analysis Settings

![transient_analysis](https://user-images.githubusercontent.com/65547096/155854507-f5d18e67-3cc7-4786-a431-59d1d6e40c3d.PNG)

### NetList

```
*  Generated for: PrimeSim
*  Design library name: sm_LDO_Voltage_Regulator
*  Design cell name: sm_LDO_VR_28nm
*  Design view name: schematic
.lib 'saed32nm.lib' TT

*Custom Compiler Version S-2021.09
*Sat Feb 26 18:18:59 2022

.global gnd!
********************************************************************************
* Library          : sm_LDO_Voltage_Regulator
* Cell             : sm_LDO_VR_28nm
* View             : schematic
* View Search List : hspice hspiceD schematic spice veriloga
* View Stop List   : hspice hspiceD
********************************************************************************
xm3 vout net33 vin vin p105 w=0.1u l=0.03u nf=1 m=1
xm2 net33 net21 vin vin p105 w=0.1u l=0.03u nf=1 m=1
xm1 net21 net50 vin vin p105 w=0.1u l=0.03u nf=1 m=1
xm0 net50 net50 vin vin p105 w=0.1u l=0.03u nf=1 m=1
xm8 net33 vin gnd! gnd! n105 w=0.1u l=0.03u nf=1 m=1
xm7 vin vin gnd! gnd! n105 w=0.1u l=0.03u nf=1 m=1
xm6 net58 vin gnd! gnd! n105 w=0.1u l=0.03u nf=1 m=1
xm5 net21 net45 net58 net58 n105 w=0.1u l=0.03u nf=1 m=1
xm4 net50 vref net58 net58 n105 w=0.1u l=0.03u nf=1 m=1
v19 vref gnd! dc=0.5
v18 vin gnd! dc=1.8
c12 vout gnd! c=50p
r15 vout gnd! r=10k
r14 net45 gnd! r=100k
r13 vout net45 r=60k








.tran '20' '100ns' start=0ns name=tran

.option primesim_remove_probe_prefix = 0
.probe v(*) i(*) level=1
.probe tran i(r15) i(v18)

.temp 25



.option primesim_output=wdf


.option parhier = LOCAL






.end
```

### Ouiescent Current

![QUIESCENT_CURRENT](https://user-images.githubusercontent.com/65547096/155853110-7623fa09-e8fa-47a0-8af2-fbe1a61ad2fc.PNG)


## AC Analysis

### Schematic

![PSSR_CKT](https://user-images.githubusercontent.com/65547096/155853014-e9792a4c-72ab-492a-92c3-d3bf0e1575fc.PNG)

### Parameters set for Voltage Source for Input Vin

![AC_PARA_1](https://user-images.githubusercontent.com/65547096/155855780-b7805380-070f-47fe-83db-8f7e5177c8f0.PNG)

### Parameters set for Voltage Source for Input Vref

![dc_para_2](https://user-images.githubusercontent.com/65547096/155854400-f2a380f2-6bd7-41d5-b288-cd084d4f3471.PNG)

### AC Analysis Settings

![AC_ANALYSIS](https://user-images.githubusercontent.com/65547096/155854856-5809e17c-db5e-4475-b357-d5a4786e5d0c.PNG)

### NetList

```
*  Generated for: PrimeSim
*  Design library name: sm_LDO_Voltage_Regulator
*  Design cell name: sm_LDO_VR_28nm
*  Design view name: schematic
.lib 'saed32nm.lib' TT

*Custom Compiler Version S-2021.09
*Sat Feb 26 18:57:00 2022

.global gnd!
********************************************************************************
* Library          : sm_LDO_Voltage_Regulator
* Cell             : sm_LDO_VR_28nm
* View             : schematic
* View Search List : hspice hspiceD schematic spice veriloga
* View Stop List   : hspice hspiceD
********************************************************************************
xm3 vout net33 vin vin p105 w=0.1u l=0.03u nf=1 m=1
xm2 net33 net21 vin vin p105 w=0.1u l=0.03u nf=1 m=1
xm1 net21 net50 vin vin p105 w=0.1u l=0.03u nf=1 m=1
xm0 net50 net50 vin vin p105 w=0.1u l=0.03u nf=1 m=1
xm8 net33 vin gnd! gnd! n105 w=0.1u l=0.03u nf=1 m=1
xm7 vin vin gnd! gnd! n105 w=0.1u l=0.03u nf=1 m=1
xm6 net58 vin gnd! gnd! n105 w=0.1u l=0.03u nf=1 m=1
xm5 net21 net45 net58 net58 n105 w=0.1u l=0.03u nf=1 m=1
xm4 net50 vref net58 net58 n105 w=0.1u l=0.03u nf=1 m=1
v19 vref gnd! dc=0.5
c12 vout gnd! c=50p
r15 vout gnd! r=10k
r14 net45 gnd! r=100k
r13 vout net45 r=60k
v24 vin gnd! dc=0 ac=1.8 sin ( 0 0 1000000 0 0 0 )








.ac dec '10' '0.1' '1000000000' name=ac

.option primesim_remove_probe_prefix = 0
.probe v(*) i(*) level=1
.probe ac v(vin) v(vout)

.temp 25



.option primesim_output=wdf


.option parhier = LOCAL






.end
```

### PSSR

![PSSR_WAVE](https://user-images.githubusercontent.com/65547096/155853401-e06efba8-e6ad-4f73-80ca-330857d0be71.PNG)


# Author:
• Soham Sen , B.Tech (Electronics and Communication Engineering), Amity University Kolkata - sohamsen25420001@gmail.com

# Acknowledgements:
• <a href='https://www.iith.ac.in/events/2022/02/15/Cloud-Based-Analog-IC-Design-Hackathon/'>Cloud Based Analog IC Design Hackathon</a></br>
• <a href='https://www.synopsys.com/'>Synopsys India</a></br>
• <a href='https://www.vlsisystemdesign.com/'>VLSI System Design (VSD) Corp. Pvt. Ltd India</a></br>
• <a href="https://www.iiit.ac.in/">IIIT Hyderabad</a><br>
• Kunal Ghosh, Co-Founder of VLSI System Design (VSD) Corp. Pvt. Ltd. - kunalghosh@gmail.com<br>
• Sameer Durgoji, NIT Karnataka<br>
• Chinmaya Panda, IIT Hyderabad<br>
• Active and vibrant hackathon community

# References:
1.  <a href='https://cutt.ly/oPmF0f0'>S.A.Z Murad. Design of CMOS Low-Dropout Voltage Regulator for Power Management Integrated Circuit in 0.18-µm Technology.</a><br>
2.	<a href='https://cutt.ly/InNnZPb'>N. H. E. Weste. Cmos vlsi design : A circuits and sys- tems perspective.</a><br>
