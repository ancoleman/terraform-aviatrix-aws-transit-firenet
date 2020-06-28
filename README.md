# Module Aviatrix Transit Firenet VPC for AWS

### Description
This module deploys a VPC, Aviatrix transit gateways and firewall instances. Defining the Aviatrix Terraform provider is assumed upstream and is not part of this module.

### Diagram
<img src="images/module-aviatrix-transit-firenet-vpc-for-aws-fortinet-ha.png"  height="250">

with ha_gw set to false, the following will be deployed:

<img src="images/module-aviatrix-transit-firenet-vpc-for-aws-fortinet.png"  height="250">

### Variables
The following variables are required:

key | value
--- | ---
region | AWS region to deploy the transit VPC in
aws_account_name | The AWS accountname on the Aviatrix controller, under which the controller will deploy this VPC
cidr | The IP CIDR wo be used to create the VPC.
firewall_image | String for the firewall image to use

Firewall images
```
Palo Alto Networks VM-Series Next-Generation Firewall Bundle 1
Palo Alto Networks VM-Series Next-Generation Firewall Bundle 1 [VM-300]
Palo Alto Networks VM-Series Next-Generation Firewall Bundle 2
Palo Alto Networks VM-Series Next-Generation Firewall Bundle 2 [VM-300]
Palo Alto Networks VM-Series Next-Generation Firewall (BYOL)
Check Point CloudGuard IaaS Next-Gen Firewall w. Threat Prevention &amp; SandBlast BYOL
Check Point CloudGuard IaaS Next-Gen Firewall with Threat Prevention
Check Point CloudGuard IaaS All-In-One
Fortinet FortiGate Next-Generation Firewall
Fortinet FortiGate (BYOL) Next-Generation Firewall
```

The following variables are optional:

key | default | value
:--- | :--- | :---
instance_size | c5.xlarge | Size of the transit gateway instances
fw_instance_size | c5.xlarge | Size of the firewall instances
ha_gw | true | Set to false to disable deploying an HA GW and FW instance
attached | true | Attach firewall instances to Aviatrix Gateways

### Outputs
This module will return the following objects:

key | description
:--- | :---
vpc | The created VPC as an object with all of it's attributes. This was created using the aviatrix_vpc resource.
transit_gateway | The created Aviatrix transit gateway as an object with all of it's attributes.