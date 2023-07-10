# Sensirion I²C SFX6XXX Arduino Library

This is the Sensirion SFX6XXX library for Arduino allowing you to 
communicate with a sensor of the SFX6XXX family over I²C.

<img src="images/product-image-sfx6xxx.png" width="300px">

Click [here](https://sensirion.com/sfc6000) to learn more about the Sensirion SFX6XXX sensor family.



## Supported sensor types

| Sensor name   | I²C Addresses  |
| ------------- | -------------- |
|[SFC6000](https://sensirion.com/products/catalog/SFC6000/)| **0x24**, 0x23, 0x22, 0x21, 0x20, 0x42, 0x41|
|[SFC6000D-5SLM](https://sensirion.com/products/catalog/SFC6000D-5slm/)| ****|
|[SFC6000D-50SLM](https://sensirion.com/products/catalog/SFC6000D-50slm/)| ****|
|[SFC6000D-20SLM](https://sensirion.com/products/catalog/SFC6000D-20slm/)| ****|
|[SFM6000](https://sensirion.com/products/catalog/SFM6000)| **0x24**, 0x23, 0x22, 0x21, 0x20, 0x42, 0x41|
|[SFM6000D-20SLM](https://sensirion.com/products/catalog/SFM6000D-20slm)| ****|
|[SFM6000D-50SLM](https://sensirion.com/products/catalog/SFM6000D-50slm)| ****|
|[SFM6000D-5SLM](https://sensirion.com/products/catalog/SFM6000D-5slm)| ****|

The following instructions and examples use a *SFC6000*.



## Installation of the library

This library can be installed using the Arduino Library manager:
Start the [Arduino IDE](http://www.arduino.cc/en/main/software) and open
the Library Manager via

`Sketch` ➔ `Include Library` ➔ `Manage Libraries...`

Search for the `Sensirion I2C SFX6XXX` library in the `Filter
your search...` field and install it by clicking the `install` button.

If you cannot find it in the library manager, download the latest release as .zip file 
and add it to your [Arduino IDE](http://www.arduino.cc/en/main/software) via

`Sketch` ➔ `Include Library` ➔ `Add .ZIP Library...`

Don't forget to **install the dependencies** listed below the same way via library 
manager or `Add .ZIP Library`

#### Dependencies
* [Sensirion Core](https://github.com/Sensirion/arduino-core)

## Sensor wiring

Use the following pin description to connect your SFX6XXX to the standard I²C bus of your Arduino board:

<img src="images/product-pinout-i2c-sfx6xxx.png" width="300px">

| *Pin* | *Cable Color* | *Name* | *Description*  | *Comments* |
|-------|---------------|:------:|----------------|------------|
| 1 | red | VDD | Supply Voltage | +24V
| 2 | black | GND | Ground | 
| 3 |  | NC | Do not connect | 
| 4 | yellow | SCL | I2C: Serial clock input | 
| 5 | purple | ADDR |  | Leave floating for default i2c address 0x24
| 6 | green | SDA | I2C: Serial data input / output | 




The recommended voltage is 24V.

### Board specific wiring
You will find pinout schematics for recommended board models below:



<details><summary>Arduino Uno</summary>
<p>

| *SFX6XXX* | *SFX6XXX Pin* | *Cable Color* | *Board Pin* |
| :---: | --- | --- | --- |
| VDD | 1 | red | None |
| GND | 2 | black | GND |
| SCL | 4 | yellow | D19/SCL |
| ADDR | 5 | purple |  |
| SDA | 6 | green | D18/SDA |



<img src="images/Arduino-Uno-Rev3-i2c-pinout.png" width="600px">
</p>
</details>



<details><summary>Arduino Nano</summary>
<p>

| *SFX6XXX* | *SFX6XXX Pin* | *Cable Color* | *Board Pin* |
| :---: | --- | --- | --- |
| VDD | 1 | red | None |
| GND | 2 | black | GND |
| SCL | 4 | yellow | A5 |
| ADDR | 5 | purple |  |
| SDA | 6 | green | A4 |



<img src="images/Arduino-Nano-i2c-pinout.png" width="600px">
</p>
</details>



<details><summary>Arduino Micro</summary>
<p>

| *SFX6XXX* | *SFX6XXX Pin* | *Cable Color* | *Board Pin* |
| :---: | --- | --- | --- |
| VDD | 1 | red | None |
| GND | 2 | black | GND |
| SCL | 4 | yellow | ~D3/SCL |
| ADDR | 5 | purple |  |
| SDA | 6 | green | D2/SDA |



<img src="images/Arduino-Micro-i2c-pinout.png" width="600px">
</p>
</details>



<details><summary>Arduino Mega 2560</summary>
<p>

| *SFX6XXX* | *SFX6XXX Pin* | *Cable Color* | *Board Pin* |
| :---: | --- | --- | --- |
| VDD | 1 | red | None |
| GND | 2 | black | GND |
| SCL | 4 | yellow | D21/SCL |
| ADDR | 5 | purple |  |
| SDA | 6 | green | D20/SDA |



<img src="images/Arduino-Mega-2560-Rev3-i2c-pinout.png" width="600px">
</p>
</details>



<details><summary>ESP32 DevKitC</summary>
<p>

| *SFX6XXX* | *SFX6XXX Pin* | *Cable Color* | *Board Pin* |
| :---: | --- | --- | --- |
| VDD | 1 | red | None |
| GND | 2 | black | GND |
| SCL | 4 | yellow | GPIO 22 |
| ADDR | 5 | purple |  |
| SDA | 6 | green | GPIO 21 |



<img src="images/esp32-devkitc-i2c-pinout.png" width="600px">
</p>
</details>


## Quick Start

1. Install the libraries and dependencies according to [Installation of the library](#installation-of-the-library)

2. Connect the SFX6XXX sensor to your Arduino as explained in [Sensor wiring](#sensor-wiring)

3. Open the `exampleUsage` sample project within the Arduino IDE:

   `File` ➔ `Examples` ➔ `Sensirion I2C SFX6XXX` ➔ `exampleUsage`

  
   The provided example is working with a SFC6000, I²C address 0x24.
   In order to use the code with another product or I²C address you need to change it in the code of `exampleUsage`. 
   You find the list with pre-defined addresses in `src/SensirionI2CSfx6xxx.h`.


5. Click the `Upload` button in the Arduino IDE or `Sketch` ➔ `Upload`

4. When the upload process has finished, open the `Serial Monitor` or `Serial
   Plotter` via the `Tools` menu to observe the measurement values. Note that
   the `Baud Rate` in the used tool has to be set to `115200 baud`.

## Contributing

**Contributions are welcome!**

We develop and test this driver using our company internal tools (version
control, continuous integration, code review etc.) and automatically
synchronize the master branch with GitHub. But this doesn't mean that we don't
respond to issues or don't accept pull requests on GitHub. In fact, you're very
welcome to open issues or create pull requests :)

This Sensirion library uses
[`clang-format`](https://releases.llvm.org/download.html) to standardize the
formatting of all our `.cpp` and `.h` files. Make sure your contributions are
formatted accordingly:

The `-i` flag will apply the format changes to the files listed.

```bash
clang-format -i src/*.cpp src/*.h
```

Note that differences from this formatting will result in a failed build until
they are fixed.


## License

See [LICENSE](LICENSE).
