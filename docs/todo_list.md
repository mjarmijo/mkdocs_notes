# TO DO

- Need to solve `["Error: Kubernetes cluster unreachable: Get \"https://192.168.1.52:6443/version\": dial tcp 192.168.1.52:6443: connect: no route to host"]`, while running: `ansible-playbook -i nuc_inventory --extra-vars '@passwd.yml' playbooks/k8s_resources.yml -vv`
- Update ansible with new ip addresses of the nucs and rerun the ansible code, see if that makes kubectl work
