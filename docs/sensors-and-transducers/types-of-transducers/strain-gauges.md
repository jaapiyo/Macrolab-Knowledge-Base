## Theory
Strain is a physical property describing the geometrical deformation caused by applying an external stress to a body. Strain is unitless but strain values are denoted with the Greek letter epsilon $\upepsilon$  or more commonly with $\upmu\upepsilon$, when talking about microstrain. For example:  $2000\;\upmu\upepsilon$. Sometimes you'll see a strain value denoted with $\text{Str}$ or $\upmu\text{Str}$.

$$\epsilon = \frac{\Delta l}{l_0}$$

Strain gauges are precise electrical resistors which are sensitive to elongation. This sensitivity comes from the stretching of the conductor causing a decrease in its cross sectional area and thus a slight increase in it's resistance.

!!! example
    A commonly used strain gauge is the FLAB-6-11 from TML ![](../media/FLAB-6-11.svg){  width="300", align=right }

    There are also stacked strain gauges available that are sensitive in three directions. These are called rosettes and a common type is the FRAB-6-11 from TML: ![](../media/FRAB-6-11.svg){ width="300", align=right }


This relationship is as follows, where $K$ is constant given by the manufacturer of the strain gauge:

$$
\epsilon \cdot K = \frac{\Delta R}{R} \quad\Rightarrow\quad \epsilon=\frac{\Delta R}{R\cdot K}
$$

### Gauge factor
The gauge factor $K$ gives the relationship between the change of electrical resistance and the strain acting on the strain gauge. It is defined as follows:

$$
K = \frac{\Delta R/R_0}{\epsilon}
$$

The gauge factor is dependent on the geometric shape of the conductor of the strain gauge, but its also influenced by it's [piezoresistive effect](https://en.wikipedia.org/wiki/Piezoresistive_effect). For common thin-film metal strain gauges (like the FLAB-6-11 from TML) this accounts for 20% of the gauge factor. The full definition for the gauge factor is as follows:

$$
K = \frac{\Delta R/R_0}{\Delta l/l_0} = \frac{\Delta R/R_0}{\epsilon} = 1 + 2 \nu + \frac{\Delta \rho/\rho_0}{\epsilon}
$$

Some gauge factors for common strain gauge materials can be seen in the table below.

| Material                          | Gauge factor |
| --------------------------------- | ------------ |
| Metal foil strain gauge           | 2 to 5       |
| Thin-film metal (e.g. constantan) | 2            |
| Single crystal silicon            | -125 to 200  |
| Polysilicon                       | ±30          |
| Thick-film resistors              | 100          |
| p-type Germanium                  | 102          |

### Converting mV/V to strain
The mV/V value is the output voltage when a maximum load is applied to a transducer. It shows the output voltage generated when 1V excitation is applied.

Often the sensitivity is specified in $\text{mV}/\text{V}$. The table below shows values assuming $K=2.0$.

| Rated output (mV/V) | Estimated effective strain (µε) |
| ------------------: | ------------------------------: |
|                 1.0 |                            ~500 |
|                 1.5 |                            ~750 |
|                 2.0 |                           ~1000 |
|                 2.5 |                           ~1250 |
|                 3.0 |                           ~1500 |


The relationship between mV/V and microstrain depends on the gauge factor ($K$).

$$
\epsilon_\mu = \frac{\text{mV/V}\cdot1000}{K}
$$

!!! note
    Load-cell manufacturers don’t publish GF because the finished load cell’s output is determined by mechanical design and trimming, not by the strain-gauge k-factor, making GF non-unique, non-measurable, and non-useful at the product level.


!!! example
    A load cell has a sensitivity $S = 2.0\;\text{mV}/\text{V}$ and a rated capacity $M_{max} = 1000\;\text{kg}$. 
    The excitation voltage $U_s = 6\;\text{V}$, therefore the full scale output of the load cell is $2\cdot6 = 12\;\text{mV}$
    If you have an amplifier with $G=1000$ the output voltage of the amplified signal at full scale is 
    
    $$
    12\cdot10^{-3}\cdot1000=12 \;\text{V}
    $$

    Now the conversion factor $C$ in the data-aquisition system is
    
    $$
    C=\frac{1000\cdot9.81}{12} = 817,5\;\text{N}/\text{V}
    $$


### Converting voltage to strain
To calculate the conversion factor it's important to know the gauge factor $K$, the bridge configuration, the excitation voltage $U_s$ and the amplifier gain $G$.

For a 1/4 bridge (1 active gauge and 3 dummy resistors) the relationship between the output voltage and the strain is defined as:
$$
\epsilon = \frac{4}{K}\cdot\frac{U_o}{U_s}\cdot G
$$
The conversion factor $C$ can be defined as:
$$ C= [\upmu\upepsilon/\text{V}] $$

!!! example
    A single strain gauge with a gauge factor $K=2.08$, 1/4 bridge, and excitation voltage $U_s=6 \text{v}$, and an amplifier gain $G=1000$.
    $$
    \epsilon = \frac{4}{2.08}\cdot\frac{U_o}{6}\cdot 1000
    $$

### Adding strain with a resistor
You can test a Wheatstone bridge by adding a resistor in parallel with a strain gauge. This will give the same effect as strain applied to the gauge.

**Adding 56 kΩ in parallel with 120 Ω**

| k    | $\upmu\upepsilon$ |
| ---- | ----------------- |
| 2.00 | 1069              |
| 2.11 | 1013              |
| 2.12 | 1008              |
| 2.13 | 1003              |
| 2.14 | 999               |

### Bridge completion
Use 1206 SMD resistors, they are less sensitive to mechanical strain. Make sure the temperature coefficient is lower than ± 25ppm/°C. This is a common value for ± 0.1% tolerance resistors.

For example ± 100ppm/°C 120 Ω resistors can change about 12 mΩ (50 µε) per degree Celsius. Which is way too much for most strain measurements.

| Manufacturer | Part nr.    | Resistance   | Temperature coefficient |
| ------------ | ----------- | ------------ | ----------------------- |
| Panasonic    | ERA8AEB121V | 120 ± 0.1% Ω | ± 25ppm/°C              |


### Definitions
$$
\begin{align}
\upepsilon&:\text{strain unit}\\
\sigma &: \text{stress }&[\text{N}/\text{mm}^2 = \text{MPa}]\\
\nu &: \text{Poisson's ratio} \\
A &: \text{area}&[\text{mm}^2]\\
E &: \text{modulus of elasticity} & [\text{N}/\text{mm}^2 = \text{MPa}]\\
F &: \text{force} & [\text{N}]\\
R &: \text{resistance} & [\Omega]\\
\rho &: \text{specific electrical resistance} & [\Omega \text{m}]\\
K &: \text{gauge factor}\\
l &: \text{length} & [\text{m}]\\
l_0 &: \text{initial length} & [\text{m}]\\
\upmu\upepsilon &: \text{notation of units of microstrain}
\end{align}
$$
