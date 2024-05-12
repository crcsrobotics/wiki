# 3.2 - IR Sensor Wiring

The IR sensor wiring diagrams are available in the [IR kit wiring PDF.](https://github.com/crcsrobotics/2023-IncisionDecision/blob/main/ir-kit-wiring.pdf) The full documentation for the IR sensor can be found [on the BEST Robotics website.](https://www.bestrobotics.org/IR_Kit/)

This page serves as a quick comparison of the wiring methods described in the PDF linked above.

## 3.2.1 - Using a Single Cortex Digital I/O Port

Using a single I/O port for the IR sensor allows for the fewest number of port to be used and is designed for basic "line break" applications like line following. This was used in 2023's "Incision Decision" for line following.

**Pros:**

- Easiest to wire
- Minimal port usage
- Device can be read easily like a sensor in RobotC (see `2.3`)

**Cons:**

- No control over what is output

## 3.2.2 - Using Separate Cortex Digital I/O Ports

Using separate I/O ports allows for basic control over output and easy sensor reading. It is designed for "line break" applications and simple signalling. It may also be used for UART communication, however, this is difficult and there are better solutions.

**Pros:**

- Easy to wire
- Device can be read easily like a sensor in RobotC (see `2.3`)
- Basic control over output

**Cons:**

- UART/hexadecimal code output is difficult
- Uses two ports

## 3.2.3 - Using a Cortex UART port (Transmit/Receive Only)

Using a Cortex UART port for transmitting or receiving only allows for precise control over output (transmit only) or advanced input (receive only). It is ideal for sending **OR** receiving hexadecimal codes, but not both. This was used in 2022's "Made 2 Order" for transmitting codes to another robot.

**Pros:**

- Easier than transmitting and receiving
- Can be used with hexadecimal commands like `sendChar` in RobotC for communication

**Cons:**

- Difficult wiring
- Cannot both send and receive

## 3.2.4 - Using a Cortex UART port (Transmit & Receive)

Using a Cortex UART port for transmitting and allows for precise control over output and input. It is ideal for sending **AND** receiving hexadecimal codes.

**Pros:**

- Can both transmit and receive in hexadecimal
- Can be used with hexadecimal commands like `sendChar` in RobotC for communication

**Cons:**

- Most difficult wiring
- Usually unnecessary
