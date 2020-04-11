### Last updated 11/04/2020
# NVS Electronic Controller



A configurable, ready-to-manufacture controller hardware design for use in low-cost CPAP ventilators. It incorporates an operator interface, pressure-sensing mechanism, and control of arbitrary actuators. It is powered by a standard 5V USB power bank or cell-phone charger.

This design is intended to accelerate development efforts towards the National Ventilator Project (NVP). Use directly as a ventilator controller or monitor, use with modification, or use as a reference design. 


Inside this repository are the following resources:

- An overview of the controller hardware design (this page)
- Printed circuit boards (PCB) designs: Gerber files and EAGLE project
- Bill of Materials
- <u>Firmware  not included</u> (sample firmware for 8-bit PIC microcontrollers is on its way)




## Ready to immediate manufacture

- Implemented on standard, 2-layer PCB
- Allowance for either through-hole (THT) or surface-mount (SMT) variants for most components - use whichever is easier/quicker.
- Relies mostly on simple, widely-available components which can be found in any hobby store or lab.
- Clear, user-friendly on-PCB labelling of controls.
- Breakouts allow for use with any arbitrary microcontroller or external electronics.


## NVP

This design is intended for use in a Non-invasive Ventilator System (NVS) which adheres to the specifications laid out in the NVP Call for Proposals of 4 April 2020. See [Documents](documents) for details.

The authors of this repository are not affiliated with the NVP or SARAO.


## Timeline

Improvement and expansion of this design is ongoing.

Ongoing work and expected completion dates are summarized in the table below.

| Description | Completion |
| ----------- | ---------- |
| Initial release | 11 April 2020 |
| New version of PCB that includes a selection motor drivers | 13 April 2020 |
| Monitor-only variant of PCB | 16 April 2020 |
| Sample firmware for 8-bit PIC microcontroller | 18 April 2020 |
| <b>Will be determind based on feedback</b> | Future |





## Documents

More information about the NVP can be found at the links below.

1. [Media release - SARAO mandated to manage the production of respiratory ventilators](https://www.sarao.ac.za/media-releases/sarao-mandated-to-manage-the-production-of-respiratory-ventilators/)
1. [National Ventilator Program (NVP) Call for Proposals (CFP)](http://www.thedti.gov.za/news2020/CFP_NVP.pdf)


## Notes and acknowledgements

This design is free for anyone to use without restriction. In the spirit of disregard for personal gain, the authors request that any additional work, done on the basis of this, be seriously considered for open-sourcing as well.

This design is <b>provided as is</b> and without warranty.

Contributions are welcome. Feedback is appreciated.



# Overview of design


## Monitor-only vs. Monitor and control

This design is available in two different flavours:

- Monitor only: Visually reports airway pressure, with auditory pressure loss and over-pressure alarms.

![Monitor onlyoverview](/nvp_controller_overview_monitor_only.png?raw=true)

- Monitor and control: Simple push-button input of target FiO<sub>2</sub> and airway pressure, actuator control

![Monitor and control overview](/nvp_controller_overview_monitor_and_control.png?raw=true)


## Core Features

| Feature | Monitor only | Monitor and control |
| ------- | :----------: | :-----------------: |
| Powered by consumer-grade USB power bank or cell-phone charger | X | X |
| LED display of actual airway pressure | X | X |
| Auditory over-pressure / pressure loss alarm | X | X |
| Push-button input and LED display of desired FiO<sub>2</sub> | | X |
| Pre-programmed control of FiO<sub>2</sub> actuation | | X |
| Push-button input and LED display of desired continuous airway pressure | | X |
| PID control of FiO<sub>2</sub> actuation | | X |
| Gas supply on/off push-buttons and LED display | | X |
| Gas supply on/off actuator control | | X |








# Sub-system overview



## Microcontroller


## Pressure sensing


## LED displays

7-segment provide feedback for the following metrics:

1. Desired inspired oxygen proportion (FiO<sub>2</sub>)
2. Desired airway pressure
3. Current airway pressure

Additionally, discrete LEDs can be used to 


LEDs are arranged in vertical rows, placed within clearly-deliniated labelled sections. Each LED is laballed with its discrete value. This eliminates the need for any seperate labelling or faceplate.

Provision is made on the PCB for either 5mm through-hole, 3mm through-hole or 0603 (1608 metric) surface-mount LEDs.


### 1. Desired inspired oxygen propoprtion

The NVS specification calls for inspired oxygen proportion (FiO<sub>2</sub>) to be set in increments of 10% over a range of 30% to 100%. An array of 8 LEDs are installed for this purpose.

Feedback for actual current FiO<sub>2</sub> is not considered.


### 2. Desired airway pressure

The NVS specification calls for airway pressure to be set within a range of 5 to 25 cmH<sub>2</sub>O. Arbitrary intervals of 5 cmH<sub>2</sub>0 results in 5 LEDs.

### 3. Actual current airway pressure

The NVS specification calls for airway pressure to be set within a range of 5 to 25 cmH<sub>2</sub>O, and for a maximum over-pressure of 40 cmH<sub>2</sub>0. A pressure monitoring range of 0 cmH<sub>2</sub>0 to 40 cmH<sub>2</sub>0 is considered. A 9-LED array provides feedback in increments of 5 cmH<sub>2</sub>0.


## Actuators

Provision is made for control of actuators with the intent of being non-prescriptive in mechanical design. Three actuators are accomodated:

1. Airway pressure control actuator
2. FiO<sub>2</sub> actuator
3. Flow control actuator


Actuator outputs can be configured in one of two modes:

- Positive/negative DC, intended for on-off solenoid actuation.
- Stepper motor control, intended for control valve actuation.


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
| I.1: Oxygen supply | R.I.2 | The NVS Oxygen inlet shall connect to standard South African hospital wall Oxygen supply or Oxygen bottle interfaces. | Not applicable to controller |
| I.1: Oxygen supply | R.I.3 | The NVS shall regulate the supplied Oxygen pressure as needed to operate effectively. | |
| I.4: Exhalent | R.I.4 | All parts coming into contact with the patient’s breath must be either disposable or able to be decontaminated between patients. | |
| I.4: Exhalent | R.I.5 | The exhaled gas shall be filtered with an easily replaceable HMEF viral filter. | Not applicable to controller |
| I.5: Patient physical interface and gas supply | R.I.6 | The mask or hood shall have a sealing mechanism to prevent the escape of exhaled air and fluids (to prevent contamination). | Not applicable to controller |
| I.5: Patient physical interface and gas supply | R.I.7 | The hood/mask and all gas supply pipes shall be made from medically approved materials. | Not applicable to controller |
| I.5: Patient physical interface and gas supply | R.I.8 | The device shall be usable with the patient in seated or lying down positions. | Not applicable to controller |
| I.5: Patient physical interface and gas supply | R.I.9 | The hood/mask shall have an anti-asphyxiation mechanism to allow for additional ambient air to enter the mask in case the inhalation gas volume exceeds the gas supply volume. | |
| I.7 Power | R.I.10 | The NVS shall connect to standard 240V, 50 Hz South African wall power socket. Only required if power interface is used. | |
| I.7 Power | R.I.11 | If the NVS function is dependent on electrical power, it shall automatically provide backup power for a period of 30 minutes or longer in case the main power supply fails. | |
| I.7 Compressed air | R.I.12 | The NVS compressed air inlet shall connect to a standard South African hospital wall compressed air supply point. Only required if compressed air interface is used. | Not applicable to controller |

## NVS functional requirements

| Function | ID | Requirement | Applicability |
| -------- | -- | ----------- | ------------- |
| Filter inlet air | R.F.1 | The NVS shall filter the ambient air inlet to a suitable breathing air standard. | Not applicable to controller |
| Add oxygen | R.F.2 | The NVS shall enable the operator to control the inspired oxygen proportion (FiO<sub>2</sub>) of the gas supplied to the patient to a value from 30% to 100% as set by the operator, either in 10% increment steps, or on a continuous scale, with an accuracy of +-5%. | |
| Regulate pressure | R.F.3 | The NVS shall maintain a constant minimum positive airway pressure at all times during the breathing cycle, as set by the operator. | |
| Regulate pressure | R.F.4 | The NVS shall enable the operator to regulate minimum positive airway pressure to a value from 5 to 25 cmH<sub>2</sub>O above ambient air pressure. | |
| Monitor pressure | R.F.5 | The NVS shall display the achieved airway pressure. | |
| Control ventilation | R.F.7 | The operator shall be able to turn the patient gas supply on and off (for fitting the device and taking it off). | |
| Prevent overpressure | R.F.8 | The NVS shall have a mechanism to ensure that the patient airway is never exposed to a gas pressure of more than 40cmH<sub>2</sub>O. | |
| Pressure loss alarm | R.F.9 | The NVS should have an alarm if there is a failure of the pressurised gas supply to the mask/hood. Note that this is not a mandatory requirement, but would be an advantage. | |


## NVS non-functional requirements

| Category | ID | Requirement | Applicability |
| -------- | -- | ----------- | ------------- |
| Electromagnetic compatibility | R.O.1 | The NVS shall comply with IEC 60601-1-2 or equivalent EMC standard. Only applicable if electronic components are used. | |
| Sanitation | R.O.2 | All external surfaces must be able to be sanitised, without damage to the device. Cleaning would be by healthcare workers manually wiping using an approved surface wipe with disinfectant or cloths and approved surface cleaning liquid. | |
| Labelling | R.O.3 | The NVS shall provide clear permanent labelling for all external interfaces. | |
| Labelling | R.O.4 | The NVS shall provide clear permanent labelling for all monitor and control points. | |
| Ergonomics | R.O.5 | The NVS shall be floor standing and mounted on a wheel base that is easy to move, and bed mountable to standard hospital bed configuration. | |
| Ergonomics | R.O.6 | The NVS shall be easy and intuitive to use and should require minimum training. | |
| Ergonomics | R.O.7 | The NVS shall provide controls and monitoring in a location that is convenient for the operator to use. | |
| Ergonomics | R.O.8 | The NVS controls shall be placed in such a way that they are not adjusted inadvertently. | |
| Ergonomics | R.O.9 | The NVS shall provide gas connection points locations that are convenient to connect and disconnect. | |
| Ergonomics | R.O.14 | The NVS system shall be delivered with operating and maintenance instructions. | |
| Reliability | R.O.10 | The NVS shall operate without failure or need for maintenance for a period of 14 days. | |
| Maintainability | R.O.11 | Following a block of 14 days, the NVS shall be maintained to allow returning to service within 1 hour. | |
| Maintainability | R.O.12 | Consumable spares (o-rings, seals, washers, filters) shall be provided with the NVS to allow a 1 hour turnaround time and a total of 10 blocks of use. | |
| Maintainability | R.O.15 | The NVS shall be delivered with operating and maintenance instructions. | |
| Manufacturability | R.O.13 | The NVS shall be manufactured using parts and materials that are readily available in large quantities on the commercial market or can be manufactured locally in South Africa. | |


