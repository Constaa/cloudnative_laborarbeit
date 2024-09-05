# Ollama chat bot

## Start Minikube

```bash
minikube start --mount-string="<your_project_path>\ollama:/c/SBX/cloud/Projekt/ollama" --mount
```

Beispiel für <your_project_path> bei mir: C:\SBX\cloud\Projekt

## Ingress einrichten

```bash
minikube addons enable ingress
```

```bash
minikube addons enable ingress-dns
```

## Start Ollama and Open-Webui

```bash
kubectl apply -k ./kubernetes
```

## Port forward Open-Webui auf Localhost

Unter _C:\Windows\System32\drivers\etc_ im File _hosts_ folgendes ergänzen:

127.0.0.1 ruhig.bleiben.com

Aleitung für MAC: https://timmehosting.de/hosts-datei-unter-macos-bearbeiten

## Zugriff auf Open-Webui über Browser

http://ruhig.bleiben.com

## Minikube stoppen

```bash
minikube stop
```

## Mnikube löschen

```bash
minikube delete
```
