## Links

[Linux](Linux)
[[kubecraft]]


## 3 Key Points

- How to set up a VM for testing/learning

## Summary

- Use Linux virtual machine manager
- Install ubuntu 24.04 iso
- Enable ssh, leave everything else stock
- Install details:
User: $Username
password: $XXXX

- How to force password auth

```bash
ssh -o PreferredAuthentications=password user@192.168.122.40
```


ssh config:
```bash
Host wakka
    HostName 192.168.122.40
    User user
    PubkeyAuthentication no
    PasswordAuthentication yes
    PreferredAuthentications password,keyboard-interactive
```


## Further Reading


## Tags


2026-02-24-0740