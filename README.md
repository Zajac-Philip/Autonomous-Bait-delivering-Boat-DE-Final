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
I2C must be enabled
The following library must be installed:
python3-rpi.gpio python3-smbus i2c-tools

## Running Process:

First, you must calibrate the compass by running the compass calibration code. By spinning the boat in a full circle, the magnetometer takes the difference between the highest and lowest values for the X and Y direction and halves them to find the offset values. These values must be put into the code for the mission navigation so that it takes proper headings.

### Mission
