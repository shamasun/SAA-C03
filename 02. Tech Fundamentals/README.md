## 2.0 Technical Fundamentals

### 2.1 YAML (YAML Ain't a Markup Language) 101
#### Introduction
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

#### Elements of a list can be written
- in-line within square brackets
- as sub-bullets below the key, using hyphen as the bullet

Example of an employee record
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

### 2.2 JSON (JavaScript Object Notation) 101

### 2.3 Encryption

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