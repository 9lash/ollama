# Running Ollama in Azure Arc enabled KIND cluster

To run: 

Arc onboard a KIND cluster.
```
kubectl apply -f llama-deployment.yaml
```

TO confirm if it works: 

```
kubectl -n azure-arc exec -ti “pod name” — /bin/bash
ollama —version
ollama pull llama3.2
ollama run llama3.2
``` 

Now you have an ollama model in azure-arc enabled airgapped kubernetes cluster. There are no egress calls to search over the internet. All responses are from the model . 

Pros: 
1. Runs on a 1 node KIND cluster
2. Useful for static knowledge base

Cons: 
1. Cannot perform tasks like performing a GET call to Kubernetes cluster API server to retrieve more information even when provided with context. It can only perform token completion. 
2. Cannot perform Search