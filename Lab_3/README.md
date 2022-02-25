<h1 align = "center">LAB 3: Building a Mixer</h1>
<p align = "center"><b>Author: Kylee Krzanich </b></p>
<p align = "center"><b>Lab Partner: Angie Thai </b></p>

## Background
In this lab, we built our first passive double balanced RF mixer. Mixers are 3-port devices which take the sum and difference of two ports, RF and LO, and output both to the other port, IF. A double balanced mixer has full port isolation which allows it to increase linearity and supress more spurious products.

We chose to create FET ring mixers because they require less power for a given IIP3 and are popular for commercial use. However, dioide ring mixers generally perform better because they are easier to match and therefore provide better rejection. 

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

As shown in Fig.2, we preplanned the connections using the selectted parts to make construction easer. 

<p align = "center">
<img src = "assets/diagram.jpg" width="500">
</p>
<p align = "center">
Fig.2 - Diagram of circuit using selected parts
</p>


## Results

First, we will analyze at the output of the mixer by using a function generator to set LO to 12 MHz and RF to 2 MHz as shown in Fig.3.

<p float="left">
<img src = "assets/LO.JPG" width="500">
<img src = "assets/RF.JPG" width="500">
</p>
<p align = "center">
Fig. 3 - Left: LO at 12MHz. Right: RF at 2MHz.
</p>

Now, looking at Fig.4, we can see that the output shown on the Spectrum Analyzer is exactly as expected. We have a peak at 10 MHz which represents <img src="https://render.githubusercontent.com/render/math?math=IF=LO-RF"> and then another large peak at 14 MHz which represents <img src="https://render.githubusercontent.com/render/math?math=IF=LO+RF">. 

<p align = "center">
<img src = "assets/IF.JPG" width="500">
</p>
<p align = "center">
Fig.4 - IF shown on Spectrum Analyzer
</p>

Now to find the 1db compression point, we change input level of RF by 1db and find the point when the gain of IF no longer increases by 1db. In our case, the compression point was 15db and the corresponding IF output is shown in Fig. 4. 

<p align = "center">
<img src = "assets/IF.JPG" width="500">
</p>
<p align = "center">
Fig.4 - IF at 1-db compression point 
</p>

The conversion gain is given by 

## Conclusion


## Acknowledgements

