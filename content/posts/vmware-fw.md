---
author: "Justin Owens"
date: 2021-01-05
title: "VMware Notes"
---

# Adding Custom Ports to ESXi Host Firewall

This post covers adding a custom syslog port but the concept can be applied for other needed firewall changes.  By default syslog uses UDP port 514.  However, most syslog servers and clients can easily be configured to use different ports.  Because ports 0-1024 are system ports that sometimes require escalated rights to bind to, the most simple solution could be to use a custom port for syslog.  The ESXi firewall by default allows common ports outbound such as 514, but probably will not allow a custom port.  This post was written using ESXi 6.7U3.


## Checking Current Firewall Configuration

Before changing anything, lets take a quick look at the current configuration.
1. Launch and login to vCenter.
2. Navigate to **Host and Clusters**.
3. Highlight the host in question within your datacenter.
4. Select **Configure** -> **Firewall**.

## Create Custom Firewall Rule
1. SSH the ESXi host.
2. Navigate to the firewall directory.
`cd /etc/vmware/firewall`
3. Create and edit a new file for the custom rule.
`vi syslog-custom.xml`
4. Below is an example of what the finished syslog-custom.xml should look like when done.
```xml
<ConfigRoot>
  <service>
    <id>syslog-custom</id>
    <rule id='0000'>
      <direction>outbound</direction>
      <protocol>udp</protocol>
      <porttype>dst</porttype>
      <port>5514</port>
    </rule>
    <enabled>false</enabled>
    <required>false</required>
  </service>
</ConfigRoot>
```

## Reload Firewall
1. `esxcli network firewall unload`
2. `esxcli network firewall load`

## Enable Syslog on Custom Port
1. `esxcli network firewall ruleset set  -e true -r syslog-custom`



> I want to credit "dnozay" on GitHub for his awesome repo explaining this.  Please give his repo a look [here](https://gist.github.com/dnozay/9352804) for a few more CLI examples that will help you get remote syslog setup.


# NSX-T Notes
  
  
`esxcfg-nics -l`  - shows mtu of physical adapters

`nsxdp-cli vswitch instance list` - list nsx backed logical switches

`nsxdp-cli vswitch mtu get -dvs switchname`  - list mtu of nsx switch

