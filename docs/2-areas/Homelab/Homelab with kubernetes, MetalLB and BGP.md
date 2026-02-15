
[[Kubernetes]]
[[Metal LB]]


https://www.growse.com/2019/04/13/at-home-with-kubernetes-metallb-and-bgp.html

Kubernetes has a general design model of separating out capabilities from implementations - a Service will simply ask for a load balanced IP address from K8s, and it’s then up to the K8s API to select an available implementation and call that to actually provide and configure that. If you’re running K8s on AWS, Amazon will provide an implementation that manages ELB resources in response to the demand by the cluster. If you spin up K8s on bare metal (e.g. via `kubeadm`), then you don’t get any implementations by default. However, [MetalLB](https://metallb.universe.tf/) is an open source implementation of a k8s load-balancer, so getting set up is a simple case of “download and install” (I used [helm](https://helm.sh) for this).

MetalLB presents a couple of different ways of solving the load balancer problem. The easiest approach to get set up with is “Level 2 mode”, where MetalLB configures each node to announce load-balanced IPs via ARP. So a Service that configures a load-balanced IP of `192.168.2.100` will cause each of the nodes that are running pods that map to that service to send ARP announcements for `192.168.2.100` on their MAC address. Local clients (on the same subnet) who want to route traffic to `192.168.2.100` simply make an ARP request, get the first response and send packets to that ethernet address. If the node goes down, the ARP announcement is withdrawn and other clients should remove that from their cache.

MetalLB provides an alternative, which is to use [BGP](https://metallb.universe.tf/configuration/#bgp-configuration) to announce IPs. BGP is the common protocol widely used for routers to announce available routes to other routers, and thus coordinate available routes for IP traffic. A typical BGP announcement is (simplistically) of the form “Hi, Subnet `x` can be routed via IP `y` with a metric of `z`”, so in the context of load-balancing, MetaLB just announces that a subnet of a single IPv4 address (a `/32`) is to be routed via the node IPv4 address that is hosting the correct pod.