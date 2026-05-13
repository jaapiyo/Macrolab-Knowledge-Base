---
title: Control 5
description: 
---

!!! note
    The hardware described on this page is still under development. It is likely to change.

# The next generation hardware controller
Since the initial deployment of the first [Control 2](../control-2) High Speed Servo Controllers in 2013, many of the uniaxial testing machines in the lab have been converted to use this as their main controller. The Control 2 replaced many Instron 8400 series that were old and tired. 

However the Control 2 hardware design was very labour intensive to manufacture. This made it difficult to produce them and they were always in shortage because of this.

The Control 5 design aims to improve the manufacturability and continue the Control 2 design ideology. It also introduces a modern interface for connecting pheriferals. So we can finally move away from the old Schenk legacy connector layouts and the many "interface boxes" that were built in order to connect everything.

The options for using servomotors/stepper motors or other output actuators will also be expanded. Together with inputs for incremental and absolute encoder systems.

# Input/output

| Channel | Function | Conditioner circuitry |
| --- | --- | - |
| AI 1 | Channel 1 (Force) | Instrumentation amp |
| AI 2 | Channel 2 (Displacement) | Instrumentation amp |
| AI 3 | Channel 3 | Instrumentation amp |
| AI 4 | Channel 4 | Instrumentation amp |
| AI 5 | Channel 5 | Instrumentation amp |
| AI 6 | Channel 6 | Instrumentation amp |
| AI 7 | SV actual current | Measured current in SV output loop (+/- 20 mA to +/- 300 mA) |
| AI 8 | External FG | External setpoint input +/- 10 V |
| AO 1 | Servovalve / servodrive | - |
| AO 2 | Analog out 1 | - |
| AO 3 | Analog out 2 | - |
| AO 4 | Analog out 3 | - |
| INCR ENC | Incremental encoder input | 422 Line Receivers |
| ABS ENC | BISS-c / SSI encoder input | 422 Line Tranceivers |
| S/D / CW/CCW | Pulsed output for stepper motors | 422 Line Transmitters |
| DI 1 | Safe stop | - |
| DI 2 | Pressure switch | - |
| DI 3 | - | - |
| DI 4 | Emergency stop | - |
| DO 1 | Manifold low pressure | Relay |
| DO 2 | Manifold high pressure / Drive enable | Relay |
| DO 3 | - | - |
| DO 4 | - | - |

The second analog input will no longer have a dedicated LVDT conditioner. The IC's used for this in Control 2 are no longer available and we will start to use temperature compensated magnetostrictive displacement transducers from now on. Existing actuators with LVDT's can be upgraded, or BICM's can be used instead.

## Inputs 1-6 (Multi-function)
Switchable input gain is desirable. Programmable gain instrumentation amplifiers are available ([AD8253](https://www.analog.com/media/en/technical-documentation/data-sheets/ad8253.pdf)) that make this easy. The amplifier gain is selectable between 1, 10, 100 and 1000. A gain of 1 is helpfull in reducing the need for switches to bypass the amplifier in direct mode. Gain of 10 will not be used that often, but a gain of 100 is intresting for silicon based strain gauge bridges with high k-factors.

In Control 2, both bridge amplifier inputs had their own adjustable excitation power supplies. Using outputs of the DAC, the output voltage and offset could be set. For Control 5 multiple excitation voltages will be available and a selection can be made simply by soldering to different contacts in the 15-pin sub-d connectors. For now ±1 V, ±3 V and ±10 V will be provided. To prevent interference each channel will get it's own output buffer amplifier.

## Analog outputs
To send analog signals to external devices analog outputs are used. These outputs must be able to drive long cables (10 m or more). Care must be taken to maintain stability in the output buffer amplifiers inside the controller. With RG-57 cables the capacitance increases about 57 pF per meter. This can quickly become problematic and cause instability in the buffer amplifier. The instability is caused mostly by internal resistance in the output pin of the amplifier. This combined with the capacitive loading causes the phase margin to decrease with increased output capacitance.

# Function generator
The internal function generator will provide the following waveforms

| Type | Description | Notes |
| --- | --- | --- |
| Ramp | Move to new setpoint with constant rate | - |
| Sine | Sinewave oscillation around current setpoint with a set amplitude and frequency | - |
| Triangle | Triangular oscillation | - |
| Square | Square wave oscillation | Usefull for PID tuning |
| Haversine | Sinewave oscillation offset by half the amplitude and starting at zero ($y(t)=\sin^2(x(t)/2)$, [More info](https://reference.wolfram.com/language/ref/Haversine.html.en)) |
| White noise | Wideband noise with equal intensity at different frequencies | Usefull for system identification (See also [PRBS Test](https://www.yokogawa.com/library/resources/white-papers/pid-tuning-in-distributed-control-systems/)) |

## Parameter sweeping
Sometimes researchers want to be able to sweep accros a certain frequency range, for instance to scan for resonant modes. Currently the controller firmware doesn't support this. Adding this will be usefull. 

We will be implementing a broader way to sweep not only frequency but also amplitude and maybe other parameters as well.