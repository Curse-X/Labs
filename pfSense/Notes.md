### Enabling SSH:
- System --> Advances --> Admin Access
	- Secure Shell
		- [x] Enable Secure Shell
		+ SSHd Key only:
			- Password
			- Public Key
			- Password and public Key
		- [ ] Allow Agent Forwarding
		+ SSH port: 22
	- Save
- Test SSH
	- ssh admin@<IP>

### Add a User:
- System --> User manager --> Add
	- [ ] This user cannot login
	- Username:
	- Password:
	- Full name:
	- Group mambership: admins (To add admin user)

### Disable and Block IPv6:
- Block
	- System --> Advanced --> Networking
		- [ ] Allow IPv6
		- Save
- Disable DHCP on WAN
	- Interfaces --> WAN --> General Configuration
		- IPv6 Configuration Type: None
	- Save
- Disable DHCP on LAN
	- Interfaces --> LAN --> General Configuration
		- IPv6 Configuration Type: None
	- Save
- Disable DHCPv6 Server
	- Services --> DHCPv6 Server & RA --> LAN --> DHCPv6 Server --> DHCPv6 Options
		- [ ] DHCPv6 Server
		- Save
- Disable DHCPv6 Rules
	- Firewall --> Rules --> LAN
		- Note: Disable all IPv6 rules (By clicking "Disable" Button)
	- Click "Apply Changes" Button

### Customize Dashboard:
- System information
- Traffic Graphs
- Firewall Logs
- Interface Statistics
- Interfaces
- Disks
- Captive Portal Status
- Netgate Services and Support
- Change Theme
	- System --> General Setup --> WebConfigurator
		- Theme:
			pfSense
			pfSense-dark
			pfSense-dark-BETA
			pfSense-BETA
			Compact-RED

### Firewall Considerations:
- Rules and Rulesets
- Stateful Filtering
- Block or Reject
- Ingerss and Egress
- Whitelisting and Blacklisting
#### Rules and Rulesets:
#### Stateful Filtering:
- Firewall keeps tracking of outbound requests and listens for and processes related replies in a state table
	- Diagnostics --> States
#### Block or Reject:
|Block                 |Reject                |
|----------------------|----------------------|
|Silently drop packet  |Reject with a reply   |
|Good for WAN interface|Good for LAN interface|
#### Ingerss and Egress:
```
      LAN       ________________________      WAN
    Egress     |                        |    Egress
 ------------> |                        | ------------>
               |                        |
               |        Firewall        |
               |                        |
 <------------ |                        | <------------
    Ingress    |________________________|    Ingress
```
#### Whitelisting and Blacklisting
- Blacklisting
	- Denying bad traffic (Ports)
	- Example:
		- Block TCP port 1337 outbound
		- but other 65534 ports not blocked
		- Blocking each unwanted ports is difficult
- Whitelisting:
