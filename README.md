# Wireshark-Packet-Analysis

## This project investigates fundamental networking technologies through practical packet analysis using Wireshark

## Project Description

This project investigates fundamental networking technologies through practical packet analysis using **Wireshark**.

The project focuses on generating and capturing real network traffic, examining protocol fields, analysing TCP/IP encapsulation, and investigating TCP sequence numbers, acknowledgement numbers, window sizes, and congestion behaviour.

The analysis applies a layered networking approach to understand how application-layer protocols such as HTTP operate over TCP/IP and how data is encapsulated as it moves through the networking layers.

---

## Purpose of the Project

The purpose of this project is to develop practical skills in analysing real internet packets and applying networking concepts to captured network traffic.

Rather than examining networking protocols only from a theoretical perspective, the project uses self-generated packet captures to investigate:

* HTTP communication.
* TCP connection establishment.
* Client and server port numbers.
* HTTP protocol versions.
* TCP/IP encapsulation.
* Packet header and payload sizes.
* TCP sequence and acknowledgement numbers.
* TCP window sizes.
* TCP congestion behaviour.

Wireshark is used as the primary tool for capturing, filtering, and analysing the network packets.

---

## Project Scope

The project is divided into three main areas of investigation.

### Task 1 – HTTP Traffic Analysis

HTTP traffic is generated and captured using a web browser and Wireshark.

The captured packets are analysed to identify the sequence of messages exchanged between the HTTP client and server.

The analysis covers:

* HTTP request and response messages.
* Transport protocol used by HTTP.
* TCP three-way handshake.
* Client and server port numbers.
* HTTP version.
* Relationship between TCP connection establishment and the subsequent HTTP communication.

The TCP handshake is examined by identifying the **SYN, SYN-ACK and ACK** packets and correlating them with the TCP connection used by the HTTP traffic.

---

## Task 2 – TCP/IP Encapsulation

TCP/IP traffic is captured and examined at different protocol layers.

The analysis investigates how application data is encapsulated as it passes through the TCP/IP model.

The captured packets are examined for:

* IP headers.
* TCP headers.
* Payload sizes.
* Total packet lengths.
* Relationships between headers, payloads and total packet size.
* Encapsulation between networking layers.

The project also considers the possibility of a Layer 2 trailer when analysing the complete frame.

The analysis demonstrates that each networking layer adds its own control information around the data received from the layer above.

---

## TCP Sequence, ACK Numbers and Congestion Control

The final task examines TCP reliability and flow/congestion-related behaviour using captured packets.

The analysis investigates:

* Raw TCP sequence numbers.
* Relative sequence numbers displayed by Wireshark.
* Acknowledgement numbers.
* TCP segment lengths.
* Expected acknowledgement numbers.
* Corresponding acknowledgement packets.
* TCP window size.
* Evidence of congestion or the absence of congestion.

The relationship between a packet's sequence number, segment length and expected acknowledgement number is examined using the captured trace.

---

## Key Networking Concepts

### HTTP over TCP

The captured HTTP traffic is analysed to determine the transport protocol used by HTTP and identify the TCP connection that carries the HTTP messages.

The TCP handshake is correlated with the HTTP session by examining the source and destination IP addresses and port numbers.

### TCP Three-Way Handshake

The connection establishment process is analysed using:

```text
Client                  Server
  |                       |
  | ---- SYN ----------> |
  | <--- SYN-ACK -------- |
  | ---- ACK ----------> |
  |                       |
  | ---- HTTP Request --> |
  | <--- HTTP Response -- |
```

The packet sequence demonstrates how TCP establishes a connection before application data is exchanged.

### Encapsulation

The project examines how data is encapsulated through the networking layers.

Conceptually:

```text
Application Data
       ↓
TCP Header + TCP Payload
       ↓
IP Header + IP Payload
       ↓
Layer 2 Frame
```

The captured packet fields are used to verify the relationship between headers, payloads and total lengths.

### Sequence and Acknowledgement Numbers

TCP sequence numbers are examined to understand how TCP tracks transmitted data.

The analysis compares Wireshark's displayed sequence numbers with the raw sequence numbers and investigates how the acknowledgement number is determined from the sequence number and amount of transmitted data.

### TCP Window and Congestion Behaviour

TCP window sizes and packet transmission behaviour are examined to determine whether the captured trace contains evidence of congestion.

The project also considers how sequence numbers and window sizes would be expected to behave when congestion affects TCP transmission.

---

## Testing and Validation

Testing was performed using self-generated network traffic rather than relying solely on pre-existing packet captures.

### HTTP Capture

The browser cache was cleared before generating HTTP traffic. Wireshark was then started before accessing an HTTP website.

The resulting capture was filtered and examined to identify the relevant HTTP and TCP packets.

### TCP Handshake Validation

The TCP handshake was validated by identifying:

```text
SYN
SYN-ACK
ACK
```

The source and destination addresses and ports were compared with the subsequent HTTP packets to establish that the handshake belonged to the HTTP connection being analysed.

### Encapsulation Validation

IP and TCP packets were inspected to identify their:

* Header sizes.
* Payload sizes.
* Total lengths.

These values were compared to verify the expected relationship:

```text
Total Length = Header Length + Payload Length
```

where applicable to the specific protocol layer being examined.

### TCP Sequence and ACK Validation

Specific TCP packets were selected from the captured trace.

Their sequence numbers, acknowledgement numbers and segment lengths were compared to determine the expected acknowledgement behaviour.

Corresponding acknowledgement packets were then identified where present.

### Congestion Analysis

The captured TCP traffic was reviewed for indicators of congestion, including changes in transmission behaviour and TCP window information.

The analysis determined whether the captured trace provided evidence of congestion and discussed the expected TCP behaviour if congestion had been present.

---

## Project Evolution

The project progressed from basic packet capture to detailed protocol analysis.

The first stage involved generating HTTP traffic and identifying the relationship between the HTTP application layer and the underlying TCP connection.

The second stage moved to packet structure and encapsulation, examining how TCP and IP headers are added to application data and how packet lengths change across the networking layers.

The final stage focused on TCP behaviour, including sequence numbers, acknowledgement numbers and window sizes. This allowed the project to move from simply identifying packets to analysing how TCP provides reliable data transmission and responds to network conditions.

---

## Outcome

The project provided practical experience in analysing real network packets using Wireshark.

The completed analysis demonstrated the ability to:

* Capture HTTP traffic.
* Identify HTTP requests and responses.
* Identify TCP transport connections.
* Recognise TCP three-way handshakes.
* Identify client and server ports.
* Determine HTTP protocol versions from captured packets.
* Analyse TCP/IP headers and payloads.
* Verify packet length relationships.
* Explain network encapsulation.
* Analyse TCP sequence numbers.
* Determine acknowledgement relationships.
* Examine TCP window sizes.
* Evaluate captured traffic for potential congestion.

The project also strengthened the connection between theoretical networking models and observable network behaviour.

---

## Conclusion

This project demonstrates how Wireshark can be used to investigate networking protocols at the packet level.

The HTTP analysis showed how an application-layer protocol operates over a TCP connection and how the TCP handshake establishes communication before application data is exchanged.

The encapsulation analysis demonstrated how protocol headers are added as data moves through the TCP/IP networking layers. The TCP analysis then examined how sequence numbers, acknowledgement numbers and window sizes support reliable communication and provide information about network behaviour.

Overall, the project provided practical evidence of how layered networking protocols operate together and how packet captures can be used to analyse and evaluate real network communication.

