> [!danger] Danger
> **Machines have no brain, always use your own!**
> 
> You might be tempted to use load-protect to make the setup safe to work on while energized. However, you can never trust an energized machine! Always de-energize the setup before working on the specimen!

Load protect is a function that will try to limit the force that is produced in the setup. It works in all control paths and internally switches to force-control within 100 us when the load protect value is reached.

Load limit is a function that stops force control and quickly (within 100 us) switches to position control whenever a limit value is reached.