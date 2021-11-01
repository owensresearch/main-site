---
title: "DN42 Peering"
date: 2021-04-27T20:00:36-04:00
---



# AS4242421099

Please send an email to justin [at] owensresearch.org for peering.

I prefer to use Wireguard for all peerings.

> Due to limitations on my network, I try to avoid peering with link-local.  By default I will use the below /128 ULA address.  If you would like something different, please let me know.



## Frankfurt, DE

**FQDN:** de-fra01.owensresearch.org  
**Bandwidth:** 1Gbps up/down  
**Endpoint IPv4:** 95.179.250.248  
**Endpoint IPv6:** 2001:19f0:6c01:acd:5400:2ff:fed9:8aad  
**Endpoint Port:** 20000 + Last 4 of your ASN  
**Tunnel IPv4:** 172.21.99.137/32  
**Tunnel IPv6:** fd42:4242:1099:179::137/128  

## Sydney, AU

**FQDN:** au-syd01.owensresearch.org  
**Bandwidth:** 1Gbps up/down  
**Endpoint IPv4:** 207.148.81.118  
**Endpoint IPv6:** 2401:c080:1800:4a90:5400:3ff:fe21:c6f7  
**Endpoint Port:** 20000 + Last 4 of your ASN  
**Tunnel IPv4:** 172.21.99.153/32  
**Tunnel IPv6:** fd42:4242:1099:179::153/128  

## Dallas, US

**FQDN:** us-dal01.owensresearch.org  
**Bandwidth:** 1Gbps up/down  
**Endpoint IPv4:** 144.202.64.27  
**Endpoint IPv6:** 2001:19f0:6401:111d:5400:3ff:fea5:3729  
**Endpoint Port:** 20000 + Last 4 of your ASN  
**Tunnel IPv4:** 172.21.99.143/32  
**Tunnel IPv6:** fd42:4242:1099:179::143/128  


# Route Filtering

 - ROA checking is performed on import/export.
 - ROA data is generated from the DN42 registry.
 - Unknown and invalid address space is not permitted on AS4242421099.
 
# Allowed Transit Traffic

 - 10.0.0.0/8
 - 172.20.0.0/14
 - 172.31.0.0/16
 - fd00::/8
 


# Communities

 - Routes originating from AS4242421099 are tagged with the regional origin community value as documented on the DN42 Wiki. [https://dn42.wiki/howto/Bird-communities](https://dn42.wiki/howto/Bird-communities)


## Large Communities
| Community | Description     |
|-----------|-----------------|
|4242421099:134:1  |  Imported @ Dallas, US PoP   |
|4242421099:134:2  |  Originated @ Dallas, US PoP   |
|4242421099:137:1  |  Imported @ Frankfurt, DE PoP  |
|4242421099:137:2  |  Originated @ Frankfurt, DE PoP  |
|4242421099:153:1  |  Imported @ Sydney, AU PoP  |
|4242421099:153:2  |  Originated @ Sydney, AU PoP  |


----


> **Page Updated: Nov. 01, 2021**