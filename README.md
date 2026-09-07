# Synchronous FIFO Design and Verification using Verilog

## Overview

This project implements a **Synchronous FIFO (First-In, First-Out)** using Verilog HDL. A FIFO is a memory buffer used to store and retrieve data in the same order in which it was written.

A synchronous FIFO operates using a **common clock** for both read and write operations. It is commonly used for temporary data storage and for managing data flow between different parts of a digital system.

## FIFO Architecture

The design consists of a memory array along with separate **read and write pointers**.

- The **write pointer** keeps track of the location where the next data item will be stored.
- The **read pointer** keeps track of the location from which the next data item will be retrieved.
- Data is always read in the same order in which it was written.
- An additional pointer bit is used to distinguish between the **Full** and **Empty** conditions.

The FIFO is implemented as a **parameterized design**, allowing the FIFO depth and data width to be changed without modifying the core logic.

## Control and Status Signals

| Signal | Description |
|--------|-------------|
| `clk` | Common clock for FIFO operations |
| `rst_n` | Active-low reset |
| `cs` | Chip Select |
| `wr_en` | Enables write operation |
| `rd_en` | Enables read operation |
| `data_in` | Input data |
| `data_out` | Output data |
| `full` | Indicates that the FIFO is full |
| `empty` | Indicates that the FIFO is empty |

## Verification

A Verilog testbench is used to verify the functionality of the FIFO under different operating conditions.

The testbench covers:

1. **Basic Read/Write**  
   Verifies that data written into the FIFO can be read back in the correct order.

2. **Continuous Back-to-Back Operations**  
   Tests multiple consecutive write operations followed by read operations to verify sustained data transfer.

3. **Full and Empty Conditions**  
   Verifies that the `full` flag is asserted when the FIFO reaches its maximum capacity and the `empty` flag is asserted when all stored data has been read.

The simulation output and waveform are used to observe the FIFO control signals, data flow, and status flags.

## Files

```text
fifo.v       - Synchronous FIFO design
fifo_tb.v    - Verilog testbench

