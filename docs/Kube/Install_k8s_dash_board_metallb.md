# To expose the Kubernetes Dashboard using MetalLB, you need to follow a few steps. Here's a guide on how to set it up

## Step 1: Install MetalLB (if not already installed)

First, ensure that MetalLB is installed and running on your Kubernetes cluster.

1. Apply the MetalLB manifest:

   ```bash
   kubectl apply -f https://raw.githubusercontent.com/metallb/metallb/v0.13.3/manifests/metallb.yaml
   ```

2. Create a ConfigMap for MetalLB to use the address pool `my-test-app` that you created:

   Here's an example `ConfigMap` for MetalLB. Replace the IP range with the appropriate range you set for the `my-test-app` pool:

   ```yaml
   apiVersion: v1
   kind: ConfigMap
   metadata:
     name: metallb-config
     namespace: metallb-system
   data:
     config: |
       address-pools:
       - name: my-test-app
         protocol: layer2
         addresses:
         - 192.168.1.240-192.168.1.250  # Use the range from your address pool
   ```

   Apply this config with:

   ```bash
   kubectl apply -f metallb-config.yaml
   ```

### Step 2: Deploy the Kubernetes Dashboard

If you haven't already deployed the Kubernetes Dashboard, you can deploy it using the following command:

```bash
kubectl apply -f https://raw.githubusercontent.com/kubernetes/dashboard/v2.7.0/aio/deploy/recommended.yaml
```

### Step 3: Create a Service to Expose the Dashboard

Next, you need to expose the Kubernetes Dashboard through a LoadBalancer service that MetalLB can assign an IP to.

Create a `Service` definition for the Kubernetes Dashboard as follows:

```yaml
apiVersion: v1
kind: Service
metadata:
  name: kubernetes-dashboard
  namespace: kubernetes-dashboard
spec:
  selector:
    k8s-app: kubernetes-dashboard
  ports:
    - protocol: TCP
      port: 80
      targetPort: 9090
  type: LoadBalancer
```

Apply the service:

```bash
kubectl apply -f dashboard-service.yaml
```

### Step 4: Verify the LoadBalancer IP

MetalLB will assign an IP from the `my-test-app` address pool to the `kubernetes-dashboard` service.

You can check the assigned IP with:

```bash
kubectl get svc -n kubernetes-dashboard
```

You should see the `EXTERNAL-IP` populated with an IP address from the `my-test-app` pool.

### Step 5: Access the Dashboard

Once the service is exposed and the IP address is assigned, you can access the Kubernetes Dashboard by visiting the assigned IP address in your browser.

If you use port 80 in the service, just navigate to:

```bash
http://<assigned-ip>
```

### Step 6: Set Up the Access Token

To log in to the Kubernetes Dashboard, you'll need to create a ServiceAccount and ClusterRoleBinding for the necessary permissions:

```bash
kubectl create serviceaccount dashboard-sa -n kubernetes-dashboard
kubectl create clusterrolebinding dashboard-sa-binding \
  --clusterrole=cluster-admin \
  --serviceaccount=kubernetes-dashboard:dashboard-sa
```

Get the token for the `dashboard-sa` ServiceAccount:

```bash
kubectl -n kubernetes-dashboard create token dashboard-sa
```

This token can be used to log in to the Kubernetes Dashboard.

### Summary

1. Install and configure MetalLB.
2. Deploy the Kubernetes Dashboard.
3. Create a LoadBalancer service to expose the dashboard using the `my-test-app` address pool.
4. Retrieve the assigned IP address.
5. Log in to the dashboard with the generated access token.

Let me know if you need further clarification!
