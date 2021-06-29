# STM32 library for BMP180 Temperature and Pressure sensor

## Usage
- Create instance of Bmp180
  - set HAL I2C Handler(type: I2C_HandleTypeDef) as arg.
```cpp
Bmp180 bmp(&hi2c1);
```
- Connection Test(optional)
```cpp
while(!bmp.TestConnection());
```
- Initialize BMP180(Get calibration params)
```cpp
bmp.Init();
```
- Get observation data
```cpp
temperture_c = bmp.GetTemperatureCelsius();
pressure = bmp.GetPressure(3);
```

## Method List
```cpp
// Constructor
Bmp180(I2C_HandleTypeDef *hi2cx);

// Public
void     Init();
bool     TestConnection();
void     LoadCalibrationParams();
uint8_t  GetRegister(uint8_t reg);
float    GetTemperatureCelsius();
float    GetTemperatureFahrenheit();
float    GetPressure(uint8_t oss);
float    CalcAltitude(float pressure, float seaLevelPressure);

// Private
int16_t  getAC1();
int16_t  getAC2();
int16_t  getAC3();
uint16_t getAC4();
uint16_t getAC5();
uint16_t getAC6();
int16_t  getB1();
int16_t  getB2();
int16_t  getMB();
int16_t  getMC();
int16_t  getMD();
uint8_t  getMeasureDelayMilliseconds();
uint16_t getMeasureDelayMicroseconds();
void     setRegister(uint8_t reg, uint8_t val);
void     setMode(uint8_t mode);
uint16_t getRawTemperature();
uint32_t getRawPressure();
```
