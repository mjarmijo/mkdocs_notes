
## /etc/hosts file

- ip-hostname pairs
- list of ip addresses and hostnames - provides hostname resolution to an ipv4 or ipv6 address
- built-in system dns bypass, has maximum priority
- A match found in the /etc/hosts file will be used before any DNS entry. If the name searched is found in the file (like localhost), no DNS resolution is performed at all as the IP is known.

```python title="etc/hosts"
192.168.1.15 server-a
192.168.1.16 server-b
192.168.1.17 server-c
192.168.1.18 server-d
```

## Resolv.conf

- /etc/resolv.conf specifies the nameservers used for DNS resolution by the host. If you are using DHCP, this file is automatically populated with DNS record issued by DHCP server.
- It specifies the nameservers in order of search preference for resolver lookups, where it will actually use the DNS protocol for resolving the hostnames.

```python title="/etc/resolv.conf"
nameserver 127.0.0.53
options edns0 trust-ad
search .
```

## /etc/nsswitch.conf

- name services switch
- Lists the order of sources that must be used by various system library lookup functions. For example, `hosts` sets the order of hostname resolution to `files (aka - /etc/hosts/)` then `dns (aka - /etc/resolv.conf)`.

```python title="/etc/nsswitch.conf"
passwd:         files systemd sss
group:          files systemd sss
shadow:         files systemd sss
gshadow:        files systemd

hosts:          files mdns4_minimal [NOTFOUND=return] dns mymachines
networks:       files
```
