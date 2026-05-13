---
title: Tuning
description: 
---
# Tuning

Tuning a control system means adjusting its parameters so it responds to errors or disturbances in a desirable way. The core goal is to make the system behave as intended eg. the output (speed, temperature, position, etc.) should reach and maintain the desired setpoint accurately.

More specifically, tuning balances several competing objectives:

- **Stability**, the system shouldn't oscillate wildly or diverge. An untuned controller can cause the output to overshoot and never settle.
- **Speed of response**, how quickly the system reaches the setpoint after a change. Faster isn't always better if it causes instability.
- **Steady-state accuracy**, eliminating the long-term error between the desired and actual output (offset).
- **Disturbance rejection**, how well the system recovers when something external disturbs it (a load change, noise, etc.).
- **Robustness**, the system should still behave acceptably even if the plant (the thing being controlled) changes somewhat over time.

These goals are often in tension. For example, making a PID controller respond faster (higher gain) tends to increase overshoot and can push it toward instability. Tuning is the act of finding the right trade-off for your specific application.

# Tuning servohydraulic systems
Know what you're controlling — position, velocity, or force? Each has different loop dynamics.
Key hydraulic dynamics to be aware of:

- The system has a hydraulic natural frequency (ωh), determined by load mass, piston area, fluid bulk modulus, and trapped volume. This is the resonance you'll be fighting.
- Below ωh the actuator behaves roughly like a double integrator (for position control), which means it has 180° of phase shift already built in — this limits how much gain you can apply before instability.
- The servovalve itself has its own bandwidth (often 100–300 Hz for a typical valve), which adds further phase lag.
- Friction and stiction create a nonlinear dead zone near zero velocity — important for low-speed or fine positioning.
- Valve null/deadband — most servovalves have a small null offset and hysteresis that needs compensation.

Characterize the plant first:

- Apply a low-amplitude swept sine or PRBS (pseudo-random binary sequence) signal open-loop and measure the frequency response (Bode plot) of the actuator output vs. valve command.
- Identify ωh and where phase starts dropping rapidly — this tells you your practical bandwidth ceiling.
- At 10 kHz your sampler is well above anything mechanical, so discretization isn't your constraint here.

## Tune in This Order: P → D → I
**Step 1 — Proportional gain (P)**

Zero out I and D.
Apply step commands and increase P until the response is reasonably fast but you start to see overshoot or oscillation developing.
Back off to roughly 50–60% of the oscillation threshold.
Hydraulic systems can tolerate decent P gain because of the inherent stiffness of the fluid, but the double-integrator plant means you'll hit instability faster than in, say, a motor drive.

**Step 2 — Derivative gain (D)**

For position control of a hydraulic actuator, D is critical — it provides the damping that the plant itself lacks.
Increase D until overshoot is reduced to an acceptable level and the step response is well-damped.
Always use a filtered derivative — a first-order low-pass on the D term is standard:

$$
D_{filtered} = \frac{D \cdot s}{(\tau_f s + 1)}​
$$

Set the derivative filter cutoff typically at 10–50x your target closed-loop bandwidth, but well below the noise floor. At 10 kHz you have headroom, but don't go too high or you're amplifying sensor noise.
Watch for high-frequency chatter in the valve command signal — the valve will wear prematurely if the command is noisy.

**Step 3 — Integral gain (I)**

Add I last, once P and D are stable.
I eliminates steady-state error and helps overcome static friction.
Increase slowly — too much I causes slow, low-frequency oscillation.
Implement anti-windup — hydraulic systems often saturate (valve at full open/close), and integrator windup will cause large overshoots on recovery. Clamping or back-calculation anti-windup is standard practice.

## Addition
**Valve null compensation:**
Apply a small offset to your control output to compensate for the valve's null position (the command value that gives zero flow). Characterize this open-loop.

**Dither signal:**
A small, high-frequency dither (typically at a frequency above your control bandwidth but within the valve's bandwidth) added to the valve command reduces stiction effects by keeping the valve spool in motion. Amplitude should be enough to overcome spool stiction without causing measurable actuator motion.

**Pressure/force feedforward:**
If you have pressure transducers, an inner pressure loop or a feedforward from load pressure can significantly improve disturbance rejection and linearise the plant.

**Velocity feedforward:**
For tracking applications (not just point-to-point), adding a velocity feedforward term (from your reference trajectory) dramatically reduces tracking error without pushing the feedback gains harder.

## Performance Targets (Frequency Domain View)
If you do the frequency response identification:

- Aim for phase margin ≥ 45° and gain margin ≥ 6–10 dB for robust stability.
- Your closed-loop bandwidth will typically be limited to 1/3 to 1/5 of ωh — trying to go faster than this risks exciting the hydraulic resonance.
- Watch the Bode plot for a resonant peak — if you see one growing as you increase gain, you're approaching instability.

## Practical Iteration
Once gains are set analytically or by the above steps:

- Test with various step amplitudes — hydraulic nonlinearities mean the system may behave differently at small vs. large commands.
- Test at different load conditions if the load changes (e.g., varying mass or back-pressure) — the hydraulic natural frequency shifts with load.
- Monitor the valve command signal in time and frequency — it should be smooth; high-frequency content means you're amplifying noise and will wear the valve.
- If you have access to it, log supply pressure during dynamic moves — pressure drops under high flow demand can destabilise a tightly tuned loop.

## Example transfer function
Showing the magnitude and phase response of a simplified hydraulic servovalve actuator open-loop plant. The plot spans 0.1 to 1000 Hz, marks the hydraulic and valve resonances, and highlights the -180° phase boundary.

<iframe src="../../media/hydr-tuning-bode.html" style="width: 100%; height: 600px; border: 0"></iframe>

## PRBS example
PRBS (pseudo-random binary sequence) is a deterministic, periodic signal that switches between two levels (+1 and −1) according to a shift-register sequence. Its power spectral density is nearly flat up to a certain frequency, then rolls off. It approximates white noise within a limited bandwidth, not across all frequencies.

**Clock rate** is the most important setting. You need it high enough that the flat band covers your frequencies of interest — at minimum past ωv at 150 Hz, so 500 Hz clock is the practical minimum. 1 kHz is a comfortable choice. Notice how below 500 Hz the annotation warns you that ωv isn't covered.

**Amplitude** should be kept small — ±3–5% of valve full scale is typical. Large enough to get a measurable response above the noise floor, small enough that the actuator stays in the linear region of the valve flow curve and doesn't move so much that it hits end stops or loads up against something.

**Register length n** controls how long the sequence is before it repeats. Longer sequences give smoother, more averaged spectra (less variance in the PSD estimate), but take longer to acquire. For your 10 kHz controller, n=8 at a 1 kHz clock gives a 255-bit period lasting only 255 ms — you'd typically run several periods and average them. n=10 gives about 1 second per period at the same clock, which is often enough in a single pass.

<iframe src="../../media/prbs.html" style="width: 100%; height: 700px; border: 0"></iframe>