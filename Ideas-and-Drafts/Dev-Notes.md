# Datasheet mockup, Design rules, Workflow Ideas

- Split the system into Power input, Analog scaling, MCU, Front-end, and Housing subsystems for better work isolation and modularity
- Power should be taken from a wall outlet via a 3 pin plug
- Analog scaling uses a summing opamp circuit to scale voltages from ±12v to MCU readable voltage (0 to 3.3v)
- The MCU must be powered by the Power subsystem not usb
- MCU must continuously send scaled voltage values as 12 or 14 bit values at high frequency (min 40kHz, ideally upto 1MHz) via the usb to the laptop
- Comms must happen via a USB port to the laptop. No wifi or bluetooth
- The frontend subsystem takes the stream of voltage readings and displays them according to users' requirements. This includes frequency scaling, pausing, noting down points on the curve etc.

---

## 1. Power

### Abstract and Description:
To power the subsystem that performs input signal voltage scaling (±12V to MCU rated voltage), stable, noiseless ±15V rails are required. This subsystem draws power from a standard wall socket and converts the power to the required specifications.

### Function
1. Draws power from a wall socket (230VAC 50Hz, 5A)
2. Steps it down
3. Rectifies and filters it
4. Regulates it to the required voltage (±15V, GND)

### Constraints
1. High efficiency (>60%)
2. Stable ±15v lines

(Need to define the following)
### Electrical Specifications
### Operating Parameters
### Mechanical Details
### Block Diagram
### Schematic
### Performance Graphs

---

## 2. Analog

### Abstract and Description
The subsystem that communicates with the laptop to visualise the signal needs the signal to be availabe in MCU readable range (0, 3.3v). The input signals may be as high as ±12v. To achieve this, a precise scaling circuit is required. This subsystem consists of a summing op amp circuit which scales and biases the input signal to the requred range

### Function
1. Takes a ±12v input signal
2. Scales it down to ±1.67v signal
3. Biases this ±1.67v signal with +1.67v to achieve a 0 to 3.3v range signal
4. Sends this scaled, biased signal to the MCU

### Constraints
1. Summing inverter + inverter setup
2. Dual channel support (or use two sets of single channel)

(Need to define the following)
### Electrical Specifications
### Operating Parameters
### Mechanical Details
### Block Diagram
### Schematic
### Performance Graphs

---

## 3. MCU

### Abstract and Description
The subsystem that displays the signal to the user requires a fast stream of signal values. This subsystem takes the scaled, biased input, converts it to into a digital signal and transfers this signal data to the laptop

### Functions
1. Convert the analog signal into a digital signal through an ADC (external or inbuilt)
2. Transfer the data via USB

### Constraints
1. High Clock frequency
2. High Sampling rate
3. 12-14 bit adc (min.)
4. High speed usb support (dk if this is a thing or if it depends on the clock rate)
5. Do not need bluetooth, wifi, LCD etc

(Need to define the following)
### Electrical Specifications
### Operating Parameters
### Mechanical Details
### Block Diagram
### Schematic
### Performance Graphs

---

## 4. Web-App

### Abstract and Description
The user needs to have a smooth and rich experience while using the scope. For this, a Single Page Web Application is required. This subsystem receives the digital signal data and provides an interface to interact with the output signal wave on the screen

### Function
1. Receive digital signal through USB (WebSerial)
2. Store this data in two register banks, one for pausing while the other keeps polling the data
3. Read the users' commands via the UI which include on/off state, pause/play state, frequency scale amplitude scale, ypos of each channel etc
4. Process the data according to the requirements and display on the screen (Plotting)
5. Provide the users with instructions on how to use the tool

### Constraints
1. Intuitive design
2. USB data input
3. Math functions support
4. Help button

(Need to define the following)
### Features and Components
### Protocols used
### Display Specs
### Tech Stack
### Block Diagram
### File Structure
### Future Features

---

## 5. Housing

### Abstract and Description
The scope hardware needs to be compact and portable to fit the use case. This subsystem is designed to keep all the components closely stacked while providing ventilation, easy access to ports and a form factor that allows for easy handling.

### Components
- 3 pin plug and cable
- Probes (Ch1, Ch2, GND)
- USB Cable
- Main Housing
  - Casing with appropriate ports
  - Fans for ventilation
  - On Off switch
  - On status LED indicator

### Constraints
- **Dimensions:** l x w x h (in mm)
- **Weight:** under 250gms
- **Ports:** AC 3 pin, Bullet connectors for signal probes, USB
- **Assembly:** Snap fit or screws
- **Ventilation:** 12v fan to push hot air out, vent holes to let cool air in
- **Material:** Light, rigid plastic
- **Power Switch**
- **On/Off state LED**

(need to define the following)
### Material
### Manufacturing Process
### Assembly Considerations
### Labelling and Compliance
