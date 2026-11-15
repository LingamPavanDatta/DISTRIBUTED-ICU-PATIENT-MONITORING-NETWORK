# DISTRIBUTED-ICU-PATIENT-MONITORING-SYSTEM
An LPC2129-based distributed ICU patient monitoring system that monitors temperature, SpO₂, and light intensity, and enables real-time sensor data communication between two nodes using CAN protocol.

## Project Overview

An LPC2129-based distributed ICU patient monitoring system designed to monitor patient parameters such as temperature, SpO₂ (blood oxygen saturation), and light intensity. The system uses two LPC2129-based nodes, where the transmitter collects sensor data and transfers it to the receiver through CAN (Controller Area Network) communication for monitoring.

## Features

- Patient SpO₂ monitoring using the MAX30102 sensor.
- Temperature measurement using an ADC input.
- Light intensity measurement using an ADC input.
- CAN-based communication between transmitter and receiver nodes.
- UART communication for displaying sensor readings.
- I2C communication for interfacing with the MAX30102 sensor.

## Hardware Components

- LPC2129 Microcontroller (Transmitter Node)
- LPC2129 Microcontroller (Receiver Node)
- MAX30102 Pulse Oximeter Sensor
- Temperature Sensor
- Light Dependent Resistor (LDR)
- CAN Transceiver Modules
- Supporting electronic components

## Software and Technologies

- Embedded C
- Keil µVision IDE
- Flash Magic
- CAN Protocol
- UART Communication
- I2C Communication
- ADC (Analog-to-Digital Conversion)

## System Architecture

The project consists of two main nodes:

### 1. Transmitter Node

- Initializes the MAX30102 sensor through I2C communication.
- Reads RED and IR sensor values from the MAX30102.
- Processes the sensor data to calculate SpO₂.
- Reads temperature and light intensity values through ADC channels.
- Packs the collected sensor values into a CAN data frame.
- Transmits the data to the receiver node using CAN communication.

### 2. Receiver Node

- Receives sensor data from the transmitter through CAN communication.
- Extracts temperature, light intensity, and SpO₂ values from the received CAN data.
- Displays the received patient monitoring information through UART communication.

## Communication Protocols

| Protocol | Purpose |
|---|---|
| CAN | Communication between transmitter and receiver |
| I2C | MAX30102 sensor interfacing |
| UART | Serial data monitoring |
| ADC | Reading analog sensor inputs |

## Project Folder Structure

```text
DISTRIBUTED-ICU-PATIENT-MONITORING-SYSTEM/
│
├── ICU_Transmitter/
│   ├── main_tx.c
│   ├── uart0_driver.c
│   ├── adc_driver.c
│   ├── can1_tx_driver.c
│   ├── i2c_driver_tx.c
│   ├── max_init.c
│   ├── max30102.h
│   ├── spo2.c
│   ├── spo2.h
│   ├── delay.c
│   └── header.h
│
├── ICU_Receiver/
│   ├── main_rx.c
│   ├── uart0_driver.c
│   ├── can1_rx_driver.c
│   └── head.h
│
└── README.md
```

## Working Principle

The transmitter node collects patient-related sensor data using the MAX30102 sensor and ADC inputs. The SpO₂ value is calculated from the RED and IR readings. The temperature, light intensity, and SpO₂ values are packed into a CAN data frame and transmitted to the receiver node.

The receiver node extracts the received values and displays the monitoring information through UART serial communication.

## Applications

- ICU patient monitoring systems
- Distributed healthcare monitoring
- Embedded medical monitoring applications
- Real-time sensor data communication

## Project Objective

To develop a distributed embedded monitoring system that collects patient-related parameters and transfers sensor information between two microcontroller nodes using CAN communication.
