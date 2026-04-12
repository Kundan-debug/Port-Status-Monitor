# Port-Status-Monitor
Course: Computer Networks - SDN_Mininet Project

Author:
- Kundan V - PES1UG24CS243

## Project Overview
This project implements an SDN-based port status monitoring system using the Ryu controller and Mininet network emulator. The objective is to monitor network link conditions in real time by detecting port status changes (UP/DOWN) in an OpenFlow-enabled switch. The system leverages the event-driven architecture of Software Defined Networking (SDN), where the controller continuously listens for port status events and logs them as informational messages or alerts. This enables dynamic visibility into network behavior and helps in identifying link failures instantly.

The project uses a simple topology consisting of two hosts connected to a single switch, managed by a remote Ryu controller. Through Mininet, network conditions such as link failures are simulated, and the controller responds by generating logs indicating port state changes. Connectivity between hosts is validated using ping tests, demonstrating how link disruptions affect communication. Overall, the project showcases the practical implementation of SDN concepts such as controller-switch interaction, OpenFlow messaging, and real-time network monitoring in a controlled virtual environment.

## Problem Statement
Traditional networks do not provide real-time visibility of port status, making it difficult to detect link failures and monitor network conditions efficiently. Manual monitoring is time-consuming and prone to delays, which can affect network reliability and performance.

## Objective
To develop an SDN-based port status monitoring system using Ryu and Mininet that detects port UP/DOWN events, logs changes, generates alerts, and displays real-time network status through controller-switch interaction using OpenFlow.

## Features
- Real-time detection of port status changes (UP/DOWN)  
- Event-driven monitoring using Ryu controller  
- Logging of port state changes in the controller terminal  
- Alert generation for link failures and port disconnections  
- Dynamic simulation of network conditions using Mininet  
- Controller–switch interaction using OpenFlow protocol  
- Verification of network connectivity through host communication (ping)  
- Simple and scalable topology for easy testing and analysis

## System Architecture
<p align="center">
  <img src="Architecture/Architecture.png" width="50%">
</p>

