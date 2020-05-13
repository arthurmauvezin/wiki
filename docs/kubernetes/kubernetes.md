# Kubernetes

## Port-forward

```bash
kubectl port-forward <pod> <from_port> <to_port>
```

`<pod>` can take many arguments as a specific pod, `pods/...`, `deployment/...`, `rs/...`, `svc/...`

## Debug

See [official documentation here](https://kubernetes.io/docs/tasks/debug-application-cluster/debug-application/)

### Print object current state and informations
```bash
kubectl describe pods ${POD_NAME}
kubectl describe rc ${CONTROLLER_NAME}
```

### Print pod logs
```bash
kubectl logs [--previous] ${POD_NAME} ${CONTAINER_NAME}
```

### Execute command in pod 
```bash
kubectl exec ${POD_NAME} -c ${CONTAINER_NAME} -- ${CMD} ${ARG1} ${ARG2} ... ${ARGN}
```

### Check service endpoint
```bash
kubectl get endpoints ${SERVICE_NAME}
```

## Tools

### Stern - Grab multi pod logs
https://github.com/wercker/stern

Usage
```
stern pod-query [flags]
```

### Krew - Plugin manager
https://github.com/kubernetes-sigs/krew/

### Kubectl aliases
https://ahmet.im/blog/kubectl-aliases/

### Kubectl ctx & ns - Change cluster and namespace on the go
https://github.com/ahmetb/kubectx

### Shpod - consistent training env image to work on Kube
https://github.com/jpetazzo/shpod



