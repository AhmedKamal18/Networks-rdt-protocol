# RTD v2.2 Readme

## Overview
RTD v2.2 is a transport layer protocol that implements a stop-and-wait pattern, supports packet corruption handling using checksum, and operates as an alternating-bit protocol. The protocol provides reliable data transfer between two communicating entities over an unreliable channel.

## Features
1. **Stop-and-Wait Pattern**: RTD v2.2 utilizes a stop-and-wait pattern, where the sender transmits a single packet and waits for an acknowledgment from the receiver before sending the next packet. This ensures reliable delivery and simplifies flow control.

2. **Packet Corruption Handling**: The protocol incorporates checksum-based packet corruption handling. The sender calculates the checksum by obtaining the ASCII code of each character in the packet and includes it in the packet. The receiver verifies the integrity of the received packet by recalculating the checksum and comparing it with the checksum received. If a corruption is detected, appropriate actions are taken.

3. **Alternating-Bit Protocol**: RTD v2.2 operates as an alternating-bit protocol. The sender assigns a unique sequence number (alternating bit) to each packet it sends. The receiver acknowledges the correct receipt of packets by sending acknowledgments (ACKs) with the expected sequence number. If the receiver receives a corrupted packet, it sends an ACK with the next expected sequence number, effectively requesting retransmission.

## Usage

### Sender
To use the RTD v2.2 protocol as a sender, follow these steps:

1. Establish a connection with the receiver using the underlying network layer.
2. Prepare the data to be sent and divide it into packets.
3. Assign a unique sequence number (alternating bit) to each packet.
4. Calculate the checksum for each packet by obtaining the ASCII code of each character in the packet.
5. Include the checksum in each packet.
6. Send a packet to the receiver.
7. Wait for an acknowledgment (ACK) from the receiver.
8. If an ACK is received with the expected sequence number, proceed to the next packet.
9. If an ACK is received with the unexpected sequence number, assume the previous packet was corrupted and retransmit it.
10. Repeat steps 6-9 until all packets are successfully transmitted and acknowledged.
11. Close the connection with the receiver.

### Receiver
To use the RTD v2.2 protocol as a receiver, follow these steps:

1. Establish a connection with the sender using the underlying network layer.
2. Wait for a packet from the sender.
3. Verify the integrity of the received packet by recalculating the checksum and comparing it with the checksum received.
4. If the packet is corrupted, send an acknowledgment (ACK) to the sender with the next expected sequence number.
5. If the packet is error-free, send an acknowledgment (ACK) to the sender with the expected sequence number.
6. Pass the valid data from the packet to the higher layers.
7. Wait for the next packet and repeat steps 3-6 until all packets are received.
8. Close the connection with the sender.

## Dependencies
The RTD v2.2 protocol implementation may have dependencies on the following:

- Underlying network layer for establishing and managing connections.
- Data structures for storing packet information, sequence numbers, and acknowledgments.

## Examples
Examples of RTD v2.2 protocol implementations can be found in the following directories:

- `examples/sender`: Contains an example implementation of the sender side.
- `examples/receiver`: Contains an example implementation of the receiver side.

Please refer to the code and accompanying documentation in these directories for further details on how to use the protocol.

## Acknowledgments
The RTD v2.2 protocol implementation was inspired by various reliable transport protocols and research papers. We would like to acknowledge the contributions of the researchers and developers in the field of networking and protocols.
