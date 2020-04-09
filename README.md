# NVP Electronic Controller

A highly-configurable, ready-to-manufacture electronic controller for use in low-cost CPAP ventilators. This design adheres to the specifications laid out in the National Ventilator Project (NVP) Call for Proposals of 4 April 2020. The authors are not affiliated with the NVP.


Inside this repository are the following resources:

- Printed circuit boards (PCB) designs, provided both as Gerber files and an Eagle project
- Bill of Materials
- Firmware for an 8-bit Microchip microcontroller


This design is free for anyone to use without restriction or acknowledgement. The authors request that any additional design work on the basis of this controller is open-sourced as well.


## Core Features

- Gas supply on/off push-buttons
- Push-button input of desired inspired oxygen proportion (FiO<sub>2</sub>)
- Push-button input of desired continuous airway pressure
- LED feedback of actual airway pressure
- Electrical control of inspired oxygen proportion actuator
- Electrical control of airway pressure actuator
- Powered by consumer-grade USB power bank or cell-phone charger


## Documents

The controller design outlined in this repository is based on the following documentation:

1. [National Ventilator Program (NVP) Call for Proposals (CFP)](http://www.thedti.gov.za/news2020/CFP_NVP.pdf)
2. 




# Sub-system overview



## Microcontroller



## LED feedback

LED arrays provide feedback for the following metrics:

1. Desired inspired oxygen proportion (FiO<sub>2</sub>)
2. Desired airway pressure
3. Current airway pressure


LEDs are arranged in vertical rows, placed within clearly-deliniated labelled sections. Each LED is laballed with its discrete value. This eliminates the need for any seperate labelling or faceplate.

Provision is made on the PCB for either 5mm through-hole, 3mm through-hole or 0603 (1608 metric) surface-mount LEDs.


### Desired inspired oxygen propoprtion

The NVS specification calls for inspired oxygen proportion (FiO<sub>2</sub>) to be set in increments of 10% over a range of 30% to 100%. An array of 8 LEDs are installed for this purpose.

Feedback for actual current FiO<sub>2</sub> is not considered.


### Desired airway pressure

The NVS specification calls for airway pressure to be set within a range of 5 to 25 cmH<sub>2</sub>O. Arbitrary intervals of 5 cmH2O results in 5 LEDs.

### Actual current airway pressure

The NVS specification calls for airway pressure to be set within a range of 5 to 25 cmH<sub>2</sub>O, and for a maximum over-pressure of 40cmH<sub>2</sub>0. A pressure monitoring range of 0cmH<sub>2</sub>0 to 40cmH<sub>2</sub>0 is considered. A 9-LED array provides feedback in increments of 5cmH<sub>2</sub>0.


## Power

Input power is provided by a USB power bank or cell-phone charger. Most end users are expected to have at least one of these consumer-grade devices already in their possession, and failing this, they are cheaply and easily sourced elsewhere.


A consumer-grade USB supply eliminates the need for on-board AC/DC conversion or 5V voltage regulation. Two configurations are possible:

1. USB charger only
2. USB charger, connected to USB power bank

A back-up power period of 30 minutes or more is given by the NVS requirement specification, and therefore the second power configuration is recommended. Power use of the controller will depend on the exact configuration. The product of the 0.5 hour requirement and typical controller current draw (for a given configuration) will provide the battery bank cappacity requirement.




# Adherence to NVS requirements

## NVS external interface requirements


| Interface | ID | Requirement  | Applicability |
| --------- | -- | ------------ | ------------- |
| I.1: Oxygen supply | R.I.1 | All gas connectors and hoses must use standard non-interchangeable connectors and be colour coded according to recognised medical standards. | Not applicable to controller |
| I.1: Oxygen supply | R.I.2 | The NVS Oxygen inlet shall connect to standard South African hospital wall Oxygen supply or Oxygen bottle interfaces. |

## 


[a link](#pcb-mounted-pressure-monitoring)



# PCB mounted pressure monitoring


