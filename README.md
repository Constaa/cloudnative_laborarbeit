# Ollama chat bot

## Zielsetzung der Anwendung
Die Zielsetzung dieser Anwendung ist es, ein selbst gehostetes LLM (Large Language
Model) Chatbot-System bereitzustellen, das auf dem eigenen Rechner betrieben wird.
Das Hosting auf der eigenen Hardware gewährleistet hohe Datensicherheit und Kontrolle
über die sensiblen Informationen. Die Anwendung nutzt eine Microservices-Architektur
auf Kubernetes, um Anfragen effizient zu verarbeiten, dynamisch zu skalieren und das
System zu überwachen. Sie kann mehrere Instanzen eines Open-Source-LLMs ausführen
und die Skalierung basierend auf der Last automatisch anpassen. Zusätzlich besteht die
Möglichkeit, bei Bedarf über APIs auf LLMs von OpenAI zuzugreifen, was jedoch mit
einem potenziell geringeren Maß an Datensicherheit verbunden ist.

Das Projekt verfügt über persistente Datenspeicherung für die LLMs sowie auch Chatverläufe etc. (Ordner wird automatisch lokal erstellt).
Somit wird auch die Datenintegrität sichergestellt wenn ein Node stirbt. 

Automatische SKalierung durch Implementierung von Prometheus möglich. Aktuell dynamisch, aber manuell. Wir starten mit 2 Deployments.

Aktuell Single-User Only, da noch keine Lösung für Multi-WebUI Deployment implementiert wurde. Ist was für die Zukunft.

Ohne GPU-Support, weshalb die Geschwindigkeit entsprechend langsam ist. 

Load Balancing automatisch durch Kubernetes. NGINX ist externer LB? --> ERgänzung notwendig

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

## Domain hinterlegen

In unserem Projekt haben wir den Ansatz gewählt, dass wir eine customized Domain hinterlegen.
Hierzu wird in der webui-ingress.yaml die Domain festegelegt. Diese muss anschließend im System ergänzt werden.

In unserem Beispiel wurde die Domain: **ruhig.bleiben.com** gewählt.


Unter _C:\Windows\System32\drivers\etc_ im File _hosts_ folgendes ergänzen:

```bash
127.0.0.1 ruhig.bleiben.com
```

Anleitung für MAC: https://timmehosting.de/hosts-datei-unter-macos-bearbeiten

## Tunnel für Minikube
Der Tunnel wird benötigt, da Minikube default nicht extern erreichbar ist.

```bash
minikube tunnel
```

## Zugriff auf Open-Webui über Browser
Registrieren und loslegen!

http://ruhig.bleiben.com

## Minikube stoppen

```bash
minikube stop
```

## Mnikube löschen

```bash
minikube delete
```
