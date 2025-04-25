# Datasheet mockup, Design rules, Workflow Ideas

- Split the system into Power input, Analog scaling, MCU, Comms, Front-end subsystems for better work isolation and modularity
- Power should be taken from a wall outlet via a 3 pin plug
- Analog scaling uses a summing opamp circuit to scale voltages from ±12v to MCU readable voltage (0 to 3.3v)
- The MCU must be powered by the Power subsystem not usb
- MCU must continuously send scaled voltage values as 12 or 14 bit values at high frequency (min 40kHz, ideally upto 1MHz) via the usb to the laptop
- Comms must happen via a USB port to the laptop. No wifi or bluetooth
- The frontend subsystem takes the stream of voltage readings and displays them according to users' requirements. This includes frequency scaling, pausing, noting down points on the curve etc.

---

## 1. Power

### Abstract and Description:
To power the subsystem that performs inout signal voltage scaling (±12V to MCU rated voltage), a stable, noiseless ±15V rails are required. This subsystem draws power from a standard wall socket and converts the power to the required specifications.

### Function:
1. Draws power from a wall socket (230VAC 50Hz, 5A)
2. Steps it down
3. Rectifies and filters it
4. Regulates it to the required voltage (±15V, GND)

### Electrical Specifications

### Operating Parameters

### Mechanical Details

### Block Diagram

### Schematic

### Performance Graphs

---

## 2. Analog

### Abstract and Description
The oscilloscope needs to be able to measure signals from +12v to -12V. For this, a 
---

## 3. MCU

### Abstract and Description
