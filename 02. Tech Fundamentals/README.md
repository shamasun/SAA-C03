## 2.0 Technical Fundamentals

### 2.1 YAML (YAML ain't Markup Language) 101
#### 2.1.1 Introduction
- Human readable data serialization language
- Unordered collection of key-value pairs. Key-values separated by colon.
- Supported values = numbers, floating point, boolean, and null
- Indentation matters. Use spaces. Denotes structure.
- Commonly used for storing configuration.
- Values can also be a
    - list
    - dictionary
    - list of dictionaries
    - dictionary with list values
- CloudFormation templates are written in YAML
#### 2.1.2 Elements of a list can be written
- in-line within square brackets
- as sub-bullets below the key, using hyphen as the bullet
#### 2.1.3 Example of an employee record[^1]
```
name: Bharathan
job: Developer
skill: Elite
employed: True
foods:
 - Apple
 - Orange
 - Strawberry
 - Mango
languages:
 perl: Elite
 python: Elite
 pascal: Lame
```
[^1]: [Ansible](https://docs.ansible.com/ansible/latest/reference_appendices/YAMLSyntax.html?raw=true)

### 2.2 JSON (JavaScript Object Notation) 101
- Object = Unordered set of key-value pairs enclosed in { }
- Array = collection of elements in [ ], separated by commas.
- Values = string, object ( $\therefore{}$ nested), number, array, true, false, null
- In AWS used for CloudFormation and Policy documents
- Forgiving. No indentation demands like YAML.

### 2.3 Encryption
#### 2.3.1 Approaches
- *At rest*
    - For protection against physical threats
    - Used fairly commonly in Cloud environments. Even if anyone finds the host machine, they can use my data.
- *In transit*
    - An encryption wrapper/ tunnel is applied.
    - Multiple individuals/ systems involved.
#### 2.3.2 Concepts
- *Plaintext*
    - Un-encrypted data.
    - Misnomer. Can be non-text data too (images, document, etc.)
- *Algorithm*
    - Takes Plaintext + Encryption key to encrypt data
    - Examples = Blowfish, AES, RC4, DES, RC5, RC6
- *Key*
    - Simply, a password
- *Cyphertext*
    - Output of encryption. Not text data. Encrypted data

#### 2.3.3 Symmetric encryption using an example
- Sender has **Plaintext data** and **Symmetric encryption key**
- Sender uses the two and encrypts them using **AES-256**
- Cyphertext is output
- But how will receiver decrypt without the key being transferred too? 

> __Note__
- Here, same key is used for encryption and decryption.
- Not recommended for data transfer, unless the key itself has been securely transferred!
- Therefore good for local file/ disk encryption.

#### 2.3.4 Asymmetric encryption using an example
- Sender and Receiver agree on using asymmetric encryption.
- Receiver has two keys - **Public key** and **Private key**.
- Receiver makes his Public key, public.
- Sender uses **Plaintext data** and Receiver's **Public key** and encrypts them using asymmetric algorithm.
- Cyphertext is output and transmitted.
- Receiver decrypts using its private key.

#### 2.3.5 Signing - a process that uses asymmetric encryption
- Receiver wants to confirm acceptance of the original message and wants to do so under signature.
- Receiver signs his acceptance message using **Private key**
- Sender uses Receiver's **Public key** to verify the identity of the signer.

#### 2.3.6 Steganography
- Hiding information within a message such that its presence is not evident to human inspection.[^2]

[^2]: [Steganography](https://en.wikipedia.org/wiki/Steganography?raw=true)

> __Note__
- Public key encrypts, while the associated private key decrypts.
- Used when two or more parties involved.
- Used in these examples
    - PGP (an email encryption system)
    - SSL/ TLS (encrypting browser communications)
    - SSH (popular method for accessing servers using key based auth)
- Computationally expensive. So, used to initally send symmetric encryption keys! Brilliant :nerd_face:
- Assymetric encryption is also useful in ID verification. 

### 2.4 Network Starter Pack 
#### 2.4.1 OSI 7-layer model
Provides a conceptual understanding of networking.
1. Physical (L1)
2. Data link (L2)
3. Network (L3)
4. Transport (L4)
5. Session (L5)
6. Presentation (L6)
7. Application (L7)

*Physical*
- Devices use shared physical media = Network cable (electrical); Fibre (light), WiFi (RF)
- Standards exist for transmitting to/ receiving from physical media. For example voltage, connector type.
- Standards help devices with a common understanding. Say, a certain voltage $\implies{}$ bit 1 or 0
- For more devices on the network, a hub is required.
- No device is uniquely identifiable on the network.
- Therefore, hubs broadcast. Results in collisions!
- No access control over which device can transmit on shared medium.
- Dumb layer. Scales poorly.

*Data link*
- Uses the physical layer.
- Uses **MAC address**, a globally unique hexadecimal address for hardware devices.
- Uses a 6-part format for sending information (**Frames**)
    - *Preamble* and *Start Frame Delimiter (SFD)*: To know start of frame
    - *Destination MAC address*
    - *Source MAC address*
    - *Ethertype*: To specify which layer 3 protocol (e.g. IP) is putting its data inside the frame.
    - *Payload*: Contains the data from layer 3.
    - *Frame Check Sequence (FCS)*: To identify errors in frame.
- Uses **Collision Detection** (CD)
    - On collision, a random back-off occurs.
    - On repeat collision, back-off occurs for longer period.
- Uses **Switch** (not Hub)
    - Does not broadcast to all PCs like a Hub.
    - Reads frames. Maintains MAC address table for devices.
    - Relays only to PC in destination MAC address.
    - Reduces collisions.
- Uses below process
    - Consider two PCs trying to communicate. PC(L) and PC(R)
    - Say, PC(L) knows MAC address of PC(R).
    - Application on PC(L) wants Ethernet to send data to MAC address of PC(R).
    - L2(L) creates a frame F1.
    - Data encapsulated into payload of F1.
    - L2(L) looks for a carrier signal on L1 (**CSMA**)
        - If signal detected, waits before transmitting (**Access control**)
        - When no signal detected, F1 is passed to L1(L).
            - L1(L) converts frame to physical standard and transmits.
            - L1(R) passes it up to L2(R).
            - L2(R) verifies destination MAC address.
            - L2(R) de-encapsulates.

*Network*
- Enables device-to-device communications over the internet.
- IP (Internet Protocol) is L3 protocol. Moves data between LANs without Point-to-Point links.
    - Two versions. IPV4 and IPv6
    - IPv4
        - IP has two parts (say, 133.33.3.7) = Network + Host
        - First two octets denote the network. Last two denote the host.
        - Matching network part $\implies{}$ local. Else remote.
        - Can be assigned 
            - Statically by humans
            - Automatically by machines (DHCP)
        - Has to be unique globally.
        - Subnet masks
            - determine which part of an IP is network and which the host.
            - configured on L3 of host device. Say, 255.255.0.0
            - help host (say, your PC) determine if IP is local or remote
            - if remote, host uses gateway (e.g., Internet router on home network) to send data.
        - Route tables and Routes
            - Router at the ISP has route tables.
            - Maps destination IP to Next hop/ target
            - ISP's router has multiple network interface cards connected to remote networks
            - ISP router will have at least 1 route table.
            - ISP router compares destination IP with the destination column of route table.
            - Sent to the "next hop" getting it one step closer to the destination.
            - Address Resolution Packet
                - When an L3 packet and you want to encapsulate it inside a frame and send to a MAC address, but the MAC address is not known.
                - Required - Protocol for identifying a MAC address of a known IP address.
                - ARP runs between L2 and L3
        - Processs (IP Routing)
            - 
        - Feature addition by L3
            - ARP
            - Route - where to forward packets?
            - Route tables - multiple routes
            - Router 

*Transport*
- In L3 
    - Out-of-order arrival of packets can happen. Each packet routed independently.
    - Packets can go missing too. Say, lost due to the number of hops limitation.
    - There can be latency in delivery too.
    - Doesn't offer any method of separating packets by application or channel. All packets from source to destination IP are all the same!



*Session*

*Presentation*

*Application*



> __Note__
- The 7 layers form the Networking stack
- Media layers = 1, 2, and 3
- Host layers = 4, 5, 6, and 7
- Layer X $\implies{}$ has functionality for layer X and below.
- MAC address is not software assigned. Unique to a specific piece of hardware.
- CSMA = Carrier Sense Multiple Access. Looks for signs of career signal on L1.
- Back-off = period during which no device attempts transmission.
- Decimal to Binary conversion (IP addressing)
    - Range = [0, 255]
    - Each number in range takes 8 bits to represent. Total 32 bits.
    - See table below

        | n                  |   8   |   7   |   6   |   5   |   4   |   3   |   2   |   1   |
        |          ---              |  ---  |  ---  |  ---  |  ---  |  ---  |  ---  |  ---  |  ---  |
        | **$2^{(n-1)}$** |  128 |  64  |  32  |  16  |   8  |   4  |   2  |  1 |
        |      **Binary number**     |       |       |       |       |       |       |       |       |
    - Conversion rule
      ![rule](https://shamasun.github.io/SAA-C03/assets/images/dec2Bin.png?raw=true)

- Binary to Decimal conversion
    - Sum the **$2^{(n-1)}$** value corresponding to all the binary values of 1
- "/24" $\implies{}$ first 24 bits for the network. Last 8 for host.

#### 2.4.1 Introduction

#### 2.4.2 Physical layer

#### 2.4.3 Data link

#### 2.4.4 Network

#### 2.4.5 Transport

#### 2.4.6 Network address translation

#### 2.4.7 Decimal to Binary Conversion (IP Addressing)

#### 2.4.8 Subnetting

#### 2.4.9 Distributed Denial of Service (DDOS)

### 2.5 Secure Sockets Layer (SSL) and Transport Layer Security (TLS)

### 2.6 VLANS, Trunks & Q-in-Q

### 2.7 Hash Functions & Hashing

### 2.8 Digital Signatures

### 2.9 DNS 101

#### 2.9.1 What does DNS do?

#### 2.9.2 Why does DNS need a complex architecture?

#### 2.9.3 How DNS works? - walking the tree

#### 2.9.4 What happens when a domain is registered?

#### 2.9.5 Why do we need DNSSEC?

#### 2.9.6 How DNSSEC Works within a Zone?

#### 2.9.7 DNSSEC Chain of Trust

#### 2.9.8 DNSSEC Root Signing Ceremony

### 2.10 Recovery Point Objective (RPO) and Recovery Time Objective (RTO)
