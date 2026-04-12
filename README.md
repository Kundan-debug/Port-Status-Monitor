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

The system follows an SDN architecture where the data plane (switch) and control plane (Ryu Controller) are separated. Mininet is used to emulate the network with hosts (h1, h2) connected to a switch.

The switch communicates with the Ryu Controller using the OpenFlow protocol. Whenever a packet arrives and no matching rule is found, the switch sends it to the controller. The controller processes the packet, makes forwarding decisions, and installs flow rules in the switch.

Additionally, the switch sends port status events to the controller whenever a link goes UP or DOWN. The controller logs these changes and generates alerts, enabling real-time monitoring and efficient network management.

Host → Switch → Controller → Decision → Switch

## Working of Ryu Controller and SDN Logic
The controller follows an event-driven model, meaning it reacts to network events instead of continuously polling the network. Whenever a packet arrives at the switch and no matching flow rule exists, the switch sends a packet_in message to the Ryu Controller. The controller then decides how to handle the packet and installs appropriate flow rules in the switch.

The controller also listens for EventOFPPPortStatus events to detect changes in port states. When a port becomes active (UP), it logs the event as an informational message (INFO). When a port goes down (DOWN), it generates an alert (ALERT), helping in real-time network monitoring and debugging.

By default, the controller implements a flooding mechanism when it does not know the destination, forwarding packets to all ports except the incoming one. Once the correct path is learned, flow rules are installed so that future packets are forwarded directly without involving the controller, improving efficiency.

## Installation and Setup
Commands:

source ryu-env310/bin/activate  
ryu-manager controller/port_monitor.py  
sudo mn --custom topology/topo.py --topo mytopo --controller remote
