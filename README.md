# Advanced Template Net Mikrotik SNMPv2

Template based on original Template Net Mikrotik SNMPv2 from stock Zabbix 3.4

## Improvements
* Added main device MAC to inventory
* Added item "Interface MAC address" for each interface (useful for mac-telnet/mac-winbox in MikroTik)
* Added unicast pps items and add its to traffic graphs
* Changed trigger "High bandwidth usage" to operate only on ethernet type interfaces (because speed of other type interfaces determines incorrect in MikroTik)
* Added Queues Simple discovery with graphs
* Added IP discovery with ICMP triggers and graphs, for multiwan configurations (discovering all IPs, except regexp)

## Installation

Tested on Zabbix 3.4+

* At first you need to import `Advanced_Template_Module_Interfaces_SNMPv2.xml`. This module is linked with the main template.
* Then import  the main module `Advanced_Template_Net_Mikrotik_SNMPv2.xml`

For correct IP discovery working, you need to add Regular Expressions (see screenshot), for discovering only public IPs:
```
IP addresses for discovery	
1	»	^(172\.(1+[6-9]|2+[0-9]|3+[0-2])\.)+[0-9]{1,3}+\.+[0-9]{1,3}$	[Result is FALSE]
2	»	^(10\.[0-9]{1,3}\.)+[0-9]{1,3}+\.+[0-9]{1,3}$			[Result is FALSE]
3	»	^(192\.168\.)+[0-9]{1,3}+\.+[0-9]{1,3}$				[Result is FALSE]
```
![RegExp IP addresses for discovery](/regexp/regexp-ip_addresses_for_discovery.png?raw=true "RegExp IP addresses for discovery")
