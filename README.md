# Kubernetes Istio Demo

THIS IS WORK IN PROGRESS UNTIL IT ACTUALLY WORKS ;)

This Istio documentation is fantastic, so this is really just taking the 
most useful bits to get something up and running as quick as possible.

## Pre-requisites

- A running kubernetes cluster

## Install Istioctl

https://istio-releases.github.io/v0.1/docs/tasks/installing-istio.html

Install the `istioctl` binary from above, and make sure it's in your `PATH` env.

## Install Istio into cluster

```
kubectl apply -f ./manifests/istio-demo.yaml
```

## Configure automatic side-car injection (optional)

https://istio.io/docs/setup/kubernetes/sidecar-injection/#automatic-sidecar-injection


```
kubectl apply -f <(istioctl kube-inject -f samples/bookinfo/kube/bookinfo.yaml)
```

## Install example app

https://istio.io/docs/guides/bookinfo/


Install an example BookInfo application into the `default` namespace.


If you don't have automatic side-car injection, run:

```
kubectl apply -f <(istioctl kube-inject -f manifests/example-app/bookinfo.yaml)
```

Else: 

```
kubectl apply -f ./manifests/example-app/bookinfo.yaml
```

## Accessing the cool stuff

The following examples use `kubectl port-forward` which enables you to access running services via localhost on your browser (instead of settign up load-balancer/dns/etc)

### Tracing 

https://istio.io/docs/tasks/telemetry/distributed-tracing/

```
kubectl port-forward -n istio-system $(kubectl get pod -n istio-system -l app=jaeger -o jsonpath='{.items[0].metadata.name}') 16686:16686
```

### Visualizing Metrics (Grafana)

https://istio.io/docs/tasks/telemetry/using-istio-dashboard/

```
kubectl -n istio-system port-forward $(kubectl -n istio-system get pod -l app=grafana -o jsonpath='{.items[0].metadata.name}') 3000:3000
```

### Querying Metrics (Prometheus)

https://istio.io/docs/tasks/telemetry/metrics-logs/

```
kubectl -n istio-system port-forward $(kubectl -n istio-system get pod -l app=prometheus -o jsonpath='{.items[0].metadata.name}') 9090:9090
```

