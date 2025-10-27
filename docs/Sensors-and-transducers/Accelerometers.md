Accelerometers convert acceleration (rate of change of velocity) into a measurable quantity like a voltage or a digital value. Accelerometers always measure acceleration relative to freefall, this is also called [proper acceleration](https://en.wikipedia.org/wiki/Proper_acceleration). On earth an accelerometer at rest will indicate approximately 1 *g* upwards. 
$$1\;\text{g}=9,81\;\text{m/s}^2$$

There two common types of accelerometers we use in the lab:
- MEMS
- Piezoelectric

MEMS accelerometers are usually very cheap (about 50 euro/piece) and can be used disposably. Commonly used models can be found in the table below.

| Name        | Range            | Output            | Note                                                                                             |
| ----------- | ---------------- | ----------------- | ------------------------------------------------------------------------------------------------ |
| ADXL335     | ± 3 *g*          | Tri-axial, analog |                                                                                                  |
| ADXL326     | ± 16 *g*         | Tri-axial, analog |                                                                                                  |
| ADXL354B    | ± 2 *g*, ± 4 *g* | Tri-axial, analog | Range selectable with pin                                                                        |
| ~~ADXL377~~ | ± 200 *g*        | Tri-axial, analog | **EOL, no longer produced**^[No longer produced https://www.analog.com/en/products/adxl377.html] |

From these types we usually buy development boards made by Adafruit because they contain a voltage regulator and output filtering capacitors. This makes it easy to use the accelerometers however care should be taken when using long cables ($l>10\;\text{m}$). The high output impedance (32 kΩ) means the accelerometer output signal will be degraded.

Piezoelectric accelerometers resist shock loading much better than MEMS types. They are also better suited for high frequency measurements. However their sensitivity doesn't reach all the way to 0 Hz. Below are a few types we have experience with:

| Name       | Range    | Output            | Note                                                               |
| ---------- | -------- | ----------------- | ------------------------------------------------------------------ |
| 830M1-0200 | ± 200 g  | Tri-axial, analog | Intenal amplifier, output is ± 1,25 V full scale                   |
| 3038-2000  | ± 2000 g | Uni-axial, bridge | Needs an instrumentation amplifier <br>and offset adjust circuitry |

Piezoelectric accelerometers are more expensive but often come with a calibration report and can be considered more reliable.

## Vibration resistant mounting
