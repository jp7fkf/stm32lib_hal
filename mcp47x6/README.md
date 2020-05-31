# STM32 library for mcp47x6 D-A Converter

## Usage
- Create instance of Mcp47x6.
  - set HAL I2C Handler(type: I2C_HandleTypeDef) as arg.
```cpp
Mcp47x6 dac(hi2c1);
```
- Set DAC Output value
```cpp
void SetDacOut(uint16_t val);
```

## Method List
```cpp
// Constructor
Mcp47x6(I2C_HandleTypeDef hi2cx):

// Public
void SetDacOut(uint16_t val);
```
