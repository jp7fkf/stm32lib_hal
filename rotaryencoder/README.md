# STM32 library for General Rotary Encoder

## Usage
- Pre-Processing
  - set A Phase of Rotary Encoder Port as EXTI.
    - Rising Edge interrupt is as default.
    - if you use Falling Edge Interrupt, set inverse true.
  - set B Phase GPIO Port/Pin of Rotary Encoder as GPUO Input.
  - Each Encoder port must be pulled up.
    - external pullup or stm32 internal pullup can be selected.
    - both of them seems to be worked.
- Create instance of RotaryEncoder
  - set GPIO Input Port/Pin assigned as B Phase of Rotary Encoder.
```cpp
RotalyEncoder renc(GPIOA, GPIO_PIN_3);
```
- Get Direction
```cpp
# inside of EXTI function(A Phase)
printf("dir: %d\r\n", renc.GetDirection(false));
// if cw, return 1. if ccw, return -1. (when inverse is false)
```
- Get incremental value
  - 1st arg is base value.
  - 2nd arg is rate.
    - rate can be set as minus value.
      - it means same as inverse.
  - return 1st arg + rate;
```cpp
int value =0;

# inside of EXTI function(A Phase)
value = renc.GetIncrementedValue(value, 10);
printf("value: %d\r\n", value);
// when CW rotation, value increase by 10.
// 0 -> 10 -> 20 -> 30... each interrupt.
```

## Method List
```cpp
// Constructor
RotaryEncoder(GPIO_TypeDef* bPhasePort, uint16_t bPhasePin);
// Public
int8_t GetDirection(bool inverse);
int GetIncrementedValue(int value, int rate);
