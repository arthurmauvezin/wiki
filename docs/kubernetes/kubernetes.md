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
