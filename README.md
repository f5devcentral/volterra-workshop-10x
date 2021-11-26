# Volterra Workshop 10x
Volterra Workshop 10x for F5ers, partners and customers.

UNDER CONSTRUCTION !!!!!!!

## Overview
Volterra Workshop 10x for F5ers, Partners and customers. This workshop is different from the Volterra 101 labs. It will be split in different sub-labs including K8S workshop and Public Cloud Networking 101.

---

## The Plan

* Per region with one local Volterra Lead
* Will be split in different session so that students can take advantage of each session, and move forward step by step

### k8s 201

* Deploy a modern app in Azure AKS
* SE deployed apps in k8S in Q3, now let's do it in a public cloud
* Understand how an app is publish in an AKS (ingress + LB)

### Volterra 101

* Use case #1 - publish a public app through Volterra Global Network (understood by the field on last Monday)
* Use case #2 - publish a private app running in the AKS on the Votlerra Global Network --> Voltconsole
  
  * Azure Networking 101
  * Understand how AKS/EKS/GKS publish apps on vnet/vpc
  * Deploy a VoltMesh on the same vnet
  * Create the LB + OP
  * Understand the workflow

* Take Away --> create your Terraform plan with all the settings used in the previous steps.

  * Keep this plan for the next workshop (2 weeks later)
  * DELETE the Volterra environment and keep the AKS up and runnning

### Volterra 102 - 2 weeks later

* Use case #4

  * Re-deploy the same Volterra environment with the Terraform
  * Lift and shift one service to AWS
    * AWS networking 101
    * TGW vs VPC
  * Understand Volterra MCN

---

## Support
For support, please open a GitHub issue.  Note, the code in this repository is community supported and is not supported by F5 Networks.  For a complete list of supported projects please reference [SUPPORT.md](SUPPORT.md).

## Community Code of Conduct
Please refer to the [F5 DevCentral Community Code of Conduct](code_of_conduct.md).

## License
[Apache License 2.0](LICENSE)

## Copyright
Copyright 2014-2020 F5 Networks Inc.


### F5 Networks Contributor License Agreement

Before you start contributing to any project sponsored by F5 Networks, Inc. (F5) on GitHub, you will need to sign a Contributor License Agreement (CLA).

If you are signing as an individual, we recommend that you talk to your employer (if applicable) before signing the CLA since some employment agreements may have restrictions on your contributions to other projects.
Otherwise by submitting a CLA you represent that you are legally entitled to grant the licenses recited therein.

If your employer has rights to intellectual property that you create, such as your contributions, you represent that you have received permission to make contributions on behalf of that employer, that your employer has waived such rights for your contributions, or that your employer has executed a separate CLA with F5.

If you are signing on behalf of a company, you represent that you are legally entitled to grant the license recited therein.
You represent further that each employee of the entity that submits contributions is authorized to submit such contributions on behalf of the entity pursuant to the CLA.