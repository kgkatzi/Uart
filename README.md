## Overview

This code implements a UART (Universal Asynchronous Receiver-Transmitter) communication system in Verilog. The system consists of a transmitter (`uart_transmitter`), a receiver (`uart_receiver`), a baud rate controller (`baud_controller`), and other supporting modules like `counter`, `anodoi`, `LEDdecoder`, `encoder`, and `decoder`.

## Modules

### `baud_controller`

- **Inputs:**
  - `clk`: Clock input.
  - `reset`: Reset signal.
  - `baud_select`: 3-bit input to select the baud rate.

- **Outputs:**
  - `sample_ENABLE`: Output signal enabling sample transmission.

### `uart_transmitter`

- **Inputs:**
  - `clk`: Clock input.
  - `reset`: Reset signal.
  - `Tx_DATA`: 8-bit data to be transmitted.
  - `baud_select`: 3-bit input to select the baud rate.
  - `TX_EN`: Transmission enable signal.
  - `Tx_WR`: Write signal.

- **Outputs:**
  - `TxD`: Transmitted data line.
  - `Tx_BUSY`: Transmission busy signal.

### `uart_receiver`

- **Inputs:**
  - `reset`: Reset signal.
  - `clk`: Clock input.
  - `baud_select`: 3-bit input to select the baud rate.
  - `RX_EN`: Receiver enable signal.
  - `RxD`: Received data line.

- **Outputs:**
  - `Rx_DATA`: Received 8-bit data.
  - `Rx_FERROR`: Frame error signal.
  - `Rx_PERROR`: Parity error signal.
  - `Rx_VALID`: Received data validity signal.
  - `LEDS`: 16-bit signal for LED display.

### `counter`

- **Inputs:**
  - `clk`: Clock input.
  - `reset`: Reset signal.
  - `Rx_EN`: Receiver enable signal.

- **Outputs:**
  - `count`: 4-bit counter value.

### `anodoi`

- **Inputs:**
  - `counter`: 4-bit counter value.

- **Outputs:**
  - `anodos3`, `anodos2`, `anodos1`, `anodos0`: Output signals for anodes.
  - `load`: Load signal.

### `LEDdecoder`

- **Inputs:**
  - `char`: 4-bit input for character display.
  - `load`: Load signal.

- **Outputs:**
  - `LED`: 8-bit output for LED display.

### `encoder` and `decoder`

These modules perform Gray code encoding and decoding, respectively.

## How to Use

1. Instantiate the modules in your top-level module, connecting the inputs and outputs as required.
2. Set appropriate values for configuration parameters and initial conditions.
3. Ensure proper connections between modules.
4. Simulate or synthesize the design using your preferred Verilog simulation or synthesis tool.

## Notes

- The baud rates are selected using the `baud_select` signal.
- Parity error, frame error, and LED display features are included in the receiver module.
- Adjust clock frequencies, reset conditions, and other parameters as needed for your specific hardware.
