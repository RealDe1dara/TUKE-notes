# Lecture 2: Things

> **IoT | Things, controllers, sensors, actuators, and control systems**  
> Source: [IoT course lecture 02](https://kurzy.kpi.fei.tuke.sk/iot1/lectures/02/)

## 1. What is a thing in IoT?

The previous lecture introduced IoT and its architectures. The project
architecture used in this course is a three-layer architecture called
**Smart Department**.

An IoT system is a system of interrelated computing devices, mechanical and
digital machines, objects, animals, or people that have unique identifiers and
can transfer data over a network without requiring human-to-human or
human-to-computer interaction.

In this lecture, a **thing** means a physical object or device. It may be a
computing, mechanical, or digital device, but it must have the components
needed to interact with its environment and communicate.

An IoT thing generally:

- has a physical representation;
- has a unique identity;
- has a programmable control unit;
- contains sensors and actuators;
- can communicate with other things or higher layers such as a gateway, edge
  system, or cloud.

## 2. The Sense–Think–Connect–Act cycle

![Sense–Think–Act cycle](../../assets/IoT/lecture-02/sense-think-act-cycle.png)

IoT devices are often described using variations of the robotic paradigm:

- **Sense** - collect information from the environment using sensors.
- **Think** or **Infer** - process the information and decide what it means.
- **Connect** - exchange data with other devices or higher layers.
- **Act** - affect the environment using actuators.

Some descriptions omit `Connect` or use `Sense–Infer–Act`, but communication is
especially important in IoT because it distinguishes connected things from
ordinary standalone devices.

## 3. Microcontrollers and microprocessors

The control unit is the programmable “brain” of an IoT thing. It is commonly
implemented with a **microcontroller**.

A **microcontroller** is an integrated circuit that contains a processor,
memory, and peripherals on one chip. It is inexpensive, compact, energy
efficient, and intended for a specific or limited set of tasks in devices such
as appliances, vehicles, sensors, and controllers.

### Microprocessor vs. microcontroller

| Microprocessor | Microcontroller |
| --- | --- |
| General-purpose processing device. | Specialised device, often described as a single-chip computer. |
| Usually provides the CPU for a computer. | Used in simple or single-purpose devices. |
| Requires external memory, I/O, timers, and other peripherals. | Includes RAM, ROM/flash, interfaces, timers, and peripherals on the chip. |
| More complex design. | Simpler design. |
| More expensive, often costing tens or hundreds of euros. | Inexpensive, often costing only a few euros. |
| Higher energy consumption, commonly tens of watts in a computer. | Low energy consumption, commonly in the range of a few watts or less. |
| Usually associated with the Von Neumann architecture. | Often associated with the Harvard architecture. |
| High clock speeds, commonly in GHz. | Lower clock speeds, commonly in MHz. |
| Example: the processor in a Raspberry Pi. | Examples: ATmega328P, ESP32, micro:bit, and RP2040. |

### Von Neumann architecture

![Von Neumann architecture](../../assets/IoT/lecture-02/von-neumann-architecture.png)
The **Von Neumann architecture**, proposed by John von Neumann in 1945, is
used by ordinary computers. Its main blocks are:
- **CPU (Central Processing Unit)**:
  - the arithmetic and logic unit performs arithmetic and logical operations;
  - the control unit coordinates the operation of the computer.
- **Memory** stores both the program and its data.
- **Input** receives information.
- **Output** produces results.

The program and data share the same memory and communication path. This makes
processing primarily sequential.

### Harvard architecture

![Harvard architecture](../../assets/IoT/lecture-02/harvard-architecture.png)
The **Harvard architecture** physically separates program memory from data
memory and uses separate buses for accessing them. This allows instructions and
data to be processed in parallel.

Important properties include:

- program instructions and data occupy different memory spaces;
- the two buses may have different widths;
- instructions and data can be accessed simultaneously;
- the address spaces are separate;
- a program cannot overwrite its own instructions as easily as in a shared
  memory design.

## 4. Popular development platforms

These platforms are useful for prototyping IoT things:

- **Raspberry Pi** - a small general-purpose computer with Wi-Fi, Bluetooth,
  BLE, and Ethernet. It needs continuous power, does not normally provide
  microcontroller-style sleep modes, and is therefore not the best choice for
  low-power interrupt-driven devices.
- **Arduino Uno** - a popular prototyping board available since 2005. It has
  32 kB of flash memory for the program and 2 kB of SRAM for variables.
- **BBC micro:bit** - an inexpensive educational board with many integrated
  components and Bluetooth Low Energy. Version 1 supports Bluetooth 4.1 and
  version 2 supports Bluetooth 5.0.
- **ESP32 boards** - microcontroller boards with Wi-Fi and Bluetooth Low
  Energy. Different versions have different layouts and commonly provide 30 or
  38 pins.
- **Raspberry Pi Pico WH** - a Raspberry Pi microcontroller board built around
  the RP2040. The course uses the Pico family and MicroPython for building
  things.

### Example board comparison

| Property | Arduino Uno | ESP32 | BBC micro:bit | Raspberry Pi Pico WH |
| --- | --- | --- | --- | --- |
| Microcontroller | ATmega328P | ESP32 | nRF52833 | RP2040 |
| Processor | - | Tensilica Xtensa LX6 | ARM Cortex-M0 | ARM Cortex-M0+ |
| Architecture | 8-bit | 32-bit | 32-bit | 32-bit |
| Cores | 1 | 2 | 1 | 2 |
| Frequency | 16 MHz | 240 MHz | 16 MHz | 133 MHz |
| SRAM | 2 kB | 520 kB | 16 kB | 264 kB |
| Flash | 32 kB | 16 MB | 256 kB | 2 MB |
| Operating voltage | 5 V | 3.3 V | 3.3 V | 3.3 V |
| Communication | - | Wi-Fi, BLE | BLE | Wi-Fi, BLE 5.2 |
| Typical current | 60 mA | 55 mA | 17 mA | 18 mA |

## 5. Sensors, actuators, and communication

### Sensors

A **sensor** converts a physical quantity into an electrical signal and then
into a numeric value that the device can process. Examples include sensors for:

- light intensity;
- temperature;
- humidity;
- distance;
- motion;
- fill level.

### Actuators

An **actuator** converts electrical energy into a physical effect. Examples
include:

- an LED;
- a motor;
- a valve;
- a heating element;
- an alarm or display.

### Communication

Communication is what makes a thing an IoT thing rather than an isolated
device. A thing may communicate with other things or with higher layers such as
an IoT gateway, edge system, or cloud.

The communication technology and protocol should be selected according to the
environment, range, power constraints, amount of data, and required reliability.
The course covers particular protocols in later lectures.

## 6. Designing an IoT thing for a smart waste bin

The course project is a smart waste-collection service. Each container can
contain a thing that monitors its state and decides when an action is needed.
The design should satisfy the general properties of an IoT thing: physical
representation, unique identity, control unit, sensors, actuators, and
communication.

Possible components include:

- **Waste-level sensor** - an ultrasonic sensor can detect when a container is
  nearly full and prevent overflow.
- **Temperature and humidity sensor** - monitors conditions that can cause
  organic waste to rot, smell, or increase fire risk.
- **Flame sensor** - can detect a fire caused by a cigarette or deliberate
  ignition and trigger an early warning.
- **Opening sensor** - records usage and can trigger actions such as measuring
  the fill level after the lid is closed.
- **Communication module** - sends measurements to a database for processing.
  Its choice depends on the container's environment.
- **Soil-moisture sensor** - useful for a compost container to monitor the
  composting process.
- **Location system** - GPS, QR codes, NFC, or another method may be useful
  depending on whether containers are static or frequently moved.
- **Status actuators** - an LED, display, or sound can show that the device is
  measuring or transmitting. These components increase energy consumption.
- **Power source** - a battery or alternative source such as solar cells may be
  necessary because a container may not have a permanent power connection.

## 7. Additional design considerations

### Size

IoT devices are often small and may belong to the category of **wearable
electronics**. A prototype can be large, but the size of the final product
still needs to be considered from the beginning.

### KISS

**KISS** means “Keep it simple, stupid” or “Keep it stupid simple.” Systems
usually work better when they are simple. This applies to the hardware,
physical design, and software.

Unnecessary complexity increases cost, energy use, maintenance effort, and the
number of possible failure points. Simplicity is not a lack of sophistication;
it is a deliberate design goal.

### Things as state machines

The behaviour of most devices can be described with a **state diagram**. Such
devices are therefore **finite-state machines** or **state machines**.

A state machine helps development by dividing a complex problem into smaller
states and transitions. Its basic notation contains only:

- **states** - the modes in which the device can operate;
- **transitions** - the events or conditions that move the device between
  states.

States and transitions can be enriched with entry actions, exit actions,
conditions, and other information. The software State design pattern can be
used to implement this model.

## 8. Open-loop and closed-loop control systems

Control systems can be explained using an automatic irrigation system.

### Open-loop control

An **open-loop system** transforms a desired value into a command without
measuring the actual result.

![Open-loop control system block diagram](../../assets/IoT/lecture-02/open-loop-block-diagram.png)

Its main blocks are:

- **desired value** - the target, for example 35% soil moisture;
- **controller** - decides what command to send without knowing the actual
  output, for example a timer that opens a valve at 05:00 for 15 minutes;
- **actuator** - converts the command into a physical action, such as a valve;
- **system/process** - the part of the world being controlled, such as a
  football field;
- **output** - the value actually produced, such as the resulting soil
  moisture.

An open-loop irrigation system may water for a fixed time or use a fixed amount
of water, but it does not know whether the target moisture was reached. It
also cannot react to disturbances such as rain, sun, or wind.

![Open-loop control system with disturbances](../../assets/IoT/lecture-02/open-loop-with-disturbances.png)

For the irrigation example, the open-loop controller, valve, and field are
shown together here:

![Open-loop irrigation system](../../assets/IoT/lecture-02/open-loop-irrigation.png)

Open-loop systems:

- do not measure the output;
- do not react to disturbances;
- are simple, inexpensive, and have fewer components that can fail.

They are suitable when conditions are stable or an inaccurate result is
acceptable, such as a fixed washing-machine program, toaster, or simple light
timer.

### Closed-loop control

A **closed-loop system** adds feedback so that it can react to the actual
output:

![Closed-loop control system block diagram](../../assets/IoT/lecture-02/closed-loop-block-diagram.png)

1. A **sensor** measures the real output, such as soil moisture.
2. A **comparison element** compares the desired value with the measured value.
3. A **controller/regulator** uses the difference to decide what to do.

The difference between the desired value \(w\) and measured output \(y\) is
the **control error** \(e\):

\[
e = w - y
\]

For irrigation:

- \(e > 0\): the soil is too dry, so irrigation should be switched on;
- \(e < 0\): the soil is wetter than desired, so irrigation should be switched
  off;
- \(e = 0\): the desired moisture has been reached.

Closed-loop systems:

- measure the output and act according to the actual state;
- react to disturbances by correcting their effects;
- are more complex and expensive because they need sensors and processing;
- can make incorrect decisions if a sensor fails or provides inaccurate data.

![Closed-loop irrigation system](../../assets/IoT/lecture-02/closed-loop-irrigation.png)

Examples include thermostats, refrigerators, car cruise control, and
sensor-based irrigation.

### Delay and overshoot

The effect of an action often does not appear immediately. This is called
**delay** or **dead time**. In irrigation, water needs time to reach the
sensor in the root zone.

If the controller ignores the delay, the sensor continues to report dry soil
after irrigation has started. The system keeps watering and eventually exceeds
the target. This is called **overshoot**.

A practical solution is to water in batches, for example for five minutes,
wait for the water to soak into the soil, and then measure again.

### Hysteresis

If a controller switches at exactly one target value, a measurement that
fluctuates slightly around that value can cause rapid on/off switching. This
wears the actuator and can make the system unstable.

**Hysteresis** uses two thresholds instead:

- switch irrigation on below the **lower threshold**, for example 30%;
- switch irrigation off above the **upper threshold**, for example 35%;
- keep the current actuator state between the two thresholds.

Without hysteresis, small measurement changes around the target can repeatedly
switch the actuator:

![Irrigation control without hysteresis](../../assets/IoT/lecture-02/irrigation-without-hysteresis.png)

With hysteresis, the lower and upper thresholds create a stable range:

![Irrigation control with hysteresis](../../assets/IoT/lecture-02/irrigation-with-hysteresis.png)

The gap between the thresholds prevents unnecessary switching. The measured
value may continue rising briefly after irrigation is turned off because of
the system's delay.

## Exam checklist

- Define an IoT thing and list its essential properties.
- Explain the Sense–Think–Connect–Act cycle.
- Distinguish a microprocessor, microcontroller, and microcomputer.
- Compare Von Neumann and Harvard architectures.
- Explain why Raspberry Pi is different from a low-power microcontroller board.
- Compare Arduino Uno, ESP32, BBC micro:bit, and Raspberry Pi Pico WH.
- Distinguish sensors, actuators, and communication modules.
- Propose components for a smart waste-bin IoT thing.
- Explain the KISS principle and model a device as a finite-state machine.
- Compare open-loop and closed-loop control.
- Explain feedback, control error, delay, overshoot, and hysteresis.

### Key takeaway

An IoT thing is a physical, identifiable, programmable, communicating device
that senses its environment and can act on it. Good IoT design combines the
right controller, sensors, actuators, communication, power source, and simple
state-based behaviour. When the result must remain correct despite changing
conditions, feedback turns an open-loop process into a closed-loop control
system.
