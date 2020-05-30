# STM32 library for SHT3x Temperture and Humidity sensor

## Usage
- Create instance of Sht3x.
  - set HAL I2C Handler(type: I2C_HandleTypeDef) as arg.
```cpp
Sht3x(I2C_HandleTypeDef hi2cx):
```
- Get observation data
```cpp
float temp, humid;
GetTempeatureHumiditySingleShot(&temp, &humid);
printf("temp: %3.2f, humid: %3.2f\r\n", temp, humid);
```

## Method List
```cpp
# Constructor
Sht3x(I2C_HandleTypeDef hi2cx):

# Public
void GetTempeatureHumiditySingleShot(float *temp, float *humid);

# Private
float calculateTempeature(uint8_t msb, uint8_t lsb);
float calculateHumidity(uint8_t msb, uint8_t lsb);
```
