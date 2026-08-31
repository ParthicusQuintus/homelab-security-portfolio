\# VLAN Segmentation  
  
## Overview  
  
My Castellum homelab uses VLAN segmentation to separate systems based on their role and security requirements rather than placing every device on a single flat network.  
  
The primary goals of the design were to:  
  
- Reduce unnecessary communication between systems especially NAS traffic.  
- Limit the impact of a compromised host  
- Separate infrastructure management from application traffic  
- Isolate security monitoring systems  
- Provide dedicated areas for lab and testing activity  
- Apply firewall rules based on network function and needs  
- Make network traffic easier to monitor and troubleshoot  
  
Inter-VLAN routing is handled by OPNsense and Omada Level 2 Switches. Using a Omada Controller for the Managed switches that carry the VLANs between network infrastructure using tagged/untagged and trunk connections. Firewall policy is handled by OPNSense at the gate, and UFW for inter-firewall rules.  
  
---  
  
## Network Segments  
  
| Segment | Purpose | Systems |  
|---|---|---|  
| Management | Infrastructure administration and management interfaces | Proxmox, network controller, switches, NAS management, infrastructure servers |  
| Servers | Internal application and service hosting | Docker hosts, databases, DNS, Kubernetes nodes, mail services |  
| IDS / Monitoring | Security monitoring, logging, and traffic analysis | Netflow, Graylog, packet analysis and monitoring systems |  
| DMZ / Public Edge | Systems that handle externally accessible traffic | Reverse proxy, authentik services, and crowdsec |  
| Lab / Transit | Networking and cybersecurity testing environment | Lab switches, test systems, training clients |  
| Wireless / Access | User and endpoint connectivity | Workstations and wireless clients |  
  
---
