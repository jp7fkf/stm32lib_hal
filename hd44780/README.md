# STM32 library for HD44780 Liquid Crystal Display

## Usage
- Create instance of Hd44780.
  - Prepare DATA GPIO Port list and Pin list(4bits or 8bits)
  - Make Instance through constructor
```cpp
// The index of array corresponds each Port/Pin
GPIO_TypeDef* dataPorts[] = {GPIOA, GPIOB, GPIOB, GPIOB};
uint16_t dataPins[] = {GPIO_PIN_15, GPIO_PIN_3, GPIO_PIN_4, GPIO_PIN_5};

Hd44780 lcd(LCD_4BITMODE,         // Mode
            GPIOA, GPIO_PIN_6,    // RS
            GPIOA, GPIO_PIN_7,    // RW
            GPIOB, GPIO_PIN_0,    // Enable
            dataPorts, dataPins); // Data
```
- Initialize HD44780
```cpp
lcd.Init();
```
- Put chars
```cpp
lcd.Puts("Hello!");
```

## Method List
```cpp
// Constructor
Hd44780(uint8_t mode, GPIO_TypeDef* rsPort, uint16_t rsPin,
    GPIO_TypeDef* rwPort,uint16_t rwPin,
    GPIO_TypeDef* enablePort, uint16_t enablePin,
    GPIO_TypeDef** dataPorts, uint16_t* dataPins):
      mode_(mode),
      rsPort_(rsPort),
      rsPin_(rsPin),
      rwPort_(rwPort),
      rwPin_(rwPin),
      enablePort_(enablePort),
      enablePin_(enablePin),
      dataPorts_(dataPorts),
      dataPins_(dataPins){
}

// Public
void Init();
void SendData(uint8_t data);
void SendCommand(uint8_t command);
void Puts(char* string);
void SetCursor(uint8_t x, uint8_t y);
void Clear();
void Home();
```
