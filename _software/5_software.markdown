---
layout: page
title: DAQ
description: Data acquisition system using the Julia language on Linux.
img: /assets/img/DAQ.png
importance: 4
---

#### Problem Description
Our group uses the [Julia language](https://julialang.org/) on Linux to acquire data and control 
instruments in laboratory and field experiments. One challenge is to be able to communicate with the 
hardware. Hardware drivers with open specifications are needed and interfaces with the Julia 
language need to be made. Another challenge is design of reactive software that reliably 
communicates with the hardware in fixed intervals. Yet another challenge is to develop graphical
 user interfaces that display the data and allows instrument control in real time. 

Below we share some of our efforts related to driver and software development. Due to the 
specialized nature of the software, the documentation of some of the repositories is not yet
complete. *If you like to collaborate on data acquisition software development don't 
hesitate to contact us.*

### DAQ Systems

A brief motivation for development of these DAQ systems is given in the [abstract](http://aaarabstracts.com/2019/viewabstract.php?pid=205) for a talk
delivered at the 2019 annual conference of the American Association for Aerosol Research.

**Professional societies and funding agencies are moving towards open data policies that 
require publication of raw data and computer software used to generate results. 
Consequently, instrument control and data acquisition (DAQ) software ought to be shared with 
publication. Most manufacturers only distribute proprietary code in binary format with 
their instruments. Research groups that build new instruments often use proprietary 
special-domain languages such as LabVIEW to implement the DAQ software. Both models are 
unsuitable for publication and difficult to evaluate for correctness. Furthermore, DAQ 
software design principles are rarely debated in the scientific literature, thus slowing 
advances in instrument development. Here I show that functional reactive programming 
principles are well suited to construct reliable, efficient, and concise code for data 
acquisition and instrument control. The approach uses a textual syntax with a functional 
programming style, signal-based data structures, asynchronous event processing, and 
interfaces with a graphical user interface. To demonstrate the utility of the approach, 
free software to operate differential mobility analyzers (DMA) in scanning mode for size 
distribution measurement is shared. The code controls the instrument and acquires multiple 
data streams at two frequencies using a multifunction DAQ device and serial communication 
on a Linux platform. Raw DMA response functions are inverted in real time using the 
methodology described in Petters (2018). With moderate financial and time investment, the 
software can be used as is to operate a complete scanning mobility particle sizer system 
using a DMA column, high-voltage power supply, and detector. The software can log multiple 
auxiliary sensors and be adapted to build more elaborate programs controlling tandem DMA 
setups with complex duty cycles. The software design principles are general, portable to 
several common programming languages, and can be applied to a wide range of instrument 
automation scenarios.**

The headers link to individual repositories hosted on GitHub.

#### [Julia-AFRP-DataAcquisition](https://github.com/mdpetters/Julia-AFRP-DataAcquisition)

This repository is a concept implementation using julia for building data acquisition systems.
This is the reference implementation for the data acquisition and control systems used in our laboratory.
It illustrates how to build a gui in GTK+, render plots and outputs, maintain precisely timed 
loops, and produce a responsive interface. The data aquisition loops are polling synthetic 
data for demonstration. No hardware I/O is performed

<img src="/assets/img/panel1.png" alt="drawing" width="380"/>
<img src="/assets/img/panel2.png" alt="drawing" width="380"/>

The GUI is created using glade. The module  contains an example of timed concurrent data 
acquisition at 1 and 10 Hz. The data are stored in a circular buffer. Data are also written 
to an interpolated 1 Hz and 10 Hz regularly gridded structure. Raw data is streamed to file 
in the ~/Data directory

The data acquisition loops are executed on a separate core. This allows the program to perform 
high-load computation tasks on the main core (e.g. real-time data processing), without affecting the 
critical timing of the DAQ loops. 

#### [Julia-SMPS-IM](https://github.com/mdpetters/Julia-SMPS-IM)

Asynchronous functional reactive programming for data acquisition and instrument control: 
Example application to scanning mobility particle sizing.

Hardware requirements include a Labjack U6 multifunction DAQ card, LJTick-DAC 0-10V 14 bit 
analog outputs, High Voltage Power Supply, 1-3 serial ports, 1-3 condensation particle 
counters, 1 differential mobility analyzer column. Optionally, 2 Rotronic RH sensors for the
sheath and sample flow are read.

The software reads the condensation particle counters using pulse counting and serial ports. 
The software controls the high voltage applied to the center of the DMA column. 

Defaults, including flow rates and scan rates are set in the gui files. The files can be 
edited using the GTK glade tool. Data inversion is performed using [DifferentialMobilityAnalyzers.jl](https://github.com/mdpetters/DifferentialMobilityAnalyzers.jl). 

### Hardware Interfaces

The components for which interfaces are listed are integrated into the equipment in our 
experimental systems. We do not advertise for, nor specifically endorse any of the systems 
below for any fitness of purpose. The software os hosted on GitHub and provided as is. 
The headers are links to the respective repositories.

#### [LabjackU6Library.jl](https://github.com/mdpetters/LabjackU6Library.jl)
Julia package to communicate with Labjack series [U6 multifunction DAQ](https://labjack.com/products/u6) 
device using the low-level [exodriver](https://github.com/labjack/exodriver).

<img src="/assets/img/2-U6.jpg" alt="drawing" width="350"/>

The U6 is one of the most used multifunction DAQ devices used in our laboratory. A subset of
the exodriver routines are repackaged into a shared library and called from julia via ```ccall```.
This package is useful for applications where timing is critical. 

Note that the high-level LabjackPython interface can be used directly from Julia using PyCall and is 
significantly more convenient to work with. See the [OmronD6FPH.jl](https://github.com/mdpetters/OmronD6FPH.jl) 
code example for how easily I2C communication can be achieved with the high-level driver.


#### [TETechTC3625RS232.jl](https://github.com/mdpetters/TETechTC3625RS232.jl)

Julia package to communicate with the TE Technology TC-36-25-RS232 temperature controller.

<img src="/assets/img/TC-36-25_RS232_02.jpg" alt="drawing" width="350"/>

The TE Technology TC-36-25-RS232 device is a bi-polar proportional-integral-derivative 
temperature controller that can modulate power input to a thermolectric device. 
It communicates through an RS 232 port. 

#### [OmronD6FPH.jl](https://github.com/mdpetters/OmronD6FPH.jl)

Julia package to communicate with the Omron D6F-PH differential pressure sensor using a 
LabJack multifunction DAQ device. 

<img src="/assets/img/board.png" alt="drawing" width="350"/>

The specific implementation is for the NC State aerosol group circuit board 
(designed by Tim Wright), which accomodates the sensor to interface directly with Labjack 
device. The device is mounted on the board and powered from the 5V reference VS power on the 
labjack. A Texas Instruments LP2950-33LPE3 voltage regulator converts the 5V input to 
3.3V to power the device. The four cables are degined to plug into a Labjack bank 
(e.g. VS, GND, FIO0, FIO1). Different banks can be used.

#### [ThorlabsDCC1545M.jl](https://github.com/mdpetters/ThorlabsDCC1545M.jl)

Julia package to communicate with the Thorlabs DCC 1545M USB 2.0 CMOS Camera.

<img src="/assets/img/19418-lrg.jpg" alt="drawing" width="250"/>

The [Thorlabs DCC 1545M](https://www.thorlabs.com/newgrouppage9.cfm?objectgroup_id=4024) is 
a 1.3 Megapixel (1280 x 1024 Pixels) monochrome camera with CMOS sensor. The package wraps 
the pyueye python library to communicate with the camera through julia.

#### [AmptekMCA8000D.jl](https://github.com/mdpetters/AmptekMCA8000D.jl)

Julia package to communicate with the [Amptek MCA8000D](https://www.amptek.com/products/multichannel-analyzers/mca-8000d-digital-multichannel-analyzer) digital multichannel analyzer. 

<img src="/assets/img/MCA.png" alt="drawing" width="250"/>

The package wraps the python [code](https://github.com/HenningFo/mca8000d) written by Henning Fo. 

#### [GEOptiSonde.jl](https://github.com/mdpetters/GEOptiSonde.jl)

Julia package for RS 232 communication with the General Eastern OptiSonde dewpoint hygrometer.

<img src="/assets/img/ge.jpeg" alt="drawing" width="250"/>

The General Eastern OptiSonde is a dew-point sensor with ± 0.2 °C accuracy. The package 
provides a julia driver for RS 232 communication with the device. It solves the issue of 
choppy data streams arriving at the port. 



