# Backup Power Circuit Design
#### Client Name: Issam Smaali

## Project Requirements
- Design a circuit to handle input from a primary power source (5V) and seamlessly switch to a backup power supply using supercapacitors.
- Use 2 x Supercapacitors in series to be able to achieve a maximum backup time of around 80 seconds.
- Integrate components like supercapacitor chargers, boost converters , and power filtering circuits.
- Ensure the backup system provides stable output voltage during transitions between main power and backup mode.
- Optimize efficiency and performance to meet system requirements.
- Research and select appropriate electronic components such as diodes, capacitors, boost converters, and supercapacitors for the design.
- Ensure the design meets cost, reliability, and space constraints.
- Prepare detailed schematics, PCB layouts, and technical documentation for production.

### Schematic Description
Illustrated below is a proposed concept of handling the design requirements. Key components / blocks are also explained below:
![image](https://github.com/user-attachments/assets/4b4b3181-9c20-4ae6-9c20-bc0c2becfbf6)

#### Key Components / Blocks
1. Buck and BOOST CONVERTER
2. Discrete charger with adjustable current and voltage limit
3. Transition between normal and backup operation

### Sequence Description
1. The DC input voltage Vin of this design can range 5v, in normal operation a buck/LDO converter supplies to load. If the main power fails there is an automatic switch over a single supercapacitor without the need of any external logic. Then the boost converter immediately starts regulating the system voltage and uses the stored energy of the super capacitor for backup operation.
2. When the main power recovers, the circuit automatically supplies the load from the mains and starts recharging the supercap.

#### Discrete Charger
A discrete charger using “TPS25940A eFuse”. When the eFuse is enabled, the super capacitor voltage starts building up after the eFuse turn ON delay and charges supracapacitor to 2.7v and to its rated capacity without thermal shutdown. During backup operation, a Schottky diode prevents the current flow from Vout to VIN to prevent any additional load on the backup power system. Similarly, the SuperCap charger circuit must have reverse current blocking capability to avoid draining the super capacitor. When the main power restores, it is important to limit the charging (inrush) current for the discharged super capacitor to avoid disturbance on the system voltage.

#### Boost Converter
The Boost converter “TPS61022RWUT” can handle a very low input voltage of 0.5v, enabling most of the energy stored in the supracapacitor to be used. It provides a stable output voltage of 3.9v at 200mA. Disable the controller where the input voltage Vin is present by adding a diode connecting the boost feedback.

### PCB Description
#### Overview of available space
The diagram below illustrates what space is available on the PCB for making additions required above. This will give a good idea in determining the size and volume of components to be used in the design. The hatched / crossed area is the place where new circuitry should reside:
![image](https://github.com/user-attachments/assets/42a35008-9995-4016-8fbf-6c0762bbd6f3)
