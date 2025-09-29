ok, but what do i want to do? 

On hardware: I want to build my own avionics pcb. I will start by getting _inspired_ by the ST FCU. 
Requirements I am capable of listing atm:
- allocating sensors: IMUs, magnetometers, baretometers.
- allocating motor drivers (MOSFETs)
- allocating bluetooth communication (eventually a radio...)
- allocating power distribution from the batery
Since I already have a ST Nucleo, the PCB design need to be like a shield for it.
Still to be decided if the MCU here is meant to run the whole software or it's just the API/interface with the avionics.

I got stuck at seeing the mophor pin layout is not available in kicad. I also tried a few templates, did not found anything useful.
I think my strategy should be:
- I do the schematic leaving out the morpho connector.
- Once I got everything sort out, I will take care about how on earth to draw CN11 and CN12. Each one is 2x35 = 70

# Todo list
[] Check the capacitor footprint is compatible with the its material. For instance, the magnetometer datasheet says the 10uF C is aluminim
[] Female connector for each motor with ESC

# Battery selection

One LiPo battery is 3.7V. 

The motor is tested on 11.1V, which leads to 3 units in series (3.7*3 = 11.1). Then I need 3 in series.

The motor continuous current is 15.6A. x4 motors -> 62.4A.

For the C-rating, a 1.5 factor over 62.4A leads to 93A. Let's say then 100A.

| Capacity (mAh) | C-rating | Max current (A) |
|----------------|----------|-----------------|
2200 | 20 | 44
2200 | 30 | 66
5000 | 20 | 100
5000 | 30 | 150
6000 | 20 | 120

ChatGPT: The most common off-the-shelf pack that fits you well is a 3S 5000 mAh 25C–30C LiPo.