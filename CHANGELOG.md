# Changelog

## v.0.8.3

### Changes that break compatibility 

- ⚠ (bh1900nux, max31725, mcp23008, mcp23x17, mcp342x, mcp4725, pca9557, pcf8574, pcf8575, qmc5883l, sht3x, tca9548, tca95x5): The order of the arguments in `xxx_init_desc()` functions has been changed to bring all drivers to a common standard: instead of `xxx_init_desc(..., i2c_port_t port, uint8_t addr, ...)`, now `xxx_init_desc(..., uint8_t addr, i2c_port_t port, ...)`. Attention: both arguments are ints, so compiler will not throw an error when building your firmware without changing it!
- (common) Dropped support for ESP-IDF v3.x

### Features

- (common) Added support for ESP32-C3
- (hts221) Driver for HTS221 temperature and humidity sensor
- (hdc1000) Driver for HDC1000 temperature and humidity sensor
- (examples) Constant parameters in examples have been moved to Kconfig.projbuild files, so you can now setup examples by `idf.py menuconfig` or `make menuconfig` instead of modifying source code.
- (examples) Added README to all examples
- (hx711) Added function to read average data
- (bh1900nux) Added software reset function
- (ds3231) Added functions to set and get aging offset register
- (esp_idf_lib_helper): Moved ets_sys.h includes to the separate file

### Bugfixes

- (i2cdev) Showing error name in error logging
- (color) Fixed narrowing conversion error
- (examples) Use SPI2_HOST in examples with ESP-IDF v4.x
- (rda5807) Replaced `ESP_LOGI()` to `ESP_LOGD()`
- (led_strip_spi) Fixed pointer arithmetic for esp8266
- (led_strip_spi) Fixed "initialized field overwritten" warning
- (mcp960x) Fixed incorrect I2C addressing

### Documentation: https://esp-idf-lib.readthedocs.io/en/0.8.3/

## v.0.8.2

### Features

- (max31865) Driver for MAX31865 resistance converter for platinum RTDs
- (pca9557) Driver for PCA9537/PCA9557 remote 4/8-bit I/O expanders for I2C-bus
- (ls7366r) Driver for LS7366R Quadrature Encoder Counter
- (ci) Added metadata support
- (bh1900nux) Driver for BH1900NUX temperature sensor

### Bugfixes

- (scd30) Fixed type casting warning
- (ccs811) Fixed claculation bug in ccs811_set_environmental_data()
- (max7219) Fixed bug with chip number in 8x8 example
- (button) Added user context do descriptor
- (si7021) Fixed delay for SHT20
- (led_strip_spi) Added brightness support
- (pcf8563) Fixed mdays/wdays bug
- (sht4x) Fixed bug in example
- (led_strip) Fixed memory leak when handling error in led_strip_init()


## v.0.8.1

### Features

- (button) Driver for GPIO button with debouncing
- (scd30) Driver for SCD30 CO₂ sensor
- (scd4x) Driver for SCD40/SCD41 miniature CO₂ sensor
- (aht) Driver for AHT10/AHT15/AHT20 temperature and humidity sensor

### Bugfixes

- (mzh19b) Fixed bug with serial buffer length used by the driver
- (framebuffer) Used a mutex instead of flag, fixed "maybe-uninitialized"
- (sgp40) Multiple bugs fixed
- (sht4x) Added 10ms timout for reading serial number
- (rda5807m) Default I2C clock lowered, example added
- (color) Fix build with c++
- (examples) Fixed build of examples for single core ESP32s (S2/C3)
- (ds18x20) Added split 18B20/18S20 reads to allow for use of DS18X20_ANY
  without flubbing the conversion on an 18B20
- (ds18x20) Added scratchpad write and copy commands


## v.0.8.0

### Features

- (wiegand) Wiegand protocol receiver
- (lib8tion) Math functions specifically designed for LED programming (port
  from FastLED)
- (color) Common library for RGB and HSV colors (port from FastLED)
- (noise) Noise generation functions (port from FastLED)
- (framebuffer) RGB framebuffer and animation component
- (mhz19b) Added support for the MH-Z19B CO2 sensor
- (ci) Dropped support for ESP-IDF < v3.5
- (ci) Preliminary and untested support for ESP32-C3
- (ci) Support ESP8266 RTOS SDK v3.3
- (doc) Added initial version of CONTRIBUTING.md

### Bugfixes

- (sht3x) Fixed documentation
- (ds18x20) Fixed ds18x20_scan_devices(), new example
- (ultrasonic) Added more precise measurement functions
- (led_strip_spi) Fixed SPI buffer limitation for ESP8266
- (led_strip) Fixed buffer overflow error for RGBW strips
- (led_strip) White component for RGBW strips now calculated automatically
- (led_strip) Fixed bug in led_strip_set_pixels()
- (led_strip) Added support for global brightness for ESP-IDF >= v4.4
- (led_strip) Improved stability for WS2812B
- (refactoring) Updated component makefiles and CMakeLists
- (i2cdev) Added option to disable all mutexes


## v.0.7.3

### Features

- (led_strip_spi) #156 SPI-based driver for SK9822/APA102 LED strips
- (ds3502) #160 Driver for nonvolatile digital potentiometer DS3502
- (sht4x) #165 Driver for SHT4x temperature and humidity sensor

### Bugfixes

- (pca9685) b633f86 Speed-ups
- (max7219) #159 Add "minus" sign and fix maximum brightness


## v.0.7.2

### Features

- (tsl2591) #149 Driver for light-to-digital converter TSL2591
- (sgp40) #137 Driver for SGP40 Indoor Air Quality Sensor
- (ccs811) #67 Driver for AMS CCS811 digital gas sensor

### Bugfixes

- (ci) #147 Cache Espressif tools
- (ci) #155 Update v4.2 branch
- (led_strip) #153 Tweak led_strip example, add README
- (led_strip) #154 Fix range bug in led_strip_fill
- (sht3x, ...) #151 Typo corrections + SHT3x corrections and improvement
- (sht3x) #152 Fix periodic measurement
- (hx711) a2b9fc5 Fix incorrect spinlock usage
- (doc) Multiple fixes
- (pca9685) ce8f3fa Fix possible race condition


## v.0.7.1

### Features

- (mcp960x) #141 Driver + example for MCP960X/L0X/RL0X
- (tsys01) #142 Driver + example for TSYS01

### Bugfixes

- (qmc5883l) dd17522 Fix possible race condition
- (tca95x5) #144 Copy-paste error, add example
- (esp_idf_lib_helpers) #143 Invalid error message
- (tsl4531) c2e835d Fix possible race condition
- (sht3x) 8289262 Fix possible race confition in SS measurement, refactoring
- (bh1750, bmp180) d57488b Fix possible race condition


## v.0.7

### Features

- (ina260) #126 Driver for INA260 precision digital current and power monitor
- (rda5807m) #25 Driver for single-chip broadcast FM radio tuner RDA5807M
- (i2cdev) #138 I2C clock stertching support


## v.0.6.1

### Bugfixes

- (ina219) #100 Potential error in ina219_get_gain
- (bme680) #121 Pressure calculation for bme680 gives wrong results


## v.0.6

### Features

- (ci) #116 Port CI process from Travis CI to GitHub Actions
- (ci) Update CI build tools
- (ads111x) #117 Support of ADS101x on top ADS111x
- (led_strip) #120 Smart LED strips support

### Bugfixes

- (ds1307) #110 wrong squarewave frequency returned
- (sht3x, hmc5883l, hx711) #118 SHT3x measurements fail after 72min
- (pca9685) d4f5e35 Fix full on/off
- (ina219) Typo fix


## v.0.5-beta

### Features

- (mcp342x) #92 Driver for ADC MCP3426/MCP3427/MCP3428

### Bugfixes

- (ds1302) #97 Fix critical section exit
