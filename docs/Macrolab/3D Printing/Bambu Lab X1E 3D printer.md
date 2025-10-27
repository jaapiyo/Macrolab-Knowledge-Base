## Preferred filament types
There are many options available for printing filaments. However to keep printer maintenance to a minimum, and to ensure consistent results we like to stick to the following types of filament used in our printers:
- Bambu Lab PETG Basic
- Bambu Lab PETG-CF
- Bambu Lab PLA-CF

PETG is really well suited for use in our lab. It is impact and water resistant, slightly flexible and has strong layer adhesion. For mechanically stressed parts that need to be strong the PETG-CF filaments are great. The added carbon fiber increases the stiffness and wear resistance of the parts significantly.

PLA-CF is the fastest printing, but still really strong filament. Where normal PLA has the tendency to be brittle and breaks easily on impact. However it's not currently known to us if this material is stable over long term or if it degrades over time.

While filaments like ABS and ASA also perform really well mechanically and have good resistance to our lab conditions, the pungent odor and relatively large thermal expansion ratios make them less ideal to print with in our lab.

Printing with Bambu Lab filaments is preferred because of the quick and easy integration in the AMS[^1] with the RFID tags that are incorporated in the spools.
[^1]: Bambu Lab Automatic Material Switcher

Buying filament without the spool holder is preferred to minimize waste. Bambu Lab spools can easily be taken apart and refilled with new filament. The new filament has it's own RFID tag so the AMS will correctly recognize it.
## Connecting to the TU Delft network
1. Request an IP address based on the MAC address of your printer. You can do this with a IT Self Service ticket.
2. Connect the printer to an active network port.
3. Install Bambu Studio on your PC.
4. Add a firewall rule on your PC to allow incoming UDP packets on port 2021.

![[bambu_autodiscovery_firewall_settings.png]]