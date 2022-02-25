<h1 align = "center">LAB 3: Building a Mixer</h1>
<p align = "center"><b>Author: Kylee Krzanich </b></p>
<p align = "center"><b>Lab Partner: Angie Thai </b></p>

## Background
In this lab, we built our first passive double balanced switching RF mixer. Mixers are 3-port devices which take the sum and difference of two ports, RF and LO, and output both to the other port, IF. A double balanced mixer has full port isolation which allows it to increase linearity and supress more spurious products. We also used a switching mixer topology instead of a multiplier because we wanted to limit the noise penalty of our circuit. 

We chose to create a FET ring mixer because they require less power for a given IIP3 (less leakage) and are popular for commercial use because of their extremely low cost. However, dioide ring mixers generally perform better because they are easier to match and therefore provide better rejection. 

### FET Ring Mixer
In Fig.1, you can see the schematic for a FET Ring Mixer. 

<p align = "center">
<img src = "assets/schematic.png" width="600">
</p>
<p align = "center">
Fig.1 - Schematic of a FET Ring Mixer
</p>

Based off of the diagram above, we used the following parts to assemble the circuit: 

- [PE4141](https://www.psemi.com/pdf/datasheets/pe4141ds.pdf)
- [ADT4-1WT+](minicircuits.com/pdfs/ADT4-1WT+.pdf)
- [50 Ohm Coaxial SMA Connector](https://www.mouser.com/datasheet/2/18/1/amphs06495_1-2259698.pdf)

As shown in Fig.2, we preplanned the connections using the selected parts to make construction easer. 

<p align = "center">
<img src = "assets/diagram.jpg" width="400">
</p>
<p align = "center">
Fig.2 - Diagram of circuit using selected parts
</p>

I have included an image of the final circuit in Fig.3 below. It was constructed on top of copper-clad strip board. 

<p align = "center">
<img src = "assets/final.jpg" width="500">
</p>
<p align = "center">
Fig.3 - Image of final circuit
</p>

## Results

First, we will analyze at the output of the mixer by using a function generator to set LO to 12 MHz and RF to 2 MHz as shown in Fig.4. This configuration is known as aa high-side downconverter.

<p float="left">
<img src = "assets/LO.JPG" width="500">
<img src = "assets/RF.JPG" width="500">
</p>
<p align = "center">
Fig. 4 - Left: LO at 12MHz. Right: RF at 2MHz.
</p>

Now, looking at Fig.5, we can see that the output shown on the Spectrum Analyzer is exactly as expected. We have a peak at 10 MHz which represents <img src="https://render.githubusercontent.com/render/math?math=IF=LO-RF"> and then another large peak at 14 MHz which represents <img src="https://render.githubusercontent.com/render/math?math=$IF=LO%2BRF$">. 

<p align = "center">
<img src = "assets/IF.JPG" width="500">
</p>
<p align = "center">
Fig.5 - IF shown on Spectrum Analyzer
</p>

You can see there is quite 

<p align = "center">
<img src = "assets/compression.JPG" width="500">
</p>
<p align = "center">
Fig.6 - Plot of compression point 
</p>

To find the 1db compression point, we changed the input level of RF by 1db at a time and found the point where the gain of IF no longer increased by 1db. In our case, the compression point was 15db and the corresponding IF output is shown in Fig. 6. As depicted in Fig.7, the idea is that we should always operate the mixer below the compression point because above it our mixer acts as a non-linear device so we will see a lot of distortion, harmonics and spurious products. 

<p align = "center">
<img src = "assets/compression_chart.png" width="600">
</p>
<p align = "center">
Fig.7 - Plot of compression point 
</p>

The conversion loss is given by  <img src="https://render.githubusercontent.com/render/math?math=\text{IF output power}-\text{RF input power}=16-7=9"> dB. This number is important because it will determine the amount of amplication we'd need in later stages. 

<p align = "center">
<img src = "assets/min.JPG" width="600">
</p>
<p align = "center">
Fig.8 - Minimum IF Frequency
</p>

To find the minimum IF frequency, we started with RF at 12.1 MHz and LO at 12 MHz. Then, we decreased RF until IF deteriorated significantly. In Fig.8, you can see IF no longer resembles a sinusoid which means we've hit the minimum IF frequency. The dioide mixers should be able to hit DC frequency but we used FET mixers so our  minimum IF frequency corresponds to <img src="https://render.githubusercontent.com/render/math?math=IF=LO-RF=30"> kHz. 

The reason the FET ring mixers can't reach 


## Conclusion
In conclusion, our FET ring mixers performed significantly worse than some of the diode ring mixers that our classmates created. 

## Acknowledgements
Thank you to Greig for helping design the FET circuit as well as provide a 5 Mhz low pass filter for viewing the minimum IF frequency on the oscilloscope. 
