# Network Configuration 

This lab uses a static IP configuration for critical servers to ensure stable log forwarding and reliable communication between systems.

## Network Overview
- Network Range: 192.168.10.0/24
- Default Gateway: 192.168.10.1
- DNS Server: 8.8.8.8

## Splunk Server Static IP Configuration

The Splunk server was configured with a static IP address to avoid IP changes that could break log forwarding from endpoints and servers.

- Hostname: Splunk Server
- Interface: enp6s3
- IP Address: 192.168.10.10/24
- DHCP: Disabled

### Netplan Configuration (Ubuntu)

```yaml
network:
  version: 2
  ethernets:
    enp6s3:
      dhcp4: no
      addresses:
        - 192.168.10.10/24
      nameservers:
        addresses:
          - 8.8.8.8
      routes:
        - to: default
          via: 192.168.10.1
