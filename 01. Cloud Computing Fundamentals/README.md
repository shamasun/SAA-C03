## Cloud Computing Fundamentals

### What is Cloud Computing?

Based on the formal definiton from [(NIST)](https://github.com/shamasun/SAA-C03/blob/703d03ef3e8df7f3fa2ee3fd2674d5acecf02d07/01.%20Cloud%20Computing%20Fundamentals/nistspecialpublication800-145.pdf). All of them need to be satisfied. Mnemonic = ONPrEM

1. **On-demand self-service**</span>: Provision as needed, without requiring human interaction.
2. **Broad network access**: Available over the network and accessed through standard mechanisms (http, https, ssh, vpn, etc.)
3. **Resource pooling**: User has no control or knowledge over location of resources **AND** Pooling over several customers using multi-tenancy.
4. **Rapid Elasticity**: Elastic provisioning and released to scale rapidly outward/ inward **AND** To consumer, capabilities appear unlimited. 
5. **Measured service**: Usage can be monitored, controlled, reported and billed.

> __Note__: 
- Internalilze these characteristics
- Each time a service is introduced, examine it w.r.t them.

### Public vs Private vs Multi vs Hybrid Cloud

1. **Public**: Using a public cloud environment
2. **Multi**: Using more than one Cloud environments. With or without a 3rd party abstraction tool.
3. **Private**: Using a Cloud environment, dedicated to a customer on-premises.
4. **Hybrid**: Private cloud + Public cloud

Side comments:
- With 3rd party abstraction tool in multi-cloud, you may loose features unique to a cloud platform. Abstraction comes at a cost.
- Names of Private cloud offerings: Outposts (AWS); Azure stack (Azure); Anthos (GCP).
- Difference between On-premises infra (VMWare, HyperV, Zen Server) vs. Private cloud. Private cloud meets Cloud Computing definition. The former usually don't.
- Using Public cloud with on-premises equipment is a Hybrid environment/ network (not Hybrid Cloud). In true Hybrid cloud, one gets the same tooling, same interface, etc. in working with both cloud environments.

### Cloud Service Models