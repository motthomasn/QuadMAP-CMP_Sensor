# QuadMAP-CMP_Sensor

Iteration of single MAP-CMP_Sensor described: https://github.com/motthomasn/MAP-CMP_Sensor 

Small module combining 4xMAP sensors and engine phase sensor (camshaft posn) for internal combustion engine management on 4-cylinder engines with individual port throttles.

This module was built for my CBR250RRi project. The aim was to allow an aftermarket ECU to achieve 720deg synchronisation or engine phase detection without the use of a physical camshaft position sensor being installed on the engine. 

The board uses NXP pressure sensors to measure the pressure pulses in each port. The pressure signal from cylinder 1 is passed to an LM397 comparator and compared to a reference voltage determined from a fixed voltage divider. 
The output signal from the comparator is normally high but when the pressure signal falls below the reference voltage, the output is pulled low. With the reference voltage set correctly, a reliable "cam position" signal can be achieved at engine idle
consisting of a single pulse per engine cycle.

**Note:** In a port throttled engine, the pressure signal may not be strong enough to produce a reliable signal throughout the engine speed/load range. In my application this is fine as the ECU I am working with (Life Racing F88R) allows the option to 
ignore the engine phase signal once 720deg synchronisation has been achieved. This means that the signal only has to be reliable during starting and idle.

The signals from all four pressure sensors are processed via LMV324 op-amps so that the output is always the minimum of the four individual signals. This ensures a more stable and reliable pressure signal for engine management.

### Sensor Pinout

Mating connector is JST JWPF 04R-JWPF-VSLE-S.

| Pin # | Description |
|:-----:|:------------|
| 1 | CMP Signal |
| 2 | GND |
| 3 | +5V |
| 4 | MAP Signal |


## Breakout Details

A breakout connector is also included to access the individual raw pressure sensors for diagnostics or possibly throttle body balancing. 

**Wire gauge:**	0.35mm2  
**Sheath:**		Raychem DR-25 1/4"  
**Connector:**	DB9 Female. RS 765-9555  
**Wire Length:**	570mm. Case to back of connector


### Breakout Pinout

| Pin # | Description |
|:-----:|:------------|
| 1 | map1 |
| 2 | map2 |
| 3 | map3 |
| 4 | map4 |
| 5 | GND |
| 6 | N/C |
| 7 | N/C |
| 8 | N/C |
| 9 | N/C |