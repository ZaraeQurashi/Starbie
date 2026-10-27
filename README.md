# Starbie 

Starbie is a custom star-shaped PCB that combines electronics, embedded programming, and a virtual pet into one project. Built around the **Seeed Studio XIAO ESP32-C3**, Starbie features a small OLED display, motion sensing, environmental sensors, and interactive buttons that let you care for a digital pet.

<img width="447" height="407" alt="image" src="https://github.com/user-attachments/assets/f05c3183-4ddc-4669-9255-60fb202bcd05" />


##  Features

-  **Custom star-shaped PCB** designed in KiCad
-  **Digital pet** displayed on a 128 × 64 OLED screen
-  **Interactive controls** using two physical buttons
-  **Motion detection** using an MPU6050 accelerometer and gyroscope
-  **Pet-care system** with feeding, playing, petting, and sleeping
-  **Pet statistics** for joy, energy, and fullness
-  **Temperature and humidity readings** using a DHT11 sensor

## Project Overview
Building Starbie meant designing the circuit, laying out and routing a PCB and finally editing the software to control
the hardware. 

I split the project into three main parts:
- Schematic design: Where I took all the components and connected them to each other using Kicad
- PCB Design: Where I turned the schematic into a physical board layout, routed traces and prepared the design
  for manufacturing using KiCad
- Code: Where I edited the program on Arduino and added personal touches to the base program.

### Schematic
The first stage of the project was creating the circuit schematic in KiCad. 

I started by setting up the required footprint and symbol libraries. Then I placed
the components into the schematic and connected them. 

The schematic shows how the XIAO ESP32-C3, OLED display, sensors, buttons, and other components are connected. 

![Starbie schematic](https://github.com/user-attachments/assets/8b46631c-d966-47de-a254-decbc8f90cf0)

### PCB Layout

Once the schematic was finalized, the next step was to convert it into a physical PCB layout. I imported
all the components into KiCad's PCB Editor and started arranging them on a custom, star shaped board I made
on the edge cuts layer.

After arranging the components, I routed the traces to connect the pads according to the schematic on both the F.CU
and B.CU layer. 

Finally, after the main layout was done, I added game artwork and my initials to the F.Silkscreen layer,
which printed the graphics onto the front of the board.

![Starbie PCB layout](https://github.com/user-attachments/assets/5307a7ad-fdbd-4574-a11b-9a30451945d2)

### Firmware and Digital Pet

For the code and firmware, I started with the existing base code and added a sparkle trail effect to make
the animations more interesting, along with adding my own custom bitmap pet. Then I adjusted the different 
variable values for the pet's health as well as adding the correct connections.

The firmware controls the display, pet interactions, motion sensing, and statistics.

![Starbie firmware and digital pet](https://github.com/user-attachments/assets/2725b172-63ad-4cc7-bb97-32b7d4c790d4)

##  Bill of Materials (BOM)

The following table lists the components used to build Starbie, including their suppliers and costs. All prices are in **CAD**.

| Component | Qty. | Supplier | Cost/Item | Total Cost |
|---|---:|---|---:|---:|
| [Seeed Studio Grove OLED Yellow & Blue Display 0.96" (SSD1315) V1.0](https://ca.robotshop.com/products/seeedstudio-grove-oled-yellow-blue-display-096-in-ssd1315-v10) | 1 | RobotShop | $7.86 | $7.86 |
| [6 DOF Gyro, Accelerometer IMU — MPU6050](https://ca.robotshop.com/products/6-dof-gyro-accelerometer-imu-mpu6050?variant=42411369627799) | 1 | RobotShop | $18.43 | $18.43 |
| [Cherry MX2A Red Keyswitch](https://ca.robotshop.com/products/cherry-mx2a-red-keyswitch) | 2 | RobotShop | $2.79 | $5.58 |
| [Seeed Studio XIAO ESP32-C3](https://ca.robotshop.com/products/seeedstudio-xiao-esp32c3-tiny-mcu-w-wi-fi-ble?variant=42740657782935) | 1 | RobotShop | $8.50 | $8.50 |
| [DHT11 Temperature & Humidity Sensor Module Breakout](https://ca.robotshop.com/products/dht11-temperature-humidity-sensor-module-breakout?variant=42412120277143) | 1 | RobotShop | $2.16 | $2.16 |
| [Custom PCB](https://cart.jlcpcb.com/quote?spm=jlcpcb.Public.2006) | 1 | JLCPCB | $15.53 | $15.53 |
| [10 kΩ Resistor](https://ca.robotshop.com/products/sparkfun-resistor-10k-ohm-pth-20-pack) | 1 | RobotShop | $1.36 | $1.36 |
| [Cherry MX Keycap — R2 (Opaque Black)](https://ca.robotshop.com/products/cherry-mx-keycap-r2-opaque-black) | 2 | RobotShop | $1.50 | $3.00 |
| **Estimated shipping** | — | — | — | **$21.97** |
| **Grand Total** | | | | **$84.39** |

**Total estimated cost: $84.39 CAD, including shipping.**


##  Controls

Starbie uses two physical buttons and motion input to interact with the digital pet.

| Input | Action |
|---|---|
| **Button 1** | Opens the radial menu |
| **Tilt the board** | Moves the menu selection |
| **Button 1 while the menu is open** | Confirms the selected action |
| **Button 2** | Toggles the statistics display |
| **Shake the board** | Increases joy by 5, decreases energy by 2, and decreases fullness by 1 |

### Radial Menu

The radial menu contains four actions for caring for the pet.

| Direction | Action | Joy Change | Energy Change | Fullness Change |
|---|---|---:|---:|---:|
| Up | **NAP** | +1 | +18 | -4 |
| Right | **PLAY** | +12 | -9 | -5 |
| Down | **FEED** | +3 | +2 | +18 |
| Left | **PET** | +7 | 0 | 0 |

The values represent the changes applied to the pet's statistics when each action is performed.

##  Hardware Connections

The firmware uses the following pin assignments for the XIAO ESP32-C3.

| Component | Signal | XIAO ESP32-C3 Pin |
|---|---|---|
| OLED display | SDA | D4 / GPIO6 |
| OLED display | SCL | D5 / GPIO7 |
| MPU6050 | SDA | D4 / GPIO6 |
| MPU6050 | SCL | D5 / GPIO7 |
| DHT11 sensor | Data | D1 / GPIO3 |
| Button 1 | Input | D2 / GPIO4 |
| Button 2 | Input | D3 / GPIO5 |

The OLED display uses the I²C address `0x3C`, while the MPU6050 uses the I²C address `0x68`.


##  Firmware

Starbie's firmware is written in **C++ for the Arduino environment**. It manages the display, reads sensor data, handles button input, and updates the digital pet's statistics.

### How It Works

- **Display:** The SSD1306 OLED displays the pet sprite, radial menu, and statistics.
- **Motion sensing:** The MPU6050's accelerometer detects board tilt to navigate the menu and shaking to trigger an interaction.
- **Pet interactions:** Feeding, playing, petting, and sleeping modify the pet's joy, energy, and fullness.
- **Statistics:** The pet's statistics are saved using the ESP32's Preferences functionality, allowing them to persist between restarts.
- **Environmental data:** The DHT11 provides temperature and humidity readings for the statistics display.

The firmware is configured for a **128 × 64 display** and uses a **32 × 32 pixel pet bitmap**.

### Required Libraries

Install the following libraries through the Arduino IDE Library Manager:

- `Adafruit GFX Library`
- `Adafruit SSD1306`
- `Adafruit MPU6050`
- `Adafruit Unified Sensor`
- `DHT sensor library`

The ESP32 board support package must also be installed and configured for the XIAO ESP32-C3.

### Uploading the Firmware

1. Install the Arduino IDE.
2. Install the ESP32 board support package and the libraries listed above.
3. Connect the XIAO ESP32-C3 to your computer.
4. Open the Starbie firmware `.ino` file.
5. Select the appropriate XIAO ESP32-C3 board and serial port.
6. Compile the sketch and resolve any errors.
7. Upload the firmware to the microcontroller.
8. Test the display, buttons, sensors, and pet interactions.

### Manufacturing Files

The repository includes the design files needed to inspect and continue editing the PCB.

| File | Purpose |
|---|---|
| `.kicad_sch` | Editable schematic |
| `.kicad_pcb` | Editable PCB layout |
| `.kicad_pro` | KiCad project settings |
| Gerber files | PCB fabrication layers |
| Drill files | Hole locations for manufacturing |
| Firmware `.ino` | Arduino firmware |
| `README.md` | Project documentation |

The Gerber and drill files can be uploaded to a PCB manufacturer to request a board. Review the generated fabrication files before placing an order.

---


