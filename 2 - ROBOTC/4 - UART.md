# 2.4 - UART Communication

UART communication allows the Cortex to communicate with other devices using a wired serial connection. Most commonly, this is used with the IR Sensor to broadcast and receive hexadecimal codes.

The UART ports are configured with the motor and sensor setup wizard under the serial port tab. The UART port must be set to "User Program".

Using the IR sensor requires a baud rate of 600. However, RobotC only supports 1.2k at the lowest. To communicate with the IR kit, a workaround must be used. In the wizard, set the baud rate to the lowest possible value.

The following code is used to add a custom baud function to RobotC:

```C
typedef unsigned long  uint32_t;
typedef unsigned short uint16_t;

typedef struct
{
  uint16_t SR;
  uint16_t RESERVED0;
  uint16_t DR;
  uint16_t RESERVED1;
  uint16_t BRR;
  uint16_t RESERVED2;
  uint16_t CR1;
  uint16_t RESERVED3;
  uint16_t CR2;
  uint16_t RESERVED4;
  uint16_t CR3;
  uint16_t RESERVED5;
  uint16_t GTPR;
  uint16_t RESERVED6;
} USART_TypeDef;

#define PERIPH_BASE           ((unsigned long)0x40000000)
#define APB1PERIPH_BASE       PERIPH_BASE
#define USART2_BASE           (APB1PERIPH_BASE + 0x4400)
#define USART3_BASE           (APB1PERIPH_BASE + 0x4800)
#define USART2                ((USART_TypeDef *) USART2_BASE)
#define USART3                ((USART_TypeDef *) USART3_BASE)

void setBaud( const TUARTs nPort, int baudRate ) {
    uint32_t tmpreg = 0x00, apbclock = 0x00;
    uint32_t integerdivider = 0x00;
    uint32_t fractionaldivider = 0x00;

    apbclock = 36000000;

    integerdivider = ((0x19 * apbclock) / (0x04 * (baudRate)));
    tmpreg = (integerdivider / 0x64) << 0x04;

    fractionaldivider = integerdivider - (0x64 * (tmpreg >> 0x04));
    tmpreg |= ((((fractionaldivider * 0x10) + 0x32) / 0x64)) & 0x0F;

    USART_TypeDef *uart = USART2;
    if( nPort == UART2 ) {
      uart = USART3;
    }
    uart->BRR = (uint16_t)tmpreg;
}
```

In the main function, the function is used like so:

```C
setBaud(UART1, 600);
```

Regular UART commands like those below are used to communicate with the device:

```C
/*
 sendChar is used to send data over a communications port.
 UART1 is the port that is used on the Cortex.
 0x55 is the hexadecimal code that is sent.
*/
sendChar(UART1, 0x55);
```

For more code examples using UART communication, see the [Made2Order repository](https://github.com/crcsrobotics/2022-made2order/blob/main/main.c).

[Up Next (2.5) ->](https://github.com/crcsrobotics/wiki/blob/main/2%20-%20ROBOTC/5%20-%20DEBUGGING.md)