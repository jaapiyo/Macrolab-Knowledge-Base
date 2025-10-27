A control system is used to regulate the behavior of a device or system using control loops. Usually a setpoint is given and the control system will change it's output such that deviation from the setpoint (error) is minimized. [[Tuning]] is used to optimize the speed at which the target is reached.

Control systems are sometimes also called *servo controller* or *servo* for short. In our lab we use a lot of [[Controller hardware|servo hydraulic controllers]] for force and displacement control in our testing machines.

## Open loop control
When a control system has no feedback method it is considered *open loop*. These are also known as *feedforward controllers*. An example of such a system is a heater that's controlled by a timer. The heater will turn on for a set amount of time, however the temperature of the heater is completely unregulated.

## Closed loop control
A system where the output of the process is measured is considered *closed loop*. Also known as *feedback controllers*. 