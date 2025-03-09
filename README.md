# SPI Modules

## Overview
This project implements an **SPI (Serial Peripheral Interface)** communication system, consisting of an **SPI Master** and an **SPI Slave**. The modules are designed to facilitate serial data transfer between devices.

## Modules
### 1. SPI Master
The SPI Master module generates the clock signal, manages chip selection, and transmits data serially using a state machine.

### Inputs:
* `clk` - System clock
* `newd` - New data signal
* `rst` - Reset signal
* `din [11:0]` - 12-bit input data

### Outputs:
* `sclk` - Serial clock signal
* `cs` - Chip select signal
* `mosi` - Master Out Slave In data line

## 2. SPI Slave
The SPI Slave module detects the start of transmission, receives data bit by bit, and signals when reception is complete.

### Inputs:
* `sclk` - Serial clock signal from master
* `cs` - Chip select signal
* `mosi` - Data line for receiving bits

### Outputs:
* `dout [11:0]` - 12-bit received data
* `done` - Signal indicating data reception completion

## 3. Top Module
The Top Module integrates the SPI Master and SPI Slave modules, facilitating communication between them.

### Inputs:
* `clk` - System clock
* `rst` - Reset signal
* `newd` - New data signal
* `din [11:0]` - Input data for SPI Master

### Outputs:
- `dout [11:0]` - Output data from SPI Slave
- `done` - Completion signal

## 4. SPI Interface
An interface file (`spi_if`) is included for easy testbench integration.

### Features
* **State Machine Based Communication** - Ensures structured and efficient data transmission.
* **12-bit Data Transfer** - Supports sending and receiving 12-bit data.
* **Clock Generation** - SPI Master generates an appropriate clock signal for the slave.

### Usage
1. Instantiate the `top` module in your design.
2. Provide input signals (`clk`, `rst`, `newd`, `din`).
3. Monitor `dout` and `done` for received data.

### Simulation & Testing
* The project can be tested using a **Verilog testbench**.
* The `spi_if` interface simplifies testbench development.

## Testbench
A testbench is included to validate the SPI communication.

### Testbench Features:
- Generates **clock and reset signals**.
- Sends test data from the SPI Master.
- Monitors received data from the SPI Slave.
- Asserts signals to verify proper functionality.

### Running the Testbench:
1. Use **[EDA Playground](https://www.edaplayground.com/)** for quick simulation.
2. Compile the testbench along with the SPI modules.
3. Run the simulation and observe the waveform to verify SPI transactions.
4. Check for expected data output and timing behavior.

### Future Enhancements
- Support for **multiple slaves** (SPI Multi-Slave).
- **Adjustable clock frequency** for SPI communication.
- **Full-duplex communication**.

## License
This project is licensed under MIT License

---

