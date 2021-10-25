# wg-clientmgr
Bash script to auto-generate client configuration files for Wireguard, includes QR code and automatic peer installation.

---

### Format is:
**wg-clientmgr [clientName] [clientIP] [allowedIPs] [serverIP]**

**[clientName]** - Label to be used for generated files, e.g. clientA_device1"

**[clientIP]** - IP and netmask to be used for client VPN address in CIDR notation (recommend /32 for all clients regardless of actual subnet size), e.g. 192.168.2.5/32"

**[allowedIPs]** - Client subnet(s) to be filtered through VPN tunnel (separated by ',', no spaces), e.g. 192.168.2.0/24,10.1.1.1/26,1.1.1.1/32 OR 0.0.0.0/0 to tunnel all traffic"

**[serverIP]** - VPN server public IP and port, e.g. 1.2.3.4:50600"

---

### Examples: 
**4th argument not included, server address set to default**

wg-clientmgr clientA_device1 192.168.2.5/32 192.168.2.0/24,10.1.1.1/26,1.1.1.1/32

**4th argument included, server address '1.2.3.4:50600' overrides default address**

wg-clientmgr clientA_device1 192.168.2.5/32 192.168.2.0/24,10.1.1.1/26,1.1.1.1/32 1.2.3.4:50600 

---

### User variables defined in script:

**$localdir** - directory for new configuration files

**$localpubkey** - location of VPN server's public key

**$serverint** - Wireguard server interface (typically wg#)

**$servercfg** - location of VPN server interface config file

**$clientdns** - DNS servers to use for client (default is OpenDNS)
