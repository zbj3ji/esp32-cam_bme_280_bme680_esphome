# ESP32-CAM & BME280/680 & Home Assistant & ESPHome integration
Using **ESP32-CAM** (AI-Thinker) with Bosch Sensors **[BME280](https://www.bosch-sensortec.com/products/environmental-sensors/humidity-sensors-bme280/)/[BME680](https://www.bosch-sensortec.com/products/environmental-sensors/gas-sensors/bme680/)** via I2C and its integration into **[Home Assistant](https://www.home-assistant.io/) via [Esphome](https://esphome.io/)**. With some small modifications you can use this code also for other boards e.g. ESP01/ESP12/... which I already tried as well. Focus here is **NOT** to show how to do flashing via esptool, just to share YAML configuration file to save your time in development phase.

*Note:* **[BME280](https://www.bosch-sensortec.com/products/environmental-sensors/humidity-sensors-bme280/)** is a temperature sensor. **[BME680](https://www.bosch-sensortec.com/products/environmental-sensors/gas-sensors/bme680/)** is a gas sensor.

# Intro

I was personally struggling to find out comprehensive tutorial, how to integrate ESP32-CAM together with any kind of Bosch sensor via I2C. The main motivation has been to use just one microcontroller (in this case ESP32-CAM) for everything - camera & temperature/gas sensor. 

# Wiring

Here in general pinout of **ESP32-CAM**. The **GPIO** names are important to set **[I2C](https://en.wikipedia.org/wiki/I%C2%B2C)** corrcetly. To this point we will come again when we write the code.

Image source: [RandomNerdTutorials.com](https://randomnerdtutorials.com/esp32-cam-ai-thinker-pinout/)

![obrazek](https://user-images.githubusercontent.com/85900069/157596660-dc251f8d-3c2d-40e0-96c1-7e147c1d8ea9.png)

Here my complete wiring:



**Be careful: BME280/680 are sensor with supply power 3.3V!** **ESP-CAM works with both 3.3/5V, but for better stability I recommend to use 5V**.

# Code

Here complete YAML file for ESP32-CAM & BME280.

Based on the ESP32 (or other microcontroller) pinout, you have to define the right I2C pins. In my case I used GPIO13 as SDA and GPIO12 as scl (see wiring above).

# Integration


This is an example, how it looks like in Home Assistant:

![obrazek](https://user-images.githubusercontent.com/85900069/157704845-a7803080-a321-4798-959b-7c81e6a83014.png)

# Image

