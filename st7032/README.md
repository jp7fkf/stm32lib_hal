# STM32 library for ST7032 LCD

## Usage
- Create instance of St7032.
  - set HAL I2C Handler(type: I2C_HandleTypeDef) as arg.
```cpp
St7032 lcd1(hi2c1);
```
- Initialize ST7032 LCD
```cpp
lcd1.Init();
```
- Put chars
```cpp
lcd1.Puts("Hello!");
```

## Method List
```cpp
St7032(I2C_HandleTypeDef hi2cx);
void Init();
void Puts(const char *p);
void Clear();
void Home();
void Display();
void NoDisplay();
void SetCursor(uint8_t line, uint8_t pos);
void Cursor();
void NoCursor();
void Blink();
void NoBlink();
void SetContrast(int val);
void AdjustContrast(int val);
uint8_t GetContrast();
virtual size_t Write(uint8_t chr);
void WriteInstruction(uint8_t cmd);
void WriteData(uint8_t data);
```
