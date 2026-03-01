# Arduino I2C Data Collection Project

## Project Description
This project interfaces multiple I2C modules using an ESP32.  
The system performs:

- I2C device scanning
- RTC (Real Time Clock) functionality
- LCD display output
- Data collection from connected I2C modules

## Hardware Used
- ESP32
- RTC Module (DS3231)
- I2C LCD Display
- Other I2C modules detected via scanner

## Files Included
- I2C_Scanner_ESP32.ino – Scans and detects connected I2C devices
- RTC_LCD_Functionality.ino – Handles RTC timekeeping and LCD output

## How It Works
1. The I2C scanner detects connected modules and verifies communication.
2. The RTC module keeps track of real-time data.
3. The LCD displays time and system information.
4. Data is collected and can be expanded for logging applications.

## Author
Shiela May Catipa 
BSCA- BCA189 
Prof. Sir Jom
03-01-26
