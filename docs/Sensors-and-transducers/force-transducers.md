Load cells based on [[strain gauges]] are commonly used to measure force in both static and dynamic testing setups. Force is measured indirectly because strain gauges measure local deformation of the base material of the load cell. A conversion factor is used to convert strain into force.

## Measuring force
Force acting on an object generates stress within the object. This amount of stress is determined by the surface area the force is acting upon.

$$
\sigma =\frac{F}{A}
$$

The relationship between stress and strain is based on a material property called the modulus of elasticity (Young's modulus). This relationship is only valid in the linear elastic region of a material.

$$
\epsilon=\sigma\cdot E
$$

The modulus of elasticity of steel is about 200 GPa, aluminum 69 GPa and concrete 30 GPa.

!!! example
    Strain in a steel cilinder as a result of an applied tension force $F=100\;\text{kN}$. With a diameter of $d=20\;\text{mm}$.

    $$
    \begin{align}
    A &= \pi\cdot d^2\\
    &= \pi\cdot 400\\
    \end{align}
    $$

    $$
    \begin{align}
    \epsilon &= \frac{F}{A\cdot E}\\
    &= \frac{100\cdot10^3}{\pi\cdot400\cdot200\cdot10^3}\\
    &\approx 378 \;\upmu\upepsilon
    \end{align}
    $$
    
Typical design targets:

- 500–800 µε → long fatigue life, lower output
- 800–1200 µε → most industrial load cells
- 1200–1800 µε → high-output, lower fatigue margin
- >2000 µε → rare, special-purpose only

This aligns closely with common 2–3 mV/V products.