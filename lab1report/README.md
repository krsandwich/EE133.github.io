# Lab 1 
#### Author: Kylee Krzanich  

## Background
In this lab, we move beyond ideal representations of common passive components and analyze the effects of parasitics on functionality. More importantly, we learn how to calibrate and use a VNA which allows us to measure parasitics. 

### Capacitor
We begin by looking at the common capacitor. It's customary to represent the imedance of a capcitor as <img src="https://render.githubusercontent.com/render/math?math=Z_C = \frac{1}{jwC}">, however, this is an oversimplified model. In reality, every component always has parasitic properties that alter its impedance, capacitance, and inductance. As Steve likes to say, "we are getting three for the price of one!". You may be able to ignore parasitics if you are constructing simple, low frequency circuits, but as we begin to venture into the RF domain, these parasitics can have dire consequences on the functionality of your circuit. 

To make this analysis simpler, we will analyze the realistic model of the capacitor in LT spice shown in Fig.1. In these simulations I used a 470pF capacitor, the same value that I used in lab. I also simulated with 0Ohm leead resistance but in reality the leads of my capacitor were long enough that they would contribute to the ESR. 
<p align = "center">
<img src = "lab1report/assets/cap_schematic.png" width="500">
</p>
<p align = "center">
Fig.1 - LT Spice Schematic of a Realistic Capacitor
</p>

Now, we use a spice directive to simulate the impedance of the capacitor, given by the equation <img src="https://render.githubusercontent.com/render/math?math=Z_C = \frac{V}{-I}">, from 1Hz to 1GHz. I expect to see that at smaller frequencies there's no need to worry about parastics. As the frequency goes up, the parasitics will change the impedance drastically. 
<p align = "center">
<img src = "lab1report/assets/cap_impedance.png" width="500">
</p>
<p align = "center">
Fig.2 - Impedance of a Realistic Capacitor from 1Hz to 1GHz
</p>

In Fig.2, we see that the impedance starts decreasing around 100Hz which represents the idealized model where impedance is roughly equal to <img src="https://render.githubusercontent.com/render/math?math=Z_C = \frac{1}{jwC}">. Then, there's a sharp dip around 250MHz. This dip is called the knee point and represents the self-resonance frequency. It can be used to find the ESL of our capacitor given by the equation <img src="https://render.githubusercontent.com/render/math?math=f = \frac{1}{2\cdot\pi\sqrt{\text{ESL}\cdot C}}">

### Inductor
Now, we can move on to the inductor and show a similar phenomenon. The formula for the imedance of an *ideal* inductor is given as <img src="https://render.githubusercontent.com/render/math?math=Z_L = jwL">. Like with a capacitor, an inductor also contains all three types of parasitics that significantly alter the functionality of your circuit. 

The realistic model of an inductor in LT spice is shown in Fig.3. The inductor I used in lab was a 2929SQ-331 inductor which has a value of 330 nH. Again, I simulated with 0Ohm lead resistance because my lead length was small and this value can usually be ignored at higher frequencies. 
<p align = "center">
<img src = "lab1report/assets/ind_schematic.png" width="500">
</p>
<p align = "center">
Fig.3 - LT Spice Schematic of a Realistic Inductor
</p>

Now, we use a spice directive to simulate the impedance of the inductor, again given by the equation <img src="https://render.githubusercontent.com/render/math?math=Z_C = \frac{V}{-I}">, from 1MHz to 2GHz. I expect to see the opposite 
<p align = "center">
<img src = "lab1report/assets/ind_impedance.png" width="500">
</p>
<p align = "center">
Fig.4 - Impedance of a Realistic Inductor from 1MHz to 2GHz
</p>

In Fig.4, we see that the impedance rises linearly with increasing frequency which is characteristic for an inductor. Then, we see that the impedance peaks around 275MHz, aka the self-resonance frequency. The self resonance frequency can be used to find the equivalent parallel capacitance of our inductor using the equation <img src="https://render.githubusercontent.com/render/math?math=f = \frac{1}{2\cdot\pi\sqrt{\text{EPC}\cdot L}}">. At frequencies higher that 275MHz, we see that our beautiful inductor starts acting like a capacitor, meaning that as frequency goes up, impedance goes down. 

## Measurements 

Now, that we've had some fun playing with LTSpice, lets learn how to use a VNA so that we can measure the parasitics of our real world capacitor. 
