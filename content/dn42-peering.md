---
title: "DN42 Peering"
date: 2021-04-27T20:00:36-04:00
---



# AS4242421099



> Please send an email to justin [at] owensresearch.org for peering. Due to limitations on my network, I try to avoid peering with link-local.  By default I will use the below /128 ULA address.  If you would like something different, please let me know.



## OR-DE-FRA-01

**FQDN:** de-fra01.owensresearch.org  
**Bandwidth:** 1Gbps up/down  
**Endpoint IPv4:** 95.179.250.248  
**Endpoint IPv6:** 2001:19f0:6c01:acd:5400:2ff:fed9:8aad  
**Endpoint Port:** 20000 + Last 4 of your ASN  
**Tunnel IPv4:** 172.21.99.137/32  
**Tunnel IPv6:** fd42:4242:1099:179::137/128  

## OR-AU-SYD-01

**FQDN:** au-syd01.owensresearch.org  
**Bandwidth:** 1Gbps up/down  
**Endpoint IPv4:** 207.148.81.118  
**Endpoint IPv6:** 2401:c080:1800:4a90:5400:3ff:fe21:c6f7  
**Endpoint Port:** 20000 + Last 4 of your ASN  
**Tunnel IPv4:** 172.21.99.153/32  
**Tunnel IPv6:** fd42:4242:1099:179::153/128  


## OR-US-EAST-01

> New connections on this node will only be created with the IPv6 tunnel address.  Additionally, the wireguard interface on both sides will require MTU 1400 to be set.



**FQDN:** us-east01.owensresearch.org  
**Bandwidth:** 1Gbps up/down  
**Endpoint IPv6:** 2001:470:e03c:42::2  
**Endpoint Port:** 20000 + Last 4 of your ASN  
**Tunnel IPv4:** 172.21.99.129/32  
**Tunnel IPv6:** fd42:4242:1099:179::129/128  
*MTU: 1400*  

# Routing Policy/Information

 - Accept all RPKI/ROA valid routes.  
 - Reject unknown and invalid routes.  
 - I am open to any experimental peering that may require an exception.  


# Communities

 - Routes originating from AS4242421099 are tagged with the regional origin community value as documented on the DN42 Wiki. [https://dn42.wiki/howto/Bird-communities](https://dn42.wiki/howto/Bird-communities)


## Large Communities
| Community | Description     |
|-----------|-----------------|
|4242421099:129:1  |  Imported @ Virginia, US PoP   |
|4242421099:129:2  |  Originated @ Virginia, US PoP   |
|4242421099:137:1  |  Imported @ Frankfurt, DE PoP  |
|4242421099:137:2  |  Originated @ Frankfurt, DE PoP  |
|4242421099:153:1  |  Imported @ Sydney, AU PoP  |
|4242421099:153:2  |  Originated @ Sydney, AU PoP  |


----


> **Page Updated: May. 17, 2021**