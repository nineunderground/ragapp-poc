### Requirements

A dedicated K8 cluster with at least a node group that has GPU nodes tainted with following:

```
        - key: "gpu-only"
          operator: "Equal"
          value: "yes"
          effect: "NoSchedule"
```

### Deploy tools

```

# kubectl apply -f https://raw.githubusercontent.com/NVIDIA/k8s-device-plugin/v0.14.0/nvidia-device-plugin.yml
# or:
kubectl apply -f .\nvidia-plugin\

kubectl create ns qdrant
kubectl apply -f .\qdrant\ -n qdrant

kubectl create ns ollama
kubectl apply -f .\ollama\ -n ollama

kubectl create ns rag
kubectl apply -f .\ragapp\ -n rag

```

### Usage

```

kubectl port-forward -n rag svc/ragapp 8000:8000
http://localhost:8000/admin/
http://localhost:8000/

```
