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
- Therefore good for local file/ disk encryption. 
- Not recommended for data transfer.

#### 2.3.4 Asymmetric encryption using an example
- Sender and Receiver agree on using asymmetric encryption.
- Receiver has two keys - **Public key** and **Private key**.
- Receiver makes his Public key, public.
- Sender uses **Plaintext data** and Receiver's **Public key** and encrypts them using asymmetric algorithm.
- Cyphertext is output and transmitted.
- Receiver decrypts using its private key.

> __Note__
- Public key encrypts. Its associated private key decrypts.
- When two or more parties involved
- Used in 
    - PGP (an email encryption system)
    - SSL/ TLS (encrypting browser communications)
    - SSH (popular method for accessing servers using key based auth)
- Computationally expensive. So, used to initally send symmetric encryption keys! Brilliant :nerd_face:

### 2.4 Network Starter Pack 

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