# Ollama chat bot

## Start Minikube

```bash
minikube start
```

## Start Ollama and Open-Webui

```bash
kubectl apply -k ./kubernetes
```

## Port forward Open-Webui auf Localhost

```bash
kubectl port-forward deployment/ollama-webui 8080:8080
```

## Minikube stoppen (kein Datenverlust)

```bash
minikube stop
```

## Mnikube löschen (Datenverlust)

```bash
minikube delete
```
