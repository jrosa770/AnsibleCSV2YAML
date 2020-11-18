# Ansible CSV to YAML

## YAML Hostvar Builder from CSV Input

Utilizes CSV based inputs to create YAML language variables and values. The playbook is mainly intended to configure Cisco ACI, but the process can be translated to other platforms as long as the proper Jinja2 template is created 

Example input .csv file:

```csv
Tenant,Alias,AppId,Tier,Subnet,Gateway,CIDR,VMMDOM
DevQA-Test01,DQA01,9999,APP,10.255.255.0,10.255.255.1,28,NonProd
DevQA-Test01,DQA01,9999,PRES,10.255.255.16,10.255.255.17,28,NonProd
DevQA-Test01,DQA01,9999,DB,10.255.255.32,10.255.255.33,28,NonProd
```

The playbook will first interact with the user. Then will process, parse and translate inputs and requirements to `YAML` format. After subsequent interactions and final confirmation, the required inputs will be inserted into the appropriate sections of the target apic's `hostvar` file for final processing and build.

The intention of the playbook is to be multiuse, not only builds, but also a section specific, work playbook, where the user can do a full build by `hostvar` edit or `.csv` import while having the ability to edit build sections from the `hostvar` file and perform adds, deletes and queries of specific components. This components are:

* Tenants (TN)
* VRF's (VRF)
* Applications Profiles (AP)
* Bridge Domains (BD) and Bridge Domain Subnets (BDS)
* End Point Groups (EPG)