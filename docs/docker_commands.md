# commands

## Ansible

## go to ansible docker file

cd /home/linux-joe/git/dockerfiles/ansible

<!-- ##  Start container and enter bash  NEVER NEED THIS SO REMOVE? 

sudo docker run --entrypoint "" -it py_ansible bash   -->

## Build the container

sudo docker build . -t py_ansible

## Start ansible container

sudo docker compose run ansible

## in the container

ansible-playbook -i nuc_inventory playbooks/hello_world.yml
ansible-playbook -i nuc_inventory playbooks/

## Sudoers and using become

ansible-playbook -i nuc_inventory --extra-vars '@passwd.yml' playbooks/shutdown.yml
ansible-playbook -i nuc_inventory --ask-vault-pass --extra-vars '@passwd.yml' playbooks/nuc_config_playbook.yml
ansible-playbook -i nuc_inventory --extra-vars '@passwd.yml' playbooks/nuc_config_playbook.yml
ansible-playbook -i nuc_inventory --extra-vars '@passwd.yml' playbooks/k8s_prereqs_playbook.yml
ansible-playbook -i nuc_inventory --extra-vars '@passwd.yml' playbooks/k8s_prereqs_playbook.yml --tags "waka"
ansible-playbook -i nuc_inventory --extra-vars '@passwd.yml' playbooks/k8s_resources.yml -vv

## site.yml and limit to 2 nodes

ansible-playbook -i nuc_inventory --extra-vars '@passwd.yml' site.yml -l nuc1,nuc4  -vv
ansible-playbook -i nuc_inventory --extra-vars '@passwd.yml' site.yml -l nuc1,nuc4  -vv --check  
ansible-playbook -i nuc_inventory --extra-vars '@passwd.yml' site.yml -vv

## Kubectl commands

`kubectl get svc nginx -o jsonpath='{.status.loadBalancer.ingress[0].ip}'`
INGRESS_EXTERNAL_IP=`kubectl get svc nginx -o jsonpath='{.status.loadBalancer.ingress[0].ip}'`

- metal lb tutorial: <https://www.adaltas.com/en/2022/09/08/kubernetes-metallb-nginx/>

kubectl -n metallb-system describe controller-7499d4584d-28ccw
kubectl -n metallb-system get secret metallb-webhook-cert -ojsonpath='{.data.ca\.crt}'
kubectl -n metallb-system get secret metallb-webhook-cert -ojsonpath='{.data.ca\.crt}' | base64 -d
kubectl -n metallb-system get secret metallb-webhook-cert -ojsonpath='{.data.ca\.crt}' | base64 -d > caBundle.pem
kubectl -n metallb-system get secret webhook-server-cert -ojsonpath='{.data.ca\.crt}'
kubectl -n metallb-system get secret webhook-server-cert -ojsonpath='{.data.ca\.crt}' | base64 -d
kubectl -n metallb-system get secret webhook-server-cert -ojsonpath='{.data.ca\.crt}' | base64 -d > caBundle.pem
kubectl create deploy nginx --image nginx
kubectl expose deploy nginx --port 80 --type LoadBalancer
kubectl delete deployment nginx
kubectl delete pod -n kube-flannel -l app=flannel
kubectl delete pod -n metallb-system
kubectl delete pod -n metallb-system -l app=metallb
kubectl delete pod -n metallb-system -l metallb
kubectl delete svc nginx
kubectl describe crd ipaddresspools.metallb.io
kubectl describe nodes
kubectl describe nodes nuc1
kubectl describe pod test-pod-nginx
kubectl describe pods
kubectl describe pods --all-namespaces
kubectl describe pods -n default
kubectl describe pods -n default nginx-7854ff8877-j292l
kubectl describe pods -n default nginx-7854ff8877-pfvhq
kubectl describe pods -n kube-flannel
kubectl describe pods -n metallb-system
kubectl describe service nginx
kubectl describe svc
kubectl describe svc kubernetes-dashboard
kubectl describe svc metallb
kubectl describe svc metallb-system
kubectl describe svc metallb-webhook-service
kubectl describe svc metallb-webhook-service -n metallb-system
kubectl edit configmap
kubectl get all
kubectl get all --all-namespaces
kubectl get crd
kubectl get endpoints -n metallb-system
kubectl get endpoints -n metallb-system~
kubectl get events --sort-by=.metadata.creationTimestamp
kubectl get logs -n kube-flannel
kubectl get logs -n kube-flannel kube-flannel-ds-8755f
kubectl get namespace
kubectl get nodes
kubectl get nodes --help
kubectl get nodes --show-label
kubectl get nodes --show-labels
kubectl get nodes -o wide
kubectl get pod --all-namespaces
kubectl get pods
kubectl get pods --all-namespaces
kubectl get pods -n default
kubectl get pods -n metallb-system
kubectl get secrets
kubectl get secrets -n metallb-system
kubectl get service -n metallb-system
kubectl get service -n metallb-system  metallb-webhook-service
kubectl get service -n metallb-system  webhook-service
kubectl get svc
kubectl get svc --help
kubectl get svc nginx
kubectl get svc nginx -o
kubectl get svc nginx -o json
kubectl get svc nginx -o jsonpath
kubectl get svc nginx -o jsonpath='{.status.loadBalancer.ingress[0].ip}
kubectl get svc nginx -o jsonpath='{.status.loadBalancer.ingress[0].ip}'
kubectl get svc nginx -o jsonpath='{.status}'
kubectl get validatingwebhookconfiguration metallb-webhook-configuration -ojsonpath='{.webhooks[0].clientConfig.caBundle}'
kubectl get validatingwebhookconfiguration metallb-webhook-configuration -ojsonpath='{.webhooks[0].clientConfig.caBundle}'
kubectl get validatingwebhookconfiguration metallb-webhook-configuration -ojsonpath='{.webhooks[0].clientConfig.caBundle}' | base64 -d
kubectl list svc
kubectl log nginx-7854ff8877-j292l
kubectl logs -n kube-flannel kube-flannel-ds-8755f
kubectl logs nginx-7854ff8877-j292l
kubectl logs test-pod-nginx
kubectl port-forward -n kubernetes-dashboard svc/kubernetes-dashboard 8080:443
kubectl proxy
kubectl run -i --tty --rm test-pod-nginx --image=nginx --restart=Never --namespace default

### expose a running service with the load balancer

k -n kubernetes-dashboard expose service kubernetes-dashboard-web --type=LoadBalancer --name=kubernetes-dashboard-svc

enable kube dashboard with https so token works: (edit the the kong proxy service to have a nodeport and go directly to i, circumvent the loadbalancer ip)

<https://github.com/kubernetes/dashboard/issues/9066#issuecomment-2254511968>
dashboard IP with kong modified: <https://192.168.1.47:32260/>
dashboard via svc external ip: 192.168.1.241:8000

# START HERE

Why the difference?  Kong is circumventing tls, but how, it is able to go directly to web? Need to understand traffic flow into k8s pods.

## helm

  100  helm repo add kubernetes-dashboard <https://kubernetes.github.io/dashboard/>
  102  /usr/local/bin/helm list --output=yaml
  103  /usr/local/bin/helm list --output=yaml --filter kube-dashboard
  104  /usr/local/bin/helm list --output=yaml --filter kubernetes-dashboard
  105  helm upgrade --install kubernetes-dashboard kubernetes-dashboard/kubernetes-dashboard --create-namespace --namespace kubernetes-dashboard
  106  helm delete kubernetes-dashboard --namespace kubernetes-dashboard

## Ansible vault

To create a new encrypted data file, run the following command:

`ansible-vault create foo.yml`

To edit an encrypted file in place, use the ansible-vault edit command. This command will decrypt the file to a temporary file and allow you to edit the file, saving it back when done and removing the temporary file:

`ansible-vault edit foo.yml`
