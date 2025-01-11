# ESP32-CAM & BME280/680 & Home Assistant & ESPHome integration
Using **ESP32-CAM** (AI-Thinker) with Bosch Sensors **[BME280](https://www.bosch-sensortec.com/products/environmental-sensors/humidity-sensors-bme280/)/[BME680](https://www.bosch-sensortec.com/products/environmental-sensors/gas-sensors/bme680/)** via I2C and its integration into **[Home Assistant](https://www.home-assistant.io/) via [Esphome](https://esphome.io/)**. With some small modifications you can use this code also for other boards e.g. ESP01/ESP12/... which I already tried as well. Focus here is **NOT** to show how to do flashing via esptool, just to share YAML configuration file used for flashing of microcontroller by esptool to save your time in development phase.

*Note:* **[BME280](https://www.bosch-sensortec.com/products/environmental-sensors/humidity-sensors-bme280/)** is a temperature sensor. **[BME680](https://www.bosch-sensortec.com/products/environmental-sensors/gas-sensors/bme680/)** has additionally a gas sensor.

# Intro

I was personally struggling to find out comprehensive tutorial, how to integrate ESP32-CAM together with any kind of Bosch sensor via I2C. **The main motivation had been to use just one microcontroller (in this case ESP32-CAM) for everything - camera & temperature/gas sensor.** 

# Wiring

Here pinout of **ESP32-CAM**. The **GPIO** names are important to set **[I2C](https://en.wikipedia.org/wiki/I%C2%B2C)** correctly. To this point we will come again when we write the code.

Image source: [RandomNerdTutorials.com](https://randomnerdtutorials.com/esp32-cam-ai-thinker-pinout/)

![obrazek](https://user-images.githubusercontent.com/85900069/157596660-dc251f8d-3c2d-40e0-96c1-7e147c1d8ea9.png)

Here my complete wiring:

![obrazek](https://user-images.githubusercontent.com/85900069/157727827-8f59f96f-6bf1-460e-8eb3-5d39d69d8707.png)

[Here](https://github.com/zbj3ji/esp32-cam_bme_280_bme680_esphome/blob/fe0fee8bdba7bd56e71f226a9bce32e7e605f066/Sketch_BME280_ESP32-CAM.fzz) you find a sketch made in Fritzing.

**Be careful: BME280/680 are sensor with supply power 3.3V!** **ESP-CAM works with both 3.3/5V, but for better stability I recommend to use 5V**.

# Code

[Here](cam_livingroom_bme280.yaml) complete YAML file for **ESP32-CAM & BME280**.

Based on the ESP32 (or other microcontroller) pinout, you have to define the right I2C pins. In my case I used GPIO13 as SDA and GPIO12 as scl (see wiring above). You can change it as you wish, but then you need to use the right pins. Another very important thing is to use correct **sensor address** - in my case **0x76**, other option is e.g. **0x77**.

[Here](https://esphome.io/components/esp32_camera.html) a default example from ESPHome web site about ESP32-CAM.

# Integration


This is an example, how it looks like in Home Assistant:

![obrazek](https://user-images.githubusercontent.com/85900069/157704845-a7803080-a321-4798-959b-7c81e6a83014.png)

# Images

| Wiring             |  Wiring |
:-------------------------:|:-------------------------:
![obrazek](https://user-images.githubusercontent.com/85900069/157709064-71d61f04-efb6-4ea1-9073-1f526c00dcc8.png) | ![obrazek](https://user-images.githubusercontent.com/85900069/157709102-d8f57a47-e469-4f89-9b7e-901a9eccf472.png)


