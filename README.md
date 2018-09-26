# Canary Deployment using Istio with Helm
## Install Istio
* Download the Istio release from the [releases page](https://github.com/istio/istio/releases/) and extract
* Apply Custom Resource Definitions: `kubectl apply -f install/kubernetes/helm/istio/templates/crds.yaml`
* Install Istio with default mutual TLS authentication: `kubectl apply -f install/kubernetes/istio-demo-auth.yaml`
* Enable Istio sidecar auto-injection `kubectl label namespace <namespace> istio-injection=enabled`

#### For SSL Certificate
Create TLS Secret for securing gateway with HTTPS:
```
kubectl create -n istio-system secret tls istio-ingressgateway-certs --key priv.pem --cert cert.pem
```

Read more about TLS ingress gateway from [Secure Ingress Doc](https://istio.io/docs/tasks/traffic-management/secure-ingress/)
