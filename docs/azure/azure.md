# Azure CLI reminder

## Connection to azure domain
```bash
az login
```

## Interact with azure registry
List all image from a registry
```bash
az acr repository list -n registry
```

List all tag of an image
```bash
az acr repository show-tags -n registry --repository app/sso/wbs_interface_sso
```

Delete specific tag of an image
```bash
az acr repository delete -n registry --repository debian --tag jessie-slim1
```

## Create security credentials for azure registry
Documentation: https://blogs.msdn.microsoft.com/stevelasker/2016/11/17/azure-container-registry-user-accounts/

### Create Read/Write user for azure registry 
```bash
az ad sp create-for-rbac --scopes subscriptions/<subscription_id>/resourceGroups/<group_id>/providers/Microsoft.ContainerRegistry/registries/registry --role Contributor --password <password>
```

#### Setup docker login Read/Write
```bash
mkdir -p /home/<user>/.docker/ && echo "{\"auths\": {\"registry\": {\"auth\": \"<token>\"}}}" > /home/<user>/.docker/config.json
```

### Create Read Only user for azure registry 
```bash
az ad sp create-for-rbac --scopes subscriptions/<subscription_id>/resourceGroups/<group_id>/providers/Microsoft.ContainerRegistry/registries/registry --role Reader --password <password>
```
#### Setup docker login Read Only

```bash
mkdir -p /home/<user>/.docker/ && echo "{\"auths\": {\"registry\": {\"auth\": \"<token>\"}}}" > /home/<user>/.docker/config.json
```
