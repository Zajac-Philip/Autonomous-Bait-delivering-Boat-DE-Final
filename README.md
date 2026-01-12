# Autonomous-Bait-delivering-Boat-DE-Final
An autonomous boa thtat navigates itself 200 yards west using a GPS and compass before returning to shore. The aim of this project for the future is to replace expensive bait drones.
## What it does

The boat gets its starting position, then selects a point 200 yards west before automatically navigating there using a compass for steering. After reaching its target position, it waits 5 seconds before returning to drop the bait. The motors use PWM to steer the boat when its current heading exceeds 20 degrees from the bearing to the target location.

## Parts Required:

- Raspberry Pi 4
- GY-271 Compass (QMC5883L magnetometer)
- GPS Module (NEO-6M)
- L298N Motor Driver
- 2x 380 Motors with propellers
- 7.4V 2S LiPo Battery
- Adjustable power supply (for testing)
- Wires
- Step Down voltage controller (LM2596 Buck Converter)

## Wiring Map

![wiring map (1)](https://github.com/user-attachments/assets/db13910b-30c6-4062-9a0c-e2a558e5f1d8)

## Required things to enable on the Pi:
- I2C must be enabled
- This library must be installed: python3-rpi.gpio python3-smbus i2c-tools

## Running Process:

First, you must calibrate the compass by running the compass calibration code. By spinning the boat in a full circle, the magnetometer takes the difference between the highest and lowest values for the X and Y direction and halves them to find the offset values. These values must be put into the code for the mission navigation so that it takes proper headings.

### Mission
The boat performs the following after starting:
- Waits for the GPS to lock then logs the home position
- Calculates the taget position 200 yards west
- Navigates to the target
- Waits 5 seconds during the bait release
- Returns to home location
## How the steering works:
After finding the target position, the distance and bearing to target are calculated using current position and bearing values. Every 0.1 seconds, the boat compares its current heading with the bearing to the target. If the difference between the two exceed 20 degrees, it turns by slowing the port outboard motor to turn left and the starboard outboard motor to turn right. When within the 20 degree range, both motors operate at full speed.

##Future Improvements:
- safety features that automatically make the boat return to the starting position during events like water entering the waterproof electronics box, or low battery.
- servo system to automatically drop the bait at the target location
- LED status indicators

## Current project state:
Currently, I have finished making an extremely rough skeleton with all of my electrical components except for the independent battery.

<img width="375" height="666" alt="IMG_3532-removebg-preview" src="https://github.com/user-attachments/assets/7672d836-4e12-4f47-9f94-2902e3a97885" />

<img width="375" height="666" alt="IMG_3533-removebg-preview" src="https://github.com/user-attachments/assets/cdccaa98-b3bc-4713-9791-59032a02aeac" />

I modeled a boat hull that is to be printed in 2 parts and fiberglassed over to waterproof and strengthen it. Both compartments contain a lower compartment which will have the bottom filled with sand so that the center of mass remains below the center of buoyancy, keeping the boat stable in the water

<img width="783" height="558" alt="Screenshot 2025-12-12 223926" src="https://github.com/user-attachments/assets/29c8d48e-7a5e-4c47-978e-c5e379d4efb3" />

<img width="617" height="362" alt="Screenshot 2025-12-12 223949" src="https://github.com/user-attachments/assets/689cdefb-972a-4b9b-bfee-1d82e33ab29c" />

Fully assembled, the hull will look like this:

<img width="840" height="588" alt="Screenshot 2025-12-02 180522" src="https://github.com/user-attachments/assets/e3bbd6b4-f58a-42be-9810-53848d85ff71" />
<img width="614" height="792" alt="Screenshot 2025-12-02 180910" src="https://github.com/user-attachments/assets/b69d7230-cefc-480b-8b8e-608a69d23280" />

