
[[Linux]]
[[dns]]

**How does /etc/hosts work?**


The concept of the /etc/hosts file is very simple, just an address and a host name:

127.0.0.1      localhost

for each line. That is a simple list of pairs of address-host.2

Its primary present-day use is to bypass DNS resolution. A match found in the /etc/hosts file will be used before any DNS entry. In fact, if the name searched (like localhost) is found in the file, no DNS resolution will be performed at all.

1 Well, the order of name resolution is actually defined in /etc/nsswitch.conf, which usually has this entry:

hosts:          files dns

which means "try files (/etc/hosts); and if it fails, try DNS."

But that order could be changed or expanded.

The hosts file contains lines of text consisting of an IP address in the first text field followed by one or more host names. Each field is separated by white space – tabs are often preferred for historical reasons, but spaces are also used. Comment lines may be included; they are indicated by an octothorpe (#) in the first position of such lines. Entirely blank lines in the file are ignored. For example, a typical hosts file may contain the following:

```
127.0.0.1   localhost loopback
::1         localhost localhost6 ipv6-localhost ipv6-loopback mycomputer.local
192.168.0.8 mycomputer.lan
10.0.0.27   mycomputer.lan
```

This example contains entries for the loopback addresses of the system and their host names, the first line is a typical default content of the hosts file. The second line has several additional (probably only valid in local systems) names. The example illustrates that an IP address may have multiple host names (localhost and loopback), and that a host name may be mapped to both IPv4 and IPv6 IP addresses, as shown on the first and second lines respectively. One name (`mycomputer.lan`) may resolve to several addresses (`192.168.0.8 10.0.0.27`). However, in that case, which one is used depends on the routes (and their priorities) set for the computer.