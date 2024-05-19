# Helm Chart Demo application

This Helm chart deploys a multi-service application on Kubernetes. The stack includes Nginx as a reverse proxy, a Java-based web application, a React-based UI, and two Python services.

## Prerequisites

- Kubernetes cluster
- Helm 3.x

## Chart Structure

├── Chart.yaml
├── values.yaml
├── templates/
│ ├── _helpers.tpl
│ ├── nginx-deployment.yaml
│ ├── nginx-service.yaml
│ ├── nginx-configmap.yaml
│ ├── java-webapp-deployment.yaml
│ ├── java-webapp-service.yaml
│ ├── react-ui-deployment.yaml
│ ├── react-ui-service.yaml
│ ├── python-service1-deployment.yaml
│ ├── python-service1-service.yaml
│ ├── python-service2-deployment.yaml
│ ├── python-service2-service.yaml
│ └── ingress.yaml
└── nginx/
└── nginx.conf


## Installation

1. Add your custom configuration to the `values.yaml` file if needed.
2. Install the chart using Helm:

```helm install kana-helm-demo ./kana-helm-demo```


Accessing the Application
Once the chart is successfully deployed, you can access the services as follows:

Nginx (Reverse Proxy): http://<nginx-service-IP>
React UI: http://<react-ui-service-IP>:3000
Java Web Application: http://<java-webapp-service-IP>:8080
Python Service 1: http://<python-service1-IP>:5000
Python Service 2: http://<python-service2-IP>:5001
If Ingress is enabled and configured, access the application via the Ingress host:

http://kana-helm-demo.local

## Customizing the Chart
You can override the default values by creating your own values.yaml file and using it when installing the chart:

```helm install kana-helm-demo ./kana-helm-demo -f your-values.yaml```

## Cleaning up
To uninstall the chart and remove all deployed resources, run:

```helm uninstall kana-helm-demo```