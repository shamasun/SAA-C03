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
1. Physical
2. Data link
3. Network
4. Transport
5. Session
6. Presentation
7. Application

*Physical*
- Devices use shared physical media = Network cable (electrical); Fibre (light), WiFi (RF)
- Standards exist for transmitting to/ receiving from physical media. For example voltage, connector type.
- Standards help devices with a common understanding. Say, a certain voltage $\implies{}$ bit 1 or 0
- For more devices on the network, a hub is required.
- No device is uniquely identifiable on the network.
- Therefore, hubs broadcast. This means collisions!
- No access control over which device can transmit on shared medium.
- Dumb layer. Scales poorly.

*Data link*
- Works on top of a working layer 1 connection.

*Network*

*Transport*

*Session*

*Presentation*

*Application*



> __Note__
- The 7 layers form the Networking stack
- Media layers = 1, 2, and 3
- Host layers = 4, 5, 6, and 7
- Layer X device $\implies{}$ it has functionality for layer X and below.


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