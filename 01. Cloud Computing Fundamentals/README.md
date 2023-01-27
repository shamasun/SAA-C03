## 1.0 Cloud Computing Fundamentals

### 1.1 What is Cloud Computing?

Based on the formal definiton from [(NIST)](/Assets/files/nistspecialpublication800-145.pdf). All of them need to be satisfied.

1. **On-demand self-service**</span>: Provision as needed, without requiring human interaction.
2. **Broad network access**: Available over the network and accessed through standard mechanisms (http, https, ssh, vpn, etc.)
3. **Resource pooling**: User has no control or knowledge over location of resources **AND** Pooling over several customers using multi-tenancy.
4. **Rapid Elasticity**: Elastic provisioning and released to scale rapidly outward/ inward **AND** To consumer, capabilities appear unlimited. 
5. **Measured service**: Usage can be monitored, controlled, reported and billed.

> __Note__
- Mnemonic = <!-- O-Ne-PooRe-Elas!-MeServe -->
- Each time a service is introduced, examine it w.r.t these characteristics.

### 1.2 Public vs Private vs Multi vs Hybrid Cloud

1. **Public**: Using a public cloud environment
2. **Multi**: Using more than one Cloud environments. With or without a 3rd party abstraction tool.
3. **Private**: Using a Cloud environment, dedicated to a customer on-premises.
4. **Hybrid**: Private cloud + Public cloud

> __Note__
- Third party abstraction tools for multi-cloud $\implies{}$ Loss of features unique to a cloud platform. Abstraction comes at a cost.
- Names of Private cloud offerings = Outposts (AWS); Azure stack (Azure); Anthos (GCP).
- Private cloud meets Cloud Computing definition.
- On-premises infra (VMWare, HyperV, Zen Server) doesn't meet Cloud Computing definition.
- Hybrid environment/ network (not Hybrid Cloud) = Using Public cloud with on-premises equipment. 
- Hybrid cloud $\implies{}$ Same tooling, same interface, for public and private cloud.

### 1.3 Cloud Service Models

#### 1.3.1 Terms & Concepts
- *Infrastructure* or *Application stack* = Facilities + Infrastructure + Servers + Virtualization + OS + Container + Runtime + Data + Application
- *Unit of consumption*
    - what you consume and pay for
    - part of the stack you manage upwards
    - Example - purchased a VM? Unit of consumption = OS

#### 1.3.2 Types of Cloud Service models
![models](../00%20Assets/images/cloud%20models.png?raw=true)