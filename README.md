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
